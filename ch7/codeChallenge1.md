# 4. coding challenging 1

```js
/**
 * Coding Challenge 2:
 * 
 * John and his family went on a holiday and went to 3 different resaturants. 
 * The bills were $124, $48 and $268
 * 
 * To tip the waiter a fair amount, John create a simple tip calculator(as a function). 
 * He likes to tip 20% of the bill when the bill is less than $50, 
 * 15% when the bill is between $50 and $200, and 10% if the bill is more than $200.
 * 
 * In the end, John would like to have 2 arrays: 
 * 1. Containing all three tips (one for ecah bill)
 * 2. Containing all three final paid amount (bill + tip).
 * 
 * (NOTE: To calculate 20% of a value, simply mulitply if with 20/100 = 0.2)
 */

 function tipCalculator(bill){
     var percentage;
     if(bill < 50){
         percentage = 0.2;
     }else if(bill >= 50 && bill < 200){
         percentage = 0.15;
     }else{
         percentage = 0.1;
     }
     return percentage * bill;
 }

 console.log(tipCalculator(100));
 
 var bills = [124, 48, 268];
 var tip = [tipCalculator(bills[0]),
            tipCalculator(bills[1]),
            tipCalculator(bills[2])];
var finalValues = [bills[0] + tips[0],
                    bills[1] + tips[1],
                    bills[2] + tips[2],]
console.log(tips);
```