`/* eslint-disable react-hooks/exhaustive-deps */

import { PlusOutlined } from '@ant-design/icons'

import { API } from '@utils/api'

import { JarvisResponse, JarvisTaskType, ParkingTaskListResponseType } from '@utils/api/src/jarvis/jarvisType'

import { Button, Card, Col, DatePicker, Form, Input, message, Row, Select, Table, Tabs, Typography } from 'antd'

import dayjs from 'dayjs'

import { observer } from 'mobx-react-lite'

import React, { useEffect, useMemo, useState } from 'react'

import { useHistory } from 'react-router-dom'

import { useAsyncFn, useMount } from 'react-use'

  

import { JarvisTaskStatus } from '@/pages/landing-page/latitude/edit'

// import MultipleLanguages from '@/components/MultipleLanguageLabel'

import { useStores } from '@/stores'

import { startTask } from '@/utils/ga'

import { useInterval } from '@/utils/hooks'

import { transformTime } from '@/utils/utils'

  

import PendingTaskPlots from '../pending-task-plots'

let defaultDate = true

interface JarvisTaskProps {

source: string

jumpTo: (taskId: string) => string

createPOI?: boolean

}

  

enum TaskType {

// 'DFP' = 20,

'Latitude' = 3,

'FSQ' = 4,

'FSQ-Non Selections' = 5

}

enum TaskPath {

// 'DFP' = 'dfp-claim/',

'Latitude' = 'latitude-claim/',

'FSQ' = 'latitude-claim/',

'FSQ-Non Selections' = 'latitude-claim/'

// 'FSQ' = 22

}

const taskTypeOptions = [

// {

// label: 'DFP',

// value: 'DFP'

// },

{

label: 'Latitude',

value: 'Latitude'

},

{

label: 'Failed Search Queries',

value: 'FSQ'

},

{

label: 'FSQ-Non Selections',

value: 'FSQ-Non Selections'

}

]

  

const useTypeOptions = [

{

label: 'PASSENGER',

value: 1

},

{

label: 'DRIVER',

value: 2

},

{

label: 'VENDOR',

value: 3

},

{

label: 'DFH5_VENDOR',

value: 4

}

]

  

const TablePagination = {

position: ['bottomCenter']

}

  

export const ClaimLatitude: React.FC<JarvisTaskProps> = observer(({ jumpTo }) => {

const { session, common } = useStores()

  

const [form] = Form.useForm<{

date: [Date, Date]

country: number

city: number

user_id?: number

user_type?: number

source?: string

}>()

  

const [selectedCounty, setSelectedCountry] = useState<number | null>(null)

const [useType, setUserType] = useState()

const [currentSource, setCurrentSource] = useState('Latitude')

const [columnData, setColumnData] = useState([])

const [taskCountAction, queryTaskCount] = useAsyncFn(

async (uploadSource: string, country_id: number, city_id: number, date?: [Date, Date]) => {

const { data } = await API.jarvis.getJarvisTaskCount({

source: TaskType[uploadSource],

country_id,

city_id,

date_from: date?.[0] ? transformTime(dayjs(date[0]).startOf('day')) : null,

date_to: date?.[1] ? transformTime(dayjs(date[1]).endOf('day')) : null,

status: 0

})

return data.data

},

[]

)

const [time, setTime] = useInterval(0)

const cities = useMemo(() => {

if (selectedCounty) {

return common.cities.filter(x => x.country_id === selectedCounty)

}

return common.cities

}, [common.cities, selectedCounty])

const [isFetching, setFetching] = useState(false)

  

const [parkingList, fetchParkingList] = useAsyncFn<

(source) => Promise<JarvisResponse<ParkingTaskListResponseType<JarvisTaskType>>>

>(

async source => {

const { id } = session.currentUser

const { data } = await API.jarvis.getParkingList({

page: 1,

page_size: 1000,

source: TaskType[source],

reviewer_id: id

})

if (data.status_code !== 0) {

message.error('Failed to get the parking tasks. ' + data.message)

return

}

return data

},

[],

{

loading: false,

value: {

message: '',

request_id: '',

status_code: 0,

data: { tasks: [], pagination: { total_count: 0, current_page: 1, page_size: 1000 } }

}

}

)

  

const history = useHistory()

  

const onClick = () => async () => {

form

?.validateFields()

.then(async values => {

const { country, city, date, user_type, user_id } = values

// const utc = convertLocalToUtc([startDate, endDate])

const params = {

source: TaskType[currentSource],

city_id: city,

user_type,

user_id,

country_id: country,

date_from: date?.[0] ? transformTime(dayjs(date[0]).startOf('day')) : null,

date_to: date?.[1] ? transformTime(dayjs(date[1]).endOf('day')) : null

}

localStorage.setItem(`Claim${currentSource}TaskRequest`, JSON.stringify(params))

setFetching(true)

let finialData = null

const { data } = await API.jarvis.claimJarvisTask(params)

finialData = data

  

while (Number(finialData.data.status) === JarvisTaskStatus['IsDup']) {

const { data } = await API.jarvis.claimJarvisTask(params)

finialData = data

}

  

if (finialData.status_code !== 0) {

if (finialData.message.includes('no task')) {

setTime(10)

return message.info('There is no data to claim')

}

  

message.error('Failed to claim the tasks. ' + finialData.message)

return

}

startTask(finialData.data.task_id)

history.push(jumpTo(TaskPath[currentSource] + finialData.data.task_id + '/' + currentSource))

})

.catch(error => {

console.error(error)

message.error(error)

})

.finally(() => {

setFetching(false)

})

}

const isNoPermission =

!session.hasRole('GoldenPOIOperator') &&

!session.hasRole('MapOps') &&

!session.hasRole('SuperAdmin') &&

!session.hasRole('KartaEngg') &&

!session.isVendor

  

const queryPendingTasks = () => {

form?.validateFields().then(values => {

const { country, city, date, source } = values

queryTaskCount(source, country, city, date)

fetchParkingList(source)

getTaskPendingPlotsData({

source,

country_id: country,

city_id: city,

date

})

})

}

  

const getTaskPendingPlotsData = async params => {

const {

country_id,

city_id,

is_merchant_food,

is_in_entrance,

date,

is_venue,

poi_source,

business_type,

signal,

user_type,

user_id,

round

} = params

const { data } = await API.jarvis.getTaskPendingPlotsData({

source: TaskType[form.getFieldValue('source')],

country_id: country_id,

city_id: city_id,

poi_source,

is_in_entrance: is_in_entrance || 2,

is_venue: is_venue || 2,

is_merchant_food: is_merchant_food || 2,

status: 0,

business_type,

signal,

is_golden: 2,

user_type,

user_id: user_id || null,

round,

date_from: date?.[0] ? transformTime(dayjs(date[0]).startOf('day')) : null,

date_to: date?.[1] ? transformTime(dayjs(date[1]).endOf('day')) : null

})

  

if (data?.data?.task_count_per_day?.length) {

data?.data?.task_count_per_day.forEach(item => {

item['type'] = 'pending task'

})

}

if (defaultDate) {

if (data?.data?.task_count_per_day[0]?.date) {

form.setFieldValue('date', [dayjs(data?.data?.task_count_per_day[0]?.date), dayjs().endOf('day')])

}

defaultDate = false

}

setColumnData(data?.data?.task_count_per_day)

}

useMount(() => {

defaultDate = true

})

useEffect(() => {

setSelectedCountry(session.currentUser.country_id)

queryPendingTasks()

}, [session.currentUser, currentSource])

  

const handleChangeDateByChart = params => {

const { date } = params

form?.setFieldValue('date', [dayjs(date), dayjs(date)])

queryPendingTasks()

}

const renderTabsItems = [

{

key: 'claim page',

label: 'Claim Page',

children: (

<div style={{ padding: 32, background: '#F3F6FB' }}>

<Card

title={

<div style={{ padding: '28px 16px' }}>

<p style={{ margin: 0, fontSize: 24 }}>

{taskCountAction.loading ? 'Loading..' : `${taskCountAction.value?.task_count || 0} tasks pending`}

</p>

</div>

}

extra={

<div

style={{

display: 'flex',

justifyContent: 'flex-end',

alignItems: 'center',

flexDirection: 'row',

gap: 10

}}

>

{session.hasOneRoles(['MapOps', 'SuperAdmin', 'KartaEngg', 'VendorMapOps', 'GDActor']) && (

<Button

style={{

borderRadius: 32

}}

disabled={!!time}

onClick={onClick()}

loading={isFetching}

type='primary'

>

{time ? (

`Please wait ${time}s`

) : (

<>

<PlusOutlined />

Claim a {currentSource} Task

</>

)}

</Button>

)}

</div>

}

>

<div style={{ width: '100%', justifyContent: 'center' }}>

<PendingTaskPlots onClick={handleChangeDateByChart} columnData={columnData} />

</div>

<Form

form={form}

layout='vertical'

onValuesChange={changes => {

if (changes?.source) {

defaultDate = true

}

form?.validateFields().then(values => {

const { source } = values

setCurrentSource(source)

queryPendingTasks()

})

}}

initialValues={{

country: session.currentUser.country_id,

city: form.getFieldValue('city') || session.currentUser.city_id,

source: 'Latitude'

}}

>

<Card

style={{ margin: '20px 0', background: 'rgb(243, 246, 251)' }}

title={

<div>

Source &nbsp;

<Form.Item noStyle name='source'>

<Select

style={{ width: 200 }}

popupClassName='universal-select'

defaultValue={'verify_places'}

options={taskTypeOptions}

/>

</Form.Item>

</div>

}

>

{isNoPermission ? (

<p>No permissions for task operation</p>

) : (

<Row gutter={15}>

<Col span={8}>

<Form.Item label='Date' name='date'>

<DatePicker.RangePicker style={{ width: '100%' }} />

</Form.Item>

</Col>

<Col span={8}>

<Form.Item required label='Country' name='country'>

<Select

onChange={id => {

form.setFieldsValue({ city: null })

defaultDate = true

setSelectedCountry(id)

}}

>

{common.countries.map(({ name, id }) => (

<Select.Option value={id} key={`county-${id}`}>

{name}

</Select.Option>

))}

</Select>

</Form.Item>

</Col>

  

<Col span={8}>

<Form.Item required label='City' name='city'>

<Select

allowClear

showSearch

filterOption={(inputValue: string, option: React.ReactElement) => {

return option.props.children.toLowerCase().includes(inputValue.toLowerCase())

}}

>

{cities.map(({ name, id }) => (

<Select.Option value={id} key={`city-${id}`}>

{name}

</Select.Option>

))}

</Select>

</Form.Item>

</Col>

{/* <Col span={8}>

<Form.Item required label='Task Type' name='source'>

<Select

placeholder='Please select the task type'

allowClear

options={taskTypeOptions}

value={currentSource}

onChange={value => {

setCurrentSource(value)

}}

></Select>

</Form.Item>

</Col> */}

{TaskType[currentSource] === 20 && (

<>

<Col span={8}>

<Form.Item label='User Type' name='user_type'>

<Select

allowClear

options={useTypeOptions}

placeholder='Please select the option'

onChange={value => {

form.setFieldsValue({ user_id: null })

setUserType(value)

}}

/>

</Form.Item>

</Col>

<Col span={8}>

<Form.Item

label='User ID'

name='user_id'

rules={[

{

validator: async (_: unknown, value): Promise<void> => {

const allValues = form.getFieldsValue()

if (allValues?.['user_type'] && !value) {

throw new Error('If select the user type, the user id can not be empty')

}

}

}

]}

>

<Input disabled={!useType} allowClear placeholder='Please input the user id'></Input>

</Form.Item>

</Col>

</>

)}

</Row>

)}

</Card>

</Form>

</Card>

</div>

)

},

{

key: 'parking list',

label: 'Parking List',

children: (

<div style={{ padding: 32, background: '#F3F6FB' }}>

<Card

title={

<div style={{ padding: '28px 16px' }}>

<p style={{ fontWeight: 600, fontSize: 24, margin: 0 }}>

{parkingList?.value?.data?.pagination?.total_count} parking lists

</p>

</div>

}

>

<Table

// eslint-disable-next-line @typescript-eslint/ban-ts-comment

// @ts-ignore

pagination={TablePagination}

dataSource={parkingList?.value?.data?.tasks}

loading={parkingList?.loading}

rowKey='task_id'

>

<Table.Column<JarvisTaskType> title='Task ID' dataIndex='task_id' />

{/* <Table.Column<JarvisTaskType> title='User Type' render={(_, record) => record?.contributor?.user_type} /> */}

<Table.Column<JarvisTaskType> title='User ID' dataIndex='reviewer_name' />

{/* <Table.Column<JarvisTaskType>

title='POI Name'

dataIndex='task_name'

render={text => <MultipleLanguages nilColor='rgb(219, 219, 219)' names={text} shortLang />}

/> */}

{/* <Table.Column title='Parked At' render={(_, record) => dayjs(record.updated_time).format('DD/MM/YYYY')} /> */}

<Table.Column<JarvisTaskType>

title='Action'

dataIndex='task_id'

render={(_, record) => {

const handleRepickTask = async () => {

try {

const { data } = await API.jarvis.repickJarvisTask(record.task_id)

if (data.status_code !== 0) {

message.error('Failed to pick the tasks ' + data.message)

return

}

history.push(

`/workflow/landing-page/${TaskPath[currentSource] + record.task_id + '/' + currentSource}`

)

} catch (error) {

console.error(error)

message.error('Failed to repick the task')

}

}

return (

// eslint-disable-next-line jsx-a11y/anchor-is-valid

<a role='button' tabIndex={0} onClick={handleRepickTask}>

Repick

</a>

)

}}

/>

</Table>

</Card>

</div>

)

}

]

  

return (

<div>

<Typography.Title level={3} style={{ padding: '20px 32px', borderBottom: '1px solid #E5E9F0' }}>

Latitude/FSQ

</Typography.Title>

  

<Tabs

className='claim-page'

size='large'

tabBarStyle={{

fontWeight: 600,

fontSize: 16

}}

defaultActiveKey='claim page'

items={renderTabsItems}

></Tabs>

</div>

)

})

  

export default ClaimLatitude``