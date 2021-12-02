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

