# 3. method 方法

- 在一个对象中绑定函数，称为这个对象的方法。

在JavaScript中，对象的定义是这样的：

```js
var xiaoming = {
    name: '小明',
    birth: 1990
};
```

- 但是，如果我们给xiaoming绑定一个函数，就可以做更多的事情。比如，写个age()方法，返回xiaoming的年龄：

```js
var xiaoming = {
    name: '小明',
    birth: 1990,
    age: function () {
        var y = new Date().getFullYear();
        return y - this.birth;
    }
};

xiaoming.age; // function xiaoming.age()
xiaoming.age(); // 今年调用是25,明年调用就变成26了
```

绑定到对象上的函数称为方法，和普通函数也没啥区别，但是它在内部使用了一个this关键字，这个东东是什么？

在一个方法内部，this是一个特殊变量，它始终指向当前对象，也就是xiaoming这个变量。
所以，this.birth可以拿到xiaoming的birth属性。




```js
```



```js
```



```js
```



```js
```



```js
```



```js
```



```js
```



```js
```



```js
```



```js
```



