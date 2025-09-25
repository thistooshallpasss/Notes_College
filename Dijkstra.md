Here's a properly formatted and organized list of Dijkstra’s algorithm-related problems and similar problems, as you've requested:

### Dijkstra’s Algorithm Problems:

1. **Path with Maximum Probability**
2. **Network Delay Time**
3. **The Maze II**
4. **The Maze III**
5. **Path with Minimum Effort**
6. **Find the City with the Smallest Number of Neighbors at a Threshold Distance**
7. **Cheapest Flights Within K Stops**
8. **Reachable Nodes in Subdivided Graph**
9. **Number of Restricted Paths from First to Last Node**
10. **Shortest Path in a Grid with Obstacles Elimination**
11. **Number of Ways to Arrive at Destination**
12. **Shortest Path in Binary Matrix**
13. **Articulation Points and Bridges**

---

### Additional Related Problems (For Dijkstra’s or Similar Algorithms):

14. **Dijkstra’s Algorithm Part - 1**
15. **Dijkstra’s Algorithm Part - 2**
16. **Dijkstra’s Algorithm Part - 3**
17. **Design Graph with Shortest Path Calculator**
18. **Find Edges in Shortest Paths**
19. **Freedom Trail**
20. **Minimum Cost to Convert String I**
21. **Minimum Cost to Make at Least One Valid Path in a Grid**
22. **Minimum Obstacle Removal to Reach Corner**
23. **Minimum Time to Visit a Cell in a Grid**
24. **Modify Graph Edge Weights**
25. **Second Minimum Time to Reach Destination**
26. **Shortest Distance After Road Addition Queries I**
27. **Trapping Rain Water II**
28. **The Maze II** (Duplicate)
29. **The Maze III** (Duplicate)

---



## Q1: Path with Maximum Probability

**Q: Problem Statement (Hinglish)**
Ek undirected weighted graph diya hai jisme nodes 0 se n-1 tak hai. Tumhe ek source aur destination node diya hoga. Har edge ki ek success probability hai. Tumhe find karna hai ki **max probability path** kya ho sakta hai source se destination tak.

**Q: Example**
n=3, edges = [[0,1],[1,2],[0,2]], succProb = [0.5,0.5,0.2], start=0, end=2
Output = 0.25 (path 0→1→2 deta hai max prob 0.5*0.5 = 0.25)

**Q: Approach (Hinglish)**
Dijkstra jaisa use karenge lekin distance maximize karna hai (multiplication probabilities). Max-heap priority queue ka use karenge.

**Q: Pseudocode**

```
priority_queue with (prob,node)
push(start,1.0)
while not empty:
    pop max prob
    if node == end: return prob
    for each nei: push prob*edgeProb
```

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

// Function to find max probability path
double maxProbability(int n, vector<vector<int>>& edges, vector<double>& succProb, int start, int end) {
    // adjacency list bana dete hai
    vector<vector<pair<int,double>>> graph(n);
    for(int i=0;i<edges.size();i++){
        int u=edges[i][0], v=edges[i][1];
        double p=succProb[i];
        graph[u].push_back({v,p});
        graph[v].push_back({u,p});
    }

    // max-heap (probability,node)
    priority_queue<pair<double,int>> pq;
    vector<double> dist(n,0.0);
    dist[start]=1.0;
    pq.push({1.0,start});

    while(!pq.empty()){
        auto [prob,node]=pq.top(); pq.pop();
        if(node==end) return prob;
        if(prob<dist[node]) continue;
        for(auto [nei,p]:graph[node]){
            double newProb=prob*p;
            if(newProb>dist[nei]){
                dist[nei]=newProb;
                pq.push({newProb,nei});
            }
        }
    }
    return 0.0;
}

/*
Time Complexity: O(E log V)  // pq operations
Space Complexity: O(V+E)    // graph + dist
*/
```

---

## Q2: Network Delay Time

**Q: Problem Statement (Hinglish)**
Directed weighted graph diya hai with n nodes. Har edge ek time dikhata hai. Tumhe ek starting node k diya hoga. Tumhe calculate karna hai minimum time sabhi nodes tak signal pahunchne me lagta hai. Agar koi node unreachable ho to -1 return karo.

**Q: Example**
n=4, times=[[2,1,1],[2,3,1],[3,4,1]], k=2
Output=2

**Q: Approach (Hinglish)**
Dijkstra use karenge kyunki shortest time nikalna hai ek source se sab tak. Max distance among all reachable nodes return karenge.

**Q: Pseudocode**

```
build graph
dijkstra from k
if any node unreachable return -1
else return max(dist)
```

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

int networkDelayTime(vector<vector<int>>& times, int n, int k) {
    vector<vector<pair<int,int>>> graph(n+1);
    for(auto &t:times){
        graph[t[0]].push_back({t[1],t[2]});
    }

    vector<int> dist(n+1,INT_MAX);
    dist[k]=0;
    priority_queue<pair<int,int>,vector<pair<int,int>>,greater<>> pq;
    pq.push({0,k});

    while(!pq.empty()){
        auto [time,node]=pq.top(); pq.pop();
        if(time>dist[node]) continue;
        for(auto [nei,w]:graph[node]){
            if(time+w<dist[nei]){
                dist[nei]=time+w;
                pq.push({dist[nei],nei});
            }
        }
    }

    int ans=0;
    for(int i=1;i<=n;i++){
        if(dist[i]==INT_MAX) return -1;
        ans=max(ans,dist[i]);
    }
    return ans;
}

/*
Time Complexity: O(E log V)
Space Complexity: O(V+E)
*/
```

---

## Q3: The Maze II

**Q: Problem Statement (Hinglish)**
Ek maze diya hai grid ke form me jisme 0 = empty, 1 = wall. Ball kisi direction me roll karegi jab tak wall ya boundary na aa jaye. Tumhe find karna hai **minimum steps ball ko start se destination tak pahunchane ke liye**. Agar possible nahi hai to -1.

**Q: Example**
maze = [[0,0,1,0,0],[0,0,0,0,0],[0,0,0,1,0],[1,1,0,1,1],[0,0,0,0,0]]
start=[0,4], dest=[4,4]
Output=12

**Q: Approach (Hinglish)**
Dijkstra use karenge kyunki har move me distance count hota hai (not uniform 1). BFS kaam nahi karega kyunki distance variable hai.

**Q: Pseudocode**

```
dijkstra with (dist,node)
roll in 4 dirs until wall
update dist
```

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

int shortestDistance(vector<vector<int>>& maze, vector<int>& start, vector<int>& dest) {
    int m=maze.size(), n=maze[0].size();
    vector<vector<int>> dist(m,vector<int>(n,INT_MAX));
    dist[start[0]][start[1]]=0;
    priority_queue<tuple<int,int,int>,vector<tuple<int,int,int>>,greater<>> pq;
    pq.push({0,start[0],start[1]});
    vector<int> dirs={0,1,0,-1,0};

    while(!pq.empty()){
        auto [d,x,y]=pq.top(); pq.pop();
        if(x==dest[0] && y==dest[1]) return d;
        if(d>dist[x][y]) continue;
        for(int k=0;k<4;k++){
            int nx=x,ny=y,steps=0;
            while(nx+dirs[k]>=0 && nx+dirs[k]<m && ny+dirs[k+1]>=0 && ny+dirs[k+1]<n && maze[nx+dirs[k]][ny+dirs[k+1]]==0){
                nx+=dirs[k];
                ny+=dirs[k+1];
                steps++;
            }
            if(d+steps<dist[nx][ny]){
                dist[nx][ny]=d+steps;
                pq.push({dist[nx][ny],nx,ny});
            }
        }
    }
    return -1;
}

