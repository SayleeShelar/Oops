# ⚡ JavaScript - Complete Beginner's Revision Guide

> Master JavaScript for web development from basics to advanced 🎯

---

## 1. 📌 What is JavaScript?

**JavaScript** = Programming language for web browsers

**Key Features:**
- ✅ Makes websites **interactive** (dynamic)
- ✅ Runs in **browser** (client-side) or server (Node.js)
- ✅ Can manipulate HTML/CSS
- ✅ Asynchronous operations (APIs, timers)
- ✅ Event handling

**The Web Trinity:**
| Layer | What | When |
|---|---|---|
| 🏗️ HTML | Structure | Page loads |
| 🎨 CSS | Styling | Applied to HTML |
| ⚡ JavaScript | Behavior | After HTML/CSS |

---

## 2. 💾 Variables & Data Types

### Variable Declaration:

```javascript
// var (old, function-scoped)
var name = "Alice";

// let (block-scoped, preferred)
let age = 25;

// const (constant, block-scoped, preferred)
const PI = 3.14159;

console.log(name);  // Alice
console.log(age);   // 25
```

> ✅ **Use const by default, let if needs to change, avoid var**

### Data Types:

```javascript
// String
let str = "Hello";

// Number
let num = 42;
let decimal = 3.14;

// Boolean
let isStudent = true;
let isEmployed = false;

// Null (intentional empty)
let empty = null;

// Undefined (uninitialized)
let undefined_var;

// Object
let student = {
    name: "Alice",
    age: 25
};

// Array
let numbers = [1, 2, 3, 4];

// Function
function greet() {
    return "Hello";
}

// Symbol (unique)
let id = Symbol("id");

// BigInt (large numbers)
let big = 123456789n;

// Check type
console.log(typeof num);        // number
console.log(typeof str);        // string
console.log(Array.isArray([1])); // true
```

---

## 3. 🔧 Operators

### Arithmetic:

```javascript
let a = 10, b = 3;

console.log(a + b);      // 13
console.log(a - b);      // 7
console.log(a * b);      // 30
console.log(a / b);      // 3.333...
console.log(a % b);      // 1 (remainder)
console.log(a ** 2);     // 100 (power)
console.log(++a);        // 11 (increment)
console.log(--b);        // 2 (decrement)
```

### Comparison:

```javascript
console.log(10 > 5);         // true
console.log(10 == "10");     // true (loose equality)
console.log(10 === "10");    // false (strict equality)
console.log(10 != 5);        // true
console.log(10 !== "10");    // true
console.log(10 >= 5);        // true
```

> ⚠️ **Always use === instead of ==**

### Logical:

```javascript
console.log(true && false);  // false
console.log(true || false);  // true
console.log(!true);          // false

// Real example
if (age >= 18 && salary > 50000) {
    console.log("Can apply for loan");
}
```

### Assignment:

```javascript
let x = 5;
x += 3;     // x = 8
x -= 2;     // x = 6
x *= 2;     // x = 12
x /= 3;     // x = 4
```

---

## 4. 📝 Strings

### Creating & Methods:

```javascript
let str = "Hello World";

// Length
console.log(str.length);            // 11

// Access character
console.log(str[0]);                // H
console.log(str.charAt(0));         // H

// Convert case
console.log(str.toUpperCase());     // HELLO WORLD
console.log(str.toLowerCase());     // hello world

// Find substring
console.log(str.includes("World")); // true
console.log(str.indexOf("World"));  // 6
console.log(str.startsWith("Hello")); // true
console.log(str.endsWith("World")); // true

// Extract substring
console.log(str.substring(0, 5));   // Hello
console.log(str.slice(0, 5));       // Hello
console.log(str.slice(-5));         // World (last 5)

// Replace
console.log(str.replace("World", "JavaScript")); // Hello JavaScript

// Split into array
console.log(str.split(" "));        // ["Hello", "World"]

// Trim whitespace
let spaced = "  Hello  ";
console.log(spaced.trim());         // Hello

// Repeat
console.log("*".repeat(5));         // *****
```

### Template Literals (Backticks):

```javascript
let name = "Alice";
let age = 25;

// Old way
let msg = "Name: " + name + ", Age: " + age;

// Modern way (template literals)
let msg = `Name: ${name}, Age: ${age}`;

console.log(msg);  // Name: Alice, Age: 25

// Multi-line
let bio = `
    Name: ${name}
    Age: ${age}
    Status: Student
`;
```

---

## 5. 📊 Arrays

### Create & Access:

```javascript
let arr = [10, 20, 30, 40, 50];

// Access
console.log(arr[0]);        // 10
console.log(arr[-1]);       // undefined (use arr[arr.length-1])
console.log(arr.length);    // 5

// Create
let empty = [];
let mixed = [1, "hello", true, null];
let nested = [[1, 2], [3, 4]];
```

