
### 🔹 **LIS (Longest Increasing Subsequence) & Variants**

1. **Longest Increasing Subsequence** (300)
2. **Longest String Chain** (1048)
3. **Russian Doll Envelopes** (354)
4. **Increasing Subsequences** (491)
5. **Number of Longest Increasing Subsequence** (673)
6. **Wiggle Subsequence** (376)
7. **Longest Arithmetic Subsequence** (1027)
8. **Longest Arithmetic Subsequence of Given Difference** (1218)
9. **Maximum Length of Pair Chain** (646)
10. **Longest Ideal Subsequence** (2370)
11. **Longest Increasing Path in a Matrix** (329)

---

### 🔹 **LCS (Longest Common Subsequence) & Variants**

1. **Longest Common Subsequence** (1143)
2. **Shortest Common Supersequence** (1092)
3. **Delete Operation for Two Strings** (583)
4. **Minimum ASCII Delete Sum for Two Strings** (712)
5. **Interleaving String** (97)
6. **Distinct Subsequences** (115)
7. **Edit Distance** (72)
8. **Regular Expression Matching** (10)
9. **Wildcard Matching** (44)
10. **Uncrossed Lines** (1035)
11. **Longest Palindromic Subsequence** (516)
12. **Palindrome Partitioning II** (132)
 "Longest Repeating Subsequence" 

---

### 🔹 **Overlapping Bridges / Interval DP & Greedy**

1. **Non-overlapping Intervals** (435)
2. **Minimum Number of Arrows to Burst Balloons** (452)
3. **Maximum Profit in Job Scheduling** (1235)
4. **Meeting Rooms** (252)
5. **Meeting Rooms II** (253)
6. **Car Pooling** (1094)
7. **My Calendar I** (729)
8. **My Calendar II** (731)
9. **My Calendar III** (732)

> 🔸 *Note:* Removed duplicates already listed (e.g., 646, 354) from this section.

---

### 🔹 **Job / Course Scheduling**

1. **Course Schedule** (207)
2. **Course Schedule II** (210)
3. **Course Schedule III** (630)
4. **Parallel Courses** (1136)
5. **Parallel Courses III** (2050)
6. **Minimum Time to Complete All Tasks** (2589)
7. **Minimum Number of Days to Eat N Oranges** (1553)
8. **Task Scheduler** (621)
9. **Reorganize String** (767)
10. **Rearrange String k Distance Apart** (358) *(Premium)*
11. **Employee Free Time** (759)


-----

## 1\. Longest Increasing Subsequence (LeetCode 300)

### **Problem Statement (PS)**

Aapko ek integer array `nums` diya gaya hai. Aapko uske andar se sabse lambi **strictly increasing subsequence** (aise elements ka sequence jo array mein aage aate hain aur hamesha badhte rehte hain) ki **length** batani hai.

### **Examples**

**Example 1:**

  * **Input:** `nums = [10, 9, 2, 5, 3, 7, 101, 18]`
  * **Output:** `4`
  * **Explanation:** Sabse lamba increasing subsequence `[2, 3, 7, 101]` hai, isliye iski length 4 hai.

**Example 2:**

  * **Input:** `nums = [0, 1, 0, 3, 2, 3]`
  * **Output:** `4`
  * **Explanation:** Yahan, sabse lamba increasing subsequence `[0, 1, 2, 3]` hai, jiski length 4 hai.

-----

### **Approach 1: Naive (Recursion with Memoization)**

Yeh approach mein hum har element ke liye do options try karte hain: ya toh use subsequence mein **shamil karein** (agar woh pichle element se bada hai) ya **na karein**. Isse bahut saari same calculations baar-baar hoti hain, jinko bachane ke liye hum **memoization** (DP) ka istemal karte hain.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Longest Increasing Subsequence

class Solution {
private:
    // dp[prev_index+1][curr_index]
    vector<vector<int>> dp;

    int solve(vector<int>& nums, int prev_index, int curr_index) {
        // Base case: Jab saare elements check kar liye
        if (curr_index == nums.size()) {
            return 0;
        }

        // Agar result pehle se calculated hai
        if (dp[prev_index + 1][curr_index] != -1) {
            return dp[prev_index + 1][curr_index];
        }

        // Option 1: Current element ko nahi lete
        int not_take = solve(nums, prev_index, curr_index + 1);

        // Option 2: Current element ko lete hain
        int take = 0;
        // Hum tabhi le sakte hain jab ya toh yeh pehla element ho (prev_index == -1)
        // ya yeh pichle liye gaye element se bada ho
        if (prev_index == -1 || nums[curr_index] > nums[prev_index]) {
            take = 1 + solve(nums, curr_index, curr_index + 1);
        }

        return dp[prev_index + 1][curr_index] = max(take, not_take);
    }

public:
    int lengthOfLIS(vector<int>& nums) {
        int n = nums.size();
        if (n == 0) return 0;
        // dp table ko -1 se initialize karte hain
        // prev_index -1 se n-1 tak ja sakta hai, isliye size n+1
        dp.resize(n + 1, vector<int>(n, -1));
        return solve(nums, -1, 0);
    }
};

/*
Time Complexity: O(n^2)
Har state (prev_index, curr_index) ke liye hum ek baar calculate karte hain. Total n*n states hain.

Space Complexity: O(n^2)
DP table ka size n*n hai.
*/
```

-----

### **Approach 2: Optimal (DP with Binary Search)**

Yeh sabse fast approach hai. Hum ek temporary array `temp` maintain karte hain. Yeh array `temp` zaroori nahi ki ek valid subsequence ho, lekin iski `length` hamesha LIS ki current length ke barabar hogi. Jab hum `nums` array ke har element ko process karte hain, hum use `temp` array mein sahi jagah par binary search ka use karke rakhte hain.

Agar element `temp` ke saare elements se bada hai, toh use `temp` ke end mein daal dete hain (LIS ki length badh gayi). Nahi toh, use `temp` ke andar uss element se replace karte hain jo usse just bada ya barabar hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Longest Increasing Subsequence

class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        if (nums.empty()) {
            return 0;
        }
        
        vector<int> temp;
        temp.push_back(nums[0]);

        for (int i = 1; i < nums.size(); ++i) {
            // Agar current element temp ke aakhri element se bada hai
            if (nums[i] > temp.back()) {
                temp.push_back(nums[i]);
            } else {
                // Nahi toh, temp mein uski sahi jagah dhundho (ceiling value)
                // lower_bound binary search karke pehla element dhundhta hai jo nums[i] se chota nahi hai
                auto it = lower_bound(temp.begin(), temp.end(), nums[i]);
                *it = nums[i];
            }
        }
        
        return temp.size();
    }
};

/*
Time Complexity: O(n log n)
Hum n elements par loop karte hain, aur har element ke liye binary search (log n) karte hain.

Space Complexity: O(n)
Worst case mein temp array ka size n ho sakta hai.
*/
```

-----

-----

## 2\. Longest String Chain (LeetCode 1048)

### **Problem Statement (PS)**

Aapko strings ka ek array `words` diya gaya hai. Ek **word chain** strings ki aisi sequence hoti hai jismein har agla word pichle word mein kahin par bhi bas **ek character** daal kar banaya ja sakta hai. Aapko sabse lambi possible word chain ki length batani hai.

### **Examples**

**Example 1:**

  * **Input:** `words = ["a","b","ba","bca","bda","bdca"]`
  * **Output:** `4`
  * **Explanation:** Sabse lambi chain hai `"a" -> "ba" -> "bda" -> "bdca"`, iski length 4 hai.

**Example 2:**

  * **Input:** `words = ["xbc","pcxbcf","xb","cxbc","pcxbc"]`
  * **Output:** `5`
  * **Explanation:** Chain hai `"xb" -> "xbc" -> "cxbc" -> "pcxbc" -> "pcxbcf"`, length 5.

-----

### **Approach 1: Naive (Plain Recursion)**

Is approach mein hum har word se shuru karke saari possible chains explore karte hain. Hum ek recursive function banate hain jo ek word se shuru hone wali sabse lambi chain dhundhta hai. Yeh approach bahut saari calculations repeat karti hai aur bade inputs ke liye TLE de sakti hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Longest String Chain

class Solution {
private:
    // Check karta hai ki kya s2, s1 ka predecessor hai
    bool isPredecessor(const string& s1, const string& s2) {
        if (s1.length() + 1 != s2.length()) return false;
        int i = 0, j = 0;
        while (i < s1.length() && j < s2.length()) {
            if (s1[i] == s2[j]) {
                i++;
            }
            j++;
        }
        return i == s1.length();
    }
    
    // Har word se start karke longest chain dhundhta hai
    int findLongestChain(const string& currentWord, const unordered_set<string>& wordSet) {
        int maxLength = 1;
        // Har possible next word banane ki koshish
        for (int i = 0; i <= currentWord.length(); ++i) {
            for (char c = 'a'; c <= 'z'; ++c) {
                string nextWord = currentWord.substr(0, i) + c + currentWord.substr(i);
                if (wordSet.count(nextWord)) {
                    maxLength = max(maxLength, 1 + findLongestChain(nextWord, wordSet));
                }
            }
        }
        return maxLength;
    }

public:
    int longestStrChain(vector<string>& words) {
        unordered_set<string> wordSet(words.begin(), words.end());
        int maxChain = 0;
        for (const string& word : words) {
            maxChain = max(maxChain, findLongestChain(word, wordSet));
        }
        return maxChain;
    }
};

/*
Time Complexity: O(N * 2^L * L) jahan L word ki max length hai
Yeh complexity bahut zyada hai, kyunki hum har word ke liye saari possibilities explore kar rahe hain.
Yeh TLE dega.

Space Complexity: O(N)
Word set aur recursion stack ke liye.
*/
```

-----

### **Approach 2: Optimal (Dynamic Programming)**

Yeh LIS jaisa hi problem hai. Sabse pehle, hum `words` array ko unki length ke hisaab se **sort** kar dete hain. Phir hum ek `map` ya `unordered_map` ka use karte hain `dp` state store karne ke liye, jahan `dp[word]` uss `word` par khatam hone wali sabse lambi chain ki length store karega.

Har word ke liye, hum uske saare possible predecessors (ek character hata kar) generate karte hain aur `dp` map mein check karte hain ki un predecessors ke liye sabse lambi chain kya thi.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Longest String Chain

class Solution {
public:
    // Custom comparator function, length ke basis par sort karne ke liye
    static bool compare(const string& s1, const string& s2) {
        return s1.length() < s2.length();
    }

    int longestStrChain(vector<string>& words) {
        // Step 1: Words ko length ke according sort karo
        sort(words.begin(), words.end(), compare);
        
        // Step 2: DP map initialize karo
        // dp[word] -> word par end hone wali longest chain ki length
        unordered_map<string, int> dp;
        int max_chain_length = 0;

        // Step 3: Har word ke liye DP value calculate karo
        for (string& word : words) {
            // Har word kam se kam 1 length ki chain banata hai (khud)
            dp[word] = 1;
            
            // Uske saare possible predecessors check karo
            for (int i = 0; i < word.length(); ++i) {
                string predecessor = word.substr(0, i) + word.substr(i + 1);
                
                // Agar predecessor dp map mein hai, toh chain update karo
                if (dp.find(predecessor) != dp.end()) {
                    dp[word] = max(dp[word], dp[predecessor] + 1);
                }
            }
            
            // Overall max length update karo
            max_chain_length = max(max_chain_length, dp[word]);
        }
        
        return max_chain_length;
    }
};

/*
Time Complexity: O(N * logN + N * L * L)
N * logN sorting ke liye. Har N word ke liye, hum L baar loop chala rahe hain (jahan L
word ki max length hai) aur substr() operation L time leta hai.

Space Complexity: O(N * L)
DP map saare words ko store kar sakta hai.
*/
```

-----

-----

## 3\. Russian Doll Envelopes (LeetCode 354)

### **Problem Statement (PS)**

Aapko 2D array `envelopes` diya gaya hai, jahan har element `[width, height]` ek envelope ke dimensions hain. Ek envelope `A` dusre envelope `B` ke andar fit ho sakta hai agar `A` ki width aur height dono `B` se **strictly** kam hon. Aapko batana hai ki aap max kitne envelopes ek dusre ke andar daal sakte hain.

### **Examples**

**Example 1:**

  * **Input:** `envelopes = [[5,4],[6,4],[6,7],[2,3]]`
  * **Output:** `3`
  * **Explanation:** Sabse lambi chain `[2,3] -> [5,4] -> [6,7]` hai.

**Example 2:**

  * **Input:** `envelopes = [[1,1],[1,1],[1,1]]`
  * **Output:** `1`
  * **Explanation:** Koi bhi envelope dusre mein fit nahi ho sakta, isliye max 1.

-----

### **Approach 1: Naive (DP on sorted array)**

Yeh problem LIS ka hi ek version hai. Pehle hum envelopes ko sort karte hain. Sorting ka tareeka important hai: **width ko increasing order mein sort karo**. Agar do envelopes ki width same hai, toh unhe **height ke decreasing order mein sort karo**.

Aisa karne ke baad, problem sirf heights par Longest Increasing Subsequence (LIS) nikalne jaisa ban jaata hai. Hum `O(n^2)` wali LIS DP yahan laga sakte hain.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Russian Doll Envelopes

class Solution {
public:
    // Custom comparator
    static bool compare(vector<int>& a, vector<int>& b) {
        // Width increasing order mein
        if (a[0] != b[0]) {
            return a[0] < b[0];
        }
        // Agar width same, toh height decreasing order mein
        return a[1] > b[1];
    }

    int maxEnvelopes(vector<vector<int>>& envelopes) {
        int n = envelopes.size();
        if (n == 0) return 0;

        // Step 1: Custom sort
        sort(envelopes.begin(), envelopes.end(), compare);
        
        // Step 2: Heights par LIS lagao (O(n^2) DP)
        vector<int> dp(n, 1);
        int max_dolls = 1;
        
        for (int i = 1; i < n; ++i) {
            for (int j = 0; j < i; ++j) {
                // Sirf height check karna kaafi hai, kyunki sorting ne width a>b or (a=b and h_a > h_b) handle kar liya hai
                if (envelopes[i][1] > envelopes[j][1]) {
                    dp[i] = max(dp[i], 1 + dp[j]);
                }
            }
            max_dolls = max(max_dolls, dp[i]);
        }
        
        return max_dolls;
    }
};

/*
Time Complexity: O(n^2)
Sorting mein O(n log n) lagta hai, lekin LIS ke do nested loops O(n^2) lete hain.

Space Complexity: O(n)
DP array ke liye.
*/
```

-----

### **Approach 2: Optimal (Sort + Binary Search LIS)**

Approach 1 jaisa hi hai, lekin LIS nikalne ke liye hum zyada efficient `O(n log n)` wala algorithm use karenge. Sorting strategy bilkul same rahegi (width increasing, same width par height decreasing). Iske baad, hum sirf heights ke upar binary search wala LIS algorithm laga denge.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Russian Doll Envelopes

class Solution {
public:
    // Custom comparator
    static bool compare(vector<int>& a, vector<int>& b) {
        if (a[0] != b[0]) {
            return a[0] < b[0];
        }
        return a[1] > b[1];
    }

    int maxEnvelopes(vector<vector<int>>& envelopes) {
        int n = envelopes.size();
        if (n == 0) return 0;

        // Step 1: Custom sort
        sort(envelopes.begin(), envelopes.end(), compare);
        
        // Step 2: Heights par LIS lagao (O(n log n) Binary Search method)
        vector<int> temp;
        temp.push_back(envelopes[0][1]);

        for (int i = 1; i < n; ++i) {
            int current_height = envelopes[i][1];
            if (current_height > temp.back()) {
                temp.push_back(current_height);
            } else {
                auto it = lower_bound(temp.begin(), temp.end(), current_height);
                *it = current_height;
            }
        }
        
        return temp.size();
    }
};

/*
Time Complexity: O(n log n)
Sorting mein O(n log n) aur LIS nikalne mein bhi O(n log n) lagta hai.

Space Complexity: O(n)
LIS nikalne ke liye temporary array ka size worst case mein n ho sakta hai.
*/
```



-----

## 5\. Number of Longest Increasing Subsequence (LeetCode 673)

### **Problem Statement (PS)**

Aapko ek integer array `nums` diya gaya hai. Aapko yeh pata lagana hai ki us array mein **sabse lambi increasing subsequence (LIS) kitni hain**. Matlab LIS ki jo bhi maximum length hai, uss length ke kitne alag-alag subsequences maujood hain.

### **Examples**

**Example 1:**

  * **Input:** `nums = [1,3,5,4,7]`
  * **Output:** `2`
  * **Explanation:** Sabse lambi increasing subsequence ki length 4 hai. Aur 4 length ke do LIS hain: `[1,3,5,7]` aur `[1,3,4,7]`.

**Example 2:**

  * **Input:** `nums = [2,2,2,2,2]`
  * **Output:** `5`
  * **Explanation:** Yahan LIS ki length 1 hai. Aur 1 length ke 5 subsequences hain: `[2]`, `[2]`, `[2]`, `[2]`, `[2]`.

-----

### **Approach 1: Naive (Backtracking)**

Is approach mein hum saare possible increasing subsequences ko recursion ka use karke generate karenge. Hum ek list mein sabse lambe subsequences ko store karenge aur aakhir mein us list ka size return kar denge. Yeh approach bahut slow hai kyunki yeh saari possibilities ko explore karti hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Number of Longest Increasing Subsequence

class Solution {
private:
    int maxLen = 0;
    int count = 0;

    void findSubsequences(vector<int>& nums, int index, vector<int>& current) {
        // Base case: jab hum array ke end tak pahunch jayein
        if (index == nums.size()) {
            if (current.size() > maxLen) {
                maxLen = current.size();
                count = 1;
            } else if (current.size() == maxLen && maxLen > 0) {
                count++;
            }
            return;
        }

        // Option 1: Current element ko lete hain (agar valid hai)
        if (current.empty() || nums[index] > current.back()) {
            current.push_back(nums[index]);
            findSubsequences(nums, index + 1, current);
            current.pop_back(); // Backtrack
        }
        
        // Option 2: Current element ko nahi lete
        findSubsequences(nums, index + 1, current);
    }
public:
    int findNumberOfLIS(vector<int>& nums) {
        vector<int> current;
        findSubsequences(nums, 0, current);
        // Agar array [2,2,2] jaisa hai, toh LIS length 1 hogi aur count 3.
        // Hamara recursion empty subsequence ke case ko handle nahi kar raha,
        // isliye agar count 0 hai (matlab koi LIS length > 0 nahi mila, except single elements)
        // toh answer n hoga.
        return count == 0 ? nums.size() : count;
    }
};

/*
Time Complexity: O(2^n)
Yeh exponential hai aur bade test cases ke liye TLE dega.

Space Complexity: O(n)
Recursion stack ki depth ke liye.
*/
```

-----

### **Approach 2: Optimal (Dynamic Programming)**

Yeh approach `O(n^2)` mein kaam karti hai. Hum do DP arrays ka use karte hain:

1.  `length[i]`: `nums[i]` par khatam hone wali LIS ki **length**.
2.  `count[i]`: `nums[i]` par khatam hone wali LIS ki **sankhya (count)**.

Hum har `i` ke liye, usse pehle ke saare `j` (j \< i) ko check karte hain. Agar `nums[i] > nums[j]`, toh hum `length` aur `count` ko update karte hain. Agar `length[j] + 1` `length[i]` se bada hai, to hum ek nayi lambi subsequence paate hain. Agar barabar hai, to hum same length ki ek aur subsequence paate hain.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Number of Longest Increasing Subsequence

class Solution {
public:
    int findNumberOfLIS(vector<int>& nums) {
        int n = nums.size();
        if (n <= 1) return n;
        
        // length[i] = LIS ki length jo nums[i] par end hoti hai
        // count[i] = LIS ka count jo nums[i] par end hota hai
        vector<int> length(n, 1);
        vector<int> count(n, 1);
        
        int max_len = 0;

        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < i; ++j) {
                if (nums[i] > nums[j]) {
                    // Agar hume LIS extend karne ka behtar tareeka milta hai
                    if (length[j] + 1 > length[i]) {
                        length[i] = length[j] + 1;
                        count[i] = count[j];
                    }
                    // Agar same length ka ek aur tareeka milta hai
                    else if (length[j] + 1 == length[i]) {
                        count[i] += count[j];
                    }
                }
            }
            max_len = max(max_len, length[i]);
        }
        
        int result = 0;
        for (int i = 0; i < n; ++i) {
            if (length[i] == max_len) {
                result += count[i];
            }
        }
        
        return result;
    }
};

/*
Time Complexity: O(n^2)
Do nested loops hain jo n tak chalte hain.

Space Complexity: O(n)
Do DP arrays (length aur count) ke liye.
*/
```

-----

-----

## 6\. Wiggle Subsequence (LeetCode 376)

### **Problem Statement (PS)**

Aapko ek integer array `nums` diya gaya hai. Ek "wiggle" subsequence woh hoti hai jismein consecutive numbers ke differences ka sign alternate karta hai (positive, negative, positive, ...). Aapko sabse lambi wiggle subsequence ki **length** batani hai. 0 difference wale subsequence ko wiggle nahi maana jaata.

### **Examples**

**Example 1:**

  * **Input:** `nums = [1,7,4,9,2,5]`
  * **Output:** `6`
  * **Explanation:** Poora array hi ek wiggle sequence hai. Differences hain: (6, -3, 5, -7, 3).

**Example 2:**

  * **Input:** `nums = [1,17,5,10,13,15,10,5,16,8]`
  * **Output:** `7`
  * **Explanation:** Ek possible sabse lambi wiggle subsequence hai `[1,17,5,10,5,16,8]`.

-----

### **Approach 1: Naive (Dynamic Programming)**

Hum do DP arrays ka istemal kar sakte hain:

  * `up[i]`: `nums[i]` par khatam hone wali sabse lambi wiggle subsequence ki length jiska aakhri difference **positive** tha.
  * `down[i]`: `nums[i]` par khatam hone wali sabse lambi wiggle subsequence ki length jiska aakhri difference **negative** tha.

Har `i` ke liye, hum pichle saare `j` (j \< i) ko check karke `up[i]` aur `down[i]` ki value nikalte hain.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Wiggle Subsequence

class Solution {
public:
    int wiggleMaxLength(vector<int>& nums) {
        int n = nums.size();
        if (n < 2) return n;

        // up[i]: LWS ki length ending at i, jiska last diff positive hai
        // down[i]: LWS ki length ending at i, jiska last diff negative hai
        vector<int> up(n, 1);
        vector<int> down(n, 1);

        for (int i = 1; i < n; ++i) {
            for (int j = 0; j < i; ++j) {
                if (nums[i] > nums[j]) {
                    // up[i] ko update karo, pichla step down hona chahiye
                    up[i] = max(up[i], down[j] + 1);
                } else if (nums[i] < nums[j]) {
                    // down[i] ko update karo, pichla step up hona chahiye
                    down[i] = max(down[i], up[j] + 1);
                }
            }
        }

        return max(up[n-1], down[n-1]);
    }
};

/*
Time Complexity: O(n^2)
Do nested loops ke kaaran.

Space Complexity: O(n)
Do DP arrays ke liye.
*/
```

-----

### **Approach 2: Optimal (Greedy Approach)**

Yeh problem ek greedy tareeke se `O(n)` mein solve ho sakti hai. Hum bas array mein "peaks" (choti) aur "valleys" (ghaati) ko count kar sakte hain. Jab bhi numbers ka trend badalta hai (increasing se decreasing ya vice versa), woh ek "wiggle" hota hai.

Hum pichle difference (`prev_diff`) ko track karte hain. Jab bhi current difference ka sign pichle difference ke sign se alag hota hai, hum length badha dete hain.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Wiggle Subsequence

class Solution {
public:
    int wiggleMaxLength(vector<int>& nums) {
        int n = nums.size();
        if (n < 2) {
            return n;
        }

        int prev_diff = nums[1] - nums[0];
        // Agar pehle do element same nahi hain to length 2, varna 1
        int length = (prev_diff != 0) ? 2 : 1;

        for (int i = 2; i < n; ++i) {
            int current_diff = nums[i] - nums[i - 1];
            
            // Jab sign change ho (aur current_diff non-zero ho)
            // Ya, jab pichla diff zero tha aur ab non-zero hai (e.g., [1,1,7])
            if ((current_diff > 0 && prev_diff <= 0) || (current_diff < 0 && prev_diff >= 0)) {
                length++;
                prev_diff = current_diff;
            }
        }
        return length;
    }
};


/*
Time Complexity: O(n)
Hum array ko bas ek baar traverse karte hain.

Space Complexity: O(1)
Hum sirf kuch variables ka istemal kar rahe hain.
*/
```