/*
Time Complexity: O(m*n log(m*n))
Space Complexity: O(m*n)
*/
```

---

## Q4: The Maze III

**Q: Problem Statement (Hinglish)**
Maze II jaisa hi hai, lekin yaha tumhe **shortest distance + lexicographically smallest path** return karna hai ball ko destination tak le jaane ke liye. Path string me hoga (u,d,l,r). Agar koi path nahi to `"impossible"`.

**Q: Example**
maze=[[0,0,0,0,0],[1,1,0,0,1],[0,0,0,0,0],[0,1,0,0,1],[0,1,0,0,0]]
start=[4,3], dest=[0,1]
Output="lul"

**Q: Approach (Hinglish)**
Dijkstra + priority queue with (dist,path,node). Agar distance same ho to path ka lexicographical order check karenge.

**Q: Pseudocode**

```
pq with (dist,path,x,y)
while pq not empty:
    pop
    if dest reached return path
    roll dirs
    update dist and path
```

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

string findShortestWay(vector<vector<int>>& maze, vector<int>& start, vector<int>& dest) {
    int m=maze.size(), n=maze[0].size();
    vector<vector<int>> dist(m,vector<int>(n,INT_MAX));
    vector<vector<string>> path(m,vector<string>(n,""));
    dist[start[0]][start[1]]=0;
    priority_queue<tuple<int,string,int,int>,vector<tuple<int,string,int,int>>,greater<>> pq;
    pq.push({0,"",start[0],start[1]});

    vector<int> dirs={0,1,0,-1,0};
    vector<char> moves={'r','d','l','u'};

    while(!pq.empty()){
        auto [d,p,x,y]=pq.top(); pq.pop();
        if(x==dest[0] && y==dest[1]) return p;
        if(d>dist[x][y] || (d==dist[x][y] && p>path[x][y])) continue;
        for(int k=0;k<4;k++){
            int nx=x,ny=y,steps=0;
            while(nx+dirs[k]>=0 && nx+dirs[k]<m && ny+dirs[k+1]>=0 && ny+dirs[k+1]<n && maze[nx+dirs[k]][ny+dirs[k+1]]==0){
                nx+=dirs[k]; ny+=dirs[k+1]; steps++;
                if(nx==dest[0] && ny==dest[1]) break;
            }
            string newPath=p+moves[k];
            if(d+steps<dist[nx][ny] || (d+steps==dist[nx][ny] && newPath<path[nx][ny])){
                dist[nx][ny]=d+steps;
                path[nx][ny]=newPath;
                pq.push({dist[nx][ny],newPath,nx,ny});
            }
        }
    }
    return "impossible";
}

/*
Time Complexity: O(m*n log(m*n))
Space Complexity: O(m*n)
*/
```

---



## Q5: Path with Minimum Effort

**Q: Problem Statement (Hinglish)**
Ek grid diya hai jisme har cell ek height represent karta hai. Tumhe (0,0) se (m-1,n-1) tak jana hai. Effort = kisi path me maximum height difference between adjacent cells. Tumhe wo path nikalna hai jisme minimum effort lage.

**Q: Example**
heights = [[1,2,2],[3,8,2],[5,3,5]]
Output = 2

**Q: Approach (Hinglish)**
Dijkstra algorithm use karenge lekin distance definition thoda alag hoga. Har cell tak pahunchne ka cost hoga `max(previousEffort, abs(diff))`.

**Q: Pseudocode**

```
pq with (effort,x,y)
while pq not empty:
  pop
  if dest reached return effort
  explore 4 dirs
  update if min effort mila
```

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

int minimumEffortPath(vector<vector<int>>& heights) {
    int m=heights.size(), n=heights[0].size();
    vector<vector<int>> dist(m,vector<int>(n,INT_MAX));
    dist[0][0]=0;
    priority_queue<tuple<int,int,int>,vector<tuple<int,int,int>>,greater<>> pq;
    pq.push({0,0,0});
    vector<int> dirs={0,1,0,-1,0};

    while(!pq.empty()){
        auto [eff,x,y]=pq.top(); pq.pop();
        if(x==m-1 && y==n-1) return eff;
        if(eff>dist[x][y]) continue;
        for(int k=0;k<4;k++){
            int nx=x+dirs[k], ny=y+dirs[k+1];
            if(nx>=0 && ny>=0 && nx<m && ny<n){
                int newEff=max(eff,abs(heights[nx][ny]-heights[x][y]));
                if(newEff<dist[nx][ny]){
                    dist[nx][ny]=newEff;
                    pq.push({newEff,nx,ny});
                }
            }
        }
    }
    return 0;
}

/*
Time Complexity: O(m*n log(m*n))
Space Complexity: O(m*n)
*/
```

---

## Q6: Find the City with the Smallest Number of Neighbors at a Threshold Distance

**Q: Problem Statement (Hinglish)**
n cities (0..n-1) aur weighted undirected edges diye gaye hai. Tumhe wo city find karni hai jiske paas threshold distance ke andar **minimum number of reachable neighbors** ho. Agar tie ho to **largest city index** return karna hai.

**Q: Example**
n=4, edges=[[0,1,3],[1,2,1],[2,3,1],[0,3,4]], threshold=4
Output=3

**Q: Approach (Hinglish)**
All-pairs shortest path chahiye → Floyd Warshall use karenge. Fir har city ke liye count kare ki kitne neighbors <= threshold distance hai. Min count ke hisaab se answer.

**Q: Pseudocode**

```
dist matrix init
floyd warshall
for each city:
   count neighbors within threshold
choose city with min count, if tie max index
```

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

int findTheCity(int n, vector<vector<int>>& edges, int distanceThreshold) {
    vector<vector<int>> dist(n,vector<int>(n,1e9));
    for(int i=0;i<n;i++) dist[i][i]=0;
    for(auto &e:edges){
        dist[e[0]][e[1]]=e[2];
        dist[e[1]][e[0]]=e[2];
    }

    // Floyd Warshall
    for(int k=0;k<n;k++){
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                if(dist[i][k]+dist[k][j]<dist[i][j])
                    dist[i][j]=dist[i][k]+dist[k][j];
            }
        }
    }

    int ans=-1, minCnt=1e9;
    for(int i=0;i<n;i++){
        int cnt=0;
        for(int j=0;j<n;j++){
            if(dist[i][j]<=distanceThreshold) cnt++;
        }
        if(cnt<=minCnt){
            minCnt=cnt;
            ans=i; // prefer larger index in tie
        }
    }
    return ans;
}

/*
Time Complexity: O(n^3)
Space Complexity: O(n^2)
*/
```

---

## Q7: Cheapest Flights Within K Stops

**Q: Problem Statement (Hinglish)**
Ek directed weighted graph diya hai jisme flights hai. Tumhe source se destination tak sabse sasta cost nikalna hai agar tum maximum K stops (edges) use kar sakte ho. Agar reachable nahi hai to -1 return karo.

