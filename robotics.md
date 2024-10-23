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
## Variable Declaration & Data Type
__Common Data Types:__
- `int` 
- `unsigned int`
- `long`
- `unsigned long`
- `float`
- `char`
- `boolean`
- `byte`
- `string`

__Variable Declaration Synatx:__
```
dataType variableName = initialValue;
```

__Example:__
```cpp
int sensorValue = 0;
float pi = 3.14;
char grade = 'A';
boolean isOn = true;
```
## Constant
### Predefined Constants
Arduino provides some built-in constants that have predefined values. Examples include:
- `HIGH` (1): Represents a high voltage (on).
- `LOW` (0): Represents a low voltage (off).
- `INPUT`, `OUTPUT`, and `INPUT_PULLUP`: Used for setting pin modes.

__Example:__
```cpp
pinMode(ledPin, OUTPUT);  // Set ledPin as an output
```
### `const` Keyword
Declares a variable as a constant, meaning its value cannot be changed once it’s assigned.

__Syntax:__
```
const dataType variableName = value;
```
### `#define` Preprocessor Directive
Defines a symbolic constant that is replaced by its value during the program's preprocessing step.

__Syntax:__
```
#define constantName value
```
## String
There are two main types of strings in Arduino:
- Character arrays (C-style strings).
- String objects (from the `String` class).
### Character Arrays
A character array is an array of characters terminated by a null character (`\0`). It is a C-style string.

__Declaring a Character Array:__
```cpp
char myString[] = "Hello, World!";
```
This is equivalent to:
```cpp
char myString[] = {'H', 'e', 'l', 'l', 'o', ',', ' ', 'W', 'o', 'r', 'l', 'd', '!', '\0'};
```
You can manipulate character arrays using functions from the C library (`string.h`), such as `strlen()`, `strcpy()`, and `strcat()`.
### String Class
__Declaring a String Object:__
```cpp
String myString = "Hello, Arduino!";
```
## Common Methods

### 1. Basic Functions

| **Function**               | **Usage**                                                                                         |
|----------------------------|---------------------------------------------------------------------------------------------------|
| `setup()`                  | Called once when the Arduino starts. Used to initialize variables, pin modes, libraries, etc.      |
| `loop()`                   | Called repeatedly after `setup()`. Contains the main logic of the program.                        |
| `pinMode(pin, mode)`       | Sets the mode of a pin (e.g., INPUT, OUTPUT).                                                     |
| `digitalWrite(pin, value)` | Sets a digital pin to HIGH or LOW (ON/OFF).                                                      |
| `digitalRead(pin)`         | Reads the value from a digital pin (HIGH or LOW).                                                 |
| `analogWrite(pin, value)`  | Writes an analog value (PWM) to a pin. Values range from 0 to 255.                              |
| `analogRead(pin)`          | Reads the value from an analog pin (range: 0-1023).                                               |
| `delay(ms)`                | Pauses the program for a specified number of milliseconds.                                        |
| `millis()`                 | Returns the number of milliseconds since the program started running.                             |

---

### 2. Mathematical Functions

| **Function**               | **Usage**                                                                                         |
|----------------------------|---------------------------------------------------------------------------------------------------|
| `min(x, y)`                | Returns the smaller of two numbers.                                                               |
| `max(x, y)`                | Returns the larger of two numbers.                                                                |
| `abs(x)`                   | Returns the absolute value of a number.                                                           |
| `pow(base, exponent)`      | Returns the result of raising `base` to `exponent`.                                               |
| `sqrt(x)`                  | Returns the square root of a number.                                                              |
| `map(value, fromLow, fromHigh, toLow, toHigh)` | Maps a number from one range to another.                                   |
| `constrain(x, a, b)`       | Constrains a value to lie between two limits (a and b).                                           |
| `random(max)`              | Returns a random number between 0 and the specified maximum.                                      |
| `random(min, max)`         | Returns a random number between the specified minimum and maximum.                                |
| `randomSeed(seed)`         | Initializes the random number generator with a seed value.                                        |

---

### 3. Timing Functions

