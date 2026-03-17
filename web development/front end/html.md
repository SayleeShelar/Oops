# 🌐 HTML - Complete Beginner's Revision Guide

> Master HTML from basics to advanced with detailed explanations + full code + output 🎯

---

## 1. 📌 What is HTML?

**HTML** = HyperText Markup Language

- A **markup language** (not programming)
- Used to create **structure** of web pages
- Uses **tags** to define what content is
- Works with CSS (styling) and JavaScript (behavior)

**The Trinity of Web:**
| Layer | Purpose | Example |
|---|---|---|
| 🏗️ **HTML** | Structure (skeleton) | `<h1>`, `<p>`, `<div>` |
| 🎨 **CSS** | Styling (clothes) | colors, fonts, layout |
| ⚙️ **JavaScript** | Behavior (movement) | clicks, animations |

---

## 2. 🔧 HTML Basics

### HTML Document Structure:

Every HTML document should have this basic structure:

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Page Title</title>
    </head>
    <body>
        <h1>Hello World!</h1>
    </body>
</html>
```

**Explanation:**
- `<!DOCTYPE html>` → Tells browser this is HTML5 (required, goes first)
- `<html>` → Root element, wraps entire page
- `<head>` → Contains metadata, title, links to CSS/JavaScript (not visible on page)
- `<title>` → Text shown in browser tab
- `<body>` → Contains all visible content

**Output in Browser:**
```
[Page Title ← shown in tab]

Hello World!
```

---

## 3. 📝 Headings and Text

### Headings:
```html
<h1>Heading 1 (largest)</h1>
<h2>Heading 2</h2>
<h3>Heading 3</h3>
<h4>Heading 4</h4>
<h5>Heading 5</h5>
<h6>Heading 6 (smallest)</h6>
```

**Output:**
```
Heading 1 (largest)        ← biggest
Heading 2
Heading 3
Heading 4
Heading 5
Heading 6 (smallest)       ← smallest
```

> ⚠️ Use `<h1>` only ONCE per page (for SEO — helps search engines understand main topic)

### Paragraphs:
```html
<p>This is a paragraph.</p>
<p>This is another paragraph.</p>
```

**Output:**
```
This is a paragraph.

This is another paragraph.
```

### Text Formatting:
```html
<p>
    <strong>Bold text</strong> (importance) vs
    <b>Bold text</b> (styling only)
</p>

<p>
    <em>Italic text</em> (emphasis) vs
    <i>Italic text</i> (styling only)
</p>

<p>
    <mark>Highlighted text</mark>
</p>

<p>
    <del>Deleted text</del> (shows strikethrough)
</p>

<p>
    <ins>Inserted text</ins> (shows underline)
</p>

<p>
    <sub>Subscript text</sub> (for H<sub>2</sub>O)
</p>

<p>
    <sup>Superscript text</sup> (for x<sup>2</sup>)
</p>
```

**Output:**
```
**Bold text** (importance) vs Bold text (styling only)

_Italic text_ (emphasis) vs Italic text (styling only)

Highlighted text (appears with yellow background)

Deleted text (shows strikethrough)

Inserted text (shows underline)

Subscript text (for H₂O)

Superscript text (for x²)
```

---

## 4. 🔗 Links

### Basic Link:
```html
<a href="https://www.example.com">Click here</a>
```

**Output:**
```
Click here  ← clickable, blue, underlined
```

### Link Types:

| Type | Syntax | Purpose |
|---|---|---|
| External | `<a href="https://...">` | Link to other websites |
| Internal | `<a href="page.html">` | Link to pages in same website |
| Anchor | `<a href="#section1">` | Jump to section within page |
| Email | `<a href="mailto:abc@example.com">` | Create email link |
| Phone | `<a href="tel:+919876543210">` | Create phone link |

```html
<!-- External link -->
<a href="https://www.google.com">Visit Google</a>

<!-- Open in new tab -->
<a href="https://www.google.com" target="_blank">Visit Google (new tab)</a>

<!-- Internal link -->
<a href="about.html">About Us</a>

<!-- Jump to section with ID -->
<a href="#contact-section">Go to Contact</a>

<!-- Email link -->
<a href="mailto:john@example.com">Email John</a>

<!-- Phone link -->
<a href="tel:+919876543210">Call me</a>

