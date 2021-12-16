1、默认绑定（独立函数调用）

```js
function foo() {
  console.log('foo')
}

foo()
```

2、隐式绑定（obj.dwj()）

```js
const obj = {
	dwj() {
		console.log('dengwenjie')
	}
}
```

3、显示绑定（call、apply、bind）

```js
function fn() {
  console.log('fn')
}

const obj1 = {
  name: 'dengwenjie'
}

fn.call(obj1) // 相当于 obj1.fn()
```

4、new 绑定

```js
function Person() {
  this.name = name
  this.age = age
}

const p1 = new Person('dengwenjie', 21)
const p2 = new Person('zhengweiwei', 17)

new 做的事情：1、会创建一个新的对象。2、this 会指向这个对象。3、会执行这个构造函数把属性和方法添加到这个对象上。4、会返回这个对象。这就是为什么构造函数里面不写 return
```

**他们的优先级**

```
new 绑定 > 显示绑定 > 隐式绑定 > 默认绑定
```