-----

-----

## 7\. Longest Arithmetic Subsequence (LeetCode 1027)

### **Problem Statement (PS)**

Aapko ek integer array `A` diya gaya hai. Aapko uski sabse lambi **arithmetic subsequence** ki length batani hai. Arithmetic subsequence woh hoti hai jiske consecutive elements ke beech ka difference constant (hamesha same) hota hai.

### **Examples**

**Example 1:**

  * **Input:** `A = [3,6,9,12]`
  * **Output:** `4`
  * **Explanation:** Poora array hi ek arithmetic subsequence hai jiska difference 3 hai.

**Example 2:**

  * **Input:** `A = [9,4,7,2,10]`
  * **Output:** `3`
  * **Explanation:** Sabse lambi arithmetic subsequence hai `[4,7,10]` jiska difference 3 hai.

-----

### **Approach 1: Brute Force**

Is approach mein hum har possible pair `(A[i], A[j])` ko start point maante hain. In do numbers se humein common difference `d = A[j] - A[i]` mil jaata hai. Phir hum array mein aage check karte hain ki aur kitne elements (`A[k]` jahan k \> j) is sequence ko aage badha sakte hain.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Longest Arithmetic Subsequence

class Solution {
public:
    int longestArithSeqLength(vector<int>& A) {
        int n = A.size();
        if (n <= 2) return n;

        int max_len = 2;

        for (int i = 0; i < n; ++i) {
            for (int j = i + 1; j < n; ++j) {
                int diff = A[j] - A[i];
                int current_len = 2;
                int last_val = A[j];

                // Sequence ke agle elements dhundho
                for (int k = j + 1; k < n; ++k) {
                    if (A[k] == last_val + diff) {
                        current_len++;
                        last_val = A[k];
                    }
                }
                max_len = max(max_len, current_len);
            }
        }
        return max_len;
    }
};

/*
Time Complexity: O(n^3)
Teen nested loops ke kaaran.

Space Complexity: O(1)
Koi extra space nahi use ho raha.
*/
```

-----

### **Approach 2: Optimal (Dynamic Programming)**

Yeh `O(n^2)` ka solution hai. Hum DP state ko aise define karte hain: `dp[i][diff]` ka matlab hai `A[i]` par khatam hone wali arithmetic subsequence ki length jiska common difference `diff` hai.

Kyunki `diff` negative aur bada ho sakta hai, hum 2D array ke bajaye array of maps ka use karenge: `vector<unordered_map<int, int>> dp(n)`.

Har `i` ke liye, hum pichle saare `j` (j \< i) ke saath uska difference nikalte hain aur `dp[i]` ko update karte hain.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Longest Arithmetic Subsequence

class Solution {
public:
    int longestArithSeqLength(vector<int>& A) {
        int n = A.size();
        if (n <= 2) return n;

        // dp[i] is a map where dp[i][diff] stores the length of the
        // arithmetic sequence ending at index i with difference diff.
        vector<unordered_map<int, int>> dp(n);
        int max_len = 2;

        for (int i = 1; i < n; ++i) {
            for (int j = 0; j < i; ++j) {
                int diff = A[i] - A[j];
                int len = 2; // Default length of a new sequence (A[j], A[i])
                
                // Agar j par same diff ki sequence pehle se hai, usko extend karo
                if (dp[j].count(diff)) {
                    len = dp[j][diff] + 1;
                }
                
                dp[i][diff] = len;
                max_len = max(max_len, dp[i][diff]);
            }
        }
        
        return max_len;
    }
};

/*
Time Complexity: O(n^2)
Do nested loops hain. Map operations average O(1) hote hain.

Space Complexity: O(n^2)
Worst case mein, har pair ka alag difference ho sakta hai, toh har map mein n entries ho sakti hain.
*/
```

-----

-----

## 8\. Longest Arithmetic Subsequence of Given Difference (LeetCode 1218)

### **Problem Statement (PS)**

Aapko ek integer array `arr` aur ek integer `difference` diya gaya hai. Aapko `arr` mein se sabse lambi aisi arithmetic subsequence ki length batani hai jiska common difference diye gaye `difference` ke barabar ho.

### **Examples**

**Example 1:**

  * **Input:** `arr = [1,2,3,4], difference = 1`
  * **Output:** `4`
  * **Explanation:** Poora array `[1,2,3,4]` hi woh subsequence hai.

**Example 2:**

  * **Input:** `arr = [1,5,7,8,5,3,4,2,1], difference = -2`
  * **Output:** `4`
  * **Explanation:** Sabse lambi subsequence `[7,5,3,1]` hai.

-----

### **Approach 1: Naive (Dynamic Programming)**

Yeh ek standard `O(n^2)` DP approach hai. `dp[i]` mein hum store karenge ki `arr[i]` par khatam hone wali, diye gaye `difference` ki, sabse lambi arithmetic subsequence ki length kya hai.

Har `i` ke liye, hum pichle saare `j` (j \< i) ko check karte hain. Agar `arr[i] - arr[j] == difference` hai, toh hum `dp[i]` ko `dp[j] + 1` se update kar sakte hain.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Longest Arithmetic Subsequence of Given Difference

class Solution {
public:
    int longestSubsequence(vector<int>& arr, int difference) {
        int n = arr.size();
        if (n == 0) return 0;

        vector<int> dp(n, 1);
        int max_len = 1;

        for (int i = 1; i < n; ++i) {
            for (int j = 0; j < i; ++j) {
                if (arr[i] - arr[j] == difference) {
                    dp[i] = max(dp[i], 1 + dp[j]);
                }
            }
            max_len = max(max_len, dp[i]);
        }
        return max_len;
    }
};

/*
Time Complexity: O(n^2)
Do nested loops hain.

Space Complexity: O(n)
DP array ke liye.
*/
```

-----

### **Approach 2: Optimal (DP with HashMap)**

Hum `O(n^2)` ko `O(n)` mein optimize kar sakte hain. Jab hum `arr[i]` par hote hain, humein pichle `j` indices ko search karne ke bajaye, seedha yeh pata lagana hota hai ki "kya `arr[i] - difference` number array mein pehle aa chuka hai, aur agar haan, to uspar khatam hone wali sequence ki length kya thi?".

Is kaam ke liye **HashMap** perfect hai. Hum ek map `dp_map` banayenge jahan `dp_map[value]` uss `value` par khatam hone wali sequence ki length store karega.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Longest Arithmetic Subsequence of Given Difference

class Solution {
public:
    int longestSubsequence(vector<int>& arr, int difference) {
        // dp_map[value] = value par end hone wali LAS ki length
        unordered_map<int, int> dp_map;
        int max_len = 0;

        for (int num : arr) {
            // Humara pichla number 'num - difference' hona chahiye
            int prev_num = num - difference;
            int prev_len = 0;
            
            // Check karo ki pichla number map mein hai ya nahi
            if (dp_map.count(prev_num)) {
                prev_len = dp_map[prev_num];
            }
            
            // Current number par end hone wali sequence ki length update karo
            dp_map[num] = prev_len + 1;
            
            // Overall max length update karo
            max_len = max(max_len, dp_map[num]);
        }
        
        return max_len;
    }
};


/*
Time Complexity: O(n)
Hum array ko bas ek baar traverse karte hain, aur map ke operations O(1) average time lete hain.

Space Complexity: O(n)
Worst case mein, map mein n alag-alag numbers store ho sakte hain.
*/
```



-----

-----

## 9\. Maximum Length of Pair Chain (LeetCode 646)

### **Problem Statement (PS)**

Aapko `n` pairs ka ek array diya gaya hai, jahan har pair `[left, right]` form mein hai aur hamesha `left < right` hota hai. Ek pair `(c, d)` dusre pair `(a, b)` ko follow kar sakta hai agar `b < c` ho. Aapko pairs ki sabse lambi possible chain ki **length** batani hai.

### **Examples**

**Example 1:**

  * **Input:** `pairs = [[1,2],[2,3],[3,4]]`
  * **Output:** `2`
  * **Explanation:** Sabse lambi chain `[[1,2], [3,4]]` hai. `[2,3]` ko `[1,2]` ke baad nahi le sakte kyunki `2 < 2` false hai.

**Example 2:**

  * **Input:** `pairs = [[1,2],[7,8],[4,5]]`
  * **Output:** `3`
  * **Explanation:** Agar hum pairs ko sort karein toh `[[1,2], [4,5], [7,8]]` ek valid 3-length ki chain hai.

-----

### **Approach 1: Naive (Dynamic Programming - LIS based)**

Yeh problem Longest Increasing Subsequence (LIS) jaisi hai. Sabse pehle, hum pairs ko unke pehle element ke basis par **sort** kar dete hain. Uske baad, hum ek DP approach lagate hain jahan `dp[i]` store karega ki `pairs[i]` par khatam hone wali sabse lambi chain ki length kya hai.

Har `i` ke liye, hum pichle saare `j` (j \< i) ko check karte hain. Agar `pairs[j][1] < pairs[i][0]`, iska matlab `pairs[i]` `pairs[j]` ke baad chain bana sakta hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Maximum Length of Pair Chain

class Solution {
public:
    int findLongestChain(vector<vector<int>>& pairs) {
        int n = pairs.size();
        if (n == 0) return 0;

        // Step 1: Pairs ko pehle element ke basis par sort karo
        sort(pairs.begin(), pairs.end());

        // Step 2: LIS wali DP lagao
        vector<int> dp(n, 1);
        int max_len = 1;

        for (int i = 1; i < n; ++i) {
            for (int j = 0; j < i; ++j) {
                // Agar pair[i] pair[j] ke baad aa sakta hai
                if (pairs[j][1] < pairs[i][0]) {
                    dp[i] = max(dp[i], dp[j] + 1);
                }
            }
            max_len = max(max_len, dp[i]);
        }
        
        return max_len;
    }
};


/*
Time Complexity: O(n^2)
Sorting mein O(n log n) lagta hai, lekin DP ke do nested loops O(n^2) time lete hain.

Space Complexity: O(n)
DP array ke liye.
*/
```

-----

### **Approach 2: Optimal (Greedy Approach)**

Yeh ek classic problem hai jise greedy approach se solve kiya ja sakta hai. Strategy yeh hai:

1.  Saare pairs ko unke **dusre element (end point)** ke basis par sort karo.
2.  Pehla pair le lo, uski length 1 ho gayi. Uske end point ko `current_end` mein store kar lo.
3.  Ab sorted pairs mein aage badho. Jo bhi pehla pair mile jiska start point `current_end` se bada ho, use apni chain mein shamil kar lo, length badhao, aur `current_end` ko is naye pair ke end point se update kar do.

Yeh approach hamesha optimal solution deti hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Maximum Length of Pair Chain

class Solution {
public:
    // Custom comparator, dusre element ke basis par sort karne ke liye
    static bool compare(const vector<int>& a, const vector<int>& b) {
        return a[1] < b[1];
    }

    int findLongestChain(vector<vector<int>>& pairs) {
        int n = pairs.size();
        if (n == 0) return 0;

        // Step 1: Pairs ko unke end point (second element) par sort karo
        sort(pairs.begin(), pairs.end(), compare);

        int chain_len = 1;
        int current_end = pairs[0][1];

        // Step 2: Greedily agla valid pair chuno
        for (int i = 1; i < n; ++i) {
            // Agar current pair ka start point pichle ke end se bada hai
            if (pairs[i][0] > current_end) {
                chain_len++;
                current_end = pairs[i][1];
            }
        }
        
        return chain_len;
    }
};

/*
Time Complexity: O(n log n)
Complexity sorting ke kaaran hai. Greedy traversal O(n) mein ho jaata hai.

Space Complexity: O(1) or O(log n)
Agar sorting in-place hoti hai to O(1), varna recursion stack ke liye O(log n).
*/
```

-----

-----

## 10\. Longest Ideal Subsequence (LeetCode 2370)

### **Problem Statement (PS)**

Aapko ek string `s` aur ek integer `k` diya gaya hai. Ek **"ideal" subsequence** aisi subsequence hoti hai jismein har do aaju-baaju ke characters (jaise `c1`, `c2`) ke beech ka absolute alphabetical difference `k` se kam ya barabar hota hai (matlab `abs(c1 - c2) <= k`). Aapko sabse lambi ideal subsequence ki **length** batani hai.

### **Examples**

**Example 1:**

  * **Input:** `s = "acfgbd", k = 2`
  * **Output:** `4`
  * **Explanation:** Sabse lambi ideal subsequence `"acbd"` hai. Inke differences hain: `abs('a'-'c')=2`, `abs('c'-'b')=1`, `abs('b'-'d')=2`. Saare `k=2` se kam ya barabar hain.

**Example 2:**

  * **Input:** `s = "abcd", k = 3`
  * **Output:** `4`
  * **Explanation:** Poori string `"abcd"` hi ek ideal subsequence hai kyunki har adjacent character ka difference 1 hai, jo `k=3` se kam hai.

-----

### **Approach 1: Naive (Dynamic Programming)**

Yeh LIS ka ek variation hai. Hum `dp[i]` mein store karenge ki `s[i]` par khatam hone wali sabse lambi ideal subsequence ki length kya hai.

Har `i` ke liye hum pichle saare `j` (j \< i) ko check karenge. Agar `abs(s[i] - s[j]) <= k` hai, to hum `s[i]` ko `s[j]` par khatam hone wali subsequence ke aage laga sakte hain. Isse `dp[i]` update hoga.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Longest Ideal Subsequence

class Solution {
public:
    int longestIdealString(string s, int k) {
        int n = s.length();
        if (n == 0) return 0;
        
        vector<int> dp(n, 1);
        int max_len = 1;

        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < i; ++j) {
                if (abs(s[i] - s[j]) <= k) {
                    dp[i] = max(dp[i], dp[j] + 1);
                }
            }
            max_len = max(max_len, dp[i]);
        }

        return max_len;
    }
};

/*
Time Complexity: O(n^2)
Do nested loops ke kaaran, jahan n string ki length hai.

Space Complexity: O(n)
DP array ke liye.
*/
```

-----

### **Approach 2: Optimal (DP with Character Array)**

Hum `O(n^2)` ko `O(n)` mein optimize kar sakte hain. Jab hum `s[i]` par hote hain, toh pichle saare `j` check karne ke bajaye, humein bas yeh jaanna hai ki `s[i]` se `k` distance ke andar aane wale characters (`c`) par khatam hone wali sabse lambi sequence ki length kya thi.

Iske liye, hum 26 size ka ek array `dp_char` use karenge. `dp_char['a']` 'a' par khatam hone wali longest ideal subsequence ki length store karega.
Jab hum `s[i]` par aate hain, hum `s[i]` ke `k`-range ke saare characters (e.g., `s[i]-k` se `s[i]+k`) ki `dp_char` values check karke maximum nikalte hain aur usse `dp_char[s[i]]` update karte hain.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Longest Ideal Subsequence

class Solution {
public:
    int longestIdealString(string s, int k) {
        // dp_char[i] -> character ('a'+i) par end hone wali LIS ki length
        vector<int> dp_char(26, 0);
        int max_len = 0;

        for (char ch : s) {
            int current_char_idx = ch - 'a';
            int longest_prev = 0;

            // Sirf k-range ke pichle characters ko dekho
            int start = max(0, current_char_idx - k);
            int end = min(25, current_char_idx + k);
            
            for (int prev_char_idx = start; prev_char_idx <= end; ++prev_char_idx) {
                longest_prev = max(longest_prev, dp_char[prev_char_idx]);
            }
            
            // Current character ke liye length update karo
            dp_char[current_char_idx] = longest_prev + 1;
            max_len = max(max_len, dp_char[current_char_idx]);
        }
        
        return max_len;
    }
};

/*
Time Complexity: O(n)
Hum string ko ek baar traverse karte hain. Andar ka loop constant time (max 26*2) chalta hai,
isliye use O(1) maan sakte hain.

Space Complexity: O(1)
Hum 26 size ka ek fixed array use kar rahe hain.
*/
```

-----

-----

## 11\. Longest Increasing Path in a Matrix (LeetCode 329)

### **Problem Statement (PS)**

Aapko ek `m x n` integers ka matrix diya gaya hai. Aapko usme **sabse lambi increasing path** ki length batani hai. Aap kisi bhi cell se chaar dishaon (left, right, up, down) mein ja sakte hain, lekin diagonally nahi.

### **Examples**

**Example 1:**

  * **Input:** `matrix = [[9,9,4],[6,6,8],[2,1,1]]`
  * **Output:** `4`
  * **Explanation:** Sabse lamba path hai `1 -> 2 -> 6 -> 9`.

**Example 2:**

  * **Input:** `matrix = [[3,4,5],[3,2,6],[2,2,1]]`
  * **Output:** `4`
  * **Explanation:** Sabse lamba path `3 -> 4 -> 5 -> 6` hai. Note: `5` se `6` jaana valid hai.

-----

### **Approach 1: Naive (DFS/Backtracking)**

Is approach mein hum har cell `(i, j)` se ek Depth First Search (DFS) shuru karte hain. Yeh DFS uss cell se shuru hone wale saare possible increasing paths ko explore karega. Hum sabhi starting cells se mile maximum path length ka record rakhte hain. Yeh approach bahut slow hai kyunki yeh ek hi cell se longest path baar-baar calculate karti hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Longest Increasing Path in a Matrix

class Solution {
private:
    int rows, cols;
    // Directions: up, down, left, right
    vector<int> dx = {0, 0, -1, 1};
    vector<int> dy = {-1, 1, 0, 0};

    int dfs(int r, int c, vector<vector<int>>& matrix) {
        int max_path = 1;
        
        for (int i = 0; i < 4; ++i) {
            int new_r = r + dy[i];
            int new_c = c + dx[i];

            if (new_r >= 0 && new_r < rows && new_c >= 0 && new_c < cols && matrix[new_r][new_c] > matrix[r][c]) {
                max_path = max(max_path, 1 + dfs(new_r, new_c, matrix));
            }
        }
        return max_path;
    }

public:
    int longestIncreasingPath(vector<vector<int>>& matrix) {
        if (matrix.empty() || matrix[0].empty()) return 0;
        rows = matrix.size();
        cols = matrix[0].size();
        
        int max_len = 0;
        for (int i = 0; i < rows; ++i) {
            for (int j = 0; j < cols; ++j) {
                max_len = max(max_len, dfs(i, j, matrix));
            }
        }
        return max_len;
    }
};

/*
Time Complexity: O(4^(m*n))
Worst case mein, har cell se hum 4 dishaon mein ja sakte hain. Yeh exponential hai aur TLE dega.

Space Complexity: O(m*n)
Recursion stack ki depth ke liye.
*/
```

-----

### **Approach 2: Optimal (DFS with Memoization)**

Naive DFS ki problem ko solve karne ke liye, hum **memoization** ka istemal karte hain. Hum ek `dp` (ya `cache`) matrix banate hain jo `dp[i][j]` mein cell `(i, j)` se shuru hone wali longest increasing path ki length ko store karega.

Jab hum `dfs(i, j)` call karte hain, sabse pehle hum check karte hain ki `dp[i][j]` pehle se calculated hai ya nahi. Agar hai, to stored value return kar dete hain. Nahi to, hum use calculate karte hain, `dp` matrix mein store karte hain, aur phir return karte hain. Isse har cell ka result sirf ek baar calculate hota hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Longest Increasing Path in a Matrix

class Solution {
private:
    int rows, cols;
    vector<vector<int>> dp;
    vector<int> dx = {0, 0, -1, 1};
    vector<int> dy = {-1, 1, 0, 0};

    int dfs(int r, int c, vector<vector<int>>& matrix) {
        // Agar result pehle se calculated hai
        if (dp[r][c] != 0) {
            return dp[r][c];
        }

        int max_path = 1;
        
        // Chaaron dishaon mein explore karo
        for (int i = 0; i < 4; ++i) {
            int new_r = r + dy[i];
            int new_c = c + dx[i];

            // Check karo ki neighbor valid hai aur value badi hai
            if (new_r >= 0 && new_r < rows && new_c >= 0 && new_c < cols && matrix[new_r][new_c] > matrix[r][c]) {
                max_path = max(max_path, 1 + dfs(new_r, new_c, matrix));
            }
        }
        
        // Result ko cache karo aur return karo
        return dp[r][c] = max_path;
    }

public:
    int longestIncreasingPath(vector<vector<int>>& matrix) {
        if (matrix.empty() || matrix[0].empty()) return 0;
        rows = matrix.size();
        cols = matrix[0].size();
        
        dp.resize(rows, vector<int>(cols, 0));
        
        int max_len = 0;
        for (int i = 0; i < rows; ++i) {
            for (int j = 0; j < cols; ++j) {
                max_len = max(max_len, dfs(i, j, matrix));
            }
        }
        return max_len;
    }
};

/*
Time Complexity: O(m*n)
Har cell ka result (dp[i][j]) sirf ek baar calculate hota hai.

Space Complexity: O(m*n)
DP matrix aur recursion stack, dono ke liye.
*/
```



-----

-----

## 1\. Longest Common Subsequence (LeetCode 1143)

### **Problem Statement (PS)**

Aapko do strings `text1` aur `text2` di gayi hain. Aapko unke sabse lambe **common subsequence** ki **length** batani hai. Ek subsequence kisi string se kuch characters (ya koi nahi) delete karke banta hai, baaki characters ka order badle bina.

### **Examples**

**Example 1:**

  * **Input:** `text1 = "abcde", text2 = "ace"`
  * **Output:** `3`
  * **Explanation:** Sabse lamba common subsequence `"ace"` hai, jiski length 3 hai.

**Example 2:**

  * **Input:** `text1 = "abc", text2 = "def"`
  * **Output:** `0`
  * **Explanation:** Dono strings mein koi bhi character common nahi hai, isliye result 0 hai.

-----

### **Approach 1: Naive (Recursion)**

Yeh ek classic recursive solution hai. Hum dono strings ke pehle character se shuru karte hain.

  * Agar characters match karte hain (`text1[i] == text2[j]`), to humari LCS ki length mein 1 jud jaata hai, aur hum dono strings mein aage badhte hain.
  * Agar match nahi karte, to hum do possibilities try karte hain: ek baar `text1` mein aage badhte hain, aur ek baar `text2` mein. In dono se jo maximum length milti hai, woh humara jawab hota hai.

Yeh approach bahut saari calculations repeat karti hai isliye TLE de sakti hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Longest Common Subsequence

class Solution {
private:
    int solve(string& text1, string& text2, int i, int j) {
        // Base case: agar koi bhi string khatam ho gayi
        if (i == text1.length() || j == text2.length()) {
            return 0;
        }

        // Agar characters match karte hain
        if (text1[i] == text2[j]) {
            return 1 + solve(text1, text2, i + 1, j + 1);
        }
        // Agar match nahi karte
        else {
            return max(solve(text1, text2, i + 1, j), solve(text1, text2, i, j + 1));
        }
    }

public:
    int longestCommonSubsequence(string text1, string text2) {
        return solve(text1, text2, 0, 0);
    }
};

/*
Time Complexity: O(2^(m+n))
Yeh exponential hai kyunki har mismatch par do branches banti hain.

Space Complexity: O(m+n)
Recursion stack ki depth ke liye.
*/
```

-----

### **Approach 2: Optimal (Dynamic Programming - Tabulation)**

Hum recursion ki repeated calculations ko DP se solve karte hain. Hum ek 2D `dp` table banate hain, jahan `dp[i][j]` `text1` ke pehle `i` characters aur `text2` ke pehle `j` characters ke beech LCS ki length store karta hai.

  * Agar `text1[i-1] == text2[j-1]`, to `dp[i][j] = 1 + dp[i-1][j-1]`.
  * Agar match nahi hota, to `dp[i][j] = max(dp[i-1][j], dp[i][j-1])`.

Aakhri cell `dp[m][n]` mein humara final answer hota hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Longest Common Subsequence

class Solution {
public:
    int longestCommonSubsequence(string text1, string text2) {
        int m = text1.length();
        int n = text2.length();

        // dp[i][j] stores LCS of text1[0...i-1] and text2[0...j-1]
        vector<vector<int>> dp(m + 1, vector<int>(n + 1, 0));

        for (int i = 1; i <= m; ++i) {
            for (int j = 1; j <= n; ++j) {
                // Agar characters match karte hain
                if (text1[i - 1] == text2[j - 1]) {
                    dp[i][j] = 1 + dp[i - 1][j - 1];
                }
                // Agar match nahi karte
                else {
                    dp[i][j] = max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }
        
        return dp[m][n];
    }
};


/*
Time Complexity: O(m * n)
Hum m*n size ki DP table ko ek baar bharte hain.

Space Complexity: O(m * n)
DP table ke liye. (Ise O(min(m,n)) mein optimize kiya ja sakta hai).
*/
```

