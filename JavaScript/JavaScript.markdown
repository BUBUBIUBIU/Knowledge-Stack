## Heap memory vs Stack memory
For stack, we release variables and collect memory after a execution context ends. But for heap, we release it when no
one refers to it.
### Stack
- First in last out. For primitive data type. Since size of primitive type are small and constant, and they are often accessed.
- But for closure, primitive type is stored in heap. 现在的 JS 引擎可以通过逃逸分析辨别出哪些变量需要存储在堆上，哪些需要存储在栈上。
### Heap
- Tree shape. Content of reference data type (Array, Function, Object). It allocates memory dynamically. Since size of reference type are big and floating.
If it is in stack, it will impact performance.
- There is a pointer in stack for reference type. It points the content of reference type in heap.
## TDZ(Temporal Dead Zone)
对于let和const这两个没有变量提升效果的关键字。在一个封闭的块级区域内，在声明这些变量前的区域都是暂时死区（使用了会报错）。
## Symbol
### When will we need it
- For example, when you are using a object offered by others, you want to add a method with same name for this object. The
conflict happens. So we need something to make sure that properties of the object are different.
- Eliminating magic string. 强耦合例子.
### How to apply Symbol
- We can set key of object to Symbol. So that naming keys will not make conflict.
- Symbol.iterator的例子。iterator是ES6为Symbol提供的内置值。他，在可迭代对象中，指向一个function能返回一个迭代器
（所以可能这个function是生成器喽）。换句话说就是对象可以像String，Array那样通过迭代器遍历。
### Others
Symbol作为属性名不会被for...in遍历到
## Deep copy vs Shallow copy
### Assignment 
Just points to the original object.
### Shallow copy
Shallow copy creates a new object. But for reference date type of original object, it still refer to.
### Deep copy
We have to create a totally different object. And for all sub objects do the same thing.
## Type coercion
### == & === & Set class
- For Set object, NaN === NaN
- For ===, it will compare value and type. For ==, it will first do type coercion then compare.
### < > <= >=
Except +, all strings will be coerced to number.
## 原生类型构造（包装）器
Number(), Boolean(), String()...
### 内部 [[Class]]
typeof 的结果为 "object" 的值（比如数组）被额外地打上了一个内部的标签属性 [[Class]]
### Boxing
为了访问.length（如一个string primitive的.length）或使用toString()这样的方法，JS通常会自动封装（boxing）基本类型来满足这个要求。
### Unboxing
当我们想访问被包装器包装好的对象的基本类型时，可以使用valueOf方法。有的时候开箱也会隐式地发生。
## How JS work behind tha scenes
Once a function is called, an execution context is created. Execution context has 3 things.  
### Variable Object  
Arguments, Variables, functions  
### Scope chain
Scope chain of a function points to a stack including itself and its parent function (the global one is process or document)
#### Closure
闭包就是能访问另一个函数作用域中变量的函数。Scope chain is destroyed, but not VO.  
Features: data privacy, avoid mess data, cost memory.  
Example: The third argument of setTimeout method. Time (次数) count function. Debounce. Throttle.
### 'this' variable
- In general function, 'this' variable points to global object. Which object call 'this', 'this' key word points to the obj.
- There are some differences between NodeJS and browser environment. 快手题中的变量在Node环境下不会挂在global object里。而是到
module上。In browser, all things normal.
- 'this' variable in arrow function points to parent function. 不是被call的位置的parent function，而是声明的位置的。
#### Double equal signs in one expression
造成内存泄漏
### Callback function (anonymous function)
## Class
### Prototype & Inheritance
Example. Class A is inherited from class B. Then, A.proto === B.prototype. This equation describes both instantiation
and inheritance. More detailed example (Person and Athlete) is in JS course.  
Methods and properties in prototype can be shared by instances.
## Promise
- 在Promise对象实例化的过程中，我们需要投入一个带有两个参数的function来实例化这个promise。注意，这个function和他的参数只是一种形式（resolve和
reject都是在promise的constructor里被定死的），和then中执行的resolved方法有本质性的区别。
- catch then Promise.all() Promise.race Promise.resolve() Promise.reject() Promise.allSettled()
- Why do developers use promise via function form?  
### then
value -> a resolved promise object with argument  
without return -> a resolved promise object with undefined as argument  
resolved promise object -> a resolved promise object, argument in returned promise will be used as argument for next then
### catch
syntax sugar
### Promise.resolve()
Promise.resolve(123) -> a resolved promise object with argument value 123
## Async/Await
- Async function always automatically returns a promise, then the promise will automatically be resolved with returned value.
- If there is no any await in async function, it executes at once then returns a promise object. Actually,
async function executes at once after it is called.
- We can first define async function. It does not execute at once like instantiation of Promise.
It needs calling to execute.
- The result Await returns is different with Promise or then method. It can return both values and promise.
If result is promise, The return value on left side of equal sign is the arguments of resolve method.
- When will the async function get stuck? If there is an await expression (whatever it returns, promise object or value),
it will stop and wait for resolve. The code after this await expression will be put into micro-task queue.
## JS运行机制 & 宏任务与微任务
JS is single-thread. At any time, it can only execute a piece of code in file. Based on my experience, two sorts of action
such as HTTP request and time action can be executed in parallel. If we wanna execute a task with huge calculation, we should
consider web worker.  
由setTimeout, 事件触发等调用的的函数，会触发新一轮的事件循环并且独立执行他自己的宏任务微任务。而不是两个宏任务先一起执行，再一起他们的微任务。
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
- First garbage collector will mark all variables in memory. 
- Second, it will remove all marks in variables which root object (alive object) can reach.
- Third, clear all marked variable and deallocate memory.
#### 循环引用不再是问题
0引用对象总是不可获得的，这句话反过来不一定对。对于循环引用，函数调用返回后，两个对象从全局对象（根对象）出发无法获取，因此他们会被GC回收。
### Common memory leak cases
- Extra global variable
- Forgetting to deallocate timer (setTimeout)
- Closure
- DOM的应用 (这个没什么遇到)

  