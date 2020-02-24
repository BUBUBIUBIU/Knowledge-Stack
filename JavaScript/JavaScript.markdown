## Type coercion
### == & ===
### < > <= >=
Except +, all strings will be coerced to number.
## How JS work behind tha scenes
Once a function is called, an execution context is created. Execution context has 3 things.  
### Variable Object  
Arguments, Variables, functions  
### Scope chain
Scope chain of a function points to a stack including itself and its parent function (the global one is process or document)
#### Closure
闭包就是能访问另一个函数作用域中变量的函数。Scope chain is destroyed, but not VO.  
Features: data privacy, avoid mess data, cost memory.  
Example: The third argument of setTimeout method. Time count function. Debounce. Throttle.
### 'this' variable
In general function, 'this' variable points to global object.  
'this' variable in arrow function points to parent function.
### Callback function (anonymous function)
## DOM & DOM operation
.getElementById() .querySelector(class name) .querySelectorAll() getElementsByTagName()  
.addEventListener('action', func) .removeEventListener()  
.innerHTML .classList.add .insertAdjacentHTML e.target.closest .getAttribute 
### 缩小DOM object抓取的范围
一般我们会用document来调用抓取element的方法，这其实是在全局抓取。但是我们可以以其他object来缩小抓取的范围。
比如你可以get到一个DOM element并把它赋值给一个变量，然后你就拿它当成handler来get它的子DOM元素。
### 捕获/冒泡
First catch then bubble. When event arrive at target, order of code decides.
### Event delegate
Bind event to parent of target element, so that the number of event registration reduces, save memory.
And we can add event to child element dynamically. 
### currentTarget vs target
currentTarget points the listener, target points the actual touched element.
### Event level
DOM0: onClick
DOM2: addEventListener
DOM3: customized event
### DOM vs Virtual DOM
The element of DOM is huge and operation for it consumes much. So we use JS to simulate DOM.
For example, a DOM element can be represented by JS object including name, tag, key.
### Diff Algorithm
Comparison of two DOM tree (new virtual DOM tree and old one).
Record difference between nodes. 
### 几种操作
抓取input field里的值，清空input field里的值
## Class
### Prototype & Inheritance
Example. Class A is inherited from class B. Then, A.proto === B.prototype.  
Methods and properties in prototype can be shared by instances. 
## Promise
catch then Promise.all() Promise.race Promise.resolve() Promise.reject()

## Async/Await
Async function always automatically returns a promise, then the promise will automatically be resolved with returned value.

If there is no any await in async function, it executes at once then returns a promise object. Actually,
async function executes at once after it is called.

We can first define async function. It does not execute at once like instantiation of Promise.
It needs calling to execute.

The result Await returns is different with Promise or then method. It can return both values and promise.
If result is promise, The return value on left side of equal sign is the arguments of resolve method.

When will the async function get stuck? If there is an await expression, it will stop and wait for resolve.
The code after this await expression will be put into micro-task queue.
## JS运行机制/宏任务与微任务/
### 宏任务
setTimeout, setInterval, 由事件触发的函数
### 微任务
process.nextTick, then
## JS的内存管理与回收机制
内存生命周期：分配，读写，释放。  
根对象： 全局对象，局部对象，DOM对象。根对象是活对象。  
活对象： 一个对象为活对象当且仅当它被一个根对象或另一个活对象指向（引用）。  
### 引用计数垃圾收集
看有没有其他对象引用到它。如果0引用，将被GC回收。
#### 问题：循环引用
解决方法，显示地将指针设为null。
### 标记-清除法
从根对象出发，找到所有从根开始引用的对象，然后再找这些对象引用的对象。
从根开始，垃圾回收器将找到所有可以获得的对象和收集所有不能获得的对象。
#### 循环引用不再是问题
0引用对象总是不可获得的，这句话反过来不一定对。对于循环引用，函数调用返回后，两个对象从全局对象（根对象）出发无法获取，因此他们会被GC回收。