**Q: Example**
n=4, flights=[[0,1,100],[1,2,100],[2,3,100],[0,2,500]], src=0, dst=3, k=1
Output=500

**Q: Approach (Hinglish)**
Bellman-Ford type relaxation karenge K+1 times (kyunki max K stops = K+1 edges). Har iteration me shortest distance update karenge.

**Q: Pseudocode**

```
dist=inf
dist[src]=0
for i=0..k:
   temp=dist
   for each edge(u,v,w):
       if dist[u]+w<temp[v]: update
return dist[dst] or -1
```

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

int findCheapestPrice(int n, vector<vector<int>>& flights, int src, int dst, int K) {
    vector<int> dist(n,1e9);
    dist[src]=0;

    for(int i=0;i<=K;i++){
        vector<int> temp=dist;
        for(auto &f:flights){
            int u=f[0], v=f[1], w=f[2];
            if(dist[u]!=1e9 && dist[u]+w<temp[v]){
                temp[v]=dist[u]+w;
            }
        }
        dist=temp;
    }
    return dist[dst]==1e9 ? -1 : dist[dst];
}

/*
Time Complexity: O(K*E)
Space Complexity: O(V)
*/
```


---


## Q8: Reachable Nodes in Subdivided Graph

**Q: Problem Statement (Hinglish)**
Ek undirected weighted graph diya hai. Har edge `(u,v,cnt)` matlab u aur v ke beech me `cnt` new nodes subdivide kiye gaye hai. Tumhare paas `maxMoves` steps hai aur tum node 0 se start karte ho. Tumhe count karna hai ki **total reachable nodes** kitne honge (original + subdivided).

**Q: Example**
n=4, edges=[[0,1,10],[0,2,1],[1,2,2]], maxMoves=6
Output=13

**Q: Approach (Hinglish)**
Dijkstra ka use karke min distance har node tak nikalenge. Har edge me kitne subdivided nodes reachable hai wo bhi count karna padega:

* min(maxMoves - dist[u], cnt) + min(maxMoves - dist[v], cnt)

**Q: Pseudocode**

```
dijkstra from 0
ans = count of nodes with dist <= maxMoves
for each edge (u,v,cnt):
   ans += min(maxMoves-dist[u],cnt)+min(maxMoves-dist[v],cnt)
   but cap at cnt
```

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

int reachableNodes(vector<vector<int>>& edges, int maxMoves, int n) {
    vector<vector<pair<int,int>>> graph(n);
    for(auto &e:edges){
        graph[e[0]].push_back({e[1],e[2]+1});
        graph[e[1]].push_back({e[0],e[2]+1});
    }
    vector<int> dist(n,INT_MAX);
    dist[0]=0;
    priority_queue<pair<int,int>,vector<pair<int,int>>,greater<>> pq;
    pq.push({0,0});

    while(!pq.empty()){
        auto [d,u]=pq.top(); pq.pop();
        if(d>dist[u]) continue;
        for(auto [v,w]:graph[u]){
            if(d+w<dist[v]){
                dist[v]=d+w;
                pq.push({dist[v],v});
            }
        }
    }

    long long ans=0;
    for(int i=0;i<n;i++){
        if(dist[i]<=maxMoves) ans++;
    }
    for(auto &e:edges){
        long long a=dist[e[0]]>maxMoves?0:maxMoves-dist[e[0]];
        long long b=dist[e[1]]>maxMoves?0:maxMoves-dist[e[1]];
        ans+=min((long long)e[2],a+b);
    }
    return ans;
}

/*
Time Complexity: O(E log V)
Space Complexity: O(V+E)
*/
```

---

## Q9: Number of Restricted Paths from First to Last Node

**Q: Problem Statement (Hinglish)**
Undirected weighted graph diya hai 1 se n nodes tak. Ek restricted path wo hai jisme har node ke distance to node n strictly decreasing ho. Tumhe count karna hai ki 1 se n tak kitne restricted paths possible hai. Answer modulo 1e9+7.

**Q: Example**
n=5, edges=[[1,2,3],[1,3,3],[2,3,1],[1,4,2],[5,2,2],[3,5,1],[5,4,10]]
Output=3

**Q: Approach (Hinglish)**

1. Dijkstra se distance of every node to node n calculate karo.
2. Fir DFS + DP (memoization) use karke count karo paths 1 se n tak with strictly decreasing distance property.

**Q: Pseudocode**

```
dist = dijkstra from n
dfs(u):
  if u==n return 1
  if memo[u] set return memo[u]
  ans=0
  for nei in adj[u]:
     if dist[nei]<dist[u]:
        ans+=dfs(nei)
  memo[u]=ans
return dfs(1)
```

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

const int MOD=1e9+7;

int dfs(int u, vector<vector<pair<int,int>>>& graph, vector<int>& dist, vector<int>& dp){
    if(u==dist.size()-1) return 1;
    if(dp[u]!=-1) return dp[u];
    long long ans=0;
    for(auto [v,w]:graph[u]){
        if(dist[v]<dist[u]){
            ans=(ans+dfs(v,graph,dist,dp))%MOD;
        }
    }
    return dp[u]=ans;
}

int countRestrictedPaths(int n, vector<vector<int>>& edges) {
    vector<vector<pair<int,int>>> graph(n+1);
    for(auto &e:edges){
        graph[e[0]].push_back({e[1],e[2]});
        graph[e[1]].push_back({e[0],e[2]});
    }

    vector<int> dist(n+1,INT_MAX);
    dist[n]=0;
    priority_queue<pair<int,int>,vector<pair<int,int>>,greater<>> pq;
    pq.push({0,n});
    while(!pq.empty()){
        auto [d,u]=pq.top(); pq.pop();
        if(d>dist[u]) continue;
        for(auto [v,w]:graph[u]){
            if(d+w<dist[v]){
                dist[v]=d+w;
                pq.push({dist[v],v});
            }
        }
    }

    vector<int> dp(n+1,-1);
    return dfs(1,graph,dist,dp);
}

/*
Time Complexity: O(E log V + V+E)
Space Complexity: O(V+E)
*/
```

---

## Q10: Shortest Path in a Grid with Obstacles Elimination

**Q: Problem Statement (Hinglish)**
Ek grid diya hai jisme 0 = free, 1 = obstacle. Tum (0,0) se (m-1,n-1) tak jana chahte ho. Tum maximum `k` obstacles hata sakte ho. Minimum steps return karo. Agar possible nahi to -1.

**Q: Example**
grid=[[0,0,0],[1,1,0],[0,0,0],[0,1,1],[0,0,0]], k=1
Output=6

**Q: Approach (Hinglish)**
BFS use karenge kyunki hume shortest path chahiye. State = (x,y,remainingK). Agar ek obstacle mila aur remainingK>0 to usko eliminate karke aage badh jao. Visited[x][y][k] maintain karenge.

**Q: Pseudocode**

```
queue with (x,y,steps,kLeft)
while not empty:
  pop
  if dest reached return steps
  explore 4 dirs
  if free -> push
  if obstacle and kLeft>0 -> push with kLeft-1
