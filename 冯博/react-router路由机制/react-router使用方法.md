# react-router使用方法

### 安装

``` bash
$ npm install react-router --save

```

### 常用使用方法

因为router就是一个react组件，所以使用起来就和使用其他普通组件是一样的

``` js
import ReactDOM from 'react-dom';
import { Router, Route, IndexRoute, browserHistory } from 'react-router';

ReactDOM.render(
<Router history={browserHistory}>
        <IndexRoute component={Home}/>
        <Route path="/users" component={UserPage}/>
        <Route path="/repos" component={ReposPage}/>
</Router>，

document.getElementById('root')

);

```
Router:路由组件的外部容器组件，用来包裹内部组件

history:用于监听浏览器地址栏的变化，配置项包括：hashHistory,browserHistory和memoryHistory

Route:定义Url路径对应的组件,path表示url中#后面的部分，component表示指定的组件

IndexRoute：设置默认页

### 嵌套使用
``` js

ReactDOM.render(
<Router history={browserHistory}>
      <Route path="/" component={App}>
        <IndexRoute component={Home}/>
        <Route path="/users" component={UserPage}/>
        <Route path="/repos" component={ReposPage}/>
      </Route>
</Router>，

document.getElementById('root')

);

```
这里我们将App作为容器组件，将需要子组件通过this.props.child传入

``` js
/**
	此处省略一万行
*/
  render() {
    const { user } = this.props;
    return (
      <div className="container-fluid">

        <Header location={this.props.location} user={user} handleLogout={() => this.handleLogout()}/>
        <div className="appContent">
          {this.props.children}
        </div>
        {
          <Footer/>
        }
        
      </div>
    ); 
  }
```

参考

官方文档[https://github.com/reactjs/react-router/tree/master/docs](https://github.com/reactjs/react-router/tree/master/docs)

中文文档[https://react-guide.github.io/react-router-cn/docs/Introduction.html](https://react-guide.github.io/react-router-cn/docs/Introduction.html)