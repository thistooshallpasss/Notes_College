### **8. Kth Largest Element in BST**

**Q: BST mein Kth Largest Element find karne ka problem, example, approach aur C++ code do.**

**A:**

  * **Problem Statement:** Ek Binary Search Tree (BST) aur ek integer `k` diya hai. Aapko BST mein `k`-th largest element find karna hai.

  * **Example:**

      * **Input:** `root = [5,3,6,2,4,null,7]`, `k = 3`
      * **Output:** `5` (Largest is 7, 2nd largest is 6, 3rd largest is 5).

  * **Approach:** Hum **Reverse Inorder Traversal** (Right -\> Root -\> Left) ka use karenge, kyunki yeh elements ko descending order mein visit karta hai. Ek counter `k` ko maintain karenge. Har node ko visit karne par `k` ko decrement karenge. Jab `k` zero ho jaayega, wohi node hamara answer hoga.

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    struct TreeNode {
        int val;
        TreeNode *left;
        TreeNode *right;
        TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
    };

    void findKthLargest(TreeNode* root, int& k, int& result) {
        if (root == nullptr || k <= 0) return;
        
        findKthLargest(root->right, k, result);
        
        k--;
        if (k == 0) {
            result = root->val;
            return;
        }
        
        findKthLargest(root->left, k, result);
    }

    int kthLargest(TreeNode* root, int k) {
        // TC: O(n), SC: O(Height)
        int result = -1;
        findKthLargest(root, k, result);
        return result;
    }
    ```

-----


### **10. Longest Valid Parentheses**

**Q: Longest Valid Parentheses ka problem, example, approach aur C++ code do.**

**A:**

  * **Problem Statement:** Ek string di hai jismein sirf `(` aur `)` hain. Aapko sabse lambi valid (well-formed) parentheses substring ki length find karni hai.

  * **Example:**

      * **Input:** `"(()"` -\> **Output:** `2` (Substring "()")
      * **Input:** `")()())"` -\> **Output:** `4` (Substring "()()")

  * **Approach:** Hum **Stack** ka use karenge, lekin is baar hum indices store karenge.

    1.  Stack mein shuru mein `-1` push karo jo base ka kaam karega.
    2.  String ko traverse karo. Agar `(` aata hai, to uska index push karo.
    3.  Agar `)` aata hai, to stack se pop karo.
    4.  Pop karne ke baad, agar stack empty nahi hai, to current index aur stack ke top index ka difference nikal kar `max_len` ko update karo. Agar stack empty ho jaata hai, to current index ko push kar do naya base banane ke liye.

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    int longestValidParentheses(string s) {
        // TC: O(n), SC: O(n)
        stack<int> st;
        st.push(-1);
        int max_len = 0;
        for (int i = 0; i < s.length(); i++) {
            if (s[i] == '(') {
                st.push(i);
            } else {
                st.pop();
                if (st.empty()) {
                    st.push(i);
                } else {
                    max_len = max(max_len, i - st.top());
                }
            }
        }
        return max_len;
    }
    ```
---
### **11. Possible Words From Phone Digits**

**Q: Phone keypad ke digits se possible words banane ka problem, example, approach aur C++ code do.**

**A:**

  * **Problem Statement:** Ek digits ki sequence di gayi hai (phone keypad waali). Aapko saare possible letter combinations batane hain jo woh number represent kar sakta hai.

  * **Example:**

      * **Input:** `"23"`
      * **Output:** `["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"]`

  * **Approach:** Hum **Backtracking (Recursion)** ka use karenge. Ek recursive function banayenge jo combination build karega. Har digit ke liye, uske corresponding saare characters par loop chalayenge, ek character ko current string mein add karke, aur agle digit ke liye function ko call karenge.

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    void solve(string digits, string output, int index, vector<string>& ans, const vector<string>& mapping) {
        if (index >= digits.length()) {
            ans.push_back(output);
            return;
        }
        int number = digits[index] - '0';
        string value = mapping[number];
        for (int i = 0; i < value.length(); i++) {
            output.push_back(value[i]);
            solve(digits, output, index + 1, ans, mapping);
            output.pop_back(); // Backtrack
        }
    }

    vector<string> letterCombinations(string digits) {
        // TC: O(4^N), SC: O(N) for recursion stack
        vector<string> ans;
        if (digits.length() == 0) return ans;
        string output = "";
        vector<string> mapping = {"", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};
        solve(digits, output, 0, ans, mapping);
        return ans;
    }
    ```

-----


### **18. LCA Of Binary Tree**

**Q: Binary Tree mein Lowest Common Ancestor (LCA) find karne ka problem, approach aur C++ code do.**

**A:**

  * **Problem Statement:** Ek binary tree aur uske do nodes `n1` aur `n2` diye gaye hain. Aapko unka **Lowest Common Ancestor** (sabse neeche wala common parent) find karna hai.

  * **Example:** Ek tree mein agar `n1` left subtree mein aur `n2` right subtree mein hai, to unka root hi LCA hoga.

  * **Approach:** Hum ek **single recursive traversal** ka use karenge.

    1.  Agar root `NULL` hai ya `n1` ya `n2` ke barabar hai, to `root` return karo.
    2.  Left aur right subtrees ke liye recursively call karo.
    3.  Agar left aur right dono calls se non-NULL result aata hai, to current root hi LCA hai.
    4.  Warna jo bhi non-NULL result hai, usse return karo.

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    struct TreeNode {
        int val;
        TreeNode *left, *right;
        TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
    };

    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        // TC: O(N), SC: O(Height)
        if (root == nullptr || root == p || root == q) {
            return root;
        }
        TreeNode* leftLCA = lowestCommonAncestor(root->left, p, q);
        TreeNode* rightLCA = lowestCommonAncestor(root->right, p, q);

        if (leftLCA != nullptr && rightLCA != nullptr) {
            return root;
        }
        return (leftLCA != nullptr) ? leftLCA : rightLCA;
    }
    ```

-----


### **24 Minimum Swaps to Sort**

**Q: Ek array ko sort karne ke liye minimum swaps find karne ka problem, approach, aur code do**

**A:**

  * **Problem Statement:** Ek array diya gaya hai Aapko minimum number of swaps batane hain jo is array ko sort karne ke liye lagenge

  * **Approach:** Hum is problem ko **Graph Cycles** ki tarah solve kar sakte hain
    1 Har element aur uske original index ka pair banayenge
    2 In pairs ko element ki value ke basis par sort karenge
    3 Ab, hum cycles find karenge Jo element apni correct sorted position par nahi hai, wahan se cycle trace karna shuru karenge
    4 Total swaps = `(Array Size) - (Number of Cycles)`

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    int minSwaps(vector<int>& arr) {
        // TC: O(n log n), SC: O(n)
        int n = arr.size();
        vector<pair<int, int>> pos(n);
        for (int i = 0; i < n; i++) {
            pos[i] = {arr[i], i};
        }
        sort(pos.begin(), pos.end());
        vector<bool> visited(n, false);
        int swaps = 0;
        for (int i = 0; i < n; i++) {
            if (visited[i] || pos[i].second == i) {
                continue;
            }
            int cycle_size = 0;
            int j = i;
            while (!visited[j]) {
                visited[j] = true;
                j = pos[j].second;
                cycle_size++;
            }
            if (cycle_size > 0) {
                swaps += (cycle_size - 1);
            }
        }
        return swaps;
    }
    ```

-----


### **36 LRU Cache**

**Q: LRU Cache design karne ka problem, approach, aur C++ code do**

**A:**

  * **Problem Statement:** Least Recently Used (LRU) Cache design karna hai jismein `get` aur `put` operations O(1) time mein hon

  * **Approach:** Hum **Hash Map** aur **Doubly Linked List** ka combination use karenge

      * **Hash Map:** `key` ko Doubly Linked List ke `node address` se map karega Taaki `get` O(1) mein ho
      * **Doubly Linked List:** Nodes ko usage ke order mein rakhega Jo node sabse recently use hua hai, woh head par hoga, aur least recently used tail par
      * **`get(key)`:** Map se node find karke, usse list se hatakar head par move kar do
      * **`put(key, value)`:** Agar key exist karta hai, to value update karke node ko head par move kar do Agar nahi, to naya node banakar head par add karo Agar capacity full ho gayi hai, to tail se node remove kar do

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    class LRUCache {
        // TC: O(1) for get and put, SC: O(capacity)
        int capacity;
        list<pair<int, int>> items; // {key, value}
        unordered_map<int, list<pair<int, int>>::iterator> cache;
    public:
        LRUCache(int cap) : capacity(cap) {}

        int get(int key) {
            if (cache.find(key) == cache.end()) return -1;
            items.splice(items.begin(), items, cache[key]);
            return cache[key]->second;
        }

        void put(int key, int value) {
            if (cache.find(key) != cache.end()) {
                items.splice(items.begin(), items, cache[key]);
                cache[key]->second = value;
                return;
            }
            if (cache.size() == capacity) {
                int key_to_del = items.back().first;
                items.pop_back();
                cache.erase(key_to_del);
            }
            items.emplace_front(key, value);
            cache[key] = items.begin();
        }
    };
    ```

