# **Greatest Common Divisor (GCD)**  

## **Definition**  
The **Greatest Common Divisor (GCD)** of two numbers is the largest positive integer that divides both numbers without leaving a remainder.  

## **Examples**  

### **Example 1**  
**Numbers:** 12, 18  
- **Divisors of 12:** {1, 2, 3, 4, 6, 12}  
- **Divisors of 18:** {1, 2, 3, 6, 9, 18}  
- **Common Divisors:** {1, 2, 3, 6}  
- **GCD:** 6  

### **Example 2**  
**Numbers:** 48, 180  
- **Divisors of 48:** {1, 2, 3, 4, 6, 8, 12, 16, 24, 48}  
- **Divisors of 180:** {1, 2, 3, 4, 5, 6, 9, 10, 12, 15, 18, 30, 36, 45, 60, 90, 180}  
- **Common Divisors:** {1, 2, 3, 4, 6, 12}  
- **GCD:** 12  

## **Relation Between GCD and Numbers**  
1. **If GCD(a, b) = 1**, numbers are co-prime (e.g., GCD(8, 15) = 1).  
2. **GCD(a, b) × LCM(a, b) = a × b**.  
3. **If b divides a, then GCD(a, b) = b**.  

---

# **C++ Implementation**  

## **1. Iterative Approach**  
- Uses the **Euclidean algorithm**.  
- Swaps values so that the larger number is always divided by the smaller one.  

```cpp
int gcd_iterative(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}
```

**Time Complexity:** O(log(min(a, b)))  

---

## **2. Recursive Approach**  
- Uses recursion to find `GCD(a, b) = GCD(b, a % b)`.  

```cpp
int gcd_recursive(int a, int b) {
    if (b == 0)
        return a;
    return gcd_recursive(b, a % b);
}
```

**Time Complexity:** O(log(min(a, b)))  

---

## **3. Brute Force Approach**  
- Starts from `min(a, b)` and checks divisibility.  

```cpp
int gcd_bruteforce(int a, int b) {
    int minVal = (a < b) ? a : b;
    for (int i = minVal; i >= 1; --i) {
        if (a % i == 0 && b % i == 0)
            return i;
    }
    return 1;
}
```

**Time Complexity:** O(min(a, b))  

---

## **4. Euclidean Algorithm with Swap**  
- Ensures the larger number is divided by the smaller one.  
- Uses `a, b = max(a, b), min(a, b)` before applying the Euclidean algorithm.  

```cpp
int gcd_euclidean_swap(int a, int b) {
    if (a < b) std::swap(a, b); // Ensure a >= b
    while (b != 0) {
        a = a % b;
        std::swap(a, b);
    }
    return a;
}
```

**Time Complexity:** O(log(max(a, b)))  

---

## **5. Built-in Function (`__gcd`)**  
- Uses `<algorithm>` library.  

```cpp
#include <algorithm>
int gcd_builtin(int a, int b) {
    return std::__gcd(a, b);
}
```

**Time Complexity:** O(log(min(a, b)))  

---

# **Full C++ Code**
```cpp
#include <iostream>
#include <algorithm> 

int gcd_iterative(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

int gcd_recursive(int a, int b) {
    if (b == 0)
        return a;
    return gcd_recursive(b, a % b);
}

int gcd_bruteforce(int a, int b) {
    int minVal = (a < b) ? a : b;
    for (int i = minVal; i >= 1; --i) {
        if (a % i == 0 && b % i == 0)
            return i;
    }
    return 1;
}

int gcd_euclidean_swap(int a, int b) {
    if (a < b) std::swap(a, b);
    while (b != 0) {
        a = a % b;
        std::swap(a, b);
    }
    return a;
}

int main() {
    int a = 48, b = 180;
    std::cout << "Iterative GCD: " << gcd_iterative(a, b) << "\n";
    std::cout << "Recursive GCD: " << gcd_recursive(a, b) << "\n";
    std::cout << "Brute Force GCD: " << gcd_bruteforce(a, b) << "\n";
    std::cout << "Euclidean GCD (Swap): " << gcd_euclidean_swap(a, b) << "\n";
    std::cout << "Built-in GCD: " << std::__gcd(a, b) << "\n";
    return 0;
}
```

---

# **Time Complexity Comparison**
| **Method**                | **Time Complexity**            |
|---------------------------|--------------------------------|
| Iterative Approach        | O(log(min(a, b)))             |
| Recursive Approach        | O(log(min(a, b)))             |
| Brute Force Approach      | O(min(a, b))                  |
| Euclidean Algorithm (Swap)| O(log(max(a, b)))             |
| Built-in `__gcd`          | O(log(min(a, b)))             |

