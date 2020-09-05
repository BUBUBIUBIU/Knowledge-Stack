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
- Vue不允许动态地添加根级别的响应式对象，但是根级别的非响应式可以。
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
即，尽管你是响应式的属性，但是你没在页面上显示的话，你被更改后也不会出发updated方法。不是响应式属性但是出现在页面上的话也同理。如果
你非想要对这些property有反应的话，可以设置watch方法来观察他们。
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
- But now we're cheating because now returning the same data object and I mean the same, not content wise but actually the same place in memory in all instances  of this component, so if we create the component twice as we do here, I actually do have two instances with the same data object.
- 但是对methods，我们可以赋予一个object。因为在methods里，每个方法内部的this关键字都指向不同的 组件的 实例。
### Registering Components Locally and Globally
- Vue.componen这种写法通常是全局（本.vue file的全局）的写法。他会把整个页面template里的<my-cmp>都替换掉。
- Locally的写法是，以变量的形式保存下来，放在特定的Vue instance的component property下，这样它的作用范围就可控了
### The "Root Component" in the App.vue File
- 对于我们用vue-cli建立出来的项目形式，其实.vue file的东西就是render函数渲染的内容，也就是root component。
- 注意<script>里是纯JS code，我们export出来的本质上是一个JS object。我们可以把他的selector看成放在main.js的el里。
### Creating a Component
- 注意在渲染的时候，我们必须要一个root component。
### Using Components
- Vue file的命名规则，首字母大写的驼峰命名法。
### Moving to a Better Folder Structure
- 优雅地进行文件分类，根据不同的功能进行划分
### How to Name your Component Tags (Selectors)
- selector，在components中和在template中，既可以用驼峰命名法，也可以用dash。
- 由于DOM是对大小写是不敏感的，所以我们一般对DOM用的都是dash命名法，而不是驼峰（在用el和template的时候特明显）。
- VueJS帮助联动dash 命名法和驼峰命名法。所以我们在script里用驼峰，在template里用dash命名法。
- 提到ES6的实例赋值特征。
### Scoping Component Styles
- 每个.vue file里的style内容的作用范围都是全局的，这会造成很多冲突和不便。
- scoped关键字可以限制style的作用范围至本.vue文件。
- 这里稍微提到了shadow DOM。Vue + scoped的模式有些像shadow DOM。
- 在用了scoped后，我们可以在DOM看到每个元素都有一个奇怪的data标签. 这些attribute不会与本身的的HTML元素的attribute产生冲突。
- indeed it's using the default html data attribute which allows us to attach custom data to elements, so it's in line with a good html style.
- div + 奇怪的attribute的模式来匹配和限制各个.vue file的style。

## Section8
### Communication Problems
- 预设前置环境，data从父组件传达子组件。
### Using Props for Parent => Child Communication
- 这里终于引入props了。意思是property from outside。形式是以array的形式。
- 注意不要把参数传死了(穿成string)，记得用v-bind。
### Naming "props"
- 同样props也可以用驼峰命名法。
### Using "props" in the Child Component
- 这节讲了在<script>内使用props。
### Validating "props"
- props的形式从array改成object。
- 两个新关键字，default，require（注意override）。type可以多选。
### Using Custom Events for Child => Parent Communication
- 这节讲怎么从子组件传data到父组件。可以用客制化事件（emit event）。
- 这里讲了一个特殊情况，就是父组件直接传参考类型下来，那我们在子组件里更改的话，父组件里也会相应地更改。（传址与传值）
- 注意，$emit只会向上传一层。即，父组件的父组件收不到事件。
- 我们可以让父组件监听 要回传data的子组件上的 特定的事件。而子组件要做好$emit的工作。
- 不建议用这种方法，理由在Vue的报错里。
### Understanding Unidirectional Data Flow
- 父组件传method给子组件A，A通过该method传data给父组件，然后父组件再将data传给子组件。
### Communicating with Callback Functions
- 这里提到第二种子组件回传父组件的方法，不用customer event。传一个可以操控父组件data的method到子组件，然后由子组件去弄他。
### Communication between Sibling Components
- customer event的操作例子，自己可以做可以做一个传method版的。这两种都必须经过父组件。
### Using an Event Bus for Communication
- 有点redux的味道，但是eventBus并没有hold住这些储存内容。
### Centralizing Code in an Event Bus
- emit method可以集中管理在eventBus里，有利于高效复用。但是监听还是在各个实例里监听。
- 同时这个eventBus object里也可以拥有data。
  
