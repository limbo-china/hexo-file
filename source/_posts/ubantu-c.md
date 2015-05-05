title: "Ubuntu_C"
date: 2015-04-21 18:44:42
tags:
categories: Ubuntu
photos: 
---
ubuntu下编译C语言
1.平台搭建
LInux下如果单纯是进行C编译环境搭建的话，是比较容易实现的，因为系统内置了编译器gcc，所以我们要做的只不过是写好c源文件然后在进行编译就可以了

如果没有gcc编译器的话，使用以下命令获取
  ~# sudo apt-get install gcc
同时要下载辅助工具
  ~# sudo apt-get install binutils

头文件库
  ~# sudo apt-get install Llibc6-dev
<!--more-->
除了gcc外，建议新手再安装以下的帮助文件，如果在编程过程中遇到什么问题的话可以参考这些文档

C Library （用来查询语法使用方式的文档）
  ~# sudo apt-get install glibc-doc
Linux下C语言编程参考文档
  ~# sudo apt-get install glibc-doc-referenc
函数的用法说明文档
  ~# sudo apt-get install manpages-dev
用来连接多个源文件生成的目标文件的程序make
  ~# sudo apt-get install make
make程序的使用说明文档
  ~# sudo apt-get install make-doc

安装了以上的说明文档后，大家在编程中如果遇到什么问题 可以使用man命令查询帮助文档，例如：
~# man getch
~# man make
查看完帮助后，按q退出文档

关于用什么写源代码，我个人推荐使用kate，经过简单的设置之后，kate能满足编写C语言的需求，且其诸多功能也为编写与检查源文件中的错误提供了很多便利（比如颜色标记，显示行好，自动折叠等）
安装方法：
# sudo apt-get install kate

－－－－－－－－－－－－－－－－－－－－－－－
2.程序编写、编译与运行

安装好之后，你可以在应用程序>其他里找到Kate，打开后在工具菜单的语法加亮和缩进中设置成c样式，然后就可以写自己的C程序了，如：
#include <stdio.h>
int main(int argc, char **argv)
{
    system("clear");
    printf("Hello World!\n");
    return 0;
}

输入完程序后用ctrl＋S保存，我这里假设保存路径为/home/user1/桌面/helloworld/hello.c

然后就是编译，打开终端，进入目录

# cd /home/user1/桌面/helloworld/

然后用gcc进行编译
# gcc -Wall hello.c

gcc会显示编译过程中发现的问题于错误，若无错误出现则会编译成文件a.out

运行程序(a.out为编译生成的文件)
# ./a.out

这时候屏幕会显示
Hello World!
~#

表示编译运行成功


－－－－－－－－－－－－－－－－－－－
其它说明：ubuntu8.04默认不支持getch(),getchar();gets()等函数，如果大家想使用则需要安装curses库文件
#    sudo apt-get install libncurses5-dbg
#    sudo apt-get isntall libncurses5-dev

并且在写源代码时要加上
#include<curses.h>
或者在用gcc编译时加上-lcurses参数，例如：
#   gcc -Wall ./hello.c -lcurses
就可以使用getch等函数了
注意：getch函数在linux控制台下无法起到暂停程序的作用，大家可以用getchar替代getch实现这个功能

－－－－－－－－－－－－－－－－－－－－－－－－－－
小技巧：
如果编写一个比较大的程序，需要很长时间完成的话，大家可以建立一个启动器，以便快速方便的进行编译，比如你要花很多天编写一个源程序，就可以在桌面上建立一个启动器，指向c程序所在的目录，起动器命令如下(这里以C源程序在/home/user1/桌面/hello/目录下为例)

gnome-terminal  --working-directory=/home/user1/桌面/hello/

以后每次进行编译时打开此起动器，就可以直接使用gcc对源程序文件名进行编译而无需输入很长的路径了
~# gcc -Wall hello.c
~#./a.out