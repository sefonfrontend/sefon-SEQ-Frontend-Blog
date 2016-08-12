# Markdown 语法

### 基本使用

1、字体

# # 一号字体
## ## 二号字体
### ### 三号字体
.
.
.
###### ###### 六号字体

2、字体

**斜体文字*  *

****粗体文字** **

******粗斜体文字******

3、链接

文字链接： [链接名字]（http://链接网址）

网址链接：<<http://网址链接>>

4、列表

无序列表

- -列表文本
	- -子列表文本

+ +列表文本
	+ +子列表文本

* *列表文本
	* +子列表文本

有序列表

	1、列表前使用（数字+空格）

	2、列表前使用（数字+空格）

	3、列表前使用（数字+空格）

5、引用

> '>' 引用文本前使用(大于号+空格)

6、图片

跟文本链接差不多，只是在前面加了一个感叹号 ！

![]（图片地址）

![](img/markdown.jpg)

7、换行

在当前行的结尾加2个空格  
就可以换行了

如果要另起一个新段落，只需要空出一行即可

8、代码

使用```包裹一段代码，并指定一种语言

例如：  
``` js
	``` js
	var sayHelloWorld=function(){
	alert("hello world");
	}
	```
```
支持的语言有：actionscript, apache, bash, clojure, cmake, coffeescript, cpp, cs, css, d, delphi, django, erlang, go, haskell, html, http, ini, java, javascript, json, lisp, lua, markdown, matlab, nginx, objectivec, perl, php, python, r, ruby, scala, smalltalk, sql, tex, vbscript, xml

### 插件推荐

OmniMarkupPreviewer

Visual Studio Code

参考 <https://gitbookio.gitbooks.io/markdown/content/index.html>