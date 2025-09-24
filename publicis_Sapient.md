**Q: What is GUI?**

**A:** GUI ka full form hai **Graphical User Interface**. Yeh ek visual tareeka hai jisse hum computer se interact karte hain. Ismein hum text commands type karne ki jagah **icons, windows, aur menus** par mouse se click karke kaam karte hain. Jaise ki aapka Windows ya Android ka screen, yeh sab GUI ke examples hain. Isne computers ko use karna bahut aasan bana diya hai.

---

**Q: What is Demand Paging in Operating System?**

**A:** Demand Paging ek virtual memory management ki technique hai. Ismein, kisi program ke saare pages (parts) ko ek saath RAM mein load nahi kiya jaata. Sirf usi page ko load karte hain jiski **CPU ko "demand" hoti hai** yaani zaroorat hoti hai. Agar CPU ko aisa page chahiye jo RAM mein nahi hai, toh ek **"page fault"** hota hai, aur OS us page ko hard disk se utha kar RAM mein le aata hai. Isse memory save hoti hai aur program jaldi start ho jaata hai.

---

**Q: What are the different states of a process?**

**A:** Ek process apni life cycle mein in 5 main states se guzarta hai:

* **New:** Jab process create ho raha hota hai.
* **Ready:** Process run hone ke liye taiyaar hai aur CPU milne ka wait kar raha hai.
* **Running:** Process ke instructions CPU par execute ho rahe hain.
* **Waiting (or Blocked):** Process kisi event (jaise I/O operation complete hone) ka wait kar raha hai.
* **Terminated:** Process ka execution poora ho chuka hai.


---

**Q: Explain zombie process?**

**A:** Ek zombie process woh hota hai jo apna kaam **khatam (terminate) kar chuka hai**, lekin process table mein uski entry abhi bhi maujood hai. Aisa isliye hota hai kyunki uske parent process ko child ka exit status (woh aakhir mein kaise band hua) padhna hota hai. Jab tak parent process `wait()` system call ka use karke is status ko padh nahi leta, tab tak child process 'zombie' bankar process table mein rehta hai.

---

**Q: What is starvation and aging in OS?**

**A:**
* **Starvation:** Yeh woh situation hai jab ek low-priority process ko run hone ke liye **CPU kabhi mil hi nahi paata** kyunki usse pehle hamesha high-priority processes aate rehte hain. Bechara process aakhir tak wait hi karta reh jaata hai.
* **Aging:** Aging, starvation ka solution hai. Yeh ek aisi technique hai jismein jo process bahut der se wait kar rahe hote hain, unki **priority time ke saath dheere-dheere badha di jaati hai**. Isse yeh ensure hota hai ki ek na ek din low-priority process ki priority itni high ho jaayegi ki use CPU mil hi jaayega.

---

**Q: What is RAID structure in OS?**

**A:** RAID ka full form hai **Redundant Array of Independent Disks**. Yeh ek technology hai jismein kai saari physical hard disks ko milakar ek single logical unit banaya jaata hai. Iska main maqsad hota hai:
1.  **Data Redundancy (Backup):** Agar ek disk fail ho jaaye, toh data doosri disk se recover ho sake.
2.  **Performance Improvement:** Data ko alag-alag disks par distribute karke read/write speed badhana.

Iske alag-alag levels hote hain jaise RAID 0, RAID 1, RAID 5, etc.


---

**Q: What is IPC?**

**A:** IPC ka matlab hai **Inter-Process Communication**. Yeh OS dwara provide kiya gaya ek mechanism hai jisse **do ya do se zyada processes aapas mein communicate kar sakte hain** aur data share kar sakte hain. Jab kai processes ko milkar koi kaam karna hota hai, tab IPC zaroori hota hai. Iske common tareeke hain Shared Memory aur Message Passing.

---

**Q: What is virtual memory?**

**A:** Virtual memory ek aisi technique hai jisse user ko yeh **illusion (bhram) hota hai ki uske paas bahut saari RAM hai**, jabki actual mein RAM limited hoti hai. OS yeh kaam program ke zaroori hisson ko RAM mein aur baaki hisson ko hard disk par rakh kar karta hai. Iski vajah se hum aise bade programs bhi chala paate hain jo actual RAM ke size se bade hote hain.

---

**Q: What's the difference between multitasking and multiprocessing OS?**

**A:** Dono alag cheezein hain:

* **Multitasking:** Ek **single CPU** par ek se zyada tasks ko itni tezi se switch kiya jaata hai ki user ko lagta hai sab kuch ek saath chal raha hai. Yeh *apparent* simultaneous execution hai.
* **Multiprocessing:** Ek system mein **do ya do se zyada CPUs** hote hain, aur alag-alag tasks sach mein (truly) ek hi samay par alag-alag CPU par chalte hain. Yeh *true* parallel execution hai.

---

**Q: What is Context Switching?**

**A:** Context Switching woh process hai jismein OS, CPU ka control ek process se hatakar doosre process ko deta hai. Aisa karne ke liye, OS pehle **current process ki state (jaise register values, program counter) ko save karta hai** aur phir **doosre process ki saved state ko load karta hai** taaki woh wahin se continue kar sake jahan usne chhoda tha. Yeh multitasking ke liye bahut zaroori hai.

---



**Q: What's the difference between HTTP and HTTPS?**

**A:** Dono hi internet par data transfer karne ke protocol hain, lekin inmein sabse bada fark **security** ka hai.
* **HTTP (Hypertext Transfer Protocol):** Ismein data plain text mein jaata hai, jise koi bhi aasani se padh sakta hai. Yeh **secure nahi hai**.
* **HTTPS (Hypertext Transfer Protocol Secure):** Yeh HTTP ka secure version hai. Ismein data **encrypt** hokar jaata hai (SSL/TLS certificate ka use karke). Isse aapka data jaise passwords ya credit card details safe rehta hai. Website ke URL mein `https://` aur browser mein ek lock (🔒) ka icon iski pehchan hai.

---

**Q: What is the network topology?**

**A:** Network Topology ka matlab hai ki ek network mein computers aur doosre devices **kaise jude hue hain**. Yeh network ka physical ya logical **layout (design)** hota hai. Kuch common topologies hain: **Bus, Star, Ring, aur Mesh**. Star topology mein saare devices ek central hub se judte hain, jabki Bus mein sab ek hi cable se judte hain.

---

**Q: What is an IPv4 address?**

**A:** IPv4 ka full form **Internet Protocol version 4** hai. Yeh ek unique numerical address hai jo network par har device (jaise computer, phone) ko pehchanne ke liye use hota hai. Yeh **32-bit** ka address hota hai jise chaar numbers ke set mein likha jaata hai aur unke beech mein dot (.) hota hai (e.g., `192.168.1.1`). Yeh internet par aapke device ka address hai.

---

**Q: What is OSI Model in Computer Networking?**

**A:** OSI (Open Systems Interconnection) Model ek **conceptual framework** hai jo network communication ko **7 layers** mein divide karta hai. Yeh samjhata hai ki data ek computer se doosre tak kaise travel karta hai. Har layer ka ek specific kaam hota hai. Yeh 7 layers hain (neeche se upar): **Physical, Data Link, Network, Transport, Session, Presentation, aur Application**.

---

**Q: What are the various types of nodes?**

**A:** Network mein, **node** koi bhi device hota hai jo data bhej, receive, ya forward kar sakta hai. Basically, yeh ek connection point hai. Iske kuch common types hain:
* **End Nodes:** Jaise aapka computer, printer, ya smartphone, jahan data journey shuru ya khatam karta hai.
* **Intermediary Nodes:** Jaise **Routers, Switches, aur Hubs**, jo network traffic ko direct aur manage karte hain.

---

**Q: What's the difference between Bluetooth and wifi?**

**A:** Dono wireless technologies hain, par unka use alag hai:
* **Wi-Fi:** Iska use **high-speed wireless internet access** ke liye hota hai aur yeh ek bade area (ghar, office) ko cover karta hai. Ismein devices ek router se connect hote hain.
* **Bluetooth:** Iska use **short-range** mein do devices ko aapas mein jodne ke liye hota hai (jaise phone ko headphones se). Iski range aur speed Wi-Fi se kam hoti hai aur yeh power bhi kam consume karta hai.

