# 🎨 CSS - Complete Beginner's Revision Guide

> Master CSS styling from basics to advanced with examples 🎯

---

## 1. 📌 What is CSS?

**CSS** = Cascading Style Sheets

- Controls **visual styling** of HTML elements
- Makes websites look beautiful and responsive
- Works alongside HTML (structure) and JavaScript (behavior)

**CSS Cascade:**
```
Inline Styles (highest specificity) → ID selectors → Class selectors → Element selectors (lowest specificity)
```

---

## 2. 🔧 CSS Syntax Basics

### Basic Syntax:
```css
selector {
    property: value;
    property: value;
}
```

### Example:
```css
p {
    color: blue;
    font-size: 16px;
}
```

**Output:** All `<p>` tags will be blue with 16px font

---

## 3. 🎯 CSS Selectors

### Element Selector:
```css
/* All paragraphs */
p {
    color: red;
}

/* All divs */
div {
    background-color: yellow;
}
```

### Class Selector:
```css
/* Any element with class="highlight" */
.highlight {
    background-color: yellow;
    font-weight: bold;
}

/* Only paragraphs with class="special" */
p.special {
    color: blue;
}
```

**HTML:**
```html
<p>Normal</p>
<p class="highlight">Highlighted</p>
<p class="special">Special</p>
```

### ID Selector:
```css
/* Element with id="header" */
#header {
    background-color: navy;
    color: white;
}
```

**HTML:**
```html
<div id="header">Main Header</div>
```

> ⚠️ **IDs must be unique** - use only once per page!

### Combination Selectors:

```css
/* Element with class */
div.container { }

/* Multiple classes */
.box.active { }

/* Element with ID */
h1#title { }

/* Multiple selectors (same rules) */
h1, h2, h3 {
    color: navy;
}

/* Descendant (nested) */
div p {
    color: blue;  /* All p inside div */
}

/* Child (direct child only) */
div > p {
    color: green;  /* Only direct p children of div */
}

/* Adjacent sibling */
p + p {
    margin-top: 20px;  /* p after another p */
}

/* Universal selector */
* {
    margin: 0;
    padding: 0;  /* Resets all elements */
}

/* Attribute selector */
input[type="text"] {
    border: 1px solid black;
}

a[href^="https"] {
    color: green;  /* Links starting with https */
}
```

---

## 4. 🎨 Colors

### Color Formats:

```css
/* Named colors */
color: red;
color: blue;
color: white;

/* Hex (6 digits) */
color: #FF0000;      /* Red */
color: #00FF00;      /* Green */
color: #0000FF;      /* Blue */

/* RGB */
color: rgb(255, 0, 0);         /* Red */
color: rgb(0, 255, 0);         /* Green */

/* RGBA (with transparency) */
color: rgba(255, 0, 0, 0.5);   /* Red with 50% transparency */

/* HSL (Hue, Saturation, Lightness) */
color: hsl(0, 100%, 50%);       /* Red */
```

### Properties:

```css
/* Text color */
color: blue;

/* Background color */
background-color: yellow;

/* Border color */
border-color: black;

/* Opacity (0-1) */
opacity: 0.5;  /* 50% transparent */
```

---

## 5. 📏 Box Model

The box model controls spacing around elements:

```
┌─────────────────────────────┐
│         Margin              │
│  ┌─────────────────────┐    │
│  │   Border            │    │
│  │  ┌───────────────┐  │    │
│  │  │  Padding      │  │    │
│  │  │ ┌──────────┐  │  │    │
│  │  │ │ Content  │  │  │    │
│  │  │ └──────────┘  │  │    │
│  │  └───────────────┘  │    │
│  └─────────────────────┘    │
└─────────────────────────────┘
```

### Code:

```css
div {
    /* Content size */
    width: 200px;
    height: 100px;
    
    /* Padding (inside) */
    padding: 20px;              /* All sides */
    padding: 10px 20px;         /* top/bottom 10px, left/right 20px */
    padding: 10px 20px 30px 40px;  /* top, right, bottom, left */
    
    /* Border */
    border: 2px solid black;
    border-radius: 5px;         /* Rounded corners */
    
    /* Margin (outside) */
    margin: 20px;               /* All sides */
    margin: 10px auto;          /* 10px top/bottom, auto left/right (center) */
}
```

### Box Sizing:

```css
/* Include padding/border in width calculation */
box-sizing: border-box;

/* Don't include (default) */
box-sizing: content-box;
```

---

## 6. 🔤 Text & Font

### Font Properties:

