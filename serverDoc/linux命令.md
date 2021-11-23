#linux命令

安装程序
```
yum instal xxx
```
安装后查看目录，例如查看ant安装目录
```
whereis ant
```
查看程序运行目录，例如查看ant运行目录
```
which ant
```
查找程序包所在的位置,例如查找ant-launcher.jar的位置
```
find / -name ant-launcher.jar
```
配置环境变量
```
vi /etc/profile 或 open /etc/profile
```
环境变量配置示例
```
export ANT_HOME=/usr/share/ant
export PATH=$PATH:$ANT_HOME/bin
```
环境变量生效
```
source /etc/profile
```
端口命令
```
lsof -i:8080  查看8080端口是否开通
netstat -aptn 查看所有开通的端口
```

运行程序
```
systemctl start xxx,例如 systemctl start docker
```
