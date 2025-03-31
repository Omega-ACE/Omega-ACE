# Jersey Number Of The Team Manager
## QUESTION
We know that prime numbers are positive integers that have exactly two distinct positive divisors. Similarly, we'll call a positive integer t, BRO-prime, if t has exactly three distinct positive divisors. 

In a cricket team,the team manager's jersey number should be a BRO-Prime Number and it should be one of the player's jersey number in the team.You are given the jersey numbers of a 11 player team. For each of them determine whether it is suitable for the team manager's jersey number.
## CONSTRAINTS
1=<JERSEY NUMBER (n) =<10000
## ABOUT THE QUESTION
- This question is adapted from the T-Prime Number Question from codeforces. <br>
https://codeforces.com/problemset/problem/230/B
## APPROACH
- BRO-prime number is defined as a number that has exactly three distinct positive divisors. The only numbers that satisfy this condition are squares of prime numbers.We use this logic to solve this question.
- We use the sieve of eratosthenes method to find the prime numbers from 2 to the root of maximum of all the jersey numbers provided.
- We take each number of the array of jersey numbers provided and check whether the number is a perfect square number and whether the root is a prime number, if this condition satisfies then number is a BRO PRIME NUMBER
## SOLUTION
## PYTHON CODE
``` python
import math
#Finding the primenumbers using sieve method
def findprimesieve(x):
    LIMIT = x+1  
    is_prime = [True] * LIMIT
    is_prime[0] = is_prime[1] = False

    for i in range(2, int(math.sqrt(LIMIT)) + 1):
        if is_prime[i]:
            for j in range(i * i, LIMIT, i):
                is_prime[j] = False
    return is_prime

# Read input
numbers = list(map(int, input().split()))
#Least Number is 1 so taking 0
ln=0
#Getting the maximum number of the given team jersey numbers
for x in numbers:
    if x>ln:
        ln=x
ln=math.isqrt(ln)
is_prime=findprimesieve(ln)
# Checking for BRO-primes
for num in numbers:
    root = math.isqrt(num)
    if root * root == num and is_prime[root]:
        print("YES")
    else:
        print("NO")
```
## C++ CODE
``` cpp
#include <iostream>
#include <vector>
#include <cmath>
using namespace std;

vector<bool> findPrimeSieve(int x) {
    int LIMIT = x + 1;
    vector<bool> is_prime(LIMIT, true);
    is_prime[0] = is_prime[1] = false;
    
    for (int i = 2; i * i < LIMIT; i++) {
        if (is_prime[i]) {
            for (int j = i * i; j < LIMIT; j += i) {
                is_prime[j] = false;
            }
        }
    }
    return is_prime;
}

int main() {
    vector<int> numbers;
    int num;
    while (cin >> num) {
        numbers.push_back(num);
    }
    
    // Finding the maximum number from input
    int ln = 0;
    for (int x : numbers) {
        if (x > ln) ln = x;
    }
    
    ln = sqrt(ln) + 1; // Ensure correct range for sieve
    vector<bool> is_prime = findPrimeSieve(ln);
    
    // Checking for BRO-primes
    for (int num : numbers) {
        int root = sqrt(num);
        if (root * root == num && is_prime[root]) {
            cout << "YES" << endl;
        } else {
            cout << "NO" << endl;
        }
    }
    
    return 0;
}
```
