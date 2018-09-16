规范阅读 
[CORS](https://www.w3.org/TR/cors/)
Response Header
1. Access-Controll-Allow-Origin 
2. Access-Controll-Allow-Credentials
3. Access-Controll-Expose-Headers 
4. Access-Controll-Max-Age 
5. Access-Controll-Allow-Methods 
6. Access-Controll-Allow-Headers

Request Header
1. Origin
2. Access-Controll-Request-Method
3. Access-Controll-Request-Headers 

When the cross-origin request algorithm is invoked, these steps must be followed:
1. If for some reason the user agent does not want to make the request terminate this algorithm and set the cross-origin request status to network error.
2. If the following conditions are true, follow the simple cross-origin request algorithm:
    + The request method is a simple method and the force preflight flag is unset.
    + Each of the author request headers is a simple header or author request headers is empty.
3. Otherwise, follow the cross-origin request with preflight algorithm. 
Note:Cross-origin requests using a method that is simple with author request headers that are not simple will have a preflight request to ensure that the resource can handle those headers. (Similarly to requests using a method that is not a simple method.)

## Simple Cross-Origin Request
Apply the make a request steps and observe the request rules below while making the request.

+ If the manual redirect flag is unset and the response has an HTTP status code of 301, 302, 303, 307, or 308
    + Apply the `redirect steps`.

+ If the end user cancels the request
    + Apply the `abort steps`.

+ If there is a network error
    + In case of DNS errors, TLS negotiation failure, or other type of network errors, apply the `network error steps`. Do not request any kind of end user interaction.

    Note: This does not include HTTP responses that indicate some type of error, such as HTTP status code 410.

+ Otherwise
    + Perform a `resource sharing check`. If it returns fail, apply the `network error steps`. Otherwise, if it returns pass, terminate this algorithm and set the `cross-origin request status` to success. Do not actually terminate the request.

## Cross-Origin Request with Preflight 

# HTTP 
Tim Berners-Lee(1989-1991)

WWW(World Wide Web)
建立在TCP和IP协议基础之上,主要由四个部分组成：
+ HTML 
+ HTTP 
+ 网络浏览器 
+ httpd 

## HTTP/0.9 单行协议 
请求由单行指令构成，以唯一可用方法GET开头，其后跟目标资源的路径
响应：只包含响应文档本身，没有HTTP头信息，也没有状态码和错误代码 

## HTTP/1.0 可扩展性 
+ 协议版本信息现在会随着每个请求发送 
+ 状态码会在响应开始时发送，使浏览器能了解请求执行成功或失败，并相应调整行为 
+ 引入了HTTP头的概念，无论是对于请求还是响应，允许传输元数据，使协议变得非常灵活，更具扩展性。
+ 在新HTTP头的帮助下，具备了传输除纯文本HTML文件以外其他类型文档的能力(Content-Type)

## HTTP/1.1 
安全传输 SSL -> TLS
复杂应用 WebDAV、REST
Server-sent envents
WebSocket
安全模型 CORS、CSP

## HTTP/2
SPDY
HTTP2是二进制协议而不是文本协议
复用协议 并行的请求能在同一个链接中处理，移除了HTTP/1.x中顺序和阻塞的约束。
压缩了headers
允许服务器在客户端缓存中填充数据 

HTTP请求
## 起始行 
+ HTTP方法 
+ 请求目标 URL 
+ HTTP版本

## Headers (不区分大小写)
+ Gerneral headers
+ Request headers
+ Entity headers

## Body
+ Single-resource bodies Content-Type和Content-Length 
+ Multple-resource bodies HTML Forms

HTTP响应
# 状态行
+ 协议版本
+ 状态码
+ 状态行文本 
# Headers 
+ Gerneral headers
+ Response headers
+ Entity headers
# Body
+ Single-resource bodies Content-Type和Content-Length 
+ Single-resource bodies Transfer-Encoding
+ Multple-resource bodies HTML Forms

HTTP/2 帧