## Section9
### Setting up the Module Project
- 预设应用场景
### Passing Content - The Suboptimal Solution
- 当我们想传一堆HTML code进入子组件时，我们就会用到这个。
### Passing Content with Slots
- 为了达到上述要求，我们就会用到slot, which allows us to pass in data from outside and render it in the child component.
听
### How Slot Content gets Compiled and Styled
- 现在我们来搞清楚，这个从父组件被传入的code是在 父组件 还是 子组件被编译的。
- 对于被传入的这部份代码，styling是在子组件，但是其他比如显示variable，v-if这些，是由父组件控制的。
### Changed Slot Styling Behavior
- 现在父组件也可以控制styling了。
### Using Multiple Slots (Named Slots)
- 这节讲的是 怎么在子组件分流 由父组件传下来的所有slot 的内容。
- 关键字slot（父），name（子）。
- 注意，named slot只能将v-slot加在template上，只有在默认scoped slot的情况下例外。
### Default Slots and Slot Defaults
- 没有被分配的slot就会跑到默认的<slot>那。
- 我们也可以为一下子组件的slot设置默认内容。当父组件传来对应的内容时，默认内容就被替代。
### Scoped slot
- 这是教程里没有的新内容，讲的是父组件如何从子组件中抽取数据的事。scoped slot的语法和named slot有点像。不要弄混。他用=表示。
### A Summary on Slots
slot的用处。
### Switching Multiple Components with Dynamic Components
- 父组件如何动态地选择子组件
- 关键字component，:is.
### Understanding Dynamic Component Behavior
- 我们在切换动态组件的时候，旧组件是被破坏的（destroyed）。
### Keeping Dynamic Components Alive
- 用keep-alive包住动态组件
### Dynamic Component Lifecycle Hooks
- 在用keep-alive的情况下，我们还有deactived和activated来模拟destroyed和created。

## Section11
### A Basic <input> Form Binding
- v-model, 跟这个关键字绑上的的data，Vue会自动追踪他的修改源。即我们修改从input field修改，变量的值会变，我们从其他地方修改，input field的值会变。
### Grouping Data and Pre-Populating Inputs
### Modifying User Input with Input Modifiers
- 介绍了几个v-model后面的modifier，lazy，trim，number
### Binding <textarea> and Saving Line Breaks
- 在<textarea>中留预设信息是没有用的，还是得看v-model。
- 在<textarea>的范围中让内容回车时，<p>中显示的内容却只是一个空格。这个时候我们可以在<p>上安上一个HTML自带的style，white-space:pre来让他出现line
break。
### Using Checkboxes and Saving Data in Arrays
- 这里的应用场景是我们想把checkbox的每个选项都装在Vue data property的一个array里。
- 首先这个data property必须是一个array，然后我们在checkbox（input tag）上用v-model绑在同一个data property上，这样Vue就会自动帮我们追踪。
### Using Radio Buttons
- 对于radio button，只要你用v-model把他们绑在同一个data property上，那么Vue就明白这组radio button里只能选一个。并且会切换到选中的值。
### Handling Dropdowns with 'select' and 'option'
- <option>可善用v-for铺开。<option>自带默认选项关键字selected，把对应的选项的selected设成true就行（如selected='...true的条件'）。
- 我们依然用v-model来绑定data中相对应的property。要注意的是，如果该property已经有值了，那他会覆盖selected的默认选项（即这也是一种默认设置法）。
### What v-model does and How to Create a Custom Control
- 这节讲了v-model的本质就是用value去显示数据，用@input去监听数据变化以及实时修改数据。
### Creating a Custom Control (Input)
- 这节讲的是自己怎么客制化一个和v-model配合的component. 其实相当于<input>元素。
- 关键点在于接受父组件的prop和经过事件触发后，要$emit相应的事件出去给位于父组件的v-model。
### Submitting a Form
- 这节讲的是如何submit form。from里面会包含很多信息。就是之前我们在网页表单里输入的那些。
- 我们先用directive里的prevent modifier来阻止浏览器的默认发送行为。然后自己handle整个submit流程。
### Assignment
- 新学一招，input元素放进label元素里就不用声明for和id来匹配了
- 注意在form里submit的时候，我们要阻止浏览器的默认行为。
- 这里注意，在客制化的input组件中，$emit的第一个参数并不是没有意义的。应该调成input。因为在父组件中的v-model监听的就是input事件。
- 注意，把computed当成property在使用。

