# LearnDocker
这个项目是我学习Docker的一个记录
<br>
docker就是一个工具，类似于虚拟机。但是比虚拟机减少了guestos层。<br>
在linux中提供进程间的隔离。这样安全性不如虚拟机，但是效率高，适合有非常大IO开销的场合，比如数据库，web服务器等。<br>
通常在服务器发行版中都支持了。<br>
例如在CentOS7中。<br>
安装如下<br>
yum install  docker<br>
完成后启动服务如下<br>
service docker start<br>
配置服务随机启动<br>
chkconfig docker on<br>
在新版CentOS中可以使用如下命令启动<br>
systemctl start docker.service<br>
systemctl enable docker.service<br>
查找可用的镜像<br>
docker  search  centos/ubuntu/<br>

