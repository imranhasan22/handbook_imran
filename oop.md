# Content
- [Generalization](#generalization)
- [UML](#uml)

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

- [Structural Diagram](#structural-diagram)
  - [Class Diagram](#class-diagram)
  - Component Diagram
  - Composite Structure Diagram
  - Deployment Diagram
  - Package Diagram
  - [Object Diagram](#object-diagram)
  - Profile Diagram
- [Behavioural Diagram](#behavioral-diagrams)
  - [Activity Diagram](#activity-diagram)
  - State Machine Diagram
  - Interaction Diagram
    - Communication Diagram
    - [Sequence Diagram](#sequence-diagram)
    - Interaction Overview Diagram
    - Timing Diagram
  - [Use Case Diagram](#use-case-diagram)

## Structural Diagram
Structure Diagrams focus on the static aspects of the system, specifically how the system is organized and how its components interact with each other. They define the physical structure of the system, including the arrangement of classes, objects, and packages.
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
Behavior Diagrams are used to model the dynamic aspects of a system—essentially, how the system behaves over time. They represent interactions, activities, and the flow of information or control within the system. These diagrams are particularly helpful for understanding what actions the system or its objects perform and how they interact.
### Use Case Diagram
It represents the system's functional requirements from an end-user's perspective and the interactions between actors (users or external systems) and a system to achieve specific goals. It gather the system needs and depicts the external view of the system.

__Components:__
- __Actors:__ External entities (users, systems) that interact with the system.
- __Use Cases:__ Functions or services the system provides.
- __Relationships:__ Shows how actors interact with use cases.
    - __Association:__ Connects actors to use cases, indicating that an actor participates in a use case.
    - __Include:__ A relationship where a use case is always included as part of another use case.
    - __Extend:__ Indicates optional behavior that extends the functionality of a use case.
- __System Boundary:__ Defines the scope of the system being modeled.

#### Example
Merge this two diagram and build one single diagram.
```
+-----------------------------------------+
|          Library Management System      |
|-----------------------------------------|
|                                         |
|  Student/Member                         |
|   ├── Search Book                       |
|   ├── Borrow Book                       |
|   |     └── (include) Search Book       |
|   ├── Return Book                       |
|   |     └── (extend) Pay Fine           |
|   ├── Reserve Book                      |
|   └── Pay Fine                          |
|                                         |
|  Librarian                              |
|   ├── Issue Book                        |
|   |     └── (include) Search Book       |
|   ├── Receive Returned Book             |
|   ├── Manage Book Records               |
|   └── Manage Member Records             |
|                                         |
|  Admin                                  |
|   ├── Generate Reports                  |
|   └── Add Librarian                     |
|                                         |
+-----------------------------------------+

+-----------------------------------------+
|       Library Management System         |
+-----------------------------------------+
|  [Search Book]                          |
|  [Borrow Book]                          | <-- include --> [Search Book]
|  [Return Book]                          | <-- extend --> [Pay Fine]
|  [Reserve Book]                         |
|  [Pay Fine]                             |
|  [Manage Book Records]                  |
|  [Issue Book]                           | <-- include --> [Search Book]
|  [Receive Returned Book]                |
|  [Manage Member Records]                |
|  [Generate Reports]                     |
|  [Add Librarian]                        |
+-----------------------------------------+
     ^            ^            ^
    /              |             \
Student/Member   Librarian       Admin

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