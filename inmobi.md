

## 1\. Word Square Problem

### Problem Statement (Hinglish)

Aapko words ki ek list di gayi hai, jinke lengths same hain. Aapko saare possible "word squares" banane hain. Ek word square tab valid hota hai jab uski har i-th row aur i-th column same string ho.

### Example

**Input:** `["area", "lead", "wall", "lady"]`
**Output:**

```
[
  ["wall",
   "area",
   "lead",
   "lady"]
]
```

**Explanation:** Yahan pe, 0th row "wall" hai aur 0th column bhi "wall" hai (w, a, l, l). Aise hi 1st row "area" aur 1st column "area" hai, and so on.

### Approaches (Hinglish)

#### Brute Force Approach

Saare words ke possible combinations (permutations) try karo. Har combination ko check karo ki woh ek valid word square hai ya nahi. Yeh approach bahut hi slow hai kyunki isme bahut saare unnecessary combinations check hote hain.

#### Optimal Approach (Backtracking with Trie)

Hum ek-ek karke row fill karenge. Har row ko add karne ke baad, hum check karenge ki abhi tak bana hua square valid hai ya nahi (matlab `j`-th column ka prefix `j`-th row ke prefix se match kar raha hai ya nahi). Agar match nahi karta, toh hum us path se aage nahi badhenge (backtrack).
Prefixes ko efficiently check karne ke liye hum saare words ko ek **Trie** data structure mein store kar sakte hain.

### C++ Code

```cpp
// Optimal Approach: Backtracking
class Solution {
public:
    vector<vector<string>> wordSquares(vector<string>& words) {
        if (words.empty()) return {};
        int n = words[0].size();
        vector<vector<string>> result;
        vector<string> current_square;
        
        // Backtracking function
        function<void(int)> solve = 
            [&](int row) {
            // Base case: jab square pura ban jaye
            if (row == n) {
                result.push_back(current_square);
                return;
            }
            
            // Agli row ke liye prefix banate hain
            string prefix = "";
            for (int i = 0; i < row; ++i) {
                prefix += current_square[i][row];
            }
            
            // Saare words check karte hain jo is prefix se start hote hain
            for (const string& word : words) {
                if (word.rfind(prefix, 0) == 0) { // Check if word starts with prefix
                    current_square.push_back(word);
                    solve(row + 1);
                    current_square.pop_back(); // Backtrack
                }
            }
        };
        
        solve(0);
        return result;
    }
};

/*
Time Complexity: O(N * 26^L), jahan N words ki sankhya hai aur L ek word ki length hai.
Har step par, hum L length tak ke prefix ke liye search karte hain.
Space Complexity: O(N * L) words ko store karne ke liye aur O(L^2) recursion stack ke liye.
*/
```

-----

## 2\. Rotten Oranges Problem

### Problem Statement (Hinglish)

Aapko ek `m x n` grid di gayi hai jisme `0` (empty cell), `1` (fresh orange), ya `2` (rotten orange) ho sakta hai. Har minute, ek rotten orange apne 4-directionally (up, down, left, right) adjacent fresh oranges ko sada deta hai. Aapko minimum time batana hai jisme saare oranges sad jayenge. Agar sabko sadana impossible hai, to `-1` return karna hai.

### Example

**Input:** `grid = [[2,1,1],[1,1,0],[0,1,1]]`
**Output:** `4`
**Explanation:** Time 0 pe (0,0) rotten hai. Har minute naye oranges sadte jayenge. 4 minute mein sab sad jayenge.

### Approach (Hinglish)

#### Optimal Approach (Multi-Source BFS)

Yeh ek classic **Multi-source Breadth-First Search (BFS)** problem hai. Hum sabhi rotten oranges se ek saath BFS start karenge.

1.  Shuru mein, saare rotten oranges `(row, col)` ko ek queue mein daal do. Saath hi, fresh oranges ki ginti kar lo.
2.  Queue se ek rotten orange nikalo aur uske 4 adjacent fresh oranges ko check karo.
3.  Agar koi fresh orange milta hai, use rotten bana do (`grid` value ko 2 kar do), use queue mein daal do, aur fresh oranges ka count kam kar do.
4.  Hum level-wise traversal karenge. Har level ek minute ko represent karta hai.
5.  Jab queue khaali ho jaye, check karo ki saare fresh oranges sad gaye hain ya nahi. Agar `fresh_oranges_count > 0` hai, to `-1` return karo. Warna, total time (levels) return karo.

### C++ Code

```cpp
// Optimal Approach: Multi-source BFS
int orangesRotting(vector<vector<int>>& grid) {
    int m = grid.size();
    int n = grid[0].size();
    queue<pair<int, int>> q;
    int freshOranges = 0;
    
    // Initial setup: rotten oranges ko queue me daalo aur fresh count karo
    for (int i = 0; i < m; ++i) {
        for (int j = 0; j < n; ++j) {
            if (grid[i][j] == 2) {
                q.push({i, j});
            } else if (grid[i][j] == 1) {
                freshOranges++;
            }
        }
    }
    
    if (freshOranges == 0) return 0;
    
    int minutes = -1;
    int dr[] = {-1, 1, 0, 0}; // Directions for row
    int dc[] = {0, 0, -1, 1}; // Directions for col
    
    // BFS start karo
    while (!q.empty()) {
        int levelSize = q.size();
        for (int i = 0; i < levelSize; ++i) {
            auto [r, c] = q.front();
            q.pop();
            
            for (int k = 0; k < 4; ++k) {
                int nr = r + dr[k];
                int nc = c + dc[k];
                
                if (nr >= 0 && nr < m && nc >= 0 && nc < n && grid[nr][nc] == 1) {
                    grid[nr][nc] = 2; // Sada do
                    freshOranges--;
                    q.push({nr, nc});
                }
            }
        }
        minutes++;
    }
    
    return freshOranges == 0 ? minutes : -1;
}

/*
Time Complexity: O(m * n) - Har cell ko ek hi baar visit kiya jayega.
Space Complexity: O(m * n) - Worst case mein, queue sabhi cells ko store kar sakti hai.
*/
```

-----

## 3\. Virus Spread & Man Escape Problem

### Problem Statement (Hinglish)

Ek grid hai jisme virus, walls, empty cells aur ek aadmi (Man) hai. Har second, virus apne 4-directionally adjacent cells mein failta hai. Aadmi bhi har second ek adjacent empty cell mein move kar sakta hai. Aapko batana hai ki kya aadmi virus ke pakad mein aane se pehle grid ke kisi boundary (edge) tak pahunch kar escape kar sakta hai.

### Approach (Hinglish)

#### Optimal Approach (Two BFS)

Is problem ko solve karne ke liye hum do alag-alag BFS chalayenge.

1.  **Virus BFS:** Pehle, ek multi-source BFS virus ke saare initial positions se chalao. Isse hum har cell `(r, c)` ke liye woh minimum time `virus_time[r][c]` nikal lenge jisme virus us cell tak pahunchega.
2.  **Man BFS:** Ab, aadmi ki starting position se ek single-source BFS chalao. Isse hum har cell `(r, c)` tak pahunchne ka minimum time `man_time[r][c]` nikalenge.
3.  Jab aadmi `(r, c)` se kisi naye cell `(nr, nc)` par jaata hai, to yeh move tabhi valid hoga jab aadmi us cell par virus se **pehle** pahunche, yaani `man_time[nr][nc] < virus_time[nr][nc]`.
4.  Agar aadmi ka BFS kisi bhi boundary cell tak is condition ko follow karte hue pahunch jaata hai, to escape possible hai.

### C++ Code

