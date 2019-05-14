# Flex布局

网页布局（layout）是CSS的一个重点应用。

布局的传统解决方案，基于盒状模型，依赖 display属性 + position属性 +float属性。针对于某些特殊布局就显得非常不方便，例如，垂直居中就不容易实现。

2009年，W3C提出了一种新的方案—-Flex布局，可以简便、完整、响应式地实现各种页面布局。目前，它已经得到了所有新版主流浏览器的支持，这意味着，现在就能很安全地使用这项功能。

## 特点
1.任何元素都可以指定为flex布局

2.设置flex布局后，子元素float、clear和vertical-align属性将失效。

## flex属性

1.[flex-direction](#flex-direction)

2.[flex-wrap](#flex-wrap)

3.[flex-flow](#flex-flow)

4.[justify-content](#justify-content)

5.[align-items](#align-items)

6.[align-content](#align-content)

## flex子元素属性

1.[order](#order)

2.[flex-grow](#flex-grow)

3.[flex-shrink](#flex-shrink)

4.[flex-basis](#flex-basis)

5.[flex](#flex)

6.[align-self](#align-self)

### flex-direction

决定flex布局排版方向，默认为横向排版

flex-direction: [row](#row) | [row-reverse](#row-reverse) | [column](#column) | [column-reverse](#column-reverse);

```html
	<div class="flex">
		<div>1</div>
		<div>2</div>
		<div>3</div>
		<div>4</div>
		<div>5</div>
		<div>6</div>
		<div>7</div>
		<div>8</div>
		<div>9</div>
	</div>
```

```css
.flex{
  display: flex;
  width: 360px;
  height: 360px;
  flex-wrap: wrap;
  justify-content: space-between;
}
.flex>div{
  display: flex;
  box-sizing: border-box;
  width: 96px;
  height: 96px;
  justify-content: center;
  align-items: center;
  font-size: 35px;
  border: 1px solid red;
}
```
#### row

(默认值)横向排版，起点为左上角

```css
.flex{
  flex-direction: row;
}
```

![](http://www.sides.top/public/img/flex.direction.row.png)

#### row-reverse

横向排版，起点为右上角

```css
.flex{
  flex-direction: row-reverse;
}
```

![](http://www.sides.top/public/img/flex.direction.row.reverse.png)

#### column

竖向排版，起点为左上角

```css
.flex{
  flex-direction: column;
}
```

![](http://www.sides.top/public/img/flex.direction.column.png)

#### column-reverse

竖向排版，起点为左下角

```css
.flex{
  flex-direction: column-reverse;
}
```

![](http://www.sides.top/public/img/flex.direction.column.reverse.png)

### flex-wrap

决定flex超出主方向布局位置时是否换行，以及换行方式

flex: [nowrap](#nowrap) | [wrap](#wrap) | [wrap-reverse](#wrap-reverse)

```html
	<div class="flex">
		<div>1</div>
		<div>2</div>
		<div>3</div>
		<div>4</div>
		<div>5</div>
		<div>6</div>
		<div>7</div>
		<div>8</div>
		<div>9</div>
	</div>
```

```css
.flex{
  display: flex;
  width: 360px;
  height: 360px;
  flex-direction: row;
  justify-content: space-between;
}
.flex>div{
  display: flex;
  box-sizing: border-box;
  width: 96px;
  height: 96px;
  justify-content: center;
  align-items: center;
  font-size: 35px;
  border: 1px solid red;
}
```

#### nowrap

默认值，不换行

```css
.flex{
  flex-wrap: nowrap;
}
```

![](http://www.sides.top/public/img/flex.wrap.nowrap.png)

#### wrap

换行，常规排版

```css
.flex{
  flex-wrap: wrap;
}
```

![](http://www.sides.top/public/img/flex.wrap.wrap.png)


#### wrap-reverse

反向换行，从最下方往上方排版

```css
.flex{
  flex-wrap: wrap-reverse;
}
```

![](http://www.sides.top/public/img/flex.wrap.wrap.reverse.png)

### flex-flow

flex-flow属性是[flex-direction](#flex-direction)属性和[flex-wrap](#flex-wrap)属性的简写形式，默认值为row nowrap。

```css
flex-flow: <flex-direction> <flex-wrap>
```

### justify-content

决定flex布局在主轴方向上的排版方法

justify-content: [flex-start](#flex-start) | [flex-end](#flex-end) | [center](#center) | [space-around](#space-around) | [space-between](#space-between)

```html
	<div class="flex">
		<div>1</div>
		<div>2</div>
		<div>3</div>
		<div>4</div>
		<div>5</div>
		<div>6</div>
		<div>7</div>
		<div>8</div>
		<div>9</div>
	</div>
```

```css
.flex{
  display: flex;
  border:1px solid blue;
  width: 360px;
  height: 360px;
  flex-wrap: wrap;
  flex-direction: row;
}
.flex>div{
  display: flex;
  box-sizing: border-box;
  width: 96px;
  height: 96px;
  justify-content: center;
  align-items: center;
  font-size: 35px;
  border: 1px solid red;
}
```
#### flex-start

默认值，沿主轴方向依次排列，无特殊样式(左对齐)

```css
.flex{
  justify-content: flex-start;
}
```

![](http://www.sides.top/public/img/justify.content.flex.start.png)

#### flex-end

沿主轴方向反向依次排列，无特殊样式(右对齐)

```css
.flex{
  justify-content: flex-end;
}
```

![](http://www.sides.top/public/img/justify.content.flex.end.png)

#### center

主轴方向居中排列，无特殊样式(居中)

```css
.flex{
  justify-content: center;
}
```

![](http://www.sides.top/public/img/justify.content.center.png)

#### space-around

主轴方向依次排列，子元素与子元素见自动生成等宽间隔，子元素与子元素的间隔子元素与父元素边框之间的间隔的两倍

```css
.flex{
  justify-content: space-around;
}
```

![](http://www.sides.top/public/img/justify.content.space.around.png)

#### space-between

主轴方向依次排列，两端无间隔，子元素与子元素见自动生成等宽间隔

```css
.flex{
  justify-content: space-between;
}
```

![](http://www.sides.top/public/img/justify.content.space.between.png)

### align-items

align-items:  flex-start | flex-end | center | [baseline](#baseline) | [stretch](#stretch)

针对子元素在单一主轴上（一行上）交叉轴的排版方式

flex-start,flex-end,center规则和[justify-content](#justify-content)相同值的规则一样，将主轴替换为交叉轴即可

```html
	<div class="flex">
		<div style="font-size:22px;">1</div>
		<div>2</div>
		<div>3</div>
		<div>4</div>
		<div style="font-size:22px;">5</div>
		<div>6</div>
		<div>7</div>
		<div>8</div>
		<div style="font-size:22px;height:auto;">9</div>
	</div>
```

```css
.flex{
  display: flex;
  border:1px solid blue;
  width: 360px;
  height: 360px;
  flex-wrap: wrap;
  flex-direction: row;
  justify-content: space-around;
}
.flex>div{
  display: flex;
  box-sizing: border-box;
  width: 96px;
  height: 96px;
  justify-content: center;
  align-items: center;
  font-size: 66px;
  border: 1px solid red;
}
```

#### baseline

```css
.flex{
  align-items: baseline;
}
```

![](http://www.sides.top/public/img/align.items.baseline.png)

#### stretch

```css
.flex{
  align-items: stretch;
}
```

![](http://www.sides.top/public/img/align.items.stretch.png)

### align-content

规则和[justify-content](#justify-content)相同值的规则一样，将主轴替换为交叉轴即可,在单一主轴（项目只有一行）上该属性无效

## flex子元素属性

作用于flex项目下的直接子元素

### order

order属性定义项目的排列顺序。数值越小，排列越靠前，默认为0。

```css
.item{
  order: <integer>;
}
```

### flex-grow

flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。

将剩余空间等比缩放大小，分配给当前指定项目

如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。

```css
.item{
  flex-grow:<float>;
}
```

### flex-shrink

flex-shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。

如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小。

负值对该属性无效。

```css
.item{
  flex-shrink:<float>;
}
```

### flex-basis

重定义项目大小，默认值auto，即项目本身大小

它可以设为跟width或height属性一样的值（比如350px），则项目将占据固定空间。

自我感觉该属性用处不大

### flex

flex属性是[flex-grow](#flex-grow)属性和[flex-shrink](#flex-shrink)属性和[flex-basis](#flex-basis)属性的简写方式

```css
flex: <flex-grow> <flex-shrink> <flex-basis>
```

### align-self

align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。

align-self: auto | flex-start | flex-end | center | baseline | stretch;

## flex css 实例

```css
.flex{
  display: flex;
  flex-flow: column nowrap;
  justify-content: flex-start;
  align-items: center;
  align-content: center;
  position: relative;
}
.flex.row{
  flex-flow: row nowrap;
}
.flex.wrap{
  flex-wrap: wrap;
}
.flex>.auto{
  width: 100%;
  flex-grow: 1;
  position: relative;
}
.row>.auto{
  width: auto;
  height: 100%;
}
.absFull{ /*针对部分浏览器使用.auto样式导致页面样式错乱*/
  position: absolute;
  top:0;
  left:0;
  right: 0;
  bottom: 0;
  overflow: auto;
}
```
