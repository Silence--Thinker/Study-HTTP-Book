# 1 了解Web及网络基础
## 1.1 使用HTTP协议访问Web
## 1.2 HTTP的诞生
### 1.2.1 为知识共享而规划Web
### 1.2.2 Web成长时代
* 日本第一个主页
* HTML1.0


### 1.2.3 驻足不前的HTTP

**HTTP/0.9**

**HTTP/1.0**

**HTTP/1.1**

## 1.3 网络基础TCP/IP
### 1.3.1 TCP/IP协议族
### 1.3.2 TCP/IP的分层管理
应用层

传输层

网络层

链路层(数据链路层，网络接口层)

### 1.3.3 TCP/IP通信传输流
## 1.4 与HTTP关系密切的协议：IP、TCP和DNS
### 1.4.1 负责传输的IP协议

使用**ARP**协议凭借**MAC**地址进行通信

### 1.4.2 确保可靠的TCP协议

**三次握手**

## 1.5 负责域名解析的DNS服务
## 1.6 各种协议与HTTP协议的关系
## 1.7 URI 和 URL
### 1.7.1 同意资源标示符

`URI`是`Uniform Resource Identifier`的缩写。RFC2396分别对这三个单词进行了如下定义。
**Uniform**

**Resource**

**Identifier**

`URI`就是由某个协议方案表示的资源的定位标示符。协议方案是指访问资源所使用的协议类型名称。

`URI`用字符串标识某一互联网资源，而`URL`表示资源的地点（互联网上所在的位置）。可见`URL`是`URI`的子集。

"RFC3986:统一资源标识符（URI）通用语法”中例举了几种`URI`的例子，如下所示。
> ftp://ftp.is.co.za/rfc/rfc1808.txt
> http://www.ietf.org/rfc/rfc/2396.txt
> ldap://[2001:db8::7]/c=GB?objectClass?one
> mailto:John.Doe@example.com
> news:comp.infosystems.www.servers.unix
> tel:+1-816-555-1212
> telnet://192.0.2.16:80/
> urn:oasis:names:specification:docbook:dtd:xml:4.1.2

### 1.7.2 URI格式
**绝对URI**

协议方案名

登陆信息（认证）

服务器地址

服务端口号

带层次的文件路径

查询字符串

片段标识符
