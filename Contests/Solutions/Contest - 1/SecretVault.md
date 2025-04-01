## Explanation :-

The program produces the next prime number of N.

1.Check Whether N is Prime:-
  Boolean function isPrime() analyzes base case and general cases and returns its truth value.

2.Obtain the next Prime Number:-
  Use isPrime() function and keep iterating using a while loop till it returns true(next Prime Number is returned).

## Explanation:
* First of all, take a boolean variable `found` and initialize it to `false`.
* Now, until that variable is `true`, increment `N` by `1` in each iteration and check whether it is prime or not.
* If it is prime, print it and change the value of `found` to `true`. Otherwise, iterate the loop until you get the next prime number.

## Solutions in cpp:-
```cpp
#include <bits/stdc++.h>
using namespace std;
 
// Function that returns true if n 
// is prime else returns false 
bool isPrime(int n) 
{ 
    // Corner cases 
    if (n <= 1)  return false; 
    if (n <= 3)  return true; 
   
    // This is checked so that we can skip  
    // middle five numbers in below loop 
    if (n%2 == 0 || n%3 == 0) return false; 
   
    for (int i=5; i*i<=n; i=i+6) 
        if (n%i == 0 || n%(i+2) == 0) 
           return false; 
   
    return true; 
} 
 
// Function to return the smallest
// prime number greater than N
int nextPrime(int N)
{
 
    // Base case
    if (N <= 1)
        return 2;
 
    int prime = N;
    bool found = false;
 
    // Loop continuously until isPrime returns
    // true for a number greater than n
    while (!found) {
        prime++;
 
        if (isPrime(prime))
            found = true;
    }
 
    return prime;
}
 
// Driver code
int main()
{
    int N = 3;
 
    cout << nextPrime(N);
 
    return 0;
}
```



## Solution in python:-

```python
import math

# Function that returns True if n 
# is prime else returns False 
def isPrime(n):
	
	# Corner cases 
	if(n <= 1):
		return False
	if(n <= 3):
		return True
	
	# This is checked so that we can skip 
	# middle five numbers in below loop 
	if(n % 2 == 0 or n % 3 == 0):
		return False
	
	for i in range(5, int(math.sqrt(n) + 1), 6): 
		if(n % i == 0 or n % (i + 2) == 0):
			return False
	
	return True

# Function to return the smallest 
# prime number greater than N 
def nextPrime(N):

	# Base case 
	if (N <= 1):
		return 2

	prime = N
	found = False

	# Loop continuously until isPrime returns 
	# True for a number greater than n 
	while(not found):
		prime = prime + 1

		if(isPrime(prime) == True):
			found = True

	return prime

# Driver code 
N = 3
print(nextPrime(N))
```