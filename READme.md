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
3️⃣ What is Event Bubbling and How Does It Work?

🔄 Event Bubbling = When an event occurs on a child element, it automatically bubbles up to its parent, grandparent, and so on.

Example:

<div id="parent">
  <button id="child">Click Me</button>
</div>

document.getElementById("child").addEventListener("click", () => {
  console.log("Button clicked");
});

document.getElementById("parent").addEventListener("click", () => {
  console.log("Parent div clicked");
});


👉 Clicking the button triggers both logs.

4️⃣ What is Event Delegation? Why is it Useful?

👨‍👩‍👧 Event Delegation = Attaching one listener to a parent element to handle events for its children (using bubbling).

✨ Benefits:

✅ Fewer event listeners → better performance

✅ Works with dynamically added elements

Example:

document.getElementById("list").addEventListener("click", (event) => {
  if (event.target.tagName === "LI") {
    console.log("List item clicked:", event.target.textContent);
  }
});

5️⃣ Difference between preventDefault() and stopPropagation()

🚫 preventDefault()

Stops the browser’s default behavior.

Example:

document.querySelector("form").addEventListener("submit", (e) => {
  e.preventDefault(); // Stops form from submitting
  console.log("Form submission blocked!");
});


🛑 stopPropagation()

Stops the event from bubbling up to parent elements.

Example:

document.getElementById("child").addEventListener("click", (e) => {
  e.stopPropagation(); // Prevents parent handler
  console.log("Only button clicked");
});


