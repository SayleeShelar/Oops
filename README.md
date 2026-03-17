# OOP in Java - SUPER SIMPLE

Like toys and games. Easy words only.

## 1. Class and Object

**Class** = Recipe for cake.
**Object** = Actual cake you eat.

```
Recipe (Class)
│
└── Cake1 (Object) , Cake2 (Object)
```

**Code**:
```java
class Dog {  // Recipe
    String name = \"Puppy\";
}

Dog myDog = new Dog();  // Make cake
System.out.println(myDog.name);  // Puppy
```

## 2. Methods

**Method** = What dog does. Like \"bark\".

```
Dog ── bark() ── Woof!
```

**Code**:
```java
class Dog {
    void bark() {
        System.out.println(\"Woof!\");
    }
}

Dog d = new Dog();
d.bark();  // Woof!
```

## 3. Polymorphism

**Poly** = Many shapes.

Animal sound() = ?
Dog sound() = Bark
Cat sound() = Meow

One word \"sound\". Different animals different sound.

**Code**:
```java
Animal pet = new Dog();
pet.sound();  // Bark (surprise!)
```

## 4. Constructors

**Constructor** = When you buy new dog, name set kar do.

```java
class Dog {
    String name;
    Dog(String n) {
        name = n;  // Auto when new Dog(\"Tom\")
    }
}
```

## 5. Static

**Static** = Same for all dogs. Like \"total dogs = 5\".

All dogs share one number.

```java
static int totalDogs = 0;
new Dog(); totalDogs ++;  // Shared
```

## 6. This

**This** = Me. Current dog.

```java
Dog(String name) {
    this.name = name;  // My name
}
```

## 7. Inheritance

**Inheritance** = Baby dog gets mama dog's run().

```
Mama Animal ─ run()
              │
           Baby Dog ─ run() + bark()
```

```java
class Dog extends Animal {
}
```

## 8. Encapsulation

**Encapsulation** = Keep money in pocket. Give only through hand.

private money;
public giveMoney()
```

## 9. Abstraction

**Abstraction** = TV remote. Press button. Inside wires hide.

abstract buttonPress();
```

## 10. Abstract

**Abstract** = Recipe without full steps. You fill.

abstract class Shape {
    abstract draw();  // You write
}
```

## 11. Interfaces

**Interface** = Rule book. \"Must fly\". How? You decide.

interface Fly {
    void fly();
}

```
Rule ─ Bird implements ─ fly high!
     ─ Plane implements ─ fly fast!
```

**Practice**: Copy code. Run. See.

Now easy?