## Section12
### Understanding Directives
- 先介绍了几个内置的directives。v-这个东西是告诉vue，这attribute是自己人。
- 注意，在用v-html的时候，Be careful when using this directive, you should sanitize your output to make sure you're not getting a victim of 
  cross-site scripting attacks because you can output html code there and that of course could also be malicious script tags.
- 如果我们想要所有的组件都能用到该directives的话，我们在main.js中注册directive（globally）, 第一个参数就是该directive的名字.
### How Directives Work - Hook Functions
- directives也像compnents那样有生命周期。
- 第一个遭遇到的就是bind(). 当我们将directive绑在元素上时就会触发它。三个参数，el是我们绑定的对象元素，binding是一些传入参数，vnode与virtual DOM有关，但很少用。对于
  后两个参数，我们一般只读不改（something you should not change at runtime）。
- inserted. 当元素被inserted入DOM时触发。我们比较少用。
- update。当本身update而他的children未update时触发。这里有新旧两个virtual DOM。
- componentUpdate.当children也被update完之后。
- unbind. 当该directive被移除的时候。
### Creating a Simple Directive
- 如何使用directive的bind给component上色
### Passing Values to Custom Directives
### Passing Arguments to Custom Directives
- arg的用法和value有点像，就是用:号绑定。
- 这里我们实现的需求是用户可以根据binding重的arg输出。
### Modifying a Custom Directive with Modifiers
- 这节讲了怎么自制modifier。如果有加载这个modifier的话，modifier array相应的部分就会变true。
### Custom Directives - A Summary
### Registering Directives Locally
- 如果我们仅想要在某个特定的组件里使用directive的话，我们可以在组件里设置，和component道理一样。
### Using Multiple Modifiers
- 这节讲了怎么使用和定义多个modifier。
- modifiers可chain。
### Passing more Complex Values to Directives
- 对于directive的value部分，我们不仅可以传string，也可以传object，好好使用。
### 关于binding.arg与binding.value的用法差异
- 前者只能用来传string类型的值，使用范围较局限，后者可以传乱七八糟的东西，用起来较广。

## Section13
### Module Introduction
### Creating a Local Filter
- filter都是自己做的，没有原生的。
- filter的作用往往只是转换一下data在template里的显示形式，而不是改变资料自己本身。
- filter的关键字的位置和components他们是同一个级别。同理filter也可以globally地注册（Vue.filter）。
- 每个tilter都有它的输入。通常在使用的时候，输入都是他的 | 号前面的那个输出。
### Global Filters and How to Chain Multiple Filters
- filter可以组成filter chain。就是前面的结果传给后面。
### An (often-times better) Alternative to Filters: Computed Properties
- 这里lecturer举了个例子，当我们要用filter去过滤一个list的时候（比如<li>），一旦页面发生re-render，Vue就会跑去对他们进行重新计算，
  这极大的耗费了效能。
