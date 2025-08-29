<<<<<<< HEAD
<<<<<<< HEAD
# JavaScript DOM & Event Handling – Q&A

This document contains clear answers to commonly asked questions about **JavaScript DOM manipulation** and **event handling**.

---

## 1️⃣ Difference between `getElementById`, `getElementsByClassName`, and `querySelector / querySelectorAll`

- **`getElementById("id")`**
  - Returns **a single element** that matches the specified `id`.
  - Example:
    ```javascript
    const header = document.getElementById("main-header");
    ```
  - Returns `null` if no element with that `id` exists.
  
- **`getElementsByClassName("className")`**
  - Returns a **live HTMLCollection** of elements with the given class.
  - Example:
    ```javascript
    const cards = document.getElementsByClassName("card");
    ```
  - Updates automatically if the DOM changes (because it is live).

- **`querySelector(selector)`**
  - Returns the **first element** that matches any CSS selector.
  - Example:
    ```javascript
    const firstCard = document.querySelector(".card");
    ```

- **`querySelectorAll(selector)`**
  - Returns a **static NodeList** of all elements matching the CSS selector.
  - Example:
    ```javascript
    const allCards = document.querySelectorAll(".card");
    ```

**Summary:**  
- `getElementById` → single element by ID.  
- `getElementsByClassName` → live collection by class.  
- `querySelector` → first matching element using CSS selector.  
- `querySelectorAll` → all matching elements using CSS selector (static).

---

## 2️⃣ How do you create and insert a new element into the DOM?

1. **Create a new element** using `document.createElement()`:
    ```javascript
    const newDiv = document.createElement("div");
    newDiv.textContent = "Hello World!";
    newDiv.className = "my-div";
    ```

2. **Insert it into the DOM** using methods like `appendChild()`, `prepend()`, `insertBefore()`:
    ```javascript
    const container = document.getElementById("container");
    container.appendChild(newDiv); // Adds at the end
    ```

3. **Other insertion methods**:
    - `container.prepend(newDiv)` → adds at the beginning
    - `parent.insertBefore(newDiv, referenceNode)` → inserts before a specific node

---

## 3️⃣ What is Event Bubbling and how does it work?

- **Event Bubbling** is a way events propagate in the DOM.
- When an event occurs on an element:
  1. It first triggers on the **target element**.
  2. Then it **bubbles up** to its parent, and then the grandparent, up to the `document` object.
  
Example:
```javascript
document.getElementById("child").addEventListener("click", () => {
  alert("Child clicked");
});
```

document.getElementById("parent").addEventListener("click", () => {
  alert("Parent clicked");
});
---
## 4️⃣ What is Event Delegation in JavaScript? Why is it useful?

- **Event Delegation** is a technique where you attach a **single event listener** to a **parent element** to handle events for its children.
- Instead of adding event listeners to every child, you **listen once on the parent** and determine which child triggered the event.

**Example:**
```javascript
document.getElementById("list").addEventListener("click", (event) => {
  if(event.target.tagName === "LI") {
    alert(`You clicked on ${event.target.textContent}`);
  }
});
```
## 5️⃣ Difference between `preventDefault()` and `stopPropagation()` methods

- **`preventDefault()`**
  - Prevents the **default action** of the element.
  - Example: Prevent a form from submitting:
    ```javascript
    document.getElementById("myForm").addEventListener("submit", (e) => {
      e.preventDefault(); // stops form submission
      alert("Form submission prevented");
    });
    ```

- **`stopPropagation()`**
  - Stops the event from **bubbling up** to parent elements.
  - Example:
    ```javascript
    const child = document.getElementById("child");
    child.addEventListener("click", (e) => {
      e.stopPropagation(); // stops bubbling to parent
      alert("Child clicked");
    });
    ```

**Summary:**  
- `preventDefault()` → stops default browser behavior.  
- `stopPropagation()` → stops event from bubbling up the DOM tree.

---

## 6️⃣ Summary of Key Points

- Use **`getElementById`** for unique element selection, and **`querySelector` / `querySelectorAll`** for flexible CSS-based selection.
- You can **create and insert new elements** dynamically with `createElement` and `appendChild`/`prepend`.
- **Event Bubbling** allows events to propagate from child to parent elements.
- **Event Delegation** improves performance by attaching a single listener to a parent for all child events.
- **`preventDefault()`** stops default browser actions, while **`stopPropagation()`** prevents event bubbling.


