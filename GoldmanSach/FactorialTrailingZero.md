# Factorial Trailing zero

link - https://leetcode.com/problems/factorial-trailing-zeroes/description/

### Problem Statement - 

Given an integer n, return the number of trailing zeroes in n!.

Note that n! = n * (n - 1) * (n - 2) * ... * 3 * 2 * 1.

### Sample Input
```
n=3
```
### Sample Output
```
0
```

### Solution

```cpp
class Solution {
public:
    int trailingZeroes(int n) {
        int x=5,zero=0;
        while((n/x)>0){
            zero+=(n/x);
            x*=5;
        }
        return zero;   
    }
};
```