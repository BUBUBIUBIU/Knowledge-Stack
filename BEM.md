## 什么是BEM
BEM是一套基于组件的WEB开发方法论，全称为Block，Element以及Modifier。它的主要思想是将WEB页面划分为各个独立的模块进行开发，消除或降低模块之间的耦合，使得代码的复用性和拓展性提高，达到优化开发体验的目的。接下来我们来看看BEM中的几个主要概念。
### Block
在BEM中，block指的是在页面中 拥有意义的 能够独立存在的 实体，比如说（上图中的）button，navigation menu或者logo。一个block的名称必须是独一无二且具有语意的。最好能描述该block的使用目的，比如navigation menu或submit button，而不是它的状态（例子）。
Block可以互相嵌套，且没有嵌套层数的限制。多个block的实体可以存在于同一个页面上。
### Element
Element作为block的一部分，其名字同样是具有语意和功能性的。但重要的一点是，element不能脱离block单独存在。举个例子，上图中menu和menu item就是block与element的关系，如果我们把一个menu item放menu之外，它是不具备任何意义的。由此我们可以得出，element的名字的结构应该是block-name__element-name.
和block一样，element之间也可以互相嵌套。
值得注意的是，一个element不能成为另一个element的一部分。block定义了名称空间，这样保证了名称空间内的element只依赖于该block name，从而不会出现语意上的歧义。
element不是必要的，例子：logo
（有修改)
### Modifier
之前提到了，block和element的名字通常都是不起状态描述作用的。那么这个任务有谁来完成呢？没错，就是Modifier。Modifier不仅起到了状态描述的作用，还包括行为（）和外表（）。  
modifier分为两种形式存在，第一种是键值对的形式，比如我们在为一个header设定大小的时候。

第二种是boolean。它其实是第一种的特殊情况，即其值为何并不相关，重要的是其存在与否。比如disabled这个属性。

## 用BEM重新定义HTML元素
这里我们借用一下Element-UI的form表单。  
![Alt text](https://github.com/BUBUBIUBIU/Knowledge-Stack/blob/master/1jbsbkghewowpcixhqwbdi7q3o9bjtsfdsuc7h2i1u5aiao3xtx.png)
大家可以看到，表单中有text-input，selector以及radio等输入型blocks。我们可以尝试着使用伪代码来解析这些blocks的构成。首先是text-input。
<pre><code>Block text-input  
Modifier multiline
Modifier disabled
  Element text-field
  Element label</code></pre>
text-input的基本功能是接受文本输入，故text-filed是其必不可少的元素，而label元素（可选）则起到提示输入内容的作用。对于功能和样式繁多的Element-UI，可能还可以添加status-icon或者placeholder这种可选元素。对于text-input这个block来说，它可以处于启用或禁用状态，也可以以单行或多行来呈现输入内容，所以这两个描述block状态和外表的修饰属于modifier。  

我们还可以再看一个比较复杂的例子，selector。
<pre><code>Block selector
Modifier disabled
Modifier multiple
  Element optgroup
  Element option
    Modifier disabled
    Modifier selected</code></pre>
注意selector和option都有disabed modifier。但是两者的作用范围是不同的，前者禁用整个block，后者仅禁用单个选项。  

看了以上两个例子后，大家可以尝试着用BEM来重构checkbox，radio等HTML元素，巩固对BEM的了解。遗憾的是，HTML在实现大多数此类元素的时候都使用了`<input>`tag。同样的，在HTML4中，不同的heading由`<h1>`到`<h6>`实现。其实对于该需求我们可以用modifier来满足。随后的HTML5也在尝试着用section类的元素来调整这一情况。





补充
CSS之误会说一下