<!-- Download a file -->
<a href="resume.pdf" download>Download Resume</a>
```

### Anchor Link Example:
```html
<!-- Navigation link -->
<a href="#section-1">Jump to Section 1</a>

<!-- Later in page -->
<h2 id="section-1">Section 1</h2>
<p>This is section 1 content.</p>
```

---

## 5. 🖼️ Images

### Basic Image:
```html
<img src="image.jpg" alt="Description of image">
```

**Attributes:**
- `src` → Path to image file (required)
- `alt` → Text if image doesn't load / for screen readers (required)
- `width` → Width in pixels
- `height` → Height in pixels
- `title` → Tooltip text on hover

```html
<!-- Basic image -->
<img src="photo.jpg" alt="A beautiful landscape">

<!-- Image with size -->
<img src="photo.jpg" alt="Landscape" width="300" height="200">

<!-- Image with title (tooltip) -->
<img src="photo.jpg" alt="Landscape" title="click to see full size">

<!-- Image as link -->
<a href="https://example.com">
    <img src="logo.png" alt="Company Logo">
</a>
```

**Image Paths:**
```html
<!-- Same folder -->
<img src="image.jpg" alt="">

<!-- Subfolder -->
<img src="images/photo.jpg" alt="">

<!-- Parent folder -->
<img src="../image.jpg" alt="">

<!-- From internet -->
<img src="https://example.com/image.jpg" alt="">
```

---

## 6. 📋 Lists

### Unordered List (bullets):
```html
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```

**Output:**
```
• Item 1
• Item 2
• Item 3
```

### Ordered List (numbered):
```html
<ol>
    <li>First step</li>
    <li>Second step</li>
    <li>Third step</li>
</ol>
```

**Output:**
```
1. First step
2. Second step
3. Third step
```

### Nested List:
```html
<ul>
    <li>Languages
        <ul>
            <li>Python</li>
            <li>Java</li>
        </ul>
    </li>
    <li>Frameworks
        <ol>
            <li>React</li>
            <li>Angular</li>
        </ol>
    </li>
</ul>
```

**Output:**
```
• Languages
  • Python
  • Java
• Frameworks
  1. React
  2. Angular
```

### Description List:
```html
<dl>
    <dt>HTML</dt>
    <dd>HyperText Markup Language - creates webpage structure</dd>
    
    <dt>CSS</dt>
    <dd>Cascading Style Sheets - styles web pages</dd>
</dl>
```

**Output:**
```
HTML
    HyperText Markup Language - creates webpage structure

CSS
    Cascading Style Sheets - styles web pages
```

---

## 7. 📊 Tables

### Basic Table:
```html
<table>
    <tr>
        <th>Header 1</th>
        <th>Header 2</th>
        <th>Header 3</th>
    </tr>
    <tr>
        <td>Data 1</td>
        <td>Data 2</td>
        <td>Data 3</td>
    </tr>
    <tr>
        <td>Data 4</td>
        <td>Data 5</td>
        <td>Data 6</td>
    </tr>
</table>
```

**Output:**
```
| Header 1 | Header 2 | Header 3 |
|----------|----------|----------|
| Data 1   | Data 2   | Data 3   |
| Data 4   | Data 5   | Data 6   |
```

**Tags:**
- `<table>` → Defines table
- `<tr>` → Table row
- `<th>` → Table header (bold, centered)
- `<td>` → Table data (cell)

### Table with Structure:
```html
<table border="1">
    <thead>
        <tr>
            <th>Name</th>
            <th>Age</th>
            <th>City</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Alice</td>
            <td>25</td>
            <td>Delhi</td>
        </tr>
        <tr>
            <td>Bob</td>
            <td>30</td>
            <td>Mumbai</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td colspan="3">Total: 2 employees</td>
        </tr>
    </tfoot>
</table>
```

**Tags:**
- `<thead>` → Header rows
- `<tbody>` → Body rows
- `<tfoot>` → Footer rows (like subtotals)

### Table with Colspan & Rowspan:
```html
<table border="1">
    <tr>
        <th colspan="2">Name</th>
        <th>Score</th>
    </tr>
    <tr>
        <td>Alice</td>
        <td>First</td>
        <td>95</td>
    </tr>
