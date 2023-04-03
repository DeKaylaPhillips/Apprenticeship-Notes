# SOLID PRINCIPLES OF OBJECT-ORIENTED PROGRAMMING EXPLAINED

*FreeCodeCamp --> <https://www.freecodecamp.org/news/solid-principles-explained-in-plain-english/>*

## SOLID Principles

- 5 principles of OOD
- Set of rules and best practices to follow while designing a class structure
- Help us understand the need for certain design patterns and software architecture

### What does 'S.O.L.I.D.' mean?

1. **S**-ingle Responsibility Principle
2. **O**-pen-Closed Principle
3. **L**-iskov Substituion Principle
4. **I**-nterface Segregation Principle
5. **D**-ependency Inversion Principle

### Background

Concepts of 'clean code', object-oriented architecture, and design patterns are interconnected due to their origins.

Purpose: *"To create understandable, readable, and testable code that many developers can collaboratively work on."*

Robert J. Martin (a.k.a. Uncle Bob), *Computer Scientist*

- introduced *principles* of SOLID
- author of "Clean Code" & "Clean Architecture"
- participant of "Agile Alliance"

Michael Feathers

- introduced the S.O.L.I.D. *acronym*

## The SINGLE RESPONSIBILITY Principle

**A class should do ONE thing and therefore it should have only a SINGLE reason to change.**

- only one potential change (database logging, logging logic, etc) in the software's specification should be able to affect the specification of the class
- if a class is a data container with fields regarding that entity, should only change when the data model is changed

**Importance:**

- decrease potential use of incompatible modules in collaborative workspace
- makes version control easier; commits can help understand classes and their usage
- decreases merge conflicts and the complexity of them

**Separating Different Types of Logic into Distinct Components:**

**PRINTING LOGIC:**

- code responsible for displaying output to a user
- ensure that application's interface is easily modified w/o affecting underlying functionality

**BUSINESS LOGIC:**

- core functionality of application
- flexible, scalable & easily modified/extended
- reusable in different contexts

**PERSISTANCE LOGIC:**

- code repsonsible for storing and retrieving data from a database or other storage medium
- generic and reusable
- used across multiple different types of applications
- ensure that changes to the way data is stored don't impact other parts of the application

**VALIDATION LOGIC:**

- ensures that user input in valid

**SECURITY LOGIC:**

- protects the application from unauthorized access

**EVENT HANDLING LOGIC:**

- responds to use actions such as button clicks

**Common Pitfalls/Anti-Patterns:**

Common mistakes that violate the SRP:

Book Class:

```javascript
class Book {
    constructor(name, author, year, price, isbn) {
        this.name = name,
        this.author = author,
        this.year = year,
        this.price = price,
        this.isbn = isbn
    }
}
```

Simple book class with fields.

Invoice Class:

```javascript
class Invoice { // This class has 3 responsibilities.
    constructor(Book, quantity, discountRate, taxRate) {
        const book = new Book()

        this.book = book,
        this.quantity = quantity,
        this.discountRate = discountRate,
        this.taxRate = taxRate,
        this.total = this.calculateTotal()
    }

    calculateTotal() { // Business logic - core functionality.
        let price = ((book.price - book.price * discountRate) * this.quantity)
        let priceWithTaxes = price * (1 + taxRate)
        return priceWithTaxes;
    }

    printInvoice() { // Printing logic here is a violation of SRP.
        console.log(`${quantity}x${book.name} ${book.price}$`);
        console.log(`Discount Rate: ${discountRate}`);
        console.log(`Tax Rate: ${taxRate}`);
        console.log(`Total: ${total}`)
    }

    saveToFile(filename) { // Persistance logic here is a violation of SRP.
        // execute code to create a file with a given name and write the invoice
    }
}
```

Contains fields about invoicing, and 3 methods (...3 responsibilities with 3 different types of logic):

- calculateTotal - calculates total price
- printInvoice - prints the invoice to the console
- saveToFile - writes the invoice to a file

**VIOLATIONS OF THIS DESIGN:**

1. printInvoice() method

    SRP states --> *class should only have a SINGLE reason to change*
    - only change: invoice calculation for the class

    In the current architecture, if the printing format needed to change, the class would have to be changed.
    - You should not have **PRINTING LOGIC** mixed with **BUSINESS LOGIC** in the same class.

2. saveToFile() method

    - method mixes **PERSISTANCE LOGIC** with **BUSINESS LOGIC**
    - extremely common mistake
    - other examples include saving to a database, making an API call, or other things related to persistance

