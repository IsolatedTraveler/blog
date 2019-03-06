# 屏幕自适应

## 介绍
 
解决移动端复杂的显示屏幕导致网页呈现不同的显示问题

## 方法

### <meta>

详情参考[<meta>标签](./../browser/meta.MarkDown)

```html
<meta name="viewport" content="width=device-width,initial-scale=1.0">
```

| 属性名 | 取值 | 描述 |
| :------ | :------ | :------ |
| width |	正整数 或 device-width |	定义视口的宽度，单位为像素 |
| height | 正整数 或 device-height |	设置layout viewport  的高度，这个属性对我们并不重要，很少使用 |
| initial-scale |	[0.0-10.0] |	设置页面的初始缩放值，为一个数字，可以带小数 |
| minimum-scale |	[0.0-10.0] |	允许用户的最小缩放值，为一个数字，可以带小数 |
| maximum-scale |	[0.0-10.0] |	允许用户的最大缩放值，为一个数字，可以带小数 |
| user-scalable |	yes/no |	是否允许用户进行缩放，值为"no"或"yes", no 代表不允许，yes代表允许 |

针对多屏幕版本使用，通过js一次性定义

```js
<script type="text/javascript">
  ((doc,win) => {
    var width1 = 320, userScalable = 'yes', maximumScale = 2 // 设置最优显示屏幕宽度、是否允许缩放操作['yes','no']、设置基础放大倍数
    var body = doc.documentElement,width = body.clientWidth
    var recalc = () => {
      var initialScale = width1 / width
      document.getElementsByTagName('meta').viewport.content = 'width=device-width, initial-scale=' + initialScale + ', maximum-scale=' + (maximumScale * initialScale) + ', user-scalable=' + userScalable
    }
    recalc()
    win.addEventListener('orientationchange' in window ? 'orientationchange' : 'resize', recalc, false);
  })(document,window)
</script>
```

### css3 rem

rem是CSS3新增的一个相对单位，使用rem为元素设定字体大小时，是相对大小，但相对的只是HTML根元素。通过它既可以做到只修改根元素就成比例地调整所有字体大小，又可以避免字体大小逐层复合的连锁反应。

目前，除了IE8及更早版本外，所有浏览器均已支持rem。对于不支持它的浏览器多写一个绝对单位的声明。这些浏览器会忽略用rem设定的字体大小。

默认html的font-size是16px，即1rem=16px，如果某div宽度为32px你可以设为2rem。

具体不同屏幕下的规则定义，即基数的定义方式：可以通过CSS定义，不同宽度范围里定义不同的基数值(结合媒体查询)，当然也可以通过js一次定义。方法如下：

```javaScript
<script type="text/javascript">
  ((doc,win) => {
    var width = 2208 /** 设置最优显示宽度 */, recalc = (a) => {
      var initialScale = win.screen.availWidth / width, fontSize = initialScale.toFixed(6) * 100
      doc.documentElement.style.fontSize = fontSize + 'px'
    }
    recalc()
    win['orientationchange' in window ? 'onorientationchange' : 'onresize'] = recalc
  })(document,window)
</script>
```

### 使用媒体查询

媒体查询也是css3的方法，其功能就是为不同的媒体设置不同的css样式，这里的“媒体”包括页面尺寸，设备屏幕尺寸等。

例如：如果浏览器窗口小于 500px, 背景将变为浅蓝色：

```css
@media only screen and (max-width: 500px) {
  body {
    background-color: lightblue;
  }
}
```

### 使用百分比

详情参考css->position 布局