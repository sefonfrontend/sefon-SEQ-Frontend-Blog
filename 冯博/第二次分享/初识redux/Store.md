## Store

通过前面两个小节了解到了Action对象和Reducer函数的作用，下面来看看Redux中另外一个核心概念Store。

Actions描述了“what happened”的事实，Reducers则根据这些actions来更新state，而Store则是Actions和Reducers连接在一起的对象。

Store是Redux中数据的统一存储，维护着state的所有内容，所以Store的主要功能就是：

- 维护应用的state内容
- 提供`getState()`方法获取 state
- 提供`dispatch(action)`方法更新 state
- 提供`subscribe(listener)`方法注册监听器

看到Store提供的方法，就可以把Action、Reducer和Store联系在一起了：

1. Store通过`dispatch(action)`方法来接收不同的Action
2. 根据Action对象的type和数据信息，Store对象可以通过Reducer函数来更新state的内容


## 创建Store对象

在Redux中，可以通过`createStore`函数来创建Store对象，`createStore`函数的参数就是Reducer函数。

    import { createStore } from 'redux';
    
    const initState = [];
    var reducer = function (state = initState, action) {
        console.log('reducer was called with state', state, 'and action', action);
    }
    
    var store = createStore(reducer);
    console.log(store);
    
通过代码的运行结果可以看到，Reducer函数会在创建Store对象的时候被调用（即使这个时候没有任何的Action）。

其实在调用`createStore`函数的时候，会通过Reducer函数来设置应用的初始state，同时dispatch一个init action('@@redux/INIT')。    


## getState和dispatch

根据前面的介绍Store对象提供了一下方法让我们获取和更新state，继续上面的例子，可以通过`getState`方法来获得当前的state：

    console.log('store state after initialization:', store.getState())

为了继续演示dispatch action，需要对Reducer函数进行一些修改，来处理特定的action：

    import { createStore } from 'redux';
    
    const initState = [];
    var reducer = function (state = initState, action) {
        switch (action.type) {
            case 'ADD_TASK':
                console.log('-> ADD_TASK Action');
                return [...state, {
                    name: action.name,
                    category: action.category
                }];
                
            default:
                return state;
        }
        
    }
    
    var store = createStore(reducer);
    console.log('initial state is:', store.getState());
    
    store.dispatch({
        type: 'ADD_TASK',
        name: 'Read ES6 spec',
        category: 'Reading'
    })
    console.log('state after ADD_TASK action:', store.getState());