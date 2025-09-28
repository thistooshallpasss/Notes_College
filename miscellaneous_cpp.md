

# 📘 C++ Formula Sheet (String + Vector)

---

## 🔹 String (`std::string`)

### ✅ Declaration

```cpp
string s = "hello";
string s(n, 'x');     // n times 'x'
```

### ✅ Size & Access

```cpp
s.size();             // length of string
s.length();           // same as size()
s.empty();            // true if empty
s[i];                 // access ith char
s.at(i);              // safe access with bounds check
s.front();            // first character
s.back();             // last character
```

### ✅ Modifications

```cpp
s.push_back('a');     // add char at end
s.pop_back();         // remove last char
s += "world";         // append string
s.append("xyz");      // append
s.insert(pos, "abc"); // insert at pos
s.erase(pos, len);    // erase substring
s.clear();            // empty string
s.replace(pos, len, "new"); // replace substring
reverse(s.begin(), s.end()); // reverse string
```

### ✅ Substrings

```cpp
s.substr(pos, len);   // substring from pos
```

### ✅ Search

```cpp
s.find("abc");        // first index of "abc" (npos if not found)
s.rfind("abc");       // last index
s.find_first_of("abc");   // first occurrence of any char from "abc"
s.find_last_of("abc");    // last occurrence
s.find_first_not_of("abc"); // first not in "abc"
s.find_last_not_of("abc");
```

### ✅ Conversion

```cpp
stoi("123");          // string → int
stol("123");          // string → long
stoll("123");         // string → long long
stoul("123");         // string → unsigned long
stof("3.14");         // string → float
stod("3.14");         // string → double
to_string(123);       // number → string
```

### ✅ Comparison

```cpp
s == "abc";           // equality
s.compare("abc");     // <0, =0, >0
```

---

## 🔹 Vector (`std::vector<T>`)

### ✅ Declaration

```cpp
vector<int> v;               // empty
vector<int> v(n);            // size n, all 0
vector<int> v(n, val);       // size n, all val
vector<int> v2(v);           // copy
```

### ✅ Size & Capacity

```cpp
v.size();               // current size
v.capacity();           // allocated capacity
v.empty();              // check empty
v.resize(n);            // change size
v.shrink_to_fit();      // reduce capacity
```

### ✅ Access

```cpp
v[i];                   // element
v.at(i);                // safe element
v.front();              // first element
v.back();               // last element
```

### ✅ Modifications

```cpp
v.push_back(x);         // add element at end
v.pop_back();           // remove last element
v.insert(v.begin()+i, x); // insert x at i
v.erase(v.begin()+i);   // erase at i
v.erase(v.begin()+l, v.begin()+r); // erase range [l,r)
v.clear();              // remove all
v.assign(n, val);       // fill with val
swap(v1, v2);           // swap contents
```

### ✅ Iterators

```cpp
v.begin();              // iterator to first
v.end();                // iterator past last
v.rbegin();             // reverse begin
v.rend();               // reverse end
```

### ✅ Algorithms (need `<algorithm>`)

```cpp
sort(v.begin(), v.end());        // ascending
sort(v.rbegin(), v.rend());      // descending
reverse(v.begin(), v.end());     // reverse
max_element(v.begin(), v.end()); // iterator to max
min_element(v.begin(), v.end()); // iterator to min
find(v.begin(), v.end(), x);     // iterator to x
count(v.begin(), v.end(), x);    // frequency of x
accumulate(v.begin(), v.end(), 0); // sum (need <numeric>)
```

### ✅ Others

```cpp
vector<int> v = {1,2,3};   // initializer list
for(auto x : v) cout<<x;   // range loop
```

---

## 🔹 Extra Useful Tricks

* **Sort with custom comparator**

```cpp
sort(v.begin(), v.end(), greater<int>()); // descending
```

* **2D Vector**

```cpp
vector<vector<int>> mat(n, vector<int>(m, 0));
```

* **Remove duplicates**

```cpp
sort(v.begin(), v.end());
v.erase(unique(v.begin(), v.end()), v.end());
```

---
# 📘 C++ String & Vector Remaining Functions (Revision Add-ons)

---

## 🔹 `std::string` (Remaining)

* `capacity()` → kitni memory allocate hui hai.
* `reserve(n)` → at least `n` characters ke liye memory reserve.
* `shrink_to_fit()` → extra memory free.
* `c_str()` → C-style `const char*` string pointer return karta hai.
* `data()` → same as `c_str()` but non-const bhi de sakta hai.
* `copy(char* buf, len, pos=0)` → substring ko buffer mein copy karta hai.
* `swap(str2)` → do strings ke contents swap.

---

## 🔹 `std::vector<T>` (Remaining)

* `operator[]` / `at(i)` → element access (already covered but dono alag hote hain: `at()` bounds check karta hai).
* `capacity()` → allocated storage.
* `reserve(n)` → kam se kam `n` elements ke liye space reserve.
* `shrink_to_fit()` → extra memory free.
* `assign(count, value)` → vector ko overwrite karke `count` copies of `value`.
* `emplace_back(args...)` → element ko directly construct karke end mein daalta hai (faster than `push_back`).
* `emplace(iterator, args...)` → given position par element construct.
* `swap(v2)` → do vectors ke contents swap.
* `clear()` → saare elements hata deta hai (size=0, capacity same).

---
# 📘 C++ STL Formula Sheet – Priority Queue, Stack, Set, Map (with Variants)

---

## 🔹 1. Stack (`std::stack<T>`)

* **LIFO (Last In, First Out)** container adapter.
* Header: `<stack>`

| Function    | Description             |
| :---------- | :---------------------- |
| `s.push(x)` | Top par element daale   |
| `s.pop()`   | Top element hataaye     |
| `s.top()`   | Top element access kare |
| `s.size()`  | Stack size              |
| `s.empty()` | Kya stack khali hai?    |

---

## 🔹 2. Queue (`std::queue<T>`)

* **FIFO (First In, First Out)** container adapter.
* Header: `<queue>`

| Function    | Description            |
| :---------- | :--------------------- |
| `q.push(x)` | End mein element daale |
| `q.pop()`   | Front element hataaye  |
| `q.front()` | Front element access   |
| `q.back()`  | Last element access    |
| `q.size()`  | Queue size             |
| `q.empty()` | Empty check            |

---

## 🔹 3. Priority Queue (`std::priority_queue<T>`)

* **Heap-based queue** (default: max-heap).
* Header: `<queue>`

### ✅ Declaration

```cpp
priority_queue<int> maxpq;                         // max-heap
priority_queue<int, vector<int>, greater<int>> minpq; // min-heap
```

| Function     | Description          |
| :----------- | :------------------- |
| `pq.push(x)` | Insert element       |
| `pq.pop()`   | Remove top (max/min) |
| `pq.top()`   | Access top element   |
| `pq.size()`  | Size of heap         |
| `pq.empty()` | Empty check          |

---

## 🔹 4. Set Variants

All sets maintain **sorted, unique** elements by default.
Header: `<set>`

### ✅ (a) `std::set<T>`

* Balanced BST (Red-Black Tree).
* Sorted order, unique elements.

| Function           | Description                                  |
| :----------------- | :------------------------------------------- |
| `s.insert(x)`      | Insert element                               |
| `s.erase(x)`       | Erase by value                               |
| `s.erase(it)`      | Erase by iterator                            |
| `s.find(x)`        | Iterator to element / `s.end()` if not found |
| `s.count(x)`       | 0 or 1 (existence check)                     |
| `s.lower_bound(x)` | First element >= x                           |
| `s.upper_bound(x)` | First element > x                            |
| `s.size()`         | Size                                         |
| `s.empty()`        | Empty check                                  |
| `s.clear()`        | Clear all                                    |

---

### ✅ (b) `std::multiset<T>`

* Sorted order, **duplicates allowed**.

* Same functions as `set`, but `count(x)` can be >1.

* `erase(x)` removes *all* occurrences of x.

---

### ✅ (c) `std::unordered_set<T>`

* Hash table implementation.
* Average O(1), unordered storage.
* No `lower_bound` / `upper_bound`.

| Function       | Description           |
| :------------- | :-------------------- |
| `us.insert(x)` | Insert element        |
| `us.erase(x)`  | Erase element         |
| `us.find(x)`   | Iterator to element   |
| `us.count(x)`  | Existence check (0/1) |

---

### ✅ (d) `std::unordered_multiset<T>`

* Hash table + duplicates allowed.
* Same as `unordered_set` but allows duplicates.

---

## 🔹 5. Map Variants

Maps store **key–value pairs**.
Header: `<map>`

### ✅ (a) `std::map<K,V>`

* Sorted by key (Red-Black Tree).
* Unique keys.

| Function           | Description           |
| :----------------- | :-------------------- |
| `m[key] = val`     | Insert / update value |
| `m.insert({k,v})`  | Insert pair           |
| `m.erase(key)`     | Erase by key          |
| `m.find(key)`      | Iterator to pair      |
| `m.count(key)`     | 0 or 1                |
| `m.lower_bound(k)` | First key >= k        |
| `m.upper_bound(k)` | First key > k         |
| `m.size()`         | Size                  |
| `m.empty()`        | Empty check           |
| `m.clear()`        | Clear all             |

---

### ✅ (b) `std::multimap<K,V>`

* Sorted, **duplicate keys allowed**.
* Same functions as `map`, but `count(key)` can be >1.

---

### ✅ (c) `std::unordered_map<K,V>`

* Hash table based, unordered.
* Unique keys.

| Function           | Description     |
| :----------------- | :-------------- |
| `um[key] = val`    | Insert/update   |
| `um.insert({k,v})` | Insert pair     |
| `um.find(key)`     | Iterator        |
| `um.count(key)`    | Existence check |
| `um.erase(key)`    | Erase element   |

---

### ✅ (d) `std::unordered_multimap<K,V>`

* Hash table based, **duplicate keys allowed**.
* Same as `unordered_map` but allows multiple entries with same key.

---
# 📘 C++ Graph Formula Sheet (Short Codes for Speed 🚀)

---

## 🔹 Graph Representation

```cpp
// Adjacency List
vector<int> g[N];   // N = max nodes

// Add edge (u,v) undirected
g[u].push_back(v);
g[v].push_back(u);

// Directed edge
g[u].push_back(v);
```

---

## 🔹 BFS (Breadth-First Search)

```cpp
void bfs(int src) {
    queue<int> q;
    vector<int> vis(N,0);
    q.push(src); vis[src]=1;
    while(!q.empty()){
        int u=q.front(); q.pop();
        for(int v:g[u]) if(!vis[v]){
            vis[v]=1; q.push(v);
        }
    }
}
```

---

## 🔹 DFS (Depth-First Search)

```cpp
void dfs(int u, vector<int>&vis){
    vis[u]=1;
    for(int v:g[u]) if(!vis[v]) dfs(v,vis);
}
```

---

## 🔹 Connected Components

```cpp
int comps=0;
vector<int> vis(N,0);
for(int i=1;i<=n;i++) 
    if(!vis[i]) { comps++; dfs(i,vis); }
```

---

## 🔹 Shortest Path (Unweighted, BFS)

```cpp
vector<int> dist(n+1, -1);
queue<int> q; q.push(src); dist[src]=0;
while(!q.empty()){
    int u=q.front(); q.pop();
    for(int v:g[u]) if(dist[v]==-1){
        dist[v]=dist[u]+1;
        q.push(v);
    }
}
```

---

## 🔹 Dijkstra (Weighted Graph)

```cpp
vector<int> d(n+1,1e9);
priority_queue<pair<int,int>,vector<pair<int,int>>,greater<>> pq;
d[src]=0; pq.push({0,src});
while(!pq.empty()){
    auto [du,u]=pq.top(); pq.pop();
    if(du!=d[u]) continue;
    for(auto [v,w]:g[u]) if(d[v]>du+w){
        d[v]=du+w;
        pq.push({d[v],v});
    }
}
```

*(Adjacency list as `vector<vector<pair<int,int>>> g` with `{neighbor,weight}`)*

---

## 🔹 Bellman-Ford (Detect Negative Cycle)

```cpp
vector<int> d(n+1,1e9); d[src]=0;
for(int i=1;i<n;i++)
  for(auto [u,v,w]:edges) 
    if(d[u]!=1e9 && d[v]>d[u]+w) d[v]=d[u]+w;

// Check negative cycle
for(auto [u,v,w]:edges)
  if(d[u]!=1e9 && d[v]>d[u]+w) { /* neg cycle */ }
```

---

## 🔹 Floyd-Warshall (All Pairs Shortest Path)

```cpp
for(int k=1;k<=n;k++)
 for(int i=1;i<=n;i++)
  for(int j=1;j<=n;j++)
   d[i][j]=min(d[i][j], d[i][k]+d[k][j]);
```

---

## 🔹 Topological Sort (Kahn’s Algo)

```cpp
queue<int> q; vector<int> indeg(n,0);
for(int u=0;u<n;u++) for(int v:g[u]) indeg[v]++;
for(int i=0;i<n;i++) if(indeg[i]==0) q.push(i);
while(!q.empty()){
    int u=q.front(); q.pop();
    for(int v:g[u]) if(--indeg[v]==0) q.push(v);
}
```

---

## 🔹 Union-Find (Disjoint Set Union – DSU)

```cpp
int par[N], sz[N];
int find(int x){ return par[x]==x?x:par[x]=find(par[x]); }
bool unite(int a,int b){
    a=find(a); b=find(b);
    if(a==b) return 0;
    if(sz[a]<sz[b]) swap(a,b);
    par[b]=a; sz[a]+=sz[b]; return 1;
}
```

---

## 🔹 Minimum Spanning Tree (Kruskal)

```cpp
sort(edges.begin(), edges.end()); // {w,u,v}
int mst=0;
for(auto [w,u,v]:edges) if(unite(u,v)) mst+=w;
```

---

## 🔹 Minimum Spanning Tree (Prim)

```cpp
priority_queue<pair<int,int>,vector<pair<int,int>>,greater<>> pq;
vector<int> vis(n,0);
pq.push({0,0}); int mst=0;
while(!pq.empty()){
    auto [w,u]=pq.top(); pq.pop();
    if(vis[u]) continue;
    vis[u]=1; mst+=w;
    for(auto [v,wt]:g[u]) if(!vis[v]) pq.push({wt,v});
}
```

---

## 🔹 Bipartite Check (BFS Coloring)

```cpp
vector<int> col(n,-1);
bool ok=true;
for(int i=0;i<n;i++) if(col[i]==-1){
    queue<int> q; q.push(i); col[i]=0;
    while(!q.empty()){
        int u=q.front(); q.pop();
        for(int v:g[u]){
            if(col[v]==-1) col[v]=col[u]^1, q.push(v);
            else if(col[v]==col[u]) ok=false;
        }
    }
}
```

