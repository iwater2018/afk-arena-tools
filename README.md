# afk-arena-tools

## 简介

使用 Python + OpenCV + PyQt5 + adb 制作的AFK Arena / 剑与远征 辅助。

原理是OpenCV识别图片，adb负责截图和点击操作。

<p align="center">
  <img src="./_docs/img/main_gui.png" alt="main_gui" width="500"/>
  <br><br>
  <b>游戏界面</b>
</p>

既然已经来了，不点个star鼓励下作者吗？

## 运行说明

电脑需要安装：

* Python3.6或以上版本
* OpenCV（从pip安装即可）
* adb（Windows版本的release包自带）
* PyQt5（从pip安装即可）

输入下面指令即可安装，Linux用户记得加sudo

```
pip install opencv-python PyQt5
```

因为使用到ADB，只能作用于安卓手机。大部分安卓模拟器也是可以的，点“USB连接手机”应该就行。

目前以下操作系统测试通过：
* Manjaro Linux
* Windows 10 (ver 1903)

双击启动脚本（懒人专用）或者运行main.py

## 操作说明

在“杂项”菜单中选择适合的方式连接adb，连接成功后点击对应功能即可。如果连不上，检查下开发者模式中的USB debug是否开启。WIFI adb可以使用这个repo内thirdparty文件夹下的app（不包含在release包里，不是我开发的，是否使用请自行决定），需要root。

分辨率在“杂项”菜单选择，默认分辨率为1440p，如果你的设备不是这个分辨率，务必更改为其它选项，否则会出现能匹配但是点不到的问题。

推图的自动重试功能需要进入选择队伍页面（正下方有“战斗”字样）才能使用

自动推图功能在首页即可使用

王座之塔功能需要进入具体的塔才能使用

注意：正常情况下匹配度大概会在97%以上的，如果匹配率出奇的低，那就开个issue吧

## 更新说明

### 【正在摸鱼中】 V1.0.8

* [ ] 一键完成每日必做的任务

### 2020.02.16 V1.0.7

* [x] 修复推图时遇到升级弹窗停下的问题（issue #4）

### 2020.01.23 V1.0.6

* [x] 截图方式改为直接读取stdout
* [x] 杂项中的截图功能改成直接弹窗显示，不再保存到本地
* [x] 每轮截图匹配之间增加1秒延时，防止截图太快造成（没什么影响的）连续点击

之前截图使用通用的方法，就是adb获取截图，通过pipe保存到本地，然后opencv读取。然而我发现，这么搞，硬盘写入量好像挺大啊，一小时写入10G妥妥的。捣鼓了半天，终于做到了直接从stdout读取图片，无需多走一步保存到本地。有需要的朋友可以参考get_img的实现。

### 2020.01.20 V1.0.5

* [x] 现在主线的“自动推图”可以处理通过特定关卡后弹出的限时礼包窗口
* [x] 增加战役页面的“挑战首领”图标检测
* [x] 修复打包脚本（之前忘了打包图片）

### 2020.01.17 V1.0.4

* [x] 修复推图到boss关就停下的问题（issue #3）

### 2020.01.12 V1.0.3

没想到真有人用，很开心，打算继续填坑

* [x] Command部分重构
* [x] 多分辨率适配（720p, 1080p, 1440p）
* [x] 重新制作匹配素材，分辨率为1440p

有时候好像会连着点两次，可能是截图太快了，反正不影响使用

### 2020.01.11 V1.0.2

* [x] 替换老旧的匹配目标图片
* [x] 适配新版游戏流程

### 2019.10.20 V1.0.1

* [x] 适配Windows系统
* [x] adb连接使用子线程防止阻塞

### 2019.10.18 V1.0.0

* [x] 最初版本发布
