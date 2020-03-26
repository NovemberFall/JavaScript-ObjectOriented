# 3. Arrow function

```js
// Arrow functions
const years = [1990, 1965, 1982, 1937];

// ES5
var ages5 = years.map(function(el){
    return 2019 - el;
});
console.log(ages5); //[29, 54, 37, 82]

// ES6
let ages6 = years.map(el => 2019 - el);
console.log(ages6); //[29, 54, 37, 82]

ages6 = years.map((el, index) => `Age elment ${index + 1}: ${2019-el}.`);
console.log(ages6);     
//["Age elment 1: 29.", "Age elment 2: 54.", "Age elment 3: 37.", "Age elment 4: 82."]

ages6 = years.map((el, index) => {
    const now = new Date().getFullYear();
    const age = now - el;
    return `Age elment ${index + 1}: ${2019-el}.`;
});
console.log(ages6);
//["Age elment 1: 29.", "Age elment 2: 54.", "Age elment 3: 37.", "Age elment 4: 82."]
```


# arraow function 2

```js
var box5 = {
    color: 'green',
    position: 1,
    clickMe: function(){
        document.querySelector('.green').addEventListener('click',function(){
            var str = 'This is box number '+ this.position + ' and it is '+
            this.color;
            alert(str);
        });
    }
}
box5.clickMe();
/* console:
This is box number undefined and it is undefined
 */
```

- The reason is that 'this' keyword, actually points to that object; but in the regular function call
  the this keyword will always point to the global object, 
  which, in the case of the brower, is the window object

- However, a very common pattern to avoid this is to simply create a new variable in here 
  and store the this variable in that new variable.

```js
// ES5
var box5 = {
    color: 'green',
    position: 1,
    clickMe: function(){
        var self = this;
        document.querySelector('.green').addEventListener('click',function(){
            var str = 'This is box number '+ self.position + ' and it is '+
            self.color;
            alert(str);
        });
    }
}
box5.clickMe(); //This is box number 1 and it is green
```


- we also can using Arrow function to avoid this:
  
```js
// ES6
const box6 = {
    color: 'green',
    position: 1,
    clickMe: function(){  
        document.querySelector('.green').addEventListener('click',
        () => {
            var str = 'This is box number '+ this.position + ' and it is '+
            this.color;
            alert(str);
        });
    }
}
box6.clickMe(); //This is box number 1 and it is green
```

# ES5 this keyword

```js
function Person(name){
    this.name = name;
}

// ES5
Person.prototype.myFriends5 = function(friends){
    var arr = friends.map(function(el)
    {
        return this.name + ' is friends with '+el;
    });
    console.log(arr);
}

var friends = ['Bob', 'Jane', 'Mark'];
new Person('John').myFriends5(friends);
/*  output:
0: " is friends with Bob"
1: " is friends with Jane"
2: " is friends with Mark"
 */
```
### We have passed the 'John' into the Person constructor, but in ES5 .map function, 
### which, reference to the gloabl window object.

- To avoid this, outside .map function, 
  
  1. we can add **var self = this**
  
  2. return **self.name + ...**

### The second way to avoid this; but it sounds a little bit weird

```js
// ES5
function Person(name){
    this.name = name;
}

Person.prototype.myFriends5 = function(friends){
    var arr = friends.map(function(el)
    {
        return this.name + ' is friends with '+el;
    }.bind(this));    //it sounds or looks a little bit weird, but is going to work
    console.log(arr);
}

var friends = ['Bob', 'Jane', 'Mark'];
new Person('John').myFriends5(friends);
/*  output:
0: "John is friends with Bob"
1: "John is friends with Jane"
2: "John is friends with Mark"
 */
```

# ES6 Arrow function to avoid this:

```js
//ES6
function Person(name){
    this.name = name;
}

Person.prototype.myFriends5 = function(friends){
    var arr = friends.map( el => {
        return this.name + ' is friends with '+el;
    });    
    console.log(arr);
}
/*  output:
0: "John is friends with Bob"
1: "John is friends with Jane"
2: "John is friends with Mark"
 */
```

- OR:

```js
Person.prototype.myFriends5 = function(friends){
    var arr = friends.map( el => `${this.name} is friends with ${el}`);    
    console.log(arr);
}
```






