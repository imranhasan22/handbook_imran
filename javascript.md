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