# ☕ Java OOP - Complete Beginner's Revision Guide

> Covers every concept with explanation + full code + output 🎯

---

## 1. 🏗️ Introduction to OOP

OOP = **Object-Oriented Programming**.
Instead of writing everything in one place, we organize code into **objects** that represent real-world things.

Think of it like this:
- A **Car** has properties (color, speed) and actions (start, stop)
- In OOP → properties = **fields**, actions = **methods**

**4 Pillars of OOP:**
| Pillar | Simple Meaning | Real-life Example |
|---|---|---|
| 🛡️ Encapsulation | Hide internal data, expose only what's needed | ATM hides its internal logic |
| 👪 Inheritance | Child gets parent's properties automatically | Child inherits parent's traits |
| 🎭 Polymorphism | Same action, different behavior | A person acts differently at home vs office |
| 🌫️ Abstraction | Show only what's necessary, hide the rest | Car steering wheel hides engine complexity |

**Why OOP?**
- ✅ Code reuse
- ✅ Easy to maintain and extend
- ✅ Models real-world problems naturally

---

## 2. 🏠 Class and Object

### 📌 What is a Class?
A **class** is a blueprint/template. It defines what properties and behaviors an object will have.
It does NOT hold actual data — it's just a design.

### 📌 What is an Object?
An **object** is a real instance created from a class. It holds actual values in memory.

```
Class  →  like a house blueprint
Object →  like the actual house built from that blueprint
```

```java
// Class definition (blueprint)
class Student {
    String name;   // field
    int age;       // field

    void introduce() {   // method
        System.out.println("Hi! I am " + name + ", age " + age);
    }
}

public class Main {
    public static void main(String[] args) {
        // Creating objects (instances)
        Student s1 = new Student();
        s1.name = "Alice";
        s1.age = 20;

        Student s2 = new Student();
        s2.name = "Bob";
        s2.age = 22;

        s1.introduce();
        s2.introduce();
    }
}
```

**Output:**
```
Hi! I am Alice, age 20
Hi! I am Bob, age 22
```

> 💡 Each object is **independent** — changing s1's name won't affect s2.

---

## 3. 🔧 Methods

A **method** is a block of code that performs a specific task.
You define it once and call it as many times as needed.

### Method Structure:
```
returnType methodName(parameters) {
    // body
}
```

```java
class Calculator {
    // Method that returns a value
    int add(int a, int b) {
        return a + b;
    }

    // Method that returns nothing (void)
    void printMessage(String msg) {
        System.out.println("Message: " + msg);
    }

    // Method with no parameters
    void greet() {
        System.out.println("Hello from Calculator!");
    }
}

public class Main {
    public static void main(String[] args) {
        Calculator calc = new Calculator();

        int result = calc.add(10, 5);
        System.out.println("Sum: " + result);

        calc.printMessage("OOP is fun");
        calc.greet();
    }
}
```

**Output:**
```
Sum: 15
Message: OOP is fun
Hello from Calculator!
```

---

## 4. 🛠️ Constructors

A **constructor** is a special method that runs **automatically** when you create an object using `new`.

**Rules:**
- Same name as the class
- No return type (not even void)
- Used to initialize fields

### Types:

**1. Default Constructor** — no parameters, sets default values

**2. Parameterized Constructor** — takes parameters, sets custom values

```java
class Book {
    String title;
    String author;
    int pages;

    // Default Constructor
    Book() {
        title = "Unknown";
        author = "Anonymous";
        pages = 0;
        System.out.println("Default constructor called");
    }

    // Parameterized Constructor
    Book(String title, String author, int pages) {
        this.title = title;
        this.author = author;
        this.pages = pages;
        System.out.println("Parameterized constructor called");
    }

    void display() {
        System.out.println(title + " by " + author + " (" + pages + " pages)");
    }
}

public class Main {
    public static void main(String[] args) {
        Book b1 = new Book();                          // calls default
        Book b2 = new Book("Java 101", "James", 350); // calls parameterized

        b1.display();
        b2.display();
    }
}
```

