WINDOWS下结合VSCODE搭建 FLUTTER 开发环境  
  
  
<br>

**大致脉络: JDK -> ANDROID SDK -> FLUTTER SDK -> VSCODE Flutter -> Android Emulator**

<hr>

# JDK

首先是下载和配置 JDK 。这一步比较简单：下载 JDK 的压缩包，解压，复制目录路径: /path/to/bin 到系统环境变量PATH中，成功。

<hr>


# ANDROID SDK

这一步采用命令行工具"sdkmanager"来下载ANDROID SDK。

下载Android命令行工具：https://developer.android.com/studio#command-tools

* 将解压缩后的文件夹更名为 latest

* 按照以下结构创建文件树，参考如下:

```

┌ android-sdk
│    ├ cmdline-tools
│    │     ├ latest
│    │     │     ├ bin
│    │     │     ├ lib
│    │     │     ├ NOTICE.txt
│    │     │     ├ source.properties

```

* 将 `/path/to/android-sdk/cmdline-tools/latest/bin` 加入系统环境变量PATH。

* sdkmanager命令用法参考：https://developer.android.com/studio/command-line/sdkmanager。

* 列出可安装的 sdk/emulator/images 列表
```
sdkmanager --list
```

* 列出已安装的包的列表
```
sdkmanager --verbose
```

* 下载相关的包
```
sdkmanager "emulator"
```

<br>

``````
sdkmanager "platform-tools" "platforms;android-30" "build-tools;30.0.3"
`````` 
下载完成后，cmdline-tools目录下会出现 emulator, system-images, platform-tools, platforms 这4个文件夹，将 emulator 和 platform-tools 的路径加入系统环境变量PATH。


<hr>


# FLUTTER SDK

* 下载和配置 FLUTTER SDK 。这一步也简单：下载 FLUTTER SDK 的压缩包，解压，复制目录路径: /path/to/bin 到系统环境PATH变量中。


* 设置代理

将` PUB_HOSTED_URL : https://pub.flutter-io.cn `和` FLUTTER_STORAGE_BASE_URL : https://storage.flutter-io.cn `加入系统环境变量PATH。

* 通过下面的命令检查你的现有环境，并将检测结果以报告形式呈现出来。仔细阅读它显示的内容，检查是否有尚未安装的软件或是有其他的步骤需要完成。

```
flutter doctor -v
```

<hr>

# VSCODE Flutter

+ 在VSCODE中安装下列4个插件：

  - Flutter(必装)

  - Dart(必装)

  - Flutter Widget Snippets(可选)
  用于编写 Flutter 组件时的代码提示

  - Dart Data Class Generator Dart(可选)
  您可以用它轻松、快速地创建 Dart 数据类，而且不需要编写样板文件或运行代码生成


* 快速创建 Flutter 项目
  VSCODE -> CTRL+SHIFT+P -> Flutter: New Project -> Application -> 项目地址 -> 输入项目名

* ` flutter devices ` 查看已经连接的设备列表。

* 运行 Flutter 项目 

在项目的根目录下： 
```
flutter run
```


+ 其它快捷键
  - r 键：点击后热加载，算是重新加载。
  - p 键：显示网格，这个可以很好的掌握布局情况，工作中很有用。
  - o 键：切换 android 和 ios 的预览模式。
  - q 键：退出调试预览模式。



<hr>


# Android Emulator

开发 Android 应用时，调试非常重要，调试分为2种：真机与模拟器。
一般人通常只有1个手机，而手机在生活中又非常重要，为了手机安全，可以使用Android模拟器充当调试平台。

第三方模拟器安装方便，在此选用第三方模拟器： Nox Android Emulator 。

* 下载安装，不必多说。为了习惯，把 Nox Android Emulator 设置为手机模式。然后在手机里面的"工具->设置"，连续点击"关于平板模式"，进入开发者模式。点击开发者选项，打开"USB调试"。

* 把原先的 **/.../Nox/bin/nox_adb.exe** 更改为 nox_adb.exe-backup, 把**/ANDROID_SDK/.../platform-tools/adb.exe**复制到 **/.../Nox/bin/** 并改名为 **nox_adb.exe**，原因：如果原生adb和nox_adb版本不一致，会相互查杀。

* 把**/path/to/Nox/bin/**加入到系统环境PATH变量中。

* 查看在运行的设备： `nox_adb devices` 


* 连接 Nox Android Emulator：

```
nox_adb connect 127.0.0.1:62001
```


* 然后启动运行vscode的flutter项目。 




<hr>

# Gradle Exception

首次运行flutter项目报错:

```
Exception in thread "main" java.lang.RuntimeException: Timeout of 120000 reached waiting for exclusive access to file: C:\Computer\Mine\.gradle\wrapper\dists\gradle-7.4-all\aacb4vb19h8nu4gfsb5ib8yiu\gradle-7.4-all.zip

```

原因在flutter项目的gradle的获取地址设置源自 **./android/gradle/wrapper/gradle-wrapper.properties** :

```
distributionUrl=https\://services.gradle.org/distributions/gradle-7.4-all.zip
```

而项目从 https://services.gradle.org/distributions/ 的下载速度很慢,因此只能手动下载gradle包，再修改gradle-wrapper.properties：

```
#distributionUrl=https\://services.gradle.org/distributions/gradle-7.4-all.zip

distributionUrl=file\:///d:/gradle-dir/gradle-7.4-all.zip
```

下载地址还是 https://services.gradle.org/distributions/


<hr>


# Attention


如果想要打包项目为APK，应该重点关注以下3个配置文件，我就是在这3个文件上踩了很久的坑：


- ``./android/build.gradle``

- ``./android/gradle.properties``

- ``./android/gradle/wrapper/gradle-wrapper.properties``


<hr>
