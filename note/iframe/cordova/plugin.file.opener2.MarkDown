# cordova-plugin-file-opener2

cordova 打开本地文件，常用于系统内部更新

## 使用方法

```js
cordova.plugins.fileOpener2.open(url, 'application/vnd.android.package-archive', {
  error() {
    console.log('安装文件打开失败')
  },
  success: function() {
    console.log('安装文件打开成功')
  }
})
```

## 最新问题

Android8.0以上对软件做了限制，不允许打开未知来源的软件

解决办法：
  
```js
  //config.xml添加以下内容
  <platform name="android">
    <config-file parent="/manifest" target="AndroidManifest.xml" xmlns:android="http://schemas.android.com/apk/res/android">
      <uses-permission android:name="android.permission.REQUEST_INSTALL_PACKAGES" />
    </config-file>
  </platform>
```