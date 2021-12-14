# 					root修改密码

## 1. 普通用户修改密码：

passwd命令，然后按照提示修改即可

## 2. root 修改普通账户密码

passwd username，例如passwd xxt然后修改即可

## 3. 无视密码规则强制修改密码

- 切换到root账户

- 使用echo命令，echo "密码" | passwd --stdin 用户

   ` echo "xxt" | passwd --stdin xxt `

  有时会报Have exhausted maximum number of retries for service这个问题，出现这个问题后就使用

  ```
  echo '用户:密码' |chpasswd
  例如
  echo 'xxt:xxt'|chpasswd
  ```

  

