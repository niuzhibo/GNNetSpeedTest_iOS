# 极牛GNSpeedTest iOS SDK 使用手册
***
##SDK 概述
极牛测速SDK为iOS平台开发使用的SDK，为iOS开发者提供简单、快捷的接口和开源调用示例，帮助开发者实现iOS平台上的测速功能实现。不仅极大降低开发门槛，同时支持客户快速在多个平台发布产品。
***

## GNSpeedTest SDK功能说明
- 可以支持极牛推流SDK测试当前网速是否适合推流。
***

## 内容摘要
---
- [工程环境](#1)
	* [运行环境](#1.1)
	* [添加工程](#1.2)
- [SDK使用示例](#2)
	* [入口类](#2.1)
	* [调用](#2.2)
- [特性说明](#3)
- [主要接口说明](#4)
	* [测速](#4.1)
	
## 工程环境<h2 id = "1">
---
### 运行环境<h3 id = "1.1">
GNSpeedTestSDK iOS SDK可运行于 iPhone/iPod Touch/iPad，支持 iOS 7.0 及以上版本; 
### 添加工程<h3 id = "1.2">
- SDK压缩包，将其中的GNSpeedTestSDK.framework添加到Xcode工程中，具体步骤为：
- 选中应用的Target，进入项目配置页面（General）
- 在Embedded Binaries的列表中添加GNSpeedTestSDK.framework。

## SDK使用示例<h2 id="2">
***
在使用`GNSpeedTestSDK`时，引入头文件

	#import <GNSpeedTestSDK/GNSpeedTestSDK.h>
	
### 入口类<h3 id = "2.1">
- GNSpeedTestSDK的入口类为**GNDataUpOrDown**，包含了开启上传功能与下载功能。

### 调用<h3 id = "2.2">
初始化测速 初始化需要几个步骤：

- 在AppDelegate中初始化GNDataUpOrDown单例；
- 设置代理；
- 进行测速；
- 根据需要获取当前网速。

```
    [[GNDataUpOrDown sharedInstance] GNInitSpeedTestSDK];
 
```

当测速结束后，会回调上行以及下行的速度。
	  
## 特性说明<h2 id = "3">
***
- 可以测试当前的网速是否支持牛直播推流。

## 主要接口说明<h2 id = "4">
***
以下为测速主要接口说明：


### 上传和下载<h3 id = "4.1">
- `- (void) GNInitSpeedTestSDK;`

		描述： 初始化SDK

		参数： 无

		说明：

    	初始化测速SDK，推荐在AppDelegate中调用。
    	
- `- (void) startToSpeedTest;`

		描述： 开始测速

		参数： 无

		说明：

    	开始测速，当测速结束后，会以回调的形式获得测速结果。
    	
- `- (void) speedTestWithDownSpeed:(long long int) DownSpeed UpSpeed:(long long int) UpSpeed;`

		描述： 测速结果回调（协议方法）

		参数： DownSpeed 下行速度  UpSpeed 上行速度

		说明：

    	结束测速后，回调结果。