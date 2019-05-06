# App技术调研

## ReactNative
> ReactNative的库大部分为社区提供

### 热更新

+ 纯ReactNative支持热更新

+ 原生 + ReactNative， 仅ReactNative部分支持热更新

### 第三方sdk支持

#### 1. 地图
> ReactNative的百度、高德地图库都是对原生sdk的封装

+ 高德地图
[sdk文档](https://lbs.amap.com/api/android-sdk/summary/, "高德地图")
    
    + **react-native-amap**：
        [react-native-amap](https://github.com/laoqiu/react-native-amap "react-native-amap")
        
        两年未更新，缺少文档
    
    + **react-native-amap3d**：
        [react-native-amap3d](https://github.com/qiuxiang/react-native-amap3d "react-native-amap3d")
        
        不支持 地理/逆地理编码、路径规划
    
+ 百度地图
    + **react-native-baidumap-sdk**
    
        不支持 路径规划

#### 2. 推送
**极光推送(JPush)**：官方提供支持库 [极光推送ReactNative SDK](https://github.com/jpush/jpush-react-native "极光推送ReactNative SDK")

#### 3. 语音
**讯飞语音(iflytek)**: 非官方库 [react-native-speech-iflytek](https://github.com/zphhhhh/react-native-speech-iflytek "讯飞语音")

#### 4. 支付


### 硬件支持

#### 1. 低功耗蓝牙(BLE)
> 蓝牙4.0开始支持BLE，低功耗蓝牙传输距离远，功耗低，但传输数据量小

> 4.0以下为传统蓝牙

**react-native-ble-plx**: https://github.com/Polidea/react-native-ble-plx

**react-native-ble-manager**: https://github.com/innoveit/react-native-ble-manager

[React Native BLE 蓝牙通信](https://juejin.im/entry/591bb3a98d6d81005899d5cc "低功耗蓝牙")

传统蓝牙暂时未找到React Native的第三方库

#### 2. 二维码
[react-native-qrcode-scanner](https://github.com/moaazsidat/react-native-qrcode-scanner)

### UI
#### 1. 页面导航
[React Navigation](https://reactnavigation.org/docs/en/getting-started.html)

[React Native Navigation](https://github.com/wix/react-native-navigation)

### 调试
#### 真机调试
> 注意手机端不能开VPN，PC端如果有抓包软件也必须关闭，实在连不上时卸载App重新安装

手机端ReactNative应用内的JS Client 连接 PC端的nodejs server(10.0.1.1:8081)


## Flutter

#### 2. 推送
**极光推送（JPush）**：官方提供支持库 [极光推送Flutter SDK](https://github.com/jpush/jpush-flutter-plugin "Flutter SDK")

#### 3. 语音
**科大讯飞(iflytek)**：未找到第三方库


## 其他

### ReactNative和原生交互
> ReactNative提供Native Module和Native UI Components来访问原生功能，需要对ios和android分别进行原生开发

+ **对Android来说**：

NativeModule继承ReactContextBaseJavaModule，只提供上下文环境，没有生命周期方法，
消息传递是单向的，只能js 流向 native，native不能主动调用js的方法

JS原生交互可传递的数据类型
```javascript
Boolean -> Bool
Integer -> Number
Double -> Number
Float -> Number
String -> String
Callback -> function
ReadableMap -> Object
ReadableArray -> Array
```

## 总结

ReactNative 地图sdk都是非官方支持（对官方的sdk进行了封装），文档较少，支持特性较少

ReactNative 蓝牙目前仅支持BLE

## 问题

1. [React Native Gesture Handler](https://github.com/kmagiera/react-native-gesture-handler "")和
[React Native Camera](https://github.com/react-native-community/react-native-camera "")
包冲突，导致
[React Navigation](https://reactnavigation.org/)和
[ReactNativeQRCodeScanner](https://github.com/moaazsidat/react-native-qrcode-scanner)无法并存

2. 第三方库长时间未更新，版本落后







