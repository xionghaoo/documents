# ReactNative(Android)
> RN开发分为完全和混合开发，原生部分以Android为例

开发前最好用git建一个版本管理，出了问题方便回滚

## 完全RN开发
> 继承ReactActivity，页面上承载各种RN组件，一个App只有一个ReactActivity

### 开发流程
> [官方文档](https://facebook.github.io/react-native/docs/getting-started)

1. 创建工程

```shell
$ react-native init ProjectName 
```

2. 运行项目
```shell
$ cd ProjectName && react-native run-android
```
上述命令会在PC端先启动一个nodejs server(10.0.1.1:8081)，
然后再启动gradle编译构建Android的原生代码，最后安装App到模拟器或者真机。

安装后启动App时执行的命令：
```shell
$ /Users/xionghao/Library/Android/sdk/platform-tools/adb -s 8XV5T15A20011060 reverse tcp:8081 tcp:8081

$ /Users/xionghao/Library/Android/sdk/platform-tools/adb -s 8XV5T15A20011060 shell am start -n com.xxx/com.xxx.MainActivity
```

这里是通过react-native命令安装的app，我们同样可以用Android Studio来自行编译构建android部分的工程，
以及安装app到模拟器或者真机。

现在就可以修改js代码，进行开发了。

### Android Studio管理android部分代码
> 如果不想用react-native run-android来安装app，我们同样可以用AndroidStudio管理android代码，
RN项目下的android文件夹可以直接用AndroidStudio打开

以安装到真机为例，构建安装完成的App报错"can not load script"，这是因为本地RN应用中JS Client不能连接到PC端nodejs server。

打开DevMenu中的Dev Settings，在Debug server host & port for device选项中设置server地址和端口号为**10.0.1.1:8081**，
注意这里需要关闭手机和PC端的VPN和PC端的抓包软件。如果还连不上，卸载App后重装。

上面的过程有几点需要说明下：
1. 安装在手机上的App只有原生代码和js Client，缺少js bundle，而连接到PC端的nodejs server会下载这个jsBundle，
每次js代码有改动，js client都会自动下载这个js bundle
2. jsBundle可以做成离线的，打包到apk中（参考***常用命令***中的jsBundle打包命令），App启动时会先加载离线jsBundle，
这样不启动nodejs server同样可以运行App


## 混合开发
> ReactNative & Android，一个App可以有多个ReactActivity

由于jsBundle是放在assets文件夹中打包进Apk的，因此RN部分通过替换jsBundle可以实现热更新，如果有多个ReactActivity则需要多个
离线jsBundle

## 常用命令

#### 单独启动nodejs server
```shell
$ yarn start
或者
$ react-native start
```

#### 启动模拟器
```shell
// Android
// 查看可用的设备，这里会列出模拟器或真机的名称
$ adb devices

// 根据上面命令列出的设备名称启动模拟器
$ emulator -avd Nexus_5X_API_28_x86 &


// ios
// 启动默认的模拟器（最新的机型）
$ open /Applications/Xcode.app/Contents/Developer/Applications/Simulator.app

// 启动指定机型的模拟器
$ ios-sim start --devicetypeid "iPhone-8-Plus, 12.2"
```

#### 重置8081端口
```shell
// 一般nodejs server连不上时执行下面的命令
$ adb reverse tcp:8081 tcp:8081
```

#### 打jsBundle离线包
```shell
$ react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res/
```
注意android目录的路径，如果不存在assets文件夹需要先创建

#### 真机打开DevMenu
+ Android
    1. 摇晃手机
    2. adb命令
    ```shell
    $ adb shell input keyevent 82
    ```

#### 模拟器打开DevMenu
+ Android 按两下R键

#### 调试
> [官方文档](https://reactnative.cn/docs/debugging/)

app内的js client连接到chrome（http://localhost:8081/debugger-ui），打开开发者工具就可以看到console的log

## 问题

### JavaScript是如何调用Java代码的？

[LiveConnect](https://stackoverflow.com/questions/6649125/calling-java-methods-in-javascript-code)

[React Native Performance Case Study, How It Differs From Native Apps: Part 1 (MessageQueue & JS Thread)](https://medium.com/@rotemmiz/react-native-internals-a-wider-picture-part-1-messagequeue-js-thread-7894a7cba868)

### JS部分导入npm包以后，AndroidStudio中提示模块无法识别

可能是缓存的问题，在RN根目录下执行下面的命令
```
$ rm -rf ./node_modules && npm install
```









