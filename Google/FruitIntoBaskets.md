# Fruit into Baskets

link - https://leetcode.com/problems/fruit-into-baskets/description/

### Problem Statement - 

You are visiting a farm that has a single row of fruit trees arranged from left to right. The trees are represented by an integer array fruits where fruits[i] is the type of fruit the ith tree produces.

You want to collect as much fruit as possible. However, the owner has some strict rules that you must follow:

You only have two baskets, and each basket can only hold a single type of fruit. There is no limit on the amount of fruit each basket can hold.
Starting from any tree of your choice, you must pick exactly one fruit from every tree (including the start tree) while moving to the right. The picked fruits must fit in one of your baskets.
Once you reach a tree with fruit that cannot fit in your baskets, you must stop.
Given the integer array fruits, return the maximum number of fruits you can pick.

### Sample Input
```
fruits = [1,2,1]
```
### Sample Output
```
3

```


### Solution

```cpp
class Solution {
public:
    int totalFruit(vector<int>& tree) {
        unordered_map<int,int> m;
        int n=tree.size();
        int l=0,r=0,ma=0,ct=0;
        while(r<n){
            if(m[tree[r]]==0) ct++;
            m[tree[r]]++;
            r++;
            while(l<r && ct>2){
                m[tree[l]]--;
                if(m[tree[l]]==0) ct--;
                l++;
            }
            ma=max(ma,r-l);
        }
        return ma;
        
    }
};
```