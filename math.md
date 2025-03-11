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

// Method 4: Modified Euclidean Algorithm (Always divide the larger by the smaller)
int gcd_euclidean(int a, int b) {
    while (a != 0 && b != 0) {
        if (a > b) 
            a %= b; // a = a % b (Keep smaller as b)
        else 
            b %= a; // b = b % a (Keep smaller as a)
    }
    return (a == 0) ? b : a;
}

int main() {
    int a = 48, b = 180;
    std::cout << "Iterative GCD: " << gcd_iterative(a, b) << "\n";
    std::cout << "Recursive GCD: " << gcd_recursive(a, b) << "\n";
    std::cout << "Brute Force GCD: " << gcd_bruteforce(a, b) << "\n";
    std::cout << "Modified Euclidean GCD: " << gcd_euclidean(a, b) << "\n";
    std::cout << "Built-in GCD: " << std::__gcd(a, b) << "\n";
    return 0;
}