- 在这种情况下，我们在computed中实现filter才是较好的选择，而在仅在<li>中展示被computed过滤之后的数据。
### Understanding Mixins
- Lecturer在这里举了一个filter重复的例子。比如local filter，我们可能会在不同的组件中需要用到同样的过滤器（computed的那种版本）。
这个时候就会造成代码冗余。这个时候我们就会需要Mixin。
### Creating and Using Mixins
- mixin的形式是array。它本质上是一个object形式的代码，但是可以填充到我们Vue instance的部分。
- 牛逼的地方是，mixin还能与我们原文件中现有的代码merge成新的组件。
### How Mixins get Merged
- 这节讲了Mixin的生命周期作用原理，如果Mixin中的代码和Mixin所嵌入的文件中都有created这个lifecycle hook，那么Mixin中的那个会先执行，
原文件中的后执行。这是为了确保原文件中的lifecycle hook可以覆盖掉mixin的内容。
### Creating a Global Mixin (Special Case!)
- 这里提到了当我们想要把某个mixin插入到所有的组件中时，我们就得注册一个全局的mixin。
- 注意，在main.js中的new Vue本身也是一个 组件/Vue instance 所以他也有自己的生命周期函数。
- 全局Mixin重的生命周期函数执行顺序是最高的。但也是最易被覆盖的。
### Mixins and Scope
- Mixin中的代码相当于直接插入对应的Vue instance。他们之间不会互相影响。即修改一个mixin的内容不会对其他使用该mixin的组件造成影响。
- 如果你想造成影响的话，eventBus或者直接引入一个JS object或许是个方案。

## Section14
### Understanding Transitions
- 一般来说，我们用v-if来控制一个元素是否render。我们可以用一个叫<transition>的元素来把它mount上DOM和unmount下来的过程做成动画。
### Preparing Code to use Transitions
- 注意，transition里只能放一个元素。如果你要放多个元素的话。你得保证他们是if else的关系（即一个出现，另一个消失）。
### Setting Up a Transition
- 不通过transition加载的动画很难通过Vue实现。
- 这里讲了transition的动画流程。如果是嵌入的动画的话，一开始有个-enter CSS class在第一帧挂载在元素上，后面开始挂载-enter-active。
- 同理，当元素要unmount时候，第一帧也有个-leave的frame，后面也跟着-leave-active。
### Assigning CSS Classes for Transitions
- 设好4个专用class，然后相对应的transition要用name来标注。
### Creating a "Fade" Transition with the CSS Transition Property
- 这里我们要做一个从透明到显现的一个效果，所以在开头的第一帧，我们就把opacity设成0. 注意，当第一帧过去后，-enter class会立刻被移除。
### Creating a "Slide" Transition with the CSS Animation Property
- 这次我们用animation。
### Mixing Transition and Animation Properties
- 注意，当transition和animation产生时常冲突时，Vue会默认用长的那个。但是这有时候不符合我们的预期。这个时候我们可以在transition里使用type来指明
  我们该完整地遵循哪种动画。
### Animating v-if and v-show
### Setting Up an Initial (on-load) Animation
- 这里讲的是，在我们刷新页面的时候（让动画显现的时候），怎么让元素自动启用动画效果。关键字是appear。
### Using Different CSS Class Names
- 这节引入了一个很牛逼的CSS动画库，animate.css。网上可以搜得到，用CDN可以装好。
- 问题来到怎么用这些class。如果我们命名了transition的话，那么transition肯定会去style那个区域里找相对应的4个-enter, -enter-active。这样我们就只能用他的
  class了。
- 这个时候我们可以在transition这个element上以style的形式配置这四个（-enter之流）东西。这样我们就可以在动画恰当的时候挂载自己想要的class。
### Using Dynamic Names and Attributes
- 这节告诉我们，transition上的各个properties都可以被:自由bind.
### Transitioning between Multiple Elements (Theory)
### Transitioning between Multiple Elements (Practice)
- 注意，在使用条件控制元素进出的时候。我们可以用v-if+v-else或者两个v-if。但是我们不能使用v-show。
- 注意到在没有key properties标明元素的情况下，第二个warning元素直接僵硬地出现，没有fade in的动画。这是因为在
  Vue看来，这两个一进一出的元素都是同一个元素。我只是替换内容罢了。所以这里我们需要key来标示这两个独立的元素。