</table>
```

**Output:**
```
|   Name    | Score |
|-----------|-------|
| Alice | First | 95  |
```

- `colspan="2"` → Spans 2 columns
- `rowspan="2"` → Spans 2 rows

---

## 8. 📝 Forms

Forms collect user input.

### Basic Form:
```html
<form action="submit.php" method="POST">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name">
    
    <label for="email">Email:</label>
    <input type="email" id="email" name="email">
    
    <button type="submit">Send</button>
</form>
```

**Output:** (in browser)
```
Name:  [________________]

Email: [________________]

       [Send]
```

**Attributes:**
- `action` → Where to send form data
- `method` → POST (secure, data in body) or GET (visible in URL)

### Input Types:

| Type | Syntax | Purpose |
|---|---|---|
| Text | `<input type="text">` | Single line text |
| Email | `<input type="email">` | Email validation |
| Password | `<input type="password">` | Hides typed text |
| Number | `<input type="number">` | Only numbers |
| Date | `<input type="date">` | Date picker |
| Time | `<input type="time">` | Time picker |
| Checkbox | `<input type="checkbox">` | Multiple selections |
| Radio | `<input type="radio">` | Single selection |
| Submit | `<input type="submit">` | Submit button |
| Reset | `<input type="reset">` | Clear form |
| Hidden | `<input type="hidden">` | Not visible to user |

```html
<form>
    <!-- Text input -->
    <input type="text" placeholder="Enter name">
    
    <!-- Email input -->
    <input type="email" placeholder="your@email.com">
    
    <!-- Password input -->
    <input type="password" placeholder="Enter password">
    
    <!-- Number input -->
    <input type="number" min="1" max="100">
    
    <!-- Date input -->
    <input type="date">
    
    <!-- Time input -->
    <input type="time">
    
    <!-- Checkbox -->
    <input type="checkbox" id="agree"> 
    <label for="agree">I agree to terms</label>
    
    <!-- Radio buttons -->
    <input type="radio" name="gender" value="male"> Male
    <input type="radio" name="gender" value="female"> Female
    
    <!-- Dropdown -->
    <select name="country">
        <option value="">Select Country</option>
        <option value="india">India</option>
        <option value="usa">USA</option>
    </select>
    
    <!-- Textarea (multi-line) -->
    <textarea rows="4" cols="40" placeholder="Type message"></textarea>
    
    <!-- Buttons -->
    <button type="submit">Submit</button>
    <button type="reset">Clear</button>
</form>
```

### Form Elements:

**Label:** Connects text with input (improves usability)
```html
<label for="username">Username:</label>
<input type="text" id="username" name="username">
```

**Fieldset & Legend:** Groups related inputs
```html
<fieldset>
    <legend>Personal Information</legend>
    <input type="text" placeholder="First Name">
    <input type="text" placeholder="Last Name">
</fieldset>
```

**Output:**
```
┌─ Personal Information ─┐
│ [First Name ________]  │
│ [Last Name  ________]  │
└────────────────────────┘
```

---

## 9. 🎨 Semantic HTML

**Semantic HTML** uses tags that describe the **meaning** of content.

### Non-Semantic (Old way):
```html
<div>
    <div>
        <h1>Article Title</h1>
        <p>Article content...</p>
    </div>
</div>
```

Divs don't tell what the content IS → bad for SEO & accessibility.

### Semantic (Modern way):
```html
<article>
    <header>
        <h1>Article Title</h1>
    </header>
    <main>
        <p>Article content...</p>
    </main>
    <footer>
        <p>Published by John</p>
    </footer>
</article>
```

Semantic tags clearly show meaning → good for SEO, accessibility, readability.

### Common Semantic Tags:

```html
<header>        <!-- Top section (logo, title, navigation) -->
<nav>           <!-- Navigation links -->
<main>          <!-- Main content (unique per page) -->
<article>       <!-- Independent article/blog post -->
<section>       <!-- Grouping related content -->
<aside>         <!-- Sidebar, related info -->
<footer>        <!-- Bottom section (copyright, links) -->
<figure>        <!-- Image with caption -->
<figcaption>    <!-- Caption for <figure> -->
<time>          <!-- Dates and times -->
```

### Complete Semantic Page Example:
```html
<!DOCTYPE html>
<html>
<head>
    <title>My Blog</title>