-----

-----

## 2\. Shortest Common Supersequence (LeetCode 1092)

### **Problem Statement (PS)**

Aapko do strings `str1` aur `str2` di gayi hain. Aapko sabse chhoti (shortest) aisi string return karni hai jiske liye `str1` aur `str2` dono uske **subsequences** hon.

### **Examples**

**Example 1:**

  * **Input:** `str1 = "abac", str2 = "cab"`
  * **Output:** `"cabac"`
  * **Explanation:** `"cabac"` mein `"abac"` (c**abac**) aur `"cab"` (**cab**ac) dono as a subsequence maujood hain.

**Example 2:**

  * **Input:** `str1 = "aaaaaaaa", str2 = "aaaaaaaa"`
  * **Output:** `"aaaaaaaa"`
  * **Explanation:** Dono strings same hain, isliye supersequence bhi wahi hogi.

-----

### **Approach 1: Naive (Plain Recursion)**

Hum ek recursive function bana sakte hain jo supersequence ko character by character build kare.

  * Agar `str1[i] == str2[j]`, to hum us character ko ek baar lete hain aur dono strings mein aage badhte hain.
  * Agar match nahi karte, to hum do options explore karte hain: (1) `str1[i]` ko lein aur `str1` mein aage badhein, (2) `str2[j]` ko lein aur `str2` mein aage badhein. Hum woh option chunte hain jo chhoti supersequence de.

Yeh approach TLE degi.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Shortest Common Supersequence

class Solution {
public:
    string solve(string s1, string s2) {
        if (s1.empty()) return s2;
        if (s2.empty()) return s1;

        if (s1[0] == s2[0]) {
            return s1[0] + solve(s1.substr(1), s2.substr(1));
        } else {
            string res1 = s1[0] + solve(s1.substr(1), s2);
            string res2 = s2[0] + solve(s1, s2.substr(1));
            return res1.length() < res2.length() ? res1 : res2;
        }
    }
    
    string shortestCommonSupersequence(string str1, string str2) {
        return solve(str1, str2);
    }
};

/*
Time Complexity: O(2^(m+n))
Exponential complexity ke kaaran TLE dega.

Space Complexity: O(m+n)
Recursion stack ki depth ke liye.
*/
```

-----

### **Approach 2: Optimal (LCS DP Table + Backtracking)**

Is problem ka core idea **LCS** hai. Shortest Common Supersequence ki length `len(str1) + len(str2) - len(LCS)` hoti hai. Hum common characters ko ek hi baar use karte hain.

**Steps:**

1.  Pehle, `str1` aur `str2` ke beech LCS ki poori DP table banayein, bilkul pichle problem ki tarah.
2.  Ab is table par **backtrack** karke string banayein. `dp[m][n]` se shuru karo.
3.  Agar `str1[i-1] == str2[j-1]`, to character common hai. Ise result mein daalo aur diagonally `(i-1, j-1)` par jao.
4.  Agar nahi, to dekho `dp[i-1][j]` aur `dp[i][j-1]` mein se kaun bada hai. Jidhar se aaye ho, uss string ka non-common character result mein daalo aur uss direction mein move karo.
5.  Aakhir mein result ko reverse kar do.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Shortest Common Supersequence

class Solution {
public:
    string shortestCommonSupersequence(string str1, string str2) {
        int m = str1.length();
        int n = str2.length();
        vector<vector<int>> dp(m + 1, vector<int>(n + 1, 0));

        // Step 1: LCS DP table banayein
        for (int i = 1; i <= m; ++i) {
            for (int j = 1; j <= n; ++j) {
                if (str1[i - 1] == str2[j - 1]) {
                    dp[i][j] = 1 + dp[i - 1][j - 1];
                } else {
                    dp[i][j] = max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }

        // Step 2: DP table se backtrack karke string banayein
        string scs = "";
        int i = m, j = n;
        while (i > 0 && j > 0) {
            if (str1[i - 1] == str2[j - 1]) {
                scs += str1[i - 1];
                i--; j--;
            } else if (dp[i - 1][j] > dp[i][j - 1]) {
                scs += str1[i - 1];
                i--;
            } else {
                scs += str2[j - 1];
                j--;
            }
        }
        
        // Bachi hui strings ke characters daalo
        while(i > 0) {
            scs += str1[i - 1];
            i--;
        }
        while(j > 0) {
            scs += str2[j - 1];
            j--;
        }
        
        // Step 3: Result ko reverse karo
        reverse(scs.begin(), scs.end());
        return scs;
    }
};


/*
Time Complexity: O(m * n)
DP table banane mein O(m*n) aur uspar backtrack karne mein O(m+n).

Space Complexity: O(m * n)
DP table ke liye.
*/
```

-----

-----

## 3\. Delete Operation for Two Strings (LeetCode 583)

### **Problem Statement (PS)**

Aapko do strings `word1` aur `word2` di gayi hain. Aapko **minimum number of steps** batane hain jismein aap `word1` aur `word2` ko equal (barabar) bana sakte hain. Ek step mein aap kisi bhi string se ek character delete kar sakte hain.

### **Examples**

**Example 1:**

  * **Input:** `word1 = "sea", word2 = "eat"`
  * **Output:** `2`
  * **Explanation:** "sea" se 's' delete karo (-\> "ea"). "eat" se 't' delete karo (-\> "ea"). Total 2 steps.

**Example 2:**

  * **Input:** `word1 = "leetcode", word2 = "etco"`
  * **Output:** `4`
  * **Explanation:** Dono strings ko "etco" banane ke liye "leetcode" se 4 characters delete karne honge.

-----

### **Approach 1: Naive (LCS by Recursion)**

Is problem ka logic yeh hai ki jo characters dono strings mein common hain (LCS), unhe humein delete nahi karna hai. Baaki sabko delete karna padega.
To minimum deletions ke liye, humein Longest Common Subsequence (LCS) ko maximize karna hoga.

Minimum Deletions = `(len1 - len_LCS) + (len2 - len_LCS)`

Hum LCS ki length plain recursion (jo TLE dega) se nikal sakte hain.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Delete Operation for Two Strings

class Solution {
private:
    int lcs(string& w1, string& w2, int i, int j) {
        if (i == w1.length() || j == w2.length()) {
            return 0;
        }
        if (w1[i] == w2[j]) {
            return 1 + lcs(w1, w2, i + 1, j + 1);
        } else {
            return max(lcs(w1, w2, i + 1, j), lcs(w1, w2, i, j + 1));
        }
    }

public:
    int minDistance(string word1, string word2) {
        int lcs_len = lcs(word1, word2, 0, 0);
        return word1.length() + word2.length() - 2 * lcs_len;
    }
};

/*
Time Complexity: O(2^(m+n))
LCS nikalne ki exponential complexity ke kaaran.

Space Complexity: O(m+n)
Recursion stack depth ke liye.
*/
```

-----

### **Approach 2: Optimal (LCS by DP)**

Bilkul upar wali approach jaisa hi hai, lekin is baar hum LCS ki length efficiently `O(m*n)` mein DP ka use karke nikalenge. Uske baad, hum same formula laga denge.

Minimum Deletions = `len(word1) + len(word2) - 2 * len(LCS)`

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Delete Operation for Two Strings

class Solution {
public:
    int minDistance(string word1, string word2) {
        int m = word1.length();
        int n = word2.length();
        
        // LCS length nikalne ke liye DP
        vector<vector<int>> dp(m + 1, vector<int>(n + 1, 0));
        for (int i = 1; i <= m; ++i) {
            for (int j = 1; j <= n; ++j) {
                if (word1[i - 1] == word2[j - 1]) {
                    dp[i][j] = 1 + dp[i - 1][j - 1];
                } else {
                    dp[i][j] = max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }
        
        int lcs_len = dp[m][n];
        
        // Formula ka use karke result nikalo
        return m + n - 2 * lcs_len;
    }
};


/*
Time Complexity: O(m * n)
LCS nikalne ki DP ki complexity.

Space Complexity: O(m * n)
DP table ke liye.
*/
```

-----

-----

## 4\. Minimum ASCII Delete Sum for Two Strings (LeetCode 712)

### **Problem Statement (PS)**

Aapko do strings `s1` aur `s2` di gayi hain. Aapko dono strings ko equal banane ke liye characters delete karne hain. Aapka goal hai ki delete kiye gaye characters ki **ASCII values ka sum minimum** ho.

### **Examples**

**Example 1:**

  * **Input:** `s1 = "sea", s2 = "eat"`
  * **Output:** `231`
  * **Explanation:** "sea" se 's' (ASCII 115) aur "eat" se 't' (ASCII 116) delete karo. Sum = 115 + 116 = 231.

**Example 2:**

  * **Input:** `s1 = "delete", s2 = "leet"`
  * **Output:** `403`
  * **Explanation:** "delete" se 'd', 'e', 'e' delete karo aur "leet" se 'l' delete karo. Sum = 100+101+101 + 108 = 410. Wait, better is to make them "eet". Delete 'd','l' from delete. Delete nothing from leet. No... make "let". Del 'd','e','e' -\> 'let'. Del 'e' -\> 'let'.
    Let's re-verify. "delete", "leet". LCS is "eet".
    Sum(delete) = d+e+l+e+t+e = 100+101+108+101+116+101 = 627.
    Sum(leet) = l+e+e+t = 108+101+101+116 = 426.
    Total Sum = 1053.
    LCS with max ASCII sum is "eet". Sum = 101+101+116 = 318.
    Result = Total Sum - 2 \* (Max ASCII sum LCS) = 1053 - 2 \* 318 = 1053 - 636 = 417. Let me check the problem.
    Ah, my logic is flawed. A simpler DP is better.
    `dp[i][j]` = min cost for `s1[i...]` and `s2[j...]`.
    My re-calculated answer is 403. Let's trace it.
    Make "eet". From "delete", delete 'd', 'l'. Sum = 100+108 = 208. From "leet", delete 'l'. Sum = 108. Total=316.
    Make "let". From "delete", delete 'd','e','e'. Sum = 100+101+101=302. From "leet", delete 'e'. Sum=101. Total=403. This is correct.

-----

### **Approach 1: Naive (Recursion)**

Ismein hum delete cost ko directly calculate karte hain. Hum `solve(i, j)` function banate hain jo `s1[i:]` aur `s2[j:]` ko equal banane ka min cost batata hai.

  * Agar `s1[i] == s2[j]`, to in characters ko delete nahi karna. Cost `solve(i+1, j+1)` se aayega.
  * Agar `s1[i] != s2[j]`, to humare paas do choice hain:
    1.  `s1[i]` ko delete karo: Cost = `s1[i]` + `solve(i+1, j)`
    2.  `s2[j]` ko delete karo: Cost = `s2[j]` + `solve(i, j+1)`
        Hum in dono mein se minimum wala chunte hain.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Minimum ASCII Delete Sum for Two Strings

class Solution {
private:
    int solve(string& s1, string& s2, int i, int j) {
        // Base case: agar dono strings end ho gayi
        if (i == s1.length() && j == s2.length()) return 0;

        // Agar s1 end ho gayi, toh s2 ke baaki characters ko delete karna padega
        if (i == s1.length()) {
            int cost = 0;
            for (int k = j; k < s2.length(); ++k) cost += s2[k];
            return cost;
        }
        
        // Agar s2 end ho gayi
        if (j == s2.length()) {
            int cost = 0;
            for (int k = i; k < s1.length(); ++k) cost += s1[k];
            return cost;
        }

        if (s1[i] == s2[j]) {
            return solve(s1, s2, i + 1, j + 1);
        } else {
            return min(s1[i] + solve(s1, s2, i + 1, j),
                       s2[j] + solve(s1, s2, i, j + 1));
        }
    }

public:
    int minimumDeleteSum(string s1, string s2) {
        return solve(s1, s2, 0, 0);
    }
};

/*
Time Complexity: O(2^(m+n))
Exponential complexity.

Space Complexity: O(m+n)
Recursion stack ke liye.
*/
```

-----

### **Approach 2: Optimal (Dynamic Programming)**

Hum upar wali recursive approach ko DP se optimize karenge. Hum ek 2D `dp` table banayenge, jahan `dp[i][j]` `s1` ke pehle `i` characters aur `s2` ke pehle `j` characters ko equal banane ka minimum ASCII delete sum store karega.

Hum table ko bottom-up fill karenge.

  * `dp[i][j]` = `dp[i-1][j-1]` agar `s1[i-1] == s2[j-1]` (koi cost nahi).
  * `dp[i][j]` = `min(dp[i-1][j] + s1[i-1], dp[i][j-1] + s2[j-1])` agar match nahi karte.

Base cases initialize karna important hai (jab ek string empty ho).

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Minimum ASCII Delete Sum for Two Strings

class Solution {
public:
    int minimumDeleteSum(string s1, string s2) {
        int m = s1.length();
        int n = s2.length();

        // dp[i][j] = min delete sum for s1[0...i-1] and s2[0...j-1]
        vector<vector<int>> dp(m + 1, vector<int>(n + 1, 0));

        // Base cases
        // Agar s1 empty hai, toh s2 ke saare characters delete karne honge
        for (int j = 1; j <= n; ++j) {
            dp[0][j] = dp[0][j - 1] + s2[j - 1];
        }
        // Agar s2 empty hai, toh s1 ke saare characters delete karne honge
        for (int i = 1; i <= m; ++i) {
            dp[i][0] = dp[i - 1][0] + s1[i - 1];
        }

        // DP table fill karo
        for (int i = 1; i <= m; ++i) {
            for (int j = 1; j <= n; ++j) {
                if (s1[i - 1] == s2[j - 1]) {
                    // Characters match, koi deletion cost nahi
                    dp[i][j] = dp[i - 1][j - 1];
                } else {
                    // Match nahi, min cost wala deletion karo
                    dp[i][j] = min(dp[i - 1][j] + s1[i - 1],  // s1[i-1] ko delete karo
                                   dp[i][j - 1] + s2[j - 1]); // s2[j-1] ko delete karo
                }
            }
        }

        return dp[m][n];
    }
};


/*
Time Complexity: O(m * n)
DP table ko bharne mein laga time.

Space Complexity: O(m * n)
DP table ke liye.
*/
```




-----

-----

## 5\. Interleaving String (LeetCode 97)

### **Problem Statement (PS)**

Aapko teen strings `s1`, `s2`, aur `s3` di gayi hain. Aapko yeh check karna hai ki kya `s3` string `s1` aur `s2` ke characters ko aapas mein milakar (interleave karke) banayi ja sakti hai, is tarah ki `s1` aur `s2` ke andar ke characters ka relative order na badle.

### **Examples**

**Example 1:**

  * **Input:** `s1 = "aabcc", s2 = "dbbca", s3 = "aadbbcbcac"`
  * **Output:** `true`
  * **Explanation:** `s3` ko `s1` ke `aabcc` aur `s2` ke `dbbca` ko interleave karke banaya ja sakta hai.

**Example 2:**

  * **Input:** `s1 = "aabcc", s2 = "dbbca", s3 = "aadbbbaccc"`
  * **Output:** `false`
  * **Explanation:** `s3` ko `s1` aur `s2` ke characters se unka order banaye rakhte hue nahi banaya ja sakta.

-----

### **Approach 1: Naive (Recursion)**

Hum ek recursive function banayenge jo `s1`, `s2` aur `s3` ke pointers (`i`, `j`, `k`) lega.

  * Agar `s3` ka current character (`s3[k]`) `s1` ke current character (`s1[i]`) se match hota hai, to hum us match ko consider karke `s1` aur `s3` mein aage badhte hain.
  * Agar `s3[k]` `s2[j]` se match hota hai, to hum us match ko consider karke `s2` aur `s3` mein aage badhte hain.
  * Agar dono se match hota hai, to hum dono रास्ते try karte hain. Agar kisi bhi raaste se `s3` poora ban jaata hai, to jawab `true` hai.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Interleaving String

class Solution {
private:
    bool solve(string& s1, string& s2, string& s3, int i, int j, int k) {
        // Base case: agar s3 poori ban gayi
        if (k == s3.length()) {
            return (i == s1.length() && j == s2.length());
        }

        bool res = false;
        // Option 1: s3 ka current character s1 se match kare
        if (i < s1.length() && s1[i] == s3[k]) {
            res = res || solve(s1, s2, s3, i + 1, j, k + 1);
        }
        // Option 2: s3 ka current character s2 se match kare
        if (j < s2.length() && s2[j] == s3[k]) {
            res = res || solve(s1, s2, s3, i, j + 1, k + 1);
        }
        
        return res;
    }

public:
    bool isInterleave(string s1, string s2, string s3) {
        // Shuruaati check: length barabar honi chahiye
        if (s1.length() + s2.length() != s3.length()) {
            return false;
        }
        return solve(s1, s2, s3, 0, 0, 0);
    }
};


/*
Time Complexity: O(2^(m+n))
Exponential kyunki har step par do branches ho sakti hain.

Space Complexity: O(m+n)
Recursion stack ki depth ke liye.
*/
```

-----

### **Approach 2: Optimal (Dynamic Programming)**

Hum recursion ko memoization ya tabulation se optimize kar sakte hain. Hum ek 2D `dp` table banayenge. `dp[i][j]` `true` hoga agar `s3` ke pehle `i+j` characters `s1` ke pehle `i` aur `s2` ke pehle `j` characters ko interleave karke banaye ja sakte hain.

  * `dp[i][j]` `true` hoga agar:
    1.  `s1` ka `i`-th character `s3` ke `(i+j)`-th character se match kare AUR `dp[i-1][j]` `true` ho.
    2.  YA `s2` ka `j`-th character `s3` ke `(i+j)`-th character se match kare AUR `dp[i][j-1]` `true` ho.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Interleaving String

class Solution {
public:
    bool isInterleave(string s1, string s2, string s3) {
        int m = s1.length();
        int n = s2.length();
        int l = s3.length();

        if (m + n != l) {
            return false;
        }

        // dp[i][j] = s1[0...i-1] aur s2[0...j-1] kya s3[0...i+j-1] banate hain?
        vector<vector<bool>> dp(m + 1, vector<bool>(n + 1, false));

        for (int i = 0; i <= m; ++i) {
            for (int j = 0; j <= n; ++j) {
                if (i == 0 && j == 0) {
                    dp[i][j] = true;
                } else if (i == 0) { // Sirf s2 se matching
                    dp[i][j] = (s2[j - 1] == s3[j - 1]) && dp[i][j - 1];
                } else if (j == 0) { // Sirf s1 se matching
                    dp[i][j] = (s1[i - 1] == s3[i - 1]) && dp[i - 1][j];
                } else {
                    bool from_s1 = (s1[i - 1] == s3[i + j - 1]) && dp[i - 1][j];
                    bool from_s2 = (s2[j - 1] == s3[i + j - 1]) && dp[i][j - 1];
                    dp[i][j] = from_s1 || from_s2;
                }
            }
        }
        
        return dp[m][n];
    }
};

/*
Time Complexity: O(m * n)
Hum m*n size ki DP table ko ek baar bharte hain.

Space Complexity: O(m * n)
DP table ke liye. (Ise O(n) mein optimize kiya ja sakta hai).
*/
```

-----

-----

## 6\. Distinct Subsequences (LeetCode 115)

### **Problem Statement (PS)**

Aapko do strings `s` aur `t` di gayi hain. Aapko yeh batana hai ki `s` ke kitne alag-alag **subsequences** hain jo `t` ke barabar hain. Jawab bada ho sakta hai isliye use integer ki range mein aana chahiye.

### **Examples**

**Example 1:**

  * **Input:** `s = "rabbbit", t = "rabbit"`
  * **Output:** `3`
  * **Explanation:** `t` ko `s` se 3 tareeko se banaya ja sakta hai: `r_abbit`, `ra_bbit`, `rab_bit`.

**Example 2:**

  * **Input:** `s = "babgbag", t = "bag"`
  * **Output:** `5`
  * **Explanation:** `s` mein 5 alag-alag "bag" subsequences hain.

-----

### **Approach 1: Naive (Recursion)**

Hum ek recursive function `solve(i, j)` banate hain jo `s` ke index `i` se aur `t` ke index `j` se shuru hone par distinct subsequences ka count dega.

  * Agar `s[i] == t[j]`, to humare paas do choice hain:
    1.  Is character ko match karo aur aage badho: `solve(i+1, j+1)`.
    2.  Is character ko ignore karke `s` mein `t[j]` ko aage dhundho: `solve(i+1, j)`.
        In dono ka sum humara jawab hoga.
  * Agar `s[i] != t[j]`, to humein `s[i]` ko ignore karna hi padega: `solve(i+1, j)`.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Distinct Subsequences

class Solution {
private:
    int solve(string& s, string& t, int i, int j) {
        // Base case: agar t poori match ho gayi
        if (j == t.length()) {
            return 1;
        }
        // Base case: agar s khatam ho gayi lekin t nahi
        if (i == s.length()) {
            return 0;
        }

        // Agar characters match karte hain
        if (s[i] == t[j]) {
            // Option 1: Match karo + Option 2: Match na karo
            return solve(s, t, i + 1, j + 1) + solve(s, t, i + 1, j);
        }
        // Agar match nahi karte
        else {
            return solve(s, t, i + 1, j);
        }
    }

public:
    int numDistinct(string s, string t) {
        return solve(s, t, 0, 0);
    }
};

/*
Time Complexity: O(2^n)
Exponential complexity ke kaaran TLE dega.

Space Complexity: O(n+m)
Recursion stack ki depth ke liye.
*/
```

-----

### **Approach 2: Optimal (Dynamic Programming)**

Hum DP ka use karke is problem ko efficiently solve kar sakte hain. `dp[i][j]` ka matlab hoga `s` ke pehle `i` characters se `t` ke pehle `j` characters banane ke kitne tareeke hain.

  * Agar `s[i-1] == t[j-1]`, to `dp[i][j]` do cheezon ka sum hoga:
    1.  `s[i-1]` ko use kiye bina (`dp[i-1][j]`).
    2.  `s[i-1]` ko `t[j-1]` se match karke (`dp[i-1][j-1]`).
  * Agar `s[i-1] != t[j-1]`, to hum `s[i-1]` ko use nahi kar sakte, isliye `dp[i][j] = dp[i-1][j]`.

Jawab bada ho sakta hai, isliye DP table mein `unsigned long long` use karna safe hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Distinct Subsequences

class Solution {
public:
    int numDistinct(string s, string t) {
        int m = s.length();
        int n = t.length();

        // dp[i][j] -> s[0..i-1] se t[0..j-1] banane ke tareeke
        // Jawab bada ho sakta hai isliye double ya unsigned long long use karo
        vector<vector<double>> dp(m + 1, vector<double>(n + 1, 0));
        
        // Base case: empty string se empty string banane ka 1 tareeka hai
        for (int i = 0; i <= m; ++i) {
            dp[i][0] = 1;
        }

        for (int i = 1; i <= m; ++i) {
            for (int j = 1; j <= n; ++j) {
                // Pehla case: s[i-1] ko use na karein
                dp[i][j] = dp[i - 1][j];
                // Dusra case: agar character match hota hai, toh use karne ka option bhi add karo
                if (s[i - 1] == t[j - 1]) {
                    dp[i][j] += dp[i - 1][j - 1];
                }
            }
        }
        
        return (int)dp[m][n];
    }
};

/*
Time Complexity: O(m * n)
DP table ko bharne mein laga time.

Space Complexity: O(m * n)
DP table ke liye. (Ise O(n) mein optimize kiya ja sakta hai).
*/
```

-----

-----

## 7\. Edit Distance (LeetCode 72)

