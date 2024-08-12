# Class
A java class is a group of values with a set of operations to manipulate this values.

It is a blueprint for creating objects. A class encapsulates data for the object and methods to manipulate that data. It is use to define a new data type(primitive).
## Attributes
Variables and methods used in the class are called attributes/fields. Attributes are accessed by creating an object of the class and dot notation.

__A class contains following members:__
- Instance Variables
- Methods
- Constructor

## Instance Variable
Variable defined within a class are called instance variables because each instance of the class(that is,each object of the class) contains its own copy of these variable.

# Object
It represent an instance of a class. It's a runtime entity that holds the state and behaviour of a class. Object is a class type variable. When you create a class, you are creating a new data type. And you can use this data type by declaring objects of this data type.

Each time you create an object of a class, a copy of each instance variables is created except static varible, its create only once.

Objects are create using the `new` keyword. Each object is stored at a unique memory location.
__Create Object:__
```java
Box myBox; // reference
myBox=new Box(); // allocate
```

## `new` Operator
It is used to create new objects
- allocates memory for the object on the heap
- initializes the object by calling its constructor
- returns a reference to that memory which is used to access the object's methods and attributes.
# Constructor
A class contructor if defined is called whenever a program creates an object of that class. It is invoked directly when an object is created and before new operator execute completely.

It doesn't have any return type, not even void and hence can't return any values. It is used to initialize objects. It is called when an instance of a class is created, and it usually sets initial values for the objects attributes.

__Types:__
1. default constructor
2. parameterized constructor

## Default Constructor
A default constructor is automatically provided by the java compiler if no constructors are explicitly defined in a class. It initializes object fields with default value(null, 0).
## Parameterized Constructor
A parameterized constructor accepts parameters, allowing you to initialize the objects fields with specific values at the time of creation.

## Constructor Chaining
It refers to the process of calling one constructor from another within the same/different class. It is used to reduce code duplication and ensure proper initialization.

# this, super keyword
- anywhere in the program
# this(), super() method
- only inside constructor
- must be first statement in a constructor.
- can't be use together

# Method
variables used in method signature are called parameter, and variables used during call are called arguments.


## Method Overloading
When more than one method with the same name is defined in the same class,it is known as method overloading as long as their parameter declarations are different.

__Method overloading is a way to achieve `static polymorphism` in java.__

## Method Overriding
The ability of a subclass to re-implement an instance method inherited from a superclass is called method overriding.
- overriding method must have same argument list and return type.
- final, static, constructor method can't be overriden.

__Method overloading is a way to achieve `dynamic polymorphism` in java.__
# Access Modifier
## `static`
- variable is declare outside method, constructor or any block
- variable can be used as common property(variable) of all objects of it's class as it's belong to class not object
- don't make multiple copy for multiple object.
## `final`
- class can't be inherited
- method can't be overriden
# OOP
__Key Concepts of OOP:__
- [Encapsulation](#encapsulation)
- [Inheritance](#inheritance)
- [Polymorphism](#polymorphism)
- [Abstraction](#Abstraction)

## Encapsulation
It involves bundling member of class into a single unit. It also invloves restricting access to some of the objects components, which is achieved by using access modifier like `private`, `protected`, `public`. The key idea is keep the internal represention of an object hidden from outside world.
```java
class BankAccount{
    private String accountNumber;
    BankAccount(String accountNumber){
        this.accountNumber=accountNumber;
    }
    public getAccountNumber(){ return accountNumber; }
}
```
- `accountNumber` cannot be accessed directly from outside the `BankAccount` class.
- `getAccountNumber()` methods provides read-only access to the `accountNumber`, ensuring that it cannot be changed from outside the class.

## Inheritance
It allow child class to inherit properties from parent class

- Java doesn't support multiple inheritance through classes but supports it through interfaces.
- Sub-class can override method defined in parent class.

__Types:__
1. Single Inheritance
2. Multilevel Inheritance - chain of class
3. Hierarchical Inheritance - multiple classes inherited from a single parent class
4. Multiple Inheritance - single child class inherited from multiple parent class(not supported through classes)

### Multiple Inheritance
```java
interface CanFly{
    void fly();
}

interface CanSwim{
    void swim();
}

class Duck implements CanFly, CanSwim{
    public void fly(){ System.out.println("Duck can fly"); }
    public void swim(){ System.out.println("Duck can swim"); }
    public void sound(){ System.out.println("I'm Duck"); }
}
```
__Wrong way:__
```java
class CanFly{
    public void fly(){ System.out.println("Duck can fly"); }
}

class CanSwim{
    public void swim(){ System.out.println("Duck can swim"); }
}

class Duck extends CanFly, CanSwim{
    public void sound(){ System.out.println("I'm Duck"); }
}
```

## Polymorphism
It refers to the ability of a single interface to represent different underlying forms(data types). It allows objects to be treated as instances of their parent class rather than their actual class.

__Types of polymorphism:__
- Static/Compile-Time Polymorphism
- Dynamic/Run-Time Polymorphism

### Static(Overloading)
```java
class Calculator{
    public int add(int a, int b){ return a+b; }
    public int add(int a, int b, int c){ return a+b+c; }
    public int add(int a, int b, int c, int d){ return a+b+c+d; }
}

public static void main(String[] args){
    Calculator calc=new Calculator();
    System.out.println(calc.add(10,20));
    System.out.println(calc.add(10,20,30));
    System.out.println(calc.add(10,20,30,40));
}
```
### Dynamic(Overriding)
```java
class Animal{
    public void sound(){
        System.out.println("Animal makes a sound");
    }
}
class Dog extends Animal{
    @Override
    public void sound(){
        System.out.println("Dog makes a sound");
    }
}
class Cat extends Animal{
    @Override
    public void sound(){
        System.out.println("Dog makes a sound");
    }
}

public static void main(String[] args){
    Animal animal=new Animal();
    Dog dog=new Dog();
    Cat cat=new Cat();

    animal.sound();
    dog.sound();
    cat.sound();
}
```
## Abstraction
It focuses on `hiding the internal implementation` of a class and exposing only the essential features to the outside world. It can't instantiated on its own and is meant to be subclassed. Abstraction is primarilly achieved using `abstract` classes and `interface`s.
### `abstract` classes
- can have both abstract & concrete method.
- can have instance variable
- can have constructor
- object can't be created
```java
abstract class Shape{
    abstract void draw();
    void display(){ System.out.println("This is a shape"); }
}
class Circle extends Shape{
    void draw(){ System.out.println("Drawing a circle"); }
}
```
### `interface`
- only have abstract method
- only `final` variable
- can't have constructor
- multiple inheritance is possible
```java
interface Shape{
    void draw();
}
class Circle implements Shape{
    public void draw(){ System.out.println("Drawing a circle"); }
    public void display(){ System.out.println("This is a shape"); }
}
```