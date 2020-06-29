## 一次完整的网络请求过程
### 域名解析
4、5步左右。浏览器自身缓存。操作系统自身DNS缓存。本地DNS服务器。
如果本地DNS服务器不行，他会往更上级发送请求，直到13台根服务器（一步一步递归地解析.au, .com）。
### TCP三次握手(建立连接)
### 建立TCP连接后发送HTTP请求
### 服务器响应HTTP请求并返回HTML代码
### 浏览器解析HTML，同时请求代码中的资源（js，CSS，图片）
浏览器拿到html文件后，开始解析其中的代码。当遇到js，CSS，image等静态资源时，向服务器发起一个HTTP请求。
### 浏览器对页面进行渲染并呈现给用户
### TCP四次挥手（断开连接）
## TCP三次握手
Client: ACK(确认标志)=0, SYN(同步标志)=1, seq=x (x is random);
Server: ACK=1, SYN=1, seq=y, ack = x+1 (y is random);
Client: ACK=1, seq=x+1, ack=y+1;
### 为什么三次
Client发送的ACK=0, SYN=1延迟抵达。如果是两次握手的话，Server端会与Client端建立连接，但是却收不到信息，空耗资源。
### TCP四次挥手
Client: FIN=1, seq=u (random)
Server: ACK=1, seq=v, ack=u+1 (v random)  
Server: FIN=1, ACK=1, seq=w, ack=u+1
Client: ACK=1, seq=u+1, ack=w+1
### 为什么需要4次挥手
当server收到client的FIN报文时，可能有数据没有传输完成，所以只能先回复一个ACK报文，表示我收到了。等到所有信息都传完之后，
再发送FIN报文。
### TIME-WAIT = 2MSL
time-wait是client在发送完最后一个确认报文的等待时间。等这么久有两个原因。一是怕server没收到自己发的最后一条信息，
导致server再次发送一次第三条信息，而自己关闭连接了又接不到。二是确保本次对话（连接）中的所有报文都已经送达，或从网络中消失，
使下一个对话不会出现上一个会话的报文。
## HTTP
IP主要解决网络路由和寻址问题；TCP主要解决如何在IP层上安全稳定地传递数据包，并保障顺序；HTTP是基于前两者的一种无状态的协议
（比如你当前打开的某个服务器的网页和你之前打开这个服务器上的网页没有任何联系）。
### Restful vs SOAP (Simple object access protocol)
SOAP专注于某些应用逻辑；如果说某些服务（银行转账）需要ACID事物的话，你就得用SOAP了。Restful则面向数据，且无状态。
### HTTP报文格式
#### 请求行
请求方法:GET，PUT，DELETE; URL:协议+主机+路径+参数; 版本协议
##### 请求方法
- 安全性。GET，HEAD方法仅仅query资源而不执行动作，所以这些方法是安全的。
- 幂等性（Idempotent）。执行N次操作A同执行1次操作A的效果是一样的。说明该方法具有等幂性。如PUT，DELETE。而OPTIONS不具有副作用，故具有内在
等幂性。
- Post vs Get: Get的参数在url里，而Post则是在消息体内；Get只能提交1024 bytes，Post可以2M；Get方法存在安全问题，因为它请求的数据会被浏览器
保存下来，攻击者可以从历史记录读取这些数据；Post必须设置content-Type为application。
#### Options
This method is to:
- get what methods such as GET POST are supported by a specific web site.
- For preflight in not simple CORS 
#### 状态行
状态码（200，301，302，304，404）；版本协议；状态信息
#### 请求头/响应头(消息报头)
键值对形式.  
Connection: keep-alive.  
Strict-Transport-Security  
Expires/Cache-Control（强缓存）  
If-Modified-Since/Last-Modified，If-None-Match/Etag  
origin, Access-Control-Allow-Origin
#### 空行
It tells server the request head ends here.
#### 请求体/响应体
三种请求体；响应体一种(HTTP文件)
### client怎么确定自己发送的消息被server收到
HTTP里，有请求就有响应，根据响应的状态码就能知道。
### HTTP 2.0
- 多路复用:
- header压缩: 一般header信息多且冗余。HTTP2使用encoder来减少需要传输的header大小。
### HTTP 1.1
- Etag/If-None-Match
#### HTTP的长连接短连接
- HTTP属于应用层协议。其长连接短连接本质上是TCP的长短连接。
- 短连接: 在HTTP1.0中，默认使用的是短连接。也就是说，浏览器和服务器每进行一次HTTP操作，就建立一次连接，完成操作后就中断。
比如，浏览器访问的HTML文件中包含如JS，图片或CSS文件时，每遇到这样一个web资源，就要建立一个HTTP会话。
- 长连接: 自HTTP1.1起，默认使用长连接。响应头的某个header里是这样：Connection: keep-alive.当一个网页打开完成后，TCP连接不会关闭。
长连接节省建立连接的资源。降低拥塞控制（支持多次请求）。
#### 服务器保活功能
## HTTPS
- 端口：HTTP 80, HTTPS 443。
- HTTP传输明文信息。
### HTTPS更注重安全。它使用对称加密算法保护客户端与服务器之间的通信。
使用随机数。
### 协商对称加密的过程使用非对称加密加密。
RSA等。
### 为了避免中间人攻击，客户端与服务器间不直接使用服务器的公钥，而是使用第三方机构发布的数字证书来获取服务器的公钥。
第三方机构用自己的私钥加密服务器的公钥，然后发送给我们（我们有第三方的公钥）。中间人无法使用自己的私钥来加密证书。
### 为了保证获得的证书是服务器而不是中间人的，我们还需要验证数字签名。
- 数字签名（数字编号），解决证书被调包（篡改）的问题，即证书内容与所对应的服务器公钥不匹配。证书编号会用第三方机构的私钥加密。
- 当第三方确认证书信息等于用公钥解密过的证书编号时，才能确认这个证书属于服务器而不是中间人（这个验证的第三方一般都在本地）。  
- 整个流程是：客户端向服务器发送证书请求。收到相应的证书后和第三方机构确认证书真伪。如果是真的则开始使用公钥。
### SSL/TSL运行机制
- 基本思路是公钥加密法
- 握手阶段，4次发送，3个随机数
### Convention of HTTP to HTTPS
#### First, application of certificate
I have to make a CSR (certificate signing request) file, which includes my personal information, address.
It is for proving the SSL certificate is for a specific guy. Then I submit CRS to certificate provider.
#### Second, install the certificate
After I get certificate, I put it in folder /etc/ssl/ (for Linux). Then I config it according to server.
#### Third, modify links
Convert all HTTP links to HTTPS links.
#### Fourth, 301 redirection
Apply 301 redirection to make HTTP request to HTTPS (about Nginx configuration).
##### Processes of 301 redirection
client sends http requests to server. Then server replies a response with 301 redirection. Next, client parse new URL,
make a new connection. 
#### HSTS (HTTP Strict Transport Security)
When a user visits a web site. Usually, he does not input 'https://' in the address field but click some links and enter HTTPS from
HTTP via 301 redirection. With in this case, attacker can intercept and alter the request. Another case is that attacker can give
user a dummy certificate, pretend to be server.  
HSTS can force browser only send HTTPS request and prevent user to accept dummy certificate.
HSTS needs a compulsory declaration in response header: Strict-Transport-Security: max-age=31536000; includeSubDomains.
### RSA
## TCP vs UDP
一般我们在说网络编程时指的是TCP编程；两者皆是传输层中的协议。
### Difference
- 有连接（字节流）与无连接（数据报）
- TCP是点对点通信，UDP可以一对多，多对一，多对多通信
- TCP要求资源多，UDP少
- TCP较稳定，UDP可能丢包
- TCP保证数据顺序，UDP不保证
### 面向报文 vs 面向字节流
### UDP应用场景
面对大量clients；对数据安全无特殊性要求；网络负担重，但对响应速度要求高。
### TCP应用场景
需要建立安全，稳定，准确的连接。
## Cross origin
### Same-origin policy
domain name, protocol, port
#### Why we need Same-origin policy
CSRF; DOM查询 iframe, 域名相似
### CORS (Cross origin resource sharing)
- Compared with JSONP, CORS supports HTTP requests, but JSONP only GET.
- Once browser find that a JS file send a request cross origin, it will add some headers such as origin. 
- Much work is done in backend
#### Simple request
- 3 HTTP method, limited request header.
- 当前浏览器的域名带着自己的名字去访问另一个server。这个名字放在HTTP request header的origin property里。  
- If server B allow the request, B will return a HTTP response with 'Access-Control-Allow-Origin' header.
- * in 'Access-Control-Allow-Origin' means server B can accept requests from any domain.
- 'Access-Control-Allow-Credentials' depends whether browser can send Cookie to server B. Default is false.
- Host property means server B. Origin property means server A.
#### Not so simple request
- Browser will send a OPTIONS request beforehand. 'Access-Control-Request-Method' declare what method applied.
- Server B will check the 'origin', 'Access-Control-Request-Method' and 'Access-Control-Request-Headers' property in preflight (if success return 200).
- After server A passed preflight, it can send request with only 'origin' property and server B only return 'Access-Control-Allow-Origin'.
## MAC
- 机器之间是通过都是通过网卡进行传输数据的，计算机之间的连接就相当于网卡之间的连接
- 网卡上的地址是独一无二的，用来标识自己全球唯一的身份
- 48位
## 内网访问外网&外网访问内网
### 内到外
找一台和内网服务器在同一级路由下的连通外网的机器，设置这台机器（如Linux中的/etc/environment的proxy），让这台机器的http和https都走一遍特定的端口。
### 原理：端口映射
子网转换
