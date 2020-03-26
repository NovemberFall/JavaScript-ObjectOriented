# 2. Sub Class

# classes and subclasses

# ES5

```js
var Person5 = function(name, yearOfBirth, job){
    this.name = name;
    this.yearOfBirth = yearOfBirth;
    this.job = job;
}

Person5.prototype.calculateAge = function(){
    var age = new Date().getFullYear() - this.yearOfBirth;
    console.log(age);
}

var john5 = new Person5('John', 1990, 'teacher');
//Person5 {name: "John", yearOfBirth: 1990, job: "teacher"}

var Athletes5 = function(name, yearOfBirth, job, olymicGames, medals){
    Person5.call(this, name, yearOfBirth, job);
    this.olymicGames = olymicGames;
    this.medals = medals;
}

Athletes5.prototype = Object.create(Person5.prototype);

Athletes5.prototype.wonMedal = function(){
    this.medals++;
    console.log(this.medals);
}

var johnAthlete5 = new Athletes5('John', 1990, 'swimmer', 3, 10);
/* 
Person5 {
  name: 'John',
  yearOfBirth: 1990,
  job: 'swimmer',
  olymicGames: 3,
  medals: 10
}
*/

johnAthlete5.calculateAge();//29
johnAthlete5.wonMedal();//11
```

# ES6

```js
//ES6
class Person6{
    constructor(name, yearOfBirth, job){
        this.name = name;
        this.yearOfBirth = yearOfBirth;
        this.job = job;
    }

    calculateAge(){
        var age = new Date().getFullYear() - this.yearOfBirth;
        console.log(age);
    }

    static greeting(){
        console.log('Hi there!');
    }
}

class Athletes6 extends Person6{
    constructor(name, yearOfBirth, job, olympicGame, medals){
        super(name, yearOfBirth, job);
        this.olympicGame = olympicGame;
        this.medals = medals;
    }

    wonMedal(){
        this.medals++;
        console.log(this.medals);
    }
}

const johnAthlete6 = new Athletes6('John', 1990, 'swimmer', 3, 10);
/* 
Athletes6 {
  name: 'John',
  yearOfBirth: 1990,
  job: 'swimmer',
  olympicGame: 3,
  medals: 10
}
*/
johnAthlete6.wonMedal();//11
johnAthlete6.calculateAge();//29
```


