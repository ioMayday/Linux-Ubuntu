  Ubuntu使用指南
  =============
  
  ## 书签导航
  
  
  [github上面MD文件书写格式说明](https://blog.csdn.net/buzaiQQ/article/details/78182639)
  
  [Ubuntu 快速入门1](https://www.jianshu.com/p/a18e55110cc4)
  
  [Ubuntu 快速入门2](https://blog.csdn.net/Jessica__Land/article/details/80654199)
  
  [Ubuntu 快速入门3](https://blog.csdn.net/chaoshengze/article/details/78012827)

## 使用技巧

  [有线网络连接（校园网）](https://blog.csdn.net/Caoyang_He/article/details/82262199)
  
  **Gcc编译搭建C/C++开发环境（命令窗口内运行）**
  
  http://c.biancheng.net/cpp/html/3418.html
  
  
## 软件安装

  [搜狗输入法](https://www.cnblogs.com/darklights/p/7722861.html)
  
  [谷歌浏览器](https://baijiahao.baidu.com/s?id=1622595992346821550&wfr=spider&for=pc&isFailFlag=1&tdsource)
  
## 设置配置

 **下载源**:设置 software 中 downloa from改成 中国的阿里云或者清华大学镜像，优先选**阿里云**的软件源，目前为Ubuntu中文社区官方推荐。

**Ros安装Kinetic-desktop-full**
[Ubuntu16.04下安装ROS Kinetic并启动小乌龟示例](https://blog.csdn.net/qq_17232031/article/details/79519308)

**gcc/g++编译环境搭建**
[参考教程](https://www.linuxidc.com/Linux/2019-04/158258.htm)

功能：已安装Gcc后，再安装不同的gcc和g++版本，并设置根据不同的需要在不同版本之间切换。

背景知识：[the difference betwen gcc and g++ ](https://www.zhihu.com/question/20940822)

````
Ctrl + Alt + T, Open the Terminal Window.
Only have brief introduction to key steps! 

1. 环境准备
首先需要安装ｇcc和ｇ++环境,安装之前查看是否有安装,使用命令:

gcc --version
g++ --version


2. 不同版本安装
# 版本安装：这里选择版本8
# 8代表版本，可换成5或者7等其他版本，较常用的低版本 5.3.0（python的CUDA3.0支持的编译器）

$ sudo apt install gcc-8
$ sudo apt install g++-8

3. 查看已安装的不同版本

$ ls /usr/bin/gcc*


4. 为各版本设置不同优先级

# gcc
$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-8 30
$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-7 40
$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-5 50

# g++
$ sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-8 30
$ sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-7 40
$ sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-5 50

5. 查看并设置默认版本

# gcc
$ sudo update-alternatives --config gcc

# g++
$ sudo update-alternatives --config g++

要维持当前值[*](当前*表示的是默认状态)，请按<回车键>。
要更改默认版本，键入选择的编号回车即可。

6. 查看默认版本更改是否生效

gcc --version
g++ --version

````
