#docker 安装指南
##docker安装
1. 设置阿里云源镜像
>yum-config-manager \
    --add-repo \
    http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
2. 安装最新版本的 Docker Engine-Community 和 containerd
>yum install docker-ce docker-ce-cli containerd.io
3. 安装docker
>systemctl start docker
4. 删除安装包
>yum remove docker-ce
5. 删除镜像、容器、配置文件等内容
>rm -rf /var/lib/docker

##docker容器操作命令
查看所有容器
>$ docker ps -a

启动容器
>docker start  容器ID

停止容器
>docker stop 容器ID

重启容器
>docker restart 容器ID

进入容器
>docker attach 容器ID

退出容器
>docker exec -it 容器ID /bin/bash

导出容器
>docker export 容器ID > xxx.tar

运行交互式容器
>docker run -i -t ubuntu:15.10 /bin/bash
-i:允许对容器对标准输入(STDIN)进行交互
-t:在容器内指定一个伪终端
ubuntu:15.10: 镜像

启动容器(后台模式)
>docker run -d ubuntu:15.10 /bin/bash

容器连接
>docker run -d -p 127.0.0.1:5000:8089 training/webapp python app.py
127.0.0.1:5000映射到8089

容器命名
>docker run --name
例如：
docker run -d -P --name runoob training/webapp python app.py



##docker镜像操作命令
列出本地主机上的镜像
>docker images
REPOSITORY：表示镜像的仓库源
TAG：镜像的标签
IMAGE ID：镜像ID
CREATED：镜像创建时间
SIZE：镜像大小

查找镜像
>docker search 镜像名称

获取新的镜像
>docker pull 镜像名称

删除镜像
>docker rmi 镜像名称

构建镜像,需要创建dockerFile

为镜像添加标签
>docker tag IMAGE ID REPOSITORY:tag名称
例如：
docker tag 860c279d2fec runoob/centos:dev

docker仓库管理

1. docker仓库注册账户
https://hub.docker.com

2. 登陆docker
