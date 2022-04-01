# 实验要求
## 任务一：用bash编写一个图片批处理脚本，实现以下功能：
* ☑️支持命令行参数方式使用不同功能

* ☑️支持对指定目录下所有支持格式的图片文件进行批处理指定目录进行批处理

* ☑️支持以下常见图片批处理功能的单独使用或组合使用

    * ☑️支持对jpeg格式图片进行图片质量压缩

    * ☑️支持对jpeg/png/svg格式图片在保持原始宽高比的前提下压缩分辨率

    * ☑️支持对图片批量添加自定义文本水印

    * ☑️支持批量重命名（统一添加文件名前缀或后缀，不影响原始文件扩展名）
  
    * ☑️支持将png/svg图片统一转换为jpg格式

## 任务二：用bash编写一个文本批处理脚本，对以下附件分别进行批量处理完成相应的数据统计任务：
* ☑️统计不同年龄区间范围（20岁以下、[20-30]、30岁以上）的球员数量、百分比

* ☑️统计不同场上位置的球员数量、百分比

* ☑️名字最长的球员是谁？名字最短的球员是谁？

* ☑️年龄最大的球员是谁？年龄最小的球员是谁？

## 任务三：用bash编写一个文本批处理脚本，对以下附件分别进行批量处理完成相应的数据统计任务：
* ☑️统计访问来源主机TOP 100和分别对应出现的总次数

* ☑️统计访问来源主机TOP 100 IP和分别对应出现的总次数

* ☑️统计最频繁被访问的URL TOP 100

* ☑️统计不同响应状态码的出现次数和对应百分比

* ☑️分别统计不同4XX状态码对应的TOP 10 URL和对应出现的总次数

* ☑️给定URL输出TOP 100访问来源主机

## 所有源代码文件必须单独提交并提供详细的-help脚本内置帮助信息<br>任务三的所有统计数据结果要求写入独立实验报告

# 实验内容
### test01.sh
* 写脚本test01.sh
![01](https://user-images.githubusercontent.com/74172793/161087916-39573311-61a8-4a98-8f03-249b860e5eb2.png)
* 运行结果
![test01-result](https://user-images.githubusercontent.com/74172793/161185253-93cc4519-e499-4a64-be4e-f6c5f7d30da1.png)

### test02.sh
* 下载所需文件
```bash
wget "https://c4pr1c3.gitee.io/linuxsysadmin/exp/chap0x04/worldcupplayerinfo.tsv"
```
* 写脚本test02.sh
![02](https://user-images.githubusercontent.com/74172793/161089203-74fdcf37-e403-4986-9c3d-38db39522599.png)
* 运行结果
![02 1](https://user-images.githubusercontent.com/74172793/161089674-137f2209-3952-4e35-b3f6-f721e08afa7b.png)

### test03.sh
* 下载并解压指定文件
```bash
wget "https://c4pr1c3.gitee.io/linuxsysadmin/exp/chap0x04/worldcupplayerinfo.tsv"
tar -xvf worldcupplayerinfo.tsv.tar.gz
```
* 写脚本
![03](https://user-images.githubusercontent.com/74172793/161090576-f218f786-17d3-4718-bdbf-74489f7281f7.png)
* 运行结果<br>
[test03.md](/chap0x04/test03.md)


# 参考资料


