<h1><b>Callbacks, Promises, and Async/Await</b></h1>

<h2><b>Callbacks:</b></h2> Asynchronous processing that waits for a function to complete its execution, a process is told to call another function when the result is ready.
<br>
<br>
Example:

```
asyncFunction(callback1);
console.log('asyncFunction has been called');
// Call when asyncFunction completes
function callback1(error) {
  if (!error) console.log('asyncFunction is complete');
}
```

However the issue with callbacks is that a single callback will be attached to a single asynchronous function and when you nest these functions it creates what’s known as callback hell. Each subsequent callback takes an argument from the previous callbacks. This sequence makes the code structure not only hard to read but maintain. Also, if there is an error in one function, all the other functions would also have errors, making error handling even more complex and tedious. 

Example:
``` 
firstFunction(args, function() {
  secondFunction(args, function() {
    thirdFunction(args, function() {
      // And so on…
    });
  });
});
```

<h2><b>Promises:</b></h2>  JavaScript object with a value that may not be available at the moment when the code line executes. These values are resolved at some point in the future. It allows you to write asynchronous code more synchronously. A promise can have three states: 
<br>
1. Pending (not fulfilled or rejected)
<br>
2. Fulfilled (Operation is successful)
<br>
3. Rejected (Operation is unsuccessful)
<br>
<br>
Example:
<br>

```
// Promise constructor
let promise = new Promise(function(resolve, reject) {
     const x = "apple";
     const y = "apple"
if (x === y) {
        resolve();
     } else {
        reject();
     }
});
// Consuming the Promise
promise
   .then(function () {
      console.log('Successful');
   })
   .catch(function () {
      console.log('Some error has occured');
   });
```

When we use Promises for asynchronous chaining it is a lot more legible as one execution is completed it will handover execution to the next one defined in the chain. 

Example:
```
promise
   .then(function () {
      console.log('Promise object resolved');
   })
   .then(function () {
      console.log('Operation successful');
   })
   .catch(function () {
      console.log('Some error has occured');
   });
// Console Output
Promise object resolved
Operation sucsessful
```

<h2><b>Async/Await:</b></h2>  Await is known as a nicer syntax for Promises. A few advantages that it has over Promises are that it is more concise and looks cleaner, and error handling is straightforward using try/catch 

Example: 
```
const makeRequest = async () => {
  try {
    const data = JSON.parse(await getJSON())
    console.log(data)
  } catch (err) {
    console.log(err)
  }
}
```

