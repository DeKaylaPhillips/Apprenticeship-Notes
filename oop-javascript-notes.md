# OBJECT ORIENTED PROGRAMMING IN JAVASCRIPT NOTES

## Object Oriented Programming

- Programming paradigm that focuses on creating objects that contain both data and functionality; able to write code using different programming paradigms
- Models real-world concepts as objects that have properties (attributes) and methods (functions)
- Objects are contained within classes
- Classes are the "template" or "blueprint" for creating objects

## Basic OOP Concepts

**Class**:

- BLUEPRINT for creating objects
- defines the properties and methods that an object will have
- define a class using the `class` keyword

**Object**:

- INSTANCE of a class
- has its own values for the properties defined in the class and can call the methods defined in the class

**Property**:

- VALUE that belongs to an object
- represents some aspect of the object's state
- can be primitive types (numbers, strings, etc...) or *other* objects

**Method**:

- FUNCTION that belongs to an object; allows the object to perform some action or computation

## Applying OOP to JavaScript

**About JavaScript:**

- multi-paradigm language; supports several programming paradigms, including OOP
- NOT "pure" object-oriented language like Java or C++
- introduction of ES6 brought new features that make it easier to write OOP code

**Classes in JavaScript:**

- objects created using "constructor functions" or classes (ES6)
- constructor functions/classes are the "template" or "blueprint" for creating new objects

```javascript
// Create an object representing a CAR using a constructor function (class pre-ES6).

function Car(make, model, year) { 
    this.make = make;
    this.model = model;
    this.year = year;
    this.drive = function() { 
        console.log("Vroom vroom!");
    };
};

// accessing information in the object

const car = new Car('Ford', 'Focus', '2007'); // creates a new Car object
console.log(car.make);  // Ford
console.log(car.model); // Focus
console.log(car.year);  // Year
car.drive();            // Vroom vroom

// Create an object representing a CAR using a class (ES6 syntax).

class Car { 
    constructor(make, model, year) { // used to initialize objects 
        this.make = make;
        this.model = model;
        this.year = year;
        this.drive = function() {
            console.log("Vroom vroom!");
        };    
    };
};

// accessing information in the object

const car = new Car('Ford', 'Focus', '2007'); // instantiate the class
console.log(car.make)   // Ford
console.log(car.model)  // Focus
console.log(car.year)   // 2007
car.drive()             // Vroom vroom!
```

**Class Structure:**

- use the `class` keyword to define a class

```javascript
class MyClass {
    constructor(param1, param2) {
        // properties
    }

    method1() {
        // code to execute
    }

    method2() {
        // code to execute
    }
}
```

`MyClass` is the name of the class

`MyClass` has a constructor function that takes two parameters

`MyClass` has 2 methods --> `method1` and `method2`

**Imports:**

How To Use a Class in Another File:

- use the `export` keyword to make the class available for import
- use the `import` keyword to import the class into another file

```javascript
// Export a class from file --> MyClass.js
export class MyClass {
    constructor(param1, param2) {
        this.property = param1,
        this.attribute = param2
    }

    method1() {
        console.log('This is from method1.')
    }

    method2() {
        console.log('This is from method2.')
    }
}

// Import a class to file --> Main.js
import { MyClass } from './MyClass.js';

const myObject = new MyClass(param1, param2);
myObject.method1();
```

**File Path Naming:**

- File path naming for classes in ES6 depends on the module system being used
- If using a bundler, like WebPack or Rollup - use *relative* paths to import class

i.e. (using *example 2*):

- When both files in the SAME directory:

```javascript
import { MyClass } from './MyClass.js';
```

- When files in DIFFERENT directories:

```javascript
import { MyClass } from './classes/MyClass.js';
```