```

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

int shortestPath(vector<vector<int>>& grid, int k) {
    int m=grid.size(), n=grid[0].size();
    vector<vector<int>> seen(m,vector<int>(n,-1));
    queue<tuple<int,int,int,int>> q; // x,y,steps,kLeft
    q.push({0,0,0,k});
    seen[0][0]=k;
    vector<int> dirs={0,1,0,-1,0};

    while(!q.empty()){
        auto [x,y,steps,rem]=q.front(); q.pop();
        if(x==m-1 && y==n-1) return steps;
        for(int d=0;d<4;d++){
            int nx=x+dirs[d], ny=y+dirs[d+1];
            if(nx>=0 && ny>=0 && nx<m && ny<n){
                int nk=rem-grid[nx][ny];
                if(nk>=0 && nk>seen[nx][ny]){
                    seen[nx][ny]=nk;
                    q.push({nx,ny,steps+1,nk});
                }
            }
        }
    }
    return -1;
}

/*
Time Complexity: O(m*n*k)
Space Complexity: O(m*n)
*/
```

---

## Q11: Number of Ways to Arrive at Destination

**Q: Problem Statement (Hinglish)**
Ek weighted undirected graph hai with `n` nodes (0..n-1). Tumhe `0` se `n-1` tak shortest path lena hai. Tumhe count karna hai ki **kitne alag shortest paths** possible hai (mod 1e9+7).

**Q: Example**
n=7, roads = [[0,6,7],[0,1,2],[1,2,3],[1,3,3],[6,3,3],[3,5,1],[6,5,1],[2,5,1],[0,4,5],[4,6,2]]
Output = 4

**Q: Approach (Hinglish)**
Dijkstra + DP:

* dist[] = shortest distance
* ways[] = number of ways to reach node with shortest distance
  Update rule:
* If new shorter distance → update dist + ways
* If equal distance → add ways

**Q: Pseudocode**

```
dist[0]=0, ways[0]=1
pq with (dist,node)
while pq not empty:
   pop
   for nei:
      if d+w < dist[nei]:
         update dist+ways
      else if d+w == dist[nei]:
         ways[nei]+=ways[node]
return ways[n-1]
```

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

const int MOD=1e9+7;

int countPaths(int n, vector<vector<int>>& roads) {
    vector<vector<pair<int,int>>> graph(n);
    for(auto &r:roads){
        graph[r[0]].push_back({r[1],r[2]});
        graph[r[1]].push_back({r[0],r[2]});
    }

    vector<long long> dist(n,LLONG_MAX), ways(n,0);
    dist[0]=0; ways[0]=1;
    priority_queue<pair<long long,int>,vector<pair<long long,int>>,greater<>> pq;
    pq.push({0,0});

    while(!pq.empty()){
        auto [d,u]=pq.top(); pq.pop();
        if(d>dist[u]) continue;
        for(auto [v,w]:graph[u]){
            if(d+w<dist[v]){
                dist[v]=d+w;
                ways[v]=ways[u];
                pq.push({dist[v],v});
            }
            else if(d+w==dist[v]){
                ways[v]=(ways[v]+ways[u])%MOD;
            }
        }
    }
    return ways[n-1]%MOD;
}

/*
Time Complexity: O(E log V)
Space Complexity: O(V+E)
*/
```

---

## Q12: Shortest Path in Binary Matrix

**Q: Problem Statement (Hinglish)**
Ek n×n binary grid diya hai. Tumhe top-left `(0,0)` se bottom-right `(n-1,n-1)` tak jana hai. Tum diagonals bhi move kar sakte ho. Har cell me `0` = free, `1` = blocked. Tumhe shortest path length nikalna hai, ya -1 agar possible nahi.

**Q: Example**
grid = [[0,1],[1,0]]
Output = 2

**Q: Approach (Hinglish)**
Simple BFS (kyunki sabhi moves cost =1). Diagonal moves bhi allow hai → 8 directions.

**Q: Pseudocode**

```
queue with (x,y,dist)
while not empty:
  pop
  if dest return dist
  push all valid neighbors
return -1
```

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

int shortestPathBinaryMatrix(vector<vector<int>>& grid) {
    int n=grid.size();
    if(grid[0][0]==1 || grid[n-1][n-1]==1) return -1;
    queue<tuple<int,int,int>> q;
    q.push({0,0,1});
    vector<vector<int>> vis(n,vector<int>(n,0));
    vis[0][0]=1;
    vector<int> dirs={-1,-1,-1,0,0,1,1,1,-1};

    while(!q.empty()){
        auto [x,y,d]=q.front(); q.pop();
        if(x==n-1 && y==n-1) return d;
        for(int k=0;k<8;k++){
            int nx=x+dirs[k], ny=y+dirs[k+1];
            if(nx>=0 && ny>=0 && nx<n && ny<n && !vis[nx][ny] && grid[nx][ny]==0){
                vis[nx][ny]=1;
                q.push({nx,ny,d+1});
            }
        }
    }
    return -1;
}

/*
Time Complexity: O(n^2)
Space Complexity: O(n^2)
*/
```

---

## Q13: Articulation Points and Bridges

**Q: Problem Statement (Hinglish)**
Ek undirected graph diya hai. Tumhe **articulation points (cut vertices)** aur **bridges (cut edges)** find karne hain.

* Articulation point: a node jisko remove karne par graph ke connected components badh jaate hain.
* Bridge: ek edge jisko remove karne par graph ke connected components badh jaate hain.

**Q: Example**
n=5, edges=[[1,0],[0,2],[2,1],[0,3],[3,4]]
Articulation Points = {0,3}
Bridges = {(3,4),(0,3)}

**Q: Approach (Hinglish)**
Tarjan’s Algorithm (DFS based):

* Maintain `tin[u]` = time of entry, `low[u]` = lowest reachable time.
* DFS traversal se update karo.
* Condition:

  * AP: if (u is root with 2+ children) OR (u not root && low[v] ≥ tin[u])
  * Bridge: if (low[v] > tin[u])

**Q: Pseudocode**

```
dfs(u,parent):
  tin[u]=low[u]=timer++
  for v in adj[u]:
    if v==parent continue
    if not visited:
       dfs(v,u)
       low[u]=min(low[u],low[v])
       if(low[v]>tin[u]) => bridge
       if(low[v]>=tin[u] && parent!=-1) => articulation
    else:
       low[u]=min(low[u],tin[v])
```

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

class Solution {
public:
    int timer;
    vector<int> tin, low, vis, isAP;
    vector<pair<int,int>> bridges;

    void dfs(int u, int p, vector<vector<int>>& adj){
        vis[u]=1;
        tin[u]=low[u]=timer++;
        int child=0;

        for(int v:adj[u]){
            if(v==p) continue;
            if(!vis[v]){
                dfs(v,u,adj);
                low[u]=min(low[u],low[v]);
                if(low[v]>tin[u]) bridges.push_back({u,v});
                if(low[v]>=tin[u] && p!=-1) isAP[u]=1;
                child++;
            }
            else{
                low[u]=min(low[u],tin[v]);
            }
        }
        if(p==-1 && child>1) isAP[u]=1;
    }

