# Bulls and Cows

link - https://leetcode.com/problems/bulls-and-cows/description/

### Problem Statement - 

You are playing the Bulls and Cows game with your friend.

You write down a secret number and ask your friend to guess what the number is. When your friend makes a guess, you provide a hint with the following info:

The number of "bulls", which are digits in the guess that are in the correct position.
The number of "cows", which are digits in the guess that are in your secret number but are located in the wrong position. Specifically, the non-bull digits in the guess that could be rearranged such that they become bulls.
Given the secret number secret and your friend's guess guess, return the hint for your friend's guess.

The hint should be formatted as "xAyB", where x is the number of bulls and y is the number of cows. Note that both secret and guess may contain duplicate digits.

### Sample Input
```
secret = "1807", guess = "7810"
```
### Sample Output
```
"1A3B"
```

### Solution

```cpp
class Solution {
public:
    string getHint(string secret, string guess) {
        int x=0,y=0;
        unordered_map<char,int>mp;
        for(int i=0;i<secret.size();i++){
            if(secret[i]==guess[i]){x++;}
            mp[secret[i]]++;
        }

        for(auto z : guess){
            if(mp[z]>0){
                y++;
                mp[z]--;
            }
        }
        y = y-x;

        string ans=to_string(x)+"A"+to_string(y)+"B";
        return ans; 
    }
};

```