---
title: gitlab搭建
date: 2019-01-24 16:32:26
tags: Linux
comments:
description: 本文介绍了在linux操作系统下安装gitlab的命令。。。。。。
---

1. 配置yum源
   vim /etc/yum.repos.d/gitlab-ce.repo

   复制以下内容：

    [gitlab-ce]

   name=Gitlab CE Repository

   baseurl=[https://mirrors.tuna.tsinghua.edu.cn/gitlab-ce/yum/el$releasever/](https://mirrors.tuna.tsinghua.edu.cn/gitlab-ce/yum/el$releasever/)

   gpgcheck=0

   enabled=1

2. 更新本地yum缓存

   sudo yum makecache

3. 安装GitLab社区版

   sudo yum install gitlab-ce        #自动安装最新版
   sudo yum install gitlab-ce-x.x.x    #安装指定版本

4. GitLab常用命令

   sudo gitlab-ctl start    # 启动所有 gitlab 组件；
   sudo gitlab-ctl stop        # 停止所有 gitlab 组件；
   sudo gitlab-ctl restart        # 重启所有 gitlab 组件；
   sudo gitlab-ctl status        # 查看服务状态；
   sudo gitlab-ctl reconfigure        # 启动服务；
   sudo vim /etc/gitlab/gitlab.rb        # 修改默认的配置文件；
   gitlab-rake gitlab:check SANITIZE=true --trace    # 检查gitlab；
   sudo gitlab-ctl tail        # 查看日志；

   安装：

   ```
   $ curl -fsSL get.docker.com -o get-docker.sh #下载get-docker.sh文件
   $ sudo sh get-docker.sh --mirror Aliyun #以阿里云镜像安装get-docker.sh脚本内容
   ```

   ------

   调优：

   ```
   $ sudo systemctl enable docker #开机启动docker
   $ sudo systemctl start docker #启动docker
   $ sudo groupadd docker #建立docker组
   $ sudo usermod -aG docker $USER #将当前用户加入 docker 组
   $ sudo vim /etc/systemd/system/multi-user.target.wants/docker.service #添加下面仓库地址到此文件
   ExecStart=/usr/bin/dockerd --registry-mirror=https://ckq4qobq.mirror.aliyuncs.com  #使用阿里云加速
   $ sudo systemctl daemon-reload #重新加载daemon
   $ sudo systemctl restart docker  #重启docker
   ```

   验证：

   ```shell
   $ sudo docker run --name webserver -d -p
   81:80 nginx 
   #docker从仓库pull下nginx镜像并命名为webserver，此镜像以后台模式，81端口映射宿主机80端口运行
   #如果下载速度较慢，可能国内镜像加速未成功。
   $ firefox #打开firefox浏览器
   #输入  localhost：81  看到nginx欢迎界面表示搭建成功
   ```