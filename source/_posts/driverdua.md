---
title: Driver DUA 操作指南
date: 2023-11-23 14:08:04
tags: DUA
---


{% note info modern %}
微软官方文档：[Create a driver only update package](https://learn.microsoft.com/en-us/windows-hardware/test/hlk/user/create-a-driver-only-update-package)
{% endnote %}

## 什么是DUA
Driver Update Acceptable (DUA) 还不知道中文怎么翻译。可针对不同种类的计算机定做客制化INF，方便源头Driver开发者分发相同的驱动程序给不同的OEM，而不需要再通过HLK进行验证。


{% note warning flat %}
DUA 提交不允许使用以下文件类型：
.exe .dll .sys
可接受的典型文件类型包括：
.inf .txt .pdf .prd
{% endnote %}


## 下载DUA Shell
登录微软合作伙伴中心，在“硬件”页面搜索目标驱动程序，并进入详情页。点击“Download DUA Shell”按钮
![](download-dua.png)
## 使用HLK加载DUA Shell
在WHQL Server端打开HLK程序，选中右上方的“Connect”选项，在弹出的选项卡中选择“Package”，并“Browse”刚才下载的文件，打开“Open”。记得勾选“Open as Driver Update package”
![](dua-1.png)
## 替换驱动程序
选择“Package”选项卡，右键点击驱动程序路径，选择“Replace Driver”，并在新弹出的对话框中选择需要替换的驱动程序所在文件夹
![](dua-2.png)
## 重新打包
对已经替换好的驱动程序重新打包并签名
![](dua-3.png)
![](dua-4.png)
## 提交微软网站
将打包好的hlkx文件提交至微软网站审核
![](upload-dua.png)

