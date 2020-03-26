# 1. let const

```js
// let and const

// ES5
var name5 = 'Jane Smith';
var age5 = 23;
name5 = 'Jane Miller';  //mutate
console.log(name5);

// ES6
const name6 = 'Jane Smith';
let age6 = 23;
name6 = 'Jane Miller';
console.log(name6);  //error, since name6 is const

```

# scope between ES5 and ES6

```js
//ES5
function driversLicence5(passedTest){
    if(passedTest){
        var firstName = 'John';
        var yearOfBirth = 1990;

    }
    console.log(firstName + ', born in '+ yearOfBirth + 
        ' is now officially allowed to drive a car.');
}
driversLicence5(true);
/* output:
John, born in 1990 is now officially allowed to drive a car. */

// ES6
function driversLicence6(passedTest){
    if(passedTest){
        let firstName = 'John';
        const yearOfBirth = 1990;

    }
    console.log(firstName + ', born in '+ yearOfBirth + 
        ' is now officially allowed to drive a car.');
}
driversLicence6(true);
/* output:
script.js:34 Uncaught ReferenceError: firstName is not defined
    at driversLicence6 (script.js:34)
    at script.js:37
 */
```

- look at the above code:
  
  1. ES5: since var defined in function scope, firstName and yearOfBirth still working.
  
  2. ES6: let and const defined in block scope so outside if statement the fistName 
     and yearofBirth don't work.

- so we change the ES6 codes:

```js
// ES6
function driversLicence6(passedTest){
    let firstName ;
    const yearOfBirth = 1990;
    if(passedTest){
        firstName = 'John';
    }
    console.log(firstName + ', born in '+ yearOfBirth + 
        ' is now officially allowed to drive a car.');
}
driversLicence6(true);
/*
John, born in 1990 is now officially allowed to drive a car. 
 */
```

- again, since ES6 is block-Scoped, outter for loop i still be 23

```js
let i = 23;
for(let i=0; i<5; i++){
    console.log(i)
}
console.log(i)
/*  output:
 0
 1
 2
 3
 4
 23
*/
```