## 生命周期方法

组件的生命周期主要包括以下几种情况

- 组件被实例化的时候

- 组件属性改变的时候

- 组件状态被改变的时候

- 组件被销毁的时候

##### 1 componentWillMount

``` C
void componentWillMount()

```
条件：第一次渲染阶段在调用 render 方法前会被调用
作用：该方法在整个组件生命周期只会被调用一次，所以可以利用该方法做一些组件内部的初始化工作

##### 2 componentDidMount

``` C
void componentDidMount()

```
条件：第一次渲染成功过后，组件对应的 DOM 已经添加到页面后调用
作用：这个阶段表示组件对应的 DOM 已经存在，我们可以在这个时候做一些依赖 DOM 的操作或者其他的一些如请求数据，和第三方库整合的操作。如果嵌套了子组件，子组件会比父组件优先渲染，所以这个时候可以获取子组件对应的 DOM。

##### 3 componentWillReceiveProps(newProps)

``` C
void componentWillReceiveProps(
  object nextProps
)

```
条件： 当组件获取新属性的时候，第一次渲染不会调用
用处： 这个时候可以根据新的属性来修改组件状态 

eg:

``` javascript
 componentWillReceiveProps: function(nextProps) {
      this.setState({
        likesIncreasing: nextProps.likeCount > this.props.likeCount
      });
    }
```
注意： 这个时候虽说是获取新属性，但并不能确定属性一定改变了，例如一个组件被多次渲染到 DOM 中，如下面：

``` javascript
 var Component = React.createClass({
        componentWillReceiveProps: function(nextProps) {
            console.log('componentWillReceiveProps', nextProps.data.bar);
        },
        rener: function() {
            return <div> {this.props.data.bar} </div>
        }
    });

    var container = document.getElementById('container');
    var mydata = {bar: 'drinks'};
    ReactDOM.render(<Component data={mydata} />, container);
    ReactDOM.render(<Component data={mydata} />, container);
    ReactDOM.render(<Component data={mydata} />, container);
```
结果会输出两次 componentWillReceiveProps，虽然属性数据没有改变，但是仍然会调用 componentWillReceiveProps 方法。

##### 4 shouldComponentUpdate(nextProps, nextState)

``` C
boolean shouldComponentUpdate(
  object nextProps, object nextState
)

```
条件： 接收到新属性或者新状态的时候在 render 前会被调用（除了调用 forceUpdate 和初始化渲染以外）
用处： 该方法让我们有机会决定是否重渲染组件，如果返回 false，那么不会重渲染组件，借此可以优化应用性能（在组件很多的情况）。

##### 5 componentWillUpdate

``` C
void componentWillUpdate(
  object nextProps, object nextState
)

```
条件：当组件确定要更新，在 render 之前调用
用处：这个时候可以确定一定会更新组件，可以执行更新前的操作
注意：方法中不能使用 setState ，setState 的操作应该在 componentWillReceiveProps 方法中调用

##### 6 componentDidUpdate

``` C
void componentDidUpdate(
  object prevProps, object prevState
)

```
条件：更新被应用到 DOM 之后
用处：可以执行组件更新过后的操作