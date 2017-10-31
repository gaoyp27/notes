Docker 学习笔记
---
一、
1、添加docker源

cat>> /etc/yum.repos.d/docker-main.repo <<EOF
[docker-main]
name=docker-main
baseurl=http://mirrors.aliyun.com/docker-engine/yum/repo/main/centos/7/
gpgcheck=1
enabled=1
gpgkey=http://mirrors.aliyun.com/docker-engine/yum/gpg
EOF

2、更新源和升级系统

yum makecache && yum update -y

3、卸载旧版本docker

yum remove -y docker*

4、列出所有版本

yum list docker-engine  --showduplicates |sort -r
[root@localhost yum.repos.d]# yum list docker-engine –showduplicates |sort -r
* updates: centos.ustc.edu.cn
Loading mirror speeds from cached hostfile
Loaded plugins: fastestmirror
* extras: centos.ustc.edu.cn
docker-engine.x86_64 1.9.1-1.el7.centos         docker-main
docker-engine.x86_64 1.9.0-1.el7.centos         docker-main
docker-engine.x86_64 1.8.3-1.el7.centos         docker-main
docker-engine.x86_64 1.8.2-1.el7.centos         docker-main
docker-engine.x86_64 1.8.1-1.el7.centos         docker-main
docker-engine.x86_64 1.8.0-1.el7.centos         docker-main
docker-engine.x86_64 1.7.1-1.el7.centos         docker-main
docker-engine.x86_64 17.03.0.ce-1.el7.centos docker-main
docker-engine.x86_64 1.7.0-1.el7.centos         docker-main
docker-engine.x86_64 1.13.1-1.el7.centos       docker-main
docker-engine.x86_64 1.13.0-1.el7.centos       docker-main
docker-engine.x86_64 1.12.6-1.el7.centos       docker-main
docker-engine.x86_64 1.12.5-1.el7.centos       docker-main
docker-engine.x86_64 1.12.4-1.el7.centos       docker-main
docker-engine.x86_64 1.12.3-1.el7.centos       docker-main
docker-engine.x86_64 1.12.2-1.el7.centos       docker-main
docker-engine.x86_64 1.12.1-1.el7.centos       docker-main
docker-engine.x86_64 1.12.0-1.el7.centos       docker-main
docker-engine.x86_64 1.11.2-1.el7.centos       docker-main
docker-engine.x86_64 1.11.1-1.el7.centos       docker-main
docker-engine.x86_64 1.11.0-1.el7.centos       docker-main
docker-engine.x86_64 1.10.3-1.el7.centos       docker-main
docker-engine.x86_64 1.10.2-1.el7.centos       docker-main
docker-engine.x86_64 1.10.1-1.el7.centos       docker-main
docker-engine.x86_64 1.10.0-1.el7.centos       docker-main
* base: mirrors.cn99.com
Available Packages

5、安装指定版本

sudo yum -y install docker-engine-<VERSION_STRING>
sudo yum -y install docker-engine-selinux-<VERSION_STRING>
PS:安装docker-engine 时安装对应版本的docker-engine-selinux 
