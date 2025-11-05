
### **1. What is a Data Structure?**

* A way to **organize and store data** efficiently for operations like insertion, deletion, searching, and sorting.
* Examples: Array, Stack, Queue, Linked List, Tree, Graph.

---

### **2. What is the difference between Array and Linked List?**

| Feature            | Array         | Linked List       |
| ------------------ | ------------- | ----------------- |
| Memory             | Contiguous    | Non-contiguous    |
| Size               | Fixed         | Dynamic           |
| Access             | Random (O(1)) | Sequential (O(n)) |
| Insertion/Deletion | Costly        | Easier            |

---

### **3. What are the different types of linked lists?**

* **Singly Linked List** – nodes with next pointer only.
* **Doubly Linked List** – next and previous pointers.
* **Circular Linked List** – last node points to first node.

---

### **4. What is a Stack? Give real-life example.**

* **LIFO (Last In First Out)** data structure.
* Operations: `push()`, `pop()`, `peek()`.
* Example: Browser back button, function call stack.

---

### **5. What is a Queue? Types of Queues?**

* **FIFO (First In First Out)** data structure.
* Types: Simple, Circular, Priority, Deque.
* Example: CPU scheduling, printer queue.

---

### **6. What is the difference between BFS and DFS?**

| Feature        | BFS           | DFS                               |
| -------------- | ------------- | --------------------------------- |
| Traversal      | Level-wise    | Depth-wise                        |
| Data Structure | Queue         | Stack/Recursion                   |
| Application    | Shortest path | Topological sort, cycle detection |

---

### **7. What is a Binary Search Tree (BST)?**

* A tree where:

  * Left subtree < Root
  * Right subtree > Root
* Enables **O(log n)** search, insertion, and deletion (average case).

---

### **8. What is the difference between linear and binary search?**

| Search | Time Complexity | Requirement   |
| ------ | --------------- | ------------- |
| Linear | O(n)            | Unsorted data |
| Binary | O(log n)        | Sorted data   |

---

### **9. What is a Hash Table?**

* Stores data as **key-value pairs** using a hash function.
* Fast lookup: **Average O(1)**, Worst O(n).
* Collisions handled via **chaining or open addressing**.

---

### **10. What are asymptotic notations?**

* Represent time/space complexity:

  * **Big O (O):** Upper bound (worst case).
  * **Omega (Ω):** Lower bound (best case).
  * **Theta (Θ):** Average case (tight bound).

---

## ⚙️ **Top 3 Scenario-Based DSA Questions (Short Answers)**

---

### **Scenario 1:**

**Q:** You need to implement a browser’s “Back” and “Forward” feature. Which data structure will you use?
**A:**

* **Two stacks**:

  * One for “Back” history.
  * One for “Forward” navigation.
* Move pages between stacks as user navigates.

---

### **Scenario 2:**

**Q:** You need to handle multiple processes waiting for CPU in order of priority. Which data structure will you use?
**A:**

* **Priority Queue (Heap)**.
* Highest priority process dequeued first.
* Implemented using **min-heap or max-heap**.

---

### **Scenario 3:**

**Q:** You must find the shortest path between two cities in a road network. Which algorithm will you use?
**A:**

* **Dijkstra’s Algorithm** (for weighted graphs with non-negative edges).
* If edges can be negative → **Bellman-Ford Algorithm**.

---