- 还有一点是，在transition中。默认是一进一出两个元素同时出现在页面中。这样看起来就没有一进一出的效果了。为了解决这个问题
  我们得用mode关键字。属性为out-in。
- out-in的意思是让old element先leave。新element再进去（使用enter的动画）。
### Listening to Transition Event Hooks
- 这节讲的是用JS操控动画的理论。从一个元素挂载到DOM到unmount下来的过程中。transition这个element会自动emit一些事件。
  我们可以用这些事件来出发函数。从而操纵动画。
### Understanding JavaScript Animations
- 这里讲到了done方法。意思是当emit时间所触发的方法执行到done后。该动画就结束了。为什么要done是因为有时候这些方法里会有一些异步方法。这不利于
  我们控制动画的进行。如果你用的是CSS的话，transition和animation自带done的效果（已指定动画时间）。
### Excluding CSS from your Animation
- 尽管我们在代码上都用的是JS而不是CSS。但是Vue还是会去检查那些特定的CSS class里有没有东西。这个动作会耗费一些效能。我们就把:css这个关键字绑上
  'false' string就好。
### Creating an Animation in JavaScript
- 这节讲的是怎么具体设置enter和leave这两个method。注意在初始化元素的动画的时候把初始化值设置好。
### Animating Dynamic Components
- 这节讲的是怎么在多个components中做选择。用的是dynamic components。
### Animating Lists with <transition-group>
### Using <transition-group> - Preparations
- 先不加动画，预设场景。
### Using <transition-group> to Animate a List
- transition-group的用法和transition一样。唯一的区别是transition不会在DOM上留下任何东西。但是transition-group会。
  默认留下span。当然你也可以通过tag关键字来设置。
- 这里，我们注意到一个问题。在移除element出文档流时，上面的元素并不会立刻滑下去。因为被移出的元素仍然占着文档流中的位置。
- 这里我们引入一个新的class。xxx-move。当某个元素的位置被改变时（比如删除，添加）。这个class就会被attach上。这个class会加在包括因元素删减 而引起位置改变的元素上。
- 我们直接在slide-move里面放一个transition。因为当一个元素的位置变动时，Vue会自动用transformX或者transformY来调整这个元素。
  我们需要做的事就是把这个调整的过程transition化，并加一个持续时间。
### Understanding the App
### Creating the App
- 就是先了解一下这个小app的整体架构
### Adding Animations
- 这里用自己写的CSS或者animate库的CSS都行。

## Section15
### Accessing Http via vue-resource - Setup
- 从terminal里安装东西时，--save就装到production dependency里了。
- 使用Vue.use来引入plugins。

## Section16
### Module Introduction
提到了SPA
### Setting up the VueJS Router (vue-router)
### Setting Up and Loading Routes
- 一般一个项目就一个router instance，不然会出问题，我们可以在main.js配置他，也可以新开一个file来配置。
- 配置好了routes后，我们把它传入本项目的router，再把router挂在在根组件上。
- router-view是组件切换的地方。
- Vue-router默认的router是hashtag的模式。可以更改。
### Understanding Routing Modes (Hash vs History)
- 浏览器默认行为，当我们在地址栏按enter键时，浏览器会向服务器发request。我们就想要避免这种默认行为，在本地handle url的变化。
- 每次改变url时，服务器永远返回给我们index.html，而我们在本地handle后面的东西（/user）。这种模式会让服务端的逻辑轻松很多。
- 这节再看看
### Navigating with Router Links
- <a>中的href也会给server发送request。VueJS的替代品是router-link
### Where am I? - Styling Active Links
- ？？？
- exact关键字解决一个两个按钮同时active的问题。因为Vue判断哪个link被匹配是通过url的，而home页面的url被user的包含，所以也被匹配，exact则取消
  这种包含关系。