| **Function**               | **Usage**                                                                                         |
|----------------------------|---------------------------------------------------------------------------------------------------|
| `delay(ms)`                | Pauses the program for a specified number of milliseconds.                                        |
| `millis()`                 | Returns the number of milliseconds since the program started running.                             |
| `micros()`                 | Returns the number of microseconds since the program started.                                     |
| `delayMicroseconds(us)`    | Pauses the program for a specified number of microseconds.                                        |

---

### 4. Serial Communication

| **Function**                | **Usage**                                                                                       |
|-----------------------------|-------------------------------------------------------------------------------------------------|
| `Serial.begin(baudrate)`    | Initializes serial communication with the specified baud rate (e.g., 9600).                     |
| `Serial.print(data)`         | Sends data to the serial port (without a newline).                                              |
| `Serial.println(data)`       | Sends data to the serial port (with a newline at the end).                                      |
| `Serial.read()`              | Reads incoming data from the serial buffer.                                                    |
| `Serial.available()`         | Returns the number of bytes available in the serial buffer.                                     |
| `Serial.flush()`             | Waits for outgoing serial data to be transmitted.                                              |
| `Serial.end()`               | Disables serial communication.                                                                 |

---

### 5. Analog I/O

| **Function**                | **Usage**                                                                                      |
|-----------------------------|------------------------------------------------------------------------------------------------|
| `analogRead(pin)`           | Reads the value from an analog pin (range: 0-1023).                                            |
| `analogWrite(pin, value)`   | Writes a PWM signal to an analog pin (range: 0-255).                                           |

---

### 6. Digital I/O

| **Function**               | **Usage**                                                                                      |
|----------------------------|------------------------------------------------------------------------------------------------|
| `pinMode(pin, mode)`       | Configures a digital pin to be either an INPUT or OUTPUT.                                       |
| `digitalWrite(pin, value)` | Sets a digital pin to HIGH or LOW.                                                             |
| `digitalRead(pin)`         | Reads the value from a digital pin (HIGH or LOW).                                              |

---

### 7. Interrupt Functions

| **Function**               | **Usage**                                                                                     |
|----------------------------|-----------------------------------------------------------------------------------------------|
| `attachInterrupt(pin, ISR, mode)` | Attaches an interrupt to a pin. The ISR is a function that runs when the interrupt occurs. |
| `detachInterrupt(pin)`      | Disables the interrupt for a specified pin.                                                   |
| `noInterrupts()`            | Disables all interrupts.                                                                      |
| `interrupts()`              | Re-enables interrupts after they have been disabled.                                          |

---

### 8. Bitwise Operations

| **Function**               | **Usage**                                                                                              |
|----------------------------|-------------------------------------------------------------------------------------------------------|
| `bitRead(value, bit)`      | Reads a bit from a value.                                                                            |
| `bitWrite(value, bit, bitValue)` | Writes a bit to a value.                                                                   |
| `bitSet(value, bit)`       | Sets a bit to 1 in a value.                                                                          |
| `bitClear(value, bit)`     | Clears a bit to 0 in a value.                                                                        |
| `bit(bitNumber)`           | Returns the value of a given bit number (e.g., bit(3) returns 0b1000 or 8).                         |

---

### 9. Other Common Functions

| **Function**               | **Usage**                                                                                         |
|----------------------------|---------------------------------------------------------------------------------------------------|
| `isnan(x)`                 | Returns `true` if the argument is NaN (Not a Number).                                             |
| `isinf(x)`                 | Returns `true` if the argument is infinity.                                                       |
| `lowByte(x)`               | Returns the low byte of an integer.                                                               |
| `highByte(x)`              | Returns the high byte of an integer.                                                              |
| `shiftOut(dataPin, clockPin, bitOrder, value)` | Shifts out a byte of data one bit at a time.                                |

---

### 10. Library-Related Methods

| **Function**               | **Usage**                                                                                           |
|----------------------------|-----------------------------------------------------------------------------------------------------|
| `#include <library.h>`     | Includes a library in your sketch.                                                                  |
| `libraryObject.begin()`    | Initializes the library, usually in the `setup()` function.                                         |
| `libraryObject.read()`     | Reads data from the hardware component controlled by the library.                                  |
| `libraryObject.write(data)`| Sends data to the hardware component controlled by the library.                                    |