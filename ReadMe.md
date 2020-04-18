  Linux使用指南  || Ubuntu 16.04
  =============
  
  ## 书签导航
  
  
  [github上面MD文件书写格式说明](https://blog.csdn.net/buzaiQQ/article/details/78182639)
  
  [Ubuntu 快速入门1](https://www.jianshu.com/p/a18e55110cc4)
  
  [Ubuntu 快速入门2](https://blog.csdn.net/Jessica__Land/article/details/80654199)
  
  [Ubuntu 快速入门3](https://blog.csdn.net/chaoshengze/article/details/78012827)

## 使用技巧

  [有线网络连接（校园网）](https://blog.csdn.net/Caoyang_He/article/details/82262199)
  
  https://blog.csdn.net/guaijiaodie2064/article/details/83041721
  
  
## 常用命令

**快捷命令**
```
Terminal
打开命令窗      Ctrl + Alt + T
中断命令行运行 Ctrl + C
命令补全 Tab
复制粘贴 Ctrl + Shift + C/V

CD命令
切换当前目录至指定的目录： cd [目录名]
  cd /   返回根目录
  cd ..  返回上一级目录
  cd ~   从当前目录进入当前用户主目录
  cd -   从当前目录进入上次所在目录
  cd ../.. 返回上两级目录

切换回图形界面  [Ctrl]+[Alt]+[F7] 
进入字符界面    Ctrl + Alt + F1 #不建议使用
添加注释       在命令行后加 #blablabla
锁屏/显示登录对话框  ctrl+alt+L	
关闭应用程序窗口  Ctrl+Q

```

**文件操作**
```
查看文件内容 cat name.c
创建文件.c  touch name.c
显示当前文件 ls
显示当前路径 pwd
创建一个目录 mkdir 目录名
删除一个文件 rm 文件名
删除一个目录 rm -r命令 待删除目录
复制目录或文件 cp test.txt /home/ubuntu/downloads/newdir    cp -r 复制目录 指定目录
移动目录或文件 mv test newdir 将文件 test 移动到 newdir目录
重命名        mv test test1 将文件 test 重命名为 test1
```
**软件安装**
```
更新源   sudo apt-get upgrade/update #注意两者区别，前者更新软件，后者更新软件源列表
安装软件 sudo apt-get install 软件名
```

**文件存储**
```
查看磁盘剩余空间: df -hl
```  


## 磁盘挂载
/usr 挂靠了许多库文件，空间应给足


## 软件安装

  [搜狗输入法](https://www.cnblogs.com/darklights/p/7722861.html)
  
  [谷歌浏览器](https://baijiahao.baidu.com/s?id=1622595992346821550&wfr=spider&for=pc&isFailFlag=1&tdsource)
  
## 设置配置

 **下载源**:设置 software 中 downloa from改成 中国的阿里云或者清华大学镜像，优先选**阿里云**的软件源，目前为Ubuntu中文社区官方推荐。

**Ros安装Kinetic-desktop-full**

[Ubuntu16.04下安装ROS Kinetic并启动小乌龟示例](https://blog.csdn.net/qq_17232031/article/details/79519308)

**Ubuntu 16.04下的gcc/g++编译环境搭建及第一个C和C++示例程序运行**

命令窗口内直接运行C/C++程序。

[参考教程1](https://www.linuxidc.com/Linux/2019-04/158258.htm)

[参考教程2](http://c.biancheng.net/cpp/html/3418.html)

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

**第一个C和C++示例程序运行**

````
// C程序
/*  *****
#include <stdio.h>
int main()
{
  puts("Hello World of C!");
  return 0;
}

******* */

// C++程序
/*  *****

#include <iostream>
using namespace std;

int main()
{
   cout << "Hello World of C++!" << endl;
   return 0;
}

******* */

1. 创建.c文件
随便找一个目录建立文件。
2. 编译文件
  c文件尽量用gcc编译
  cpp（C++）用g++编译
3. 运行
  方法1：直接把这个文件拖到Terminal上，通过按回车键运行
  方法2：./test_main.out 直接按路径下的文件打开运行

命令如下：
touch main.c #创建
gedit main.c #复制上段代码,编辑保存
gcc main.c -o test_main #编译mian.c，以test_main为名，输出的文件格式后缀为.out

touch main.cpp #创建
gedit main.cpp #复制上段代码,编辑保存
gcc main.cpp -o test_main #编译mian.pp，以test_main为名，输出的文件格式后缀为.out

````
