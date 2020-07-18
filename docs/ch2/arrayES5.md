# 2. Array ES5

```js
/*****************************
* Arrays
*/

// Initialize new array
var names = ['John', 'Mark', 'Jane'];
var years = new Array(1990, 1969, 1948);

console.log(names[2]);
console.log(names.length);

// Mutate array data
names[1] = 'Ben';
names[names.length] = 'Mary';
console.log(names); //["John", "Ben", "Jane", "Mary"]

// Different data types
var john = ['John', 'Smith', 1990, 'designer', false];

john.push('blue');//[John", "Smith", 1990, "designer", false, "blue"]
john.unshift('Mr.');
console.log(john);//["Mr.", "John", "Smith", 1990, "designer", false, "blue"]

john.pop();
john.pop();
john.shift();
console.log(john); //["John", "Smith", 1990, "designer"]

console.log(john.indexOf(23));//-1

var isDesigner = john.indexOf('designer') === -1 ? 'John is NOT a designer' : 'John IS a designer';
console.log(isDesigner);//John IS a designer
```



###  `Array.filter() mthod`


```js
const scores = [10, 30, 15, 25, 50, 40, 5];

const filteredScores = scores.filter((score) => {
    return score > 20;
});
console.log(filteredScores);

//[30, 25, 50, 40]






const users = [
    { name: 'shaun', permium: true },
    { name: 'yoshi', permium: false },
    { name: 'mario', permium: false },
    { name: 'chun-li', permium: true },
];

const permiumUsers = users.filter((user) => {
    return user.permium;
})
console.log(permiumUsers);

/* 
[
  { name: 'shaun', permium: true },
  { name: 'chun-li', permium: true }
]
*/
```

- we can alter 

```js
const users = [
    { name: 'shaun', permium: true },
    { name: 'yoshi', permium: false },
    { name: 'mario', permium: false },
    { name: 'chun-li', permium: true },
];

const permiumUsers = users.filter((user) => user.permium);
console.log(permiumUsers);
/* 
[
  { name: 'shaun', permium: true },
  { name: 'chun-li', permium: true }
]
*/
```


```js
const products = [
    { name: 'gold star', price: 20 },
    { name: 'mushroom', price: 40 },
    { name: 'green shells', price: 30 },
    { name: 'banana skin', price: 10 },
    { name: 'red shells', price: 50 },
];
const saleProducts = products.map((product) => {
    if (product.price > 30) {
        product.price = product.price / 2;
        return product;
    } else {
        return product;
    }
})
console.log(saleProducts, products);

//output:
[
  { name: 'gold star', price: 20 },
  { name: 'mushroom', price: 20 },
  { name: 'green shells', price: 30 },
  { name: 'banana skin', price: 10 },
  { name: 'red shells', price: 25 }
]
[
  { name: 'gold star', price: 20 },
  { name: 'mushroom', price: 20 },
  { name: 'green shells', price: 30 },
  { name: 'banana skin', price: 10 },
  { name: 'red shells', price: 25 }
]
```

- when we `console.log(saleProducts, products);` , we get the same results
  
- they're going to be exactly the same because it's directly edited the original one 
  because when we take in an item from an array 
  it's an object and we edited over here it's editing it directly. 

- This isn't a copy of the object that we pass in 
  it's the object directly that we're passing it. 
  So then when we edit it it's going to edit the original value 
  and we don't want to do that. 


### `To avoid this, we need to overwrite the above codes:`

```js
const products = [
    { name: 'gold star', price: 20 },
    { name: 'mushroom', price: 40 },
    { name: 'green shells', price: 30 },
    { name: 'banana skin', price: 10 },
    { name: 'red shells', price: 50 },
];

const saleProducts = products.map((product) => {
    if (product.price > 30) {
        return {
            name: product.name,
            price: product.price / 2
        }
    } else {
        return product;
    }
})

console.log(saleProducts, products);

//output:
[
  { name: 'gold star', price: 20 },
  { name: 'mushroom', price: 20 },
  { name: 'green shells', price: 30 },
  { name: 'banana skin', price: 10 },
  { name: 'red shells', price: 25 }
] [
  { name: 'gold star', price: 20 },
  { name: 'mushroom', price: 40 },
  { name: 'green shells', price: 30 },
  { name: 'banana skin', price: 10 },
  { name: 'red shells', price: 50 }
```

