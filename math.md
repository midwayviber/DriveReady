# Greatest Common Divisor (GCD)

## Definition
The **Greatest Common Divisor (GCD)** of two numbers is the largest positive integer that divides both numbers without leaving a remainder.

## Examples

### Example 1
**Numbers:** 12, 18  
**Divisors of 12:** {1, 2, 3, 4, 6, 12}  
**Divisors of 18:** {1, 2, 3, 6, 9, 18}  
**Common Divisors:** {1, 2, 3, 6}  
**GCD:** 6

### Example 2
**Numbers:** 48, 180  
**Divisors of 48:** {1, 2, 3, 4, 6, 8, 12, 16, 24, 48}  
**Divisors of 180:** {1, 2, 3, 4, 5, 6, 9, 10, 12, 15, 18, 30, 36, 45, 60, 90, 180}  
**Common Divisors:** {1, 2, 3, 4, 6, 12}  
**GCD:** 12

## Relation Between GCD and Numbers
1. **If GCD(a, b) = 1**, numbers are co-prime (e.g., GCD(8, 15) = 1).
2. **GCD(a, b) × LCM(a, b) = a × b**.
3. **If b divides a, then GCD(a, b) = b**.

## C++ Implementation
### Step-by-Step Explanation
1. **Using Iteration:** Start with `min(a, b)`, check divisibility.
2. **Using Recursion:** Apply `GCD(a, b) = GCD(b, a % b)` until `b == 0`.
3. **Using Brute Force:** Start from `min(a, b)`, decrement until a common divisor is found.
4. **Using Built-in Function:** `__gcd(a, b)` in `<algorithm>`.

```cpp
#include <iostream>
#include <algorithm> // For built-in __gcd function

// Method 1: Iterative approach
int gcd_iterative(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

// Method 2: Recursive approach
int gcd_recursive(int a, int b) {
    if (b == 0)
        return a;
    return gcd_recursive(b, a % b);
}

// Method 3: Brute Force approach
int gcd_bruteforce(int a, int b) {
    int min = (a < b) ? a : b;
    for (int l = min; l >= 1; --l) {
        if (a % l == 0 && b % l == 0)
            return l;
    }
    return 1;
}

int main() {
    int a = 48, b = 180;
    std::cout << "Iterative GCD: " << gcd_iterative(a, b) << "\n";
    std::cout << "Recursive GCD: " << gcd_recursive(a, b) << "\n";
    std::cout << "Brute Force GCD: " << gcd_bruteforce(a, b) << "\n";
    std::cout << "Built-in GCD: " << std::__gcd(a, b) << "\n";
    return 0;
}
```

## Complexity Analysis
- **Iterative & Recursive**: O(log(min(a, b)))
- **Brute Force**: O(min(a, b))
- **Built-in `__gcd`**: Optimized for efficiency

## Summary
- GCD finds the largest common factor.
- It can be solved using iterative, recursive, brute force, or built-in methods.
- GCD helps in LCM calculation and number theory applications.

