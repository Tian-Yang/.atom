#docker learning doc
## docker基础知识
###概述
>Docker 是一个开源的应用容器引擎，基于 Go 语言 并遵从 Apache2.0 协议开源。
Docker 可以让开发者打包他们的应用以及依赖包到一个轻量级、可移植的容器中，然后发布到任何流行的 Linux 机器上，也可以实现虚拟化。
容器是完全使用沙箱机制，相互之间不会有任何接口（类似 iPhone 的 app）,更重要的是容器性能开销极低。

###镜像(Image)
Docker镜像就相当于是一个root文件系统。比如官方镜像ubuntu:16.04就包含了完整的一套Ubuntu16.04最小系统的root文件系统

###容器(Container)
镜像(Image)和容器(Container)的关系，就像是面向对象程序设计中的类和实例一样，镜像是静态的定义，容器就是镜像运行的实体。容器可以被创建、启动、停止、删除、暂停等

###仓库(Repository)
仓库可以看成一个代码控制中心，用来保存镜像


##docker安装
1. 设置阿里云源镜像
```
yum-config-manager \
    --add-repo \
    http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```
2. 安装最新版本的 Docker Engine-Community 和 containerd
```
yum install docker-ce docker-ce-cli containerd.io
```
3. 安装docker
```
systemctl start docker
```
4. 删除安装包
```
yum remove docker-ce
```
5. 删除镜像、容器、配置文件等内容
```
rm -rf /var/lib/docker
```

##docker容器操作命令
查看所有容器
```
$ docker ps -a
```

启动容器
```
docker start  容器ID
```
停止容器
```
docker stop 容器ID
```
重启容器
```
docker restart 容器ID
```
进入容器方式1
```
docker attach 容器ID
//Docker attach可以attach到一个已经运行的容器的stdin，然后进行命令执行的动作。
但是需要注意的是，如果从这个stdin中exit，会导致容器的停止。
```
进入容器方式2
```
docker exec -it id ./bin/bash
```

退出容器
```
exit
//退出容器是可能出现
There are stoped jobs.
//查看运行的jobs
jobs -l
//杀死job进程
var/solr/data/Ik_core/conf# kill -9 201
```
导出容器
```
docker export 容器ID > xxx.tar
```
运行交互式容器
```
docker run -i -t ubuntu:15.10 /bin/bash
-i:允许对容器对标准输入(STDIN)进行交互
-t:在容器内指定一个伪终端
ubuntu:15.10: 镜像
```

启动容器(后台模式)
```
docker run -d ubuntu:15.10 /bin/bash
```
容器连接
```
docker run -d -p 127.0.0.1:5000:8089 training/webapp python app.py
127.0.0.1:5000映射到8089
```
容器命名
```
docker run --name
例如：
docker run -d -P --name runoob training/webapp python app.py
```

##docker镜像操作命令
列出本地主机上的镜像
```
docker images
REPOSITORY：表示镜像的仓库源
TAG：镜像的标签
IMAGE ID：镜像ID
CREATED：镜像创建时间
SIZE：镜像大小
```
查找镜像
```
docker search 镜像名称
```
获取新的镜像
```
docker pull 镜像名称
```
删除镜像
```
docker rmi 镜像名称
```
构建镜像,需要创建dockerFile

为镜像添加标签
```
docker tag IMAGE ID REPOSITORY:tag名称
例如：
docker tag 860c279d2fec runoob/centos:dev
docker仓库管理
```
1. docker仓库注册账户
https://hub.docker.com

2. 登陆docker

##docker安装软件
1. 拉去镜像
```
docker pull 镜像名:版本号
```
2. 查看已安装镜像
```
docker images
```
3. 运行镜像容器
```
docker run -itd --name mysql-test -p 3306:3306 -e MYSQL_ROOT_PASSWORD=666666 mysql
//-p 3306:3306 ：映射容器服务的 3306 端口到宿主机的 3306 端口，外部主机可以直接通过 宿主机ip:3306 访问到 MySQL 的服务。
//MYSQL_ROOT_PASSWORD=123456：设置 MySQL 服务 root 用户的密码。
```
4. 查看是否安装成功
```
docker ps
```

###安装centos
```
docker pull centos:latest
docker images
docker run -itd --name centos-test centos
docker ps
```
###安装mysql
```
docker pull mysql:last
docker images
docker run -itd --name mysql-test -p 3306:3306 -e MYSQL_ROOT_PASSWORD=666666 mysql
docker ps
mysql -h localhost -u root -p
```
