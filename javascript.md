# Syntactic Sugar
It refers to syntax that makes code easier to write and read but doesn't add new functionality to the language. It actually a shorthand for a common operation that could be expressed in an alternate.
- Arrow Functions
- Template Literals
- Destructuring Assignments
- Defautl Parameters
- Class
# Expression VS Statement
## Expresssion
A valid unit of code that resolves to a value.
- as simple as a number or a variable or a function.
- Example: `5`, `x+2`, `Mat.max(1,2)`
## Statement
A complete unit of execution.
- do not return a vaule but execute some some logic.
- Example: `let x=5;`, `if(x<4){`
# Synchronous vs Asynchronous
Most of the language work synchronously by default. Javascript is a synchronous programming language also but if we want to work with any remote server which is called ajax call, javascript behaves like asynchronous. 

## Synchronous
It means each statement is executed one after the other, in order they appear in the code(Top to Bottom). Synchronous code `blocks` the execution of subsequent code until the current operation finishes. It's operations is slow and you can predict the order of execution as well.
```
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
```
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
# Error VS Exception
## Error 
An object that represents an issue that occurs during the execution of a program. It is a buit-in object with several types such as `TypeError`, `ReferenceError`, `SyntaxError`, `RangeError`.
```
let x=1;
console.log(y); // ReferenceError
```
## Exception
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
## throw
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
## Error Object
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