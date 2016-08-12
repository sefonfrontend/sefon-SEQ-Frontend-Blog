# git 常用命令

* 初始化仓库 init

``` bash
$ git init

```

* 克隆仓库 clone

``` bash
$ git clone <url>

```

例如：clone github中jquery的仓库

``` bash
$ git clone https://github.com/jquery/jquery.git

```
* 暂存 add

``` bash
$ git add <filename>

或者全部暂存

$ git add <*/--all>

```
* 提交 commit

``` bash
$ git commit -m <提交说明>

```
例如：
``` bash 
$ git commit -m "初始化项目文件"
```
* 推送 push

``` bash
$ git push origin <branch>

```
branch 为仓库分支名词，主线为master

例如：

``` bash
$ git push origin master

```
* 更新 pull

``` bash
$ git pull

```

参考 <http://rogerdudler.github.io/git-guide/index.zh.html>
