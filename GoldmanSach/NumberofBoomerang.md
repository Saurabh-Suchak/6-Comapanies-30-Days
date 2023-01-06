# Number of Boomerangs

link - https://leetcode.com/problems/number-of-boomerangs/description/

### Problem Statement - 
You are given n points in the plane that are all distinct, where points[i] = [xi, yi]. A boomerang is a tuple of points (i, j, k) such that the distance between i and j equals the distance between i and k (the order of the tuple matters).

Return the number of boomerangs.

### Sample Input
```
points = [[0,0],[1,0],[2,0]]
```
### Sample Output
```
2
Explanation: The two boomerangs are [[1,0],[0,0],[2,0]] and [[1,0],[2,0],[0,0]].
```

### Solution

```cpp


class Solution {
public:
    int numberOfBoomerangs(vector<vector<int>>& points) {
        if(points.size()<3)return 0;
        unordered_map<int,int>mp;
        int count=0;

        for(int i=0;i<points.size();i++){
            mp.clear();
            for(int j=0;j<points.size();j++){
                if(j==i){continue;}
                int d=pow(points[i][0]-points[j][0],2) + pow(points[i][1]-points[j][1],2);
                mp[d]++;
            }

            for(auto& m:mp){
                if(m.second>=2)count=count+m.second*(m.second-1)/2;
            }
        }return 2*count;
    }
};

```