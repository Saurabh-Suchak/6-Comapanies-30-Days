# Top k freq words

link - https://leetcode.com/problems/top-k-frequent-words/description/

### Problem Statement - 

Given an array of strings words and an integer k, return the k most frequent strings.

Return the answer sorted by the frequency from highest to lowest. Sort the words with the same frequency by their lexicographical order.

 


### Sample Input
```
words = ["i","love","leetcode","i","love","coding"], k = 2
```
### Sample Output
```
["i","love"]
Explanation: "i" and "love" are the two most frequent words.
Note that "i" comes before "love" due to a lower alphabetical order.

```


### Solution

```cpp
class Solution {
public:
    
     static bool comparator(pair<string,int> p1, pair<string,int> p2)
    {
        if(p1.second>p2.second || (p1.second==p2.second && p1.first<p2.first))
            return true;
        return false;
    }
    
    vector<string> topKFrequent(vector<string>& words, int k) {
        unordered_map<string,int> m1;
        
        for(int i=0; i<words.size(); i++)
            m1[words[i]]++;
        
        vector<pair<string,int>> v1;
        for(auto it=m1.begin(); it!=m1.end(); it++)
            v1.push_back({it->first,it->second});
        
        sort(v1.begin(),v1.end(),comparator);
        
        vector<string> ans;
        for(int i=0; i<k; i++)
        {
            ans.push_back(v1[i].first);
        }
        
        return ans;
    }
};

```