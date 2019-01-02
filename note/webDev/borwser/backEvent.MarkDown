# 监听浏览器后退事件（手机通过JS监听返回按钮事件）

在开发过程中我们经常遇到需要自定义返回按钮跳转到指定位置，而并非按照历史纪录一级一级向后跳转

本文将详细介绍如何利用浏览器自带的popstate事件监听浏览器返回事件，并跳转到指定位置

## popstate

The popstate event is fired when the active history entry changes. If the history entry being activated was created by a call to history.pushState() or was affected by a call to history.replaceState(), the popstate event's state property contains a copy of the history entry's state object.

Note that just calling history.pushState() or history.replaceState() won't trigger a popstate event. The popstate event will be triggered by doing a browser action such as a click on the back or forward button (or calling history.back() or history.forward() in JavaScript).

Browsers tend to handle the popstate event differently on page load. Chrome (prior to v34) and Safari always emit a popstate event on page load, but Firefox doesn't.

上面这段内容是MDN Web docs 对popState事件的说明，翻译过来为：

当活动历史记录条目更改时，将触发popstate事件。如果被激活的历史记录条目是通过对history.pushState（）的调用创建的，或者受到对history.replaceState（）的调用的影响，popstate事件的state属性包含历史条目的状态对象的副本。

需要注意的是调用history.pushState()或history.replaceState()不会触发popstate事件。只有在做出浏览器动作时，才会触发该事件，如用户点击浏览器的回退按钮（或者在Javascript代码中调用history.back()）

不同的浏览器在加载页面时处理popstate事件的形式存在差异。页面加载时Chrome和Safari通常会触发(emit )popstate事件，但Firefox则不会。

总结来说：

popstate事件只有浏览器返回按钮以及history.back()事件更改历史记录时触发，hhistory.pushState()或history.replaceState()事件不会触发popstate事件

## 使用方法

```javascript
  if (window.history && window.history.pushState) {
    window.onpopstate = function() {
      //后退按钮触发事件
    }
  }
```

### Vue实例