## Time Complexity

### Definition:
Time Complexity refers to the amount of time taken by an algorithm to run as a function of the input size (n). It helps in evaluating the efficiency of an algorithm.

---

### Example: Finding the number of even numbers from `1` to `N`

#### **Approach 1: Using a Loop (O(n))**
```cpp
#include <iostream>
using namespace std;

int countEvenLoop(int n) {
    int count = 0;
    for (int i = 1; i <= n; i++) {
        if (i % 2 == 0) count++;
    }
    return count;
}

int main() {
    int n = 10;
    cout << countEvenLoop(n); // Output: 5
}
```
- **Time Complexity: O(n)** (Linear Time Complexity)
- As `n` increases, the number of iterations grows linearly.

#### **Approach 2: Using Formula (O(1))**
```cpp
#include <iostream>
using namespace std;

int countEvenFormula(int n) {
    return n / 2;
}

int main() {
    int n = 10;
    cout << countEvenFormula(n); // Output: 5
}
```
- **Time Complexity: O(1)** (Constant Time Complexity)
- The result is computed directly without looping.

---

## **Big O, Theta (Θ), and Omega (Ω) Notations**

### **1. Big O Notation (O)**
- Represents the **worst-case** scenario.
- Upper bound on the time complexity.
- **Example:** If an algorithm runs in `O(n^2)`, it means for large `n`, the execution time grows at most proportional to `n^2`.

#### **Example Code:**
```cpp
void exampleFunction(int n) {
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            cout << i << j << endl;
        }
    }
}
```
- **Time Complexity: O(n²)** (Nested Loops)
- **Reason:** The inner loop runs `n` times for each iteration of the outer loop → `n * n = n²`.

---

### **2. Theta Notation (Θ)**
- Represents the **average-case** scenario.
- It gives both an upper and lower bound.
- **Example:** If an algorithm is `Θ(n)`, it means it always takes `cn` time for some constant `c`.

#### **Example Code:**
```cpp
void exampleFunctionTheta(int n) {
    for (int i = 0; i < n; i++) {
        cout << i << endl;
    }
}
```
- **Time Complexity: Θ(n)**
- **Reason:** It always executes `n` times, so it is both upper and lower bounded by `n`.

---

### **3. Omega Notation (Ω)**
- Represents the **best-case** scenario.
- Lower bound on the time complexity.
- **Example:** If an algorithm runs in `Ω(n)`, it means it will take at least `n` operations in the best case.

#### **Example Code:**
```cpp
int linearSearch(int arr[], int n, int key) {
    for (int i = 0; i < n; i++) {
        if (arr[i] == key)
            return i; // Found at index i
    }
    return -1; // Not found
}
```
- **Best Case (Ω(1))**: If the key is found at the first index.
- **Worst Case (O(n))**: If the key is at the last index or not present.
- **Average Case (Θ(n))**: On average, the key will be found halfway through the array.

---

### **Summary of Complexity Notations**
| Notation | Meaning | Example |
|----------|----------|----------|
| **O(n²)** | Worst-case time complexity | Nested loops |
| **Θ(n)** | Average-case time complexity | Single loop |
| **Ω(1)** | Best-case time complexity | Finding the first element in a search |

These notations help analyze the efficiency of algorithms and make informed decisions in problem-solving. 🚀

## Time Complexity

### Definition:
Time Complexity refers to the amount of time taken by an algorithm to run as a function of the input size (n). It helps in evaluating the efficiency of an algorithm and comparing different approaches.

---

### **Common Time Complexities with Examples**

#### **O(1) - Constant Time**
- Example: Picking a book from a shelf.
- Code Analogy: Accessing an element in an array.
```cpp
int getFirstElement(vector<int> &arr) {
    return arr[0]; // Always takes the same time, no matter the size of arr
}
```

#### **O(n) - Linear Time**
- Example: Reading a book page by page.
- Code Analogy: Traversing an array.
```cpp
void printArray(vector<int> &arr) {
    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " ";
    }
}
```

#### **O(log n) - Logarithmic Time**
- Example: Searching for a word in a dictionary by flipping pages in halves.
- Code Analogy: Binary Search.
```cpp
int binarySearch(vector<int> &arr, int target) {
    int left = 0, right = arr.size() - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == target) return mid;
        else if (arr[mid] < target) left = mid + 1;
        else right = mid - 1;
    }
    return -1;
}
```

