# **1. Time Complexity**

## **Definition:**
Time Complexity refers to the amount of time taken by an algorithm to run as a function of the input size (n). It helps in evaluating the efficiency of an algorithm.

---

# **2. Example: Finding the number of even numbers from `1` to `N`**

### **Approach 1: Using a Loop (O(n))**
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

---

### **Approach 2: Using Formula (O(1))**
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

# **3. Big O, Theta (Θ), and Omega (Ω) Notations**

## **3.1 Big O Notation (O)**
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

## **3.2 Theta Notation (Θ)**
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

## **3.3 Omega Notation (Ω)**
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

---

# **4. Common Time Complexities with Examples**

## **4.1 O(1) - Constant Time**
- Example: Picking a book from a shelf.
- Code Analogy: Accessing an element in an array.
```cpp
int getFirstElement(vector<int> &arr) {
    return arr[0]; // Always takes the same time, no matter the size of arr
}
```

---

## **4.2 O(n) - Linear Time**
- Example: Reading a book page by page.
- Code Analogy: Traversing an array.
```cpp
void printArray(vector<int> &arr) {
    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " ";
    }
}
```

---

## **4.3 O(log n) - Logarithmic Time**
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

---

## **4.4 O(n²) - Quadratic Time**
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

---

## **4.5 O(n³) - Cubic Time**
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

---

## **4.6 O(n log n) - Linearithmic Time**
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

---

## **4.7 O(n!) - Factorial Time**
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

---

# **5. Time Complexity Calculation: Procedural Phase Only**

## **5.1 Why Don't We Add Time Complexities?**
- When analyzing time complexity, we focus only on the **procedural phase** (core logic of the algorithm).  
- Input (I/O) operations like reading values or printing results are generally **O(1) or O(n)** and are **not considered** in complexity calculations.  
- We do **not add complexities**; instead, we take the **dominant term** (the highest order of growth).  

---

## **5.2 Code Example**
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

---

## **5.3 Step-by-Step Complexity Analysis**

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

---

## **5.4 Final Complexity Calculation**
- **Input For Loop** → O(n) (Ignored)  
- **While Loop (Two-Pointer)** → O(n) (Considered)  
- **Output For Loop** → O(n) (Ignored)  

**Final Complexity: O(n)**  

---

## **5.5 Key Takeaways**
- **Only the procedural phase is considered** in complexity analysis.  
- **Input and output operations are ignored** as they do not impact algorithmic efficiency.  
- **The two-pointer approach runs in O(n) time**, even though it moves from both ends.  
- **Final complexity remains O(n)** because all loops run sequentially, not nested.

---

# **6. Recursion and Time Complexity**

## **6.1 Print Numbers from 1 to N (O(n))**
```cpp
#include <iostream>
using namespace std;

void printNumbers(int n) {
    if (n == 0) return;  
    printNumbers(n - 1);  
    cout << n << " ";  
}

int main() {
    int n = 10;
    cout << "Numbers from 1 to " << n << ": ";
    printNumbers(n);
    cout << endl;
    return 0;
}
```
- **Time Complexity: O(n)**  
- **Reason:** The function calls itself `n` times, and each call does O(1) work.

---

## **6.2 Sum of First N Numbers (O(n))**
```cpp
#include <iostream>
using namespace std;

int sum(int n) {
    if (n == 0) return 0;
    return n + sum(n - 1);
}

int main() {
    int n = 10;
    cout << "Sum of first " << n << " numbers: " << sum(n) << endl;
    return 0;
}
```
- **Time Complexity: O(n)**  
- **Reason:** The function calls itself `n` times, and each call does O(1) work.

---

## **6.3 Print Even Numbers from N to 0 (O(n))**
```cpp
#include <iostream>
using namespace std;

void printEven(int n) {
    if (n <= 0) return;
    printEven(n - 2);
    cout << n << " ";
}

int main() {
    int n = 10;
    cout << "Even numbers from " << n << " to 0: ";
    printEven(n);
    cout << endl;
    return 0;
}
```
- **Time Complexity: O(n)**  
- **Reason:** The function reduces `n` by 2 each time, resulting in `n/2` calls. Since O(n/2) = O(n).

---

## **6.4 Multiplication using Addition (O(n))**
```cpp
#include <iostream>
using namespace std;

int multiply(int a, int b) {
    if (b == 0) return 0;
    return a + multiply(a, b - 1);
}

int main() {
    int a = 5, b = 3;
    cout << "Multiplication of " << a << " and " << b << ": " << multiply(a, b) << endl;
    return 0;
}
```
- **Time Complexity: O(n)**  
- **Reason:** The function calls itself `b` times, and each call does O(1) work.

---

## **6.5 Factorial of a Number (O(n))**
```cpp
#include <iostream>
using namespace std;

int factorial(int n) {
    if (n == 0) return 1;
    return n * factorial(n - 1);
}

int main() {
    int n = 5;
    cout << "Factorial of " << n << ": " << factorial(n) << endl;
    return 0;
}
```
- **Time Complexity: O(n)**  
- **Reason:** The function calls itself `n` times, and each call does O(1) work.

---

### **1. Brute Force Approach**
The simplest way to check if a number `n` is prime is to test divisibility by all integers from `2` to `n-1`.

