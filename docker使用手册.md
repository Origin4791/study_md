# 									docker使用手册

## 1.  centos安装docker：

​	sudo yum install docker

## 2. docker安装以后无法使用docker pull命令：

好像是因为没有启动docker，使用如下命令即可（一般第一条启动就好了），执行完后用ps -ef查看docker进程在不在就行了

```
sudo -
systemctl start docker
systemctl enable docker
systemctl restart docker
```

有一个小tips，每次使用docker前必须启动docker，使用 sudo systemctl start docker启动docker，如果

## 3. 普通用户必须使用sudo命令才可以使用docker命令

## 4. docker的常用命令

- ```dockerfile
  docker pull ubuntu:18.04     # 获取镜像
  可以使用docker pull --help查看docker pull的作用
  ```

- ```bash
  docker run -it --rm ubuntu:18.04 bash    # 运行镜像
  ```

- ```dockerfile
  docker image ls     # 列出已经下载的镜像(顶层镜像)
  docker image ls -a  # 列出所有的镜像
  docker image ls -f  # 使用-f来筛选东西
  ```

- ```dockerfile
  docker image rm [选项] <镜像1>
  # 镜像1可以是短ID， 长ID， 镜像名， 或者 镜像摘要，docker image ls默认列出的就是短id，一般取前3个字符就好了，只要可以区分别的镜像就好了
  ```

- ```dockerfile
  docker run --name webserver -d -p 80:80 nginx
  # 用 nginx 镜像启动一个容器，命名为 webserver，并且映射了 80 端口
  docker exec -it webserver bash 
  # docker exec 交互式终端方式进入 webserver 容器，并执行了 bash 命令，也就是获得一个可操作的 Shell
  ```

- ```dockerfile
  docker diff webserver
  # 通过 docker diff 命令看到具体的改动
  ```

## 5.  Dockerfile的写法

