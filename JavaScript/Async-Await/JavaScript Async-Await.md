# JavaScript Async-Await
 
An async function is a function declared with the async keyword, and the await keyword is permitted within it.
#### Meaning of Asynchronous :
#### Start something now and finish it later

#### For example Lets consider :
```javascript
console.log('task11️⃣');
setTimeout(_=>console.log('timeout2⌛'),0)
Promise.resolve().then(_=>console.log('promise3😝'),0)
console.log('task44️⃣');
```
### Output:
```
task11️⃣
task44️⃣
promise3⌛
timeout2😝
```
### Explanation
1. task1 would get executed since its in the mainstream.
2. timeout2 will be queued for the future task.
3. Then the promise3 will be queued to run the micro task queue immediately after the current task.
4. And finally the last console log gets executed right away.

## Async function
An async function is a function declared with the async keyword, and the await keyword is permitted within it. The async and await keywords enable asynchronous, promise-based behaviour to be written in a cleaner style, avoiding the need to explicitly configure promise chains.
 
```javascript
Syntax
asyncfunctionname(param0)
{
statements
}
asyncfunctionname(param0,param1)
{
statements
}
asyncfunctionname(param0,param1,/* … ,*/paramN)
{
statements
}
```

#### Parameters
**name**
The function's name.
**param** (Optional)
The name of an argument to be passed to the function.
**statements** (Optional)
The statements comprising the body of the function. The await mechanism may be used.
 
 
#### Example
```javascript 
const getData = async() => {
    var data = "Hello World";
    return data;
}
 
getData().then(data => console.log(data));
```
#### Output:
Hello World

## Await: 
Await function is used to wait for the promise. It could be used within the async block only. It makes the code wait until the promise returns a result. It only makes the async block wait.
#### Example:
```javascript
const getData = async() => {
    var y = await "Hello World";
    console.log(y);
}
console.log(1);
getData();
console.log(2);
```
#### Output:
```
1
2
Hello World
```

Notice that the console prints 2 before the **“Hello World”**. This is due to the usage of the await keyword. 
