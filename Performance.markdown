### Less to make HTTP request
### Less code or compress code
Applying webpack or other tool to compress
### Less image/Compress image/Responsive image technique
Compress image: 减小图片解析度和质量  
Responsive image technique: 'picture' tag; pixel density, viewpoint；art direction, resolution switching, 
### shouldComponentUpdate in React
没必要render别render
### Lazy loading
Some components will be downloaded and rendered only when we need. We probably
need router module to load component code.
### Throttle&Debounce (防抖&节流)
连续照片列子，电梯例子
#### Throttle
指定时间间隔内只会执行一次任务。  
例子：当我们需要知道scroll bar是否移动到底部时，我们一般都会在scroll事件被触发后无时无刻地监听
和判断是否滑动到了底部。这种做法很耗效能。我们可以使用closure来做一个计时function，使用setTimeout
来隔一段判断我们是否滑到了底部。
#### Debounce
在任务频繁触发的情况下，只有任务触发的间隔超过指定间隔，任务才会执行  
例子：输入栏，向服务器请求判断用户名是否已被占用，一般我们不会在用户持续输入的时候向服务器发送request，
这样操作对服务器压力很大，用户体验也不佳。较好的做法是当用户输入字符后一段时间内不再有字符输入，那我们就
向服务器请求判断用户名是否被占用。  
同样也要用到closure。closure里存的是前一个setTimeout的handler。如果新触发一次事件的话，记得要把前一次的
setTimeout清理掉。汉堡project也有用到防抖。
### Browser cache/CDN
对静态资源极其有效。详细内容在browser file里。
### HTTP/CDN/浏览器缓存
### webpack
How to improve front-end performance via webpack? The key point is output of webpack which
running in the browser.
#### 1 Compress JS code, remove redundant code (comments)
Compression of JS by plugins like UglifyJsPlugin or of CSS by CSSnano.
#### 2 CDN
#### 3 Tree shaking
删除死代码？
#### 4 提取公共代码
 

