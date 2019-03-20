---
title: oninstack安装
date: 2018-08-29 19:07:11
tags: Linux
description: Linux 下搭建oninstack环境
---
1. **linux 命令**

   - 修改主机名： vi /etc/hostname
   - scp wfxAdmin.war root@39.104.48.138:/hnccnet/tomcat/cpsServer/webapps
   - mv 重命名
   - cp-r /www /aa 复制文件夹
   - chown -R www:www  XXX
   - jar-xvf  xxx.war xxx 

2. iptables

   - 关闭iptables service iptables stop  
   - 查看iptables iptables -nvL  cat/etc/sysconfig/iptables
   - ptables -I INPUT 4 -p tcp -m state --state NEW -m tcp --dport 3306 -jACCEPT
   - service iptables save #保存iptables规则

3. nginx.conf 配置

   ```nginx
   root /data/wwwroot/default;
   index index.html index.jsp; 
   location / {
     proxy_pass http://lbbzcy.xin;
   }
   ```

4. mysql 命令
   -  mysql -uroot -p
   -  source ***.sql
   -  grant all privileges on 数据库.* to 用户@'%' identified by '密码';#授权语句，特别注意有分号
   -  flush privileges;

5. tomcat   tomcat  server.xml  vhost/localhost.xml      



​	