```cpp
// Yeh ek conceptual problem hai, isliye ek general function structure diya gaya hai.
bool canManEscape(vector<vector<char>>& grid) {
    int m = grid.size();
    int n = grid[0].size();

    // Step 1: Virus BFS
    vector<vector<int>> virus_time(m, vector<int>(n, INT_MAX));
    queue<pair<int, int>> virus_q;
    pair<int, int> man_start;

    // Grid ko initialize karo
    for (int i = 0; i < m; ++i) {
        for (int j = 0; j < n; ++j) {
            if (grid[i][j] == 'V') {
                virus_q.push({i, j});
                virus_time[i][j] = 0;
            } else if (grid[i][j] == 'M') {
                man_start = {i, j};
            }
        }
    }

    int dr[] = {-1, 1, 0, 0};
    int dc[] = {0, 0, -1, 1};

    // Virus ke liye time calculate karo
    int time = 0;
    while (!virus_q.empty()) {
        int levelSize = virus_q.size();
        time++;
        for (int i = 0; i < levelSize; ++i) {
            auto [r, c] = virus_q.front();
            virus_q.pop();
            for (int k = 0; k < 4; ++k) {
                int nr = r + dr[k];
                int nc = c + dc[k];
                if (nr >= 0 && nr < m && nc >= 0 && nc < n && grid[nr][nc] != '#' && virus_time[nr][nc] == INT_MAX) {
                    virus_time[nr][nc] = time;
                    virus_q.push({nr, nc});
                }
            }
        }
    }
    
    // Step 2: Man BFS
    queue<tuple<int, int, int>> man_q; // {row, col, time}
    man_q.push({man_start.first, man_start.second, 0});
    vector<vector<bool>> visited(m, vector<bool>(n, false));
    visited[man_start.first][man_start.second] = true;

    while (!man_q.empty()) {
        auto [r, c, t] = man_q.front();
        man_q.pop();

        // Check for escape condition
        if (r == 0 || r == m - 1 || c == 0 || c == n - 1) {
            return true;
        }

        for (int k = 0; k < 4; ++k) {
            int nr = r + dr[k];
            int nc = c + dc[k];
            int next_time = t + 1;

            if (nr >= 0 && nr < m && nc >= 0 && nc < n && grid[nr][nc] != '#' && !visited[nr][nc]) {
                // Main condition: Aadmi virus se pehle pahunche
                if (next_time < virus_time[nr][nc]) {
                    visited[nr][nc] = true;
                    man_q.push({nr, nc, next_time});
                }
            }
        }
    }

    return false;
}

/*
Time Complexity: O(m * n) - Do baar BFS chalega, dono O(m*n).
Space Complexity: O(m * n) - virus_time grid aur queue ke liye.
*/
```

-----

## 4\. Search in a Row-wise and Column-wise Sorted Matrix

### Problem Statement (Hinglish)

Aapko ek `m x n` matrix di gayi hai. Iski har row left-to-right sorted hai aur har column top-to-bottom sorted hai. Aapko ek `target` value ko is matrix mein efficiently search karna hai.

### Example

**Input:** `matrix = [[1,4,7],[2,5,8],[3,6,9]]`, `target = 5`
**Output:** `true`

### Approaches (Hinglish)

#### Brute Force Approach

Poore matrix ke har element ko ek-ek karke check karo ki woh `target` ke barabar hai ya nahi. Iski time complexity `O(m*n)` hogi.

#### Optimal Approach (Staircase Search)

Yeh ek bahut hi clever approach hai.

1.  Search ko matrix ke **top-right corner** se start karo. (Aap bottom-left se bhi kar sakte hain).
2.  Current element ko `target` se compare karo:
      * Agar `current == target`, to mil gaya, `true` return karo.
      * Agar `current > target`, iska matlab `target` is column mein nahi ho sakta (kyunki neeche ke saare elements aur bade hain). Isliye, ek column peeche jao (`col--`).
      * Agar `current < target`, iska matlab `target` is row mein nahi ho sakta (kyunki isse pehle ke saare elements chhote hain). Isliye, ek row neeche jao (`row++`).
3.  Yeh process tab tak karo jab tak aap grid ke bahar na nikal jao. Agar `target` nahi milta to `false` return karo.

### C++ Code

```cpp
// Optimal Approach: Staircase Search
bool searchMatrix(vector<vector<int>>& matrix, int target) {
    if (matrix.empty() || matrix[0].empty()) {
        return false;
    }
    
    int m = matrix.size();
    int n = matrix[0].size();
    
    int row = 0;
    int col = n - 1; // Top-right corner se start
    
    while (row < m && col >= 0) {
        if (matrix[row][col] == target) {
            return true;
        } else if (matrix[row][col] > target) {
            col--; // Peeche jao
        } else {
            row++; // Neeche jao
        }
    }
    
    return false;
}

/*
Time Complexity: O(m + n) - Worst case mein, aap 'm' rows aur 'n' columns traverse karenge.
Space Complexity: O(1) - Koi extra space use nahi hua.
*/
```

-----

## 5\. Shortest Path in a Binary Matrix

### Problem Statement (Hinglish)

Aapko ek `n x n` binary matrix (`0` aur `1` ki grid) di gayi hai. Aapko top-left corner `(0,0)` se bottom-right corner `(n-1, n-1)` tak ka sabse chhota "clear path" nikalna hai. Ek clear path sirf un cells se ban sakta hai jinki value `0` hai. Aap **8 directions** (horizontal, vertical, and diagonal) mein move kar sakte hain. Path ki length total cells ki ginti hai. Agar koi path possible nahi hai, to `-1` return karo.

### Example

**Input:** `grid = [[0,0,0],[1,1,0],[1,1,0]]`
**Output:** `4`
**Explanation:** Sabse chhota path hai `(0,0) -> (0,1) -> (1,2) -> (2,2)`. Is path mein 4 cells hain.

### Approach (Hinglish)

#### Optimal Approach (BFS)

Jab bhi unweighted grid/graph mein shortest path nikalna ho, **BFS** sabse best approach hai.

1.  **Edge cases:** Check karo ki start `(0,0)` ya end `(n-1, n-1)` blocked (`1`) to nahi hai. Agar hai, to `-1` return karo.
2.  Ek queue banao jisme `{row, col, distance}` store ho. Start mein `{0, 0, 1}` daal do (path length 1 se shuru hoti hai).
3.  Ek cell ko visit karne ke baad, usko dobara visit na karne ke liye, `grid` mein uski value `0` se `1` kar do.
4.  Queue se `(r, c)` nikalo. Agar yeh destination hai, to `distance` return kar do.
5.  Warna, uske sabhi 8 valid neighbors (`(nr, nc)` jo grid ke andar ho aur `0` ho) ko queue mein `{nr, nc, distance + 1}` ke saath daal do aur unhe visited mark kar do.
6.  Agar queue khaali ho jaati hai aur destination nahi milta, to iska matlab koi path nahi hai, to `-1` return karo.

### C++ Code

```cpp
// Optimal Approach: BFS
int shortestPathBinaryMatrix(vector<vector<int>>& grid) {
    int n = grid.size();
    if (grid[0][0] == 1 || grid[n-1][n-1] == 1) {
        return -1;
    }
    
    queue<tuple<int, int, int>> q; // {row, col, distance}
    q.push({0, 0, 1});
    grid[0][0] = 1; // Visited mark kar do
    
    // 8 directions ke liye offsets
    int dr[] = {-1, -1, -1, 0, 0, 1, 1, 1};
    int dc[] = {-1, 0, 1, -1, 1, -1, 0, 1};
    
    while (!q.empty()) {
        auto [r, c, dist] = q.front();
        q.pop();
        
        if (r == n - 1 && c == n - 1) {
            return dist;
        }
        
        // 8 directions mein explore karo
        for (int i = 0; i < 8; ++i) {
            int nr = r + dr[i];
            int nc = c + dc[i];
            
            if (nr >= 0 && nr < n && nc >= 0 && nc < n && grid[nr][nc] == 0) {
                grid[nr][nc] = 1; // Visited mark kar do
                q.push({nr, nc, dist + 1});
            }
        }
    }
    
    return -1; // Path nahi mila
}

/*
Time Complexity: O(n*n) - Har cell ko ek hi baar visit kiya jayega.
Space Complexity: O(n*n) - Worst case mein, queue sabhi cells ko store kar sakti hai.
*/
```

----



## 1\. Find Articulation Point/Bridge in a Network

### Problem Statement (Hinglish)

Aapko ek undirected graph diya gaya hai. Aapko iske "critical connections" dhoondhne hain, jo do tarah ke hote hain:

1.  **Articulation Point (or Cut Vertex):** Aisa vertex jisko graph se hatane par graph ke connected components ki sankhya badh jaati hai. Yeh network mein single points of failure hote hain.
2.  **Bridge (or Cut Edge):** Aisa edge jisko graph se hatane par connected components ki sankhya badh jaati hai.

### Example

Graph: Edges (0-1), (1-2), (2-3), (3-4), (2-5), (5-6), (6-7), (7-5)

  * **Articulation Points:** 2, 3, 5
  * **Bridges:** (1-2), (2-3), (3-4)

### Approaches (Hinglish)

#### Brute Force Approach

  * **For Articulation Points:** Har vertex ko ek-ek karke hatao. Har baar check karo ki graph ke connected components badhe ya nahi (using BFS/DFS). Complexity: $O(V \\times (V+E))$.
  * **For Bridges:** Har edge ko ek-ek karke hatao. Har baar check karo ki connected components badhe ya nahi. Complexity: $O(E \\times (V+E))$.
    Yeh approaches bade graphs ke liye bahut slow hain.

#### Optimal Approach (Tarjan's Algorithm using DFS)

Yeh algorithm ek hi DFS traversal mein saare articulation points aur bridges nikal leta hai.

