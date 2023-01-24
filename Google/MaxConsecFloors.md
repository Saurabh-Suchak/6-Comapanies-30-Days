# Max consecutive floors without special floor

link - https://leetcode.com/problems/maximum-consecutive-floors-without-special-floors/description/

### Problem Statement - 

Alice manages a company and has rented some floors of a building as office space. Alice has decided some of these floors should be special floors, used for relaxation only.

You are given two integers bottom and top, which denote that Alice has rented all the floors from bottom to top (inclusive). You are also given the integer array special, where special[i] denotes a special floor that Alice has designated for relaxation.

Return the maximum number of consecutive floors without a special floor.


### Sample Input
```
 bottom = 2, top = 9, special = [4,6]
```
### Sample Output
```
The following are the ranges (inclusive) of consecutive floors without a special floor:
- (2, 3) with a total amount of 2 floors.
- (5, 5) with a total amount of 1 floor.
- (7, 9) with a total amount of 3 floors.
Therefore, we return the maximum number which is 3 floors.

```


### Solution

```cpp

class Solution {
public:
    int maxConsecutive(int bottom, int top, vector<int>& special) {
        int ans=0;
        sort(special.begin(),special.end());
        for(int i=1;i<special.size();i++){
            ans=max(ans,special[i]-special[i-1]-1);
        }
        return max({ans,special[0]-bottom,top-special[special.size()-1]});

    }
};
```