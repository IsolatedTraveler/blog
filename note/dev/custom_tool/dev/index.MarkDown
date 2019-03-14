# 自定义快捷开发工具开发说明

## 配置

## 公共方法

### 使用

```js
// 两种任选一种
const config = require('/config.js')
const {name,name1,name2...} = require('/config.js')
```

#### 提示信息

```js
const {msg} = require('config.js')
/**
 * @name        msg
 * @result      根据state值打印出不同等级的提示信息
 * @params      message   提示信息
 * @params      state     提示状态    0-提示    1-信息    2-警告      3-成功      4-错误    5-错误并退出
 */
msg(message,state)
```
#### 参数判断

```js
const {checkParams,checkParam} = require('config.js')
checkCommand(params,config)
/**
 * @name        checkCommand
 * @result      检查必需参数是否合符要求
 * @params      params    待检查的参数    Array
 * @params      config    命令参数配置信息
 */
```
#### 执行API

```js
const {commandExe} = require('config.js')
commandExe(params,name,url)
/**
 * @name        commandExe
 * @result      执行自定义API
 * @params      params    后续运行参数
 * @params      name      api下的具体方法
 * @params      url       相对路径目录
 */
```

#### 对api结果进行处理

```js
const {resultDeal} = require('config.js')
resultDeal(result)
/**
 * @name        resultDeal
 * @result      对api结果进行处理
 * @params      result      api运行结果
 */
```

## 已完成api

