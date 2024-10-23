# Content
- [Introduction](#introduction)
- [Arduino](#arduino---programming)
# Introduction
A robot is a programmable machine that can carry out tasks autonomously or semi-autonomously. These machines are capable of perceiving their environment, processing information, and executing actions to achieve specific objectives.

## Key Components
Input, processor, output, memory, power supply are the hardware part of the robots, programming is called software.
### 1.`Input(Sensors)`
It gather real-time data from the environment to make informed decisions and take actions.

- Vision sensors (cameras, infrared)
- Proximity sensors (to detect nearby objects)
- Gyroscopes and accelerometers (for orientation and movement)
- Touch sensors (detect physical interaction)
- Microphones (for sound recognition)
### 2.`Processor(Microcontroller)`
It processes the sensor data, runs algorithms, and sends commands to actuators to execute appropriate actions. It is a cheap or specialized circuit which is used for making decision. This is handled by a control system (microcontroller, processor, or compute).

- `Microcontroller`: A compact integrated circuit designed to manage the operations of a robot. Examples include Arduino, STM32.
- `Microprocessor`: A more powerful processing unit like a Raspberry Pi or NVIDIA Jetson, used for robots that need more computing power for complex tasks like AI-based navigation or object recognition.
### 3.`Output (Actuators)`
It execute physical actions like moving, picking up objects, or even communicating with humans based on the decisions made by the control system.

- __Motors__: Electric motors that convert electrical signals into mechanical movement.
    - __DC motors__ for general motion control (e.g., driving wheels).
    - __Servo motors__ for precise angular control (e.g., in robotic arms).
    - __Stepper motors__ for controlled, incremental movements.
- __End Effectors__: Tools at the end of robotic arms, like grippers, welders, or cutting tools, that allow the robot to interact with objects in the environment.
- __Displays/Sound Output__: Some robots also output information to screens, lights, or speakers to communicate with humans.
### 4.`Memory`
It enables the robot to remember and store critical data, ensuring the robot can function efficiently by recalling programs and sensor information when needed.

### 5.`Power Supply`
Robots need energy to operate, which can come from batteries, solar power, electrical grids, or other sources.

### 6.`Programming(Software)`
It defines the logic of the robot’s behavior, allowing it to understand sensor data, process it, and perform actions.

# Arduino - Programming
## Sketch
Every sketch (which is what Arduino programs are called) has two essential functions: setup() and loop(). These functions define the structure of the program and how it operates.


### `setup()`
The `setup()` function is called once when your Arduino board is powered on or reset. It is used to initialize variables, pin modes, libraries, and other components that your program will use.

__Syntax:__
```
void setup() {
  // Initialization code here
}
```
### `loop()`
The `loop()` function is the heart of an Arduino sketch. After the setup() function runs once, the `loop()` function runs continuously in a loop, allowing your program to repeat certain actions indefinitely.

__Syntax:__
```
void loop() {
  // Code that runs repeatedly
}
```
## Structure
Every Arduino sketch must contain these two functions, even if they are empty. Here's how the basic structure looks:
```
void setup() {
  // Code that runs once goes here
}

void loop() {
  // Code that runs repeatedly goes here
}
```
### Example
Let's consider an example where an LED is connected to pin 13 of the Arduino, and we want it to blink on and off every second.
```cpp
// Define the pin number for the LED
const int ledPin = 13;

void setup() {
  // Initialize the digital pin as an output.
  pinMode(ledPin, OUTPUT);
}

void loop() {
  // Turn the LED on (HIGH is the voltage level)
  digitalWrite(ledPin, HIGH);
  // Wait for a second
  delay(1000);
  // Turn the LED off by making the voltage LOW
  digitalWrite(ledPin, LOW);
  // Wait for a second
  delay(1000);
}
```