-----

### **39 Alien Dictionary**

**Q: Alien Dictionary problem ka approach aur C++ code do**

**A:**

  * **Problem Statement:** Ek alien language ke sorted dictionary ke words diye gaye hain Aapko us language ke characters ka order find karna hai

  * **Approach:** Yeh **Topological Sort** ka application hai
    1 Pehle hum words se ek character dependency graph banayenge Dictionary mein consecutive words ko compare karke pehla mismatching character humein ek edge dega (e g , "baa", "abcd" -\> `b` -\> `a`)
    2 Is graph par Topological Sort apply karenge jo humein characters ka correct order dega

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    // (Uses the topologicalSort function from the previous question)
    string findOrder(string dict[], int N, int K) {
        vector<int> adj[K];
        for(int i=0; i<N-1; i++) {
            string s1 = dict[i];
            string s2 = dict[i+1];
            for(int j=0; j<min(s1.length(), s2.length()); j++) {
                if(s1[j] != s2[j]) {
                    adj[s1[j]-'a'].push_back(s2[j]-'a');
                    break;
                }
            }
        }
        vector<int> topo = topologicalSort(K, adj);
        string ans = "";
        for(int it : topo) ans += char(it + 'a');
        return ans;
    }
    ```

-----

### **40 Burning Tree**

**Q: Burning Tree problem ka approach aur C++ code do**

**A:**

  * **Problem Statement:** Ek binary tree aur ek target node diya hai Agar aag target node se shuru ho, to poore tree ko jalne mein kitna minimum time lagega Aag har second mein adjacent nodes (parent, children) tak failti hai

  * **Approach:**
    1 Pehle hum parent pointers ka ek map banayenge aur target node ka address find karenge
    2 Phir, hum target node se **BFS** start karenge Queue mein hum `(node, time)` store karenge
    3 Har step mein, hum node ke children aur parent (jo visited na ho) ko queue mein `time+1` ke saath daal denge
    4 BFS ke dauran jo maximum time record hoga, wahi hamara answer hai

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    struct Node { int data; Node *left, *right; };

    Node* createParentMapping(Node* root, int target, map<Node*, Node*>& nodeToParent) {
        Node* res = NULL;
        queue<Node*> q;
        q.push(root);
        nodeToParent[root] = NULL;
        while(!q.empty()) {
            Node* front = q.front();
            q.pop();
            if(front->data == target) res = front;
            if(front->left) {
                nodeToParent[front->left] = front;
                q.push(front->left);
            }
            if(front->right) {
                nodeToParent[front->right] = front;
                q.push(front->right);
            }
        }
        return res;
    }

    int burnTree(Node* root, int target) {
        // TC: O(N), SC: O(N)
        map<Node*, Node*> nodeToParent;
        Node* targetNode = createParentMapping(root, target, nodeToParent);
        map<Node*, bool> visited;
        queue<Node*> q;
        q.push(targetNode);
        visited[targetNode] = true;
        int time = 0;
        while(!q.empty()) {
            bool flag = false;
            int size = q.size();
            for(int i=0; i<size; i++) {
                Node* front = q.front(); q.pop();
                if(front->left && !visited[front->left]) {
                    flag = true; visited[front->left] = true; q.push(front->left);
                }
                if(front->right && !visited[front->right]) {
                    flag = true; visited[front->right] = true; q.push(front->right);
                }
                if(nodeToParent[front] && !visited[nodeToParent[front]]) {
                    flag = true; visited[nodeToParent[front]] = true; q.push(nodeToParent[front]);
                }
            }
            if(flag) time++;
        }
        return time;
    }
    ```

---


## **41 Number of Distinct Islands**

**Q: Number of Distinct Islands problem ka statement, example, approach, aur C++ code do**

**A:**

  * **Problem Statement:** Aapko ek 2D grid di gayi hai jismein '1' (land) aur '0' (water) hain Aapko unique-shaped islands ka count batana hai

  * **Example:**

      * **Input:** `[[1,1,0], [0,1,1], [0,0,0], [1,1,0]]`
      * **Output:** `2` (Pehle do islands ka shape L-shape hai, but rotated hai, to unhe alag maana ja sakta hai Is problem mein translation-invariant shape count karna hai)

  * **Approach:** Hum **DFS** ka use karke har island ko find karenge Jab hum ek island ko traverse karte hain, hum uske shape ko starting cell ke relative coordinates ke roop mein store karte hain (e g , `(row - start_row, col - start_col)`) In unique shapes (jo vector of pairs honge) ko ek **Set** mein daal denge Aakhir mein, set ka size hi hamara answer hoga

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    void dfs(int r, int c, int r0, int c0, vector<vector<int>>& grid, vector<pair<int, int>>& shape) {
        if (r<0 || c<0 || r>=grid.size() || c>=grid[0].size() || grid[r][c]==0) return;
        
        grid[r][c] = 0; // Mark as visited
        shape.push_back({r - r0, c - c0});
        
        dfs(r+1, c, r0, c0, grid, shape);
        dfs(r-1, c, r0, c0, grid, shape);
        dfs(r, c+1, r0, c0, grid, shape);
        dfs(r, c-1, r0, c0, grid, shape);
    }

    int countDistinctIslands(vector<vector<int>>& grid) {
        // TC: O(m*n), SC: O(m*n)
        if (grid.empty()) return 0;
        set<vector<pair<int, int>>> unique_shapes;
        for (int i = 0; i < grid.size(); i++) {
            for (int j = 0; j < grid[0].size(); j++) {
                if (grid[i][j] == 1) {
                    vector<pair<int, int>> shape;
                    dfs(i, j, i, j, grid, shape);
                    sort(shape.begin(), shape.end()); // Canonical representation
                    unique_shapes.insert(shape);
                }
            }
        }
        return unique_shapes.size();
    }
    ```

-----

## **42 Edit Distance**

**Q: Edit Distance problem ka statement, approach, aur C++ code do**

**A:**

  * **Problem Statement:** Do strings `word1` aur `word2` di gayi hain Aapko minimum operations (insert, delete, ya replace) batane hain jo `word1` ko `word2` mein badalne ke liye zaroori hain

  * **Approach:** Yeh ek classic **Dynamic Programming** problem hai Hum ek 2D `dp` table banayenge jahan `dp[i][j]` `word1` ke shuru ke `i` characters ko `word2` ke shuru ke `j` characters mein badalne ka minimum cost store karega

      * Agar `word1[i-1] == word2[j-1]` hai, to koi operation nahi lagega: `dp[i][j] = dp[i-1][j-1]`
      * Agar alag hain, to hum insert, delete, ya replace mein se minimum cost lenge: `dp[i][j] = 1 + min({dp[i-1][j], dp[i][j-1], dp[i-1][j-1]})`

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    int minDistance(string word1, string word2) {
        // TC: O(m*n), SC: O(m*n)
        int m = word1.length(), n = word2.length();
        vector<vector<int>> dp(m + 1, vector<int>(n + 1));

        for (int i = 0; i <= m; i++) dp[i][0] = i;
        for (int j = 0; j <= n; j++) dp[0][j] = j;

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (word1[i - 1] == word2[j - 1]) {
                    dp[i][j] = dp[i - 1][j - 1];
                } else {
                    dp[i][j] = 1 + min({dp[i - 1][j], dp[i][j - 1], dp[i - 1][j - 1]});
                }
            }
        }
        return dp[m][n];
    }
    ```

