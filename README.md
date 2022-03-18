# 2022-linux-public-dangyuyan
2022-linux-public-dangyuyan created by GitHub Classroom
# 作业要求
·记录发行版基本信息、记录内核版本基本信息\
·新添加网卡实现开机自动启动和获取IP\
·scp传输文件
·ssh免密登录

# 1.
```
//查看发行版基本信息
lsb -release -a 
```
![outversion](https://user-images.githubusercontent.com/74172793/156969556-177822f2-e36d-46cd-8991-d137cf910c9c.png)

```
//查看内核版本信息
uname -a
```
![inversion](https://user-images.githubusercontent.com/74172793/156969531-0dcd67e9-4b62-4b80-9602-a838f1359434.png)

# 2.
现在虚拟机设置里面添加网卡3，在命令行输入```ifconfig```查看正在工作的所有网卡，发现新加的网卡不在里面
![workingnet](https://user-images.githubusercontent.com/74172793/156969591-40ed1591-6da5-4c9e-9cc2-4a3f88ee8c55.png)
![allnet](https://user-images.githubusercontent.com/74172793/156969463-bbcc2359-49c1-4653-ac16-3d9dc42a4a19.png)
接着用
```
cd /etc/netplan
ls
```
找到安装文件
![find](https://user-images.githubusercontent.com/74172793/156969518-21070c40-d91d-4d08-8ffd-f89f516da004.png)
再用
```
sudo vi /etc/netplan/00-installer-config.yaml
```
进行网卡添加操作
![addnewnet](https://user-images.githubusercontent.com/74172793/156969462-d95ab3d8-d34f-4780-a948-0b4ebb50dadb.png)
保存退出后再用```ifconfig```查看显示已经在工作中了
![networkdone](https://user-images.githubusercontent.com/74172793/156969547-e74e48f6-f14c-4db3-996d-6456a39fa08c.png)

# 3.
用下面的代码实现将本机文件复制到远程服务器上
```
scp /home/administrator/（本地文件的绝对路径）news.txt（要复制的文件） root@192.168.6.129:（远程服务器的ip）/etc/squid（将文件复制到位于远程服务器上的路径）
```
eg：在虚拟机中建一个txt文件并找到它的路径
![addatxt](https://user-images.githubusercontent.com/74172793/156969753-3c5c0c7c-3e30-4ce0-8f45-a9d6c215107a.png)
用
```
scp -r cuc@192.168.56.101:/home/cuc ./
```
将文件复制到本机桌面上
![scptodesktop](https://user-images.githubusercontent.com/74172793/156969577-fb131027-d6b7-4452-b568-e5cf76a5b29b.png)
![copy](https://user-images.githubusercontent.com/74172793/156969505-c5d52d17-d895-4a07-bf22-1f9430b642b0.png)

# 4.
使用
```
ssh-keygen -t rsa
```
生成本机的公私钥；
![ssh-keygen](https://user-images.githubusercontent.com/74172793/156969582-708640b3-1cde-44d6-b329-1498a1858afe.png)
接着用
```
ssh-copy-id cuc@192.168.56.101
```
把主机上生成的公钥传到cuc@192.168.56.101中；
![copy-id](https://user-images.githubusercontent.com/74172793/156969509-fc9ac19c-8718-4907-8601-47b0c9de61c6.png)
就搞定了~
![done](https://user-images.githubusercontent.com/74172793/156969514-520df096-4a29-47f2-a3f7-c9aafaa39791.png)

# 参考资料
·[win10SSH免密](https://zhuanlan.zhihu.com/p/401327519)\
·[查看网卡](https://www.runoob.com/linux/linux-comm-ifconfig.html)\
·[ubuntu网卡启动](https://jingyan.baidu.com/article/9113f81b7995df2b3214c702.html)
