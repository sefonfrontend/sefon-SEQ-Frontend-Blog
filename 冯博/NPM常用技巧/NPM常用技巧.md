# NPM常用技巧

* script

package.json 文件中的srcipt配置项中可以添加一些常用的命令，比如单元测试、启动服务

例如：webpack-dev-server

``` js

  "scripts": {
    "build":"webpack-dev-server"
  },

```

使用：

``` bash

$ npm run build

```

作用：

不用手动去输入一些比较长的命令行，避免出错，提高开发调试代码的速度
