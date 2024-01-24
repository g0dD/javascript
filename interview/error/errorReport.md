## 错误上报

#### ajax 进行上报

有严格的跨域限制
上报请求可能会阻塞业务
请求容易丢失（被浏览器强制 cancel）

#### image 上报

get 请求 数据量有限

#### sendBeacon

navigator.sendBeacon() 方法可用于通过 HTTP POST 将少量数据 异步 传输到 Web 服务器。
方法会使用户代理在有机会时异步地向服务器发送数据，同时不会延迟页面的卸载或影响下一导航的载入性能，这意味着：

数据发送是可靠的。
数据异步传输。
不影响下一导航的载入。