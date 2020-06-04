## CSS

### 1. css 的引入方式

- 内联样式

- 文档样式
- 外部样式

### 2. css文件编码和import引入

- 在css文件中使用@charset指定文件编码,一般都是UTF-8

- 在css文件中使用@import  url(./base.css)方式引入其他样式表,@import的效率比link元素效率低

### 3. 统配选择器的使用

- 所有元素
- 一般用来给所有元素作一些通用性的设置
- 比如内边距、外边距
- 效率比较 低，尽量不用

### 4. 元素选择器、class选择器、id选择器

1. 元素选择器
2. class选择器
3. id选择器

### 5. 常用的css属性

- color: 前景色(文字颜色)
- font-size:文字大小
- background-color:背景色
- width:宽度
- height:高度

### 6. font

- font是一个缩写属性
- font-style font-variant font-weight font-size/line-height font-family

div {

​	font: italic small-caps 700 20px/40px "宋体";

}

- [ ] font-style、font-variant、font-weight顺序可以调换，也可以省略
- [ ] /line-height可以省略,如果不省略,必须跟在font-size后面
- [ ] font-size、font-family不可以调换顺序，不可以省略



### 7. 属性选择器

..

### 8. 后代选择器 子选择器 兄弟选择器

- div span

div 下面直接和间接子元素

- div>span

div 下面的直接子元素,不包括间接子元素 (> 前后可以有空格)

- div+p

div后面紧挨着的p元素(div、p必须是兄弟关系)

- div~p

div后面的p元素(div、p元素必须是兄弟关系)

### 9. 交集选择器 并集选择器

- div.one

同时符合2个条件的元素: div元素 class值有one

- div.one[title="test"]

所有同时符合3个条件的元素: div元素、class值有one、title属性值等于test

- div, .one, [title="test"]

所有的div元素 + 所有class值有one的元素 + 所有title属性值等于test的元素

### 10. 伪类

1. #### 分类

   1. 动态伪类

      :link :visited :hover :active :focus

   2. 目标伪类

      :target

   3. 语言伪类

      :lang()

   4. 元素状态伪类

      :enabled :disabled :checked

   5. 结构伪类

      :nth-child()、:nth-last-child()、:nth-of-type()、:nth-last-of-type()、

      :first-child、:last-child、:first-of-type、:last-of-type

      :root、:only-child、:only-of-type、:empty

   6. 否定伪类

      :not()

   7. 

2. #### 动态伪类

   a:link 未访问的链接

   a:visited 已访问的链接

   a:hover 鼠标挪动到链接上

   a:active 激活的链接()

   :hover必须放在:link和:viested后面才能完全生效

   :active必须放在:hover后面才能完全生效

   :focus 指当前拥有输入焦点的元素

3. #### 结构伪类

   - :nth-child(1) :nth-child(n) :nth-child(2n) :nth-child-child(2n+1) :nth-child(even) :nth-child(odd) n是自然数, 是父元素中的第几个元素
   - :nth-last-child 倒着数
   - 


### 11. 伪元素

常用的伪元素

- :first-line ::first-line
- :first-letter ::first-letter
- :before ::before
- :after ::after

### 12. CSS优先级

!important (10000)> 内联样式 (1000)> id选择器 (100)> 类选择器、属性选择器、伪类 (10)> 元素选择器、伪元素 (1)> 通配符 (0)

### 13. 列表元素

- ol 

  有序元素列表，直接子元素是li

- ul

  无序元素列表，直接子元素是li

- dt dl dd

  定义列表，直接子元素是dl dd

- 列表的css属性

  - list-style-type

    设置li元素前面的标记样式

    通常设置为none，同时设置margin:0,padding:0

  - list-style-image

    设置某张图片为li元素前面的标记，会覆盖list-style-type的设置

  - list-style-position

    设置li元素前面标记的位置，可以去outside、inside2个值

  - list-style 

    type、image、position的缩写属性

  他们都可以继承，所以设置为ol、ul元素，默认也会应用到li元素

### 13. 表格

border-collapse 设置 collapse 边框合并

### 14. margin

##### 上下margin传递

- margin-top传递

  如果块级元素的顶部线和父元素的顶部线重叠，那么这个块级元素的margin-top值会传递给父元素

- magin-bottom传递

  如果块级元素的底部线和父元素的底部线重叠，并且父元素的高度是auto，那么这个块级元素的margin-bottom值会传递给父元素

