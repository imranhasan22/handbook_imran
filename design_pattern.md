# Index
- [Code Smells](#code-smells)
    - [Within Classes](#code-smells-within-classes)
        - [Comment](#comment)
        - [Long Method](#long-method)
        - [Long Parameter List](#long-parameter-list)
    - [Between Classes](#)
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