### **Problem Statement (PS)**

Aapko do strings `word1` aur `word2` di gayi hain. Aapko `word1` ko `word2` mein badalne ke liye minimum kitne **operations** lagenge, yeh batana hai. Aap 3 tarah ke operations kar sakte hain:

1.  **Insert** a character
2.  **Delete** a character
3.  **Replace** a character

### **Examples**

**Example 1:**

  * **Input:** `word1 = "horse", word2 = "ros"`
  * **Output:** `3`
  * **Explanation:** `horse` -\> `rorse` (replace 'h' with 'r'), `rorse` -\> `rose` (delete 'r'), `rose` -\> `ros` (delete 'e').

**Example 2:**

  * **Input:** `word1 = "intention", word2 = "execution"`
  * **Output:** `5`

-----

### **Approach 1: Naive (Recursion)**

Hum `solve(i, j)` function banate hain jo `word1[i:]` ko `word2[j:]` mein badalne ka minimum cost dega.

  * Agar `word1[i] == word2[j]`, to koi operation nahi karna. Cost `solve(i+1, j+1)` se aayega.
  * Agar `word1[i] != word2[j]`, to humare paas 3 choices hain, aur hum unka minimum lenge:
    1.  **Insert:** `1 + solve(i, j+1)`
    2.  **Delete:** `1 + solve(i+1, j)`
    3.  **Replace:** `1 + solve(i+1, j+1)`

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Edit Distance

class Solution {
private:
    int solve(string& w1, string& w2, int i, int j) {
        // Base case: agar word1 khatam, toh word2 ke baaki characters insert karne honge
        if (i == w1.length()) return w2.length() - j;
        // Base case: agar word2 khatam, toh word1 ke baaki characters delete karne honge
        if (j == w2.length()) return w1.length() - i;

        if (w1[i] == w2[j]) {
            return solve(w1, w2, i + 1, j + 1);
        } else {
            int insert_op = 1 + solve(w1, w2, i, j + 1);
            int delete_op = 1 + solve(w1, w2, i + 1, j);
            int replace_op = 1 + solve(w1, w2, i + 1, j + 1);
            return min({insert_op, delete_op, replace_op});
        }
    }
public:
    int minDistance(string word1, string word2) {
        return solve(word1, word2, 0, 0);
    }
};

/*
Time Complexity: O(3^(m+n))
Har step par 3 branches ho sakti hain. Exponential.

Space Complexity: O(m+n)
Recursion stack depth ke liye.
*/
```

-----

### **Approach 2: Optimal (Dynamic Programming)**

Yeh Levenshtein distance ka classic DP solution hai. Hum ek `dp[i][j]` table banate hain, jo `word1` ke pehle `i` characters ko `word2` ke pehle `j` characters mein badalne ka min cost store karti hai.

  * Agar `word1[i-1] == word2[j-1]`, to `dp[i][j] = dp[i-1][j-1]` (koi naya operation nahi).
  * Agar match nahi karte, to `dp[i][j] = 1 + min(dp[i-1][j], dp[i][j-1], dp[i-1][j-1])`. Yahan `min` ke andar teeno operations (delete, insert, replace) ki costs hain.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Edit Distance

class Solution {
public:
    int minDistance(string word1, string word2) {
        int m = word1.length();
        int n = word2.length();
        
        vector<vector<int>> dp(m + 1, vector<int>(n + 1, 0));
        
        // Base cases: empty string ko badalne ke liye
        for (int i = 0; i <= m; ++i) dp[i][0] = i; // i deletes
        for (int j = 0; j <= n; ++j) dp[0][j] = j; // j inserts
        
        for (int i = 1; i <= m; ++i) {
            for (int j = 1; j <= n; ++j) {
                if (word1[i - 1] == word2[j - 1]) {
                    dp[i][j] = dp[i - 1][j - 1];
                } else {
                    dp[i][j] = 1 + min({
                        dp[i - 1][j],      // Delete
                        dp[i][j - 1],      // Insert
                        dp[i - 1][j - 1]   // Replace
                    });
                }
            }
        }
        
        return dp[m][n];
    }
};


/*
Time Complexity: O(m * n)
DP table ko bharne mein laga time.

Space Complexity: O(m * n)
DP table ke liye.
*/
```

-----

-----

## 8\. Regular Expression Matching (LeetCode 10)

### **Problem Statement (PS)**

Aapko ek input string `s` aur ek pattern `p` diya gaya hai. Pattern `p` mein do special characters ho sakte hain:

  * `.` (dot) : Kisi bhi ek single character se match karta hai.
  * `*` (asterisk) : Apne se just pehle wale character ke **zero ya zyada** occurrences se match karta hai.

Aapko batana hai ki kya pattern `p` poori string `s` se match karta hai.

### **Examples**

**Example 1:**

  * **Input:** `s = "aa", p = "a*"`
  * **Output:** `true`
  * **Explanation:** `*` ka matlab 'a' ka zero ya zyada baar aana. Yahan 'a' do baar aakar `s` se match kar gaya.

**Example 2:**

  * **Input:** `s = "ab", p = ".*"`
  * **Output:** `true`
  * **Explanation:** `.` ka matlab koi bhi character, aur `*` ka matlab zero ya zyada baar. Toh `.*` ka matlab "kuchh bhi, kitni bhi baar".

-----

### **Approach 1: Naive (Recursion)**

Yeh problem recursion se solve ho sakti hai, lekin `*` ka case thoda tricky hai. `solve(i, j)` check karega ki `s[i:]` `p[j:]` se match hota hai ya nahi.

  * Agar agla character `*` hai (`p[j+1] == '*'`), to do choices hain:
    1.  `*` ke pattern (`p[j]`) ko zero baar use karo aur pattern mein 2 aage badh jao (`solve(i, j+2)`).
    2.  Agar `s[i]` `p[j]` se match hota hai, to `s[i]` ko consume karo aur `s` mein 1 aage badho (`solve(i+1, j)`).
  * Agar agla character `*` nahi hai, to normal match karo.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Regular Expression Matching

class Solution {
public:
    bool isMatch(string s, string p) {
        // Base case: agar pattern khatam
        if (p.empty()) return s.empty();

        bool first_match = (!s.empty() && (p[0] == s[0] || p[0] == '.'));

        if (p.length() >= 2 && p[1] == '*') {
            // Case 1: * ko zero match ke liye use karo
            // Case 2: * ko ek ya zyada match ke liye use karo
            return (isMatch(s, p.substr(2)) ||
                    (first_match && isMatch(s.substr(1), p)));
        } else {
            return first_match && isMatch(s.substr(1), p.substr(1));
        }
    }
};

/*
Time Complexity: O(2^(m+n))
Exponential.

Space Complexity: O(m+n)
Recursion stack ki depth ke liye.
*/
```

-----

### **Approach 2: Optimal (Dynamic Programming)**

Hum ek `dp[i][j]` table banayenge jo batayega ki kya `s` ke pehle `i` characters `p` ke pehle `j` characters se match karte hain.

  * Agar `p[j-1]` ek normal character ya `.` hai: `dp[i][j] = dp[i-1][j-1]` agar characters match karte hain.

  * Agar `p[j-1]` `*` hai:

      * Yeh do cheezon ko represent karta hai: `p[j-2]*`.

    <!-- end list -->

    1.  `*` ko zero match ke liye use karein: Is case mein `p[j-2]*` ko ignore kar sakte hain, to result `dp[i][j-2]` par depend karega.
    2.  `*` ko ek ya zyada match ke liye use karein: Is case mein `s[i-1]` ko `p[j-2]` se match karna hoga, aur baaki `s[0...i-2]` ko `p[0...j-1]` (yaani `p[j-2]*` ke saath) se match hona chahiye, to result `dp[i-1][j]` par depend karega.

    Final transition: `dp[i][j] = dp[i][j-2] || (first_match && dp[i-1][j])`.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Regular Expression Matching

class Solution {
public:
    bool isMatch(string s, string p) {
        int m = s.length(), n = p.length();
        vector<vector<bool>> dp(m + 1, vector<bool>(n + 1, false));
        dp[0][0] = true;

        // "a*", "a*b*", "a*b*c*" jaise patterns ko handle karna
        for (int j = 1; j <= n; j++) {
            if (p[j - 1] == '*') {
                dp[0][j] = dp[0][j - 2];
            }
        }

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (p[j - 1] == '.' || p[j - 1] == s[i - 1]) {
                    dp[i][j] = dp[i - 1][j - 1];
                } else if (p[j - 1] == '*') {
                    dp[i][j] = dp[i][j - 2]; // Zero occurrences
                    if (p[j - 2] == '.' || p[j - 2] == s[i - 1]) {
                        dp[i][j] = dp[i][j] || dp[i - 1][j]; // One or more occurrences
                    }
                } else {
                    dp[i][j] = false;
                }
            }
        }
        return dp[m][n];
    }
};


/*
Time Complexity: O(m * n)
DP table ko bharne ka time.

Space Complexity: O(m * n)
DP table ke liye.
*/
```

-----

-----

## 9\. Wildcard Matching (LeetCode 44)

### **Problem Statement (PS)**

Aapko ek input string `s` aur ek pattern `p` diya gaya hai. Pattern `p` mein do special characters ho sakte hain:

  * `?` : Kisi bhi ek single character se match karta hai.
  * `*` : Kisi bhi sequence of characters (khaali sequence सहित) se match karta hai.

Aapko batana hai ki kya pattern `p` poori string `s` se match karta hai.

### **Examples**

**Example 1:**

  * **Input:** `s = "aa", p = "*"`
  * **Output:** `true`
  * **Explanation:** `*` poori string "aa" se match kar sakta hai.

**Example 2:**

  * **Input:** `s = "cb", p = "?a"`
  * **Output:** `false`
  * **Explanation:** `?` 'c' se match ho jaayega, lekin 'a' 'b' se match nahi hoga.

-----

### **Approach 1: Naive (Recursion)**

Yeh Regex matching se thoda aasan hai. `solve(i, j)` check karega ki `s[i:]` `p[j:]` se match hota hai ya nahi.

  * Agar `p[j] == '*'` hai:
    1.  `*` ko empty sequence maano: `solve(i, j+1)`.
    2.  `*` ko `s[i]` se match karo aur `s` mein aage badho: `solve(i+1, j)`.
  * Agar `p[j] == '?'` ya `p[j] == s[i]`, to dono mein aage badho: `solve(i+1, j+1)`.
  * Baki sab cases mein `false`.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Wildcard Matching

class Solution {
private:
    bool solve(string& s, string& p, int i, int j) {
        // Base case: pattern khatam
        if (j == p.length()) return i == s.length();
        // Base case: string khatam
        if (i == s.length()) {
            // Baaki ka pattern sirf '*' hona chahiye
            for(int k=j; k<p.length(); ++k) if(p[k] != '*') return false;
            return true;
        }

        if (p[j] == '*') {
            // Option 1: * ko empty maano | Option 2: * ko ek char se match karo
            return solve(s, p, i, j + 1) || solve(s, p, i + 1, j);
        } else if (p[j] == '?' || s[i] == p[j]) {
            return solve(s, p, i + 1, j + 1);
        } else {
            return false;
        }
    }

public:
    bool isMatch(string s, string p) {
        return solve(s, p, 0, 0);
    }
};

/*
Time Complexity: O(2^(m+n))
Exponential.

Space Complexity: O(m+n)
Recursion stack ke liye.
*/
```

-----

### **Approach 2: Optimal (Dynamic Programming)**

Hum ek `dp[i][j]` table banayenge jo batayega ki kya `s` ke pehle `i` characters `p` ke pehle `j` characters se match karte hain.

  * Agar `p[j-1]` `?` hai ya `s[i-1]` se match karta hai: `dp[i][j] = dp[i-1][j-1]`.
  * Agar `p[j-1]` `*` hai:
    1.  `*` ko empty sequence maano. Iska matlab `p` ke `j-1` characters `s` ke `i` characters se match hone chahiye. Result `dp[i][j-1]` par depend karega.
    2.  `*` ko ek ya zyada characters se match karo. Iska matlab `p` ke `j` characters `s` ke `i-1` characters se match hone chahiye. Result `dp[i-1][j]` par depend karega.
        Final transition: `dp[i][j] = dp[i-1][j] || dp[i][j-1]`.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Wildcard Matching

class Solution {
public:
    bool isMatch(string s, string p) {
        int m = s.length();
        int n = p.length();
        
        vector<vector<bool>> dp(m + 1, vector<bool>(n + 1, false));
        dp[0][0] = true;
        
        // Base case: agar s empty hai
        for (int j = 1; j <= n; j++) {
            if (p[j - 1] == '*') {
                dp[0][j] = dp[0][j - 1];
            }
        }
        
        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (p[j - 1] == '*') {
                    // Option 1: * ko empty maano
                    // Option 2: * ko ek char se match karo
                    dp[i][j] = dp[i][j - 1] || dp[i - 1][j];
                } else if (p[j - 1] == '?' || s[i - 1] == p[j - 1]) {
                    dp[i][j] = dp[i - 1][j - 1];
                } else {
                    dp[i][j] = false;
                }
            }
        }
        
        return dp[m][n];
    }
};

/*
Time Complexity: O(m * n)
DP table ko bharne ka time.

Space Complexity: O(m * n)
DP table ke liye.
*/
```



-----

-----

## 10\. Uncrossed Lines (LeetCode 1035)

### **Problem Statement (PS)**

Aapko do integer arrays `nums1` aur `nums2` diye gaye hain. Aap `nums1` ke ek element `nums1[i]` aur `nums2` ke ek element `nums2[j]` ke beech ek line (rekha) kheench sakte hain agar dono ki value barabar ho (`nums1[i] == nums2[j]`). Aapko aisi maximum lines banani hain jismein koi bhi do lines aapas mein **cross** na karein.

### **Examples**

**Example 1:**

  * **Input:** `nums1 = [1,4,2], nums2 = [1,2,4]`
  * **Output:** `2`
  * **Explanation:** Hum `nums1[0]` (value 1) ko `nums2[0]` (value 1) se aur `nums1[2]` (value 2) ko `nums2[1]` (value 2) se connect kar sakte hain. Isse 2 non-crossing lines banti hain.

**Example 2:**

  * **Input:** `nums1 = [2,5,1,2,5], nums2 = [10,5,2,1,5,2]`
  * **Output:** `3`
  * **Explanation:** Hum 3 lines bana sakte hain jo `[5, 2, 5]` ya `[5, 1, 2]` jaise common subsequences ko represent karti hain.

-----

### **Approach 1: Naive (Recursion)**

Yeh problem asal mein **Longest Common Subsequence (LCS)** nikalne jaisa hi hai. Lines ka cross na karne ka matlab hai ki agar hum `nums1[i]` ko `nums2[j]` se jodte hain, to agla connection `nums1[i']` se `nums2[j']` ke liye `i' > i` aur `j' > j` hona chahiye. Yeh LCS ki definition hai.

Hum LCS nikalne ke liye plain recursion use kar sakte hain, jo TLE dega.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Uncrossed Lines

class Solution {
private:
    int solve(vector<int>& n1, vector<int>& n2, int i, int j) {
        // Base case: agar koi bhi array khatam ho gaya
        if (i == n1.size() || j == n2.size()) {
            return 0;
        }

        // Agar elements match karte hain, ek line ban gayi
        if (n1[i] == n2[j]) {
            return 1 + solve(n1, n2, i + 1, j + 1);
        }
        // Agar match nahi karte
        else {
            return max(solve(n1, n2, i + 1, j), solve(n1, n2, i, j + 1));
        }
    }

public:
    int maxUncrossedLines(vector<int>& nums1, vector<int>& nums2) {
        return solve(nums1, nums2, 0, 0);
    }
};

/*
Time Complexity: O(2^(m+n))
Yeh exponential hai kyunki har mismatch par do branches banti hain.

Space Complexity: O(m+n)
Recursion stack ki depth ke liye.
*/
```

-----

### **Approach 2: Optimal (Dynamic Programming - LCS)**

Kyunki yeh problem LCS hi hai, hum isko solve karne ke liye standard DP approach ka istemal karenge. Hum ek 2D `dp` table banayenge, jahan `dp[i][j]` `nums1` ke pehle `i` elements aur `nums2` ke pehle `j` elements ke beech maximum uncrossed lines (ya LCS length) ko store karega.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Uncrossed Lines

class Solution {
public:
    int maxUncrossedLines(vector<int>& nums1, vector<int>& nums2) {
        int m = nums1.size();
        int n = nums2.size();

        // dp[i][j] stores LCS of nums1[0...i-1] and nums2[0...j-1]
        vector<vector<int>> dp(m + 1, vector<int>(n + 1, 0));

        for (int i = 1; i <= m; ++i) {
            for (int j = 1; j <= n; ++j) {
                // Agar elements match karte hain
                if (nums1[i - 1] == nums2[j - 1]) {
                    dp[i][j] = 1 + dp[i - 1][j - 1];
                }
                // Agar match nahi karte
                else {
                    dp[i][j] = max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }
        
        return dp[m][n];
    }
};


/*
Time Complexity: O(m * n)
Hum m*n size ki DP table ko ek baar bharte hain.

Space Complexity: O(m * n)
DP table ke liye.
*/
```

-----

-----

## 11\. Longest Palindromic Subsequence (LeetCode 516)

### **Problem Statement (PS)**

Aapko ek string `s` di gayi hai. Aapko uski sabse lambi **palindromic subsequence** ki **length** batani hai. Palindrome woh hota hai jo aage aur peeche se padhne par same ho.

### **Examples**

**Example 1:**

  * **Input:** `s = "bbbab"`
  * **Output:** `4`
  * **Explanation:** Sabse lambi palindromic subsequence `"bbbb"` hai.

**Example 2:**

  * **Input:** `s = "cbbd"`
  * **Output:** `2`
  * **Explanation:** Sabse lambi palindromic subsequence `"bb"` hai.

-----

### **Approach 1: Naive (Recursion)**

Hum ek recursive function `solve(i, j)` banate hain jo string ke हिस्से `s[i...j]` ke liye LPS ki length nikalega.

  * Agar `s[i] == s[j]`, iska matlab yeh dono characters palindrome ka hissa ban sakte hain. To length hogi `2 + solve(i+1, j-1)`.
  * Agar `s[i] != s[j]`, to hum ya to `i` ko chhodenge (`solve(i+1, j)`) ya `j` ko (`solve(i, j-1)`) aur dono se maximum lenge.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Longest Palindromic Subsequence

class Solution {
private:
    vector<vector<int>> memo;
    int solve(string& s, int i, int j) {
        // Base case 1: ek hi character bacha
        if (i == j) return 1;
        // Base case 2: invalid range
        if (i > j) return 0;
        
        if (memo[i][j] != -1) return memo[i][j];

        if (s[i] == s[j]) {
            return memo[i][j] = 2 + solve(s, i + 1, j - 1);
        } else {
            return memo[i][j] = max(solve(s, i + 1, j), solve(s, i, j - 1));
        }
    }

public:
    int longestPalindromeSubseq(string s) {
        int n = s.length();
        memo.resize(n, vector<int>(n, -1));
        return solve(s, 0, n - 1);
    }
};

/*
Time Complexity: O(2^n) without memoization. With memoization (as coded), it is O(n^2).
Is code mein maine memoization use kiya hai, jo ise optimal bana deta hai,
par logic recursive (naive) soch par based hai.

Space Complexity: O(n^2)
Memoization table aur recursion stack ke liye.
*/
```

-----

### **Approach 2: Optimal (DP using LCS on Reversed String)**

Yeh ek bahut clever trick hai. Kisi bhi string `s` ka **Longest Palindromic Subsequence** uss string `s` aur uske reverse `rev_s` ke beech ka **Longest Common Subsequence (LCS)** hota hai.

**Steps:**

1.  Di gayi string `s` ka reverse karke ek nayi string `rev_s` banayein.
2.  `s` aur `rev_s` ke beech LCS ki length standard DP se nikal lein.
3.  Wahi length humara jawab hoga.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Longest Palindromic Subsequence

class Solution {
public:
    int longestPalindromeSubseq(string s) {
        string rev_s = s;
        reverse(rev_s.begin(), rev_s.end());
        
        int n = s.length();
        vector<vector<int>> dp(n + 1, vector<int>(n + 1, 0));

        // s aur rev_s ke beech LCS nikalo
        for (int i = 1; i <= n; ++i) {
            for (int j = 1; j <= n; ++j) {
                if (s[i - 1] == rev_s[j - 1]) {
                    dp[i][j] = 1 + dp[i - 1][j - 1];
                } else {
                    dp[i][j] = max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }
        
        return dp[n][n];
    }
};


/*
Time Complexity: O(n^2)
LCS nikalne ki DP ki complexity.

Space Complexity: O(n^2)
DP table ke liye.
*/
```

-----

-----

## 12\. Palindrome Partitioning II (LeetCode 132)

### **Problem Statement (PS)**

Aapko ek string `s` di gayi hai. Aapko string `s` ko aisi substrings mein partition (katna) hai ki har substring ek **palindrome** ho. Aapko is kaam ke liye **minimum kitne cuts** lagenge, yeh batana hai.

### **Examples**

**Example 1:**

  * **Input:** `s = "aab"`
  * **Output:** `1`
  * **Explanation:** Ek cut karke `["aa", "b"]` bana sakte hain. Dono "aa" aur "b" palindrome hain.

**Example 2:**

  * **Input:** `s = "a"`
  * **Output:** `0`
  * **Explanation:** String pehle se hi palindrome hai, isliye 0 cuts.

-----

### **Approach 1: Naive (Recursion)**

Hum ek recursive function `solve(i)` banate hain, jo `s` ke index `i` se aakhir tak ki substring ke liye minimum cuts batata hai.

  * `solve(i)` ke andar, hum `j` ko `i` se `n-1` tak loop karte hain.
  * Har `j` ke liye hum check karte hain ki kya `s[i...j]` ek palindrome hai.
  * Agar hai, to yeh ek valid partition ho sakta hai. Hum `1 + solve(j+1)` cuts try karte hain.
  * Hum saare valid `j` se mile results ka minimum le lete hain.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Palindrome Partitioning II

class Solution {
private:
    bool isPalindrome(string& s, int start, int end) {
        while(start < end) {
            if(s[start++] != s[end--]) return false;
        }
        return true;
    }
    
    int solve(string& s, int i, vector<int>& memo) {
        // Base case: string khatam ya pehle se palindrome
        if(i == s.length()) return -1; // -1, kyunki aakhri partition ke baad cut nahi lagta
        
        if (memo[i] != -1) return memo[i];

        int min_cuts = INT_MAX;
        for (int j = i; j < s.length(); ++j) {
            if (isPalindrome(s, i, j)) {
                int cuts = 1 + solve(s, j + 1, memo);
                min_cuts = min(min_cuts, cuts);
            }
        }
        return memo[i] = min_cuts;
    }
public:
    int minCut(string s) {
        vector<int> memo(s.length(), -1);
        return solve(s, 0, memo);
    }
};

/*
Time Complexity: O(2^n * n) without memoization. With memoization, it's O(n^2 * n)
kyunki har state O(n) mein palindrome check kar rahi hai. Ye TLE de sakta hai.

Space Complexity: O(n)
Memoization array aur recursion stack ke liye.
*/
```

-----

### **Approach 2: Optimal (Dynamic Programming)**

Yeh ek 2-step DP solution hai.

1.  **Palindrome Pre-computation:** Pehle, hum ek 2D DP table `isPal[i][j]` banate hain jo `O(n^2)` mein yeh pre-calculate kar leti hai ki kaun kaun si substrings palindrome hain. Isse palindrome check `O(1)` mein ho jaata hai.
2.  **Cuts DP:** Phir hum ek 1D DP array `cuts[i]` banate hain, jahan `cuts[i]` `s` ke pehle `i` characters (`s[0...i-1]`) ke liye minimum cuts store karta hai. `cuts[i]` ko calculate karne ke liye hum pichle `j` (j \< i) ko check karte hain. Agar `s[j...i-1]` palindrome hai, to hum `cuts[i] = min(cuts[i], cuts[j] + 1)` kar sakte hain.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Palindrome Partitioning II

class Solution {
public:
    int minCut(string s) {
        int n = s.length();
        if (n <= 1) return 0;

        // Step 1: Pre-compute which substrings are palindromes
        vector<vector<bool>> isPal(n, vector<bool>(n, false));
        for (int gap = 0; gap < n; ++gap) {
            for (int i = 0, j = gap; j < n; ++i, ++j) {
                if (gap == 0) isPal[i][j] = true;
                else if (gap == 1) isPal[i][j] = (s[i] == s[j]);
                else isPal[i][j] = (s[i] == s[j]) && isPal[i + 1][j - 1];
            }
        }

        // Step 2: Calculate minimum cuts using another DP
        vector<int> cuts(n);
        for (int i = 0; i < n; ++i) {
            if (isPal[0][i]) {
                cuts[i] = 0; // Agar s[0...i] palindrome hai, 0 cuts
            } else {
                cuts[i] = i; // Max cuts
                for (int j = 0; j < i; ++j) {
                    if (isPal[j + 1][i]) { // Agar s[j+1...i] palindrome hai
                        cuts[i] = min(cuts[i], cuts[j] + 1);
                    }
                }
            }
        }
        
        return cuts[n - 1];
    }
};


/*
Time Complexity: O(n^2)
Palindrome table banane mein O(n^2) aur cuts DP table banane mein bhi O(n^2).

Space Complexity: O(n^2)
Palindrome DP table ke liye.
*/
```

