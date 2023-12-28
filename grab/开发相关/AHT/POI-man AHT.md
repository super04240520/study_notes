
poi
1. 后端加了创建以及更新两个[API](https://gitlab.myteksi.net/gophers/go/-/merge_requests/138580/diffs)提供了reference参数，用于统计referType以及referID, 分别是任务类型和task任务id，通过路由参数获取传值，主要用于POI details等项目直接用poi man更新但没task的绑定
2. POI man的AHT计算，提供一个计时器，可暂停，清零，半自动化计算AHT，背景可参考, task id计算可用时间戳base32或者64生成uuid [https://docs.google.com/presentation/d/1FGTk2x7pvAnMJv-RwkgiKbx4Wy8f_qwmkslxWGpK9qI/edit#slide=id.g29fac86d414_0_0](https://docs.google.com/presentation/d/1FGTk2x7pvAnMJv-RwkgiKbx4Wy8f_qwmkslxWGpK9qI/edit#slide=id.g29fac86d414_0_0)