#### **O(n²) - Quadratic Time**
- Example: Comparing each student in a class with every other student.
- Code Analogy: Nested loops.
```cpp
void printPairs(vector<int> &arr) {
    for (int i = 0; i < arr.size(); i++) {
        for (int j = 0; j < arr.size(); j++) {
            cout << "(" << arr[i] << ", " << arr[j] << ")\n";
        }
    }
}
```

#### **O(n³) - Cubic Time**
- Example: Checking all possible group combinations in a class of students.
- Code Analogy: Triple nested loops.
```cpp
void printTriplets(vector<int> &arr) {
    for (int i = 0; i < arr.size(); i++) {
        for (int j = 0; j < arr.size(); j++) {
            for (int k = 0; k < arr.size(); k++) {
                cout << "(" << arr[i] << ", " << arr[j] << ", " << arr[k] << ")\n";
            }
        }
    }
}
```

#### **O(n log n) - Linearithmic Time**
- Example: Organizing a bookshelf by dividing books into groups and sorting them.
- Code Analogy: Merge Sort.
```cpp
void mergeSort(vector<int> &arr, int left, int right) {
    if (left >= right) return;
    int mid = left + (right - left) / 2;
    mergeSort(arr, left, mid);
    mergeSort(arr, mid + 1, right);
    // Merging step (not shown for brevity)
}
```

#### **O(n!) - Factorial Time**
- Example: Arranging people in all possible seating orders.
- Code Analogy: Generating all permutations.
```cpp
void permute(vector<int> &arr, int l, int r) {
    if (l == r) {
        for (int num : arr) cout << num << " ";
        cout << "\n";
        return;
    }
    for (int i = l; i <= r; i++) {
        swap(arr[l], arr[i]);
        permute(arr, l + 1, r);
        swap(arr[l], arr[i]);
    }
}
```

---

### **Summary of Time Complexities**
| Notation | Example Analogy | Complexity |
|----------|------------------|------------|
| **O(1)** | Picking a book from a shelf | Constant |
| **O(n)** | Reading a book page by page | Linear |
| **O(log n)** | Searching for a word in a dictionary | Logarithmic |
| **O(n²)** | Comparing every student with every other | Quadratic |
| **O(n³)** | Checking all possible groups of students | Cubic |
| **O(n log n)** | Sorting books by dividing into groups | Linearithmic |
| **O(n!)** | Arranging people in all possible seating orders | Factorial |

Understanding these complexities helps in choosing efficient algorithms for different problems. 🚀


# **Time Complexity Calculation: Procedural Phase Only**  

## **Why Don't We Add Time Complexities?**  
- When analyzing time complexity, we focus only on the **procedural phase** (core logic of the algorithm).  
- Input (I/O) operations like reading values or printing results are generally **O(1) or O(n)** and are **not considered** in complexity calculations.  
- We do **not add complexities**; instead, we take the **dominant term** (the highest order of growth).  

## **Code Example**  
```cpp
void process(int arr[], int n) {
    // Input Phase (Ignored in Complexity)
    for (int i = 0; i < n; i++) {  // O(n)
        cin >> arr[i];
    }

    // Two-pointer approach (Procedural Phase)
    int left = 0, right = n - 1;
    while (left < right) {  // O(n)
        cout << arr[left] << " " << arr[right] << " ";
        left++;
        right--;
    }

    // Output Phase (Ignored in Complexity)
    for (int i = 0; i < n; i++) {  // O(n)
        cout << arr[i] << " ";
    }
}
```

## **Step-by-Step Complexity Analysis**  

1. **For Loop (Input Phase)**  
   - Runs **n times**.  
   - Each iteration takes **O(1)** time.  
   - **Ignored in final complexity calculation**.  

2. **While Loop (Two-Pointer Approach)**  
   - Moves two pointers from both ends toward the center.  
   - Covers **n elements** in **O(n) time**.  
   - **Considered in complexity analysis**.  

3. **For Loop (Output Phase)**  
   - Runs **n times**.  
   - Each iteration takes **O(1)** time.  
   - **Ignored in final complexity calculation**.  

## **Final Complexity Calculation**  
- **Input For Loop** → O(n) (Ignored)  
- **While Loop (Two-Pointer)** → O(n) (Considered)  
- **Output For Loop** → O(n) (Ignored)  

**Final Complexity: O(n)**  

## **Key Takeaways**  
- **Only the procedural phase is considered** in complexity analysis.  
- **Input and output operations are ignored** as they do not impact algorithmic efficiency.  
- **The two-pointer approach runs in O(n) time**, even though it moves from both ends.  
- **Final complexity remains O(n)** because all loops run sequentially, not nested.
