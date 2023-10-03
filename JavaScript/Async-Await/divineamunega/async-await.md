## JavaScript Async Await ✋

### Table of Contents

a. [Introduction](#introduction)
b. [Promises](#promises)
c. [Async Functions](#conclusion)
d. [Conclusion](#conclusion)

## Introduction

<p style="font-size: 16px;">
Before Explaining Async-Await, let's understand why we need it in Javascript.
</p>

<p style="font-size: 16px;"> 
JavaScript (JS) is primarily single-threaded and synchronous by default. (This means that JS code is executed one operation at a time, in the order it appears in your script.). This is no problem at all when you are not doing tasks that take a lot of time.

But doing tasks that takes a lot of time synchronously will make your app slow, because remember JS is single threded. It will wait for the time-consuming task to finish before runing the other parts of your code.

Thankfully we have a solution which are called Promises

</p>

#### Promises

<p style="font-size: 16px;">
 Promises are objects which reserve space for the outcome of a task, so other code can run while waiting for the task to finish.Promises have three states in Js. <br>

<b>Pending:</b> The state at which the task is stil running in the background.
<b>Resolved:</b> The state at which the task as completed running successfully.
<b>Rejected:</b> The state at which the task as encoutered an error during running.

We cannot use promises normally like we do other values because rememer a promise reserves space for a task and your code continues runing without blocking the execution of your code.

Let's see this example below. This Promise resolves after 10 seconds. But we are trying to log it to the console immediatly. We cannot access the value because promises do not block code execution. They just create a space for the outcome and the code continue with execution. So the result we would get from this will be meaninless and we wont be able to use it to do anything.

```JavaScript
function longRunningTask() {
    return new Promise((res) => {
        setTimeout(() => {
            res(['Promise Resolved. This is the data']);
        }, 10000);
    });
}

console.log(longRunningTask())
// Result : Promise {<pending>}

```

We can handle promises using asyncronous functions and the await keyword.

</p>

#### Async And Await

<p style="font-size:16px;">
    Async functions in JavaScript are functions that execute asynchronously, allowing JavaScript to continue executing code while they run in the background. They achieve this by always returning promises.

The await keyword is used inside async functions to temporarily pause the code until a promise is finished. It can only be used inside async functions because using it elsewhere would stop the code completely, which goes against the idea of async and promises in the first place. (Using it outside an async function is not JS syntax and would throw a syntax error)

In this example below we define an an async function by putting the async keyword before it. Now we can call our friend (longRunningTask) from before here and get the a result. The await keyword pauses the execution of the function until the promise is either resolved or rejected

```JavaScript
async function runLongRunningTask () {
    const data = await longRunningTask();
    console.log(data);
}

runLongRunningTask()
// Result (After 10 seconds): ['Promise Resolved. This is the data']

```

</p>

#### Conclusion

<p> 
In conclusion, the await keyword in JavaScript is a powerful tool that can be used with any function or expression that returns a Promise. While commonly associated with asynchronous tasks like fetching data from APIs, its versatility extends to a wide range of scenarios, including database operations, file handling, timers, third-party API integrations, and more. By allowing you to await asynchronous operations, async and await contribute to code that is more readable, maintainable, and efficient, simplifying the process of working with asynchronous tasks in JavaScript.

</p>
