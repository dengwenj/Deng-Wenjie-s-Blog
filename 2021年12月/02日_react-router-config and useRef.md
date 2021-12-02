### react-router-config

```js
import Home from "../pages/Home";
import About from "../pages/About";
import Message from "../pages/Message";
import News from "../pages/News";

const routes = [
    {
        path: '/home',
        // exact: true,
        component: Home,
        routes: [
            {
                path: '/home/message',
                component: Message,
            },
            {
                path: '/home/news',
                component: News
            }
        ]
    },
    {
        path: '/about',
        // exact: true,
        component: About,
    }
];

export default routes;
```

```jsx
{renderRoutes(routes)} // 渲染出来
```

```jsx
{renderRoutes(this.props.route.routes, { name: 'dwj', age: 18 })} // 渲染嵌套路由
```
### useRef

**有类似实例变量的东西吗?**

**有！[`useRef()`](https://zh-hans.reactjs.org/docs/hooks-reference.html#useref) Hook 不仅可以用于 DOM refs。「ref」 对象是一个 `current` 属性可变且可以容纳任意值的通用容器，类似于一个 class 的实例属性。**

 `useRef()` 和自建一个 `{current: ...}` 对象的唯一区别是，`useRef` 会在每次渲染时返回同一个 ref 对象。

返回的 ref 对象在组件的整个生命周期内持续存在,因为在整个生命周期中保持不变（地址值不变）所以即使修改了内部，也不会影响