```css
p {
    /* Font family */
    font-family: Arial, Helvetica, sans-serif;  /* Fallbacks */
    
    /* Font size */
    font-size: 16px;
    font-size: 1.5em;           /* Relative to parent */
    font-size: 2rem;            /* Relative to root */
    
    /* Font weight (bold) */
    font-weight: normal;        /* 400 */
    font-weight: bold;          /* 700 */
    font-weight: 900;           /* Very bold */
    
    /* Font style */
    font-style: italic;
    font-style: normal;
    
    /* Line height */
    line-height: 1.5;
    line-height: 20px;
    
    /* Text color */
    color: blue;
    
    /* Text alignment */
    text-align: left;
    text-align: center;
    text-align: right;
    text-align: justify;
    
    /* Text decoration */
    text-decoration: underline;
    text-decoration: none;      /* Remove underline from links */
    text-decoration: overline;
    text-decoration: line-through;
    
    /* Text transform */
    text-transform: uppercase;
    text-transform: lowercase;
    text-transform: capitalize;
    
    /* Letter spacing */
    letter-spacing: 2px;
    
    /* Word spacing */
    word-spacing: 5px;
    
    /* Text shadow */
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
}
```

### Google Fonts:

```html
<!-- In head -->
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
```

```css
body {
    font-family: 'Roboto', sans-serif;
}
```

---

## 7. 🎭 Backgrounds

```css
element {
    /* Solid color */
    background-color: blue;
    
    /* Background image */
    background-image: url('image.jpg');
    background-size: cover;        /* Cover entire area */
    background-size: contain;      /* Fit inside */
    background-size: 100px 100px;  /* Specific size */
    
    /* Background position */
    background-position: top left;
    background-position: center;
    background-position: 50% 50%;
    
    /* Background repeat */
    background-repeat: repeat;     /* Tile */
    background-repeat: no-repeat;  /* Don't repeat */
    background-repeat: repeat-x;   /* Repeat horizontally */
    background-repeat: repeat-y;   /* Repeat vertically */
    
    /* Background attachment */
    background-attachment: scroll; /* Scroll with page */
    background-attachment: fixed;  /* Fixed (parallax effect) */
    
    /* Shorthand */
    background: url('image.jpg') no-repeat center / cover;
    
    /* Gradient background */
    background: linear-gradient(to right, red, blue);
    background: radial-gradient(circle, red, blue);
}
```

---

## 8. 📦 Display Property

Controls how element is rendered.

```css
/* Block (full width, new line) */
display: block;
/* <p>, <div>, <h1> - default */

/* Inline (only needed width) */
display: inline;
/* <span>, <a>, <strong> - default */

/* Inline-block (inline + block properties) */
display: inline-block;

/* Flex (powerful layout) */
display: flex;
flex-direction: row;           /* horizontal */
flex-direction: column;        /* vertical */
justify-content: center;       /* Align main axis */
align-items: center;           /* Align cross axis */
gap: 10px;                     /* Space between items */

/* Grid (2D layout) */
display: grid;
grid-template-columns: 1fr 2fr 1fr;
grid-template-rows: auto;
gap: 20px;

/* None (hidden) */
display: none;

/* Visibility (hidden but takes space) */
visibility: hidden;
visibility: visible;
```

---

## 9. 🔲 Flexbox (Important!)

Flexible layout system - great for alignment.

### Basic Flex:

```css
.container {
    display: flex;
    flex-direction: row;        /* horizontal */
    justify-content: center;    /* Align horizontally */
    align-items: center;        /* Align vertically */
    gap: 20px;                  /* Space between items */
}
```

### Justify Content:

```
flex-start  →  items ___________
center      →  ___ items ______
flex-end    →  ___________ items
space-between → item _ item _ item
space-around  → _ item _ item _ item _
```

### Flex Items:

```css
.container > div {
    flex: 1;                    /* Grow equally */
    flex-grow: 2;              /* Grow more */
    flex-shrink: 0;            /* Don't shrink */
    flex-basis: 200px;         /* Base width */
}
```

### Example:

```html
<div class="container">
    <div>Box 1</div>
    <div>Box 2</div>
    <div>Box 3</div>
</div>

<style>
    .container {
        display: flex;
        justify-content: space-between;
        gap: 10px;
    }
</style>
```

**Output:** Three boxes evenly distributed with 10px gap

---

## 10. 📐 Grid (2D Layout)

