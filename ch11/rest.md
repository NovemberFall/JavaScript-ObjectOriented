# 3. Rest parameters

```js
//ES5
function isFullAge5(){
    console.log(arguments);
}
isFullAge5(1990, 1999, 1965)
/* 
0: 1990
1: 1999
2: 1965
callee: ƒ isFullAge5()
length: 3
Symbol(Symbol.iterator): ƒ values()
__proto__: Object
*/

function isFullAge5(){
    var argsArr = Array.prototype.slice.call(arguments);

    argsArr.forEach(element => {
        console.log((2016 - element) >= 18);
    });
}
isFullAge5(1990, 1999, 1965); // true false true
isFullAge5(1990, 1999, 1965, 2016, 1987); // true false true false true
```

### `ES6`

```js
function isFullAge6(...years){
    years.forEach(element => console.log((2016 - element) >= 18));
}

isFullAge6(1990, 1999, 1965); // true false true
```
