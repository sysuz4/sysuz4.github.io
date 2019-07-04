# 易闲圈 后台部署文档
springboot + Nginx + mysql

---

## 一、 部署架构图
![deploy](https://github.com/ArtemisZGL/sysuz4.github.io/blob/master/img/backend.png?raw=true)
---

## 二、 部署流程

### 1.1 服务器系统环境
- 阿里云 Ubuntu 16.04 LTS Server
  
### 1.2 Docker 安装
- [官方参考链接](https://docs.docker.com/install/linux/docker-ce/ubuntu/#prerequisites)

- [中文参考链接](https://yeasy.gitbooks.io/docker_practice/content/install/ubuntu.html)

- 亦可参考以下命令进行安装
```
$ sudo apt-get update

$ sudo apt-get install \
    linux-image-extra-$(uname -r) \
    linux-image-extra-virtual
$ sudo apt-get update

$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
$ sudo add-apt-repository \
    "deb [arch=amd64] https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu \
    $(lsb_release -cs) \
    stable"
$ sudo apt-get update

$ sudo apt-get install docker-ce
$ sudo systemctl enable docker
$ sudo systemctl start docker

```

若通过上面链接中给出的安装测试 `sudo docker run hello-world` ，则证明安装成功。

### 1.3 Mysql-Client 安装
`sudo apt install mysql-client`

## 2.服务器程序配置运行

### 2.1 拉取后台源代码并创建相关目录

在root文件夹下创建swsad文件夹，并拉取后台源码（其它路径也行，不过后面的命令要相应的进行更改）放置到swsad文件夹中
```
mkdir swsad  

git clone https://github.com/sysuz4/AppServer

mv /AppServer/* /swsad/
```

### 2.2 创建数据库
使用源码中的schema-utf8.sql进行数据库的创建

```
mysql -u root -p

输入密码

set password for root@localhost = password('Swsad123456'); 

create database yxq;

use yxq;

source schema-utf8.sql;
```

### 2.3 使用docker配置启动nginx
由于nginx除了作为反向代理服务器之外，还作为静态文件服务器，因此通过docker创建nginx容器时还要进行文件目录等的挂载


1.搜索nginx镜像  
` docker search nginx`

2.拉取nginx镜像  
` docker pull nginx`

3.创建启动容器  
` docker run --name nginx -d --net=host -p 80:80 -v /root/swsad/images:/images nginx`

4.配置nginx
将源码中的配置文件复制到docker容器中  
` sudo docker cp /root/swsad/default.conf nginx:/etc/nginx/conf.d/ `

### 2.4 使用docker配置启动服务器
通过源码中的dockerfile创建镜像并运行

```
cd /root/swsad

docker build -t yxq:zgl

docker run -d --net=host -p 9999:9999 --privileged=true -v /root/swsad/images:/images --name yxq-1.0 yxq:zgl

```
