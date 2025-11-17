```markdown
# Algorithms Implementation in Java

## 1. Quick Sort
### **Java Code:**
```java
public class QuickSort {
    public void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            int p = partition(arr, low, high);
            quickSort(arr, low, p - 1);
            quickSort(arr, p + 1, high);
        }
    }
    
    private int partition(int[] arr, int low, int high) {
        int pivot = arr[high];
        int i = low - 1;
        
        for (int j = low; j < high; j++) {
            if (arr[j] <= pivot) {
                i++;
                swap(arr, i, j);
            }
        }
        swap(arr, i + 1, high);
        return i + 1;
    }
    
    private void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}
```

### **Answer:**
* Select pivot → partition array
* Recursively sort subarrays
* Avg: O(n log n), Worst: O(n²)

---

## 2. Merge Sort

### **Java Code:**
```java
public class MergeSort {
    public void mergeSort(int[] arr, int l, int r) {
        if (l < r) {
            int mid = (l + r) / 2;
            mergeSort(arr, l, mid);
            mergeSort(arr, mid + 1, r);
            merge(arr, l, mid, r);
        }
    }
    
    private void merge(int[] arr, int l, int mid, int r) {
        int n1 = mid - l + 1;
        int n2 = r - mid;
        
        int[] left = new int[n1];
        int[] right = new int[n2];
        
        for (int i = 0; i < n1; i++) left[i] = arr[l + i];
        for (int j = 0; j < n2; j++) right[j] = arr[mid + 1 + j];
        
        int i = 0, j = 0, k = l;
        while (i < n1 && j < n2) {
            if (left[i] <= right[j]) {
                arr[k] = left[i];
                i++;
            } else {
                arr[k] = right[j];
                j++;
            }
            k++;
        }
        
        while (i < n1) arr[k++] = left[i++];
        while (j < n2) arr[k++] = right[j++];
    }
}
```

### **Answer:**
* Divide → sort → merge
* Time: O(n log n), Space: O(n)

---

## 3. GCD (Euclid's Algorithm)

### **Java Code:**
```java
public class GCD {
    public int gcd(int a, int b) {
        while (b != 0) {
            int temp = a % b;
            a = b;
            b = temp;
        }
        return a;
    }
    
    // Recursive version
    public int gcdRecursive(int a, int b) {
        if (b == 0) return a;
        return gcdRecursive(b, a % b);
    }
}
```

### **Answer:**
* Repeated modulo
* Time: O(log(min(a,b)))

---

## 4. Binary Search

### **Java Code:**
```java
public class BinarySearch {
    public int binarySearch(int[] arr, int key) {
        int low = 0, high = arr.length - 1;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (arr[mid] == key) return mid;
            else if (key < arr[mid]) high = mid - 1;
            else low = mid + 1;
        }
        return -1;
    }
}
```

### **Answer:**
* Works on sorted arrays
* Time: O(log n)

---

## 5. Detect Cycle in Linked List (Floyd)

### **Java Code:**
```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int x) { val = x; }
}

public class CycleDetection {
    public boolean hasCycle(ListNode head) {
        if (head == null) return false;
        
        ListNode slow = head;
        ListNode fast = head;
        
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) return true;
        }
        return false;
    }
}
```

### **Answer:**
* Slow & fast pointers
* Time: O(n), Space: O(1)

---

## 6. BFS and DFS

### **BFS (Java):**
```java
import java.util.*;

public class GraphTraversal {
    public void bfs(List<List<Integer>> adj, int start) {
        boolean[] visited = new boolean[adj.size()];
        Queue<Integer> queue = new LinkedList<>();
        
        visited[start] = true;
        queue.offer(start);
        
        while (!queue.isEmpty()) {
            int node = queue.poll();
            System.out.print(node + " ");
            
            for (int neighbor : adj.get(node)) {
                if (!visited[neighbor]) {
                    visited[neighbor] = true;
                    queue.offer(neighbor);
                }
            }
        }
    }
```

### **DFS (Java):**
```java
    public void dfs(List<List<Integer>> adj, int node, boolean[] visited) {
        visited[node] = true;
        System.out.print(node + " ");
        
        for (int neighbor : adj.get(node)) {
            if (!visited[neighbor]) {
                dfs(adj, neighbor, visited);
            }
        }
    }
}
```

### **Answer:**
* BFS → level order
* DFS → depth-first
* Time: O(V + E)

---

## 7. Dijkstra's Algorithm

### **Java Code:**
```java
import java.util.*;

