# DAA Repository

Welcome to the **DAA Repository**! This repository is a collection of codes, algorithms, and notes related to the **Design and Analysis of Algorithms (DAA)** course. It aims to serve as a comprehensive resource for learning and revising key concepts in DAA.

---

## Features

- 📚 **Well-Documented Codes**: Each algorithm is thoroughly documented with explanations.
- 🧪 **Test Cases**: Every code includes test cases to validate correctness.
- 🚀 **Optimized Solutions**: Focused on writing efficient and clean code.
- 📂 **Organized Structure**: All files are categorized for easy navigation.

---

## Contents

1. **Sorting Algorithms**

   - Insertion Sort
   - Bubble Sort
   - Merge Sort
   - Quick Sort
  
3. **Searching Algorithms (Not Added)**
   - Binary Search
   - Linear Search

4. **Graph Algorithms (Not Added)**
   - Dijkstra's Algorithm
   - Floyd-Warshall Algorithm

5. **Dynamic Programming (Not Added)**
   - Longest Common Subsequence (LCS)
   - 0/1 Knapsack Problem

6. **Greedy Algorithms(Not Added)**
   - Huffman Encoding
   - Kruskal's Algorithm

7. **Divide and Conquer (Contents are on-the-way......Coming Soon)**
   - Strassen's Matrix Multiplication
   - Closest Pair of Points

---
```import sys
import heapq
from collections import defaultdict

def main():
    input = sys.stdin.read
    data = input().split()
    
    M = int(data[0])
    A = int(data[1])
    B = int(data[2])
    
    graph = defaultdict(list)
    index = 3
    
    for _ in range(M):
        X = int(data[index])
        Y = int(data[index+1])
        Z = int(data[index+2])
        graph[X].append((Z, Y))
        graph[Z].append((X, Y))
        index += 3
    
    # If A and B are the same, shortest path is 0
    if A == B:
        print("YES")
        print(0)
        return

    # Dijkstra's algorithm
    if A not in graph or B not in graph:
        print("NO")
        return
    
    dist = {}
    heap = [(0, A)]  # (distance, node)
    
    while heap:
        current_dist, u = heapq.heappop(heap)
        if u in dist:
            continue
        dist[u] = current_dist
        if u == B:
            break
        for v, w in graph[u]:
            if v not in dist:
                heapq.heappush(heap, (current_dist + w, v))
    
    if B in dist:
        print("YES")
        print(dist[B])
    else:
        print("NO")

if __name__ == "__main__":
    main()
```

## 📌 Chapter: Insertion Sort

### **Introduction**
Insertion Sort is a simple and efficient comparison-based sorting algorithm that builds the final sorted array one element at a time.

### **Algorithm**
1. Iterate from index `1` to `n-1`.
2. Compare the current element with its predecessors.
3. Shift elements to the right to make space for the correct position of the current element.
4. Repeat until the array is sorted.

### **Pseudo Code**

```plaintext
for(i=1;i<size;i++)
{
   temp=list[i];
      j=i-1;
   while((temp<list[j]) && (j>=0))
   {
      list[j+1]=list[j];
         j=j-1;
   }
} list[j+1]=temp;
```
### **Code Implementation in C**
```c
#include <stdio.h>

void insertionSort(int list[], int size) {
    int temp, j;
    for (int i = 1; i < size; i++) {
        temp = list[i];
        j = i - 1;

        // Move elements of list[0..i-1] that are greater than temp to one position ahead
        while (j >= 0 && list[j] > temp) {
            list[j + 1] = list[j];
            j = j - 1;
        }

        // Insert temp into the correct position
        list[j + 1] = temp;
    }
}

void printArray(int list[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", list[i]);
    }
    printf("\n");
}

int main() {
    int list[] = {12, 11, 13, 5, 6};
    int size = sizeof(list) / sizeof(list[0]);

    printf("Original array: \n");
    printArray(list, size);

    insertionSort(list, size);

    printf("Sorted array: \n");
    printArray(list, size);

    return 0;
}

```

### **Time Complexity Analysis**
- **Best Case (`O(n)`)**: Already sorted array.
- **Worst Case (`O(n²)`)**: Reverse sorted array.
- **Average Case (`O(n²)`)**: Random order.

### **Advantages**
✔ Efficient for small data sets.

✔ Simple and easy to implement.

✔ Stable sorting algorithm (preserves the order of equal elements).

### **Disadvantages**
✖ Not suitable for large data sets due to `O(n²)` complexity.

✖ Inefficient compared to Quick Sort and Merge Sort.

### **Applications**
📌 **Used in small databases where simplicity matters.**

📌 **Effective for nearly sorted data (adaptive sorting).**

📌 **Used in educational purposes to teach sorting concepts.**

### **Graphical Representation**
```mermaid
%%{init: {"theme": "base", "themeVariables": {"background": "#f4f4f4", "fontFamily": "Arial", "fontSize": "16px"}}}%%
graph TD;
    subgraph uroy80
    A[5, 3, 8, 6, 2] --> B[3, 5, 8, 6, 2];
    B --> C[3, 5, 8, 6, 2];
    C --> D[3, 5, 6, 8, 2];
    D --> E[2, 3, 5, 6, 8];
    end
```

```mermaid
%%{init: {"theme": "base", "themeVariables": {"background": "#f4f4f4", "fontFamily": "Arial", "fontSize": "16px"}}}%%
graph LR;
    subgraph uroy80
    A[Unsorted: 5, 3, 8, 6, 2] -->|Insert 3| B[3, 5, 8, 6, 2];
    B -->|Insert 8| C[3, 5, 8, 6, 2];
    C -->|Insert 6| D[3, 5, 6, 8, 2];
    D -->|Insert 2| E[2, 3, 5, 6, 8];
    E -->|Sorted| F[(Final Sorted Array)];
    end
```

---

## Contribution Guidelines

Contributions are welcome! Please follow these steps:

1. Fork this repository.
2. Create a new branch: `git checkout -b feature-name`.
3. Commit your changes: `git commit -m 'Add a new feature'`.
4. Push to the branch: `git push origin feature-name`.
5. Open a pull request.

---

## Contact

- **GitHub Profile**: [uroy80](https://github.com/uroy80)
- **Email**: ushamroy80@gmail.com

---

### Happy Coding! 😊
