# Minimum Deletions to Make Array Divisible

link - https://leetcode.com/problems/minimum-deletions-to-make-array-divisible/description/

### Problem Statement - 

You are given two positive integer arrays nums and numsDivide. You can delete any number of elements from nums.

Return the minimum number of deletions such that the smallest element in nums divides all the elements of numsDivide. If this is not possible, return -1.

Note that an integer x divides y if y % x == 0.

### Sample Input
```
nums = [2,3,2,4,3], numsDivide = [9,6,9,3,15]
```
### Sample Output
```
 2
Explanation: 
The smallest element in [2,3,2,4,3] is 2, which does not divide all the elements of numsDivide.
We use 2 deletions to delete the elements in nums that are equal to 2 which makes nums = [3,4,3].
The smallest element in [3,4,3] is 3, which divides all the elements of numsDivide.
It can be shown that 2 is the minimum number of deletions needed.
```

### Solution-1 (brute force)  accepted

```cpp
class Solution {
public:
    int minOperations(vector<int>& nums, vector<int>& numsDivide) {
        sort(nums.begin(),nums.end());
// check if 0 del required
        int z=1;
        for(int j=0;j<numsDivide.size();j++){
            if(numsDivide[j]%nums[0]!=0){z=0;break;}
        }
        if(z==1)return 0;
// check for del other than 0
        for(int i=1;i<nums.size();i++){
            int flag=1;
            // if same consecutive number then skip calculating
            if(nums[i]==nums[i-1]){continue;}
            for(int j=0;j<numsDivide.size();j++){
                if(numsDivide[j]%nums[i]!=0){flag=0;break;}
            }
            if(flag==1)return i;
        }return -1;
    }
};

```

### Solution-2 (using gcd)

```cpp

class Solution {
public:
int minOperations(vector<int>& nums, vector<int>& numsDivide) {
        int hcf = numsDivide[0];
        for (auto& a: numsDivide)
            hcf = gcd(g, a);
        sort(nums.begin(), nums.end());
        for (int i = 0; i < nums.size() && nums[i] <= hcf; i++)
            if (hcf % nums[i] == 0)
                return i;
        return -1;
    }
}

```