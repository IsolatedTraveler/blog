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

在浏览器开发中，实际上我们必不能真正的监听到浏览器自带的后退按钮事件，移动开发中，不同过封装程序，我们也不能单纯的通过js代码监听到手机的后退按钮事件。此处我们通过监听浏览器history的改变结合[vuex-store](./../vuex/store.MarkDown)实现模拟监听浏览器后退按钮的效果

1.在store中定义浏览器后退事件(用于判断当前后退事件是否有其他操作)

```javaScript
import Vuex from 'vuex'
import Vue from 'vue'
Vue.use(Vuex)
var state = {
  backEvent: null
},
getters = {
  backEvent(state,getters){
    return state.backEvent
  }
},
mutations = {
  backEvent(state,val) {
    state.backEvent = val
  }
};
export default new Vuex.Store({
  state,
  getters,
  mutations
})
```
2.在App.vue中监听history的变化

```javaScript
export default {
  computed:{
    backEvent() {
      return this.$store.getters.backEvent;
    }
  },
  mounted() {
    var that = this;
    if (window.history && window.history.pushState) {
      window.onpopstate = function() {
        if(that.backEvent){
          that.backEvent()
          that.$store.commit('backEvent',null)
        }
      }
    }
  }
}
```
**缺点：**

1.popState仅仅是监听history改变，并不能阻止浏览器的后退事件。即：无论我们在backEvent中做了何种处理，路由实际上是发生了更改的，当前页面也进行了重新加载。

本文实例也可通过监听[vue-router](./../vue/router.MarkDown#导航守卫)实现同样效果，且无上述缺点