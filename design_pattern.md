# Index
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