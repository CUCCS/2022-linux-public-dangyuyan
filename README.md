|      版本    | ubuntu                 | CentOS     |
| ---        |    ----              |          ---   |
| 安装应用      | ```apt install```        | ```yum install -y```   |
| 卸载应用      |```sudo apt-get --purge remove tshark```        | ```yum remove ```     |
|查看安装路径|```dpkg -L tmux```|```rpm -qal \| grep ``` |
|查找文件名|```sudo find / -name '*666*'```|``` find / -name '*666*'```|
|查找文件内容|```sudo grep -r '666'./ --exclude=*.cast```|```find . \| xargs grep -ri '666'```|
|zip压缩与解压缩|```zip ```<br>```unzip -o```|```zip```<br>```unzip -o```|
|gzip压缩与解压缩|```gzip```<br>```gzip -dv```|```gzip```<br>```gzip -dv```|
|tar压缩与解压缩|```tar -cvf```<br>```tar -xvf```|```tar -cvf```<br>```tar -xvf```|
|bzip2压缩与解压缩|```bzip2```<br>```bunzip2```|```bzip2```<br>```bunzip2```|
|7z压缩与解压缩|```7z a -t7z -r```<br>```7z x 1.7z -r -o./```|```7za a -t7z ```<br>```7za x 1.7z -r -o./```|
|rar压缩与解压缩|```rar a```<br>```rar x```|```wget http://rarlab.com/rar/rarlinux-x64-5.3.0.tar.gz --no-check-certificate```<br>```tar解压```<br>```cd rar```<br>```make```<br>```rar a ```<br>```rar x```|
|硬件信息获取|```cat /proc/cpuinfo \|grep 'model name'获取目标系统CPU```<br>```cat /proc/meminfo \|grep MemTotal 查看内存大小```<br>```sudo fdisk -l \|grep Disk查看硬盘信息```|```grep 'model name'/proc/cpuinfo获取目标系统CPU```<br>```grep MemTotal /proc/meminfo获取内存大小```<br>```fdisk -l \|grep Disk查看硬盘信息```|

# 详细内容：
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

# CentOS版本
![版本](https://user-images.githubusercontent.com/74172793/158055777-add0e4b9-d521-4853-89a6-30654886742a.png)

## 1.【软件包管理】
```
#安装
yum install tmux
```
```
#卸载
yum remove tshark
```
![看安装路径](https://user-images.githubusercontent.com/74172793/158056603-0e875cb5-c58b-4a85-9307-2b69ac21b67f.png)


## 2.【文件管理】
![文件名](https://user-images.githubusercontent.com/74172793/158056614-27a69dc6-b6b0-4793-ba08-7e7bb3d02620.png)
![内容](https://user-images.githubusercontent.com/74172793/158056618-20dcbb07-4705-4c64-9e33-d9711111336c.png)

## 3.【文件压缩与解压缩】

（1）zip
![zip](https://user-images.githubusercontent.com/74172793/158056630-2dbd3cac-e199-4a64-9821-048f35a6da8f.png)
![unzip](https://user-images.githubusercontent.com/74172793/158056642-fd3790fb-f42e-45b2-962e-de236d1bbd10.png)

（2）gzip
![gzip](https://user-images.githubusercontent.com/74172793/158056657-e822db6f-f49f-406b-b407-ae2fb41b6cf1.png)

（3）tar
![tar](https://user-images.githubusercontent.com/74172793/158056667-fed677e9-0ad3-4c17-842e-43f038047775.png)

（4）bzip2
![bzip2](https://user-images.githubusercontent.com/74172793/158056675-bfb399c3-f2c3-4b4d-870a-a93f19efb559.png)

（5）7z
![7z](https://user-images.githubusercontent.com/74172793/158056682-a84b355b-6712-4800-91c2-69b3a14ef4e3.png)
![7z2](https://user-images.githubusercontent.com/74172793/158056684-a4cab255-7cd5-4d54-b69c-a3a3eddbeb83.png)

（6）rar
先查看内核版本，看是32位还是64位
![rar1](https://user-images.githubusercontent.com/74172793/158056690-19b6239f-f99a-4fd0-bee3-3aff945f0033.png)
然后用```wget http://rarlab.com/rar/rarlinux-x64-5.3.0.tar.gz --no-check-certificate```下载压缩包
![rar2](https://user-images.githubusercontent.com/74172793/158056691-e35d9956-229c-49c4-8f94-59ef7e012923.png)
用tar把压缩包解压
![rar3](https://user-images.githubusercontent.com/74172793/158056692-3d9b6d36-6add-442a-9593-1cd0441a6bf4.png)
切换到rar路径，make配置
![rar4](https://user-images.githubusercontent.com/74172793/158056693-e52a8c9c-48dd-423c-b780-0633676a08bd.png)
然后就可以使用rar了
![rar5](https://user-images.githubusercontent.com/74172793/158056694-3b21789d-0f3a-44b0-9076-4cb88155d9e2.png)

## 4.【子进程管理】
![ping](https://user-images.githubusercontent.com/74172793/158056708-8cec3641-2e63-47e0-b042-050baa5f38a3.png)
![ping2](https://user-images.githubusercontent.com/74172793/158056709-a8598998-eefb-45bd-aba9-76724dac0ee3.png)

## 5.【硬件信息获取】
![硬件信息](https://user-images.githubusercontent.com/74172793/158056727-1bda7745-196b-4f9b-805b-4af69e633ff4.png)

# 参考资料
·[如何查找文件](https://jingyan.baidu.com/article/3065b3b6b28b7cbecff8a4e8.html)\
·[查找硬件信息](https://blog.csdn.net/qq_15437629/article/details/51601521)\
·[centos解压rar](https://www.php.cn/centos/446562.html)