```css
.grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;    /* 3 equal columns */
    grid-template-columns: 200px 1fr 200px;  /* Fixed + flexible */
    grid-template-rows: 100px 200px;      /* Row heights */
    gap: 20px;                            /* Space between */
}

/* Auto-responsive columns */
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
```

---

## 11. 💫 Positioning

```css
/* Static (default) */
position: static;

/* Relative (relative to normal position) */
position: relative;
top: 20px;          /* Move down 20px */
left: 10px;         /* Move right 10px */

/* Absolute (relative to nearest positioned parent) */
position: absolute;
top: 0;
right: 0;           /* Top-right corner */

/* Fixed (relative to viewport - stays on screen) */
position: fixed;
bottom: 20px;
right: 20px;        /* Bottom-right, stays visible while scrolling */

/* Sticky (fixed when you scroll past it) */
position: sticky;
top: 0;             /* Stick to top when scrolling */

/* Z-index (layering) */
z-index: 10;        /* Higher = on top */
z-index: 1;
```

---

## 12. ⚡ Transitions & Animations

### Transitions:

```css
button {
    background-color: blue;
    transition: background-color 0.3s ease;
    /* Property, Duration, Timing */
}

button:hover {
    background-color: red;
}
/* Change happens smoothly over 0.3 seconds */
```

### Animations:

```css
@keyframes slideIn {
    0% {
        transform: translateX(-100px);
        opacity: 0;
    }
    50% {
        opacity: 0.5;
    }
    100% {
        transform: translateX(0);
        opacity: 1;
    }
}

.box {
    animation: slideIn 1s ease-in-out;
    animation-delay: 0.5s;          /* Start after 0.5s */
    animation-iteration-count: infinite;  /* Repeat forever */
    animation-direction: alternate;  /* Forward then backward */
}
```

### Transforms:

```css
.box {
    transform: translateX(50px);     /* Move right */
    transform: translateY(20px);     /* Move down */
    transform: scale(1.5);           /* Enlarge 1.5x */
    transform: rotate(45deg);        /* Rotate */
    transform: skew(10deg);          /* Skew */
    
    /* Multiple transforms */
    transform: translateX(50px) rotate(45deg) scale(1.2);
}
```

---

## 13. 📱 Responsive Design

### Media Queries:

```css
/* Desktop (default) */
.container {
    width: 1200px;
}

/* Tablets */
@media (max-width: 768px) {
    .container {
        width: 100%;
        padding: 20px;
    }
    
    .sidebar {
        display: none;
    }
}

/* Mobile phones */
@media (max-width: 480px) {
    .container {
        width: 100%;
    }
    
    h1 {
        font-size: 18px;
    }
}

/* Large screens */
@media (min-width: 1400px) {
    .container {
        width: 1400px;
    }
}
```

### Mobile-First Approach:

```css
/* Mobile first (smallest) */
.container {
    width: 100%;
}

/* Tablet and up */
@media (min-width: 768px) {
    .container {
        width: 768px;
    }
}

/* Desktop and up */
@media (min-width: 1024px) {
    .container {
        width: 1024px;
    }
}
```

---

## 14. 🔗 Pseudo-classes & Pseudo-elements

### Pseudo-classes:

```css
/* Link states */
a:link { }           /* Unvisited */
a:visited { }        /* Visited */
a:hover { }          /* Mouse over */
a:active { }         /* Being clicked */
a:focus { }          /* Keyboard focus */

/* Element states */
input:checked { }    /* Checked checkbox */
input:disabled { }   /* Disabled */
input:focus { }      /* Has focus */

/* Position-based */
li:first-child { }   /* First item */
li:last-child { }    /* Last item */
li:nth-child(2) { }  /* 2nd item */
li:nth-child(odd) { }  /* Odd items */
li:nth-child(even) { } /* Even items */

/* Content-based */
p:empty { }          /* Empty paragraphs */
div:not(.special) { } /* Everything except .special */
```

### Pseudo-elements:

```css
/* Before element */
p::before {
    content: "Note: ";
    color: red;
}
/* Output: Note: [paragraph content] */

/* After element */
p::after {
    content: " ✓";
}

/* First letter */
p::first-letter {
    font-size: 2em;
    font-weight: bold;
}

/* First line */
p::first-line {
    color: blue;
}

/* Selection highlight */
p::selection {
    background-color: yellow;
}
```

---

## 15. 🛡️ Shadows & Effects

