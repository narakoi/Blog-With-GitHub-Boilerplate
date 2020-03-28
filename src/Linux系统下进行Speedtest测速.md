---
layout: post
title: 在Linux中使用Speedtest测速完整版
slug: clashrtoswitch
date: 2020-03-28 07:21
status: publish
author: KOI
categories: 
  - Linux
tags:
  - Linux
  - speedtest
excerpt: 来测个速⑧
---

> Speedtest是Ookla推出的一款基于全球视图的可视化网速测试工具。与众不同的是它可以在一个世界地图上来选择指定的测试服务器，用绿色三角标记的是建议用来测速的服务器，白点标记的是可用测试点服务器。测试的结果显示了你连接到此服务器的上传及下载速率，网络延时等信息。

## 快速配置

```bash
wget -N --no-check-certificate https://raw.github.com/sivel/speedtest-cli/master/speedtest.py
chmod a+rx speedtest.py
python speedtest.py
```

运行脚本后如果提示

```bash
-bash: python: command not found
```

可能是因为部分Linux系统自带的是python3，这个时候我们只需要稍微修改下，将运行脚本命令修改为

```bash
python3 speedtest.py
```

代码执行结果如下（参考）

```bash
root@debian:~# python3 speedtest.py
Retrieving speedtest.net configuration...
Testing from Choopa, LLC (108.160.13x.xx)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by OPEN Project (via 20G SINET) (Tokyo) [13.54 km]: 2.292 ms
Testing download speed................................................................................
Download: 1278.77 Mbit/s
Testing upload speed......................................................................................................
Upload: 2230.29 Mbit/s

```

就能测出小鸡的运行速度叻(vu is best!



## 分享结果

有时候我们会想分享一下测速结果，如果是直接复制测速数据的话有点不太雅观，这个时候我们可以将测速结果生成一张图片并分享，只需要稍微修改下运行脚本命令

```bash
python speedtest.py --share
```

如果是python3的话就改为

```bash
python3 speedtest.py --share
```

代码执行结果如下（参考）

```bash
root@debian:~# python3 speedtest.py --share
Retrieving speedtest.net configuration...
Testing from Choopa, LLC (108.160.13x.xx)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by IPA CyberLab (Bunkyo) [14.09 km]: 2.729 ms
Testing download speed................................................................................
Download: 1003.16 Mbit/s
Testing upload speed......................................................................................................
Upload: 1574.85 Mbit/s
Share results: https://www.speedtest.net/result/9197068694.png

```

在浏览器里复制SpeedTest生成给你的图片地址：https://www.speedtest.net/result/9197068694.png

就能得到一张简洁，精美的测速图。

![vu is best！](https://www.speedtest.net/result/9197068694.png)

## 进阶配置

众所周知，SpeedTest的测速是以节点最近的一个测速点进行测速。有时候默认的测速点会很迷惑，速度经常跑不上去，这可能是由于机子ip没有被识别到正确的地址，导致测速点可能隔着一条太平洋。这个时候我们可以指定区域测速。

比如我们指定小鸡在日本区域进行测速，那么我们可以先列出日本区域的测速节点。输入指令

```bash
python speedtest.py --list | grep Japan
# python3的话使用下面这条
python3 speedtest.py --list | grep Japan
```

执行后输出如下

```bash
root@debian:~# python3 speedtest.py --list | grep Japan
24333) Rakuten Mobile , Inc (Tokyo, Japan) [13.54 km]
15047) OPEN Project (via 20G SINET) (Tokyo, Japan) [13.54 km]
28910) fdcservers.net (Tokyo, Japan) [13.54 km]
21569) i3D.net (Tokyo, Japan) [13.54 km]
14623) IPA CyberLab (Bunkyo, Japan) [14.09 km]
 8407) Allied Telesis Capital Corporation (Sagamihara, Japan) [35.57 km]
 6087) Allied Telesis Capital Corporation (Fussa-shi, Japan) [42.59 km]
 7139) SoftEther Corporation (Tsukuba, Japan) [57.04 km]
 6766) JAIST(ino-lab) (Nomi, Japan) [305.16 km]
24774) Local24 Inc., (Kyoto, Japan) [368.32 km]
 6405) Allied Telesis Capital Corporation (Misawa, Japan) [584.23 km]
18709) extride inc (Hitoyoshi, Japan) [911.19 km]
 6581) haza (Haebaru, Japan) [1549.99 km]
21118) GLBB Japan (Naha, Japan) [1551.81 km]
30230) Lequios (Naha City, Japan) [1551.81 km]
31181) Allied Telesis Capital Corp. (Okinawa, Japan) [1557.43 km]

```

前面数字代表的是测速节点的数字id，后面xxx Km指测速点与小鸡的物理距离。

比方说我们要在 i3D.net 这个测速点进行测速并分享，那么我们可以修改启动命令为

```
python speedtest.py --server 21569 --share
# python3 用下面这条
python3 speedtest.py --server 21569 --share
```

如果想要更多测速节点参考的话，可以使用命令

```
python speedtest.py --list|more
# python3
python3 speedtest.py --list|more
```

获取更多国家地区的测速节点。

