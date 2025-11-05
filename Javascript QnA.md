
## 🧠 **Top 10 Most Common JavaScript Questions (Short Answers)**

---

### **1. What is JavaScript?**

* Lightweight, **interpreted, event-driven** scripting language.
* Runs in browsers to make web pages **interactive and dynamic**.

---

### **2. Difference between `var`, `let`, and `const`?**

| Keyword | Scope           | Re-declaration | Re-assignment |
| ------- | --------------- | -------------- | ------------- |
| var     | Function-scoped | Yes            | Yes           |
| let     | Block-scoped    | No             | Yes           |
| const   | Block-scoped    | No             | No            |

---

### **3. What are data types in JavaScript?**

* **Primitive:** String, Number, Boolean, Null, Undefined, Symbol, BigInt
* **Non-primitive:** Object, Array, Function

---

### **4. What is Hoisting?**

* JavaScript moves variable and function **declarations** to the top of their scope during compilation.
* Example: You can call a function before it’s declared.

---

### **5. What is the difference between `==` and `===`?**

| Operator | Comparison                                      | Example             |
| -------- | ----------------------------------------------- | ------------------- |
| `==`     | Checks **value** only (type conversion allowed) | `'5' == 5 → true`   |
| `===`    | Checks **value + type**                         | `'5' === 5 → false` |

---

### **6. What is a closure?**

* A function having access to its **outer function’s scope** even after the outer function has returned.
* Example:

  ```js
  function outer() {
    let x = 10;
    return function inner() { return x; };
  }
  ```

---

### **7. What is an event loop in JavaScript?**

* Mechanism that handles **asynchronous operations** (callbacks, promises).
* Executes **call stack → callback queue → microtask queue** continuously.

---

### **8. What are callbacks and promises?**

* **Callback:** Function passed as an argument, executed after completion of another function.
* **Promise:** Object representing eventual completion (resolve/reject).

  ```js
  promise.then().catch();
  ```

---

### **9. What is DOM?**

* **Document Object Model:** Tree structure representing HTML.
* JS can manipulate elements via `document.getElementById()`, etc.

---

### **10. What is the difference between synchronous and asynchronous programming?**

| Type         | Execution                        | Example                   |
| ------------ | -------------------------------- | ------------------------- |
| Synchronous  | One task at a time               | `alert()`                 |
| Asynchronous | Non-blocking, runs in background | `setTimeout()`, `fetch()` |

---

## ⚙️ **Top 3 Scenario-Based JavaScript Questions (Short Answers)**

---

### **Scenario 1:**

**Q:** You click a button, but nothing happens. How will you debug it?
**A:**

1. Check browser **console** for errors.
2. Verify **event listener** (`addEventListener` or `onclick`).
3. Ensure **script is loaded** (`<script>` tag at correct place).
4. Check **DOM element ID/class** correctness.

---

### **Scenario 2:**

**Q:** You need to fetch data from an API and display it on the web page. How will you do it?
**A:**

```js
fetch('https://api.example.com/data')
  .then(res => res.json())
  .then(data => console.log(data))
  .catch(err => console.error(err));
```

* Uses **Fetch API** (Promise-based).
* Handles asynchronous data loading.

---

### **Scenario 3:**

**Q:** You need to run a function every 5 seconds without blocking other code. What will you use?
**A:**

* Use `setInterval()` or `setTimeout()` (asynchronous).

  ```js
  setInterval(myFunc, 5000);
  ```
* Non-blocking due to **event loop**.

---
