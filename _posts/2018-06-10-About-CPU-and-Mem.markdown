---
layout:     post
title:      About the cpu and mem
subtitle:   "top and pstack"
date:       2018-06-10 12:00:00
author:     "Chao"
header-img: "img/post-bg-2015.jpg"
tags:
    - Linux
---



  在多线程的程序中，如果出现了cpu和内存过高。 比价难以判断到底是哪个线程的的哪个函数造成的。而用几个linux命令：__ps__ ,  __top__ , __pstack__ 相结合,可以比较好的辅助我们定位到问题的根源。

 1. ps命令查看程序PID
```shell
ps -ef | grep eventinput | grep -v "eventinput"
```
![ps](http://pa5sgvs11.bkt.clouddn.com/ps.PNG)
这里要分析的程序名称为`eventinput`s。

2.top命令查看程序的cpu,mem利用情况
```shell
top -Hp 35624
```
![top](http://pa5sgvs11.bkt.clouddn.com/top.PNG)
其中， `-H`的作用是展示进程号35624下的每一个线程
![top -Hp](http://pa5sgvs11.bkt.clouddn.com/top1.PNG)
3.pstack命令查看堆栈信息
```shell
pstack 35624
```
![pstack](http://pa5sgvs11.bkt.clouddn.com/pstack.PNG)
pstack用法比较简单，后面跟线程号。没有其它任何参数。如果pstack后加父进程号，则会打印父进程和所有子线程的堆栈信息。为了单独看某子线程的信息，可以pstack后直接加该子线程号。例如，`top -Hp`展示的六个线程中，PID为35634的线程cpu,内存较高，可以用`pstack`命令单独看该线程的堆栈信息。
```shell
pstack 35634
```
![pstack](http://pa5sgvs11.bkt.clouddn.com/pstack1.PNG)
多次重复运行该命令， 可以看到函数`MAddMinuteOfMinute`一直在运行中。
根据以上信息，大体可以掌握程序的运行大体状况。可以辅助我们找到异常情况的根源。
