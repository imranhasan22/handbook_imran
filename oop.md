# Generalization
Generalization is a fundamental concept in object-oriented programming (OOP). It refers to the process of extracting shared characteristics (attributes and behaviors) from two or more specific classes to create a more general class, which can serve as their parent or base class. This parent class is considered a "generalized" version of the more specific child classes.

__Example:__ Consider the case of vehicles. There are many types of vehicles (e.g., cars, bikes, trucks), but they all share common features such as having wheels, engines, and the ability to move. Therefore, we can generalize these specific types of vehicles into a parent class called "Vehicle."
```lua
             +-------------+
             |   Vehicle    |
             +-------------+
                /     |     \
               /      |      \
       +--------+ +--------+ +--------+
       |  Car   | |  Bike  | |  Truck |
       +--------+ +--------+ +--------+
```
__Implementation:__
```java
class Vehicle {
    String brand, model;
    int wheels;

    Vehicle(String brand, String model, int wheels) {
        this.brand = brand;
        this.model = model;
        this.wheels = wheels;
    }

    void move() {
        System.out.println(brand + " " + model + " moves with " + wheels + " wheels.");
    }
}

class Car extends Vehicle {
    int doors;

    Car(String brand, String model, int wheels, int doors) {
        super(brand, model, wheels);
        this.doors = doors;
    }

    void openDoors() {
        System.out.println(brand + " " + model + " opens " + doors + " doors.");
    }
}

class Bike extends Vehicle {
    String handleType;

    Bike(String brand, String model, int wheels, String handleType) {
        super(brand, model, wheels);
        this.handleType = handleType;
    }

    void ride() {
        System.out.println(brand + " " + model + " ridden with " + handleType + " handles.");
    }
}

public class Main {
    public static void main(String[] args) {
        new Car("Toyota", "Corolla", 4, 4).move();
        new Bike("Yamaha", "YZF", 2, "sport").ride();
    }
}
```
# UML
Unified Modeling Language (UML) is a standardized visual language used to model the structure and behavior of software systems. 
## Structural Diagrams
### Class Diagram
It shows the classes, their attributes, methods, and relationships.
```
+-----------------+       +------------------+
|    Library      |       |    LibraryMember  |
+-----------------+       +------------------+
| name            |       | name             |
| address         |       | membershipId     |
+-----------------+       +------------------+
| addBook()       |       | borrowBook()     |
| removeBook()    |       | returnBook()     |
+-----------------+       +------------------+
        |                         |
        +-------------------------+
                Association (Library contains LibraryMembers)
```
### Object Diagram
It shows a snapshot of the objects at a particular point in time, their states, and their relationships. Similar to class diagrams, but shows actual instances (objects) rather than class definitions.
```
+-----------------+           +------------------+
|    Library1     |           |  Member1: John    |
+-----------------+           +------------------+
| name: CityLib   |           | name: John Doe    |
| address: City A |           | membershipId: 123 |
+-----------------+           +------------------+
                Library1 has Member1 (object relationship)
```
## Behavioral Diagrams
It represents the system's functional requirements from an end-user's perspective.

__Components:__
- __Actors:__ External entities (users, systems) that interact with the system.
- __Use Cases:__ Functions or services the system provides.
- __Relationships:__ Shows how actors interact with use cases.
```
+----------------------------+
|        Library System       |
+----------------------------+
|  [Borrow Book]              |
|  [Return Book]              |
|  [Search Catalog]           |
+----------------------------+
      ^          ^
     /            \
Member         Librarian
```
## Sequence Diagram
It shows how objects interact in a time-sequenced manner.

__Components:__
- `Lifelines:` Represent objects or actors.
- `Messages:` Interactions (method calls) exchanged between lifelines over time.
```
Member          Library       Book
 |                |            |
 |   borrowBook() |            |
 |--------------->|            |
 |                | checkAvail |
 |                |----------->|
 |                | avail=true |
 |<---------------|            |
 |                | lendBook() |
```
## Activity Diagram
It represents workflows and the sequence of activities.

__Components:__
- `Activities:` Actions performed.
- `Transitions:` Movement between activities.
- `Decision Points:` Forks where different paths may be taken.
```
[Start] --> Borrow Book --> [Is Book Available?] --No--> [End]
                                  |
                                 Yes
                                  |
                                Issue Book --> [End]
```
## State Diagram
It models the different states an object can be in and the transitions between those states.

__Components:__
- `States:` Different statuses an object can have.
- `Transitions:` Triggers causing a change from one state to another.
```
[Available] --borrowBook()--> [Checked Out]
 [Checked Out] --returnBook()--> [Available]
```