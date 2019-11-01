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
4. https://www.geeksforgeeks.org/segregate-even-and-odd-elements-in-a-linked-list/
sol.

My Code
```cpp
node* segregate(node* head){
    if(!head or !head->next)
        return NULL;
    
    node* temp = head;
    while(temp){
        if(temp->val%2)
            break;
        temp = temp->next;
    }
    node* odd_start = temp;
    
    temp = head;
    while(temp){
        if(temp->val%2 == 0)
            break;
        temp = temp->next;
    }
    node* even_start = temp;
    
    if(odd_start == NULL || even_start == NULL)
        return head;
        
    temp = head;
    node* odd = new node(0);
    node* even = new node(0);
    while(temp){
        if(temp->val%2 == 0){
            even->next = temp;
            even = even->next;
        }
        else{
            odd->next = temp;
            odd = odd->next;
        }
        temp = temp->next;
    }
    even->next = odd_start;
    odd->next = NULL;
    return even_start;
}
```
5. Maximum sum such that no two elements are adjacent

sol. https://www.geeksforgeeks.org/maximum-sum-such-that-no-two-elements-are-adjacent/(1-D DP)

6.Find Median in a stream

sol.https://practice.geeksforgeeks.org/problems/find-median-in-a-stream/0

7. Maximum points on a same line.

sol.https://www.geeksforgeeks.org/count-maximum-points-on-same-line/

8. Diameter of a tree

sol.https://www.geeksforgeeks.org/diameter-of-a-binary-tree-in-on-a-new-method/

9. Perfect sum Problem

sol. https://ide.geeksforgeeks.org/9RUT7vHrby

11. Rotten-Oranges problem

sol. https://practice.geeksforgeeks.org/problems/rotten-oranges/

12. Boundary Traversal of a Tree

sol. https://www.geeksforgeeks.org/boundary-traversal-of-binary-tree/

13. Ugly Numbers Solution

sol. 
```cpp
#include<bits/stdc++.h>

#define ll long long

using namespace std;

ll f(ll x){
    return((x/2+x/3+x/5) - (x/6+x/15+x/10) + x/30);
}
ll bsearch(ll x,ll lo, ll hi){
    ll ans;
    while(lo <= hi){
        ll mid = lo + (hi-lo)/2; // find mid
        
        ll count = f(mid); // find what uglieth number is mid
        
        if(count < x)
            lo = mid+1;
        else if(x < count)
            hi = mid-1;
        else{
            ans = mid;
            hi = mid-1;  // it may be possible that ans came from rounding off x
        }
    }
    return ans;
}
int nthUglyNumber(int n) {
    
    return bsearch(n, 1, (ll)pow(10,18));
}

int main(){
    int T, N;
    cin >> T;
    while(T--){
        cin >> N;
        
        cout << nthUglyNumber(N-1)<<endl;
    }
}
```

# Sam

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
## imp
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

My code
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

sol. https://www.geeksforgeeks.org/urlify-given-string-replace-spaces/

My code
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
2. Count possible decodings of given Digit sequence DP question 

sol. https://www.geeksforgeeks.org/count-possible-decodings-given-digit-sequence/

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
4. Dice throw DP question 

sol. https://www.geeksforgeeks.org/dice-throw-dp-30/

6. Longest Increasing Sequence and Longest Decreasing Sequence

sol. https://www.geeksforgeeks.org/longest-increasing-subsequence-dp-3/

7. Longest Common Subsequence

sol. https://www.geeksforgeeks.org/longest-common-subsequence-dp-4/

8.Find the length of smallest substring with maximum number of distinct characters.

sol. Microsoft 3rd Question

9. Euler Totient Function

sol. https://www.geeksforgeeks.org/eulers-totient-function/
 First solution in discussion is segmented sieve.
 
10. Mean Mode Median of an Unsorted Array.

sol. https://www.geeksforgeeks.org/program-for-mean-and-median-of-an-unsorted-array/

