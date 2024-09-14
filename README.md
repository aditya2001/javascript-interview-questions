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
const calculate = (a, b, operation) => {
        console.log("Result is");
   return operation(a,b);
}
// Define a callback function that takes two arguments
const substraction = (a,b) => {
    return a-b;
}
// Define a callback function that takes two arguments
const addition = (a,b) => {
    return a+b;
}
console.log(calculate(5, 4, addition));
```

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
Problem with function scope of car is , sometimes we want to access information only inside normal block, but with var is it exposed outside normal block and accessible for the entire function.
This could give undesirable results. let and const are block scoped.