- So that's why we create a new object over here 
  because then that doesn't edit the original value 
  because we're crating a new object and 
  we're setting that equal to the product price of it too. 

- We're just saying the new price property on our new object is equal to this. 


### `Reduce method`

```js
//reduce method
const scores = [10, 30, 15, 25, 70, 90, 30];

const result = scores.reduce((accumulator, currentValue) => {
    if (currentValue > 50) {
        accumulator++;
    }
    return accumulator;
}, 0);

console.log(result);

//output:
2
```




```js
const scores = [
    { player: 'mario', score: 50 },
    { player: 'yoshi', score: 30 },
    { player: 'mario', score: 70 },
    { player: 'crystal', score: 60 }
];

const marioTotal = scores.reduce((acc, curr) => {
    if (curr.player === 'mario') {
        acc += curr.score;
    }
    return acc;
}, 0);

console.log(marioTotal);
//120
```












### `Find method`

- The find() method returns the value of the first element in the array 
  that satisfies the provided testing function. Otherwise undefined is returned.

```js
// Find method
const scores = [10, 5, 0, 40, 60, 10, 20, 70];

const firstHighScore = scores.find((score) => {
    return score > 50;
});
console.log(firstHighScore);

//60
```








### `sort method`

```js
//sort method

//example 1 - sorting strings
const names = ['mario', 'shaun', 'chun-li', 'yoshi', 'luigi'];

names.sort();
console.log(names);
// [ 'chun-li', 'luigi', 'mario', 'shaun', 'yoshi' ]


//example 2 - sorting numbers
const scores = [10, 50, 20, 5, 35, 70, 45];
scores.sort();
console.log(scores);
/* 
[
  10, 20, 35, 45,
   5, 50, 70
]
*/



//example 3 - sorting objects
const players = [
    { name: 'mario', score: 20 },
    { name: 'luigi', score: 10 },
    { name: 'chun-li', score: 50 },
    { name: 'yoshi', score: 30 },
    { name: 'shaun', score: 70 }
];

players.sort((a, b) => {
    if (a.score > b.score) {
        return -1;
    } else if (b.score > a.score) {
        return 1;
    } else {
        return 0;
    }
});

console.log(players)
/* 
[
  { name: 'shaun', score: 70 },
  { name: 'chun-li', score: 50 },
  { name: 'yoshi', score: 30 },
  { name: 'mario', score: 20 },
  { name: 'luigi', score: 10 }
]
*/
```



- we can alter players.sort()
  
```js
//example 3 - sorting objects
const players = [
    { name: 'mario', score: 20 },
    { name: 'luigi', score: 10 },
    { name: 'chun-li', score: 50 },
    { name: 'yoshi', score: 30 },
    { name: 'shaun', score: 70 }
];

players.sort((a, b) => b.score - a.score);
console.log(players)


//output:
[
  { name: 'shaun', score: 70 },
  { name: 'chun-li', score: 50 },
  { name: 'yoshi', score: 30 },
  { name: 'mario', score: 20 },
  { name: 'luigi', score: 10 }
]





//example 2 - sorting numbers
const scores = [10, 50, 20, 5, 35, 70, 45];
scores.sort((a, b) => b - a)
console.log(scores)
```







###  `chaining Array methods`

```js
//chaining array methods
const products = [
    { name: 'gold star', price: 30 },
    { name: 'green shell', price: 10 },
    { name: 'red shells', price: 40 },
    { name: 'banana skin', price: 5 },
    { name: 'mushroom', price: 50 },
];

const filtered = products.filter(product => product.price > 20);
const promos = filtered.map(product => {
    return `the ${product.name} is ${product.price / 2} pounds`;
});
console.log(promos)

//output:
[
  'the gold star is 15 pounds',
  'the red shells is 20 pounds',
  'the mushroom is 25 pounds'
]
```

- the other way:

```js
//chaining array methods
const products = [
    { name: 'gold star', price: 30 },
    { name: 'green shell', price: 10 },
    { name: 'red shells', price: 40 },
    { name: 'banana skin', price: 5 },
    { name: 'mushroom', price: 50 },
];

const promos = products
    .filter(product => product.price > 20)
    .map(product => `the ${product.name} is ${product.price / 2} pounds`);
console.log(promos);

//output:
[
  'the gold star is 15 pounds',
  'the red shells is 20 pounds',
  'the mushroom is 25 pounds'
]

```

