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
