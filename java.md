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
It represent an instance of a class. It's a runtime entity that holds the state and behaviour of a class.

Objects are create using the `new` keyword. Each object is stored at a unique memory location.
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
## Method Overriding
The ability of a subclass to re-implement an instance method inherited from a superclass is called method overriding.
- overriding method must have same argument list and return type.
- final, static, constructor method can't be overriden.