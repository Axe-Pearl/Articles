<!-- This is my take on async await -->

# Javascript Async/Await

Async/Await is a special syntax to work with **promises** in a more comfortable way by avoiding something called as *.then()* chaining that occurs in **promises**. It is very easy to understand and use.

The keyword **async** is used to define a function as an asynchronous function which returns a promise which is either resolved or rejected and has the value assigned to it with whatever we return in the async function.

The **await** keyword is used to pause the execution of the async function until a promise is returned which is either fulfilled or rejected. While waiting for the Promise to settle, the async function yields control back to the caller, allowing other code to run. Once the Promise is resolved, the async function resumes execution, and it either returns a fulfilled Promise with a value or throws an error, which results in a rejected Promise.

One very important thing to note is that if an async function is not explicitly (directly) returning a promise then it will implicitly return a promise which is reolved and has a value of undefined.

**NOTE**: If the await keyword has a primitive value like an integer next to it then it returns an already resolved promise with the value being the primitive data which we wrote next to the await keyword. 

# Syntax for Async/Await

With normal javascript function: 
``` 
async function fun () {
  const fetchData = await fetch('www.xyz.com');
  return fetchData;
}
```

With arrow function: 
```
const fun = async () => {
  const fetchData = await fetch('www.xyz.com');
  return fetchData;
}
```

# Let's understand the flow of code with a basic example: 

```

const url = 'https://course-api.com/react-tabs-project';

console.log('Starting the function'); // 1st Statement

function printData(data) {
  console.log('Inside print function'); // 3rd Statement. Note: The data right now is undefined as fetch promise is still in pending state.
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
**NOTE**: The Statements are commented in the code.

Explanation for the above code: 

When code starts executing the 1st statement is printed and now the getData() func. is called.

The moment getData() function is called, since it's an async function a promise is defined for fetchData which looks like {value: undefined, state: pending, onFulfillHandler: []}. Now we go inside the function body.

When we get inside the fucntion body the 2nd statement is printed.

Now we encounter a the fetch method with await keyword. When we encounter await, we are thrown outside the getData func and we go inside fetch func first which downloading data from url inside runtime.Meanwhile the fetch method returns promise which is not resolved so it looks like {value: undefined, state: pending, onFulfillHandler: [], onRejectHandler: []} which then gets stored in microtask queue as the promise was immediately returned after informing the runtime. Now we are outside the function executing rest of the code.

Now the printData() function is called which takes the fetcheData as an argument. When we enter the prinData function the 3rd and 4th statements are printed. Now we come across the setTimeout() method where JS tells runtime to start a timer of 3s and we exit the function.

The 5th Statement is printed and then a piece of for-loop code runs for sometime after which we print the 6th statement.

After the global code and call stack is empty the event loop goes and checks the microtask queue for functions and it encounters the getData function. When we go inside the function the fetch method has finished downloading the data and made the promise to go from pending to resolved state. Now the fetch promise looks like {value: downData, state: resolved, onFulfillHandler: []}. rawData variable is the value of the promise now. Now we print the 7th statement.

Now the json method parses the raw data into json data and we get out of the function as it has the await keyword and getData function goes into microtask queue. Now that the global piece of data and call stack are empty we check the microtask queue and again go into getData func and prints the 8th statement.

Now when we encounter the return statement inside the getData function, the getData func. returns the json value. Now the fetchData promise gets resolved and receives the json as value. Now the promise looks like {value: json, state: pending, onFulfillHandler: []}. Meanwhile during all this the timer for setTimeout func inside runtime finished and went inside the callback queue. Now this func. is executed, prints the 9th statement and then we are done.


