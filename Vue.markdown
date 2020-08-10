## Section1
### Course Introduction
- Vue.js is very small and lean without router or other modules.
- Compared with React and Angular, Vue is not only faster at loading time but also runtime.
- There are many modules for Vue.
### Let's Create our First VueJS Application
- 教了怎么安装Vue，介绍了一个web编辑器，jsfiddle.net.
- Vue object is core of Vue. Vue object的实例对象控制HTML代码的模版（template）。
- Vue对象实例化需要一个object作为参数。object里有相对应的reserved key. 比如我们可以用el property来控制HTML file里哪段代码受该Vue object的控制。
- 在HTML file中，相应的，我们可以用HTML元素的id property来定位Vue对象修饰的特定元素。
- el中#app对应的是id，.app对应的是class修饰中的第一个元素。
- data是Vue的另一个reserved word。被某个Vue对象修饰的HTML元素可以使用该对象中的data内容，但要特殊语法。
### Extending the VueJS Application
- 这节我们做的效果有点类似于双向绑定。即我们在input元素里输入啥，Vue中的title也随之更改。当然，页面显示的内容也随之改变。
- 这里我们引入Vue里directive的概念。他是Vue中，放在元素里的特殊的property。
- directive的语法是v-on关键字+你要监听的事件类型，这里我们监听input。再者跟一个出发函数。逻辑有点类似于addEventListener method。
- 然后我们可以在相对应的Vue object里宣告和定义该method。
- 这里有个比较奇怪的点，我们在使用Vue中的data的内容时可以直接用this关键字来指向。这其实与Vue对象的封装有关。不过这里，我们只要知道用this关键字既能
access到data，也能access到method。
- 接下来是怎么获取用户输入的问题。好在我们在由事件引发调用JS method的时候Vue或者JS会把event这个object自动传进method里(同时，这个event对象也是由
JS自己产生的)。所以我们只需要宣告一个method的对象参数就好。
### Course Structure
这节讲了怎么学习Vue以及流程
### Setup VueJS Locally
这节讲了怎么用最简单的方式使用Vue.js。
## Section2
### Understanding VueJS Templates
- 这节解释的事Vue.js与HTML间的那层关系。
- Vue.js并没有将Vue对象存在一个变量中。而是将他和被控制的HTML做一个connection。
- 当检查网页的时候，我们可以在源码上看到，全是正常的HTML code。
- 总得来说，Vue.js基于HTML code制作了一个template。然后基于JS在这个temporary HTML上进行一顿操作。最后根据这个template生成真正的HTML。最后
浏览器根据真正的HTML render DOM。
### How the VueJS Template Syntax and Instance Work Together
- 注意，在由HTML产生的template中，我们要call的method return回来的内容必须能被转换成string.
### Accessing Data in the Vue Instance
- 这一节再次强调了this关键字在Vue对象里的指代功能。
- 强调了在HTML template使用Vue property和JS里使用的不同。
### Binding to Attributes
这节讲了怎么将Vue对象里的内容绑定在HTML template里。主要是一些语法. v-bind改变了HTML元素的attribute的用法。
### Understanding and Using Directives
- 这节讲的是Vue里的directives都是啥，怎么用。
- 他们在HTML里的作用，就像在告诉Vue要做什么。比如v-bind。bind something to my data. 我们也可以写自己的instruction/directives。
- 这里，某个特定的HTML元素attribute作为v-bind的arguments。
### Disable Re-Rendering with v-once
- 这节讲了v-once的一个应用场景。一般browser在编译html的时候，一旦变量被更改（比如说lecture中的title），那么网页会被re-render一次，使得所有的
title都使用最新的内容。
- 但是我们想让HTML file编译出来的网页有一种顺序执行的效果，即在title的内容被更改之前，我们使用老的内容。这时，我们就会用到v-once。
- 我们可以在某个container element上放一个v-once。这样在这个container中所有有关Vue对象的data都不会被update。
### How to Output Raw HTML
- 根据Vue的特性，Vue只会render string到页面上而不会在template中把页面转化成真正的HTML元素。
- 如果我们要把这个string转化成HTML元素的话，我们得使用v-html这个instruction，这样这个string就会被编译成相应的HTML元素。
- Vue的默认行为有一个好处就是能放CSRF攻击。如果使用了v-html的话，就要小心CSRF攻击。
### Listening to Events
- 这节讲的是一个简单的使用v-on的例子，和addListerner有点像。
### Getting Event Data from the Event Object
这节讲的是怎么使用event object里的资料。
### Passing your own Arguments with Events
- 这节讲了两种使用场景，一是如果在HTML中要call一个Vue里的method并传入argument该怎么办。
- 第二是，在前一个场景下，我们还要传入JS自带的event object。该怎么办。这里，我们要在HTML file中用到一个特殊的$符号放在参数前面。
### Modifying an Event - with Event Modifiers
- 这节我们面对的应用场景是，当我们不想某个HTML元素的子元素会触发和父元素一样的事件时。
- 这里提示一下，事件绑定的method都是在冒泡阶段被触发的。
- 一种方法是使用JS event里自带的stopPropagation。
- 这里，我们还可以用一个更elegant的方法。Vue有自带的stop关键字。
- 这种关键字算是event modifier。还有一个event modifier是preventDefault。
### Listening to Keyboard Events
- 这节针对的是由按键触发的事件。当我们想要在一个input元素里输入东西，并在结束后敲击回车表示结束并弹出alert。
- 这里我们可以用到特殊的key modifier。
### Writing JavaScript Code in the Templates
- 这节讲了一个在HTML template里使用JS code的现象。
- 我们不仅可以在大括号内使用变量，call function。甚至可以放一些简单的JS代码。Lecturer的原话是放一些expression或者statement。
- 但是像if else这种复杂的东西就放不进去。
### Using Two-Way-Binding
- 这节讲的是怎么做到双向绑定。用笨一点的办法，我们可以用v-on监听敲击事件，然后激活相对应的method来改变name这个变量。
- Vue提供了v-model这个关键字。可以直接让我们绑定相对应的variable。
### Reacting to Changes with Computed Properties
- 这里提到了一种情况。当不同的sources，比如不同的method，在update同一个变量时，可能会造成代码的冗余和难维护。
- 在解决了上一个问题后，我们遇到了第二个问题。比如我们想更新某个variable，但是用于这个variable的更新会re-render页面。从而导致一些无关的method
被执行，损耗效能。
- 为了应对上一种情况，我们可以在Vue对象里使用computed这个关键字。computed里面放的也是method。但是我们用的时候都是像用变量一样(就像用data的property
一样)。即我们在用computed的property输出东西的时候，Vue就会分析，这个property输出的结果是否与正在更新的变量有关。
- Lecturer也用一组对比实验来证明了这点（computed与method）。Caching the result.
- 这里提醒一下，callback function如果不是箭头函数的话，this关键字指向的是window。
### An Alternative to Computed Properties: Watching for Changes
- 这一节讲的是另一个使用场景，我们需要时刻监视着某个变量的动态，看他是否变化。
- 这里举的例子是，你需要run一个异步的任务。
- 一般computed都是用来完成同步任务的。Watch完成异步任务。
- computed这个东西设计出来就是为了节省效能的，所以我们一般把一些简单代码放到里面执行，这个时候同步执行这些代码对整个系统运行不会造成太大的影响。
- 而Watch监听一个频繁变化的变量的话，Watch里的JS code会被反复执行。基于JS单线程的特性，这样很吃整个前端系统的效能，所以我们干脆让Watch里执行的代码异步。
### Saving Time with Shorthands
- 这里介绍两个代码简写。v-on:可以用@来表示。意思是at某某事件，我们做什么什么。
- v-bind可以直接用:。
### Dynamic Styling with CSS Classes - Basics
- 这节讲的是怎么通过Vue往HTML元素上加CSS class。
- 我们可以把class和一个JS对象绑定起来。对象内部的语法是key作为CSS class的名，value作为boolean变量，表示是否要安上该class。
### Dynamic Styling with CSS Classes - Using Objects
- 这节讲的是如果HTML template中关于CSS class的内容太多，我们如何把它output到JS中。
### Dynamic Styling with CSS Classes - Using Names
- 另一种加载CSS class的方法。用名字。array中如果存在冲突的话，根据CSS file里的位置来决定优先级。
- 在:class中添加CSS class比在普通class attribute添加要麻烦一些。因为我们要在相对应的Vue object里存上相应的变量（这样我们在HTML template
里就不用加引号修饰了）。
- 直接在[]用CSS file里的class得加引号修饰。
### Setting Styles Dynamically (without CSS Classes)
- 这一节讲的是修改style。全程用style，没有class。
### Styling Elements with the Array Syntax
- 和Class的用法差不多。
## Section2
### Conditional Rendering with v-if
- 这里讲的是如何有条件地在页面中显示一个HTML元素。
- 我们用到v-if这个directive。当条件不满足时，该元素会被直接移出DOM（包括其子元素），而不是被hidden。
- v-else则是和上面那个v-if互换的部分。
### Using an Alternative v-if Syntax
- 这节讲的是template和v-if的联动。template tag元素是HTML5的新东西，他本身不会被render到DOM上。
- 我们通常用template来整合一些并列的元素。然后通过template来管理他们。
- 如果用div的话，可能会带来一些side effect。但由于template本身不会在DOM中被渲染，所以不用担心。
### Don't Detach it with v-show
- 这节介绍的是v-show。作用和v-if一样，但是本质上的区别是消失的元素还存留在DOM中，只不过被加上了display: none.
### Rendering Lists with v-for
tag li上的v-for关键字。他这里可以动态地为我们建立一个新变量来access array中的元素。我们可以像用data中的property一样使用该变量。
### Getting the Current Index
遍历array中内容和index的语法。
### Using an Alternative v-for Syntax
v-for和template的联动。这样可以复制几遍template中的内容。
### Looping through Objects
用v-for来遍历对象，包括value，key，index等。
### Looping through a List of Numbers
就是一个特殊的语法，用来遍历数字的。
### Keeping Track of Elements when using v-for
- 这一节讲的比较理论。老师用HTML template的例子来说明一些事实。
- 当我们要用v-for来渲染一个array时，我们在array的最后插入元素，且key设为index的话，浏览器再渲染，这样OK。
- 因为v-for在更新已经渲染的元素列表时，默认使用就地服用策略。即之前存在array里的元素都被复用。
- 而如果在array中插入元素，key的设置使用index的话，所有改元素之后的元素都要被重新渲染，因为key被改变了。这样很消耗效能。故我们在选择key的时候，
往往选那个唯一且不会变化的property来作为array item的key。
- 延伸内容是virtual DOM的diff算法。
## Section4
### Setting up the Course Project
这节讲的是怎么设置progressbar。
### Showing the Player Controls Conditionally
- 这节讲的是怎么操作控制面板。
- 一个小知识点。当v-if和v-else联用的时候，两者操控的元素必须是同一个tag并且else的把部分要跟随if。
### Implementing a "Start Game" Method
- 安装上"eventListener".
### Implementing an "Attack" Method
实现简单版的attack method
### Write better Code - Time for Refactoring!
优化一下attack method。这节还讲到一个confirm方法，和alert有点像。
### Implementing a "Heal" Method
### Finishing the Action Buttons
### Creating an Action Log
### Printing the Log (v-for)
### Finishing the Log
### Wrap Up
- 这里讲了一下，Vue可以让我们把注意力放在JS上，尤其是逻辑部分。而不像纯JS代码一样，注重与怎么与DOM交互，怎么fetch DOM元素。
- Vue让HTML template与JS的部分建立一种connection。
## Section5
### Some Basics about the VueJS Instance
- Vue instance is a middle man between our DOM (our HTML code) and our business logic.
- 这里提了两个应用场景等待学习，一是多个div元素对应不同的Vue instance。二是我们可以在该instance的外部修改这个对象的property。
### Using Multiple Vue Instances
- 这里出了一个小bug。app元素找不到。重启一下IDE解决了。
- 注意，在instance里，this关键字只能指代本instance。
### Accessing the Vue Instance from Outside
- 为了能在别的Vue instance里access其他的Vue instance里的property。我们可以把该实例存在一个variable里。一般称为vm。
- 我们不仅能在其他的Vue对象里access，还能在JS file的任何一个角落操作。
- Vue在这里起到的是一个proxy的作用。
### How VueJS manages your Data and Methods
- 我们放进Vue对象的constructor里的对象参数再经过一定转化之后变成Vue的property。
- Vue在这个过程中会监视着，看看那些properties被改变。
- 但是如果我们在定义并宣告了该Vue对象后，我们再在外部给他加property，这个时候我们是监视不了这个外部加入的property的。
- 最直接的证据是，当我们把vm1 print出来后，我们看到每一个被watch的property都有对应的get和set method。而外部加入的property没有。
### A Closer Look at $el and $data
- 这一节lecturer给我们说了，除了vm1.title这种access Vue对象data的方法，我们还可以用vm1.$data.title来存取。
- 因为被传入Vue constructor的参数的data那个对象就被赋予给$data这个property了。
- 老师还强调了Vue如何与普通JS交互。
### Placing $refs and Using them on your Templates
- 在用纯JS编写代码时，我们通常会用query等selector来access HTML里的DOM元素。这次我们讲到的$ref就起这个作用。
- 这里出现里一个和lecture不一样的地方，setTimeout并没有更新我们的vm1 title。不同的browser对这个情况有不同的反应。
- 这里我们暂时使用 childNodes[0].data 作为过度。
- 开发中最好不要直接通过$ref去修改DOM元素，会带来很多意想不到的副作用。
- 老师在最后强调了，通过$ref去修改DOM的结果可能被Vue的template覆盖。我们要分清楚，DOM和Vue通过HTML code生成的template是两回事。有的时候我们
直接修改DOM，但是当Vue re-render某些东西时，会覆盖掉之前的从DOM修改内容。所以$ref最好用来读东西。
### Mounting a Template
- Vue与template的关系：Vue通过HTML code 得到template（这个template存在内存里），并可以把他们快速转化成DOM。这是Vue deriving template的第一种方法。
第二种是由template property声明，并且可以通过el property或$mount方法挂载。el和mount一对，HTML和template一对。
- $mount是Vue对象自带的原生方法。带$符号的基本都是。
- 在Vue实例中的template，我们不能写多行。
- 这里先讲一个小知识点，关于el，template，和render方法。在lecture中，我们会发现当el和template同时存在时，用$mount将一个Vue实例挂载在HTML上
该挂载点对应的DOM元素会被template的内容取代（似乎另有innerHTML有关的用法），因为template的优先级高于el（这是第二种得到template方法）。
这个取代效果与$mount无关。
- Vue中的template可以输入一些小型的DOM元素（非多行）。我们可以通过普通的JS手段access一个DOM元素，并把该Vue instance插入进去（appendChild）。
- el一般用于你已知要插入哪个元素的情况。$mount用于你先写好Vue instance但是还没有决定好插入在哪里的情况。
- 最后lecturer讲了一种用法，先把一个元素从DOM中fetch出来，作为一个插入点。在这之前，我们得先用$mount函数挂载Vue instance，尽管它out off screen
（就是在DOM上看不到）。最后再把这个挂载后的实例插入。挂载这步是必不可少的。
- 最后一种做法，那个预先挂载的那步不是特别了解，可能是需要让template先被complied。我们能且仅能通过.$el来访问被挂载的Vue实例（对应的template？）。
### Using Components
- 这节讲了一个template复用的问题。一般用Vue实例去挂载的话，往往只对第一个挂载的元素有效。
- 但是我们可以用到Vue.component, 他有2个参数，前一个是selector，即我们要取代/挂载的元素，后一个参数是template。
- 注意这个Vue.component的指令要放在setTimeout前？盲猜和Vue的生命周期有关。
- 这节本质上还是强调component/template的可复用性。
### Limitations of some Templates
- 这节提到了两个Version的VueJS。
- 第一个运行在浏览器里，有compiler。这个版本支持template property。(re-compiled)
- 第二个version的VueJS是不带compiler的。我们在build的过程中已经把要转化成DOM的template编译好。当我们要re-render DOM的时候，我们也只能使用
这些已经编译好的template。但是这个版本的好处就是小且快。(pre-complied)
### How VueJS Updates the DOM
- 这里再次提到了Vue实例与DOM之间的互动依赖于template，以及template的两种来源。
- JS很快，但是DOM操作很慢。
- 提到了virtual DOM。一种以JS的形式表现的DOM。如果Vue中的数据做了更改，我们会recreate a new virtual DOM。然后与旧的virtual DOM进行比较，
更新那些有差异的部分。最后舍弃旧的virtual DOM。
### The VueJS Instance Lifecycle
- 和React一样，Vue实例的lifecycle始于constructor method。
- 然后我们进入beforeCreate方法。这个method的意义在于初始化我们传进去的一些data和events（就是以object形式传入Vue constructor的那些东西）。
- 接下来，我们再进入create方法。
- 然后，我们再编译并得出template。template可以从HTML得来，或者template property得来。
- 然后进入beforeMount方法，这是在我们要挂载被编译好的template前发生的。
- 接下来我们就把相对应的元素替换为template，这一步应该指的是把所有的template中的变量替换为实际值，该绑好method的地方就绑好。
- 最后就把template mount到DOM上。
- 接下来，当我们要更新页面的时候（由于data changed等原因）。在re-render DOM之前，我们会先进入beforeUpdate方法。
- 在re-render DOM之后，我们今进入updated method。
- 当我们要destroyed一个Vue instance时，同理也有destroyed和beforeDestroyed method。
### The VueJS Instance Lifecycle in Practice
- 这节实操怎么使用lifeCycle method。
- 这里注意一个点，如果新旧virtual DOM是一样的话，那么vue是不会让页面被re-render的。即不会触发beforeUpdate和updated method。
- $destroy是Vue实例里自带的destroy method。他会断开该Vue实例对DOM的逻辑上的一切控制。
## Section6
### Why do we need a Development Server?
- 我们需要将ES6转化为ES5，以保证代码能在各个浏览器中运行。
- 虽然我们能在本地通过browser open file（file protocol）的方式开发web页面，但是真实世界中，访问者毕竟还是通过互联网访问服务器中的内容。
所以我们可以在自己的机器上模拟一个server，这样我们就能通过http的方式来fetch web内容。
- 我们还需要实现lazy loading。
- 以上3点就是我们需要用development server的理由。
### What does "Development Workflow" mean?
- 我们写的第一手code到放在服务器上能服务client的过程中，我们可以做一些动作。
- 编译single file template. 也指Vue.app file.
- SFT有益于我们缩小VueJS code的大小。因为在browser中不会发生编译.当然re-rendering会一直发生，但是template都已经被渲染好。complied means
transformed to JS. 以下是原文。
- Single file templates are a powerful alternative to using the el property and inferring a template from the dom or the 
template property. Single file templates, as the name implies it's basically the template outsourced into a separate 
file and the workflow we'll be using has a certain, let's say tool in it which understands such single 
file templates and then is able to compile them. And I mean with that compile them during the development workflow 
so that the app we ship already has the compiled templates, so the template transformed into javascript code which is 
then executable in the browser. That is different to the current approach,
- Right now we're using a setup where everything gets compiled in the browser, we're shipping strings or this element 
selector and we're leaving it to vuejs to select these parts in the dom at runtime and compile it from the native dom there.
- Now with that approach, we're able to compile it on our machine which makes it much faster and smaller because we're 
able to get rid of this compiler and we are shipping the finished code.
- 不区分大小写的component selector，JS或CSS的preprocessor。
### Using the Vue CLI to create Projects
- Vue loader，作用和webpack差不多。
- Vue CLI有几种不同的template，这里的template和之前Vue从HTML中得出来的template不是一个东西。最简单的就是simple的那个版本，也就是lecturer最早用的那种，
只要一个index.html和从CDN引入Vue就行了。同样，也有webpack的template，就是显得更复杂。
- 对于template compliation，除了simple的那个版本以外，其他workflow都支持。
### Installing the Vue CLI and Creating a new Project
- 先通过NPM装Vue CLI
- 可以通过Vue CLI建立一个Vue project，并指定workflow的模式。
- 这时候我们建立出来的项目文件夹里只有简单的package.json, webpack配置文档等东西。我们需要用npm install来根据package.json把该打好的包都打好。
- 打好了后，项目文件夹里大部分都是development dependencies，少量是webpack需要的东西。
- 最后通过npm dev run来启动该项目的development server。即可以随时根据项目中内容的改变re-render的进程。
### An Overview over the Webpack Template Folder Structure
- 这节讲解的是Vue项目的文件结构。
- src folder是专门来放我们的写的code的地方。
- .babelrc配置文件（转ES6到ES5的）
- 作为入口的index.html文件，其中有一个build的script tag。这个tag里面是webpack打包过后的东西。在开发者模式中，我们是不会见到这个/dist/build.js
file的。因为它被存在memory里。
- package.json. 其中有vue-loader，这是一个与single file template有关的loader。
- webpack配置文件
### Understanding ".vue" Files
- Single file template: 不再借助el和template properties获得template。
- 主要是三个file之间的互动。main.js中的实例指定挂载的点, 以及渲染方法。Vue.app是SFT。Vue 选项中的 render 函数若存在，则 Vue 构造函数不会从 
template 选项或通过 el 选项指定的挂载元素中提取出的 HTML 模板编译渲染函数。
- 当index.html被loaded时，main.js被执行。main.js里的vue实例的el property只起到挂载的作用而起不到inferring template的作用。
- 在 vue.js实例里的 h function takes a template, a vuejs template to be rendered. h到底是啥？App就是Vue.app export出来的东西。
- 一般情况下，Vue.app由三部分组成：template，script以及style。
- 即使没有export内容，仅靠template也可以render。
- render后，index.html中的挂载点会被覆盖。
### Understanding the Object in the Vue File
- export default那块就是实例化Vue instance的参数对应的部分。主要负责该 组件/instance 的逻辑部分。
### How to Build your App for Production
- 生成发布版本。
### More about ".vue" Files and the CLI
### Debugging VueJS Projects
介绍了两个工具？再看看
## Section 7
### An Introduction to Components
- 提了在HTML template里简单版的Vue instance复用行不通。只有第一个被挂载。
- 第一个参数是选择器，第二个是Vue的实例，注意选择器名最好不要与第三方包冲突。
- 由于component继承于Vue实例，如果我们直接用object的形式来定义data property，那会干涉其他的组件的data（这里再多研究一下？）。
- 所以，仅在root vue instance使用object形式就行了。另一种使用data的方式，用function return应运而生。该function直接return一个object。
### Storing Data in Components with the Data Method
- 这节讲了组件如何被复用，且避免data sharing。Lecturer这里举的例子是 由一个组件产生的两个Vue实例 的data property同时指向一个object（即指针指向memory中相同的位置）。
这种情况下，两个instance share一个data。这也是为什么每个Vue instance要以function的形式return一个独立的object的原因。以下是原文。
- But now we're cheating because now returning the same data object and I mean the same, not content wise but actually the same place in memory in all instances of this component, so if we create the component twice as we do here, I actually do have two instances with the same data object.
- 但是对methods，我们可以赋予一个object。因为在methods里，每个方法内部的this关键字都指向不同的 组件的 实例。
### Registering Components Locally and Globally
- Vue.componen这种写法通常是全局（本.vue file的全局）的写法。他会把整个页面template里的<my-cmp>都替换掉。
- Locally的写法是，以变量的形式保存下来，放在特定的Vue instance的component property下，这样它的作用范围就可控了。
### The "Root Component" in the App.vue File
- 对于我们用vue-cli建立出来的项目形式，其实.vue file的东西就是render函数渲染的内容，也就是root component。
- 注意<script>里是纯JS code，我们export出来的本质上是一个JS object。我们可以把他的selector看成放在main.js的el里。
### Creating a Component
- 注意在渲染的时候，我们必须要一个root component。
### Using Components
- Vue file的命名规则，首字母大写的驼峰命名法。
























