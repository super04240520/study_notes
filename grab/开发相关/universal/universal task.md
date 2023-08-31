

1、需要重现拉取 poi_data by id
2、Change some page anchors

todo: 
task相关
~~1、 毛点问题 pri。~~ 
	a: 数据在store进行区分，计算属性判断是否存在值
	~~b:  ops判断后的yes 或no的值。需要确认一下~~~~~~
	 日期选择时需要判断是否重复。
页面相关
		根据exist location 获取地图相关信息
			map联动
		 ~~name的多次添加~~ 暂用现有组件。
		 address 根据 国家进行normalize
数据相关：
	    除hours相关的数据提取,测试
	    接收数据转换（custom 部分）
	    form data集成
		    数据提交转换
		
<font color="#c0504d">**与ui的区别**</font>
	1.  ~~name的多次添加~~ 暂用现有组件。
	2. hour还是使用24小时制
	3. 
	

1:   universal task workflow 1.0

~~*poi_category ---- bussiness_type*~~


~~当poi exist 选择 NO 时，其他card 不展示，放到store中渲染。~~

在addresss 选择 yes 时，展示下面 unit 等（根据国家判断，渲染）
                           no时不展示。 放到组建内部渲染。
~~2: image 参数需要前端请求，切id
[https://prd-karta-crowdsourcing.s3.ap-southeast-1.amazonaws.com](https://prd-karta-crowdsourcing.s3.ap-southeast-1.amazonaws.com) 
key::::::
images/2023/6/29/63a58ceb-2814-4bd2-8afd-ecc51db43ee1.jpeg](https://prd-karta-crowdsourcing.s3.ap-southeast-1.amazonaws.com/images/2023/6/29/63a58ceb-2814-4bd2-8afd-ecc51db43ee1.jpeg)
	       `"[https://prd-karta-crowdsourcing.s3.ap-southeast-1.amazonaws.com/images/2023/6/29/63a58ceb-2814-4bd2-8afd-ecc51db43ee1.jpeg](https://prd-karta-crowdsourcing.s3.ap-southeast-1.amazonaws.com/images/2023/6/29/63a58ceb-2814-4bd2-8afd-ecc51db43ee1.jpeg)"~~`

TODO:
	name 添加自动填充
	~~image review tab 需要添加~~
	~~exist 的remark~~ 
E-7cQ4AaGrzN4rv9Ywo0jpw==

label 可以添加
ui颜色，tab颜色
user_type - user_id
~~yes or no 添加tag 用于区分~~
~~add place 需要review， 使用之前的review-modle~~
~~图片的correct也可以review  ridion button~~ 

name回填需要 选择多语言select选择



renpin需要项目要一下。


0: 整个项目覆盖
1、history page 更换list 图片
2、claim a task button 更换椭圆型
3、action button。  
4、两边的tab，左侧tab,绿色需要
5、头部task id。 有一些状体tag
6、review 部分背景，字体颜色
7、collector label 添加两行 tab
8、yes or no Disagree Collector/
9、radio  color
10、form背景颜色
11、 select 与remark 拉长距离近一点
12、custom 改成 Reviewer marker 使用verify 的样式
13、add  name 的tooltip / select
14、sunday 不加冒号
15、time 选择 closed添加艰巨， 组件padding尽量调整
16、time  modal 选额 border 左右不对齐
17、image review：  bad + good photo
18、submit 的modal 重写
19、点击exist 选择no的时候，tab变成灰色。


添加  poi -information
address 是否需要拼接，返回数据是否包含。
~~*source 进入不同陆游 包一层，根据source 进入不同页面*~~
image 后期会加入squence id 和 index。需要在数据层面，做兼容。


29号
~~0, task status 根据 task operation 判断，只有 init accept reject 三种~~
1~~、添加maker-动画。偏移量设置
		边界~~
2、address 添加is_normalize
	ui有出入。
3、TODO: image 后期会加入squence id 和 index。需要在数据层面，做兼容。
<font color="#ffc000">4、hours组件，错误提醒，自动填充当前时间</font>
QA case
1、添加realtime dedup
2、国家限制。只开PH
3、report 添加类型 下载
4、选择后 yes or no 后，必填
5、图片review必须后才能提交
	~~如果图片全部是bad的话，再聊一下。~~  去掉form的option
~~6、三个时间框。是否添加。~~


data：
	1、extra 数据确认



