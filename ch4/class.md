# 1. Class

=======
- **Classes, unlike functions are not hoisted. You need to declare a class before you can construct an instance.**
  
- A class can have at most one constructor. 
  After all, class is just syntactic sugar for defining a constructor function.
  If you declare a class without a constructor, 
  it automatically gets a constructor with an empty body.

- Unlike in an object literal, in a class declaration, 
  you do not use commas to separate the method definitions.

- The body of a class is executed in strict mode.

---

### `ES5`

```js
var Person5 = function(name, yearOfBirth, job){
    this.name = name;
    this.yearOfBirth = yearOfBirth;
    this.job = job;
}

Person5.prototype.calculateAge = function(){
    var age = new Date().getFullYear - this.yearOfBirth;
    console.log(age);
}

var john5 = new Person5('John', 1990, 'teacher');
/* 
Person5 {name: "John", yearOfBirth: 1990, job: "teacher"}
job: "teacher"
name: "John"
yearOfBirth: 1990
__proto__: Object
*/
```

### `ES6`

```js
class Person6{
    constructor(name, yearOfBirth, job){
        this.name = name;
        this.yearOfBirth = yearOfBirth;
        this.job = job;
    }

    calculateAge(){
        var age = new Date().getFullYear - this.yearOfBirth;
        console.log(age);
    }
}

const john6 = new Person6('John', 1990, 'teacher');
/* 
Person6 {name: "John", yearOfBirth: 1990, job: "teacher"}
job: "teacher"
name: "John"
yearOfBirth: 1990
__proto__: Object
*/
```

### `adding a static method to a class`

```js
class Person6{
    constructor(name, yearOfBirth, job){
        this.name = name;
        this.yearOfBirth = yearOfBirth;
        this.job = job;
    }

    calculateAge(){
        var age = new Date().getFullYear - this.yearOfBirth;
        console.log(age);
    }

    static greeting(){
        console.log('Hi there!');
    }
}

Person6.greeting(); // Hi there
```





### `class contructor`

```js
class User{
    constructor(){
        //set up properties
        this.username = 'mario';
    }
}

const userOne = new User();
// the 'new' keyword
// 1 - it creates a new empty object{}
// 2 - it binds the value of 'this' to the new empty object
// 3 - it calls the constructor function to 'build' the object
```

