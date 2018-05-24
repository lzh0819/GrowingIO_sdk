## Android cordova 集成 {#android-cordova}

### **添加cordova插件** {#cordova}


```
cordova plugin add cordova-growingio-plugin
```

注意：cordova-growing-plugin依赖cordova.5.0.0以上，目前不支持低版本。

### **导入SDK** {#sdk}

ANDROID/BUILD.GRADLE文件添加

```
buildscript {
```

注意高亮部分的sdk版本

### **修改BUILD.GRADLE文件** {#build-gradle}

找到ANDROID/APP/BUILD.GRADLE文件加入以下代码

```
apply plugin: 'com.android.application'
```

### **修改AndroidManifest.xml文件** {#androidmanifest-xml}

在AndroidManifest.xml文件添加以下代码：

```
<?xml version="1.0" encoding="utf-8"?>
```

### **修改app.java文件** {#app-java}

在app.java添加以下代码


```
ackage com.example.wenke.gioeesdkandroiddemo;
```

### **配置cordova** {#cordova-0}

当应用程序打开时，需要初始化会话并启动采集功能。所以，在deviceready或者resume事件触发时，可以通过下列方式初始化会话。


```
// sample index.js
```