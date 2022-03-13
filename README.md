# ubuntu20.04版本
## 1.【软件包管理】
（1）tmux
```
#查看安装版本
apt-cache policy tmux
```
```
#查看被安装到了哪个路径上
dpkg -L tmux
```
[![tmux](https://asciinema.org/a/tvqAXSLyC4NX0zps4OWv6Pz0B.svg)](https://asciinema.org/a/tvqAXSLyC4NX0zps4OWv6Pz0B)

 ps：因为查看tmux的时候发现已经安装了，就没再装一遍

（2）tshark
[![tshark](https://asciinema.org/a/v4kQS2ymIa3C3RVkuN96cEU6K.svg)](https://asciinema.org/a/v4kQS2ymIa3C3RVkuN96cEU6K)

## 2.【文件管理】
```
#查找文件名包含666的文件
sudo find / -name '*666*'
```
```
#查找文件内容包含666的文件
sudo grep -r '666'./ --exclude=*.cast
```
[![666](https://asciinema.org/a/3BC5lYph9DG0oi2WZbVEUosiF.svg)](https://asciinema.org/a/3BC5lYph9DG0oi2WZbVEUosiF)

## 3.【文件压缩与解压缩】

（1）zip
用```zip```压缩，用```unzip```解压缩
[![zip](https://asciinema.org/a/2p2wtCbPJjvS6P1OWqNmqzUgG.svg)](https://asciinema.org/a/2p2wtCbPJjvS6P1OWqNmqzUgG)

（2）gzip
用```gzip```压缩，用```gzip -dv```解压缩
[![gzip](https://asciinema.org/a/KThm8ajbFznwNNRqH6cOneiBD.svg)](https://asciinema.org/a/KThm8ajbFznwNNRqH6cOneiBD)

（3）tar
用```tar -cvf```压缩，用```tar -xvf```解压缩
[![tar](https://asciinema.org/a/c9Z44efrhqNZQAD9aPJRp7JFb.svg)](https://asciinema.org/a/c9Z44efrhqNZQAD9aPJRp7JFb)

（4）bzip2
用```bzip2```压缩，用```bunzip2```解压缩
[![bzip2](https://asciinema.org/a/ZHoSoDuZYAmscXIv9t5LPb7wd.svg)](https://asciinema.org/a/ZHoSoDuZYAmscXIv9t5LPb7wd)

（5）7z
用```7z a -t7z -r```压缩，用```sudo 7z x 1.7z -r -o./ ```解压缩
[![7z](https://asciinema.org/a/yIHBeasVJ4ves6WXnBn4DhFk5.svg)](https://asciinema.org/a/yIHBeasVJ4ves6WXnBn4DhFk5)

（6）rar
用```sudo rar a```压缩，用```sudo rar x```解压缩
[![rar](https://asciinema.org/a/mLt70cv980FAaHpKogWhm5KJ1.svg)](https://asciinema.org/a/mLt70cv980FAaHpKogWhm5KJ1)

## 4.【子进程管理试验】
[![子进程管理](https://asciinema.org/a/z4H6os6Gyj8wImGuri45MMx3e.svg)](https://asciinema.org/a/z4H6os6Gyj8wImGuri45MMx3e)

## 5.【硬件信息获取】
```
#获取目标系统的CPU信息
cat /proc/cpuinfo |grep 'model name'
```
```
#获取内存大小
cat /proc/meminfo |grep MemTotal 
```
```
#获取硬盘数量和容量信息
sudo fdisk -l |grep Disk
```
[![硬件信息获取](https://asciinema.org/a/EGPnZHPLj05TlaTjTsFW5O5bo.svg)](https://asciinema.org/a/EGPnZHPLj05TlaTjTsFW5O5bo)