---
# 🌳 Binary Tree Bramhastra (C++)

---

## 🔹 Representation

### 1. **Node Structure (Classical)**

```cpp
struct Node {
    int val;
    Node *left, *right;
    Node(int x) : val(x), left(NULL), right(NULL) {}
};
```

### 2. **Array Representation (Heap-like)**

* **0-based indexing:**

  * `left = 2*i + 1`
  * `right = 2*i + 2`
  * `parent = (i-1)/2`
* **1-based indexing (common in heaps):**

  * `left = 2*i`
  * `right = 2*i + 1`
  * `parent = i/2`

👉 **Always normalize to 0-based** → algorithms simple ho jaate hain.

---

## 🔹 Traversals (Recursive Shortcodes)

```cpp
void inorder(Node* root) {
    if (!root) return;
    inorder(root->left);
    cout << root->val << " ";
    inorder(root->right);
}

void preorder(Node* root) {
    if (!root) return;
    cout << root->val << " ";
    preorder(root->left);
    preorder(root->right);
}

void postorder(Node* root) {
    if (!root) return;
    postorder(root->left);
    postorder(root->right);
    cout << root->val << " ";
}
```

---

## 🔹 Traversals (Iterative Shortcodes)

### Inorder (stack)

```cpp
void inorder(Node* root) {
    stack<Node*> st;
    Node* cur = root;
    while (cur || !st.empty()) {
        while (cur) { st.push(cur); cur = cur->left; }
        cur = st.top(); st.pop();
        cout << cur->val << " ";
        cur = cur->right;
    }
}
```

### Level Order (BFS)

```cpp
void levelOrder(Node* root) {
    queue<Node*> q;
    q.push(root);
    while (!q.empty()) {
        Node* cur = q.front(); q.pop();
        cout << cur->val << " ";
        if (cur->left) q.push(cur->left);
        if (cur->right) q.push(cur->right);
    }
}
```

---

## 🔹 Tree Build Tricks

### From array (0-based)

```cpp
Node* build(vector<int>& a, int i=0) {
    if (i >= a.size() || a[i] == -1) return NULL; // -1 = null node
    Node* root = new Node(a[i]);
    root->left = build(a, 2*i+1);
    root->right = build(a, 2*i+2);
    return root;
}
```

### From input edges (like graph)

```cpp
unordered_map<int, Node*> mp;
Node* root = NULL;
for (auto [u,v,dir] : edges) {
    if (!mp[u]) mp[u] = new Node(u);
    if (!mp[v]) mp[v] = new Node(v);
    if (dir == 'L') mp[u]->left = mp[v];
    else mp[u]->right = mp[v];
    if (!root) root = mp[u];
}
```

---

## 🔹 Classical Problems Short Snippets

* **Height of Tree**

```cpp
int height(Node* root) {
    if (!root) return 0;
    return 1 + max(height(root->left), height(root->right));
}
```

* **Count Nodes**

```cpp
int count(Node* root) {
    if (!root) return 0;
    return 1 + count(root->left) + count(root->right);
}
```

* **Check Balanced**

```cpp
int check(Node* root) {
    if (!root) return 0;
    int l = check(root->left), r = check(root->right);
    if (l == -1 || r == -1 || abs(l-r) > 1) return -1;
    return 1 + max(l,r);
}
```

* **Lowest Common Ancestor (LCA)**

```cpp
Node* LCA(Node* root, Node* a, Node* b) {
    if (!root || root==a || root==b) return root;
    Node* l = LCA(root->left,a,b);
    Node* r = LCA(root->right,a,b);
    return !l ? r : !r ? l : root;
}
```

---

## 🔹 0-based vs 1-based Handling (Bramhastra Trick)

* Input given as **1-based array** (heap style):
  → Convert instantly: `u--, v--`.
* Input as **letters (A,B,C)**:
  → Convert: `idx = c - 'A'`.
* Input as **array with nulls (-1)**:
  → Build tree via index rules.

👉 **Always convert to 0-based inside code** (classical form).
👉 **Output convert back** only if problem demands.

---

⚡ **Rule of Thumb**:

1. Graph ho ya Tree → normalize **0-based internal representation**.
2. Traversals ka template yaad rakho (recursive + iterative).
3. Build functions ke liye ek ready snippet rakho (array / edge list).

---
# 📘 Stacks, Queues & Heap Bramhastra (C++ STL Cheatsheet)

---

## 🔹 Stack (LIFO)

```cpp
#include <stack>
stack<int> st;
```

### Common Ops:

* `st.push(x)` → element daalo
* `st.pop()` → top hatado
* `st.top()` → top element
* `st.empty()` → check empty
* `st.size()` → size

### Trick Problems:

* **Balanced Parentheses / Next Greater Element**
* **Undo operations**

⚡ Iteration → stack ko copy karke pop-pop.

---

## 🔹 Queue (FIFO)

```cpp
#include <queue>
queue<int> q;
```

### Common Ops:

* `q.push(x)` → back pe daalo
* `q.pop()` → front hatao
* `q.front()` → first element
* `q.back()` → last element
* `q.empty()`, `q.size()`

### Uses:

* BFS traversal
* Sliding window (with deque)

---

## 🔹 Deque (Double Ended Queue)

```cpp
#include <deque>
deque<int> dq;
```

### Common Ops:

* `dq.push_back(x)` / `dq.push_front(x)`
* `dq.pop_back()` / `dq.pop_front()`
* `dq.front()`, `dq.back()`
* `dq.empty()`, `dq.size()`

### Trick:

* Best for **Sliding Window Maximum**.

---

## 🔹 Priority Queue (Heap)

```cpp
#include <queue>

// Max-Heap (default)
priority_queue<int> pq;

// Min-Heap
priority_queue<int, vector<int>, greater<int>> minpq;
```

### Common Ops:

* `pq.push(x)` → O(log n)
* `pq.pop()` → top hatado
* `pq.top()` → max/min element
* `pq.empty()`, `pq.size()`

---

## 🔹 Heap Variants

* **Custom Comparator**

```cpp
struct cmp {
    bool operator()(int a, int b) {
        return a > b; // min-heap
    }
};
priority_queue<int, vector<int>, cmp> pq;
```

* **Array se Heap Banana**

```cpp
make_heap(v.begin(), v.end());       // max heap
pop_heap(v.begin(), v.end()); v.pop_back(); 
push_heap(v.begin(), v.end()); 
```
---
## 🔹 Functions ka kaam short mein

* **`make_heap(begin, end)`**
  Vector ke elements ko **heapify** karke ek **max-heap** bana deta hai.

  * Time: O(n)

* **`pop_heap(begin, end)`**
  Heap ka **sabse bada element (top)** ko `end-1` pe bhej deta hai.
  Lekin vector ka size same rehta hai!
  👉 Isliye hamesha `v.pop_back()` likhte hain taaki woh element delete bhi ho jaye.

* **`push_heap(begin, end)`**
  Jab aap `v.push_back(x)` karke ek element daalte ho, tab heap property toot jaati hai.
  `push_heap()` use karte hi woh heap ko phir se theek kar deta hai.

---
⚡ Rarely used, priority_queue simpler hai.

---

## 🔹 Classical Problems

### 1. Kth Largest Element

```cpp
priority_queue<int, vector<int>, greater<int>> pq;
for (int x : arr) {
    pq.push(x);
    if (pq.size() > k) pq.pop();
}
cout << pq.top();
```

### 2. Sliding Window Maximum

```cpp
deque<int> dq;
for (int i=0;i<n;i++) {
    if (!dq.empty() && dq.front() <= i-k) dq.pop_front();
    while (!dq.empty() && a[dq.back()] <= a[i]) dq.pop_back();
    dq.push_back(i);
    if (i >= k-1) cout << a[dq.front()] << " ";
}
```

### 3. Merge K Sorted Lists

* Use min-heap with `{value, list_idx}`.

### 4. Top K Frequent Elements

* Use **unordered_map + min-heap**.

---

## 🔹 0-based vs 1-based Indexing in Heap

* **0-based (C++ STL uses this internally)**

  * left = `2*i+1`, right = `2*i+2`
* **1-based (common in textbooks/CP)**

  * left = `2*i`, right = `2*i+1`

👉 Always normalize to **0-based** internally.

---

# ⚡ Rule of Thumb

1. **Stack = LIFO** (DFS, Undo, Next Greater)
2. **Queue = FIFO** (BFS, Producer-Consumer)
3. **Deque = Hybrid** (Sliding Window, Monotonic Queue)
4. **Priority Queue = Heap** (Greedy, Scheduling, Dijkstra)


---
# 📘 Linked List – Short Code Snippets (C++)

---

## 🔹 1. Node Definition

```cpp
struct Node {
    int data;
    Node* next;
    Node(int val) : data(val), next(NULL) {}
};
```

---

## 🔹 2. Insert at Head

```cpp
void insertHead(Node*& head, int val) {
    Node* n = new Node(val);
    n->next = head;
    head = n;
}
```

---

## 🔹 3. Insert at Tail

```cpp
void insertTail(Node*& head, int val) {
    Node* n = new Node(val);
    if (!head) { head = n; return; }
    Node* t = head;
    while (t->next) t = t->next;
    t->next = n;
}
```

---

## 🔹 4. Delete by Value

```cpp
void deleteVal(Node*& head, int val) {
    if (!head) return;
    if (head->data == val) { Node* t=head; head=head->next; delete t; return; }
    Node* cur=head;
    while (cur->next && cur->next->data!=val) cur=cur->next;
    if (cur->next) { Node* t=cur->next; cur->next=cur->next->next; delete t; }
}
```

---

## 🔹 5. Search

```cpp
bool search(Node* head, int key) {
    while (head) {
        if (head->data == key) return true;
        head = head->next;
    }
    return false;
}
```

---

## 🔹 6. Reverse Linked List (Iterative)

```cpp
Node* reverse(Node* head) {
    Node* prev=NULL; Node* cur=head;
    while (cur) {
        Node* nxt=cur->next;
        cur->next=prev;
        prev=cur; cur=nxt;
    }
    return prev;
}
```

---

## 🔹 7. Find Middle (Slow & Fast Pointer)

```cpp
Node* middle(Node* head) {
    Node* slow=head; Node* fast=head;
    while (fast && fast->next) {
        slow=slow->next; fast=fast->next->next;
    }
    return slow;
}
```

---

## 🔹 8. Detect Cycle (Floyd’s Algorithm)

```cpp
bool hasCycle(Node* head) {
    Node* slow=head; Node* fast=head;
    while (fast && fast->next) {
        slow=slow->next; fast=fast->next->next;
        if (slow==fast) return true;
    }
    return false;
}
```

---

## 🔹 9. Merge Two Sorted Linked Lists

```cpp
Node* merge(Node* a, Node* b) {
    if (!a) return b;
    if (!b) return a;
    if (a->data < b->data) { a->next=merge(a->next,b); return a; }
    else { b->next=merge(a,b->next); return b; }
}
```

---

## 🔹 10. Reverse in K-Groups (Template)

```cpp
Node* reverseK(Node* head, int k) {
    Node* cur=head; int cnt=0;
    while (cur && cnt<k) { cur=cur->next; cnt++; }
    if (cnt<k) return head;
    cur=head; Node* prev=NULL; cnt=0;
    while (cur && cnt<k) {
        Node* nxt=cur->next;
        cur->next=prev;
        prev=cur; cur=nxt; cnt++;
    }
    head->next=reverseK(cur,k);
    return prev;
}
```

---
# 📘 Bit Manipulation – Short Code Snippets (C++)

---

## 🔹 1. Check if kth bit is set

```cpp
bool isSet(int n, int k) {
    return (n & (1 << k)) != 0;
}
// 0-based indexing
// Example: n=5 (101), k=0 → true, k=1 → false
```

---

## 🔹 2. Set kth bit

```cpp
int setBit(int n, int k) {
    return n | (1 << k);
}
// Example: n=5 (101), k=1 → 111 (7)
```

---

## 🔹 3. Clear kth bit

```cpp
int clearBit(int n, int k) {
    return n & ~(1 << k);
}
// Example: n=5 (101), k=2 → 001 (1)
```

---

## 🔹 4. Toggle kth bit

```cpp
int toggleBit(int n, int k) {
    return n ^ (1 << k);
}
// Example: n=5 (101), k=0 → 100 (4)
```

---

## 🔹 5. Count set bits (1s)

```cpp
int countBits(int n) {
    return __builtin_popcount(n); // for int
}
// 0b1011 → 3
```

* For `long long`: `__builtin_popcountll(n)`

---

## 🔹 6. Check if n is power of 2

```cpp
bool isPower2(int n) {
    return n > 0 && (n & (n-1)) == 0;
}
```

---

## 🔹 7. Lowest Set Bit / Isolate rightmost 1

```cpp
int lowbit(int n) {
    return n & -n;
}
// Example: n=12 (1100) → 4 (0100)
```

---

## 🔹 8. Turn off rightmost 1

```cpp
int turnOff(int n) {
    return n & (n-1);
}
// Example: n=12 (1100) → 8 (1000)
```

---

## 🔹 9. XOR tricks

* Swap two numbers without temp:

```cpp
a ^= b;
b ^= a;
a ^= b;
```

* Find single number in array where others appear twice:

```cpp
int single = 0;
for(int x : arr) single ^= x;
```

---

## 🔹 10. Subset / Masking Loop

```cpp
int n = 3; // number of elements
for(int mask=0; mask<(1<<n); mask++) {
    for(int i=0; i<n; i++) {
        if(mask & (1<<i)) {
            // i-th element included in subset
        }
    }
}
```

---

## 🔹 11. Bitwise Operations Summary

| Operation   | C++  | Example     |     |        |
| ----------- | ---- | ----------- | --- | ------ |
| AND         | `&`  | `5 & 3 = 1` |     |        |
| OR          | `    | `           | `5  | 3 = 7` |
| XOR         | `^`  | `5 ^ 3 = 6` |     |        |
| NOT         | `~`  | `~5 = -6`   |     |        |
| Shift Left  | `<<` | `5<<1 = 10` |     |        |
| Shift Right | `>>` | `5>>1 = 2`  |     |        |

---
# 📘 Mathematics – Short Code Snippets (C++)

---

## 🔹 1. GCD (Greatest Common Divisor)

### a) Built-in

```cpp
int g = gcd(a, b); // C++17+
```

### b) Euclid’s Algorithm (Recursive)

```cpp
int gcd(int a, int b) {
    if(b==0) return a;
    return gcd(b, a%b);
}
```

