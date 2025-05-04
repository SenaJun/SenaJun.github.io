---
layout:     post
title:      公主链接大厅 Live2D 动画提取、超分、补帧、合并全流程
subtitle:   公主连结大厅动画制作教程
date:       2025-05-05
author:     SenaJun
header-img: img/PCR_Game_Data_Extraction/PCR_Game_Data_Extraction_Head.jpg
catalog: true
tags:
    - WallpaperEngine
    - 教程
    - 超分
    - 补帧
    - 公主连结
    - PCR
    - プリンセスコネクト
---

# 公主链接大厅 Live2D 动画提取、超分、补帧、合并全流程

**请勿将提取后的所有物品用作商业用途，且请勿提取任何游戏未实装的角色资料并公布于网络，若您进行了包括但不限于以上的操作，请后果自负，本教程仅供学习参考，所有后果概不负责**

## 需要准备的东西

**注意**：我不会提供任何工具的下载地址，以下所有工具请自行搜索查找下载

* Windows 10/11 电脑
* **建议至少 RTX 2060 以上显卡（影响超分时长）**
* DMM 版公主连结
* 可以运行 DMM 版的科学上网工具
* VGMToolbox
* Waifu2x-Extension-GUI
* ffmpeg 组件

---

## 第一步：找到 PCR 的数据包存储位置

默认为：`C:\Users\用户名\AppData\LocalLow\Cygames\PrincessConnectReDive`
游戏内视频文件则是：`C:\Users\用户名\AppData\LocalLow\Cygames\PrincessConnectReDive\m`

**记住这个位置，需要从这里把大厅动画复制出来**

这里推荐使用 `mklink` 指令将游戏数据转移到别的硬盘

1. 首先记录下 Cygames 文件夹默认存储位置的地址，默认位置这里称为`PatchCy01`
2. 后将默认的 Cygames 文件夹整个移动到你想放的位置，这个位置的地址这里称为`PatchCy02`
3. 最后使用 CMD，输入 `mklink /J PatchCy01 PatchCy02`
4. 去 `C:\Users\用户名\AppData` 内是否出现一个 Cygames 的快捷方式文件夹，有既是成功了

**这一步很重要**
在游戏视频数据文件夹内（`.\m`），将文件按照最新修改时间排序，这能方便你找到正在提取的角色动画的文件。