### Navigating from Code (Imperative Navigation)
- 这节我们想通过JS转到某个页面。
- push?
### Setting Up Route Parameters
- 这节讲怎么通过url传参，关键符号是:.
### Fetching and Using Route Parameters
- 讲怎么获取和操做params，$route可以access router。
### Reacting to Changes in Route Parameters
- 这里结揭示一个问题，同url但是params不同的情况下，相应的component不会re-created。这就会造成某些数据不能即使更新。
- 这是因为我们并没有改动data本身。即我们把$route中的某个值赋给data的id，但我们只是传值而已。所以$route被改变时，组件不会re-render。
- $route前面加不加this是取决于他在script中的位置的。如果他在data里的话就加。如果他只是在watch中处于一个被监听的对象，就不加。
- 这里再次提示了computed和watch的不同，前者具有缓存特征，后者则是单纯的callBack function. 这里用computed或者watch都行。
### vue-router 2.2: Extract Route Params via "props"
- 这里提供的一种新特性是将$route的params绑在props上传下去，这样组件就会随着params的更变而re-render（三种方法）。
### Setting Up Child Routes (Nested Routes)
- 这里的lecturer指出了，实际开发的情况都不怎么会hardcode这些routes的跳转按钮的。
- 我们这节还要implement一些child route（nested route）。我们可以在routes那里配置他。关键字是children。注意child routes的path是遵守之前我们提到的路径定于规则的。
这里我们不加/，这节贴在/User的后面。
- 注意，对于nested routes。我们的router-view应该放在父组件的下面。
### Navigating to Nested Routes
- 这里有个点是我们不需要watch $route.params.id 的变化。因为无论如何我们都要退回到上一层，然后再次通过link来看各个component的输出。这种情况下，组件肯定是会被re-render的。
### Making Router Links more Dynamic
- 动态地使用$route.params.id作为url。
### A Better Way of Creating Links - With Named Routes
- 有的时候<router-link>的to path内容特别长的话，我们可以用name property来修饰它。
- 首先要在routes里设置好name。然后以object的property的形式传入router-link。同时，我们还可以传入params这些东西（params这块刚好填充router-link的to link中需要的参数）。 
### Using Query Parameters
- 这个Query的用法和params差不多。但是放在URL的最后面。是一个可选项。由.query提取，query是object的形式。
### Multiple Router Views (Named Router Views)
- 这里讲到了router-view如何根据name布局。
### Redirecting
- 单一地址重定向。
### Setting Up "Catch All" Routes / Wildcards
- *全地址速配符。
### Animating Route Transitions
- 要看做动画的那节。？？
### Passing the Hash Fragment
- #data的行为？default
- 这里我们可以通过:to property来把hash加入要转到的url里（hash关键字），但问题是我们并没有看到跳转的效果。
### Controlling the Scroll Behavior
- router有个专门管scroll position的函数。
- 你可以通过调整（return）坐标来跳到你下一个要到的页面的位置。
- 或者通过return selector来跳到某个元素的位置。
- 或者可以通过savedPosition跳到走之前的位置(浏览器前进后退的时候)。
### Protecting Routes with Guards
### Using the "beforeEnter" Guard
- 对于check user是否能跳转入的guards，我们有三种。
- 一是在main.js里放置beforeEach。这个method会check整个项目的每一次路由跳转。
- 在该method中，next函数是可以让这次跳转成功的关键。并且可以改变跳转的路径。如果next中放一个false的话，则表示不允许跳转。
- 第二点是在routes里，粒度更小，beforeEnter。
- 第三点是component level。vue-router有个类似lifecycle hook的函数，beforeRouteEnter()
- 在next()的外面，我们是无法access该instance的内容的（如this.link）。因为该instance还没有确认loaded。我们只能以这种方式access和操作他的property, 
  next(vm => vm.link); 在这个next()外面，我们可以做一些authentication check，看看用户是否有资格 next.
### Using the "beforeLeave" Guard
- 这节讲的是离开组件时的route检查。只有一个组件级的guard。beforeRouteLeave。毕竟全局的话，再check也已经来不及了。
### Loading Routes Lazily
- 一般情况下，我们用webpack打包出来的东西都是一个大的JS file。
- Vue的lazy loading就是语法比较奇怪一点。
- require的第一个参数是我们想要加载的file。第二个arrow function是一个异步函数。require本身是一个同步及时的import函数. 现在有新语法了，可以再研究一下。（待看）
- 当我们想要将多个bundle变成一个大bundle时，我们只要用一个名称把这些lazy loading绑起来就好。
## Section17
### Why a Different State Management May Be Needed
- eventBus会引出两个问题，一是emit大量的事件，而是我们很难追踪修改（谁改了谁）。

