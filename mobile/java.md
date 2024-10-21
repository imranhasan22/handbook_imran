Index

- [Class](#class)
- [Object](#object)
- [Constructor](#constructor)
- [Method](#method)
- [Access Modifier](#access-modifier)
- [Keywords](#keywords)
- [Interface](#interface)
- [OOP](#oop)
- [Multitasking](#multitasking)
- [Thread](#thread)
- [File Handling](#file-handling)
# Class

A java class is a group of values with a set of operations to manipulate this values.

It is a blueprint for creating objects. A class encapsulates data for the object and methods to manipulate that data. It is use to define a new data type(primitive).

## Attributes

Variables and methods used in the class are called attributes/fields. Attributes are accessed by creating an object of the class and dot notation.

**A class contains following members:**

- Instance Variables
- Methods
- Constructor

## Instance Variable

Variable defined within a class are called instance variables because each instance of the class(that is,each object of the class) contains its own copy of these variable.

# Object

It represent an instance of a class. It's a runtime entity that holds the state and behaviour of a class. Object is a class type variable. When you create a class, you are creating a new data type. And you can use this data type by declaring objects of this data type.

Each time you create an object of a class, a copy of each instance variables is created except static varible, its create only once.

Objects are create using the `new` keyword. Each object is stored at a unique memory location.
**Create Object:**

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

It doesn't inherited as it's not part of class member.
**Types:**

1. default constructor
2. parameterized constructor

## Default Constructor

A default constructor is automatically provided by the java compiler if no constructors are explicitly defined in a class. It initializes object fields with default value(null, 0).It has the same access modifier as the class.

## Parameterized Constructor

A parameterized constructor accepts parameters, allowing you to initialize the objects fields with specific values at the time of creation.

## Constructor Chaining

It refers to the process of calling one constructor from another within the same/different class. It is used to reduce code duplication and ensure proper initialization.

Each class calls the constructor of its parent class when it is instantiated, leading to a chain of constructor calls. Constructor doesn't inherited as it's not part of the class member. But in every inheritance constructor of parent class will be called, which result constructor chaining.

```java
class SuperParent{
    SuperParent(){
        System.out.println("I'm Super Parent");
    }
    SuperParent(int x){
        System.out.println("I'm Super Parent with "+x);
    }
}
class Parent extends SuperParent{
    Parent(){
        System.out.println("I'm Parent");
    }
    Parent(int x){
        System.out.println("I'm Parent with "+x);
    }
}
class Child extends Parent{
    Child(){
        System.out.println("I'm Child");
    }
    Child(int x){
        System.out.println("I'm Child with "+x);
    }
}
class SuperChild extends Child{
    SuperChild(){
        super(4);
        System.out.println("I'm SuperChild");
    }
    SuperChild(int x){
        System.out.println("I'm SuperChild with "+x);
    }
}
```

# Method

variables used in method signature are called parameter, and variables used during call are called arguments.

## Method Overloading

When more than one method with the same name is defined in the same class,it is known as method overloading as long as their parameter declarations are different.

**Method overloading is a way to achieve `static polymorphism` in java.**

## Method Overriding

The ability of a subclass to re-implement an instance method inherited from a superclass is called method overriding.

- overriding method must have same argument list and return type.
- final, static, constructor method can't be overriden.

**Method overloading is a way to achieve `dynamic polymorphism` in java.**

If a method in a subclass has the same method signature as a method in its superclass, the subclass method overrides the inherited method. If a method in a subclass has the different method signature as a method in its superclass, the subclass method overloads the inherited method.

```java
class SuperParent{
    static void show(double x){
        System.out.println("Super Parent");
    }
}
class Parent extends SuperParent{
    static void show(int x){
        System.out.println("Parent");
    }
}
class Test extends Parent{
    public static void main(String[] args){
        show(4);
        show(4.5);
    }
}
```

# Access Modifier

```
== Everywhere ===========
                        |
==Same Package========  |
			         |  |
== Sub  Class =====  |  |
			      |  |  |
==Parent Class==  |  |  |
|              |  |  |  |
|   PRIVATE    |  |  |  |
|		       |  |  |  |
================  |  |  |
   PROTECTED      |  |  |
===================  |  |
    DEFAULT          |  |
======================  |
     PUBLIC             |
=========================
```

## `static`

- variable is declare outside method, constructor or any block
- variable can be used as common property(variable) of all objects of it's class as it's belong to class not object
- don't make multiple copy for multiple object.
- method can't use `this` or `super` keyword.

**Belongs to the Class:** doen't make multiple instances for multiple object.

```java
class Parent{
    static int x=5;
    void show(){
        System.out.println(x);
    }
}
class Test{
    public static void main(String[] args){
        Parent p1= new Parent();
        Parent p2= new Parent();
        p1.x=10;
        p2.x=10;
        p1.show();
        p2.show();
    }
}
```

As x belongs to the `Parent` class, any modification to `x` through one instance will affect all instances of the class.

**No Access to Instance Variables or Methods:** Static methods can only access other static methods or static variables of the class. They cannot directly access instance variables or methods because they are not associated with an object (instance) and thus have no knowledge of instance-level data. So, we have to create an instance of the class inside static method to access non-static property.

```java
class Test{
    static int x=5;
    int y=10;
    public static void main(String[] args){
        System.out.println(x);
        // System.out.println(y); // on-static variable y cannot be referenced from a static context

        Test t=new Test();
        System.out.println(t.y);
    }
}
```

## `private`

- accessible within the class it is declared
- can't accessible not even in child class

## `protected`

- accessible anywhere within the same package

## `default`

- accessible anywhere within the same package

# Keywords

## `final`

- class can't be inherited
- method can't be overriden
- variable can be inherited but can't modifyable

## this, super keyword

- anywhere in the program

### this

- differentiate the local scope and class scope.
  **Passing Current Object as Argument:**

```java
class ClassB{
    void show(ClassA a){
        System.out.println(a.x);
    }
}
class ClassA{
    int x = 5;
    ClassB b = new ClassB();
    void show(){
        b.show(this);
    }
}
class Test{
    public static void main(String[] args){
        ClassA a = new ClassA();
        a.show();
    }
}
```

**Returning the Current Object:**

```java
class ClassA{
    int x = 5;
    ClassA show(){
        return this;
    }
}
class Test{
    public static void main(String[] args){
        ClassA a = new ClassA();
        ClassA s = a.show();
        System.out.println(s.x);
    }
}
```

### super

- refer immediate parent class

## this(), super() method

- only inside constructor
- must be first statement in a constructor.
- can't be use together

### this()

### super()

- invoke immediate parent class constructor

# Interface

It defines a set of methods that a class must implement. It allows for a form of abstraction, enabling the seperation of what a class can do from how it does it.

- It only contain method signature and declaration.
- All methods are implicitly `public` and `abstract`
- All fields are implicitly `public`, `static`, `final`
- Can't have constructor, meaning you can't instantiate(object creation) direclty
- One interface can extend another interface, and classes are implment interfaces

# OOP

**Key Concepts of OOP:**

- [Encapsulation](#encapsulation)
- [Inheritance](#inheritance)
- [Polymorphism](#polymorphism)
- [Abstraction](#abstraction)

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

**Types:**

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

**Wrong way:**

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

**Types of polymorphism:**

- Static/Compile-Time Polymorphism
- Dynamic/Run-Time Polymorphism

### Static(Overloading)

Define in compilation time.

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

Effect are shown in run-time.

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

# Multitasking

Multitasking is the capability of performing multiple tasks simultaneously. In Java, multitasking can be achieved using two main approaches:

1. [Process-based multitasking (Heavyweight)](#process-based-multitasking)
2. Thread-based multitasking (Lightweight)

## Process-based Multitasking

- Each process has its own memory space.
- Processes do not share memory space with each other.
- Each task is a seperate independent program(process).
- Switching between processes is more expensive because the operating system must save the state of one process and load the state of another.
- Java doesn't directly support process-based multitasking but it can create new processes using classes like `ProcessBuilder` or `Runtime`.

**Example:** Running external programs like opening a file using `Runtime.getRuntime().exec()`.

## Thread-based Multitasking

- A thread is a lightweight sub-process and is the smallest unit of a program that can execute independently.
- All threads of a process share the same memory space.
- Each task is a seperate independent part of same program
- Switching between threads is more efficient compared to processes.
- Java provides built-in support for threads through: - `java.lang.Thread` class - `java.lang.Runnable` interface
  This is the most common form of multitasking in Java, and it is what we generally mean when we refer to multitasking in Java.

# Thread

## Main Thread

It is the initial thread that starts when a Java program begins its execution. It is created by the Java Virtual Machine (JVM) to start running the main() method of a program.

It serves as the entry point for all Java programs and controls the life cycle of other threads if they are created within the main() method.

### Characteristics of the Main Thread

- **Automatically Created:** The JVM automatically creates the main thread when the program starts.
- **Entry Point:** It is the entry point of every Java application, starting with the `main()` method.
- **Thread Name:** By default, the name of the main thread is `main`.
- **Default Priority:** The main thread has a default priority of `5` (normal priority).
- **Control Over Other Threads:** The main thread can create, start, and manage other threads. It continues to run until either the `main()` method completes or the JVM is instructed to exit.
- **Execution Order:** Even though the main thread is the first to start, it does not necessarily finish first, especially if it creates other threads that continue running. The order in which threads finish depends on their tasks and execution.

**Examplee:**

```java
public class Man {
    public static void main(String[] args) {
        // Getting a reference to the main thread
        Thread mainThread = Thread.currentThread();
        System.out.println("Main thread name: " + mainThread.getName());
        System.out.println("Main thread priority: " + mainThread.getPriority());
        System.out.println("Is main thread alive? " + mainThread.isAlive());

        // Setting the name of the main thread
        mainThread.setName("PrimaryThread");
        System.out.println("Renamed main thread: " + mainThread.getName());

        System.out.println("Main thread is ending.");
    }
}
```

## Creation

There are two ways to create threads in Java:

1. Extending the `Thread` class
2. Implementing the `Runnable` interface

### Extending `Thread`

- This approach involves creating a subclass of the `Thread` class and overriding its `run()` method.
- The `run()` method contains the code that defines the task that the thread will execute.

**Example:**

```java
class MyThread extends Thread {
    public void run() {
        // Code that the thread will execute
        for (int i = 1; i <= 5; i++) {
            System.out.println("Thread " + Thread.currentThread().getId() + " is running: " + i);
            try {
                Thread.sleep(500); // Sleep for 500 milliseconds
            } catch (InterruptedException e) {
                System.out.println(e);
            }
        }
    }
}

public class ThreadExample {
    public static void main(String[] args) {
        MyThread t1 = new MyThread(); // Create first thread
        MyThread t2 = new MyThread(); // Create second thread

        t1.start(); // Start the first thread
        t2.start(); // Start the second thread
    }
}
```

### Implementing `Runnable`

- This approach involves creating a class that implements the `Runnable` interface and defining the `run()` method.
- It allows more flexibility because your class does not need to extend `Thread` (which is beneficial when you want to extend another class).

**Example:**

```java
class MyRunnable implements Runnable {
    public void run() {
        // Code that the thread will execute
        for (int i = 1; i <= 5; i++) {
            System.out.println("Thread " + Thread.currentThread().getId() + " is running: " + i);
            try {
                Thread.sleep(500); // Sleep for 500 milliseconds
            } catch (InterruptedException e) {
                System.out.println(e);
            }
        }
    }
}

public class RunnableExample {
    public static void main(String[] args) {
        MyRunnable myRunnable = new MyRunnable();

        Thread t1 = new Thread(myRunnable); // Create first thread
        Thread t2 = new Thread(myRunnable); // Create second thread

        t1.start(); // Start the first thread
        t2.start(); // Start the second thread
    }
}
```

## LifeCycle

- **New:** Thread object is created but `start()` is not yet called.
- **Runnable:** After `start()`, the thread is ready to run but might not be running if the CPU is busy.
- **Running:** The thread is executing its `run()` method.
- **Blocked/Waiting:** The thread is paused, waiting for a resource or a condition to become true.
- **Terminated:** The thread finishes execution or is stopped.

## Methods

### Creation and Control

- `start()` - Starts a new thread by calling its `run()` method. It transitions the thread from the new state to the runnable state.
- `run()` - Contains the code that is executed by the thread. This method should be overridden.
- `yield()` - Suggests to the JVM that the current thread is willing to yield its current use of a processor. It makes the currently running thread move to the runnable state to allow other threads of the same priority to execute.
- `sleep(long millis)` - Causes the current thread to sleep (pause execution) for the specified number of milliseconds.
- `join()` - Waits for the thread on which this method is called to die (finish execution). This can be used to ensure that a thread completes before the execution of another thread continues.
  - Overloads:
    - `join()` - Waits indefinitely.
    - `join(long millis)` - Waits for the specified milliseconds.
    - `join(long millis, int nanos)` - Waits for the specified time in milliseconds and nanoseconds.

### Status and Information

- `isAlive()` - Returns true if the thread is still alive (has been started and has not yet terminated).
- `isInterrupted()` - Returns true if the thread has been interrupted. It does not clear the interrupted status of the thread.
- `getId()` - Returns the unique ID of the thread.
- `getName() / setName(String name)` - Gets or sets the name of the thread.
- `getPriority() / setPriority(int newPriority)` - Gets or sets the priority of the thread (values between `Thread.MIN_PRIORITY` (1) and `Thread.MAX_PRIORITY` (10)). The default is `Thread.NORM_PRIORITY` (5).
- `getState()` - Returns the current state of the thread as an instance of `Thread.State` enum (e.g., `NEW`, `RUNNABLE`, `BLOCKED`, `WAITING`, `TIMED_WAITING`, `TERMINATED`).getId():
  Returns the unique ID of the thread.

### Thread Management

- `currentThread()` (Static method) - Returns a reference to the currently executing thread object.

# File Handling
## `File`
It represents both file and directory pathnames in an abstract manner. It allows us to create, delete, and manipulate files and directories, as well as check file properties.
### Common Methods
1. `exists()`: Checks if a file or directory exists.
2. `createNewFile()`: Creates a new file if it does not exist.
3. `delete()`: Deletes a file or directory.
4. `mkdir()` and `mkdirs()`: Creates a single or multiple directories.
5. `getName()`: Returns the name of the file or directory.
6. `getAbsolutePath()`: Returns the absolute path of the file.
7. `length()`: Returns the size of the file in bytes.
8. `canRead()`, `canWrite()`, `canExecute()`: Checks if the file is readable, writable, or executable.
9. `isFile()` and `isDirectory()`: Checks if the `File` object represents a file or a directory.
10. `list()` and `listFiles()`: Lists files and directories inside a director
### Example
```java
import java.io.File;
import java.io.IOException;

public class FileClassExample {
    public static void main(String[] args) {
        // Step 1: Create a File object for a new file
        File file = new File("example.txt");

        // Step 2: Create the file if it doesn't exist
        try {
            if (file.createNewFile()) {
                System.out.println("File created: " + file.getName());
            } else {
                System.out.println("File already exists.");
            }
        } catch (IOException e) {
            System.out.println("An error occurred while creating the file.");
            e.printStackTrace();
        }

        // Step 3: Display file properties
        System.out.println("File name: " + file.getName());
        System.out.println("Absolute path: " + file.getAbsolutePath());
        System.out.println("Is writable: " + file.canWrite());
        System.out.println("Is readable: " + file.canRead());
        System.out.println("Is executable: " + file.canExecute());
        System.out.println("Is a file: " + file.isFile());
        System.out.println("Is a directory: " + file.isDirectory());
        System.out.println("File size (bytes): " + file.length());

        // Step 4: Create a directory
        File directory = new File("sampleDirectory");
        if (directory.mkdir()) {
            System.out.println("Directory created: " + directory.getName());
        } else {
            System.out.println("Directory already exists.");
        }

        // Step 5: List files in the directory (if there are any)
        System.out.println("Files in the directory:");
        File[] files = directory.listFiles();
        if (files != null && files.length > 0) {
            for (File f : files) {
                System.out.println(" - " + f.getName());
            }
        } else {
            System.out.println("No files found in the directory.");
        }

        // Step 6: Delete the file
        if (file.delete()) {
            System.out.println("File deleted: " + file.getName());
        } else {
            System.out.println("Failed to delete the file.");
        }

        // Step 7: Delete the directory
        if (directory.delete()) {
            System.out.println("Directory deleted: " + directory.getName());
        } else {
            System.out.println("Failed to delete the directory. It may not be empty.");
        }
    }
}
```
## `FileReader`
It is used to read the contents of a file as a stream of characters. It is designed for reading character files and is typically used for reading text data.
### Common Methods
1. `read()` - Reads a single character from the file.
2. `close()` - Closes the file reader and releases any system resources associated with it.
3. `ready()` - Tells whether the input stream is ready to be read.
### Example
```java
import java.io.FileReader;
import java.io.BufferedReader;
import java.io.IOException;

public class FileReaderExample {
    public static void main(String[] args) {
        // Specify the file name to read
        String fileName = "example.txt";
        
        // Using try-with-resources to ensure the file is closed automatically
        try (FileReader fileReader = new FileReader(fileName);
             BufferedReader bufferedReader = new BufferedReader(fileReader)) {
            
            String line;
            // Read the file line by line
            while ((line = bufferedReader.readLine()) != null) {
                System.out.println(line); // Print each line to the console
            }
        } catch (IOException e) {
            System.out.println("An error occurred while reading the file: " + e.getMessage());
        }
    }
}
```