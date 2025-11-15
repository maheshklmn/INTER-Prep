

---

## 1. Quick Sort
### **Pseudocode (C-style):**
```c
void quickSort(int arr[], int low, int high) {
    if (low < high) {
        int p = partition(arr, low, high);
        quickSort(arr, low, p - 1);
        quickSort(arr, p + 1, high);
    }
}
````

### **Answer:**

* Select pivot → partition array.
* Recursively sort subarrays.
* Avg: O(n log n), Worst: O(n²).

---

## 2. Merge Sort

### **Pseudocode:**

```c
void mergeSort(int arr[], int l, int r) {
    if (l < r) {
        int mid = (l + r) / 2;
        mergeSort(arr, l, mid);
        mergeSort(arr, mid + 1, r);
        merge(arr, l, mid, r);
    }
}
```

### **Answer:**

* Divide → sort → merge.
* Time: O(n log n), Space: O(n).

---

## 3. GCD (Euclid’s Algorithm)

### **Pseudocode:**

```c
int gcd(int a, int b) {
    while (b != 0) {
        int temp = a % b;
        a = b;
        b = temp;
    }
    return a;
}
```

### **Answer:**

* Repeated modulo.
* Time: O(log(min(a,b))).

---

## 4. Binary Search

### **Pseudocode:**

```c
int binarySearch(int arr[], int n, int key) {
    int low = 0, high = n - 1;
    while (low <= high) {
        int mid = (low + high) / 2;
        if (arr[mid] == key) return mid;
        else if (key < arr[mid]) high = mid - 1;
        else low = mid + 1;
    }
    return -1;
}
```

### **Answer:**

* Works on sorted arrays.
* Time: O(log n).

---

## 5. Detect Cycle in Linked List (Floyd)

### **Pseudocode:**

```c
bool hasCycle(Node* head) {
    Node *slow = head, *fast = head;
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
        if (slow == fast) return true;
    }
    return false;
}
```

### **Answer:**

* Slow & fast pointers.
* Time: O(n), Space: O(1).

---

## 6. BFS and DFS

### **BFS (C-style):**

```c
void bfs(int start) {
    queue<int> q;
    visited[start] = true;
    q.push(start);

    while (!q.empty()) {
        int node = q.front(); q.pop();
        for (int v : adj[node]) {
            if (!visited[v]) {
                visited[v] = true;
                q.push(v);
            }
        }
    }
}
```

### **DFS (C-style):**

```c
void dfs(int node) {
    visited[node] = true;
    for (int v : adj[node]) {
        if (!visited[v]) dfs(v);
    }
}
```

### **Answer:**

* BFS → level order.
* DFS → depth-first.
* Time: O(V + E).

---

## 7. Dijkstra’s Algorithm

### **Pseudocode:**

```c
void dijkstra(int src) {
    priority_queue<pair<int,int>> pq;
    dist[src] = 0;
    pq.push({0, src});

    while (!pq.empty()) {
        int u = pq.top().second;
        pq.pop();

        for (auto edge : adj[u]) {
            int v = edge.to, w = edge.weight;
            if (dist[u] + w < dist[v]) {
                dist[v] = dist[u] + w;
                pq.push({-dist[v], v});
            }
        }
    }
}
```

### **Answer:**

* Uses min-priority queue.
* Time: O(E log V).

---

## 8. Kadane’s Algorithm (Max Subarray Sum)

### **Pseudocode:**

```c
int maxSubArray(int arr[], int n) {
    int max_sum = arr[0], curr = arr[0];
    for (int i = 1; i < n; i++) {
        curr = max(arr[i], curr + arr[i]);
        max_sum = max(max_sum, curr);
    }
    return max_sum;
}
```

### **Answer:**

* Track current + max.
* Time: O(n).

---

## 9. Heap Sort

### **Pseudocode:**

```c
void heapSort(int arr[], int n) {
    buildMaxHeap(arr, n);
    for (int i = n - 1; i >= 1; i--) {
        swap(arr[0], arr[i]);
        heapify(arr, i, 0);
    }
}
```

### **Answer:**

* Build heap → extract max repeatedly.
* Time: O(n log n).

---

## 10. Reverse a Linked List

### **Pseudocode:**

```c
Node* reverse(Node* head) {
    Node *prev = NULL, *curr = head;
    while (curr) {
        Node* nextNode = curr->next;
        curr->next = prev;
        prev = curr;
        curr = nextNode;
    }
    return prev;
}
```

### **Answer:**

* Change next pointers iteratively.
* Time: O(n), Space: O(1).

---

# 🎯 Scenario-Based Questions (C-Style Logic Included)

---

## 1. Sorting 1 Billion Numbers

### **Answer:**

* Use **External Merge Sort**.
* Handles disk-based large data.
* O(n log n) performance.

---

## 2. Search Function Slow on Large Data

### **Answer:**

* Use **Binary Search** if sorted.
* Use **Hashing** for O(1) average lookups.
* Build **index** for repeated searches.

---

## 3. Shortest Delivery Routes in City Map

### **Answer:**

* Use **Dijkstra** → weighted shortest path.
* Use **A*** if you need heuristics.
* Floyd-Warshall for all-pairs.

---