### c) Euclid’s Algorithm (Iterative)

```cpp
int gcd(int a, int b) {
    while(b) {
        int r = a % b;
        a = b; b = r;
    }
    return a;
}
```

---

## 🔹 2. LCM (Least Common Multiple)

```cpp
int lcm = (a / gcd(a,b)) * b; // avoid overflow: divide first
```

---

## 🔹 3. Factorial

### a) Iterative

```cpp
long long fact(int n) {
    long long ans=1;
    for(int i=2;i<=n;i++) ans *= i;
    return ans;
}
```

### b) Recursive

```cpp
long long fact(int n) {
    if(n<=1) return 1;
    return n * fact(n-1);
}
```

---

## 🔹 4. nCr (Combinations)

### a) Factorial Formula

```cpp
long long nCr(int n,int r){
    return fact(n)/(fact(r)*fact(n-r));
}
```

### b) Iterative without factorial (prevents overflow)

```cpp
long long nCr(int n,int r){
    if(r>n-r) r=n-r;
    long long ans=1;
    for(int i=0;i<r;i++) ans = ans * (n-i) / (i+1);
    return ans;
}
```

---

## 🔹 5. Prime Check

```cpp
bool isPrime(int n){
    if(n<=1) return false;
    for(int i=2;i*i<=n;i++) if(n%i==0) return false;
    return true;
}
```

---

## 🔹 6. Sieve of Eratosthenes (Generate primes up to N)

```cpp
int N = 1000000;
vector<bool> isPrime(N+1, true);
isPrime[0]=isPrime[1]=false;
for(int i=2;i*i<=N;i++){
    if(isPrime[i]){
        for(int j=i*i;j<=N;j+=i) isPrime[j]=false;
    }
}
```

---

## 🔹 7. Divisors of n

```cpp
vector<int> divisors(int n){
    vector<int> div;
    for(int i=1;i*i<=n;i++){
        if(n%i==0){
            div.push_back(i);
            if(i != n/i) div.push_back(n/i);
        }
    }
    sort(div.begin(), div.end());
    return div;
}
```

---

## 🔹 8. Square root / Cube root

```cpp
int sq = sqrt(n);      // floor(sqrt(n))
int cb = cbrt(n);      // cube root
```

---

## 🔹 9. Floor, Ceil

```cpp
double x = 2.7;
int f = floor(x); // 2
int c = ceil(x);  // 3
```

---

## 🔹 10. Lower Bound / Upper Bound (C++ STL)

```cpp
vector<int> v = {1,3,3,5,7};
auto it1 = lower_bound(v.begin(), v.end(), 3); // points to first >=3
auto it2 = upper_bound(v.begin(), v.end(), 3); // points to first >3
```

---

## 🔹 11. Power / Modular Power

```cpp
long long power(long long a,long long b){
    long long res=1;
    while(b){
        if(b&1) res*=a;
        a*=a;
        b>>=1;
    }
    return res;
}

// Modular version
long long modPow(long long a,long long b,long long m){
    long long res=1;
    a%=m;
    while(b){
        if(b&1) res=(res*a)%m;
        a=(a*a)%m;
        b>>=1;
    }
    return res;
}
```

---

## 🔹 12. Extended Euclidean (for Modular Inverse)

```cpp
int gcdExtended(int a,int b,int &x,int &y){
    if(a==0){ x=0;y=1;return b;}
    int x1,y1;
    int g = gcdExtended(b%a,a,x1,y1);
    x=y1-(b/a)*x1;
    y=x1;
    return g;
}

// Modular inverse of a modulo m (if gcd(a,m)=1)
int modInverse(int a,int m){
    int x,y;
    gcdExtended(a,m,x,y);
    return (x%m + m)%m;
}
```

---

## 🔹 13. Sum of Arithmetic / Geometric Series

```cpp
long long arithSum(int a,int d,int n){
    return n*(2LL*a + (n-1)*d)/2;
}

long long geomSum(int a,int r,int n){ // r!=1
    long long res = a*(pow(r,n)-1)/(r-1);
    return res;
}
```

---

## 🔹 14. Miscellaneous

* **Count digits**: `int cnt = log10(n)+1;`
* **Check even/odd**: `n%2` or `n&1`
* **Swap numbers**: `a^=b; b^=a; a^=b;`
---

## 🔹 1. Floor (largest integer ≤ x)

```cpp
int myFloor(double x){
    int ans = (int)x;         // truncate decimal
    if(ans > x) ans--;        // handle negative numbers
    return ans;
}

// Example:
// x = 2.7 → myFloor(x) = 2
// x = -2.7 → myFloor(x) = -3
```

---

## 🔹 2. Ceil (smallest integer ≥ x)

```cpp
int myCeil(double x){
    int ans = (int)x;
    if(ans < x) ans++;        // add 1 if there is fractional part
    return ans;
}

// Example:
// x = 2.3 → myCeil(x) = 3
// x = -2.3 → myCeil(x) = -2
```

---

## 🔹 3. Lower Bound (first element ≥ key in sorted array)

```cpp
int lowerBound(vector<int>& v, int key){
    int l=0, r=v.size()-1, ans=v.size();
    while(l<=r){
        int m = l + (r-l)/2;
        if(v[m] >= key){
            ans = m;   // possible answer
            r = m-1;   // search left
        } else {
            l = m+1;
        }
    }
    return ans; // index of first >= key, or v.size() if not found
}

// Example:
// v = {1,3,3,5}, key=3 → returns index 1
// key=4 → returns 3
```

---

## 🔹 4. Upper Bound (first element > key in sorted array)

```cpp
int upperBound(vector<int>& v, int key){
    int l=0, r=v.size()-1, ans=v.size();
    while(l<=r){
        int m = l + (r-l)/2;
        if(v[m] > key){
            ans = m;   // possible answer
            r = m-1;   // search left
        } else {
            l = m+1;
        }
    }
    return ans; // index of first > key, or v.size() if not found
}

// Example:
// v = {1,3,3,5}, key=3 → returns index 3
// key=6 → returns 4
```

---
# 📘 Sorting – Short Code Snippets (C++)

---

## 🔹 1. Sort Vector / Array (Ascending)

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v = {5,2,9,1,5,6};
    sort(v.begin(), v.end()); // Ascending
    for(int x:v) cout << x << " "; // 1 2 5 5 6 9
}
```

* For **array**:

```cpp
int a[] = {5,2,9,1};
sort(a, a+4); // a+size
```

---

## 🔹 2. Sort Descending

```cpp
sort(v.begin(), v.end(), greater<int>()); // Descending
```

* Custom comparator:

```cpp
sort(v.begin(), v.end(), [](int a,int b){ return a>b; }); // Desc
```

---

## 🔹 3. Sort Pair Vector

```cpp
vector<pair<int,int>> vp = {{1,2},{3,1},{2,4}};
sort(vp.begin(), vp.end()); // by first, then second
// Custom: by second
sort(vp.begin(), vp.end(), [](pair<int,int> a, pair<int,int> b){ 
    return a.second < b.second; 
});
```

---

## 🔹 4. Sort 2D Vector

```cpp
vector<vector<int>> v2 = {{1,5},{2,3},{1,2}};
sort(v2.begin(), v2.end()); 
// Sorts by first column, then second
```

---

## 🔹 5. Partial Sort (First K elements)

```cpp
partial_sort(v.begin(), v.begin()+k, v.end()); 
```

* Top-k smallest elements sorted in first k positions.

---

## 🔹 6. Reverse a Vector / Array

```cpp
reverse(v.begin(), v.end());
```

---

## 🔹 7. Custom Sort (Even before Odd)

```cpp
sort(v.begin(), v.end(), [](int a,int b){
    if(a%2==0 && b%2!=0) return true;
    if(a%2!=0 && b%2==0) return false;
    return a < b;
});
```

---

## 🔹 8. Bubble / Selection / Insertion (For small arrays)

### Bubble Sort

```cpp
for(int i=0;i<n;i++)
    for(int j=0;j<n-i-1;j++)
        if(a[j]>a[j+1]) swap(a[j],a[j+1]);
```

### Selection Sort

```cpp
for(int i=0;i<n-1;i++){
    int minIdx=i;
    for(int j=i+1;j<n;j++) if(a[j]<a[minIdx]) minIdx=j;
    swap(a[i],a[minIdx]);
}
```

### Insertion Sort

```cpp
for(int i=1;i<n;i++){
    int key=a[i], j=i-1;
    while(j>=0 && a[j]>key){ a[j+1]=a[j]; j--; }
    a[j+1]=key;
}
```

---

## 🔹 9. Kth Largest / Smallest

```cpp
nth_element(v.begin(), v.begin()+k-1, v.end()); // k-th smallest
int kth_smallest = v[k-1];
int kth_largest = v[v.size()-k]; // after nth_element + sort if needed
```

---

## 🔹 10. Stable Sort

```cpp
stable_sort(v.begin(), v.end());
```

* Maintains relative order of equal elements.

---

⚡ **Rule of Thumb:**

* **sort()** → default ascending
* **greater<int>() / custom lambda** → descending / custom
* **partial_sort() / nth_element()** → top-k / kth element
* **reverse()** → simple reverse
* **stable_sort()** → equal elements order preserved

---


# 📘 Sweep Line Approach – Short Code Snippets (C++)

---

## 🔹 1. Maximum Overlapping Intervals

**Problem:** Given `n` intervals `[l,r]`, find maximum number of intervals overlapping at any point.

**Time Complexity:** (O(n \log n))

```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
    vector<pair<int,int>> intervals = {{1,3},{2,5},{4,6}};
    vector<pair<int,int>> events;

    for(auto &it: intervals){
        events.push_back({it.first, 1});  // interval start
        events.push_back({it.second, -1}); // interval end
    }

    sort(events.begin(), events.end()); // sort by coordinate
    int curr=0, ans=0;
    for(auto &e: events){
        curr += e.second;
        ans = max(ans, curr);
    }
    cout << ans; // max overlapping intervals
}
```

**Explanation:**

* We convert intervals into events: start (+1) and end (-1)
* Sort all events → O(n log n)
* Sweep from left to right, maintain **current overlap** → O(n)

---

## 🔹 2. Line Sweep – Counting Points in Intervals

**Problem:** Given points and intervals, count how many points lie in each interval.

**Time Complexity:** (O((n+m)\log(n+m)))

```cpp
struct Event {
    int x,type,index; // type: 0=interval start,1=point,2=interval end
};

int main(){
    vector<pair<int,int>> intervals = {{1,3},{2,5},{4,6}};
    vector<int> points = {2,3,5};
    vector<Event> events;

    for(int i=0;i<intervals.size();i++){
        events.push_back({intervals[i].first, 0, i}); // start
        events.push_back({intervals[i].second, 2, i}); // end
    }
    for(int i=0;i<points.size();i++){
        events.push_back({points[i], 1, i}); // point
    }

    sort(events.begin(), events.end(), [](Event a, Event b){
        if(a.x==b.x) return a.type < b.type; // order: start<point<end
        return a.x < b.x;
    });

    int active=0;
    vector<int> pointCount(points.size(),0);
    for(auto &e: events){
        if(e.type==0) active++;           // interval starts
        else if(e.type==2) active--;      // interval ends
        else pointCount[e.index] = active; // point occurs
    }

    for(auto x: pointCount) cout<<x<<" "; // number of intervals covering each point
}
```

---

## 🔹 3. Rectangle Area / Union of Intervals

**Idea:** Sweep vertically, process horizontal edges as events.

* Events: `{y, type(+1/-1), x1, x2}`
* Sort by y-coordinate, sweep y-axis
* Maintain active intervals on x-axis (segment tree / multiset)
* Complexity: (O(n \log n))

*(Classic for “Union of Rectangles” problem in contests.)*

```cpp
// Conceptual snippet
struct Event{int y,type,x1,x2;};
sort(events.begin(), events.end(), [](Event a, Event b){return a.y<b.y;});
multiset<pair<int,int>> active; // active intervals
for(Event e:events){
    // process sweep line
    // add/remove interval in active set
    // compute area covered using active intervals
}
```

---

## 🔹 4. Sweep Line Template

**Steps:**

1. Convert objects (intervals, rectangles, segments) into **events**.
2. Sort events by **coordinate** (and type for tie-breaking).
3. Use **counter / multiset / map / segment tree** to maintain active set.
4. Sweep from left → right (or bottom → top) and update answer.

**Time Complexity:**

* Sorting events: (O(n \log n))
* Sweeping events: (O(n \log n)) if using set/map, (O(n)) if simple counter.

---

⚡ **Rule of Thumb:**

* Sweep line = **sort events + maintain active structure**
* Often reduces (O(n^2)) overlap problems → (O(n log n))
* Classic problems: max overlap, interval union length, points in intervals, rectangle union area

---



# 🏹 Striver-Style C++ Code Snippets – Formula Sheet

## 1️⃣ Binary Tree

### a) Morris Inorder Traversal (O(1) space)

```cpp
void morrisTraversal(TreeNode* root) {
    TreeNode* curr = root;
    while(curr) {
        if(!curr->left) { 
            cout << curr->val << " "; 
            curr = curr->right; 
        } else {
            TreeNode* pre = curr->left;
            while(pre->right && pre->right != curr) pre = pre->right;
            if(!pre->right) { pre->right = curr; curr = curr->left; }
            else { pre->right = nullptr; cout << curr->val << " "; curr = curr->right; }
        }
    }
}
// TC: O(n), SC: O(1)
```

### b) Flatten Binary Tree

```cpp
void flatten(TreeNode* root) {
    if(!root) return;
    flatten(root->left);
    flatten(root->right);
    TreeNode* temp = root->right;
    root->right = root->left;
    root->left = nullptr;
    TreeNode* t = root;
    while(t->right) t=t->right;
    t->right = temp;
}
// TC: O(n), SC: O(n) due to recursion
```

---

## 2️⃣ Graph

### a) Kruskal MST

```cpp
struct Edge { int u,v,w; };
bool cmp(Edge &a, Edge &b){ return a.w < b.w; }

int find(int u, vector<int> &parent){
    if(parent[u]==u) return u;
    return parent[u]=find(parent[u], parent);
}