-----

-----

## 13\. Longest Repeating Subsequence

### **Problem Statement (PS)**

Aapko ek string `s` di gayi hai. Aapko uski sabse lambi **repeating subsequence** ki length batani hai. Yeh ek aisi subsequence hoti hai jo string mein do baar aati hai, lekin dono baar unke corresponding characters ke **original indices alag-alag** hone chahiye.

### **Examples**

**Example 1:**

  * **Input:** `s = "AABEBCDD"`
  * **Output:** `3`
  * **Explanation:** Subsequence "ABD" repeat hoti hai. Pehli "ABD" indices (0, 2, 6) se aur doosri (1, 4, 7) se banti hai.

**Example 2:**

  * **Input:** `s = "banana"`
  * **Output:** `3`
  * **Explanation:** "ana" subsequence repeat hoti hai. Indices (1,3,5) vs (1,3,5) nahi... (1,3,5) vs (2,4,6) is not possible. (`b**ana**na`) indices `(1,3,5)` vs (`ban**ana**`) indices `(3,5,?)`.
    Let's re-verify: `s = banana`. LRS "ana". First `_ana__` indices (1,3,4). Second `__ana_` indices (2,4,5). Okay. The indices of a character in the two subsequences must be different.
    Correct explanation: Subsequence "ana" repeat hoti hai. Ek `_ana__` (indices 1, 3, 4) aur doosri `__ana` (indices 2, 4, 5).

-----

### **Approach 1: Naive (Recursion)**

Yeh problem LCS ka ek variation hai. Hum string ka LCS usi ke saath nikalte hain, bas ek extra condition ke saath: jab bhi do character match karein, unke indices same nahi hone chahiye.

`solve(i, j)` function `s[i:]` aur `s[j:]` ke beech LRS nikalega.

  * Agar `s[i] == s[j]` aur `i != j`, to `1 + solve(i+1, j+1)`.
  * Nahi to `max(solve(i+1, j), solve(i, j+1))`.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Longest Repeating Subsequence

class Solution {
public:
    int solve(string& s, int i, int j, vector<vector<int>>& memo) {
        if (i >= s.length() || j >= s.length()) {
            return 0;
        }
        if (memo[i][j] != -1) return memo[i][j];

        if (s[i] == s[j] && i != j) {
            return memo[i][j] = 1 + solve(s, i + 1, j + 1, memo);
        } else {
            return memo[i][j] = max(solve(s, i + 1, j, memo), solve(s, i, j + 1, memo));
        }
    }

    int LongestRepeatingSubsequence(string str){
        int n = str.length();
        vector<vector<int>> memo(n, vector<int>(n, -1));
        return solve(str, 0, 0, memo);
    }
};

/*
Time Complexity: O(2^n) without memoization. O(n^2) with memoization.
Is code mein memoization use kiya gaya hai.

Space Complexity: O(n^2)
Memoization table aur recursion stack ke liye.
*/
```

-----

### **Approach 2: Optimal (Dynamic Programming)**

Hum LCS wali DP table hi use karenge. Hum string `s` ka LCS usi ke copy ke saath nikalenge. `dp[i][j]` `s` ke pehle `i` characters aur `s` ke pehle `j` characters ke beech LRS ki length dega.

Transition logic mein bas ek chhota sa badlav hoga:

  * Agar `s[i-1] == s[j-1]` AUR `i != j`, to `dp[i][j] = 1 + dp[i-1][j-1]`.
  * Nahi to `dp[i][j] = max(dp[i-1][j], dp[i][j-1])`.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Longest Repeating Subsequence

class Solution {
public:
	int LongestRepeatingSubsequence(string str){
	    int n = str.length();
	    vector<vector<int>> dp(n + 1, vector<int>(n + 1, 0));
	    
	    for (int i = 1; i <= n; ++i) {
	        for (int j = 1; j <= n; ++j) {
	            // Agar characters match karte hain aur unke indices alag hain
	            if (str[i - 1] == str[j - 1] && i != j) {
	                dp[i][j] = 1 + dp[i - 1][j - 1];
	            }
	            // Nahi to LCS wala logic
	            else {
	                dp[i][j] = max(dp[i - 1][j], dp[i][j - 1]);
	            }
	        }
	    }
	    
	    return dp[n][n];
	}
};


/*
Time Complexity: O(n^2)
DP table ko bharne ka time.

Space Complexity: O(n^2)
DP table ke liye.
*/
```

-----

-----

## 1\. Non-overlapping Intervals (LeetCode 435)

### **Problem Statement (PS)**

Aapko `intervals` ka ek array diya gaya hai, jahan har interval `[start, end]` ek range represent karta hai. Aapko yeh batana hai ki **minimum kitne intervals ko remove karna padega** taaki baaki bache hue intervals aapas mein overlap na karein.

### **Examples**

**Example 1:**

  * **Input:** `intervals = [[1,2],[2,3],[3,4],[1,3]]`
  * **Output:** `1`
  * **Explanation:** `[1,3]` ko remove karne se baaki intervals non-overlapping ho jaate hain.

**Example 2:**

  * **Input:** `intervals = [[1,2],[1,2],[1,2]]`
  * **Output:** `2`
  * **Explanation:** Do `[1,2]` ko remove karna padega taaki sirf ek bache.

-----

### **Approach 1: Naive (DP based on LIS)**

Yeh problem is sawaal ke barabar hai: "maximum kitne non-overlapping intervals rakhe ja sakte hain?". Ek baar yeh mil jaaye, to hum `total_intervals - max_kept_intervals` se jawab nikal sakte hain.

Is approach mein hum intervals ko **start time** ke basis par sort karte hain aur phir Longest Increasing Subsequence (LIS) jaisa logic lagate hain. `dp[i]` store karega ki `intervals[i]` ko shamil karte hue, maximum kitne non-overlapping intervals ban sakte hain.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Non-overlapping Intervals

class Solution {
public:
    int eraseOverlapIntervals(vector<vector<int>>& intervals) {
        int n = intervals.size();
        if (n == 0) return 0;

        // Step 1: Start time ke basis par sort karo
        sort(intervals.begin(), intervals.end());

        // Step 2: LIS jaisa DP lagao
        vector<int> dp(n, 1);
        int max_non_overlap = 1;

        for (int i = 1; i < n; ++i) {
            for (int j = 0; j < i; ++j) {
                // Agar interval[j] interval[i] se pehle khatam hota hai (non-overlapping)
                if (intervals[j][1] <= intervals[i][0]) {
                    dp[i] = max(dp[i], 1 + dp[j]);
                }
            }
            max_non_overlap = max(max_non_overlap, dp[i]);
        }
        
        // Remove kiye jaane wale intervals = Total - Max jo rakh sakte hain
        return n - max_non_overlap;
    }
};

/*
Time Complexity: O(n^2)
Sorting mein O(n log n) aur DP ke do nested loops mein O(n^2).

Space Complexity: O(n)
DP array ke liye.
*/
```

-----

### **Approach 2: Optimal (Greedy Approach)**

Yeh ek classic "Activity Selection" problem hai jise greedy tareeke se solve kiya ja sakta hai. Strategy yeh hai ki hum hamesha us interval ko chunein jo sabse jaldi khatam hota hai.

1.  Saare intervals ko unke **end time** ke basis par sort karo.
2.  Pehle interval ko chuno aur uske end time ko `last_end` maan lo. Count ko 1 kar do.
3.  Ab baaki intervals par jao. Agar kisi interval ka start time `last_end` se bada ya barabar hai, to iska matlab woh overlap nahi kar raha. Use chuno, count badhao, aur `last_end` update kar do.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Non-overlapping Intervals

class Solution {
public:
    // Custom comparator, end time ke basis par sort karne ke liye
    static bool compare(const vector<int>& a, const vector<int>& b) {
        return a[1] < b[1];
    }

    int eraseOverlapIntervals(vector<vector<int>>& intervals) {
        int n = intervals.size();
        if (n == 0) return 0;

        // Step 1: End time ke basis par sort karo
        sort(intervals.begin(), intervals.end(), compare);

        int kept_count = 1;
        int last_end_time = intervals[0][1];

        // Step 2: Greedily non-overlapping intervals chuno
        for (int i = 1; i < n; ++i) {
            // Agar current interval ka start pichle ke end ke baad hai
            if (intervals[i][0] >= last_end_time) {
                kept_count++;
                last_end_time = intervals[i][1];
            }
        }
        
        return n - kept_count;
    }
};

/*
Time Complexity: O(n log n)
Complexity sorting ke kaaran hai.

Space Complexity: O(1) or O(log n)
Sorting ke liye.
*/
```

-----

-----

## 2\. Minimum Number of Arrows to Burst Balloons (LeetCode 452)

### **Problem Statement (PS)**

Aapko 2D space mein kuch balloons diye gaye hain. Har balloon ek horizontal line segment `[x_start, x_end]` se represent hota hai. Aap vertical arrows `x` coordinate par fire kar सकते हैं. Ek arrow us balloon ko phod dega jiska `x_start <= x <= x_end` ho. Aapko **minimum kitne arrows** fire karne honge taaki saare balloons phoot jayein.

### **Examples**

**Example 1:**

  * **Input:** `points = [[10,16],[2,8],[1,6],[7,12]]`
  * **Output:** `2`
  * **Explanation:** Ek arrow x=6 par fire karke `[2,8]` aur `[1,6]` ko phoda ja sakta hai. Dusra arrow x=11 par `[10,16]` aur `[7,12]` ko phod dega.

**Example 2:**

  * **Input:** `points = [[1,2],[3,4],[5,6],[7,8]]`
  * **Output:** `4`
  * **Explanation:** Saare balloons alag-alag hain, isliye har ek ke liye ek arrow lagega.

-----

### **Approach 1: Greedy (Sort by Start Point)**

Ek aam greedy approach yeh ho sakti hai ki hum balloons ko unke **start point** ke hisaab se sort karein. Phir, hum overlapping balloons ke groups ko merge karne ki koshish karein. Pehle balloon ko lein, aur dekhein ki agle balloons uske saath overlap karte hain ya nahi. Jab tak overlap milta hai, unka common overlapping region nikalte jao. Jaise hi agla balloon overlap nahi karta, hume ek naya arrow chahiye.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Minimum Number of Arrows to Burst Balloons

class Solution {
public:
    int findMinArrowShots(vector<vector<int>>& points) {
        if (points.empty()) return 0;

        // Step 1: Start point ke basis par sort karo
        sort(points.begin(), points.end());

        int arrows = 1;
        // Current arrow ka effective range
        int current_end = points[0][1];

        for (size_t i = 1; i < points.size(); ++i) {
            // Agar agla balloon current arrow ke range mein hai
            if (points[i][0] <= current_end) {
                // Overlapping region ko chhota karo
                current_end = min(current_end, points[i][1]);
            } else {
                // Naya arrow chahiye
                arrows++;
                current_end = points[i][1];
            }
        }
        
        return arrows;
    }
};


/*
Time Complexity: O(n log n)
Sorting ke kaaran.

Space Complexity: O(1) or O(log n)
Sorting ke liye.
*/
```

-----

### **Approach 2: Optimal (Greedy, Sort by End Point)**

Yeh sabse saaf aur aasan greedy strategy hai. Iska idea yeh hai ki agar hume ek arrow fire karna hi hai, to use aisi jagah fire karein jo zyada se zyada aage ke balloons ko phod sake. Aisa karne ke liye, hum arrow ko overlapping group ke sabse pehle **end point** par fire karte hain.

1.  Saare balloons ko unke **end point** ke basis par sort karo.
2.  Ek arrow lo (`arrows = 1`) aur use pehle balloon ke end point par fire karo (`arrow_pos = points[0][1]`).
3.  Ab baaki balloons par jao. Agar kisi balloon ka start point `arrow_pos` se aage hai, iska matlab woh pichle arrow se nahi phoota. Hume ek naya arrow chahiye. `arrows` badhao aur `arrow_pos` ko is naye balloon ke end point par set kar do.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Minimum Number of Arrows to Burst Balloons

class Solution {
public:
    // Custom comparator (optional, default pair sort bhi chalega start par)
    static bool compare(const vector<int>& a, const vector<int>& b) {
        return a[1] < b[1];
    }
    
    int findMinArrowShots(vector<vector<int>>& points) {
        if (points.empty()) return 0;
        
        // Step 1: End point ke basis par sort karo
        sort(points.begin(), points.end(), compare);
        
        int arrows = 1;
        int arrow_pos = points[0][1];
        
        // Step 2: Greedily arrows count karo
        for (size_t i = 1; i < points.size(); ++i) {
            // Agar current balloon pichle arrow se nahi phoota
            if (points[i][0] > arrow_pos) {
                arrows++;
                arrow_pos = points[i][1];
            }
        }
        
        return arrows;
    }
};

/*
Time Complexity: O(n log n)
Sorting ke kaaran.

Space Complexity: O(1) or O(log n)
Sorting ke liye.
*/
```

-----

-----

## 3\. Maximum Profit in Job Scheduling (LeetCode 1235)

### **Problem Statement (PS)**

Aapko `n` jobs di gayi hain, jahan har job ka ek `startTime`, `endTime`, aur `profit` hai. Aapko jobs ka ek aisa subset chunna hai jisse aapko **maximum profit** mile, is shart par ki chune gaye subset mein koi bhi do jobs time mein overlap na karein.

### **Examples**

**Example 1:**

  * **Input:** `startTime = [1,2,3,3]`, `endTime = [3,4,5,6]`, `profit = [50,10,40,70]`
  * **Output:** `120`
  * **Explanation:** Jobs 1 (time 1-3, profit 50) aur 4 (time 3-6, profit 70) chuno. Total profit = 50 + 70 = 120.

**Example 2:**

  * **Input:** `startTime = [1,2,3,4,6]`, `endTime = [3,5,10,6,9]`, `profit = [20,20,100,70,60]`
  * **Output:** `150`
  * **Explanation:** Jobs 1 (1-3, 20), 4 (4-6, 70), 5 (6-9, 60) chuno. Total = 150. Wait, 1-3 (20) and 3-10 (100) -\> 120. Better is Jobs 1, 4, 5. Or Jobs 2 (2-5, 20), 5 (6-9, 60). Best is Job 3 (3-10, 100), plus Job 1 (1-3, 20). Total 120. A better choice is Job 2 (2-5, 20), and Job 5 (6-9, 60), total is 80. Or Job 1 (1-3, 20) and Job 4 (4-6, 70) and Job 5(6-9, 60). No... job 4 and 5 overlap. Let's recheck.
    `[1,3,20], [2,5,20], [3,10,100], [4,6,70], [6,9,60]`.
    If we take job [3,10,100], we can take job [1,3,20]. Profit=120.
    If we take job [4,6,70], we can take job [1,3,20]. Profit=90. Then we can take job [6,9,60]. Profit=90+60=150.
    So, Jobs with index 0, 3, 4 (using original indexing): startTime[0], startTime[3], startTime[4]. Profit = 20+70+60 = 150. This is the correct explanation.

-----

### **Approach 1: Naive (Recursion)**

Yeh ek "Weighted Interval Scheduling" problem hai. Hum sabse pehle jobs ko unke **start time** ke basis par sort karte hain. Phir, hum ek recursive function `solve(index)` banate hain jo `index` se aage ki jobs se max profit batata hai.
Har `job[index]` ke liye do options hain:

1.  **Job ko na karein:** Profit hoga `solve(index + 1)`.
2.  **Job ko karein:** Profit hoga `job[index].profit + solve(next_job)`, jahan `next_job` pehli aisi job hai jo `job[index]` ke khatam hone ke baad shuru hoti hai.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Maximum Profit in Job Scheduling

struct Job {
    int start, end, profit;
};

class Solution {
private:
    int solve(int index, vector<Job>& jobs) {
        if (index >= jobs.size()) {
            return 0;
        }

        // Option 1: Current job ko na karein
        int not_take = solve(index + 1, jobs);

        // Option 2: Current job ko karein
        // Agli non-overlapping job dhundho
        int next_job_index = jobs.size();
        for (int j = index + 1; j < jobs.size(); ++j) {
            if (jobs[j].start >= jobs[index].end) {
                next_job_index = j;
                break;
            }
        }
        int take = jobs[index].profit + solve(next_job_index, jobs);

        return max(take, not_take);
    }
public:
    int jobScheduling(vector<int>& startTime, vector<int>& endTime, vector<int>& profit) {
        int n = startTime.size();
        vector<Job> jobs(n);
        for(int i=0; i<n; ++i) {
            jobs[i] = {startTime[i], endTime[i], profit[i]};
        }

        sort(jobs.begin(), jobs.end(), [](const Job& a, const Job& b){
            return a.start < b.start;
        });

        return solve(0, jobs);
    }
};

/*
Time Complexity: O(2^n)
Exponential complexity ke kaaran TLE dega.

Space Complexity: O(n)
Recursion stack ke liye.
*/
```

-----

### **Approach 2: Optimal (DP with Binary Search)**

Hum upar wali recursive approach ko DP (memoization) se optimize karenge. `dp[i]` store karega ki `job[i]` se shuru karke max kitna profit ho sakta hai.
`next_job` ko har baar `O(n)` mein dhundhne ke bajaye, hum **binary search** (`lower_bound`) ka use karenge, kyunki jobs start time par sorted hain. Isse `next_job` `O(log n)` mein mil jaayegi.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Maximum Profit in Job Scheduling

struct Job {
    int start, end, profit;
};

class Solution {
private:
    vector<int> memo;
    // start_times vector for binary search
    vector<int> start_times;
    
    int solve(int index, vector<Job>& jobs) {
        if (index >= jobs.size()) {
            return 0;
        }
        if(memo[index] != -1) return memo[index];

        // Option 1: Current job ko na karein
        int not_take = solve(index + 1, jobs);

        // Option 2: Current job ko karein
        // Agli non-overlapping job binary search se dhundho
        auto it = lower_bound(start_times.begin() + index, start_times.end(), jobs[index].end);
        int next_job_index = distance(start_times.begin(), it);
        
        int take = jobs[index].profit + solve(next_job_index, jobs);

        return memo[index] = max(take, not_take);
    }
public:
    int jobScheduling(vector<int>& startTime, vector<int>& endTime, vector<int>& profit) {
        int n = startTime.size();
        vector<Job> jobs(n);
        for(int i=0; i<n; ++i) {
            jobs[i] = {startTime[i], endTime[i], profit[i]};
        }

        sort(jobs.begin(), jobs.end(), [](const Job& a, const Job& b){
            return a.start < b.start;
        });
        
        // Binary search ke liye alag se start times nikal lo
        for(int i=0; i<n; ++i) {
            start_times.push_back(jobs[i].start);
        }
        
        memo.resize(n, -1);
        return solve(0, jobs);
    }
};

/*
Time Complexity: O(n log n)
Sorting mein O(n log n). DP ke n states hain, aur har state O(log n) leti hai binary search ke liye.

Space Complexity: O(n)
DP memoization array aur recursion stack ke liye.
*/
```

-----

-----

## 4\. Meeting Rooms (LeetCode 252)

### **Problem Statement (PS)**

Aapko meetings ke time `intervals` ka ek array diya gaya hai, jahan `intervals[i] = [start, end]`. Aapko yeh batana hai ki kya ek व्यक्ति saari meetings attend kar sakta hai (yaani, koi bhi do meetings overlap nahi karti).

### **Examples**

**Example 1:**

  * **Input:** `intervals = [[0,30],[5,10],[15,20]]`
  * **Output:** `false`
  * **Explanation:** `[0,30]` meeting `[5,10]` aur `[15,20]` dono ke saath overlap karti hai.

**Example 2:**

  * **Input:** `intervals = [[7,10],[2,4]]`
  * **Output:** `true`
  * **Explanation:** Yeh dono meetings alag-alag time par hain.

-----

### **Approach 1: Naive (Brute Force)**

Sabse seedha tareeka hai ki hum har possible pair of meetings ko check karein. Agar koi bhi ek pair aapas mein overlap karta hai, to hum `false` return kar denge. Agar saare pairs check karne ke baad koi overlap nahi milta, to `true` return karenge.

Do intervals `[s1, e1]` aur `[s2, e2]` overlap karte hain agar `s1 < e2` aur `s2 < e1` ho.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Meeting Rooms

class Solution {
public:
    bool canAttendMeetings(vector<vector<int>>& intervals) {
        int n = intervals.size();
        for (int i = 0; i < n; ++i) {
            for (int j = i + 1; j < n; ++j) {
                // Check for overlap
                // s1 < e2 and s2 < e1
                if (intervals[i][0] < intervals[j][1] && intervals[j][0] < intervals[i][1]) {
                    return false;
                }
            }
        }
        return true;
    }
};

/*
Time Complexity: O(n^2)
Do nested loops saare pairs ko check karte hain.

Space Complexity: O(1)
Koi extra space use nahi hua.
*/
```

-----

### **Approach 2: Optimal (Sorting)**

Ek zyada efficient tareeka sorting ka use karta hai. Agar hum saari meetings ko unke **start time** ke anusaar sort kar dein, to humein bas aaju-baaju (adjacent) wali meetings ko check karna hoga.

1.  Intervals ko start time ke basis par sort karo.
2.  Ab sorted list par jao. Agar kisi bhi meeting ka `start time` usse pichli meeting ke `end time` se kam hai, to iska matlab overlap hai. `false` return karo.
3.  Agar poora loop bina overlap ke khatam ho jaata hai, to `true` return karo.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Meeting Rooms

class Solution {
public:
    bool canAttendMeetings(vector<vector<int>>& intervals) {
        if (intervals.empty()) {
            return true;
        }

        // Step 1: Start time ke basis par sort karo
        sort(intervals.begin(), intervals.end());

        // Step 2: Overlap check karo
        for (size_t i = 1; i < intervals.size(); ++i) {
            // Agar current meeting ka start pichli ke end se pehle hai
            if (intervals[i][0] < intervals[i - 1][1]) {
                return false;
            }
        }
        
        return true;
    }
};

/*
Time Complexity: O(n log n)
Complexity sorting ke kaaran hai.

Space Complexity: O(1) or O(log n)
Sorting ke liye.
*/
```

-----

-----

## 5\. Meeting Rooms II (LeetCode 253)

### **Problem Statement (PS)**

Aapko meetings ke time `intervals` ka ek array diya gaya hai. Aapko yeh batana hai ki saari meetings ko accommodate karne ke liye **minimum kitne conference rooms** ki zaroorat padegi.

### **Examples**

**Example 1:**

  * **Input:** `intervals = [[0,30],[5,10],[15,20]]`
  * **Output:** `2`
  * **Explanation:** `[5,10]` aur `[15,20]` ek room mein ho sakti hain, lekin `[0,30]` ke liye doosra room lagega.

**Example 2:**

  * **Input:** `intervals = [[7,10],[2,4]]`
  * **Output:** `1`
  * **Explanation:** Dono meetings ek hi room mein alag-alag time par ho sakti hain.

-----

### **Approach 1: Using Priority Queue (Min-Heap)**

Is problem ka matlab hai ki kisi bhi ek time par maximum kitni meetings ek saath chal rahi hain.

