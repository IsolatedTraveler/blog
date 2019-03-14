# 判断当前访问平台

## 应用场景

开发中往往需要兼容开发，考虑到不同的平台设备对内容需求往往不一样，为此需要进行针对设计。

目前我所接触到的业务都是根据这些属性的不同区分不同的入口，比如要区分是IOS还是Android客户端进行访问的，或者是区分是否是微信访问的等等。

## 判断方式

### 方式一

利用navigator对象

Navigator 对象包含有关浏览器的信息。不过应当注意，navigator 对象没有统一标准，但所有浏览器都支持该对象

| 属性名 | 描述 |
| :------ | :------ |
| appCodeName | 返回浏览器的代码名。 |
| appMinorVersion | 返回浏览器的次级版本。 |
| appName | 返回浏览器的名称。 |
| appVersion | 返回浏览器的平台和版本信息。 |
| browserLanguage | 返回当前浏览器的语言。 |
| cookieEnabled | 返回指明浏览器中是否启用 cookie 的布尔值。 |
| cpuClass | 返回浏览器系统的 CPU 等级。 |
| onLine | 返回指明系统是否处于脱机模式的布尔值。 |
| platform | 返回运行浏览器的操作系统平台。 |
| systemLanguage | 返回 OS 使用的默认语言。 |
| userAgent | 返回由客户机发送服务器的 user-agent 头部的值。 |
| userLanguage | 返回 OS 的自然语言设置。 |

利用navigator的 userAgent 属性可以对平台信息做出判断

```js
// userAgent属性是一个只读的字符串，申明浏览器用于HTPP请求的用户代理头的值，简单点说其实就是通过UserAgent可以取得浏览器类别、版本，客户端操作系统等信息。
/**
 * 获取操作系统类型，
 * 0 Android
 * 1 iOS
 * 2 其他
 */
function getOSType() {
  if (/(Android)/i.test(navigator.userAgent)) {
    return 0;
  } else if (/(iPhone|iPad|iPod|iOS)/i.test(navigator.userAgent)) {
    return 1;
  } else {
    return 2;
  }
}
//js判断当前环境是否是微信环境
function is_weixin(){
  var ua = navigator.userAgent.toLowerCase();
  if(ua.match(/MicroMessenger/i)=="micromessenger") {
    return true;
  } else {
    return false;
  }
}
```