</head>
<body>
    <header>
        <h1>My Awesome Blog</h1>
        <nav>
            <a href="/">Home</a>
            <a href="/about">About</a>
            <a href="/contact">Contact</a>
        </nav>
    </header>

    <main>
        <article>
            <h2>First Post</h2>
            <time datetime="2024-01-15">January 15, 2024</time>
            <p>This is my first blog post...</p>
        </article>

        <article>
            <h2>Second Post</h2>
            <time datetime="2024-01-20">January 20, 2024</time>
            <p>This is my second blog post...</p>
        </article>
    </main>

    <aside>
        <h3>Related Articles</h3>
        <ul>
            <li><a href="#">Old Post 1</a></li>
            <li><a href="#">Old Post 2</a></li>
        </ul>
    </aside>

    <footer>
        <p>&copy; 2024 My Blog. All rights reserved.</p>
    </footer>
</body>
</html>
```

---

## 10. 🔤 Special Characters & Symbols

### HTML Entities:
```html
<p>&lt;p&gt;</p>           <!-- < and > symbols -->
<p>&amp; means AND</p>    <!-- & symbol -->
<p>&quot;Quoted text&quot;</p>  <!-- " quotes -->
<p>&copy; 2024</p>        <!-- © copyright -->
<p>&reg; Trademark</p>    <!-- ® -->
<p>&nbsp;&nbsp;&nbsp;</p> <!-- Non-breaking spaces -->
<p>&euro; 100</p>         <!-- € -->
<p>&hearts; &clubs;</p>   <!-- ♥ ♣ -->
```

**Output:**
```
<p>

& means AND

"Quoted text"

© 2024

® Trademark

   (spaces)

€ 100

♥ ♣
```

### Common Entities:
| Symbol | Code | Symbol | Code |
|---|---|---|---|
| `<` | `&lt;` | `>` | `&gt;` |
| `&` | `&amp;` | `"` | `&quot;` |
| `©` | `&copy;` | `™` | `&trade;` |
| `€` | `&euro;` | `¥` | `&yen;` |

---

## 11. 📄 Meta Tags

Meta tags provide **metadata** about the page (not visible on page).

```html
<head>
    <!-- Character encoding (UTF-8 for all languages) -->
    <meta charset="UTF-8">
    
    <!-- Responsive design (scales for mobile) -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <!-- Description for search engines -->
    <meta name="description" content="Learn HTML from basics to advanced">
    
    <!-- Keywords for search engines -->
    <meta name="keywords" content="HTML, web development, tutorial">
    
    <!-- Author of page -->
    <meta name="author" content="John Doe">
    
    <!-- Refresh page every 30 seconds -->
    <meta http-equiv="refresh" content="30">
    
    <!-- Search engine crawling -->
    <meta name="robots" content="index, follow">
</head>
```

**Why important?**
- `charset` → Ensures correct text display
- `viewport` → Makes page mobile-friendly
- `description` → What appears in Google search results
- `keywords` → SEO optimization

---

## 12. 🔗 External Resources

### CSS Stylesheet:
```html
<head>
    <link rel="stylesheet" href="styles.css">
</head>
```

### JavaScript File:
```html
<body>
    <!-- ... content ... -->
    <script src="script.js"></script>  <!-- at end of body -->
</body>
```

### Favicon (page icon):
```html
<head>
    <link rel="icon" href="favicon.ico">
</head>
```

### Google Fonts:
```html
<head>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
</head>
```

### Bootstrap (CSS framework):
```html
<head>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
```

---

## 13. 📦 Block vs Inline Elements

### Block Elements:
- Take up **full width** (start newline)
- Respect margin, padding

```html
<div>This is a div (block)</div>
<div>Next div starts on new line</div>
```

**Output:**
```
This is a div (block)
Next div starts on new line
```

**Common block elements:**
`<div>`, `<p>`, `<h1>-<h6>`, `<ul>`, `<ol>`, `<section>`, `<header>`, `<footer>`

### Inline Elements:
- Only take needed **width** (no newline)
- Ignore top/bottom margin

```html
<span>This is inline</span>
<span>stays on same line</span>
```

**Output:**
```
This is inline stays on same line
```

**Common inline elements:**
`<span>`, `<a>`, `<strong>`, `<em>`, `<img>`, `<button>`

### Inline-Block:
- Acts like **inline** but respects **block** properties
- CSS: `display: inline-block;`