-----

## **43 Bridges In A Graph**

**Q: Graph mein Bridges find karne ka problem, approach, aur code do**

**A:**

  * **Problem Statement:** Ek undirected graph diya hai Aapko saari **bridges** find karni hain Bridge ek aisi edge hoti hai jisko hatane se graph disconnected ho jaata hai

  * **Approach:** Hum **Tarjan's Bridge-Finding Algorithm** ka use karenge jo DFS par based hai Hum har node ke liye do values track karte hain: `discovery_time` (jab node pehli baar visit hua) aur `low_link_value` (sabse purana ancestor jo back-edge se pahuncha ja sake) Ek edge `u-v` bridge tab hoti hai jab `low_link_value[v] > discovery_time[u]`

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    void findBridges(int u, int parent, int& timer, vector<int>& disc, vector<int>& low, 
                     vector<vector<int>>& adj, vector<vector<int>>& bridges) {
        disc[u] = low[u] = timer++;
        for (int v : adj[u]) {
            if (v == parent) continue;
            if (disc[v] != -1) { // Back-edge
                low[u] = min(low[u], disc[v]);
            } else { // Forward-edge
                findBridges(v, u, timer, disc, low, adj, bridges);
                low[u] = min(low[u], low[v]);
                if (low[v] > disc[u]) {
                    bridges.push_back({u, v});
                }
            }
        }
    }

    vector<vector<int>> criticalConnections(int n, vector<vector<int>>& connections) {
        // TC: O(V+E), SC: O(V)
        vector<vector<int>> adj(n);
        for(auto& conn : connections) {
            adj[conn[0]].push_back(conn[1]);
            adj[conn[1]].push_back(conn[0]);
        }
        vector<int> disc(n, -1), low(n, -1);
        vector<vector<int>> bridges;
        int timer = 0;
        findBridges(0, -1, timer, disc, low, adj, bridges);
        return bridges;
    }
    ```

-----

## **44 Phone directory**

**Q: Phone directory problem ka statement, approach, aur code do**

**A:**

  * **Problem Statement:** Contacts ki ek list aur ek query string di hai Query ke har prefix ke liye, woh saare contacts return karne hain jo uss prefix se shuru hote hain

  * **Approach:** Iske liye sabse best data structure **Trie** hai
    1 Saare contacts ko Trie mein insert kar do Har Trie node mein ek list/vector rakho jo uss node tak aane wale saare contacts ko store kare
    2 Query string par character by character traverse karo aur Trie mein neeche jaate jao Har step par, current node par jo contacts ki list hai, wahi uss prefix ka result hoga

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    struct TrieNode {
        TrieNode* children[26];
        vector<string> common_prefix_words;
    };

    void insert(TrieNode* root, string key) {
        TrieNode* curr = root;
        for (char ch : key) {
            int index = ch - 'a';
            if (!curr->children[index]) curr->children[index] = new TrieNode();
            curr = curr->children[index];
            curr->common_prefix_words.push_back(key);
        }
    }

    vector<vector<string>> phoneDirectory(vector<string>& contacts, string query) {
        // TC: O(N*L + Q*L), SC: O(N*L)
        TrieNode* root = new TrieNode();
        for (string& contact : contacts) insert(root, contact);
        
        vector<vector<string>> result;
        TrieNode* curr = root;
        for (char ch : query) {
            int index = ch - 'a';
            if (curr && curr->children[index]) {
                curr = curr->children[index];
                result.push_back(curr->common_prefix_words);
            } else {
                curr = nullptr;
                result.push_back({"0"}); // No contact found
            }
        }
        return result;
    }
    ```

-----

## **45 Minimum Cost Path**

**Q: Grid mein Minimum Cost Path find karne ka problem, approach, aur code do**

**A:**

  * **Problem Statement:** Ek 2D grid di hai jismein har cell ka ek cost hai Aapko top-left (`[0][0]`) se bottom-right (`[m-1][n-1]`) tak jaane ka minimum cost path find karna hai Aap sirf right ya down move kar sakte hain

  * **Approach:** Hum **Dynamic Programming** ka use karenge Ek `dp[m][n]` table banayenge jahan `dp[i][j]` `[0][0]` se `[i][j]` tak pahunchne ka minimum cost store karega

      * Recurrence relation: `dp[i][j] = grid[i][j] + min(dp[i-1][j], dp[i][j-1])`

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    int minPathSum(vector<vector<int>>& grid) {
        // TC: O(m*n), SC: O(1) by modifying grid in-place
        int m = grid.size(), n = grid[0].size();
        for (int i = 1; i < m; i++) grid[i][0] += grid[i - 1][0];
        for (int j = 1; j < n; j++) grid[0][j] += grid[0][j - 1];

        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                grid[i][j] += min(grid[i - 1][j], grid[i][j - 1]);
            }
        }
        return grid[m - 1][n - 1];
    }
    ```

-----

## **46 Overlapping Intervals**

**Q: Overlapping Intervals ko merge karne ka problem, approach, aur code do**

**A:**

  * **Problem Statement:** Intervals ka ek collection diya hai Aapko saare overlapping intervals ko merge karke naya collection of intervals banana hai

  * **Approach:**
    1 Sabse pehle saare intervals ko unke **start time** ke basis par sort kar lo
    2 Ek `result` vector lo aur usmein pehla interval daal do
    3 Baaki intervals par iterate karo Agar current interval `result` ke last interval se overlap karta hai ( `current.start <= result.back.end` ), to `result` ke last interval ka `end` update kar do (`max(result.back.end, current.end)`)
    4 Agar overlap nahi karta, to current interval ko `result` mein push kar do

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        // TC: O(n log n), SC: O(n) or O(1) depending on result storage
        if (intervals.empty()) return {};
        sort(intervals.begin(), intervals.end());
        vector<vector<int>> merged;
        merged.push_back(intervals[0]);
        for (int i = 1; i < intervals.size(); i++) {
            if (intervals[i][0] <= merged.back()[1]) {
                merged.back()[1] = max(merged.back()[1], intervals[i][1]);
            } else {
                merged.push_back(intervals[i]);
            }
        }
        return merged;
    }
    ```

-----

## **47 Diameter of a Binary Tree**

**Q: Binary Tree ka diameter nikalne ka problem, approach, aur code do**

**A:**

  * **Problem Statement:** Ek binary tree ka diameter nikalna hai Diameter tree mein किन्हीं do nodes ke beech sabse lamba path hota hai

  * **Approach:** Hum **DFS/Recursion** ka use karenge Ek helper function banayenge jo har node ke liye uske subtree ki height return karega Saath hi, ek variable (reference ya global) `diameter` ko har node par update karte jayenge `diameter = max(diameter, left_height + right_height)`

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    struct TreeNode { int val; TreeNode *left, *right; };

    int height(TreeNode* node, int& diameter) {
        if (!node) return 0;
        int lh = height(node->left, diameter);
        int rh = height(node->right, diameter);
        diameter = max(diameter, lh + rh);
        return 1 + max(lh, rh);
    }

    int diameterOfBinaryTree(TreeNode* root) {
        // TC: O(N), SC: O(Height)
        int diameter = 0;
        height(root, diameter);
        return diameter;
    }
    ```

-----

## **48 Stock buy and sell**

**Q: Stock buy and sell (multiple transactions) ka problem, approach, aur code do**

**A:**

  * **Problem Statement:** Ek array diya hai jahan `prices[i]` i-th day ka stock price hai Aap multiple times stock khareed aur bech sakte hain, lekin ek time par ek hi stock hold kar sakte hain Maximum profit nikalna hai

  * **Approach:** Yeh ek **Greedy** problem hai Hum bas har us din profit book karenge jab price pichle din se zyada ho Iska matlab hai, hum saare upward slopes ka sum le rahe hain Jab bhi `prices[i] > prices[i-1]` ho, to `prices[i] - prices[i-1]` ko total profit mein add kar do

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    int maxProfit(vector<int>& prices) {
        // TC: O(N), SC: O(1)
        int profit = 0;
        for (int i = 1; i < prices.size(); i++) {
            if (prices[i] > prices[i-1]) {
                profit += prices[i] - prices[i-1];
            }
        }
        return profit;
    }
    ```