**HOW TO FIX THE PRINT FUNCTION:**

Create two new classes for printing and persistence logic.

```javascript

class Invoice { // Contains 1 responsibility
    constructor(Book, quantity, discountRate, taxRate) {
        const book = new Book()

        this.book = book,
        this.quantity = quantity,
        this.discountRate = discountRate,
        this.taxRate = taxRate,
        this.total = this.calculateTotal()
    }

    calculateTotal() { // Business logic - core functionality.
        let price = ((book.price - book.price * discountRate) * this.quantity)
        let priceWithTaxes = price * (1 + taxRate)
        return priceWithTaxes;
    }
}

class InvoicePrinter { // Contains 1 responsibility
    constructor(Invoice) {
        const invoice = new Invoice()

        this.invoice = invoice
    }

    print() {
        console.log(`${quantity}x${book.name} ${book.price}$`);
        console.log(`Discount Rate: ${discountRate}`);
        console.log(`Tax Rate: ${taxRate}`);
        console.log(`Total: ${total}`);
    }
}

class InvoicePersistence { // Contains 1 responsibility
    constructor(Invoice) {
        const invoice = new Invoice()

        this.invoice = invoice
    }

    saveToFile(filename) { 
        // code to execute to create a file with a given name
    }
}
```

## The OPEN-CLOSED Principle

**Classes should be open for extension and closed to modification.**

- Modification --> changing the code of an existing class
- Extension --> adding new functionality

- we should be able to add new functionality without touching the existing code for the class
- modifying existing code increases the risk of creating bugs
- avoid touching the tested and reliable (mostly) production code if possible

**How would you add new functionality without touching the class?**

- interfaces and/or..
- abstract classes

**Helpful ways to implement OCP in JavaScript:**

**STRATEGY PATTERNS:**

- behaviroal design pattern that defines a family of algorithms, encapsulates each one, and makes them interchangeable

```javascript
class Calculator {
    constructor(strategy) {
        this.strategy = strategy;
    }

    calculate(a, b) {
        return this.strategy.calculate(a, b);
    }
}

class AddStrategy {
    calculate(a, b) {
        return a + b;
    }
}

class SubtractStrategy {
    calculate(a, b) {
        return a - b;
    }
}

// Usage:
const calculator = new Calculator(new AddStrategy());
console.log(calculator.calculate(5, 3));
```

1. Creates a new instance of the `Calculator` class and assigns it to the calculator variable
2. `new` keyword used to create a new object from the `Calculator`
3. `Calculator` constructor takes one arg - an object of a class that implements the `calculate` method
4. `new AddStrategy()` creates a new instance of the AddStrategy class and passes it ass an arg to the `Calculator` constructor

The `calculator` object is configured to use the `AddStrategy` when the `calculate` method is called.

Now add a new strategy without modifying the Calculator class:

```javascript
class MultiplyStrategy {
    calculate(a, b) {
        return a * b;
    }
}

calculator.strategy = new MultiplyStrategy(); // calculator property to be used for calculation is the multiplication class
console.log(calculator.calculate(5, 3)); // the calculate method within the multiplication class accepts two nums as args for calculation
```

1. Assigns a new object of the `MultiplyStrategy` class to the `strategy` property of the `calculator` object
    This changes the strategy used by the calculator to the multiplication strategy.
2. When the `calculate` method is called, it will use the `MultiplyStrategy` to perform the calculaton

`Calculator` is open for *extension* - can add new strategies to it (i.e. `MultiplyStrategy`) without modifying the `Calculator` class itself

- By allowing the `strategy` property to be set to different objects that implement the `calculate` method, the `Calculator` class can perform calculations using different strategies without needing to be modified itself.
- Class is more flexible and easier to extend with new functionality, which follows the Open-Closed principle.

**FACTORY PATTERNS:**

- creational design pattern that provides an interface for creating objects in a superclass but allows subclasses to alter the type of objects that will be created

