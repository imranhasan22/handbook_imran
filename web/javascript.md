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
    - [IIFE](#iife)
    - [First Class Function](#first-class-function)
    - [Lexical Scoping](#lexical-scoping)
    - [Template Literal](#template-literal)
- [Thread](#thread)
- [Execution Context](#execution-context)
- [Synchronous](#synchronous)
- [Asynchronous](#asynchronous)
- [Callback Function](#callback-function)
- [Promise](#promise)
- [async/await](#asyncawait)
- [Class](#class)
- [Constructor](#constructor)
- [OOP](#oop)
# Javascript
__Dynamic Typing:__ JavaScript is a dynamically typed language, meaning you don't need to declare variable types explicitly. The type is determined at runtime.
__Interpreted Language:__ Unlike compiled languages like C or Java, JavaScript code is interpreted by the browser in real-time, which makes development and debugging more flexible and fast.
__Prototype-based Object Orientation:__ JavaScript uses prototypes rather than classical inheritance models (like in Java or C++). This means objects can inherit properties directly from other objects.
__First-class Functions:__ Functions in JavaScript are first-class citizens, meaning they can be treated like any other variable. They can be passed as arguments, returned from other functions, and assigned to variables.
- high-level
- just-in-time-compiled
- multi-paradigm
- event-driven
- functional
- imperative-programming-style
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

__ReferenceError__: Occurs when a variable that isn’t declared or isn’t accessible is referenced. This often happens due to misspellings, accessing variables in the temporal dead zone, or outside their scope.

__SyntaxError__: Occurs when code does not conform to the correct syntax of the language. This type of error is detected before the code is executed and typically involves missing or incorrect syntax elements.

__TypeError__: Occurs when a value is not of the expected type, such as calling a non-function as a function, or accessing properties on `null` or `undefined`.

__Explaination:__
```js
let i = 50;
for (let i = 0; i < 5; i++) {
    console.log(i);
}
console.log(i);
```
- memory allocate for initial `a` in script object with global scope
- memory allocate for last `a` in script object with local scope
### Temporal Dead Zone
Variables declared with `var` are hoisted at the top of their function scope. It means they are initialized with `undefined` even before the code execution reaches the declaration.

However, variables declared with `let` and `const` are also hoisted but they are not initialized. Instead, they are placed in the Temporal Dead Zone frome the start ot the block until the declaration is encountered.

TDZ refers to the period during which a variable is in scope but cannot be accessed because it has not been initialized.

`var` variable allocate memory in global `window` object but `let` and `const` memory allocate memory in `script` object which is why it handle differntly and value is not initialized. you can access `var` variable within `window` object(`window.variable_name`) but you can't access `let`, `const` variable except their name.
## Error 
### Error 
An object that represents an issue that occurs during the execution of a program. It is a buit-in object with several types such as `TypeError`, `ReferenceError`, `SyntaxError`, `RangeError`.
```js
let x=1;
console.log(y); // ReferenceError
```
### Exception
When an error occurs, it creates an exception that handleed using `try`, `catch`, `finally`.
```js
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
```js
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
```js
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
```js
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
## IIFE
`Immediatley Invoked Function Expression` is a function that runs as soon as it is defined.
### Syntax
```js
(function(){
// your code here
}())
```
__OR__
```js
(function(){
// your code here
})()
```
Function Expression also works with IIFE
```js
const sum=(function(){
    return 10+20;
}())
console.log(sum);
```
`sum` will be `30`, don't need call the function
# First Class Function
- Function can be used as value like storing in variable, passing as arguments, returning as value.
## HOF
High Order Function is a function that either:
- takes one or more functions as arguments.
- returns a function as its result.

__Common HOF in Javascript:__
- [map()](#map)
- [filter()](#filter)
- [reduce()](#reduce)
- [forEach()](#forEach)
- [sort()](#sort)
### Custom HOF
__Example:__
```js
const performOperation=(operation)=>{
    console.log("Operation Request Accepted");
    return operation;
}
const add=(a,b)=>{
    return a+b;
}
const addOperation=performOperation(add);
console.log(addOperation(4,5));
```
`performOperation` is a HOF
# Lexical Scoping
It determines how variable names are resolved in nested functions which is by their position within the source code, specifically where they are declared within the nested scopes (such as functions or blocks).
# Template Literal
It enclosed by backticks(`) rather than a single quote or double quote.
1. __String Interppolation__ - embed expressions directly within the string using `${}`
    ```js
    const name="Masum";
    console.log(`Hello ${name}`);
    consle.log(`The sume of 5 and 6: ${5+6}`)
    ```
2. __Multi-line String__ - create multi-line string without using special character like `\n`
3. __Nesting__
```js
const person={name:"Masum",school:"SSS",college:"HAC",university:"NSTU"}
console.log(`
Name: ${person.name}
Education:
${
`School: ${person.school},
College: ${person.school},
University: ${person.university}
`}
`)
```
4. __Tagged Template Literals__ - It allow to parse template literals with a function.
```js
const tag=(strings,...values)=>{
    console.log(strings);
    console.log(values);
}
const firstperson="Masum";
const secondperson="Billah";
tag`Hello ${firstperson} and ${secondperson}`;
```
- `strings` - An array containing the literal portions of the template(the parts of the string that are not expressions)
- `values` - the rest parameter(`...values`) contains the evaluated values of the embeded expressions(the parts inside `${}`)

__Output:__
```js
[ 'Hello ', ' and ', '' ]
[ 'Masum', 'Billah' ]
```
Don't forget to call the tagged function with backtick. Regular functin output this.
```js
tag(`Hello ${firstperson} and ${secondperson}`)
// Hello Masum and Billah
// []
```
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
It means each statement is executed one after the other, in order they appear in the code(Top to Bottom). Synchronous code `blocks`(whole browser, user can't even click any event) the execution of subsequent code until the current operation finishes. It's operations is slow and you can predict the order of execution as well.
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

But if you look into the output sequence, this doesn't follow proper order, though it execute asynchronously.
```
Take Order 1
Proces Order Start 1
Proceed Order 1
Completed Order 1
Take Order 2
Proces Order Start 2
Proceed Order 2
Completed Order 2
Processing Order 1
Processing Order 2
```
See the output, order completion execute before processing order. But it should be execute sequentially, like take order, process order, complete order. Callback function solve this problem, with callback function we can execute function sequentially as well as asynchronously.

Look at this example, order 1 and order 2 execute sequentially and asynchroously.
```js
const takeOrder=(orderNumber, callback)=>{
    console.log(`Take Order ${orderNumber}`);
    callback(orderNumber);
}
const processOrder=(orderNumber ,callback)=>{
    console.log(`Proces Order Start ${orderNumber}`);

    setTimeout(()=>{
        console.log(`Proceed Order ${orderNumber}`);
        callback(orderNumber)
    },3000);

}
const completeOrder=(orderNumber, callback)=>{
    console.log(`Completed Order ${orderNumber}`);

}

takeOrder(1,(orderNumber)=>{
    processOrder(1, (orderNumber)=>{
        completeOrder(1);
    })
})
takeOrder(2,(orderNumber)=>{
    processOrder(2, (orderNumber)=>{
        completeOrder(2);
    })
})
```
# Callback Function
A callback function is a function that is passed as an `argument` to another function and is `executed after the completion` of that function.

The idea behind a callback function is to make sure that a certain code is executed only after another code has finished executing.

In the script below, due to the asynchronous behaviour of javascript, the processing script run first, then the fetching script. But this shouldn't happen, fetching script should run first, then processing script.
```js
const fetchData=()=>{
    console.log("Fetching Data...")
    setTimeout(()=>{
        console.log("Data Fetched")
    }, 3000)
}
const processData=(data)=>{
    console.log("Processing Data -> "+data);
}
fetchData();
processData("completed");
```
Callback function solve this problem by ensuring the execution of argument function before completion the parente function.
```js
const fetchData=(callback)=>{
    console.log("Fetching Data...")
    setTimeout(()=>{
        console.log("Data Fetched")
        callback("Completed")
    }, 3000)
}
const processData=(data)=>{
    console.log("Processing Data -> "+data);
}
fetchData(processData);
```
## Callback Hell
A situation where multiple nested callbacks are used in asynchronous code, resulting look like pyramid, difficult to read, maintain and debug.
```js
const readFile=(filename, callback)=>{
    setTimeout(() => {
        console.log(`Reading file: ${filename}`);
        callback(null, "file data");
    }, 1000);
}
const processData=(data, callback)=>{
    setTimeout(() => {
        console.log("Processing data");
        callback(null, "processed data");
    }, 1000);
}
const saveFile=(filename, data, callback)=>{
    setTimeout(() => {
        console.log(`Saving file: ${filename}`);
        callback(null);
    }, 1000);
}
const logSuccess=(filename, callback)=>{
    setTimeout(() => {
        console.log(`Success: ${filename} saved successfully`);
        callback(null);
    }, 1000);
}
readFile('file1.txt', (error, data)=>{
    processData(data, (error, processedData)=>{
        saveFile('file2.txt', processedData, (error)=>{
            logSuccess('file2.txt', (error)=>{
                console.log("All operations completed successfully!");
            });
        });
    });
});
```
# Promise
A promise is an object that represent the eventual completion or failure of an `asynchronouse` operation and its resulting value.

## Structure of a Promise
It is created using the `Promise` constructor, which takes a function(called the executor function) with two parameter: `resolve` and `reject`.
```js
const promise=new Promise((resolve, reject)=>{
    // ASYNCHRONOUS OPERATION
    const successful=true;

    successful?resolve():reject();
})
```
The value passed in resolve method catch in the callback function of `then()` method and the value passed in reject method catch in the callback function of `catch()` method
## Using Promise
Promises are used with `.then()` and `.catch()` method to handle the outcomes.
- `then()` is called when the promise is fulfilled
- `catch()` is called when promise is rejected
```js
const promise=new Promise((resolve, reject)=>{
    // ASYNCHRONOUS OPERATION
    const successful=true;

    successful?resolve("Resolve"):reject("Reject");
})

promise.then((resolve)=>{
    console.log(resolve)
    console.log("Then");
}).catch(()=>{
    console.log("Catch");
}).finally(()=>{
    console.log("Finally");
})
```
## Promise Chain
Promises can be chained to run asynchronouse task sequenially which resolve callback hell.
1. __Convert Functions to Return Promises__
For each function that uses a callback, refactor it to return a Promise instead.
    ```js
    const takeOrder=(orderNumber)=>{
        return new Promise((resolve)=>{
            console.log(`Take Order ${orderNumber}`)
            resolve(orderNumber);
        })
    }
    const processOrder=(orderNumber)=>{
        return new Promise((resolve)=>{
            console.log(`Proces Order Start ${orderNumber}`);

            setTimeout(()=>{
                console.log(`Proceed Order ${orderNumber}`);
                resolve(orderNumber)
            },3000);
        })

    }
    const completeOrder=(orderNumber)=>{
        return new Promise((resolve)=>{
            console.log(`Completed Order ${orderNumber}`);
            resolve(orderNumber);
        })
    }
    ```
2. __Chain the Promises__
Once the functions return Promises, chain them using `.then()` and `.catch()` method.
    ```js
    takeOrder(1)
        .then(orderNumber=>processOrder(orderNumber))
        .then((orderNumber)=>completeOrder(orderNumber))
        .catch(()=>console.log("Error Occurred"))
    takeOrder(2)
        .then(orderNumber=>processOrder(orderNumber))
        .then((orderNumber)=>completeOrder(orderNumber))
        .catch(()=>console.log("Error Occurred"))
    ```
# async/await
It is a syntax built on top of Promises that allows writting asynchronous code in a manner that looks synchronouse, making it easier to read and write.
- `async` is a function that returns promises.
- `await` - is a keyword which use to pause execution of the function until the promise is resolved or rejected. It can only be used inside `async` function.
```js
const handleOrder=async(orderNumber)=>{
    const takedOrder=await takeOrder(orderNumber);
    const proceedOrder=await processOrder(takedOrder);
    const compltedOrder=await completeOrder(proceedOrder);
}
handleOrder(1);
handleOrder(2);
```
# Class
Unlike other programming language, there is nothing about `class` programming till ES5. Which create confusion about is it really a oop laguage or not?

But the actual scenario is, yes, it is a oop language, but unlike other language it is not `class` based language. ES6 solved the issue.
## ES5
```js
var Parent=function(name, dob){
    this.name=name;
    this.dob=dob;
    this.details=function(){
        return "name: "+name+" dob:"+dob;
    }
}
```
## ES6
```js
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
# Constructor
## Default Function Constructor
### ES5
```js
var Parent=function(name, dob){
    name?name=name:name="masum";
    dob?dob=dob:dob="june";

    this.name=name;
    this.dob=dob;
}
```
### ES6
```js
var Parent=function(name="masum", dob="june"){
    this.name=name;
    this.dob=dob;
}
```
# OOP
- [Encapsulation](#encapsulation)
- [Inheritance](#inheritance)
- [Polymorphism](#polymorphism)
- [Abstraction](#abstraction)
## Encapsulation
Encapsulation is about bundling the data (properties) and methods that operate on that data within a single unit, typically an object or a class.
```js
class BankAccount {
  #accountNumber;  // Private field using #

  constructor(accountNumber) {
    this.#accountNumber = accountNumber;
  }

  getAccountNumber() {
    return this.#accountNumber;
  }
}
```
- `public` - all properties and methods of a class are public by default.
- `private` - Properties or methods defined with `#` cannot be accessed or modified outside the class
- `protected`- Properties or methods defined with `_` can be accessible within the class and its subclasses but not from outside.
## Inheritance
```js
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
## Polymorphism
Polymorphism allows methods to do different things based on the object they are called on. It allows a child class to provide a specific implementation of a method already defined in its parent class.
```js
class Animal {
  speak() {
    return 'The animal makes a sound.';
  }
}

class Dog extends Animal {
  speak() {
    return 'The dog barks.';
  }
}

class Cat extends Animal {
  speak() {
    return 'The cat meows.';
  }
}

const myDog = new Dog();
const myCat = new Cat();

console.log(myDog.speak());
console.log(myCat.speak());
```
## Abstraction
Abstraction means hiding the complexity of the implementation and exposing only the essential details.
```js
class BankAccount {
  constructor(balance) {
    this._balance = balance; // Private variable (conventionally)
  }

  deposit(amount) {
    if (amount > 0) {
      this._balance += amount;
      console.log(`Deposited: $${amount}`);
    } else {
      console.log('Invalid deposit amount.');
    }
  }

  withdraw(amount) {
    if (amount > 0 && amount <= this._balance) {
      this._balance -= amount;
      console.log(`Withdrew: $${amount}`);
    } else {
      console.log('Invalid withdrawal amount.');
    }
  }

  getBalance() {
    return this._balance;
  }
}

const account = new BankAccount(1000);
account.deposit(500);
console.log(account.getBalance()); // Output: 1500
account.withdraw(300);
console.log(account.getBalance()); // Output: 1200
```
__Explaination:__
- The `_balance` property is conventionally treated as private (though it can still be accessed directly). This encapsulates the balance from direct modification.
- `deposit()`, `withdraw()`, and `getBalance()` methods provide controlled ways to interact with _balance.
- The user of the `BankAccount` class doesn't need to know how the balance is updated internally—they just use the methods