---

## 14. 📌 Divs and Spans

### Div (Block):
```html
<div class="container">
    <h2>Section</h2>
    <p>Content goes here</p>
</div>
```

Used to **group block content** together for styling.

### Span (Inline):
```html
<p>This is <span class="highlight">important</span> text</p>
```

Used to **style parts of text** without breaking line.

---

## 15. 🔍 Attributes

**Attributes** provide additional info about elements.

```html
<!-- id: unique identifier for one element -->
<div id="main-content">Content</div>

<!-- class: groups multiple elements for styling -->
<button class="btn btn-primary">Click me</button>

<!-- title: tooltip on hover -->
<img src="photo.jpg" title="Click to enlarge">

<!-- data-*: custom attributes for JavaScript -->
<div data-user-id="123" data-role="admin">User</div>

<!-- disabled: disables form element -->
<button disabled>Disabled Button</button>

<!-- required: makes form field mandatory -->
<input type="email" required>

<!-- readonly: can't edit -->
<input type="text" value="Can't change" readonly>

<!-- maxlength: limits characters -->
<input type="text" maxlength="10">

<!-- multiple: allow multiple selections -->
<input type="file" multiple>
```

---

## 16. 📍 Comments

HTML comments are **not visible** on page.

```html
<!-- This is a comment -->

<!-- 
    Multi-line comment
    Useful for documenting code
    Or disabling code temporarily
-->

<p>This is visible</p>
<!-- <p>This is hidden</p> -->
```

---

## 17. 🎯 Document Type & Language

### DOCTYPE:
```html
<!DOCTYPE html>  <!-- Must be first line -->
```

Tells browser this is HTML5.

### Language:
```html
<html lang="en">              <!-- English -->
<html lang="es">              <!-- Spanish -->
<html lang="hi">              <!-- Hindi -->
```

Helps with:
- Spell check
- Google translate
- Screen readers (pronunciation)

---

## 18. 📱 Responsive Design Basics

### Viewport Meta Tag:
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

**Without this:**
- Mobile phones show zoomed-out desktop version
- Very hard to read

**With this:**
- Scales properly on mobile
- Readable on all screen sizes

### Image Responsiveness:
```html
<!-- Image won't overflow -->
<img src="photo.jpg" alt="" style="max-width: 100%; height: auto;">

<!-- Or in CSS: img { max-width: 100%; height: auto; } -->
```

---

## 19. 💾 Accessibility (A11y)

Making websites usable for **everyone**, including people with disabilities.

### Key Practices:

**1. Alt text for images:**
```html
<!-- Good -->
<img src="logo.png" alt="Apple inc. logo">

<!-- Bad -->
<img src="logo.png" alt="image">
```

**2. Semantic HTML:**
```html
<!-- Good - tags show meaning -->
<header><h1>Title</h1></header>

<!-- Bad - no meaning -->
<div><div>Title</div></div>
```

**3. Proper heading hierarchy:**
```html
<!-- Good -->
<h1>Main Title</h1>
<h2>Subtitle</h2>
<h3>Sub-section</h3>

<!-- Bad -->
<h1>Main Title</h1>
<h4>Jumps levels</h4>
```

**4. Form labels:**
```html
<!-- Good - label connected to input -->
<label for="email">Email:</label>
<input id="email" type="email">

<!-- Bad - no connection -->
Email: <input type="email">
```

**5. Link text clarity:**
```html
<!-- Good - clear what link is -->
<a href="about.html">Learn about us</a>

<!-- Bad - "click here" not descriptive -->
<a href="about.html">Click here</a>
```

**6. ARIA attributes:**
```html
<!-- When semantic HTML not possible -->
<div role="button" aria-label="Close menu">✕</div>

<!-- aria-live: announce changes to screen readers -->
<div aria-live="polite">Updated content</div>
```

---

## 20. 🛡️ Best Practices

### 1. Always include DOCTYPE and html lang:
```html
<!DOCTYPE html>
<html lang="en">
```

### 2. Always include meta tags:
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Page Title</title>
</head>
```

### 3. Use semantic HTML:
```html
<!-- Good -->
<header>...</header>
<main>...</main>
<footer>...</footer>

