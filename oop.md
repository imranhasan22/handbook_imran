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
It shows how objects interact in a time-sequenced manner. It captures the flow of messages between objects or components, representing their interactions in a time-ordered sequence. Sequence diagrams are often used to model the logic of methods, functions, and use cases, especially to show how various parts of a system collaborate.

__Components:__
- __Actors/Objects:__ Represent the entities (objects, users, or external systems) that interact in the scenario.
- __Lifelines:__ Vertical dashed lines that represent the life span of an object during the interaction.
- __Activation Bars:__ Thicker vertical rectangles(__not dashed__) along a lifeline showing the time an object is active and performing a task.
- __Messages:__ Horizontal arrows between lifelines that represent communication (method calls, responses, or signals). These can be:
    - __Synchronous__ (solid line with a filled arrowhead): Represents a call where the sender waits for a response.
    - __Asynchronous__ (solid line with an open arrowhead): Represents a call where the sender does not wait for a response.
    - __Return Messages__ (dashed line): Represents the return of control or data from the receiver back to the sender.

__Example:__
```
Student          LibrarySystem           Librarian           Database
   |                   |                     |                    |
   |------------------>|                     |                    |
   |   Search Book     |                     |                    |
   |                   |-------------------->|                    |
   |                   |   Verify Availability                    |
   |                   |                     |------------------->|
   |                   |                     |  Check Book Stock  |
   |                   |                     |<-------------------|
   |                   |<--------------------|                    |
   |   Book Found      |                     |                    |
   |                   |                     |                    |
   |------------------>|                     |                    |
   |   Borrow Book     |                     |                    |
   |                   |-------------------->|                    |
   |                   |   Validate User     |                    |
   |                   |                     |                    |
   |                   |                     |------------------->|
   |                   |                     |   Update Records   |
   |                   |                     |<-------------------|
   |                   |<--------------------|                    |
   |   Borrow Success  |                     |                    |
   |<------------------|                     |                    |
   |   Confirmation    |                     |                    |
```
### Other Symbol
__Conditional:__
```
----------------
| alt |        | 
|------        | 
|              |
|  condition   |
|              |
|---------------
|              |
|   else       |
|              |
|---------------
```
__Loop:__
```
----------------
| loop |       | 
|------        | 
|              |
|  statement   |
|              |
|---------------
```
__Activation Bar__
```
        |
        |
        |
        |
        |
        |
        |
        |
        |
        |
```
__Message:__
```
    ---
    | |
    ---
```
## Activity Diagram
It represents workflows and the sequence of activities. It define what activities user perform during a use case.

Each use case in a use case diagram can be further explored by creating an activity diagram. It's common to create an activity diagram for each use case identified in the use case diagram.

__Components:__
- __Activities:__ Represent tasks or actions performed in the workflow. Each activity is denoted by a rounded rectangle.
- __Start Node:__ Indicates the beginning of a process. It is represented by a filled black circle.
- __End Node:__ Marks the end of the process flow. It is represented by a black circle with a surrounding border.
- __Transitions/Arrows:__ Arrows show the flow or transition from one activity to the next.
- __Decision Node:__ Depicted as a diamond shape, it represents branching in the workflow based on conditions. Each outgoing arrow is labeled with a condition.
- __Merge Node:__ A diamond shape without conditions where multiple flows join back together.
- __Fork Node:__ Represented as a thick horizontal or vertical line, it splits a single flow into multiple parallel flows.
- __Join Node:__ A thick line that synchronizes multiple parallel flows into a single flow.
- __Swimlanes:__ Vertical or horizontal partitions used to organize activities by the responsible actors or departments. This helps in visually associating actions with particular actors.
### Example
```
+-------------------------+   +---------------------+   +---------------------+
|        Start            |-->|   Search Book       |-->| Book Available?     |
+-------------------------+   +---------------------+   +---------+-----------+
                                                     |           |
                                                     |           v
                                                     |   +---------------------+
                                                     |   | Book Not Available  |
                                                     |   | Notify User         |
                                                     |   +---------------------+
                                                     |           |
                                                     |           v
                                                     |   +---------------------+
                                                     |   |  End                |
                                                     |   +---------------------+
                                                     |
                                                     v
+-------------------------+   +---------------------+   +---------------------+
|  Verify Membership      |-->|  Valid Member?      |-->|  Borrow Book        |
+-------------------------+   +---------+-----------+   +---------------------+
                                        |                   
                                        |                   +---------------------+
                                        |                   |  Record Borrowing   |
                                        v                   +---------------------+
                              +---------------------+                   |
                              |  Not a Member       |                   |
                              |  Notify User        |                   v
                              +---------------------+   +---------------------+
                                        |               |  Issue Receipt       |
                                        v               +---------------------+
                                  +------------------+             |
                                  |        End       |<-------------+
                                  +------------------+

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