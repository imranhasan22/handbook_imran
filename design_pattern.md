# Content
- [Code Smells](#code-smells)
    - [Within Classes](#code-smells-within-classes)
        - [Comment](#comment)
        - [Long Method](#long-method)
        - [Long Parameter List](#long-parameter-list)
        - [Duplicate Code](#duplicate-code)
        - [Dead Code](#dead-code)
        - [Large Class](#large-class)
    - [Between Classes](#between-classes)
        - [Data Class](#data-class)
        - [Data Clumps](#data-clumps)
        - [Alternative Classes with Different Interfaces](#alternative-classes-with-different-interfaces)
        - [Refused Bequest](#refused-bequest)
        - [Lazy Class](#lazy-class)
        - [Shotgun Surgery](#shotgun-surgery)
- [Solid Principle](#solid-principle)
    - [Single Responsibility Principle (SRP)](#single-responsibility-principle-srp)
    - [Open/Closed Principle (OCP)](#openclosed-principle-ocp)
    - [Liskov Substitution Principle (LSP)](#liskov-substitution-principle-lsp)
    - [Interface Segregation Principle (ISP)](#interface-segregation-principle-isp)
    - [Dependency Inversion Principle (DIP)](#dependency-inversion-principle-dip)
- [Design Patterns](#design-patterns)
    - [Creational Design Pattern](#creational-design-pattern)
        - [Singleton Method Design Pattern](#singleton-method-design-pattern)
        - [Factory Method Design Pattern](#factory-method-design-pattern)
        - [Abstract Factory Method Design Pattern](#abstract-factory-design-pattern)
        - Prototype Method Design Pattern
        - Builder Method Design Pattern
    - [Structural Design Pattern](#structural-design-pattern)
        - [Adapter Method Design Pattern](#adapter-method-design-pattern)
        - [Decorator Method Design Pattern](#decorator-method-design-pattern)
        - Bridge Method Design Pattern
        - Composite Method Design Pattern
        - Facade Method Design Pattern
        - Flyweight Method Design Pattern
        - Proxy Method Design Pattern
    - Behavioral Design Pattern
        - Chain Of Responsibility Method Design Pattern
        - Interpreter Method Design Pattern
        - State Method Design Pattern
        - Strategy Method Design Pattern
        - Template Method Design Pattern
        - Visitor Method Design Pattern
        - Command Method Design Pattern
        - Mediator Method Design Pattern
        - Memento Method Design Patterns
        - Observer Method Design Pattern
# Code Smells
When we work on an application and write codes for it, we see a few patterns that are needed to be refactored. Those patterns either `duplicates`, or might make `code dependent on other code`. Such patterns are called Code Smells and detection of such code is called Code Smelling.

Code Smells are not the bugs of the program. With code smells too, your program might work just fine. They do not prevent the program from functioning or are incorrect. They just signify the weakness in design and might increase the risk of bugs and program failure in the future.

## Types of Code Smells
Although there are more than a hundred of code smells. The list of the most common and the most repeating code smells are given below. These are broadly divided into `2 main categories`.
    - Within Classes
    - Between Classes
## Code Smells Within Classes
### Comment
Comment can be used for explaining the code. But what if our written code is self-explanatory, then we don't need to use comment. Overuse or missuse can give worst readiability experience.

__Definition:__ Comment Code Smell refers to the overuse or misuse of comments in the code, indicating that the code might be poorly written or not self-explanatory enough.

While comments can be helpful in explaining complex logic, excessive or unnecessary comments often suggest that the code itself could be improved to become more readable or self-explanatory.

#### Why Comment Code Smell is a Problem?
- __Redundant Comments:__ When comments explain something that is obvious from the code itself, they become redundant.

    __Example:__
    ```java
    // This is a constructor for the Customer class
    public Customer() {
        // Initialize the customer's name to an empty string
        this.name = "";
        // Set the customer's age to zero
        this.age = 0;
    }
    ```
    The comments here are stating what is already clear from the code, a constructor.
    __Better Approach:__
    ```java
    public Customer() {
        this.name = "";
        this.age = 0;
    }
    ```
- __Outdated Comments:__ Comments can become outdated if the code changes but the comments don’t get updated.

    __Example:__
    ```java
    // Fetch the customer's name from the database
    String customerName = getCustomerNameFromCache();
    ```
    The comment suggests that the code is fetching the customer's name from the database, but the method is actually fetching it from a cache.

    __Better Aproach:__
    ```java
    String customerName = getCustomerName();
    ```
- __Commented-Out Code:__ Leaving large blocks of commented-out code can cause confusion about whether that code is still needed or not.

    __Example:__
    ```java
    public void processPayment(Payment payment) {
        // PaymentGateway gateway = new PaymentGateway();
        // gateway.connect();
        // gateway.process(payment);
    
        payment.processLocally();
    }
    ```
    It’s not clear whether this code should be kept for future use, removed completely, or if it’s obsolete.
    __Better Aproach:__
    ```java
    public void processPayment(Payment payment) {
        payment.processLocally();
    }
    ```
### Long Method 
A long method contains too many lines of code. Any code with more than 25 lines of code should make you question.
#### Why Long Methods Are a Problem
- Reduced Readability
- Harder to Debug
- Low Reusability

__Solution:__ Split the method into smaller methods, each with a single responsibility.
### Long Parameter List
Any function with more parameters is obviously more complex. One of the thumb rules is to use a maximum of 3 to 4 parameters in a function.
#### Why Long Parameter Lists Are a Problem?
- Reduces Readability
- Increases the Likelihood of Errors
- Difficult to Maintain

__Solution:__ When a set of parameters naturally belongs together, group them into a single object and pass it through the method.
### Duplicate Code
Duplicate Code code smell occurs when the same or very similar code appears in more than one place in a program. This is considered problematic because it leads to higher maintenance costs, increases the chances of bugs, and makes code more difficult to modify or extend.

__Solution:__
- __Extract Method__: If you have similar blocks of code in different parts of a class, you can refactor that logic into a separate method. If the duplicated code is found across multiple classes, extract the common code into a shared method(in a different class).
- __Pull-Up Constructor Body__: If multiple classes contain similar behavior, you can use inheritance or interfaces to abstract the shared logic into a base class or interface.
### Dead Code
Dead Code code smell refers to parts of the codebase that are never executed or used in the program.

__Solution:__ Just removed it.
### Large Class
Large Class code smell occurs when a class in an application contains too many responsibilities or too much code, making it difficult to understand, maintain, and modify. This happens when a class tries to handle more than it should, violating the Single Responsibility Principle (SRP), which states that a class should have only one reason to change.

__Solution:__ Just separate into multiple classes.
## Between Classes
### Data Class
A Data Class code smell refers to classes that primarily consist of fields, no methods, may associated with getter and setter methods. It have lacking of meaningful behavior or logic. Instead of having methods that operate on their data, they simply store it.

These classes typically violate key object-oriented principles like encapsulation and cohesion. Instead of encapsulating behavior and acting as meaningful abstractions, they act as mere containers for data. They can’t independently operate on the data that they own.

__Solution:__ introduce some behavior and keep some logic inside the class
### Data Clumps
Data Clumps code smell occurs when the same group of data items (variables, parameters, fields) tend to appear together in multiple places in the code. Instead of repeating the same set of data multiple times, this group should be encapsulated in a class or structure, which reduces duplication, increases readability, and improves maintainability.

__Problem:__
```java
public class Order {
    private String customerName;
    private String customerAddress;
    private String customerPhone;
    
    public Order(String customerName, String customerAddress, String customerPhone) {
        this.customerName = customerName;
        this.customerAddress = customerAddress;
        this.customerPhone = customerPhone;
    }

    public void processOrder(String customerName, String customerAddress, String customerPhone) {
        System.out.println("Processing order for " + customerName);
        System.out.println("Shipping to: " + customerAddress);
        System.out.println("Contact phone: " + customerPhone);
    }

    public void shipOrder(String customerName, String customerAddress, String customerPhone) {
        System.out.println("Shipping order for " + customerName);
        System.out.println("Address: " + customerAddress);
        System.out.println("Phone: " + customerPhone);
    }
}
```
__Solution:__
```java
public class Customer {
    private String name;
    private String address;
    private String phone;

    public Customer(String name, String address, String phone) {
        this.name = name;
        this.address = address;
        this.phone = phone;
    }

    public String getName() {
        return name;
    }

    public String getAddress() {
        return address;
    }

    public String getPhone() {
        return phone;
    }
}

public class Order {
    private Customer customer;
    
    public Order(Customer customer) {
        this.customer = customer;
    }

    public void processOrder() {
        System.out.println("Processing order for " + customer.getName());
        System.out.println("Shipping to: " + customer.getAddress());
        System.out.println("Contact phone: " + customer.getPhone());
    }

    public void shipOrder() {
        System.out.println("Shipping order for " + customer.getName());
        System.out.println("Address: " + customer.getAddress());
        System.out.println("Phone: " + customer.getPhone());
    }
}
```
### Alternative Classes with Different Interfaces
Alternative Classes with Different Interfaces code smell occurs when two or more classes are doing the same or similar jobs but have different method names or interfaces.

__Solution:__ If two classes have similar functionality, merge them into once class with a single interface. If classes perform similar but slightly different tasks, introduce a common interface or abstract class that both classes can implement or inherit from. If the classes can't be merged, you can extract the common functionality into a helper class and delegate the work to it.
### Refused Bequest
Refused Bequest is a code smell that occurs when a subclass inherits methods or properties from a parent class but doesn’t use or “want” them. This can happen when a subclass extends a base class but only needs part of its functionality, resulting in an awkward inheritance relationship. The subclass essentially "refuses" some of the inheritance it receives, leading to unused or irrelevant code in the subclass.

This code smell usually indicates poor inheritance design and violates the Liskov Substitution Principle (LSP), which states that objects of a subclass should be able to substitute objects of the base class without altering the correctness of the program.

__Solution:__ refactor the base class into two or more classes and allow the subclass to inherit from the appropriate one or you can use interface.
### Lazy Class
Lazy Class is a code smell that occurs when a class doesn’t do enough work to justify its existence. This happens when a class is created for a specific purpose but over time ends up with very few methods or limited functionality.

__Soultion:__ Remove unnecessary part, or merge the use full part with a relevent class
### Shotgun Surgery
Shotgun Surgery is a code smell that occurs when a change in one part of the code requires making several small changes across multiple classes or methods.

__Solution:__ Consolidate related behavior into a single class or fewer classes. Group related data into classes, and hide unnecessary dependencies.
# Solid Principle
The SOLID principles are a set of five design principles intended to make object-oriented software designs more understandable, flexible, and maintainable

The SOLID principle helps in reducing tight coupling. Tight coupling means a group of classes are highly dependent on one another which you should avoid in your code.

Opposite of tight coupling is loose coupling and your code is considered as a good code when it has loosely-coupled classes.
Loosely coupled classes minimize changes in your code, helps in making code more reusable, maintainable, flexible and stable.
## Single Responsibility Principle (SRP)
A class should have only one reason to change, meaning it should only have one job or responsibility.
## Open/Closed Principle (OCP)
Software entities (classes, modules, functions, etc.) should be open for extension but closed for modification.
## Liskov Substitution Principle (LSP)
Objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program.
## Interface Segregation Principle (ISP)
Clients should not be forced to depend on interfaces they do not use. Instead of one large interface, multiple smaller and more specific interfaces are preferable.
## Dependency Inversion Principle (DIP)
High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details, and details should depend on abstractions.

__Example__: Suppose a class `BackendDeveloper` directly depends on another class `Database`. This creates tight coupling between the two classes.

__Violation of DIP:__
```java
class Database {
    public void connect() {
        System.out.println("Connected to database");
    }
}

class BackendDeveloper {
    private Database database;

    public BackendDeveloper(Database database) {
        this.database = database;
    }

    public void develop() {
        database.connect();
        System.out.println("Developing backend...");
    }
}
```
__Applying DIP:__
```java
interface DatabaseConnection {
    void connect();
}

class MySQLConnection implements DatabaseConnection {
    public void connect() {
        System.out.println("Connected to MySQL database");
    }
}

class BackendDeveloper {
    private DatabaseConnection databaseConnection;

    public BackendDeveloper(DatabaseConnection databaseConnection) {
        this.databaseConnection = databaseConnection;
    }

    public void develop() {
        databaseConnection.connect();
        System.out.println("Developing backend...");
    }
}
```
# Design Patterns
## Creational Design Pattern
These patterns deal with object creation. They aim to simplify the creation process and provide mechanisms for creating objects in a manner that suits the given situation.
### Singleton Method Design Pattern
Ensures that a class has only one instance and provides a global point of access to it.
#### Structure
- `Private constructor`: This prevents other classes from creating new instances.
- `Static private instance`: This holds the single instance of the class.
- `Static method (getInstance)`: Provides a global point of access to the instance.
#### Example
```java
public class Singleton {
    // Step 1: Create a private static instance of the class.
    private static Singleton instance;

    // Step 2: Make the constructor private to prevent instantiation.
    private Singleton() {
        // ...
    }

    // Step 3: Provide a public static method to get the instance.
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```
### Factory Method Design Pattern
Defines an interface for creating an object but lets subclasses alter the type of object that will be created. This pattern is useful when the creation process varies based on input conditions.
#### Structure
- `Product (interface)`: Defines the interface for objects created by the factory method.
- `Concrete Product`: Implements the product interface.
- `Factory`: Declares the factory method, which returns an object of type Product. It may also define the default implementation of the factory method.
#### Example
```java
// Product interface
interface Animal {
    void speak();
}

// Concrete Products
class Dog implements Animal {
    public void speak() {
        System.out.println("Bark!");
    }
}

class Cat implements Animal {
    public void speak() {
        System.out.println("Meow!");
    }
}

// Factory
class AnimalFactory {
    public Animal getAnimal(String type) {
        if ("Dog".equalsIgnoreCase(type)) {
            return new Dog();
        } else if ("Cat".equalsIgnoreCase(type)) {
            return new Cat();
        }
        return null;
    }
}
```
### Abstract Factory Design Pattern
It provides an interface for creating families of related or dependent objects without specifying their concrete classes. This pattern is especially useful when your system needs to create different types of objects that belong to a group, where each object group is logically related but differs in concrete implementation.
#### Structure
- `Abstract Product`: Declares an interface for a type of product object.
    ```java
    // Abstract product for Button
    interface Button {
        void paint();
    }
    
    // Abstract product for Checkbox
    interface Checkbox {
        void paint();
    }
    ```
- `Abstract Factory`: Declares an interface for creating abstract products.
    ```java
    // Abstract factory
    interface GUIFactory {
        Button createButton();
        Checkbox createCheckbox();
    }
    ```
- `Concrete Product`: Implements the interface to create specific products.
    ```java
    // Concrete product for Windows Button
    class WindowsButton implements Button {
        @Override
        public void paint() {
            System.out.println("Rendering a button in Windows style.");
        }
    }

    // Concrete product for MacOS Button
    class MacOSButton implements Button {
        @Override
        public void paint() {
            System.out.println("Rendering a button in MacOS style.");
        }
    }

    // Concrete product for Windows Checkbox
    class WindowsCheckbox implements Checkbox {
        @Override
        public void paint() {
            System.out.println("Rendering a checkbox in Windows style.");
        }
    }

    // Concrete product for MacOS Checkbox
    class MacOSCheckbox implements Checkbox {
        @Override
        public void paint() {
            System.out.println("Rendering a checkbox in MacOS style.");
        }
    }
    ```
- `Concrete Factory`: Implements the interface to create concrete products.
    ```java
    // Concrete factory for Windows
    class WindowsFactory implements GUIFactory {
        @Override
        public Button createButton() {
            return new WindowsButton();
        }

        @Override
        public Checkbox createCheckbox() {
            return new WindowsCheckbox();
        }
    }

    // Concrete factory for MacOS
    class MacOSFactory implements GUIFactory {
        @Override
        public Button createButton() {
            return new MacOSButton();
        }

        @Override
        public Checkbox createCheckbox() {
            return new MacOSCheckbox();
        }
    }
    ```
- `Client`: Uses the factory methods to create objects but remains unaware of their concrete implementation.
    ```java
    // Client class
    class Application {
        private Button button;
        private Checkbox checkbox;

        // The client code doesn't need to know which factory it works with
        public Application(GUIFactory factory) {
            button = factory.createButton();
            checkbox = factory.createCheckbox();
        }

        public void paint() {
            button.paint();
            checkbox.paint();
        }
    }
    ```
#### Example
```java
// Abstract product for Button
interface Button {
    void paint();
}

// Abstract product for Checkbox
interface Checkbox {
    void paint();
}

// Concrete product for Windows Button
class WindowsButton implements Button {
    @Override
    public void paint() {
        System.out.println("Rendering a button in Windows style.");
    }
}

// Concrete product for MacOS Button
class MacOSButton implements Button {
    @Override
    public void paint() {
        System.out.println("Rendering a button in MacOS style.");
    }
}

// Concrete product for Windows Checkbox
class WindowsCheckbox implements Checkbox {
    @Override
    public void paint() {
        System.out.println("Rendering a checkbox in Windows style.");
    }
}

// Concrete product for MacOS Checkbox
class MacOSCheckbox implements Checkbox {
    @Override
    public void paint() {
        System.out.println("Rendering a checkbox in MacOS style.");
    }
}

// Abstract factory
interface GUIFactory {
    Button createButton();
    Checkbox createCheckbox();
}

// Concrete factory for Windows
class WindowsFactory implements GUIFactory {
    @Override
    public Button createButton() {
        return new WindowsButton();
    }

    @Override
    public Checkbox createCheckbox() {
        return new WindowsCheckbox();
    }
}

// Concrete factory for MacOS
class MacOSFactory implements GUIFactory {
    @Override
    public Button createButton() {
        return new MacOSButton();
    }

    @Override
    public Checkbox createCheckbox() {
        return new MacOSCheckbox();
    }
}

// Client class
class Application {
    private Button button;
    private Checkbox checkbox;

    // The client code doesn't need to know which factory it works with
    public Application(GUIFactory factory) {
        button = factory.createButton();
        checkbox = factory.createCheckbox();
    }

    public void paint() {
        button.paint();
        checkbox.paint();
    }
}

public class Main {
    private static Application configureApplication() {
        Application app;
        GUIFactory factory;

        // Simulating environment detection
        String osName = System.getProperty("os.name").toLowerCase();
        if (osName.contains("mac")) {
            factory = new MacOSFactory();
        } else {
            factory = new WindowsFactory();
        }

        app = new Application(factory);
        return app;
    }

    public static void main(String[] args) {
        Application app = configureApplication();
        app.paint();  // Paints the UI components
    }
}
```
## Structural Design Pattern
Structural patterns deal with object composition and typically help simplify the structure by identifying relationships.
### Adapter Method Design Pattern
Allows objects with incompatible interfaces to work together by wrapping one of the objects with an adapter that performs the necessary conversions.
```java
// Target interface
interface MediaPlayer {
    void play(String audioType, String fileName);
}

// Adaptee
class VLCPlayer {
    public void playVLC(String fileName) {
        System.out.println("Playing VLC file: " + fileName);
    }
}

// Adapter
class MediaAdapter implements MediaPlayer {
    private VLCPlayer vlcPlayer;

    public MediaAdapter() {
        vlcPlayer = new VLCPlayer();
    }

    @Override
    public void play(String audioType, String fileName) {
        if (audioType.equalsIgnoreCase("vlc")) {
            vlcPlayer.playVLC(fileName);
        }
    }
}

// Client
class AudioPlayer implements MediaPlayer {
    private MediaAdapter mediaAdapter;

    @Override
    public void play(String audioType, String fileName) {
        if (audioType.equalsIgnoreCase("vlc")) {
            mediaAdapter = new MediaAdapter();
            mediaAdapter.play(audioType, fileName);
        } else {
            System.out.println("Unsupported media type.");
        }
    }
}
```
### Decorator Method Design Pattern
It allows behavior to be added to individual objects, either statically or dynamically, without affecting the behavior of other objects from the same class. It’s useful when you want to add responsibilities to objects at runtime without modifying their code.

__Component:__
```java
interface Beverage {
    String getDescription();
    double cost();
}
```
__ConcreteComponent:__
```java
class Espresso implements Beverage {
    @Override
    public String getDescription() {
        return "Espresso";
    }

    @Override
    public double cost() {
        return 1.99;
    }
}
```
__Decorator:__
```java
abstract class AddOnDecorator implements Beverage {
    protected Beverage beverage;

    public AddOnDecorator(Beverage beverage) {
        this.beverage = beverage;
    }

    @Override
    public String getDescription() {
        return beverage.getDescription();
    }

    @Override
    public double cost() {
        return beverage.cost();
    }
}
```
__ConcreteDecorators:__
```java
// ConcreteDecorator 1: Adds milk
class MilkDecorator extends AddOnDecorator {

    public MilkDecorator(Beverage beverage) {
        super(beverage);
    }

    @Override
    public String getDescription() {
        return beverage.getDescription() + ", Milk";
    }

    @Override
    public double cost() {
        return beverage.cost() + 0.50;
    }
}

// ConcreteDecorator 2: Adds sugar
class SugarDecorator extends AddOnDecorator {

    public SugarDecorator(Beverage beverage) {
        super(beverage);
    }

    @Override
    public String getDescription() {
        return beverage.getDescription() + ", Sugar";
    }

    @Override
    public double cost() {
        return beverage.cost() + 0.20;
    }
}
```
__Implementation:__
```java
public class CoffeeShop {
    public static void main(String[] args) {
        // Order an Espresso
        Beverage beverage = new Espresso();
        System.out.println(beverage.getDescription() + " $" + beverage.cost());

        // Add milk to the espresso
        beverage = new MilkDecorator(beverage);
        System.out.println(beverage.getDescription() + " $" + beverage.cost());

        // Add sugar to the espresso with milk
        beverage = new SugarDecorator(beverage);
        System.out.println(beverage.getDescription() + " $" + beverage.cost());
    }
}
```