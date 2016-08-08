# git on windows

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

[参考文档](http://my.oschina.net/tearlight/blog/193913)