1.  Hum har vertex `u` ke liye do values maintain karte hain:
      * `discovery_time[u]`: Jab hum `u` ko pehli baar visit karte hain (discovery time).
      * `low_link_time[u]`: `u` ya uske subtree se, kisi "back-edge" ka use karke, sabse pehle discovered hue vertex ka discovery time.
2.  DFS traversal ke dauraan, for an edge `(u, v)` (jahan `u`, `v` ka parent hai):
      * **Bridge Condition:** Agar `low_link_time[v] > discovery_time[u]`, to edge `(u, v)` ek bridge hai. Iska matlab `v` ke subtree se `u` ya uske kisi purvaj (ancestor) tak pahunchne ka koi aur raasta (back-edge) nahi hai.
      * **Articulation Point Condition:**
          * DFS tree ka root ek articulation point hota hai agar uske 2 se zyada children hon.
          * Koi aur vertex `u` ek articulation point hota hai agar uska koi child `v` aisa ho jiske liye `low_link_time[v] >= discovery_time[u]`.

### C++ Code

```cpp
// Optimal Approach: Tarjan's Algorithm
vector<int> articulation_points;
vector<pair<int, int>> bridges;
int timer;

void find_aps_and_bridges(int u, int p, vector<int>& disc, vector<int>& low, vector<bool>& visited, vector<vector<int>>& adj) {
    visited[u] = true;
    disc[u] = low[u] = timer++;
    int children = 0;

    for (int v : adj[u]) {
        if (v == p) continue;

        if (visited[v]) {
            // Back-edge mila
            low[u] = min(low[u], disc[v]);
        } else {
            children++;
            find_aps_and_bridges(v, u, disc, low, visited, adj);
            low[u] = min(low[u], low[v]);

            // Bridge condition
            if (low[v] > disc[u]) {
                bridges.push_back({u, v});
            }

            // Articulation point condition
            if (p != -1 && low[v] >= disc[u]) {
                // To avoid duplicates, we can use a set or check before pushing
                // For simplicity, let's assume we handle duplicates later
                articulation_points.push_back(u);
            }
        }
    }
    // Special case for root
    if (p == -1 && children > 1) {
        articulation_points.push_back(u);
    }
}

void solve(int V, vector<vector<int>>& adj) {
    vector<int> disc(V, -1), low(V, -1);
    vector<bool> visited(V, false);
    timer = 0;
    articulation_points.clear();
    bridges.clear();

    for (int i = 0; i < V; ++i) {
        if (!visited[i]) {
            find_aps_and_bridges(i, -1, disc, low, visited, adj);
        }
    }
    // You can process the articulation_points and bridges vectors here.
    // Note: The articulation_points vector might have duplicates, use a set for unique points.
}

/*
Time Complexity: O(V + E) - Kyunki yeh ek standard DFS traversal hai.
Space Complexity: O(V) - Recursion stack aur arrays ke liye.
*/
```

-----

## 2\. Bipartite Graph Check

### Problem Statement (Hinglish)

Aapko ek graph diya gaya hai. Aapko check karna hai ki kya yeh **bipartite** hai. Ek graph bipartite tab hota hai jab uske saare vertices ko do alag-alag sets (`Set A` aur `Set B`) mein baanta ja sake, is tarah ki graph ki har edge `Set A` ke ek vertex ko `Set B` ke ek vertex se jodti ho. Koi bhi edge same set ke do vertices ko nahi jodti.

### Example

**Input Graph:** Edges (0-1), (1-2), (2-3), (3-0).
**Output:** `true`
**Explanation:** Hum vertices ko do sets mein baant sakte hain: `Set A = {0, 2}` aur `Set B = {1, 3}`. Har edge ek set se dusre set tak jaati hai.
Agar is graph mein ek edge (0-2) hoti, to yeh bipartite nahi hota.

### Approach (Hinglish)

#### Optimal Approach (Graph Coloring using BFS/DFS)

Ek graph bipartite tabhi hota hai jab usme koi **odd-length cycle** na ho. Hum is property ko check karne ke liye graph coloring ka use karte hain.

1.  Do colors lo (e.g., `0` aur `1`). Ek `color` array banao aur sabko `-1` (uncolored) se initialize karo.
2.  Kisi bhi uncolored vertex se start karo (hum yahan BFS ka use karenge).
3.  Source vertex ko color `0` do aur queue mein daal do.
4.  Jab tak queue khaali na ho:
      * Ek vertex `u` nikalo.
      * Uske saare neighbors `v` ko check karo:
          * Agar `v` uncolored (`-1`) hai, to use `u` se opposite color do aur queue mein daal do.
          * Agar `v` pehle se colored hai aur uska color `u` ke color jaisa **hi** hai, to iska matlab ek odd-length cycle mil gayi hai. Graph bipartite nahi hai. `false` return karo.
5.  Yeh process graph ke saare components ke liye repeat karo. Agar poora traversal bina kisi conflict ke ho jaye, to graph bipartite hai. `true` return karo.

### C++ Code

```cpp
// Optimal Approach: BFS Coloring
bool isBipartite(int V, vector<vector<int>>& adj) {
    vector<int> color(V, -1); // -1: uncolored, 0: color A, 1: color B

    for (int startNode = 0; startNode < V; ++startNode) {
        if (color[startNode] == -1) {
            queue<int> q;
            q.push(startNode);
            color[startNode] = 0;

            while (!q.empty()) {
                int u = q.front();
                q.pop();

                for (int v : adj[u]) {
                    if (color[v] == -1) {
                        color[v] = 1 - color[u]; // Opposite color do
                        q.push(v);
                    } else if (color[v] == color[u]) {
                        return false; // Conflict: Same color on adjacent nodes
                    }
                }
            }
        }
    }
    return true;
}

/*
Time Complexity: O(V + E) - Standard BFS traversal.
Space Complexity: O(V) - Color array aur queue ke liye.
*/
```

-----

## 3\. Maximum Sum of Nodes in Binary Tree (No Two are Adjacent)

### Problem Statement (Hinglish)

Aapko ek binary tree diya gaya hai. Aapko un nodes ka maximum possible sum nikalna hai, is shart ke saath ki koi bhi do chune gaye nodes aapas mein adjacent na ho (matlab ek dusre ke parent-child na ho).

### Example

**Input Tree:**

```
    10
   /  \
  1    2
       / \
      3   4
```

**Output:** `17`
**Explanation:** Hum nodes `10`, `3`, aur `4` ko chunte hain. Sum = `10 + 3 + 4 = 17`. Yeh valid hai kyunki inme se koi bhi do nodes adjacent nahi hain.

### Approach (Hinglish)

#### Optimal Approach (DP on Trees / Post-order Traversal)

Yeh problem Dynamic Programming ka ek classic example hai. Hum har node ke liye do values nikalenge, ek recursive function (post-order traversal) ka use karke.
Function har node ke liye ek pair `{sum_if_included, sum_if_excluded}` return karega.

1.  `sum_if_included`: Is node ko **chunne** par subtree se milne wala maximum sum.
2.  `sum_if_excluded`: Is node ko **na chunne** par subtree se milne wala maximum sum.

**Calculation for a `node`:**

1.  Recursively left aur right children ke liye solution nikalo:
    `left_sums = solve(node->left)`
    `right_sums = solve(node->right)`
2.  **Agar `node` ko include karte hain:**
    Toh hum uske children ko nahi le sakte.
    `sum_if_included = node->val + left_sums.excluded + right_sums.excluded`
3.  **Agar `node` ko exclude karte hain:**
    Toh hum uske children ko le bhi sakte hain aur nahi bhi. Hum dono children ke subtrees se maximum possible sum lenge.
    `sum_if_excluded = max(left_sums.included, left_sums.excluded) + max(right_sums.included, right_sums.excluded)`
4.  Base Case: Agar `node == NULL`, to `{0, 0}` return karo.
5.  Final answer root ke liye `max(sum_if_included, sum_if_excluded)` hoga.

### C++ Code

```cpp
// Struct for Node
struct Node {
    int data;
    Node *left, *right;
};

// Optimal Approach: DP on Tree
pair<int, int> solve(Node* root) {
    if (root == nullptr) {
        return {0, 0}; // {included_sum, excluded_sum}
    }
    
    // Left aur right subtrees ke liye recursively solve karo
    pair<int, int> left_sum = solve(root->left);
    pair<int, int> right_sum = solve(root->right);
    
    // Case 1: Current node ko include karte hain
    // Toh children ko include nahi kar sakte
    int sum_included = root->data + left_sum.second + right_sum.second;
    
    // Case 2: Current node ko exclude karte hain
    // Toh children ke dono cases (included/excluded) me se max le sakte hain
    int sum_excluded = max(left_sum.first, left_sum.second) + 
                       max(right_sum.first, right_sum.second);
                       
    return {sum_included, sum_excluded};
}

int getMaxSum(Node *root) {
    pair<int, int> result = solve(root);
    return max(result.first, result.second);
}

/*
Time Complexity: O(N) - Kyunki hum har node ko ek hi baar visit karte hain.
Space Complexity: O(H) - Recursion stack ki height ke barabar, jahan H tree ki height hai.
*/
```

