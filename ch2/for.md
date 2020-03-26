# 1. for loop

# for loop with continue and break;

```js
/**
 * Loops and iteration
 */

var john = ['John', 'Smith', 1990, 'designer', false, 'blue'];

for(var i=0; i<john.length; i++){
    if(typeof john[i] !== 'string'){
        continue;
    }
    console.log(john[i]);
}

console.log('\n')
for(var i=0; i<john.length; i++){
    if(typeof john[i] !== 'string'){
        break;
    }
    console.log(john[i]);
}

console.log('\n')
// Looping backwards
for(var i = john.length - 1; i>=0; i--){
    console.log(john[i]);
}

```