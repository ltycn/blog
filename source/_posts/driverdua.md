---
title: Driver DUA 操作指南
date: 2023-11-23 14:08:04
tags: DUA
---


{% note info modern %}
微软官方文档：[Create a driver only update package](https://learn.microsoft.com/en-us/windows-hardware/test/hlk/user/create-a-driver-only-update-package)
{% endnote %}

# 什么是DUA
Driver Update Acceptable (DUA) 还不知道中文怎么翻译。可针对不同种类的计算机定做客制化INF，方便源头Driver开发者分发相同的驱动程序给不同的OEM，而不需要再通过HLK进行验证。


{% note warning modern %}
注意：
DUA 提交不允许使用以下文件类型：

.exe
.dll
.sys
可接受的典型文件类型包括：

.inf
.txt
.pdf
.prd
{% endnote %}


# 下载DUA Shell
![](download-dua.png)
# 使用HLK加载DUA Shell
![](dua-1.png)
# 替换驱动程序
![](dua-2.png)
# 重新打包
![](dua-3.png)
![](dua-4.png)
# 提交微软网站
![](upload-dua.png)

