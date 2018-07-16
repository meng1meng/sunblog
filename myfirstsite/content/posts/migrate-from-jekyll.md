---
date: 2018-07-13
linktitle: docker
title: docker
weight: 10
---

http://my.ishadowx./net

docker常用命令pull，run，exec，ps，kill，images，build，push，tag
# 起一个镜像的操作：
## docker help
    docker pull nginx  下载镜像
daocloud--hub.docloud.io镜像市场
    docker pull daocloud--hub.docloud.io
可以在公司内部私有库下载镜像，在网址上下载。
    docker images|grep nginx查一下镜像的名字
## docker run -d 镜像名  启动镜像
-e加环境变量
-p8080:80  指定端口本地8080端口映射到服务器的80端口
## docker ps查看镜像  进程
nginx与Tomcat，Apache类似，服务器，80,81端口
## 打开镜像地址：
    docker-machine.exe env查看所有环境变量
## winpty docker exec -it  运行的容器中进到这个容器
winpty 是指在Windows下
## exit退出
## docker kill 进程号  杀进程，可以通过docker ps查看
# Dockerfile构建一个镜像
在以上基础上的文件下，在本地创建一个nginx文件夹，创建一个Dockerfile的文件夹，里面有from，run。是基于刚才的镜像创建的一个新的镜像。
分享过在微信文件助手中
## docker build 构建一个镜像可以通过help查看具体操作
-t +镜像名 构建
    docker images|grep nginx
通过指定端口可以在服务器上显示镜像的内容
## push把本地的镜像推到远程
    docker push注册可以推到远程服务器上
docker login hub.docker.com
## docker tag 镜像名  给镜像打标签
练习：使用docker起一个MySQL的镜像：
.私库中找到MySQL镜像
网页上输入https://registry.saas.hand-china.com，找到MySQL--least最新复制直接在dockertoolbox运行
（1）docker pull registry.saas.hand-china.com/tools/mysql:5.6下载镜像
docker pull registry.saas.hand-china.com/tools/nginx:latest
（2）docker images|grep mysql查看镜像名
（3）docker run --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root -d registry.saas.hand-china.com/tools/mysql 5.6 
--name重新命名为mysql,后面的长串是镜像的名字
（3）docker ps查看ID，即images为registry.saas.hand-china.com/tools/mysql 5.6  ，name为mysql的镜像ID。
（4）winpty docker exec -it f5d8 //bin/bash  进入mysql容器


