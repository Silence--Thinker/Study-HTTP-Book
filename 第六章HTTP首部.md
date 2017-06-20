# 6 HTTP首部

`HTTP`协议的请求和响应报文中必定包含`HTTP首部`，只是我们平时在使用`Web`的过程中感受不到它。本章我们一起来学习`HTTP首部`的结构，以及首部中各字段的用法。

## 6.1 HTTP 报文首部

<center>
![](./Screenshot/WX20170616-101039@2x.png)
</center>

**HTTP请求报文**

<center>
![](./Screenshot/WX20170616-093459@2x.png)
</center>

**HTTP响应报文**

<center>
![](./Screenshot/WX20170616-093739@2x.png)
</center>

## 6.2 HTTP 首部字段

### 6.2.1 HTTP 首部字段传递重要信息

使用首部字段是为了给浏览器和服务器提供`报文主体大小`、所使用的`语言`、`认证信息`等内容。

### 6.2.2 HTTP 首部字段结构

`HTTP`首部字段是由`首部字段名`和`字段值`构成的，中间用冒号`:`分隔。

### 6.2.3 4种 HTTP 首部字段类型

`HTTP`首部字段根据实际用途被分为以下四种类型。

**通用首部字段**（`General Header Fields`）

请求报文和响应报文两方都会使用的首部。

**请求首部字段**（`Request Header Fields`）

从客户端向服务器端发送请求报文时使用的首部。补充了请求的附加内容、客户端信息、响应内容相关优先级等信息。

**响应首部字段**（`Response Header Fields`）

从服务器端向客户端返回响应报文时使用的首部。补充了响应的附加内容，也会要求客户端附加额外的内容信息。

**实体首部字段**（`Entity Header Fields`）

针对请求报文和响应报文的实体部分使用的首部。补充了资源内容更新时间等与实体有关的信息。

### 6.2.4 HTTP/1.1 首部字段一览

`Http/1.1`规范定义了如下47中首部字段。

**通用首部字段**

|首部字段名				|说明|
|:--					|:--			|
| Cache-Control		|控制缓存的行为	|
| Connection			|逐跳首部、连接的管理 |
| Date					|报文指令 |
| Pragma				|控制缓存的行为	|
| Trailer				|报文末端的首部一览	|
| Transfer-Encoding	|指定报文主体的传输编码方式 |
| Upgrade				|升级为其他协议	|
| Via					|代理服务器的相关信息	|
| Warning				|错误通知	|

**请求首部字段**

|首部字段名			|说明 |
|:--				|:-- |
| Accept			|用户代理可处理的媒体类型	|
| Accept-Charset	|优先的字符集 |
| Accept-Encoding	|优先的内容编码 |
| Accept-Language	| 优先的语言（自然语言）|
| Authorization	|Web认证信息 |
| Expect			|期待服务器的特定行为 |
| From				|用户的电子邮箱地址	|
| Host				|请求资源所在服务器	|
| If-Match		|比较实体标记（ETag) |
| If-Modified-Since	|比较资源的更新时间 |
| If-None-Match	|比较实体标记（与If-Match相反）|
| If-Range	|资源未更新时发送实体Byte的范围请求 |
| If-Unmodified-Since 	|比较资源的更新时间（与If-Modified-Since相反） |
| Max-Forwards	|最大传输逐跳数	|
| Proxy-Authorization	|代理服务器要求客户端的认证信息 |
| Range			|实体的字节范围请求	|
| Referer			|对请求中URI的原始获取方 |
| TE				|传输编码的优先级 |
| User-Agent		|HTTP客户端程序的信息 |

**响应首部字段**

|首部字段名			|说明 |
|:--				|:-- |
| Accept-Ranges	|是否接受字节范围请求	|
| Age				|推算资源创建经过时间	|
| ETag				|资源的匹配信息	|
| Location		|令客户端重定向至指定URI	|
| Proxy-Authenticate	|代理服务器对客户端的认证信息 |
| Retry-After		|对再次发起请求的时机要求 |
| Server			|HTTP服务器的安装信息	|
| Vary				|代理服务器缓存的管理信息	|
| WWW-Authenticate		|服务器对客户端的认证信息 |

**实体首部字段**