int kruskal(int n, vector<Edge> &edges){
    sort(edges.begin(), edges.end(), cmp);
    vector<int> parent(n);
    iota(parent.begin(), parent.end(), 0);
    int cost=0;
    for(auto &e: edges){
        int pu=find(e.u,parent), pv=find(e.v,parent);
        if(pu!=pv){ parent[pu]=pv; cost+=e.w; }
    }
    return cost;
}
// TC: O(E log E), SC: O(V)
```

### b) Prim MST (Adjacency List)

```cpp
int prim(int n, vector<vector<pair<int,int>>> &adj){
    vector<int> key(n,INT_MAX), vis(n,0);
    key[0]=0;
    int res=0;
    priority_queue<pair<int,int>, vector<pair<int,int>>, greater<>> pq;
    pq.push({0,0});
    while(!pq.empty()){
        int u=pq.top().second; pq.pop();
        if(vis[u]) continue;
        vis[u]=1; res+=key[u];
        for(auto &p: adj[u]){
            int v=p.first, w=p.second;
            if(!vis[v] && w<key[v]){
                key[v]=w;
                pq.push({key[v],v});
            }
        }
    }
    return res;
}
// TC: O(E log V)
```

### c) Tarjan – Bridges

```cpp
vector<int> disc, low; int time=0;
vector<vector<int>> bridges;
void dfs(int u, int p, vector<vector<int>> &adj){
    disc[u]=low[u]=++time;
    for(int v: adj[u]){
        if(v==p) continue;
        if(!disc[v]){
            dfs(v,u,adj);
            low[u]=min(low[u],low[v]);
            if(low[v]>disc[u]) bridges.push_back({u,v});
        } else low[u]=min(low[u],disc[v]);
    }
}
// TC: O(V+E)
```

---

## 3️⃣ Union-Find (Disjoint Set)

### a) Union by Rank + Path Compression

```cpp
vector<int> parent, rankD;
void makeSet(int n){ parent.resize(n); rankD.resize(n,0); iota(parent.begin(), parent.end(), 0); }
int findSet(int u){ if(u==parent[u]) return u; return parent[u]=findSet(parent[u]); }
void unionSet(int u,int v){
    u=findSet(u); v=findSet(v);
    if(u==v) return;
    if(rankD[u]<rankD[v]) parent[u]=v;
    else if(rankD[u]>rankD[v]) parent[v]=u;
    else { parent[v]=u; rankD[u]++; }
}
// TC: almost O(1) amortized
```

---

## 4️⃣ Sorting – Quick Snippets

### a) Quick Sort (Pivot = start)

```cpp
int partition(vector<int> &v, int l, int r){
    int pivot=v[l], i=l+1;
    for(int j=l+1;j<=r;j++){
        if(v[j]<pivot) swap(v[i++],v[j]);
    }
    swap(v[l],v[i-1]);
    return i-1;
}
void quickSort(vector<int> &v,int l,int r){
    if(l<r){
        int p=partition(v,l,r);
        quickSort(v,l,p-1); quickSort(v,p+1,r);
    }
}
// TC: O(n log n), SC: O(log n)
```

### b) Heap Sort

```cpp
void heapify(vector<int>&v,int n,int i){
    int largest=i,l=2*i+1,r=2*i+2;
    if(l<n && v[l]>v[largest]) largest=l;
    if(r<n && v[r]>v[largest]) largest=r;
    if(largest!=i){ swap(v[i],v[largest]); heapify(v,n,largest); }
}
void heapSort(vector<int>&v){
    int n=v.size();
    for(int i=n/2-1;i>=0;i--) heapify(v,n,i);
    for(int i=n-1;i>0;i--){ swap(v[0],v[i]); heapify(v,i,0); }
}
// TC: O(n log n), SC: O(1)
```

### c) Count Sort

```cpp
void countSort(vector<int>&v){
    int mx=*max_element(v.begin(),v.end());
    vector<int> cnt(mx+1,0);
    for(int x:v) cnt[x]++;
    int idx=0;
    for(int i=0;i<=mx;i++)
        while(cnt[i]--) v[idx++]=i;
}
// TC: O(n+max), SC: O(max)
```

### d) Radix Sort

```cpp
int getMax(vector<int> &v){ return *max_element(v.begin(),v.end()); }
void countSortRadix(vector<int> &v,int exp){
    vector<int> output(v.size()); int cnt[10]={0};
    for(int i=0;i<v.size();i++) cnt[(v[i]/exp)%10]++;
    for(int i=1;i<10;i++) cnt[i]+=cnt[i-1];
    for(int i=v.size()-1;i>=0;i--){
        output[cnt[(v[i]/exp)%10]-1]=v[i]; cnt[(v[i]/exp)%10]--;
    }
    for(int i=0;i<v.size();i++) v[i]=output[i];
}
void radixSort(vector<int> &v){
    int m=getMax(v);
    for(int exp=1;m/exp>0;exp*=10) countSortRadix(v,exp);
}
// TC: O(d*(n+10)), SC: O(n+10)
```

---


# 🏹 Striver-Style C++ Snippets – Batch 2

---

## 1️⃣ Union by Size

```cpp
vector<int> parent, sizeUF;

void makeSet(int n){
    parent.resize(n); sizeUF.resize(n,1);
    iota(parent.begin(), parent.end(), 0);
}

int findSet(int u){
    if(u==parent[u]) return u;
    return parent[u]=findSet(parent[u]); // path compression
}

void unionBySize(int u, int v){
    u=findSet(u); v=findSet(v);
    if(u==v) return;
    if(sizeUF[u]<sizeUF[v]) swap(u,v);
    parent[v]=u;
    sizeUF[u]+=sizeUF[v];
}
// TC: almost O(1) amortized
```

---

## 2️⃣ Deflattening Binary Tree

```cpp
TreeNode* deflatten(vector<int> &preorder){
    if(preorder.empty()) return nullptr;
    TreeNode* root=new TreeNode(preorder[0]);
    TreeNode* curr=root;
    for(int i=1;i<preorder.size();i++){
        curr->right=new TreeNode(preorder[i]);
        curr=curr->right;
    }
    return root;
}
// TC: O(n), SC: O(n)
```

---

## 3️⃣ Quick Sort – Other Versions

### Pivot = end

```cpp
int partitionEnd(vector<int>&v,int l,int r){
    int pivot=v[r], i=l-1;
    for(int j=l;j<r;j++){
        if(v[j]<pivot) swap(v[++i],v[j]);
    }
    swap(v[i+1],v[r]);
    return i+1;
}

void quickSortEnd(vector<int>&v,int l,int r){
    if(l<r){
        int p=partitionEnd(v,l,r);
        quickSortEnd(v,l,p-1); quickSortEnd(v,p+1,r);
    }
}
```

### Pivot = Median of 3

```cpp
int medianPivot(vector<int>&v,int l,int r){
    int m=l+(r-l)/2;
    if(v[l]>v[m]) swap(v[l],v[m]);
    if(v[l]>v[r]) swap(v[l],v[r]);
    if(v[m]>v[r]) swap(v[m],v[r]);
    swap(v[m],v[r]); // median at end
    return partitionEnd(v,l,r);
}

void quickSortMedian(vector<int>&v,int l,int r){
    if(l<r){
        int p=medianPivot(v,l,r);
        quickSortMedian(v,l,p-1); quickSortMedian(v,p+1,r);
    }
}
```

---

## 4️⃣ Burn Tree (Infection in Tree)

```cpp
int minTimeBurn(TreeNode* root, int target){
    unordered_map<TreeNode*,TreeNode*> parentMap;
    TreeNode* targetNode=nullptr;

    // BFS to map parent pointers
    queue<TreeNode*> q;
    q.push(root);
    while(!q.empty()){
        auto node=q.front(); q.pop();
        if(node->val==target) targetNode=node;
        if(node->left){ parentMap[node->left]=node; q.push(node->left); }
        if(node->right){ parentMap[node->right]=node; q.push(node->right); }
    }

    unordered_set<TreeNode*> visited;
    q.push(targetNode); visited.insert(targetNode);
    int time=0;
    while(!q.empty()){
        int sz=q.size(); bool flag=false;
        for(int i=0;i<sz;i++){
            auto node=q.front(); q.pop();
            for(auto neigh:{node->left,node->right,parentMap[node]})
                if(neigh && visited.find(neigh)==visited.end()){ visited.insert(neigh); q.push(neigh); flag=true; }
        }
        if(flag) time++;
    }
    return time;
}
// TC: O(n), SC: O(n)
```

---

## 5️⃣ Fulkerson (Max Flow) – Edmonds-Karp

```cpp
int bfs(vector<vector<int>>&cap, vector<vector<int>>&adj, int s, int t, vector<int>& parent){
    fill(parent.begin(), parent.end(), -1);
    queue<pair<int,int>> q; q.push({s,INT_MAX});
    parent[s]=-2;
    while(!q.empty()){
        int u=q.front().first, flow=q.front().second; q.pop();
        for(int v:adj[u]){
            if(parent[v]==-1 && cap[u][v]>0){
                parent[v]=u;
                int new_flow=min(flow, cap[u][v]);
                if(v==t) return new_flow;
                q.push({v,new_flow});
            }
        }
    }
    return 0;
}

int maxFlow(int n,int s,int t, vector<vector<int>>&cap, vector<vector<int>>&adj){
    int flow=0; vector<int> parent(n);
    int new_flow;
    while(new_flow=bfs(cap,adj,s,t,parent)){
        flow+=new_flow;
        int cur=t;
        while(cur!=s){
            int prev=parent[cur];
            cap[prev][cur]-=new_flow;
            cap[cur][prev]+=new_flow;
            cur=prev;
        }
    }
    return flow;
}
// TC: O(E*F), SC: O(V+E)
```

---

## 6️⃣ Kahn Topological Sort

```cpp
vector<int> kahnTopo(int n, vector<vector<int>>& adj){
    vector<int> indeg(n,0), topo;
    for(auto &v:adj) for(int u:v) indeg[u]++;
    queue<int> q;
    for(int i=0;i<n;i++) if(indeg[i]==0) q.push(i);
    while(!q.empty()){
        int u=q.front(); q.pop();
        topo.push_back(u);
        for(int v:adj[u]){
            indeg[v]--;
            if(indeg[v]==0) q.push(v);
        }
    }
    return topo; // empty if cycle
}
// TC: O(V+E)
```

---

## 7️⃣ Articulation Points / Bridges – Tarjan

```cpp
vector<int> disc, low;
vector<bool> ap;
int timeT=0;
void tarjanAP(int u,int parent, vector<vector<int>>& adj){
    disc[u]=low[u]=++timeT;
    int children=0;
    for(int v:adj[u]){
        if(v==parent) continue;
        if(disc[v]==0){
            children++;
            tarjanAP(v,u,adj);
            low[u]=min(low[u],low[v]);
            if(parent!=-1 && low[v]>=disc[u]) ap[u]=true;
        } else low[u]=min(low[u],disc[v]);
    }
    if(parent==-1 && children>1) ap[u]=true;
}
// TC: O(V+E)
```

---


# 📝 C++ String Snippets – Classical / Popular

---

## 1️⃣ Reverse a String

```cpp
string s = "hello";
reverse(s.begin(), s.end()); 
cout << s; // "olleh"
// TC: O(n), SC: O(1)
```

---

## 2️⃣ Palindrome Check

```cpp
bool isPalindrome(string s){
    int l=0, r=s.size()-1;
    while(l<r) if(s[l++]!=s[r--]) return false;
    return true;
}
// TC: O(n), SC: O(1)
```

---

## 3️⃣ String to Integer / Integer to String

```cpp
int x = stoi("123");         // string -> int
string s = to_string(456);   // int -> string
```

---

## 4️⃣ Substring Extraction

```cpp
string s = "abcdefgh";
string sub = s.substr(2,3);  // from index 2, length 3
cout << sub; // "cde"
// TC: O(len), SC: O(len)
```

---

## 5️⃣ Find / Count Substring

```cpp
string s = "ababcab";
size_t pos = s.find("ab");   // first occurrence
cout << pos; // 0

// Count all occurrences
int count=0, i=0;
while((i=s.find("ab",i)) != string::npos){ count++; i++; }
cout << count; // 2
```

---

## 6️⃣ Replace / Erase / Insert

```cpp
string s = "hello";
s.replace(1,3,"XYZ"); // replace 3 chars from index 1
cout << s; // "hXYZo"

s.erase(1,3); // erase 3 chars from index 1
s.insert(1,"ABC"); // insert at index 1
```

---

## 7️⃣ Split String by Delimiter (Classical way)

```cpp
string s = "a,b,c,d";
stringstream ss(s);
string token;
vector<string> res;
while(getline(ss, token, ',')) res.push_back(token);
// res = ["a","b","c","d"]
```

---

## 8️⃣ Count Frequency of Characters

```cpp
string s = "aabcc";
vector<int> freq(26,0);
for(char c:s) freq[c-'a']++;
// freq[0]=2, freq[1]=1, freq[2]=2
```

---

## 9️⃣ Lexicographical Permutations

```cpp
string s = "abc";
sort(s.begin(), s.end());
do {
    cout << s << "\n";
} while(next_permutation(s.begin(), s.end()));
// TC: O(n! * n)
```

---

## 🔟 Longest Common Prefix (LCP) – Classical Approach

```cpp
string longestCommonPrefix(vector<string> &strs){
    if(strs.empty()) return "";
    string prefix = strs[0];
    for(int i=1;i<strs.size();i++){
        while(strs[i].find(prefix)!=0) prefix = prefix.substr(0,prefix.size()-1);
        if(prefix=="") break;
    }
    return prefix;
}
// TC: O(N*M), N=number of strings, M=length of prefix
```

---

## 1️⃣1️⃣ KMP – Prefix Function / LPS Array

```cpp
vector<int> computeLPS(string s){
    int n=s.size();
    vector<int> lps(n,0);
    for(int i=1,len=0;i<n;){
        if(s[i]==s[len]) lps[i++]=++len;
        else if(len) len=lps[len-1];
        else lps[i++]=0;
    }
    return lps;
}
// TC: O(n), SC: O(n)
```

---

## 1️⃣2️⃣ Z-Algorithm (Pattern Matching / Substrings)

```cpp
vector<int> Z(string s){
    int n=s.size(); vector<int> z(n,0);
    for(int i=1,l=0,r=0;i<n;i++){
        if(i<=r) z[i]=min(r-i+1,z[i-l]);
        while(i+z[i]<n && s[z[i]]==s[i+z[i]]) z[i]++;
        if(i+z[i]-1>r) l=i,r=i+z[i]-1;
    }
    return z;
}
// TC: O(n), SC: O(n)
```

---

## 1️⃣3️⃣ Rolling Hash (Rabin-Karp Style) – Substring Hash

```cpp
const int p = 31, m = 1e9+9;
vector<long long> p_pow, h;
void computeHash(string &s){
    int n=s.size(); p_pow.resize(n); h.resize(n+1);
    p_pow[0]=1;
    for(int i=1;i<n;i++) p_pow[i]=(p_pow[i-1]*p)%m;
    for(int i=0;i<n;i++) h[i+1]=(h[i]+(s[i]-'a'+1)*p_pow[i])%m;
}
long long substringHash(int l,int r){ // [l,r]
    return (h[r+1]-h[l]+m)%m;
}
// TC: O(n) preprocessing, O(1) per query
```

---
# 🧵 String Hashing & Rolling Hash – Advanced Snippets

---

## 1️⃣ Polynomial / Rolling Hash – Precompute Powers & Prefix Hash

```cpp
const int p = 31;          // prime base (26 for lowercase)
const int m = 1e9+9;       // large prime modulus

