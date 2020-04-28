## SYN (flood) 洪范攻击
Attacker sends a huge number of connection request (ACK=0, SYN=1) to Server. So that server has to allocate resource for
these fake connections.
## SSL Strip (SSL剥离攻击)
Stripping the encryption of HTTPS, so that client and server are using plaintext (especially in the first
time we convert HTTP to HTTPS).
## XSS
Attacker insert some bad scripts into web page. When user look through this web page and browser of user A executes or parses
script of this page. Something bad happens.
### 储存型 XSS
- For a forum, a attacker can submit his code (for example, as some comments) to the board. When common users want to see
comments, their browser will parse the bad script.
### 反射型 XSS
- Tempt user to click a camouflaged link. And server will extra bad code from URL, concat them into HTML. Then, server
return the HTML to user browser.
### DOM型 XXS
- 前两者都是属于服务端型攻击，这个属于前端型攻击。它使user上当的方法和反射型的相同，但是坏事都是由浏览器单独完成的。
### Solutions
- 以预防为主。注意用户return回来的HTML file和url链接。对关键词做各种转义等。
## CSRF (Cross-site request forgery, 跨站请求伪造)
Attacker (A) pretends to be client (C), send request to server B. For example, client C sent a message to server B, and B
return a response with cookie for authentication. Then C open another website A, the JS in C can send a request to B to
do something bad for C with cookie from B.
### Solutions
#### Same-origin policy
#### Solutions for server side
- cookie hashing