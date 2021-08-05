# Forsaken-Mail
==============
## Docker部署
#### 1、docker一键安装脚本
``` bash
wget -qO- get.docker.com | sh  #官方安装
curl -sSL https://get.daocloud.io/docker | sh  #国内daodocker安装,推荐
``` 

#### 2、容器安装邮箱
``` bash
docker run --restart=always --name forsaken-mail -d -p 25:25 -p 3000:3000 veip007/forsaken-mail
``` 
此为3000单端口（已设置开机启动容器）  不懂的话请默认此命令安装

``` bash
docker run --restart=always --name forsaken-mail -d -p 25:25 -p 80:3000 -p 1234:3000 -p 3000:3000 -p 8080:3000 veip007/forsaken-mail
```
#多端口（80,1234 3000,8080，已设置开机启动容器）



#### 3、卸载docker（忽略此步）
``` bash
apt-get remove docker-ce
```
## Linux部署

```
1、安装git
#centos
yum install git -y

#ubuntu/Debian
apt-get install git

2、安装nvm
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.0/install.sh | bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
 
3、安装nodejs和 npm
nvm install 6.10.0
 
4、查看nodejs版本是否正确，显示 6.10.0
node -v
 
5、下载项目源码
git clone https://github.com/malaohu/forsaken-mail.git
cd forsaken-mail
 
6、安装项目需要的库
npm install
 
7、安装pm2工具
npm install -g pm2
 
8、禁用postfix和sendmail
killall sendmail
/etc/init.d/postfix stop
chkconfig --level 3000 postfix off
chkconfig --level 3000 sendmail off
 
9、启动项目
pm2 start bin/www
 
10、设置开机启动
pm2 startup
pm2 save

```



#### 打开浏览器并输入
``` bash
http://localhost:3000
```


### 域名访问：
​
1. 域名解析

（1）首先MX记录：将100mail.ga的MX设定为123.123.123.123，值赋为10 

```Mail server```与```Name```都填写域名

（2）然后A记录：将100mail.ga绑到123.123.123.123


​其中100mail.ga为您域名地址。123.123.123.123为您安装好本项目的服务器IP


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

启动 ```systemctl start docker```

守护进程重启  ```sudo systemctl daemon-reload```

重启docker服务   ```systemctl restart  docker```

重启docker服务  ```sudo service docker restart```

关闭docker   ```service docker stop```   

关闭docker  ```systemctl stop docker```

#### Docker常用命令
```docker restart xxx       #重启xxx容器```

```docker stop xxx          #停止xxx容器```

```docker start xxx         #启动xxx容器```

```docker rm -v xxx         #删除xxx容器```