-----

## 4\. Diameter of a Binary Tree

### Problem Statement (Hinglish)

Aapko ek binary tree diya gaya hai. Aapko uska **diameter** nikalna hai. Diameter tree ke kisi bhi do nodes ke beech ka sabse lamba path hota hai. Path ki length usme aane wale edges ki sankhya hoti hai. Yeh zaroori nahi hai ki path root se hokar guzre.

### Example

**Input Tree:**

```
      1
     / \
    2   3
   / \
  4   5
```

**Output:** `3`
**Explanation:** Sabse lamba path `4 -> 2 -> 1 -> 3` ya `5 -> 2 -> 1 -> 3` hai. Iski length (edges ki ginti) 3 hai.

### Approach (Hinglish)

#### Optimal Approach (DFS / Height-based)

Hum is problem ko tree ki height nikalne wale logic ko modify karke solve kar sakte hain. Ek hi DFS traversal mein kaam ho jayega.

1.  Ek variable `diameter` banayeinge (global ya reference se pass karenge) jo maximum diameter ko store karega.
2.  Ek recursive function `height(node)` banayeinge jo do kaam karega:
      * `node` par rooted subtree ki height return karega.
      * Har `node` par, usse guzarne wale path ki length (diameter) ko calculate karega aur global `diameter` ko update karega.
3.  **Logic for a `node`:**
      * Recursively left subtree ki height (`lh`) aur right subtree ki height (`rh`) nikalo.
      * Is `node` se guzarne wala longest path `lh + rh` hoga.
      * Global `diameter` ko `max(diameter, lh + rh)` se update kar do.
      * Function se `1 + max(lh, rh)` return karo, jo is `node` ki height hai.
4.  Base Case: Agar `node == NULL`, to 0 return karo.

### C++ Code

```cpp
// Struct for Node
struct Node {
    int data;
    Node *left, *right;
};

// Optimal Approach: Modified Height Calculation
int calculate_height_and_update_diameter(Node* root, int& diameter) {
    if (root == nullptr) {
        return 0;
    }
    
    // Left aur right subtree ki height nikalo
    int left_height = calculate_height_and_update_diameter(root->left, diameter);
    int right_height = calculate_height_and_update_diameter(root->right, diameter);
    
    // Current node se pass hone wala longest path
    // Isse global diameter ko update karo
    diameter = max(diameter, left_height + right_height);
    
    // Current node ki height return karo
    return 1 + max(left_height, right_height);
}


int diameterOfBinaryTree(Node* root) {
    int diameter = 0;
    calculate_height_and_update_diameter(root, diameter);
    return diameter;
}
/*
Time Complexity: O(N) - Har node ko ek hi baar visit kiya jayega.
Space Complexity: O(H) - Recursion stack ki wajah se, jahan H tree ki height hai.
*/
```

----


## 1\. Multi-source BFS in 1D Array (Jump Game IV)

### Problem Statement (Hinglish)

Aapko ek integers ka array `arr` aur ek starting index `0` diya gaya hai. Aapko minimum jumps mein array ke last index `(n-1)` tak pahunchna hai. Aap `i`-th index se teen tarah se jump kar sakte hain:

1.  **`i + 1`** (agar `i + 1 < n`)
2.  **`i - 1`** (agar `i - 1 >= 0`)
3.  **`j`** (jahan `arr[i] == arr[j]` aur `i != j` ho). Yeh ek "teleport" jump hai.

### Example

**Input:** `arr = [100, -23, -23, 404, 100, 23, 23, 23, 3, 404]`
**Output:** `3`
**Explanation:** Sabse chhota path hai: `index 0` -\> `index 4` (value 100 se teleport) -\> `index 3` (value 404 se teleport) -\> `index 9` (value 404 se teleport). Total 3 jumps.

### Approach (Hinglish)

#### Optimal Approach (Modified BFS)

Yeh shortest path problem hai, isliye BFS best hai. Nodes array ke indices honge.

1.  **Preprocessing:** Graph ke saare edges pehle se banana (`O(N^2)`) mehanga padega. Isliye, hum ek `map` banayenge jo har value ke saare indices ko store karega. `map<int, vector<int>>`. Isse teleport jumps aasani se mil jayenge.
2.  **BFS Logic:**
      * Ek queue `q` aur ek `visited` array maintain karo.
      * Queue mein start index `0` daalo aur use visited mark karo.
      * Level-wise BFS chalao (har level ek jump hai).
      * Har step mein, `i`-th index se, uske neighbors (`i-1`, `i+1`) aur map se milne wale saare teleport indices `j` ko queue mein daalo (agar woh visited na ho).
3.  **Crucial Optimization:** Jab aap ek value `V` ke saare teleport locations ko queue mein daal dein, to map se us `V` ki entry ko **delete kar do**. Aisa karne se hum baar-baar same value ke teleport locations ko process karne se bach jayenge, jisse Time Limit Exceeded (TLE) nahi aayega.

### C++ Code

```cpp
// Optimal Approach: BFS with optimization
int minJumps(vector<int>& arr) {
    int n = arr.size();
    if (n <= 1) return 0;

    // Step 1: Preprocessing
    unordered_map<int, vector<int>> indicesOfValue;
    for (int i = 0; i < n; i++) {
        indicesOfValue[arr[i]].push_back(i);
    }

    queue<int> q;
    vector<bool> visited(n, false);
    q.push(0);
    visited[0] = true;
    int jumps = 0;

    // Step 2: BFS
    while (!q.empty()) {
        int size = q.size();
        while (size--) {
            int i = q.front();
            q.pop();

            if (i == n - 1) return jumps;

            // Jump to j where arr[i] == arr[j]
            vector<int>& teleport_indices = indicesOfValue[arr[i]];
            for (int j : teleport_indices) {
                if (!visited[j]) {
                    visited[j] = true;
                    q.push(j);
                }
            }
            // Step 3: Crucial Optimization
            teleport_indices.clear();

            // Jump to i+1
            if (i + 1 < n && !visited[i + 1]) {
                visited[i + 1] = true;
                q.push(i + 1);
            }
            // Jump to i-1
            if (i - 1 >= 0 && !visited[i - 1]) {
                visited[i - 1] = true;
                q.push(i - 1);
            }
        }
        jumps++;
    }

    return -1;
}
/*
Time Complexity: O(N) - Har index aur edge (including teleport edges) ko ek hi baar process kiya jaata hai.
Space Complexity: O(N) - Map, queue, aur visited array ke liye.
*/
```

-----

## 2\. Unique Paths

### Problem Statement (Hinglish)

Ek `m x n` grid ke top-left corner `(0,0)` par ek robot hai. Use bottom-right corner `(m-1, n-1)` tak jaana hai. Robot har step mein ya to **neeche (down)** ya **daayein (right)** ja sakta hai. Aise kitne unique paths possible hain?

### Example

**Input:** `m = 3, n = 2`
**Output:** `3`
**Explanation:** 3 paths hain: Right -\> Down -\> Down, Down -\> Right -\> Down, Down -\> Down -\> Right.

### Approach (Hinglish)

#### Optimal Approach (Dynamic Programming)

Let `dp[i][j]` = `(i, j)` tak pahunchne ke total unique paths.

  - Kisi bhi cell `(i, j)` par pahunchne ke do hi tareeke hain: ya to upar wale cell `(i-1, j)` se ya left wale cell `(i, j-1)` se.
  - **Recurrence Relation:** `dp[i][j] = dp[i-1][j] + dp[i][j-1]`
  - **Base Case:** Pehli row aur pehle column ke har cell tak pahunchne ka sirf 1 tareeka hai (sirf right ya sirf down jaakar). So, `dp[0][j] = 1` aur `dp[i][0] = 1`.

### C++ Code

```cpp
// Optimal Approach: Tabulation DP
int uniquePaths(int m, int n) {
    vector<vector<int>> dp(m, vector<int>(n, 1));

    for (int i = 1; i < m; i++) {
        for (int j = 1; j < n; j++) {
            // Har cell ke liye, upar aur left se aane wale paths ko add karo
            dp[i][j] = dp[i-1][j] + dp[i][j-1];
        }
    }
    
    return dp[m-1][n-1];
}
/*
Time Complexity: O(m * n) - Poore grid ko ek baar traverse karte hain.
Space Complexity: O(m * n) - DP table ke liye. (Ise O(n) mein optimize kiya ja sakta hai).
*/
```

-----

## 3\. Unique Paths II (With Obstacles)

### Problem Statement (Hinglish)

