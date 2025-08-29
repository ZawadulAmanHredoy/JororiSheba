# 🌐 JavaScript DOM & Events – Q&A

This document contains clear answers with examples for common **JavaScript DOM** and **Event Handling** questions.  

---

## 1️⃣ Difference between `getElementById`, `getElementsByClassName`, and `querySelector / querySelectorAll`

- 🔹 **`getElementById("id")`**
  - Finds an element by its unique **ID**.
  - Returns a **single element**.
  - Example:
    ```js
    let title = document.getElementById("main-title");
    ```

- 🔹 **`getElementsByClassName("class")`**
  - Finds all elements with a specific **class name**.
  - Returns an **HTMLCollection** (array-like).
  - Example:
    ```js
    let items = document.getElementsByClassName("list-item");
    ```

- 🔹 **`querySelector("selector")`**
  - Finds the **first element** matching a CSS selector.
  - Example:
    ```js
    let firstItem = document.querySelector(".list-item");
    ```

- 🔹 **`querySelectorAll("selector")`**
  - Finds **all elements** matching a CSS selector.
  - Returns a **NodeList** (can use `forEach`).
  - Example:
    ```js
    let allItems = document.querySelectorAll(".list-item");
    ```

---

## 2️⃣ How to Create and Insert a New Element into the DOM

📌 Steps:  
1. **Create** the element  
2. **Set content/attributes**  
3. **Insert into the DOM**

Example:
```js
// Step 1: Create
let newDiv = document.createElement("div");

// Step 2: Add content and attributes
newDiv.textContent = "Hello World!";
newDiv.className = "box";

// Step 3: Insert into the DOM
document.body.appendChild(newDiv);
---

## 3️⃣ What is Event Bubbling and How Does It Work?

- 🔹 **Definition**
  - Event bubbling means that when an event happens on a child element, it first runs its handler, then the handler of its parent, and so on up the DOM tree.

- 🔹 **How it works**
  - Events start from the **innermost target element** and then bubble up to the ancestors.

- 🔹 **Example**
  ```html
  <div id="parent">
    <button id="child">Click Me</button>
  </div>