vector<long long> p_pow;   // p^i mod m
vector<long long> h;       // prefix hashes

void computeHash(string &s){
    int n = s.size();
    p_pow.resize(n);
    h.resize(n+1);
    p_pow[0] = 1;
    for(int i=1;i<n;i++) p_pow[i] = (p_pow[i-1]*p)%m;
    h[0]=0;
    for(int i=0;i<n;i++) 
        h[i+1] = (h[i] + (s[i]-'a'+1)*p_pow[i])%m;
}

// substring hash [l,r] 0-based
long long substringHash(int l,int r){
    long long hash_val = (h[r+1]-h[l]+m)%m;
    hash_val = (hash_val * 1LL * modInverse(p_pow[l], m)) % m;
    return hash_val;
}

// modular inverse using Fermat
long long modInverse(long long x, long long m){
    long long res = 1, e = m-2;
    while(e){
        if(e&1) res = (res*x)%m;
        x = (x*x)%m; e>>=1;
    }
    return res;
}
// TC: O(n) preprocessing, O(1) per query
```

---

## 2️⃣ Rabin-Karp – Pattern Matching

```cpp
int rabinKarp(string &text, string &pattern){
    int n = text.size(), m = pattern.size();
    computeHash(text); // prefix hash of text
    long long patternHash=0, pow_m=1;
    for(int i=0;i<m;i++){ 
        patternHash = (patternHash + (pattern[i]-'a'+1)*pow_m)%::m;
        if(i<m-1) pow_m = (pow_m*p)%::m;
    }
    for(int i=0;i<=n-m;i++){
        if(substringHash(i,i+m-1)==patternHash) return i;
    }
    return -1;
}
// TC: O(n+m), SC: O(n)
```

---

## 3️⃣ Count Distinct Substrings

```cpp
long long countDistinctSubstrings(string s){
    int n=s.size();
    computeHash(s);
    set<long long> hashes;
    for(int l=0;l<n;l++)
        for(int r=l;r<n;r++)
            hashes.insert(substringHash(l,r));
    return hashes.size();
}
// TC: O(n^2), SC: O(n^2) - can optimize with double hash
```

---

## 4️⃣ Longest Common Substring via Binary Search + Rolling Hash

```cpp
bool hasCommonSubstring(string &s1, string &s2, int len){
    set<long long> hashes;
    computeHash(s1);
    for(int i=0;i+len-1<s1.size();i++) hashes.insert(substringHash(i,i+len-1));
    computeHash(s2);
    for(int i=0;i+len-1<s2.size();i++)
        if(hashes.count(substringHash(i,i+len-1))) return true;
    return false;
}

int longestCommonSubstring(string &s1, string &s2){
    int l=0, r=min(s1.size(), s2.size()), ans=0;
    while(l<=r){
        int mid=(l+r)/2;
        if(hasCommonSubstring(s1,s2,mid)) ans=mid,l=mid+1;
        else r=mid-1;
    }
    return ans;
}
// TC: O((n+m) log min(n,m)), SC: O(n)
```

---

## 5️⃣ Palindromic Substrings (Hash-based)

```cpp
string s_rev;
vector<long long> h_rev, p_pow;

void prepare(string s){
    s_rev = s; reverse(s_rev.begin(), s_rev.end());
    computeHash(s);
    computeHash(s_rev); // same prefix hash function for reversed
}

bool isPalindrome(int l,int r){
    long long h1 = substringHash(l,r);
    long long h2 = substringHash(s.size()-1-r, s.size()-1-l); // reversed hash
    return h1==h2;
}
// TC: O(1) per query after O(n) preprocessing
```

---

## 6️⃣ Double Hashing (to avoid collisions)

```cpp
const int p1=31,m1=1e9+7;
const int p2=53,m2=1e9+9;

pair<long long,long long> substringHash2(int l,int r, vector<long long> &h1, vector<long long> &h2, vector<long long> &p_pow1, vector<long long> &p_pow2){
    long long hash1 = (h1[r+1]-h1[l]+m1)%m1;
    hash1 = (hash1*modInverse(p_pow1[l],m1))%m1;
    long long hash2 = (h2[r+1]-h2[l]+m2)%m2;
    hash2 = (hash2*modInverse(p_pow2[l],m2))%m2;
    return {hash1, hash2};
}
// TC: O(1) per query, SC: O(n)
```

---

### ✅ Notes / Classical Uses:

* **Pattern matching** → Rabin-Karp
* **Palindrome detection** → hash s vs reversed s
* **Substring comparison** → O(1) using rolling hash
* **Distinct substrings / LCS** → binary search + hash
* **Double hashing** → avoid collisions in large datasets

---


# 🧵 Dynamic Programming – Classical Snippets

---

## 1️⃣ Fibonacci (Top-down + Bottom-up)

```cpp
// Top-Down (Memoization)
int fib(int n, vector<int> &dp){
    if(n<=1) return n;
    if(dp[n]!=-1) return dp[n];
    return dp[n] = fib(n-1,dp)+fib(n-2,dp);
}
// TC: O(n), SC: O(n)

// Bottom-Up (Tabulation)
int fibBU(int n){
    vector<int> dp(n+1);
    dp[0]=0; dp[1]=1;
    for(int i=2;i<=n;i++) dp[i]=dp[i-1]+dp[i-2];
    return dp[n];
}
// TC: O(n), SC: O(n)
```

---

## 2️⃣ 0/1 Knapsack

```cpp
int knapsack(vector<int> &wt, vector<int> &val, int W){
    int n=wt.size();
    vector<vector<int>> dp(n+1,vector<int>(W+1,0));
    for(int i=1;i<=n;i++){
        for(int w=0;w<=W;w++){
            if(wt[i-1]<=w) dp[i][w]=max(dp[i-1][w], val[i-1]+dp[i-1][w-wt[i-1]]);
            else dp[i][w]=dp[i-1][w];
        }
    }
    return dp[n][W];
}
// TC: O(n*W), SC: O(n*W)
```

---

## 3️⃣ Longest Common Subsequence (LCS)

```cpp
int lcs(string &s1, string &s2){
    int n=s1.size(), m=s2.size();
    vector<vector<int>> dp(n+1, vector<int>(m+1,0));
    for(int i=1;i<=n;i++){
        for(int j=1;j<=m;j++){
            if(s1[i-1]==s2[j-1]) dp[i][j]=1+dp[i-1][j-1];
            else dp[i][j]=max(dp[i-1][j], dp[i][j-1]);
        }
    }
    return dp[n][m];
}
// TC: O(n*m), SC: O(n*m)
```

---

## 4️⃣ Minimum Edit Distance

```cpp
int minEditDistance(string &s1,string &s2){
    int n=s1.size(), m=s2.size();
    vector<vector<int>> dp(n+1, vector<int>(m+1,0));
    for(int i=0;i<=n;i++) dp[i][0]=i;
    for(int j=0;j<=m;j++) dp[0][j]=j;
    for(int i=1;i<=n;i++){
        for(int j=1;j<=m;j++){
            if(s1[i-1]==s2[j-1]) dp[i][j]=dp[i-1][j-1];
            else dp[i][j]=1+min({dp[i-1][j-1], dp[i][j-1], dp[i-1][j]});
        }
    }
    return dp[n][m];
}
// TC: O(n*m), SC: O(n*m)
```

---

## 5️⃣ Coin Change (Number of Ways)

```cpp
int coinChangeWays(vector<int>& coins, int amount){
    vector<int> dp(amount+1,0); dp[0]=1;
    for(int c:coins){
        for(int i=c;i<=amount;i++) dp[i]+=dp[i-c];
    }
    return dp[amount];
}
// TC: O(n*amount), SC: O(amount)
```

---

## 6️⃣ Maximum Subarray Sum (Kadane’s Algorithm – DP)

```cpp
int maxSubArray(vector<int>& nums){
    int n=nums.size(), curr=0, best=INT_MIN;
    for(int x:nums){
        curr=max(x,curr+x);
        best=max(best,curr);
    }
    return best;
}
// TC: O(n), SC: O(1)
```

---

## 7️⃣ Matrix Chain Multiplication

```cpp
int matrixChain(vector<int> &arr){
    int n=arr.size();
    vector<vector<int>> dp(n,vector<int>(n,0));
    for(int len=2;len<n;len++){
        for(int i=1;i+len-1<n;i++){
            int j=i+len-1; dp[i][j]=INT_MAX;
            for(int k=i;k<j;k++)
                dp[i][j]=min(dp[i][j], dp[i][k]+dp[k+1][j]+arr[i-1]*arr[k]*arr[j]);
        }
    }
    return dp[1][n-1];
}
// TC: O(n^3), SC: O(n^2)
```

---

## 8️⃣ Longest Increasing Subsequence (LIS)

```cpp
int LIS(vector<int> &arr){
    int n=arr.size();
    vector<int> dp(n,1);
    for(int i=0;i<n;i++)
        for(int j=0;j<i;j++)
            if(arr[i]>arr[j]) dp[i]=max(dp[i], dp[j]+1);
    return *max_element(dp.begin(), dp.end());
}
// TC: O(n^2), SC: O(n)
```

**Optimized (O(n log n))**

```cpp
int LIS_opt(vector<int>& arr){
    vector<int> temp;
    for(int x:arr){
        auto it=lower_bound(temp.begin(), temp.end(), x);
        if(it==temp.end()) temp.push_back(x);
        else *it=x;
    }
    return temp.size();
}
// TC: O(n log n), SC: O(n)
```

---

## 9️⃣ 2D Grid DP (Unique Paths)

```cpp
int uniquePaths(int m,int n){
    vector<vector<int>> dp(m,vector<int>(n,1));
    for(int i=1;i<m;i++)
        for(int j=1;j<n;j++)
            dp[i][j]=dp[i-1][j]+dp[i][j-1];
    return dp[m-1][n-1];
}
// TC: O(m*n), SC: O(m*n)
```

---

## 🔟 DP on Trees (Subtree Sum)

```cpp
int dfs(TreeNode* root, vector<int> &dp){
    if(!root) return 0;
    int left=dfs(root->left, dp);
    int right=dfs(root->right, dp);
    int total=root->val+left+right;
    dp[root->val]=total;
    return total;
}
// TC: O(n), SC: O(n)
```

---


# 🧵 DP – Classical Problems Snippets

---

## 1️⃣ **0/1 Knapsack Variations**

### Max Value

```cpp
int knapsack(vector<int>& wt, vector<int>& val, int W){
    int n=wt.size();
    vector<int> dp(W+1,0);
    for(int i=0;i<n;i++){
        for(int w=W; w>=wt[i]; w--)
            dp[w] = max(dp[w], dp[w-wt[i]] + val[i]);
    }
    return dp[W];
}
// TC: O(n*W), SC: O(W)
```

---

## 2️⃣ **Unbounded Knapsack / Coin Change (Max Sum)**

```cpp
int unboundedKnapsack(vector<int>& wt, vector<int>& val, int W){
    vector<int> dp(W+1,0);
    for(int w=0; w<=W; w++){
        for(int i=0;i<wt.size();i++)
            if(wt[i]<=w) dp[w]=max(dp[w], dp[w-wt[i]]+val[i]);
    }
    return dp[W];
}
// TC: O(n*W), SC: O(W)
```

---

## 3️⃣ **Subset Sum Problem**

```cpp
bool subsetSum(vector<int>& arr, int sum){
    int n=arr.size();
    vector<bool> dp(sum+1,false);
    dp[0]=true;
    for(int num:arr)
        for(int i=sum;i>=num;i--)
            dp[i] = dp[i] || dp[i-num];
    return dp[sum];
}
// TC: O(n*sum), SC: O(sum)
```

---

## 4️⃣ **Longest Increasing Subsequence (LIS)**

```cpp
int LIS(vector<int>& arr){
    int n=arr.size();
    vector<int> dp(n,1);
    for(int i=0;i<n;i++)
        for(int j=0;j<i;j++)
            if(arr[i]>arr[j]) dp[i]=max(dp[i], dp[j]+1);
    return *max_element(dp.begin(), dp.end());
}
// TC: O(n^2), SC: O(n)
```

**Optimized O(n log n)**

```cpp
int LIS_opt(vector<int>& arr){
    vector<int> temp;
    for(int x:arr){
        auto it=lower_bound(temp.begin(), temp.end(), x);
        if(it==temp.end()) temp.push_back(x);
        else *it=x;
    }
    return temp.size();
}
// TC: O(n log n), SC: O(n)
```

---

## 5️⃣ **Longest Common Subsequence (LCS)**

```cpp
int LCS(string &a, string &b){
    int n=a.size(), m=b.size();
    vector<vector<int>> dp(n+1, vector<int>(m+1,0));
    for(int i=1;i<=n;i++)
        for(int j=1;j<=m;j++)
            dp[i][j]=(a[i-1]==b[j-1]?1+dp[i-1][j-1]:max(dp[i-1][j], dp[i][j-1]));
    return dp[n][m];
}
// TC: O(n*m), SC: O(n*m)
```

---

## 6️⃣ **Edit Distance (Levenshtein)**

```cpp
int editDistance(string &a, string &b){
    int n=a.size(), m=b.size();
    vector<vector<int>> dp(n+1, vector<int>(m+1,0));
    for(int i=0;i<=n;i++) dp[i][0]=i;
    for(int j=0;j<=m;j++) dp[0][j]=j;
    for(int i=1;i<=n;i++)
        for(int j=1;j<=m;j++)
            dp[i][j] = (a[i-1]==b[j-1]?dp[i-1][j-1]:1+min({dp[i-1][j-1], dp[i-1][j], dp[i][j-1]}));
    return dp[n][m];
}
// TC: O(n*m), SC: O(n*m)
```

---

## 7️⃣ **Max Sum Increasing Subsequence**

```cpp
int maxSumIS(vector<int>& arr){
    int n=arr.size();
    vector<int> dp(arr.begin(), arr.end());
    for(int i=1;i<n;i++)
        for(int j=0;j<i;j++)
            if(arr[i]>arr[j]) dp[i]=max(dp[i], dp[j]+arr[i]);
    return *max_element(dp.begin(), dp.end());
}
// TC: O(n^2), SC: O(n)
```

---

## 8️⃣ **Matrix Chain Multiplication**

```cpp
int matrixChain(vector<int> &arr){
    int n=arr.size();
    vector<vector<int>> dp(n,vector<int>(n,0));
    for(int len=2;len<n;len++)
        for(int i=1;i+len-1<n;i++){
            int j=i+len-1; dp[i][j]=INT_MAX;
            for(int k=i;k<j;k++)
                dp[i][j]=min(dp[i][j], dp[i][k]+dp[k+1][j]+arr[i-1]*arr[k]*arr[j]);
        }
    return dp[1][n-1];
}
// TC: O(n^3), SC: O(n^2)
```

---

## 9️⃣ **Egg Dropping Problem**

```cpp
int eggDrop(int n, int k){ // n eggs, k floors
    vector<vector<int>> dp(n+1, vector<int>(k+1,0));
    for(int i=1;i<=n;i++)
        for(int j=1;j<=k;j++){
            if(i==1) dp[i][j]=j;
            else{
                dp[i][j]=INT_MAX;
                for(int x=1;x<=j;x++)
                    dp[i][j]=min(dp[i][j], 1+max(dp[i-1][x-1], dp[i][j-x]));
            }
        }
    return dp[n][k];
}
// TC: O(n*k^2), SC: O(n*k)
```

---

## 🔟 **DP on Trees (Subtree Sum / Diameter)**

```cpp
int treeDiameter(TreeNode* root, int &res){
    if(!root) return 0;
    int l=treeDiameter(root->left,res);
    int r=treeDiameter(root->right,res);
    res=max(res,l+r);
    return 1+max(l,r);
}
// TC: O(n), SC: O(n)
```

---

## 1️⃣1️⃣ **Bitmask DP (TSP / Subset)**

```cpp
int tsp(int mask,int pos,vector<vector<int>> &dist, vector<vector<int>> &dp){
    int n=dist.size();
    if(mask==(1<<n)-1) return dist[pos][0];
    if(dp[mask][pos]!=-1) return dp[mask][pos];
    int ans=INT_MAX;
    for(int city=0;city<n;city++)
        if(!(mask&(1<<city)))
            ans=min(ans, dist[pos][city]+tsp(mask|(1<<city), city, dist, dp));
    return dp[mask][pos]=ans;
}
// TC: O(n*2^n), SC: O(n*2^n)
```

---

---

# 🧵 DP + Bit Manipulation – Classical Snippets

---

## 1️⃣ **Subset Sum / Subset DP (Bitmask)**

```cpp
int subsetSum(vector<int>& arr, int sum){
    int n=arr.size();
    vector<int> dp(1<<n,0);
    dp[0]=0;
    for(int mask=1;mask<(1<<n);mask++){
        int last = __builtin_ctz(mask); // last set bit (0-based)
        int prev = mask^(1<<last);
        dp[mask] = dp[prev] + arr[last];
    }
    int ans=0;
    for(int mask=0; mask<(1<<n); mask++)
        if(dp[mask]==sum) ans++;
    return ans;
}
// TC: O(n*2^n), SC: O(2^n)
```

---

## 2️⃣ **Traveling Salesman Problem (TSP) – Bitmask DP**

```cpp
int tsp(int mask,int pos,vector<vector<int>> &dist, vector<vector<int>> &dp){
    int n=dist.size();
    if(mask==(1<<n)-1) return dist[pos][0]; // all visited
    if(dp[mask][pos]!=-1) return dp[mask][pos];
    int ans=INT_MAX;
    for(int city=0;city<n;city++)
        if(!(mask&(1<<city)))
            ans=min(ans, dist[pos][city]+tsp(mask|(1<<city), city, dist, dp));
    return dp[mask][pos]=ans;
}
// TC: O(n*2^n), SC: O(n*2^n)
```

---

## 3️⃣ **Counting Number of Set Bits (Classic)**

```cpp
int countSetBits(int x){
    return __builtin_popcount(x); // for int
}