Yeh *Unique Paths* jaisa hi hai, lekin ab grid mein kuch **obstacles** (badhaayein) bhi hain, jo `1` se mark ki gayi hain. Aapko `0` se mark kiye gaye cells se path banana hai. Obstacle par nahi ja sakte.

### Example

**Input:** `obstacleGrid = [[0,0,0],[0,1,0],[0,0,0]]`
**Output:** `2`

### Approach (Hinglish)

#### Optimal Approach (Dynamic Programming)

Logic same rahega, bas obstacles ko handle karna hai.

  - **Recurrence Relation:**
      - Agar `grid[i][j] == 1` (obstacle), to `dp[i][j] = 0`.
      - Agar `grid[i][j] == 0`, to `dp[i][j] = dp[i-1][j] + dp[i][j-1]`.
  - **Base Case:**
      - Agar start `(0,0)` hi obstacle hai, to `0` paths honge.
      - Pehli row aur column ko fill karte waqt, agar koi obstacle milta hai, to uske aage ke saare cells tak pahunchne ke `0` ways honge.

### C++ Code

```cpp
// Optimal Approach: Tabulation DP
int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
    int m = obstacleGrid.size();
    int n = obstacleGrid[0].size();
    
    // DP table long long lo taki overflow na ho.
    vector<vector<long long>> dp(m, vector<long long>(n, 0));
    
    // Agar start ya end hi obstacle hai
    if (obstacleGrid[0][0] == 1 || obstacleGrid[m-1][n-1] == 1) return 0;
    
    dp[0][0] = 1;

    // Pehla column fill karo
    for (int i = 1; i < m; i++) {
        if (obstacleGrid[i][0] == 0) {
            dp[i][0] = dp[i-1][0];
        }
    }
    
    // Pehli row fill karo
    for (int j = 1; j < n; j++) {
        if (obstacleGrid[0][j] == 0) {
            dp[0][j] = dp[0][j-1];
        }
    }
    
    for (int i = 1; i < m; i++) {
        for (int j = 1; j < n; j++) {
            if (obstacleGrid[i][j] == 0) {
                dp[i][j] = dp[i-1][j] + dp[i][j-1];
            }
        }
    }
    
    return dp[m-1][n-1];
}
/*
Time Complexity: O(m * n)
Space Complexity: O(m * n)
*/
```

-----

## 4\. A Batsman Scores Target using Only 1, 4, 6

### Problem Statement (Hinglish)

Ek batsman ko `target` runs banane hain. Woh har ball par sirf `1`, `4`, ya `6` run bana sakta hai. Aise kitne alag-alag sequences hain jisse woh `target` score tak pahunch sakta hai?

### Example

**Input:** `target = 5`
**Output:** `3`
**Explanation:** Sequences hain: `{1,1,1,1,1}`, `{1,4}`, `{4,1}`.

### Approach (Hinglish)

#### Optimal Approach (Dynamic Programming)

Let `dp[i]` = `i` runs banane ke total tareeke.

  - `i` runs banane ke liye, aakhri shot ya to `1`, `4`, ya `6` ka ho sakta hai.
  - **Recurrence Relation:** `dp[i] = dp[i-1] + dp[i-4] + dp[i-6]`
  - **Base Case:** `dp[0] = 1` (0 run banane ka ek tareeka: koi run na banana).

### C++ Code

```cpp
// Approach 1: Recursive DP (Memoization)
int solveMemo(int target, vector<int>& memo) {
    if (target == 0) return 1;
    if (target < 0) return 0;
    if (memo[target] != -1) return memo[target];
    
    int ways = 0;
    ways += solveMemo(target - 1, memo); // 1 run maara
    ways += solveMemo(target - 4, memo); // 4 run maara
    ways += solveMemo(target - 6, memo); // 6 run maara
    
    return memo[target] = ways;
}

int countWaysRecursive(int target) {
    vector<int> memo(target + 1, -1);
    return solveMemo(target, memo);
}

// Approach 2: Iterative DP (Tabulation)
int countWaysIterative(int target) {
    vector<int> dp(target + 1, 0);
    dp[0] = 1; // Base case

    for (int i = 1; i <= target; ++i) {
        if (i >= 1) dp[i] += dp[i-1];
        if (i >= 4) dp[i] += dp[i-4];
        if (i >= 6) dp[i] += dp[i-6];
    }
    return dp[target];
}
/*
Time Complexity: O(target) - Dono approaches ke liye.
Space Complexity: O(target) - DP array/recursion stack ke liye.
*/
```

-----

## 5\. Wildcard Pattern Matching

### Problem Statement (Hinglish)

Aapko ek string `s` (text) aur ek pattern `p` diya gaya hai. Pattern mein do special characters ho sakte hain:

  - `?`: Kisi bhi ek character se match karta hai.
  - `*`: Kisi bhi sequence of characters (including empty sequence) se match karta hai.
    Aapko batana hai ki kya pattern `p` poori string `s` se match karta hai.

### Example

**Input:** `s = "adceb"`, `p = "*a*b"`
**Output:** `true`

### Approach (Hinglish)

#### Optimal Approach (Dynamic Programming)

Let `dp[i][j]` = `true` agar `s` ka `i` length ka prefix, `p` ke `j` length ke prefix se match karta hai.

  - **Base Case:** `dp[0][0] = true` (empty string, empty pattern).
  - **Cases for `p[j-1]`:**
    1.  **`p[j-1]` is a character or `?`**: Match tabhi hoga jab `s[i-1]` same character ho (ya `p` mein `?` ho) AUR `s` aur `p` ke pehle ke prefixes bhi match karte hon. `dp[i][j] = (s[i-1] == p[j-1] || p[j-1] == '?') && dp[i-1][j-1]`
    2.  **`p[j-1]` is `*`**: `*` do kaam kar sakta hai:
          - **Empty Sequence**: `*` ko ignore karo. Match `dp[i][j-1]` par depend karega.
          - **One or more characters**: `*` ne `s[i-1]` ko match kiya. Ab `*` ko `s` ke baaki characters se match karna hai. Match `dp[i-1][j]` par depend karega.
          - So, `dp[i][j] = dp[i][j-1] || dp[i-1][j]`

### C++ Code

```cpp
// Optimal Approach: Tabulation DP
bool isMatch(string s, string p) {
    int m = s.length();
    int n = p.length();
    
    vector<vector<bool>> dp(m + 1, vector<bool>(n + 1, false));
    dp[0][0] = true; // Empty string matches empty pattern
    
    // Handle patterns like a*, a*b*, *
    for (int j = 1; j <= n; j++) {
        if (p[j-1] == '*') {
            dp[0][j] = dp[0][j-1];
        }
    }
    
    for (int i = 1; i <= m; i++) {
        for (int j = 1; j <= n; j++) {
            if (p[j-1] == '*') {
                dp[i][j] = dp[i][j-1] || dp[i-1][j];
            } else if (p[j-1] == '?' || s[i-1] == p[j-1]) {
                dp[i][j] = dp[i-1][j-1];
            } else {
                dp[i][j] = false;
            }
        }
    }
    
    return dp[m][n];
}
/*
Time Complexity: O(m * n)
Space Complexity: O(m * n)
*/
```

-----

## 6\. Longest Valid Parentheses

### Problem Statement (Hinglish)

Aapko ek string di gayi hai jisme sirf `(` aur `)` hain. Aapko sabse lambe valid (well-formed) parentheses **substring** ki length nikalni hai.

### Example

**Input:** `s = ")()())"`
**Output:** `4`
**Explanation:** Sabse lamba valid substring "()()" hai, jiski length 4 hai.

### Approaches (Hinglish)

#### Brute Force Approach

Saare possible substrings (`O(N^2)`) generate karo aur har ek ko check karo ki woh valid hai ya nahi (`O(N)`). Total `O(N^3)`. Bahut slow hai.

#### Stack-based Approach

Ek stack use karo jo indices store karega. Shuru mein stack mein `-1` daal do (yeh base ka kaam karega). Jab `(` aaye to index push karo. Jab `)` aaye to pop karo. Pop karne ke baad, abhi ke index aur stack ke top element ke index ka difference nikal kar max length update karo.

#### Optimal Approach (Dynamic Programming)

Let `dp[i]` = `i`-th index par **end** hone wale longest valid parentheses ki length.

  - Agar `s[i] == '('`, to `dp[i] = 0`.
  - Agar `s[i] == ')'`:
      - **Case 1: `s[i-1] == '('`** (like `...()`). Length = 2 + isse pehle wale valid substring ki length. `dp[i] = dp[i-2] + 2`.
      - **Case 2: `s[i-1] == ')'`** (like `...))` ). Hum `s[i]` ke matching `(` ko dhoondhte hain. Agar `i-1` par end hone wale valid part ki length `L = dp[i-1]` hai, to matching `(` `i-L-1` par ho sakta hai. Agar wahan `(` milta hai, to total length = `L` + `2` + isse pehle (`i-L-2`) ke valid part ki length.