**Output:**
```
Default constructor called
Parameterized constructor called
Unknown by Anonymous (0 pages)
Java 101 by James (350 pages)
```

> ⚠️ If you write any constructor yourself, Java will NOT provide a default one automatically.

---

## 5. 👈 `this` Keyword

`this` refers to the **current object** — the object that is calling the method or constructor.

### 3 Main Uses:

**1. Resolve name conflict** between field and parameter

**2. Call another constructor** from within a constructor using `this()`

**3. Return current object** for method chaining

```java
class Person {
    String name;
    int age;
    String city;

    // Use 1: this.field to distinguish from parameter
    Person(String name, int age, String city) {
        this.name = name;   // this.name = field, name = parameter
        this.age = age;
        this.city = city;
    }

    // Use 2: constructor chaining with this()
    Person(String name) {
        this(name, 18, "Unknown");  // calls the 3-param constructor
        System.out.println("Single-param constructor used");
    }

    // Use 3: return this for chaining
    Person setCity(String city) {
        this.city = city;
        return this;  // returns current object
    }

    void display() {
        System.out.println(name + " | Age: " + age + " | City: " + city);
    }
}

public class Main {
    public static void main(String[] args) {
        Person p1 = new Person("Alice", 25, "Delhi");
        p1.display();

        Person p2 = new Person("Bob");  // uses chained constructor
        p2.display();

        // Method chaining using 'this'
        Person p3 = new Person("Carol", 30, "Mumbai");
        p3.setCity("Pune").display();  // chained call
    }
}
```

**Output:**
```
Single-param constructor used
Alice | Age: 25 | City: Delhi
Bob | Age: 18 | City: Unknown
Carol | Age: 30 | City: Pune
```

---

## 6. 📊 `static` Keyword

`static` means the member **belongs to the class**, not to any specific object.
All objects **share** the same static variable.

### When to use static?
- Counters (how many objects created)
- Utility/helper methods (like `Math.sqrt()`)
- Constants (`static final`)

```java
class Employee {
    static int totalCount = 0;  // shared by ALL employees
    String name;
    int id;

    Employee(String name) {
        totalCount++;           // increments for every new object
        this.id = totalCount;
        this.name = name;
    }

    // Static method — called on class, not object
    static void showTotal() {
        System.out.println("Total Employees: " + totalCount);
    }

    void showInfo() {
        System.out.println("ID: " + id + " | Name: " + name);
    }
}

public class Main {
    public static void main(String[] args) {
        Employee.showTotal();   // before creating any

        Employee e1 = new Employee("Alice");
        Employee e2 = new Employee("Bob");
        Employee e3 = new Employee("Carol");

        e1.showInfo();
        e2.showInfo();
        e3.showInfo();

        Employee.showTotal();   // after creating 3
    }
}
```

**Output:**
```
Total Employees: 0
ID: 1 | Name: Alice
ID: 2 | Name: Bob
ID: 3 | Name: Carol
Total Employees: 3
```

> ⚠️ Static methods **cannot** use `this` or access non-static fields directly.

---

## 7. 👪 Inheritance

Inheritance lets a **child class** reuse fields and methods from a **parent class** using `extends`.

Think of it as: Dog **IS-A** Animal → Dog inherits Animal's behavior.

### Types of Inheritance:

```
Single:           Multilevel:          Hierarchical:
  Animal            Animal                 Animal
    ↑                  ↑                  /      \
   Dog              Mammal             Dog        Cat
                       ↑
                      Dog
```

