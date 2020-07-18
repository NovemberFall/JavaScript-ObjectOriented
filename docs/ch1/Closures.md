# 4. Closures

- Example:

```js
function user(name) {
    var age, sex;
    return {
      getName: function() {
        return name;
      },
      setName: function(newName) {
        name = newName;
      },
      getAge: function() {
        return age;
      },
      setAge: function(newAge) {
        age = newAge;
      },
      getSex: function() {
        return sex;
      },
      setSex: function(newSex) {
        sex = newSex;
      }
    }
  }
  
  var whh = user('王花花');
  whh.setSex('女');
  whh.setAge(22);
  var name = whh.getName();
  var sex = whh.getSex();
  var age = whh.getAge();
  console.log(name, sex, age);//王花花 女 22
```


- Summary:**An inner function has always access to the variables and parameters of its outer function, even after the outer function has returned.**

```js
function retirement(retirementAge){
    var a = ' years left until retirement.';
    return function(yearOfBirth){
        var age = 2019-yearOfBirth;
        console.log((retirementAge - age) + a);
    }
}

var retirementUS = retirement(66);
/* 1. pass parameter 66 into function retirement, which, (1) declares a variable 'a' here
 (2) return the anonymous function with parameter 'yearOfBirth'; then this function finished
 and its execution context gets popped off the stack
 */
retirementUS(1990); //Output: 37 years left until retirement.
/* 2. In this function, we use the retirementAge paramenter of this outer function here
and also a variable 'a' that is also declared outside of this anonymous function.
When we run this anonymous function, this works, so somehow, we are still use these variables
even after retirement function, which declares these variables, already stopped its execution.
 */
/**
 * Overall: Our inner function here is able to use the retirement variable and a variable of this
 * function here that is already gone. It has already returned. But somehow the variables are still
 * there, and this is the closure. 
 * /
 
// equal: 
//retirement(66)(1990);
```

# convert to Clsures functioning

```js
/* 
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
*/

function interviewQuestion(job){
    return function(name){
        if(job === 'designer'){
            console.log(name + ', can you please explain what '+
            'UX design is?');
        }else if (job === 'teacher'){
            console.log('What subject do you teach, '+name+'?');
        }else{
            console.log('Hello '+name+', what do you do?');
        }
    }
}
interviewQuestion('teacher')('John'); //What subject do you teach, John?
```