### Array Methods:

```javascript
let arr = [1, 2, 3];

// Add/Remove
arr.push(4);            // [1, 2, 3, 4] - add to end
arr.pop();              // [1, 2, 3] - remove from end
arr.unshift(0);         // [0, 1, 2, 3] - add to start
arr.shift();            // [1, 2, 3] - remove from start

// Find
console.log(arr.includes(2));       // true
console.log(arr.indexOf(2));        // 1
console.log(arr.find(x => x > 2));  // 3

// Transform
let doubled = arr.map(x => x * 2);  // [2, 4, 6]

// Filter
let even = arr.filter(x => x % 2 === 0); // [2]

// Sum
let sum = arr.reduce((acc, x) => acc + x, 0); // 6

// Sort
arr.sort();             // [1, 2, 3]
arr.sort((a, b) => b - a); // [3, 2, 1] (descending)

// Reverse
arr.reverse();          // Reverse order

// Join
console.log(arr.join(", ")); // "3, 2, 1"

// Slice (copy part)
console.log(arr.slice(1, 3)); // [2, 1]

// Splice (modify array)
arr.splice(1, 1, 99);   // Insert/remove at position
```

---

## 6. 🗂️ Objects

### Create & Access:

```javascript
// Create object
let student = {
    name: "Alice",
    age: 25,
    city: "Delhi",
    gpa: 3.8
};

// Access properties
console.log(student.name);          // Alice
console.log(student["age"]);        // 25

// Add property
student.email = "alice@example.com";

// Remove property
delete student.gpa;

// Check property exists
console.log("name" in student);     // true

// All keys
console.log(Object.keys(student));  // ["name", "age", "city", "email"]

// All values
console.log(Object.values(student)); // ["Alice", 25, "Delhi", ...]

// Key-value pairs
console.log(Object.entries(student));
```

### Methods in Objects:

```javascript
let student = {
    name: "Alice",
    age: 25,
    
    // Method
    introduce: function() {
        return `Hi, I'm ${this.name}`;
    },
    
    // Arrow function (no `this`)
    getAge: () => {
        return this.age;  // Won't work with arrow
    }
};

console.log(student.introduce());   // Hi, I'm Alice
```

---

## 7. 🎯 Functions

### Basic Function:

```javascript
// Declaration
function add(a, b) {
    return a + b;
}

console.log(add(5, 3));     // 8

// Expression
const multiply = function(a, b) {
    return a * b;
};

console.log(multiply(5, 3)); // 15

// Arrow function (modern)
const subtract = (a, b) => {
    return a - b;
};

const subtract = (a, b) => a - b;  // Short form

console.log(subtract(10, 3)); // 7
```

### Default Parameters:

```javascript
function greet(name = "Guest") {
    console.log(`Hello, ${name}`);
}

greet();           // Hello, Guest
greet("Alice");    // Hello, Alice
```

### Rest Parameters:

```javascript
function sum(...numbers) {
    return numbers.reduce((a, b) => a + b, 0);
}

console.log(sum(1, 2, 3, 4));     // 10
```

### Destructuring:

```javascript
// Array destructuring
let [a, b, c] = [1, 2, 3];
console.log(a);  // 1

// Object destructuring
let {name, age} = {name: "Alice", age: 25};
console.log(name);  // Alice
```

---

## 8. ❓ Conditionals

### If-Else:

```javascript
let age = 20;

if (age < 13) {
    console.log("Child");
} else if (age < 18) {
    console.log("Teen");
} else {
    console.log("Adult");
}

// Output: Adult
```

### Switch:

```javascript
let day = 3;

switch(day) {
    case 1:
        console.log("Monday");
        break;
    case 2:
        console.log("Tuesday");
        break;
    case 3:
        console.log("Wednesday");
        break;
    default:
        console.log("Unknown");
}

// Output: Wednesday
```

### Ternary Operator:

```javascript
let status = age >= 18 ? "Adult" : "Minor";
console.log(status);

// Nested
let ticket = age < 5 ? "Free" : age < 65 ? "Adult" : "Senior";
```

---

## 9. 🔁 Loops

### For Loop:

```javascript
for (let i = 0; i < 5; i++) {
    console.log(i);  // 0, 1, 2, 3, 4
}

// For-in (keys)
let obj = {a: 1, b: 2};
for (let key in obj) {
    console.log(key, obj[key]);
}

// For-of (values)
let arr = [10, 20, 30];
for (let val of arr) {
    console.log(val);
}
```

### While Loop:

```javascript
let i = 0;
while (i < 5) {
    console.log(i);
    i++;
}
```

### Array Methods (instead of loops):

```javascript
let arr = [1, 2, 3, 4, 5];

