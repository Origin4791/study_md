# 1. 查看所有分支 ： 

## git branch -r 或者git branch -a

# 2.指定分支克隆：

## git clone -b develop 链接

# 3. 切换到某个分支：

## git checkout -b origin/develop(切换到develop分支)

# 4. 在某个分支上新建分支：

## git checkout -b xxtong(在当前分支上新建xxtong分支，注意前面没有origin)

# 5. 将该分支推到线上：

## git push origin xxtong(将xxtong分支推到线上)

# 6.删除某个分支

## git push origin --delete xxt_dev(删除远程的xxt_dev分支)

## git branch -d xxtong（删除本地的xxtong分支）

