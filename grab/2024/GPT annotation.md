1、poi id 可选 并可以搜索, 创建 2
~~2、accept的 pin hover的pop up 数据展示(根据source判断数据源) 0.5~~
3、annotation 页面 按钮问题 2
		a: 画框确定当前task
			~~当点击图片时, 其他根据当前task, 锁定, 将其他btn disable~~
		 ~~b:  根据是是否存在 画框数据, 给定task 一个状态, 比如: no annotation data ,画后去除~~
	
4、annotation review
      a: 图片定位到annotation 框 (kartaview api)
        ~~gpt 信息和poi 数据的转换(选中逻辑切换). 还有gpt 卡片展示逻辑修复~~
    b: disable the btn when user submit the task(change status)
    <font color="#c0504d">  c:  update existing_duplicated_poi_ids 问题,</font>
5、图片点击问题
		~~根据img id和task id  re-render(不同task共用同一张360)~~
		 
<font color="#ffc000">history review page for annotation review </font>
1、ID 可选, 动态添加 
		a:  可删除review的框,同时保持id跟框了联动
			i: 通过model 展示poi信息
			 详情参考Jarvis  [jarvis.geo.azure.stg-myteksi.com/codeless-portal/login/concedo?redirect=%2Fmicro-task%2FEHEpPYL7CII\_Ob1jM91HmWQ%3D%3D#latitude=1.5483214&longit[…]59&zoom=15.793842916991498](https://jarvis.geo.azure.stg-myteksi.com/codeless-portal/micro-task/EHEpPYL7CII_Ob1jM91HmWQ==#latitude=1.5483214&longit[…]59&zoom=15.793842916991498)
         b: 不同颜色区别框选状态