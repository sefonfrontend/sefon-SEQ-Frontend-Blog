# 认识github
![](img/github.jpg)

### 什么是github

github是一个基于git的代码托管平台，付费用户可以建私人仓库，我们一般的免费用户只能建公开仓库，也就是代码要公开

### 使用方法

* 第一步 注册账号

注册账号需要准备的一个有效的邮箱

* 第二步 建立仓库


* 第三步 克隆仓库

### github常用的名词解释

* Pull requests
“请求合并”
* Issues
“疑问”
* Gist
基于Git的代码片段管理服务
* Repositories
“仓库”
* Public activity
“公共活动” 记录所有这个仓库下的一切活动
* Followers
“粉丝”
* Starred
“已点赞”
* Following
“正在关注的”
* Watch
“关注”
* Star
“点赞”
* Fork
“叉” 类似于copy，将人家的仓库拷贝到自己的仓库中去
* Wiki
“文档” 通常是放一些项目需要的帮助文档
* Pulse
“脉冲”，默认对该仓库下最近一个星期的提交数据进行统计，
* Graphs
“图”，实质是对从仓库建立开始到目前为止所有对master主线的贡献者用图表的方式进行统计
* Contributors
“贡献者”，本意也是这个意思，表示参与维护这个仓库所有的成员
* Traffic
“流量” 流量分析
* Commits
“提交”
* Code frequency
代码修改频率
* Punch card
“穿孔卡片” 以X轴为一天24小时 以Y轴为一个星期7天，通过穿孔卡片的形式进行展示仓库贡献者在星期几的几点是最活跃的
* Network
“网络图” 通过网络图的方式进行展示仓库发生的变化
* Members
“成员” 指一个team中的成员

### windows连接不成功github解决方法

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

### github 图形化界面

* github desktop <https://desktop.github.com/>