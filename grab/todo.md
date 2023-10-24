1. Dependency-Update  [Log in - Jira](https://jira.grab.com/browse/IS-72403)
	1. 需要升级的包：
	~~2. osmtogeojson 内部. 升级完成
		1. minimist:0.0.5
		2. xmldom:0.1.27~~
	3. string-strip-html, 卡普勒。<font color="#ffff00">移除</font>
	4. mixin-deep、set-value --》 kepler内部
		1. 未找到
		2. 
	~~5. @antv/data-set:0.8.9~~
	~~6. redux:3.7.2~~
	7. pannellum.   内部。<font color="#c0504d">是否尝试更新npm上的</font>  <font color="#ffff00"> 可以移除</font>. 
		1. 替换了一下，无影响
	~~8. moment~~
	~~9. fabr. c~~
	~~10. string-strip-html~~
	~~11.  @mapbox/mapbox-gl-draw:1.1.2~~
	~~12.  dexie~~



![[Pasted image 20231018141254.png]]  提交时校验


~~2-checker  设置最小值 input.~~ , street-name 更新取消和点X，

 ~~调整 form 的宽度的调整,  图片btn~~
 ~~website去掉前缀，~~


TODO:
	**poi相关**
1~~. poi不存在street id时，不应该自动默认填充街道  update的时候不存在的时候不填，创建的时候填充~~
	IT.2GYS44HJDYLCE edit not auto fill
	
~~1. street list添加create a new street~~
2. 
 3。street 创建返回duplicate时，有机制可选择返回的street id
	 拿到dedup的id
4~~. 根据街道名称搜索，返回结果去重 @xiao.hu~~~~ 
5. 显示选择的街道相关地理信息在地图上
	1. 显示路径图 low
	2. 1.305887,103.82109.  STREET.37UOHRYM5E0JV
6. update street有bug，关闭不了
	1. name 清空的问题


**poi colleciton相关**
	比如  place page need to get poi_id ?
