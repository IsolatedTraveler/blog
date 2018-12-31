# Flex布局

网页布局（layout）是CSS的一个重点应用。

布局的传统解决方案，基于[盒状模型](./box.MarkDown)，依赖 [display](./display.MarkDown)属性 + [position](./positon.MarkDown)属性 +[ float](./float.MarkDown)属性。针对于某些特殊布局就显得非常不方便，例如，垂直居中就不容易实现。

2009年，W3C提出了一种新的方案—-Flex布局，可以简便、完整、响应式地实现各种页面布局。目前，它已经得到了所有新版主流浏览器的支持，这意味着，现在就能很安全地使用这项功能。

## 特点
1.任何元素都可以指定为flex布局

2.设置flex布局后，子元素[float](./float.MarkDown)、[clear](./clear.MarkDown)和[vertical-align](./verticalAlign.MarkDown)属性将失效。

## flex属性

1.flex-direction
2.flex-wrap
3.flex-flow
4.justify-content
5.align-items
6.align-content