![数据包路径参考](https://raw.githubusercontent.com/SenaJun/SenaJun.github.io/refs/heads/main/img/PCR_Game_Data_Extraction/FileLocation.png)

---

## 第二步：提取角色大厅 Live2D 动画

公主连结日服官方的 Live2D 不是实时渲染的，是以动画的形式循环呈现的，所以我们仅需提取出文件，即可解码成视频后进行后续所有工作。

**注**：所有提取工作，不需要你拥有该角色；

### 01. 当你已拥有需要提取角色的情况下

1. 找到该角色，随便拿一个角色为例，在 **キャラ** 角色列表查看此角色，即 **キャラ強化** ，随后点击左下角的角色头像   ![文件提取](https://raw.githubusercontent.com/SenaJun/SenaJun.github.io/refs/heads/main/img/PCR_Game_Data_Extraction/Character_01.png)
2. 进入 **キャラ詳細** 后，点击左边角色图片右上角的放大按钮，会弹出 **データダウンロード** ，点击 OK 下载即可   ![文件提取_02](https://raw.githubusercontent.com/SenaJun/SenaJun.github.io/refs/heads/main/img/PCR_Game_Data_Extraction/Character_02.png)
3. 前往游戏数据包目录`C:\Users\用户名\AppData\LocalLow\Cygames\PrincessConnectReDive\m`，按照最新修改时间排序，通常来说，**最上面的文件**就是刚刚下载好的大厅动画，将该动画复制到桌面或其他方便你下一步操作的位置。
4. 打开 **VGMToolbox** 后进行设置
   * 左边导航栏依次点击 **Misc. Tools → Stream Tools → Video Demultiplexer** ；
   * 随后右边窗口 **Options** 位置，将 **Forma**t 选择为 **USM (CRI Movie2)**；
   * 由于提取的大厅动画没有音频，所以右边选上 **Extract Video Only** 仅提取视频
     ![文件提取_03](https://raw.githubusercontent.com/SenaJun/SenaJun.github.io/refs/heads/main/img/PCR_Game_Data_Extraction/Character_03.png)
5. 将提取出来的文件，拖入 **Drop Files Here** 下方的空白区域，软件会自动解码文件，后得到一个 **.m2v** 的视频文件，到这一步，提取完成     ![文件提取_04](https://raw.githubusercontent.com/SenaJun/SenaJun.github.io/refs/heads/main/img/PCR_Game_Data_Extraction/Character_04.png)
6. 最后建议将提取好的视频文件整理好，方便后续操作；**注意：以下步骤均为此文件布局进行举例！** ![拆包_01](https://raw.githubusercontent.com/SenaJun/SenaJun.github.io/refs/heads/main/img/PCR_Game_Data_Extraction/Waifu2x_01.png)

### 02. 当你未拥有需要提取角色的情况下

**这里分两种方法：**

* 你的好友拥有该角色的情况下：
  
  * 与好友沟通，让 **ta** 把你需要提取的角色，设置为玩家头像，即主页 **メニュー → プロフィール** 个人名片页面的头像；
  * 随后你去 **メニュー → フレンド → フレンド一覧** 好友一栏找到你的好友，点击好友头像旁的感叹号按钮，弹出玩家 **プロフィール** 个人名片后，长按玩家头像；
  * 这时候会弹出一个 **キャラ詳細**，到此，**剩余的步骤便跟上面 01-2 步骤一致**；
* 你的好友也没有拥有该角色的情况下：
  
  * 这种情况下，你需要前去 **メニュー → フレンド → フレンド管理 → フレンドを探す**
  * 在茫茫玩家人海中，找到某个玩家挂着你需要提取的那个角色的头像
  * 随后点击玩家头像旁的感叹号按钮，弹出玩家 **プロフィール** 个人名片后，长按玩家头像；
  * 这时候会弹出一个 **キャラ詳細**，到此，**剩余的步骤便跟上面 01-2 步骤一致**；

---

## 第三步：使用 ffmpeg 拆帧

**此步骤建议提前部署好 ffmpeg 的 windows 环境变量，以方便未来的每一次使用**

1. 打开 `CMD`
2. 输入 `ffmpeg -i ".\Video.m2v" ".\PNG\%08d.png"` **注意一定要输入 `&08d.png` ffmpeg 拆包过程中会自动排序每一帧并命名，这一步很重要！** ![拆包_02](https://raw.githubusercontent.com/SenaJun/SenaJun.github.io/refs/heads/main/img/PCR_Game_Data_Extraction/Waifu2x_02.png)
3. 等待拆包完成，通常情况下拆包后一共是 240 张，默认为 29.97 帧，部分特殊卡面会有不同，自己点开看看视频长度算一下就知道了拆包张数是否正确了；

---

## 第四步：使用 Waifu2x-Extension-GUI 进行降噪超分

条件允许的情况下，超分引擎推荐使用 **RealESRGAN-NCNN-Vulkan**，模型使用**2D动漫模型 Anime-HQ-W4xEX**，这是目前效果最好的超分引擎，但代价是速度非常慢，以我的 4070 Super 举例，240 张的大厅动画，通常需要 20 分钟。按照下图设置即可，线程数按照自己显卡的显存进行设置，不懂的话直接无脑按右上角红色按钮中的**优化设定** ![超分_01](https://raw.githubusercontent.com/SenaJun/SenaJun.github.io/refs/heads/main/img/PCR_Game_Data_Extraction/Waifu2x_03.png)
也可以使用 **Real-CUGAN-NCNN-Vulkan** 引擎，这个引擎也能又相当不错的超分效果，且速度对比 **RealESRGAN-NCNN-Vulkan** 快了很多

**以下使用 RealESRGAN-NCNN-Vulkan 引擎进行举例**

将 **.\PNG** 文件夹拖入软件的文件列表，图片样式(RealESRGAN)修改为**2D动漫**，放大倍率**2.0**，修改输出文件夹为 **.\waifu2x**，启用，并勾选**保留原文件名**，随后点击开始等待超分即可；
![超分_01](https://raw.githubusercontent.com/SenaJun/SenaJun.github.io/refs/heads/main/img/PCR_Game_Data_Extraction/Waifu2x_04.png)

---

## 第五步：使用 rife-ncnn-vulkan 进行补帧

**注意：rife-ncnn-vulkan 引擎不需要另外下载，Waifu2x-Extension-GUI 的文件夹内自带，由于我没有买这个软件的 Pro 版本，所以需要手动操作才能得到最佳效果**

1. 打开 **Waifu2x-Extension-GUI** 目录，找到 **rife-ncnn-vulkan** 文件夹，同样建议设置 windows 环境变量以方便未来的每一次超分操作；
2. 打开 `cmd`
3. 输入 `rife-ncnn-vulkan_waifu2xEX -i "./waifu2x/"  -m rife-v4.17 -o "./output/"`
   
   * 注 01：**rife-v4.17** 模型是 **Waifu2x-Extension-GUI** 版本的 **rife-ncnn-vulkan** 才有的模型
   * 注 02：**rife-ncnn-vulkan** 的进阶操作请自行查阅官方 Github
   * 注 04：命令中仅需要填写文件路径，不需要写文件名
4. 等待补帧完成即可

---

## 第六步：使用 ffmpeg 进行合成

1. 打开 `cmd`
2. 输入 `ffmpeg -framerate 59.94 -i ".\Output\%08d.png" -c:a copy -b:v 40M -minrate 40M -maxrate 40M -bufsize 60M -c:v libx264 -pix\_fmt yuv420p ".\output.mp4"` 进行合成
   * 注 01：码率我设置的是 40M，有需要可以自己另外指定
   * 注 02：为什么文件名写的是 `%08d.png` 请看 **03-2** 的拆帧部分
   * 注 03：指定 59.94 帧率，是因为视频初始帧是 29.97
3. 等待合成完成

---

## 第七步：裁切及加长，裁切封面

1. 裁切 21:9 版本 **（此步不想做可以不做，我是因为以前自己用了几年带鱼屏，朋友也在用，所以就做了，分辨率是 3440Ⅹ1440）**
2. 发布 Youtube 版本 **这里我是加长了一个大概 1 分 10 秒长的视频，用来发布 Youtube 后可以给创意工坊添加视频**
3. 用 Photoshop 之类的工具，随便选择一帧，裁切成 1:1 的方形图，用作发布 Wallpaper Engine 的封面；**注意，封面图片大小不能超过 1MB；**

---

## 第八步：发布 Wallpaper Engine

1. 打开 **Wallpaper Engine**，左下角有一个**壁纸编辑器**，打开后有个欢迎页面，把完成品的视频拖入**创建壁纸**的蓝色大方框内即可开始编辑发布内容；
2. 随后点击左上角的**创意工坊**按钮，点击**在创意工坊上分享壁纸**后会弹出一个发布到创业工坊的窗口，以下是发布模板：

样式选择 **Anime / Game** ，这里我一直选的都是 Anime 所以就懒得改了

### 标题+描述格式：

```
16:9 プリコネR 公主连结 PrincessConnect! Re: Dive [角色中文名+角色日文完整名+英文名]

16:9 プリコネR 公主连结 PrincessConnect! Re: Dive

[h1]16:9 Princess Connect! Re: Dive Character Live Wallpaper[/h1]
[h1]プリンセスコネクトリダイブ[/h1]
[h1]超异域公主连结！Re: Dive[/h1]
[b]Resolution: 16:9 3584 x 2016[/b]
[b]Overall Bit Rate: ≈40Mb/s ± 3Mb/s

3★[角色中文名]
3★[角色日文完整名+英文名]

[b]After RealESRGAN upscaling + rife-ncnn-vulkan frame processing[/b]

[b]21:9 3440 x 1440 Resolution：[/b]
[有做的话贴上 21:9 版本的链接即可，没做就删掉]

[b]Princess Connect! Re: Dive 16:9 Collections：[/b]
https://steamcommunity.com/sharedfiles/filedetails/?id=2134024999 [有做合集的话改成自己的合集即可，没做就删掉]

[b]Princess Connect! Re: Dive 21:9 Collections：[/b]
https://steamcommunity.com/sharedfiles/filedetails/?id=2137377323 [有做合集的话改成自己的合集即可，没做就删掉]
```

### 例子：

```
16:9 プリコネR 公主连结 PrincessConnect! Re: Dive 千歌 礼服 3★チカ（儀装束） - Chika

16:9 プリコネR 公主连结 PrincessConnect! Re: Dive

[h1]16:9 Princess Connect! Re: Dive Character Live Wallpaper[/h1]
[h1]プリンセスコネクトリダイブ[/h1]
[h1]超异域公主连结！Re: Dive[/h1]
[b]Resolution: 16:9 3584 x 2016[/b]
[b]Overall Bit Rate: ≈40Mb/s ± 3Mb/s

3★千歌 礼服
3★チカ（儀装束） - Chika

[b]After RealESRGAN upscaling + rife-ncnn-vulkan frame processing[/b]

[b]21:9 3440 x 1440 Resolution：[/b]
https://steamcommunity.com/sharedfiles/filedetails/?id=3454821326

[b]Princess Connect! Re: Dive 16:9 Collections：[/b]
https://steamcommunity.com/sharedfiles/filedetails/?id=2134024999

[b]Princess Connect! Re: Dive 21:9 Collections：[/b]
https://steamcommunity.com/sharedfiles/filedetails/?id=2137377323
```
