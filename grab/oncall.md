1、booking 找 FYI @/oncall-geo-tools 里的同学，geo-tools上这个booking debugging tool 
已经 deprecated 了，如果想看 booking information，让找 [@oncall-dexter](https://grab.enterprise.slack.com/admin/user_groups). 如果问 debugging tool API 或者上面的 Nav Deviation tab 的事儿，hand over to [@wenchao.xu](https://grab.slack.com/team/U03KANVDXMZ) 了，可以转发给 [@oncall-route-engine](https://grab.enterprise.slack.com/admin/user_groups) ..

2、dax 区分android or ios √[@karta-poi-adr](https://grab.slack.com/admin/user_groups) [@karta-poi-ios](https://grab.slack.com/admin/user_groups)
3、权限 If others want to check POI & sta, I think techsupport role maybe better
permission deny. Please request the `**StaOperator**` **role. FYI** [https://docs.google.com/document/d/1ayGcfFrVyKCd8OWhENYFmt8cMPM8-4RVYDvaByNqvOc/edit](https://docs.google.com/document/d/1ayGcfFrVyKCd8OWhENYFmt8cMPM8-4RVYDvaByNqvOc/edit)


[@oncall-geo-tools-customer](https://grab.enterprise.slack.com/admin/user_groups) related to ops tool & kartaMaps issues on Geo-tools portal, POI karta portal & vendor portal review workflow issues  
[@oncall-map-tiles](https://grab.enterprise.slack.com/admin/user_groups) map tiles issues  
[@zhifan.pan](https://grab.slack.com/team/WRVC4RJ7M) GrabMap Web issues, SDK.  
[@oncall-kartaview](https://grab.enterprise.slack.com/admin/user_groups) kartaview issues  
[@karta-poi-adr](https://grab.enterprise.slack.com/admin/user_groups) [@karta-poi-ios](https://grab.enterprise.slack.com/admin/user_groups) POI crowdsourcing mobile device issue.   geofence @yazhen.yuan
[@oncall-route-engine](https://grab.enterprise.slack.com/admin/user_groups) route issue



4: 更改越南 house number source：  **Required for residential POI, optional for non-residential POI** 

1、nearby标记 对应国家语言
	点击后展示多语言
2、如果开启啦normalization 移除admin area
	po-man
	workflow
3、检查
4、2 checker AHT


oncall记录：
	
	KARTAPLACE-1493


~~food的两个source report page~~
~~poi-collection 的布局~~



当poi 状态是 active的时候，禁止编辑,
	减少task

street 清除时，禁用edit
	多语言删除， 取消。进入model 编辑更新。


看下slack 频道 #ask-cn-it
 
Huiyuan Shi对所有人说 (2023年12月8日，10:52)
123.125.92.227:4443
221.122.65.147:4443 
这个地址测试一下 如果可以 临时使用这个地址

Hi [@kelvin.mathew](https://grab.slack.com/team/WRU33AAF4), please ask them try to open this [page](chrome://flags/) and search `rasterization`. If there is disabled, please set `default` or `enabled`.  It is optional but if enable these options may accelerate image rendering on local devices. Team will also keep tracking this issue do some optimization maybe. cc [@changlin.shi](https://grab.slack.com/team/U02GD57JRSL)

Screenshot 2023-12-27 at 18.14.58.png