1.  Saari meetings ko unke **start time** ke anusaar sort karo.
2.  Ek **min-priority queue** (min-heap) ka use karo jo rooms ke "free hone ka time" (yaani, meeting ka end time) store karega.
3.  Ab har meeting ke liye:
      * Agar priority queue khali nahi hai aur current meeting ka start time queue ke top (sabse jaldi free hone wale room) ke end time se bada ya barabar hai, to iska matlab woh room ab free hai. Usko queue se `pop` kar do.
      * Current meeting ko ek room do, yaani uska end time queue mein `push` kar do.
4.  Poore process mein priority queue ka jo maximum size hoga, wahi humara jawab hai.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Meeting Rooms II

class Solution {
public:
    int minMeetingRooms(vector<vector<int>>& intervals) {
        if (intervals.empty()) return 0;

        // Step 1: Start time ke basis par sort karo
        sort(intervals.begin(), intervals.end());

        // Min-heap jo meeting end times ko store karega
        priority_queue<int, vector<int>, greater<int>> pq;
        
        // Pehli meeting ke liye ek room
        pq.push(intervals[0][1]);
        
        for (size_t i = 1; i < intervals.size(); ++i) {
            // Agar sabse jaldi free hone wala room available hai
            if (intervals[i][0] >= pq.top()) {
                pq.pop(); // Room free ho gaya
            }
            // Current meeting ko room do
            pq.push(intervals[i][1]);
        }
        
        return pq.size();
    }
};

/*
Time Complexity: O(n log n)
Sorting O(n log n) leti hai. Har element PQ mein ek baar push aur pop hota hai, jo O(log n) leta hai. Total O(n log n).

Space Complexity: O(n)
Worst case mein, saari meetings overlap karengi aur PQ ka size n ho jaayega.
*/
```

-----

### **Approach 2: Optimal (Two Pointers/Chronological Ordering)**

Yeh approach thodi alag hai par utni hi efficient hai. Ismein hum meetings ko events ki tarah treat karte hain: ek "start" event aur ek "end" event.

1.  Saare `start times` aur `end times` ko do alag-alag arrays mein daalo.
2.  Dono arrays ko sort karo.
3.  Do pointers ka use karo: `s_ptr` start times ke liye aur `e_ptr` end times ke liye.
4.  Ab `start_times` array par `s_ptr` se iterate karo.
      * Agar `start_times[s_ptr]` `end_times[e_ptr]` se kam hai, to iska matlab ek nayi meeting shuru ho gayi isse pehle ki koi purani khatam ho. Hume ek aur room chahiye. `rooms++`.
      * Agar `start_times[s_ptr]` `end_times[e_ptr]` se bada ya barabar hai, to iska matlab ek meeting khatam ho chuki hai. Ek room free ho gaya. `e_ptr++`. (Room count `rooms` kam nahi karte, hum bas max count track karte hain).
5.  Maximum `rooms` ki value humara jawab hai.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Meeting Rooms II

class Solution {
public:
    int minMeetingRooms(vector<vector<int>>& intervals) {
        int n = intervals.size();
        if (n == 0) return 0;

        vector<int> start_times(n);
        vector<int> end_times(n);
        for(int i=0; i<n; ++i) {
            start_times[i] = intervals[i][0];
            end_times[i] = intervals[i][1];
        }

        // Step 1: Dono arrays ko sort karo
        sort(start_times.begin(), start_times.end());
        sort(end_times.begin(), end_times.end());

        int rooms = 0;
        int max_rooms = 0;
        int s_ptr = 0, e_ptr = 0;

        // Step 2: Two pointers se events process karo
        while (s_ptr < n) {
            // Agar ek meeting shuru ho rahi hai isse pehle ki koi khatam ho
            if (start_times[s_ptr] < end_times[e_ptr]) {
                rooms++; // Ek aur room chahiye
                s_ptr++;
            } else {
                // Ek meeting khatam ho gayi, room free hua
                // Isliye naya room nahi chahiye, hum purana use kar sakte hain
                s_ptr++;
                e_ptr++;
            }
            max_rooms = max(max_rooms, rooms);
        }

        return max_rooms;
    }
};


/*
Time Complexity: O(n log n)
Dono arrays ko sort karne mein O(n log n) lagta hai. Two pointer traversal O(n) hai.

Space Complexity: O(n)
Start aur End times ke liye do extra arrays ke liye.
*/
```




-----

-----

## 6\. Car Pooling (LeetCode 1094)

### **Problem Statement (PS)**

Aapko ek car di gayi hai jiski ek `capacity` (shamta) hai. Aapko `trips` ka ek array diya gaya hai, jahan har trip `[numPassengers, from, to]` yeh batata hai ki kitne passengers ko location `from` se `to` tak le jaana hai. Aapko batana hai ki kya car saare passengers ko unki respective trips ke liye pick up aur drop off kar sakti hai, bina kisi bhi samay car ki `capacity` se zyada hue.

### **Examples**

**Example 1:**

  * **Input:** `trips = [[2,1,5],[3,3,7]]`, `capacity = 4`
  * **Output:** `false`
  * **Explanation:** Location 3 se 5 ke beech, car mein 2+3=5 passengers honge, jo capacity 4 se zyada hai.

**Example 2:**

  * **Input:** `trips = [[2,1,5],[3,3,7]]`, `capacity = 5`
  * **Output:** `true`
  * **Explanation:** Maximum 5 passengers location 3 se 5 ke beech honge, jo capacity ke barabar hai, isliye yeh possible hai.

-----

### **Approach 1: Naive (Simulation)**

Is approach mein hum poori journey ko simulate karte hain. Kyunki locations 0 se 1000 tak hain, hum 1001 size ka ek array bana sakte hain jo har location par passengers ka count rakhega. Har trip ke liye, hum uske `from` se `to` tak ke har location par passenger count badha denge. Aakhir mein check karenge ki kisi bhi location par count `capacity` se zyada to nahi hua.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Car Pooling

class Solution {
public:
    bool carPooling(vector<vector<int>>& trips, int capacity) {
        // Maan lete hain ki locations 0 se 1000 tak hain
        vector<int> passengers_at_location(1001, 0);

        for (const auto& trip : trips) {
            int num_passengers = trip[0];
            int from = trip[1];
            int to = trip[2];
            
            // Har location par passenger count badhao
            for (int i = from; i < to; ++i) {
                passengers_at_location[i] += num_passengers;
                // Saath-saath check karlo
                if (passengers_at_location[i] > capacity) {
                    return false;
                }
            }
        }
        
        return true;
    }
};


/*
Time Complexity: O(N * M)
Jahan N trips ka number hai aur M locations ki range hai (yahan 1000).
Har trip ke liye hum uski range mein loop kar rahe hain.

Space Complexity: O(M)
Location ka count store karne wale array ke liye.
*/
```

-----

### **Approach 2: Optimal (Difference Array / Sweep-line)**

Har location par count badhane ke bajaye, yeh approach zyada efficient hai. Hum sirf "events" (passenger pick-up aur drop-off) ko record karte hain. Hum ek array `location_changes` banate hain.

  * Jab `num` passengers `from` par car mein aate hain, hum `location_changes[from] += num` karte hain.
  * Jab woh `to` par utarte hain, hum `location_changes[to] -= num` karte hain.

Iske baad, hum is `location_changes` array par ek baar shuru se aakhir tak jaate hain, current passenger count ka hisaab rakhte hue. Agar yeh count kabhi bhi `capacity` se zyada hota hai, to jawab `false` hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Car Pooling

class Solution {
public:
    bool carPooling(vector<vector<int>>& trips, int capacity) {
        // Maan lete hain ki max location 1000 hai
        vector<int> location_changes(1001, 0);

        for (const auto& trip : trips) {
            int num_passengers = trip[0];
            int from = trip[1];
            int to = trip[2];
            
            location_changes[from] += num_passengers; // Passengers car mein aaye
            location_changes[to] -= num_passengers;   // Passengers utar gaye
        }

        int current_passengers = 0;
        for (int i = 0; i <= 1000; ++i) {
            current_passengers += location_changes[i];
            if (current_passengers > capacity) {
                return false;
            }
        }
        
        return true;
    }
};


/*
Time Complexity: O(N + M)
Jahan N trips ka number hai aur M locations ki range hai. Hum trips par ek baar
aur locations par ek baar iterate karte hain.

Space Complexity: O(M)
Location changes wale array ke liye.
*/
```

-----

-----

## 7\. My Calendar I (LeetCode 729)

### **Problem Statement (PS)**

Aapko ek `MyCalendar` class banani hai jiska ek `book(start, end)` method ho. Yeh method ek naye event ko calendar mein book karne ki koshish karta hai. Agar naya event kisi pehle se book kiye gaye event ke saath **overlap** nahi karta, to method `true` return karta hai aur event book ho jaata hai. Agar overlap karta hai, to method `false` return karta hai aur event book nahi hota.

### **Examples**

**Example 1:**

  * `MyCalendar.book(10, 20)` -\> `true` (Booked)
  * `MyCalendar.book(15, 25)` -\> `false` (Overlap with [10, 20])
  * `MyCalendar.book(20, 30)` -\> `true` (Booked, 20 par touch karna overlap nahi hai)

-----

### **Approach 1: Naive (List/Vector)**

Sabse aasan tareeka hai ki hum saare booked events ko ek simple list ya vector mein store kar lein. Jab bhi koi naya `book` request aata hai, hum is list ke har event ke saath check karte hain ki naya event overlap kar raha hai ya nahi.

Do intervals `[s1, e1)` aur `[s2, e2)` overlap karte hain agar `s1 < e2` aur `s2 < e1` ho.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: My Calendar I

class MyCalendar {
private:
    vector<pair<int, int>> bookings;

public:
    MyCalendar() {}
    
    bool book(int start, int end) {
        for (const auto& b : bookings) {
            // Overlap condition: max(start1, start2) < min(end1, end2)
            if (max(start, b.first) < min(end, b.second)) {
                return false;
            }
        }
        
        // Agar koi overlap nahi, to book karo
        bookings.push_back({start, end});
        return true;
    }
};

/*
Time Complexity: O(N) per book call
Jahan N ab tak ke bookings ka number hai. Har call ke liye poori list check karni padti hai.
Total N calls ke liye O(N^2).

Space Complexity: O(N)
Saare bookings ko store karne ke liye.
*/
```

-----

### **Approach 2: Optimal (Balanced BST / `std::map`)**

Har baar poori list check karne se behtar hai ki hum intervals ko sorted rakhein. Iske liye `std::map` (jo C++ mein ek balanced binary search tree hai) ek accha data structure hai. Hum map mein `start` time ko key aur `end` time ko value bana sakte hain.

Jab naya event `[start, end)` aata hai, hum map mein `lower_bound(start)` se check karte hain. Hume bas uske aaju-baaju ke intervals se overlap check karna hota hai, poori list se nahi.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: My Calendar I

class MyCalendar {
private:
    map<int, int> bookings; // key: start, value: end

public:
    MyCalendar() {}
    
    bool book(int start, int end) {
        // Pehla event dhundho jiska start time humare start time se bada ya barabar hai
        auto next_it = bookings.lower_bound(start);

        // Check karo ki agla event humare naye event ke saath overlap to nahi kar raha
        // next_it->first < end
        if (next_it != bookings.end() && next_it->first < end) {
            return false;
        }
        
        // Check karo ki pichla event humare naye event ke saath overlap to nahi kar raha
        // start < prev_it->second
        if (next_it != bookings.begin()) {
            auto prev_it = prev(next_it);
            if (start < prev_it->second) {
                return false;
            }
        }
        
        // Agar koi overlap nahi
        bookings[start] = end;
        return true;
    }
};

/*
Time Complexity: O(log N) per book call
Map mein search aur insert operations O(log N) lete hain.

Space Complexity: O(N)
Saare bookings ko store karne ke liye.
*/
```

-----

-----

## 8\. My Calendar II (LeetCode 731)

### **Problem Statement (PS)**

Aapko ek `MyCalendarTwo` class banani hai. Iska `book(start, end)` method `true` return karega aur event ko book karega agar naya event add karne se koi **triple-booking** (teen events ek hi time par overlap) na ho. **Double-booking** allowed hai. Agar triple-booking ho rahi hai, to `false` return karega.

### **Examples**

  * `MyCalendarTwo.book(10, 20)` -\> `true` (1 booking)
  * `MyCalendarTwo.book(50, 60)` -\> `true` (1 booking)
  * `MyCalendarTwo.book(10, 40)` -\> `true` (Overlap: [10, 20] double booked hai)
  * `MyCalendarTwo.book(5, 15)` -\> `false` (Overlap: [10, 15] triple booked ho jaayega)

-----

### **Approach 1: Naive (Two Lists)**

Hum do lists maintain kar sakte hain:

1.  `bookings`: Saare single events ko store karegi.
2.  `overlaps`: Saare double-booked (overlapping) time intervals ko store karegi.

Jab naya event aata hai:

1.  Pehle check karo ki kya yeh `overlaps` list ke kisi interval se overlap kar raha hai. Agar haan, to yeh triple-booking banayega -\> `false` return karo.
2.  Agar nahi, to ab `bookings` list ke har event se iska overlap check karo. Jitne bhi overlaps milein, unhe `overlaps` list mein daal do.
3.  Aakhir mein, naye event ko `bookings` list mein daal do aur `true` return karo.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: My Calendar II

class MyCalendarTwo {
private:
    vector<pair<int, int>> bookings;
    vector<pair<int, int>> overlaps; // Double bookings

public:
    MyCalendarTwo() {}
    
    bool book(int start, int end) {
        // Check for triple booking
        for (const auto& o : overlaps) {
            if (max(start, o.first) < min(end, o.second)) {
                return false;
            }
        }
        
        // Naye overlaps dhoondho aur add karo
        for (const auto& b : bookings) {
            int overlap_start = max(start, b.first);
            int overlap_end = min(end, b.second);
            if (overlap_start < overlap_end) {
                overlaps.push_back({overlap_start, overlap_end});
            }
        }
        
        bookings.push_back({start, end});
        return true;
    }
};


/*
Time Complexity: O(N^2) per book call
Kyunki hum dono lists par iterate kar sakte hain, aur overlaps list bhi badh sakti hai.

Space Complexity: O(N^2)
Worst case mein, overlaps list ka size N^2 tak ja sakta hai.
*/
```

-----

### **Approach 2: Optimal (Difference Map / Sweep-line)**

Yeh approach timeline par "events" (start aur end times) ko track karti hai. Hum ek `map` ka use karte hain jahan key `time` hai aur value `+1` (event start) ya `-1` (event end) hai.

  * Jab `book(start, end)` call hota hai, hum `timeline[start]++` aur `timeline[end]--` karte hain.
  * Ab hum timeline par shuru se aakhir tak jaate hain aur dekhte hain ki kisi bhi point par active events ka count 3 ya usse zyada to nahi ho raha.
  * Agar count 3 ho jaata hai, to booking invalid hai. Hum map mein kiye gaye changes ko **revert** karte hain aur `false` return karte hain.
  * Agar poori timeline check karne par count 3 nahi hota, to booking valid hai, aur hum `true` return karte hain.

<!-- end list -->

```cpp
#include <bits/stdc++.h;
using namespace std;

// Problem: My Calendar II

class MyCalendarTwo {
private:
    map<int, int> timeline;

public:
    MyCalendarTwo() {}
    
    bool book(int start, int end) {
        timeline[start]++; // Ek event shuru hua
        timeline[end]--;   // Ek event khatam hua

        int active_events = 0;
        for (auto const& [time, count_change] : timeline) {
            active_events += count_change;
            if (active_events >= 3) {
                // Triple booking! Revert changes.
                timeline[start]--;
                timeline[end]++;
                return false;
            }
        }
        
        return true;
    }
};


/*
Time Complexity: O(N) per book call
Jahan N ab tak ke distinct start/end points ka number hai. Har call mein hum poora map
traverse karte hain.

Space Complexity: O(N)
Map mein N points store karne ke liye.
*/
```

-----

-----

## 9\. My Calendar III (LeetCode 732)

### **Problem Statement (PS)**

Aapko ek `MyCalendarThree` class banani hai. Iska `book(start, end)` method hamesha event ko calendar mein add karega. Method ko hamesha **maximum number of simultaneous events (k-booking)** return karna hai jo ab tak calendar mein hue hain. Matlab, kisi bhi ek point in time par, maximum kitne events aapas mein overlap kar rahe hain.

### **Examples**

  * `MyCalendarThree.book(10, 20)` -\> returns `1`
  * `MyCalendarThree.book(50, 60)` -\> returns `1`
  * `MyCalendarThree.book(10, 40)` -\> returns `2` (ab [10, 20] aur [10, 40] overlap kar rahe hain)
  * `MyCalendarThree.book(5, 15)` -\> returns `3` (ab [5,15], [10,20], [10,40] ka overlap [10,15] mein hai)

-----

### **Approach 1: Naive (Brute-force checking points)**

Har `book` call ke baad, hum saare unique start aur end points ko collect kar sakte hain. Phir, in sorted points ke beech ke har segment ke liye, hum count kar sakte hain ki us segment mein kitne total events active hain. Isse humein max overlap (k-booking) mil jaayega. Yeh approach har call mein kaafi redundant kaam karti hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: My Calendar III

class MyCalendarThree {
private:
    vector<pair<int, int>> bookings;
public:
    MyCalendarThree() {}
    
    int book(int start, int end) {
        bookings.push_back({start, end});
        
        set<int> points;
        for(const auto& b : bookings) {
            points.insert(b.first);
            points.insert(b.second);
        }
        
        int max_k = 0;
        
        // Har do consecutive points ke beech ka mid-point check karo
        auto it = points.begin();
        if (it != points.end()) {
             auto next_it = std::next(it);
             while(next_it != points.end()) {
                 int mid_point = *it;
                 int current_overlap = 0;
                 for(const auto& b : bookings) {
                     if(b.first <= mid_point && mid_point < b.second) {
                         current_overlap++;
                     }
                 }
                 max_k = max(max_k, current_overlap);
                 it = next_it;
                 next_it = std::next(it);
             }
        }
        
        // Agar sirf ek booking hai
        if (max_k == 0 && !bookings.empty()) return 1;

        return max_k;
    }
};

/*
Time Complexity: O(N^2 * log N) per book call
N unique points ho sakte hain, N^2 pairs. Har call mein points ko set mein daalna O(N log N)
aur phir N points ke liye N bookings check karna O(N^2).

Space Complexity: O(N)
Bookings aur points store karne ke liye.
*/
```

-----

### **Approach 2: Optimal (Difference Map / Sweep-line)**

Yeh 'My Calendar II' jaisa hi hai, lekin yahan humein `false` return nahi karna. Hum bas maximum active events ka count track karte hain. Hum ek sorted `map` use karte hain jo timeline par event count ke changes ko store karta hai.

  * `timeline[start]++` (ek event shuru hua)
  * `timeline[end]--` (ek event khatam hua)

Har `book` call ke baad, hum is map ko traverse karte hain, active events ka running sum nikalte hain, aur is sum ki maximum value ko update karte hain.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: My Calendar III

class MyCalendarThree {
private:
    map<int, int> timeline;
    int max_k = 0;

public:
    MyCalendarThree() {}
    
    int book(int start, int end) {
        timeline[start]++; // Ek event shuru hua
        timeline[end]--;   // Ek event khatam hua

        int active_events = 0;
        
        // Active events ka max count nikalo
        for (auto const& [time, count_change] : timeline) {
            active_events += count_change;
            max_k = max(max_k, active_events);
        }
        
        return max_k;
    }
};


/*
Time Complexity: O(N) per book call
Jahan N ab tak ke distinct start/end points ka number hai. Har call mein hum poora map
traverse karte hain. Agar N bahut bada hai, to yeh O(N log N) for each book call bhi socha ja sakta hai (N calls, har call N log N for map traversal etc.),
lekin ek call ke liye map traversal O(N) hai.

Space Complexity: O(N)
Map mein N points store karne ke liye.
*/
```



-----

-----

## 1\. Course Schedule (LeetCode 207)

### **Problem Statement (PS)**

Aapko `numCourses` (total courses) aur `prerequisites` ka ek array diya gaya hai. Har prerequisite `[a, b]` ka matlab hai ki course `a` lene ke liye pehle course `b` karna zaroori hai. Aapko yeh batana hai ki kya saare courses finish karna **possible** hai ya nahi.

### **Examples**

**Example 1:**

  * **Input:** `numCourses = 2, prerequisites = [[1,0]]`
  * **Output:** `true`
  * **Explanation:** Course 1 karne ke liye course 0 karna hai. Yeh bilkul possible hai.

**Example 2:**

  * **Input:** `numCourses = 2, prerequisites = [[1,0],[0,1]]`
  * **Output:** `false`
  * **Explanation:** Course 1 ke liye 0 zaroori hai, aur 0 ke liye 1. Yeh ek cycle hai, isliye courses poore nahi kiye ja sakte.

-----

### **Approach 1: Naive (DFS with Cycle Detection)**

Hum is problem ko ek directed graph ki tarah dekh sakte hain, jahan har course ek node hai. Agar course `a` ke liye `b` zaroori hai, to `b` se `a` ki taraf ek edge hai. Problem yeh hai ki is graph mein koi **cycle** hai ya nahi.

Hum har node se Depth First Search (DFS) karke cycle detect kar sakte hain. Hum do 'visited' arrays rakhenge: ek `visited` (jo node process ho chuke hain) aur ek `recursionStack` (jo current DFS path mein hain). Agar hum DFS karte hue kisi aise node par pahunche jo pehle se `recursionStack` mein hai, to iska matlab cycle hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Course Schedule

class Solution {
private:
    bool hasCycle(int u, vector<vector<int>>& adj, vector<bool>& visited, vector<bool>& recursionStack) {
        visited[u] = true;
        recursionStack[u] = true;

        for (int v : adj[u]) {
            if (!visited[v]) {
                if (hasCycle(v, adj, visited, recursionStack)) {
                    return true;
                }
            } else if (recursionStack[v]) {
                // Agar node visited hai aur current path mein bhi hai, to cycle hai
                return true;
            }
        }
        
        recursionStack[u] = false; // Backtrack
        return false;
    }

public:
    bool canFinish(int numCourses, vector<vector<int>>& prerequisites) {
        vector<vector<int>> adj(numCourses);
        for (const auto& p : prerequisites) {
            adj[p[1]].push_back(p[0]); // Edge from prerequisite to course
        }
        
        vector<bool> visited(numCourses, false);
        vector<bool> recursionStack(numCourses, false);
        
        for (int i = 0; i < numCourses; ++i) {
            if (!visited[i]) {
                if (hasCycle(i, adj, visited, recursionStack)) {
                    return false;
                }
            }
        }
        
        return true;
    }
};


/*
Time Complexity: O(V + E)
Jahan V courses (vertices) aur E prerequisites (edges) hain. Hum har node aur edge ko ek baar visit karte hain.

Space Complexity: O(V + E)
Adjacency list, visited arrays, aur recursion stack ke liye.
*/
```

-----

### **Approach 2: Optimal (Topological Sort - Kahn's Algorithm)**

Yeh BFS-based approach hai, jise Kahn's Algorithm kehte hain.

1.  Sabse pehle, hum har course ka `in-degree` (uske kitne prerequisites hain) calculate karte hain.
2.  Ek queue banate hain aur usmein saare courses daal dete hain jinka `in-degree` 0 hai (yaani, unka koi prerequisite nahi hai).
3.  Jab tak queue khali na ho:
      * Ek course ko queue se nikalo.
      * Us course par dependent saare courses (uske neighbors) ka `in-degree` 1 se kam kar do.
      * Agar kisi neighbor ka `in-degree` 0 ho jaaye, to use queue mein daal do.
4.  Aakhir mein, agar humne `numCourses` ke barabar courses process kar liye, to iska matlab koi cycle nahi thi aur saare courses possible hain.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Course Schedule

class Solution {
public:
    bool canFinish(int numCourses, vector<vector<int>>& prerequisites) {
        vector<vector<int>> adj(numCourses);
        vector<int> inDegree(numCourses, 0);

        for (const auto& p : prerequisites) {
            adj[p[1]].push_back(p[0]);
            inDegree[p[0]]++;
        }
        
        queue<int> q;
        for (int i = 0; i < numCourses; ++i) {
            if (inDegree[i] == 0) {
                q.push(i);
            }
        }
        
        int courses_done = 0;
        while (!q.empty()) {
            int u = q.front();
            q.pop();
            courses_done++;
            
            for (int v : adj[u]) {
                inDegree[v]--;
                if (inDegree[v] == 0) {
                    q.push(v);
                }
            }
        }
        
        return courses_done == numCourses;
    }
};

