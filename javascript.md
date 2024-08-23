# Index
- [Javascript](#javascript)
    - [Syntactic Sugar](#syntactic-sugar)
    - [Expression](#expression)
    - [Statement](#statement)
    - [Variable Declaration](#variable-declaration)
    - [Temporal Dead Zone](#temporal-dead-zone)
    - [Error](#error)
    - [Exception](#exception)
    - [throw](#throw)
    - [Error Object](#error-object)
    - [Truthy](#truthy)
    - [Falsy](#falsy)
    - [Console](#console)
- [Thread](#thread)
- [Execution Context](#execution-context)
- [Synchronous](#synchronous)
- [Asynchronous](#asynchronous)
# Javascript
## Syntactic Sugar
It refers to syntax that makes code easier to write and read but doesn't add new functionality to the language. It actually a shorthand for a common operation that could be expressed in an alternate.
- Arrow Functions
- Template Literals
- Destructuring Assignments
- Defautl Parameters
- Class
## Expression and Statement
Expression produce value, statement perform an action
### Expression
A valid unit of code that resolves to a value.
- as simple as a number or a variable or a function.
- expression written in a single line
- a function stored in a variable(`var`, `let`, `const`) will be called expression as it's produce(return) value which may stored in that variable.
- Example: `5`, `x+2`, `Mat.max(1,2)`
```js
const someFunc=()=>{
    // Function Expression
}
```
### Statement
A complete unit of execution.
- do not return a vaule but execute some some logic.
- a normal function without variable declaration(`var`, `let`, `const`) is a statement as it's perform an action when it is called
- Example: `let x=5;`, `if(x<4){`
```js
someFunc(){
    // Function Statement
}
```
## Variable Declaration
- updating/re-assigning `const` variable create `TypeError: Assignment to constant variable.` error.
    ```js
    const a="hello";
    a="hi";
    ```
- a variable with same name can be declare twice with `var` but not with `let` and `const`, it will create `SyntaxError: Identifier 'a' has already been declared`.
    ```JS
    let a='hello'; // ERROR
    let a="hi"; // ERROR

    var b="hello";
    var b="hello";
    ```
    a  variable with same name can be declare twice with `let` if both are in different scope, this is not applicable for `const`. 
    ```js
    let a=5;
    console.log(a);
    {
        let a=4;
        console.log(a);
    }
    console.log(a);
    ```
- `var` maintain function/global scope, `let` and `const` maintain local scope.
- Using any variable before declaration with `var` return `undefined` due to hoisting but with `let` and `const` it will return an error of `ReferenceError: Cannot access 'myVariable' before initialization` due to temporal deadzone.
    ```js
    console.log(myVariable);
    let myVariable="Hello";
    ```
### Temporal Dead Zone
Variables declared with `var` are hoisted at the top of their function scope. It means they are initialized with `undefined` even before the code execution reaches the declaration.

However, variables declared with `let` and `const` are also hoisted but they are not initialized. Instead, they are placed in the Temporal Dead Zone frome the start ot the block until the declaration is encountered
## Error 
### Error 
An object that represents an issue that occurs during the execution of a program. It is a buit-in object with several types such as `TypeError`, `ReferenceError`, `SyntaxError`, `RangeError`.
```
let x=1;
console.log(y); // ReferenceError
```
### Exception
When an error occurs, it creates an exception that handleed using `try`, `catch`, `finally`.
```
try{
    let x=1;
    console.log(y); // ReferenceError
}catch(error){
    console.log(error)
}
```
In summary, error is a problem and exception is the handling mechanism for such problems.
### throw
It is used to create and throw custom errors or exceptions. By using `throw` you are generating an exception that disrupts the normal flow of the code, allowing it to be caught and handled by `try...catch` blocks.
```
const age=17;
try{
    if(age<18){
        throw("You are too young");
        console.log("will not execute");
    }else{
        console.log("your are adult");
    }
}catch(error){
    console.log("will not execute");
    console.log(error);
}
```
It allows you to create and propagate exceptions, enabling you to handle errors and control the flow of your program when something goes wrong.
### Error Object
The `Error` object is a buit-in object that provides a standarized way to handle and describe errors in a program.

__Properties:__
- `name` - represent the name of the error type.
- `message` - describe the error.
- `stack` - details about the error.

__Handle Error:__
```
try{
    if(age<18){
        throw new Error("You are too young");
    }else{
        console.log("your are adult");
    }
}catch(error){
    console.log(error.name); // Error
    console.log(error.message); // You are too young
    console.log(error.stack);
}
```
__Custom Error:__
```
class CustomError extends Error{
    constructor(message){
        super(message);
        this.name="Custom Error";
        this.stack="Error Occured at specific line";
    }
}
let customError=new CustomError("Error Occurred");
console.log(customError.name) // Custom Error
console.log(customError.message) // Error Occurred
console.log(customError.stack) // Error Occured at specific line
```
## Truthy
A `truthy` value is any value that is considered `true` when encountered a boolean context. All values are truthy unless they are defined as falsy.
- non-zero numbers
- no-empty strings
- objects and arrays even empty object and array
- any function
- `new Date()` is truthy
- `Symbol()` is truthy
- `Infinity` and `-Infinity` both are truthy
## Falsy
A `falsy` value is any value that is considered `false` when encountered a boolean context. There are only few falsy values in javascript:
- `0`, `-0`, `false` are falsy
- BigInt zero `0n` is falsy
- empty string
- `null`, `undefined`, `NaN` is falsy
## Console
- to write multiple line in console use `shift+Enter`
# Thread
## Process
A process is an independent program in execution with its own memory space

## Thread
A thread is the smallest unit of execution within a process. It allow a program to perform multiple task simultaneously.

## Multithread
Multiple threads can exist within the same process sharing the same space but executiong independently.

## Threads in Javascript
Javascript is inherently single-threaded, meaning it execute one operation at a time within a single thread.
1. __Heap__ is s region of memory where javascript store variables.
2. __Call Stack__

    Where js keeps track of function calls and their execution context. When a function is invoked, it gets added to the call stack. Once the execution is complete, it gets removed from the stack.
3. __Execution Context__

    Before any code runs, javascript creates an execution context which is responsible for setting up the environment where your code runs.
## Multithreads in Javascript
Modern js environment offer ways to simulate multit-hreading through web workers and other concurrency mechanisms.
1. __Web Workers__

    It allow js to run scripts in the background, independent of the main execution thread. It enable task that are computionally heavy run without blocking the user interface
2. __Callback Queue__

    Contain a list of tasks that are waiting to be executed. When an asynchronous operation completes, its callback is placed in the callback queue.
3. __Event Loop__
    
    Its primary job is to continously monitor the call stack and callback queue, managing the execution of code, collectiong and processing events and executiong sub-tasks.
# Execution Context
## Types
- [Global Execution Context](#global-execution-context)
- [Functon Execution Context](#functon-execution-context)
- [Eval Execution Context](#eval-execution-context)
```js
const root=5;
const squareNumber=(n)=>{
    int a=n*n;
    return a;
}
const square=squareNumber(root);
```
## Memory Management
- [Heap](#heap)
- [Callstack](#callstack)
## Phases of Execution
- [Creation Phase](#creation-phase)
- [Execution Phase](#execution-phase)
### Global Execution Context
- Created when javascript starts executing
- It's the base execution context
- It hase the global object
    - `window` in browser
    - `global` in Node.js
- `this` pointing the global object
- variable and functions declared at the global level are stored in this context
### Functon Execution Context
- Created whenever a function is invoked
- Each funtion call has its own execution context
- contain local variable, `arguments` object
### Eval Execution Context
- Created when code is executed inside an `eval` function
### Creation Phase
Memory is allocated for variables and functions. Variables are set to `undefined`([Hoisting](#hoisting)), and functions are stored the function body.

__Explaination:__
- Global Execution Context
    - memory allocate for `root` and values set to `undefined`
    - memory allocate for `squareNumber` and values set to the description of the function
- Function Execution Context
    - memory allocate for `a` and values set to `undefined`
    - pushed the new execution context onto the stack
### Execution Phase
- Code is executed line by line
- variables are assigned their actual values(replacing `undefined`)

__Explaination:__
- Global Execution Context
    - `root` variable replace it's value with `5` instead of `undefined`
    - return the value of `squareNumber` whenver it is called
- Function Execution Context
    - replace the value of `a` with `n*n`
    - return the value of `a` when the function is invoked
## Callstack
- its also called `Execution Context Stack`
- whenever a new execution context is created(a function is invoked), it is pushed onto the stack
- when a function is completes, its execution context is popped off the stack
## Heap
- it stores the value of the variables, functions.
# Synchronous vs Asynchronous
Most of the language work synchronously by default. Javascript is a synchronous programming language also but if we want to work with any remote server which is called ajax call, javascript behaves like asynchronous. 

## Synchronous
It means each statement is executed one after the other, in order they appear in the code(Top to Bottom). Synchronous code `blocks` the execution of subsequent code until the current operation finishes. It's operations is slow and you can predict the order of execution as well.
```js
const processOrder=(orderNumber)=>{
    console.log(`Processing Order ${orderNumber}`);

    let currentTime=new Date().getTime();
    while(currentTime+3000>=new Date().getTime());

    console.log(`Proceed Order ${orderNumber}`);
}
console.log("Take Order 1");
processOrder(1);
console.log("Completed Order 1");
console.log("Take Order 1");
processOrder(2);
console.log("Completed Order 1");
```
## Asynchronous
It allow to handle operations that take time to complete such as network request, file reading, timers erct `without blocking` the main thread.
```js
const processOrder=(orderNumber, requiredTime)=>{
    console.log(`Proces Order Start ${orderNumber}`);

    setTimeout(()=>{
        console.log(`Processing Order ${orderNumber}`);
    },requiredTime);

    console.log(`Proceed Order ${orderNumber}`);
}
console.log("Take Order 1");
processOrder(1, 3000);
console.log("Completed Order 1");
console.log("Take Order 1");
processOrder(2,5000);
console.log("Completed Order 1");
```
# OOP
## Class
Unlike other programming language, there is nothing about `class` programming till ES5. Which create confusion about is it really a oop laguage or not?

But the actual scenario is, yes, it is a oop language, but unlike other language it is not `class` based language. ES6 solved the issue.
### ES5
```
var Parent=function(name, dob){
    this.name=name;
    this.dob=dob;
    this.details=function(){
        return "name: "+name+" dob:"+dob;
    }
}
```
### ES6
```
class Parent{
    constructor(name, dob){
        this.name=name;
        this.dob=dob;
    }
    details=()=>{
        return `name: ${this.name} age: ${this.dob}`;
    }
}
```
## Inheritance
```
class Teacher extends Parent{
    constructor(name, dob, subject){
        super(name, dob);
        this.subject=subject;
    }
    details=()=>{
        return `name: ${this.name} age: ${this.dob} sub: ${this.subject}`;
    }
}
```
## Constructor
### Default Function Constructor
#### ES5
```
var Parent=function(name, dob){
    name?name=name:name="masum";
    dob?dob=dob:dob="june";

    this.name=name;
    this.dob=dob;
}
```
#### ES6
```
var Parent=function(name="masum", dob="june"){
    this.name=name;
    this.dob=dob;
}
```