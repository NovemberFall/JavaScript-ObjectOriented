# 1. delete operator

```js
The JavaScript delete operator removes a property from an object; 
if no more references to the same property are held, 
it is eventually released automatically.
```

```js
const Employee = {
  firstname: 'John',
  lastname: 'Doe'
}

console.log(Employee.firstname);
// expected output: "John"

delete Employee.firstname;

console.log(Employee.firstname);
// expected output: undefined
```


- The `delete` operator removes a given property from an object. 
  On successful deletion, it will return `true`, else `false` will be returned.

#### Ex:

```js
var Employee = {
  age: 28,
  name: 'abc',
  designation: 'developer'
}

console.log(delete Employee.name);   // returns true
console.log(delete Employee.age);    // returns true

// When trying to delete a property that does 
// not exist, true is returned 
console.log(delete Employee.salary); // returns true
```