|首部字段名				|说明 |
|:--					|:-- |
| Allow				|资源可支持的HTTP方法	|
| Content-Encoding	|实体主体适用的编码方式 |
| Content-Language	|实体主体的自然语言	|
| Content-Length		|实体主体的大小（单位：字节）|
| Content-Location	|替代对应资源的URI	|
| Content-MD5			|实体主体的报文摘要	|
| Content-Range		|实体主体的位置范围	|
| Content-Type		|实体主体的媒体类型	|
| Expires				|实体主体过期的日期时间	|
| Last-Modified		|资源的最后修改日期时间	|

### 6.2.5 非HTTP/1.1 首部字段
### 6.2.6 End-to-end 首部和 Hop-by-hop 首部

端到端首部（**End-to-end Header**）

逐跳首部（**Hop-by-hop Header**）

下面列举了`HTTP/1.1`中的**逐跳首部**字段。除这8个首部字段之外，其他所有字段都属于**端到端首部**。

* **Connection**
* **Keep-Alive**
* **Proxy-Authenticate**
* **Proxy-Authorization**
* **Trailer**
* **TE**
* **Transfer-Enconding**
* **Upgrade**

## 6.3 HTTP/1.1 通用首部字段

通用首部字段是指，请求报文和响应报文双方都会使用的首部。

### 6.3.1 Cache-Control

通过指定首部字段`Cache-Control`的指令，就能操作缓存的工作机制.

### 6.3.2 Connection

`Connection`首部字段具备两个作用。

* 控制不在转发给代理的首部字段
* 管理持久连接

**控制不在转发给代理的首部字段**

在客户端发送请求和服务器返回响应内，使用`Connection`首部字段，可控制不再转发给代理的首部字段（即`HoP-by-hoP`首部）。

> connection: 不再转发的首部字段名

**管理持久连接**

`HTTP/1.1`版本的默认连接都是持久连接。为此，客户端会在持久连接上连续发送请求。当服务器端想明确断开连接时，则指定`Connection`首部字段的值为`Close`。

> connection: Keep-Alive

`HTTP/1.1`之前的HTTP版本的默认连接都是非持久连接。为此，如果想在旧版本的HTTP协议上维持持续连接，则需要指定`Connection`首部字段的值为`Keep-Alive`。

### 6.3.3 Date

首部字段`Date`表明创建`HTTP`报文的日期和时间。

`HTTP/1.1`协议使用在`RFC1123`中规定的日期时间的格式，如下示例。

> Date: Tue, 03 Dul 2012 04:40:59 GMT

之前的`HTTP`协议版本中使用在`RFC850`中定义的格式，如下所示。

> Date: Tue, 03-Dul-12 04:40:59 GMT

除此之外，还有一种格式。它与`C标准库`内的`asctime()`函数的输出格式一致。

> Date: Tug Dul 03 04:40:59 2012

### 6.3.4 Pragma

`Pragma`是`HTTP/1.1`之前版本的历史遗留字段，仅作为与`HTTP/1.0`的向后兼容而定义。

所有的中间服务器如果都能以`HTTP/1.1`为基准，那直接采用`Cache-Control:no-cache`指定缓存的处理方式是最理想的。但要整体掌握全部中间服务器使用的`HTTP`协议版本缺失不现实的。因此，发送的请求会同时含有下面两个首部字段。

> Cache-Control: no-cache
> Pragma: no-cache

### 6.3.5 Trailer

首部字段`Trailer`会事先说明在报文主体后记录了哪些首部字段。该首部字段可应用在`HTTP/1.1`版本分块传输编码时。

