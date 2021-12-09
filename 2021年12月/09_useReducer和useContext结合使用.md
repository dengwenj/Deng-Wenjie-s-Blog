useReducer（知道 redux 的话，就知道 useReducer 如何工作了） 和 useContext 结合使用。我总结了几点什么时候使用 useReducer：1、如果 state 是一个数组或者对象，2、如果 state 变化很复杂，经常一个操作需要修改很多 state，比如：login 登陆到时候就可以用 useReducer。

useContext 和 useReducer 使用：将 dispatch 函数作为 context 的 value，共享给页面的子组件，在 useReducer 结合 useCountext，通过 context 把 dispatch 函数提供给组件树中的所有组件使用，而不是通过 props 添加回调函数到方式一层层传递。如果页面组件层级比较深，并且需要子组件触发 state 的变化，可以考虑 useContext + useReducer。

demo 如下：

父组件：

![img](https://pic2.zhimg.com/80/v2-ecdde799a4f9077f927026a8e8b44e2d_1440w.jpg)

子组件：

![img](https://pic3.zhimg.com/80/v2-16ea388a1a0e56a88d493ca1b8b9a782_1440w.jpg)

