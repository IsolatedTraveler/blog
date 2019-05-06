# cordova 项目打包开发

## 1.安装Cordova开发环境

node,cordova,jdk,sdk,gradle(java编译器)

cordova 安装： npm install -g cordova

### 环境配置
  
jdk:

  1.添加环境变量JAVA_HOME(jdk安装路径)
  
  2.修改环境变量PATH(添加:%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin)

sdk:

  1.添加环境变量ANDROID_HOME(sdk安装路径)

  2.修改环境变量PATH(添加:%ANDROID_HOME%\platform-tools;%ANDROID_HOME%\tools)

gradle

  1.修改环境变量PATH(添加gradle所在路径/bin)

## 创建项目

  cordova create xxx com.example.xxx 别名(项目创建)

  cd xxx

  cordova platform add ...(平台安装)

  cordova pllugin add ...(插件安装)

| 取值 | 描述 |
| :------ | :------ |
| xxx | 文件名，项目简称(英文) |
| example | 公司域名 |
| 别明 | 项目名，项目打包后的名字 |

## 项目打包

cordova build ...

这样打包生成的是调试版本的安装包，换一个电脑环境重新部署该项目，将生成一个新的项目，两则将appid不同，为解决该问题，应对应用进行签名打包部署，每一次进行小范围的修改都要重新打包安装，不便于开发使用，为解决该问题，引入热更新

### 签名打包

1.生成签名文件：keytool -genkey -v -keystore demo.keystore -alias demo -keyalg RSA -validity 20000

2.签名打包： cordova build android --release -- --keystore=../my-release-key.keystore --storePassword=password --alias=alias_name --password=password

| 取值 | 描述 |
| :------ | :------ |
| --keystore | 二进制文件的路径，可以容​​纳一组密钥 |
| --storePassword | 密钥库的密码 |
| --alias | id指定用于签名的私钥 |
| --password | 	指定私钥的密码 |
| --keystoreType | 默认值：基于文件扩展名自动检测pkcs12或jks |

### 热更新

1.安装热更新插件（cordova-hot-code-push-plugin）

2.安装热更新服务（npm install -g cordova-hot-code-push-cli）

3.配置热更新相关参数

cordova-hcp init

```json
  // 根目录新建cordova-hcp.json文件
  {
    "name": "tyxt",
    "ios_identifier": "",
    "android_identifier": "",
    "update": "start", 
    "min_native_interface": 1,
      "content_url": '更新服务地址'
  }
```

4.cordova-hcp build

5.将生成的文件从www目录下的文件拷贝到第三步配置的content_url目录下

6.修改config.xml配置文件

```xml
<!-- 添加以下代码 -->
<chcp>
<config-file url="更新服务地址"/>
</chcp>
```

7.打包

8.小范围修改：执行第四五步骤

9.大范围修改：执行第四步到第七步骤