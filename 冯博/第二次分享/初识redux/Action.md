Action是一个对象，用来代表所有会引起状态（state）变化的行为（例如服务端的响应，页面上的用户操作）。

假如我们要实现一个任务管理系统，那么*添加任务*的Action对象就会是下面的形式：

    {
        type: 'ADD_TASK',
        name: 'Read ES6 spec',
        category: 'Reading'
    }

Action对象是**行为**的描述，一般都会包含下面的信息：

- 一个字符串类型的`type`字段来表示将要执行的动作    
- 需要传递给应用的其他数据信息（例子中的`name`和`category`），数据形式用户可以自定义


### Action创建函数

Action通过Action创建函数（Action Creator）来创建，Action Creator是一个函数，最终返回一个Action对象。

对于*添加任务*这个行为，对应的Action Creator如下：

    function addTask(name, category) {
        return {
            type: ADD_TASK,
            name,
            category
        };
    }

