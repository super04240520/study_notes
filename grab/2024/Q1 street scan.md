[Figma](https://www.figma.com/file/sujHcqYen1591yimqoavQX/Karta-Street-Scan?type=design&node-id=0-1&mode=design&t=6eeuQd7X9zMVErgs-0)



[Log in - Jira](https://jira.grab.com/browse/JARVIS-1837)

[Log In - Grab Wiki](https://wiki.grab.com/pages/viewpage.action?spaceKey=GEO&title=%5BNew%5D+Universal+Task+Review+API)
街景图重新更改，task图片做分类。


test: w21zdz
w7g0v6
current: [JARVIS-1900](https://jira.grab.com/browse/JARVIS-1900)



 KARTAPLACE-1850
q缺:
 1、street view 
 2、card 和 maker联动
	 select all 和单独的 checked的数据 以及maker 联动
 3、single submit / 单独的详情card, 
 ~~4、maker的状态更新~~
 5、submit
	 两个提交
 ~~6、套索数据提取~~
	 ~~需要一个工具函数, 提取出选择的taskid, 需要在layer中,添加task_id~~
	 

qw3zk5

ui:
	编辑后的状态, 
	 同时选中,同时编辑
	 选中一个,编辑另一个.


claim 新增source


4月2
	1、拉索, 添加filer
	2、 随机claim 10个。 low
	 3、~~猫店定位。 pre-task。~~ 只有更新状态时, 进行下一个. 1
	 4~~、nearby list table 1~~
	 ~~5、form 添加 admian area parh 1~~
	 6、点击跳转,latitude的form的页面 1
	 7、appear hours for card
	 ~~8、edit 后, 默认选中task,  maker位置没有更新 1~~
	 ~~9、name取值,取第一个值. 1~~
	 ~~10、sumbit erro 没报出来  1~~~~
	 ~~11, submit &next只要有成功的, 就可以点击1~~
	 12, 去掉claim hash的日期

demo  mock
	w7erbj
去除status
	 nearby 搜索高亮 icon 变小, 
	 ~~margin 改变小一点.~~ 
	  前端不展示:  已经操作过的
     添加一个filter 在拉索和task中的拉索
     task list 改成抽屉. 图片展示在右侧.


1. ~~geohash map 没按照用户所属跳转 [@dongming.wang](https://grab.slack.com/team/WS8MXCUMD)~~
2. landing page filter如果选择或者添选的geohash值，pending count数量不对 [@changlin.shi](https://grab.slack.com/team/U02GD57JRSL) chao.an
3. 套索圈选的point，shift按键冲突，layer UI样式， 销毁error [@dongming.wang](https://grab.slack.com/team/WS8MXCUMD)
4. ~~选中的point layer样式，非选中的为透明状态 [@changlin.shi](https://grab.slack.com/team/U02GD57JRSL)~~
5. task submit error  @ anchao
6. ~~API error message [@changlin.shi](https://grab.slack.com/team/U02GD57JRSL)~~
7. ~~同一地点多个poi覆盖UI，search nearby UI需要设计~~
8. kartaview tool [@dongming.wang](https://grab.slack.com/team/WS8MXCUMD)
9. ~~latitude 图片添加 [@changlin.shi](https://grab.slack.com/team/U02GD57JRSL)~~
10. 更改layout，允许显示多个状态的task以及filter [@changlin.shi](https://grab.slack.com/team/U02GD57JRSL)
11. ~~跳转到详情页面编辑 [@changlin.shi](https://grab.slack.com/team/U02GD57JRSL)~~
12. ~~创建额外新的poi [@changlin.shi](https://grab.slack.com/team/U02GD57JRSL)~~
	 

E-YKjfiLwZM3dtxbJ6QAjeA==



4.9 
 1. geohash map rerender @dongming.wang
 2.  accept reject的有信息框
 3. task maker 换 成layer和feature组合 就可以拖拽了 文字 style  @changlin
	 1. 当review时,非review的layer只灰
 4. 聚合layer的状态。和hover后的poi name   @dongming
 5. task list页面 页面聚合 @dongming
 6. filter btn @changlin
 7. gettaskby geohash 与get detail的状态不一致 @chao.an
 8.  全部走batch-submit @changlin
 9. 点击更新后, card按钮全部disable掉, 做完就置灰 @changlin
 10. 进详情后,的nearby style. @changlin
 11. ath 中 submisubmit跟计时器绑定 @changlin  按钮 AHT submit
 12. author在submis上的时候,绑定
 13. batch park 状态拦截 @chao.an
 14. latitude source create new poi 接口 @chao.an
 15. claim page count @chao.an
 16. imge的值text的值