/*
Time Complexity: O(V + E)
Graph banane aur BFS traversal ka time.

Space Complexity: O(V + E)
Adjacency list, in-degree array, aur queue ke liye.
*/
```

-----

-----

## 2\. Course Schedule II (LeetCode 210)

### **Problem Statement (PS)**

Yeh problem 'Course Schedule I' jaisi hi hai. Par is baar, agar saare courses karna possible hai, to aapko unka ek **valid order** return karna hai. Agar possible nahi hai (cycle hai), to ek **empty array** return karna hai.

### **Examples**

**Example 1:**

  * **Input:** `numCourses = 4, prerequisites = [[1,0],[2,0],[3,1],[3,2]]`
  * **Output:** `[0,1,2,3]` or `[0,2,1,3]`
  * **Explanation:** Pehle 0, phir 1 aur 2 (kisi bhi order mein), aur aakhir mein 3. Yeh ek valid course order hai.

**Example 2:**

  * **Input:** `numCourses = 2, prerequisites = [[1,0],[0,1]]`
  * **Output:** `[]`
  * **Explanation:** Cycle hai, isliye koi valid order possible nahi hai.

-----

### **Approach 1: Naive (DFS-based Topological Sort)**

Yeh approach topological sort karne ke liye DFS ka use karti hai.

1.  Har unvisited node par DFS call karo.
2.  DFS function mein, pehle node ke saare neighbors par recursively visit karo.
3.  Jab saare neighbors process ho jaayein, tab current node ko ek stack mein `push` kar do.
4.  Cycle detection ke liye pichle problem jaisa `recursionStack` bhi use karna hoga. Agar cycle milti hai to seedha empty array return kar do.
5.  Aakhir mein, stack se elements ko pop karke result array mein daalo.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Course Schedule II

class Solution {
private:
    bool hasCycle(int u, vector<vector<int>>& adj, vector<int>& visited, stack<int>& st) {
        visited[u] = 1; // Mark as visiting

        for (int v : adj[u]) {
            if (visited[v] == 1) return true; // Cycle detected
            if (visited[v] == 0) {
                if (hasCycle(v, adj, visited, st)) return true;
            }
        }
        
        visited[u] = 2; // Mark as visited
        st.push(u);
        return false;
    }

public:
    vector<int> findOrder(int numCourses, vector<vector<int>>& prerequisites) {
        vector<vector<int>> adj(numCourses);
        for (const auto& p : prerequisites) {
            adj[p[1]].push_back(p[0]);
        }
        
        stack<int> st;
        vector<int> visited(numCourses, 0); // 0: unvisited, 1: visiting, 2: visited
        
        for (int i = 0; i < numCourses; ++i) {
            if (visited[i] == 0) {
                if (hasCycle(i, adj, visited, st)) {
                    return {}; // Cycle hai, to empty array
                }
            }
        }
        
        vector<int> order;
        while (!st.empty()) {
            order.push_back(st.top());
            st.pop();
        }
        return order;
    }
};

/*
Time Complexity: O(V + E)
DFS traversal ka time.

Space Complexity: O(V + E)
Adjacency list, visited array, aur stack ke liye.
*/
```

-----

### **Approach 2: Optimal (Kahn's Algorithm BFS)**

Yeh approach 'Course Schedule I' ke BFS approach ka extension hai. Wahan hum sirf count kar rahe the, yahan hum course order ko ek result array mein store karenge.

  * Jab bhi hum kisi course ko queue se `pop` karte hain, use hum `result` array mein daal dete hain.
  * Aakhir mein, agar `result` array ka size `numCourses` ke barabar hai, to hum `result` return karte hain.
  * Agar nahi, to iska matlab graph mein cycle thi, aur hum ek empty array return karte hain.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Course Schedule II

class Solution {
public:
    vector<int> findOrder(int numCourses, vector<vector<int>>& prerequisites) {
        vector<vector<int>> adj(numCourses);
        vector<int> inDegree(numCourses, 0);

        for (const auto& p : prerequisites) {
            adj[p[1]].push_back(p[0]);
            inDegree[p[0]]++;
        }
        
        queue<int> q;
        for (int i = 0; i < numCourses; ++i) {
            if (inDegree[i] == 0) {
                q.push(i);
            }
        }
        
        vector<int> order;
        while (!q.empty()) {
            int u = q.front();
            q.pop();
            order.push_back(u);
            
            for (int v : adj[u]) {
                inDegree[v]--;
                if (inDegree[v] == 0) {
                    q.push(v);
                }
            }
        }
        
        if (order.size() == numCourses) {
            return order;
        }
        return {}; // Cycle thi
    }
};

/*
Time Complexity: O(V + E)
Graph banane aur BFS traversal ka time.

Space Complexity: O(V + E)
Adjacency list, in-degree array, aur queue ke liye.
*/
```

-----

-----

## 3\. Course Schedule III (LeetCode 630)

### **Problem Statement (PS)**

Aapko `n` online courses diye gaye hain, jahan har course `[duration_i, lastDay_i]` se represent hota hai. Iska matlab hai ki course `i` ko `duration_i` din lagte hain aur use `lastDay_i` (inclusive) tak khatam karna zaroori hai. Aap courses ko back-to-back le sakte hain. Aapko batana hai ki aap **maximum kitne courses** kar sakte hain.

### **Examples**

**Example 1:**

  * **Input:** `courses = [[100,200],[200,1300],[1000,1250],[2000,3200]]`
  * **Output:** `3`
  * **Explanation:** Pehle 100-din ka course, phir 1000-din ka, aur phir 200-din ka course. Total time: 1300, jo 1300 ki deadline tak ho jaata hai.

**Example 2:**

  * **Input:** `courses = [[1,2],[2,3]]`
  * **Output:** `2`
  * **Explanation:** Dono courses kiye ja sakte hain.

-----

### **Approach 1: Naive (Recursion/Backtracking)**

Is approach mein hum courses ke saare possible subsets try karenge. Har subset ke liye hum check karenge ki kya uske saare courses ko deadlines ke andar poora kiya ja sakta hai. Phir hum sabse bade valid subset ka size return karenge. Yeh approach `O(2^n * n!)` ke aas paas hogi kyunki har subset ke liye order bhi matter karta hai, isliye TLE degi.

*Iska code likhna bahut complex hai aur yeh guaranteed TLE dega, isliye yahan optimal approach par focus karna behtar hai.*

-----

### **Approach 2: Optimal (Greedy with Priority Queue)**

Yeh ek greedy problem hai. Iska sabse accha solution priority queue ka use karta hai. Strategy yeh hai:

1.  Saare courses ko unki **deadline (`lastDay`)** ke basis par sort karo.
2.  Ek `max-priority queue` ka istemal karo jo ab tak liye gaye courses ki `duration` ko store karega. Ek `currentTime` variable rakho jo 0 se shuru hoga.
3.  Ab sorted courses par iterate karo:
      * Agar current course ko lene se `(currentTime + duration <= lastDay)` deadline meet ho rahi hai, to use le lo. Uski `duration` ko priority queue mein daalo aur `currentTime` update karo.
      * Agar deadline meet nahi ho rahi, to check karo ki kya priority queue mein koi aisa course hai jiski duration current course se zyada hai. Agar hai, to us lambe course ko `swap` kar do. Yaani, priority queue se max duration wala course nikalo, `currentTime` se uski duration hatao, aur naye (chote) course ki duration `currentTime` aur priority queue mein daal do. Aisa karne se hum time bachate hain.
4.  Aakhir mein, priority queue ka size hi humara jawab hoga.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Course Schedule III

class Solution {
public:
    // Custom comparator, deadline (lastDay) ke basis par sort karne ke liye
    static bool compare(const vector<int>& a, const vector<int>& b) {
        return a[1] < b[1];
    }
    
    int scheduleCourse(vector<vector<int>>& courses) {
        // Step 1: Courses ko deadline par sort karo
        sort(courses.begin(), courses.end(), compare);

        // Max-heap jo durations store karega
        priority_queue<int> pq;
        int current_time = 0;

        for (const auto& course : courses) {
            int duration = course[0];
            int lastDay = course[1];

            // Agar course ko time par kar sakte hain
            if (current_time + duration <= lastDay) {
                current_time += duration;
                pq.push(duration);
            } 
            // Agar nahi kar sakte, to swap karne ki koshish karo
            else if (!pq.empty() && pq.top() > duration) {
                // Sabse lambe purane course ko is naye chote course se badlo
                current_time -= pq.top();
                pq.pop();
                current_time += duration;
                pq.push(duration);
            }
        }
        
        return pq.size();
    }
};

/*
Time Complexity: O(N log N)
Sorting mein O(N log N). Loop N baar chalta hai, aur har baar PQ operation O(log N) leta hai.

Space Complexity: O(N)
Worst case mein, priority queue saare courses ki durations store kar sakti hai.
*/
```

-----

-----

## 4\. Parallel Courses (LeetCode 1136)

### **Problem Statement (PS)**

Aapke paas `n` courses hain, 1 se `n` tak. `relations` array prerequisites batata hai. Ek semester mein, aap jitne marzi courses le sakte hain, bas unke prerequisites uss semester se pehle poore ho chuke hon. Aapko batana hai ki saare courses complete karne mein **minimum kitne semesters** lagenge. Agar saare courses karna impossible hai (cycle hai), to `-1` return karo.

### **Examples**

**Example 1:**

  * **Input:** `n = 3, relations = [[1,3],[2,3]]`
  * **Output:** `2`
  * **Explanation:** Semester 1 mein course 1 aur 2. Semester 2 mein course 3.

**Example 2:**

  * **Input:** `n = 3, relations = [[1,2],[2,3],[3,1]]`
  * **Output:** `-1`
  * **Explanation:** Cycle hai, isliye impossible.

-----

### **Approach 1: Naive (DFS)**

Yeh problem graph mein longest path nikalne jaisi hai. Hum har node se DFS karke usse shuru hone wale longest path ki length nikal sakte hain.
`depth[node] = 1 + max(depth(neighbor))` over all neighbors.
Is approach ko efficient banane ke liye memoization zaroori hai. Saath hi, cycle detection bhi karna hoga. Agar cycle milti hai to `-1` return karna hoga.

*(Yeh approach code mein lagbhag optimal jaisi hi ban jaati hai, isliye hum seedhe optimal BFS approach dekhenge jo is problem ke liye zyada natural hai.)*

-----

### **Approach 2: Optimal (BFS - Kahn's Algorithm)**

Yeh "topological sort by levels" hai. Har level ek semester ko represent karta hai.

1.  Graph banayein aur sabhi courses ka `in-degree` calculate karein.
2.  Queue mein woh saare courses daalein jinka `in-degree` 0 hai. Yeh semester 1 ke courses hain.
3.  Ab level-by-level BFS chalayein:
      * Ek level ke saare courses ko queue se nikalein (yeh ek semester hai).
      * Semester count badhayein.
      * In courses ke saare neighbors ka `in-degree` kam karein.
      * Agar kisi neighbor ka `in-degree` 0 ho jaaye, to use agle level ke liye queue mein daal dein.
4.  Agar aakhir mein process kiye gaye courses `n` ke barabar nahi hain, to cycle thi. `-1` return karein. Nahi to `semester count` return karein.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Parallel Courses

class Solution {
public:
    int minimumSemesters(int n, vector<vector<int>>& relations) {
        vector<vector<int>> adj(n + 1);
        vector<int> inDegree(n + 1, 0);
        
        for(const auto& rel : relations) {
            adj[rel[0]].push_back(rel[1]);
            inDegree[rel[1]]++;
        }
        
        queue<int> q;
        for(int i = 1; i <= n; ++i) {
            if(inDegree[i] == 0) {
                q.push(i);
            }
        }
        
        int semesters = 0;
        int courses_done = 0;
        
        while(!q.empty()) {
            int level_size = q.size();
            semesters++;
            for(int i = 0; i < level_size; ++i) {
                int u = q.front();
                q.pop();
                courses_done++;
                
                for(int v : adj[u]) {
                    inDegree[v]--;
                    if(inDegree[v] == 0) {
                        q.push(v);
                    }
                }
            }
        }
        
        return courses_done == n ? semesters : -1;
    }
};

/*
Time Complexity: O(V + E)
Graph banane aur BFS traversal ka time. V courses, E relations.

Space Complexity: O(V + E)
Adjacency list, in-degree array, aur queue ke liye.
*/
```

-----

-----

## 5\. Parallel Courses III (LeetCode 2050)

### **Problem Statement (PS)**

Yeh 'Parallel Courses' jaisa hi hai, par is baar har course `i` ko complete karne mein `time[i]` mahine lagte hain. Aap ek course tabhi shuru kar sakte hain jab uske saare prerequisites poore ho chuke hon. Aap ek saath kitne bhi courses kar sakte hain. Aapko batana hai ki saare courses complete karne mein **minimum kitna time** lagega.

### **Examples**

**Example 1:**

  * **Input:** `n = 3, relations = [[1,3],[2,3]], time = [3,2,5]` (Courses 1-based, time 0-based)
  * **Output:** `8`
  * **Explanation:** Course 1 (3 mahine) aur 2 (2 mahine) time 0 par shuru honge. Course 3 shuru karne ke liye dono ka poora hona zaroori hai. Course 1 time 3 par, course 2 time 2 par khatam hoga. To course 3, time 3 par shuru ho sakta hai. Use 5 mahine lagenge. Total time = 3 + 5 = 8.

-----

### **Approach 1: Naive (DFS)**

Hum har node ke liye `maxTimeToFinish[node]` calculate kar sakte hain. Yeh uss node tak pahunchne ka "critical path" (sabse lamba weighted path) hoga.
`maxTimeToFinish[node] = time[node] + max(maxTimeToFinish(prerequisite))`
Iske liye DFS with memoization ka use karna hoga.

*(Yeh approach bhi code mein optimal jaisi hi banti hai, isliye hum seedhe optimal BFS approach dekhenge.)*

-----

### **Approach 2: Optimal (Topological Sort BFS)**

Yeh problem graph mein "critical path" nikalne jaisi hai. Hum topological sort ka use karenge.

1.  Graph banayein aur `in-degree` calculate karein.
2.  Ek `completionTime` array banayein jo har course ka earliest finish time store karega.
3.  Queue mein 0 `in-degree` wale courses daalein. Inka `completionTime` unke apne `time` ke barabar hoga.
4.  BFS (Kahn's Algorithm) chalayein:
      * Ek course `u` ko queue se nikalein.
      * Uske har neighbor `v` ke liye:
          * `v` ko shuru karne se pehle uske saare prerequisites khatam hone chahiye. To, `v` ka finish time uske sabse late finish hone wale prerequisite par depend karega.
          * Update `completionTime[v] = max(completionTime[v], completionTime[u] + time[v])`.
          * `v` ka `in-degree` kam karein. Agar 0 ho jaaye, to use queue mein daalein.
5.  Poore process ke baad, `completionTime` array ki maximum value hi humara final answer hogi.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Parallel Courses III

class Solution {
public:
    int minimumTime(int n, vector<vector<int>>& relations, vector<int>& time) {
        vector<vector<int>> adj(n);
        vector<int> inDegree(n, 0);

        for (const auto& rel : relations) {
            int u = rel[0] - 1; // 0-based indexing
            int v = rel[1] - 1; // 0-based indexing
            adj[u].push_back(v);
            inDegree[v]++;
        }

        queue<int> q;
        // completionTime[i] = course i ka earliest finish time
        vector<int> completionTime(n, 0);

        for (int i = 0; i < n; ++i) {
            if (inDegree[i] == 0) {
                q.push(i);
                completionTime[i] = time[i];
            }
        }

        while (!q.empty()) {
            int u = q.front();
            q.pop();

            for (int v : adj[u]) {
                // v ko tabhi shuru kar sakte hain jab u khatam ho
                // Hum v ke saare prerequisites ke max completion time ka wait karenge
                completionTime[v] = max(completionTime[v], completionTime[u] + time[v]);
                inDegree[v]--;
                if (inDegree[v] == 0) {
                    q.push(v);
                }
            }
        }
        
        // Final answer poore project ka completion time hai,
        // jo ki kisi bhi course ke max completion time ke barabar hoga.
        return *max_element(completionTime.begin(), completionTime.end());
    }
};

/*
Time Complexity: O(V + E)
Graph banane aur BFS traversal ka time. V courses, E relations.

Space Complexity: O(V + E)
Adjacency list, in-degree array, aur completionTime array ke liye.
*/
```


-----

-----

## 6\. Minimum Time to Complete All Tasks (LeetCode 2589)

### **Problem Statement (PS)**

Aapko `n` tasks ka ek 2D array `tasks` diya gaya hai, jahan har task `[start_i, end_i, duration_i]` se represent hota hai. Aapko har task ko uske `start` aur `end` time ke beech mein, `duration_i` samay ke liye poora karna hai. Aap ek hi samay mein kai tasks kar sakte hain. Aapko batana hai ki saare tasks ko poora karne ke liye computer ko **minimum total kitne time units** tak on rakhna padega.

### **Examples**

**Example 1:**

  * **Input:** `tasks = [[2,3,1],[4,5,1],[1,5,2]]`
  * **Output:** `2`
  * **Explanation:** Ek task time 2 par, aur doosra time 5 par karne se saare tasks poore ho jaate hain. Total 2 time units ke liye computer on rahega.

**Example 2:**

  * **Input:** `tasks = [[1,3,2],[2,5,3],[5,6,2]]`
  * **Output:** `4`
  * **Explanation:** Time 2, 3, 5, 6 par computer on karke saare tasks kiye ja sakte hain. Total 4 time units.

-----

### **Approach 1: Naive (Brute-force Time Slots)**

Is approach mein hum har task ke liye uske `[start, end]` range mein se `duration` time slots chunne ke saare combinations try kar sakte hain. Phir un combinations ka union (total on time) nikal kar minimum dhundh sakte hain. Yeh approach bahut hi zyada complex aur slow (exponential) hai, isliye iska code practical nahi hai.

*Is problem ke liye koi simple naive code likhna mushkil hai, isliye hum seedhe optimal greedy approach par focus karenge, jo iska intended solution hai.*

-----

### **Approach 2: Optimal (Greedy Approach)**

Is problem ko solve karne ka sabse accha tareeka greedy hai. Logic yeh hai ki humein tasks ko **jitna late ho sake utna late** karna chahiye. Aisa karne se jo time slots hum on karte hain, unke aage aane wale tasks dwara reuse hone ka chance badh jaata hai.

1.  Saare tasks ko unke **end time** ke basis par sort karo.
2.  Ek `time_slots` set/array rakho jo on kiye gaye time ko track karega.
3.  Ab sorted tasks par iterate karo:
      * Har task ke liye, pehle check karo ki uski kitni `duration` pehle se on kiye gaye `time_slots` mein poori ho chuki hai.
      * Agar abhi bhi `needed_time` baaki hai, to task ke `end` time se peeche ki taraf jao aur `needed_time` ke barabar "off" slots ko "on" kar do (set mein daal do).

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Minimum Time to Complete All Tasks

class Solution {
public:
    int findMinimumTime(vector<vector<int>>& tasks) {
        // Step 1: Tasks ko end time par sort karo
        sort(tasks.begin(), tasks.end(), [](const auto& a, const auto& b) {
            return a[1] < b[1];
        });

        // Track karega ki kaun se time slots on hain
        vector<bool> time_on(2001, false);

        for (const auto& task : tasks) {
            int start = task[0], end = task[1], duration = task[2];
            
            // Step 2: Check karo ki kitna duration pehle se cover ho chuka hai
            int covered_time = 0;
            for (int t = start; t <= end; ++t) {
                if (time_on[t]) {
                    covered_time++;
                }
            }

            int needed_time = duration - covered_time;
            
            // Step 3: Agar zaroorat hai, to late se late time slots on karo
            if (needed_time > 0) {
                for (int t = end; t >= start && needed_time > 0; --t) {
                    if (!time_on[t]) {
                        time_on[t] = true;
                        needed_time--;
                    }
                }
            }
        }

        int total_on_time = 0;
        for (int i = 0; i <= 2000; ++i) {
            if (time_on[i]) {
                total_on_time++;
            }
        }
        return total_on_time;
    }
};


/*
Time Complexity: O(N * D)
Jahan N tasks ka number hai aur D max end time (2000) hai. Sorting O(N log N) hai,
lekin loop O(N*D) dominate karega.

Space Complexity: O(D)
Time slots ko track karne wale array ke liye.
*/
```

-----

-----

## 7\. Minimum Number of Days to Eat N Oranges (LeetCode 1553)

### **Problem Statement (PS)**

Aapke paas `n` santre (oranges) hain. Har din aap neeche diye gaye kaam kar sakte hain:

1.  Ek santra khao.
2.  Agar `n` 2 se divisible hai, to aap `n/2` santre kha sakte hain. Aapke paas `n - n/2 = n/2` santre bachenge.
3.  Agar `n` 3 se divisible hai, to aap `2n/3` santre kha sakte hain. Aapke paas `n - 2n/3 = n/3` santre bachenge.

Aapko batana hai ki `n` santron ko 0 karne mein **minimum kitne din** lagenge.

### **Examples**

**Example 1:**

  * **Input:** `n = 10`
  * **Output:** `4`
  * **Explanation:** 10 -\> 5 (khaaye n/2) -\> 4 (khaaya 1) -\> 2 (khaaya 1) -\> 1 (khaaye n/2) -\> 0. No... 10 -\> 5 (1 din) -\> 4 (1 din) -\> 2 (1 din) -\> 1 (1 din) -\> 0 (1 din) = 5 din.
    Better: 10 -\> 9 (1 din) -\> 3 (1 din) -\> 1 (1 din) -\> 0 (1 din) = 4 din.

**Example 2:**

  * **Input:** `n = 6`
  * **Output:** `3`
  * **Explanation:** 6 -\> 3 (khaaye n/2) -\> 1 (khaaye 2n/3) -\> 0 (khaaya 1). Total 3 din.

-----

### **Approach 1: Naive (BFS)**

Yeh ek shortest path problem jaisa hai, jahan har state santron ki sankhya hai. Hum Breadth-First Search (BFS) ka use karke 0 tak ka sabse chhota raasta dhundh sakte hain.

1.  Ek queue mein `n` daalo.
2.  Level-by-level traverse karo. Har level ek din represent karta hai.
3.  Queue se `current_n` nikalo aur uske saare possible next states (`current_n - 1`, `current_n / 2`, `current_n / 3`) ko queue mein daalo.
4.  Ek `visited` set ka use karo taaki hum same state ko baar baar process na karein.
5.  Jab hum 0 par pahunche, tab tak jitne levels (din) lage, wahi jawab hai.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Minimum Number of Days to Eat N Oranges

class Solution {
public:
    int minDays(int n) {
        queue<int> q;
        q.push(n);
        unordered_set<int> visited;
        visited.insert(n);
        
        int days = 0;
        
        while (!q.empty()) {
            int level_size = q.size();
            days++;
            for (int i = 0; i < level_size; ++i) {
                int current_n = q.front();
                q.pop();

                // Option 1: Eat 2n/3
                if (current_n % 3 == 0) {
                    int next_n = current_n / 3;
                    if (next_n == 0) return days;
                    if (visited.find(next_n) == visited.end()) {
                        q.push(next_n);
                        visited.insert(next_n);
                    }
                }
                // Option 2: Eat n/2
                if (current_n % 2 == 0) {
                    int next_n = current_n / 2;
                    if (next_n == 0) return days;
                    if (visited.find(next_n) == visited.end()) {
                        q.push(next_n);
                        visited.insert(next_n);
                    }
                }
                // Option 3: Eat 1
                int next_n = current_n - 1;
                if (next_n == 0) return days;
                if (visited.find(next_n) == visited.end()) {
                    q.push(next_n);
                    visited.insert(next_n);
                }
            }
        }
        return days;
    }
};

/*
Time Complexity: BFS ki complexity V+E jaisi hoti hai. Yahan states bahut zyada ho sakti hain.
Bade 'n' ke liye TLE de sakta hai.

Space Complexity: O(N)
Visited set aur queue ke liye.
*/
```

