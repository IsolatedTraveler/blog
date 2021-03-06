# 基于Vue-cli和webpack搭建开发环境

## 1.安装vue开发环境

node,vue-cli

## 2.项目初始化

vue init webpack ProjectName

根据提示设置你的项目信息

cd ProjectName

npm install vue-router   路由管理（必需）详情参考[vue router](./router.MarkDown)

npm install vuex         全局状态管理（非必需）详情参考[vue store](./store.MarkDown)

npm install axios        基于Promise的HTTP客户端，用于浏览器和node.js（非必需）

npm install qs           结合axios使用，序列化字符串（非必需）

npm install sass-loader node-sass --save-dev    引入scss/less(非必需)

## 3.自定义配置

### 更改端口

src:  ProjectName/config/index.js

更改内容

    port:8080

    host:'localhost'   ->     host:'0.0.0.0'    解决IP地址问失败的问题

### 更改包名

src: ProjectName/config/index.js

更改内容

    index: path.resolve(__dirname, '../dist/index.html')     更改打包文件路径，方便确认文件位置

    assetsRoot: path.resolve(__dirname, '../dist')       同上

    assetsPublicPath: '/'    ->     assetsPublicPath: './'     变绝对路径为相对路径，解决项目未放在主页时资源加载出错

### 4.自定义eslint规则

ProjectName/.eslintrc.js

#### 函数检验规则

命令：space-before-function-paren

说明：此规则旨在在函数括号之前强制执行一致的间距，因此，只要空格不符合指定的偏好，就会发出警告。

用法：

    "space-before-function-paren": ["error", {
        "anonymous": "always",
        "named": "always",
        "asyncArrow": "never"
    }]

always（默认）需要一个空格，然后(是参数。

never在(参数后面不允许任何空格。

anonymous是用于匿名函数表达式（例如function () {}）。

named是用于命名函数表达式（例如function foo () {}）。

asyncArrow是用于异步箭头函数表达式（例如async () => {}）