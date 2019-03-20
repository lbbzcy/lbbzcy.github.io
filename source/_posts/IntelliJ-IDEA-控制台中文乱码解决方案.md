---
title: IntelliJ IDEA 控制台中文乱码解决方案
date: 2019-02-27 14:35:06
tags:  工具使用
description: IntelliJ IDEA 控制台中文乱码解决方案。。。。。。
---

#### 配置Intellij的配置文件

![](IntelliJ-IDEA-控制台中文乱码解决方案/20190227143717.png)

idea的安装目录，修改如图配置文件。添加

```shell
-Dfile.encoding=UTF-8
```

#### 配置项目编码及IDE编码

![](IntelliJ-IDEA-控制台中文乱码解决方案/20190227144412.png)

#### 配置项目启动服务器参数

![](IntelliJ-IDEA-控制台中文乱码解决方案/20190227144538.png)