int countSetBitsLL(long long x){
    return __builtin_popcountll(x); // for long long
}
// TC: O(1)
```

---

## 4️⃣ **Iterate Over All Subsets of a Mask**

```cpp
int mask = 0b1011; // example mask
for(int sub=mask; sub; sub=(sub-1)&mask){
    // sub contains all subsets of mask
}
// TC: O(2^k) where k = # of set bits in mask
```

---

## 5️⃣ **DP on Subsets (Minimum/Maximum Cost)**

```cpp
int n = arr.size();
vector<int> dp(1<<n,INT_MAX);
dp[0]=0;
for(int mask=0;mask<(1<<n);mask++){
    for(int i=0;i<n;i++){
        if(!(mask&(1<<i))) // if i-th element not in mask
            dp[mask|(1<<i)] = min(dp[mask|(1<<i)], dp[mask]+cost[i]);
    }
}
// TC: O(n*2^n), SC: O(2^n)
```

---

## 6️⃣ **Minimum Vertex Cover in Tree (Bitmask DP)**

```cpp
int dp[1<<20]; // example size for small trees
// mask: included vertices
// use dfs + bitmask DP to calculate minimal vertex cover
// TC: O(n*2^n)
```

*(Tree-specific bitmask DP usually small n <= 20)*

---

## 7️⃣ **Mask-based Hamiltonian Path / Subset Optimization**

```cpp
int n = adj.size(); // graph size
vector<vector<int>> dp(1<<n, vector<int>(n,INT_MAX));
// dp[mask][i] = min cost to reach node i with visited nodes mask
dp[1][0]=0; // start at node 0
for(int mask=1;mask<(1<<n);mask++){
    for(int u=0;u<n;u++){
        if(mask&(1<<u)){
            for(int v=0;v<n;v++){
                if(!(mask&(1<<v)))
                    dp[mask|(1<<v)][v] = min(dp[mask|(1<<v)][v], dp[mask][u]+cost[u][v]);
            }
        }
    }
}
// TC: O(n^2*2^n), SC: O(n*2^n)
```

---

## 8️⃣ **Bitmask Tricks / Utilities**

```cpp
int x = 13; // 1101
int lowbit = x & -x;       // lowest set bit
bool isSet = x & (1<<i);   // check i-th bit
int setBit = x | (1<<i);   // set i-th bit
int unsetBit = x & ~(1<<i);// unset i-th bit
int toggle = x ^ (1<<i);   // toggle i-th bit
int cnt = __builtin_popcount(x); // number of set bits
```

---

## 9️⃣ **Subset DP Example – Partition Equal Subset Sum**

```cpp
bool canPartition(vector<int>& nums){
    int sum=accumulate(nums.begin(),nums.end(),0);
    if(sum%2!=0) return false;
    int target=sum/2, n=nums.size();
    vector<bool> dp(1<<n,false);
    dp[0]=true;
    for(int mask=0;mask<(1<<n);mask++){
        int s=0;
        for(int i=0;i<n;i++) if(mask&(1<<i)) s+=nums[i];
        if(s==target) return true;
    }
    return false;
}
// TC: O(n*2^n), SC: O(2^n)
```

---



# 🧵 Multisource BFS – Classical Snippets

---

## 1️⃣ **Multisource BFS – 1D (Array / Line)**

**Problem:** Multiple sources (positions) se simultaneously BFS / shortest distance calculate karna.

```cpp
vector<int> multiSourceBFS1D(vector<int> &arr, vector<int> &sources){
    int n = arr.size();
    vector<int> dist(n, -1); 
    queue<int> q;

    for(int src : sources){
        dist[src] = 0;
        q.push(src);
    }

    while(!q.empty()){
        int u = q.front(); q.pop();
        for(int v : {u-1,u+1}){ // neighbors in 1D
            if(v>=0 && v<n && dist[v]==-1){
                dist[v] = dist[u]+1;
                q.push(v);
            }
        }
    }
    return dist;
}
// TC: O(n), SC: O(n)
```

**Use case:**

* Spread of infection along a line
* Minimum distance from multiple stations

---

## 2️⃣ **Multisource BFS – 2D (Grid)**

**Problem:** Multiple sources in a grid (matrix) to calculate **minimum distance** to each cell.

```cpp
vector<vector<int>> multiSourceBFS2D(vector<vector<int>>& grid, vector<pair<int,int>> sources){
    int n = grid.size(), m = grid[0].size();
    vector<vector<int>> dist(n, vector<int>(m,-1));
    queue<pair<int,int>> q;

    for(auto src : sources){
        dist[src.first][src.second] = 0;
        q.push(src);
    }

    vector<int> dx = {-1,1,0,0};
    vector<int> dy = {0,0,-1,1};

    while(!q.empty()){
        auto [x,y] = q.front(); q.pop();
        for(int k=0;k<4;k++){
            int nx = x+dx[k], ny = y+dy[k];
            if(nx>=0 && nx<n && ny>=0 && ny<m && dist[nx][ny]==-1){
                dist[nx][ny] = dist[x][y]+1;
                q.push({nx,ny});
            }
        }
    }
    return dist;
}
// TC: O(n*m), SC: O(n*m)
```

**Use case:**

* Zombie infection spread in matrix
* Fire spread / water flow from multiple sources
* Minimum distance to nearest hospital / gate

---

## 3️⃣ **Classical Variant – Infection / Burn Tree (1D/2D)**

```cpp
// 1D Infection Time
vector<int> burnTree1D(vector<int>& tree, vector<int>& infected){
    return multiSourceBFS1D(tree, infected);
}

// 2D Fire / Zombie Spread
vector<vector<int>> burnTree2D(vector<vector<int>>& grid, vector<pair<int,int>>& infected){
    return multiSourceBFS2D(grid, infected);
}
```

* **TC:** O(n) for 1D, O(n*m) for 2D
* **SC:** O(n) for 1D, O(n*m) for 2D

---

## ✅ Notes / Classical Use

1. **Queue Initialization**: All sources pushed initially
2. **Distance Array**: `-1` or `INF` marks unvisited
3. **4-directional or neighbor loop**: 1D → left/right, 2D → up/down/left/right
4. **BFS Propagation**: Each level = distance/time
5. **Applications**: Zombie infection, Fire spread, Nearest gate, Multi-source shortest path

---




# 🟢 1️⃣ Count All Square Submatrices with All Ones – Leetcode 1277

**Problem Statement:**
Ek **binary matrix** di hui hai (0/1). Hume count karna hai **sab square submatrices** jisme **sirf 1 ho**.

**Example Input / Output:**

```text
Input:
matrix = [
  [0,1,1],
  [1,1,1],
  [0,1,1]
]
Output: 10

Explanation:
Squares of size 1: 6
Squares of size 2: 3
Squares of size 3: 1
Total = 10
```

**Pseudocode (DP):**

```
dp[i][j] = 0 if matrix[i][j]==0
dp[i][j] = min(dp[i-1][j], dp[i][j-1], dp[i-1][j-1]) + 1 if matrix[i][j]==1
ans += dp[i][j]
```

**CPP Code:**

```cpp
int countSquares(vector<vector<int>>& mat){
    int n = mat.size(), m = mat[0].size();
    vector<vector<int>> dp(n, vector<int>(m,0));
    int ans=0;
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
            if(mat[i][j]==1){
                if(i==0 || j==0) dp[i][j]=1;
                else dp[i][j]=min({dp[i-1][j],dp[i][j-1],dp[i-1][j-1]})+1;
                ans+=dp[i][j];
            }
        }
    }
    return ans;
}
// TC: O(n*m), SC: O(n*m)
```

---

# 🟢 2️⃣ Count Rectangles with All Ones – Leetcode 1504 / CP Classic

**Problem Statement:**
Binary matrix di hui hai. Count karo **sab rectangles** jisme sirf 1 ho.

**Example Input / Output:**

```text
Input:
matrix = [
 [1,1],
 [1,1]
]
Output: 9

Explanation:
Rectangles of size 1x1: 4
Rectangles of size 1x2: 2
Rectangles of size 2x1: 2
Rectangles of size 2x2: 1
Total = 4+2+2+1=9
```

**Pseudocode:**

```
For each row:
   height[j] = matrix[i][j]==0 ? 0 : height[j]+1
   For each column, count rectangles ending at (i,j) using height
```

**CPP Code (DP / Histogram Style):**

```cpp
int countRectangles(vector<vector<int>>& mat){
    int n=mat.size(), m=mat[0].size();
    vector<int> height(m,0);
    int ans=0;
    for(int i=0;i<n;i++){
        stack<int> st; // monotonic stack
        vector<int> sum(m,0);
        for(int j=0;j<m;j++){
            height[j] = mat[i][j]==0 ? 0 : height[j]+1;
            while(!st.empty() && height[st.top()]>=height[j]) st.pop();
            int k = st.empty()?-1:st.top();
            sum[j] = height[j]*(j-k) + (k>=0?sum[k]:0);
            ans+=sum[j];
            st.push(j);
        }
    }
    return ans;
}
// TC: O(n*m), SC: O(m)
```

---

# 🟢 3️⃣ Maximal Square – Leetcode 221

**Problem Statement:**
Binary matrix di hui hai. Find **maximum area square** with 1s.

**Example Input / Output:**

```text
Input:
matrix = [
 [1,0,1,0],
 [1,0,1,1],
 [1,1,1,1]
]
Output: 4

Explanation: Largest square has size 2x2 → area = 4
```

**Pseudocode (DP):**

```
dp[i][j] = 0 if matrix[i][j]==0
dp[i][j] = min(dp[i-1][j], dp[i][j-1], dp[i-1][j-1]) +1 if matrix[i][j]==1
max_area = max(max_area, dp[i][j]^2)
```

**CPP Code:**

```cpp
int maximalSquare(vector<vector<int>>& mat){
    int n=mat.size(), m=mat[0].size();
    vector<vector<int>> dp(n, vector<int>(m,0));
    int max_side=0;
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
            if(mat[i][j]==1){
                if(i==0 || j==0) dp[i][j]=1;
                else dp[i][j]=min({dp[i-1][j], dp[i][j-1], dp[i-1][j-1]})+1;
                max_side = max(max_side, dp[i][j]);
            }
        }
    }
    return max_side*max_side;
}
// TC: O(n*m), SC: O(n*m)
```

---

# 🟢 4️⃣ Maximal Rectangle – Leetcode 85

**Problem Statement:**
Binary matrix di hui hai. Find **maximum area rectangle** with 1s.

**Example Input / Output:**

```text
Input:
matrix = [
 [1,0,1,0,0],
 [1,0,1,1,1],
 [1,1,1,1,1],
 [1,0,0,1,0]
]
Output: 6

