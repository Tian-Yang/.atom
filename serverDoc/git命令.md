#git命令
##github基础设置
1. 设置username和email（github每次commit都会记录他们）
>git config --global user.name "tianYang"
>git config --global user.email "739558011@qq.com"

2. 通过终端命令创建ssh key
>ssh-keygen -t rsa -C "739558011@qq.com"

3. 打开创建生成的id_rsa.pub文件(公钥)
>vi .ssh/id_rsa.pub
4. 复制id_rsa.pub中的key
5. 访问github,访问Settings>SSH and GPG kyes>New SSH key，将公钥复制进文本框
6. 验证ssh连接，ssh -T git@github.com
7. 如果使用jenkins，将私钥 id_rsa复制到jenkins中
