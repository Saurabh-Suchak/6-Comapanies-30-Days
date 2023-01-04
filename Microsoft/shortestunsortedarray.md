# Shortest Unsorted Continuous SubArray 

link - https://leetcode.com/problems/shortest-unsorted-continuous-subarray/description/

### Problem Statement - 
Given an integer array nums, you need to find one continuous subarray that if you only sort this subarray in ascending order, then the whole array will be sorted in ascending order.

Return the shortest such subarray and output its length.

### Sample Input
```
nums = [2,6,4,8,10,9,15]
```
### Sample Output
```
5
Explanation: You need to sort [6, 4, 8, 10, 9] in ascending order to make the whole array sorted in ascending order.
```

### Solution 1 (sorting) - nlogn time complexity

```cpp
class Solution {
public:
    int findUnsortedSubarray(vector<int>& nums) {int c=0;
        vector<int>copy=nums;int mini=0;
        int maxi=0;

        sort(nums.begin(),nums.end());

        for(int i=0;i<nums.size();i++){
            if(copy[i]!=nums[i]){
                mini=i;break;}}

        for(int i=nums.size()-1;i>=0;i--){
            if(copy[i]!=nums[i]){
                maxi=i;break;}}

        
        if(mini==0 && maxi==0)return 0;
        else return maxi-mini+1;
    }
};

```


### Solution 2  - n time complexity