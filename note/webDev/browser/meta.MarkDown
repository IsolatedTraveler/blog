# <meta> 元素可提供有关页面的元信息

<meta> 标签位于文档的头部，不包含任何内容。<meta> 标签的属性定义了与文档相关联的名称/值对。

## 特点

<meta> 标签永远位于 head 元素内部。

元数据总是以名称/值的形式被成对传递的。

## 使用方法

## 用途举例

### 手机屏幕自适应（viewport）

<meta name="viewport" content="width=device-width,initial-scale=1.0">

| 属性名 | 取值 | 描述 |
| :------ | :------ | :------ |
| width |	正整数 或 device-width |	定义视口的宽度，单位为像素 |
| height | 正整数 或 device-height |	设置layout viewport  的高度，这个属性对我们并不重要，很少使用 |
| initial-scale |	[0.0-10.0] |	设置页面的初始缩放值，为一个数字，可以带小数 |
| minimum-scale |	[0.0-10.0] |	允许用户的最小缩放值，为一个数字，可以带小数 |
| maximum-scale |	[0.0-10.0] |	允许用户的最大缩放值，为一个数字，可以带小数 |
| user-scalable |	yes/no |	是否允许用户进行缩放，值为"no"或"yes", no 代表不允许，yes代表允许 |