**Code:**
```cpp
#include <iostream>
using namespace std;

bool isPrimeBruteForce(int n) {
    if (n <= 1) return false;
    for (int i = 2; i < n; i++) {
        if (n % i == 0) return false;
    }
    return true;
}

int main() {
    int n = 29;
    if (isPrimeBruteForce(n))
        cout << n << " is prime." << endl;
    else
        cout << n << " is not prime." << endl;
    return 0;
}
```

**Time Complexity:**  
- **Worst Case:** \( O(n) \)  
- **Explanation:** The loop runs from `2` to `n-1`, so for large `n`, this is inefficient.

---

### **2. Optimize Loop Range (Up to √n)**
If `n` is not prime, it must have at least one divisor less than or equal to `√n`. So, we only need to check divisibility up to `√n`.

**Code:**
```cpp
#include <iostream>
#include <cmath>
using namespace std;

bool isPrimeOptimized(int n) {
    if (n <= 1) return false;
    for (int i = 2; i <= sqrt(n); i++) {
        if (n % i == 0) return false;
    }
    return true;
}

int main() {
    int n = 29;
    if (isPrimeOptimized(n))
        cout << n << " is prime." << endl;
    else
        cout << n << " is not prime." << endl;
    return 0;
}
```

**Time Complexity:**  
- **Worst Case:** \( O(\sqrt{n}) \)  
- **Explanation:** The loop now runs from `2` to `√n`, which is significantly faster for large `n`.

---

### **3. Skip Even Numbers (Except 2)**
All even numbers greater than `2` are not prime. So, we can skip even numbers after checking for divisibility by `2`.

**Code:**
```cpp
#include <iostream>
#include <cmath>
using namespace std;

bool isPrimeSkipEvens(int n) {
    if (n <= 1) return false;
    if (n == 2) return true;
    if (n % 2 == 0) return false;
    for (int i = 3; i <= sqrt(n); i += 2) { // Check only odd numbers
        if (n % i == 0) return false;
    }
    return true;
}

int main() {
    int n = 29;
    if (isPrimeSkipEvens(n))
        cout << n << " is prime." << endl;
    else
        cout << n << " is not prime." << endl;
    return 0;
}
```

**Time Complexity:**  
- **Worst Case:** \( O(\sqrt{n}) \)  
- **Explanation:** The loop now runs only for odd numbers, reducing the number of iterations by half.

---

### **4. Use 6k ± 1 Optimization**
All primes greater than `3` are of the form `6k ± 1`. This further reduces the number of iterations.

**Code:**
```cpp
#include <iostream>
#include <cmath>
using namespace std;

bool isPrime6kOptimized(int n) {
    if (n <= 1) return false;
    if (n <= 3) return true;
    if (n % 2 == 0 || n % 3 == 0) return false;
    for (int i = 5; i * i <= n; i += 6) {
        if (n % i == 0 || n % (i + 2) == 0) return false;
    }
    return true;
}

int main() {
    int n = 29;
    if (isPrime6kOptimized(n))
        cout << n << " is prime." << endl;
    else
        cout << n << " is not prime." << endl;
    return 0;
}
```

**Time Complexity:**  
- **Worst Case:** \( O(\sqrt{n}) \)  
- **Explanation:** The loop now checks only numbers of the form `6k ± 1`, reducing the number of iterations further.

---

### **5. Sieve of Eratosthenes (Precompute Primes)**
If you need to check primality for multiple numbers, precompute primes using the Sieve of Eratosthenes.

**Code:**
```cpp
#include <iostream>
#include <vector>
#include <cmath>
using namespace std;

vector<bool> sieveOfEratosthenes(int limit) {
    vector<bool> sieve(limit + 1, true);
    sieve[0] = sieve[1] = false;
    for (int i = 2; i <= sqrt(limit); i++) {
        if (sieve[i]) {
            for (int j = i * i; j <= limit; j += i) {
                sieve[j] = false;
            }
        }
    }
    return sieve;
}

bool isPrimeSieve(int n, vector<bool>& sieve) {
    if (n <= sieve.size() - 1) return sieve[n];
    else {
        // Fallback to optimized method for numbers > limit
        if (n <= 1) return false;
        if (n <= 3) return true;
        if (n % 2 == 0 || n % 3 == 0) return false;
        for (int i = 5; i * i <= n; i += 6) {
            if (n % i == 0 || n % (i + 2) == 0) return false;
        }
        return true;
    }
}

int main() {
    int limit = 100;
    vector<bool> sieve = sieveOfEratosthenes(limit);

    int n = 29;
    if (isPrimeSieve(n, sieve))
        cout << n << " is prime." << endl;
    else
        cout << n << " is not prime." << endl;
    return 0;
}
```

**Time Complexity:**  
- **Precomputation:** \( O(n \log \log n) \)  
- **Query:** \( O(1) \) for numbers ≤ limit, \( O(\sqrt{n}) \) for numbers > limit.

---

### **Summary of Optimizations**
1. **Brute Force:** \( O(n) \)  
2. **Optimize Loop Range (√n):** \( O(\sqrt{n}) \)  
3. **Skip Even Numbers:** \( O(\sqrt{n}) \) (but fewer iterations)  
4. **6k ± 1 Optimization:** \( O(\sqrt{n}) \) (even fewer iterations)  
5. **Sieve of Eratosthenes:** \( O(n \log \log n) \) for precomputation, \( O(1) \) for queries.

---

### **Most Optimized Approach**
For a single query, use the **6k ± 1 optimization**. For multiple queries, use the **Sieve of Eratosthenes**.
