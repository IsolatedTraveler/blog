# emmet插件

## 介绍

Emmet是一个Web开发人员的工具包，可以极大地改善您的HTML和CSS工作流程

基本上，大多数文本编辑器允许您存储和重用常用的代码块，称为“片段”。虽然片段是提高工作效率的好方法，但所有实现都存在常见的陷阱：您必须先定义片段，然后才能在运行时扩展它们。

Emmet将片段构思提升到一个全新的水平：您可以键入类似CSS的表达式，可以动态解析，并根据您在缩写中键入的内容生成输出。Emmet是为Web开发人员开发和优化的，其工作流程依赖于HTML / XML和CSS，但也可以与编程语言一起使用。

## 使用

vscode 内置了Emmet 插件，但默认未开启。

use-setting 中添加以下代码
```json
  "emmet.triggerExpansionOnTab": true,
  "emmet.includeLanguages": {
    "vue-html": "html",
    "vue": "html"
  },
  "emmet.syntaxProfiles": {
    "vue-html": "html",
    "vue": "html"
  }
```

## 语法

### 添加类、id、属性、文本

```html
eg : elem.class#id[attr=attrVal]{text}

result : <elem class="class" id="id" attr="attrVal">text</elem>
```

### 嵌套分组

> 子元素

+ 兄弟元素

() 分组

```html
eg : div>((p>span)+span)

result: <div>
  <p><span></span></p>
  <span></span>
</div>
```

### 定义多个相同元素

```html
eg : span*3

result : <span></span><span></span><span></span>
```