- 这节讲了怎么初始化一个store，以及怎么存取，操作他。
### Why a Centralized State Alone Won't Fix It
- 这里描述的问题是，当我们在不同的组件中对某个store中的property做同一个计算流程时，这种行为很损效能
### Understanding Getters
- 这个时候，getter就出来了。我们可以吧这个计算流程放到getter里，然后由getter return这个结果。
### Using Getters
我们可以有各种各样的getters
### Mapping Getters to Properties
- 这节指出一个问题，如果getters多的话，代码会变得非常冗余，这个时候我们就需要mapGetters。mapGettters返回的是一个object，刚好match computed。
- 那么这个时候问题又来了，mapGetters占用了整个computed，我们无法放置自己的computed进来。
- 那么我们就需要用ES6的...符号把mapGetters拆解开，并配合我们自己的computed properties。
- 新的问题又来了，compiler无法识别..., 这个时候我们再装个babel就好。
### Understanding Mutations
- 与getter对应的是mutation。当有一个component通过mutation改了某个property后，所有监听该property的组件都会收到更新消息。
### Using Mutations
- 像操作getter一样操作mutations。
### Why Mutations have to run Synchronously
- 现在要想办法异步更新state了。Mutation中只能执行同步的东西。
### How Actions improve Mutations
- 在component trigger和mutation更变store之间，我们会放一个actions来run异步代码。然后由actions来触发mutation。
### Using Actions
- 我们可以把在actions里传进来的object拆解掉。只用我们要用的部分。??
- 同步任务的话，还是直接使用mutation的mapMutation，异步的话才使用actions。
- actions有对应的mapActions。
### Mapping Actions to Methods
- 这节讲了怎么往actions和mutation里传参数。
### A Summary of Vuex
复习
### Two-Way-Binding (v-model) and Vuex
- 这节讲的是解决Vuex的two-way binding的问题。
- 我们想要对store里的property做two-way binding。
- 第一种办法是建立一个dispatch method。然后把input拆解成value（显示值）和input（监听值，并call method）。
- 第二种办法可以用v-model. 我们要在computed中以object的形式定义某个property。然后这个property有get和set两个method。
get就是取值的那个menthod，set则是设置值的method。用到这种method和property形式的情况极其少见。
### Improving Folder Structures
### Modularizing the State Management
- 这里指出了，对于counter，他的getter，actions等操作是一套，我们可以把它放到一个file中。对于value，他也有自己的一套东西。我们可以把他的也独立出来。
- 用modules关键字在store中引入。
### Using Separate Files
- 这里又提出了一个新的情况。当某个复杂的actions或getter属于不同的module时，我们该怎么把它提取出来。
- 新的import方法。
### Using Namespaces to Avoid Naming Problems
- 这里提到了众多actions，getters名字重复的问题。
- 我们通常会把它们的命名统一到一个file里。这样如果file中export的名字冲突的话，马上就会报错。
- 注意output的名字要全大写。
### Auto-namespacing with Vuex 2.1
- 这里提到了自动给予不同的module不同的命名空间的事，还不是太懂，可以再看看。？
## Section22
### Project Setup
- 设置了一下firebase。
### Axios Setup
- 设置了一下Axios
### Sending a POST Request
- post, if we plan on essentially creating an array of data on the backend, put if we just want to write one object.？
- 一般来说axios.post接受两个参数，url + 发送的内容。
- axios will automatically stringfy data.
### Sending a GET Request
### Accessing & Using Response Data
讲的是去了data后怎么操作
### Setting a Global Request Configuration
- 这节讲的是怎么为项目的axios配置一些全局的设置。比如默认url，默认headers这些的。
- 如果我们要配置的东西少的话，我们就直接在main.js里配置，多的话就另开一个新文件。
### Using Interceptors
- 像是项目的http过滤器，我们可以在发出和接收的时候做一些配置，弄弄header什么的。
- 记住一定要return。
### Custom Axios Instances
- 如果你的项目只和一个url进行HTTP交互的话，那么我们用一个axios instance就足够了。如果你要和多个url进行互动，那么就可以create多个axios的
  instance，并自己进行配置, 包括baseURL，header什么的。
