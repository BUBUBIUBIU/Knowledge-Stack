## Section8
### Why CSS Grid: A Whole New Mindset
- Grids擅长二维布局，flexbox擅长一维。
- 一些术语，grid container，grid items, grid line, gutter, grid track, gird area, grid cell
### Quick Setup for This Section
- 简单的做一些配置
### Creating Our First Grid
- 简单的讲一个矩形分成6份。通过grid的container的一些properties。
### Getting Familiar with the fr Unit
- 有的时候我们要定义的条数太多了，我们可以用repeat这个function来做。
- fr可以占满所有空间, 使用百分比作为track长度的时候，是不会考虑到gap的。
### Positioning Grid Items
- 这节讲的是怎么通过特定的CSS properties来安排块级元素的位置。
- 当该元素被安排后，剩下的元素会依旧按照先后顺序排列，就像该元素被移出文档流一样。
### Spanning Grid Items
- 块级元素的占位有显示和隐式之分。
- grid-column里的 -1 指的是到column或者row的尽头（当你不知道该占多少格时使用）。span指的是要占据多少格。
### Naming Grid Lines
- 之前都是以行号为边界，这次我们可以把每一行做一个命名（一行个已有多个名字），然后以这些名字来分行。
- 如果你想在repeat方法里加名字的话，不用担心line重名的问题，grid会自动给他们编号。
### Naming Grid Areas
- 这节用的是area功能，他的概念有点像用string来布局，然后用安排各个元素填入这些布局。
- 这种布局方式适合较小的layout。
### Implicit Grids vs. Explicit Grids
- 这节讲的是隐式的grid布局。这种情况会发生在元素多余grid cells的时候。
- 我们可以设置多余的元素是以column的形式排列还是以row的形式排列。并且为他们加上style。
### Aligning Grid Items
- 这节讲的是justify系列和align-item系列。grid相较于flex多了一个维度。注意align-self会覆盖align-items的东西。
### Aligning Tracks
- 这节讲的是align整条track。
- justify管的是横向的移动，align管的是纵向的移动。
- 有的时候元素为了遵循HTML的元素排列算法，会生成一个空洞，这个时候可以用dense关键字去填补这些空洞。
### Using min-content, max-content and the minmax() function
- max-content关键字放的位置和1fr一样。它的效果是可以让空间缩小到刚好放下内容的程度，并且不会break line。
- min-content则会break line。长度取决于最长的那个单词(最小宽度值最大的那个元素的宽度值)。
- minmax则是一个控制某一个row或者columns的属性，我们可以设置上下限。
- 这里还提到的一个点就是，当长度或宽度设为1fr时，平时他们都是相等长度的，但是下限是能容纳自己cell里的内容。所以在view缩得很小的时候，某些columns
或者rows的长度是不一样的。
### Responsive Layouts with auto-fit and auto-fill
- auto-fit和auto-fill会在很大程度上取代media query。
- auto-fit是根据repeat里的宽度给你生成相应数量的div，但是最后那几个宽/长度为0. auto-fill则是处于填满状态。
- auto-fit还得搭配minmax和auto-rows这些。