Explanation:
Largest rectangle is 2x3 → area = 6
```

**Pseudocode (Histogram + Stack):**

```
For each row:
   height[j] = matrix[i][j]==0 ? 0 : height[j]+1
   max area histogram(height)
```

**CPP Code:**

```cpp
int largestRectangleArea(vector<int>& heights){
    stack<int> st;
    heights.push_back(0);
    int ans=0;
    for(int i=0;i<heights.size();i++){
        while(!st.empty() && heights[st.top()]>=heights[i]){
            int h = heights[st.top()]; st.pop();
            int w = st.empty()?i:i-st.top()-1;
            ans=max(ans,h*w);
        }
        st.push(i);
    }
    return ans;
}

int maximalRectangle(vector<vector<int>>& mat){
    if(mat.empty()) return 0;
    int n=mat.size(), m=mat[0].size();
    vector<int> height(m,0);
    int ans=0;
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++)
            height[j] = mat[i][j]==0?0:height[j]+1;
        ans = max(ans, largestRectangleArea(height));
    }
    return ans;
}
// TC: O(n*m), SC: O(m)
```

---

# 🟢 5️⃣ Count Rectangles with Area ≤ K – CP Classical

**Problem Statement:**
Binary matrix / grid di hui hai. Count rectangles jinka **area ≤ K**.

**Idea / Pseudocode:**

* Enumerate all rectangles → O(n^2 * m^2)
* For each rectangle calculate area → if ≤ K, count++
* Optimization: prefix sum for 0/1 sum constraints

**CPP Code (Naive Version):**

```cpp
int countRectAreaK(vector<vector<int>>& mat, int K){
    int n=mat.size(), m=mat[0].size(), ans=0;
    for(int i1=0;i1<n;i1++){
        for(int j1=0;j1<m;j1++){
            for(int i2=i1;i2<n;i2++){
                for(int j2=j1;j2<m;j2++){
                    int area=(i2-i1+1)*(j2-j1+1);
                    if(area<=K) ans++;
                }
            }
        }
    }
    return ans;
}
// TC: O(n^2*m^2), SC: O(1)
```

---

✅ **Summary / Notes:**

| Problem                  | Technique                | TC         | SC     |
| ------------------------ | ------------------------ | ---------- | ------ |
| Count Squares            | DP                       | O(n*m)     | O(n*m) |
| Count Rectangles         | DP + Histogram           | O(n*m)     | O(m)   |
| Maximal Square           | DP                       | O(n*m)     | O(n*m) |
| Maximal Rectangle        | Histogram + Stack        | O(n*m)     | O(m)   |
| Rectangles with area ≤ K | Brute-force / Prefix Sum | O(n^2*m^2) | O(1)   |

---


# 🟢 1️⃣ Largest Rectangle in Histogram – Leetcode 84

**Problem Statement:**
Ek array heights[] di hui hai, jisme **bar heights** hain. Find **maximum area rectangle** jo consecutive bars ke andar aa sakta hai.

**Example Input / Output:**

```text
Input: heights = [2,1,5,6,2,3]
Output: 10

Explanation: Largest rectangle is [5,6] → area = 5*2=10
```

**Pseudocode (Monotonic Stack):**

```
append 0 to heights
stack st
for i=0 to n:
    while st not empty and heights[st.top()] >= heights[i]:
        h = heights[st.top()]; st.pop()
        w = st.empty()? i : i - st.top() -1
        ans = max(ans, h*w)
    st.push(i)
```

**CPP Code:**

```cpp
int largestRectangleArea(vector<int>& heights){
    stack<int> st;
    heights.push_back(0); // sentinel
    int ans=0;
    for(int i=0;i<heights.size();i++){
        while(!st.empty() && heights[st.top()]>=heights[i]){
            int h = heights[st.top()]; st.pop();
            int w = st.empty()? i : i-st.top()-1;
            ans = max(ans, h*w);
        }
        st.push(i);
    }
    return ans;
}
// TC: O(n), SC: O(n)
```

---

# 🟢 2️⃣ Maximal Rectangle in Binary Matrix – Leetcode 85

**Problem Statement:**
Binary matrix di hui hai. Find **maximum area rectangle** with 1s only.

**Idea / Explanation:**

* Convert **each row** into **histogram heights**
* Apply **Largest Rectangle in Histogram** per row

**CPP Code:**

```cpp
int maximalRectangle(vector<vector<int>>& mat){
    if(mat.empty()) return 0;
    int n=mat.size(), m=mat[0].size();
    vector<int> height(m,0);
    int ans=0;
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++)
            height[j] = mat[i][j]==0?0:height[j]+1;
        ans = max(ans, largestRectangleArea(height)); // previous snippet
    }
    return ans;
}
// TC: O(n*m), SC: O(m)
```

---

# 🟢 3️⃣ Largest Square in Binary Matrix – Leetcode 221

**Problem Statement:**
Binary matrix di hui hai. Find **maximum area square** with all 1s.

**Idea / Explanation:**

* DP approach: `dp[i][j] = min(dp[i-1][j], dp[i][j-1], dp[i-1][j-1]) + 1`
* Track **max side**, area = side^2

**CPP Code:**

```cpp
int maximalSquare(vector<vector<int>>& mat){
    int n=mat.size(), m=mat[0].size();
    vector<vector<int>> dp(n, vector<int>(m,0));
    int max_side=0;
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
            if(mat[i][j]==1){
                if(i==0 || j==0) dp[i][j]=1;
                else dp[i][j]=min({dp[i-1][j],dp[i][j-1],dp[i-1][j-1]})+1;
                max_side = max(max_side, dp[i][j]);
            }
        }
    }
    return max_side*max_side;
}
// TC: O(n*m), SC: O(n*m)
```

---

# 🟢 4️⃣ Maximal Rectangle with Constraints (e.g., area ≤ K) – CP Classical

**Problem Statement:**
Binary matrix / grid di hui hai. Count **all rectangles** jinka area ≤ K (or sum ≤ K).

**Idea / Explanation:**

* Enumerate all possible rectangles → O(n^2*m^2)
* Use **prefix sum** to calculate area / sum efficiently

**CPP Code (Naive / Brute Force):**

```cpp
int countRectAreaK(vector<vector<int>>& mat, int K){
    int n=mat.size(), m=mat[0].size(), ans=0;
    for(int i1=0;i1<n;i1++){
        for(int j1=0;j1<m;j1++){
            for(int i2=i1;i2<n;i2++){
                for(int j2=j1;j2<m;j2++){
                    int area=(i2-i1+1)*(j2-j1+1);
                    if(area<=K) ans++;
                }
            }
        }
    }
    return ans;
}
// TC: O(n^2*m^2), SC: O(1)
```

---

# ✅ Summary Table

| Problem                            | Technique                | TC         | SC     |
| ---------------------------------- | ------------------------ | ---------- | ------ |
| Largest Rectangle in Histogram     | Monotonic Stack          | O(n)       | O(n)   |
| Maximal Rectangle in Binary Matrix | Histogram + Stack        | O(n*m)     | O(m)   |
| Largest Square in Binary Matrix    | DP                       | O(n*m)     | O(n*m) |
| Maximal Rectangle with Constraints | Brute Force / Prefix Sum | O(n^2*m^2) | O(1)   |

---


# 🟢 1️⃣ Count Rectangles in N x M Grid – CP Classic

**Problem Statement:**
Given N rows aur M columns ka grid. Count karo **sab possible rectangles**.

**Example Input / Output:**

```text
Input: N=2, M=3
Output: 18

Explanation:
Rectangles = (N*(N+1)/2) * (M*(M+1)/2)
= (2*3/2)*(3*4/2) = 3*6 = 18
```

```text
Input: N=3, M=3
Output: 36
```

**Pseudocode / Formula:**

```
rectangles = (N*(N+1)/2) * (M*(M+1)/2)
```

**CPP Code:**

```cpp
long long countRectangles(int N, int M){
    return 1LL*N*(N+1)/2 * 1LL*M*(M+1)/2;
}
// TC: O(1), SC: O(1)
```

---

# 🟢 2️⃣ Count Squares in N x M Grid – CP Classic

**Problem Statement:**
Given N rows aur M columns ka grid. Count karo **sab possible squares**.

**Example Input / Output:**

```text
Input: N=3, M=2
Output: 8

Explanation:
min(N,M)=2
Squares of size 1x1: 3*2=6
Squares of size 2x2: 2*1=2
Total = 6+2=8
```

```text
Input: N=4, M=4
Output: 30
```

**Pseudocode / Formula:**

```
count=0
for k=1 to min(N,M):
    count += (N-k+1)*(M-k+1)
```

**CPP Code:**

```cpp
long long countSquares(int N, int M){
    long long ans=0;
    for(int k=1;k<=min(N,M);k++){
        ans += 1LL*(N-k+1)*(M-k+1);
    }
    return ans;
}
// TC: O(min(N,M)), SC: O(1)
```

---

# 🟢 3️⃣ Number of Rectangles with Sum = K – Leetcode 1074 / 1504

**Problem Statement:**
Matrix of integers di hui hai. Count **submatrices** jinka **sum = K**.

**Example Input / Output:**

```text
Input:
matrix = [
 [1,2],
 [3,4]
], K=3
Output: 2

Explanation: Submatrices with sum=3: [[1,2]] and [[3]]
```

```text
Input:
matrix = [
 [0,1,0],
 [1,1,1],
 [0,1,0]
], K=2
Output: 4
```

**Idea / Explanation:**

* Use **2D prefix sum**
* Enumerate top-left & bottom-right → O(n^2*m^2)
* Optimized with **1D prefix sum + hashmap** per row pair

**CPP Code (Naive Prefix Sum):**

```cpp
int numSubmatrixSumTarget(vector<vector<int>>& mat, int target){
    int n=mat.size(), m=mat[0].size();
    vector<vector<int>> pre(n+1, vector<int>(m+1,0));
    for(int i=1;i<=n;i++)
        for(int j=1;j<=m;j++)
            pre[i][j] = mat[i-1][j-1] + pre[i-1][j] + pre[i][j-1] - pre[i-1][j-1];
    
    int ans=0;
    for(int i1=1;i1<=n;i1++){
        for(int j1=1;j1<=m;j1++){
            for(int i2=i1;i2<=n;i2++){
                for(int j2=j1;j2<=m;j2++){
                    int sum = pre[i2][j2]-pre[i1-1][j2]-pre[i2][j1-1]+pre[i1-1][j1-1];
                    if(sum==target) ans++;
                }
            }
        }
    }
    return ans;
}
// TC: O(n^2*m^2), SC: O(n*m)
```

---

# 🟢 4️⃣ Max Rectangle Sum / Max Square Sum – Kadane 2D / DP

**Problem Statement:**
Given a 2D matrix (integers), find **maximum sum rectangle** / square.

**Example Input / Output:**

```text
Input:
matrix = [
 [1,2,-1],
 [-3,4,2],
 [1,-1,5]
]
Output: 10

Explanation:
Rectangle [[4,2],[-1,5]] sum = 10
```

**Idea / Explanation:**

* Use **Kadane 1D** per **compressed rows**
* Enumerate row pairs → compress columns → apply max subarray sum

**CPP Code:**

```cpp
int maxSumRectangle(vector<vector<int>>& mat){
    int n=mat.size(), m=mat[0].size();
    int ans=INT_MIN;
    for(int top=0;top<n;top++){
        vector<int> temp(m,0);
        for(int bottom=top;bottom<n;bottom++){
            for(int j=0;j<m;j++) temp[j]+=mat[bottom][j];
            // Kadane's on temp
            int sum=0, maxSum=INT_MIN;
            for(int x:temp){
                sum = max(x, sum+x);
                maxSum = max(maxSum,sum);
            }
            ans = max(ans,maxSum);
        }
    }
    return ans;
}
// TC: O(n^2*m), SC: O(m)
```

---

# ✅ Summary Table – Grid Rectangles / Squares

| Problem                         | Technique               | TC          | SC     |
| ------------------------------- | ----------------------- | ----------- | ------ |
| Count rectangles N x M          | Combinatorics formula   | O(1)        | O(1)   |
| Count squares N x M             | Sum over k              | O(min(N,M)) | O(1)   |
| Number of rectangles with sum=K | 2D prefix sum / hashmap | O(n^2*m^2)  | O(n*m) |
| Max rectangle sum               | Kadane 2D               | O(n^2*m)    | O(m)   |

---

# 🟢 1️⃣ Max Rectangle with 1s Only – Leetcode 85

**Problem Statement:**
Binary matrix di hui hai (0/1). Find **maximum area rectangle** jisme **sirf 1 ho**.

**Example Input / Output:**

```text
Input:
matrix = [
 [1,0,1,0,0],
 [1,0,1,1,1],
 [1,1,1,1,1],
 [1,0,0,1,0]
]
Output: 6

Explanation:
Largest rectangle = [[1,1,1],[1,1,1]] (2x3) → area=6
```

```text
Input:
matrix = [
 [0,1],
 [1,1]
]
Output: 2
```

**Idea / Explanation:**

* Har row ko **histogram heights** me convert karo
* Har row pe **Largest Rectangle in Histogram** apply karo

**CPP Code:**

```cpp
int largestRectangleArea(vector<int>& heights){
    stack<int> st; heights.push_back(0);
    int ans=0;
    for(int i=0;i<heights.size();i++){
        while(!st.empty() && heights[st.top()]>=heights[i]){
            int h=heights[st.top()]; st.pop();
            int w = st.empty()?i:i-st.top()-1;
            ans = max(ans,h*w);
        }
        st.push(i);
    }
    return ans;
}

int maximalRectangle(vector<vector<int>>& mat){
    if(mat.empty()) return 0;
    int n=mat.size(), m=mat[0].size();
    vector<int> height(m,0);
    int ans=0;
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++)
            height[j] = mat[i][j]==0?0:height[j]+1;
        ans = max(ans, largestRectangleArea(height));
    }
    return ans;
}
// TC: O(n*m), SC: O(m)
```

---

# 🟢 2️⃣ Max Rectangle with at Most K Zeros – CP / Matrix Problem

**Problem Statement:**
Binary matrix di hui hai (0/1). Find **maximum area rectangle** jisme **at most K zeros** ho.

**Example Input / Output:**

```text
Input:
matrix = [
 [1,0,1],
 [1,1,0]
], K=1
Output: 4