```java
// Parent class
class Animal {
    String name;

    Animal(String name) {
        this.name = name;
    }

    void eat() {
        System.out.println(name + " is eating");
    }

    void breathe() {
        System.out.println(name + " is breathing");
    }
}

// Single Inheritance: Dog extends Animal
class Dog extends Animal {
    String breed;

    Dog(String name, String breed) {
        super(name);        // calls Animal's constructor
        this.breed = breed;
    }

    void bark() {
        System.out.println(name + " says: Woof! Woof!");
    }
}

// Multilevel Inheritance: Puppy extends Dog extends Animal
class Puppy extends Dog {
    Puppy(String name) {
        super(name, "Mixed");
    }

    void play() {
        System.out.println(name + " is playing!");
    }
}

public class Main {
    public static void main(String[] args) {
        System.out.println("--- Dog ---");
        Dog d = new Dog("Bruno", "Labrador");
        d.eat();      // from Animal
        d.breathe();  // from Animal
        d.bark();     // own method

        System.out.println("\n--- Puppy (Multilevel) ---");
        Puppy p = new Puppy("Coco");
        p.eat();      // from Animal (2 levels up)
        p.bark();     // from Dog
        p.play();     // own method
    }
}
```

**Output:**
```
--- Dog ---
Bruno is eating
Bruno is breathing
Bruno says: Woof! Woof!

--- Puppy (Multilevel) ---
Coco is eating
Coco says: Woof! Woof!
Coco is playing!
```

