# Understanding JavaScript Async/Await

Async/Await is a special syntax designed to work with promises in a more intuitive way, without relying on `.then()` chaining commonly seen in promises. It provides a cleaner and more readable way to handle asynchronous code.

The `async` keyword is used to define a function as asynchronous. This means it returns a promise that can be either resolved or rejected, depending on what is returned within the async function.

The `await` keyword is used to pause the execution of the async function until a promise is resolved or rejected. This allows other code to run while the async function is waiting for the promise to settle. Once the promise is resolved, the async function resumes execution.

One important note is that if an async function doesn't explicitly return a promise, it will implicitly return a resolved promise with a value of `undefined`.

## Syntax for Async/Await

### Using a normal function:

```javascript
async function fetchData() {
  const data = await fetch('www.xyz.com');
  return data;
}
```
## code flow example

```javascript
const url = 'https://course-api.com/react-tabs-project';

console.log('Starting the function'); // 1st Statement

function printData(data) {
  console.log('Inside print function'); // 3rd Statement
  console.log(data.value); // 4th Statement.
  
  setTimeout(() => {
    console.log(data); // 9th statement
  }, 3000)
}

async function getData () {
  console.log('Inside async function') // 2nd Statement
  const rawData = await fetch(url) 
  console.log('Fetching data is complete') // 7th statement
  const json = await rawData.json() 
  console.log('Fetched data: ', json) // 8th statement

  return json //value returned
}

const fetchData = getData(); 

printData(fetchData); 
console.log('Outside'); // 5th statement
for (let index = 0; index < 100000000; index++) {
  
}

console.log('Global code and call stack are now empty'); // 6th statement
```

## CODE EXPLANATION

- Code begins executing, printing the 1st statement. `getData()` function is called.
- Inside `getData()`, the 2nd statement is printed.
- A fetch method with `await` pauses execution. Control steps out of `getData` as it returns a pending promise.
- `printData()` is called with `fetchData` as an argument, executing the 3rd and 4th statements.
- The 5th statement is printed, followed by a for-loop.
- After the loop, the 6th statement is printed.
- Promise from `fetch` resolves in the background, data is fetched. Inside `getData()`, 7th and 8th statements print.
- `getData` returns JSON, resolving `fetchData`. `printData` receives JSON, executes the 9th statement with `setTimeout`.


# Summary

This code demonstrates the usage of Async/Await in JavaScript. 

- The `async` keyword defines functions as asynchronous, allowing them to return promises.
- `await` pauses execution until a promise is resolved or rejected, improving code readability.
- The example showcases fetching data from a URL and handling it using Async/Await.
- The code flow is explained in 8 concise bullet points for easy comprehension.

This serves as a concise overview of the code's purpose and key features.