Explanation:
Rectangle [[1,0],[1,1]] has 1 zero → area=4
```

```text
Input:
matrix = [
 [1,0],
 [0,1]
], K=0
Output: 1
```

**Idea / Explanation:**

* Use **2D prefix sum** of zeros
* Enumerate all rectangles (top-left & bottom-right)
* Count zeros in rectangle → if ≤K, update max area

**CPP Code (Naive / Prefix Sum):**

```cpp
int maxRectWithKZeros(vector<vector<int>>& mat, int K){
    int n=mat.size(), m=mat[0].size(), ans=0;
    vector<vector<int>> pre(n+1, vector<int>(m+1,0));
    for(int i=1;i<=n;i++)
        for(int j=1;j<=m;j++)
            pre[i][j] = (mat[i-1][j-1]==0?1:0) + pre[i-1][j] + pre[i][j-1] - pre[i-1][j-1];
    
    for(int i1=1;i1<=n;i1++){
        for(int j1=1;j1<=m;j1++){
            for(int i2=i1;i2<=n;i2++){
                for(int j2=j1;j2<=m;j2++){
                    int zeros = pre[i2][j2]-pre[i1-1][j2]-pre[i2][j1-1]+pre[i1-1][j1-1];
                    if(zeros<=K)
                        ans = max(ans,(i2-i1+1)*(j2-j1+1));
                }
            }
        }
    }
    return ans;
}
// TC: O(n^2*m^2), SC: O(n*m)
```

---

# 🟢 3️⃣ Max Area Histogram (Skyline / Buildings) – Leetcode 84

**Problem Statement:**
Given heights of bars, find **maximum rectangle area** under histogram.

**Example Input / Output:**

```text
Input: heights = [2,1,5,6,2,3]
Output: 10

Explanation: Largest rectangle [5,6] → area=5*2=10
```

```text
Input: heights = [2,4]
Output: 4
```

**CPP Code:** *(Same as previous snippet)*

```cpp
int largestRectangleArea(vector<int>& heights){
    stack<int> st; heights.push_back(0);
    int ans=0;
    for(int i=0;i<heights.size();i++){
        while(!st.empty() && heights[st.top()]>=heights[i]){
            int h=heights[st.top()]; st.pop();
            int w = st.empty()?i:i-st.top()-1;
            ans = max(ans,h*w);
        }
        st.push(i);
    }
    return ans;
}
// TC: O(n), SC: O(n)
```

---

# 🟢 4️⃣ Count Rectangles with Exact Area – CP Classic

**Problem Statement:**
N x M grid di hui hai. Count all **rectangles** jinka **area = A**.

**Example Input / Output:**

```text
Input: N=3, M=3, A=2
Output: 12

Explanation:
- Rectangles of size 1x2: 3*2=6
- Rectangles of size 2x1: 2*3=6
Total = 6+6=12
```

```text
Input: N=2, M=4, A=4
Output: 3

Explanation:
- Only rectangles 2x2 = 2x2 possible = (2-2+1)*(4-2+1)=1*3=3
```

**Pseudocode:**

```
count = 0
for h=1 to N:
    if A % h != 0: continue
    w = A/h
    if w > M: continue
    count += (N-h+1)*(M-w+1)
```

**CPP Code:**

```cpp
long long countRectWithArea(int N,int M,int A){
    long long ans=0;
    for(int h=1;h<=N;h++){
        if(A%h!=0) continue;
        int w = A/h;
        if(w>M) continue;
        ans += 1LL*(N-h+1)*(M-w+1);
    }
    return ans;
}
// TC: O(N), SC: O(1)
```

---

# ✅ Summary Table – Rectangle / Histogram Batch

| Problem                          | Technique                | TC         | SC     |
| -------------------------------- | ------------------------ | ---------- | ------ |
| Max rectangle with 1s only       | Histogram + Stack        | O(n*m)     | O(m)   |
| Max rectangle with ≤ K zeros     | Prefix Sum + Brute-force | O(n^2*m^2) | O(n*m) |
| Max area histogram               | Monotonic Stack          | O(n)       | O(n)   |
| Count rectangles with exact area | Combinatorics / Loop     | O(N)       | O(1)   |

---
# 🟢 1️⃣ Activity Selection Problem

**Problem Statement:**
Given start[] and end[] times of activities, select **maximum number of non-overlapping activities**.

**CPP Code:**

```cpp
struct Activity { int start, end; };
int maxActivities(vector<Activity>& act){
    sort(act.begin(), act.end(), [](Activity &a, Activity &b){return a.end<b.end;});
    int ans=1, lastEnd=act[0].end;
    for(int i=1;i<act.size();i++){
        if(act[i].start >= lastEnd){
            ans++; lastEnd=act[i].end;
        }
    }
    return ans;
}
// TC: O(nlogn), SC: O(1)
```

---

# 🟢 2️⃣ Fractional Knapsack

**Problem Statement:**
Given items with weight[] and value[], and capacity W, maximize value. **Fractional items allowed**.

**CPP Code:**

```cpp
struct Item{int val, wt;};
bool cmp(Item &a, Item &b){ return (double)a.val/a.wt > (double)b.val/b.wt; }

double fractionalKnapsack(int W, vector<Item>& items){
    sort(items.begin(), items.end(), cmp);
    double ans=0;
    for(auto &it: items){
        if(W >= it.wt){ ans+=it.val; W-=it.wt; }
        else { ans += it.val * ((double)W/it.wt); break; }
    }
    return ans;
}
// TC: O(nlogn), SC: O(1)
```

---

# 🟢 3️⃣ Job Sequencing Problem (Deadline / Profit)

**Problem Statement:**
Jobs with deadline[] and profit[]. Maximize **profit** with at most one job per deadline.

**CPP Code:**

```cpp
struct Job{ int id, profit, deadline; };
bool cmp(Job &a, Job &b){ return a.profit>b.profit; }

pair<int,int> jobScheduling(vector<Job>& jobs){
    sort(jobs.begin(), jobs.end(), cmp);
    int maxDead = 0;
    for(auto &j: jobs) maxDead = max(maxDead, j.deadline);
    vector<int> slot(maxDead+1, -1);
    int countJobs=0, totalProfit=0;
    for(auto &j: jobs){
        for(int d=j.deadline; d>0; d--){
            if(slot[d]==-1){ slot[d]=j.id; countJobs++; totalProfit+=j.profit; break; }
        }
    }
    return {countJobs, totalProfit};
}
// TC: O(nlogn + n*maxDeadline), SC: O(maxDeadline)
```

---

# 🟢 4️⃣ Minimum Coins / Change Problem

**Problem Statement:**
Given coins[] and amount, find **minimum number of coins** (if greedy applicable, i.e., canonical denominations).

**CPP Code:**

```cpp
int minCoins(vector<int>& coins, int amount){
    sort(coins.rbegin(), coins.rend()); // descending
    int ans=0;
    for(int c: coins){
        ans += amount/c;
        amount %= c;
    }
    return amount==0 ? ans : -1; // -1 means not possible
}
// TC: O(nlogn), SC: O(1)
```

---

# 🟢 5️⃣ Huffman Encoding (Greedy / Priority Queue)

**Problem Statement:**
Given char[] with frequency[], build **min cost prefix code**.

**CPP Code:**

```cpp
struct Node{ char ch; int freq; Node *l,*r; Node(char c,int f):ch(c),freq(f),l(NULL),r(NULL){} };
struct cmp{ bool operator()(Node* a, Node* b){ return a->freq > b->freq; }};

int huffmanCost(vector<int>& freq){
    priority_queue<Node*, vector<Node*>, cmp> pq;
    for(int f: freq) pq.push(new Node('$',f));
    int totalCost=0;
    while(pq.size()>1){
        Node *a=pq.top(); pq.pop();
        Node *b=pq.top(); pq.pop();
        Node *newNode = new Node('$', a->freq + b->freq);
        totalCost += a->freq + b->freq;
        pq.push(newNode);
    }
    return totalCost;
}
// TC: O(nlogn), SC: O(n)
```

---

# 🟢 6️⃣ Gas Station / Circular Petrol Problem

**Problem Statement:**
n stations with petrol[] and cost[] to next. Find **starting station** to complete circle (if exists).

**CPP Code:**

```cpp
int canCompleteCircuit(vector<int>& gas, vector<int>& cost){
    int total=0, tank=0, start=0;
    for(int i=0;i<gas.size();i++){
        tank += gas[i]-cost[i];
        total += gas[i]-cost[i];
        if(tank<0){ start=i+1; tank=0; }
    }
    return total>=0?start:-1;
}
// TC: O(n), SC: O(1)
```

---

# 🟢 7️⃣ Greedy Interval Merging

**Problem Statement:**
Merge overlapping intervals.

**CPP Code:**

```cpp
vector<vector<int>> mergeIntervals(vector<vector<int>>& intervals){
    if(intervals.empty()) return {};
    sort(intervals.begin(), intervals.end());
    vector<vector<int>> merged;
    merged.push_back(intervals[0]);
    for(int i=1;i<intervals.size();i++){
        if(intervals[i][0] <= merged.back()[1])
            merged.back()[1] = max(merged.back()[1], intervals[i][1]);
        else
            merged.push_back(intervals[i]);
    }
    return merged;
}
// TC: O(nlogn), SC: O(n)
```

---

# ✅ Summary Table – Greedy Classical

| Problem             | Technique              | TC               | SC             |
| ------------------- | ---------------------- | ---------------- | -------------- |
| Activity Selection  | Sort by end            | O(nlogn)         | O(1)           |
| Fractional Knapsack | Sort by value/weight   | O(nlogn)         | O(1)           |
| Job Sequencing      | Sort by profit + array | O(n*maxDeadline) | O(maxDeadline) |
| Min Coins           | Sort descending        | O(nlogn)         | O(1)           |
| Huffman Encoding    | Min-heap               | O(nlogn)         | O(n)           |
| Gas Station         | Greedy sum             | O(n)             | O(1)           |
| Merge Intervals     | Sort + merge           | O(nlogn)         | O(n)           |

---


# 🟢 1️⃣ Maximum Sum Subarray of Size K

**Problem Statement:**
Given array `arr[]` and integer `K`, find **maximum sum** of subarray of size K.

```cpp
int maxSumSubarray(vector<int>& arr, int K){
    int n=arr.size(), sum=0, ans=INT_MIN;
    for(int i=0;i<n;i++){
        sum += arr[i];
        if(i>=K) sum -= arr[i-K];
        if(i>=K-1) ans = max(ans,sum);
    }
    return ans;
}
// TC: O(n), SC: O(1)
```

---

# 🟢 2️⃣ Minimum Size Subarray with Sum ≥ S

**Problem Statement:**
Given array `arr[]` and integer `S`, find **smallest length** subarray whose sum ≥ S.

```cpp
int minSubArrayLen(vector<int>& arr, int S){
    int n=arr.size(), sum=0, ans=INT_MAX;
    int left=0;
    for(int right=0;right<n;right++){
        sum += arr[right];
        while(sum >= S){
            ans = min(ans, right-left+1);
            sum -= arr[left++];
        }
    }
    return ans==INT_MAX?0:ans;
}
// TC: O(n), SC: O(1)
```

---

# 🟢 3️⃣ Longest Substring Without Repeating Characters

**Problem Statement:**
Given string `s`, find length of **longest substring** without repeating chars.

```cpp
int lengthOfLongestSubstring(string s){
    vector<int> last(256,-1);
    int n=s.size(), ans=0, start=0;
    for(int i=0;i<n;i++){
        if(last[s[i]] >= start) start = last[s[i]]+1;
        last[s[i]]=i;
        ans = max(ans,i-start+1);
    }
    return ans;
}
// TC: O(n), SC: O(256)=O(1)
```

---

# 🟢 4️⃣ Maximum Sum Subarray with Size ≤ K (Variable Size)

**Problem Statement:**
Given array, find max sum of subarray **size ≤ K**.

```cpp
int maxSumAtMostK(vector<int>& arr, int K){
    int n=arr.size(), sum=0, ans=INT_MIN;
    int left=0;
    for(int right=0;right<n;right++){
        sum += arr[right];
        while(right-left+1 > K) sum -= arr[left++];
        ans = max(ans,sum);
    }
    return ans;
}
// TC: O(n), SC: O(1)
```

---

# 🟢 5️⃣ Count of Subarrays with Sum = K (Using Sliding Window – Only for Non-negative Numbers)

**Problem Statement:**
Given array of **non-negative numbers**, count subarrays with sum = K.

```cpp
int countSubarraysSumK(vector<int>& arr, int K){
    int n=arr.size(), left=0, sum=0, ans=0;
    for(int right=0;right<n;right++){
        sum += arr[right];
        while(sum > K && left<=right) sum -= arr[left++];
        if(sum==K) ans++;
    }
    return ans;
}
// TC: O(n), SC: O(1)
// Note: Works only if arr[i] ≥ 0
```

---

# 🟢 6️⃣ Sliding Window Maximum (Leetcode 239)

**Problem Statement:**
Given array `arr[]` and window size `k`, find **maximum in each window**.

```cpp
vector<int> maxSlidingWindow(vector<int>& arr, int k){
    int n=arr.size();
    deque<int> dq; vector<int> ans;
    for(int i=0;i<n;i++){
        while(!dq.empty() && dq.front() <= i-k) dq.pop_front();
        while(!dq.empty() && arr[dq.back()] <= arr[i]) dq.pop_back();
        dq.push_back(i);
        if(i>=k-1) ans.push_back(arr[dq.front()]);
    }
    return ans;
}
// TC: O(n), SC: O(k)
```

---

# 🟢 7️⃣ Longest Subarray with At Most K Distinct Elements

**Problem Statement:**
Find **longest subarray** with at most K distinct elements.

```cpp
int longestSubarrayKDistinct(vector<int>& arr, int K){
    unordered_map<int,int> freq;
    int left=0, ans=0;
    for(int right=0;right<arr.size();right++){
        freq[arr[right]]++;
        while(freq.size()>K){
            if(--freq[arr[left]]==0) freq.erase(arr[left]);
            left++;
        }
        ans = max(ans,right-left+1);
    }
    return ans;
}
// TC: O(n), SC: O(n)
```

---

# ✅ Summary Table – Sliding Window Classical

| Problem                         | Technique       | TC   | SC   |
| ------------------------------- | --------------- | ---- | ---- |
| Max sum subarray size K         | Fixed window    | O(n) | O(1) |
| Min length subarray sum ≥ S     | Variable window | O(n) | O(1) |
| Longest substring unique        | Hash / map      | O(n) | O(1) |
| Max sum subarray ≤ K            | Variable window | O(n) | O(1) |
| Count subarrays sum=K (non-neg) | Variable window | O(n) | O(1) |
| Sliding window maximum          | Deque           | O(n) | O(k) |
| Longest subarray ≤ K distinct   | Map + window    | O(n) | O(n) |

---




---