    void articulationAndBridges(int n, vector<vector<int>>& edges){
        vector<vector<int>> adj(n);
        for(auto &e:edges){
            adj[e[0]].push_back(e[1]);
            adj[e[1]].push_back(e[0]);
        }
        timer=0;
        tin.assign(n,-1);
        low.assign(n,-1);
        vis.assign(n,0);
        isAP.assign(n,0);
        bridges.clear();

        for(int i=0;i<n;i++){
            if(!vis[i]) dfs(i,-1,adj);
        }

        cout<<"Articulation Points: ";
        for(int i=0;i<n;i++) if(isAP[i]) cout<<i<<" ";
        cout<<"\nBridges: ";
        for(auto &b:bridges) cout<<"("<<b.first<<","<<b.second<<") ";
        cout<<"\n";
    }
};

/*
Time Complexity: O(V+E)
Space Complexity: O(V+E)
*/
```

---


## Q14: Dijkstra’s Algorithm Part - 1 (Basics: shortest path from source)

**Q: Problem Statement (Hinglish)**
Ek weighted undirected graph diya hai, tumhe ek fixed source `src` se sabhi nodes tak ke shortest distances nikalne hain. Agar koi node unreachable hai toh distance = ∞.

**Q: Example**
n=5, edges=[[0,1,2],[0,2,4],[1,2,1],[1,3,7],[2,4,3]], src=0
Output = [0,2,3,9,6]

**Q: Approach (Hinglish)**

* Priority queue (min-heap) use karo
* dist[src]=0, baaki INF
* Jab tak pq khali nahi hota, min-distance node leke uske neighbors update karo

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

vector<int> dijkstra(int V, vector<vector<int>> adj[], int S) {
    vector<int> dist(V, INT_MAX);
    dist[S]=0;
    priority_queue<pair<int,int>, vector<pair<int,int>>, greater<>> pq;
    pq.push({0,S});

    while(!pq.empty()){
        auto [d,u]=pq.top(); pq.pop();
        if(d>dist[u]) continue;
        for(auto &edge:adj[u]){
            int v=edge[0], w=edge[1];
            if(dist[u]+w<dist[v]){
                dist[v]=dist[u]+w;
                pq.push({dist[v],v});
            }
        }
    }
    return dist;
}

/*
Time Complexity: O((V+E) log V)
Space Complexity: O(V+E)
*/
```

---

## Q15: Dijkstra’s Algorithm Part - 2 (Shortest path reconstruction)

**Q: Problem Statement (Hinglish)**
Sirf distance nahi, balki tumhe **actual shortest path** (source → destination) print karni hai. Agar path nahi milta toh `-1`.

**Q: Example**
Graph: same as above, src=0, dest=4
Output Path: [0,1,2,4] with distance 6

**Q: Approach (Hinglish)**

* Saath me `parent[]` array rakho
* Jab bhi dist update ho, `parent[v]=u`
* Last me dest se parent array reverse traverse karke path nikaalo

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

vector<int> dijkstraPath(int V, vector<vector<int>> adj[], int S, int D) {
    vector<int> dist(V, INT_MAX), parent(V);
    for(int i=0;i<V;i++) parent[i]=i;
    dist[S]=0;
    priority_queue<pair<int,int>, vector<pair<int,int>>, greater<>> pq;
    pq.push({0,S});

    while(!pq.empty()){
        auto [d,u]=pq.top(); pq.pop();
        if(d>dist[u]) continue;
        for(auto &edge:adj[u]){
            int v=edge[0], w=edge[1];
            if(dist[u]+w<dist[v]){
                dist[v]=dist[u]+w;
                parent[v]=u;
                pq.push({dist[v],v});
            }
        }
    }

    if(dist[D]==INT_MAX) return {-1};

    vector<int> path;
    int node=D;
    while(parent[node]!=node){
        path.push_back(node);
        node=parent[node];
    }
    path.push_back(S);
    reverse(path.begin(),path.end());
    return path;
}
```

---

## Q16: Dijkstra’s Algorithm Part - 3 (Using adjacency matrix / multiple queries)

**Q: Problem Statement (Hinglish)**
Kabhi kabhi graph adjacency matrix ke form me diya hota hai. Tumhe `src` se shortest distance nikalna hai **without using STL pq** (sirf arrays). Ye ek simpler version hai (O(V²)).

**Q: Example**
adjMatrix =

```
0 4 0 0 0  
4 0 8 0 0  
0 8 0 7 0  
0 0 7 0 9  
0 0 0 9 0
```

src=0
Output = [0,4,12,19,28]

**Q: Approach (Hinglish)**

* dist[] = INF initially
* har step pe **minimum unvisited node** choose karo (O(V))
* uske neighbors update karo

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

vector<int> dijkstraMatrix(int V, vector<vector<int>>& graph, int src){
    vector<int> dist(V, INT_MAX);
    vector<int> vis(V,0);
    dist[src]=0;

    for(int i=0;i<V-1;i++){
        int u=-1;
        for(int j=0;j<V;j++){
            if(!vis[j] && (u==-1 || dist[j]<dist[u])) u=j;
        }
        vis[u]=1;
        for(int v=0;v<V;v++){
            if(graph[u][v] && !vis[v] && dist[u]!=INT_MAX){
                dist[v]=min(dist[v], dist[u]+graph[u][v]);
            }
        }
    }
    return dist;
}

/*
Time Complexity: O(V^2)
Space Complexity: O(V)
*/
```

---


## Q17: Design Graph with Shortest Path Calculator

**Q: Problem Statement (Hinglish)**
Tumhe ek class banani hai jo graph ko represent kare aur shortest path query answer kare.
Operations:

1. `addEdge(u,v,w)` → weighted edge add karo
2. `shortestPath(node1,node2)` → node1 se node2 tak ka shortest distance return karo, agar path nahi toh `-1`.

**Q: Example**

```
Graph g(5, {{0,1,4},{0,2,3},{1,2,1},{1,3,2},{2,3,4}});
g.shortestPath(0,3) → 6
```

**Q: Approach (Hinglish)**
Har query ke liye Dijkstra run karenge. Adjacency list maintain karenge.

**Q: Pseudocode**

```
class Graph:
   store adj list
   addEdge(u,v,w)
   shortestPath(u,v): run dijkstra return dist[v]
```

**Q: C++ Function/Class**

```cpp
#include<bits/stdc++.h>
using namespace std;

class Graph {
    int n;
    vector<vector<pair<int,int>>> adj;
public:
    Graph(int n, vector<vector<int>>& edges){
        this->n=n;
        adj.resize(n);
        for(auto &e:edges){
            adj[e[0]].push_back({e[1],e[2]});
        }
    }
    void addEdge(vector<int> edge){
        adj[edge[0]].push_back({edge[1],edge[2]});
    }
    int shortestPath(int src,int dst){
        vector<int> dist(n,1e9);
        dist[src]=0;
        priority_queue<pair<int,int>,vector<pair<int,int>>,greater<>> pq;
        pq.push({0,src});
        while(!pq.empty()){
            auto [d,u]=pq.top();pq.pop();
            if(d>dist[u]) continue;
            for(auto &[v,w]:adj[u]){
                if(dist[u]+w<dist[v]){
                    dist[v]=dist[u]+w;
                    pq.push({dist[v],v});
                }
            }
        }
        return dist[dst]==1e9 ? -1:dist[dst];
    }
};

/*
Time Complexity: O((V+E) log V) per query
Space Complexity: O(V+E)
*/
```

---

