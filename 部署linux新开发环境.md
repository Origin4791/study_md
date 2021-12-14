# 一. 软件资源下载

## 1. 从服务器上下载相关的安装包，目前需要的是virtualBox虚拟机和centos7镜像

## 2.服务器ip：10.253.48.29  kode/kode



# 二.安装虚拟机和centos操作系统

## 1. virtualBox就一路‘下一步’下去即可，如果实在不会就百度一下

## 2. 安装centos（其实就是给centos配置一些参数）

### 	 （1）这里推荐最小化安装，安装一个无图形界面的版本即可，如果实在不会，建议参考下面的链接：https://blog.csdn.net/weixin_45115705/article/details/100538773

###  	（2）建议在安装的过程中就设置root的密码和新建一个账号，这样后面会方便很多（只是建议而已）

### 	（3）其中最关键的就是联网，之前网络设置错了浪费了很多时间，网络配置见下所示

- 在virtualbox中设置当前机器的连接方式是网络地址转换（NAT）模式

- 进入centos里面修改下网络配置文件 

- ```
  cd /etc/sysconfig/network-scripts/
  ```

- 我的该级目录如下所示：![image-20210825153022825](C:\Users\xiaotong.xie\AppData\Roaming\Typora\typora-user-images\image-20210825153022825.png)

- 我使用的是无线网，所有修改ifcfg-enp0s3即可（不同机器的名字可能不一样，但基本上长得都差不多）

- vi 这个文件然后将最后一行ONBOOT改为yes在保存退出即可

- ![image-20210825153236307](C:\Users\xiaotong.xie\AppData\Roaming\Typora\typora-user-images\image-20210825153236307.png)

- 最后重启下网络服务然后在ping百度看看能不能ping通

- ```
  systemctl restart network （centos7 之前的版本命令是service network restart）
  ```

  ### （4）查看网络问题的方法

  - ipconfig看看当前网络的情况，如果提示该命令不可用时就说明没有安装ifconfig

    

    (5)linux用户添加sudo权限

    https://blog.csdn.net/qq_39290007/article/details/81125750

    （6）修改虚机的硬盘大小

    https://blog.csdn.net/weixin_30077373/article/details/116584915

    出错的时候使用下面的链接

    https://blog.csdn.net/chongke5244/article/details/100737114/

    （7）virbox安装增强功能
    https://blog.csdn.net/cigan3637/article/details/100621213
    无法复制粘贴可能是因为设备->共享粘贴板没有设置双向

    （8）winscp或者vscode连接上虚拟机（不要设置端口转发）
    + 网络设为NAT模式
    + vi /etc/sysconfig/network-scripts/ifcfg-enp0s3 将ONBOOT改为yes在重启网络service network restart
    + 配置端口转发。链接见下
    + https://www.cnblogs.com/lhat/p/6838206.html
    
  
    

