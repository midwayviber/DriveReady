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



