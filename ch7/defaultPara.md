# 3. Default Parameters

### `Default Parameters`

```js
function SmithPerson(firstName, yearOfBirth, lastName, nationality) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.yearOfBirth = yearOfBirth;
    this.nationality = nationality;
}

var john = new SmithPerson('John', 1990);
console.log(john)



//output:
SmithPerson {
  firstName: 'John',
  lastName: undefined,
  yearOfBirth: 1990,
  nationality: undefined
}
```

```js
function SmithPerson(firstName, yearOfBirth, lastName, nationality) {
    lastName === undefined ? lastName = 'Smith' : lastName = lastName;

    nationality === undefined ? nationality = 'american' : nationality = nationality;
    this.firstName = firstName;
    this.lastName = lastName;
    this.yearOfBirth = yearOfBirth;
    this.nationality = nationality;
}

var john = new SmithPerson('John', 1990);
console.log(john)

//output:
SmithPerson {
  firstName: 'John',
  lastName: 'Smith',
  yearOfBirth: 1990,
  nationality: 'american'
}

```

### `ES6`

```js
//ES6
function SmithPerson(firstName, yearOfBirth, lastName = 'Smith', nationality = 'american') {
    this.firstName = firstName;
    this.lastName = lastName;
    this.yearOfBirth = yearOfBirth;
    this.nationality = nationality;
};
var john = new SmithPerson('John', 1990);
var emily = new SmithPerson('Emily', 1983, 'Diaz', 'spanish');

console.log(john)
console.log(emily)


//output:
SmithPerson {
  firstName: 'John',
  lastName: 'Smith',
  yearOfBirth: 1990,
  nationality: 'american'
}
SmithPerson {
  firstName: 'Emily',
  lastName: 'Diaz',
  yearOfBirth: 1983,
  nationality: 'spanish'
}
```