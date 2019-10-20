# Micro 
1. Minimum adjacent swap required to make a string palindrome.
(solutionhttps://stackoverflow.com/questions/51796237/minimum-number-of-swaps-to-convert-a-string-to-palindrome?fbclid=IwAR0cd5QgtoVZHHyuoCspcI7KDVhjA8VdqmytEqQLyOSmCWXRi6tcql7fj60)
https://www.codechef.com/problems/ENCD12
https://www.codechef.com/viewsolution/26846686

Solution: Iska solution samjh nhi aarha

2. https://www.geeksforgeeks.org/closest-pair-of-points-using-divide-and-conquer-algorithm/

Solution:http://people.csail.mit.edu/indyk/6.838-old/handouts/lec17.pdf 
        isme bahut sahi description hai

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
# Samsu

1.https://www.geeksforgeeks.org/greedy-algorithm-to-find-minimum-number-of-coins/

2.minimum-absolute-difference-between-2-non-contiguous-equal-subarrays
sol.
```
int mindifference(int *arr, int n){
        set<int>st1,st2;
        sort(arr, arr+n);
        int i = 0, j = n-1;
        bool in = true;
        while(i<j){
               if(in){
                        st1.insert(arr[i++]);
                        st1.insert(arr[j--]);
                        in = false;
               }
               else{
                        st2.insert(arr[i++]);
                        st2.insert(arr[j--]);
                        in = true;  
               }
        }
        int sum1 = 0, sum2 = 0;
        for(auto x:st1){
                sum1 += x;
        }
        for(auto x:st2){
                sum2 += x;
        }
        
        return abs(abs(sum1 -sum2) - arr[i]);
}
```

3.count nodes of subtrees of another subtree
sol.
```
int count(TreeNode* tree){
        if(tree == NULL)
             return 0;
        return count(tree->left)+count(tree->right)+1;
}
bool isSame(TreeNode* s, TreeNode* t){
        if(s==nullptr && t==nullptr){
            return true;
        }
        if(s==nullptr || t==nullptr ){
            return false;
        }
        if(s->val!=t->val){
            return false;
        }
        return isSame(s->left, t->left) && isSame(s->right,t->right);
    }
    
int countSubtree(TreeNode* s, TreeNode* t) {
        if(s==nullptr){
            return 0;
        }
        if(isSame(s,t)){
           return count(s);
        }

        return max(countSubtree(s->left,t), countSubtree(s->right,t));
}
```
