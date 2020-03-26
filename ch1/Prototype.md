# 2. Prototype

### factory function

```javascript
function user(name, age, gender){
    var person = {};
    person.name = name;
    person.age = age;
    person.gender = gender;
    return person;
}

var Tim = user('Tim', 20, 'male');
console.log('Tim:', Tim);


```

# Constructor; this way should use new keyword

```javascript
function user(name, age, gender){
     this.name = name;
     this.age = age;
     this.gender = gender;
 }

 var pTim = new user('Tim', 18, 'male');
 console.log('Tim: ', pTim);

 function Dog(){
     this.age = 5;
     this.gender = 'male';
     this.speak = function(){
         console.log('Woof...')
     }
 }
 var dog = new Dog();
 console.log('dog: ', dog);

```

# JavaScript Object Prototypes 

- All JavaScript objects inherit properties and methods from a prototype.

```javascript

function Person(first, last, age, eyecolor) {
    this.firstName = first;
    this.lastName = last;
    this.age = age;
    this.eyeColor = eyecolor;
}

var myFather = new Person("John", "Doe", 50, "blue");
var myMother = new Person("Sally", "Rally", 48, "green");
```  

- We also learned that you can not add a new property to an existing object constructor:

```javascript
Person.nationality = "English";    // Error: 
console.log(myFather.nationality);  //undefined
``` 

# Prototype Inheritance
### All JavaScript objects inherit properties and methods from a prototype:

- **Date** objects inherit from **Date.prototype**

- **Array** objects inherit from **Array.prototype**

- **Person** objects inherit from **Person.prototype**

# The **Object.prototype** is on the top of the prototype inheritance chain:  
### Date objects, Array objects, and Person objects inherit from Object.prototype.

- The JavaScript prototype property allows you to add new properties to object constructors: 

```javascript
// The correct way:
Person.prototype.nationality = "English";
console.log(myFather.nationality);   //output: English
console.log(myMother.nationality);   //output: English
```  

```javascript
// We also can change the prototype.property
Person.prototype.nationality = "Chinese";
console.log(myFather.nationality);   //output: Chinese
console.log(myMother.nationality);   //output: Chinese

//We can check the _proto_ if they are equal
console.log(myFather._proto_ === myMother._proto_); //True



//We also can check the instance's constructor
console.log(myFather.constructor);   //Point to function Person()
console.log('\n')

//We can define a new object
var myBrother = new myFather.constructor('Tom', 'Zheng', 30, 'black');
console.log(myBrother);
Person.prototype.nationality = "English";
console.log(myBrother.nationality);   // English
```  
