# Micro 
1. Minimum adjacent swap required to make a string palindrome.
(solutionhttps://stackoverflow.com/questions/51796237/minimum-number-of-swaps-to-convert-a-string-to-palindrome?fbclid=IwAR0cd5QgtoVZHHyuoCspcI7KDVhjA8VdqmytEqQLyOSmCWXRi6tcql7fj60)
https://www.codechef.com/problems/ENCD12
https://www.codechef.com/viewsolution/26846686

Solution: Iska solution samjh nhi aarha

2. https://www.geeksforgeeks.org/closest-pair-of-points-using-divide-and-conquer-algorithm/

Solution:

3. https://leetcode.com/problems/longest-substring-without-repeating-characters/
```cpp
  int lengthOfLongestSubstring(string s) {
        unordered_set<char> uset;
        int res = 0;
        int ws=0, we=0;
        int n = s.length();
        
        while(ws<n and we<n) {
            if(uset.find(s[we]) == uset.end()) {
                uset.insert(s[we]);
                we+=1;
                res = max(res, (int)uset.size());
            }
            else {
                uset.erase(s[ws]);
                ws += 1;
            }
        }
        
        return res;
    }
```