## Q18: Find Edges in Shortest Paths

**Q: Problem Statement (Hinglish)**
Ek weighted undirected graph diya hai aur tumhe find karna hai ki kaunse edges **at least ek shortest path** ka part hain from source (1) to destination (n).

**Q: Example**
n=5, edges=[[1,2,2],[1,3,3],[2,4,2],[3,5,1],[4,5,2]]
Output = { (1,2), (2,4), (4,5), (3,5) }

**Q: Approach (Hinglish)**

* Dijkstra run karo from source → dist1[]
* Dijkstra run karo from dest → dist2[]
* Total shortestDist = dist1[n]
* Agar edge(u,v,w) satisfy kare: `dist1[u]+w+dist2[v]==shortestDist` (ya reverse), toh wo edge ek shortest path ka part hai.

**Q: Pseudocode**

```
dist1 = dijkstra(src)
dist2 = dijkstra(dest)
shortest = dist1[dest]
for edge(u,v,w):
   if dist1[u]+w+dist2[v]==shortest OR dist1[v]+w+dist2[u]==shortest:
       mark edge
```

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

vector<int> dijkstraHelper(int n, int src, vector<vector<pair<int,int>>>& adj){
    vector<int> dist(n+1,1e9);
    dist[src]=0;
    priority_queue<pair<int,int>,vector<pair<int,int>>,greater<>> pq;
    pq.push({0,src});
    while(!pq.empty()){
        auto [d,u]=pq.top();pq.pop();
        if(d>dist[u]) continue;
        for(auto &[v,w]:adj[u]){
            if(dist[u]+w<dist[v]){
                dist[v]=dist[u]+w;
                pq.push({dist[v],v});
            }
        }
    }
    return dist;
}

vector<vector<int>> findEdgesInShortestPaths(int n, vector<vector<int>>& edges){
    vector<vector<pair<int,int>>> adj(n+1);
    for(auto &e:edges){
        adj[e[0]].push_back({e[1],e[2]});
        adj[e[1]].push_back({e[0],e[2]});
    }
    auto dist1=dijkstraHelper(n,1,adj);
    auto dist2=dijkstraHelper(n,n,adj);
    int shortest=dist1[n];
    vector<vector<int>> ans;
    for(auto &e:edges){
        int u=e[0], v=e[1], w=e[2];
        if(dist1[u]+w+dist2[v]==shortest || dist1[v]+w+dist2[u]==shortest){
            ans.push_back(e);
        }
    }
    return ans;
}

/*
Time Complexity: O((V+E) log V)
Space Complexity: O(V+E)
*/
```

---

## Q19: Freedom Trail

**Q: Problem Statement (Hinglish)**
Ek circular ring string (clockwise rotate kar sakte ho) aur ek key string diya hai. Tumhe ring ko rotate karke aur button press karke key banani hai. Ek move = ek rotate (left/right by 1) ya ek press. Minimum steps nikalna hai.

**Q: Example**
ring="godding", key="gd"
Output=4

**Q: Approach (Hinglish)**

* DP + memoization use karenge.
* har key char ke liye ring me sab positions store karo.
* DP(state: currentRingPos, keyIndex) → minSteps.
* Transition: try all occurrences of key[i], calculate rotate distance (min clockwise, anticlockwise).

**Q: Pseudocode**

```
dp(pos,i):
  if i==len(key) return 0
  ans=INF
  for each index in positions[key[i]]:
      step = min(|pos-index|, n-|pos-index|)
      ans=min(ans, step+1+dp(index,i+1))
  return ans
```

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

int dpHelper(int pos,int idx,string& ring,string& key,unordered_map<char,vector<int>>& mp,vector<vector<int>>& memo){
    if(idx==key.size()) return 0;
    if(memo[pos][idx]!=-1) return memo[pos][idx];
    int n=ring.size();
    int ans=1e9;
    for(int next:mp[key[idx]]){
        int diff=abs(pos-next);
        int step=min(diff,n-diff);
        ans=min(ans, step+1+dpHelper(next,idx+1,ring,key,mp,memo));
    }
    return memo[pos][idx]=ans;
}

int findRotateSteps(string ring,string key){
    unordered_map<char,vector<int>> mp;
    for(int i=0;i<ring.size();i++) mp[ring[i]].push_back(i);
    vector<vector<int>> memo(ring.size(), vector<int>(key.size(),-1));
    return dpHelper(0,0,ring,key,mp,memo);
}

/*
Time Complexity: O(|ring| * |key| * avgOccurrences)
Space Complexity: O(|ring| * |key|)
*/
```

---
## Q20: Minimum Cost to Convert String I

**Q: Problem Statement (Hinglish)**
Tumhe do strings `s` aur `t` diye gaye hain, same length ke. Tumhe s ko t me convert karna hai. Ek operation me tum ek character ko dusre me convert kar sakte ho, cost given hai rules me. Tumhe **minimum total cost** nikalna hai. Agar convert karna possible nahi ho toh -1 return karo.

**Q: Example**
s="abcd", t="bcda"
rules: a→b(1), b→c(2), c→d(3), d→a(4)
Output = 10

**Q: Approach (Hinglish)**

* Characters ke beech cost ka graph banao.
* Floyd Warshall se **minimum conversion cost** nikal lo for all pairs.
* Har position pe s[i]→t[i] ka cost add karo. Agar koi impossible (INF) mila toh -1.

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

long long minimumCost(string s, string t, vector<char>& original, vector<char>& changed, vector<int>& cost) {
    if(s.size()!=t.size()) return -1;
    vector<vector<long long>> dist(26,vector<long long>(26,1e12));
    for(int i=0;i<26;i++) dist[i][i]=0;
    for(int i=0;i<original.size();i++){
        dist[original[i]-'a'][changed[i]-'a']=min(dist[original[i]-'a'][changed[i]-'a'],(long long)cost[i]);
    }
    for(int k=0;k<26;k++)
        for(int i=0;i<26;i++)
            for(int j=0;j<26;j++)
                dist[i][j]=min(dist[i][j],dist[i][k]+dist[k][j]);

    long long ans=0;
    for(int i=0;i<s.size();i++){
        if(s[i]==t[i]) continue;
        if(dist[s[i]-'a'][t[i]-'a']==1e12) return -1;
        ans+=dist[s[i]-'a'][t[i]-'a'];
    }
    return ans;
}

