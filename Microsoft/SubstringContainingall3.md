# Number of Substrings containing all 3 Characters

link - https://leetcode.com/problems/number-of-substrings-containing-all-three-characters/description/

### Problem Statement - 

Given a string s consisting only of characters a, b and c.

Return the number of substrings containing at least one occurrence of all these characters a, b and c.


### Sample Input
```
s = "abcabc"
```
### Sample Output
```
10
Explanation: The substrings containing at least one occurrence of the characters a, b and c are "abc", "abca", "abcab", "abcabc", "bca", "bcab", "bcabc", "cab", "cabc" and "abc" (again). 
```

### Solution

```cpp
class Solution {
public:
    int numberOfSubstrings(string s) {
        
        int left = 0 , right = 0 , end = s.size() - 1;
        unordered_map<char,int> map;
        
        int count = 0;
        
        while(right != s.size())
        {
            map[s[right]] += 1; 
            
            while(map['a'] && map['b'] && map['c'])
            {
                count += 1 + (end - right);
                
				
                map[s[left]] -= 1; 
                left++;
            }
            right++;
        }
        return count;
    }
};

```