### Understanding "Centralized State"
- Vuex就和Redux差不多，也是在一个separate file中维护一个全局变量（store），然后各个component修改或读取他。
## Section 25
### Module Introduction
- vue create = vue init. 可以有preset和Custom config（客制化配置）两种模式。
- 在旧版Vue中，一旦你配置好项目后，就很难更改他（得去webpack的配置文件里改）。但是CLI3后的Vue可以轻松做到。（Vue add @vue/plugin-name）
### Creating a Project
- vue init在装了cli3后失效。vue create. 然后一顿设置。
- 在user folder里，我们可以看到一个.userc的隐藏文件。这个文件里我们可以看到我们之前对Vue做的种种设置。
### Analyzing the Created Project
- package.json的三块内容，dependency，devDependency，script。
- 在Vue-cli3之后的版本，webpack.config file不见了。
- 最后还有一个browserlist内容，这块指明你的web项目所服务的浏览器范围。
- 后面有些内容没记？？
### Using Plugins
- 插件（plugins）要遵循一些命名规则。
- vue的plugin通常是 vue-cli-pluin-名字。官方的前面都加一个@符号。
- 得益于这个命名标准，我们添加plugin的时候就vue add plugin名字就好。
### CSS Pre-Processors
- 现场演示了一下怎么加CSS preprocessor的。
### Environment Variables
- 环境变量通常是整个项目都要用得到的。比如aip key，url，对于test环境或者其他环境。
- 我们通常把这些环境变量存在目录的最上级（和src同一级）。以.env命名这个文件。Vue会自动读取他。
- 在使用这些变量的时候，我们在JS code里要加process.env.xxxx这样。
- 对于三种不同的模式（mode为development，production，test），我们可以用不同的file来定义这些环境变量. 只要在.env后面加.development等就行。
- 变量命名也有讲究，必须要以VUE_APP_开头。不然Vue识别不了。
### Building the Project
讲了以不同的的mode build项目
### Instant Prototyping
- 先讲了一下我们可以让vue-cli-service全局化，但是要-g安装。这样我们就可以在文件夹外build或dev东西了。
- 另一个是instance prototyping. 前一个功能可以让我们在在任意一个位置run vue-cli-service，那么我们可以直接vue run xxx.vue，直接在浏览器里看这个组件。
- 当然，如果这个组件对其他组件有很强的依赖的话，会产生麻烦。
### Different Build Targets
- 三种build的模式，甚至可以进行组件级build，目前用不太到。？？
### Using the "Old" CLI Templates (vue init)
- 这节讲的是怎么让Vue2的init指令复活。我们只需要在全局中装@vue/init-cli就好。剩下的操作和Vue2一摸一样。
### Using the Graphical User Interface (GUI)
- 图形化界面，太屌了。
### Alternative Lazy Loading Syntax
- 就是更变语法的那个点。

## 其他
### 什么会触发Vue组件的re-render
- data属性的更变会引发re-render，props更新（本质上是data的更新）。
- 注意Vue无法动态地追踪数组和对象的变动（比如通过index改变数组内容等）。文档里有相应的解决方案。
### Vue.use与Vue.component
- Vue.component就是注册全局组件。而Vue.use则是注册插件。插件（plugin）本质上是一个对象。其中含有一个install方法，而Vue.use就会调用这个方法。
- 这个方法中不仅有注册组件（Vue.component），还有Vue.directive(), Vue.mixin()等。可以说是包含了Vue.component。


Vuex真有dispatch吗？

Vuex也不能trace啊？























