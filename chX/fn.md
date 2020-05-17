# function

### arguments

- JavaScript还有一个免费赠送的关键字`arguments`，它只在函数内部起作用，
  并且永远指向当前函数的调用者传入的所有参数。`arguments`类似`Array`但它不是一个`Array`：

```js
function foo(x) {
    console.log('x = ' + x);
    for (var i = 0; i < arguments.length; i++) {
        console.log('arg ' + i + ' = ' + arguments[i]);
    }
}
foo(10, 20, 30);

/* 
x = 10
arg 0 = 10
arg 1 = 20
arg 2 = 30
 */
```

---


## rest参数

- ES6标准引入了rest参数，上面的函数可以改写为：

```js
function foo1(a, b, ...rest) {
    console.log('a = ' + a);
    console.log('b = ' + b);
    console.log(rest);
}

foo1(1, 2, 3, 4, 5);
// 结果:
// a = 1
// b = 2
// Array [ 3, 4, 5 ]

foo1(1);
// 结果:
// a = 1
// b = undefined
// Array []
```

---

## 小心你的return语句

- 前面我们讲到了JavaScript引擎有一个在行末自动添加分号的机制，这可能让你栽到return
  语句的一个大坑：

```js
function foo() {
    return { name: 'foo' };
}

foo(); // { name: 'foo' }
```

---

如果把return语句拆成两行：

```js
function foo() {
    return
        { name: 'foo' };
}

foo(); // undefined
```

- 要小心了，由于JavaScript引擎在行末自动添加分号的机制，上面的代码实际上变成了：

```js
function foo() {
    return; // 自动添加了分号，相当于return undefined;
        { name: 'foo' }; // 这行语句已经没法执行到了
}
```

- 所以正确的多行写法是：

```js
function foo() {
    return { // 这里不会自动加分号，因为{表示语句尚未结束
        name: 'foo'
    };
}
```

