# Linux及其常用命令介绍

## Linux介绍

> 详询度娘

## 目录结构

### 绝对路径和相对路径

- 绝对路径

 从根目录开始

- 相对路径
  1. 目标目录相对于当前目录的位置
  2. `.`代表当前目录, `..`代表上级目录

### 文件系统

- `windows`  每个驱动器都有自己的根目录
- `linux`
  1. `/` 根目录
  2. `/bin`和`/usr/bin` `bin`是binary的缩写,  可执行二进制文件的目录. 如常用的命令`ls`,`tar`,`mv`等
  3. `/home`:  用户的家目录,用`~`表示
  4. `/lib`和`/usr/lib`和`/usr/local/lib`:  系统使用的库函数目录
  5. `/usr/include`:  头文件

## 文件权限

`-rw-r--r--  1 fqw  staff  521  7 17 10:51 sql.md`

1. 第一个字母代表文件的类型
  + `-`:  代表普通文件
  + `d`:  代表文件夹
  + `c`:  代表硬件字符设备
  + `b`:  代表硬件块设备
  + `s`:  代表socket文件
  + `p`:  代表管道文件
  + `l`:  代表软链接文件
2. 后9个字母代表三组权限: 文件所有者, 用户组, 其它组

## 命令使用方式和技巧

`命令 --help`
`man 命令`
`tab`键自动补全, 上下键查看最近命令


## 常用命令

### 文件管理

1. 查看文件`ls`
  - `-a`:  显示指定目录下所有目录与文件, 包括隐藏文件
  - `-l`:  以列表方式显示文件详细信息
  - `-h`:  配合`-l`以人性化的方式显示文件大小

2. 输出重定向`>`和`>>`
2. 分屏显示查看的文件`more`
3. 管道`|`, 清屏`clear`, 切换工作目录`cd`,显示当前路径`pwd`
4. 创建目录`mkdir`, 删除目录`rmdir`,删除文件`rm`
5. 创建软链接`ln`, `ln [-s] 源文件  链接文件`
6. 查看或者合并文件内容`cat`
7. 文本搜索`grep` `grep [-ivn] 搜索字符 文件名` , 比如在test.txt文件里查找hello, `grep hello text.txt`
8. 查找文件`find`, `find 查找路径 -name 文件名 `
9. 拷贝文件`cp`
10. 移动文件`mv`
11. 获取文件类型`file`
12. 归档管理`tar`,只负责打包, 解包,不负责压缩
13. 文件压缩解压 `gzip` `tar -zcvf xxx.tar.gz *.py` 和 `tar -zxvf xxx.tar.gz -C /xxx`
13. 文件压缩解压 `bzip2`  `tar -jcvf xxx.tar.bz2 *.py` 和 `tar -jxvf xxx.tar.bz2`
13. 文件压缩解压 `zip`和`unzip`, `unzip -d ./xxx test.zip`
14. `df -h` 显示硬盘使用情况
15. `du -h` 显示当前目录使用情况
16. `kill -9 PID`
19. 查看命令所在目录`which`

### 用户权限管理

1. 查看当前用户`who`, 查看登陆用户`whoami`和`w`, 退出登录用户`exit`, 切换用户`su`和`su -`
2. 添加,删除组用户 `groupadd`/ `groupdel`
3. 修改用户所在组 `usermod -g 用户组 用户名`,  `sudo usermod -a -G adm 用户名`
4. 添加用户账号 `useradd`, 设置用户密码`passwd`, 删除用户`userdel`, 查询用户登陆权限`last`   `sudo useradd xxx -m` `sudo passwd xxx`
5. 修改文件权限`chmod`| `chmod 777 文件名`,  修改文件所有者`chown`, 修改文件所属组`chgrp`

### 系统管理

1. 查看当前日历`cal`
2. 显示或设置时间`date`
3. 查看进程信息`ps -aux`, 动态显示进程`top`, 杀死进程`kill`, `kill -9 PID`
4. 后台程序`命令 &`, 查看后台运行程序`jobs`, `fg`
5. 关机重启 `reboot`,`shutdown -h 20:25`
6. 字符界面和图形界面切换``和`sudo service lightdm start` 命令进入图形界面
7. 显示硬盘使用情况`df -h` ,检测目录所占磁盘空间`du`
8. ubuntu应用软件安装和卸载`sudo apt-get update`和`sudo apt-get install xxx` 和`sudo apt-get remove xxx`
9. 查看或配置网卡信息`ifconfig`
10. 测试远程主机连通性`ping`
11. 网络路由设置 `route`
12. 监控网络状态 `netstat`

## vim

### vim命令模式下

- `H`:移动光标到屏幕上面
- `M`:移动光标到屏幕中间
- `L`:移动光标到屏幕下面
- `20G`: 快速回到第20行
- `gg`: 快速回到第1行
- `G`: 快速回到最后一行
- `D`: 删除到行末尾; `d0`: 删除到行首
- `r`: 替换光标上的字符, `R`: 替换光标后面的字符,
- `1,10%S/被替换的/替换的/g`
- 重复输入二次`Z`, 保存并退出, `set nu`和`set nonu`
