---
title: shadowsocks实现翻墙
date: 2019-01-28 18:49:30
tags: Linux
toc: true
description: Linux 下搭建服务器实现翻墙。。。。。。
---

#### 一、环境介绍：

　　1、服务器：

　　　　CentOS7.0_x86_64

　　2、Windows客户端

　　　　Windows 10

#### 二、安装部署：

  1、安装Shadowsocks服务端：

 ```shell
   # yum update
   # yum install python-setuptools && easy_install pip
   # pip install shadowsocks
 ```

 2、配置Shadowsocks：

  此文件默认不存在，需要创建：

 ```shell
 # vim /etc/shadowsocks.json
 {
     "server":"your_server_ip",
     "server_port":8388,
     "password":"yourpassword",
     "timeout":300,
     "method":"aes-256-cfb",
     "fast_open":false,
     "workers": 1
 }
 注：有的简化版centos 不识别 vim 命令，请先安装 vim 
 
 \# yum install vim -y
 
 上面代码的解释：
 server：服务器 IP地址 (IPv4/IPv6)
 
 server_port：服务器监听的端口，一般设为80，443等，注意不要设为使用中的端口
 
 password：设置密码，自定义
 
 timeout：超时时间（秒）
 
 method：加密方法，可选择 “aes-256-cfb”, “rc4-md5”等等。推荐使用 “rc4-md5”
 
 fast_open：true 或 false。如果你的服务器 Linux 内核在3.7+，可以开启 fast_open 以降低延迟。
 
 workers：workers数量，默认为 1
 　　
 ```

3、多用户配置

 如要你需要分享SS服务给朋友或家人，可以配置多个SS账户，具体可以参考下面的代码。

 ```
 {
 	"server":"your_server_ip",
     "port_password":{
         "8381":"pass1", 
         "8382":"pass2",
         "8383":"pass3",
         "8384":"pass4"
     },
     "timeout":60,
     "method":"rc4-md5",
     "fast_open":false,
     "workers":1
 }
 注意：json的格式，注意空格和Tab的用法要一致！
 ```

 　4、启动Shadowsocks：

```shell
# ssserver -c /etc/shadowsocks.json -d start
INFO: loading config from /etc/shadowsocks.json
2017-01-10 22:38:12 WARNING  warning: your timeout 60 seems too short
2017-01-10 22:38:12 INFO     loading libcrypto from libcrypto.so.10
started
```

```shell
5、加入开机自启：
修改下面文件
# vim  /etc/rc.d/rc.local
加入下面内容
/usr/bin/ssserver -c /etc/shadowsocks.json -d start
保存并推出 vim, CentOS 7正打算抛弃/etc/rc.d/rc.local，重启前需要运行以下命令获得权限，否则rc.local不会执行     
# chmod +x /etc/rc.d/rc.local
```

####  三、使用Windows客户端连接测试：

```
1、下载Shadowsocks客户端：
2、配置Shadowsocks客户端
```

![](G:\编程资料\日记\shadowsocks客户端配置.png)

具体信息如下：

```shell
服务器IP  ：your_server_ip
服务器端口 ：8381
密码: pass1
加密：rc4-md5
```

```
3.访问谷歌，看是否成功
```

   https://www.google.com/



__推荐一个海外服务器地址：https://www.vultr.com/?ref=7539196 比较好用，适合自己搭建vpn。速度很快。__