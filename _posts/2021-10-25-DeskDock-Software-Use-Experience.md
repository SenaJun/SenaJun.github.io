---
layout:     post
title:      DeskDock 软件使用感受
subtitle:   使用方法及使用感受
date:       2021-10-25
author:     SenaJun
header-img: img/DeskDock/DeskDock_Head.jpg
catalog: true
tags:
    - Android
    - 软件
    - 使用感受
    - 个人看法
---

# DeskDock 软件使用方法及使用感受

## 写在前面

这个软件是我在 18 年的时候就发现的，直到 21 年才买了 Pro 版本 ~~（为了上班可以通过鼠标键盘来控制手机摸鱼）~~

其实软件实际使用后，效果其实是类似多模无线键盘那种感觉的 ~~（我才不说我没用过多模无线键盘，根本不知道切换设备的时候是怎么样的）~~，只是 DeskDock 在切换设备时要比多模无线键盘更直接；不过相对的，由于该软件长时间没有维护，导致在无线连接上经常出现连结不上要反复操作几次的尴尬情况，有时候也会出现一些明明 WiFi 信号爆表（路由器就在旁边）却会有卡顿等延迟的诡异现象，导致有时候使用体验并没有想象的好。

不过 DeskDock 搭配立式无线充电底座一起使用，效果意外的很不错

