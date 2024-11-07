# Content

- [Basic](#basic)
- [JSON](#json)
- [Standard PHP Library](#standard-php-library)

# Basic

**PHP Tags:** PHP code is embedded within HTML using special tags. PHP code starts with `<?php` and ends with `?>`.

**Variables:** Variables in PHP start with a dollar sign (`$`) followed by the variable name.

**Echo and Print:** `echo` and `print` are used to output data. Both can display text or variables, though `echo` is slightly faster and allows multiple parameters.

**`foreach` Loop**
The `foreach` loop is designed specifically for iterating over arrays. It goes through each element of an array, making it particularly useful for associative arrays.

```php
$fruits = ["apple", "banana", "cherry"];

foreach ($fruits as $fruit) {
    echo "Fruit: $fruit\n";
}
```

```php
$person = ["name" => "John", "age" => 30, "city" => "New York"];

foreach ($person as $key => $value) {
    echo "$key: $value\n";
}
```

**Pass by Reference:** pass arguments by reference using the `&` symbol, so changes made to the parameter inside the function affect the original variable.

```php
function addFive(&$num) {
    $num += 5;
}

$number = 10;
addFive($number); // Pass $number by reference
echo "New value: $number";
```

## Constants

define constants using either the `define()` function or the `const` keyword.

```php
define("CONSTANT_NAME", value, case_insensitivity);
const PI = 3.14159;
```

### Magic Constants

PHP also has magic constants that provide information about the file, line number, and other context-specific details. These constants change based on where they are used within the code.

Some commonly used magic constants include:

1. `__LINE__`: The current line number in the file.
2. `__FILE__`: The full path and filename of the file.
3. `__DIR__`: The directory of the file.
4. `__FUNCTION__`: The function name.
5. `__CLASS__`: The class name.
6. `__METHOD__`: The class method name.

## Scope

**Static Scope:** In PHP, variables within functions are typically destroyed after the function executes. Static variables, however, retain their values between function calls. You can declare a variable as static by using the static keyword.

```php
function testStaticScope() {
    static $counter = 0; // Declared as static
    $counter++;
    echo "Counter: $counter\n";
}

testStaticScope(); // Output: Counter: 1
testStaticScope(); // Output: Counter: 2
testStaticScope(); // Output: Counter: 3
```

**Global Scope:** PHP also provides a `$GLOBALS` superglobal array, which allows access to global variables from anywhere in the code, even inside functions, without needing the `global` keyword.

```php
$globalVariable = "I'm global!";

function testGlobalScope() {
    echo $GLOBALS['globalVariable']; // Accessing global variable using $GLOBALS
}

testGlobalScope(); // Output: I'm global!
```

## Build-in Functions

### String

- `strlen()`: Returns the length of a string.
- `str_replace()`: Replaces occurrences of a substring within a string.
- `strpos()`: Finds the position of the first occurrence of a substring in a string.

### Array

- `array_push()`: Adds one or more elements to the end of an array.
- `array_pop()`: Removes the last element from an array.
- `count()`: Returns the number of elements in an array.

### Date

- `date()`: Formats a local date and time.
- `time()`: Returns the current Unix timestamp.
- `strtotime()`: Parses an English textual datetime into a Unix timestamp.

## Anonymous Functions

An anonymous function is simply a function without a name. It’s often assigned to a variable so you can reuse or call it multiple times if needed. Anonymous functions are commonly used in scenarios where the function is used only in a specific place, like within a callback.

```php
$sayHello = function($name) {
    return "Hello, $name!";
};

// Using the function
echo $sayHello("Alice"); // Output: Hello, Alice!
```

## Closures

In PHP, a closure is a special kind of anonymous function that can capture variables from its surrounding scope, allowing it to "remember" values even after it has been called. This is done using the `use` keyword.

Closures are helpful when you need to use a variable that was defined outside the function but only within the function’s scope.

```php
// Define a variable outside the function
$message = "Good Morning";

// Create a closure that uses the $message variable
$greet = function($name) use ($message) {
    return "$message, $name!";
};

// Using the closure
echo $greet("Alice"); // Output: Good Morning, Alice!
```

```php
$count = 1;

// Closure to increment $count
$incrementCount = function() use (&$count) {
    $count++;
};

// Call the closure multiple times
$incrementCount();
$incrementCount();
echo $count; // Output: 3
```

## Array

There are three primary types of arrays:

1. **Indexed Arrays**: Arrays with numerical indices, starting at zero by default.
2. **Associative Arrays**: Arrays with custom keys (strings) instead of numerical indices.
   . **Multidimensional Arrays**: Arrays that contain one or more arrays within them.

### Sorting Functions

- `sort()`: Sorts an indexed array in ascending order.
- `rsort()`: Sorts an indexed array in descending order.
- `asort()`: Sorts an associative array by value in ascending order, preserving keys.
- `ksort()`: Sorts an associative array by key in ascending order.
- `arsort()`: Sorts an associative array by value in descending order, preserving keys.
- `krsort()`: Sorts an associative array by key in descending order.

### Merging Arrays

- `array_merge()`: Merges two or more arrays, appending values from later arrays.
- `array_merge_recursive()`: Similar to `array_merge()`, but it merges nested arrays recursively.

### Array Filtering

- `array_filter()`: Filters elements of an array based on a callback function. Only elements for which the callback returns `true` are kept.

### Array Mapping

- `array_map()`: Applies a callback function to each element in one or more arrays, returning a new array with the results.

### Array Searching

- `in_array()`: Checks if a value exists in an array.
- `array_search()`: Searches for a specific value and returns the first corresponding key.

### Array Reduction

- `array_reduce()`: Reduces an array to a single value by applying a callback function.

# JSON

## Encoding JSON

To convert a PHP array or object into JSON format, you use the `json_encode()` function. This function takes a PHP array or object as input and returns a JSON-encoded string.

`json_encode()` automatically handles nested arrays and objects, converting them into valid JSON format.

## Decoding JSON

To convert a JSON string back into a PHP array or object, use the `json_decode()` function. By default, `json_decode()` converts JSON into a PHP object, but you can specify a second parameter as true to get an associative array instead.

## Handling JSON Errors

Both json_encode() and json_decode() can sometimes encounter errors. You can use json_last_error() and json_last_error_msg() to check for issues.

```php
// Malformed JSON string
$jsonData = '{"name":"Alice","age":25,"city":"New York"'; // Missing closing brace

$data = json_decode($jsonData);

if (json_last_error() !== JSON_ERROR_NONE) {
    echo "JSON Error: " . json_last_error_msg(); // Output: JSON Error: Syntax error
}
```

# Standard PHP Library
## SplStack (Stack)
```php
$stack = new SplStack();

// Push elements onto the stack
$stack->push("first");
$stack->push("second");
$stack->push("third");

// Pop elements off the stack
echo $stack->pop(); // Output: third
echo $stack->pop(); // Output: second
echo $stack->pop(); // Output: first
```
- `$stack->push()` adds elements to the stack.
- `$stack->pop()` removes and returns the top element.
## SplQueue (Queue)
```php
$queue = new SplQueue();

// Enqueue elements into the queue
$queue->enqueue("first");
$queue->enqueue("second");
$queue->enqueue("third");

// Dequeue elements from the queue
echo $queue->dequeue(); // Output: first
echo $queue->dequeue(); // Output: second
echo $queue->dequeue(); // Output: third
```
- `$queue->enqueue()` adds elements to the end of the queue.
- `$queue->dequeue()` removes and returns elements from the front of the queue.
## SplDoublyLinkedList
```php
$list = new SplDoublyLinkedList();

// Adding elements to the list
$list->push("first");
$list->push("second");
$list->push("third");

// Traverse the list forwards
$list->rewind();
while ($list->valid()) {
    echo $list->current() . "\n"; // Output: first, second, third
    $list->next();
}

// Traverse the list backwards
$list->setIteratorMode(SplDoublyLinkedList::IT_MODE_LIFO);
foreach ($list as $item) {
    echo $item . "\n"; // Output: third, second, first
}
```
- `$list->push()` adds elements to the end of the list.
- `rewind()` and `next()` allow for forward traversal.
## Summary of Key SPL Data Structures
1. __SplStack__: LIFO stack.
2. __SplQueue__: FIFO queue.
3. __SplDoublyLinkedList__: Doubly linked list allowing bidirectional traversal.
4. __SplFixedArray__: Array with a fixed size.
5. __SplHeap__: Priority-based sorting with `SplMinHeap` and `SplMaxHeap`.
6. __SplObjectStorage__: Stores objects as keys with optional associated data.
7. __SplPriorityQueue__: Queue with element priorities.