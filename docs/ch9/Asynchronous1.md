# 2. 异步编程 Asynchronous

    1. call back

    2. generator

    3. promise

    4. async + await


### `Promise`

- 主要用于异步计算

- 可以将异步操作队列化，按照期望的顺序执行，返回符合预期的结果

- 可以在对象之间传递和操作promise， 帮助我们处理队列

#### javascript 包含大量异步操作

- javascript 为检查表单而生

- 创造它的首要目标是操作dom

- 所以，javascript 的操作大多都是异步的

#### 为什么异步操作可以避免界面冻结？

- 假设你去一家饭店，自己找座位坐下了，然后招呼服务员拿菜单

- 服务员说：“对不起，我是`同步`服务员，我要服务完这张桌子才能招呼你。”

- 你是不是很生气很想抽ta？

- 那一桌人明明已经吃上了，你只是想要菜单，这么小的一个动作，服务员却要你等到别人的一个大动作完成。

- 这就是`同步`的问题：

- `顺序交付的工作1234， 必须按照1234的顺序完成。`


#### 异步

- 异步，则是将耗时很长的 a 交付的工作交给系统之后， 就去继续做 b 交付的工作。 等到系统完成前面的工作之后，
  再通过回调或者事件，继续做 a 剩下的工作。

- 从观察者的角度来看起来，a b 工作的完成顺序，和交付他们的事件顺序无关，所以叫`异步`。


#### 稍有不慎，就会踏入`callback hell`

`除此之外，还有更深层次的问题`

- 假设需求：

- 遍历目录，找出最大的一个文件


### 以下才是Promise诞生的原因：

```js
a(function (resultsFromA) {
  b(resultsFromA, function (resultsFromB) {
    c(resultsFromB, function (resultsFromC) {
      d(resultsFromC, function (resultsFromD) {
        e(resultsFromD, function (resultsFromE) {
          f(resultsFromE, function (resultsFromF) {
            console.log(resultsFromF);
          })
        })
      })
    })
  })
});
```

#### 回调有四个问题

1. 嵌套层次很深，难以维护

2. 无法正常使用return 和 throw

3. 无法正常检索堆栈信息

4. 多个回调之间难以建立联系




#### 浏览器中的javascript

- 异步操作以事件为主

- callback主要出现在 ajax 和 file api

- 这个时候问题尚不严重


#### 有了node.js之后

`对异步的依赖进一步加剧了。。。`

- 无阻塞高并发，是node.js的招牌

- 异步操作是其保障

- 大量操作依赖callback function



### `Promise的概念和优点`

【优点】

- Promise是一个代理对象，它和原先要进行的操作并无关系

- Promise通过引入一个回调，避免了更多的回调
  
【状态】

- `pending`：待定，称为初始状态

- `fulfilled`：实现，称为操作成功状态

- `rejected`：被否决，称为操作失败状态

- 当Promise状态发生改变的时候，就会触发.then()里的响应函数来处理后续步骤

- Promise状态已经改变，就不会再变


### `Promise的基本语法`

```js
new Promise(
    /* 执行器 executor */
    function (resolve, reject) {
      // 一段耗时很长的异步操作
      resolve(); // 数据处理完成
      reject(); // 数据处理出错
    }
 ).then(function A() {
    // 成功，下一步
  }, function B() {
    // 失败，做相应处理
  });
```

### `Promise一个简单的例子`

```js
console.log('here we go');
new Promise(resolve => {
    setTimeout(() => {
      resolve('hello');
      console.log(123);
    }, 2000);
  })
  .then(name => {
    console.log(name + ' world');
  });

/* 
here we go
123
hello world
*/
```

- 以上代码和课程稍微有些不同，目的是和定时器做一些对比，以此发现一点什么。

```js
console.log('here we go');
setTimeout(() => {
  greeting("hello");
  console.log(123);
}, 2000)

function greeting(name) {
  console.log(name + ' world');
}

/* 
here we go
hello world
123
*/
```

- 通过以上两段代码的运行结果比较，可以浅显的得出：**resolve()状态引发的then()是异步的**


### `Promise两步执行的范例`

```js
console.log('here we go');
new Promise(resolve => {
    setTimeout(() => {
      resolve('hello');
    }, 2000);
  })
  .then(value => {
    console.log(value);
    return new Promise(resolve => {
      setTimeout(() => {
        resolve('world');
      }, 2000);
    });
  })
  .then(value => {
    console.log(value + ' world');
  });
```

- 这个范例主要是简单的演示了Promise如何解决回调地狱这个让人头大的问题。


### 对已经完成的Promise执行then()

```js
console.log('start');
let promise = new Promise(resolve => {
  setTimeout(() => {
    console.log('the promise fulfilled');
    resolve('hello, world');
  }, 1000);
});

setTimeout(() => {
  promise.then(value => {
    console.log(value);
  });
}, 3000);

/* 
start
the promise fulfilled
hello, world

*/
```

- 讲师的原话：这段代码展示了Promise作为队列这个重要的特性，就是说我们在任何一个地方生成了一个Promise对象，
  都可以把它当做成一个变量传递到其他地方执行。不管Promise前面的状态到底有没有完成，队列都会按照固定的顺序去执行。



### `then()不返回Promise`

```js
console.log('here we go');
new Promise(resolve => {
    setTimeout(() => {
      resolve('hello');
    }, 2000);
  })
  .then(value => {
    console.log(value);
    console.log('everyone');
    (function () {
      return new Promise(resolve => {
        setTimeout(() => {
          console.log('Mr.Laurence');
          resolve('Merry Xmas');
        }, 2000);
      });
    }());
    return false;
  })
  .then(value => {
    console.log(value + ' world');
  });

/* 
here we go
hello
everyone
false world
Mr.Laurence
*/  
```

- 我对以上代码的理解是这样的：最后一个then()方法里的value值代表的是上一个then()里的返回值，
  当没有return的时候，默认返回值为undefined。而resolve()里的数据为什么没被调用呢？因为上一个then()方法里return的是false而不是Promise实例。



### `then()解析`

- then()接受两个函数作为参数，分别代表fulfilled和rejected

- then()返回一个新的Promise实例，所以它可以链式调用

- 当前面的Promise状态改变时，then()根据其最终状态，选择特定的状态响应函数执行

- 状态响应函数可以返回新的Promise或其他值

- 如果返回新的Promise，那么下一级then()会在新的Promise状态改变之后执行

- 如果返回其他任何值，则会立刻执行下一级then()

