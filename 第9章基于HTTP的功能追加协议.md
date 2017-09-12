# 9 基于 HTTP 的功能追加协议

## 9.1 基于 HTTP 的协议

## 9.2 消除 HTTP 瓶颈的 SPDY

### 9.2.1 HTTP 的瓶颈

* 一条连接上只可发送一个请求。
* 请求只能从客户端开始。
* 请求/响应首部未经压缩就发送。
* 发送冗长的首部
* 可任意选择数据压缩格式

**Ajax** 的解决方法

**Comet** 的解决方法

**SPDY** 的目标

### 9.2.2 SPDY 的设计与功能

使用`SPDY`后，`HTTP`协议额外获得以下功能。

**多路复用流**

**赋予请求优先级**

**压缩HTTP首部**

**推送功能**

**服务器提示功能**

### 9.2.3 SPDY 消除 Web 瓶颈了吗

## 9.3 使用浏览器进行全双工通信的WebSocket

### 9.3.1 WebSocket 的设计与功能

### 9.3.2 WebSocket 协议

WebSocket 协议的主要特点

**推送功能**

**减少通信量**

* 握手·请求
* 握手·响应
* WebSocket API

## 9.4 期盼已久的 HTTP/2.0

**HTTP/2.0特点**

* SPDY
* HTTP Speed + Mobility （微软）
* Network-Friendly HTTP Upgrade (移动端标准)

## 9.5 Web 服务器管理文件的 WebDAV

### 9.5.1 扩展 HTTP/1.1 的 WebDAV

### 9.5.2 WebDAV 内新增的方法及状态码












