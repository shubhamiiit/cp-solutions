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
```cpp
void solve(int ele,int currSum,int index,int maxe,int * arr,int & answer,int sum,int n){
        if(ele==maxe){
            int ssum=sum-currSum;
            if(abs(currSum-ssum)<answer)
                answer=abs(currSum-ssum);
            return;
        }
        if(index>=n){
            return;
        }
        solve(ele+1,currSum+arr[index],index+1,maxe,arr,answer,sum,n);
        solve(ele,currSum,index+1,maxe,arr,answer,sum,n);
}
int FindMinimumDifference(int *arr,int n){
    int sum=0;
    for(int i=0;i<n;i++){
        sum+=arr[i];
    }
    int answer=INT_MAX;
    solve(0,0,0,n/2,arr,answer,sum,n);
    return answer;
}
```

3.count nodes of subtrees of another subtree
sol.
```cpp
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
# AppD
See MCQ and these questions on https://imgur.com/a/PIXIxR8

Post Solutions of these:

1. UserName Disparity 
2. Ticket Resellers
3. Vowels
4. Activate Fountain
https://leetcode.com/discuss/interview-question/363036/twitter-oa-2019-activate-fountain
5. Array of length n, sliding window of size x, get minimum value in all the windows and finally return the maximum. x <= n <= 1000000   
sol.
```cpp
#include<bits/stdc++.h>
using namespace std;
int main()
 {
	int t;
	cin >> t;
	
	while(t--){
	    int n,k;
	    cin >> n >> k;
	    vector<int>A(n);
	    
	    for(int i=0;i<n;i++)cin >> A[i];
	    
	    deque<int>Q;
	    int i=0;
	    for(i=0;i<k;i++){
	        while(!Q.empty() and A[i] >= A[Q.back()])
	            Q.pop_back();
	        
	        Q.push_back(i);
	    }
	    
	    while(i<n){
	        cout << A[Q.front()] <<" ";
	        
	        while(!Q.empty() and Q.front() <= i-k)
	            Q.pop_front();
	       
	        while(!Q.empty() and A[i] >= A[Q.back()])
	            Q.pop_back();
	            
	        Q.push_back(i);
	        i++;
	    }
	    cout << A[Q.front()] <<endl;
	}
	return 0;
}
```

6. Angry animals
sol.

7.Almost Sorted Array - find minimum nos that must be deleted so that array is almost sorted.(Longest Increasing Subsequence)
sol. 
```cpp
#include<bits/stdc++.h>
using namespace std;
int main()
 {
	int t;
	cin >> t;
	while(t--){
	    int n;
	    cin >> n;
	    
	    vector<int>A(n);
	    for(int i=0;i<n;i++)cin >> A[i];
	    vector<int>dp(n,1);
	    
	    int maxim = 0;
	    for(int i=1;i<n;i++){
	        for(int j=0;j<i;j++){
	            if(A[i] > A[j] and dp[i] < dp[j]+1){
	                dp[i] = dp[j] + 1;
	            }
	        }
	    }
	    
	    for(int i=0;i<n;i++){
	        maxim = max(maxim, dp[i]);
	    }
	    cout << n - maxim <<endl;
	}
	return 0;
}
```

9. Mud Walls:
https://fizzbuzzer.com/mud-walls/

sol.
```cpp
int maxHeight(int[] stickPositions, int[] stickHeights) {
        int n = stickPositions.length;
        int m = stickHeights.length;
        int maxim = 0;

        for (int i=0; i<n-1; i++) {
            if (stickPositions[i]<stickPositions[i+1]-1) {
                // We have a gap
                int heightDiff =  abs(stickHeights[i+1] - stickHeights[i]);
                int gapLen = stickPositions[i+1] - stickPositions[i] - 1;
                int localMax = 0;
                if (gapLen > heightDiff) {
                    int low = max(stickHeights[i+1], stickHeights[i]) + 1;
                    int remainingGap = gapLen - heightDiff - 1;
                    localMax = low + remainingGap/2;

                } else {
                    localMax = min(stickHeights[i+1], stickHeights[i]) + gapLen;
                }

                maxim = max(max, localMax);
            }
        }

        return maxim;
    }
```
# AMZ
1. URLify
	https://www.geeksforgeeks.org/urlify-given-string-replace-spaces/
sol.
```cpp
#include<bits/stdc++.h>
using namespace std;
int main()
 {
	int t;
	cin >> t;
	while(t--){
	    string str;
	    cin.ignore(100, '\n');
	    getline(cin ,str);
	    
	    int k;
	    cin >> k;
	    
	    int i=0;
	   
	    while(str[i] == ' '){
	        i++;
	    }
	    
	    reverse(str.begin(), str.end());
	    i= 0;
	    while(str[i] == ' '){
	        i++;
	    }
	    reverse(str.begin(), str.end());
	    
	    string s = "";
	    
	    for(i=0;i<str.length();i++){
	        if(str[i] == ' ')
	            s += "%20";
	        else
	            s += str[i];
	    }
	    cout << s <<endl;
	}
	return 0;
}
```
2.https://www.geeksforgeeks.org/count-possible-decodings-given-digit-sequence/
sol.
```cpp
#include<bits/stdc++.h>
using namespace std;
int main()
 {
	int t;
	cin >> t;
	
	while(t--){
	    int n;
	    cin >> n;
	    
	    string s;
	    cin >> s;
	    
	    vector<int>dp(n+1, 0);
	    
	    dp[0] = 1;
	    dp[1] = 1;
	    
	    if(s[0] == '0'){
	        cout << 0 <<endl;
	        continue;
	    }
	    
	    for(int i=2;i<=n;i++){
	        if(s[i-1] > '0')
	            dp[i] = dp[i-1];
	            
	        if(s[i-2] == '1' || (s[i-2] == '2' and s[i-1] < '7'))
	            dp[i] += dp[i-2];
	    }
	    
	    cout << dp[n] <<endl;
	}
	return 0;
}
```
3.Sort numbers when rank of each number in decimal system is changed.(Could anyone please elaborate the question or give some link of this question on some website)   as per my understanding when each number is mapped to another number for eg. 1 has rank 4, 2 has 9, etc and then you have to sort the modified number system.

sol. This solution is mine, as question is unclear it may be possible that this solution is incorrect. 
```cpp
map<int, int> sort_by_rank(map<int, int>mp) {
	map<int, int>res;
	
	for(auto i:mp){
	    res[i.second] = i.first;
	}
	
	sort(res.begin(), res.end());
	return res;
}
```
