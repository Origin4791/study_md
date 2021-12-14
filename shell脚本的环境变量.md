#   								shell脚本的环境变量

## 1. 查看环境变量

- ### printenv：列出当前bash的环境变量

  - #### printenv  PATH:指定打出某个变量的值（一般我们想看的就是PATH的值）

  - #### printenv | less :由于一般环境变量都比较多，所以需要上下翻页来看，使用less命令既可以使用键盘或者鼠标上下滚动来看环境变量了（详情查看less的用法）

- ### export   ：列出当前所有的环境变量，当然也可以使用less来上下滚动查看，或者grep来查看某个特定的变量

  

## 2. 环境变量部分解读

- SHELL : shell 程序的名字

- HOME : 用户家目录

- LANG : 定义了字符集以及语言编码方式

- OLD PWD : 先前的工作目录

- PATH : 由冒号分开的目录列表，**<u>当你输入可执行程序名后，会搜索 这个目录列表</u>**

- PWD : 当前工作目录

- USER : 你的用户名

  

## 3.  shell配置文件解析

1. **登录用户**读取的启动文件

- /etc/profile ： 应用于所有用户的全局配置脚本
- ˜/.bash profile ： 当前用户的启动文件（~表示当前用户的家目录）
- ˜/.bash login ： 如果文件 ˜/.bash profile 没有找到，bash 会尝试读取这个脚本

2. **非登录用户**读取的启动文件，除了读取以上启动文件之外，非登录 shell 会话也会继承它们父进程的环境设置，通常是一
   个登录 shell

- /etc/bash.bashrc ： 应用于所有用户的全局配置文件
- ˜/.bashrc ：  当前用户的启动文件

3. 在 GUI 模式下运行终端会话时，非登录 shell 会话会出现，在 GUI 模式下运行终端会话时，非登录 shell会话会出现。在用户看来，***∼/.bashrc是最重要的文件，***因为无论是登录shell还是非登录shell都会先读取这个文件，所以现在我们最好就修改这个文件（因为公司的服务器一般都是没有gui的，所以一般修改 bash profile文件也可 ）

   

## 4. bash profile文件解析

![](C:\Users\xiaotong.xie\AppData\Roaming\Typora\typora-user-images\image-20211110181915446.png)

- 以 “#” 开头的行是注释，shell 不会读取它们

- ```
  if [ -f ~/.bashrc ];
  then . ~/.bashrc 
  fi
  ```

  上述这句话的意思翻译如下，即如果有.bashrc的时候就先读这个文件

  ```
  If the file ~/.bashrc exists, then read the ~/.bashrc file.
  
  ```

- shell脚本会从配置文件中找到PATH这个变量，这个变量一般保存可执行程序的路径，比如我们打ls这个命令，shell就会先从PATH目录下找到/bin/ls，然后就可以执行ls命令

- 使用参数展开的方式修改PATH变量

  ```
  [me@linuxbox ~]$ foo="This is some" 
  [me@linuxbox ~]$ echo $foo 
  This is some 
  [me@linuxbox ~]$ foo="$foo text." 
  [me@linuxbox ~]$ echo $foo 
  This is some text.
  ```

  $ foo 就是变量所对应的值，下面这行代码就是

  ```
  PATH=$PATH:$HOME/bin
  ```

  

