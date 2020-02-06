##Class/Prototype/Inheritance/

##Promise

##Async/Await
We can first define async function. It does not execute at once like instantiation of Promise.
It needs calling to execute.

The result Await returns is different with Promise or then method. It returns the value which is the arguments
of resolve method.

Async function always automatically returns a promise, then the promise will automatically be resolved with returned value

If there is no any await in async function, it executes at once then returns a promise object. Actually,
async function executes at once then it is called.

When will the async function get stuck? If a await expresion gets a promise object, it will stop and wait for resolve.
The code after this await expression will be put into micro-task queue.  

##JS运行机制/宏任务与微任务/