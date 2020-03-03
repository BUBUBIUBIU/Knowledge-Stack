## Property
### Box Model (box-sizing property)
content + padding + border + margin;  
content-box: full width = width(content) + padding + border;  
border-box: width = content + padding + border;
### display property
- block  
- inline  
- inline-block  
- flex-box
### flex-box
#### container
- flex-direction: 行还是列，正序排还是倒序排  
- flex-wrap：分不分行  
- align-items：让子item沿cross-axis为准排列  
- justify-content：items沿main-axis排列  
- align-content：让子item沿cross-axis为准排列（多行）
#### item
flex = grow + shrink + basis  
align-self：
### position property
relative：默认  
absolute：跟着荧幕定位移动，会随参照对象元素的高度和宽度变化而变化  
fixed：固定在网页中的某个位置
## SASS
### Variable
### Mixin
A piece of reusable CSS code, can get variable as argument.
### function
### nesting structure
& mark
##Responsive design
### rm与rem

## CSS居中
1 margin: 0 auto (使用这个方法前要先设定width property，因为margin的参照物是width)  
2 text-align: center. 加在父元素上，子元素居中  
3 position: absolute + top: 50% left: 50% + transform(-50%, -50%)  
4 absolute + 上下左右: 0 + margin: 0  
5 flex container + justify-content: center + align-items: center
## CSS梯形
1 div + 4条border设置好  
2 clip path: polygon(参数是4各点，可用百分号表示)

