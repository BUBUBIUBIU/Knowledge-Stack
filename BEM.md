## 什么是BEM
BEM是一套基于组件的WEB开发方法论，全称为block，element以及modifier。它的主要思想是将WEB页面划分为各个独立的模块进行开发，消除或降低模块之间的耦合，使得代码的复用性和拓展性提高，达到优化开发体验的目的。接下来我们来看看BEM中的几个主要概念。
### Block
<img src="https://github.com/BUBUBIUBIU/Knowledge-Stack/blob/master/1jbsbkghewowpcixhqwbdi7q3o9bjtsfdsuc7h2i1u5aiao3xtx.png" width="500"/>  

* 在BEM中，block指的是在页面中具有意义且能够独立存在的实体，比如说（上图中的）button，navigation menu和logo。一个block的名称必须是独一无二且具有语意的。最好能描述该block的使用目的，比如navigation menu或submit button，而不是它的状态，比如red button。
```
<!-- 正确示范 -->
<button class="submit-button"></button>

<!-- 错误示范 -->
<button class="red-button"></button>
```
* block可以互相嵌套，且没有嵌套层数的限制。多个block的实体可以存在于同一个页面上。
```
<!-- header block -->
<header class="header">
    <!-- logo block -->
    <div class="logo"></div>

    <!-- navigation-menu block -->
    <div class="navigation-menu"></div>
</header>
```
### Element
* element作为block的一部分，其名字同样是具有语意和功能性的。但重要的一点是，element不能脱离block单独存在。举个例子，上图中menu和menu item就是block与element的关系，如果我们把一个menu item放menu之外，它是不具备任何意义的。element的名字的结构为block-name__element-name，由两个下划线隔开。
```
<!-- search-form block -->
<form class="search-form">
    <!-- search form里的input element -->
    <input class="search-form__input">

    <!-- search里的button element -->
    <button class="search-form__button">Search</button>
</form>
```
* 和block一样，element之间也可以互相嵌套。值得注意的是，一个element不能成为另一个element的一部分。block定义了名称空间，这样保证了名称空间内的element只依赖于该block name，从而不会出现语意上的歧义。
```
<!-- 正确示范 -->
<form class="search-form">
    <div class="search-form__content">
        <input class="search-form__input">
        
        <button class="search-form__button">Search</button>
    </div>
</form>

<!-- 错误示范 -->
<form class="search-form">
    <div class="search-form__content">
        <input class="search-form__content__input">
        
        <button class="search-form__content__button">Search</button>
    </div>
</form>
```
* element不是必要的，比如一个logo block.
```
    <div class="logo">logo</div>
```
补充
### Block还是Element？
当一个组件在页面中的性质较为独立，且服用需求高的时候，它适合成为block。而对某个组件有强依附性的组件，我们可以将其定义为element。
### Modifier
* 之前提到了，block和element的名字通常都是不起状态描述作用的。那么这个任务由谁来完成呢？没错，就是modifier。modifier不仅起到了状态描述的作用，还包括行为（比如某些block或element的动画的移动方向）和外表（大小，颜色等）。命名规则上，modifier与element或者block以单个下划线隔开。  
* modifier分为两种形式存在，第一种是键值对的形式，比如我们在为一个header设定大小的时候。
```
<!-- size为small的header -->
<header class="header_size_s"></header>

<!-- size为medium的header -->
<header class="header_size_m"></header>
```
* 第二种是boolean。它其实是第一种的特殊情况，即其值为何并关键，重要的是其存在与否。比如disabled这个属性。
```
<!-- 禁用状态下的button -->
<button class="button button_disabled"></button>

<!-- 启用状态下的button -->
<button class="button"></button>
```
在了解了BEM的几个主要概念后，让我们通过BEM来重新认识HTML。
## 用BEM重新定义HTML元素
<img src="https://github.com/BUBUBIUBIU/Knowledge-Stack/blob/master/1jbsbkghewowpcixhqwbdi7q3o9bjtsfdsuc7h2i1u5aiao3xtx.png" width="500"/>  

这里我们借用一下Element-UI的form表单。大家可以看到，表单中有text-input，selector以及radio等输入型blocks。我们可以尝试着使用伪代码来解析这些blocks的构成。首先是text-input。
```
Block text-input  
Modifier multiline
Modifier disabled
  Element text-field
  Element label
```
text-input的基本功能是接受文本输入，故text-filed是其必不可少的元素，而label元素（可选）则起到提示输入内容的作用。对于功能和样式繁多的Element-UI，可能还可以添加status-icon或者placeholder这种可选元素。对于text-input这个block来说，它可以处于启用或禁用状态，也可以以单行或多行来呈现输入内容，所以这两个描述block状态和外表的修饰属于modifier。  

我们还可以再看一个比较复杂的例子，selector。
```
Block selector
Modifier disabled
Modifier multiple
  Element optgroup
  Element option
    Modifier disabled
    Modifier selected
```
注意selector和option都有disabed modifier。但是两者的作用范围是不同的，前者禁用整个block，后者仅禁用单个选项。  

看了以上两个例子后，大家可以尝试着用BEM来重构checkbox，radio等HTML元素，巩固对BEM的了解。遗憾的是，HTML在实现大多数此类元素的时候都使用了`<input>`tag。同样的，在HTML4中，不同的heading由`<h1>`到`<h6>`实现。其实对于该需求我们可以用modifier来满足。随后的HTML5也在尝试着用section类的元素来调整这一情况。





补充
CSS之误会说一下
