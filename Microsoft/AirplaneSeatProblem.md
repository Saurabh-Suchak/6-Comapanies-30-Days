# Airplane seat problem

link - https://leetcode.com/problems/airplane-seat-assignment-probability/description/

### Problem Statement - 

n passengers board an airplane with exactly n seats. The first passenger has lost the ticket and picks a seat randomly. But after that, the rest of the passengers will:

Take their own seat if it is still available, and
Pick other seats randomly when they find their seat occupied
Return the probability that the nth person gets his own seat.

### Sample Input
```
n = 1
```
### Sample Output
```
 1.00000
Explanation: The first person can only get the first seat.
```



### Solution
```cpp
class Solution {
public:
    double nthPersonGetsNthSeat(int n) {
        if(n==1)return 1;
        else return 0.5;
    }
};
```