### C++ Code

```cpp
// Approach 2: Stack-based
int longestValidParentheses_Stack(string s) {
    stack<int> st;
    st.push(-1);
    int maxLength = 0;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] == '(') {
            st.push(i);
        } else {
            st.pop();
            if (st.empty()) {
                st.push(i);
            } else {
                maxLength = max(maxLength, i - st.top());
            }
        }
    }
    return maxLength;
}

// Approach 3: Optimal DP
int longestValidParentheses_DP(string s) {
    int n = s.length();
    if (n < 2) return 0;
    
    vector<int> dp(n, 0);
    int maxLength = 0;
    
    for (int i = 1; i < n; i++) {
        if (s[i] == ')') {
            if (s[i-1] == '(') { // Case: ...()
                dp[i] = (i >= 2 ? dp[i-2] : 0) + 2;
            } else { // Case: ...))
                int prev_len = dp[i-1];
                if (i - prev_len - 1 >= 0 && s[i - prev_len - 1] == '(') {
                    dp[i] = prev_len + 2 + (i - prev_len - 2 >= 0 ? dp[i - prev_len - 2] : 0);
                }
            }
        }
        maxLength = max(maxLength, dp[i]);
    }
    return maxLength;
}
/*
Stack & DP Approach:
Time Complexity: O(N) - Ek hi pass mein solution mil jata hai.
Space Complexity: O(N) - Stack ya DP array ke liye.
*/
```

----


## 1\. Letter Combination of a Phone Number

### Problem Statement (Hinglish)

Aapko `2` se `9` tak ke digits ka ek string diya gaya hai. Ek purane phone ke keypad par har digit kuch letters ko represent karta hai (jaise `2` -\> `abc`, `3` -\> `def`). Aapko saare possible letter combinations return karne hain jo in digits se ban sakte hain.

### Example

**Input:** `digits = "23"`
**Output:** `["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"]`

### Approach (Hinglish)

#### Optimal Approach (Backtracking)

Yeh ek classic recursion aur backtracking problem hai. Hum har digit ke liye ek letter chunte jayenge aur combination banayenge.

1.  Sabse pehle, ek mapping bana lo jo har digit ko uske corresponding letters se jodti hai.
2.  Ek recursive function `solve(index, current_combination)` likho.
3.  **Base Case:** Jab `index` input `digits` string ki length ke barabar ho jaye, iska matlab ek poora combination ban gaya hai. Use result list mein add kar do.
4.  **Recursive Step:**
      * Current digit (`digits[index]`) ke saare possible letters nikalo.
      * Har letter ke liye:
          * Use `current_combination` mein add karo.
          * Agli digit ke liye `solve(index + 1, ...)` call karo.
          * Call ke baad, us letter ko `current_combination` se **hata do** (yeh **backtracking** step hai), taaki agle combination ke liye jagah ban sake.

### C++ Code

```cpp
// Optimal Approach: Backtracking
class Solution {
public:
    vector<string> letterCombinations(string digits) {
        if (digits.empty()) return {};
        
        vector<string> result;
        string current_combo;
        vector<string> mapping = {"", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};
        
        function<void(int)> solve = 
            [&](int index) {
            // Base case: Jab saare digits process ho gaye
            if (index == digits.length()) {
                result.push_back(current_combo);
                return;
            }
            
            // Current digit ke liye letters nikalo
            string letters = mapping[digits[index] - '0'];
            
            // Har letter ko try karo
            for (char letter : letters) {
                current_combo.push_back(letter);       // Choose
                solve(index + 1);                      // Explore
                current_combo.pop_back();              // Unchoose (Backtrack)
            }
        };
        
        solve(0);
        return result;
    }
};
/*
Time Complexity: O(4^N * N), jahan N digits ki length hai. Har digit ke max 4 options ho sakte hain. N se multiply final combinations ko copy karne ke liye.
Space Complexity: O(N) - Recursion stack ki depth.
*/
```

-----

## 2\. Find Unique Element in a Sorted Array

### Problem Statement (Hinglish)

Aapko ek **sorted** integer array diya gaya hai. Ismein har element theek do baar aata hai, siwaye ek element ke jo sirf ek baar aata hai. Aapko woh unique (ek baar aane wala) element dhoondhna hai.

### Example

**Input:** `nums = [1, 1, 2, 3, 3, 4, 4, 8, 8]`
**Output:** `2`

### Approach (Hinglish)

#### Optimal Approach (Modified Binary Search)

Hum is problem ko `O(log N)` time mein binary search se solve kar sakte hain. Normal array mein, pairs `(arr[0], arr[1])`, `(arr[2], arr[3])`... aise hote. Unique element is pattern ko tod deta hai.

1.  Hum binary search `low`, `high` pointers se start karenge.
2.  Middle index `mid` nikalo. Hum `mid` ko hamesha ek **even** index par laane ki koshish karenge. Agar `mid` odd hai, to use `mid--` kar do. Aisa karne se hum hamesha ek pair `(arr[mid], arr[mid+1])` ko check kar sakte hain.
3.  **Check:**
      * Agar `arr[mid] == arr[mid+1]`, iska matlab `mid` tak sab kuch theek hai aur unique element right side mein hai. To hum search space ko `low = mid + 2` kar denge.
      * Agar `arr[mid] != arr[mid+1]`, iska matlab unique element ya to `mid` par hai ya uske left mein. To hum search space ko `high = mid` kar denge.
4.  Jab `low == high` ho jayega, wahi hamara answer hoga.

*(Note: Agar array sorted na hota, to sabse aasan tareeka **XOR** hota. Saare elements ka XOR lene se pairs cancel ho jate aur sirf unique element bachta.)*

### C++ Code

```cpp
// Optimal Approach: Modified Binary Search
int singleNonDuplicate(vector<int>& nums) {
    int low = 0;
    int high = nums.size() - 1;
    
    while (low < high) {
        int mid = low + (high - low) / 2;
        
        // Mid ko even index par adjust karo
        if (mid % 2 == 1) {
            mid--;
        }
        
        // Check karo ki pair theek hai ya nahi
        if (nums[mid] == nums[mid + 1]) {
            // Pattern theek hai, unique element right mein hai
            low = mid + 2;
        } else {
            // Pattern toot gaya, unique element left mein (ya mid par) hai
            high = mid;
        }
    }
    
    return nums[low];
}
/*
Time Complexity: O(log N) - Binary search ke kaaran.
Space Complexity: O(1) - Koi extra space nahi.
*/
```

-----

## 3\. Find The Repeating And Missing Number

### Problem Statement (Hinglish)

Aapko `1` se `N` tak ke numbers ka ek unsorted array diya gaya hai, jiska size `N` hai. Is array mein, ek number `A` do baar aa raha hai (repeating) aur ek number `B` gayab hai (missing). Aapko `A` aur `B` dhoondhne hain.

### Example

**Input:** `arr = [3, 1, 2, 5, 3]`, `N=5`
**Output:** Repeating = `3`, Missing = `4`

### Approaches (Hinglish)

#### Approach 1: Mathematical Sums

1.  `1` se `N` tak ke numbers ka expected sum (`S_N`) aur sum of squares (`S2_N`) nikalo.
      * $S\_N = N(N+1)/2$
      * $S2\_N = N(N+1)(2N+1)/6$
2.  Diye gaye array ka actual sum (`S_arr`) aur sum of squares (`S2_arr`) nikalo.
3.  Let repeating number be `X` and missing be `Y`.
      * $S\_{arr} - S\_N = X - Y$
      * $S2\_{arr} - S2\_N = X^2 - Y^2 = (X-Y)(X+Y)$
4.  In do equations ko solve karke `X` aur `Y` nikal lo.

#### Approach 2: XOR Technique

1.  Saare array elements aur `1` se `N` tak ke saare numbers ka aapas mein XOR lo.
    `xor_sum = (arr[0]^arr[1]...^arr[N-1]) ^ (1^2...^N)`
    Isse `xor_sum = X ^ Y` milega.
2.  `xor_sum` ka **rightmost set bit** (sabse pehla `1` right se) nikalo. Yeh bit `X` aur `Y` mein alag-alag hoga.
3.  Ab saare numbers (array ke bhi aur 1 se N tak ke bhi) ko do groups mein baanto - ek jisme yeh bit `1` hai, aur dusra jisme yeh `0` hai.
4.  Dono groups ke numbers ka alag-alag XOR lo. Ek group ka result `X` hoga aur dusre ka `Y`.

### C++ Code

