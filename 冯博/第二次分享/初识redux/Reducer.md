## Reducer

Action对象仅仅是描述了行为的相关信息，至于如何通过特定的行为来更新state，就需要看看Reducer了。

## Reducer简介

关于Reducer，最简单的描述就是:

- Reducer是一个函数
- 该函数接收两个参数，一个旧的状态previousState和一个Action对象
- 返回一个新的状态newState


根据上面的描述，Reducer函数就可以表示为：

    (previousState, action) => newState
    
    
Reducer是一个pure function，避免在Reducer中做下面的事情：

- Mutate its arguments;
- Perform side effects like API calls and routing transitions;
- Call non-pure functions, e.g. Date.now or Math.random();    
    
    
## 设计state的结构

既然Reducer是根据Action来更新state的一个函数，那么在开始设计Reducer的时候，就需要设计state的结构。

例如，在任务管理的这个应用中，就可以将state表示为下面的结构，在这个结构中：

- `taskCategory`表示当前选择的任务类别，用来进行任务过滤
- `tasks`表示用来获得的任务列表


    {
        taskCategory: 'All',
        tasks: [
            {
                name: 'Write a blog',
                category: 'Writing'
            },
            {
                name: 'Read ES6 spec',
                category: 'Reading'
            }
        ]
    }     
    

当有了state的结构之后，就可以给整个应用创建一个*初始*的state了，表示应用启动的时候`taskCategory`选择的是`All`，`tasks`列表为空。

    const initialState = {
        taskCategory: 'All',
        tasks: []
    };
    
    
## 处理Action

有了state的结构和初始的state之后，就可以开始实现Reducer函数了，Reducer函数的形式通常如下：

    function reducer(state = [], action) {
        // code to handle different actions
        switch (action.type) {
            case SPECIAL_ACTION:
                // code to update state with SPECIAL_ACTION action
                // then return the new state
            default:
                return state
        }
    }

结合任务管理的例子，就可以实现如下的Reducer函数：
    
    function taskApp(state = initialState, action) {
        switch (action.type) {
            case SELECT_CATEGORY:
                return Object.assign({}, state, {
                    taskCategory: action.category
                });
                
            case ADD_TASK:
                return Object.assign({}, state, {
                    tasks: [...state.tasks, {
                        name: action.name,
                        category: action.category
                    }]
                });
                
            default:
                return state;
        }
    }    
    
    
关于Reducer函数的实现有下面两个注意点：

1. 不要在Reducer函数的内部修改state
2. 在`default`的情况下返回旧的state


## 拆分Reducer

当Reducer函数越来越长的时候，可以把逻辑关系上不太紧密的Action处理逻辑差分到不同的Reducer函数中，例如上面的例子就可以拆分为两个Reducer函数：

    function tasks(state = [], action) {
        switch (action.type) {
            case ADD_TASK:
                return [...state, {
                    name: action.name,
                    category: action.category
                }];
                
            default:
                return state;
        }
    }    
    
    function category(state = 'All', action) {
        switch (action.type) {
            case SELECT_CATEGORY:
                return action.category;
                
            default:
                return state;
        }
    }       
    
    function taskApp(state = initialState, action) {
        return {
            category: category(state.taskCategory, action),
            tasks: tasks(state.tasks, action)
        };
    }

通过上面的实现可以看到，拆分后的Reducer的代码更加清晰了，每个Reducer的规模都不会太大。    
    
但是对于Reducer的拆分一定要注意以下几点：

- 拆分后每个Rreducer函数**只负责管理全局state中的一部分**（tasks这个Reducer值负责state中的tasks列表）
- 拆分会每个Reducer函数的**state默认参数值**对应它管理的那部分state的数据


上面的代码中，通过taskApp对各个Reducer进行了合并，在Redux中提供了`combineReducers()`工具类来完成Reducer的合并，这样就可以简化taskApp函数的实现：

    import { combineReducers } from 'redux';
    
    const taskApp = combineReducers({
        category,
        tasks
    });
    
    export default taskApp;
    