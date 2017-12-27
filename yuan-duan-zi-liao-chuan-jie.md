# 远端资料串接

需由后端工程师写好对接的 API ，订出呼叫的规则，才能由前端呼叫。

## 引入 Ajax 模组
---

在目标 JS 内引入 Ajax API 模组
> import * as share from './share.es6';

### 使用方法

```
   let tempvals = Array(page, dutyid);
   let result; // 结果
   let tempitem = share.ajaxarr("dutynews", tempvals, "/ajax");
   // "dutynews" -> API 名称
   // tempvals -> 资料参数阵列
   // "/ajax" 固定名称，

   tempitem.success(function(data) {
       if (data[0] == "ERR") {
           result = "ERR";
       } else {
           result = "SUCCESS";
           // 成功读取完成时，执行
       }
   });

   tempitem.error(function(xhr, ajaxOptions, thrownError) {});

   tempitem.complete(function() {
       if (result == "SUCCESS") {
          // 完成读取完成时，执行
       }
   });
```
说明：
- API 名称对照请参阅 [Star API](/file/star-api-setting.xlsx)

