# LearnDocker
这个项目是我学习Docker的一个记录
<br>
docker就是一个工具，类似于虚拟机。但是比虚拟机减少了guestos层。<br>
在linux中提供进程间的隔离。这样安全性不如虚拟机，但是效率高，适合有非常大IO开销的场合，比如数据库，web服务器等。<br>

1、在Deepin 15.11中安装Docker   
sudo apt-get install docker-ce   
注意：所有操作最好都用超级用户，否则会提示权限问题。   
2、设置启动   
#systemctl enable docker   
#systemctl start docker   
3、更换镜像源：   
#vi /etc/docker/daemon.json   
{   
"registry-mirrors": ["http://hub-mirror.c.163.com"]   
}   
#systemctl restart docker.service   
4、下载镜像   
#docker pull library/hello-world   
5、运行hello-world镜像   
#docker run hello-world   
6、查看当前镜像列表   
#docker images   
7、查看docker版本   
#docker version   
8、docker镜像默认保存位置   
/var/lib/docker/     
进入containers,每一个序列号，都是一个镜像   
9、运行交互式的容器   
我们通过docker的两个参数 -i -t，让docker运行的容器实现"对话"的能力   
runoob@runoob:~$ docker run -i -t ubuntu:15.10 /bin/bash   
10、查看正在运行的容器   
#docker ps   
11、删除不需要的容器   
#docker rmi -f 3556258649b2   
12、搜索镜像   
#docker search ubuntu   
13、查看容器所占空间、数据卷   
#docker system df   
14、运行nginx的镜像   
run --name Mywebserver -d -p 8080:80 nginx   //将80端口映射为主机的8080   
15、容器内拷贝文件   
docker cp hello.html c0462d5e1878://usr/share/nginx/html   
16、获取一个正在运行容器的shell   
docker exec -it c0462d5e1878 bash   
17、通过主机目录映射到容器   
docker run -p 80:80 -d -v $PWD/html:usr/share/nginx/html docker.io/nginx -v $PWD/html:usr/share/nginx/html   
表示把当前路径下html目录映射为usr/share/nginx/html 也就是说主机下的html就是容器下的usr/share/nginx/html html内的文件修改和添加就等同于容器usr/share/nginx/html文件操作 外网访问就可以访问得到，就不用再登录容器操作文件了   
18、停止docker   
docker stop c0462d5e1878   
19、容器内安装vim   
apt-get update   
apt-get install vim   
apt install iputils-ping   
apt install net-tools       # ifconfig    
20、导出容器快照到本地文件   
$ sudo docker ps -a   
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                    PORTS               NAMES   
7691a814370e        ubuntu:14.04        "/bin/bash"         36 hours ago        Exited (0) 21 hours ago                       test   
$ sudo docker export 7691a814370e > ubuntu.tar   
21、从容器快照文件中再导入为镜像   
$ cat ubuntu.tar | sudo docker import - test/ubuntu:v1.0   
$ sudo docker images   
REPOSITORY          TAG                 IMAGE ID            CREATED              VIRTUAL SIZE   
test/ubuntu         v1.0                9d37a6082e97        About a minute ago   171.3 MB   
22、将镜像保存为压缩包文件   
docker save nginx | gzip > nginx-latest.tar.gz   
23、加载镜像   
docker load -i nginx-latest.tar.gz   
24、将镜像从一个主机迁移到另一个主机：   
docker save hello-world | bzip2 | ssh root@10.140.1.120 "cat | docker load"   