![screenshot_1](https://raw.githubusercontent.com/SenaJun/SenaJun.github.io/master/img/DeskDock/DeskDock_Screenshot_1_270x600.jpg)![screenshot_2](https://raw.githubusercontent.com/SenaJun/SenaJun.github.io/master/img/DeskDock/DeskDock_Screenshot_2_270x600.jpg)

由于我只有一台主力机，备用机也只有好几年前的千元红米机器，所以无法自行拍摄很多图片或者制作 Gif 来供演示，本篇文章可能文字描述偏多，且图片较少，我会尽量找到一些素材做成 Gif 作为参考，还请见谅。

## 软件功能简述

[DeskDock] ，是一款通过 **USB 数据线** 或 **[TCP/IP][article-tcpip]** 与 **Android**（不支持 iOS）设备**共享 Windows/iMac 计算机的鼠标与键盘** 的应用。


与传统的将手机屏幕镜像投射到电脑上的 _[Scrcpy]_ 有所不同，[DeskDock] 就像电脑的副屏一样，可以将鼠标移动到屏幕边界，即可切换您的 Android 设备上并通关计算机的鼠标键盘操控您的 Android 设备

* **注1：** Android 设备需要通过开发者选项打开 USB 调试；
* **注2：** 该软件最后更新日为 **2019年10月21日** ，后续还会不会更新并不清楚，或许开发者已经抛弃这款应用了；
* **注3：** 目前该应用最高**应该**可以支持到 **Windows11** 及 **Android11** 版本（由于没有 iMac 设备，我并不知道能支持到什么系统），未来是否能支持新系统还是个未知数；

[![DeskDock Logo](https://raw.githubusercontent.com/SenaJun/SenaJun.github.io/master/img/DeskDock/DeskDock_LOGO.png "DeskDock Logo")](https://play.google.com/store/apps/details?id=com.floriandraschbacher.deskdock.free&hl=ja&gl=US)

[DeskDock]: https://play.google.com/store/apps/details?id=com.floriandraschbacher.deskdock.free&hl=ja&gl=US
[Scrcpy]: https://github.com/Genymobile/scrcpy


---

## 事前准备

### Android 设备开启 USB 调试

在开始使用之前，需要先通过 Android 的开发者选项，打开 USB 调试选项
不同品牌的 Android 手机打开开发者选项的方法都稍微有些不同，这里以读者都会打开为前提，不都做阐述，实在不会的还请出门百度查询如何打开后再继续阅读。

### 通关 Google Play 下载 [DeskDock Free] 进行先行体验

[DeskDock (Pro)] 为付费应用，**日区** Google Play 的价格为 **620JPY**；
不过官方有推出 Free 版本供用户体验应用，且由于在上面的简述中提到的 **注1** 和 **注2** 所以不建议大家一上来就付费买 Pro，还请使用过 Free 版本后，并不在乎 **注1** 和 **注2** 后，再进行购买。

[DeskDock Free]: https://play.google.com/store/apps/details?id=com.floriandraschbacher.deskdock.free&hl=ja&gl=US
[DeskDock (Pro)]: https://play.google.com/store/apps/details?id=com.floriandraschbacher.deskdock.pro&hl=ja&gl=US

### 电脑下载 DeskDockServer

同手机上的 DeskDock 相同，桌面上的 DeskDockServer 已经停止维护，能找到的最新版本就是 **Ver.1.2.2** 版本

DeskDockServer 为免费应用，且非常重要，没有此软件便无法使用 DeskDock 功能，还请注意
这里我提供了 **[OneDrive]** 和 **[百度云网盘 提取码: 7ign]** 两种下载方式 **（百度云炸了不会补）**

**注4：** 由于我没有 MacBook 设备，这里就先贴一个 **[DeskDock Server For Mac]** 的链接供 Mac 用户作为参考

[DeskDock Server For Mac]: https://www.macupdate.com/app/mac/57770/deskdock-server
[百度云网盘 提取码: 7ign]: https://pan.baidu.com/s/15lIBBlMmEIa5XubQNEiRcg
[OneDrive]: https://1drv.ms/u/s!Ai5xEaZt3wFGh_1czaWfliGZaW0RqA?e=f34PMx

### 更新 Windows JAVA 至最新版本

使用 DeskDockServer for Windows 时，需要对应的 JAVA 环境 （JRE 1.7 or newer on your computer if you haven't already.)

此步骤不需要手动去找对应的 JAVA 版本，在 Windows 启动 DeskDockSever 之后，会弹出需要更新 JAVA 版本的提示，点击确定会自动打开浏览器跳转到 JAVA 下载页面，直接下载并安装即可

[Java 下载页面](https://java.com/zh-CN/download/)

**注5：** iMac 用户需自行确认是否需要对应的运行环境

---

## 通过 USB 数据线连结

> 以下操作均已 Android 手机已启用 USB 调试，且各个设备已经安装好对应软件为前提

### 连结设备并使用

1. 通过 USB 数据线将手机连接至电脑，并在手机上打开 DeskDock
2. 在 Windows/iMac 设备中启动 DeskDock Server
3. Android 设备授权计算机 USB 调试 **（非私人设备/环境下请勿勾选一律允许调试）**
4. 连结完成，开始使用

有线连结相当简单，连接上设备打开对应程序即可直接使用

**具体的使用方法和快捷键操作会在后面进行说明**

## 通过 WiFi 局域网连结

### 将 Android 设备连接至电脑

_DeskDock_ 使用 `adb` 与设备通信，并且 `adb` 支持通过 TCP/IP [连接]到设备，此步骤与 Scrcpy 的无线连接相同，读者也可以参考 _Scrcpy_ 的 Readme 文档进行操作。

1. 将设备和电脑连接至同一 Wi-Fi；
2. 打开 设置 → 关于手机 → 状态信息，获取设备的 IP 地址，也可以执行以下的命令：
   ```bash
   adb shell ip route | awk '{print $9}'
   ```
3. 启用设备的网络 adb 功能 `adb tcpip 5555`。
4. 断开设备的 USB 连接。
5. 连接到您的设备：`adb connect DEVICE_IP:5555` _(将 `DEVICE_IP` 替换为设备 IP)_.
6. 启动 DeskDock 及 DeskDockServer，软件自动配置设备

[连接]: https://developer.android.com/studio/command-line/adb.html#wireless

### DeskDock 支持多设备无线连接

若您在电脑中已经启动 DeskDeckServer
您通过 `adb connect` 连接了多台设备，您可通过 `adb devices` 查看每个设备的连接状态
此时同样在手机启动 DeskDock 并点击 `CONNECT` 按钮进行自动配对即可正常使用

您可以同时通过 _DeskDock_ 同时连接多个设备并切换操作。

## DeskDockServer 设置

### 调整手机窗口激活位置

与 _Windows/Mac_ 的多显示器设置相同，可以**随意调整**手机屏幕的位置，该位置主要为**鼠标超出电脑显示器边缘，并切换激活手机操控的位置**

当手机为熄屏状态时，将鼠标移动到手机，便可激活手机（点亮屏幕）

同时若通过 <kbd>CTRL</kbd> + <kbd>鼠标离开手机屏幕</kbd> 的操作让鼠标返回到电脑显示器，即可将手机屏幕熄灭同时锁定屏幕

![Screenshot_3](https://raw.githubusercontent.com/SenaJun/SenaJun.github.io/master/img/DeskDock/DeskDock_Screenshot_3.png)

### Advanced 更多设置

关于这里的额外设置内容（特别是 _Synergy_ 设置），一般都不会用到 ~(我也没去研究过怎么用就是了)~

_Screen Switch Shortcut_，这个快捷键似乎是无法处罚的，尝试过几次都没见到有自动切换到手机，所以我也放弃了

**Dark Tray Icon - 深色托管图标**，这个可能常用点，其他设置如果有读者知道怎么用，欢迎来教教我ww

![Screenshot_4](https://raw.githubusercontent.com/SenaJun/SenaJun.github.io/master/img/DeskDock/DeskDock_Screenshot_4.png)

### DeskDock Android 端更多设置

在 Android（被控制） 端也是有更多的设置可供调节的，如：**光标大小、光标速度、物理键盘输入控制**等等，我主要就是用来控制和输入就足够了，并没有研究太多的设置，这方面有兴趣的用户可自行尝试。

![screenshot_5](https://raw.githubusercontent.com/SenaJun/SenaJun.github.io/master/img/DeskDock/DeskDock_Screenshot_5_270x600.jpg)![screenshot_6](https://raw.githubusercontent.com/SenaJun/SenaJun.github.io/master/img/DeskDock/DeskDock_Screenshot_6_270x600.jpg)

## 快捷键操作

快捷键操作比较常用且可以使用的，似乎就只有 **关闭屏幕、调节音量和亮度** 这三样了

另外的 **多点触控、水平滚动、隐藏光标（鼠标）、截取屏幕** 尝试过多次似乎都没有任何反应无法使用的样子，这也是比较可惜的地方

| 操作                              | 快捷键                                       |
 | --------------------------------- | :------------------------------------------- |
 | 多点触控（似乎不可用）              | <kbd>CTRL</kbd> + <kbd>鼠标移动</kbd>         |
 | 关闭屏幕                          | <kbd>CTRL</kbd> + <kbd>鼠标离开手机屏幕</kbd>   |
 | 调节手机音量                      | <kbd>CTRL</kbd> + <kbd>鼠标滚轮滚动</kbd>       |
 | 调节手机亮度                      | <kbd>CTRL</kbd> + <kbd>ALT</kbd> + <kbd>鼠标滚轮滚动</kbd>          |
 | 水平滚动 （似乎不可用）            | <kbd>ALT</kbd> + <kbd>鼠标滚轮滚动</kbd>               |
 | 隐藏光标（似乎不可用）             | <kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>H</kbd>     |
 | 截取屏幕至电脑剪贴板（似乎不可用）  | <kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>S</kbd>     |
