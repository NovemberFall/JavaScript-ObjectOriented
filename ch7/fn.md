# 1. function es5

# Passing functions as Arguments

- A function is an instance of the Object types;

- A function behaves like any other object;

- We can store functions in a variable;

- We can pass a function ase an argument to another function;

- We can return a function from a function

```js
var years = [1990, 1965, 1937, 2005, 1998];
function arrayCalc(arr, fn){
    var arrRes = [];
    for(var i=0; i<arr.length; i++){
            arrRes.push(fn(arr[i]));
    }
    return arrRes;
}

function calculateAge(el){
    return 2019 - el;
}

function isFullAge(el){
    return el >= 18;
}

function maxHeartRate(el){
    if(el >= 18 && el <= 81){
        return Math.round(206.9 - (0.67 * el));
    }else{
        return -1;
    }
}

var ages = arrayCalc(years, calculateAge);
var fullAge = arrayCalc(ages, isFullAge);
var rates = arrayCalc(ages, maxHeartRate);
console.log(ages);
console.log(fullAge);
console.log(rates);
```

# Functions returning functions

```js
function interviewQuestion(job){
    if(job === 'designer'){
        return function(name){
            console.log(name + ', can you please explain what '+
            'UX design is?');
        }
    }else if(job === 'teacher'){
        return function(name){
            console.log('What subject do you teach, '+name+'?');
        }
    }else{
        return function(name){
            console.log('Hello '+name+', what do you do?');
        }
    }
}

var teacherQuestion = interviewQuestion('teacher');
var designerQuestion = interviewQuestion('designer');

teacherQuestion('John');
designerQuestion('John');
//Generic function
designerQuestion('Jane');
designerQuestion('Jim');
designerQuestion('Mike');

interviewQuestion('teacher')('Jane');
//left part [interviewQuestion('teacher')] return a function, then 
//passing parameter 'Jane' into the returned function
```

# Immediately Invoked Function Expressions

```js
/* 
Immediately Invoked Function Expressions 
        IIFE  (pattern)
*/

function game(){
    var score = Math.random() * 10;
    console.log(score >= 5);
}
game();

(function(){
    var score = Math.random() * 10;
    console.log(score >= 5);
})();

//console.log(score);  //here is error, since it cannot access variable from IIFE

(function(goodLuck){
    var score = Math.random() * 10;
    console.log(score >= 5 - goodLuck);
})(5);
```



