```css
/* Text shadow */
h1 {
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
    /* offset-x, offset-y, blur-radius, color */
}

/* Box shadow */
.box {
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    box-shadow: 0 0 0 5px rgba(0, 0, 255, 0.5);  /* Glow */
    box-shadow: 5px 5px 15px rgba(0, 0, 0, 0.3), -5px -5px 15px rgba(255, 255, 255, 0.5);  /* Multiple */
}

/* Filter effects */
.image {
    filter: blur(5px);
    filter: brightness(1.2);
    filter: contrast(1.5);
    filter: grayscale(100%);
    filter: sepia(100%);
    filter: invert(100%);
    filter: hue-rotate(90deg);
    filter: saturate(2);
    filter: drop-shadow(5px 5px 10px rgba(0, 0, 0, 0.5));
}
```

---

## 16. 📋 Common Properties Table

| Property | Values | Use |
|---|---|---|
| `display` | block, inline, flex, grid, none | Layout |
| `position` | static, relative, absolute, fixed | Positioning |
| `width` | 200px, 50%, auto | Width |
| `height` | 100px, 50%, auto | Height |
| `color` | red, #FF0000, rgb(255,0,0) | Text color |
| `background-color` |  Any color | Background |
| `font-size` | 16px, 1.5em, 2rem | Font size |
| `font-weight` | normal, bold, 700 | Boldness |
| `border` | 2px solid black | Border |
| `padding` | 20px, 10px 20px | Inside space |
| `margin` | 20px, 10px auto | Outside space |
| `text-align` | left, center, right | Text alignment |
| `justify-content` | center, space-between | Flex alignment |
| `align-items` | center, flex-start | Flex alignment |
| `opacity` | 0-1 | Transparency |

---

## 17. 🎯 Best Practices

### 1. Use meaningful class names:
```css
/* Good */
.btn-primary { }
.user-profile { }

/* Bad */
.red { }
.box1 { }
```

### 2. Avoid inline styles:
```html
<!-- Bad -->
<p style="color: blue; font-size: 16px;">Text</p>

<!-- Good -->
<p class="paragraph">Text</p>
```

### 3. Use shorthand:
```css
/* Good */
padding: 10px 20px;
margin: 10px;

/* Less efficient */
padding-top: 10px;
padding-right: 20px;
padding-bottom: 10px;
padding-left: 20px;
```

### 4. Mobile-first approach:
```css
/* Mobile default */
.container {
    width: 100%;
}

/* Larger screens */
@media (min-width: 768px) {
    .container {
        width: 768px;
    }
}
```

### 5. Reset default styles:
```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```

---

## 📋 Quick Reference

| Task | Code |
|---|---|
| Center flex items | `display: flex; justify-content: center; align-items: center;` |
| Full width/height | `width: 100%; height: 100%;` |
| Center horizontally | `margin: 0 auto;` |
| Responsive image | `max-width: 100%; height: auto;` |
| Hide element | `display: none;` or `visibility: hidden;` |
| Rounded corners | `border-radius: 5px;` |
| Box shadow | `box-shadow: 0 2px 10px rgba(0,0,0,0.1);` |
| Hover effect | `.btn:hover { background-color: red; }` |
| Smooth transition | `transition: all 0.3s ease;` |
| Responsive text | `font-size: clamp(16px, 5vw, 32px);` |

---

## 🧠 Placement Interview Questions

1. **What is CSS?**
   - Cascading Style Sheets for styling HTML elements

2. **Difference between class and ID?**
   - ID is unique (use once), class can repeat (use many times)

3. **What's the CSS box model?**
   - Content → Padding → Border → Margin

4. **Explain CSS specificity**
   - Inline > ID > Class > Element

5. **What is Flexbox?**
   - Layout system for flexible 1D alignment

6. **What is CSS Grid?**
   - Layout system for 2D layouts (rows & columns)

7. **How to make a responsive website?**
   - Use media queries, flexible units, mobile-first

8. **What are pseudo-classes?**
   - :hover, :active, :focus - state-based selectors

9. **What are pseudo-elements?**
   - ::before, ::after, ::first-letter - add virtual elements

10. **How to center content?**
    - Flexbox: justify-content center + align-items center
    - Or: margin: auto

11. **What's the difference between margin and padding?**
    - Margin is outside, padding is inside

12. **How to make images responsive?**
    - `max-width: 100%; height: auto;`

13. **What are media queries?**
    - CSS rules that apply at specific screen sizes

14. **How to create animations?**
    - @keyframes + animation property

15. **What's the difference between position absolute and fixed?**
    - Absolute: relative to parent, Fixed: stays on screen always

---

> 💡 **Tip:** Practice building layouts with Flexbox + Grid → Add animations → Make responsive → Master CSS! 🚀
