# 4. High-Order Function

- 如果你读过Google的那篇大名鼎鼎的论文[MapReduce: Simplified Data Processing on Large Clusters](https://research.google/pubs/pub62/),  你就能大概明白map/reduce的概念。


## Map

- 举例说明，比如我们有一个函数f(x)=x2，要把这个函数作用在一个数组[1, 2, 3, 4, 5, 6, 7, 8, 9]上，就可以用map实现如下：

![](img/2020-05-17-13-21-18.png)

- 由于map()方法定义在JavaScript的Array中，我们调用Array的map()方法，传入我们自己的函数，就得到了一个新的Array作为结果：


```js
'use strict';

function pow(x) {
    return x * x;
}



var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
var results = arr.map(pow); // [1, 4, 9, 16, 25, 36, 49, 64, 81]
console.log(results);
```


- 注意：map()传入的参数是pow，即函数对象本身。

- 你可能会想，不需要map()，写一个循环，也可以计算出结果：

```js
var f = function (x) {
    return x * x;
};

var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
var result = [];
for (var i=0; i<arr.length; i++) {
    result.push(f(arr[i]));
}
```

- 的确可以，但是，从上面的循环代码，我们无法一眼看明白“把f(x)作用在Array的每一个元素并把结果生成一个新的Array”。

- 所以，map()作为高阶函数，事实上它把运算规则抽象了，因此，我们不但可以计算简单的 
  $${f(x) = x^2}$$   
  还可以计算任意复杂的函数，比如，把Array的所有数字转为字符串：

```js
var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
arr.map(String); // ['1', '2', '3', '4', '5', '6', '7', '8', '9']
```

- 只需要一行代码。

---


## reduce

- 再看reduce的用法。Array的reduce()把一个函数作用在这个Array的[x1, x2, x3...]上，
  这个函数必须接收两个参数，reduce()把结果继续和序列的下一个元素做累积计算，其效果就是：

```js
[x1, x2, x3, x4].reduce(f) = f(f(f(x1, x2), x3), x4)
```

- 比方说对一个Array求和，就可以用reduce实现：

```js
var arr = [1, 3, 5, 7, 9];
arr.reduce(function (x, y) {
    return x + y;
}); // 25
```

