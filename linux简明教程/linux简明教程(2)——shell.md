---
title: linux简明教程(2)——shell

date: 2022-5-9 15:00:02

updated: 2022-5-9 15:00:02

tags:

- linux

categories:

- linux简明教程

---

# 一.shell本质

- shell本质是一个命令行程序，也是绝大多数人接触的linux下第一个命令行程序。shell其实是一个语法解析器，并且有自己的语法，叫做shell语言，它和c语言，python语言本质都是一样的

- 历史上有很多shell程序，像sh、bash、zsh等等都是，虽然名字不同，但是底层原理是一样的

# 二.shell初体验

- 当你在命令行看到类似`[root@VM-24-8-centos ~]#`的文字的时候，就说明你正在使用shell，其中root表示你当前的用户是root用户，@是分隔符，机器名是VM-24-8-centos，~表示你当前所在的目录是家目录，#后是要输入的命令内容

# 三.shell命令

- shell中命令有两种类型，一是内建命令，新手只需要记住cd是内建命令就可以，这类命令是shell自带的；二是外部命令，这类命令不是shell自带，是由其他人编写的

- 这两种命令的不同之处在于，当shell执行外部命令时，会fork一个子进程来执行该命令，然后shell等待命令执行结束；当shell执行内建命令时，不会新建子进程

# 三.shell变量

- shell语言中有变量的概念，和c语言python语言的变量概念一样。shell中变量分为两类，一是`环境变量`，二是`局部变量`。两种变量的区别是，`环境变量可以由父进程传递给fork出来的子进程`，局部变量不可以

- 在shell中定义一个局部变量MYNAME如下，此时这个shell进程就拥有了一个局部变量MYNAME
  
  ```shell
  $ MYNAME=zs
  ```

- 如果想定义环境变量，语法和局部变量类型，前面加上export就可以了，此时这个shell拥有了一个环境变量MYNAME，当它执行命令的时候，fork出来的子进程也会拥有MYNAME这个环境变量
  
  ```shell
  $ export MYNAME=zs
  ```

# 四.linux中重要的环境变量

- 在命令行中执行env命令，可以看到很多环境变量，下面是一些重要的环境变量
  
  ```shell
  $ env
  USER=root
  HOME=/root
  SHELL=/usr/bin/zsh
  PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin
  ```

- USER：你当前登录的用户名

- HOME：当前登录用户的家目录

- SHELL：当前执行的shell程序的位置在哪里，上述例子的shell就是/usr/bin目录下的bash程序

- `PATH`：可执行文件的路径，这个环境变量非常重要，因为会经常修改它来添加可执行文件的路径。PATH变量以冒号作为分隔符，分隔一个个路径，这些路径下面都是可执行程序，多亏有了PATH环境变量，你才能方便地使用命令

# 五.执行命令

- 可以简单地把命令分为两种，一种是所在路径位于环境变量PATH中的命令，另一种是路径不在环境变量PATH中的命令

- 对于第一种命令，直接输入命令的名字即可执行，因为shell会到环境变量PATH里的目录下寻找该命令

- 对于第二种命令，需要在命令的前面带上它的路径才可以执行
