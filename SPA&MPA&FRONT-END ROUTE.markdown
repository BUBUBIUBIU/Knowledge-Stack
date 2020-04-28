## SPA
- Only one HTML file. We apply JS to route page.
## MPA
- Each HTML file represent each web page. For folder structure, HTML and CSS files for same web page are put in same folder.
## Problem of SPA
在页面内容改变时，由于页面本身的URL不变，导致：
- SPA无法记住用户的操作记录，这样就不能前进或后退网站了
- SPA虽然有多种页面展示形式，但是只有一个URL，对SEO不友好
## Solution (front-end route)
- 在改变URL的同时不让浏览器向服务器发送请求
- 浏览器可以监听到URL的变化
### Hash
- Hash is text after '#' sign in URL.
- Change of hash doesn't result in sending request but triggering hash event.
### History
- Initially, history is for forwarding and backing in one tab.
- Three two methods: replaceState (更换栈指针的url地址), pushState (压入栈). 
- Key event: popstate. It will not be triggered by replaceState and pushState.
- Please don't forget to prevent default behavior of browser.
- 但需要注意的是，history 在修改 url 后，虽然页面并不会刷新，但我们在手动刷新，或通过 url 直接进入应用的时候，
  服务端是无法识别这个 url 的。因为我们是单页应用，只有一个 html 文件，服务端在处理其他路径的 url 的时候，就会出现404的情况。
  所以，如果要应用 history 模式，需要在服务端增加一个覆盖所有情况的候选资源：如果 URL 匹配不到任何静态资源，则应该返回单页应用的 html 文件。
### History vs Hash
- History can use any url, but hash can only use the part after #.
- pushState will record all histories, but if the hash values are same, hash cannot record history.
- pushState can use 'state' object which includes some information like scroll position.
## React router
- 本质上是实现URL和UI界面的同步。
- React router is based on history module, a third party of JS. This module is based on hash and history of HTML5.  


 

 