---

**Q: What is Bridge in Computer Network?**

**A:** Bridge ek network device hai jo OSI model ke **Layer 2 (Data Link Layer)** par kaam karta hai. Iska main kaam **do alag-alag network segments (LANs) ko jodna** hai. Yeh MAC addresses ke basis par traffic ko filter karta hai, jisse network mein faltu ka traffic kam hota hai aur performance behtar hoti hai.

---

**Q: What is VPN?**

**A:** VPN ka full form hai **Virtual Private Network**. Yeh public internet par ek **secure aur encrypted connection (tunnel)** banata hai. VPN aapke **IP address ko chhipa deta hai** aur aapke data ko encrypt kar deta hai, jisse aapki online activity private aur safe rehti hai. Isse security aur privacy badhti hai.

---

**Q: What is the firewall?**

**A:** Firewall ek **network security system** hai jo ek digital diwaar ki tarah kaam karta hai. Yeh aapke private network aur internet ke beech mein rehta hai aur aane-jaane waale network traffic ko monitor karta hai. Pehle se set kiye gaye security rules ke hisaab se yeh decide karta hai ki **kis traffic ko allow karna hai aur kisko block karna hai**, taaki unauthorized access ko roka ja sake.

---

**Q: What is a subnet?**

**A:** Subnet ka matlab hai **"network ke andar ek chhota network"**. Ek bade IP network ko chote-chote, manageable parts mein divide karne ke process ko **subnetting** kehte hain. Aisa karne se network ki performance behtar hoti hai, security badhti hai aur network ko manage karna aasan ho jaata hai.

----


**Q: What are Constraints in SQL?**

**A:** SQL Constraints **rules** hote hain jo hum table ke columns par lagate hain. Inka kaam data ki **accuracy aur integrity** ko maintain karna hai, yaani table mein galat data enter hone se rokna.
Kuch common constraints hain:
* **NOT NULL:** Ensure karta hai ki column mein koi `NULL` value na ho.
* **UNIQUE:** Ensure karta hai ki column ki saari values ek doosre se alag hon.
* **PRIMARY KEY:** Har row ko uniquely identify karta hai. Yeh `NOT NULL` aur `UNIQUE` ka combination hota hai.
* **FOREIGN KEY:** Do tables ko aapas mein link karta hai.
* **CHECK:** Ensure karta hai ki column ki value ek specific condition ko poora kare.
* **DEFAULT:** Agar user koi value na de, toh yeh ek default value set kar deta hai.

---

**Q: What's the difference between DDL, DML, and DCL in SQL?**

**A:** SQL commands ko unke kaam ke basis par 3 groups mein baanta gaya hai:

* **DDL (Data Definition Language):** Yeh commands database ke **structure (schema)** ko define karne ke kaam aati hain.
    * **Examples:** `CREATE` (table banana), `ALTER` (change karna), `DROP` (delete karna).
* **DML (Data Manipulation Language):** Yeh commands table ke andar ke **data ko manage** karne ke kaam aati hain.
    * **Examples:** `SELECT` (data dekhna), `INSERT` (data daalna), `UPDATE`, `DELETE`.
* **DCL (Data Control Language):** Yeh commands user **permissions aur access control** manage karne ke kaam aati hain.
    * **Examples:** `GRANT` (permission dena), `REVOKE` (permission wapas lena).

---

**Q: What is Normalization?**

**A:** Normalization, database design ki ek process hai jismein hum tables ko is tarah se organize karte hain ki **data redundancy (duplication) kam se kam ho** aur **data integrity (correctness aur consistency) bani rahe**. Ismein ek badi table ko todkar choti-choti, well-structured tables mein baanta jaata hai aur unke beech relationships banaye jaate hain.

---

**Q: What’s the Difference Between RDBMS and DBMS?**

**A:**
* **DBMS (Database Management System):** Yeh ek software hai jo data ko store, manage, aur retrieve karta hai. Data kisi bhi format mein ho sakta hai, jaise file system.
* **RDBMS (Relational Database Management System):** Yeh ek special type ka DBMS hai jismein data hamesha **tables (rows aur columns)** ke form mein store hota hai. Iski sabse badi khaasiyat yeh hai ki ismein alag-alag tables ke beech mein **relationships** define kiye jaa sakte hain.

**Simple bhasha mein:** Har RDBMS ek DBMS hai, lekin har DBMS ek RDBMS nahi hota. MySQL, Oracle, SQL Server sab RDBMS ke examples hain.

---

**Q: What is Join?**

**A:** SQL `JOIN` clause ka use **do ya do se zyada tables se rows ko unke related column ke basis par combine karne** ke liye kiya jaata hai. Jab aapko aisi information chahiye jo alag-alag tables mein store hai, tab aap `JOIN` ka use karte hain. Common types hain: **`INNER JOIN`**, **`LEFT JOIN`**, **`RIGHT JOIN`**, aur **`FULL OUTER JOIN`**.

---

**Q: What is a transaction?**

**A:** Ek transaction, operations ka ek group hai jo ek **single logical unit of work** ki tarah kaam karta hai. Ek transaction mein saare operations ya toh **safalta se poore hote hain (Commit)** ya agar koi ek bhi fail hota hai toh **saare ke saare undo ho jaate hain (Rollback)**. Aisa nahi ho sakta ki aadha kaam ho aur aadha na ho.
**Example:** Bank transfer, jismein ek account se paise debit hona aur doosre mein credit hona ek poora transaction hai.

---

**Q: Explain the ACID properties of a DBMS?**

**A:** ACID properties transactions ki reliability aur consistency ko ensure karti hain.
* **A - Atomicity:** Iska matlab hai "all or nothing". Ya toh transaction ke saare steps poore honge ya ek bhi nahi.
* **C - Consistency:** Transaction ke poora hone ke baad database ek valid state mein rehta hai, koi galat data save nahi hota.
* **I - Isolation:** Agar ek saath kai transactions chal rahe hain, toh woh ek doosre ke kaam mein interfere nahi karte. Har transaction ko lagta hai ki woh akela hi chal raha hai.
* **D - Durability:** Agar ek transaction safalta se commit ho gaya hai, toh woh change permanent hota hai, chahe system crash ho ya power fail ho jaaye.

---

**Q: What is OLTP?**

**A:** OLTP ka full form hai **Online Transaction Processing**. Yeh aise systems hote hain jahan par bahut saare, **chote-chote aur fast transactions** real-time mein hote hain. Iska main focus data ko jaldi se insert, update, aur delete karne par hota hai.
**Examples:** ATM se paise nikalna, online shopping karna, ya railway ticket book karna.

---

**Q: What are the various forms of Normalization?**

**A:** Normalization ke kai levels hote hain, jinhe Normal Forms (NF) kehte hain. Sabse zaroori aur common hain:
* **First Normal Form (1NF):** Har table cell mein sirf ek single (atomic) value honi chahiye.
* **Second Normal Form (2NF):** Table 1NF mein honi chahiye aur saare non-key columns, poore primary key par fully dependent hone chahiye.
* **Third Normal Form (3NF):** Table 2NF mein honi chahiye aur usmein koi bhi transitive dependency nahi honi chahiye (matlab koi non-key column kisi doosre non-key column par depend na kare).
* **BCNF (Boyce-Codd Normal Form):** Yeh 3NF ka ek stricter version hai.

---

**Q: What is a View?**

**A:** Ek View ek **virtual table** hoti hai, jiska apna koi physical data nahi hota. Yeh ek stored SQL query ke result set par based hoti hai. View bilkul ek real table ki tarah dikhti hai (rows aur columns ke saath), lekin yeh apna data ek ya ek se zyada base tables se leti hai. Iska use complex queries ko aasan banane aur data par security lagane ke liye kiya jaata hai.

---


### **1. Reverse The Array**

**Q: Problem statement, example, approach aur C++ code do array ko reverse karne ke liye.**

