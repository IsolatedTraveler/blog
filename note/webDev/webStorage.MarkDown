# 本地数据存储（客户端存储）

本地存储数据分为四种方式：

  1.[cookie](#cookie)

  2.[webStorage](#webStorage)

  3.Flash存储

  4.IndexedDB

## 局限性

多数浏览器提供了隐身/私密模式，这与本地存储的使用存在根本矛盾，为防止用户禁用本地存储，在使用本地存储前应对使用环境进行校验，检查本地存储功能是否可用

## webStorage

提供了通过浏览器存储键/值对，以更直观的方式比使用cookie机制

### 特点

1.客户端存储数据技术，本地存储

2.每个存储源不能大于10MB

3.包括[localStorage](#localStorage),[sessionStorage](#sessionStorage)

### localStorage,sessionStorage公有API

#### setItem

type: Function

param: {String} [key] (required) 存储数据别名，用于获取/清除/修改数据的唯一识别码

param: {String} [valie] (required) 值

return {Undefined}

target: 设置/修改指定存储键值对

#### getItem

type: Function

param: {String} [key] (required) 存储数据别名，用于获取/清除/修改数据的唯一识别码

return {String || Null} 值

target: 获取指定存储键值对

#### removeItem

type: Function

param: {String} [key] (required) 存储数据别名，用于获取/清除/修改数据的唯一识别码

return {Undefined}

target: 清除指定存储键值对

#### clear

type: Function

param: null

return {Undefined}

target: 清除所有存储键值对

#### key

type: Function

param:

#### length

type: Attribute

return {Number}  存储数据个数

### localStorage

#### 特点

1.生命周期永久（用户不清除localStorage信息，这些信息将永久保存）

2.仅在客户端保存，不参与和服务器通信

### sessionStorage

#### 特点

## cookie