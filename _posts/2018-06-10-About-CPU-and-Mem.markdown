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



  �ڶ��̵߳ĳ����У����������cpu���ڴ���ߡ� �ȼ������жϵ������ĸ��̵߳ĵ��ĸ�������ɵġ����ü���linux���__ps__ ,  __top__ , __pstack__ ����,���ԱȽϺõĸ������Ƕ�λ������ĸ�Դ��

 1. ps����鿴����PID
```shell
ps -ef | grep eventinput | grep -v "eventinput"
```
![ps](http://pa5sgvs11.bkt.clouddn.com/ps.PNG)
����Ҫ�����ĳ�������Ϊ`eventinput`s��

2.top����鿴�����cpu,mem�������
```shell
top -Hp 35624
```
![top](http://pa5sgvs11.bkt.clouddn.com/top.PNG)
���У� `-H`��������չʾ���̺�35624�µ�ÿһ���߳�
![top -Hp](http://pa5sgvs11.bkt.clouddn.com/top1.PNG)
3.pstack����鿴��ջ��Ϣ
```shell
pstack 35624
```
![pstack](http://pa5sgvs11.bkt.clouddn.com/pstack.PNG)
pstack�÷��Ƚϼ򵥣�������̺߳š�û�������κβ��������pstack��Ӹ����̺ţ�����ӡ�����̺��������̵߳Ķ�ջ��Ϣ��Ϊ�˵�����ĳ���̵߳���Ϣ������pstack��ֱ�ӼӸ����̺߳š����磬`top -Hp`չʾ�������߳��У�PIDΪ35634���߳�cpu,�ڴ�ϸߣ�������`pstack`����������̵߳Ķ�ջ��Ϣ��
```shell
pstack 35634
```
![pstack](http://pa5sgvs11.bkt.clouddn.com/pstack1.PNG)
����ظ����и���� ���Կ�������`MAddMinuteOfMinute`һֱ�������С�
����������Ϣ������������ճ�������д���״�������Ը��������ҵ��쳣����ĸ�Դ��
