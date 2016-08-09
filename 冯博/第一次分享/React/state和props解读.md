### 组件状态State

React 中每个组件可以存储自己的当前状态， 以一个 switch 开关组件为例，开关的状态可以存储在组件内部。

React 的渲染结果是由组件属性和状态共同决定的，状态和属性的区别是，状态维护在组件内部，属性是由外部控制，我们先介绍组件状态相关细节

控制状态的 API 为：

1 this.state：组件的当前状态

2 getInitialState：获取组件的初始状态，在组件加载的时候会被调用一次，返回值赋予 this.state 作为初始值

3 this.setState：

- 组件状态改变时，可以通过 this.setState 修改状态

- setState 方法支持按需修改，如 state 有两个字段，仅当 setState 传入的对象包含字段 key 才会修改属性

- 每次调用 setState 会导致重渲染调用 render 方法

- 直接修改 state 不会重渲染组件

``` javascipt
var Switch = React.createClass({
        // 定义组件的初始状态，初始为关
        getInitialState: function() {
            return {
                open: false
            }
        },
        // 通过 this.state 获取当前状态
        render: function() {
            console.log('render switch component');
            var open = this.state.open;
            return <label className="switch"> 
                        <input type="checkbox" checked={open}/> 
                    </label>
        },
        // 通过 setState 修改组件状态
        // setState 过后会 React 会调用 render 方法重渲染
        toggleSwitch: function() {
            var open = this.state.open;
            this.setState({
                open: !open
            });
        }
    })
```

### 组件属性 Props

React 组件可以传递属性给组件，传递方法和 HTML 中无异, 可以通过 this.props 获取组件属性

属性相关的 API 为:

1 this.props: 获取属性值

2 getDefaultProps: 获取默认属性对象，会被调用一次，当组件类创建的时候就会被调用，返回值会被缓存起来，当组件被实例化过后如果传入的属性没有值，会返回默认属性值

3 this.props.children：子节点属性

4 propTypes: 属性类型检查

以一个代办事项的列表项组件为例:

``` javascript
// props.name 表示代办事项的名称
    var TodoItem = React.createClass({
        render: function() {
            var props = this.props;
            return <div className="todo-item">
                        <span className="todo-item__name">{props.name}</span>
                    </div>
        }
    });

    ReactDOM.render(
        <TodoItem name="代办事项1"/>, 
         document.getElementById('example'));
```