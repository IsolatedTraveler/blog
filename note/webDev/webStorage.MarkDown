# 本地数据存储（客户端存储）

本地存储数据分为四种方式：

  1.[cookie](#cookie)

  2.[webStorage](#webStorage)

  3.Flash存储：借助Flash播放器

  4.IndexedDB

## webStorage

提供了通过浏览器存储键/值对，以更直观的方式比使用cookie机制

### 特点

1.客户端存储数据技术，本地存储

2.每个存储源不能大于10MB

3.包括localStorage,sessionStorage

### 优点：

1.存储数据量大

2.不会随http请求一起发送

### 缺点：

1.在浏览器的隐私模式下不能读取

2.本质是在读写文件，写入数据量大的话会卡（FF是将localstorage写入内存中的）

3.不能被爬虫读取

## 局限性

多数浏览器提供了隐身/私密模式，这与本地存储的使用存在根本矛盾，为防止用户禁用本地存储，在使用本地存储前应对使用环境进行校验，检查本地存储功能是否可用

### localStorage,sessionStorage公有API

#### setItem

type: Function

target: 设置/修改指定存储键值对

param: {String} [key] (required) 存储数据别名，用于获取/清除/修改数据的唯一识别码

param: {String} [valie] (required) 值

return {Undefined}

#### getItem

type: Function

target: 获取指定存储键值对

param: {String} [key] (required) 存储数据别名，用于获取/清除/修改数据的唯一识别码

return {String || Null} 值

#### removeItem

type: Function

target: 清除指定存储键值对

param: {String} [key] (required) 存储数据别名，用于获取/清除/修改数据的唯一识别码

return {Undefined}

#### clear

type: Function

param: null

target: 清除所有存储键值对

return {Undefined}

#### key

type: Function

param: {Number} [index] (required) 存储数据别名按字母排序后的序列值

return {String || Null} 获取key

#### length

type: Attribute

target: 获取storage存储数据总数量

return {Number}  存储数据个数

### localStorage,sessionStorage异同点

不同浏览器无法共享localStorage或sessionStorage中的信息。相同浏览器的不同页面间可以共享相同的 localStorage（页面属于相同域名和端口），但是不同页面或标签页间无法共享sessionStorage的信息。这里需要注意的是，页面及标 签页仅指顶级窗口，如果一个标签页包含多个iframe标签且他们属于同源页面，那么他们之间是可以共享sessionStorage的。

## cookie

### 特点

1.生命周期只在设置的cookie过期时间内有效，即使窗口或浏览器关闭。

2.存放数据大小为4K左右且有个数限制（各浏览器不同），一般不能超过20个。

3.与服务器端通信：每次都会携带在HTTP头中，如果使用cookie保存过多数据会带来性能问题。

4.Cookie需要程序员自己封装，源生的Cookie接口不太友好

### 优点：极高的扩展性和可用性

1.通过良好的编程，可控制cookie保存对象的大小。

2.通过加密和安全传输技术，减少cookie被破解的可能性。

3.控制cookie的生命周期，使之不会永远有效。这样的话偷盗者很可能拿到的就是一个过期的cookie。

### 缺点

1.cookie的长度和数量的限制。每个domain最多只能有20条cookie，每个cookie长度不能超过4KB。否则会被截掉。

2.安全性问题。如果cookie被人拦截，那个人就可以获取到所有session信息。

3.有些状态不能保存在客户端。例如，为了防止重复提交表单，我们需要在服务端保存一个计数器。若吧计数器保存在客户端，则起不到什么作用。