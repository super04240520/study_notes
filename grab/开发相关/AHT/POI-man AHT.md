
poi
1. 后端加了创建以及更新两个[API](https://gitlab.myteksi.net/gophers/go/-/merge_requests/138580/diffs)提供了reference参数，用于统计referType以及referID, 分别是任务类型和task任务id，通过路由参数获取传值，主要用于POI details等项目直接用poi man更新但没task的绑定
[Sign in to Grab | Slack](https://grab.slack.com/archives/C048HBNDLUT/p1703495222253719)

关于poi details和Nudge跳转到poi man的更新创建操作，有以下两个问题  

1. POI details和Nudge传到poi man的refer_type需要确定两个固定值用以区别，后端有个验证 cc [@wenyue.zhao](https://grab.slack.com/team/U0271RHPQKD)
2. 传过来的task_id可以是未加密的吗

`POI_DETAILS`, `POI_NUDGE`

![:确定的手势:](https://a.slack-edge.com/production-standard-emoji-assets/14.0/apple-small/1f44c@2x.png)1

![白色的对勾](https://a.slack-edge.com/production-standard-emoji-assets/14.0/apple-small/2705@2x.png)![眼睛](https://a.slack-edge.com/production-standard-emoji-assets/14.0/apple-small/1f440@2x.png)![举起双手](https://a.slack-edge.com/production-standard-emoji-assets/14.0/apple-small/1f64c@2x.png)

![](https://ca.slack-edge.com/EPTPF553J-WS8MXCUMD-382e30e0e07b-48)

Dongming Wang  [3 天前](https://grab.slack.com/archives/C048HBNDLUT/p1703497183969069?thread_ts=1703495222.253719&cid=C048HBNDLUT)  

[#2](https://grab.slack.com/archives/C01CFNGFX1Q) 主要原因是GT的operation的log里的task id是int类型，所以想取jarvis任务id的后半部分 0_40_XXXXX

![](https://ca.slack-edge.com/EPTPF553J-U02T9457D16-601650c724ad-48)

Chao An![:表示发言的气泡:](https://a.slack-edge.com/production-standard-emoji-assets/14.0/apple-large/1f4ac.png)  [3 天前](https://grab.slack.com/archives/C048HBNDLUT/p1703497231934879?thread_ts=1703495222.253719&cid=C048HBNDLUT)  

好，那我就带上 XXXXXX 这个 id 信息就![[Pasted image 20231228105717.png]]
1. POI man的AHT计算，提供一个计时器，可暂停，清零，半自动化计算AHT，背景可参考, task id计算可用时间戳base32或者64生成uuid [https://docs.google.com/presentation/d/1FGTk2x7pvAnMJv-RwkgiKbx4Wy8f_qwmkslxWGpK9qI/edit#slide=id.g29fac86d414_0_0](https://docs.google.com/presentation/d/1FGTk2x7pvAnMJv-RwkgiKbx4Wy8f_qwmkslxWGpK9qI/edit#slide=id.g29fac86d414_0_0)



1764----


KARTAPLACE-1673