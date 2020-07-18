# 5. Everything is an object

![](img/14.png)

- Every JavaScript object has a **prototype property**, which makes inheritance possible in JavaScript;
  
- The prototype property of an object is where we put methods and properties that we want **other objects to inherit**;
  
- The Constructor's prototype property is NOT the prototype of the Constructor itself, it's the prototype of **ALL** instances that are created through it;
  
- When a certain method(or property) is called, the search starts in the object itself, 
  and if it cannot be found, the search moves on to the object's prototype. 
  This continues until the method is found: **prototype chain**

# define a function:

```javascript
var Person = function(name, yearOfBirth, job){
    this.name = name;
    this.yearOfBirth = yearOfBirth;
    this.job = job;
    this.calculateAge = function(){
        console.log(2019- this.yearOfBirth);
    }
}
```

- we can use prototype

```javascript
var Person = function(name, yearOfBirth, job){
    this.name = name;
    this.yearOfBirth = yearOfBirth;
    this.job = job;
}

Person.prototype.calculateAge = function(){
    console.log(2019- this.yearOfBirth);
};
```


```javascript
var Person = function(name, yearOfBirth, job){
    this.name = name;
    this.yearOfBirth = yearOfBirth;
    this.job = job;
}

Person.prototype.calculateAge = function(){
    console.log(2019- this.yearOfBirth);
};

Person.prototype.lastName = 'Smith';

var john = new Person('John', 1990, 'teacher');
var jane = new Person('Jane', 1969, 'designer');
var mark = new Person('Mark', 1948, 'retired');

john.calculateAge();
jane.calculateAge();
mark.calculateAge();

console.log(john.lastName)
console.log(jane.lastName)
console.log(mark.lastName)
```
- the above codes,
- because it is the prototype proterty of the function constructor. 
- All John, jane and Mark inherit this property.

```js
//Object.Create
var personProto = {
    calculateAge: function(){
        console.log(2019 - this.yearOfBirth);
    }
};

var john = Object.create(personProto);
john.name = 'John';
john.yearOfBirth = 1990;
john.job = 'teacher';

var jane = Object.create(personProto, {
    name:{ value: 'Jane'},
    yearOfBirth:{ value: 1969},
    job: {value: 'designer'}
});
```

# Primitives vs objects

```ts
// primitives
var a = 23;
var b = a;
a = 46;
console.log(a);     //46
console.log(b);     //23

// Objects
var obj1 = {
    name: 'John',
    age: 26;
};
var obj2 = obj1;
obj1.age = 30;
console.log(obj1.age);  //30
console.log(obj2.age);  //30
```

- we didn't create a new object; only create a reference to object1