```cpp
// Optimal Approach: XOR Technique
vector<int> findRepeatingAndMissing_XOR(const vector<int> &A) {
    long long n = A.size();
    int xor_sum = 0;
    
    // Step 1: X^Y nikalo
    for(int i = 0; i < n; i++) {
        xor_sum ^= A[i];
        xor_sum ^= (i + 1);
    }
    
    // Step 2: Rightmost set bit nikalo
    int rightmost_set_bit = xor_sum & -xor_sum;
    
    int x = 0, y = 0; // x = repeating, y = missing
    
    // Step 3: Numbers ko do groups me baanto
    for(int i = 0; i < n; i++) {
        if(A[i] & rightmost_set_bit) {
            x ^= A[i];
        } else {
            y ^= A[i];
        }
        
        if((i + 1) & rightmost_set_bit) {
            x ^= (i + 1);
        } else {
            y ^= (i + 1);
        }
    }
    
    // Check karo kaun sa repeating hai aur kaun sa missing
    for(int i = 0; i < n; i++) {
        if (A[i] == x) {
            return {x, y}; // x repeating, y missing
        }
    }
    return {y, x}; // y repeating, x missing
}

/*
Time Complexity: O(N) - Ek hi pass mein solution.
Space Complexity: O(1) - Koi extra space nahi.
*/
```

-----

## 4\. Find Element in Rotated Sorted Array

### Problem Statement (Hinglish)

Aapko ek sorted array diya gaya hai jo kisi unknown pivot par rotate kiya gaya hai (e.g., `[0,1,2,4,5,6,7]` se `[4,5,6,7,0,1,2]`). Aapko ek `target` value di gayi hai. Agar `target` array mein hai, to uska index return karo, warna `-1`. Array mein duplicates nahi hain.

### Example

**Input:** `nums = [4,5,6,7,0,1,2]`, `target = 0`
**Output:** `4`

### Approach (Hinglish)

#### Optimal Approach (Modified Binary Search)

Hum standard binary search ko thoda modify karenge. Har step par, hum check karenge ki `mid` ke left ya right mein se kaun sa part sorted hai.

1.  Binary search `low`, `high`, `mid` se start karo.
2.  Check karo ki left part (`nums[low]` se `nums[mid]`) sorted hai ya nahi. Yeh tabhi hoga jab `nums[low] <= nums[mid]`.
      * **Agar left part sorted hai:** Check karo ki `target` is sorted part ki range mein hai (`nums[low] <= target < nums[mid]`).
          * Agar haan, to right part ko discard karo (`high = mid - 1`).
          * Agar nahi, to left part ko discard karo (`low = mid + 1`).
      * **Agar left part sorted nahi hai:** Iska matlab right part (`nums[mid]` se `nums[high]`) zaroor sorted hoga.
          * Check karo ki `target` is right sorted part ki range mein hai (`nums[mid] < target <= nums[high]`).
          * Agar haan, to left part ko discard karo (`low = mid + 1`).
          * Agar nahi, to right part ko discard karo (`high = mid - 1`).
3.  Jab `low > high` ho jaye to loop khatam.

### C++ Code

```cpp
// Optimal Approach: Modified Binary Search
int search(vector<int>& nums, int target) {
    int low = 0, high = nums.size() - 1;
    
    while (low <= high) {
        int mid = low + (high - low) / 2;
        
        if (nums[mid] == target) {
            return mid;
        }
        
        // Check karo ki left part sorted hai ya nahi
        if (nums[low] <= nums[mid]) {
            // Agar target left sorted part me hai
            if (target >= nums[low] && target < nums[mid]) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        } 
        // Matlab right part sorted hai
        else {
            // Agar target right sorted part me hai
            if (target > nums[mid] && target <= nums[high]) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
    }
    
    return -1;
}
/*
Time Complexity: O(log N)
Space Complexity: O(1)
*/
```

-----

## 5\. Count Subarrays with Given XOR

### Problem Statement (Hinglish)

Aapko ek integer array `A` aur ek integer `B` diya gaya hai. Aapko un subarrays ki total sankhya batani hai jinka XOR sum `B` ke barabar hai.

### Example

**Input:** `A = [4, 2, 2, 6, 4]`, `B = 6`
**Output:** `4`
**Explanation:** Subarrays with XOR 6 hain: `{6}`, `{4, 2}`, `{2, 2, 6}`, `{4, 2, 2, 6, 4}`.

### Approach (Hinglish)

#### Optimal Approach (Prefix XOR with Hashmap)

Yeh "Subarray with Given Sum" problem jaisa hi hai, bas `+` ki jagah `^` (XOR) hai.

1.  Let `prefix_xor` be the XOR from start of array to current index `i`.
2.  Hum ek subarray `[j..i]` ka XOR nikalna chahte hain.
    `XOR(j..i) = prefix_xor[i] ^ prefix_xor[j-1]`
3.  Humein `XOR(j..i) == B` chahiye.
    `prefix_xor[i] ^ prefix_xor[j-1] = B`
    Isko rearrange karne par: `prefix_xor[j-1] = prefix_xor[i] ^ B`.
4.  **Algorithm:**
      * Ek `map` banayeinge jo `prefix_xor` ki frequency store karega.
      * Array ko traverse karo, har step par `current_xor` maintain karo.
      * Har index `i` par, hum `y = current_xor ^ B` dhoondhenge. `map` mein `y` ki jitni frequency hogi, utne hi naye subarrays `i` par khatam honge jinka XOR `B` hai.
      * Count update karo aur `current_xor` ki frequency `map` mein badha do.

### C++ Code

```cpp
// Optimal Approach: Prefix XOR with Hashmap
int countSubarraysWithXOR(vector<int> &A, int B) {
    unordered_map<int, int> prefix_xor_freq;
    int count = 0;
    int current_xor = 0;
    
    // Shuru mein, ek prefix_xor 0 hota hai (empty subarray).
    prefix_xor_freq[0] = 1;
    
    for (int x : A) {
        // Current prefix xor update karo
        current_xor ^= x;
        
        // y = current_xor ^ B dhoondho
        int y = current_xor ^ B;
        
        // Agar y map me hai, to count badhao
        if (prefix_xor_freq.count(y)) {
            count += prefix_xor_freq[y];
        }
        
        // Current prefix_xor ki frequency badhao
        prefix_xor_freq[current_xor]++;
    }
    
    return count;
}
/*
Time Complexity: O(N) - Ek hi pass mein. Map operations O(1) on average.
Space Complexity: O(N) - Worst case mein map saare unique prefix xors store karega.
*/
```

----


## 1\. Connect N Ropes with Minimum Cost

### Problem Statement (Hinglish)

Aapko `N` ropes (rassiyan) di gayi hain, har ek ki alag-alag length hai. Do ropes ko jodne ka cost unki lengths ke sum ke barabar hota hai. Aapko saari ropes ko jodkar ek single rope banani hai. Aisa karne ka **minimum** possible cost kya hoga?

### Example

**Input:** Ropes `[4, 3, 2, 6]`
**Output:** `29`
**Explanation:**

1.  Sabse choti ropes `2` aur `3` ko jodo. Cost = `5`. Ab ropes hain: `[4, 6, 5]`. Total cost ab tak: `5`.
2.  Ab sabse choti ropes `4` aur `5` ko jodo. Cost = `9`. Ab ropes hain: `[6, 9]`. Total cost ab tak: `5 + 9 = 14`.
3.  Aakhri do ropes `6` aur `9` ko jodo. Cost = `15`. Ab rope hai: `[15]`. Final cost: `14 + 15 = 29`.

### Approach (Hinglish)

#### Optimal Approach (Greedy with Min-Heap)

Yeh ek classic **greedy** problem hai. Har step par, agar hum hamesha do **sabse choti** ropes ko jodenge, to overall cost minimum hoga. Is approach ko efficiently implement karne ke liye hum **min-heap** (C++ mein `priority_queue`) ka use karte hain.

1.  Ek min-heap banao aur usme saari rope lengths daal do.
2.  Jab tak heap mein ek se zyada rope bachi hai, loop chalao:
      * Heap se do sabse choti ropes nikalo (heap ka top do baar pop karo).
      * In dono lengths ko jodo. Yeh is step ka cost hai. Is cost ko ek `total_cost` variable mein add karte jao.
      * Jo nayi rope bani hai (jiska length dono ka sum hai), use wapas heap mein daal do.
3.  Jab loop khatam hoga, `total_cost` mein minimum possible cost hoga.

### C++ Code