- 如何防止出现传递问题

  - 给父元素设置padding-top\padding-bottom

  - 给父元素设置border

  - 触发BFC：设置overflow为auto/hidden

  - 如何触发BFC（BFC可以理解为一个结界）

    - 浮动可以触发

    - 设置一个元素的overflow为非visible

      auto hidden scorll

- 建议

  - margin一般是用来设置兄弟元素之间的间距

  - padding一般是用来设置父子元素之间的间距

##### 上下margin折叠

- 垂直方向上相邻的2个margin（margin-top、margin-bottom）有可能会合并为1个margin，这种现象叫做collapse（折叠）
- 水平方向上的margin（margin-left、margin-right）永远不会collapse
- 折叠后最终值的计算规则
  - 两个值进行比较，取较大的值
- 如何防止margin collapse
  - 只设置其中一个元素的margin

### 15. 定位

##### 15.1 position

###### 利用position可以对元素进行定位,常用取值有4个

- static：静态定位
- relative：相对定位
- absolute：绝对定位(判断父元素是否是非static定位，否则一直向上查找父元素)
- flexd：固定定位（直接相对于浏览器视口定位）

###### 脱标元素的特点

脱离标准流的元素:position: fixed/absolute,float

-  可以随意设置宽高
- 宽高默认由内容决定
- 不再受标准流的约束
- 不再给父元素汇报宽高数据

###### 绝对定位技巧

​	绝对定位元素

​	position值为absolute或者fixed的元素

​	对于绝对定位元素来说

​	定位参考对象的宽度 = left + right + margin-left + magin-right + 绝对定位元素实际占用宽度

​	定位参考对象的高度 = top + bottom + margin-top + margin-bottom + 绝对定位元素实际占用高度

​	如果希望绝对定位元素的宽高和定位参考对象一样，可以给绝对定位元素设置以下属性：left:0、right：0、top：0、bottom：0、margin：0

​	如果希望绝对定位元素在定位参考对象中居中显示，可以给绝对定位元素设置以下属性：left：0、right：0、top：0、bottom：0、margin：auto，另外还必须设置具体的宽高

### 16. 浮动

###### 浮动规则1

元素一旦浮动后

- 脱离标准流
- 朝着向左或向右方向移动，直到自己的边界紧贴着包含块（一般是父元素）或者其他 浮动元素的边界为止
- 定位元素会层叠到浮动元素的上面： 标准流元素->浮动元素->定位元素

###### 浮动规则2

- 浮动元素不能与行内级元素层叠，行内级内容将会被浮动元素推出
  - 比如行内级元素、inline-block元素、块级元素的文字内容

###### 浮动规则3

行内级元素、inline-block元素浮动后，其顶部将与所在行的顶部对齐

###### 浮动规则4

如果元素向左（右）浮动，浮动元素的左（右）边界不能超出包含块的左（右）边界

###### 浮动规则5

浮动元素之间不能进行层叠

如果一个浮动元素，另一个浮动元素已经在那个位置了，后浮动的元素将紧贴着前一个浮动元素（左浮找左浮，右浮找右浮）

如果水平方向剩余的空间不够显示浮动元素，浮动元素将向下移动，直到有充足的空间为止

浮动规则6

浮动元素的顶端不能超过包含块的顶端，也不能超过之前所有浮动元素的顶端

###### 浮动存在的问题

- 由于浮动元素脱离了标注流，变成了脱标元素，所以不再向父元素汇报高度。父元素计算总高度是，就不会计算子元素的高度，导致高度坍塌的问题

- 解决父元素高度坍塌问题的过程，一般叫做清浮动（清理浮动、清除浮动）

- 清浮动的目的

  让父元素计算总高度的时候，把浮动子元素的高度算进去

- 清浮动的常见方法

  - 给父元素设置固定高度

    扩展性不好（不推荐）

  - 在父元素最后增加一个空的块级子元素，并且让它设置clear:both

    会增加很多无意义的空标签，维护麻烦

    违反了结构与样式分离的原则（不推荐）

  - 在父元素最后增加一个br标签：<br clear="all">

    会增加很多无意义的空标签，维护麻烦

    违反了结构与样式分离的原则（不推荐）

  - .clear-fix::after {

    ​	content: "",

    ​	clear:both;

    ​	display:block;

    ​	height: 0;/*兼容旧浏览器*/

    ​	visibility:hidden；/*兼容旧浏览器*/

    }

    .clear-fix {

    ​	*zoom: 1;/*兼容ie6~ie7*/

    }

### 17. img在div中的垂直居中

img {

​	position:relative;

​	top:50%;

​	transform:translate(0,-50%)

}