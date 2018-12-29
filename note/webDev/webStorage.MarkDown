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

param: key, value

#### getItem

param: key

#### removeItem

param: key

#### key

#### length

### localStorage

#### 特点

1.生命周期永久（用户不清除localStorage信息，这些信息将永久保存）

2.仅在客户端保存，不参与和服务器通信

### sessionStorage

## cookie

