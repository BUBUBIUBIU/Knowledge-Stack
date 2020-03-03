### Browser
#### prerequisite
##### Thread vs Process
A process can have many threads. Different threads of the same process share resource (memory, CPU). Process is the smallest
unit CPU allocate resource for (CPU分配资源的最小单位, 能拥有和独立运行资源的最小单位）。Thread is the smallest unit that OS schedule CPU for. (线程是CPU调度的最小单位, 线程是建立在进程基础上的一次程序运行单位)
#### About browser
Browser has multiple processes. And OS allocate resource (CPU, memory) to it. There are some core processes.
#### Browser process (main process)
It is responsible for create or end a process. Moreover, manage network resource, download (网络资源管理，下载等)。
#### Plugin process
Browser create a process for each plugins (每种插件对于一个进程)。
#### GPU process
It is responsible for 3D paint/render.
#### 浏览器内核/浏览器渲染进程/renderer process
This is the most frequent process developer interacts with. It is responsible for rendering page, JS execution, event loop.
It is a multi thread process. There are some core thread.
##### GUI rendering thread
It renders browser UI, parses HTML, CSS. Then builds DOM tree. 布局和绘制。回流？该线程和JS引擎线程是互斥的。当JS引擎线程执行时，GUI线程
会被挂起。GUI更新会被保存在一个队列中等到JS引擎空闲时被立即执行。
##### JS engine thread (JS引擎线程)
负责解析和运行JS代码。其一直等待着任务队列中的任务到来，然后加以处理。一个Tab页（render进程）中无论什么时候都只有一个JS线程在运行JS程序。由于JS引擎线程
和GUI渲染线程是互斥的，如果JS执行时间过长，会导致页面渲染不连贯甚至阻塞。
##### 事件触发线程 & 定时触发器线程 & 异步HTTP请求线程
#### 浏览器多进程优势
避免单个page crash影响整个浏览器；避免第三方插件crash影响浏览器；多进程充分利用多核优势，提高效能；方便使用沙河模型隔离插件等进程，提高稳定性。
#### Browser进程和浏览器内核之间的通信
Browser进程收到用户请求，首先需要获取页面内容（比如通过网络下载资源），随后通过 RendererHost 接口传递给 Renderer process. Render进程的render
接口接收到消息，简单处理后，交给渲染线程。渲染线程（GUI rendering thread）在加载和渲染网页时，可能会需要Browser进程获取资源或GPU线程来帮助渲染。
中途可能会有JS线程操作DOM，造成回流？和重绘。最后renderer进程将结果发送给browser进程，browser进程接收到结果并将结果绘制出来。
### Browser cache
- For browser cache, we avoid causing cache when we develop app. But after we released web app, we have to think how to
manage it, so that accelerate accessing speed.  
- When browser is loading data, it will check the header of request(data). If 该资源命中强缓存，则不会发送请求到服务器。For example,
when browser is parsing HTML file and it needs CSS of it, if browser can get CSS file from cache, it will not send request to server.  
- When 强缓存没有起作用时，browser sends a request to server. Server will check the HTTP header of requested data. If 命中协商缓存，服务器会
返回一个响应. But not the data. It tells browser can load these data from cache.  
- When 协商缓存也没有命中时，浏览器直接从服务器download数据。协商缓存应配合着强缓存使用，如果不启用强缓存的话，协商缓存没有意义。  
- Above is browser default behaviors. It could be changed by ctrl + f5强制刷新页面，直接从服务器加载。或者f5刷新网页时，会跳过强缓存，但是
检查协商缓存。
#### 强缓存
- Expires, 存在于http response header里。表示资源在客户端缓存的有效期。Expires caches absolute time. Browser will caches the whole
data including header. When browser request this data, it will go to cache and compare the times of each other. If 没有命中
强缓存, when browser is loading data, the header of Expires will be updated.  
- Cache-Control. 服务器与客户端时间不一致带来的问题，Cache-control 存的是相对时间。客户端拿第一次请求的时间加上Cache-Control的值，再与当前时间
做对比来判断资源是否过期。同理没有命中重新download资源时，Cache-Control会被更新。Cache-Control的优先级高于Expires。
##### 怎么启用强缓存
用代码的话两种方式；用应用的话tomcat，Nginx可配置
##### 不想启用强缓存怎么办
When I am developing app, browser will cache image, CSS and JS file default. 在开发环境下会因为强缓存导致资源没有及时更新而看不到最新效果，
有多种方法解决这个问题，如ctrl + f5等。Or we can set Cache-control: no-store;
##### 什么时候适合使用强缓存
强缓存一般适用于静态资源。比如为静态资源配置超长的Expires或Cache-Control。这样用户访问页面时，只会在第一次访问时download资源。但是这样又带来一个新的问题。
For example, when you already cached a image, but web site has changed it, so you miss the latest version. 但是这个问题已有解决方法（不在此
详述）。强缓存对于动态资源需慎用。比如说服务端页面 以及 引用静态资源的html code。一旦他们被强缓存，可能user cannot see the latest result.
#### 协商缓存
- 当强缓存没有命中时，browser will send a request to server to check 协商缓存是否命中。如果协商缓存命中，response status will be 304
and Not modified.  
- Last-Modified, If-Modified-Since: When browser first requests data, server will add a response header, Last-Modified.
This header means the last time when data was updated. When browser request that data again, it will add if-Modified-Since
to header. 这个 if-Modified-Since 上的时间就是缓存里 Last-Modified 的时间。服务器会判断这个时间有没有过期，没有的话则返回304 Not Modified,
有的话则正常返回资源内容。如果协商缓存没有命中，Last-Modified Header在加载资源时也会被更新，下次请求时，If-modified-Since会启用上次返回的Last-Modified。  
- Etag, If-None-Match: 有时候会出现服务器上资源有变化，但是最后修改时间却没有变化的情况。At this time, we need Etag and If-None-Match. 
同样也是第一次返回资源时，response header里有Etag header。这个东西是服务端生成的唯一资源标识符。浏览器再次想服务器请求该资源时，会把这个Etag放在
If-None-Match的request header里，如果服务器端检查到match的话，就会回一个304 + Etag，即使这个Etag和之前的Etag一样（这点与Last-Modified不同）。
否则则返回一个所需资源 + 新的Etag。
##### 什么时候使用协商缓存
大部分应用都会使用协商缓存。分布式系统不适合用Etag，因为每台机器生成的Etag不一样。
### CDN(content distributed network)
一般开发人员口中的缓存指的是两个东西，一是浏览器里的缓存，二是CDN里的缓存。  
CDN是用户和服务器之间的一个cache层。主要动作为推送（由源服务器）和拉取（由浏览器发送要求）
