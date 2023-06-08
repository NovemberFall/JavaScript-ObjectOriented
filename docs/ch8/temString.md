## 1. Template String

- ES5
  
```js
let firstName = 'John';
let lastName = 'Smith';
const yearOfBirth = 1990;

function calcAge(year){
    return 2016-year;
}

//ES5
console.log('This is '+firstName+ ' '+lastName+' . He was born in'+
yearOfBirth + '. Today, he is '+calcAge(yearOfBirth)+' years old.');
/* output:
 This is John Smith . He was born in 1990. Today, he is 26 years old.
 */

//ES5
console.log('This is '+firstName+ ' '+lastName+' . He was born in'+
yearOfBirth + '. Today, he is '+calcAge(yearOfBirth)+' years old.');
/* This is John Smith . He was born in1990. Today, he is 26 years old. */

//ES6
console.log(`This is ${firstName} ${lastName}. He was born in ${yearOfBirth}. Today, he is ${calcAge(yearOfBirth)} years old.`);
/* This is John Smith. He was born in 1990. 
Today, he is 26 years old. */


const n = `${firstName} ${lastName}`;
console.log(n.startsWith('J'));  //true
console.log(n.endsWith('th'));  //true
console.log(n.includes(' '));  //true
console.log(firstName.repeat(5)); //JohnJohnJohnJohnJohn
console.log(`${firstName} `.repeat(5)); //John John John John John
```