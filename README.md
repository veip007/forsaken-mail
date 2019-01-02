# Forsaken-Mail
==============

#### 1、docker一键安装脚本
``` bash
wget -qO- get.docker.com | sh  #官方安装
curl -sSL https://get.daocloud.io/docker | sh  #国内daodocker安装,推荐
``` 

#### 2、容器安装邮箱
``` bash
docker run --restart=always --name forsaken-mail -d -p 25:25 -p 80:3000 veip007/forsaken-mail
``` 
此为80单端口（已设置开机启动容器）

``` bash
docker run --restart=always --name forsaken-mail -d -p 25:25 -p 80:3000 -p 1234:3000 -p 3000:3000 -p 8080:3000 veip007/forsaken-mail
```
#多端口（80,1234 3000,8080，已设置开机启动容器）

#### 3、打开浏览器并输入
``` bash
http://localhost:3000
```

#### 4、卸载docker
``` bash
apt-get remove docker-ce
```

### docker常用命令

#### 关闭容器
``` bash
docker stop forsaken-mail
```

#### 删除容器
``` bash
docker rm forsaken-mail
```

#### 删除镜像
``` bash
docker rmi veip007/forsaken-mail
```

#### 列出镜像
``` bash
docker images
```

#### 删除镜像
``` bash
docker rmi  <IMAGE ID>
```

#### 列出容器
``` bash
docker ps -a
```

#### 删除容器
``` bash
docker rm  <CONTAINER ID>
```

#### 停止和删除所有Docker容器
``` bash
docker stop $(docker ps -a -q) & docker rm $(docker ps -a -q)
```