/*
Time Complexity: O(26^3 + |s|)
Space Complexity: O(26^2)
*/
```

---

## Q21: Minimum Cost to Make at Least One Valid Path in a Grid

**Q: Problem Statement (Hinglish)**
Ek m×n grid hai jisme har cell ek direction dikhata hai (1=right,2=left,3=down,4=up). Tum (0,0) se (m-1,n-1) tak jaana chahte ho. Agar tum direction follow karte ho to cost=0, agar tumhe kisi aur direction me jaana hai to cost=1. Minimum cost nikalna hai.

**Q: Example**
grid=[[1,1,3],[3,2,2],[1,1,4]]
Output=0

**Q: Approach (Hinglish)**

* Ye ek **0-1 BFS problem** hai.
* Deque use karenge: agar move same direction hai to push_front (cost=0), nahi to push_back (cost=1).

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

int minCost(vector<vector<int>>& grid) {
    int m=grid.size(), n=grid[0].size();
    vector<vector<int>> dist(m,vector<int>(n,1e9));
    deque<pair<int,int>> dq;
    dq.push_back({0,0});
    dist[0][0]=0;
    vector<int> dx={0,0,1,-1};
    vector<int> dy={1,-1,0,0};

    while(!dq.empty()){
        auto [x,y]=dq.front(); dq.pop_front();
        for(int k=0;k<4;k++){
            int nx=x+dx[k], ny=y+dy[k];
            if(nx>=0 && ny>=0 && nx<m && ny<n){
                int newCost=dist[x][y]+(grid[x][y]!=k+1);
                if(newCost<dist[nx][ny]){
                    dist[nx][ny]=newCost;
                    if(grid[x][y]==k+1) dq.push_front({nx,ny});
                    else dq.push_back({nx,ny});
                }
            }
        }
    }
    return dist[m-1][n-1];
}

/*
Time Complexity: O(m*n)
Space Complexity: O(m*n)
*/
```

---

## Q22: Minimum Obstacle Removal to Reach Corner

**Q: Problem Statement (Hinglish)**
Tumhe ek grid diya hai jisme 0 = empty aur 1 = obstacle. Tumhe (0,0) se (m-1,n-1) tak minimum obstacles remove karke jaana hai.

**Q: Example**
grid=[[0,1,1],[1,1,0],[1,1,0]]
Output=2

**Q: Approach (Hinglish)**

* Again **0-1 BFS** use karenge.
* Agar next cell=0 hai to push_front, agar 1 hai to push_back with +1 cost.

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

int minimumObstacles(vector<vector<int>>& grid) {
    int m=grid.size(), n=grid[0].size();
    vector<vector<int>> dist(m,vector<int>(n,1e9));
    deque<pair<int,int>> dq;
    dq.push_back({0,0});
    dist[0][0]=grid[0][0];
    vector<int> dx={0,0,1,-1}, dy={1,-1,0,0};

    while(!dq.empty()){
        auto [x,y]=dq.front(); dq.pop_front();
        for(int k=0;k<4;k++){
            int nx=x+dx[k], ny=y+dy[k];
            if(nx>=0 && ny>=0 && nx<m && ny<n){
                int newCost=dist[x][y]+grid[nx][ny];
                if(newCost<dist[nx][ny]){
                    dist[nx][ny]=newCost;
                    if(grid[nx][ny]==0) dq.push_front({nx,ny});
                    else dq.push_back({nx,ny});
                }
            }
        }
    }
    return dist[m-1][n-1];
}

/*
Time Complexity: O(m*n)
Space Complexity: O(m*n)
*/
```

---

## Q23: Minimum Time to Visit a Cell in a Grid

**Q: Problem Statement (Hinglish)**
Ek m×n grid hai jisme har cell me ek non-negative integer likha hai → matlab us cell ko tabhi visit kar sakte ho jab time ≥ us cell ka value. Tum (0,0) se (m-1,n-1) tak sabse jaldi pahunchna chahte ho. Har move ka time +1.

**Q: Example**
grid=[[0,2,4],[3,2,1],[1,0,0]]
Output=4

**Q: Approach (Hinglish)**

* Dijkstra priority_queue use karenge.
* Har move me time=max(currentTime+1, grid[nextCell]). Agar wait karna pade to bhi handle ho jayega.

**Q: C++ Function**

```cpp
#include<bits/stdc++.h>
using namespace std;

int minimumTime(vector<vector<int>>& grid) {
    int m=grid.size(), n=grid[0].size();
    if(grid[0][1]>1 && grid[1][0]>1) return -1; // edge case

    vector<vector<int>> dist(m,vector<int>(n,1e9));
    dist[0][0]=0;
    priority_queue<tuple<int,int,int>,vector<tuple<int,int,int>>,greater<>> pq;
    pq.push({0,0,0});
    vector<int> dx={0,0,1,-1}, dy={1,-1,0,0};

    while(!pq.empty()){
        auto [t,x,y]=pq.top(); pq.pop();
        if(x==m-1 && y==n-1) return t;
        if(t>dist[x][y]) continue;
        for(int k=0;k<4;k++){
            int nx=x+dx[k], ny=y+dy[k];
            if(nx>=0 && ny>=0 && nx<m && ny<n){
                int nt=t+1;
                if(nt<grid[nx][ny]){ 
                    int diff=grid[nx][ny]-nt;
                    if(diff%2==1) nt=grid[nx][ny];
                    else nt=grid[nx][ny]+1;
                }
                if(nt<dist[nx][ny]){
                    dist[nx][ny]=nt;
                    pq.push({nt,nx,ny});
                }
            }
        }
    }
    return -1;
}

/*
Time Complexity: O(m*n log(m*n))
Space Complexity: O(m*n)
*/
```

---





## 27. Trapping Rain Water II

**Q: Problem Statement (Hinglish)**
Tumhe ek 2D grid (matrix) di gayi hai jo ek terrain represent karti hai, jisme har cell ki height hai.
Barish ke baad kitna paani trap ho sakta hai usko find karo. Paani grid ke andar tabhi rukega jab uske charo taraf badi boundary hogi.

**Example**

```
Input: heightMap = [
  [1,4,3,1,3,2],
  [3,2,1,3,2,4],
  [2,3,3,2,3,1]
]
Output: 4
Explanation: 4 units water trap ho sakta hai.
```

---

**Approach (Hinglish, crisp)**

* Ye 2D version hai **Trapping Rain Water** ka.
* Boundary cells paani ko bahar nikal dete hain → toh sabse chhoti boundary se start karna hoga.
* Use **Priority Queue (Min Heap)**:

  1. Pehle saare boundary cells heap mein daalo.
  2. Heap se sabse chhoti height nikalo, aur uske neighbors check karo.
  3. Agar neighbor ki height chhoti hai, toh wahan paani trap hoga = `max(0, currHeight - neighborHeight)`.
  4. Fir neighbor ko heap mein daalo with updated max boundary height.
* Ye ek BFS + heap approach hai (like Dijkstra).

---

**Pseudocode**

```
1. Push all boundary cells into minHeap, mark visited
2. While heap not empty:
   a. Pop smallest height cell
   b. For each unvisited neighbor:
       - water += max(0, currHeight - neighborHeight)
       - push neighbor with max(currHeight, neighborHeight)
3. Return total water
```

---

**C++ Code (main working function)**

```cpp
#include <bits/stdc++.h>
using namespace std;

