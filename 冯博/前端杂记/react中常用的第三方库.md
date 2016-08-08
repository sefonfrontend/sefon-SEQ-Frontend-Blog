# react中常用的第三方库

### [classnames](https://github.com/JedWatson/classnames)

一个给react动态加入样式类的工具库

比如：在使用分页控件的时候，当在第一页的时候需要将上一页的按钮不能点，当为最后一页的时候下一页的按钮不能点，或者没有数据的时候分页控件不能用，那么可以这样写：

``` js

 const prevStyles=classNames('prev-page',{disabled:page<=1});
 const nextStyles=classNames('next-page',{disabled:users && users.length===0});

```