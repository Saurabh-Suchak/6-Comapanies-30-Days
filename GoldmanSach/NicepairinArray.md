# Number of Nicepairs in Array

link - https://leetcode.com/problems/count-nice-pairs-in-an-array/description/

### Problem Statement - 

You are given an array nums that consists of non-negative integers. Let us define rev(x) as the reverse of the non-negative integer x. For example, rev(123) = 321, and rev(120) = 21. A pair of indices (i, j) is nice if it satisfies all of the following conditions:

0 <= i < j < nums.length
nums[i] + rev(nums[j]) == nums[j] + rev(nums[i])
Return the number of nice pairs of indices. Since that number can be too large, return it modulo 109 + 7.

### Sample Input
```
Input: nums = [42,11,1,97]
```
### Sample Output
```
2
Explanation: The two pairs are:
 - (0,3) : 42 + rev(97) = 42 + 79 = 121, 97 + rev(42) = 97 + 24 = 121.
 - (1,2) : 11 + rev(1) = 11 + 1 = 12, 1 + rev(11) = 1 + 11 = 12
```

### Solution

```cpp
class Solution {
public:
int rev(int n){
	int rev_num = 0;
  while (n != 0) {
    rev_num = rev_num * 10 + n % 10;
    n = n / 10;
  }return rev_num;
}

    int countNicePairs(vector<int>& nums) {
	long count = 0;
	unordered_map<int, long> mp;

	for(auto& num : nums) mp[num - rev(num)]++;

	for(auto& pair : mp){
        count = (count + (pair.second * (pair.second - 1)) / 2) % 1000000007;
    }  
		 
	return count;
}
};
```