**A:**

  * **Problem Statement:** Ek array diya gaya hai, aapko uske elements ko reverse order mein karna hai.

  * **Example:**

      * **Input:** `arr = [10, 20, 30, 40, 50]`
      * **Output:** `[50, 40, 30, 20, 10]`

  * **Approach:** Hum **Two-Pointer** approach ka use karenge. Ek pointer (`start`) array ke shuru mein aur doosra pointer (`end`) array ke aakhir mein rakhenge. Jab tak `start` pointer `end` se chhota hai, hum `arr[start]` aur `arr[end]` ko swap karte rahenge aur pointers ko ek doosre ki taraf move karte rahenge.

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    void reverseArray(vector<int>& arr) {
        // TC: O(n), SC: O(1)
        int start = 0;
        int end = arr.size() - 1;
        while (start < end) {
            swap(arr[start], arr[end]);
            start++;
            end--;
        }
    }
    ```

-----

### **2. Triplet Sum in Array**

**Q: Problem statement, example, approach aur C++ code do Triplet Sum ke liye.**

**A:**

  * **Problem Statement:** Ek array aur ek target sum `X` diya hai. Aapko batana hai ki kya array mein koi 3 elements (triplet) hain jinka sum `X` ke barabar hai.

  * **Example:**

      * **Input:** `arr = [1, 4, 45, 6, 10, 8]`, `X = 22`
      * **Output:** `true` (Kyunki 4 + 8 + 10 = 22)

  * **Approach:** Pehle array ko sort karenge. Phir, ek loop chalaenge aur har element `arr[i]` ko fix karenge. Baaki bache hue array mein, Two-Pointer approach use karke `X - arr[i]` sum ko dhoondhenge.

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    bool findTriplet(vector<int>& arr, int x) {
        // TC: O(n^2), SC: O(1)
        sort(arr.begin(), arr.end());
        int n = arr.size();
        for (int i = 0; i < n - 2; i++) {
            int left = i + 1;
            int right = n - 1;
            while (left < right) {
                if (arr[i] + arr[left] + arr[right] == x) {
                    return true;
                } else if (arr[i] + arr[left] + arr[right] < x) {
                    left++;
                } else {
                    right--;
                }
            }
        }
        return false;
    }
    ```

-----

### **3. Kadane’s Algorithm**

**Q: Kadane’s Algorithm ka problem statement, example, approach aur C++ code do.**

**A:**

  * **Problem Statement:** Ek array diya hai. Aapko us **contiguous subarray** ka sum nikalna hai jiska sum sabse zyada (maximum) ho.

  * **Example:**

      * **Input:** `arr = [-2, 1, -3, 4, -1, 2, 1, -5, 4]`
      * **Output:** `6` (Subarray hai `[4, -1, 2, 1]`)

  * **Approach:** Hum do variables lenge: `current_max` aur `global_max`. Array ko traverse karte waqt, har element ko `current_max` mein add karenge. Agar `current_max` kabhi negative ho jaata hai, to usse `0` reset kar denge. Har step par, `global_max` ko `current_max` ke saath compare karke update karte rahenge.

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    int maxSubarraySum(vector<int>& arr) {
        // TC: O(n), SC: O(1)
        int current_max = 0;
        int global_max = INT_MIN;
        for (int i = 0; i < arr.size(); i++) {
            current_max += arr[i];
            if (global_max < current_max) {
                global_max = current_max;
            }
            if (current_max < 0) {
                current_max = 0;
            }
        }
        return global_max;
    }
    ```

-----

### **4. Trapping Rain Water**

**Q: Trapping Rain Water ka problem statement, example, approach aur C++ code do.**

**A:**

  * **Problem Statement:** Ek non-negative integers ka array diya hai jo elevation map (buildings ki height) represent karta hai. Aapko calculate karna hai ki baarish ke baad in buildings ke beech kitna paani jama (trap) ho sakta hai.

  * **Example:**

      * **Input:** `height = [0, 1, 0, 2, 1, 0, 1, 3, 2, 1, 2, 1]`
      * **Output:** `6`

  * **Approach:** Har building `height[i]` ke liye, hum uske left mein sabse unchi building (`left_max`) aur right mein sabse unchi building (`right_max`) nikalenge. `height[i]` par `min(left_max, right_max) - height[i]` paani jama hoga. Isko optimize karne ke liye, hum do arrays `left[]` aur `right[]` pehle se hi bana lenge jismein har index ke liye max left aur max right store hoga.

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    int trap(vector<int>& height) {
        // TC: O(n), SC: O(n)
        int n = height.size();
        if (n == 0) return 0;
        vector<int> left(n), right(n);
        left[0] = height[0];
        for (int i = 1; i < n; i++) {
            left[i] = max(left[i - 1], height[i]);
        }
        right[n - 1] = height[n - 1];
        for (int i = n - 2; i >= 0; i--) {
            right[i] = max(right[i + 1], height[i]);
        }
        int water = 0;
        for (int i = 0; i < n; i++) {
            water += min(left[i], right[i]) - height[i];
        }
        return water;
    }
    ```

-----

### **5. Delete middle node of a Linked List**

**Q: Linked list ke middle node ko delete karne ka problem statement, example, approach aur C++ code do.**

**A:**

  * **Problem Statement:** Ek singly linked list di hai. Aapko uske middle node ko delete karna hai. Agar list ki length even hai to do middle nodes honge, us case mein second middle node ko delete karna hai.

  * **Example:**

      * **Input:** `1 -> 2 -> 3 -> 4 -> 5`
      * **Output:** `1 -> 2 -> 4 -> 5` (Node 3 delete ho gaya)

  * **Approach:** Hum **Slow aur Fast Pointer** approach ka use karenge. Fast pointer do steps chalta hai aur slow pointer ek step. Jab fast pointer end tak pahunchega, slow pointer middle node par hoga. Middle node ko delete karne ke liye hum slow pointer se ek node pehle (`prev`) ka track rakhenge aur `prev->next = slow->next` kar denge.

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    struct ListNode {
        int val;
        ListNode *next;
        ListNode(int x) : val(x), next(nullptr) {}
    };

    ListNode* deleteMiddle(ListNode* head) {
        // TC: O(n), SC: O(1)
        if (head == nullptr || head->next == nullptr) return nullptr;

        ListNode *slow = head;
        ListNode *fast = head;
        ListNode *prev = nullptr;

        while (fast != nullptr && fast->next != nullptr) {
            prev = slow;
            slow = slow->next;
            fast = fast->next->next;
        }
        
        prev->next = slow->next;
        delete slow;
        return head;
    }
    ```

-----

### **6. Minimum Subarray With Required Sum**

**Q: Minimum Subarray With Required Sum ka problem, example, approach aur C++ code do.**

**A:**

  * **Problem Statement:** Ek positive integers ka array aur ek target sum `S` diya hai. Aapko us sabse chote **contiguous subarray** ki length batani hai jiska sum `S` se bada ya barabar (`>= S`) ho.

  * **Example:**

      * **Input:** `arr = [2, 3, 1, 2, 4, 3]`, `S = 7`
      * **Output:** `2` (Subarray hai `[4, 3]`)

  * **Approach:** Hum **Sliding Window** technique ka use karenge. Ek `start` aur ek `end` pointer lenge. `end` ko aage badha kar `current_sum` mein elements add karte jayenge. Jaise hi `current_sum >= S` hoga, hum window ki length ko check karenge aur `start` pointer ko aage badha kar window ko chota karenge.

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    int minSubArrayLen(int s, vector<int>& nums) {
        // TC: O(n), SC: O(1)
        int n = nums.size();
        int min_len = INT_MAX;
        int start = 0;
        int current_sum = 0;
        for (int end = 0; end < n; end++) {
            current_sum += nums[end];
            while (current_sum >= s) {
                min_len = min(min_len, end - start + 1);
                current_sum -= nums[start];
                start++;
            }
        }
        return (min_len == INT_MAX) ? 0 : min_len;
    }
    ```

-----

### **7. Cycle Detection In Undirected Graph**

**Q: Undirected graph mein cycle detect karne ka problem, example, approach aur C++ code do.**

