# 实验内容：
## 1.[根据Systemd 入门教程：命令篇](http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html)完成基本操作<br>2.[根据Systemd 入门教程：实战篇](http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-part-two.html)完成相关操作<br>3.完成后的自查清单

# 具体内容:
## 一.[根据Systemd 入门教程：命令篇](http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html)完成基本操作

<br>1.systemd-analyze
```
# 查看启动耗时
$ systemd-analyze                                                                                       

# 查看每个服务的启动耗时
$ systemd-analyze blame

# 显示瀑布状的启动过程流
$ systemd-analyze critical-chain

# 显示指定服务的启动流
$ systemd-analyze critical-chain atd.service
```
[![analyze](https://asciinema.org/a/wrCzzrXm4rT6wwzOMf5oG4w5o.svg)](https://asciinema.org/a/wrCzzrXm4rT6wwzOMf5oG4w5o)

<br>2.hostnamectl
```
# 显示当前主机的信息
$ hostnamectl

# 设置主机名。
$ sudo hostnamectl set-hostname rhel7
```
[![hostnamectl](https://asciinema.org/a/RqQyTfc5kB0rWEU6ekgyHrQQv.svg)](https://asciinema.org/a/RqQyTfc5kB0rWEU6ekgyHrQQv)

<br>3.localectl
```
# 查看本地化设置
$ localectl

# 设置本地化参数。
$ sudo localectl set-locale LANG=en_GB.utf8
$ sudo localectl set-keymap en_GB
```
[![locatectl](https://asciinema.org/a/U5FVSwfEAWQ1VUFykw7oQV9bx.svg)](https://asciinema.org/a/U5FVSwfEAWQ1VUFykw7oQV9bx)

<br>4.timedatectl
```
# 查看当前时区设置
$ timedatectl

# 显示所有可用的时区
$ timedatectl list-timezones                                                                                   

# 设置当前时区
$ sudo timedatectl set-timezone America/New_York
$ sudo timedatectl set-time YYYY-MM-DD
$ sudo timedatectl set-time HH:MM:SS
```
[![timedatectl](https://asciinema.org/a/MR3TFxyN86pPVajt3ZKHIsT2e.svg)](https://asciinema.org/a/MR3TFxyN86pPVajt3ZKHIsT2e)

<br>5.loginctl
```
# 列出当前session
$ loginctl list-sessions

# 列出当前登录用户
$ loginctl list-users

# 列出显示指定用户的信息
$ loginctl show-user cuc
```
[![login](https://asciinema.org/a/yDqGuQiVQoMjJHJbkNmkfw5G9.svg)](https://asciinema.org/a/yDqGuQiVQoMjJHJbkNmkfw5G9)

<br>6.systemctl list-units
```
# 列出正在运行的 Unit
$ systemctl list-units

# 列出所有Unit，包括没有找到配置文件的或者启动失败的
$ systemctl list-units --all

# 列出所有没有运行的 Unit
$ systemctl list-units --all --state=inactive

# 列出所有加载失败的 Unit
$ systemctl list-units --failed

# 列出所有正在运行的、类型为 service 的 Unit
$ systemctl list-units --type=service
```
[![list-unit](https://asciinema.org/a/FZhQ1gzw2YCQAKsQmK3LbR1KV.svg)](https://asciinema.org/a/FZhQ1gzw2YCQAKsQmK3LbR1KV)

<br>7.Unit 的状态
```
# 显示系统状态
$ systemctl status

# 显示单个 Unit 的状态
$ sysystemctl status bluetooth.service

# 显示远程主机的某个 Unit 的状态
$ systemctl -H cuc@rhel7.example.com status httpd.service
```
[![status](https://asciinema.org/a/WzM9IGr2yhGllAnx6zNqeFe9Q.svg)](https://asciinema.org/a/WzM9IGr2yhGllAnx6zNqeFe9Q)

<br>8.Unit 管理
```

# 立即启动一个服务
$ sudo systemctl start apache.service

# 立即停止一个服务
$ sudo systemctl stop apache.service

# 重启一个服务
$ sudo systemctl restart apache.service

# 杀死一个服务的所有子进程
$ sudo systemctl kill apache.service

# 重新加载一个服务的配置文件
$ sudo systemctl reload apache.service

# 重载所有修改过的配置文件
$ sudo systemctl daemon-reload

# 显示某个 Unit 的所有底层参数
$ systemctl show httpd.service

# 显示某个 Unit 的指定属性的值
$ systemctl show -p CPUShares httpd.service

# 设置某个 Unit 的指定属性
$ sudo systemctl set-property httpd.service CPUShares=500
```
[![management](https://asciinema.org/a/ZsqLSA1oVj9v2pDzce65cNNOu.svg)](https://asciinema.org/a/ZsqLSA1oVj9v2pDzce65cNNOu)

<br>9.systemctl list-dependencies
```
$ systemctl list-dependencies nginx.service
$ systemctl list-dependencies --all nginx.service
```
[![dependencies](https://asciinema.org/a/cvXZFwccSIv1Aa6EJxxEzK245.svg)](https://asciinema.org/a/cvXZFwccSIv1Aa6EJxxEzK245)

<br>10.Unit 的配置文件
```
$ sudo systemctl enable clamd@scan.service
$ sudo systemctl disable clamd@scan.service

# 列出所有配置文件
$ systemctl list-unit-files

# 列出指定类型的配置文件
$ systemctl list-unit-files --type=service

#查看配置文件的内容
$ systemctl cat atd.service
```
[![document](https://asciinema.org/a/tzjsybPFL77dIXNIVKhQtwI3B.svg)](https://asciinema.org/a/tzjsybPFL77dIXNIVKhQtwI3B)

<br>11.Target
```
# 查看当前系统的所有 Target
$ systemctl list-unit-files --type=target

# 查看一个 Target 包含的所有 Unit
$ systemctl list-dependencies multi-user.target

# 查看启动时的默认 Target
$ systemctl get-default

# 设置启动时的默认 Target
$ sudo systemctl set-default multi-user.target

# 切换 Target 时，默认不关闭前一个 Target 启动的进程，
# systemctl isolate 命令改变这种行为，
# 关闭前一个 Target 里面所有不属于后一个 Target 的进程
$ sudo systemctl isolate multi-user.target
```
[![target](https://asciinema.org/a/BGJLRu7BkOazf5oypYLIvRvki.svg)](https://asciinema.org/a/BGJLRu7BkOazf5oypYLIvRvki)

<br>12.日志管理
```
# 查看所有日志（默认情况下 ，只保存本次启动的日志）
$ sudo journalctl

# 查看内核日志（不显示应用日志）
$ sudo journalctl -k

# 查看系统本次启动的日志
$ sudo journalctl -b
$ sudo journalctl -b -0

# 查看上一次启动的日志（需更改设置）
$ sudo journalctl -b -1

# 查看指定时间的日志
$ sudo journalctl --since="2012-10-30 18:17:16"
$ sudo journalctl --since "20 min ago"
$ sudo journalctl --since yesterday
$ sudo journalctl --since "2015-01-10" --until "2015-01-11 03:00"
$ sudo journalctl --since 09:00 --until "1 hour ago"

# 显示尾部的最新10行日志
$ sudo journalctl -n

# 显示尾部指定行数的日志
$ sudo journalctl -n 20

# 实时滚动显示最新日志
$ sudo journalctl -f

# 查看指定服务的日志
$ sudo journalctl /usr/lib/systemd/systemd

# 查看指定进程的日志
$ sudo journalctl _PID=1

# 查看某个路径的脚本的日志
$ sudo journalctl /usr/bin/bash

# 查看指定用户的日志
$ sudo journalctl _UID=33 --since today

# 查看某个 Unit 的日志
$ sudo journalctl -u nginx.service --since today

# 实时滚动显示某个 Unit 的最新日志
$ sudo journalctl -u nginx.service -f

# 合并显示多个 Unit 的日志
$ journalctl -u nginx.service -u php-fpm.service --since today

# 查看指定优先级（及其以上级别）的日志，共有8级
$ sudo journalctl -p err -b

# 日志默认分页输出，--no-pager 改为正常的标准输出
$ sudo journalctl --no-pager

# 以 JSON 格式（单行）输出
$ sudo journalctl -b -u nginx.service -o json

# 以 JSON 格式（多行）输出，可读性更好
$ sudo journalctl -b -u nginx.serviceqq
 -o json-pretty

# 显示日志占据的硬盘空间
$ sudo journalctl --disk-usage

# 指定日志文件占据的最大空间
$ sudo journalctl --vacuum-size=1G

# 指定日志文件保存多久
$ sudo journalctl --vacuum-time=1years
```
[![1](https://asciinema.org/a/650769WPbUuv4W0CXaZ5VCIzY.svg)](https://asciinema.org/a/650769WPbUuv4W0CXaZ5VCIzY)
[![2](https://asciinema.org/a/hxVqxYMnBWbYRXmIvFoil6fvw.svg)](https://asciinema.org/a/hxVqxYMnBWbYRXmIvFoil6fvw)

## 二.[根据Systemd 入门教程：实战篇](http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-part-two.html)完成相关操作
[![shizhan](https://asciinema.org/a/HxcVr7ribkXuTzH8F6gUKZev6.svg)](https://asciinema.org/a/HxcVr7ribkXuTzH8F6gUKZev6)

## 三.自查清单
1.如何添加一个用户并使其具备sudo执行程序的权限？
```
#添加用户
sudo adduser ziyi
#赋予sudo权限
sudo usermod -G sudo ziyi
```
![建新用户](https://user-images.githubusercontent.com/74172793/159149989-42abaa10-8b5b-4198-ab5c-b4c556865887.png)
![新建好了用户](https://user-images.githubusercontent.com/74172793/159150001-057676eb-0c63-4d4c-96f5-01638f31072b.png)

<br>2.如何将一个用户添加到一个用户组？
```
usermod -a -G <groupname> <username>
```

<br>3.如何查看当前系统的分区表和文件系统详细信息？
```
sudo fdisk -l 
```
![查看分区表](https://user-images.githubusercontent.com/74172793/159150104-540b20c2-d056-478d-b1c3-87698c28a4de.png)

<br>4.如何实现开机自动挂载Virtualbox的共享目录分区？
<br>首先在virtualbox的设备-共享文件夹里面设置好:
![配置](https://user-images.githubusercontent.com/74172793/159150161-a1a7c6a1-a6a4-469d-aa8b-f7ab27c12a99.png)
<br>然后在/mnt路径下新建一个share文件夹
```
cd /mnt && sudo mkdir share 
```
<br>接着用挂载口令
```
sudo mount -t vboxsf sharefile /mnt/share
```
<br>最后修改fstab文件:添加
```sharefile /mnt/share/ vboxsf defaults 0 0```就可以了
![共享文件夹](https://user-images.githubusercontent.com/74172793/159150296-a43298a0-fab9-4d9d-8a6f-104500de7923.png)

<br>5.基于LVM（逻辑分卷管理）的分区如何实现动态扩容和缩减容量？
```
lvextend -L +扩容大小 <挂载目录>
lvreduce -L -缩容大小 <挂载目录>
```

<br>6.如何通过systemd设置实现在网络连通时运行一个指定脚本，在网络断开时运行另一个脚本？
```
systemctl cat systemd-networkd.service 
systemctl daemon-reload
```
![自测6](https://user-images.githubusercontent.com/74172793/159150534-067ff051-9394-48b8-8cfd-563feb19d28d.png)

<br>7.如何通过systemd设置实现一个脚本在任何情况下被杀死之后会立即重新启动？
<br>在[Service]中修改下面的代码：
```
StartLimitIntervalSec=0
Restart=always
RestartSec=1
```

# 参考资料
·[apache - Ubuntu 'Failed to restart apache2.service: Unit apache2.service not found.'](https://stackoverflow.com/questions/62431012/ubuntu-failed-to-restart-apache2-service-unit-apache2-service-not-found)\
·[Virtualbox实现共享文件夹并自动挂载](https://blog.csdn.net/hexf9632/article/details/93774198)\
·[Linux之systemd服务配置及自动重启](https://blog.csdn.net/zong596568821xp/article/details/102739649)
