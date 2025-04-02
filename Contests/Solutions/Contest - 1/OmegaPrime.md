## Explanation:
1. Prime Number Check (`is_prime` function) 
   - The function `is_prime(num)` checks whether a given number is prime.  
   - It returns `False` for numbers less than 2.  
   - It iterates from `2` to `sqrt(num)`, checking divisibility. If `num` is divisible by any number in this range, it returns `False`; otherwise, it returns `True`.  

2. LCM Computation for Pairs
   - The function `is_omega_prime(n, arr)` initializes `min_lcm` to infinity and `max_lcm` to 0.  
   - It iterates through all pairs `(i, j)` in the array and calculates their LCM using `math.lcm(arr[i], arr[j])`.  
   - It keeps track of the smallest and largest LCM values found.  

3. Checking the Difference 
   - After computing `min_lcm` and `max_lcm`, it calculates their difference: `max_lcm - min_lcm`.  
   - It then checks whether this difference is a prime number using the `is_prime` function.  

4. Final Output 
   - If the difference is prime, it returns `"YES"`; otherwise, it returns `"NO"`.  
   - The program reads input values, computes the result using `is_omega_prime(n, arr)`, and prints the final answer.



## Solution in CPP:

```cpp
#include <iostream>
#include <vector>
#include <cmath>
#include <limits>
using namespace std;

// Function to check if a number is prime
bool is_prime(int num) {
    if (num < 2) return false;
    for (int i = 2; i <= sqrt(num); i++) {
        if (num % i == 0) return false;
    }
    return true;
}

// Function to compute the LCM of two numbers
int lcm(int a, int b) {
    return (a / __gcd(a, b)) * b;
}

// Function to determine if Omega Prime condition holds
string is_omega_prime(int n, vector<int>& arr) {
    int min_lcm = numeric_limits<int>::max();
    int max_lcm = 0;
    
    // Compute all possible LCMs for pairs (i, j)
    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            int lcm_val = lcm(arr[i], arr[j]);
            min_lcm = min(min_lcm, lcm_val);
            max_lcm = max(max_lcm, lcm_val);
        }
    }
    
    // Check if the difference is prime
    return is_prime(max_lcm - min_lcm) ? "YES" : "NO";
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    cout << is_omega_prime(n, arr) << endl;
    return 0;
}
```

## Solution in Python:

```python
import math

def is_prime(num):
    if num < 2:
        return False
    for i in range(2, int(math.sqrt(num)) + 1):
        if num % i == 0:
            return False
    return True

def is_omega_prime(n, arr):
    min_lcm = float('inf')
    max_lcm = 0
    
    # Compute all possible LCMs for pairs (i, j)
    for i in range(n):
        for j in range(i + 1, n):
            lcm_val = math.lcm(arr[i], arr[j])
            min_lcm = min(min_lcm, lcm_val)
            max_lcm = max(max_lcm, lcm_val)
    
    # Check if the difference is prime
    return "YES" if is_prime(max_lcm - min_lcm) else "NO"

# Input reading
n = int(input())
arr = list(map(int, input().split()))

# Output result
print(is_omega_prime(n, arr))
```