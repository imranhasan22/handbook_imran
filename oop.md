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