> HTTP/1.1 200 OK
> 
> Date: Tue, 03 Jul 2012 04:40:56 GMT
> 
> Content-Type: text/html
> 
> Transfer-Encoding: chunked
> 
> Trailer: Expires
> (报文主体）
> 
> 0
> 
> Expires: Tue, 28 Sep 2004 23:59:59 GMT

以上用例中，指定首部字段`Trailer`的值为`Expires`，在报文主体之后(分块长度0之后）出现了首部字`Expires`。

### 6.3.6 Transfer-Encoding

首部字段`Transfer-Encoding`规定了传输报文主体时采用的编码方式。

`HTTP/1.1`的传输编码仅对分块传输编码有效。

### 6.3.7 Upgrade

首部字段`Upgrade`用于检测`HTTP`协议以及其他协议是否可使用更高的版本进行通信，其参数值可以用来指定一个完全不同的通信协议。

### 6.3.8 Via

使用首部字段`Via`是为了追踪客户端与服务器之间的请求和响应报文的传输路径。

报文经过代理或网关时，会先在首部字段`Via`中附加该服务器的信息，然后再进行转发。

<center>
![](./Screenshot/QQ20170619-153406@2x.png)
</center>

### 6.3.9 Warning

`HTTP/1.1`的`Warning`首部是从`HTTP/1.0`的响应首部（`Retry-After`）演变过来的。该首部通常会告知用户一些与缓存相关的问题的警告。

> Warning: 113 gw.hackr.jp:8080 "Heuristic expiration" Tue, 03

Warning首部的格式如下。最后的日期时间部分可省略

> Warning:[警告码][警告的主机:端口号]“[警告内容]”（[日期时间])

|警告码	|警告内容							|说明 |
|:--	|:-- 								|:-- |
| 110	|Response is stale (响应已过期）|代理返回己过期的资源 |
| 111	|Revalidation failed (再验证失败））|代理再验证资源有效性时失败（服务器无法到达等原因） |
| 112	|Disconnection operation (断开连接操作）|代理与互联网连接被故意切断 |
| 113	|Heuristic expiration (试探性过期）|响应的使用期超过24小时（有效缓存的设定时间大于24小时的情况下） |
| 199	|Miscellaneous warning (杂项警告）|任意的警告内容 |
| 214	|Transformation applied (使用 了转换）|代理对内容编码或媒体类型等执行了某些处理时 |
| 299	|Miscellaneous persistent warning (持久杂项警告| 任意的警告内容 |

## 6.4 请求首部字段

请求首部字段是从客户端往服务器端发送请求报文中所使用的字段，用于补充请求的附加信息、客户端信息、对响应内容相关的优先级等内容。

### 6.4.1 Accept

Accept首部字段可通知服务器，用户代理能够处理的媒体类型及媒体类型的相对优先级。可使用type/subtype这种形式，一次指定多种媒体型。

**文本文件**

text/html, text/plain, text/css ...
application/xhtml+xml, application/xml...

**图片文件**

image/jpeg, image/gif，image/png ...

**视频文件**

video/mpeg, video/quicktime ...

**应用程序使用的二进制文件**

application/octet-stream, application/zip ...

当服务器提供多种内容时，将会首先返回`权重值`（权重值用q表示，默认为1.0，取值0~1，如:q=1.0）最高的媒体类型。

### 6.4.2 Accept-Charset

> Accept-Charset: iso-8859-5, Unicode-1-1;q=0.8

`Accept-Charset`首部字段可用来通知服务器用户代理*支持的字符集及字符集的相对优先顺序*。另外，可一次性指定多种字符集。与首部字Accept相同的是可用权重q值来表示相对优先级。

### 6.4.3 Accept-Encoding

> Accept-Encoding: gzip, deflate

`Accept-Encoding`首部字段用来告知服务器用户代理*支持的内容编码及内容编码的优先级顺序*。可一次性指定多种内容编码。

* gzip
* compress
* deflate
* identity

### 6.4.4 Accept-Language

> Accept - Language: zh-cn., zh;q=0.7^en-us^en;q=0.3

首部字段`Accept-Language`用来告知服务器用户代理能够处理的*自然语言集*（指中文或英文等），以及自然语言集的相对优先级。可一次指定多种自然语言集。

### 6.4.5 Authorization

> Authorization: Basic dWVub3NlbjpwYXNzd29yZA==

首部字段`Authorization`是用来告知服务器，用户代理的认证信息（证书值）。通常，想要通过服务器认证的用户代理会在接收到返回的`401`状态码响应后，把首部字段`Authorization`加入请求中。共用缓存在接收到含有`Authorization`首部字段的请求时的操作处理会略有差异。

### 6.4.6 Expect

> Expect: 100-continue

客户端使用首部字段`Expect`来告知服务器，期望出现的某种特定行为。因服务器无法理解客户端的期望作出回应而发生错误时，会返回状态码 `417 Expectation Failed`。

### 6.4.7 From

首部字段From用来告知服务器使用用户代理的用户的电子邮件地址。通常，其使用目的就是为了显示搜索引擎等用户代理的负责人的电子邮件联系方式。使用代理时，应尽可能包含From首部字段（但可能会因代理不同，将电子邮件地址记录在User-Agent首部字段内）。

### 6.4.8 Host

> Host: www.hackr.jp

首部字段`Host`会告知服务器，请求的资源所处的互联网主机名和端口号。Host首部字段在`HTTP/1.1`规范内是*唯——个必须被包含*在请求内的首部字段。

### 6.4.9 If-Match

> If-Match: "123456"

形如`If-xxx`这种样式的请求首部字段，都可称为`条件请求`。服务器接收到附带条件的请求后，只有判断指定条件为真时，才会执行请求。

首部字段`If-Match`，属附带条件之一，它会告知服务器匹配资源所用的实体标记（`ETag`)值。这时的服务器无法使用`弱ETag`值。（请参照本章有关首部字段ETag的说明）。

服务器会比对`If-Match`的字段值和资源的`ETag`值，仅当两者一致时，才会执行请求。反之，则返回状态码`412 Precondition Failed`的响应。

### 6.4.10 If-Modified-Since

> If-Modified-Since: Thu, 15 Apr 2004 00:00:00 GMT

`If-Modified-Since`用于确认代理或客户端拥有的本地资源的有效性。获取资源的更新日期时间，可通过确认首部字段Last-Modified来确定。

### 6.4.11 If-None-Match

首部字段`If-None-Match`属于附带条件之一。它和首部字段`If-Match`作用相反。用于指定`If-None-Match`字段值的实体标记（`ETag`)值与请求资源的`ETag`不一致时，它就告知服务器处理该请求。

### 6.4.12 If-Range

首部字段`If-Range`属于附带条件之一。它告知服务器若指定的`If-Range` 字段值（`ETag`值或者时间）和请求资源的`ETag`值或时间相一致时，则作为范围请求处理。反之，则返回全体资源。

### 6.4.13 If-Unmodified-Since

> If-Unmodified-Since: Thu, 03 ]ul 2012 00:00:00 GMT

首部字段`If-Unmodified-Since`和首部字段`If-Modified-Since`的作用相反。它的作用的是告知服务器，指定的请求资源只有在字段值内指定的日期时间之后，未发生更新的情况下，才能处理请求。如果在指定日期时间后发生了更新，则以状态码`412 Precondition Failed`作为响应返回。

### 6.4.14 Max-Forwards

> Max-Forwards: 10

通过`TRACE`方法或`OPTIONS`方法，发送包含首部字段`Max-Forwards`的请求时， 该字段以十进制整数形式指定可经过的服务器最大数目。服务器在往下一个服务器转发请求之前，`Max-Forwards`的值减1后重新赋值。当服务器接收到`Max-Forwards`值为0的请求时，则不再进行转发，而是直接返回响应。

### 6.4.15 Proxy-Authorization

> Proxy-Authorization: Basic dGlwOjkpNLAGfFY5

接收到从代理服务器发来的认证质询时，客户端会发送包含首部字段`Proxy-Authorization`的请求，以告知服务器认证所需要的柄息。

### 6.4.16 Range

> Range: bytes=5001-10000

接收到附带`Range`首部字段请求的服务器，会在处理请求之后返回状态码为`206 Partial Content`的响应。无法处理该范围请永时，则会返回状态码200 OK的响应及全部资源。

### 6.4.17 Referer

> Referer: http://www.hackr.jp/index.htm

首部字段`Referer`会告知服务器请求的原始资源的`URI`

### 6.4.18 TE

> TE: gzip, deflate;q=0.5

首部字段`TE`会告知服务器客户端能够处理响应的传输编码方式及相对优先级。它和首部字段`Accept-Encoding`的功能很相像，但是用于传输编码。

### 6.4.19 User-Agent

> User-Agent: Mozilla/5.0 (Windows NT 6.1; W0W64; nv:13.0) Gee

首部字段`User-Agent`会将创建请求的浏览器和`用户代理名称等`信息传达给服务器。

由网络爬虫发起请求时，有可能会在字段内添加爬虫作者的电子邮件地址。此外，如果请求经过代理，那么中间也很可能被添加上代理服务器的名称。

## 6.5 响应首部字段

响应首部字段是由服务器端向客户端返回响应报文中所使用的字段，用于补充响应的附加信息、服务器信息，以及对客户端的附加要求等信息。

### 6.5.1 Accept-Ranges

> Accept-Ranges: bytes

首部字段Accept-Ranges是用来告知客户端服务器是否能处理范围请求，以指定获取服务器端某个部分的资源。

### 6.5.2 Age

> Age: 600

首部字段`Age`能告知客户端，源服务器在多久前创建了响应。字段值的单位为秒。

若创建该响应的服务器是缓存服务器，Age值是指缓存后的响应再次发起认证到认证完成的时间值。代理创建响应时必须加上首部字段`Age`。

### 6.5.3 ETag

> ETag: "34e544327886546ce7676aff67678acd67"

首部字段`ETag`能告知客户端实体标识。它是一种可将资源以字符串形式做*唯一性标识*的方式。服务器会为每份资源分配对应的`ETag`。

**强ETag值和弱Tag值**

强ETag值

强ETag值，不论实体发生多么细微的变化都会改变其值。

> ETag: "usagi-1234"

弱ETag值

弱ETag值只用于提示资源是否相同。只有资源发生了根本改变，产生差异时才会改变ETag值。这时，会在字段值最开始处附加W/。

> ETag: W/"usagi-1234n

### 6.5.4 Location

> Location: http://www.usagidesign.jp/sample.html

使用首部字段`Location`可以将响应接收方引导至某个与请求URI位置不同的资源。

基本上，该字段会配合`3xx: Redirection`的响应，提供重定向的。

### 6.5.5 Proxy-Authenticate

> Proxy-Authenticate: Basic realm = "UsagidesignAuth"

首部字段Proxy-Authenticate会把由代理服务器所要求的认证信息发送给客户端。

### 6.5.6 Retry-After

> Retry-After: 120

首部字段`Retry-After`告知客户端应该在多久之后再次发送请求。主要配合状态码`503 Service Unavailable`响应，或`3xx Redirect`响应一起使用。

### 6.5.7 Server

> Server: Apache/2.2.6 (Unix) PHP/5.2.5

首部字段Server告知客户端当前服务器上安装的HTTP服务器应用程序的信息。不单单会标出服务器上的软件应用名称，还有可能包括版本号和安装时启用的可选项。

### 6.5.8 Vary

> Vary: Accept-Language

首部字段`Vary`可对缓存进行控制。源服务器会向代理服务器传达关于本地缓存使用方法的命令。

### 6.5.9 WWW-Authenticate

> WWW-Authentic ate: Basic realm= "Usagidesign Auth"

首部字段`WWW-Authenticate`用于HTTP访问认证。它会告知客户端适用于访问请求URI所指定资源的认证方案（`Basic`或是`Digest`)和带参数提示的质询（`challenge`)。状态码4`01 Unauthorized`响应中，肯定带有首部字段`WWW-Authenticate`。

## 6.6 实体首部字段

实体首部字段是包含在请求报文和响应报文中的实体部分所使用的首部，用于补充内容的更新时间等与实体相关的信息。

### 6.6.1 Allow

> Allow: GET, HEAD

首部字段`Allow`用于通知客户端能够支持`Request-URI`指定资源的所有HTTP方法。当服务器接收到不支持的HTTP方法时，会以状态码`405 Method Not Allowed`作为响应返回。与此同时，还会把所有能支持的`HTTP`方法写入首部字段`Allow`后返回。

### 6.6.2 Content-Encoding

> Content-Encoding: gzip

首部字段`Content-Encoding`会告知客户端服务器对实体的主体部分选用的内容编码方式。内容编码是指在不丢失实体信息的前提下所进行的压缩。

主要采用以下4种内容编码的方式。

* gzip
* compress
* deflate
* identity

### 6.6.3 Content-Language

> Content-Language: zh-CN

首部字段Content-Language会告知客户端，实体主体使用的自然语言(指中文或英文等语言）。

### 6.6.4 Content-Length

### 6.6.5 Content-Location