Here are the complete markdown notes for **LCM** with explanations, formulas, and C++ implementations.  

---

# **Least Common Multiple (LCM)**  

## **Definition**  
The **Least Common Multiple (LCM)** of two numbers is the smallest positive integer that is **divisible by both numbers**.  

## **Examples**  

### **Example 1**  
**Numbers:** 4, 6  
- **Multiples of 4:** {4, 8, 12, 16, 20, 24, ...}  
- **Multiples of 6:** {6, 12, 18, 24, 30, ...}  
- **Common Multiples:** {12, 24, ...}  
- **LCM:** 12  

### **Example 2**  
**Numbers:** 15, 25  
- **Multiples of 15:** {15, 30, 45, 60, 75, ...}  
- **Multiples of 25:** {25, 50, 75, 100, ...}  
- **Common Multiples:** {75, 150, ...}  
- **LCM:** 75  

---

# **LCM Formula**  
LCM can be calculated using **GCD (Greatest Common Divisor)**:  

\[
LCM(a, b) = \frac{a \times b}{GCD(a, b)}
\]

This formula is efficient because **GCD(a, b) × LCM(a, b) = a × b**.  

---

# **C++ Implementations**  

## **1. Using the Formula (`LCM = (a * b) / GCD`)**  
- Uses the **Euclidean algorithm** for GCD first, then calculates LCM.  

```cpp
int gcd(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

int lcm(int a, int b) {
    return (a / gcd(a, b)) * b; // Avoids integer overflow
}
```

**Time Complexity:** O(log(min(a, b)))  

---

## **2. Iterative Approach (Checking Multiples)**  
- Finds **LCM by checking multiples** of `max(a, b)`.  

```cpp
int lcm_iterative(int a, int b) {
    int maxVal = (a > b) ? a : b;
    while (true) {
        if (maxVal % a == 0 && maxVal % b == 0)
            return maxVal;
        maxVal++;
    }
}
```

**Time Complexity:** O(a × b) (worst case, very slow)  

---

## **3. Brute Force (Finding Smallest Common Multiple)**  
- Loops from `max(a, b)` to `a × b`.  

```cpp
int lcm_bruteforce(int a, int b) {
    int maxVal = (a > b) ? a : b;
    for (int i = maxVal; i <= a * b; i++) {
        if (i % a == 0 && i % b == 0)
            return i;
    }
    return a * b; // Worst case
}
```

**Time Complexity:** O(a × b)  

---

## **4. Built-in Function (`std::lcm` in C++17)**  
- Uses `<numeric>` header in **C++17 and above**.  

```cpp
#include <numeric>
int lcm_builtin(int a, int b) {
    return std::lcm(a, b);
}
```

**Time Complexity:** O(log(min(a, b)))  

---

# **Full C++ Code**
```cpp
#include <iostream>
#include <numeric> 

int gcd(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

int lcm(int a, int b) {
    return (a / gcd(a, b)) * b;
}

int lcm_iterative(int a, int b) {
    int maxVal = (a > b) ? a : b;
    while (true) {
        if (maxVal % a == 0 && maxVal % b == 0)
            return maxVal;
        maxVal++;
    }
}

int lcm_bruteforce(int a, int b) {
    int maxVal = (a > b) ? a : b;
    for (int i = maxVal; i <= a * b; i++) {
        if (i % a == 0 && i % b == 0)
            return i;
    }
    return a * b;
}

int main() {
    int a = 15, b = 25;
    std::cout << "LCM using formula: " << lcm(a, b) << "\n";
    std::cout << "LCM using iterative: " << lcm_iterative(a, b) << "\n";
    std::cout << "LCM using brute force: " << lcm_bruteforce(a, b) << "\n";
    std::cout << "LCM using built-in (C++17+): " << std::lcm(a, b) << "\n";
    return 0;
}
```

---

# **Time Complexity Comparison**
| **Method**                | **Time Complexity**            |
|---------------------------|--------------------------------|
| LCM using GCD formula     | O(log(min(a, b)))             |
| Iterative Approach        | O(a × b)                      |
| Brute Force Approach      | O(a × b)                      |
| Built-in `std::lcm` (C++17+)| O(log(min(a, b)))           |

---

# **Summary**
- **LCM** finds the smallest number divisible by both `a` and `b`.  
- The best way to compute **LCM** is:  
  1. **Using `LCM = (a * b) / GCD(a, b)`** (Most efficient).  
  2. **Iterative method (Checking multiples)** (Slow).  
  3. **Brute force (Looping from `max(a, b)` to `a × b`)** (Very slow).  
  4. **Built-in `std::lcm` (Fastest, but requires C++17+).**  

