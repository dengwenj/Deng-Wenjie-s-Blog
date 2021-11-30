## Lodash 是一个一致性、模块化、高性能的 JavaScript 实用工具库，

lodash的所有函数都不会在原有的数据上进行操作，而是复制出一个新的数据而不改变原有数据

lodash是一套工具库，内部封装了很多字符串、数组、对象等常见数据类型的处理函数

```js
const lodash = require('lodash')
```

1、`omit`

```js
lodash.omit(object, [props]) // 可以删除 object 对象中的属性

const obj = {name: 'dwj', age: 21, sex: '男'}
lodash.omit(obj, [age, sex]) // {name: 'dwj'}
```

2、`isNil`

```js
lodash.isNil(value) // 检查 value 是否是 null 或者 undefined，返回的是布尔值
```

3、`isEmpty`

```js
检查 value 是否为一个空对象，集合，映射或者set。返回的是布尔值，value 不为对象，集合返回 true，否则返回 fasle
lodash.isEmpty(true) // 返回为 true
lodash.isEmpty({name: 'weiwei'}) // false
```

