# App技术调研

## ReactNative
> ReactNative的库大部分为社区提供

### 热更新

+ 纯ReactNative支持热更新

+ 原生 + ReactNative， 仅ReactNative部分支持热更新

### 第三方sdk支持
> app上常用的功能：地图、推送

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

### 硬件支持
> 蓝牙

#### 1. 低功耗蓝牙(BLE)
> 蓝牙4.0开始支持BLE，低功耗蓝牙传输距离远，功耗低，但传输数据量小

> 4.0以下为传统蓝牙

**react-native-ble-plx**: https://github.com/Polidea/react-native-ble-plx

**react-native-ble-manager**: https://github.com/innoveit/react-native-ble-manager

[React Native BLE 蓝牙通信](https://juejin.im/entry/591bb3a98d6d81005899d5cc "低功耗蓝牙")

传统蓝牙暂时未找到React Native的第三方库

### UI



### 调试



## Flutter

#### 2. 推送
**极光推送（JPush）**：官方提供支持库 [极光推送Flutter SDK](https://github.com/jpush/jpush-flutter-plugin "Flutter SDK")

#### 3. 语音
**科大讯飞(iflytek)**：未找到第三方库


## 其他

ReactNative音视频相关的第三方库也相对较少

## 总结

ReactNative 地图sdk都是非官方支持（对官方的sdk进行了封装），文档较少，支持特性较少

ReactNative 蓝牙目前仅支持BLE

如果没有跨平台需求，建议用原生 或者 原生+ReactNative




