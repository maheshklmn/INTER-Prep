
### **1. What is an Operating System?**

* It’s system software that acts as an interface between the user and hardware.
* Manages processes, memory, files, I/O devices, and security.
* Examples: Windows, Linux, UNIX.

---

### **2. What is the difference between a process and a thread?**

* **Process:** Independent program in execution with its own memory space.
* **Thread:** Lightweight process; shares memory and resources within a process.
* Thread creation is faster; communication between threads is easier.

---

### **3. What are the different types of scheduling algorithms?**

* **Preemptive:** CPU can be taken away (e.g., Round Robin, SJF preemptive).
* **Non-preemptive:** Once CPU assigned, can’t be taken away (e.g., FCFS, SJF).
* Common types: FCFS, SJF, Priority, Round Robin, Multilevel Queue.

---

### **4. What is deadlock? What are its necessary conditions?**

* **Deadlock:** Situation where processes wait indefinitely for resources.
* **Conditions (Coffman’s):**

  1. Mutual exclusion
  2. Hold and wait
  3. No preemption
  4. Circular wait

---

### **5. How can a deadlock be prevented or avoided?**

* **Prevention:** Break one of the four conditions.
* **Avoidance:** Use algorithms like **Banker’s Algorithm** to ensure safe state.
* **Detection & recovery:** Allow deadlock, detect, then recover.

---

### **6. What is the difference between paging and segmentation?**

| Aspect        | Paging               | Segmentation                   |
| ------------- | -------------------- | ------------------------------ |
| Basis         | Fixed-size blocks    | Logical divisions (code, data) |
| Size          | Fixed                | Variable                       |
| Purpose       | Efficient memory use | Logical organization           |
| Fragmentation | Internal             | External                       |

---

### **7. What is virtual memory?**

* Memory management technique combining RAM + disk space.
* Enables running large programs by using **paging/swapping**.
* Implemented using **page tables** and **page replacement algorithms** (LRU, FIFO).

---

### **8. Explain page fault.**

* Occurs when a program tries to access a page not in main memory.
* OS fetches the page from secondary storage → updates page table → resumes process.

---

### **9. Difference between kernel and user mode.**

| Mode        | Access                  | Example                     |
| ----------- | ----------------------- | --------------------------- |
| Kernel Mode | Full access to hardware | Device drivers, OS services |
| User Mode   | Restricted access       | User applications           |

---

### **10. What is a context switch?**

* Process of saving the state of a running process and loading another.
* Involves saving registers, program counter, stack pointer, etc.
* Context switching adds overhead.

---

## ⚙️ **Top 3 Scenario-Based OS Questions (with direct answers)**

### **Scenario 1:**

**Q:** Two processes are waiting for each other’s resources. What is happening and how do you resolve it?
**A:**

* This is a **deadlock**.
* Resolve by:

  * Killing one process or preempting resources.
  * Using deadlock prevention (break circular wait).
  * Or avoiding via Banker’s Algorithm.

---

### **Scenario 2:**

**Q:** A process is running but frequently being swapped out and in. What could be the cause?
**A:**

* **Thrashing** — excessive paging activity due to insufficient physical memory.
* Solutions:

  * Increase RAM.
  * Reduce multiprogramming level.
  * Use better page replacement policies.

---

### **Scenario 3:**

**Q:** System performance drops sharply when multiple I/O operations happen simultaneously. Why?
**A:**

* **I/O bottleneck** or **CPU waiting for I/O completion**.
* Solutions:

  * Use **asynchronous I/O** or **spooling**.
  * Use **DMA (Direct Memory Access)** to reduce CPU load.
  * Optimize disk scheduling (e.g., **SCAN/LOOK algorithm**).

---