-----

## **49 Spirally traversing a matrix**

**Q: Matrix ko spirally traverse karne ka problem, approach, aur code do**

**A:**

  * **Problem Statement:** Ek `m x n` matrix di gayi hai Aapko uske saare elements ko spiral order mein print karna hai

  * **Approach:** Hum **char pointers** (`top`, `bottom`, `left`, `right`) ka use karke matrix ki boundaries ko shrink karenge
    1 Pehle `left` se `right` tak top row traverse karo
    2 Phir `top` se `bottom` tak right column traverse karo
    3 Phir `right` se `left` tak bottom row traverse करो
    4 Phir `bottom` se `top` tak left column traverse karo
    Yeh process tab tak repeat karo jab tak saare elements cover na ho jayein

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    vector<int> spirallyTraverse(vector<vector<int>>& matrix) {
        // TC: O(m*n), SC: O(1) (excluding result)
        if (matrix.empty()) return {};
        int m = matrix.size(), n = matrix[0].size();
        int top = 0, bottom = m - 1, left = 0, right = n - 1;
        vector<int> result;
        while (top <= bottom && left <= right) {
            for (int i = left; i <= right; i++) result.push_back(matrix[top][i]);
            top++;
            for (int i = top; i <= bottom; i++) result.push_back(matrix[i][right]);
            right--;
            if (top <= bottom) {
                for (int i = right; i >= left; i--) result.push_back(matrix[bottom][i]);
                bottom--;
            }
            if (left <= right) {
                for (int i = bottom; i >= top; i--) result.push_back(matrix[i][left]);
                left++;
            }
        }
        return result;
    }
    ```

-----

## **50 Longest Subsequence With Difference One**

**Q: Longest Subsequence With Difference One ka problem, approach, aur code do**

**A:**

  * **Problem Statement:** Ek array diya hai Aapko longest subsequence ki length batani hai jiske adjacent elements ka absolute difference 1 ho

  * **Approach:** Hum **Dynamic Programming** ka use karenge Ek **hash map** `dp` lenge jahan `dp[x]` number `x` par khatam hone wali longest subsequence ki length store karega Array ke har element `num` ke liye, `dp[num] = 1 + dp[num - 1]` se update karenge Overall maximum length ko track karte rahenge

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    int longestSubsequence(vector<int>& arr) {
        // TC: O(N), SC: O(N)
        unordered_map<int, int> dp;
        int maxLen = 0;
        for (int num : arr) {
            // Considering both num-1 and num+1
            int len1 = dp.count(num - 1) ? dp[num - 1] : 0;
            int len2 = dp.count(num + 1) ? dp[num + 1] : 0;
            dp[num] = 1 + max(len1, len2);
            maxLen = max(maxLen, dp[num]);
        }
        return maxLen;
    }
    ```

-----

## **51 Bipartite Graph**

**Q: Bipartite Graph check karne ka problem, approach, aur C++ code do**

**A:**

  * **Problem Statement:** Ek graph diya hai, aapko check karna hai ki kya woh Bipartite hai (kya uske vertices ko do alag sets mein is tarah baanta ja sakta hai ki koi bhi edge same set ke do vertices ko connect na kare)

  * **Approach:** Hum **Graph Coloring (BFS)** ka use karenge Hum do colors (`1` aur `-1`) use karenge
    1 Kisi bhi uncolored node se BFS shuru karo aur use color `1` do
    2 Jab bhi kisi node se uske uncolored neighbor par jao, to use opposite color do
    3 Agar kabhi aisa neighbor milta hai jo pehle se colored hai aur uska color current node jaisa hi hai, to graph Bipartite nahi hai
    4 Agar poora traversal bina conflict ke ho jata hai, to graph Bipartite hai

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    bool isBipartite(int V, vector<vector<int>>& adj) {
        // TC: O(V+E), SC: O(V)
        vector<int> color(V, 0); // 0: uncolored, 1: color1, -1: color2
        for (int i = 0; i < V; i++) {
            if (color[i] == 0) {
                queue<int> q;
                q.push(i);
                color[i] = 1;
                while (!q.empty()) {
                    int u = q.front(); q.pop();
                    for (int v : adj[u]) {
                        if (color[v] == 0) {
                            color[v] = -color[u];
                            q.push(v);
                        } else if (color[v] == color[u]) {
                            return false;
                        }
                    }
                }
            }
        }
        return true;
    }
    ```

-----

## **52 Palindrome Partitioning**

**Q: Palindrome Partitioning ka problem, approach, aur code do**

**A:**

  * **Problem Statement:** Ek string `s` di hai, use is tarah partition karna hai ki har part ek palindrome ho Aise saare possible partitions batane hain

  * **Approach:** Hum **Backtracking** ka use karenge
    1 Ek recursive function banayenge jo current index se aage ke partitions dhoondhega
    2 Function mein, `index` se `i` tak ke substrings par loop chalayenge
    3 Agar substring `s[index...i]` palindrome hai, to use current path mein add karke `i+1` se aage ke liye recursively call karenge
    4 Call ke baad, backtrack karenge (substring ko path se hata denge)

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    bool isPalindrome(const string& s, int start, int end) {
        while(start <= end) if(s[start++] != s[end--]) return false;
        return true;
    }

    void findPartitions(int index, string& s, vector<string>& path, vector<vector<string>>& result) {
        if (index == s.size()) {
            result.push_back(path);
            return;
        }
        for (int i = index; i < s.size(); ++i) {
            if (isPalindrome(s, index, i)) {
                path.push_back(s.substr(index, i - index + 1));
                findPartitions(i + 1, s, path, result);
                path.pop_back(); // Backtrack
            }
        }
    }

    vector<vector<string>> partition(string s) {
        // TC: O(N * 2^N), SC: O(N)
        vector<vector<string>> result;
        vector<string> path;
        findPartitions(0, s, path, result);
        return result;
    }
    ```

-----

## **53 Reverse Stack**

**Q: Stack ko reverse karne ka problem (bina extra space), approach, aur code do**

**A:**

  * **Problem Statement:** Ek stack ko reverse karna hai, lekin aap koi loop ya extra data structure (jaise doosra stack) use nahi kar sakte Sirf recursion allowed hai

  * **Approach:** Hum **Recursion** ka use karenge
    1 **`reverse(stack)`:** Yeh function stack ke top element ko nikalega, baaki stack ko recursively reverse karega, aur phir nikale gaye element ko stack ke **bottom** mein insert kar dega
    2 **`insertAtBottom(stack, item)`:** Yeh helper function item ko stack ke bottom mein daalta hai Yeh bhi recursive hai

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    void insertAtBottom(stack<int>& st, int item) {
        if (st.empty()) {
            st.push(item);
            return;
        }
        int top = st.top();
        st.pop();
        insertAtBottom(st, item);
        st.push(top);
    }

    void reverseStack(stack<int>& st) {
        // TC: O(N^2), SC: O(N) for recursion stack
        if (!st.empty()) {
            int top = st.top();
            st.pop();
            reverseStack(st);
            insertAtBottom(st, top);
        }
    }
    ```

-----

## **54 MergeSort Linked List**

**Q: Linked List par Merge Sort lagane ka problem, approach, aur code do**

**A:**

  * **Problem Statement:** Ek linked list di hai, use Merge Sort ka use karke sort karna hai

  * **Approach:**
    1 **Find Middle:** Pehle list ka middle find karenge (Slow and Fast Pointer se)
    2 **Divide:** List ko middle se do alag lists mein tod denge
    3 **Recur:** Dono halves par recursively `mergeSort` call karenge
    4 **Merge:** Dono sorted halves ko merge karke ek single sorted list banayenge

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    struct ListNode { int val; ListNode *next; };

    ListNode* merge(ListNode* l1, ListNode* l2) {
        ListNode dummy(0);
        ListNode* tail = &dummy;
        while (l1 && l2) {
            if (l1->val < l2->val) { tail->next = l1; l1 = l1->next; }
            else { tail->next = l2; l2 = l2->next; }
            tail = tail->next;
        }
        tail->next = l1 ? l1 : l2;
        return dummy.next;
    }

    ListNode* sortList(ListNode* head) {
        // TC: O(N log N), SC: O(log N)
        if (!head || !head->next) return head;
        ListNode *slow = head, *fast = head, *prev = nullptr;
        while (fast && fast->next) {
            prev = slow;
            slow = slow->next;
            fast = fast->next->next;
        }
        prev->next = nullptr; // Split the list
        ListNode* l1 = sortList(head);
        ListNode* l2 = sortList(slow);
        return merge(l1, l2);
    }
    ```