```javascript
class Animal {
    makeSound() {
        //
    }
}

class Dog extends Animal {
    makeSound() {
        return "Woof!";
    }
}

class Cat extends Animal {
    makeSound() {
        return "Meow!";
    }
}

class AnimalFactory {
    static createAnimal(animalType) {
        switch(animalType) {
            case 'Dog':
                return new Dog();
            case 'Cat':
                return new Cat()
            default:
                throw new Error(`Unknown animal type: ${animalType}`);
        }
    }
}

// Usage:
const animalType = 'Dog';
const animal = AnimalFactory.createAnimal(animalType);
console.log(animal.makeSound()); // Output: Woof!

// Add a new animal without modifying the AnimalFactory class
class Cow extends Animal {
    makeSound() {
        return 'Moo!';
    }
}

AnimalFactory.createAnimal = function(animalType) {
    switch(animalType) {
         case 'Dog':
            return new Dog();
        case 'Cat':
            return new Cat();
        case 'Cow': // functionality extended here to include a cow
            return new Cow();
        default:
            throw new Error(`Unknown animal type: ${animalType}`);
            
    }
}

const newAnimalType = 'Cow';
const newAnimal = AnimalFactor.createAnimal(newAnimalType);
console.log(newAnimal.makeSound());
```

The `AnimalFactory` class is open for extension; can now add new animal types to it without modifying the `AnimalFactory` class itself

## The LISKOV SUBSTITUTION Principle

**Objects of a superclass should be able to be replaced with objects of its subclass without affecting the correctness of the program.**

- emphasizes the importance of inheritance and polymorphism in OOP
- objects of derived classes can be treated as objects of their base classes without any issues

i.e.)   Class B is a subclass of Class A.

**Should be able to pass a Class B object to any method expecting a Class A object.**

- when inheritance is used, assume that the child class inherits everything that the superclass has
- child class extends the behavior but never narrows it down
- not obeying this principle leads to bugs that are hard to detect
- easy-to-understand the principle, but hard to detect in code

```javascript

// A Rectangle class, and getArea function that returns the area of a rectangle.

class Rectangle {
    constructor(width, height) {
        this.width = width,
        this.height = height
    }

    getWidth() {
        return this.width;
    } 

    setWidth(width) {
        this.width = width;
    }

    getHeight() {
        return this.height;
    }

    setHeight(height) {
        this.height = height;
    }

    getArea() {
        return this.width * this.height
    }
}

// A Square class - note: a square is a special type of rectangle where the width is equal to the height

class Square extends Rectangle { // creates a subclass that inherits from a parent class
    constructor(size) { // size parameter sets the width and height properties of the square    
        super(size, size);  
    }

    setWidth(width) { // overrides to ensure that both properties are always the same for a square
        super.setWidth(width);
        super.setHeight(width);
    }

    setHeight(height) { // calling either this method, or setWidth() updates both properties using the value passed in
        super.setHeight(height);
        super.setWidth(height);
    }
}

```

`super` is used to call the corresponding method of the parent class (`Rectangle`) and update the `width` and `height` properties accordingly

i.e.)

```javascript
const rectangle = new Rectangle(5, 10);
console.log(rectangle.getArea());

const square = new Square(10);
console.log(square.getArea());
```

Square class extends the functionality of the Rectangle class

- Set height and width to the same value in the constructor
- Do not want clients to change height or weight in a way that can violate the square property
- Override setters to set both properties whenever one is changed - *violates the principle because it changes the behavior of the `Rectangle` class*

## The INTERFACE SEGRATION Principle

**Many client-specific interfaces are better than one general-purpose interface.**

- segregation --> keeping things separated; focus is on separating the interfaces
- do not force clients to implement a function that isn't needed

*In JavaScript, ...*

- If a class needs to implement an interface, it should only implement the methods that are actually needed, rather than implementing the entire interface.
- Separate the different interfaces you'll be defining!

i.e.)

Instead of ...

```javascript
class Animal { // provides 3 methods, but Fish class only needs 1
    eat() {
        console.log("Animal eating...")
    }
    sleep() {
        console.log("Animal sleeping...")
    }
    swim() {
        console.log("Animal swimming...")
    }
}

class Fish {
    constructor() {
        this.animal = new Animal()
    }
    swim () {
        this.animal.swim()
    }
}
```

Do *this* instead to ensure classes are not forced to imlement methods they do not need...

```javascript
const ISwim = { // separate interface
    swim: function() {};
};

class Fish {
    swim() {
        console.log("Fish swimming...")
    }
}

class Fish {} // error: Class 'Fish' incorrectly implements interface 'ISwim'
```

By defining and implementing interfaces in this way, you ensure code is modular and follows the principles of ISP, even in dynamically-typed languages like JavaScript.

## The DEPENDENCY INVERSION Principle

**Classes should depend upon interfaces or abstract classes instead of concrete classes and functions.**

*Note:* OCP states the goal of OO architecture, DIP sets the primary mechanism

- want classes to be open to extension --> reorganize dependencies to depend on interfaces/abstract classes instead of concrete classes
