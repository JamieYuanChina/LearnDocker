# LearnDocker
这个项目是我学习Docker的一个记录

docker就是一个工具，类似于虚拟机。但是比虚拟机减少了guestos层。
在linux中提供进程间的隔离。这样安全性不如虚拟机，但是效率高，适合有非常大IO开销的场合，比如数据库，web服务器等。
通常在服务器发行版中都支持了。
例如在CentOS7中。
安装如下
yum install  docker
完成后启动服务如下
service docker start
配置服务随机启动
chkconfig docker on
在新版CentOS中可以使用如下命令启动
systemctl start docker.service
systemctl enable docker.service
查找可用的镜像
docker  search  centos/ubuntu/

