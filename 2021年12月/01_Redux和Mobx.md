### Mobx的架构

MobX 的核心是观察者模式。

- Store 是被观察者（observable）
- 组件是观察者（observer）

一旦`Store`有变化，会立刻被组件观察到，从而引发重新渲染。

### Redux的架构

Redux 的核心概念

- 所有的状态存放在`Store`。组件每次重新渲染，都必须由状态变化引起。
- 用户在 UI 上发出`action`。
- `reducer`函数接收`action`，然后根据当前的`state`，计算出新的`state`。

[![img](https://github.com/ruanyf/jstraining/raw/master/docs/images/redux-architecture.png)](https://github.com/ruanyf/jstraining/blob/master/docs/images/redux-architecture.png)

- MobX：响应式（Reactive）管理，state 是可变对象，适合中小型项目
- Redux：函数式（Functional）管理，state 是不可变对象，适合大型项目