// Function: trapRainWater 2D
int trapRainWater(vector<vector<int>>& heightMap) {
    int m = heightMap.size(), n = heightMap[0].size();
    if (m <= 2 || n <= 2) return 0; // 2D border case: paani trap hi nahi hoga
    
    // Min-heap {height, x, y}
    priority_queue<vector<int>, vector<vector<int>>, greater<>> pq;
    vector<vector<int>> vis(m, vector<int>(n, 0));
    
    // Step 1: saare boundary cells heap mein daalo
    for (int i = 0; i < m; i++) {
        pq.push({heightMap[i][0], i, 0});
        pq.push({heightMap[i][n-1], i, n-1});
        vis[i][0] = vis[i][n-1] = 1;
    }
    for (int j = 0; j < n; j++) {
        pq.push({heightMap[0][j], 0, j});
        pq.push({heightMap[m-1][j], m-1, j});
        vis[0][j] = vis[m-1][j] = 1;
    }
    
    // Step 2: process heap
    int res = 0;
    int dirs[4][2] = {{1,0},{-1,0},{0,1},{0,-1}};
    while (!pq.empty()) {
        auto top = pq.top(); pq.pop();
        int h = top[0], x = top[1], y = top[2];
        
        // check neighbors
        for (auto &d : dirs) {
            int nx = x + d[0], ny = y + d[1];
            if (nx < 0 || ny < 0 || nx >= m || ny >= n || vis[nx][ny]) continue;
            vis[nx][ny] = 1;
            
            // Agar neighbor ki height kam hai → water trap hoga
            res += max(0, h - heightMap[nx][ny]);
            
            // Push max boundary height
            pq.push({max(h, heightMap[nx][ny]), nx, ny});
        }
    }
    return res;
}

/*
Time Complexity: O(m * n * log(m*n))  (heap operations)
Space Complexity: O(m * n)  (visited + heap)
*/
```

---

## 28. The Maze II

**Q: Problem Statement (Hinglish)**
Ek ball maze (grid) ke andar hai. Ball 4 directions (up, down, left, right) me roll kar sakti hai, lekin woh tab tak rukegi jab tak wall ya boundary na aa jaye. Tumhe ball ka **shortest distance** nikalna hai start se destination tak. Agar destination tak nahi jaa sakti toh -1 return karo.

**Example**

```
maze = [[0,0,1,0,0],
        [0,0,0,0,0],
        [0,0,0,1,0],
        [1,1,0,1,1],
        [0,0,0,0,0]]
start = [0,4], destination = [4,4]
Output = 12
```

---

**Approach (Hinglish, crisp)**

* Ye normal BFS nahi hai kyunki ball beech me ruk nahi sakti.
* Har move me ball roll karti hai aur ek wall ke pehle rukti hai.
* Use **Dijkstra’s Algorithm**:

  * Har cell ke liye min distance store karo.
  * Priority queue use karo (min-heap).
  * Jab kisi direction me roll karte ho → steps count karo jab tak wall na aaye.
  * Agar newDist < dist[nx][ny], update and push.

---

**Pseudocode**

```
1. dist matrix = INF
2. PQ = {0, start}
3. While PQ not empty:
   a. Pop min dist cell
   b. For each direction → roll until wall
   c. If newDist < dist[nx][ny] → update
4. Return dist[destination] or -1
```

---

**C++ Code (main working function)**

```cpp
#include <bits/stdc++.h>
using namespace std;

// Function: shortest distance in Maze II
int shortestDistance(vector<vector<int>>& maze, vector<int>& start, vector<int>& dest) {
    int m = maze.size(), n = maze[0].size();
    vector<vector<int>> dist(m, vector<int>(n, 1e9));
    dist[start[0]][start[1]] = 0;
    
    priority_queue<vector<int>, vector<vector<int>>, greater<>> pq;
    pq.push({0, start[0], start[1]});
    
    int dirs[4][2] = {{1,0},{-1,0},{0,1},{0,-1}};
    while (!pq.empty()) {
        auto top = pq.top(); pq.pop();
        int d = top[0], x = top[1], y = top[2];
        if (x == dest[0] && y == dest[1]) return d;
        
        for (auto &dir : dirs) {
            int nx = x, ny = y, steps = 0;
            while (nx+dir[0] >= 0 && nx+dir[0] < m && ny+dir[1] >= 0 && ny+dir[1] < n 
                   && maze[nx+dir[0]][ny+dir[1]] == 0) {
                nx += dir[0]; ny += dir[1]; steps++;
            }
            if (d + steps < dist[nx][ny]) {
                dist[nx][ny] = d + steps;
                pq.push({dist[nx][ny], nx, ny});
            }
        }
    }
    return -1;
}

/*
Time Complexity: O(m*n*log(m*n))  (PQ operations)
Space Complexity: O(m*n)  (dist matrix)
*/
```

---

## 29. The Maze III

**Q: Problem Statement (Hinglish)**
Ye Maze II ka extension hai. Ball ko start se destination tak le jana hai, lekin ab tumhe **lexicographically smallest path** bhi return karna hai agar multiple shortest paths exist karein. Directions = "u", "d", "l", "r". Agar destination unreachable hai → "impossible".

**Example**

```
maze = [[0,0,0,0,0],
        [1,1,0,0,1],
        [0,0,0,0,0],
        [0,1,0,0,1],
        [0,0,0,0,0]]
start = [4,3], destination = [0,1]
Output = "lul"
```

---

**Approach (Hinglish, crisp)**

* Again use **Dijkstra** but ab hume 2 cheezein track karni hongi:

  1. Minimum distance
  2. Path string (lexicographically smallest)
* PQ me `{dist, path, x, y}` rakho.
* Jab bhi new cell pe jao, agar shorter distance mile to update karo.
* Agar same distance mile to lexicographically smaller path choose karo.

---

**Pseudocode**

```
1. dist matrix = INF, path matrix = ""
2. PQ = {0, "", start}
3. While PQ not empty:
   a. Pop {d, path, x, y}
   b. If destination reached → return path
   c. For each direction roll
   d. Update if shorter or equal but lex smaller path
4. Return "impossible"
```

---

**C++ Code (main working function)**

```cpp
#include <bits/stdc++.h>
using namespace std;

// Function: lexicographically smallest path in Maze III
string findShortestWay(vector<vector<int>>& maze, vector<int>& ball, vector<int>& hole) {
    int m = maze.size(), n = maze[0].size();
    vector<vector<int>> dist(m, vector<int>(n, 1e9));
    vector<vector<string>> path(m, vector<string>(n, ""));
    
    dist[ball[0]][ball[1]] = 0;
    priority_queue<tuple<int,string,int,int>, vector<tuple<int,string,int,int>>, greater<>> pq;
    pq.push({0, "", ball[0], ball[1]});
    
    vector<pair<int,string>> dirs = {{1,"d"},{-1,"u"},{0,"r"},{0,"l"}};
    
    while (!pq.empty()) {
        auto [d, p, x, y] = pq.top(); pq.pop();
        if (x == hole[0] && y == hole[1]) return p;
        
        for (auto [dx, dir] : dirs) {
            int dy = 0; 
            if (dir == "l") { dx=0; dy=-1; }
            else if (dir == "r") { dx=0; dy=1; }
            
            int nx = x, ny = y, steps = 0;
            while (nx+dx>=0 && nx+dx<m && ny+dy>=0 && ny+dy<n && maze[nx+dx][ny+dy]==0) {
                nx += dx; ny += dy; steps++;
                if (nx == hole[0] && ny == hole[1]) break;
            }
            
            string newPath = p + dir;
            if (d+steps < dist[nx][ny] || (d+steps==dist[nx][ny] && newPath < path[nx][ny])) {
                dist[nx][ny] = d+steps;
                path[nx][ny] = newPath;
                pq.push({dist[nx][ny], newPath, nx, ny});
            }
        }
    }
    return "impossible";
}

/*
Time Complexity: O(m*n*log(m*n)) (Dijkstra with PQ)
Space Complexity: O(m*n) (dist + path matrices)
*/
```

---