-----

## **55 Count Distinct Elements In Every Window**

**Q: Har window mein distinct elements count karne ka problem, approach, aur code do**

**A:**

  * **Problem Statement:** Ek array aur ek window size `k` diya hai Aapko har `k` size ki window mein distinct (unique) elements ka count batana hai

  * **Approach:** Hum **Sliding Window with a Hash Map** ka use karenge
    1 Pehli `k` size ki window ke elements ki frequency ko hash map mein store karo Map ka size pehli window ka answer hoga
    2 Phir window ko ek-ek karke slide karo
    \* Window se nikalne wale element ki frequency map mein kam karo (agar 0 ho jaye to map se hata do)
    \* Window mein aane wale naye element ki frequency badha do
    3 Har step par map ka size hi uss window ka answer hoga

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    vector<int> countDistinct(vector<int>& arr, int k) {
        // TC: O(N), SC: O(K)
        vector<int> result;
        unordered_map<int, int> freq;
        for (int i = 0; i < k; i++) freq[arr[i]]++;
        result.push_back(freq.size());
        
        for (int i = k; i < arr.size(); i++) {
            freq[arr[i-k]]--;
            if (freq[arr[i-k]] == 0) freq.erase(arr[i-k]);
            freq[arr[i]]++;
            result.push_back(freq.size());
        }
        return result;
    }
    ```

-----

## **56 Alternate Print**

**Q: Do threads se alternately numbers print karne ka problem, approach, aur code do**

**A:**

  * **Problem Statement:** Do threads ka use karke 1 se N tak numbers print karne hain, jahan ek thread saare odd numbers print kare aur doosra saare even numbers, in sequence

  * **Approach:** Hum **Mutex** aur **Condition Variables** ka use karke threads ko synchronize karenge

      * Ek shared counter, ek mutex, aur do condition variables (`cond_odd`, `cond_even`) lenge
      * **Odd Thread:** Lock karke check karega ki kya counter odd hai Agar nahi, to `cond_odd` par wait karega Print karne ke baad, counter badha kar `cond_even` ko notify karega
      * **Even Thread:** Lock karke check karega ki kya counter even hai Agar nahi, to `cond_even` par wait karega Print karne ke baad, counter badha kar `cond_odd` ko notify karega

  * **C++ Code:**

    ```cpp
    #include <iostream>
    #include <thread>
    #include <mutex>
    #include <condition_variable>
    using namespace std;

    mutex mtx;
    condition_variable cv;
    int counter = 1;

    void printNumbers(int limit, bool is_even) {
        while (counter <= limit) {
            unique_lock<mutex> lock(mtx);
            cv.wait(lock, [is_even] { return (counter % 2 == (is_even ? 0 : 1)) || counter > 10; });
            if (counter > limit) break;
            cout << "Thread " << (is_even ? 2 : 1) << ": " << counter++ << endl;
            lock.unlock();
            cv.notify_all();
        }
    }
    // To run:
    // int main() {
    //     thread t1(printNumbers, 10, false);
    //     thread t2(printNumbers, 10, true);
    //     t1.join();
    //     t2.join();
    //     return 0;
    // }
    ```

-----

## **57 Job Sequencing Problem**

**Q: Job Sequencing Problem ka statement, approach, aur C++ code do**

**A:**

  * **Problem Statement:** `N` jobs di hain, har job ki ek deadline aur ek profit hai Har job ek unit time leti hai Maximum profit find karna hai

  * **Approach:** Yeh ek **Greedy** problem hai
    1 Saare jobs ko unke **profit** ke descending order mein sort kar lo
    2 Ek boolean `slot` array lo (size = max deadline) jo time slots ko track karega
    3 Sorted jobs par iterate karo Har job ke liye, uski deadline se neeche pehla available slot dhoondho (from `deadline-1` to `0`)
    4 Agar slot mil jaata hai, to job ko uss slot mein place karo, profit add karo, aur slot ko occupied mark kar do

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    struct Job { int id, dead, profit; };

    static bool comparison(Job a, Job b) { return (a.profit > b.profit); }

    pair<int, int> JobScheduling(Job arr[], int n) {
        // TC: O(N log N + N*M), SC: O(M) where M=max_deadline
        sort(arr, arr + n, comparison);
        int max_deadline = 0;
        for (int i = 0; i < n; i++) max_deadline = max(max_deadline, arr[i].dead);

        vector<int> slot(max_deadline + 1, -1);
        int count = 0, total_profit = 0;
        
        for (int i = 0; i < n; i++) {
            for (int j = arr[i].dead; j > 0; j--) {
                if (slot[j] == -1) {
                    slot[j] = i;
                    count++;
                    total_profit += arr[i].profit;
                    break;
                }
            }
        }
        return {count, total_profit};
    }
    ```

-----

## **58 Sliding Maximum**

**Q: Sliding Window Maximum ka problem, approach, aur C++ code do**

**A:**

  * **Problem Statement:** Ek array aur ek window size `k` diya hai Aapko har `k` size ki window ka maximum element find karna hai

  * **Approach:** Hum ek **Deque (Double-Ended Queue)** ka use karenge Deque mein hum window ke elements ke **indices** ko is tarah store karenge ki unke corresponding values decreasing order mein hon
    1 Window slide karte waqt, naye element ke liye, deque ke peeche se unn sabhi elements ko hata do jo naye element se chhote hain
    2 Naye element ka index peeche push karo
    3 Deque ke front se unn indices ko hatao jo ab window ka hissa nahi hain
    4 Har step par, deque ka front element hi uss window ka maximum hoga

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    vector<int> maxSlidingWindow(vector<int>& nums, int k) {
        // TC: O(N), SC: O(K)
        deque<int> dq;
        vector<int> result;
        for (int i = 0; i < nums.size(); i++) {
            if (!dq.empty() && dq.front() == i - k) {
                dq.pop_front();
            }
            while (!dq.empty() && nums[dq.back()] < nums[i]) {
                dq.pop_back();
            }
            dq.push_back(i);
            if (i >= k - 1) {
                result.push_back(nums[dq.front()]);
            }
        }
        return result;
    }
    ```

-----

## **59 Valid Perfect Square**

**Q: Valid Perfect Square check karne ka problem (bina sqrt), approach, aur code do**

**A:**

  * **Problem Statement:** Ek positive integer `num` diya hai Pata lagana hai ki kya woh ek perfect square hai, bina library function `sqrt` use kiye

  * **Approach:** Hum **Binary Search** ka use karenge Hum 1 se `num` ke beech mein uss number `x` ko dhoondhenge jiska square `num` ke barabar ho

      * `mid` nikalo Agar `mid*mid == num`, to `true`
      * Agar `mid*mid > num`, to search left half mein karo
      * Agar `mid*mid < num`, to search right half mein karo
      * Overflow se bachne ke liye `mid` ko `long long` lena zaroori hai

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    bool isPerfectSquare(int num) {
        // TC: O(log N), SC: O(1)
        if (num < 1) return false;
        long long low = 1, high = num;
        while (low <= high) {
            long long mid = low + (high - low) / 2;
            if (mid * mid == num) {
                return true;
            } else if (mid * mid < num) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        return false;
    }
    ```

-----

## **60 Trie**

**Q: Trie data structure ka implementation (insert, search, startsWith) do**

