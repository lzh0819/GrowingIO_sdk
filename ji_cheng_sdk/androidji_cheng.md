## Android集成 {#android}

### **导入SDK** {#sdk}

在 project 级别的 build.gradle 文件中添加 vds-gradle-plugin 依赖：

```
    buildscript {
```

### **添加插件、依赖和对应资源**

在 module 级别的 build.gradle 文件中添加 com.growingio.android 插件、vds-android-agent 依赖和对应的资源：


```
apply plugin: 'com.android.application'
	
	//更新前：compile 'com.growingio.android:vds-android-agent:OP-2.0.7@aar'
```

*   确保URL scheme、项目ID和 SDK的版本准确。

### **添加URL scheme** {#url-scheme}

把URL Scheme添加到您的项目，以便我们唤醒您的程序，进行圈选。将该产品的URLScheme添加到你的AndroidManifest.xml中的LAUNCHER Activity下。例如

```
<?xml version="1.0" encoding="utf-8"?>
```

*   请添加一整个 intent-filter 区块，并确保其中只有一个 data 字段
*   确保URL scheme准确

### **修改app.java文件** {#app-java}

在app.java中添加以下代码：

```
package com.example.wenke.gioeesdkandroiddemo;
```

### **修改MainActivity.java文件** {#mainactivity-java}

在MainActivity.java中添加以下代码：

```
package com.example.wenke.gioeesdkandroiddemo;
```
### **代码混淆** {#-0}

如果你启用了混淆，请在你的proguard-rules.pro中加入如下代码：

```
-keep class com.growingio.android.sdk.** {
```

### **重要配置项** {#-1}

2.3.7.1采集广告banner数据

很多应用的界面上方都有横向滚动的 Banner 广告。

对于此类广告，如果您的应用通过 ViewPager、AdapterView 或者 RecyclerView 实现，请在 Banner创建时（包括动态创建）调用下面的接口来采集数据。

GrowingIO.getInstance().trackBanner(banner, bannerDescriptions)

其中 bannerDescriptions 是 List&lt;String&gt;类型，包含所有广告图对应的广告内容描述，内容描述需要跟广告的顺序相同。

例如，当您有 5 张广告图时，只需创建一个 String 类型的 List，然后按 5 个广告出现的顺序给 List 的元素设置对应的广告描述，同样设置 5 个元素即可。