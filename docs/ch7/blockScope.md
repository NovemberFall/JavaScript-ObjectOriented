# 4. block scope IIFE

#  block-scope 

```js
{
    const a = 1;
    let b = 2;
}
console.log(a + b); //error since ES6 block-scope

//ES5
(function(){
    var c = 3;
})();

console.log(c); //error, since IIFES also block-scoped
```

# function-scope

```js

{
    const a = 1;
    let b = 2;
    var c = 3;  //since var is function-scope
}
console.log(c);   //3
```
---


## JS IIEF

https://www.cnblogs.com/shiyou00/p/10631013.html


```js
function outputNumbers(count) {
    for (var i = 0; i < count; i++) {
        console.log(i);
    }

    console.log("************total:");
    console.log(i);   //计数
}


outputNumbers(10);
```

```js
JavaScript没有块级作用域的概念。但是通过IIEF 立即执行函数我们可以实现块级作用域。

这个函数中定义了一个for循环，而变量i的初始值被设置为0。在Java、C++等语言中，
变量i只会在for循环的语句块中有定义，循环一旦结束，变量i就会被销毁。

可是在JavaScrip中，变量i是定义在ouputNumbers()的活动对象中的，
因此从它有定义开始，就可以在函数内部随处访问它。





即使像下面这样错误地重新声明同一个变量，也不会改变它的值.
function outputNumbers(count){
    for (var i=0; i < count; i++){
        console.log(i);
    }

    var i;         //重新声明变量
    console.log(i);      //计数
}


JavaScript从来不会告诉你是否多次声明了同一个变量；
遇到这种情况，它只会对后续的声明视而不见（不过，它会执行后续声明中的变量初始化）。
匿名函数可以用来模仿块级作用域并避免这个问题。



用作块级作用域（通常称为私有作用域）的匿名函数的语法如下所示。
(function(){
    //这里是块级作用域
})();

以上代码定义并立即调用了一个匿名函数。将函数声明包含在一对圆括号中，
表示它实际上是一个函数表达式。而紧随其后的另一对圆括号会立即调用这个函数。

现在对上面的函数进行改造



function outputNumbers(count){
    (function () {
        for (var i=0; i < count; i++){
            console.log(i);
        }
    })();

    console.log(i);   //导致一个错误！
}

在这个重写后的outputNumbers()函数中，我们在for循环外部插入了一个私有作用域。
在匿名函数中定义的任何变量，都会在执行结束时被销毁。因此，变量i只能在循环中使用，使用后即被销毁。
```





## two more example

```js
var Employee = (function () {
    function Employee(name, salary) {
        this.name = name;
        this.salary = salary;
    }
    Employee.prototype.display =
        function () {
            console.log(this.name);
        };
    return Employee;
})();
var emp = new Employee("Jon", 87321);
console.log(emp.salary);











var Employee = new function () {
    function Employee(name, salary) {
        this.name = name;
        this.salary = salary;
    }
    Employee.prototype.display =
        function () {
            console.log(this.name);
        };
    return Employee;
}
var emp = new Employee("Jon", 87321);
console.log(emp.salary);

```

