# Flex布局

网页布局（layout）是CSS的一个重点应用。

布局的传统解决方案，基于[盒状模型](./box.MarkDown)，依赖 [display](./display.MarkDown)属性 + [position](./positon.MarkDown)属性 +[ float](./float.MarkDown)属性。针对于某些特殊布局就显得非常不方便，例如，垂直居中就不容易实现。

2009年，W3C提出了一种新的方案—-Flex布局，可以简便、完整、响应式地实现各种页面布局。目前，它已经得到了所有新版主流浏览器的支持，这意味着，现在就能很安全地使用这项功能。

## 特点
1.任何元素都可以指定为flex布局

2.设置flex布局后，子元素[float](./float.MarkDown)、[clear](./clear.MarkDown)和[vertical-align](./verticalAlign.MarkDown)属性将失效。

## flex属性

1.[flex-direction](#flex-direction)

2.[flex-wrap](#flex-wrap)

3.[flex-flow](#flex-flow)

4.[justify-content](#justify-content)

5.[align-items](#align-items)

6.[align-content](#align-content)

## [flex子元素属性](#flex子元素属性)

1.[order](#order)

2.[flex-grow](#flex-grow)

3.[flex-shrink](#flex-shrink)

4.[flex-basis](#flex-basis)

5.[flex](#flex)

6.[align-self](#align-self)

### flex-direction

决定flex布局排版方向，默认为横向排版

flex-direction: [row](#row) | [row-reverse](#row-reverse) | [column](#column) | [column-reverse](column-reverse);

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

## flex css 实例

```css
.flex{
  display: flex;
  flex-flow: column nowrap;
  justify-content: flex-start;
  align-items: center;
  align-content: center;
}
.flex.row{
  flex-flow: row nowrap;
}
.flex.wrap{
  flex-wrap: wrap;
}
.flex>div{
  width: 100%;
  position: relative;
}
.row>div{
  width: auto;
  height: 100%;
}
.flex>.auto{
  flex-grow: 1;
}
```