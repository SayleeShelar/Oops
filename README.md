# Java OOP Concepts - Detailed Technical Explanations with Examples

Professional guide with **technical code examples**, **line-by-line breakdowns**, **concept clearing through execution flow**, and **key insights**. Perfect for understanding + interviews.

## 1. Classes and Objects

**Concept**: Class defines structure (fields + methods). Object is runtime instance with memory allocation.

**Why?** Organizes code around entities.

**Detailed Example** (Line-by-line):
```java
// Line 1: Class definition - blueprint
class BankAccount {
    // Line 2: Instance fields - unique per object
    double balance = 0.0;
    String accountNumber;
    
    // Line 3: Method - behavior
    void deposit(double amount) {
        balance += amount;  // Modifies this object's balance
    }
}

public class Main {
    public static void main(String[] args) {
        // Line 4: Object creation - heap allocation
        BankAccount acc1 = new BankAccount();
        acc1.accountNumber = \"ACC001\";
        acc1.deposit(100.0);  // acc1.balance = 100.0
        
        BankAccount acc2 = new BankAccount();  // Separate memory
        acc2.accountNumber = \"ACC002\";
        acc2.deposit(200.0);  // acc2.balance = 200.0
        
        System.out.println(acc1.balance);  // 100.0
        System.out.println(acc2.balance);  // 200.0
    }
}
```

**Execution Flow**:
```
main() starts
new BankAccount() → heap: acc1 {balance=0, accountNumber=null}
deposit(100) → acc1.balance = 100
new BankAccount() → heap: acc2 {balance=0}
deposit(200) → acc2.balance = 200
Print: 100.0, 200.0
```

**Clearing**: Each `new` creates **independent memory**. Fields are **per-object**.

## 2. Methods

**Concept**: Reusable code blocks. Signature = name + params + return type.

**Detailed Example**:
```java
class MathUtils {
    // Method 1: Returns value
    public int multiply(int a, int b) {
        int result = a * b;
        return result;  // Sends back to caller
    }
    
    // Method 2: No return (void), prints
    public void printSum(int x, int y) {
        System.out.println(\"Sum = \" + (x + y));
    }
}

public class Main {
    public static void main(String[] args) {
        MathUtils math = new MathUtils();
        
        int product = math.multiply(4, 5);  // Caller receives 20
        System.out.println(product);  // 20
        
        math.printSum(10, 20);  // Sum = 30 (no return)
    }
}
```

**Flow**:
```
multiply(4,5) called → result=20 → return 20 → product=20
printSum(10,20) called → print \"Sum=30\" → end
```

**Clearing**: Methods **operate on object's state**. Overloading allows flexibility.

## 3. Polymorphism

**Concept**: One interface, multiple implementations. Runtime: JVM picks correct method.

**Detailed Example**:
```java
// Base class
abstract class Shape {
    String color;
    Shape(String c) { color = c; }
    abstract double getArea();  // Polymorphic method
}

// Derived classes
class Circle extends Shape {
    double radius;
    Circle(String c, double r) { 
        super(c); 
        radius = r; 
    }
    double getArea() { 
        return Math.PI * radius * radius; 
    }
}

class Rectangle extends Shape {
    double width, height;
    Rectangle(String c, double w, double h) { 
        super(c); 
        width = w; height = h; 
    }
    double getArea() { 
        return width * height; 
    }
}

public class Main {
    public static void main(String[] args) {
        // Polymorphic array
        Shape[] shapes = {
            new Circle(\"Red\", 5),
            new Rectangle(\"Blue\", 4, 6)
        };
        
        for(Shape s : shapes) {
            System.out.println(s.color + \" area: \" + s.getArea());
        }
    }
}
```

**Output**:
```
Red area: 78.53981633974483
Blue area: 24.0
```

**Flow**:
```
s = Circle obj → getArea() resolves to Circle.getArea() → PI*r*r
s = Rectangle → Rectangle.getArea() → w*h
```

**Clearing**: Reference type `Shape` but **actual object type** decides method (dynamic dispatch).

## 4. Constructors

**Concept**: Initializes object on creation. Chainable.

**Detailed Example**:
```java
class Employee {
    String name;
    int id;
    
    // Constructor 1: Parameterized
    Employee(String n, int i) {
        name = n;
        id = i;
    }
    
    // Constructor 2: Calls Constructor 1 (chaining)
    Employee(String n) {
        this(n, 0);  // Calls above with default id
    }
    
    void display() {
        System.out.println(name + \", ID: \" + id);
    }
}

public class Main {
    public static void main(String[] args) {
        Employee e1 = new Employee(\"John\", 101);  // Constructor 1
        e1.display();  // John, ID: 101
        
        Employee e2 = new Employee(\"Jane\");  // Constructor 2 → chaining
        e2.display();  // Jane, ID: 0
    }
}
```

**Clearing**: `this()` must be **first statement**. Ensures proper init order.

## 5. Static Keyword

**Concept**: Class-level, shared memory, loaded once.

