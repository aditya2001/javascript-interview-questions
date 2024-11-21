# javascript-interview-questions

## 1. What is JavaScript?
JavaScript -> JavaScript is a scripting language, its directly executed inside the browser without the need to compile before hand.
It's mostly used to make webpages more interactive like fetching the data, animation, checking for errors etc.
The ability to run in the browser is the biggest advantage of JavaScript.

It's not a standalone language like Java, rather integrated with HTML to make webpages more interactive. 
JavaScript is a loosely types language means user doesn't have to worry about the data type of variable before declaration.

## 2. Dynamic typing in JavaScript?
JavaScript is a dynamic language with dynamic types. variables are not associated with any particular type and any variable can be assigned or reassigned values of different types.
```java
let foo = 42; // foo is now a number
foo = "bar"; // foo is now a string
foo = true; // foo is now a boolean
```

## 3. What are the different JavaScript datatypes ?

### Primitive Data Types ->

| DataType    | Description                   | Examples                        | 
|-------------|-------------------------------|---------------------------------| 
| `String`    | `Sequence of characters`      | `'hello', "hello world!", etc.` |
| `Number`    | `Integer`                     | `3, 3.234, 3e-2, etc.`          | 
| `BigInt`    | `Integer`                     |                                 | 
| `Boolean`   | `true or false`               | `true or false;`                | 
| `Undefined` | `variable not initialized`    | `let a;`                        |
| `Null`      | `null represents empty value` | `	let a = null;`                | 
| `Symbol`    |                               |                                 | 

### Non Primitive Data Types ->
 JavaScript Object -> An Object holds data in the form of key-value pairs. For example,
JavaScript object ae written with curly braces {}. Object properties are written as name:value pairs.
```java 
let student = {
 firstName: "John",
 lastName: null,
 class: 10
 };
```

## 4. What is a callback function in JavaScript?
Callback is a function that is passed as an argument to another function.
Callbacks allow you to continue executing code, while operation is being executed in the background. Once the operation is completed callback is called.This was we can ensure program remains responsive and user experience is not impacted. 

```java 
// Define a function that takes a callback as an argument
function calculate(a, b, operation){
    console.log("Perform operation")
    return operation(a,b);
}
// Define a callback function that takes two arguments
const substraction = (a,b) => {
    return a-b;
}
// Define a callback function that takes two arguments
function addition(a, b){
    return a+b;
}
console.log(calculate(5, 4, addition));
```

## 5. Why use callback in automated testing?
When writing automated tests, especially for web applications, you often encounter asynchronous operations like waiting for elements to load or interacting with APIs. Callback functions help you manage these asynchronous tasks efficiently, ensuring that your test steps execute in the correct order..

```java
function findElement(driver, locator, callback) {
    driver.wait(until.elementLocated(locator), 10000).then(() => {
        driver.findElement(locator).then((element) => {
            callback(element);
        });
    });
}

function click(element){
     element.click().then(() => {
            console.log('Element clicked successfully.');
        });
}

findElement(driver, locator, click);

## 5. Difference between var, let and constant in JavaScript?
In JavaScript type of variables is decided at run time.

| var              | let                   | const                                    | 
|------------------|-----------------------|------------------------------------------| 
| `used initially` | `let has block scope` | `used when we want the value to be same` |

var -> can sometime produce undesirable results.

Function Scope -> Scope is the boundary represented by {}. There are 2 types of blocks function block and normal block.

1. Function Block {} we provide immediately after function declaration.

```java 
function add (){
console.log("print");
}
```

2. Normal block {} - is used with if or for loops.
```java 
if(true){
}
```

## 6. Why is let used instead of var now?
Problem with function scope of var is , sometimes we want to access information only inside normal block, but with var is it exposed outside normal block and accessible for the entire function.
This could give undesirable results. let and const are block scoped.


## 7. Map() method of array?
map() method creates a new array populated with the results of callback method applied on every array element.

```java

let arr = [3, 4, 5, 6];
let modifiedArr = arr.map(function(element){
    return element *3;
});

modifiedArr; // [9, 12, 15, 18]

```

1. map does not change original array.
2. map() creates a new array from calling a function for every array element.


## 8. forEach() method of array?
The forEach() method is passed a callback function as an argument for each element in an array.

```java

const items = [12, 24, 36];
const copy = [];

items.forEach(function (item) {
    copy.push(item);
});

console.log(copy);

```

```java

let userData = [
    {
    displayname: "phone",
    quantity: 1
    },
    {
    displayname: "notebook",
    quantity: 2
    }
];


function formatData(userData){
    const result =[];

    userData.forEach(function(item){
        result.push({
         label: item.displayname,
         value: item.quantity
        });
    })
    console.log(result);
}

formatData(userData);
 
```

## 9. Promises in javascript?

Promise is an object in java script that will produce a value in future.
This usually applied to asynchronous operation. Instead of blocking code execution until data loads, you can define them as promised, so that code execution conitnues
with other parts of the code.It’s a way to handle asynchronous operations more elegantly than callbacks, allowing for better chaining and error handling.

When promise completes, you can use data, in some cases promises pass and some cases it fails.
Promises were introduced to solve the problems associated with callback hell and to provide a more structured way of handling asynchronous operations.
Promise has 3 states -

1. Pending
2. Fulfilled - Promise resolves and returns a value
3. Rejected - Promise fails with an error.

When promise is fulfilled, you can access resolved data in the then method of the promise.

Promise.the(value => {

})

It is also possible that then method can return another promise, so you can chain another then method.

#### When promise is rejected-
When a promise is rejeted, you can access the error information returned in the catch method of the promise.
Think of catch as this doesnot so I catch the error, so that it doesnot break the application.


Promises are consumed using the .then(), .catch(), and .finally() methods:


```java
Promise.then(data => {
   dataIsLoading = false;
})
.catch( error => {
dataIsLoading = false;

})
.finally( ()=> {
    dataLoading = false;
})
```

```java
fetch('https://api.example.com/data')
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));

console.log("This runs immediately, without waiting for the fetch to complete");
```

## 10. Advantages of Promise?
1. Better readability: Promises allow for a more linear and readable code structure.
2. Better error handling: Promises have a standardized way to handle errors using .catch().
3. Chaining: Promises can be easily chained for sequential asynchronous operations.

```java

function fetchUserData(userId) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (userId === 123) {
        const user = { id: 123, name: 'John Doe', email: 'john@example.com' };
        resolve(user);
      } else {
        reject(new Error('User not found'));
      }
    }, 2000);
  });
}

console.log('Fetching user data...');

fetchUserData(123)
  .then((user) => {
    console.log('User data:', user);
  })
  .catch((error) => {
    console.error('Error:', error.message);
  })
  .finally(() => {
    console.log('Operation completed');
  });

console.log('Promise created, waiting for resolution...');
```

### 11. Why do we need to manage asynchronous operations?
1. Multitasking: Users can interact with other parts of the application while waiting for certain operations to finish.
2. Responsiveness: Asynchronous operations allow the UI to remain responsive while waiting for data or processing to complete.
3. API Calls: When fetching data from servers, the response time can vary. Asynchronous operations prevent the application from freezing while waiting for responses.
4. Parallel Operations: Asynchronous programming allows multiple operations to be initiated simultaneously, potentially reducing overall execution time.
