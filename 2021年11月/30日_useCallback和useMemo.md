### 要不要使用 useMemo 和 useCallback

**useMemo 缓存的是一个变量，useCallback 缓存的是一个函数。在依赖没有变的时候返回的变量或者函数都是旧的那个**



#### 哪些情况一个组件会重新渲染？

  **1、组件自己的 state 变化**

  **2、父组件传递过来的 props 变化**

  **3、父组件重新渲染了**



#### useMemo 使用场景

**如果一些值的计算量很大，那么可以用 useMemo 来做一个缓存，只有依赖变化时才会重新计算，而不是每次渲染时都进行计算**

#### useCallback 使用场景

**1、对于需要传递`函数`给子组件的场合，不使用 useCallback 的话，子组件每次都会重新渲染**

**2、在调用节流、防抖函数时**

**3、在 useEffect（） 中使用外部创建的函数, 但不希望这个函数一直变化, 导致 useEffect 被重复触发**

父组件：

```jsx
import React, { useCallback, useMemo, useState } from 'react'

import Child from './Child'

export default function Demo() {
    const [count, setCount] = useState(0)
    const [num, setNum] = useState(0)

    const [totle, setTotle] = useState(10)

    const headleClick = () => {
        setCount(count + 1)
    }

    /* 父组件给子组件传递函数的时候可以用 useCallback，如果没有用 useCallback 当父组件更新的时候子组件也会更新，
      但是子组件仅仅是更新而已，没有做别的事情 
        useCallback 是返回的一个函数，当依赖项没有变化的时候返回的这个函数永远是一样的  
    */
    const clickNum = useCallback(() => {
        setNum(num + 1)
    }, [num])

    /* 
        useMemo 它的一个参数是函数，函数要有一个返回值，这个返回值就是 useMemo 的返回值。
        当它的依赖项没有改变的时候返回的是原来的值
        如果一些值的计算量很大，那么可以用 useMemo 来做一个缓存，只有依赖变化时才会重新计算，而不是每次渲染时都进行计算
    */
    function t(value) {
        console.log('被调用了！！');
        let count = 0;
        for (let i = 1; i <= value; i++) {
            count += i
        }
        return count
    }

    // const totleCount = t(totle)
    const totleCount = useMemo(() => {
        return t(totle)
    }, [totle])

    const headleTotle = () => {
        setTotle(totle + 1)
    }

    return (
        <div>
            <div>count:{count}</div>
            <button onClick={headleClick}>+1</button>
            <button onClick={headleTotle}>+</button>
            <div>totleCount:{totleCount}</div>
            <hr />
            <Child click={clickNum} num={num} />
        </div>
    )
}

// export default function Hello() {
//     /* 
//         useCallback 结合 useEffect 使用
//     */
//     const [name, setName] = useState('');
//     // const consoleLog = () => {
//     //     console.log('没有被 useCallback 包裹的consoleLog执行了');
//     // };
//     // 这样的话 这个函数只有不会变化了
//     const consoleLog = useCallback(() => {
//         console.log('没有被 useCallback 包裹的consoleLog执行了');
//     }, [])
//     useEffect(() => {
//         consoleLog();
//         console.log("useEffect 执行了");
//     }, [consoleLog]);
//     console.log("render 生命周期触发了");
//     return (<div>
//         <input value={name} onChange={(e) => {
//             setName(e.target.value);
//         }} />
//     </div>);
// }
```

子组件：

```jsx
import React, { memo } from 'react'

const Child = memo(({ num, click }) => {
    const headleClickChild = () => {
        click()
    }

    console.log('被调用了');
    return (
        <>
            <div>num:{num}</div>
            <button onClick={headleClickChild}>+1</button>
        </>
    )
})

export default Child
```

### 个人观点

**1、在出现性能问题后，进行优化时可以考虑使用 useMemo 和 useCallback 对性能进行一定的优化**

**2、如果没有性能问题可以不用，这样可以更专注于代码本身逻辑**

