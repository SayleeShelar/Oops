# Java OOP Concepts - Crystal Clear Interview Revision Guide

Beginner-friendly with **step-by-step breakdowns**, **runnable examples with OUTPUT**, **visual diagrams**, **pitfalls**, and **detailed interview answers**. Revise in 20 mins!

## 1. Classes and Objects

**Definition**: A **class** is a blueprint/template defining data (fields) and behavior (methods). An **object** is a real instance created from the class.

**Why use?** Models real-world entities. Enables code reuse.

**Step-by-step Creation**:
1. Define class with fields/methods.
2. Create object using `new`.

**Syntax**:
```java
// Step 1: Define class
class Car {
    String brand;     // Field (data)
    String color;     // Field
}

// Step 2: Create object
Car myCar = new Car();  // Object
myCar.brand = \"Toyota\";
```

**Full Runnable Example**:
```java
class Car {
    String brand = \"Unknown\";
}

public class Main {
    public static void main(String[] args) {
        Car car1 = new Car();  // Object 1
        car1.brand = \"Toyota\";
        
        Car car2 = new Car();  // Object 2 (independent)
        System.out.println(car1.brand);  // OUTPUT: Toyota
        System.out.println(car2.brand);  // OUTPUT: Unknown
    }
}
```
**Expected Output**:
```
Toyota
Unknown
```

**Visual**:
```
Class Car (Blueprint) ──┐
                        ├── Object car1 (Toyota, Red)
                        └── Object car2 (Unknown, Blue)
```

**Key Points**:
- Objects have **independent state** (fields).
- Memory: Class in method area, Objects in heap.
- Pitfall: Forgetting `new` → compile error.

**Interview Q&A**:
1. **Class vs Object?** Class=design, Object=implementation. Like Car class vs your actual car.
2. **Object lifecycle?** Created (`new`), Used, Garbage collected (no references).

## 2. Methods

**Definition**: Blocks of code inside class to perform actions. Can take inputs (parameters), return output.

**Why?** Encapsulates logic, reusable, organized code.

**Syntax Breakdown**:
- `accessModifier returnType name(params) { body }`
- `void` = no return.

**Full Example**:
```java
class Calculator {
    // Method with return
    int add(int a, int b) {
        return a + b;
    }
    
    // Void method
    void printHello() {
        System.out.println(\"Hello!\");
    }
}

public class Main {
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        int result = calc.add(5, 3);  // Call method
        System.out.println(result);   // OUTPUT: 8
        calc.printHello();            // OUTPUT: Hello!
    }
}
```
**Output**:
```
8
Hello!
```

**Key Points**:
- **Overloading**: Same name, different params (compile-time polymorphism).
  Example: `add(int,int)` and `add(int,int,int)`
- Access: `public` (anywhere), `private` (class only).
- Pitfall: Forgetting `()` when calling method.

**Interview**:
1. **Overloading vs Overriding?** Overloading: same class, param change. Overriding: child class, same signature.
   ```java
   // Overloading example
   void print(int x) { }
   void print(String s) { }
   ```

## 3. Polymorphism

**Definition**: \"Many forms\". Same interface, different implementations.

**Why?** Write code for parent type, run on child objects flexibly.

**Two Types**:

1. **Compile-time (Overloading)**: Method selection at compile.

2. **Runtime (Overriding)**: Method selection at runtime via virtual table.

**Visual Flow**:
```
Client Code ── calls ── Animal.sound()
                    ↓ (Runtime checks type)
                actual: Dog.sound()
```

**Example**:
```java
class Animal {
    void makeSound() { 
        System.out.println(\"Animal sound\");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() { 
        System.out.println(\"Dog barks\");
    }  // Override
}

class Cat extends Animal {
    @Override
    void makeSound() { 
        System.out.println(\"Cat meows\");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal[] animals = {new Dog(), new Cat()};
        for(Animal a : animals) {
            a.makeSound();  
        }
    }
}
```
**Output**:
```
Dog barks
Cat meows
```

**Key Points**:
- Requires **inheritance**.
- `@Override` annotation (good practice).
- Pitfall: Without `virtual` dispatch, no runtime poly.

**Interview**:
1. **Runtime poly mechanism?** Dynamic Method Dispatch (JVM checks actual object type at runtime).

## 4. Constructors

**Definition**: Auto-called method on `new`. Initializes object.

**Why?** Set initial values, validate data.

**Types**:
- Default: no-arg, compiler provides.
- Parameterized: custom.

**Example**:
```java
class Person {
    String name;
    
    // Parameterized constructor
    Person(String n) {
        name = n;  // Or this.name = n;
    }
    
    // Default constructor (compiler adds if none)
    Person() {
        name = \"Unknown\";
    }
}

public class Main {
    public static void main(String[] args) {
        Person p1 = new Person(\"Alice\");  // Calls parameterized
        Person p2 = new Person();           // Calls default
        System.out.println(p1.name);  // Alice
        System.out.println(p2.name);  // Unknown
    }
}
```

**Key Points**:
- No return type.
- Called **only once** per object.
- Chain: `this(args)` or `super(args)` first line.
- Pitfall: No-arg forgotten → compiler error if others present.

**Interview**:
1. **Constructor vs Method?** Constructor: no return, auto-called on new. Method: manual call.

## 5. Static Keyword

**Definition**: Class-level (shared). Not tied to object.

**Why?** Utilities, counters, constants (Math.PI).

**Memory Visual**:
```
Class Area ── static vars/methods (shared)
Heap       ── instance vars (per object)
```

**Example**:
```java
class Student {
    static int totalStudents = 0;  // Shared counter
    
    Student() {
        totalStudents++;  // Increments shared var
    }
    
    static void showCount() {  // No object needed
        System.out.println(\"Total: \" + totalStudents);
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student();
        Student s2 = new Student();
        Student.showCount();  // OUTPUT: Total: 2
    }
}
```

