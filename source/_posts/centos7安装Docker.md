---
title: centos7安装Docker
date: 2018-09-03 21:52:56
tags: Linux
categories: Linux
description: 本文介绍了在centos7环境下面安装docker的步骤和注意事项。。。。。。
---

1. Docker版本 : 

   * 社区版（CE）:Docker Community Edition（CE）非常适合希望开始使用Docker并尝试使用基于容器的应用程序的个人开发人员和小型团队。
   * 企业版（EE）: Docker企业版（EE）专为企业开发和IT团队而设计，他们可以在生产中大规模构建，发布和运行业务关键型应用程序。

2. Docker安装方式：

   安装之前需要卸载旧版本 

   ```shell
   $ sudo yum remove docker \
                     docker-client \
                     docker-client-latest \
                     docker-common \
                     docker-latest \
                     docker-latest-logrotate \
                     docker-logrotate \
                     docker-selinux \
                     docker-engine-selinux \
                     docker-engine
   ```

   * 使用存储库安装

     * 设置存储库

       * 安装所需的包。`yum-utils`提供了`yum-config-manager` 效用，并`device-mapper-persistent-data`和`lvm2`由需要 `devicemapper`存储驱动程序。

         ```shell
         $ sudo yum install -y yum-utils \
           device-mapper-persistent-data \
           lvm2
         ```

       * 使用以下命令设置稳定存储库。即使您还想从边缘或测试存储库安装构建，您始终需要稳定的存储 库。

         ``` shell
         $ sudo yum-config-manager \
             --add-repo \
             https://download.docker.com/linux/centos/docker-ce.repo
         ```

       * 可选：启用边缘和测试存储库。这些存储库包含在docker.repo上面的文件中，但默认情况下处于禁用状态。您可以将它们与稳定存储库一起启用。

         ```shell
         $ sudo yum-config-manager --enable docker-ce-edge
         $ sudo yum-config-manager --enable docker-ce-test
         ```

     * 设置存储库

       1. 安装最新版本的Docker CE，或转到下一步安装特定版本：

          ```shell
          $ sudo yum install docker-ce
          ```

       2. 要安装特定版本的Docker CE，请列出repo中的可用版本，然后选择并安装：

          一个。列出并对您的仓库中可用的版本进行排序。此示例按版本号对结果进行排序，从最高到最低，并被截断

          ``` shell
          $ yum list docker-ce --showduplicates | sort -r
          docker-ce.x86_64            18.03.0.ce-1.el7.centos             docker-ce-stable
          $ sudo yum install docker-ce-<VERSION STRING>
          ```

       3. 尚未启动。该docker组已创建，但没有用户添加到该组。

          ```shell
          $ sudo systemctl start docker
          ```

   * 从包安装

     1. 转到 https://download.docker.com/linux/centos/7/x86_64/stable/Packages/ 并下载.rpm要安装的Docker版本的文件。

     2. 安装Docker CE，将下面的路径更改为您下载Docker软件包的路径。

        ```
        $ sudo yum install /path/to/package.rpm
        ```

        Docker已安装但尚未启动。该docker组已创建，但没有用户添加到该组。

     3. 启动Docker。

        ```shell
        $ sudo systemctl start docker
        ```

     4. docker通过运行hello-world 映像验证是否已正确安装。

        ```shell
        $ sudo docker run hello-world
        ```

   * 使用便利脚本安装

     ```shell
     $ curl -fsSL https://get.docker.com -o get-docker.sh
     $ sudo sh get-docker.sh
     
     <output truncated>
     
     If you would like to use Docker as a non-root user, you should now consider
     adding your user to the "docker" group with something like:
     
       sudo usermod -aG docker your-user
     
     Remember to log out and back in for this to take effect!
     
     WARNING: Adding a user to the "docker" group grants the ability to run
              containers which can be used to obtain root privileges on the
              docker host.
              Refer to https://docs.docker.com/engine/security/security/#docker-daemon-attack-surface
              for more information.
     ```

   * 卸载Docker CE

     * 卸载Docker包：

       ```shell
       $ sudo yum remove docker-ce
       ```

     * 主机上的图像，容器，卷或自定义配置文件不会自动删除。要删除所有图像，容器和卷：

       ```shell
       $ sudo rm -rf /var/lib/docker
       ```