// forEach
arr.forEach(x => console.log(x));

// map
let doubled = arr.map(x => x * 2);

// filter
let even = arr.filter(x => x % 2 === 0);

// reduce
let sum = arr.reduce((acc, x) => acc + x, 0);
```

---

## 10. 🌐 DOM Manipulation

### Select Elements:

```javascript
// Single element
let elem = document.getElementById("myId");
let elem = document.querySelector(".myClass");
let elem = document.querySelector("p");

// Multiple elements
let elems = document.getElementsByClassName("myClass");
let elems = document.querySelectorAll("p");

// By tag
let elems = document.getElementsByTagName("div");
```

### Manipulate Content:

```javascript
let elem = document.getElementById("demo");

// Get/Set text
elem.textContent = "New text";
console.log(elem.textContent);

// Get/Set HTML
elem.innerHTML = "<p>New paragraph</p>";
console.log(elem.innerHTML);

// Get/Set attributes
elem.setAttribute("class", "highlight");
elem.getAttribute("id");
elem.removeAttribute("class");
```

### Manipulate Styles:

```javascript
let elem = document.getElementById("box");

// Direct style
elem.style.color = "red";
elem.style.backgroundColor = "yellow";
elem.style.fontSize = "20px";

// Add/Remove classes
elem.classList.add("active");
elem.classList.remove("inactive");
elem.classList.toggle("hidden");
if (elem.classList.contains("active")) {
    console.log("Active!");
}
```

### Create & Remove Elements:

```javascript
// Create
let newDiv = document.createElement("div");
newDiv.textContent = "New element";
newDiv.className = "box";

// Add to page
let parent = document.getElementById("container");
parent.appendChild(newDiv);

// Insert at specific position
let nextElem = document.getElementById("first");
parent.insertBefore(newDiv, nextElem);

// Remove
newDiv.remove();
parent.removeChild(newDiv);
```

---

## 11. 🎪 Event Handling

### Add Event Listeners:

```javascript
let btn = document.getElementById("myBtn");

// Method 1
btn.addEventListener("click", function() {
    console.log("Button clicked!");
});

// Method 2 (Arrow function)
btn.addEventListener("click", () => {
    console.log("Button clicked!");
});

// Method 3 (HTML attribute - avoid)
// <button onclick="handleClick()">Click</button>
```

### Common Events:

```javascript
// Mouse events
elem.addEventListener("click", (e) => {});  // Click
elem.addEventListener("dblclick", (e) => {}); // Double click
elem.addEventListener("mouseover", (e) => {}); // Hover
elem.addEventListener("mouseout", (e) => {});  // Leave
elem.addEventListener("mousedown", (e) => {}); // Press
elem.addEventListener("mouseup", (e) => {});   // Release

// Keyboard events
elem.addEventListener("keydown", (e) => {
    console.log(e.key);  // Which key pressed
});
elem.addEventListener("keyup", (e) => {});
elem.addEventListener("keypress", (e) => {});

// Form events
form.addEventListener("submit", (e) => {
    e.preventDefault();  // Stop default submit
});
input.addEventListener("change", (e) => {
    console.log(e.target.value);
});
input.addEventListener("input", (e) => {});  // While typing

// Window events
window.addEventListener("load", () => {}); // Page loaded
window.addEventListener("scroll", () => {}); // Scrolling
window.addEventListener("resize", () => {}); // Window resized
```

### Event Object:

```javascript
btn.addEventListener("click", (event) => {
    console.log(event.type);        // "click"
    console.log(event.target);      // The element clicked
    console.log(event.clientX);     // Mouse X position
    console.log(event.clientY);     // Mouse Y position
    
    event.preventDefault();         // Stop default action
    event.stopPropagation();        // Stop bubbling
});
```

---

## 12. ⏰ Asynchronous JavaScript

### Callbacks:

```javascript
function fetchData(callback) {
    setTimeout(() => {
        let data = "Data loaded";
        callback(data);
    }, 1000);
}

fetchData((result) => {
    console.log(result);  // After 1 second: Data loaded
});
```

### Promises:

```javascript
let promise = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("Success!");  // or reject("Error!")
    }, 1000);
});

promise
    .then(result => {
        console.log(result);
    })
    .catch(error => {
        console.log(error);
    })
    .finally(() => {
        console.log("Done");
    });

// Output:
// Success!
// Done
```

### Async/Await (Modern):

```javascript
async function getData() {
    try {
        let response = await fetch("https://api.example.com/data");
        let data = await response.json();
        console.log(data);
    } catch (error) {
        console.log("Error:", error);
    }
}

getData();
```

### Fetch API:

```javascript
// GET
fetch("https://api.example.com/users")
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.log(error));

