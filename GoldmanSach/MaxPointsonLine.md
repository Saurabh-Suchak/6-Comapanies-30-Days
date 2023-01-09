# Max Points on a Line

link - https://leetcode.com/problems/max-points-on-a-line/description/

### Problem Statement - 
Given an array of points where points[i] = [xi, yi] represents a point on the X-Y plane, return the maximum number of points that lie on the same straight line.

Return the number of boomerangs.

### Sample Input
```
points = [[1,1],[2,2],[3,3]]
```
### Sample Output
```
3
```

### Solution

```cpp

// take a single point and find slope to all from it, store in map and find max

class Solution {
public:
    int maxPoints(vector<vector<int>> &points) {
    int ans=1;
    for(int i = 0; i < points.size(); i++){
        unordered_map<double, int> map;
        for(int j = i + 1; j < points.size(); j++){
            if(points[i][0] == points[j][0]){
                map[INT_MAX]++;
            }
            else{
                double slope = double(points[i][1] - points[j][1]) / double(points[i][0] - points[j][0]);
                map[slope]++;
            }
        }
        
        for(auto it:map){
            ans=max(ans,it.second+1);
        }
    
    return ans;
    }
};

```