```cpp
int mode(int a[], int n){
	map<int, int>mp;
	int max;
	int val;
	for(int i=0;i<n;i++){
		mp[a[i]]++;
		if(max < mp[a[i]]){
			max = mp[a[i]];
			val = a[i];
		}
	}
	return val;
}
```
10. Evaluation of Postfix Expression

sol. https://www.geeksforgeeks.org/stack-set-4-evaluation-postfix-expression/

11. Infix to Postfix expression

sol. https://www.geeksforgeeks.org/stack-set-2-infix-to-postfix/

12. Maximum contigouous subarray sum

sol. 
```cpp
int max_sum(int A[], int N){
    long long best = LONG_MIN,sum = 0;
	    
    for(int i=0;i<N;i++){
	sum = max(A[i], sum+A[i]);
	best = max(best, sum);
    }
   return best;    
}
```
13. Given a, b and c coefficients of a quadratic equation, find the roots of the equation(assume roots to be real).

sol.
```cpp
pair<double, double> roots_of_Q(int a, int b, int c){
    pair<double, double>p;
    p.first = (-b + sqrt((b*b) - (4*a*c)))/(2*a);
    p.second = (-b - sqrt((b*b) - (4*a*c)))/(2*a);
    return p;
}
```
14. Serialize and deserialize a n-ary Tree

sol. https://www.cnblogs.com/Dylan-Java-NYC/p/11056027.html

15. Nth node from last

sol.https://www.geeksforgeeks.org/nth-node-from-the-end-of-a-linked-list/

# GSex
1.https://leetcode.com/problems/product-of-array-except-self/submissions/

sol.
```cpp
vector<int> productExceptSelf(vector<int>& nums) {
	int n = nums.size();

	vector<int>asc(n);

	asc[0] = nums[0];

	for(int i=1;i<n;i++){
	    asc[i] = nums[i]*asc[i-1];
	}

	int r = 1;
	for(int i=n-1;i>0;i--){
	    asc[i] = asc[i-1]*r;
	    r *= nums[i];
	}
	asc[0] = r;
return asc;
}
```
# MathWorks

1. Roll a string

sol. https://github.com/msdeep14/Algorithms-Practice/blob/master/roll-string.cpp

2. Find two numbers with their XORs and Sum

sol.https://www.geeksforgeeks.org/find-two-numbers-sum-xor/

# Adobe

1. Given an array, Just remove adjacent pairs of duplicate elements and return number of remaining elements.
Eg. A=[1,1,2,2,3] so answer is 1

If A=[1,1,2,2,1,3] so answer is 2. (3rd one will not be removed as it will not form a pair with any other 1)

if A=[1,2,2,1,3,3] so answer is 0.

Sol. 
```cpp
int rem_adj_pairs(vector<int> &A){
	stack<int>st;
	for(int i=0;i<A.size();i++){
		if(!st.empty()){
			if(st.top() == A[i])
				st.pop();
			else
				st.push(A[i]);
		}
		else
			st.push(A[i]);
	}

	return st.size();
}

```
2. Given a string s. Return substring of length 5 which occurs maximum times. If several of them exists, then you know what to do.
Yes, return the lexicographicaly smallest one. 5<=N<=10^6.

Eg. s= “bbbbbaaaaabbabababa. So answer is “ababa”.

Eg. s=”heisagoodboy” So answer is “agood”.

sol. 
```cpp
string max_substring_5(string str){
	set<string>st;
	unordered_map<string,int>mp;
	
	for(int i=0;i<=str.length()-5;i++){
	    string s = str.substr(i,5);
	    mp[s]++;
	}
	long long maxi = 0;
	for(auto i:mp){
	    if(i.second > maxi){
	        maxi = i.second;
	    }
	}
	
	for(auto i:mp){
	    if(i.second == maxi){
	        st.insert(i.first);
	    }
	}

	return *st.begin();
}
```
