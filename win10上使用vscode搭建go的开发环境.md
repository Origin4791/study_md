# 				win10上使用vscode搭建go的开发环境

# 1. 下载安装包

- ### go安装包：https://golang.google.cn/dl/

- ### vscode安装包：https://code.visualstudio.com/

# 2. 安装过程

## 2.1  go的安装：

- 一定要记住go的安装路径，后面配置环境变量的时候需要用到

  ![](C:\Users\xiaotong.xie\AppData\Roaming\Typora\typora-user-images\image-20211126104159412.png)

## 2.2 vscode安装

一路next吧，好像没什么问题

## 2.3 环境变量的配置

- 系统变量里新增一个GOPATH环境变量，值就是你存放go代码的路径（一般是新建一个路径里面放go项目。该目录下有bin、pkg、source三个目录）
- path里面加两个值，分别是你安装的go的bin目录（上图的位置）和GOPATH的位置

## 2.4  go项目目录

在进行`Go`语言开发的时候，我们的代码总是会保存在`$GOPATH/src`目录下。在工程经过`go build`、`go install`或`go get`等指令后，会将下载的第三方包源代码文件放在`$GOPATH/src`目录下， 产生的二进制可执行文件放在 `$GOPATH/bin`目录下，生成的中间缓存文件会被保存在 `$GOPATH/pkg` 下。

## 2.5 vscode的安装go插件

- 按下 `Ctrl+Shift+P`  在输入框中输入go:install，选择Go:Install/Update Tools这个命令，然后全选所有的插件。然后安装即可

- 一般都会安装失败，需要添加代理，打开powershell输入

- ```shell
  # 配置 GOPROXY 环境变量
  $env:GOPROXY = "https://goproxy.io,direct"
  # 还可以设置不走 proxy 的私有仓库或组，多个用逗号相隔（可选）
  $env:GOPRIVATE = "git.mycompany.com,github.com/my/private"
  ```

- 保持上述设置长期有效的方式：

- ```text
  1. 右键 我的电脑 -> 属性 -> 高级系统设置 -> 环境变量
  2. 在 “[你的用户名]的用户变量” 中点击 ”新建“ 按钮
  3. 在 “变量名” 输入框并新增 “GOPROXY”
  4. 在对应的 “变量值” 输入框中新增 “https://goproxy.io,direct”
  5. 最后点击 “确定” 按钮保存设置
  ```

##  





### 