<!-- Instead of -->
<div class="header">...</div>
<div class="main">...</div>
<div class="footer">...</div>
```

### 4. Keep IDs unique:
```html
<!-- Good -->
<input id="email-field" type="email">

<!-- Bad -->
<input id="field" type="email">
<input id="field" type="text">  <!-- Duplicate ID -->
```

### 5. Close all tags properly:
```html
<!-- Good -->
<img src="photo.jpg" alt="">
<br>

<!-- Bad -->
<img src="photo.jpg">
<br>
```

### 6. Use meaningful class names:
```html
<!-- Good -->
<div class="user-profile"></div>
<button class="btn-submit"></button>

<!-- Bad -->
<div class="red"></div>
<button class="btn1"></button>
```

### 7. Write comments for complex sections:
```html
<!-- User registration form -->
<form>
    <input type="email" placeholder="Email">
    <input type="password" placeholder="Password">
</form>
```

### 8. Validate your HTML:
Use online validator: https://validator.w3.org/

---

## 📋 Quick Reference Table

| Element | Purpose | Example |
|---|---|---|
| `<a>` | Link | `<a href="page.html">Link</a>` |
| `<img>` | Image | `<img src="pic.jpg" alt="">` |
| `<p>` | Paragraph | `<p>Text</p>` |
| `<h1>-<h6>` | Headings | `<h1>Title</h1>` |
| `<div>` | Container (block) | `<div>...</div>` |
| `<span>` | Container (inline) | `<span>...</span>` |
| `<ul>` | Unordered list | `<ul><li>Item</li></ul>` |
| `<ol>` | Ordered list | `<ol><li>1st</li></ol>` |
| `<table>` | Table | `<table><tr><td>Cell</td></tr></table>` |
| `<form>` | Form | `<form action="url"></form>` |
| `<input>` | Form input | `<input type="text">` |
| `<button>` | Button | `<button>Click</button>` |
| `<header>` | Top section | `<header>...</header>` |
| `<footer>` | Bottom section | `<footer>...</footer>` |
| `<nav>` | Navigation | `<nav>...</nav>` |
| `<main>` | Main content | `<main>...</main>` |

---

## 🧠 Interview Quick-Fire Answers

- **What is HTML?** → Markup language used to create web page structure
- **What does DOCTYPE do?** → Tells browser to use HTML5 standards
- **Why use semantic HTML?** → Better for SEO, accessibility, and code readability
- **Difference between id and class?** → id is unique (one per page), class can repeat (many per page)
- **What's the purpose of alt text?** → Displays if image doesn't load, helps screen readers understand image
- **When to use div vs span?** → div for block content, span for inline text
- **What are HTTP methods in forms?** → GET (visible in URL, limited data) and POST (secure, more data)
- **What are meta tags for?** → Provide metadata like charset, viewport, description for search engines
- **How to make website mobile-friendly?** → Use viewport meta tag and responsive CSS
- **What is accessibility?** → Making websites usable for everyone including people with disabilities

---

## 🎯 Placement Interview Questions

### Common Questions:

1. **Explain the basic structure of an HTML document**
   - Answer: DOCTYPE, `<html>`, `<head>`, `<body>`

2. **What's the difference between `<strong>` and `<b>` tags?**
   - Answer: `<strong>` implies importance (semantic), `<b>` is just bold styling

3. **How to embed video in HTML5?**
   - Answer: `<video controls><source src="video.mp4" type="video/mp4"></video>`

4. **What is form validation?**
   - Answer: Checking if user input is correct before sending (HTML5: `required`, `type="email"`, etc.)

5. **Explain the difference between block and inline elements**
   - Answer: Block takes full width, inline takes needed width only

6. **What's the purpose of the viewport meta tag?**
   - Answer: Makes website responsive and scales properly on mobile devices

7. **How do you create a hyperlink?**
   - Answer: `<a href="url">Link text</a>`

8. **What are semantic elements?**
   - Answer: Elements that describe meaning (like `<header>`, `<footer>`, `<article>`) instead of generic `<div>`

9. **How to create a form dropdown?**
   - Answer: Use `<select>` with `<option>` elements

10. **What's the difference between GET and POST in forms?**
    - Answer: GET is visible in URL/not secure, POST is hidden/more secure for sensitive data

---

> 💡 **Tip:** Practice building complete pages from scratch → understand how all tags work together → repeat! 🚀
