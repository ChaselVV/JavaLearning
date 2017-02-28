#什么是docker
Docker是一个开源的引擎，可以轻松的为任何应用创建一个轻量级的、可移植的、自给自足的容器。   
开发者在笔记本上编译测试通过的容器可以批量地在生产环境中部署，  
包括VMs（虚拟机）、bare metal、OpenStack 集群和其他的基础应用平台。    

Docker通常用于如下场景：  
* web应用的自动化打包和发布；  
* 自动化测试和持续集成、发布；  
* 在服务型环境中部署和调整数据库或其他的后台应用；  
* 从头编译或者扩展现有的OpenShift或Cloud Foundry平台来搭建自己的PaaS环境。  
	
#Docker解决什么问题  
1. 用image的概念解决环境冲突的问题。  
2. Continuous Integration/Deployment.
3. Packaging and deploying applications
4. Build your own PAAS
5. Deploy applications at hyperscale

#安装docker
apt-get install docker  
docker 使用：Build,Ship,Run  
Build Once, Run Anywhere!   --developers  
Congiure Once, Run Anywhere  

service docker start  
docker pull ubuntu


问题：root@chenvv-VirtualBox:/home/chenvv/docker# docker run ubuntu  
docker: Error response from daemon: rpc error: code = 2 desc = "oci runtime error: exec format error".  

分析原因：
应该是本地映射的目录在container中不存在导致的
看到github上有相同的错误：https://github.com/docker/docker/issues/23474

解决办法：检查本地映射的目录与container中的目录一致性（或者是否存在）  
The image that your build is based upon, resin/rpi-raspbian:wheezy-20160518, is an ARM-based image. Cross architecture image builds are not supported on Docker Hub. Only x86-based images can be built in Docker Hub/Cloud.

我的解决办法：下载32位镜像

#Docker 课程
[Docker 之道](http://edu.csdn.net/course/detail/194)

#Docker Cmd
docker search ubuntu  
docker pull ubuntu

ubuntu32位镜像制作：  
1. [下载32位ubuntu镜像](http://openvz.org/Download/template/precreated)  
2. cat ubuntu-12.04-x86-minimal.tar.gz |docker import - ubuntu-12.04  
3. docker run -i -t Ubuntu /bin/bash

docker ps –q –l  
docker stop $id  
docker start $id

#AUFS

#Docker 资源
[docker.com](https://www.docker.com/)  
[git-docker](https://github.com/docker/docker)  
[Containers-Introduction](http://lwn.net/Articles/199643/)  
[Operating-system-level_virtualization](https://en.wikipedia.org/wiki/Operating-system-level_virtualization)    
[linuxcontainers](https://linuxcontainers.org/)  
[Cgroups](https://en.wikipedia.org/wiki/Cgroups)  
[Aufs](https://en.wikipedia.org/wiki/Aufs)  
[为什么容器技术将主宰世界](http://www.kuqin.com/shuoit/20151105/348787.html)  
[10张图带你深入理解Docker容器和镜像](http://blog.csdn.net/x931100537/article/details/49633107)