> ❌ Java does NOT support multiple inheritance with classes (a class can't extend two classes).

---

## 8. 🎭 Polymorphism

Poly = many, Morph = forms. **Same method name, different behavior.**

### Type 1: Method Overloading (Compile-time Polymorphism)
Same method name, **different parameters**. Decided at compile time.

```java
class MathHelper {
    // Same name, different parameter types/count
    int multiply(int a, int b) {
        return a * b;
    }

    double multiply(double a, double b) {
        return a * b;
    }

    int multiply(int a, int b, int c) {
        return a * b * c;
    }
}

public class Main {
    public static void main(String[] args) {
        MathHelper m = new MathHelper();

        System.out.println(m.multiply(3, 4));           // int version
        System.out.println(m.multiply(2.5, 4.0));       // double version
        System.out.println(m.multiply(2, 3, 4));        // 3-param version
    }
}
```

**Output:**
```
12
10.0
24
```

---

### Type 2: Method Overriding (Runtime Polymorphism)
Child class **redefines** a parent method. Decided at runtime.

```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog says: Woof!");
    }
}

class Cat extends Animal {
    @Override
    void sound() {
        System.out.println("Cat says: Meow!");
    }
}

class Cow extends Animal {
    @Override
    void sound() {
        System.out.println("Cow says: Moo!");
    }
}

public class Main {
    public static void main(String[] args) {
        // Parent reference, child object → runtime decides which sound()
        Animal a1 = new Dog();
        Animal a2 = new Cat();
        Animal a3 = new Cow();

        a1.sound();   // Dog's version
        a2.sound();   // Cat's version
        a3.sound();   // Cow's version
    }
}
```

**Output:**
```
Dog says: Woof!
Cat says: Meow!
Cow says: Moo!
```

> 💡 `@Override` annotation is optional but recommended — it tells Java you're intentionally overriding.

---

## 9. 🛡️ Encapsulation

Encapsulation = **wrapping data (fields) and methods together** + **restricting direct access** to fields.

**How?** Make fields `private` → provide `public` getters and setters.

**Why?** To protect data from invalid or accidental changes.

```java
class BankAccount {
    private String owner;
    private double balance;   // hidden from outside

    BankAccount(String owner, double initialBalance) {
        this.owner = owner;
        if (initialBalance >= 0)
            this.balance = initialBalance;
    }

    // Getter — read balance
    public double getBalance() {
        return balance;
    }

    // No direct setter for balance — use deposit/withdraw instead
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposited: " + amount);
        } else {
            System.out.println("Invalid deposit amount!");
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("Withdrawn: " + amount);
        } else {
            System.out.println("Insufficient balance or invalid amount!");
        }
    }

    public void showBalance() {
        System.out.println(owner + "'s Balance: " + balance);
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount acc = new BankAccount("Alice", 1000);
        acc.showBalance();

        acc.deposit(500);
        acc.showBalance();

        acc.withdraw(200);
        acc.showBalance();

        acc.withdraw(2000);  // should fail
    }
}
```

**Output:**
```
Alice's Balance: 1000.0
Deposited: 500.0
Alice's Balance: 1500.0
Withdrawn: 200.0
Alice's Balance: 1300.0
Insufficient balance or invalid amount!
```

---

## 10. 🌫️ Abstraction (Abstract Class)

Abstraction = **show only what's necessary, hide the internal details**.

An **abstract class** can have:
- Abstract methods (no body — child MUST implement)
- Regular methods (with body — shared logic)

```java
abstract class Shape {
    String color;

    Shape(String color) {
        this.color = color;
    }

    // Abstract method — no body, child must define
    abstract double area();
    abstract double perimeter();

    // Regular method — shared by all shapes
    void display() {
        System.out.println("Shape: " + this.getClass().getSimpleName());
        System.out.println("Color: " + color);
        System.out.println("Area: " + area());
        System.out.println("Perimeter: " + perimeter());
        System.out.println("---");
    }
}

class Circle extends Shape {
    double radius;

    Circle(String color, double radius) {
        super(color);
        this.radius = radius;
    }

    @Override
    double area() { return Math.PI * radius * radius; }

    @Override
    double perimeter() { return 2 * Math.PI * radius; }
}

class Rectangle extends Shape {
    double length, width;

    Rectangle(String color, double length, double width) {
        super(color);
        this.length = length;
        this.width = width;
    }

    @Override
    double area() { return length * width; }

    @Override
    double perimeter() { return 2 * (length + width); }
}

public class Main {
    public static void main(String[] args) {
        Shape s1 = new Circle("Red", 5);
        Shape s2 = new Rectangle("Blue", 4, 6);

        s1.display();
        s2.display();

        // Shape s = new Shape("Green");  ❌ ERROR — can't instantiate abstract class
    }
}
```

**Output:**
```
Shape: Circle
Color: Red
Area: 78.53981633974483
Perimeter: 31.41592653589793
---
Shape: Rectangle
Color: Blue
Area: 24.0
Perimeter: 20.0
---
```

---

## 11. 📜 Interfaces

An **interface** is a 100% abstract contract — it only defines **what** to do, not **how**.

**Key Points:**
- All methods are `public abstract` by default
- All fields are `public static final` by default
- A class can implement **multiple interfaces** (solves multiple inheritance problem)
- Java 8+: can have `default` and `static` methods with body

```java
interface Flyable {
    void fly();   // abstract by default
}

interface Swimmable {
    void swim();
}

interface Runnable {
    void run();
}

// Duck implements multiple interfaces
class Duck implements Flyable, Swimmable, Runnable {
    String name;

    Duck(String name) { this.name = name; }

    @Override
    public void fly()  { System.out.println(name + " is flying"); }

    @Override
    public void swim() { System.out.println(name + " is swimming"); }

    @Override
    public void run()  { System.out.println(name + " is running"); }
}

// Fish only swims
class Fish implements Swimmable {
    @Override
    public void swim() { System.out.println("Fish is swimming silently"); }
}

public class Main {
    public static void main(String[] args) {
        Duck duck = new Duck("Donald");
        duck.fly();
        duck.swim();
        duck.run();

        System.out.println("---");

        Fish fish = new Fish();
        fish.swim();
    }
}
```

**Output:**
```
Donald is flying
Donald is swimming
Donald is running
---
Fish is swimming silently
```

### Interface vs Abstract Class:
| Feature | Abstract Class | Interface |
|---|---|---|
| Methods | Abstract + concrete | Abstract (+ default in Java 8+) |
| Variables | Any type | `public static final` only |
| Multiple inheritance | ❌ No | ✅ Yes |
| Constructor | ✅ Yes | ❌ No |

---

## 12. 👨 `super` Keyword

`super` refers to the **parent class**. Used to:
1. Call parent's constructor → `super()`
2. Call parent's method → `super.methodName()`
3. Access parent's field → `super.fieldName`

```java
class Vehicle {
    String brand;
    int speed;

    Vehicle(String brand, int speed) {
        this.brand = brand;
        this.speed = speed;
        System.out.println("Vehicle constructor: " + brand);
    }

    void showInfo() {
        System.out.println("Brand: " + brand + " | Speed: " + speed + " km/h");
    }
}

class Car extends Vehicle {
    int doors;

    Car(String brand, int speed, int doors) {
        super(brand, speed);   // MUST be first line — calls Vehicle's constructor
        this.doors = doors;
        System.out.println("Car constructor: " + brand);
    }

    @Override
    void showInfo() {
        super.showInfo();      // calls Vehicle's showInfo()
        System.out.println("Doors: " + doors);
    }
}

public class Main {
    public static void main(String[] args) {
        Car c = new Car("Toyota", 180, 4);
        System.out.println("---");
        c.showInfo();
    }
}
```

**Output:**
```
Vehicle constructor: Toyota
Car constructor: Toyota
---
Brand: Toyota | Speed: 180 km/h
Doors: 4
```

> ⚠️ `super()` must always be the **first statement** in a constructor.

---

## 13. 🔒 `final` Keyword

`final` means **cannot be changed/extended/overridden**.

| Where used | Meaning |
|---|---|
| `final` variable | Value can't be changed (constant) |
| `final` method | Can't be overridden by child |
| `final` class | Can't be extended (no subclass) |

```java
// final class — cannot be extended
final class MathConstants {
    static final double PI = 3.14159;       // constant
    static final double EULER = 2.71828;    // constant
}

class Circle {
    final double radius;   // must be set once, can't change after

    Circle(double radius) {
        this.radius = radius;
    }

    final double area() {   // final method — can't be overridden
        return MathConstants.PI * radius * radius;
    }
}

public class Main {
    public static void main(String[] args) {
        Circle c = new Circle(7);
        System.out.println("Radius: " + c.radius);
        System.out.println("Area: " + c.area());
        System.out.println("PI value: " + MathConstants.PI);

        // c.radius = 10;  ❌ ERROR — final variable can't be changed
        // MathConstants.PI = 3;  ❌ ERROR — final field
    }
}
```

**Output:**
```
Radius: 7.0
Area: 153.93791
PI value: 3.14159
```

---

## 14. 🔑 Access Modifiers

Access modifiers control **who can access** a class, field, or method.

| Modifier | Same Class | Same Package | Subclass (other pkg) | Other Package |
|---|---|---|---|---|
| `private` | ✅ | ❌ | ❌ | ❌ |
| `default` (no keyword) | ✅ | ✅ | ❌ | ❌ |
| `protected` | ✅ | ✅ | ✅ | ❌ |
| `public` | ✅ | ✅ | ✅ | ✅ |

```java
class AccessDemo {
    private   int privateVar   = 10;   // only this class
    int           defaultVar   = 20;   // same package
    protected int protectedVar = 30;   // package + subclasses
    public    int publicVar    = 40;   // everywhere

    void showAll() {
        // All accessible inside the same class
        System.out.println("private:   " + privateVar);
        System.out.println("default:   " + defaultVar);
        System.out.println("protected: " + protectedVar);
        System.out.println("public:    " + publicVar);
    }
}

class Child extends AccessDemo {
    void showAccessible() {
        // privateVar  ❌ not accessible
        System.out.println("default:   " + defaultVar);    // ✅ same package
        System.out.println("protected: " + protectedVar);  // ✅ subclass
        System.out.println("public:    " + publicVar);     // ✅ always
    }
}

public class Main {
    public static void main(String[] args) {
        AccessDemo obj = new AccessDemo();
        System.out.println("--- From same class ---");
        obj.showAll();

        System.out.println("\n--- From subclass ---");
        Child child = new Child();
        child.showAccessible();
    }
}
```

**Output:**
```
--- From same class ---
private:   10
default:   20
protected: 30
public:    40

--- From subclass ---
default:   20
protected: 30
public:    40
```

---

## 15. 🆙 Object Class

Every Java class **automatically extends** `java.lang.Object`.
This means every object has these methods by default:

| Method | Purpose |
|---|---|
| `toString()` | Returns string representation of object |
| `equals()` | Checks logical equality between two objects |
| `hashCode()` | Returns integer hash (used in HashMap, HashSet) |

```java
class Student {
    String name;
    int rollNo;

    Student(String name, int rollNo) {
        this.name = name;
        this.rollNo = rollNo;
    }

    // Without override, prints: Student@hashcode (not useful)
    @Override
    public String toString() {
        return "Student[name=" + name + ", roll=" + rollNo + "]";
    }

    // Without override, checks reference (memory address), not values
    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;                  // same reference
        if (!(obj instanceof Student)) return false;   // type check
        Student other = (Student) obj;
        return this.rollNo == other.rollNo && this.name.equals(other.name);
    }

    // Always override hashCode when you override equals
    @Override
    public int hashCode() {
        return rollNo * 31 + name.hashCode();
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student("Alice", 101);
        Student s2 = new Student("Alice", 101);
        Student s3 = new Student("Bob", 102);

        // toString()
        System.out.println(s1);           // auto-calls toString()
        System.out.println(s2.toString());

        // equals()
        System.out.println("\ns1.equals(s2): " + s1.equals(s2));  // true — same data
        System.out.println("s1.equals(s3): " + s1.equals(s3));  // false — different

        // == checks reference (memory address)
        System.out.println("s1 == s2: " + (s1 == s2));  // false — different objects

        // hashCode()
        System.out.println("\ns1 hashCode: " + s1.hashCode());
        System.out.println("s2 hashCode: " + s2.hashCode());  // same as s1
    }
}
```

**Output:**
```
Student[name=Alice, roll=101]
Student[name=Alice, roll=101]

s1.equals(s2): true
s1.equals(s3): false
s1 == s2: false

s1 hashCode: 63479860
s2 hashCode: 63479860
```

> 💡 Rule: If two objects are `equals()`, they **must** have the same `hashCode()`.

---

## 📋 Quick Summary Table

| # | Concept | Key Point | Keyword |
|---|---|---|---|
| 1 | OOP | Code organized around objects | — |
| 2 | Class & Object | Blueprint & its real instance | `class`, `new` |
| 3 | Methods | Reusable named code blocks | `void`, `return` |
| 4 | Constructors | Auto-called on object creation | same name as class |
| 5 | `this` | Refers to current object | `this` |
| 6 | `static` | Belongs to class, shared by all | `static` |
| 7 | Inheritance | Child reuses parent code | `extends` |
| 8 | Polymorphism | Overload (compile) / Override (runtime) | `@Override` |
| 9 | Encapsulation | Private fields + getters/setters | `private` |
| 10 | Abstraction | Hide details, force implementation | `abstract` |
| 11 | Interface | Contract for multiple inheritance | `interface`, `implements` |
| 12 | `super` | Access parent constructor/method | `super` |
| 13 | `final` | Constant / no override / no extend | `final` |
| 14 | Access Modifiers | Control visibility of members | `private/default/protected/public` |
| 15 | Object Class | Root class with toString/equals/hashCode | `@Override` |

---

## 🧠 Interview Quick-Fire Answers

- **Difference between class and object?** → Class is blueprint, object is instance
- **Overloading vs Overriding?** → Overloading = same name, different params (compile-time). Overriding = child redefines parent method (runtime)
- **Abstract class vs Interface?** → Abstract class can have constructors + concrete methods. Interface is a pure contract, supports multiple inheritance
- **Why encapsulation?** → To protect data from invalid access/modification
- **What does `final` do?** → Prevents change (variable), override (method), or extension (class)
- **What is `super()`?** → Calls parent constructor, must be first line in child constructor
- **Why override `hashCode()` with `equals()`?** → To maintain contract: equal objects must have equal hash codes

---

> 💡 **Tip:** Read concept → trace the code manually → check output → repeat! 🚀