-----

### **Approach 2: Optimal (Top-down DP with Memoization)**

BFS se behtar Top-down DP (ya recursion with memoization) hai. `solve(k)` ka matlab `k` santre khaane mein minimum din.

  * `solve(0) = 0`, `solve(1) = 1`.
  * `k` santre khaane ke liye, hum `k/2` ya `k/3` tak jaana chahenge. Iske liye humein pehle `k` ko 2 ya 3 se divisible banana hoga (1-1 karke kha kar).
      * `k/2` tak jaane mein `(k % 2)` din (1-1 karke khaane) + 1 din (`k/2` khaane) + `solve(k/2)` din lagenge.
      * `k/3` tak jaane mein `(k % 3)` din + 1 din + `solve(k/3)` din lagenge.
  * In dono options ka minimum humara jawab hoga.
  * Hum ek `map` ka use karenge intermediate results ko store (memoize) karne ke liye.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Minimum Number of Days to Eat N Oranges

class Solution {
private:
    unordered_map<int, int> memo;

public:
    int minDays(int n) {
        if (n <= 1) {
            return n;
        }
        if (memo.count(n)) {
            return memo[n];
        }

        // Option 1: Eat until divisible by 2, then eat n/2
        int op1 = (n % 2) + 1 + minDays(n / 2);
        
        // Option 2: Eat until divisible by 3, then eat 2n/3
        int op2 = (n % 3) + 1 + minDays(n / 3);

        return memo[n] = min(op1, op2);
    }
};

/*
Time Complexity: O(log^2 N) or something close to it.
Kyunki hum 'n' ko tezi se divide karte hain, states bahut kam ho jaati hain.

Space Complexity: O(log N)
Map mein recursion path ke states store honge.
*/
```

-----

-----

## 8\. Task Scheduler (LeetCode 621)

### **Problem Statement (PS)**

Aapko CPU ko execute karne ke liye `tasks` ka ek array diya gaya hai (har character ek task hai). Har task 1 time unit leta hai. Same task ke do instances ke beech mein kam se kam `n` units ka "cooldown" period hona chahiye. Har time unit mein CPU ya to ek task kar sakta hai ya "idle" (khaali) reh sakta hai. Saare tasks ko poora karne mein **minimum kitna time** lagega, yeh batana hai.

### **Examples**

**Example 1:**

  * **Input:** `tasks = ["A","A","A","B","B","B"]`, `n = 2`
  * **Output:** `8`
  * **Explanation:** Ek possible schedule hai: A -\> B -\> idle -\> A -\> B -\> idle -\> A -\> B.

**Example 2:**

  * **Input:** `tasks = ["A","A","A","B","B","B"]`, `n = 0`
  * **Output:** `6`
  * **Explanation:** Cooldown 0 hai, to saare tasks ek ke baad ek kiye ja sakte hain: A,A,A,B,B,B.

-----

### **Approach 1: Naive (Simulation with Priority Queue)**

Hum is process ko time unit by time unit simulate kar sakte hain.

1.  Har task ki frequency count karo.
2.  Ek `max-priority queue` mein saare tasks ki frequencies daalo.
3.  Ek loop chalao jo time ko represent karta hai. Har `n+1` time units ke 'cycle' mein:
      * `n+1` baar, PQ se sabse frequent task nikalo, uski frequency kam karo, aur use ek temporary list mein daal do.
      * Cycle ke baad, temporary list ke saare tasks ko (jinki freq \> 0 hai) wapas PQ mein daal do.
      * Total time ko accordingly badhao.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Task Scheduler

class Solution {
public:
    int leastInterval(vector<char>& tasks, int n) {
        unordered_map<char, int> counts;
        for (char t : tasks) {
            counts[t]++;
        }

        priority_queue<int> pq;
        for (auto const& [task, freq] : counts) {
            pq.push(freq);
        }

        int time = 0;
        while (!pq.empty()) {
            vector<int> temp;
            // Ek cycle (n+1) units ka hota hai
            for (int i = 0; i <= n; ++i) {
                if (!pq.empty()) {
                    temp.push_back(pq.top());
                    pq.pop();
                }
            }

            for (int freq : temp) {
                if (freq - 1 > 0) {
                    pq.push(freq - 1);
                }
            }
            
            // Time badhao
            // Agar PQ empty hai, to yeh aakhri cycle tha
            time += pq.empty() ? temp.size() : n + 1;
        }
        
        return time;
    }
};

/*
Time Complexity: O(T * log(U))
Jahan T total time hai aur U unique tasks (max 26) hain. Har cycle mein hum PQ se nikalte aur daalte hain.

Space Complexity: O(U) or O(1)
Map aur PQ ke liye, jo max 26 size ke honge.
*/
```

-----

### **Approach 2: Optimal (Greedy / Mathematical)**

Is problem ka time schedule sabse zyada frequent task par depend karta hai.

1.  Sabse frequent task ki frequency (`max_freq`) nikalo.
2.  Kitne tasks hain jinki frequency `max_freq` ke barabar hai (`count_max_freq`)?
3.  Socho, `max_freq` wala task `A` hai. Schedule `A ... A ... A ... A` jaisa dikhega. `max_freq-1` gaps honge.
4.  Har gap kam se kam `n` units lamba hona chahiye. To in gaps ko fill karne ke liye `(max_freq - 1) * n` time slots hain.
5.  Aakhri baar jab saare `max_freq` wale tasks execute honge, unhe `count_max_freq` time slots lagenge.
6.  To, total time kam se kam `(max_freq - 1) * (n + 1) + count_max_freq` hoga.
7.  Ek special case hai: jab itne saare alag-alag tasks hon ki koi idle time ho hi na. Us case mein total time bas `tasks.size()` hoga.
8.  To final jawab in dono ka maximum hoga.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Task Scheduler

class Solution {
public:
    int leastInterval(vector<char>& tasks, int n) {
        unordered_map<char, int> counts;
        int max_freq = 0;
        for (char task : tasks) {
            counts[task]++;
            max_freq = max(max_freq, counts[task]);
        }

        // Formula-based approach
        // (max_freq - 1) gaps hain
        // Har gap n+1 size ka (task + n idle slots)
        int time = (max_freq - 1) * (n + 1);
        
        // Aakhri cycle mein kitne max_freq wale tasks hain
        int count_max_freq = 0;
        for (auto const& [task, freq] : counts) {
            if (freq == max_freq) {
                count_max_freq++;
            }
        }
        time += count_max_freq;

        // Final answer total tasks se kam nahi ho sakta
        return max((int)tasks.size(), time);
    }
};

/*
Time Complexity: O(N)
Jahan N tasks ka total number hai, frequency count karne ke liye.

Space Complexity: O(U) or O(1)
Map ke liye, jo max 26 size ka hoga.
*/
```

-----

-----

## 9\. Reorganize String (LeetCode 767)

### **Problem Statement (PS)**

Aapko ek string `s` di gayi hai. Aapko uske characters ko is tarah **rearrange** karna hai ki koi bhi do aaju-baaju (adjacent) ke characters same na hon. Agar aisa karna possible hai, to koi bhi ek valid rearranged string return karo. Agar nahi, to ek empty string `""` return karo.

### **Examples**

**Example 1:**

  * **Input:** `s = "aab"`
  * **Output:** `"aba"`

**Example 2:**

  * **Input:** `s = "aaab"`
  * **Output:** `""`
  * **Explanation:** 'a' ko is tarah nahi rakha ja sakta ki koi do 'a' saath na aayein.

-----

### **Approach 1: Naive (Backtracking)**

Hum string ke saare permutations generate kar sakte hain aur har permutation ko check kar sakte hain ki kya woh valid hai (koi adjacent characters same nahi hain). Jaise hi pehla valid permutation milta hai, use return kar do. Agar koi nahi milta, to `""` return karo. Yeh approach `O(n! * n)` hogi, jo TLE degi.

*(Iska code likhna complex hai aur yeh guaranteed TLE dega, isliye hum seedhe optimal greedy approach par focus karenge.)*

-----

### **Approach 2: Optimal (Greedy with Priority Queue)**

Greedy strategy yeh hai ki har step par hum sabse frequent character ko rakhein jo pichle character se alag ho.

1.  Sabse pehle, har character ki frequency count karo. Check karo ki kya solution possible hai. Solution tabhi impossible hai jab kisi ek character ki frequency `(n+1)/2` se zyada ho.
2.  Ek `max-priority queue` ka use karo, jismein `(frequency, character)` ke pairs store honge.
3.  Jab tak priority queue mein 1 se zyada element hai:
      * Do sabse frequent characters (`top1`, `top2`) ko `pop` karo.
      * Unhe result string mein `append` karo.
      * Unki frequencies kam karke (agar \> 0 hain) wapas `push` kar do.
4.  Aakhir mein agar queue mein koi ek element bachta hai, to use append kar do.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Reorganize String

class Solution {
public:
    string reorganizeString(string s) {
        unordered_map<char, int> counts;
        for (char c : s) {
            counts[c]++;
        }

        priority_queue<pair<int, char>> pq;
        for (auto const& [key, val] : counts) {
            // Possibility check
            if (val > (s.length() + 1) / 2) {
                return "";
            }
            pq.push({val, key});
        }
        
        string res = "";
        
        while (pq.size() >= 2) {
            auto top1 = pq.top(); pq.pop();
            auto top2 = pq.top(); pq.pop();
            
            res += top1.second;
            res += top2.second;
            
            top1.first--;
            top2.first--;
            
            if (top1.first > 0) pq.push(top1);
            if (top2.first > 0) pq.push(top2);
        }
        
        if (!pq.empty()) {
            res += pq.top().second;
        }
        
        return res;
    }
};

/*
Time Complexity: O(N log U)
Jahan N string ki length aur U unique characters (max 26) hain. Frequency count O(N) hai.
PQ operations O(log U) lete hain, aur hum N baar loop karte hain.

Space Complexity: O(U) or O(1)
Map aur PQ ke liye.
*/
```

-----

-----

## 10\. Rearrange String k Distance Apart (LeetCode 358 - Premium)

### **Problem Statement (PS)**

Aapko ek non-empty string `s` aur ek integer `k` diya gaya hai. Aapko string ko is tarah **rearrange** karna hai ki koi bhi do same characters ke beech kam se kam `k` characters ka distance ho. Agar possible hai, to rearranged string return karo, varna empty string `""`.

### **Examples**

**Example 1:**

  * **Input:** `s = "aabbcc", k = 3`
  * **Output:** `"abcabc"`
  * **Explanation:** Har same character ke beech kam se kam 3 ka distance hai.

**Example 2:**

  * **Input:** `s = "aaadbbcc", k = 2`
  * **Output:** `"abacabcd"`
  * **Explanation:** Valid hai.

**Example 3:**

  * **Input:** `s = "aaabc", k = 3`
  * **Output:** `""`
  * **Explanation:** 'a' ko 3 ke distance par nahi rakha ja sakta.

-----

### **Approach 1: Naive (Backtracking)**

"Reorganize String" jaisa hi, hum saare permutations generate karke check kar sakte hain. Lekin yeh `O(n!)` hoga aur TLE dega.

*(Iska code bhi practical nahi hai, isliye hum seedhe optimal greedy approach par focus karenge.)*

-----

### **Approach 2: Optimal (Greedy with Priority Queue)**

Yeh 'Reorganize String' ka extension hai. Yahan cooldown 2 ke bajaye `k` hai.

1.  Har character ki frequency count karo.
2.  Ek `max-priority queue` mein `(frequency, character)` pairs daalo.
3.  Ek `waitQueue` (normal queue) ka use karo jo un characters ko store karega jo abhi "cooldown" mein hain. Wait queue `(frequency, char)` pairs store karegi. Iska size `k` hoga.
4.  Jab tak result string poori na ban jaaye:
      * `waitQueue` se un characters ko `priority queue` mein wapas daalo jinka cooldown poora ho gaya hai.
      * `priority queue` se sabse frequent character nikalo. Use result mein `append` karo.
      * Uski frequency kam karke use `waitQueue` mein daal do.
      * Agar `priority queue` khali hai lekin string poori nahi bani, to iska matlab rearrangement possible nahi.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Rearrange String k Distance Apart

class Solution {
public:
    string rearrangeString(string s, int k) {
        if (k == 0) return s;

        unordered_map<char, int> counts;
        for (char c : s) {
            counts[c]++;
        }

        priority_queue<pair<int, char>> pq;
        for (auto const& [key, val] : counts) {
            pq.push({val, key});
        }
        
        string res = "";
        // Wait queue (char, freq) un characters ke liye jo cooldown mein hain
        queue<pair<int, char>> wait_q;

        while (res.length() < s.length()) {
            // Agar PQ khali hai, par string poori nahi bani, to impossible
            if (pq.empty()) {
                return "";
            }

            auto top = pq.top();
            pq.pop();
            
            res += top.second;
            top.first--;
            
            wait_q.push(top);

            // Cooldown poora hone par wait queue se wapas PQ mein daalo
            if (wait_q.size() >= k) {
                auto ready = wait_q.front();
                wait_q.pop();
                if (ready.first > 0) {
                    pq.push(ready);
                }
            }
        }

        return res;
    }
};

/*
Time Complexity: O(N log U)
Jahan N string ki length aur U unique characters (max 26) hain.

Space Complexity: O(U) or O(1)
Map, PQ, aur wait queue ke liye.
*/
```

-----

-----

## 11\. Employee Free Time (LeetCode 759)

### **Problem Statement (PS)**

Aapko employees ke schedules ki ek list `schedule` di gayi hai. Har employee ka schedule `[start, end]` time intervals ki ek sorted list hai jo unke busy time ko batati hai. Aapko saare employees ka **common free time** nikalna hai (woh time jab koi bhi employee busy nahi hai). Result ko sorted intervals ki list mein return karna hai.

### **Examples**

**Example 1:**

  * **Input:** `schedule = [[[1,2],[5,6]],[[1,3]],[[4,10]]]`
  * **Output:** `[[3,4]]`
  * **Explanation:** Saare employees `[3,4]` ke time interval mein free hain.

**Example 2:**

  * **Input:** `schedule = [[[1,3],[6,7]],[[2,4]],[[2,5],[9,12]]]`
  * **Output:** `[[5,6],[7,9]]`

-----

### **Approach 1: Naive (Collect and Merge)**

Sabse aasan tareeka hai:

1.  Saare employees ke saare busy intervals ko ek hi list mein daal do.
2.  Is "master" list ko **start time** ke basis par sort karo.
3.  Ab is list par "Merge Intervals" wala logic lagao. Saare overlapping intervals ko merge karke ek final `busy_times` list banao.
4.  Aakhir mein, is `busy_times` list ke beech ke "gaps" hi common free time honge.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Employee Free Time

class Interval {
public:
    int start;
    int end;

    Interval() {}

    Interval(int _start, int _end) {
        start = _start;
        end = _end;
    }
};

class Solution {
public:
    vector<Interval> employeeFreeTime(vector<vector<Interval>> schedule) {
        // Step 1: Saare intervals ko ek list mein daalo
        vector<Interval> all_intervals;
        for (const auto& emp_schedule : schedule) {
            for (const auto& interval : emp_schedule) {
                all_intervals.push_back(interval);
            }
        }

        if (all_intervals.empty()) return {};

        // Step 2: Master list ko sort karo
        sort(all_intervals.begin(), all_intervals.end(), [](const Interval& a, const Interval& b) {
            return a.start < b.start;
        });

        // Step 3: Intervals ko merge karo
        vector<Interval> merged_intervals;
        merged_intervals.push_back(all_intervals[0]);
        for (size_t i = 1; i < all_intervals.size(); ++i) {
            if (all_intervals[i].start <= merged_intervals.back().end) {
                merged_intervals.back().end = max(merged_intervals.back().end, all_intervals[i].end);
            } else {
                merged_intervals.push_back(all_intervals[i]);
            }
        }

        // Step 4: Gaps (free time) nikalo
        vector<Interval> free_time;
        for (size_t i = 1; i < merged_intervals.size(); ++i) {
            if (merged_intervals[i-1].end < merged_intervals[i].start) {
                free_time.push_back(Interval(merged_intervals[i-1].end, merged_intervals[i].start));
            }
        }

        return free_time;
    }
};

/*
Time Complexity: O(N log N)
Jahan N saare employees ke total intervals hain. Complexity sorting dominate karti hai.

Space Complexity: O(N)
Saare intervals ko store karne wali master list ke liye.
*/
```

-----

### **Approach 2: Optimal (Priority Queue / Heap)**

Ek memory-efficient approach "Merge K Sorted Lists" jaisi hai. Hum ek `min-priority queue` ka use karte hain jo hamesha us interval ko top par rakhta hai jo sabse jaldi shuru hota hai.

1.  Ek min-priority queue banayein. Har employee ka pehla interval (saath mein employee ka index aur uske schedule mein interval ka index) ismein daalein.
2.  Jab tak PQ khali na ho:
      * Sabse jaldi shuru hone wala interval `(top)` nikalo.
      * Is `top` interval ko `previous_busy_interval` ke saath compare karo. Agar `top.start > previous_busy_interval.end` hai, to ek free time `[previous.end, top.start]` mil gaya.
      * `previous_busy_interval` ko `top` ke saath merge karke update karo.
      * Jis employee ka interval humne nikala, agar uske paas aur intervals hain, to uska agla interval PQ mein daal do.

<!-- end list -->

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Employee Free Time

class Interval {
public:
    int start;
    int end;
    Interval(int _start, int _end) : start(_start), end(_end) {}
};

// {interval_start, emp_idx, interval_idx}
using P = pair<int, pair<int, int>>;

class Solution {
public:
    vector<Interval> employeeFreeTime(vector<vector<Interval>> schedule) {
        // Min-heap
        priority_queue<P, vector<P>, greater<P>> pq;

        // Har employee ka pehla interval PQ mein daalo
        for (int i = 0; i < schedule.size(); ++i) {
            if (!schedule[i].empty()) {
                pq.push({schedule[i][0].start, {i, 0}});
            }
        }
        
        vector<Interval> result;
        if(pq.empty()) return result;
        
        // Pehla busy interval
        auto top = pq.top();
        pq.pop();
        int prev_end = schedule[top.second.first][top.second.second].end;

        // Us employee ka agla interval daalo
        if(schedule[top.second.first].size() > 1){
            pq.push({schedule[top.second.first][1].start, {top.second.first, 1}});
        }

        while (!pq.empty()) {
            top = pq.top();
            pq.pop();
            int emp_idx = top.second.first;
            int interval_idx = top.second.second;
            Interval current_interval = schedule[emp_idx][interval_idx];

            // Agar gap hai, to woh free time hai
            if (current_interval.start > prev_end) {
                result.push_back(Interval(prev_end, current_interval.start));
            }
            
            // Busy time ko update karo
            prev_end = max(prev_end, current_interval.end);
            
            // Us employee ka agla interval daalo
            if(schedule[emp_idx].size() > interval_idx + 1) {
                pq.push({schedule[emp_idx][interval_idx + 1].start, {emp_idx, interval_idx + 1}});
            }
        }

        return result;
    }
};

/*
Time Complexity: O(N log K)
Jahan N total intervals hain aur K employees ka number hai. Har interval PQ mein ek baar
jaata hai, aur PQ operations O(log K) lete hain.

Space Complexity: O(K)
Priority queue mein at most K intervals (har employee se ek) honge.
*/
```

-----

-----

## 4\. Increasing Subsequences (LeetCode 491)

### **Problem Statement (PS)**

Aapko ek integer array `nums` diya gaya hai. Aapko uske **saare alag-alag** (unique) **increasing subsequences** return karne hain jinki length **kam se kam 2** ho. Order matter nahi karta.

### **Examples**

**Example 1:**

  * **Input:** `nums = [4,6,7,7]`
  * **Output:** `[[4,6],[4,7],[4,6,7],[4,6,7,7],[6,7],[6,7,7],[7,7],[4,7,7]]`
  * **Explanation:** Ye saare possible unique increasing subsequences hain jinki length \>= 2 hai.

**Example 2:**

  * **Input:** `nums = [4,4,3,2,1]`
  * **Output:** `[[4,4]]`
  * **Explanation:** Sirf `[4,4]` hi ek valid increasing (non-decreasing) subsequence hai.

-----

### **Approach 1: Naive (Backtracking with a Set)**

Kyunki humein saare possible subsequences chahiye, **backtracking** (recursion) ek natural choice hai. Hum ek recursive function banayenge jo 0-index se shuru hoga aur har element ke liye decide karega ki use current subsequence mein add karna hai ya nahi. Add karne ki condition yeh hai ki `nums[i]` current subsequence ke aakhri element se bada ya barabar ho.

Duplicate subsequences se bachne ke liye, hum saare valid subsequences ko ek **`set`** mein store karenge.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Increasing Subsequences

class Solution {
private:
    set<vector<int>> unique_subsequences;
    
    void findSubsequencesHelper(vector<int>& nums, int index, vector<int>& current) {
        // Base case
        if (index == nums.size()) {
            if (current.size() >= 2) {
                unique_subsequences.insert(current);
            }
            return;
        }

        // Option 1: Current element ko nahi lete
        findSubsequencesHelper(nums, index + 1, current);
        
        // Option 2: Current element ko lete hain
        // (agar woh increasing order maintain karta hai)
        if (current.empty() || nums[index] >= current.back()) {
            current.push_back(nums[index]);
            findSubsequencesHelper(nums, index + 1, current);
            current.pop_back(); // Backtrack
        }
    }

public:
    vector<vector<int>> findSubsequences(vector<int>& nums) {
        vector<int> current;
        findSubsequencesHelper(nums, 0, current);
        
        // Set se result ko vector mein convert karo
        return vector<vector<int>>(unique_subsequences.begin(), unique_subsequences.end());
    }
};

/*
Time Complexity: O(2^n * n)
Worst case mein 2^n subsequences ho sakte hain, aur har subsequence ko set mein
insert karne mein O(n) lag sakta hai.

Space Complexity: O(2^n * n)
Set saare subsequences ko store karega.
*/
```

-----

### **Approach 2: Optimal (Backtracking with Local Set for Pruning)**

Pichli approach mein hum saare paths generate karke baad mein `set` se duplicates hata rahe the. Ek behtar tareeka hai ki hum duplicate paths ko generate hi na karein.

Hum recursion ke har level par ek local `set` (`used_in_this_level`) maintain kar sakte hain. Yeh set track karega ki uss level par kaunse numbers pehle hi use ho chuke hain. Agar hum `nums = [4, 7, 7]` par hain aur `[4]` bana chuke hain, toh agle level par jab hum pehla `7` use karenge, toh use `used_in_this_level` mein daal denge. Jab hum dusre `7` par aayenge, hum dekhenge ki `7` toh is level par pehle hi use ho chuka hai, isliye hum use skip kar denge. Isse duplicate branches banti hi nahi hain.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Problem: Increasing Subsequences

class Solution {
private:
    vector<vector<int>> result;
    
    void find(vector<int>& nums, int index, vector<int>& current) {
        // Agar current subsequence valid hai (length >= 2), result mein add karo
        if (current.size() >= 2) {
            result.push_back(current);
        }
        
        // Ek set, jo is recursion level par use hue numbers ko track karega
        unordered_set<int> used_in_this_level;
        
        for (int i = index; i < nums.size(); ++i) {
            // Condition 1: Agar current number pichle se chota hai, skip karo
            if (!current.empty() && nums[i] < current.back()) {
                continue;
            }
            
            // Condition 2: Agar is level par yeh number pehle use ho chuka hai, skip karo
            if (used_in_this_level.count(nums[i])) {
                continue;
            }
            
            // Number ko use karo
            used_in_this_level.insert(nums[i]);
            current.push_back(nums[i]);
            find(nums, i + 1, current);
            current.pop_back(); // Backtrack
        }
    }

public:
    vector<vector<int>> findSubsequences(vector<int>& nums) {
        vector<int> current;
        find(nums, 0, current);
        return result;
    }
};

/*
Time Complexity: O(2^n * n)
Worst-case complexity same rehti hai kyunki humein saare subsequences
generate karne hi padte hain, lekin yeh pruning ke kaaran average case mein
kaafi faster chalta hai.

Space Complexity: O(n * 2^n)
Result ko store karne ke liye. Recursion stack ki depth O(n) hogi.
*/
```

----


