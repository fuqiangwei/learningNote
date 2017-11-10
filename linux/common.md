# linux 常见问题

## linux

- `sudo service lightdm start` 命令进入图形界面
- `tar -zcvf xxx.tar.gz *.py` 和 `tar -zxvf xxx.tar.gz -C /xxx`
- `tar -jcvf xxx.tar.bz2 *.py` 和 `tar -jxvf xxx.tar.bz2`
- `unzip -d ./xxx test.zip`
- `kill -9 PID`
- `df -h` 显示硬盘使用情况
- `du -h` 显示当前目录使用情况
- `sudo useradd xxx -m` `sudo passwd xxx`
- `sudo usermod -a -G adm 用户名`
- `chmod 777 文件名`

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