**Detailed Example**:
```java
class Counter {
    static int count = 0;  // Class memory (1 copy)
    
    static {  // Static init block (runs once)
        System.out.println(\"Class loaded\");
    }
    
    Counter() {
        count++;  // All objects share
    }
    
    static void showCount() {
        System.out.println(\"Objects created: \" + count);
    }
}

public class Main {
    public static void main(String[] args) {
        Counter.showCount();  // 0 (static call)
        new Counter();
        new Counter();
        Counter.showCount();  // 2
    }
}
```

**Output**:
```
Class loaded
Objects created: 0
Objects created: 2
```

**Clearing**: Static lives in **method area**. No object needed to access.

## 6. This Keyword

**Concept**: Refers to current instance.

**Detailed Example**:
```java
class Chain {
    int value;
    
    Chain(int v) {
        value = v;
    }
    
    Chain setValue(int v) {
        this.value = v;  // Current object's field
        return this;  // Return current for chaining
    }
    
    Chain doubleIt() {
        this.value *= 2;  // Same
        return this;
    }
}

public class Main {
    public static void main(String[] args) {
        Chain c = new Chain(10)
            .setValue(5)    // this.value=5
            .doubleIt();    // this.value=10
        System.out.println(c.value);  // 10
    }
}
```

**Clearing**: Resolves scope ambiguity + enables **fluent interfaces** (chaining).

## 7. Inheritance

**Concept**: IS-A relationship. Child gets parent's members.

**Detailed Example**:
```java
class Vehicle {  // Superclass
    String brand;
    Vehicle(String b) { brand = b; }
    void start() { System.out.println(brand + \" starts\"); }
}

class Car extends Vehicle {  // Subclass
    int doors;
    Car(String b, int d) {
        super(b);  // Parent constructor
        doors = d;
    }
    void accelerate() { System.out.println(brand + \" accelerates\"); }
}

public class Main {
    public static void main(String[] args) {
        Car myCar = new Car(\"Toyota\", 4);
        myCar.start();      // Inherited  OUTPUT: Toyota starts
        myCar.accelerate(); // Own        OUTPUT: Toyota accelerates
    }
}
```

**Clearing**: `super()` calls **parent constructor first**. Private not inherited.

## 8. Encapsulation

**Concept**: Data hiding + controlled access.

**Detailed Example**:
```java
class Temperature {
    private double celsius;  // Hidden
    
    // Controlled access
    public void setCelsius(double value) {
        if (value >= -273.15) {  // Validation
            celsius = value;
        }
    }
    
    public double getCelsius() {
        return celsius;
    }
    
    public double getFahrenheit() {
        return (celsius * 9/5) + 32;
    }
}

public class Main {
    public static void main(String[] args) {
        Temperature t = new Temperature();
        t.setCelsius(25);  // OK
        System.out.println(t.getFahrenheit());  // 77.0
        // t.celsius = -300;  ❌ Can't - protected!
    }
}
```

**Clearing**: External code **can't corrupt state**. Business logic inside.

## 9. Abstraction

**Concept**: Expose essentials, hide complexity.

**Detailed Example**:
```java
abstract class Database {
    abstract void connect();  // Implement later
    abstract void query(String sql);
    
    // Common code
    void execute(String sql) {
        connect();
        query(sql);
        System.out.println(\"Done\");
    }
}

class MySQL extends Database {
    void connect() {
        System.out.println(\"MySQL connected\");
    }
    void query(String sql) {
        System.out.println(\"Query: \" + sql);
    }
}

public class Main {
    public static void main(String[] args) {
        Database db = new MySQL();
        db.execute(\"SELECT * FROM users\");  
    }
}
```

**Output**:
```
MySQL connected
Query: SELECT * FROM users
Done
```

**Clearing**: Client uses `execute()` - **no database details needed**.

## 10. Abstract Keyword

**Concept Clearing**:
- **Abstract class**: Can't `new`, may have body.
- **Abstract method**: No body `{}` - force override.

**Rules Table**:
|      | Abstract Class | Abstract Method |
|------|----------------|-----------------|
| new? | No             | N/A             |
| Body?| Yes some       | No              |
| Extend? | Must override abstracts | Yes         |

**Pitfall Clearing**: Non-abstract child **must implement all** abstracts.

## 11. Interfaces

**Concept**: Contract for behavior. Multiple OK.

**Detailed Example**:
```java
interface Logger {
    void log(String message);  // Must implement
    
    default void logError(String err) {  // Java 8
        log(\"ERROR: \" + err);
    }
}

interface Printable {
    void print();
}

class ConsoleLogger implements Logger, Printable {
    public void log(String msg) {
        System.out.println(\"LOG: \" + msg);
    }
    
    public void print() {
        log(\"Printing...\");
    }
}

public class Main {
    public static void main(String[] args) {
        Logger logger = new ConsoleLogger();
        logger.log(\"Hello\");     // LOG: Hello
        logger.logError(\"Oops\"); // LOG: ERROR: Oops
        
        Printable p = (ConsoleLogger) logger;
        p.print();  // LOG: Printing...
    }
}
```

**Clearing**: **Multiple contracts** (Logger + Printable). Default methods reduce boilerplate.

---

**Mastery Steps**:
1. Copy-run every example.
2. Change values, see effects.
3. Trace execution mentally.

**Now concepts 100% clear through technical examples!**