**A:**

  * **Problem Statement:** Ek undirected graph diya hai. Pata lagana hai ki usmein cycle hai ya nahi.

  * **Example:**

      * **Input:** Graph with 3 nodes and edges (0,1), (1,2), (2,0).
      * **Output:** `true` (Kyunki 0-1-2-0 ek cycle hai).

  * **Approach:** Hum **DFS (Depth First Search)** ka use karenge. Hum graph ko traverse karenge. Agar traversal ke dauran hum kisi aise node par pahunchte hain jo pehle se visited hai aur woh hamare current node ka parent nahi hai, to iska matlab graph mein cycle hai.

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    bool isCycleUtil(int u, int parent, vector<int> adj[], vector<bool>& visited) {
        visited[u] = true;
        for (int v : adj[u]) {
            if (!visited[v]) {
                if (isCycleUtil(v, u, adj, visited)) return true;
            } else if (v != parent) {
                return true;
            }
        }
        return false;
    }

    bool isCycle(int V, vector<int> adj[]) {
        // TC: O(V+E), SC: O(V)
        vector<bool> visited(V, false);
        for (int i = 0; i < V; i++) {
            if (!visited[i]) {
                if (isCycleUtil(i, -1, adj, visited)) return true;
            }
        }
        return false;
    }
    ```

-----

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

### **9. Parenthesis Checker**

**Q: Parenthesis Checker ka problem, example, approach aur C++ code do.**

**A:**

  * **Problem Statement:** Ek string di hai jismein `(`, `)`, `{`, `}`, `[`, `]` brackets hain. Check karna hai ki yeh brackets balanced (well-formed) hain ya nahi.

  * **Example:**

      * **Input:** `"{([])}"` -\> **Output:** `true`
      * **Input:** `"([)]"` -\> **Output:** `false`

  * **Approach:** Hum **Stack** ka use karenge. String ko traverse karenge.

    1.  Agar opening bracket (`(`, `{`, `[`) milta hai, to use stack mein push karo.
    2.  Agar closing bracket milta hai, to check karo ki stack ka top element matching opening bracket hai ya nahi. Agar hai to pop karo, nahi to `false` return karo.
    3.  Loop ke baad, agar stack empty hai to `true`, warna `false`.

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    bool isValid(string s) {
        // TC: O(n), SC: O(n)
        stack<char> st;
        for (char c : s) {
            if (c == '(' || c == '{' || c == '[') {
                st.push(c);
            } else {
                if (st.empty()) return false;
                if (c == ')' && st.top() != '(') return false;
                if (c == '}' && st.top() != '{') return false;
                if (c == ']' && st.top() != '[') return false;
                st.pop();
            }
        }
        return st.empty();
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

### **12. Palindrome Pairs**

**Q: Palindrome Pairs ka problem, example, approach aur C++ code do.**

**A:**

  * **Problem Statement:** Unique words ki ek list di gayi hai. Aapko saare alag-alag indices `(i, j)` ke pairs find karne hain, jisse `words[i] + words[j]` ek palindrome ban jaaye.

  * **Example:**

      * **Input:** `["bat", "tab", "cat"]`
      * **Output:** `[[0, 1], [1, 0]]` (kyunki "battab" aur "tabbat" palindromes hain)

  * **Approach:** Hum **Hash Map** ka use karenge. Pehle saare words aur unke index ko map mein store karenge. Phir har word ke liye, uske saare possible prefixes aur suffixes check karenge. Agar prefix palindrome hai, to hum bache hue suffix ka reverse map mein dhoondhenge. Agar suffix palindrome hai, to hum bache hue prefix ka reverse map mein dhoondhenge.

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    bool isPalindrome(string s) {
        int left = 0, right = s.length() - 1;
        while (left < right) {
            if (s[left++] != s[right--]) return false;
        }
        return true;
    }

    vector<vector<int>> palindromePairs(vector<string>& words) {
        // TC: O(n * k^2), SC: O(n*k) where n=words.size, k=avg word length
        unordered_map<string, int> m;
        for (int i = 0; i < words.size(); i++) m[words[i]] = i;
        vector<vector<int>> ans;

        for (int i = 0; i < words.size(); i++) {
            for (int j = 0; j <= words[i].size(); j++) {
                string pre = words[i].substr(0, j);
                string suf = words[i].substr(j);

                if (isPalindrome(pre)) {
                    string rev_suf = suf;
                    reverse(rev_suf.begin(), rev_suf.end());
                    if (m.count(rev_suf) && m[rev_suf] != i) {
                        ans.push_back({m[rev_suf], i});
                    }
                }
                if (suf.length() != 0 && isPalindrome(suf)) {
                    string rev_pre = pre;
                    reverse(rev_pre.begin(), rev_pre.end());
                    if (m.count(rev_pre) && m[rev_pre] != i) {
                        ans.push_back({i, m[rev_pre]});
                    }
                }
            }
        }
        return ans;
    }
    ```

-----

### **13. Find the Number Occurring Odd Number of Times**

**Q: Odd number of times occur hone waale number ko find karne ka problem, example, approach aur C++ code do.**

**A:**

  * **Problem Statement:** Ek array diya hai jismein saare numbers even number of times aate hain, siwaye ek number ke jo odd number of times aata hai. Aapko woh number find karna hai.

  * **Example:**

      * **Input:** `[4, 2, 4, 5, 2, 3, 3]`
      * **Output:** `5`

  * **Approach:** Iska sabse optimal solution **XOR operator** ka use karna hai. `a ^ a = 0` aur `a ^ 0 = a` hota hai. Jab hum saare array elements ka XOR karenge, to jo numbers even times aaye hain woh aapas mein cancel hokar 0 ban jayenge, aur sirf odd times aane waala number bachega.

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    int getOddOccurrence(vector<int>& arr) {
        // TC: O(n), SC: O(1)
        int result = 0;
        for (int num : arr) {
            result = result ^ num;
        }
        return result;
    }
    ```

-----

### **14. Search In A 2D Matrix**

**Q: 2D Matrix mein search karne ka problem, example, approach aur C++ code do.**

**A:**

  * **Problem Statement:** Ek `m x n` sorted matrix di hai jismein har row left-to-right sorted hai aur har agli row ka pehla element pichli row ke last element se bada hai. Target value ko search karna hai.

  * **Example:**

      * **Input:** `matrix = [[1,3,5],[10,11,16],[23,30,34]]`, `target = 11`
      * **Output:** `true`

  * **Approach:** Poore matrix ko ek single sorted 1D array ki tarah treat karke hum **Binary Search** laga sakte hain. `mid` index se row aur column `row = mid / cols` aur `col = mid % cols` formula se nikal sakte hain.

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        // TC: O(log(m*n)), SC: O(1)
        if (matrix.empty()) return false;
        int rows = matrix.size();
        int cols = matrix[0].size();
        int low = 0;
        int high = (rows * cols) - 1;

        while (low <= high) {
            int mid = low + (high - low) / 2;
            int mid_val = matrix[mid / cols][mid % cols];
            if (mid_val == target) {
                return true;
            } else if (mid_val < target) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        return false;
    }
    ```

-----

### **15. Cycle Detection in a Singly Linked List**

**Q: Singly linked list mein cycle detect karne ka problem, example, approach aur C++ code do.**

**A:**

  * **Problem Statement:** Ek linked list di hai. Pata lagana hai ki usmein cycle (loop) hai ya nahi.

  * **Example:** Ek list jismein last node `NULL` ki jagah list ke kisi pichle node ko point kar raha ho.

  * **Approach:** Hum **Floyd's Cycle-Finding Algorithm** (jise **Slow and Fast Pointer** bhi kehte hain) ka use karenge. Ek `slow` pointer ek step aur ek `fast` pointer do step aage badhega. Agar list mein cycle hoga, to `fast` pointer ghoom kar `slow` pointer se zaroor milega.

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    struct ListNode {
        int val;
        ListNode *next;
        ListNode(int x) : val(x), next(nullptr) {}
    };

    bool hasCycle(ListNode *head) {
        // TC: O(n), SC: O(1)
        if (head == nullptr || head->next == nullptr) return false;
        
        ListNode *slow = head;
        ListNode *fast = head;
        
        while (fast != nullptr && fast->next != nullptr) {
            slow = slow->next;
            fast = fast->next->next;
            if (slow == fast) {
                return true;
            }
        }
        return false;
    }
    ```

-----

### **16. Ninja island (Number of Islands)**

**Q: Number of Islands ka problem, example, approach aur C++ code do.**

**A:**

  * **Problem Statement:** Ek 2D grid di gayi hai jismein '1' (land) aur '0' (water) hain. Aapko total islands ka count batana hai. Island horizontally ya vertically connected '1's se banta hai.

  * **Example:**

      * **Input:** `[[ '1', '1', '0' ], [ '1', '1', '0' ], [ '0', '0', '1' ]]`
      * **Output:** `2`

  * **Approach:** Grid par traverse karenge. Jab bhi '1' milega, hum island count ko `+1` karenge aur uss cell se **DFS (Depth First Search)** start karke uss island ke saare connected '1's ko '0' (ya visited) mark kar denge, taaki woh dobara count na hon.

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    void dfs(int r, int c, vector<vector<char>>& grid) {
        if (r < 0 || c < 0 || r >= grid.size() || c >= grid[0].size() || grid[r][c] == '0') {
            return;
        }
        grid[r][c] = '0'; // Mark as visited
        dfs(r + 1, c, grid);
        dfs(r - 1, c, grid);
        dfs(r, c + 1, grid);
        dfs(r, c - 1, grid);
    }

    int numIslands(vector<vector<char>>& grid) {
        // TC: O(m*n), SC: O(m*n) for recursion stack
        if (grid.empty()) return 0;
        int count = 0;
        for (int i = 0; i < grid.size(); i++) {
            for (int j = 0; j < grid[0].size(); j++) {
                if (grid[i][j] == '1') {
                    count++;
                    dfs(i, j, grid);
                }
            }
        }
        return count;
    }
    ```

-----

### **17. Print the Pattern**

**Q: Ek common number pattern print karne ka problem, approach aur C++ code do.**

**A:**

  * **Problem Statement:** Ek integer `N` ke liye, `N` rows ka right-angled triangle pattern print karo.

  * **Example:** `N = 4`

    ```
    1
    1 2
    1 2 3
    1 2 3 4
    ```

  * **Approach:** Hum **nested loops** ka use karenge. Bahar wala loop rows ko control karega (1 se `N` tak). Andar wala loop har row mein print hone wale numbers ko control karega (1 se current row number tak).

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    void printPattern(int N) {
        // TC: O(N^2), SC: O(1)
        for (int i = 1; i <= N; i++) {
            for (int j = 1; j <= i; j++) {
                cout << j << " ";
            }
            cout << endl;
        }
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

### **19. Reverse Linked List**

**Q: Linked List ko reverse karne ka problem, example, approach aur C++ code do.**

**A:**

  * **Problem Statement:** Ek singly linked list di hai, use reverse karna hai.

  * **Example:**

      * **Input:** `1 -> 2 -> 3 -> NULL`
      * **Output:** `3 -> 2 -> 1 -> NULL`

  * **Approach:** Hum **iterative method** use karenge jismein teen pointers (`prev`, `current`, `next_node`) honge. Hum list ko traverse karte hue har node ka `next` pointer uske pichle node (`prev`) ki taraf point karwa denge.

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

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
            next_node = current->next; // store next node
            current->next = prev;     // reverse the link
            prev = current;           // move prev one step forward
            current = next_node;      // move current one step forward
        }
        head = prev;
        return head;
    }
    ```

-----

### **20. Kth Smallest Element**

**Q: Array mein Kth Smallest Element find karne ka problem, example, approach aur C++ code do.**

**A:**

  * **Problem Statement:** Ek array aur ek integer `k` diya hai. Aapko us array ka `k`-th sabse chota element find karna hai.

  * **Example:**

      * **Input:** `arr = [7, 10, 4, 3, 20, 15]`, `k = 3`
      * **Output:** `7` (3rd smallest element)

  * **Approach:** Optimal solution ke liye hum **Max-Heap** (C++ mein `priority_queue`) ka use karenge. Hum array ke pehle `k` elements ko heap mein daalenge. Phir, baaki elements ke liye, agar koi element heap ke top (jo ki ab tak ka sabse bada element hai) se chota hai, to hum top ko hata kar naye element ko daal denge. Aakhir mein, heap ka top hi hamara answer hoga.

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    int findKthSmallest(vector<int>& arr, int k) {
        // TC: O(n log k), SC: O(k)
        priority_queue<int> maxHeap; // Max-heap
        for (int i = 0; i < arr.size(); i++) {
            maxHeap.push(arr[i]);
            if (maxHeap.size() > k) {
                maxHeap.pop();
            }
        }
        return maxHeap.top();
    }
    ```

---


### **21 Reverse Words in a String**

**Q: Ek string mein words ko reverse karne ka problem, example, approach aur C++ code do**

**A:**

  * **Problem Statement:** Ek string di gayi hai, aapko uske words ko reverse order mein karna hai Extra spaces ko handle karna hai

  * **Example:**

      * **Input:** `"the sky is blue"`
      * **Output:** `"blue is sky the"`

  * **Approach:** Hum **Two-pass** approach ka use kar sakte hain
    1 Pehle poori string ko reverse kar do (`"eulb si yks eht"`)
    2 Phir, string ko traverse karo aur har word ko individually reverse kar do (`"blue is sky the"`)

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    string reverseWords(string s) {
        // TC: O(n), SC: O(1) if in-place modification is allowed
        reverse(s.begin(), s.end());
        int start = 0, end = 0, i = 0;
        int n = s.length();
        while (i < n) {
            while (i < n && s[i] == ' ') i++;
            if (i == n) break; 
            start = end;
            while (i < n && s[i] != ' ') {
                s[end++] = s[i++];
            }
            reverse(s.begin() + start, s.begin() + end);
            s[end++] = ' ';
        }
        if (end > 0) s.resize(end - 1);
        else s.resize(0);
        return s;
    }
    ```

-----

### **22 Stack using queue**

**Q: Queues ka use karke Stack implement karne ka approach aur C++ code do**

**A:**

  * **Problem Statement:** Aapko sirf do queues ka use karke ek LIFO (Last-In-First-Out) Stack implement karna hai

  * **Approach (Push operation ko costly banakar):**
    1 **Push(x):** Naye element `x` ko `q2` mein daalo Phir `q1` ke saare elements ko `q2` mein move karo Aakhir mein `q1` aur `q2` ko swap kar do
    2 **Pop():** `q1` se seedha element nikaal do
    3 **Top():** `q1` ka front element return kar do

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    class MyStack {
        // TC: Push O(n), Pop O(1), Top O(1), SC: O(n)
        queue<int> q1, q2;
    public:
        void push(int x) {
            q2.push(x);
            while (!q1.empty()) {
                q2.push(q1.front());
                q1.pop();
            }
            swap(q1, q2);
        }
        int pop() {
            int val = q1.front();
            q1.pop();
            return val;
        }
        int top() {
            return q1.front();
        }
        bool empty() {
            return q1.empty();
        }
    };
    ```

-----

### **23 Maximum Sum Rectangle**

**Q: 2D Matrix mein maximum sum waale rectangle ko find karne ka problem, approach, aur code do**

**A:**

  * **Problem Statement:** Ek 2D matrix di gayi hai Aapko us submatrix ka sum nikalna hai jiska sum sabse zyada ho

  * **Approach:** Hum **Kadane's Algorithm** ko 2D ke liye extend karenge
    1 Do columns, `left` aur `right`, ko fix karenge
    2 In fixed columns ke liye, har row ke elements ka sum karke ek temporary 1D array banayenge
    3 Is 1D array par Kadane's algorithm lagakar maximum sum subarray nikalenge
    4 Yeh process saare possible `left` aur `right` column pairs ke liye repeat karenge aur maximum sum ko track karenge

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    int kadane(vector<int>& arr) {
        int max_so_far = INT_MIN, current_max = 0;
        for (int x : arr) {
            current_max += x;
            if (max_so_far < current_max) max_so_far = current_max;
            if (current_max < 0) current_max = 0;
        }
        return max_so_far;
    }

    int maxSumRectangle(vector<vector<int>>& mat) {
        // TC: O(cols*cols*rows), SC: O(rows)
        int rows = mat.size(), cols = mat[0].size();
        int max_sum = INT_MIN;
        for (int left = 0; left < cols; left++) {
            vector<int> temp(rows, 0);
            for (int right = left; right < cols; right++) {
                for (int i = 0; i < rows; i++) {
                    temp[i] += mat[i][right];
                }
                max_sum = max(max_sum, kadane(temp));
            }
        }
        return max_sum;
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

### **25 Find Duplicates In Array**

**Q: Array mein duplicates find karne ka problem, approach, aur code do (elements 0 se n-1 hain)**

**A:**

  * **Problem Statement:** Ek `n` size ka array diya hai jismein `0` se `n-1` tak ke numbers hain Aapko saare duplicate elements find karne hain

  * **Approach:** Hum ek smart **in-place** technique use karenge
    1 Array ko traverse karo
    2 Har element `arr[i]` ke liye, hum index `arr[i] % n` par jayenge aur wahan `n` add kar denge (`arr[arr[i] % n] += n`)
    3 Dobara traverse karo, agar kisi index `i` par `arr[i] / n > 1` hai, to `i` ek duplicate element hai

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    vector<int> findDuplicates(vector<int>& arr) {
        // TC: O(n), SC: O(1) (excluding answer space)
        int n = arr.size();
        vector<int> duplicates;
        for (int i = 0; i < n; i++) {
            arr[arr[i] % n] = arr[arr[i] % n] + n;
        }
        for (int i = 0; i < n; i++) {
            if (arr[i] / n > 1) {
                duplicates.push_back(i);
            }
        }
        return duplicates;
    }
    ```

-----

### **26 Merge Sort**

**Q: Merge Sort algorithm ka approach aur C++ code do**

**A:**

  * **Problem Statement:** Aapko Merge Sort algorithm implement karna hai

  * **Approach:** Yeh **Divide and Conquer** par based hai
    1 **Divide:** Array ko recursively do half mein tab tak todo jab tak har part mein ek hi element na bach jaye
    2 **Conquer:** Phir, in chhote sorted parts ko aapas mein merge karke bade sorted parts banao, jab tak poora array sort na ho jaye

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    void merge(vector<int>& arr, int left, int mid, int right) {
        int n1 = mid - left + 1;
        int n2 = right - mid;
        vector<int> L(n1), R(n2);
        for(int i=0; i<n1; i++) L[i] = arr[left + i];
        for(int j=0; j<n2; j++) R[j] = arr[mid + 1 + j];
        
        int i = 0, j = 0, k = left;
        while(i < n1 && j < n2) {
            if(L[i] <= R[j]) arr[k++] = L[i++];
            else arr[k++] = R[j++];
        }
        while(i < n1) arr[k++] = L[i++];
        while(j < n2) arr[k++] = R[j++];
    }

    void mergeSort(vector<int>& arr, int left, int right) {
        // TC: O(n log n), SC: O(n)
        if (left < right) {
            int mid = left + (right - left) / 2;
            mergeSort(arr, left, mid);
            mergeSort(arr, mid + 1, right);
            merge(arr, left, mid, right);
        }
    }
    ```

-----

### **27 Search Elements in an Array**

**Q: Array mein element search karne ka problem, approach, aur code do**

**A:**

  * **Problem Statement:** Ek array aur ek target element diya hai Agar element array mein hai to uska index return karo, warna -1

  * **Approach:** Hum **Linear Search** ka use karenge
    1 Array ke shuru se aakhir tak ek-ek karke har element ko check karenge
    2 Agar element target ke barabar milta hai, to uska index return kar denge
    3 Agar poora array check karne ke baad bhi element nahi milta, to -1 return karenge

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    int linearSearch(vector<int>& arr, int target) {
        // TC: O(n), SC: O(1)
        for (int i = 0; i < arr.size(); i++) {
            if (arr[i] == target) {
                return i;
            }
        }
        return -1;
    }
    ```

-----

### **28 N Queens**

**Q: N-Queens problem ka approach aur C++ code do**

**A:**

  * **Problem Statement:** N×N chessboard par N queens ko is tarah place karna hai ki koi bhi do queens ek doosre ko attack na kar sakein

  * **Approach:** Hum **Backtracking** ka use karenge
    1 Ek function banayenge jo column-by-column queens place karne ki koshish karega
    2 Har column ke liye, hum har row mein queen rakh kar dekhenge
    3 Agar kisi row mein queen rakhna safe hai (koi aur queen usse attack na kar rahi ho), to queen rakh kar agle column ke liye function ko recursively call karenge
    4 Agar aage solution nahi milta, to hum **backtrack** karenge (queen hata denge) aur ussi column ki agli row try karenge

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    bool isSafe(int row, int col, vector<string>& board, int n) {
        int r = row, c = col;
        while (r >= 0 && c >= 0) if (board[r--][c--] == 'Q') return false;
        r = row; c = col;
        while (c >= 0) if (board[r][c--] == 'Q') return false;
        r = row; c = col;
        while (r < n && c >= 0) if (board[r++][c--] == 'Q') return false;
        return true;
    }

    void solve(int col, vector<string>& board, vector<vector<string>>& ans, int n) {
        if (col == n) {
            ans.push_back(board);
            return;
        }
        for (int row = 0; row < n; row++) {
            if (isSafe(row, col, board, n)) {
                board[row][col] = 'Q';
                solve(col + 1, board, ans, n);
                board[row][col] = '.'; // Backtrack
            }
        }
    }

    vector<vector<string>> solveNQueens(int n) {
        // TC: O(N!), SC: O(N*N)
        vector<vector<string>> ans;
        vector<string> board(n, string(n, '.'));
        solve(0, board, ans, n);
        return ans;
    }
    ```

-----

### **29 Symmetric Tree**

**Q: Symmetric Tree check karne ka problem, approach, aur C++ code do**

**A:**

  * **Problem Statement:** Ek binary tree diya hai, check karna hai ki kya woh apni mirror image hai

  * **Approach:** Hum **Recursion** ka use karenge
    1 Ek helper function `isMirror(node1, node2)` banayenge
    2 Yeh function check karega ki kya `node1` ka left subtree `node2` ke right subtree ka mirror hai, aur `node1` ka right subtree `node2` ke left subtree ka mirror hai
    3 Main function se hum `isMirror(root->left, root->right)` call karenge

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    struct TreeNode {
        int val;
        TreeNode *left, *right;
    };

    bool isMirror(TreeNode* t1, TreeNode* t2) {
        if (!t1 && !t2) return true;
        if (!t1 || !t2) return false;
        return (t1->val == t2->val) && isMirror(t1->left, t2->right) && isMirror(t1->right, t2->left);
    }

    bool isSymmetric(TreeNode* root) {
        // TC: O(N), SC: O(Height)
        if (!root) return true;
        return isMirror(root->left, root->right);
    }
    ```

-----

### **30 Insert Into A Binary Search Tree**

**Q: Binary Search Tree (BST) mein element insert karne ka approach aur C++ code do**

**A:**

  * **Problem Statement:** Ek Binary Search Tree (BST) aur ek value di hai Aapko us value ko BST mein insert karna hai aur BST ki properties maintain karni hain

  * **Approach:** Hum **Recursive** approach use karenge
    1 Agar root `NULL` hai, to naya node banakar return kar do
    2 Agar value root ki value se chhoti hai, to left subtree mein insert karne ke liye recursively call karo
    3 Agar value root ki value se badi hai, to right subtree mein insert karne ke liye recursively call karo

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    struct TreeNode {
        int val;
        TreeNode *left, *right;
        TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
    };

    TreeNode* insertIntoBST(TreeNode* root, int val) {
        // TC: O(Height), SC: O(Height)
        if (root == nullptr) {
            return new TreeNode(val);
        }
        if (val < root->val) {
            root->left = insertIntoBST(root->left, val);
        } else {
            root->right = insertIntoBST(root->right, val);
        }
        return root;
    }
    ```

-----

### **31 Next Greater Element**

**Q: Next Greater Element find karne ka problem, approach, aur C++ code do**

**A:**

  * **Problem Statement:** Ek array diya hai Har element ke liye, uske right side mein pehla element find karna hai jo usse bada ho Agar nahi hai to -1

  * **Approach:** Hum **Stack** ka use karenge
    1 Array ko **right se left** traverse karenge
    2 Har element `arr[i]` ke liye, stack se tab tak pop karenge jab tak stack ka top `arr[i]` se chhota ya barabar hai
    3 Pop karne ke baad, agar stack empty hai to `arr[i]` ka next greater element -1 hai, warna stack ka top element hai
    4 `arr[i]` ko stack mein push kar denge

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    vector<int> nextGreaterElement(vector<int>& arr) {
        // TC: O(n), SC: O(n)
        int n = arr.size();
        vector<int> result(n);
        stack<int> s;
        for (int i = n - 1; i >= 0; i--) {
            while (!s.empty() && s.top() <= arr[i]) {
                s.pop();
            }
            if (s.empty()) {
                result[i] = -1;
            } else {
                result[i] = s.top();
            }
            s.push(arr[i]);
        }
        return result;
    }
    ```

-----

### **32 Deletion In Circular Linked List**

**Q: Circular Linked List se node delete karne ka approach aur C++ code do**

**A:**

  * **Problem Statement:** Ek Circular Linked List aur ek `key` di hai Aapko `key` waale node ko delete karna hai

  * **Approach:**
    1 Pehle list ko traverse karke node to be deleted (`curr`) aur uske pichle node (`prev`) ko find karenge
    2 **Case 1: Node head hai** Last node ko find karke uska `next` ko `head->next` par point karayenge aur naya head set kar denge
    3 **Case 2: Node beech mein ya aakhir mein hai** `prev->next` ko `curr->next` par point karayenge
    4 Aakhir mein `curr` node ko free kar denge

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    struct Node { int data; Node *next; };

    void deleteNode(Node*& head, int key) {
        // TC: O(n), SC: O(1)
        if (head == nullptr) return;
        Node *curr = head, *prev = nullptr;
        while (curr->data != key) {
            if (curr->next == head) return; // Not found
            prev = curr;
            curr = curr->next;
        }
        if (curr == head) { // Deleting head
            prev = head;
            while(prev->next != head) prev = prev->next;
            head = curr->next;
            prev->next = head;
        } else { // Deleting other node
            prev->next = curr->next;
        }
        delete curr;
    }
    ```

-----

### **33 Height of Binary Tree**

**Q: Binary Tree ki height find karne ka problem, approach, aur C++ code do**

**A:**

  * **Problem Statement:** Ek binary tree diya hai, aapko uski height (ya maximum depth) nikalni hai

  * **Approach:** Hum **Recursion** ka use karenge Height of a tree = `1 + max(height of left subtree, height of right subtree)` Base case: Agar node `NULL` hai to height `0` hogi

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    struct TreeNode {
        int val;
        TreeNode *left, *right;
    };

    int height(TreeNode* root) {
        // TC: O(n), SC: O(Height)
        if (root == nullptr) {
            return 0;
        }
        int leftHeight = height(root->left);
        int rightHeight = height(root->right);
        return 1 + max(leftHeight, rightHeight);
    }
    ```

-----

### **34 Merge Two Sorted Arrays**

**Q: Do sorted arrays ko merge karne ka problem, approach, aur C++ code do**

**A:**

  * **Problem Statement:** Do sorted arrays diye gaye hain, aapko unhe merge karke ek single sorted array banana hai

  * **Approach:** Hum **Two-Pointer** technique ka use karenge
    1 Ek naya result array banayenge
    2 Do pointers, `i` aur `j`, lenge jo dono arrays ke start mein honge
    3 `arr1[i]` aur `arr2[j]` ko compare karenge, jo chhota hoga use result mein daal denge aur uske pointer ko aage badha denge
    4 Jab ek array khatam ho jaye, to doosre array ke bache hue saare elements ko result mein daal denge

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    vector<int> mergeArrays(vector<int>& arr1, vector<int>& arr2) {
        // TC: O(m+n), SC: O(m+n)
        int m = arr1.size(), n = arr2.size();
        vector<int> result(m + n);
        int i = 0, j = 0, k = 0;
        while (i < m && j < n) {
            if (arr1[i] < arr2[j]) {
                result[k++] = arr1[i++];
            } else {
                result[k++] = arr2[j++];
            }
        }
        while (i < m) result[k++] = arr1[i++];
        while (j < n) result[k++] = arr2[j++];
        return result;
    }
    ```

-----

### **35 Compress the String**

**Q: String ko compress karne ka problem, example, approach, aur C++ code do**

**A:**

  * **Problem Statement:** Ek string ko compress karna hai jismein consecutive repeated characters ko character aur uske count se replace karna hai

  * **Example:**

      * **Input:** `"aaabbbcc"`
      * **Output:** `"a3b3c2"`

  * **Approach:**
    1 Ek `result` string banayenge
    2 Original string ko traverse karenge aur har consecutive group of same characters ka count nikalenge
    3 Jab character badle ya string khatam ho, to pichle character aur uske count ko `result` string mein append kar denge

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    string compressString(string s) {
        // TC: O(n), SC: O(n)
        if (s.empty()) return "";
        string compressed = "";
        int count = 1;
        for (int i = 0; i < s.length(); i++) {
            if (i + 1 < s.length() && s[i] == s[i+1]) {
                count++;
            } else {
                compressed += s[i];
                compressed += to_string(count);
                count = 1;
            }
        }
        return compressed;
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

### **37 0 - 1 Knapsack Problem**

**Q: 0-1 Knapsack problem ka approach aur C++ code do**

**A:**

  * **Problem Statement:** N items ke weights aur values diye gaye hain Ek `W` capacity ka knapsack (bag) hai Aapko items ko is tarah select karna hai ki total value maximum ho, aur total weight `W` se zyada na ho Har item ya to poora liya ja sakta hai ya nahi liya ja sakta

  * **Approach:** Hum **Dynamic Programming** ka use karenge Ek 2D `dp` table banayenge `dp[i][w]` ka matlab hoga '`i` items use karke `w` weight capacity mein maximum value'

      * **`dp[i][w] = max(value[i-1] + dp[i-1][w - weight[i-1]], dp[i-1][w])`**

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    int knapsack(int W, vector<int>& wt, vector<int>& val, int n) {
        // TC: O(n*W), SC: O(n*W)
        vector<vector<int>> dp(n + 1, vector<int>(W + 1, 0));
        for (int i = 1; i <= n; i++) {
            for (int w = 1; w <= W; w++) {
                if (wt[i - 1] <= w) {
                    dp[i][w] = max(val[i - 1] + dp[i - 1][w - wt[i - 1]], dp[i - 1][w]);
                } else {
                    dp[i][w] = dp[i - 1][w];
                }
            }
        }
        return dp[n][W];
    }
    ```

-----

### **38 Topological sort**

**Q: Topological Sort ka approach aur C++ code do**

**A:**

  * **Problem Statement:** Ek Directed Acyclic Graph (DAG) diya hai, aapko uske vertices ka ek linear ordering nikalna hai, jismein har edge `u -> v` ke liye `u`, `v` se pehle aaye

  * **Approach (Kahn's Algorithm - BFS based):**
    1 Sabse pehle saare nodes ka in-degree (unpar aane wali edges) calculate karo
    2 Jin nodes ka in-degree `0` hai, unhe ek queue mein daal do
    3 Jab tak queue empty na ho jaye, queue se ek node nikalo, use result mein add karo, aur uske saare neighbors ka in-degree ek se kam kar do
    4 Agar kisi neighbor ka in-degree `0` ho jaye, to use bhi queue mein daal do

  * **C++ Code:**

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    vector<int> topologicalSort(int V, vector<int> adj[]) {
        // TC: O(V+E), SC: O(V)
        vector<int> in_degree(V, 0);
        for (int i = 0; i < V; i++) {
            for (int u : adj[i]) {
                in_degree[u]++;
            }
        }
        queue<int> q;
        for (int i = 0; i < V; i++) {
            if (in_degree[i] == 0) {
                q.push(i);
            }
        }
        vector<int> result;
        while (!q.empty()) {
            int u = q.front();
            q.pop();
            result.push_back(u);
            for (int v : adj[u]) {
                in_degree[v]--;
                if (in_degree[v] == 0) {
                    q.push(v);
                }
            }
        }
        return result;
    }
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

-----

## **3 SQL mein Joins kya hain? Alag-alag types ke Joins samjhaiye.**

**A:**
**Joins** ka use SQL mein do ya do se zyada tables se data ko unke beech ke **related column** (jaise `employee_id`) ke basis par combine karke ek saath laane ke liye kiya jaata hai.

Sabse common types ke Joins yeh hain:

  * **`INNER JOIN`:**

      * Yeh sirf wahi rows return karta hai jinke liye dono tables mein matching value milti hai. Yeh sabse common join hai.
      * **Example:** Sirf unn employees ki list dega jinka department, `Departments` table mein मौजूद hai.

  * **`LEFT JOIN` (ya `LEFT OUTER JOIN`):**

      * Yeh **left table ki saari rows** aur right table ki sirf matching rows return karta hai.
      * Agar right table mein koi match nahi milta, to wahaan `NULL` dikhata hai.
      * **Example:** Saare employees ki list dega, bhale hi unka department assign na hua ho.

  * **`RIGHT JOIN` (ya `RIGHT OUTER JOIN`):**

      * Yeh `LEFT JOIN` ka ulta hai. Yeh **right table ki saari rows** aur left table ki sirf matching rows return karta hai.
      * Agar left table mein match nahi milta, to wahaan `NULL` dikhata hai.
      * **Example:** Saare departments ki list dega, bhale hi unmein koi employee na ho.

  * **`FULL OUTER JOIN`:**

      * Yeh dono tables ki **saari rows** return karta hai.
      * Jahaan bhi match milta hai, data dikhata hai, aur jahaan nahi milta, wahaan `NULL` dikhata hai.

-----

## **4 Normalization kya hai?**

**A:**
**Normalization**, database design karne ki ek aisi process hai jismein data ko tables mein is tarah se organize kiya jaata hai ki **data redundancy** (data ka baar-baar repeat hona) kam se kam ho aur **data integrity** (data ka sahi aur consistent hona) bani rahe.

**Iska Main Maqsad (Goal):**

  * **Data Duplication ko kam karna:** Ek hi jaankari ko alag-alag jagah store hone se rokna.
  * **Data Anomalies ko hatana:** Data ko insert, update, ya delete karte waqt hone waali problems se bachna.

Is process mein, hum ek badi table ko todkar choti-choti, aapas mein aasaani se judi hui (well-structured) tables mein baant dete hain. Normalization ke alag-alag levels hote hain jinhe **Normal Forms** (jaise 1NF, 2NF, 3NF) kehte hain.

-----

## **5 `UNION` aur `UNION ALL` mein kya difference hai?**

**A:**
Dono hi operators do ya do se zyada `SELECT` statements ke results ko combine karke ek single result set banate hain. Lekin inmein ek bahut bada fark hai:

  * **`UNION`:**

      * Yeh result set se **duplicate rows ko hata deta hai**.
      * Yeh sirf **unique rows** ko hi return karta hai.
      * Duplicates hatane ke liye isse internally data ko sort karna padta hai, isliye yeh `UNION ALL` se thoda **slow** hota hai.

  * **`UNION ALL`:**

      * Yeh result set se **duplicate rows ko nahi hatata**.
      * Yeh dono `SELECT` statements ke **saare results** ko jaisa ka taisa (as-is) combine kar deta hai.
      * Kyunki isse koi extra check nahi karna padta, yeh `UNION` se **fast** hota hai.

**Example:**
Agar table A mein `{1, 2}` aur table B mein `{2, 3}` hai:

  * `SELECT * FROM A UNION SELECT * FROM B` ka result hoga `{1, 2, 3}`.
  * `SELECT * FROM A UNION ALL SELECT * FROM B` ka result hoga `{1, 2, 2, 3}`.

---

## **1 REST APIs kya hain?**

**A:**
**REST** ka full form hai **Representational State Transfer**. Yeh software banane ka ek architectural style (design karne ka tareeka) hai.

Jab do alag-alag software applications ko aapas mein baat karni hoti hai, to woh **API** (Application Programming Interface) ka istemaal karte hain. Aur jab koi API, REST ke rules ko follow karti hai, to use **RESTful API** kehte hain.

**Simple bhasha mein,** yeh ek restaurant ke waiter ki tarah hai:
* Aap (client/frontend) waiter (API) ko ek order (request) dete hain.
* Waiter us order ko kitchen (server/backend) tak le jaata hai.
* Kitchen order taiyaar karta hai aur waiter (API) use aap tak (response) laata hai.

Yeh web services banane ka sabse popular tareeka hai, jo standard **HTTP methods** ka use karta hai:
* **`GET`:** Data ko server se maangne (read) ke liye.
* **`POST`:** Server par naya data banane (create) ke liye.
* **`PUT`:** Server par maujood data ko update karne ke liye.
* **`DELETE`:** Server se data ko delete karne ke liye.

---
## **2 HTTP aur HTTPS mein kya difference hai?**

**A:**
Dono hi web browser aur server ke beech data transfer karne ke protocols hain. Inmein sabse bada aur zaroori fark **Security** ka hai.

* **HTTP (Hypertext Transfer Protocol):**
    * Ismein data **plain text** mein jaata hai.
    * Yeh **secure nahi hai**. Koi bhi hacker aapka data (jaise password, credit card details) beech mein padh sakta hai.

* **HTTPS (Hypertext Transfer Protocol Secure):**
    * Yeh HTTP ka **secure version** hai. 'S' ka matlab hi **Secure** hai.
    * Yeh data ko transfer karne se pehle **encrypt** (ek secret code mein badal) kar deta hai. Iske liye yeh **SSL/TLS certificate** ka use karta hai.
    * Encryption ke kaaran, data poori tarah safe rehta hai.

Aap kisi website ki pehchan uske URL mein `https://` aur browser mein bane **lock 🔒 icon** se kar sakte hain.



---
## **3 Software Development Life Cycle (SDLC) ko samjhaiye.**

**A:**
**SDLC** ka full form hai **Software Development Life Cycle**. Yeh ek poora process ya framework hai jo ek high-quality software ko plan karne se lekar banane, test karne, aur maintain karne tak ke saare steps ko define karta hai.

Yeh ek ghar banane jaisa hai, jiske **6 main stages** hote hain:

1.  **Requirement Gathering:** Grahak se uski zarooratein (requirements) samjhna. (Ghar mein kitne kamre chahiye?)
2.  **Planning & Design:** Software ka blueprint ya architecture design karna. (Ghar ka naksha banana).
3.  **Implementation / Coding:** Developers dwara actual code likhna. (Ghar ko banana).
4.  **Testing:** Software mein bugs aur galtiyon ko dhoondhna aur theek karna. (Ghar ki quality check karna).
5.  **Deployment:** Software ko users ke liye live (launch) karna. (Grahak ko ghar handover karna).
6.  **Maintenance:** Software launch hone ke baad uski dekhbhaal karna, updates dena, aur aane waali problems ko fix karna. (Ghar ka regular repair aur maintenance).

---
## **4 Agile methodology kya hai?**

**A:**
**Agile** software develop karne ka ek modern, flexible, aur tezi se kaam karne wala tareeka hai. Yeh traditional **Waterfall model** (jahan ek kaam khatam hone ke baad hi doosra shuru hota hai) se bilkul alag hai.

Agile mein, poore project ko **chhote-chhote hisson** mein tod diya jaata hai. In hisson par **chhote-chhote cycles** mein kaam hota hai.

* **Sprints:** In chhote development cycles ko **sprints** kehte hain, jo aam taur par 1 se 4 hafte ke hote hain.
* **Lagatar Feedback:** Har sprint ke aakhir mein, team ek chhota sa working software feature client ko dikhati hai. Isse client se lagatar **feedback** milta rehta hai.
* **Flexibility:** Agar client ko koi naya change chahiye, to use agle sprint mein aasaani se shaamil kiya jaa sakta hai.
Iska main focus **team collaboration, customer satisfaction, aur badalte hue requirements ko apnane** par hota hai. Iske do popular frameworks hain: **Scrum** aur **Kanban**.
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