# 2. function example

# javaScript function

```javascript

/**
 * Functions
 */
function calculateAge(birthYear){
    return 2019 - birthYear;
}
var ageJohn = calculateAge(1990);
var ageMike = calculateAge(1948);
var ageJane = calculateAge(1969);
console.log(ageJohn, ageMike, ageJane);

function yearsUntilRetirement(year, firstName){
    var age = calculateAge(year);
    var retirement = 65 - age;

    if(retirement > 0){
        console.log(firstName + ' retires in '+retirement+' years.');
    }else{
        console.log(firstName + ' is already retired.');
    }
    
}
yearsUntilRetirement(1990, 'John');
yearsUntilRetirement(1948, 'Mike');
yearsUntilRetirement(1990, 'Jane');
console.log("\n")
/**
 * Function Statements and Expressions
 */
var whatDoYouDo = function(job, firstName){
    switch(job){
        case 'teacher':
            return firstName + 'teachs kids how to code';
        case 'driver':
            return firstName + 'drives a cab in Lisbon';
        case 'designer':
            return firstName + 'designs beautiful websites';
        default:
            return firstName + ' does something else';
    }
}
console.log(whatDoYouDo('teacher','John'));
console.log(whatDoYouDo('designer','John'));
console.log(whatDoYouDo('retired','John'));
console.log('\n')

```