```cpp
// Optimal Approach: Min-Heap
long long connectRopes(int* arr, int n) {
    // Min-heap
    priority_queue<int, vector<int>, greater<int>> min_heap;
    
    // Saari ropes ko heap me daalo
    for(int i = 0; i < n; i++) {
        min_heap.push(arr[i]);
    }
    
    long long total_cost = 0;
    
    // Jab tak ek hi rope na bach jaye
    while(min_heap.size() > 1) {
        // Do sabse choti ropes nikalo
        int first = min_heap.top();
        min_heap.pop();
        int second = min_heap.top();
        min_heap.pop();
        
        // Unhe jodo aur cost calculate karo
        long long current_cost = first + second;
        total_cost += current_cost;
        
        // Nayi rope ko wapas heap me daalo
        min_heap.push(current_cost);
    }
    
    return total_cost;
}
/*
Time Complexity: O(N log N) - N ropes ko heap mein daalne aur har baar nikalne ke liye.
Space Complexity: O(N) - Heap ko store karne ke liye.
*/
```

-----

## 2\. Convert Number to Words

### Problem Statement (Hinglish)

Aapko ek non-negative integer (0 ya usse bada) diya gaya hai. Aapko use English words mein convert karna hai. Number `2^31 - 1` tak ho sakta hai.

### Example

**Input:** `12345`
**Output:** `"Twelve Thousand Three Hundred Forty Five"`

### Approach (Hinglish)

#### Optimal Approach (Grouping by Thousands)

Hum number ko 3-digit ke chunks mein process karenge. Har chunk "Thousand", "Million", "Billion" jaise units ko represent karega.

1.  Sabse pehle, words ke liye arrays/vectors bana lo:
      * `ones[]`: "One", "Two", ... "Nine"
      * `teens[]`: "Ten", "Eleven", ... "Nineteen"
      * `tens[]`: "", "", "Twenty", "Thirty", ... "Ninety"
2.  Ek helper function `convertChunk(num)` banao jo `0` se `999` tak ke number ko words mein badalta hai. Yeh function hundreds, tens, aur ones place ko handle karega.
3.  Main logic mein, input number ko `1000` se repeatedly divide karo.
4.  Har baar, remainder (jo `0-999` ke beech hoga) ko `convertChunk` function se words mein convert karo aur uske aage appropriate unit (`"Thousand"`, `"Million"`, etc.) jodo.
5.  Saare parts ko reverse order mein jodkar final string banao. Edge cases (jaise `0` aur extra spaces) ka dhyan rakho.

### C++ Code

```cpp
// Direct Conversion Approach
class Solution {
private:
    vector<string> ones = {"", "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine"};
    vector<string> teens = {"Ten", "Eleven", "Twelve", "Thirteen", "Fourteen", "Fifteen", "Sixteen", "Seventeen", "Eighteen", "Nineteen"};
    vector<string> tens = {"", "", "Twenty", "Thirty", "Forty", "Fifty", "Sixty", "Seventy", "Eighty", "Ninety"};

    // 1000 se chote number ko convert karne wala function
    string convertChunk(int n) {
        if (n >= 100) {
            return ones[n / 100] + " Hundred" + (n % 100 == 0 ? "" : " " + convertChunk(n % 100));
        } else if (n >= 20) {
            return tens[n / 10] + (n % 10 == 0 ? "" : " " + ones[n % 10]);
        } else if (n >= 10) {
            return teens[n - 10];
        } else if (n > 0) {
            return ones[n];
        }
        return "";
    }
    
public:
    string numberToWords(int num) {
        if (num == 0) return "Zero";
        
        string result = "";
        vector<string> units = {"", "Thousand", "Million", "Billion"};
        int i = 0;
        
        while (num > 0) {
            int chunk = num % 1000;
            if (chunk != 0) {
                string chunk_str = convertChunk(chunk);
                result = chunk_str + (i > 0 ? " " + units[i] : "") + (result.empty() ? "" : " " + result);
            }
            num /= 1000;
            i++;
        }
        
        return result;
    }
};
/*
Time Complexity: O(log10(N)) ya O(1) - Kyunki number of digits limited hai. Har 3 digits ke liye constant time lagta hai.
Space Complexity: O(log10(N)) ya O(1) - Result string ki length.
*/
```

-----

## 3\. Implement Stack using Queue

### Problem Statement (Hinglish)

Aapko sirf **queue** data structure ka use karke ek **stack** (LIFO - Last In, First Out) implement karna hai. Stack ke `push`, `pop`, `top`, aur `empty` operations implement karne hain.

### Approach (Hinglish)

#### Optimal Approach (Using a Single Queue)

Hum ek hi queue ka use karke `push` operation ko thoda mehenga banakar stack implement kar sakte hain. Idea yeh hai ki har `push` ke baad, naya element hamesha queue ke front mein aa jaye.

  * **`push(x)`:**
    1.  Naye element `x` ko queue ke end mein add karo.
    2.  Ab, queue ke pehle se maujood saare `size - 1` elements ko ek-ek karke queue se nikalo (dequeue) aur wapas queue ke end mein daal do (enqueue).
    3.  Is rotation se naya element `x` ab queue ke front mein aa gaya hai.
  * **`pop()`:** Queue ke front se element hata do (`q.pop()`), kyunki sabse naya element wahi hai.
  * **`top()`:** Queue ka front element (`q.front()`) return karo.
  * **`empty()`:** Check karo ki queue empty hai ya nahi (`q.empty()`).

### C++ Code

```cpp
// Single Queue Approach
class MyStack {
public:
    queue<int> q;

    MyStack() {}
    
    // Naye element ko push karo aur queue ko rotate karo
    void push(int x) {
        int s = q.size();
        q.push(x);
        for (int i = 0; i < s; i++) {
            q.push(q.front());
            q.pop();
        }
    }
    
    // Front se pop karo
    int pop() {
        int top_val = q.front();
        q.pop();
        return top_val;
    }
    
    // Front ko return karo
    int top() {
        return q.front();
    }
    
    bool empty() {
        return q.empty();
    }
};

/*
Time Complexity:
- push: O(N) - Har push par queue rotate hoti hai.
- pop: O(1)
- top: O(1)
- empty: O(1)
Space Complexity: O(N) - Elements ko store karne ke liye.
*/
```

-----

## 4\. Implement a Hash Table

### Problem Statement (Hinglish)

Ek basic Hash Table (ya Hash Map) data structure implement karo jo `string` keys aur `int` values ko store kare. Isme `insert(key, value)`, `search(key)`, aur `remove(key)` operations hone chahiye. Collision ko **separate chaining** (linked list) se handle karo.

### Approach (Hinglish)

1.  **Main Structure:** Ek `vector` of `list<pair<string, int>>` banayenge. Yeh vector hamara **bucket array** hoga. Har index ek "bucket" hai, aur har bucket ek linked list hai jisme `(key, value)` pairs store honge.
2.  **Hash Function:** Ek simple hash function banayenge. Yeh `key` (string) ko lega aur ek integer hash code generate karega. Is hash code ko `table_size` se modulo karke bucket ka index nikalenge.
3.  **`insert(key, value)`:**
      * Key ka hash use karke bucket index (`idx`) nikalo.
      * `table[idx]` (linked list) mein iterate karo. Agar key pehle se hai, to uski value update kar do.
      * Agar key nahi milti, to list ke end mein naya `(key, value)` pair add kar do.
4.  **`search(key)`:**
      * Bucket index nikalo.
      * Bucket ki linked list mein search karo. Agar key mil jaye to value return karo, warna error ya default value (e.g., -1) return karo.
5.  **`remove(key)`:**
      * Bucket index nikalo.
      * Bucket ki linked list mein key ko dhoondh kar remove kar do.

### C++ Code

```cpp
// Hash Table with Separate Chaining
class HashTable {
private:
    int TABLE_SIZE;
    vector<list<pair<string, int>>> table;

    // Simple hash function
    int hashFunction(string key) {
        int hash_val = 0;
        for (char c : key) {
            hash_val += c;
        }
        return hash_val % TABLE_SIZE;
    }

public:
    HashTable(int size) {
        TABLE_SIZE = size;
        table.resize(TABLE_SIZE);
    }

    void insert(string key, int value) {
        int index = hashFunction(key);
        for (auto& pair : table[index]) {
            if (pair.first == key) {
                pair.second = value; // Update if key exists
                return;
            }
        }
        table[index].push_back({key, value}); // Insert new pair
    }

    int search(string key) {
        int index = hashFunction(key);
        for (const auto& pair : table[index]) {
            if (pair.first == key) {
                return pair.second; // Key found
            }
        }
        return -1; // Key not found
    }

    void remove(string key) {
        int index = hashFunction(key);
        table[index].remove_if([&](const pair<string, int>& pair) {
            return pair.first == key;
        });
    }
};

/*
Average Case Time Complexity (assuming good hash function):
- insert: O(1)
- search: O(1)
- remove: O(1)
Worst Case Time Complexity (sare keys ek hi bucket me): O(N)
Space Complexity: O(N + K) - jahan N total elements hain aur K table ka size hai.
*/
```


----