public class Dijkstra {
    public int[] dijkstra(List<List<int[]>> graph, int src) {
        int n = graph.size();
        int[] dist = new int[n];
        Arrays.fill(dist, Integer.MAX_VALUE);
        dist[src] = 0;
        
        PriorityQueue<int[]> pq = new PriorityQueue<>((a, b) -> a[1] - b[1]);
        pq.offer(new int[]{src, 0});
        
        while (!pq.isEmpty()) {
            int[] current = pq.poll();
            int u = current[0];
            
            for (int[] edge : graph.get(u)) {
                int v = edge[0], weight = edge[1];
                if (dist[u] + weight < dist[v]) {
                    dist[v] = dist[u] + weight;
                    pq.offer(new int[]{v, dist[v]});
                }
            }
        }
        return dist;
    }
}
```

### **Answer:**
* Uses min-priority queue
* Time: O(E log V)

---

## 8. Kadane's Algorithm (Max Subarray Sum)

### **Java Code:**
```java
public class Kadane {
    public int maxSubArray(int[] arr) {
        int maxSum = arr[0];
        int currentSum = arr[0];
        
        for (int i = 1; i < arr.length; i++) {
            currentSum = Math.max(arr[i], currentSum + arr[i]);
            maxSum = Math.max(maxSum, currentSum);
        }
        return maxSum;
    }
}
```

### **Answer:**
* Track current + max
* Time: O(n)

---

## 9. Heap Sort

### **Java Code:**
```java
public class HeapSort {
    public void heapSort(int[] arr) {
        int n = arr.length;
        
        // Build max heap
        for (int i = n / 2 - 1; i >= 0; i--)
            heapify(arr, n, i);
        
        // Extract elements from heap
        for (int i = n - 1; i >= 0; i--) {
            // Move current root to end
            int temp = arr[0];
            arr[0] = arr[i];
            arr[i] = temp;
            
            // Call max heapify on the reduced heap
            heapify(arr, i, 0);
        }
    }
    
    private void heapify(int[] arr, int n, int i) {
        int largest = i;
        int left = 2 * i + 1;
        int right = 2 * i + 2;
        
        if (left < n && arr[left] > arr[largest])
            largest = left;
        
        if (right < n && arr[right] > arr[largest])
            largest = right;
        
        if (largest != i) {
            int swap = arr[i];
            arr[i] = arr[largest];
            arr[largest] = swap;
            
            heapify(arr, n, largest);
        }
    }
}
```

### **Answer:**
* Build heap → extract max repeatedly
* Time: O(n log n)

---

## 10. Reverse a Linked List

### **Java Code:**
```java
public class LinkedListReverse {
    public ListNode reverse(ListNode head) {
        ListNode prev = null;
        ListNode curr = head;
        
        while (curr != null) {
            ListNode nextNode = curr.next;
            curr.next = prev;
            prev = curr;
            curr = nextNode;
        }
        return prev;
    }
    
    // Recursive version
    public ListNode reverseRecursive(ListNode head) {
        if (head == null || head.next == null) return head;
        
        ListNode newHead = reverseRecursive(head.next);
        head.next.next = head;
        head.next = null;
        
        return newHead;
    }
}
```

### **Answer:**
* Change next pointers iteratively
* Time: O(n), Space: O(1)

---

# 🎯 Scenario-Based Questions

---

## 1. Sorting 1 Billion Numbers

### **Answer:**
* Use **External Merge Sort**
* Handles disk-based large data
* O(n log n) performance
* Java's `Arrays.parallelSort()` for large in-memory datasets

---

## 2. Search Function Slow on Large Data

### **Answer:**
* Use **Binary Search** if sorted
* Use **HashMap** for O(1) average lookups
* Build **index** for repeated searches
* Consider **Bloom Filters** for membership tests

---

## 3. Shortest Delivery Routes in City Map

### **Answer:**
* Use **Dijkstra** → weighted shortest path
* Use **A*** if you need heuristics
* Floyd-Warshall for all-pairs
* Java libraries: JGraphT for graph algorithms
```
