# 本地数据存储（客户端存储）

本地存储数据分为四种方式：

  1.cookie

  2.webStorage

  3.Flash存储

  4.IndexedDB

## webStorage

### 特点

1.客户端存储数据技术，本地存储

2.每个存储源不能大于10MB

3.包括localStorage,sessionStorage

### API

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

return {String || Null} 值

target: 清除指定存储键值对

#### key

type: Function

param:

#### length

type: Attribute

### localStorage

#### 特点

1.生命周期永久（用户不清除localStorage信息，这些信息将永久保存）

2.仅在客户端保存，不参与和服务器通信

### sessionStorage

## cookie

