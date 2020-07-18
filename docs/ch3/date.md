# 1. Date | Time

### Date & Time

```js
//dates & times
const now = new Date();
console.log(now);
// Fri Jul 26 2019 00:19:51 GMT-0700 (Pacific Daylight Time)

console.log(typeof now); //object

console.log('getFullYear:', now.getFullYear());
console.log('getMonth:', now.getMonth());
console.log('getDate:', now.getDate());
console.log('getDay:', now.getDay());
console.log('getHours:', now.getHours());
console.log('getMinutes:', now.getMinutes());
console.log('getSeconds:', now.getSeconds());

/*
getFullYear: 2019
getMonth: 6
getDate: 26
getDay: 5
getHours: 0
getMinutes: 23
getSeconds: 57
*/




//tiemstamps
console.log('timestamp', now.getTime());  //timestamp 1564125919286


//date strings
console.log(now.toDateString());
console.log(now.toTimeString());
console.log(now.toLocaleString());

/*
Fri Jul 26 2019
00:26:40 GMT-0700 (Pacific Daylight Time)
7/26/2019, 12:26:40 AM
*/
```