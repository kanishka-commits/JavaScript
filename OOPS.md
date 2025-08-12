# JavaScript OOP Concepts & Interview Practice
JavaScript is multi-paradigm — it supports OOP, functional, and procedural styles.
## **Definition of OOP**
**Object-Oriented Programming (OOP)** is a programming paradigm that organizes code into **objects** — collections of properties (data) and methods (functions) that operate on that data.
It helps in **code reusability, modularity, and maintainability**.

---

## **Core OOP Concepts in JavaScript**

### **1. Class**
Blueprint for creating objects. Classes define properties and methods that the created objects (instances) will have.
```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  greet() {
    console.log(`Hi, I’m ${this.name}`);
  }
}
const john = new Person("John", 25);
john.greet();
```

### **2. Object**
A collection of key-value pairs. It can be created from a class or directly as an object literal.
```javascript
const car = {
  brand: "Tesla",
  drive() {
    console.log("Driving...");
  }
};
```

### **3. Encapsulation**
Bundling data (properties) and methods (functions) into one unit and restricting direct access to some properties for data safety.
```javascript
class BankAccount {
  #balance = 0; // private
  deposit(amount) { this.#balance += amount; }
  getBalance() { return this.#balance; }
}
```

### **4. Abstraction**
Hiding complex implementation details and showing only the essential features through a public interface.
```javascript
// Abstraction example in OOP
class CoffeeMachine {
  start() {
    console.log("Starting the coffee machine...");
  }

  brewCoffee() {
    console.log("Brewing coffee...");
  }

  // Internal method - hidden from the user
  #heatWater() {
    console.log("Heating water internally...");
  }

  // Public method that uses the private method
  makeCoffee() {
    this.start();
    this.#heatWater(); // user doesn't see this implementation
    this.brewCoffee();
    console.log("Coffee is ready! ☕");
  }
}

// Using the abstraction
const myMachine = new CoffeeMachine();
myMachine.makeCoffee(); // Simple call for the user
// myMachine.#heatWater(); // ❌ Not allowed - private
```

### **5. Inheritance**
Allows one class to acquire properties and methods of another class, promoting code reuse.
```javascript
// Abstract-like class (cannot be directly instantiated)
class Animal {
  constructor(name) {
    if (new.target === Animal) {
      throw new Error("Cannot instantiate abstract class directly");
    }
    this.name = name;
  }

  eat() {
    console.log(`${this.name} is eating...`);
  }

  // Abstract method (must be implemented by child classes)
  makeSound() {
    throw new Error("makeSound() must be implemented by subclass");
  }
}

// Child class - Dog
class Dog extends Animal {
  makeSound() {
    console.log("Bark! Bark!");
  }
}
// Usage
const dog = new Dog("Buddy");
dog.eat();        // Buddy is eating...
dog.makeSound();  // Bark! Bark!
```

### **6. Polymorphism**
Allows methods to have the same name but behave differently depending on the object that calls them.
```javascript
// Parent class
class Animal {
  speak() {
    console.log("Some generic animal sound");
  }
}

// Child class
class Dog extends Animal {
  speak() {
    console.log("Bark!");
  }
}

// Function that shows polymorphism
function makeAnimalSpeak(animal) {
  animal.speak(); // Same method call, different output depending on object
}

// Creating objects
const dog = new Dog();

// Using the same function for different objects
makeAnimalSpeak(dog); // Bark!
```

### **7. `this` keyword**
Refers to the object that is executing the current function. Its value depends on how the function is called.
```javascript
class Example {
  show() { console.log(this); }
}
new Example().show(); // Example {}
```

### **8. Prototypes**
The mechanism by which JavaScript objects inherit properties and methods from other objects.
```javascript
function Person(name) { this.name = name; }
Person.prototype.greet = function() { console.log(`Hi, I’m ${this.name}`); };
```

### **9. Method Overriding**
When a child class redefines a method inherited from its parent class.
```javascript
class Parent { greet() { console.log("Hello"); } }
class Child extends Parent { greet() { console.log("Hi!"); } }
```

### **10. Static Methods**
Methods that belong to the class itself, not its instances.
```javascript
class MathUtil {
  static add(a, b) { return a + b; }
}
console.log(MathUtil.add(2, 3)); // 5
```

---

## **JavaScript OOP Interview Questions**

### **1. Class vs Prototype**
**Q:** What is the difference between **class** and **prototype** in JavaScript?  
**A:** Classes are ES6 syntax sugar over prototypes; under the hood, JavaScript still uses prototypes for inheritance.

---

### **2. `this` keyword loss**
When you assign a method to a variable, it loses its original `this` context.
```javascript
class Test {
  constructor() {
    this.value = 42;
  }
  show() {
    console.log(this.value);
  }
}
const obj = new Test();
const fn = obj.show;
fn(); // undefined
```

---

### **3. Inheritance**
```javascript
class Employee {
  constructor(name, salary) {
    this.name = name;
    this.salary = salary;
  }
  getDetails() {
    return `${this.name} earns ${this.salary}`;
  }
}
class Manager extends Employee {
  constructor(name, salary, department) {
    super(name, salary);
    this.department = department;
  }
  getDetails() {
    return `${super.getDetails()} and manages ${this.department}`;
  }
}
```

---

### **4. Encapsulation**
Use private fields (with `#`) to protect data from direct external modification.
```javascript
class BankAccount {
  #balance = 0;
  deposit(amount) { this.#balance += amount; }
  getBalance() { return this.#balance; }
}
```

---

### **5. Polymorphism**
Different classes can define methods with the same name but different behaviors.
```javascript
class Animal { speak() { console.log("Animal sound"); } }
class Dog extends Animal { speak() { console.log("Bark"); } }
```

---

### **6. Static Methods**
Static methods are called on the class itself, not on instances.
```javascript
class Utils {
  static add(a, b) { return a + b; }
}
const u = new Utils();
console.log(u.add); // undefined
```

---

### **7. Prototype Chain**
Add shared methods to a constructor function's prototype so all instances can use them.
```javascript
function Person(name) { this.name = name; }
Person.prototype.sayHi = function() { console.log(`Hi, I’m ${this.name}`); };
```

---

### **8. Getters and Setters**
Special methods for reading (`get`) and updating (`set`) private or protected properties.
```javascript
class User {
  #age;
  get age() { return this.#age; }
  set age(value) {
    if (value < 0) throw new Error("Invalid age");
    this.#age = value;
  }
}
```

---

### **9. Abstraction Limitation**
JavaScript doesn’t enforce abstraction; you must implement it manually or use TypeScript.

---

### **10. Multiple Inheritance**
JavaScript doesn’t support multiple inheritance directly but can simulate it using mixins.
```javascript
const canFly = Base => class extends Base { fly() { console.log("Flying"); } };
class Animal {}
class Bird extends canFly(Animal) {}
```
