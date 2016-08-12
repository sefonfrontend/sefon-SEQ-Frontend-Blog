# 认识git

![](./img/git.jpg)

### git是什么?

> git是目前世界上最先进的分布式版本控制系统，没有之一

### git和其他版本控制系统的区别？

git VS SVN

1、设计模式

git : 分布式

SVN ：集中式

2、角色

git 既是服务器又是客户端

SVN 服务器和客户端是分离的

3、权限

git 没有权限的设置

SVN 可以为不同的用户设置不同的权限

### 安装

下载软件

windows版本下载地址：[https://git-scm.com/downloads](https://git-scm.com/downloads)

配置用户名和Email

``` bash

$ git config --global user.name "your name"

$ git config --global user.password "your password"

```
### git图形化的界面软件

*（推荐）Source Tree <https://www.sourcetreeapp.com/>

* git GUI

### windows 连接github连接不上的解决方法 

在windows环境中安装完git后，通过git bash界面进行clone代码的时候，经常会出现连接不上网络，

这是由于中国网络防火墙的问题，这种情况下只能通过代理的方式进行，推荐使用goAgent,goAgent

的代理地址一般为127.0.0.1:8087

在git bash中执行以下命令：

``` bash

$ git config --global http.proxy 127.0.0.1:8087

```

设置完这个就可以成功连接上github了，但是又会抛出另外一个问题，就是提示没有找到证书，因为github是使用的https协议，

但是这里我们可以不用管这个，通过以下设置可以忽略掉这个问题

``` bash
$ git config --global http.sslVerify false

```

通过以上2步就能成功连上github

参考<http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000>

