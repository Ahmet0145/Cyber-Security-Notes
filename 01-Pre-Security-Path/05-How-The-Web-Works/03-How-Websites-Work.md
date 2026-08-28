# 🌐 Web Application Fundamentals & Client-Side Security

This section explores the core components of modern web applications, detailing how browsers interact with servers, the structural and functional role of HTML and JavaScript, and common security vulnerabilities found in client-side implementations.

---

## 🏗️ 1. Architecture of a Web Application

A web application relies on a client-server architecture to process user requests and serve content.
```
+------------------+         Request from browser         +--------------------+
|                  | -----------------------------------> |                    |
|  Client Browser  |                                      |     Web Server     |
| (Chrome, Safari) | <----------------------------------- | (Processes Data &  |
|                  |         Response from server         |  Returns HTML/JS)  |
+------------------+                                      +--------------------+
```

Web applications consist of two primary operational components:
* **Front End (Client-Side):** The user-facing component executed within the web browser. It governs layout, presentation, visual styling, and user interaction.
* **Back End (Server-Side):** The remote server-side component that handles application logic, database operations, user authentication, and processes incoming requests to yield HTTP responses.

---

## 📜 2. HTML (HyperText Markup Language) Structure

HTML forms the foundational markup language used to structure web pages through elements (tags).

### Code Structure
```html
<!DOCTYPE html>
<html>
<head>
  <title>Page Title</title>
</head>
<body>
  <h1>Example Heading</h1>
  <p>Example paragraph..</p>
</body>
</html>
```

### Component Breakdown

* **`<!DOCTYPE html>`**: Defines the document type as HTML5 to ensure proper standardization across different browsers.
* **`<html>`**: The root element enclosing all other HTML elements on the page.
* **`<head>`**: Contains metadata and resources about the page (e.g., `<title>`, meta tags, external scripts).
* **`<body>`**: Encloses the visible content displayed directly in the browser window.
* **`<h1>`**: Renders a top-level heading.
* **`<p>`**: Defines a text paragraph.

### HTML Attributes & Identifiers

Elements utilize attributes to store metadata, pass identifiers, or adjust styling:

* **`class` Attribute:** Assigns shared styling classes to multiple elements (e.g., `<p class="bold-text">`).
* **`src` Attribute:** Defines the file path or URL location of embedded media (e.g., `<img src="img/cat.jpg">`).
* **`id` Attribute:** Assigns a unique identifier to a single element (e.g., `<p id="example">`). Unlike classes, `id` values must be unique across the document and are primarily referenced for DOM manipulation via JavaScript and specific CSS styling.

---

## ⚡ 3. JavaScript (JS) & Dynamic Interactivity
While HTML constructs document structure and CSS defines visual layout, JavaScript provides programmatic interactivity and real-time page updates.

JavaScript Integration & Methods
JavaScript can be embedded directly within <script> tags or imported remotely:
```
<script src="/location/of/javascript_file.js"></script>
```

Document Object Model (DOM) Manipulation: JavaScript dynamically modifies HTML content in real time. For instance, selecting an element by its unique id and modifying its inner text:

```
document.getElementById("demo").innerHTML = "Hack the Planet";
```

Event Handlers: Elements leverage event attributes (e.g., onclick, onhover) to execute scripts upon user interaction:
```
<button onclick="document.getElementById('demo').innerHTML = 'Button Clicked';">Click Me!</button>
```

---

## 🛡️ 4. Security Perspective

Here are the two most common web security issues in simple terms:

### 1. Sensitive Data Exposure
* **Concept:** When you right-click on a website and select *"View Page Source"*, you can see the website's entire HTML and JavaScript code.
* **Risk:** Developers sometimes forget test passwords (e.g., `admin:password123`), secret API keys, or hidden URLs inside HTML comments (`<!-- comment -->`). Attackers can read these to gain unauthorized access.

### 2. HTML / Script Injection
* **Concept:** This happens when a website takes what a user types into an input field (like a name box) and displays it directly on the screen without checking it first.
* **Risk:** If a user types malicious code—like `<script>alert(1)</script>`—instead of a normal name, the browser will run that code on the page. Attackers can use this to execute harmful scripts on victim machines.
* **Golden Rule:** **Never trust user input.** Always clean (sanitize) any text entered by users before showing it on the page.
