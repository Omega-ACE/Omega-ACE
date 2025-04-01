## Explanation:

* Initialize a Boolean Variable
    - Take a boolean variable found and initialize it to false.

* Increment Until Prime is Found
    - Until found is true, increment N by 1 in each iteration and check whether it is prime or not.

* Check for Prime
    - If it is prime, print it and change the value of found to true.
    - Otherwise, iterate the loop until you get the next prime number.

* Efficient Calculation
    - Since LCM is computed iteratively using the lcm() function:
        - The time complexity is approximately O(n log M), where M is the maximum number in the array (due to the Euclidean algorithm for GCD).
        - This approach efficiently finds the smallest number that is a multiple of all given numbers.


## Solution in CPP:

```cpp
#include <iostream>
using namespace std;

// Function to calculate Greatest Common Divisor (GCD)
int gcd(int a, int b) {
    if (b == 0) return a;
    return gcd(b, a % b);
}

// Function to calculate Least Common Multiple (LCM)
int lcm(int a, int b) {
    return (a * b) / gcd(a, b);
}

// Solve function
int solve(int n, int cycle[]) {
    int ans = cycle[0]; // Start with the first cycle
    for (int i = 1; i < n; i++) {
        ans = lcm(ans, cycle[i]); // Find LCM iteratively
    }
    return ans;
}

int main(){
    int n = 4;
    int cycle[] = {12,36,30,18};
    cout << solve(n, cycle) << endl;
}
```

## Solution in Python:
```python
def GCD(a, b):
    if b == 0:
        return a
    return GCD(b, a % b)

def LCM(a, b):
    return (a * b) // GCD(a, b)

def solve(n, cycle):
    ans = cycle[0]  # Start with the first cycle
    for i in range(1, n):
        ans = LCM(ans, cycle[i])  # Find LCM iteratively
    return ans

print(solve(4,[12,18,36,30]))

```