**A:**

  * **Problem Statement:** Ek Trie (Prefix Tree) data structure implement karo jismein `insert`, `search`, aur `startsWith` methods hon

  * **Approach:**

      * Ek `TrieNode` class banayenge jismein 26 children ke pointers aur ek `isEndOfWord` flag hoga
      * **`insert`:** Word ke har character ke liye, root se traverse karke naye nodes banate jayenge
      * **`search`:** Word ke har character ke liye traverse karenge aur aakhir mein `isEndOfWord` flag check karenge
      * **`startsWith`:** `search` jaisa hi hai, bas aakhir mein `isEndOfWord` flag check nahi karna padta

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    struct TrieNode {
        TrieNode* children[26];
        bool isEndOfWord;
        TrieNode() {
            isEndOfWord = false;
            for(int i=0; i<26; i++) children[i] = nullptr;
        }
    };

    class Trie {
        // TC: O(L) for all ops, SC: O(total chars)
        TrieNode* root;
    public:
        Trie() { root = new TrieNode(); }

        void insert(string word) {
            TrieNode* curr = root;
            for (char ch : word) {
                int index = ch - 'a';
                if (!curr->children[index]) curr->children[index] = new TrieNode();
                curr = curr->children[index];
            }
            curr->isEndOfWord = true;
        }

        bool search(string word) {
            TrieNode* curr = root;
            for (char ch : word) {
                int index = ch - 'a';
                if (!curr->children[index]) return false;
                curr = curr->children[index];
            }
            return curr != nullptr && curr->isEndOfWord;
        }

        bool startsWith(string prefix) {
            TrieNode* curr = root;
            for (char ch : prefix) {
                int index = ch - 'a';
                if (!curr->children[index]) return false;
                curr = curr->children[index];
            }
            return curr != nullptr;
        }
    };
    ```
    

---

---
### **Java & OOPS Concepts**

**Q: OOPS ke concepts kya hain?**
**A:** OOPS (Object-Oriented Programming System) ke **chaar main pillars** (concepts) hain:
1.  **Encapsulation** (एनकैप्सुलेशन)
2.  **Abstraction** (एब्स्ट्रैक्शन)
3.  **Inheritance** (इनहेरिटेंस)
4.  **Polymorphism** (पॉलीमॉरफिज़्म)

---
**Q: OOPS ke pillars ko real-life examples ke saath samjhaiye.**
**A:**
* **Encapsulation:** Iska matlab hai data (variables) aur uss data par kaam karne waale code (methods) ko ek saath ek single unit (class) mein baandh dena.
    * **Example:** Ek medical capsule, jiske andar dawai (data) surakshit hoti hai aur bahar se access nahi ki jaa sakti. Aap sirf capsule ko kha sakte hain (method use kar sakte hain), dawai ko direct nahi chhed sakte. Isse **data hiding** achieve hoti hai.

* **Abstraction:** Iska matlab hai user ko sirf zaroori jaankari dikhana aur internal complexity (details) ko chhupana.
    * **Example:** Jab aap TV ka remote use karte hain, to aap sirf volume ya channel change karne waale button (zaroori cheezein) dekhte hain. Remote ke andar ka circuit kaise kaam karta hai (complexity), woh aapse chhupa hota hai.

* **Inheritance:** Jab ek class (child class) doosri class (parent class) ki properties aur behavior ko haasil (inherit) karti hai. Isse **code reusability** badhti hai.
    * **Example:** Ek 'Beta' apne 'Pita' ke gun (properties) jaise surname aur zameen (assets) inherit karta hai.

* **Polymorphism:** Iska matlab hai "ek naam, kai kaam". Jab koi cheez (method ya object) alag-alag situations mein alag-alag tarah se behave karti hai.
    * **Example:** Aapka smartphone. Hai to ek hi object, lekin aap usse call kar sakte hain, photo kheench sakte hain, aur game bhi khel sakte hain. Object ek, kaam anek. Iske do types hain: **Method Overloading** aur **Method Overriding**.

---
**Q: Abstract class aur Interface mein kya difference hai?**
**A:**

| Feature         | Abstract Class                                                                              | Interface                                                                                                             |
| :-------------- | :------------------------------------------------------------------------------------------ | :-------------------------------------------------------------------------------------------------------------------- |
| **Methods**     | Ismein abstract (bina body ke) aur non-abstract (body ke saath) dono methods ho sakte hain. | Java 8 se pehle, sirf abstract methods hote the. Ab `default` aur `static` methods (body ke saath) bhi ho sakte hain. |
| **Variables**   | Ismein `final`, `non-final`, `static`, `non-static` sabhi tarah ke variables ho sakte hain. | Iske saare variables by default `public`, `static`, aur `final` hote hain.                                            |
| **Inheritance** | Ek class sirf **ek** abstract class ko `extend` kar sakti hai.                              | Ek class **kai** interfaces ko `implement` kar sakti hai.                                                             |
| **Constructor** | Iska constructor hota hai.                                                                  | Iska constructor nahi hota.                                                                                           |

---
**Q: Method Overriding aur Method Overloading kya hai?**
**A:**
* **Method Overloading (Compile-time Polymorphism):** Jab ek hi class mein, **same naam ke kai methods** hote hain, lekin unke **parameters** (arguments) alag hote hain (ya to number of parameters alag ho, ya unka data type alag ho).
    * **Example:** `add(int a, int b)` aur `add(int a, int b, int c)`.

* **Method Overriding (Run-time Polymorphism):** Jab ek **child class** apne **parent class** ke method ko wapas se apni zaroorat ke hisaab se define karti hai. Method ka naam aur parameters same rehte hain. Yeh **inheritance** mein hota hai.
    * **Example:** `Animal` class ka `makeSound()` method hai. `Dog` class usse override karke "Barks" print karegi aur `Cat` class "Meows" print karegi.

---
**Q: Kya hum static method ko override kar sakte hain?**
**A:** **Nahi.** Hum static method ko override nahi kar sakte. Static methods class se jude hote hain, object se nahi. Agar aap child class mein same naam ka static method banate bhi hain, to use **Method Hiding** kehte hain, overriding nahi.

---
**Q: Java mein `final` keyword kya hai?**
**A:** `final` keyword kisi bhi cheez ko **constant** ya **aprivartansheel** (non-changeable) banane ke liye use hota hai.
* **`final` variable:** Uski value ko dobara assign nahi kar sakte.
* **`final` method:** Usko child class mein override nahi kar sakte.
* **`final` class:** Usko koi doosri class inherit (extend) nahi kar sakti.

---
**Q: `static` keyword ko samjhaiye.**
**A:** `static` keyword ka matlab hai ki woh cheez (variable ya method) class se belong karti hai, na ki uske alag-alag objects se.
* **`static` variable:** Iski ek hi copy banti hai jo uss class ke saare objects ke beech **shared** hoti hai.
* **`static` method:** Isse bina object banaye, seedhe class ke naam se call kar sakte hain (jaise `Math.random()`). Yeh sirf static data ko hi access kar sakta hai.

---
**Q: `==` aur `.equals()` method mein kya difference hai?**
**A:**
* **`==` (Operator):** Yeh **reference** ko compare karta hai. Yeh check karta hai ki kya do variables memory mein **same object** ko point kar rahe hain. Primitive types (like `int`, `char`) ke liye yeh value compare karta hai.
* **`.equals()` (Method):** Yeh **content** (value) ko compare karta hai. `String` jaisi classes mein yeh method check karta hai ki kya dono objects ke andar ka content same hai, bhale hi woh memory mein alag-alag jagah par hon.

---
**Q: Functional interfaces, lambda expressions, aur Stream API ko samjhaiye.**
**A:** Yeh sab **Java 8** ke powerful features hain:
* **Functional Interface:** Ek aisa interface jismein sirf **ek abstract method** ho. Jaise `Runnable`.
* **Lambda Expression:** Yeh ek **bina naam ka function** hota hai jo functional interface ke method ko chote aur saaf tareeke se implementation deta hai. Isse code bahut concise ho jaata hai. Syntax: `(parameter) -> { body }`.
* **Stream API:** Yeh collections (jaise `List`, `Set`) par bulk operations (jaise filtering, mapping, sorting) karne ka ek naya aur declarative tareeka hai. Isse aap data ko ek stream ki tarah process kar sakte hain.

---
**Q: `ArrayList` aur `LinkedList` mein kya difference hai?**
**A:**
* **ArrayList:**
    * Internally **dynamic array** use karta hai.
    * Kisi bhi element ko **get karna (access karna) fast** hota hai (O(1)).
    * Beech mein se element **add ya remove karna slow** hota hai (O(n)) kyunki baaki elements ko shift karna padta hai.

* **LinkedList:**
    * Internally **doubly linked list** use karta hai (har node agle aur pichle node se juda hota hai).
    * Beech mein se element **add ya remove karna fast** hota hai (O(1)).
    * Kisi element ko **get karna (access karna) slow** hota hai (O(n)) kyunki shuru se traverse karna padta hai.

---
**Q: `HashMap` internally kaise kaam karta hai?**
**A:** `HashMap` **hashing** ke principle par kaam karta hai:
1.  Jab aap `put(key, value)` karte hain, to Java pehle `key` ka ek unique **`hashCode()`** nikalta hai.
2.  Is `hashCode()` se ek **index** (bucket location) calculate kiya jaata hai.
3.  Aapka key-value pair uss index par store ho jaata hai.
4.  Agar uss index par pehle se koi aur key hai (jise **collision** kehte hain), to nayi key-value pair ussi index par ek **Linked List** (ya balanced tree) mein add ho jaati hai.

---
**Q: Multithreading kya hai?**
**A:** Multithreading ek process hai jismein ek single program ke andar kai chote-chote tasks (**threads**) ek saath (concurrently) chalte hain. Yeh CPU ka behtar istemaal karne aur application ko responsive banane mein madad karta hai. Jaise ek music player mein, ek thread gaana chala raha hota hai aur doosra thread UI handle kar raha hota hai.

---
**Q: Java mein Exception Handling kya hai?**
**A:** Exception handling ek mechanism hai jisse hum **runtime errors** (exceptions) ko gracefully handle karte hain, taaki hamara program achanak band (crash) na ho jaaye. Iske liye hum **`try`**, **`catch`**, aur **`finally`** blocks ka use karte hain. `try` block mein error-prone code rakhte hain aur `catch` block mein uss error ko pakad kar handle karte hain.

---
**Q: `throw` aur `throws` mein kya difference hai?**
**A:**
* **`throw`:** Yeh keyword method ke **andar** use hota hai. Iska kaam ek exception ko **create karke fekna** (throw karna) hai.
* **`throws`:** Yeh keyword method ke **signature** (declaration) mein use hota hai. Yeh compiler ko batata hai ki "yeh method is type ka exception fek sakta hai, isliye jo bhi isse call kare, woh isse handle karne ke liye taiyaar rahe."

---
**Q: Java mein Diamond Problem kya hai?**
**A:** Diamond problem **multiple inheritance** se judi ek samasya hai. Maan lijiye Class `D`, Class `B` aur `C` ko inherit karti hai, aur `B` aur `C` dono Class `A` ko inherit karti hain. Agar `A` ka koi method `B` aur `C` dono ne override kiya hai, to `D` confuse ho jaayega ki kiska method use kare. Java classes ke saath multiple inheritance allow nahi karta, isliye yeh problem aati nahi. Lekin **interfaces ke default methods** ke saath yeh ho sakti hai, jise child class mein method ko override karke solve karna padta hai.

---
**Q: Immutable class kya hai aur kaise banayein? Mutable aur Immutable class kya hoti hai?**
**A:**
* **Mutable Class:** Ek aisi class jiska object banane ke baad uski values ko **change kiya ja sakta hai**. Jaise `StringBuilder`.
* **Immutable Class:** Ek aisi class jiska object ek baar ban gaya to uski values ko **change nahi kiya ja sakta**. Koi bhi change karne par ek naya object banta hai. Jaise `String`.

* **Immutable Class banane ke steps:**
    1.  Class ko **`final`** banayein taaki use inherit na kiya jaa sake.
    2.  Saare variables ko **`private final`** banayein.
    3.  Variables ko change karne ke liye koi **setter methods** na banayein.
    4.  Saare variables ko **constructor** ke through initialize karein.
    5.  Agar class mein koi mutable object (jaise `ArrayList`) hai, to uska reference direct return na karein, uski **copy return karein**.

---



### **1. Reverse a linked list**

**Q: Linked List ko reverse karne ka approach aur code do.**

**A:**

  * **Problem Statement:** Ek singly linked list di gayi hai. Aapko usse reverse karna hai.

      * **Example:** `Input: 1 -> 2 -> 3 -> 4 -> NULL`
      * **Output:** `4 -> 3 -> 2 -> 1 -> NULL`

  * **Approach:** Iske liye sabse accha iterative tareeka hai jismein hum **teen pointers** ka istemaal karte hain: `prev`, `current`, aur `next_node`.

    1.  Shuru mein, `prev` ko `NULL` aur `current` ko `head` par set karo.
    2.  Jab tak `current` `NULL` na ho jaaye, loop chalao.
    3.  Loop ke andar, pehle `current` ke agle node ko `next_node` mein store kar lo.
    4.  Ab `current` node ke link ko reverse karo (`current->next = prev`).
    5.  Aakhir mein, saare pointers ko ek step aage badha do (`prev = current`, `current = next_node`).

  * **C++ Code:**

    ```cpp
    #include <iostream>

    struct ListNode {
        int val;
        ListNode *next;
        ListNode(int x) : val(x), next(nullptr) {}
    };

    ListNode* reverseList(ListNode* head) {
        // TC: O(n), SC: O(1)
        ListNode* prev = nullptr;
        ListNode* current = head;
        ListNode* next_node = nullptr;

        while (current != nullptr) {
            // Agle node ko store karo
            next_node = current->next; 
            
            // Current node ka link reverse karo
            current->next = prev;     
            
            // Pointers ko aage badhao
            prev = current;           
            current = next_node;      
        }
        // Naya head ab 'prev' hoga
        head = prev;
        return head;
    }
    ```

-----

### **2. Check if a string is a palindrome**

**Q: String palindrome hai ya nahi, yeh check karne ka approach aur code do.**

**A:**

  * **Problem Statement:** Ek string di gayi hai. Pata lagana hai ki woh palindrome hai ya nahi. Palindrome woh string hoti hai jo aage aur peeche se padhne par same ho.

      * **Example:** `Input: "madam"` -\> `Output: true`
      * **Example:** `Input: "hello"` -\> `Output: false`

  * **Approach:** Hum **Two-Pointer** approach ka use karenge.

    1.  Ek pointer (`start`) string ke shuru mein (index 0) aur doosra pointer (`end`) string ke aakhir mein rakho.
    2.  Jab tak `start` pointer `end` se chhota hai, tab tak loop chalao.
    3.  Har step par, `start` aur `end` ke characters ko compare karo. Agar woh alag hain, to string palindrome nahi hai, `false` return kar do.
    4.  Agar characters same hain, to `start` ko aage aur `end` ko peeche badhao.
    5.  Agar loop poora chal jaata hai, iska matlab string palindrome hai, `true` return kar do.

  * **C++ Code:**

    ```cpp
    #include <iostream>
    #include <string>

    bool isPalindrome(std::string s) {
        // TC: O(n), SC: O(1)
        int start = 0;
        int end = s.length() - 1;

        while (start < end) {
            if (s[start] != s[end]) {
                return false;
            }
            start++;
            end--;
        }
        return true;
    }
    ```

-----

### **3. Sort a map by its values**

**Q: Map ko uski values ke basis par sort karne ka code do.**

**A:**

  * **Problem Statement:** Ek map diya gaya hai. Aapko usse uski values ke hisaab se sort karna hai.

      * **Example:** `Input: { "A": 3, "B": 1, "C": 2 }`
      * **Output:** `B: 1, C: 2, A: 3`

  * **Approach:** C++ mein `std::map` ko direct uski values se sort nahi kar sakte, kyunki woh keys ke basis par sorted hota hai. Iska tareeka yeh hai:

    1.  Map ke saare `(key, value)` pairs ko ek **`vector` of `pair`** mein copy kar lo.
    2.  Ab is vector ko `std::sort` function aur ek **custom comparator** ka use karke sort karo.
    3.  Custom comparator function vector ke pairs ko unki second value (`pair.second`) ke basis par compare karega.

  * **C++ Code:**

    ```cpp
    #include <iostream>
    #include <vector>
    #include <map>
    #include <algorithm>

    // Custom comparator function
    bool compareByValue(const std::pair<std::string, int>& a, const std::pair<std::string, int>& b) {
        return a.second < b.second;
    }

    void sortMapByValue() {
        // TC: O(n log n), SC: O(n)
        std::map<std::string, int> myMap = {{"Apple", 30}, {"Banana", 10}, {"Cherry", 20}};

        // Step 1: Map ke pairs ko vector mein copy karo
        std::vector<std::pair<std::string, int>> vec(myMap.begin(), myMap.end());

        // Step 2: Vector ko custom comparator se sort karo
        std::sort(vec.begin(), vec.end(), compareByValue);

        // Print the sorted vector
        for (const auto& pair : vec) {
            std::cout << pair.first << ": " << pair.second << std::endl;
        }
    }
    ```

-----

### **4. Factorial of a large number**

**Q: Bade number ka factorial nikalne ka approach aur code do.**

**A:**

  * **Problem Statement:** Ek bahut bade number ka factorial nikalna hai, jiska result `long long int` mein bhi fit na ho.

      * **Example:** `Input: 100` -\> `Output: 9332621...` (bahut bada number)

  * **Approach:** Hum result ko ek **`vector<int>`** mein store karenge, jahan har element ek digit ko represent karega.

    1.  Ek `result` vector banayein aur usmein `1` daal dein (`result = {1}`).
    2.  `2` se lekar diye gaye number `N` tak ek loop chalayein.
    3.  Har number `x` ke liye, `result` vector ke har digit ko `x` se multiply karein, school waali multiplication ki tarah. Ek `carry` variable maintain karein.
    4.  Yeh process `result` vector ko update karta jayega. Aakhir mein, `result` vector ko reverse order mein print kar dein.

  * **C++ Code:**

    ```cpp
    #include <iostream>
    #include <vector>
    #include <algorithm>

    void factorial(int n) {
        // TC: O(n * log10(n!)), SC: O(log10(n!))
        std::vector<int> result;
        result.push_back(1); // Shuru mein result 1 hai

        for (int x = 2; x <= n; x++) {
            int carry = 0;
            // Result vector ko x se multiply karo
            for (int i = 0; i < result.size(); i++) {
                int prod = result[i] * x + carry;
                result[i] = prod % 10; // Current digit store karo
                carry = prod / 10;    // Baaki carry aage bhejo
            }
            // Bacha hua carry aage add karo
            while (carry) {
                result.push_back(carry % 10);
                carry = carry / 10;
            }
        }

        // Result ko reverse order mein print karo
        for (int i = result.size() - 1; i >= 0; i--) {
            std::cout << result[i];
        }
        std::cout << std::endl;
    }
    ```

-----

### **5. Sort an array of 0s and 1s in one pass**

**Q: Ek array jismein sirf 0s aur 1s hain, usse ek pass mein sort karne ka approach aur code do.**

**A:**

  * **Problem Statement:** Ek array diya hai jismein sirf `0` aur `1` hain. Aapko usse ek hi pass mein (single traversal) sort karna hai.

      * **Example:** `Input: [0, 1, 1, 0, 1, 0, 0]`
      * **Output:** `[0, 0, 0, 0, 1, 1, 1]`

  * **Approach:** Iske liye **Two-Pointer** approach best hai.

    1.  Ek pointer `low` ko array ke shuru mein (index 0) aur doosra pointer `high` ko array ke aakhir mein rakho.
    2.  Jab tak `low < high` hai, tab tak loop chalao.
    3.  Agar `arr[low]` `0` hai, iska matlab woh sahi jagah par hai, to `low` ko aage badhao (`low++`).
    4.  Agar `arr[high]` `1` hai, iska matlab woh bhi sahi jagah par hai, to `high` ko peeche karo (`high--`).
    5.  Agar `arr[low]` `1` hai aur `arr[high]` `0` hai, iska matlab dono galat jagah par hain. Unhe `swap` kar do aur phir `low` ko aage aur `high` ko peeche karo.

  * **C++ Code:**

    ```cpp
    #include <iostream>
    #include <vector>
    #include <algorithm> // for std::swap

    void sort01(std::vector<int>& arr) {
        // TC: O(n), SC: O(1)
        int low = 0;
        int high = arr.size() - 1;

        while (low < high) {
            if (arr[low] == 0) {
                low++;
            } else if (arr[high] == 1) {
                high--;
            } else {
                // arr[low] is 1 and arr[high] is 0, so swap them
                std::swap(arr[low], arr[high]);
                low++;
                high--;
            }
        }
    }
    ```
---

-----

## **1 `DELETE`, `TRUNCATE`, aur `DROP` mein kya difference hai?**

**A:**
Yeh teeno commands data ya table ko hatane ke kaam aati hain, lekin inka kaam karne ka tareeka aur asar bilkul alag hai.

| Feature            | `DELETE`                                                        | `TRUNCATE`                                                    | `DROP`                                                          |
| :----------------- | :-------------------------------------------------------------- | :------------------------------------------------------------ | :-------------------------------------------------------------- |
| **Command Type**   | DML (Data Manipulation Language)                                | DDL (Data Definition Language)                                | DDL (Data Definition Language)                                  |
| **Kaam Kya Hai?**  | Table se ek ya ek se zyada **rows** ko hatata hai.              | Table se **saari rows** ko ek saath hata deta hai.            | Poore **table ko uske structure ke saath** delete kar deta hai. |
| **`WHERE` Clause** | Haan, use kar sakte hain (specific rows hatane ke liye).        | Nahi, use nahi kar sakte.                                     | Nahi, use nahi kar sakte.                                       |
| **Speed**          | Slow hota hai (kyunki har row ko individually check karta hai). | Fast hota hai (poori table ko ek saath khali karta hai).      | Bahut fast hai.                                                 |
| **Rollback**       | Haan, transaction ko rollback kar sakte hain.                   | Nahi, rollback nahi kar sakte (mostly database systems mein). | Nahi, rollback nahi kar sakte.                                  |

**Simple bhasha mein:**

  * **DELETE:** Diary se kuch specific panne (rows) faadna.
  * **TRUNCATE:** Diary ke saare panne faad dena, lekin diary (table structure) ko rakhna.
  * **DROP:** Poori diary ko hi jala dena.

-----

## **2 Second-highest salary find karne ki query likho.**

**A:**
Ek employee table se second-highest salary nikalne ke kai tareeke hain. Do sabse common aur acche tareeke yeh hain:

**Approach 1: `LIMIT` aur `OFFSET` ka use karke (MySQL/PostgreSQL)**
Yeh tareeka pehle saari salaries ko descending order mein sort karta hai, phir pehli (highest) salary ko skip (`OFFSET 1`) karke agle ek result (`LIMIT 1`) ko utha leta hai.

```sql
SELECT Salary 
FROM Employee
ORDER BY Salary DESC
LIMIT 1 OFFSET 1;
```

**Approach 2: `DENSE_RANK()` Window Function ka use karke (Standard SQL)**
Yeh sabse behtar tareeka hai kyunki yeh duplicate salaries ko aasaani se handle kar leta hai. `DENSE_RANK()` har unique salary ko ek rank deta hai.

```sql
SELECT Salary 
FROM (
    SELECT 
        Salary, 
        DENSE_RANK() OVER (ORDER BY Salary DESC) as dr
    FROM Employee
) AS SalaryRank
WHERE dr = 2;
```




---
**Behavioral & Project-Based Questions**

* Tell me about your most challenging project.
* How do you handle a situation where you don't know the answer?
* Why do you want to join Publicis Sapient?
* Where do you see yourself in the next 5 years?
* What are your strengths and weaknesses?
* Explain your project architecture.
* What was your role in the project?

---