**Key Points**:
- Access: `ClassName.staticMember`
- Can't use `this`/`super`.
- Static init block: `{ static { code; } }`
- Pitfall: Static can't access non-static.

**Interview**:
1. **Static method override?** No (hiding, not overriding).

## 6. This Keyword

**Definition**: Points to **current object** in instance context.

**Uses**:
1. Disambiguate field vs param.
2. Call other constructors (`this()`).
3. Pass/return current object.

**Example**:
```java
class Rectangle {
    int width, height;
    
    // Use 1: Disambiguate
    Rectangle(int width, int height) {
        this.width = width;   // this.field = param
        this.height = height;
    }
    
    // Use 2: Constructor chaining
    Rectangle(int side) {
        this(side, side);     // Calls above
    }
    
    // Use 3: Return this
    Rectangle scale(int factor) {
        this.width *= factor;
        return this;  // Chaining
    }
}
```

**Key Points**:
- Unavailable in static.
- Pitfall: `this` in static → compile error.

**Interview**:
1. **When mandatory?** When param shadows field name.

## 7. Inheritance

**Definition**: Child acquires parent's fields/methods (`extends`).

**Why?** Reuse, hierarchy (is-a: Dog **is-a** Animal).

**Types**:
```
Single: A←B
Multilevel: A←B←C
Hierarchical: A←B, A←C
(No multiple: A←B+C)
```

**Example**:
```java
class Animal {  // Parent
    String name;
    void eat() { System.out.println(name + \" eating\"); }
}

class Dog extends Animal {  // Child
    void bark() { System.out.println(name + \" barks\"); }
    
    Dog(String n) {
        super.name = n;  // super = parent
    }
}

public class Main {
    public static void main(String[] args) {
        Dog d = new Dog(\"Rex\");
        d.eat();  // Inherited  OUTPUT: Rex eating
        d.bark(); // Own       OUTPUT: Rex barks
    }
}
```

**Key Points**:
- `super.method()`, `super()` first in ctor.
- All classes extend `Object`.
- Pitfall: Private members not inherited.

**Interview**:
1. **Java multiple inheritance?** No classes (diamond problem), yes interfaces.

## 8. Encapsulation

**Definition**: Bundle data+methods, hide internals (private + public accessors).

**Why?** Data security, validation, maintainability.

**Example**:
```java
class Account {
    private double balance;  // Hidden
    
    // Public accessors
    public void deposit(double amt) {
        if (amt > 0) balance += amt;  // Validation
    }
    
    public double getBalance() {
        return balance;
    }
}

public class Main {
    public static void main(String[] args) {
        Account acc = new Account();
        acc.deposit(100);
        System.out.println(acc.getBalance());  // 100
        // acc.balance = -50;  ❌ Compile error - safe!
    }
}
```

**Key Points**:
- Principle: Hide details, expose interfaces.
- Pitfall: Public fields break encapsulation.

**Interview**:
1. **How achieved?** Private fields + public getter/setter.

## 9. Abstraction

**Definition**: Show **what** to do, hide **how**.

**Why?** Simplify complexity (user doesn't need internals).

**Visual**:
```
User: Vehicle.start()
Impl: Petrol? Diesel? Electric?  (Hidden)
```

**Tools**: Abstract class (partial), Interface (full).

**Example**:
```java
abstract class Shape {
    // Abstract: child must implement
    abstract double area();
    
    // Concrete
    void display() {
        System.out.println(\"Area: \" + area());
    }
}

class Circle extends Shape {
    double radius;
    Circle(double r) { radius = r; }
    
    double area() { return Math.PI * radius * radius; }
}
```

**Key Points**:
- Forces implementation.
- Pitfall: Forgetting override → runtime error.

**Interview**:
1. **Abstraction vs Encapsulation?** Abstraction: hide complexity. Encapsulation: hide data.

## 10. Abstract Keyword

**Details**: Marks class/method as incomplete.

**Rules**:
```
Abstract class:
- Can't instantiate (new Shape() ❌)
- Can have concrete methods
- Child: extend + override abstracts

Abstract method:
- No body {}
- Child must override
```

**Pitfall**: Abstract method in non-abstract class → error.

**Interview**:
1. **Abstract class constructor?** Yes, called via super().

## 11. Interfaces

**Definition**: Pure contract (methods without body pre-J8). Multiple inheritance.

**Evolution**:
- Pre-J8: Abstract methods + constants.
- J8+: default, static methods.

**Example**:
```java
interface Drawable {
    void draw();  // Must implement
    
    default void msg() {  // J8
        System.out.println(\"Drawing...\");
    }
}

class Rectangle implements Drawable {
    public void draw() {
        System.out.println(\"Rectangle\");
    }
}

public class Main {
    public static void main(String[] args) {
        Drawable d = new Rectangle();
        d.draw();  // Rectangle
        d.msg();   // Drawing...
    }
}
```

**Key Points**:
```
vs Abstract Class:
| Feature          | Interface     | Abstract Class |
|------------------|---------------|----------------|
| Multiple?        | Yes           | No             |
| Constructor?     | No            | Yes            |
| Fields?          | Constants     | Any            |
| Default methods? | Yes           | Yes            |
```

**Interview**:
1. **Diamond problem solution?** Default method overriding priority: class > interface.

---

**Revision Checklist**:
- [ ] Run all examples
- [ ] Memorize tables/differences
- [ ] Explain verbally with diagrams

**Pro Tip**: Concepts interconnect - Inheritance enables Polymorphism!

Clear now? Practice coding! 🚀

