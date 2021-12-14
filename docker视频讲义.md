#    									docker视频讲义

# 1. 常见名词

- 镜像（image）：相当于一个模板，通过这个模板可以创建容器服务，通过一个镜像可以创建多个容器
- 容器（container）：服务或者项目都是运行在容器上的，容器可以启动，删除，禁止等
- 仓库（repository）：存放镜像的地方

# 2. 安装docker

## 2.1 方法

完全根据docker的官方文档来安装，具体地址见下：https://docs.docker.com/engine/install/centos/

## 2.1  查看环境

```
To install Docker Engine, you need a maintained version of CentOS 7 or 8. Archived versions aren’t supported or tested.
```

官方文档说必须是centos 7以上，所以安之前要弄清楚目前服务器的版本：cat /etc/os-release

![](C:\Users\xiaotong.xie\AppData\Roaming\Typora\typora-user-images\image-20211210152036254.png)

## 2.2 卸载老版本的docker

```
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

## 2.3 安装docker需要的相关仓库

```dockerfile
 sudo yum install -y yum-utils
 sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo  # d这里是官方的地址（国外的）
 sudo yum-config-manager \
	--add-repo \
	https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo # 推荐使用（国内的阿里云镜像，比较快，尽量安装这个）
```

## 2.4 更新yum软件包

```
yum makecache fast
```

## 2.5  安装docker

```
sudo yum install docker-ce docker-ce-cli containerd.io
```

## 2.6 配置镜像加速

- 注册个阿里云账号，https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors

- 执行图片中的命令即可

  ![](C:\Users\xiaotong.xie\AppData\Roaming\Typora\typora-user-images\image-20211210171744876.png)

- 检查加速器是否生效：sudo docker info

  ![](C:\Users\xiaotong.xie\AppData\Roaming\Typora\typora-user-images\image-20211210171915461.png)

## 2.7 启动docker

```
sudo systemctl start docker
docker version
```

## 2.8 确认docker安装成功

```
sudo docker run hello-world
```

## 2.9 卸载

```dockerfile
sudo yum remove docker-ce docker-ce-cli containerd.io   # 删除应用
sudo rm -rf /var/lib/docker    # 删除下载的包
sudo rm -rf /var/lib/containerd
```

# 3. docker的常用命令

## 3.1 帮助命令

```dockerfile
docker version
docker info
docker 命令 --help
官网帮助文档的地址：https://docs.docker.com/reference/
```

## 3.2 镜像命令

```
docker images ：查看所有本地的主机上的镜像（注意是images不是image）
docker search + 镜像： 在docker hub上搜索镜像
docker pull + 镜像：在docker上下载镜像
   不加 tag 的时候默认下载最新版，一般可以在镜像名称后面加个版本号下载指定版本，比如docker pull mysql 5.7
docker rmi -f + 镜像：删除镜像（可以通过镜像名称，也可以是镜像id）
   骚操作删除：docker rmi -f $(docker images -aq) $表示把（）里面的东西当作参数传进去
```

## 3.3 容器命令

### 3.3.1   docker  run 

参数说明:

- --name="name" : 给容器个名字开区分容器
- -d ：后台方式运行，相当于nobup
- -it ：使用交互方式运行，进入容器内查看内容
- -P : 指定容器的端口
  - -P ：主机端口：容器端口。例如 8080：8080（最常用）
  - -P ：容器端口
  - -P ：ip：主机端口：容器端口
- -p ：随机指定端口

