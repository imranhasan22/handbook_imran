# Content

- [Introduction](#introduction)
- [Development Boards](#development-boards)
  - [ESP 32 Board](#esp-32-board)
- [Arduino Programming](#arduino---programming)
- [Components](#components)
  - [Breadboard](#breadboard)
  - [Buzzer](#buzzer)
  - [Ultrasonic Sonar Sensor](#ultrasonic-sonar-sensor)
  - [Infrared Sensor](#infrared-sensor)

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

- **Motors**: Electric motors that convert electrical signals into mechanical movement.
  - **DC motors** for general motion control (e.g., driving wheels).
  - **Servo motors** for precise angular control (e.g., in robotic arms).
  - **Stepper motors** for controlled, incremental movements.
- **End Effectors**: Tools at the end of robotic arms, like grippers, welders, or cutting tools, that allow the robot to interact with objects in the environment.
- **Displays/Sound Output**: Some robots also output information to screens, lights, or speakers to communicate with humans.

### 4.`Memory`

It enables the robot to remember and store critical data, ensuring the robot can function efficiently by recalling programs and sensor information when needed.

### 5.`Power Supply`

Robots need energy to operate, which can come from batteries, solar power, electrical grids, or other sources.

### 6.`Programming(Software)`

It defines the logic of the robot’s behavior, allowing it to understand sensor data, process it, and perform actions.

# Development Boards

A development board in robotics is a small, single-board computer or microcontroller board used to control and interact with sensors, actuators, and other electronic components in robotic systems. These boards are essential for prototyping and development in robotics, as they allow for programming, testing, and integration of various robotic functions. They come with input/output (I/O) pins, communication interfaces, and often support additional modules, making them versatile and widely used in both educational and professional robotics projects.

## Key Features of Development Boards for Robotics

1. **Microcontroller or Processor**: The board's "brain" that executes code and processes data. Microcontrollers (like the ATmega on Arduino boards) and microprocessors (like the ARM Cortex on Raspberry Pi boards) are common choices.
2. **I/O Pins**: These pins enable the board to interact with external components such as sensors, motors, LEDs, and displays. Pins can be digital (for on/off signals) or analog (for variable signals).
3. **Power Supply Options**: Development boards are often designed to work with various power sources (battery, USB, or adapter) to meet different project needs.
4. **Communication Interfaces**: Interfaces like I2C, SPI, UART, Bluetooth, and Wi-Fi allow communication between the board and other components, as well as with external devices like computers or smartphones.
5. **Programming Interface**: Most boards have a USB or other port for programming and debugging. They are compatible with IDEs (Integrated Development Environments) that allow users to write and upload code.

## Examples of Development Boards

### 1. **Arduino Uno**

- **Description**: The Arduino Uno is one of the most popular microcontroller-based development boards, especially suited for beginners. It uses the ATmega328P microcontroller, which is an 8-bit microcontroller with 32 KB of flash memory for storing code.
- **Key Features**:
  - 14 digital I/O pins and 6 analog inputs.
  - Operates at 5V, making it compatible with many sensors and actuators.
  - Simple programming via the Arduino IDE.
- **Example Project**: **Line-Following Robot**
  - **Explanation**: In a line-following robot project, the Arduino Uno controls the motors and processes signals from infrared (IR) sensors. The IR sensors detect the contrast between a black line and a white surface. Based on this data, the Arduino adjusts motor speed and direction to keep the robot on track.

### 2. **ESP32**

- **Description**: The ESP32 is a microcontroller board with built-in Wi-Fi and Bluetooth capabilities. It’s well-suited for IoT (Internet of Things) applications in robotics where remote control or data logging is required.
- **Key Features**:
  - Dual-core processor and multiple GPIO pins.
  - Supports low-power operation, making it suitable for battery-powered projects.
  - Built-in Wi-Fi and Bluetooth for easy network connectivity.
- **Example Project**: **Remote-Controlled Car**
  - **Explanation**: With the ESP32, you can create a small car that can be controlled remotely over Wi-Fi. By setting up a server on the ESP32, commands can be sent from a smartphone or computer to control the car’s movement. This can be extended to include additional functionalities like sending sensor data back to the user.

### 3. **Raspberry Pi 4**

- **Description**: The Raspberry Pi 4 is a small, powerful single-board computer with a microprocessor, making it capable of running an operating system like Linux. It’s ideal for complex robotics projects that require high computing power.
- **Key Features**:
  - Multiple USB ports, GPIO pins, HDMI output, and camera interface.
  - Capable of handling more complex tasks like image processing, making it suitable for machine learning applications.
  - Can connect to the internet via Ethernet or Wi-Fi.
- **Example Project**: **Obstacle-Avoiding Robot with Vision**
  - **Explanation**: The Raspberry Pi 4 can be used to control a robot that avoids obstacles using camera input. By processing images from a camera feed, the Raspberry Pi can use machine learning algorithms (such as object detection) to identify obstacles. It can then adjust motor controls to navigate around obstacles.

## Choosing the Right Development Board

The choice of board depends on the project requirements:

- **Simple projects** (like controlling LEDs or making simple sensors interact) are well-suited to boards like the **Arduino Uno**.
- **IoT-based robotics projects** where **connectivity** is essential benefit from using boards like the **ESP32**.
- **Complex projects** requiring higher computation power, such as **image processing or machine learning tasks**, are more appropriate for the **Raspberry Pi**.

## Microprocessor vs Microcontroller

| **Feature**                   | **Microprocessor**                                                               | **Microcontroller**                                                            |
| ----------------------------- | -------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| **Architecture**              | CPU only; requires external memory, I/O, and peripherals                         | Integrated CPU, memory (RAM, ROM, Flash), I/O peripherals                      |
| **Primary Function**          | General-purpose processing; suited for complex computations                      | Dedicated control-oriented tasks; designed for specific embedded applications  |
| **Components**                | Lacks built-in memory and I/O; needs external components                         | Built-in memory (RAM/ROM), timers, ADC, and GPIO pins                          |
| **Processing Power**          | High processing power; capable of handling complex tasks                         | Moderate processing power; optimized for real-time control                     |
| **Power Consumption**         | Higher power consumption due to complex operations                               | Low power consumption, suitable for battery-operated devices                   |
| **Cost**                      | Generally more expensive due to higher complexity                                | Lower cost, as it integrates all components on a single chip                   |
| **Ease of Development**       | Requires additional components and a more complex setup                          | Easier to develop with, often simpler setup and programming                    |
| **Performance**               | High-performance, suitable for multitasking and complex algorithms               | Moderate performance, ideal for handling simple, dedicated tasks               |
| **Applications in Robotics**  | Used in advanced robotics for tasks like image processing, AI, and path planning | Used for motor control, sensor reading, and actuator control in simpler robots |
| **Examples**                  | Intel i5, AMD Ryzen, ARM Cortex-A series                                         | Arduino (ATmega328), STM32, PIC series, ARM Cortex-M series                    |
| **Programming Complexity**    | More complex; often requires operating systems (e.g., Linux)                     | Simple, often programmed using bare-metal or RTOS                              |
| **External Support Required** | Requires additional chips for I/O, memory, etc.                                  | Self-contained; minimal external components needed                             |
| **Size and Form Factor**      | Larger size, typically in SoC or computer boards                                 | Small, compact size; available in various form factors                         |
| **Examples in Robotics**      | NVIDIA Jetson for autonomous robots, Raspberry Pi for AI tasks                   | Arduino for simple robots, ARM Cortex-M for robotic arms                       |
| **Memory Architecture**       | Uses separate external RAM and ROM                                               | On-chip memory (usually a mix of RAM, ROM, and Flash)                          |
| **Typical Clock Speed**       | Higher clock speeds, often >1 GHz                                                | Lower clock speeds, usually in the range of MHz                                |
| **Data Processing**           | Suitable for processing large datasets, running AI models                        | Limited to smaller, control-oriented data processing                           |

# ESP 32 Board

## Power and Control Pins

| **Board Label** | **ESP32 Function** | **Description**                                           |
| --------------- | ------------------ | --------------------------------------------------------- |
| **EN**          | EN                 | Enable pin. Active HIGH. Used to reset the chip.          |
| **BOOT**        | GPIO0              | Boot mode selection pin. Pull LOW to enter flashing mode. |

## Pin Labels and GPIO Mapping

| **Board Label** | **ESP32 GPIO Number** | **Description**                                |
| --------------- | --------------------- | ---------------------------------------------- |
| **3U3**         | ---                   | 3.3V power output (regulated onboard).         |
| **GND**         | ---                   | Ground pin. Common reference for the circuit.  |
| **D15**         | GPIO15                | General-purpose I/O, ADC2 channel 3, touch T3. |
| **D2**          | GPIO2                 | General-purpose I/O, ADC2 channel 2, touch T2. |
| **D4**          | GPIO4                 | General-purpose I/O, ADC2 channel 0, touch T0. |
| **RX2**         | GPIO16                | UART2 RX pin.                                  |
| **TX2**         | GPIO17                | UART2 TX pin.                                  |
| **D5**          | GPIO5                 | General-purpose I/O, HSPI_CS.                  |
| **D18**         | GPIO18                | General-purpose I/O, SPI_CLK, PWM.             |
| **D19**         | GPIO19                | General-purpose I/O, SPI_MISO, PWM.            |
| **D21**         | GPIO21                | I2C SDA, general-purpose I/O.                  |
| **RX0**         | GPIO3                 | UART0 RX pin (used for programming).           |
| **TX0**         | GPIO1                 | UART0 TX pin (used for programming).           |
| **D22**         | GPIO22                | I2C SCL, general-purpose I/O.                  |
| **D23**         | GPIO23                | SPI_MOSI, general-purpose I/O.                 |

| **Board Label** | **ESP32 GPIO Number** | **Description**                                |
| --------------- | --------------------- | ---------------------------------------------- |
| **VIN**         | ---                   | Input power pin (typically 5V).                |
| **GND**         | ---                   | Ground pin. Common reference for the circuit.  |
| **D13**         | GPIO13                | General-purpose I/O, ADC2 channel 4, touch T4. |
| **D12**         | GPIO12                | General-purpose I/O, ADC2 channel 5, touch T5. |
| **D14**         | GPIO14                | General-purpose I/O, ADC2 channel 6, touch T6. |
| **D27**         | GPIO27                | General-purpose I/O, ADC2 channel 7, touch T7. |
| **D26**         | GPIO26                | General-purpose I/O, DAC2, ADC2 channel 9.     |
| **D25**         | GPIO25                | General-purpose I/O, DAC1, ADC2 channel 8.     |
| **D33**         | GPIO33                | General-purpose I/O, ADC1 channel 5, touch T8. |
| **D32**         | GPIO32                | General-purpose I/O, ADC1 channel 4, touch T9. |
| **D35**         | GPIO35                | Input-only GPIO, ADC1 channel 7.               |
| **D34**         | GPIO34                | Input-only GPIO, ADC1 channel 6.               |
| **UN**          | GPIO39 (VN)           | Input-only GPIO, ADC1 channel 3.               |
| **UP**          | GPIO36 (VP)           | Input-only GPIO, ADC1 channel 0.               |
| **EN**          | EN                    | Chip enable pin. Active HIGH.                  |

## Description

### Power and Ground Pins

#### VIN

Input pin to supply power to the ESP32. Typically connected to a 5V source. Connect VIN with positive(+) voltage of the battery.

#### GND

Common reference point for all circuits. Always connect to the ground of external devices. Connect GND with negative(-) voltage of any external devices including battery and sensors.

#### 3U3

Provides a 3.3V output from the onboard voltage regulator. Can be used to power low-power sensors or modules. It provides positive(+) voltage.

# Arduino - Programming

## Sketch

Every sketch (which is what Arduino programs are called) has two essential functions: setup() and loop(). These functions define the structure of the program and how it operates.

### `setup()`

The `setup()` function is called once when your Arduino board is powered on or reset. It is used to initialize variables, pin modes, libraries, and other components that your program will use.

**Syntax:**

```cpp
void setup() {
  // Initialization code here
}
```

### `loop()`

The `loop()` function is the heart of an Arduino sketch. After the setup() function runs once, the `loop()` function runs continuously in a loop, allowing your program to repeat certain actions indefinitely.

**Syntax:**

```cpp
void loop() {
  // Code that runs repeatedly
}
```

## Structure

Every Arduino sketch must contain these two functions, even if they are empty. Here's how the basic structure looks:

```cpp
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

**Common Data Types:**

- `int`
- `unsigned int`
- `long`
- `unsigned long`
- `float`
- `char`
- `boolean`
- `byte`
- `string`

**Variable Declaration Synatx:**

```
dataType variableName = initialValue;
```

**Example:**

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

**Example:**

```cpp
pinMode(ledPin, OUTPUT);  // Set ledPin as an output
```

### `const` Keyword

Declares a variable as a constant, meaning its value cannot be changed once it’s assigned.

**Syntax:**

```
const dataType variableName = value;
```

### `#define` Preprocessor Directive

Defines a symbolic constant that is replaced by its value during the program's preprocessing step.

**Syntax:**

```
#define constantName value
```

## String

There are two main types of strings in Arduino:

- Character arrays (C-style strings).
- String objects (from the `String` class).

### Character Arrays

A character array is an array of characters terminated by a null character (`\0`). It is a C-style string.

**Declaring a Character Array:**

```cpp
char myString[] = "Hello, World!";
```

This is equivalent to:

```cpp
char myString[] = {'H', 'e', 'l', 'l', 'o', ',', ' ', 'W', 'o', 'r', 'l', 'd', '!', '\0'};
```

You can manipulate character arrays using functions from the C library (`string.h`), such as `strlen()`, `strcpy()`, and `strcat()`.

### String Class

**Declaring a String Object:**

```cpp
String myString = "Hello, Arduino!";
```

## Common Methods

### 1. Basic Functions

| **Function**               | **Usage**                                                                                     |
| -------------------------- | --------------------------------------------------------------------------------------------- |
| `setup()`                  | Called once when the Arduino starts. Used to initialize variables, pin modes, libraries, etc. |
| `loop()`                   | Called repeatedly after `setup()`. Contains the main logic of the program.                    |
| `pinMode(pin, mode)`       | Sets the mode of a pin (e.g., INPUT, OUTPUT).                                                 |
| `digitalWrite(pin, value)` | Sets a digital pin to HIGH or LOW (ON/OFF).                                                   |
| `digitalRead(pin)`         | Reads the value from a digital pin (HIGH or LOW).                                             |
| `analogWrite(pin, value)`  | Writes an analog value (PWM) to a pin. Values range from 0 to 255.                            |
| `analogRead(pin)`          | Reads the value from an analog pin (range: 0-1023).                                           |
| `delay(ms)`                | Pauses the program for a specified number of milliseconds.                                    |
| `millis()`                 | Returns the number of milliseconds since the program started running.                         |

---

### 2. Mathematical Functions

| **Function**                                   | **Usage**                                                          |
| ---------------------------------------------- | ------------------------------------------------------------------ |
| `min(x, y)`                                    | Returns the smaller of two numbers.                                |
| `max(x, y)`                                    | Returns the larger of two numbers.                                 |
| `abs(x)`                                       | Returns the absolute value of a number.                            |
| `pow(base, exponent)`                          | Returns the result of raising `base` to `exponent`.                |
| `sqrt(x)`                                      | Returns the square root of a number.                               |
| `map(value, fromLow, fromHigh, toLow, toHigh)` | Maps a number from one range to another.                           |
| `constrain(x, a, b)`                           | Constrains a value to lie between two limits (a and b).            |
| `random(max)`                                  | Returns a random number between 0 and the specified maximum.       |
| `random(min, max)`                             | Returns a random number between the specified minimum and maximum. |
| `randomSeed(seed)`                             | Initializes the random number generator with a seed value.         |

---

### 3. Timing Functions

| **Function**            | **Usage**                                                             |
| ----------------------- | --------------------------------------------------------------------- |
| `delay(ms)`             | Pauses the program for a specified number of milliseconds.            |
| `millis()`              | Returns the number of milliseconds since the program started running. |
| `micros()`              | Returns the number of microseconds since the program started.         |
| `delayMicroseconds(us)` | Pauses the program for a specified number of microseconds.            |

---

### 4. Serial Communication

| **Function**             | **Usage**                                                                   |
| ------------------------ | --------------------------------------------------------------------------- |
| `Serial.begin(baudrate)` | Initializes serial communication with the specified baud rate (e.g., 9600). |
| `Serial.print(data)`     | Sends data to the serial port (without a newline).                          |
| `Serial.println(data)`   | Sends data to the serial port (with a newline at the end).                  |
| `Serial.read()`          | Reads incoming data from the serial buffer.                                 |
| `Serial.available()`     | Returns the number of bytes available in the serial buffer.                 |
| `Serial.flush()`         | Waits for outgoing serial data to be transmitted.                           |
| `Serial.end()`           | Disables serial communication.                                              |

---

### 5. Analog I/O

| **Function**              | **Usage**                                            |
| ------------------------- | ---------------------------------------------------- |
| `analogRead(pin)`         | Reads the value from an analog pin (range: 0-1023).  |
| `analogWrite(pin, value)` | Writes a PWM signal to an analog pin (range: 0-255). |

---

### 6. Digital I/O

| **Function**               | **Usage**                                                 |
| -------------------------- | --------------------------------------------------------- |
| `pinMode(pin, mode)`       | Configures a digital pin to be either an INPUT or OUTPUT. |
| `digitalWrite(pin, value)` | Sets a digital pin to HIGH or LOW.                        |
| `digitalRead(pin)`         | Reads the value from a digital pin (HIGH or LOW).         |

---

### 7. Interrupt Functions

| **Function**                      | **Usage**                                                                                  |
| --------------------------------- | ------------------------------------------------------------------------------------------ |
| `attachInterrupt(pin, ISR, mode)` | Attaches an interrupt to a pin. The ISR is a function that runs when the interrupt occurs. |
| `detachInterrupt(pin)`            | Disables the interrupt for a specified pin.                                                |
| `noInterrupts()`                  | Disables all interrupts.                                                                   |
| `interrupts()`                    | Re-enables interrupts after they have been disabled.                                       |

---

### 8. Bitwise Operations

| **Function**                     | **Usage**                                                                   |
| -------------------------------- | --------------------------------------------------------------------------- |
| `bitRead(value, bit)`            | Reads a bit from a value.                                                   |
| `bitWrite(value, bit, bitValue)` | Writes a bit to a value.                                                    |
| `bitSet(value, bit)`             | Sets a bit to 1 in a value.                                                 |
| `bitClear(value, bit)`           | Clears a bit to 0 in a value.                                               |
| `bit(bitNumber)`                 | Returns the value of a given bit number (e.g., bit(3) returns 0b1000 or 8). |

---

### 9. Other Common Functions

| **Function**                                   | **Usage**                                             |
| ---------------------------------------------- | ----------------------------------------------------- |
| `isnan(x)`                                     | Returns `true` if the argument is NaN (Not a Number). |
| `isinf(x)`                                     | Returns `true` if the argument is infinity.           |
| `lowByte(x)`                                   | Returns the low byte of an integer.                   |
| `highByte(x)`                                  | Returns the high byte of an integer.                  |
| `shiftOut(dataPin, clockPin, bitOrder, value)` | Shifts out a byte of data one bit at a time.          |

---

### 10. Library-Related Methods

| **Function**                | **Usage**                                                         |
| --------------------------- | ----------------------------------------------------------------- |
| `#include <library.h>`      | Includes a library in your sketch.                                |
| `libraryObject.begin()`     | Initializes the library, usually in the `setup()` function.       |
| `libraryObject.read()`      | Reads data from the hardware component controlled by the library. |
| `libraryObject.write(data)` | Sends data to the hardware component controlled by the library.   |

# Components

## Breadboard

The breadboard is a white rectangular board with small embedded holes to insert electronic components.

### Layout

### Power Rails

Along the top and bottom edges, there are two long rows. These are typically used to distribute power and are labeled `+` for positive voltage and `-` for ground. Each rail is isolated and can provide different voltages for various parts of the circuit. They are connected `horizontally`.

It means a single horizontal line of a breadboard has the same connection. It is because the metal strip underneath the breadboard at the top and bottom are connected horizontally. Hence, it provides the same connection in a row. The two top and bottom parts of a breadboard are generally used for power connections.

### Terminal Strips

**Arrangement:** Terminal strips are the main area where electronic components are inserted. Each column has a series of holes aligned `vertically`, and each row is grouped into 5-hole blocks.

The vertical connection of the center part means a single vertical line in a breadboard provides the same connection. It is useful when we need to connect the different components in series.

**Electrical Connection:** In each 5-hole block, all five holes are electrically connected in a row (or column), allowing multiple component leads to be connected together. For example, if you insert the legs of an LED into one of these blocks, the current can flow through the connected path.

**Central Divider/Gap:** The terminal strips are divided by a central channel that runs lengthwise. This gap is specifically designed to accommodate ICs. When you place an IC in this central gap, each pin on one side of the IC is isolated from the pins on the other side, making it easier to connect other components to individual pins.

## Buzzer

A buzzer is a simple component used to produce sound. Buzzers can be either active or passive:

- **Active Buzzer**: Emits a constant tone when powered. Requires only HIGH/LOW signals.
- **Passive Buzzer**: Needs a PWM (Pulse Width Modulation) signal to produce varying tones.

Active Buzzer is used for alarm, simple feedback (button presses). Passive Buzzer is used for playing melodies, generating dynamic alerts or tones.

### Hardware Setup

- Connect the positive terminal (VCC) of the buzzer to a GPIO pin (e.g., GPIO23).
- Connect the negative terminal (GND) of the buzzer to the GND pin on the ESP32.

### Controlling

**Active Buzzer:** With an active buzzer, you only need to send a HIGH signal to make it beep.

```cpp
digitalWrite(buzzerPin, HIGH/LOW); // Turn ON/OFF buzzer
```

**Passive Buzzer:** For a passive buzzer, you use PWM signals to generate tones.

```cpp
tone(buzzerPin, 1000); // Play 1kHz tone
...
noTone(buzzerPin);
```

## Ultrasonic Sonar Sensor

Sonar sensors, like the HC-SR04, are used for distance measurement by emitting ultrasonic waves and measuring their echo.

### Structure

The HC-SR04 sensor has four pins:

- **VCC**: Power supply (5V).
- **GND**: Ground.
- **TRIG**: Trigger pin (to send ultrasonic signals).
- **ECHO**: Echo pin (to receive the reflected signal).

### Hardware Setup

- Connect VCC to the ESP32's VIN (5V).
- Connect GND to the ESP32's GND.
- Connect the TRIG pin to a GPIO pin (e.g., GPIO5).
- Connect the ECHO pin to another GPIO pin (e.g., GPIO18).

### Controlling

```cpp
#define TRIG_PIN 5   // GPIO5 connected to TRIG
#define ECHO_PIN 18  // GPIO18 connected to ECHO

void setup() {
    Serial.begin(115200);             // Start Serial communication
    pinMode(TRIG_PIN, OUTPUT);        // Set TRIG as OUTPUT
    pinMode(ECHO_PIN, INPUT);         // Set ECHO as INPUT
}

void loop() {
    // Send a HIGH pulse for 10 µs to the TRIG pin
    digitalWrite(TRIG_PIN, LOW);
    delayMicroseconds(2);
    digitalWrite(TRIG_PIN, HIGH);
    delayMicroseconds(10);
    digitalWrite(TRIG_PIN, LOW);

    // Measure the duration of the ECHO pin HIGH
    long duration = pulseIn(ECHO_PIN, HIGH);

    // Calculate the distance in cm (duration / 2) * 0.034
    float distance = (duration / 2.0) * 0.034;

    // Print the distance
    Serial.print("Distance: ");
    Serial.print(distance);
    Serial.println(" cm");

    delay(500); // Delay before the next measurement
}
```

### How It Works

1. The ESP32 sends a HIGH pulse (`10 µs`) to the TRIG pin to emit ultrasonic waves.
2. The sensor emits a sound wave at `40 kHz`.
3. The wave hits an object and reflects back.
4. The sensor sets the ECHO pin HIGH for the time it takes the wave to return.
5. The ESP32 calculates the distance based on the time the ECHO pin stays HIGH.

### Applications

- **Obstacle Detection**: Robots or vehicles can use sonar sensors to avoid collisions.
- **Level Monitoring**: Measure water or material levels in a container.
- **Automation**: Trigger actions (e.g., opening doors) based on proximity.

## Infrared Sensor

Infrared (IR) sensors are widely used for object detection, proximity sensing, and remote control systems. They work by emitting infrared light and detecting the reflected signal or decoding signals from IR remotes.

### Types of IR Sensors

- \*_IR Proximity Sensor_: Used for detecting nearby objects. Emits IR light and detects the reflected light.
- \*_IR Receiver Module (e.g., TSOP1738)_: Decodes IR signals from a remote control.
- \*_IR Transmitter and Receiver Pair_: Used in line-following robots or simple communication.

### Structure

An IR proximity sensor typically has 3 pins:

- **VCC**: Power supply (3.3V or 5V).
- **GND**: Ground.
- **OUT**: Output pin (digital HIGH/LOW signal).

### Hardware Setup

- Connect VCC to the ESP32's 3.3V (or 5V if supported by the sensor).
- Connect GND to the ESP32's GND.
- Connect the OUT pin to a GPIO pin (e.g., GPIO23).

### Controlling

```cpp
#define IR_PIN 23 // GPIO23 connected to the OUT pin of the IR sensor

void setup() {
    Serial.begin(115200);    // Start Serial communication
    pinMode(IR_PIN, INPUT);  // Set IR_PIN as INPUT
}

void loop() {
    int irValue = digitalRead(IR_PIN); // Read the sensor value

    if (irValue == LOW) { // Object detected
        Serial.println("Object Detected!");
    } else {
        Serial.println("No Object");
    }

    delay(100); // Small delay to reduce Serial output clutter
}
```

### Applications

- **Object Detection**: Detect nearby objects using IR proximity sensors like automatic door opening systems.
- **Line-Following Robots**: Use an IR pair to follow a line or detect edges.
- **Remote Control**: Use an IR receiver to decode and respond to remote control signals.
- **Communication**: Simple data transmission using an IR transmitter and receiver.
