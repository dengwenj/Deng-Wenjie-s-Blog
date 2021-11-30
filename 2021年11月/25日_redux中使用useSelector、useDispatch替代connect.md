# redux中使用useSelector、useDispatch替代connect

与 一样`connect()`，应该首先将整个应用程序包装在一个`<Provider>`组件中，以使存储在整个组件树中可用

```jsx
const store = createStore(rootReducer)

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
)
```

``useSelector``

主要作用： 从`redux`的`store`对象中提取数据(`state`)

```jsx
const zState = useSelector(state => state)
```

`useState`

```jsx
const store = useStore()
```

这个`Hook`返回`redux` `<Provider>`组件的`store`对象的引用

`useDispatch`

主要作用：就是操作状态的方法

```jsx
    const state = useSelector(state => state) // 就是用来获取状态的
    const dispatch = useDispatch() // 用来操作状态的方法 
    const store = useStore()
    console.log(store);
    console.log(dispatch);
    console.log(state);

    const headleClick = () => {
        dispatch({type:'dwj', data:'dwj and weiwei'})
    }

    return (
        <div>
            <h3>{state.countReducer}</h3>
            <button onClick={headleClick}>点击</button>
        </div>
    )		
```