// POST
fetch("https://api.example.com/users", {
    method: "POST",
    headers: {
        "Content-Type": "application/json"
    },
    body: JSON.stringify({
        name: "Alice",
        email: "alice@example.com"
    })
})
    .then(response => response.json())
    .then(data => console.log(data));

// With async/await
async function getUsers() {
    const response = await fetch("https://api.example.com/users");
    const data = await response.json();
    return data;
}
```

---

## 13. 💾 Local/Session Storage

```javascript
// LocalStorage (persists after browser close)
localStorage.setItem("username", "alice");
console.log(localStorage.getItem("username")); // alice
localStorage.removeItem("username");
localStorage.clear();  // Clear all

// SessionStorage (clears when tab closes)
sessionStorage.setItem("token", "abc123");
console.log(sessionStorage.getItem("token"));

// Check if exists
if (localStorage.getItem("username")) {
    console.log("User already saved");
}

// JSON storage
let user = {name: "Alice", age: 25};
localStorage.setItem("user", JSON.stringify(user));
let loaded = JSON.parse(localStorage.getItem("user"));
```

---

## 14. 📦 Classes & Objects

### ES6 Classes:

```javascript
class Student {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    
    introduce() {
        return `Hi, I'm ${this.name}`;
    }
    
    static isAdult(age) {
        return age >= 18;
    }
}

let s1 = new Student("Alice", 25);
console.log(s1.introduce());         // Hi, I'm Alice
console.log(Student.isAdult(25));    // true
```

### Inheritance:

```javascript
class Animal {
    speak() {
        return "Some sound";
    }
}

class Dog extends Animal {
    speak() {
        return "Woof!";
    }
}

let dog = new Dog();
console.log(dog.speak());  // Woof!
```

---

## 15. 🎁 Higher-Order Functions

Functions that take or return functions:

```javascript
// Takes function as argument
function applyTwice(func, value) {
    return func(func(value));
}

let double = x => x * 2;
console.log(applyTwice(double, 5));  // 20 (5*2*2)

// Returns function
function multiplier(factor) {
    return (x) => x * factor;
}

let double = multiplier(2);
console.log(double(5));  // 10

// Common: map, filter, reduce, addEventListener
```

---

## 16. 📋 Most Important Methods

### String Methods:
```
.charAt() .toUpperCase() .toLowerCase() .substring() .slice()
.indexOf() .includes() .split() .replace() .trim()
```

### Array Methods:
```
.push() .pop() .shift() .unshift() .map() .filter()
.reduce() .find() .sort() .reverse() .join() .includes()
```

### Object Methods:
```
.keys() .values() .entries() .assign() .create()
```

### DOM Methods:
```
document.querySelector() .getElementById() .getElementsByClassName()
.addEventListener() .appendChild() .removeChild() .classList
```

---

## 📋 Quick Summary Table

| # | Concept | Code | Example |
|---|---|---|---|
| 1 | Variable | `let x = 10;` | x = 10 |
| 2 | String | `` `Hello ${name}` `` | Template literal |
| 3 | Array | `[1, 2, 3]` | List |
| 4 | Object | `{name: "Alice"}` | Key-value |
| 5 | Function | `(x) => x * 2` | Arrow function |
| 6 | If-Else | `if (cond) {...}` | Conditional |
| 7 | Loop | `for (let i=0; i<5; i++)` | Iteration |
| 8 | Map | `.map(x => x*2)` | Transform array |
| 9 | Filter | `.filter(x => x>5)` | Select array |
| 10 | Reduce | `.reduce((a,b)=>a+b)` | Aggregate |

---

## 🧠 Placement Interview Questions

1. **What is JavaScript?**
   - Language for interactive web pages, runs in browser

2. **Difference between var, let, const?**
   - var is function-scoped (avoid), let/const are block-scoped

3. **What is hoisting?**
   - Variables/functions moved to top (var/function hoisted, let/const not)

4. **== vs ===?**
   - == loose equality (type coercion), === strict (no coercion)

5. **What is this?**
   - Reference to current object

6. **Arrow function vs regular function?**
   - Arrow functions don't have their own `this`

7. **What is closure?**
   - Function that remembers variables from outer scope

8. **What is event delegation?**
   - Adding event listener to parent instead of many children

9. **What is async/await?**
   - Modern way to handle asynchronous code

10. **What is Promise?**
    - Object representing completion (resolve/reject) of async operation

11. **What is callback?**
    - Function passed to another function

12. **DOM vs BOM?**
    - DOM = Document (page content), BOM = Browser (window, location)

13. **What is JSON?**
    - Data format: `JSON.stringify()`, `JSON.parse()`

14. **What is localStorage?**
    - Browser storage persisting after close

15. **What is spread operator?**
    - `...` to spread array/object elements

---

> 💡 **Tip:** JavaScript = HTML manipulation + Events + Async. Master these three pillars! 🚀
