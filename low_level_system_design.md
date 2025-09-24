# 📌 LLD Interview Questions List

### 🟢 Easy Level

1. **Design Tic Tac Toe**
2. **Design Snake and Ladder Game** ✅ (added)
3. **Design LRU Cache**
4. **Design Parking Lot** ✅ (added)
5. **Design Stack Overflow (basic Q\&A)**
6. **Design Vending Machine**
7. **Design Logging Framework**
8. **Design Coffee Vending Machine** ✅ (added; extension of vending machine)
9. **Design Task Management System (like Trello/Jira)**
10. **Design Traffic Signal Control System**

---

### 🟡 Medium Level

1. **Design ATM**
2. **Design LinkedIn (basic social network)**
3. **Design Pub-Sub System** ✅ (added)
4. **Design an Elevator System**
5. **Design Car Rental System**
6. **Design Online Auction System (like eBay)**
7. **Design Hotel Management System**
8. **Design Digital Wallet (like Paytm/Google Pay)**
9. **Design Airline Management System**
10. **Design Library Management System**
11. **Design Restaurant Management System**
12. **Design Concert Ticket Booking System**
13. **Design Social Network Service (like Facebook)**

---

### 🔴 Hard Level


1. **Design CricInfo (Live Commentary System)**
2. **Design Splitwise**
3. **Design Chess Game**
4. **Design Course Registration System (university portal)**
5. **Design Movie Ticket Booking System (like BookMyShow)** ✅ (added)
6. **Design Online Stock Brokerage System**
7. **Design Ride-Sharing System (like Uber)**
8. **Design Music Streaming Service (like Spotify)**
9. **Design Online Shopping Service (like Amazon/Flipkart)**
10. **Design Food Delivery System (like Swiggy/Zomato)**

---


### 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * Ek 3x3 ka grid hona chahiye.
      * Do players honge: Player 1 ('X') aur Player 2 ('O').
      * Players ek ke baad ek apni chaal chalenge.
      * Ek player khaali cell mein apna symbol (X ya O) daal sakta hai.
      * Game tab jeeta jaayega jab koi player 3 symbols ek line (horizontal, vertical, ya diagonal) mein bana le.
      * Agar board bhar jaaye aur koi na jeete, toh game draw ho jaayega.
      * Game ke end mein winner ya draw ka result dikhana hoga.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Scalability:** Zaroorat nahi hai, yeh ek simple 2-player game hai.
      * **Performance:** Game bahut fast hona chahiye, koi delay nahi.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Yeh ek console-based game hai (command-line par chalega).
      * Ek hi machine par do players khelenge.
      * Internet ya multi-player ki zaroorat nahi hai.

-----

### 2. Mukhya Objects (Core Objects)

Teen mukhya classes hongi:

1.  **`Player`:**

      * **Attributes:** `string name`, `char symbol` ('X' ya 'O').
      * **Methods:** Constructor to set name and symbol, getters to get them.

2.  **`Board`:**

      * **Attributes:** `vector<vector<char>> grid` (3x3 grid ko store karne ke liye).
      * **Methods:**
          * `initializeGrid()`: Board ko shuru mein khaali set karna.
          * `printBoard()`: Board ko console par display karna.
          * `placeMark(int row, int col, char symbol)`: Diye gaye position par symbol place karna.
          * `checkWin(char symbol)`: Check karna ki koi jeeta ya nahi.
          * `isFull()`: Check karna ki board bhar gaya ya nahi.

3.  **`Game`:**

      * **Attributes:** `Board board`, `Player* player1`, `Player* player2`, `Player* currentPlayer`.
      * **Methods:**
          * `start()`: Game ka main loop shuru karna.
          * `playTurn()`: Current player se input lena aur move chalna.
          * `swapPlayer()`: Turn ko doosre player par switch karna.
          * `isGameOver()`: Check karna ki game khatm ho gaya ya nahi.

-----

### 3. Classes ke Beech Rishte (Relationships)

  * **Composition:**
      * `Game` class ke andar `Board` object hai. (`Game` **has-a** `Board`). Board game ke bina exist nahi kar sakta.
      * `Game` class ke andar do `Player` objects hain. (`Game` **has-a** `Player`).
  * **Inheritance/Interfaces:** Is simple game ke liye inheritance ya abstract classes ki zaroorat nahi hai. Yeh over-engineering hoga.

-----

### 4. Data Storage

  * Yeh ek simple console game hai, isliye saara data (board state, player details) **in-memory** rahega. Game band hone par data chala jaayega.
  * Database ya file storage ki koi zaroorat nahi hai.

-----

### 5. Concurrency

  * Game turn-based hai, isliye ek samay par ek hi player move karega.
  * Multiple users ya threads ko handle karne ki koi zaroorat nahi hai. Isliye locks ya synchronization ki zaroorat nahi hai.

-----

### 6. Scalability

  * Yeh design 2-player game ke liye banaya gaya hai aur yeh scalable nahi hai.
  * Agar isko 10M users ke liye banana ho, toh client-server architecture, networking, aur database ka istemal karna padega, jo is design ke scope se bahar hai.

-----

### 7. Galtiyon ko Sambhalna (Error Handling)

  * **Invalid Input:** Agar player aisi row/column daalta hai jo board par nahi hai (e.g., row 5), toh system ek error message dega aur dobara input maangega.
  * **Occupied Cell:** Agar player aisi jagah move chalta hai jahan pehle se 'X' ya 'O' hai, toh system error dega aur dobara input maangega.

-----

### 8. Design ke Siddhant (Principles)

  * **SOLID Principles:**
      * **Single Responsibility Principle (SRP):** Har class ka ek hi kaam hai. `Board` sirf board manage karta hai, `Player` sirf player ki details rakhta hai, aur `Game` sirf game ke rules aur flow ko control karta hai.
      * **Open/Closed Principle (OCP):** Yeh design abhi OCP follow nahi kar raha. Agar board ka size 3x3 se 4x4 karna ho, toh `Board` aur `Game` class mein changes karne padenge. Is simple game ke liye yeh theek hai.
  * **Extensibility:** Naye features add karna (jaise score keeping) `Game` class mein aasani se kiya ja sakta hai.

-----

### 9. APIs

  * Console application hone ke kaaran koi REST API ya gRPC interface nahi hai. Iska "interface" command-line hi hai, jahan user row aur column number input karta hai.

-----

### Tic Tac Toe ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// ===================================
// == PLAYER CLASS ==
// ===================================
// Yeh class player ki details rakhti hai - naam aur symbol (X/O)
class Player {
public:
    string name;
    char symbol;

    Player(string name, char symbol) {
        this->name = name;
        this->symbol = symbol;
    }
};

// ===================================
// == BOARD CLASS ==
// ===================================
// Yeh class 3x3 ke grid aur usse judi logic ko manage karti hai.
class Board {
public:
    vector<vector<char>> grid;

    Board() {
        // Board ko initialize karo, shuru mein sab jagah khaali (' ')
        grid = vector<vector<char>>(3, vector<char>(3, ' '));
    }

    // Board ko console par print karna
    void printBoard() {
        cout << "-------------" << endl;
        for (int i = 0; i < 3; i++) {
            cout << "| ";
            for (int j = 0; j < 3; j++) {
                cout << grid[i][j] << " | ";
            }
            cout << endl << "-------------" << endl;
        }
    }

    // Diye gaye row/col par symbol place karna
    bool placeMark(int row, int col, char symbol) {
        if (row >= 0 && row < 3 && col >= 0 && col < 3 && grid[row][col] == ' ') {
            grid[row][col] = symbol;
            return true; // Move successful
        }
        return false; // Move invalid
    }

    // Jeetne ki condition check karna
    bool checkWin(char symbol) {
        // Rows aur Columns check karo
        for (int i = 0; i < 3; i++) {
            if ((grid[i][0] == symbol && grid[i][1] == symbol && grid[i][2] == symbol) ||
                (grid[0][i] == symbol && grid[1][i] == symbol && grid[2][i] == symbol)) {
                return true;
            }
        }
        // Diagonals check karo
        if ((grid[0][0] == symbol && grid[1][1] == symbol && grid[2][2] == symbol) ||
            (grid[0][2] == symbol && grid[1][1] == symbol && grid[2][0] == symbol)) {
            return true;
        }
        return false;
    }

    // Board bhar gaya ya nahi (Draw condition)
    bool isFull() {
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                if (grid[i][j] == ' ') {
                    return false;
                }
            }
        }
        return true;
    }
};

// ===================================
// == GAME CLASS ==
// ===================================
// Yeh class game ke poore flow, rules, aur player turns ko manage karti hai.
class Game {
private:
    Board board;
    Player* player1;
    Player* player2;
    Player* currentPlayer;

public:
    Game(string p1Name, string p2Name) {
        player1 = new Player(p1Name, 'X');
        player2 = new Player(p2Name, 'O');
        currentPlayer = player1; // Shuruaat Player 1 se
    }
    
    // Memory ko free karne ke liye destructor
    ~Game() {
        delete player1;
        delete player2;
    }

    // Players ki turn switch karna
    void swapPlayer() {
        if (currentPlayer == player1) {
            currentPlayer = player2;
        } else {
            currentPlayer = player1;
        }
    }

    // Game shuru karne ka main function
    void start() {
        while (true) {
            board.printBoard();
            cout << currentPlayer->name << " (" << currentPlayer->symbol << "), enter your move (row and column): ";
            
            int row, col;
            cin >> row >> col;

            // Move ko place karne ki koshish karo
            if (board.placeMark(row, col, currentPlayer->symbol)) {
                // Agar move valid hai, toh jeetne ki condition check karo
                if (board.checkWin(currentPlayer->symbol)) {
                    board.printBoard();
                    cout << currentPlayer->name << " wins!" << endl;
                    break; // Game khatm
                }
                // Agar board bhar gaya hai, toh draw
                else if (board.isFull()) {
                    board.printBoard();
                    cout << "It's a draw!" << endl;
                    break; // Game khatm
                }
                // Agar game chalu hai, toh player switch karo
                else {
                    swapPlayer();
                }
            } else {
                // Agar move invalid hai
                cout << "Invalid move. Try again." << endl;
            }
        }
    }
};

// ===================================
// == MAIN FUNCTION ==
// ===================================
int main() {
    Game ticTacToe("Player 1", "Player 2");
    ticTacToe.start();
    return 0;
}
```



---

=

### 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * Ek game board hoga, aam taur par 1 se 100 tak.
      * Multiple players (2 se 4) khel sakenge.
      * Ek pasa (die) hoga jo 1 se 6 tak ka number dega.
      * Players bari-bari se pasa phenkenge aur apni goti (token) aage badhayenge.
      * Agar goti saanp (snake) ke munh par aati hai, toh woh neeche poonch par chali jaayegi.
      * Agar goti seedhi (ladder) ke neeche aati hai, toh woh upar chadh jaayegi.
      * Jo khiladi sabse pehle aakhiri square (100) par pahunchega, woh jeet jaayega.
      * Jeetne ke liye aakhiri square par aana zaroori hai; agar pasa phenkne par number aage nikal jaaye, toh goti wahin rahegi.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Scalability / Concurrency:** Zaroorat nahi hai. Yeh ek local multiplayer game hai.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Yeh ek console-based game hai.
      * Sabhi players ek hi machine par khelenge.
      * Board ka size 100 hai aur ek hi pasa hai.

-----

### 2. Mukhya Objects (Core Objects)

Chaar mukhya classes hongi:

1.  **`Player`:**

      * **Attributes:** `string name`, `int position`.
      * **Methods:** Constructor to set name and initial position, getters/setters.

2.  **`Dice`:**

      * **Attributes:** Nahi.
      * **Methods:** `roll()`: 1 se 6 ke beech ek random number return karega.

3.  **`Board`:**

      * **Attributes:** `int size`, `map<int, int> snakes`, `map<int, int> ladders`. (Map ka key start position hai aur value end position).
      * **Methods:** Constructor to set up the board, `getNewPosition(int currentPosition)`: Check karega ki current position par saanp ya seedhi hai ya nahi aur nayi position return karega.

4.  **`Game`:**

      * **Attributes:** `Board board`, `Dice dice`, `queue<Player*> players`, `Player* winner`.
      * **Methods:**
          * `initializeGame()`: Players ko add karna aur game setup karna.
          * `start()`: Game ka main loop shuru karna jo tab tak chalta hai jab tak koi jeet na jaaye.
          * `playTurn()`: Current player ke liye pasa roll karna, goti move karna, aur game state update karna.

-----

### 3. Classes ke Beech Rishte (Relationships)

  * **Composition:**
      * `Game` class ke andar `Board`, `Dice`, aur `Player` objects hain. (`Game` **has-a** `Board`, `Dice`, `Players`). Yeh sabhi game ke zaroori hisse hain.
  * **Inheritance/Interfaces:** Is simple game ke liye inki zaroorat nahi hai. Saare rishte "has-a" type ke hain.

-----

### 4. Data Storage

  * Saara data (board state, player positions) **in-memory** rahega. Game session ke dauraan hi data maujood rahega.
  * Database ya file storage ki koi zaroorat nahi hai.

-----

### 5. Concurrency

  * Game turn-based aur sequential hai. Ek samay par ek hi player khelega.
  * Concurrency ya thread management ki koi zaroorat nahi hai.

-----

### 6. Scalability

  * Yeh design kuch local players ke liye hai. Ise bade online multiplayer game mein badalne ke liye client-server architecture ki zaroorat padegi, jo is design ke scope mein nahi hai.

-----

### 7. Galtiyon ko Sambhalna (Error Handling)

  * Is game mein user input bahut kam hai (sirf 'Enter' dabana). Isliye user input validation ki zaroorat nahi hai.
  * Game ka logic (jaise 100 se aage na jaana) rules ka hissa hai, error nahi.

-----

### 8. Design ke Siddhant (Principles)

  * **SOLID Principles:**
      * **Single Responsibility Principle (SRP):** Har class ka ek hi kaam hai. `Board` sirf board ke layout (saanp/seedhi) ko jaanta hai. `Dice` sirf roll karna jaanta hai. `Player` apni position jaanta hai. `Game` sabko milakar khel chalata hai.
  * **Extensibility:** Yeh design kaafi extensible hai. Board ka size, saanp aur seedhi ki positions ko `Game` class mein aasani se badla ja sakta hai bina doosri classes ko chhede.

-----

### 9. APIs

  * Console application hone ke kaaran koi external API nahi hai. User ka interface command-line hai.

-----

### Snake and Ladder ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// ===================================
// == PLAYER CLASS ==
// ===================================
// Yeh class khiladi ki details rakhti hai - naam aur current position
class Player {
public:
    string name;
    int position;

    Player(string name) {
        this->name = name;
        this->position = 0; // Sabhi players 0 se shuru karte hain (board ke bahar)
    }
};

// ===================================
// == DICE CLASS ==
// ===================================
// Yeh class pasa (die) ko represent karti hai.
class Dice {
public:
    // 1 se 6 ke beech ek random number return karta hai
    int roll() {
        return (rand() % 6) + 1;
    }
};

// ===================================
// == BOARD CLASS ==
// ===================================
// Yeh class game board, saanp, aur seedhiyon ko manage karti hai.
class Board {
public:
    int size;
    map<int, int> snakes;
    map<int, int> ladders;

    Board(int size, map<int, int> s, map<int, int> l) {
        this->size = size;
        this->snakes = s;
        this->ladders = l;
    }

    // Yeh function check karta hai ki nayi position par saanp ya seedhi hai ya nahi
    int getNewPosition(int currentPosition) {
        if (snakes.count(currentPosition)) {
            cout << "Oh no! Saanp ne kaat liya! " << currentPosition << " se " << snakes[currentPosition] << " par." << endl;
            return snakes[currentPosition];
        }
        if (ladders.count(currentPosition)) {
            cout << "Yay! Seedhi mil gayi! " << currentPosition << " se " << ladders[currentPosition] << " par." << endl;
            return ladders[currentPosition];
        }
        return currentPosition; // Koi badlav nahi
    }
};

// ===================================
// == GAME CLASS ==
// ===================================
// Yeh class game ke poore flow, rules, aur player turns ko manage karti hai.
class Game {
private:
    Board board;
    Dice dice;
    queue<Player*> players;
    Player* winner;

public:
    Game(int boardSize, map<int, int> s, map<int, int> l, vector<string> playerNames) 
        : board(boardSize, s, l) {
        // Random number generation ke liye seed set karna
        srand(time(0));
        
        // Players ko game mein add karna
        for (const auto& name : playerNames) {
            players.push(new Player(name));
        }
        winner = nullptr;
    }

    ~Game() {
        while(!players.empty()){
            delete players.front();
            players.pop();
        }
    }

    // Game shuru karne ka main function
    void start() {
        cout << "Khel shuru ho gaya!" << endl;
        while (winner == nullptr) {
            playTurn();
        }
        cout << "Khel khatm! " << winner->name << " jeet gaya!" << endl;
    }

    // Ek player ki turn chalna
    void playTurn() {
        // Current player ko queue se nikalo
        Player* currentPlayer = players.front();
        players.pop();

        cout << "\n" << currentPlayer->name << " ki bari hai. Current position: " << currentPlayer->position << endl;
        cout << "Pasa roll karne ke liye Enter dabayein...";
        cin.get(); // Wait for user to press Enter

        int diceValue = dice.roll();
        cout << currentPlayer->name << " ne " << diceValue << " roll kiya." << endl;

        int newPosition = currentPlayer->position + diceValue;

        // Jeetne ki condition
        if (newPosition == board.size) {
            winner = currentPlayer;
        } 
        // Agar 100 se aage nikal gaye
        else if (newPosition > board.size) {
            cout << "Aap " << board.size << " se aage nahi ja sakte." << endl;
        } 
        // Normal move
        else {
            newPosition = board.getNewPosition(newPosition);
            currentPlayer->position = newPosition;
            cout << currentPlayer->name << " ki nayi position hai: " << currentPlayer->position << endl;
        }
        
        // Player ko wapas queue mein daal do
        players.push(currentPlayer);
    }
};

// ===================================
// == MAIN FUNCTION ==
// ===================================
int main() {
    // Game ka setup
    map<int, int> snakes = {{17, 7}, {54, 34}, {62, 19}, {64, 60}, {87, 24}, {93, 73}, {95, 75}, {99, 78}};
    map<int, int> ladders = {{4, 14}, {9, 31}, {20, 38}, {28, 84}, {40, 59}, {51, 67}, {63, 81}, {71, 91}};
    vector<string> playerNames = {"Amit", "Babita"};

    Game snakeAndLadder(100, snakes, ladders, playerNames);
    snakeAndLadder.start();

    return 0;
}
```

---


### 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * Cache ki ek fixed **capacity** honi chahiye.
      * **`get(key)` operation:** Agar key cache mein hai, toh uski value return karo aur use "sabse naya istemal hua" (most recently used) mark karo. Agar key nahi hai, toh -1 return karo.
      * **`put(key, value)` operation:** Agar key pehle se hai, toh uski value update karo aur use "most recently used" mark karo. Agar key nahi hai:
          * Agar cache full nahi hai, toh naya item daalo.
          * Agar cache full hai, toh "sabse purana istemal hua" (least recently used) item nikalo aur phir naya item daalo.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Performance:** `get` aur `put` dono operations bahut tez hone chahiye, ideally **O(1) time complexity** mein. Yeh sabse zaroori requirement hai.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Yeh cache ek single-threaded environment mein kaam karega.
      * Keys aur values simplicity ke liye integers hain.

-----

### 2. Mukhya Objects (Core Objects)

O(1) performance paane ke liye, hum do data structures ka istemal karenge:

1.  **Hash Map (`unordered_map` in C++):**

      * Yeh key se value tak O(1) mein pahunchne mein madad karega.
      * Lekin, map se yeh nahi pata chalta ki kaunsa item kab istemal hua.
      * Hum map mein key ke saath value nahi, balki uss item ke address (iterator/pointer) ko store karenge jo doosre data structure mein hai.
      * **`unordered_map<int, list<pair<int, int>>::iterator> cacheMap;`**

2.  **Doubly Linked List (`list` in C++):**

      * Yeh items ko unke istemal ke order mein rakhega.
      * **Sabse naya (Most Recently Used - MRU)** item list ke **head (front)** par hoga.
      * **Sabse purana (Least Recently Used - LRU)** item list ke **tail (back)** par hoga.
      * List mein kisi bhi element ko O(1) mein aage (front par) laaya ja sakta hai ya peeche se hataya ja sakta hai, agar hamare paas uska address ho.

**In dono ko milakar:** Map hamein O(1) mein list ke node tak pahunchayega, aur list hamein O(1) mein order badalne degi.

  * **Mukhya Class:** `LRUCache`

-----

### 3. Classes ke Beech Rishte (Relationships)

  * **Composition:**
      * `LRUCache` class ke andar ek `unordered_map` aur ek `list` hai. (`LRUCache` **has-a** `map` and **has-a** `list`). Yeh dono iske internal working ke liye zaroori hain.

-----

### 4. Data Storage

  * Yeh ek **in-memory** cache hai. Data application ke chalne tak hi memory mein rahega.
  * Database ya file storage ki koi zaroorat nahi hai.

-----

### 5. Concurrency

  * Yeh design single-threaded hai. Agar multiple threads ek saath `get` ya `put` call karein, toh data corrupt ho sakta hai.
  * Multi-threaded environment ke liye, `get` aur `put` functions ke andar **locks (`std::mutex`)** lagane padenge taaki ek samay par ek hi thread cache ko access kar paaye.

-----

### 6. Scalability

  * Yeh design ek single machine ki memory tak hi seemit hai.
  * Distributed cache (jo multiple machines par faila ho) ke liye Redis ya Memcached jaisi alag architecture ka istemal hota hai.

-----

### 7. Galtiyon ko Sambhalna (Error Handling)

  * **Cache Miss:** Agar `get` operation mein key nahi milti, toh function -1 return karega.
  * **Invalid Capacity:** Constructor mein check kiya ja sakta hai ki capacity 0 se badi ho.

-----

### 8. Design ke Siddhant (Principles)

  * **Single Responsibility Principle (SRP):** `LRUCache` class ka ek hi kaam hai - LRU caching logic ko manage karna.
  * **Encapsulation:** Cache ke andar ke `map` aur `list` private hain. User sirf `get` aur `put` public methods ke through hi interact kar sakta hai, jisse internal complexity chhipi rehti hai.

-----

### 9. APIs

  * Public API bahut saaf hai:
    1.  `LRUCache(int capacity)`: Cache ko initialize karne ke liye.
    2.  `int get(int key)`: Value paane ke liye.
    3.  `void put(int key, int value)`: Value daalne ya update karne ke liye.

-----

### LRU Cache ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// ===================================
// == LRU CACHE CLASS ==
// ===================================
// Yeh class LRU Cache ke poore logic ko implement karti hai.
class LRUCache {
private:
    int capacity;
    // Doubly Linked List: Order maintain karne ke liye (MRU -> LRU)
    // Hum pair<key, value> store karenge taaki jab LRU item hatana ho toh map se key bhi hata sakein.
    list<pair<int, int>> itemsList;
    
    // Hash Map: O(1) mein list ke node tak pahunchne ke liye
    // Key ko list ke iterator (address) se map karenge.
    unordered_map<int, list<pair<int, int>>::iterator> cacheMap;

public:
    LRUCache(int capacity) {
        this->capacity = capacity;
    }

    // `get` operation: O(1)
    int get(int key) {
        // Agar key map mein nahi hai, toh cache miss
        if (cacheMap.find(key) == cacheMap.end()) {
            return -1;
        }

        // Agar key mil gayi, toh use "Most Recently Used" banana hai.
        // Iske liye, use list mein se hata kar aage (front mein) laga do.
        // `splice` operation O(1) mein yeh kaam karta hai.
        list<pair<int, int>>::iterator it = cacheMap[key];
        itemsList.splice(itemsList.begin(), itemsList, it);
        
        // Value return karo. `it->second` ya `itemsList.front().second` dono kaam karenge.
        return it->second;
    }

    // `put` operation: O(1)
    void put(int key, int value) {
        // Agar key pehle se exist karti hai
        if (cacheMap.find(key) != cacheMap.end()) {
            // Uski value update karo aur use MRU bana do (list ke front mein le aao)
            list<pair<int, int>>::iterator it = cacheMap[key];
            it->second = value;
            itemsList.splice(itemsList.begin(), itemsList, it);
            return;
        }

        // Agar key nayi hai, aur cache full ho chuka hai
        if (cacheMap.size() == capacity) {
            // Sabse purana (Least Recently Used) item nikalo
            // Yeh list ke aakhir (back) mein hoga
            pair<int, int> lruItem = itemsList.back();
            itemsList.pop_back();
            cacheMap.erase(lruItem.first);
        }

        // Naya item daalo (yeh automatically MRU ban jaayega)
        // Ise list ke front mein daalo
        itemsList.push_front({key, value});
        // Map mein uski entry karo, jismein list ke front ka address (iterator) ho
        cacheMap[key] = itemsList.begin();
    }
};

// ===================================
// == MAIN FUNCTION ==
// ===================================
int main() {
    // 2 capacity ka cache banate hain
    LRUCache cache(2);

    cache.put(1, 10); // Cache: {1: 10}
    cache.put(2, 20); // Cache: {2: 20, 1: 10}

    cout << "Value for key 1: " << cache.get(1) << endl; // Returns 10. Cache ab: {1: 10, 2: 20} (1 MRU ban gaya)

    cache.put(3, 30); // Cache full hai. LRU item (2) niklega. Cache: {3: 30, 1: 10}

    cout << "Value for key 2: " << cache.get(2) << endl; // Returns -1 (kyunki 2 nikal chuka hai)

    cache.put(4, 40); // Cache full hai. LRU item (1) niklega. Cache: {4: 40, 3: 30}

    cout << "Value for key 1: " << cache.get(1) << endl; // Returns -1
    cout << "Value for key 3: " << cache.get(3) << endl; // Returns 30
    cout << "Value for key 4: " << cache.get(4) << endl; // Returns 40

    return 0;
}
```

---


### 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * Parking lot mein multiple floors (manzil) honge.
      * Har floor par alag-alag type ki parking spots (jagah) hongi: **Motorcycle**, **Car (Compact)**, **Truck (Large)** ke liye.
      * Gaadi (vehicle) parking lot mein enter kar sakti hai.
      * Entry par, ek **Ticket** generate hogi jismein entry time aur spot details hongi.
      * System ko gaadi ke type ke hisaab se khaali spot dhoondhna aana chahiye.
      * Gaadi exit kar sakti hai.
      * Exit par, parking ki duration ke hisaab se **fee calculate** hogi.
      * Payment process kiya jaayega.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Concurrency:** System ko ek saath multiple gaadiyon ki entry aur exit handle karna aana chahiye (thread-safe hona chahiye).
      * **Scalability:** Design aisa ho ki भविष्य mein naye floors ya naye type ki spots aasani se add kiye ja sakein.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Hum ek hi parking lot ko design kar rahe hain.
      * Parking fee ghante (hourly) ke hisaab se lagti hai.

-----

### 2. Mukhya Objects (Core Objects)

1.  **`Vehicle` (Gaadi):**

      * Yeh ek abstract class hogi.
      * **Attributes:** `string licensePlate`.
      * **Derived Classes:** `Motorcycle`, `Car`, `Truck`. Har class batayegi ki woh kis type ki hai.

2.  **`ParkingSpot` (Parking ki Jagah):**

      * Yeh bhi ek abstract class hogi.
      * **Attributes:** `int spotNumber`, `bool isOccupied`.
      * **Derived Classes:** `MotorcycleSpot`, `CompactSpot`, `LargeSpot`.

3.  **`ParkingFloor` (Parking ki Manzil):**

      * **Attributes:** `int floorNumber`, alag-alag type ke `ParkingSpot` ki lists.
      * **Methods:** `findAvailableSpot()`, `parkVehicle()`.

4.  **`ParkingTicket`:**

      * **Attributes:** `string ticketId`, `Vehicle* vehicle`, `ParkingSpot* spot`, `time_t entryTime`.

5.  **`PaymentStrategy`:**

      * Payment karne ke alag-alag tareekon ke liye ek abstract class.
      * **Derived Classes:** `CashPayment`, `CreditCardPayment`.

6.  **`ParkingLot` (Main Controller):**

      * Yeh poore system ka main entry point hai.
      * **Attributes:** Saare `ParkingFloor`s ki list, saare active `ParkingTicket`s ka map.
      * **Methods:** `entry()`, `exit()`, `calculateFee()`.

-----

### 3. Classes ke Beech Rishte (Relationships)

  * **Composition:**
      * `ParkingLot` **has-a** `ParkingFloor`.
      * `ParkingFloor` **has-a** `ParkingSpot`.
  * **Inheritance:**
      * `Motorcycle`, `Car`, `Truck` **is-a** `Vehicle`.
      * `MotorcycleSpot`, `CompactSpot`, `LargeSpot` **is-a** `ParkingSpot`.
  * **Association:**
      * `ParkingTicket` ek `Vehicle` aur ek `ParkingSpot` se juda hota hai.

-----

### 4. Data Storage

  * Active tickets (`ParkingTicket`) ka data system crash hone par bhi safe rehna chahiye. Real-world system mein iske liye database ka istemal hota hai.
  * Is design mein hum ise **in-memory** maan kar chalenge.

-----

### 5. Concurrency

  * `entry()` aur `exit()` methods critical hain. Jab ek hi khaali spot ke liye do gaadiyan ek saath aati hain, toh system ko ise theek se handle karna chahiye.
  * In functions ko thread-safe banane ke liye **locks (`std::mutex`)** ka istemal karna zaroori hai taaki shared data (jaise khaali spots ki list) corrupt na ho.

-----

### 6. Scalability

  * Yeh design ek parking lot ke liye hai. Ise naye floors aur spots add karke scale kiya ja sakta hai.
  * Multiple parking lots ko manage karne ke liye, ek `ParkingLotManager` class banayi ja sakti hai.

-----

### 7. Galtiyon ko Sambhalna (Error Handling)

  * **Parking Full:** Agar kisi type ki gaadi ke liye koi spot khaali nahi hai, toh `entry()` method ko yeh handle karna chahiye (e.g., "Parking Full" ka message dena).
  * **Invalid Ticket:** `exit()` method ko galat ticket ID ke case ko handle karna chahiye.

-----

### 8. Design ke Siddhant (Principles)

  * **Single Responsibility Principle (SRP):** Har class ka ek hi kaam hai. `ParkingSpot` apni state batata hai, `ParkingFloor` apne spots manage karta hai, aur `ParkingLot` poora flow control karta hai.
  * **Open/Closed Principle (OCP):** Abstract classes (`Vehicle`, `ParkingSpot`) ka istemal karke hum system ko extend kar sakte hain. Hum nayi gaadi (jaise `Bus`) aur nayi spot type (`BusSpot`) add kar sakte hain bina `ParkingLot` class ko change kiye.
  * **Facade Pattern:** `ParkingLot` class ek facade ki tarah kaam karti hai, jo ek complex system (floors, spots, tickets) ko use karne ke liye ek simple interface (`entry`, `exit`) deti hai.

-----

### 9. APIs

  * System ka public API `ParkingLot` class ke methods honge:
      * `ParkingTicket* entry(Vehicle* vehicle)`
      * `double exit(string ticketId, PaymentStrategy* paymentStrategy)`

-----

### Parking Lot ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Enums for types to avoid magic strings
enum class VehicleType { MOTORCYCLE, CAR, TRUCK };
enum class SpotType { MOTORCYCLE_SPOT, COMPACT_SPOT, LARGE_SPOT };

// Forward Declarations
class ParkingSpot;
class Vehicle;
class ParkingTicket;

// ===================================
// == VEHICLE HIERARCHY ==
// ===================================
// Vehicle ek abstract class hai
class Vehicle {
protected:
    string licensePlate;
public:
    Vehicle(string plate) : licensePlate(plate) {}
    virtual VehicleType getType() = 0; // Abstraction
    string getLicensePlate() { return licensePlate; }
    virtual ~Vehicle() {}
};

class Motorcycle : public Vehicle { // Inheritance
public:
    Motorcycle(string plate) : Vehicle(plate) {}
    VehicleType getType() override { return VehicleType::MOTORCYCLE; } // Polymorphism
};

class Car : public Vehicle {
public:
    Car(string plate) : Vehicle(plate) {}
    VehicleType getType() override { return VehicleType::CAR; }
};

// ===================================
// == PARKING SPOT HIERARCHY ==
// ===================================
// ParkingSpot ek abstract class hai
class ParkingSpot {
protected:
    int spotNumber;
    bool isOccupied;
public:
    ParkingSpot(int num) : spotNumber(num), isOccupied(false) {}
    virtual SpotType getType() = 0;
    void park() { isOccupied = true; }
    void vacate() { isOccupied = false; }
    bool isAvailable() { return !isOccupied; }
    virtual ~ParkingSpot() {}
};

class MotorcycleSpot : public ParkingSpot {
public:
    MotorcycleSpot(int num) : ParkingSpot(num) {}
    SpotType getType() override { return SpotType::MOTORCYCLE_SPOT; }
};

class CompactSpot : public ParkingSpot {
public:
    CompactSpot(int num) : ParkingSpot(num) {}
    SpotType getType() override { return SpotType::COMPACT_SPOT; }
};

// ===================================
// == CORE LOGIC CLASSES ==
// ===================================
// ParkingFloor class ek manzil ke saare spots ko manage karti hai
class ParkingFloor {
private:
    int floorNumber;
    map<SpotType, vector<ParkingSpot*>> spots;
public:
    ParkingFloor(int floorNum); // Implementation can create spots
    ~ParkingFloor();
    ParkingSpot* findAvailableSpot(VehicleType type);
    void parkVehicle(Vehicle* vehicle, ParkingSpot* spot);
};

// ParkingTicket entry par generate hota hai
class ParkingTicket {
private:
    string ticketId;
    Vehicle* vehicle;
    ParkingSpot* spot;
    time_t entryTime;
public:
    ParkingTicket(Vehicle* v, ParkingSpot* s);
    time_t getEntryTime();
    string getTicketId();
};

// ===================================
// == PAYMENT STRATEGY ==
// ===================================
class PaymentStrategy {
public:
    virtual bool processPayment(double amount) = 0;
    virtual ~PaymentStrategy() {}
};

class CreditCardPayment : public PaymentStrategy {
public:
    bool processPayment(double amount) override;
};

// ===================================
// == MAIN CONTROLLER (FACADE) ==
// ===================================
// ParkingLot poore system ko manage karta hai
class ParkingLot {
private:
    vector<ParkingFloor*> floors;
    map<string, ParkingTicket*> activeTickets;
    mutex mtx; // Concurrency control ke liye

public:
    ParkingLot(int numFloors);
    ~ParkingLot();
    
    // Gaadi ke aane ka process
    ParkingTicket* entry(Vehicle* vehicle);
    
    // Gaadi ke jaane ka process
    double exit(string ticketId, PaymentStrategy* paymentStrategy);
    
    // Fee calculate karna
    double calculateFee(ParkingTicket* ticket);
};


// main function jahan se program shuru hoga
int main() {
    // Yahan par ParkingLot class ka object banakar saare operations manage kiye ja sakte hain.
    cout << "Parking Lot System Design Ready!" << endl;

    // Example Usage
    ParkingLot* myParkingLot = new ParkingLot(2);
    Car* myCar = new Car("UP70-AB1234");
    
    // Car Entry
    ParkingTicket* ticket = myParkingLot->entry(myCar);
    if(ticket) {
        cout << "Gaadi park ho gayi. Ticket ID: " << ticket->getTicketId() << endl;
    } else {
        cout << "Maaf kijiye, parking full hai." << endl;
    }
    
    // Car Exit (kuch samay baad)
    // double fee = myParkingLot->exit(ticket->getTicketId(), new CreditCardPayment());
    // cout << "Total fee: " << fee << endl;
    
    delete myParkingLot;
    delete myCar;
    // delete ticket;

    return 0;
}

```

---


### 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * **Users:** Register kar sakte hain aur unka ek reputation score hoga.
      * **Questions:** Users ek title aur body ke saath sawaal post kar sakte hain.
      * **Answers:** Doosre users in sawaalon ke jawab de sakte hain.
      * **Comments:** Users questions aur answers dono par chhoti tippani (comment) kar sakte hain.
      * **Voting:** Users questions aur answers ko **upvote** ya **downvote** kar sakte hain, jisse author ki reputation par asar padta hai.
      * **Accept Answer:** Sawaal poochhne wala user kisi ek jawab ko "accepted" mark kar sakta hai.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Scalability:** System ko laakhon users aur posts handle karne ke liye scalable hona chahiye.
      * **Concurrency:** Ek hi samay par hazaron users voting, posting, aur commenting kar rahe honge, system ko ise handle karna aana chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Yeh ek basic design hai. Tags, searching, aur advanced reputation logic jaise features abhi scope se bahar hain.

-----

### 2. Mukhya Objects (Core Objects)

1.  **`User`:**

      * **Attributes:** `userId`, `username`, `reputation`.
      * **Methods:** `postQuestion()`, `postAnswer()`, `addComment()`, `voteOnContent()`.

2.  **`Content` (Abstract Class):**

      * Yeh ek base class hai taaki Question, Answer, aur Comment mein code repeat na ho.
      * **Attributes:** `contentId`, `author` (User\*), `text`, `voteCount`, `timestamp`.
      * **Methods:** `upvote()`, `downvote()`.

3.  **`Question` (Content se Inherited):**

      * **Attributes:** `title`, `vector<Answer*> answers`, `Answer* acceptedAnswer`.
      * **Methods:** `addAnswer()`, `acceptAnswer()`.

4.  **`Answer` (Content se Inherited):**

      * **Attributes:** `bool isAccepted`.

5.  **`Comment` (Content se Inherited):**

      * **Attributes:** Iske paas koi extra attribute nahi hoga.

6.  **`QASystem` (Main Controller):**

      * **Attributes:** `map<int, User*> users`, `map<int, Question*> questions`.
      * **Methods:** `registerUser()`, `postQuestion()`, `postAnswer()`.

-----

### 3. Classes ke Beech Rishte (Relationships)

  * **Inheritance:**
      * `Question`, `Answer`, `Comment` **is-a** `Content`.
  * **Composition:**
      * `Question` **has-many** `Answer`s.
  * **Association:**
      * `User` posts `Content`.
      * `Answer` ek `Question` se juda hota hai.

-----

### 4. Data Storage

  * Yeh ek bada system hai, isliye iske liye ek mazboot **database** (jaise PostgreSQL ya MySQL) zaroori hai.
  * High traffic data jaise votes ke liye **NoSQL database** aur fast access ke liye **caching** (Redis/Memcached) ka istemal kiya jaana chahiye. Is design mein hum sab kuch in-memory rakhenge.

-----

### 5. Concurrency

  * System mein high concurrency hogi. `voteCount` jaise data ko update karna **atomic** hona chahiye.
  * Real-world system mein iske liye database transactions ya **locks (`std::mutex`)** ka istemal hota hai taaki ek hi post par do log ek saath vote karein toh count galat na ho.

-----

### 6. Scalability

  * System ko scale karne ke liye **load balancers**, **database sharding**, aur **caching** jaisi techniques zaroori hongi. Yeh design ek single-node concept par focus karta hai.

-----

### 7. Galtiyon ko Sambhalna (Error Handling)

  * User apni hi post par vote nahi kar sakta.
  * User kisi aur ke sawaal ka answer accept nahi kar sakta.
  * Sawaal ka title khaali nahi ho sakta.

-----

### 8. Design ke Siddhant (Principles)

  * **Single Responsibility Principle (SRP):** Har class ka kaam bata hua hai. `User` user actions, `Question` apne answers, aur `QASystem` poora flow manage karta hai.
  * **Open/Closed Principle (OCP):** `Content` ki abstract class banane se hum भविष्य mein naye type ke content (jaise `Poll`) aasani se add kar sakte hain bina puraane code ko badle.

-----

### 9. APIs

  * Ek real-world system mein REST APIs honge:
      * `POST /questions`: Naya sawaal post karne ke liye.
      * `POST /questions/{id}/answers`: Jawab post karne ke liye.
      * `POST /content/{id}/vote`: Vote karne ke liye.
      * `GET /questions/{id}`: Sawaal aur uske jawab dekhne ke liye.

-----

### Stack Overflow ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class User;
class Content;
class Question;
class Answer;
class Comment;

// ===================================
// == USER CLASS ==
// ===================================
class User {
private:
    int userId;
    string username;
    int reputation;
public:
    User(int id, string name);
    void postQuestion(string title, string text);
    void postAnswer(Question* question, string text);
    void addComment(Content* content, string text);
    void vote(Content* content, bool isUpvote);
    void displayProfile();
};

// ===================================
// == CONTENT HIERARCHY (BASE CLASS) ==
// ===================================
// Content ek abstract class hai (Question, Answer, Comment ke liye)
class Content {
protected:
    int contentId;
    User* author;
    string text;
    int voteCount;
    time_t timestamp;
public:
    Content(int id, User* author, string text);
    void applyVote(bool isUpvote);
    virtual void display() = 0; // Abstraction
    virtual ~Content() {}
};

// ===================================
// == CONCRETE CONTENT CLASSES ==
// ===================================
class Answer; // Forward declare for Question

class Question : public Content { // Inheritance
private:
    string title;
    vector<Answer*> answers;
    Answer* acceptedAnswer;
public:
    Question(int id, User* author, string title, string text);
    void addAnswer(Answer* answer);
    void acceptAnswer(Answer* answer);
    void display() override; // Polymorphism
};

class Answer : public Content {
private:
    bool isAccepted;
public:
    Answer(int id, User* author, string text);
    void markAsAccepted(bool status);
    void display() override;
};

class Comment : public Content {
public:
    Comment(int id, User* author, string text);
    void display() override;
};


// ===================================
// == MAIN CONTROLLER CLASS ==
// ===================================
class QASystem {
private:
    map<int, User*> users;
    map<int, Question*> questions;
public:
    ~QASystem();
    void registerUser(int id, string name);
    void postNewQuestion(int userId, string title, string text);
    void postNewAnswer(int userId, int questionId, string text);
    void voteOnContent(int userId, int contentId, bool isUpvote); // Simplified
    void displayQuestion(int questionId);
};


// main function jahan se program shuru hoga
int main() {
    // Yahan par QASystem class ka object banakar saare operations manage kiye ja sakte hain.
    cout << "Stack Overflow (Q&A System) Design Ready!" << endl;

    // Example Usage
    QASystem* stackOverflow = new QASystem();
    stackOverflow->registerUser(1, "Amit");
    stackOverflow->registerUser(2, "Babita");
    
    stackOverflow->postNewQuestion(1, "C++ mein Polymorphism kya hai?", "Mujhe runtime polymorphism samjhna hai.");
    stackOverflow->postNewAnswer(2, 1, "Virtual functions ka istemal karke runtime polymorphism achieve hota hai.");

    cout << "\n--- Sawaal Dekhein ---" << endl;
    stackOverflow->displayQuestion(0); // Assuming first question has ID 0

    delete stackOverflow;
    return 0;
}
```

---
Ek vending machine ka core design **State Design Pattern** ka istemal karke banaya jaata hai. Ismein mukhya class `VendingMachine` hoti hai, jo apni vartaman sthiti (current state) ke hisaab se alag-alag behave karti hai. Yeh states (jaise `NoCoinState`, `HasCoinState`) ek abstract base class `VendingMachineState` se inherit hoti hain, aur `Item` aur `Inventory` jaisi helper classes system ko poora karti hain.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * Machine sikke (coins) accept karegi.
      * User ek product chun sakega.
      * Agar aavashyak shartein (paryapt paise, stock mein item) poori hoti hain, toh machine product dispense karegi.
      * Machine bache hue paise (change) wapas karegi.
      * User transaction cancel kar sakega.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Reliability:** Machine crash nahi honi chahiye aur लेन-देन (transactions) sahi dhang se poora hona chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Yeh design ek single user-at-a-time model par aadharit hai.
      * Machine sirf coins leti hai, card ya online payment nahi.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`Item`:**

      * **Attributes:** `itemId`, `name`, `price`.
      * Yeh machine mein rakhe ek product ko represent karta hai.

2.  **`Inventory`:**

      * **Attributes:** `map<Item*, int> itemStock` (har item ki kitni quantity hai).
      * **Methods:** `addItem()`, `deductItem()`, `isAvailable()`. Yeh saare items ke stock ko manage karta hai.

3.  **`VendingMachineState` (Abstract Class):**

      * Yeh machine ki alag-alag states (avasthayein) ke liye ek blueprint (template) hai.
      * **Methods:** `insertCoin()`, `selectProduct()`, `dispenseProduct()`, `cancelTransaction()`. Yeh sabhi **pure virtual** honge (**Abstraction**).

4.  **Concrete States (Jaise `NoCoinState`, `HasCoinState`, `SoldState`):**

      * Yeh `VendingMachineState` se inherit karenge (**Inheritance**).
      * Har state in methods ko apne hisaab se implement karega. Jaise, `NoCoinState` mein `selectProduct` kaam nahi karega, jabki `HasCoinState` mein karega (**Polymorphism**).

5.  **`VendingMachine` (Main Controller / Context):**

      * **Attributes:** `VendingMachineState* currentState`, `Inventory* inventory`, `double currentBalance`.
      * **Methods:** `insertCoin()`, `selectProduct()`. Yeh methods apne `currentState` object ko kaam delegate karte hain.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Composition:** `VendingMachine` **has-an** `Inventory` aur sabhi possible states ke instances.
  * **Inheritance:** `NoCoinState`, `HasCoinState`, etc. **is-a** `VendingMachineState`.
  * **Association:** `VendingMachine` ek samay par ek hi `currentState` se juda hota hai, aur yeh state badalti rehti hai.

-----

### \#\# 4. Data Storage

  * Saara data, jaise inventory aur current balance, **in-memory** store hota hai. Ek real-world connected machine mein, yeh data ek central server ke saath sync ho sakta hai.

-----

### \#\# 5. Concurrency

  * Yeh design single-user ke liye hai, isliye concurrency ek chinta ka vishay nahi hai. Ek samay par ek hi vyakti machine ka istemal kar raha hai.

-----

### \#\# 6. Scalability

  * Yeh design ek machine ke liye hai. Agar bahut saari machines ko manage karna ho, toh ek central `VendingMachineManager` service banani padegi jo sabhi machines ki inventory aur sales ko monitor kare.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * **Paisa nahi daala:** User bina paise daale product select karta hai.
  * **Kam paise:** User product ke daam se kam paise daalta hai.
  * **Out of Stock:** User aisa product chunta hai jo stock mein nahi hai.
  * **State Design Pattern** in sabhi cases ko aasani se handle karta hai, kyunki har state mein har action ka ek defined behavior hota hai.

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **State Design Pattern:** Yeh is design ka mukhya pattern hai. Yeh object (machine) ko apni internal state badalne par apna behavior badalne ki anumati deta hai. Isse code saaf rehta hai aur `if-else` ki lambi chains se bacha jaata hai.
  * **Single Responsibility Principle (SRP):** Har state class sirf us state ke behavior ke liye zimmedar hai. `Inventory` sirf stock manage karti hai.
  * **Open/Closed Principle (OCP):** Agar भविष्य mein ek nayi state (jaise `MaintenanceState`) jodna ho, toh hum ek nayi class bana sakte hain bina puraane state classes ko chhede.

-----

### \#\# 9. APIs

  * Vending machine ka public "API" uske physical buttons hain, jinko hum in methods se represent karte hain:
      * `void insertCoin(double amount)`
      * `void selectProduct(int itemId)`
      * `void pressCancel()`

-----

### \#\# Vending Machine ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class VendingMachine;
class VendingMachineState;
class Item;

// ===================================
// == ENCAPSULATION (Core Components) ==
// ===================================
// Item class, machine ke andar rakhe product ko represent karti hai.
class Item {
private:
    int itemId;
    string name;
    double price;
public:
    Item(int id, string name, double price);
    int getId();
    string getName();
    double getPrice();
};

// Inventory class, saare items ke stock ko manage karti hai.
class Inventory {
private:
    map<Item*, int> itemStock; // Kaunsa item kitna hai
public:
    void addItem(Item* item, int quantity);
    void deductItem(Item* item);
    int getStockCount(Item* item);
};

// ===================================
// == ABSTRACTION & INHERITANCE (State Pattern Base) ==
// ===================================
// VendingMachineState ek abstract class hai. Yeh machine ki alag-alag states ka blueprint hai.
class VendingMachineState {
public:
    // Pure virtual functions (Abstraction).
    // Har state ko in actions ka jawab dena hoga.
    virtual void insertCoin(VendingMachine* machine, double amount) = 0;
    virtual void selectProduct(VendingMachine* machine, Item* item) = 0;
    virtual void dispenseProduct(VendingMachine* machine) = 0;
    virtual ~VendingMachineState() {} // Virtual destructor
};

// ===================================
// == INHERITANCE & POLYMORPHISM (Concrete States) ==
// ===================================
// Har specific state VendingMachineState se inherit ho rahi hai.

// Jab machine mein paise nahi hain.
class NoCoinState : public VendingMachineState {
public:
    void insertCoin(VendingMachine* machine, double amount) override;
    void selectProduct(VendingMachine* machine, Item* item) override;
    void dispenseProduct(VendingMachine* machine) override;
};

// Jab machine mein paise daal diye gaye hain.
class HasCoinState : public VendingMachineState {
public:
    void insertCoin(VendingMachine* machine, double amount) override;
    void selectProduct(VendingMachine* machine, Item* item) override;
    void dispenseProduct(VendingMachine* machine) override;
};

// Jab product bik chuka hai aur dispense hone wala hai.
class SoldState : public VendingMachineState {
public:
    void insertCoin(VendingMachine* machine, double amount) override;
    void selectProduct(VendingMachine* machine, Item* item) override;
    void dispenseProduct(VendingMachine* machine) override;
};

// ===================================
// == MAIN CONTROLLER CLASS (Context for State Pattern) ==
// ===================================
// VendingMachine class poori machine ko manage karti hai.
class VendingMachine {
private:
    VendingMachineState* currentState;
    Inventory* inventory;
    double currentBalance;
    // Machine apni sabhi possible states ko hold karegi
    VendingMachineState* noCoinState;
    VendingMachineState* hasCoinState;
    VendingMachineState* soldState;

public:
    VendingMachine();
    ~VendingMachine();
    
    // User actions jo state par delegate honge
    void insertCoin(double amount);
    void selectProduct(Item* item);
    
    // Internal helper methods
    void setState(VendingMachineState* state);
    void addToBalance(double amount);
    double getBalance();
    void dispenseProduct(); // Helper to be called by SoldState
    
    // State classes ko access dene ke liye getters
    VendingMachineState* getNoCoinState();
    VendingMachineState* getHasCoinState();
    VendingMachineState* getSoldState();
    Inventory* getInventory();
};

// main function jahan se program shuru hoga
int main() {
    // Yahan par VendingMachine ka object banakar system ko chalaya ja sakta hai.
    cout << "Vending Machine System Design Ready!" << endl;
    return 0;
}
```

---
Ek logging framework ka core design teen mukhya components par aadharit hota hai: **Loggers**, **Appenders**, aur **Formatters**. Application **Logger** ka istemal karke log messages bhejti hai. Logger in messages ko ek ya ek se adhik **Appenders** ko bhejta hai, jo log ko aakhiri manzil (jaise console ya file) tak likhne ke liye zimmedar hote hain. Likhne se pehle, har message ko ek **Formatter** ke zariye ek aavashyak format (jaise timestamp add karna) mein badla jaata hai.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * Alag-alag severity levels par messages log karna (jaise `DEBUG`, `INFO`, `WARN`, `ERROR`).
      * Run-time par log level set karne ki suvidha (jaise, production mein sirf `INFO` aur usse upar ke logs dikhana).
      * Logs ko ek saath multiple jagahon par bhejna (jaise, console par bhi aur ek file mein bhi).
      * Log message ke format ko customize karna (jaise, `[TIMESTAMP] [LEVEL]: MESSAGE`).
      * Logger ki hierarchy (chain) banana, jahan child logger apne parent ki configuration inherit kar sake.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Performance:** Logging ka application ki main performance par bahut kam asar hona chahiye. Iske liye **asynchronous logging** ek zaroori feature hai.
      * **Thread-Safety:** Multiple threads se ek saath log karne par output corrupt nahi hona chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Hum ek library design kar rahe hain jise doosre applications istemal karenge.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`LogLevel` (Enum):**

      * Log ki severity (`DEBUG`, `INFO`, `WARN`, `ERROR`, `FATAL`) ko represent karne ke liye.

2.  **`LogMessage`:**

      * Ek log event se judi saari jaankari (level, message, timestamp, thread ID) ko ek jagah encapsulate karta hai.

3.  **`Formatter` (Abstract Class):**

      * `LogMessage` ko ek formatted string mein badalta hai.
      * **Derived Classes:** `SimpleFormatter`, `PatternFormatter`.

4.  **`Appender` (Abstract Class):**

      * Formatted string ko aakhiri manzil tak likhta hai. Ise **Strategy Pattern** ka ek roop maana ja sakta hai.
      * **Derived Classes:** `ConsoleAppender`, `FileAppender`, `NetworkAppender`.

5.  **`Logger`:**

      * Application isi class se interact karta hai.
      * **Attributes:** `name`, `LogLevel`, `vector<Appender*>`.
      * **Methods:** `debug()`, `info()`, `warn()`, `error()`.

6.  **`LogManager` (Singleton Pattern):**

      * Ek central class jo `Logger` instances ko create aur manage karti hai. Yeh sunishchit karta hai ki ek hi naam ke logger ka ek hi instance ho.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Composition:** `Logger` **has-many** `Appenders`. `Appender` **has-a** `Formatter`.
  * **Inheritance/Abstraction:**
      * `ConsoleAppender`, `FileAppender` **is-a** `Appender`.
      * `SimpleFormatter` **is-a** `Formatter`.
  * **Chain of Responsibility:** Loggers ek hierarchy mein ho sakte hain. Agar ek logger ke paas koi appender nahi hai, toh woh log message ko apne parent logger ko bhej sakta hai.

-----

### \#\# 4. Data Storage

  * Data storage ki zimmedari `Appender` ki hoti hai. `FileAppender` file mein store karta hai, `DatabaseAppender` database mein.

-----

### \#\# 5. Concurrency

  * Yeh bahut zaroori hai. **Appenders thread-safe hone chahiye.**
  * `FileAppender` jaise shared resource ko access karte samay **`std::mutex`** ka istemal karna zaroori hai taaki alag-alag threads se aane wale messages aapas mein mix na ho jayein.
  * High performance ke liye, **asynchronous logging** ka design banaya jaata hai, jahan application threads messages ko ek thread-safe queue mein daal dete hain aur ek alag background thread unhe likhne ka kaam karta hai.

-----

### \#\# 6. Scalability

  * Yeh design naye appenders aur formatters add karke aasani se scale kiya ja sakta hai (**Open/Closed Principle**).
  * Bade distributed systems ke liye, ek `NetworkAppender` banaya ja sakta hai jo logs ko ek central logging server (jaise ELK Stack ya Splunk) par bhejta hai.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * Ek logging framework ko kabhi bhi main application ko crash nahi karna chahiye.
  * Agar log file nahi khul paati hai, toh `FileAppender` ko chup-chaap fail ho jaana chahiye ya console par ek error message de dena chahiye.

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Single Responsibility Principle (SRP):** Har component ka ek hi kaam hai: `Logger` message leta hai, `Appender` likhta hai, aur `Formatter` format karta hai.
  * **Open/Closed Principle (OCP):** Hum naye appenders aur formatters add kar sakte hain bina `Logger` class ko badle.
  * **Dependency Inversion Principle:** `Logger` concrete classes jaise `FileAppender` par nahi, balki `Appender` abstract class par depend karta hai.

-----

### \#\# 9. APIs

  * Framework ka istemal karne wale developer ke liye mukhya API `Logger` class hai:
      * `logger->info("User logged in successfully.");`
      * `logger->error("Database connection failed.");`
  * Logger paane ke liye API `LogManager` provide karta hai:
      * `Logger* logger = LogManager::getLogger("my-app");`

-----

### \#\# Logging Framework ka C++ Code

```cpp
#include <bits/stdc++.h>
#include <mutex> // For thread safety
using namespace std;

// Log ki severity levels
enum class LogLevel { DEBUG, INFO, WARN, ERROR, FATAL };

// Ek log event ki saari jaankari
class LogMessage {
public:
    LogLevel level;
    string message;
    // Yahan timestamp, thread_id etc. bhi ho sakte hain
};

// ===================================
// == FORMATTER HIERARCHY ==
// ===================================
class Formatter {
public:
    virtual string format(const LogMessage& msg) = 0;
    virtual ~Formatter() {}
};

class SimpleFormatter : public Formatter {
public:
    string format(const LogMessage& msg) override {
        // Simple format: [LEVEL] message
        string levelStr;
        switch (msg.level) {
            case LogLevel::INFO: levelStr = "INFO"; break;
            case LogLevel::WARN: levelStr = "WARN"; break;
            case LogLevel::ERROR: levelStr = "ERROR"; break;
            default: levelStr = "DEBUG"; break;
        }
        return "[" + levelStr + "] " + msg.message;
    }
};

// ===================================
// == APPENDER HIERARCHY (STRATEGY PATTERN) ==
// ===================================
// Appender ek abstract class hai jo batata hai ki log kahan likha jaayega
class Appender {
protected:
    Formatter* formatter;
    mutex mtx; // Har appender thread-safe hona chahiye
public:
    Appender(Formatter* fmt) : formatter(fmt) {}
    virtual void write(const LogMessage& msg) = 0;
    virtual ~Appender() { delete formatter; }
};

class ConsoleAppender : public Appender {
public:
    ConsoleAppender(Formatter* fmt) : Appender(fmt) {}
    void write(const LogMessage& msg) override {
        lock_guard<mutex> lock(mtx); // Mutex lock
        cout << formatter->format(msg) << endl;
    }
};

class FileAppender : public Appender {
private:
    ofstream logFile;
public:
    FileAppender(Formatter* fmt, const string& filename) : Appender(fmt) {
        logFile.open(filename, ios::app);
    }
    void write(const LogMessage& msg) override {
        lock_guard<mutex> lock(mtx);
        if (logFile.is_open()) {
            logFile << formatter->format(msg) << endl;
        }
    }
};

// ===================================
// == LOGGER CLASS ==
// ===================================
// Application is class ke through log karti hai
class Logger {
private:
    string name;
    LogLevel minLevel;
    vector<Appender*> appenders;
public:
    Logger(string name) : name(name), minLevel(LogLevel::DEBUG) {}
    ~Logger() {
        for(auto appender : appenders) delete appender;
    }

    void addAppender(Appender* appender) {
        appenders.push_back(appender);
    }
    void setMinLevel(LogLevel level) {
        minLevel = level;
    }

    void log(LogLevel level, const string& message) {
        if (level >= minLevel) {
            LogMessage msg{level, message};
            for (auto& appender : appenders) {
                appender->write(msg);
            }
        }
    }
    // Helper methods
    void info(const string& message) { log(LogLevel::INFO, message); }
    void warn(const string& message) { log(LogLevel::WARN, message); }
    void error(const string& message) { log(LogLevel::ERROR, message); }
};

// ===================================
// == LOG MANAGER (SINGLETON) ==
// ===================================
class LogManager {
public:
    static Logger& getLogger() {
        // Simple singleton implementation for demonstration
        static Logger instance("root");
        return instance;
    }
private:
    LogManager() {} // private constructor
};

// main function jahan se framework ka istemal dikhaya gaya hai
int main() {
    // Framework ko configure karna
    Logger& logger = LogManager::getLogger();
    logger.setMinLevel(LogLevel::INFO); // Sirf INFO aur usse upar ke logs dikhao

    // Ek appender banate hain jo console par log karega
    logger.addAppender(new ConsoleAppender(new SimpleFormatter()));
    
    // Ek aur appender banate hain jo file mein log karega
    logger.addAppender(new FileAppender(new SimpleFormatter(), "app.log"));

    // Application ab log karna shuru kar sakti hai
    cout << "Logging framework istemal kiya ja raha hai..." << endl;
    logger.info("User 'Amit' ne login kiya.");
    logger.warn("Disk space kam ho raha hai.");
    logger.error("Database se connection fail ho gaya.");
    
    // Yeh log nahi dikhega kyunki minLevel INFO hai
    logger.log(LogLevel::DEBUG, "Yeh ek debug message hai.");

    cout << "Logs console aur app.log file mein check karein." << endl;

    return 0;
}
```

---
Ek coffee vending machine ka design do mukhya design patterns ka istemal karke banaya jaata hai: **State Pattern** machine ki alag-alag avasthayein (states) jaise 'paise daalna' ya 'coffee banana' manage karne ke liye, aur **Decorator Pattern** alag-alag tarah ki coffee (jaise Espresso, Latte) banane ke liye. Core classes mein `CoffeeMachine` (main controller), `MachineState` (abstract state), `Beverage` (abstract coffee), aur `Milk`, `Sugar` jaise decorators shamil hain.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * Machine alag-alag coffee bana sakti hai: **Espresso** (base), **Latte** (Espresso + Milk), **Cappuccino**.
      * Users extra cheezein jaise **Sugar** add kar sakte hain.
      * Machine paise accept karegi.
      * User apni pasand ki coffee select karega.
      * Machine check karegi ki paryapt paise daale gaye hain aur ingredients (coffee, milk, etc.) maujood hain.
      * Machine coffee dispense karegi aur bache hue paise wapas karegi.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Reliability:** Machine ko har transaction ko sahi dhang se poora karna chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Yeh ek single-user-at-a-time machine hai.
      * Hum coffee banane aur machine ki state manage karne ke logic par focus kar rahe hain.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`Beverage` (Abstract Class - Decorator Pattern ka base):**

      * Yeh kisi bhi pey padarth (beverage) ka base hai.
      * **Methods:** `getDescription()`, `getCost()` (dono pure virtual).

2.  **`Espresso` (Concrete Beverage):**

      * Yeh `Beverage` se inherit karta hai aur hamari base coffee hai.

3.  **`CondimentDecorator` (Abstract Decorator):**

      * Yeh `Beverage` se inherit karta hai. Iska kaam base coffee mein extra cheezein (milk, sugar) "decorate" karna hai.
      * **Attributes:** `Beverage* beverage` (jise decorate kiya ja raha hai).

4.  **`Milk`, `Sugar` (Concrete Decorators):**

      * Yeh `CondimentDecorator` se inherit karte hain. `Milk` `getDescription()` mein "+ Milk" jod dega aur `getCost()` mein milk ka daam jod dega.

5.  **`CoffeeMachineState` (Abstract Class - State Pattern ka base):**

      * Yeh machine ki states ka blueprint hai.
      * **Methods:** `insertMoney()`, `selectBeverage()`, `dispense()` (sabhi pure virtual).

6.  **Concrete States (`IdleState`, `CollectingMoneyState`):**

      * Yeh `CoffeeMachineState` se inherit karte hain aur har state ke anusaar alag-alag behavior define karte hain.

7.  **`Inventory`:**

      * **Attributes:** Ingredients ka stock (coffee beans, milk, sugar).
      * **Methods:** `checkAvailability()`, `useIngredients()`.

8.  **`CoffeeMachine` (Main Controller):**

      * **Attributes:** `CoffeeMachineState* currentState`, `Inventory* inventory`, `double currentBalance`.
      * Poori machine ke flow ko control karta hai.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **State Pattern:** `CoffeeMachine` **has-a** `CoffeeMachineState`. Concrete states **are-a** `CoffeeMachineState`.
  * **Decorator Pattern:** `CondimentDecorator` **is-a** `Beverage` aur **has-a** `Beverage`. `Milk` **is-a** `CondimentDecorator`.
  * **Composition:** `CoffeeMachine` **has-an** `Inventory`.

-----

### \#\# 4. Data Storage

  * Saara data (inventory, current balance) **in-memory** rahega.

-----

### \#\# 5. Concurrency

  * Ek samay par ek hi user machine istemal karega, isliye concurrency ek badi chinta nahi hai.

-----

### \#\# 6. Scalability

  * **Decorator Pattern** ki vajah se nayi coffee types ya naye add-ons (jaise Caramel syrup) jodna bahut aasan hai. Sirf ek nayi decorator class banani padegi.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * **Kam paise:** Machine check karegi ki daale gaye paise coffee ke daam se zyada ya barabar hain.
  * **Ingredients khatm:** Coffee banane se pehle machine inventory check karegi.
  * In sabhi scenarios ko State Pattern ke zariye alag-alag states mein handle kiya jaata hai.

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **State Design Pattern:** Machine ke behavior ko uski state ke anusaar badalta hai. Yeh `if-else` ki jagah ek saaf-suthra solution hai.
  * **Decorator Pattern:** Bina base classes ko badle, runtime par objects mein nayi functionality (jaise milk, sugar) add karne ki suvidha deta hai.
  * **Open/Closed Principle (OCP):** Hum nayi states aur naye condiments add kar sakte hain bina maujooda code ko badle.

-----

### \#\# 9. APIs

  * Machine ka public API uske physical buttons ko represent karta hai:
      * `void insertMoney(double amount)`
      * `void selectBeverage(BeverageType type, list<CondimentType> condiments)`
      * `void pressDispenseButton()`

-----

### \#\# Coffee Vending Machine ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// ===================================
// == BEVERAGE HIERARCHY (DECORATOR PATTERN) ==
// ===================================
// Base class for all beverages
class Beverage {
public:
    virtual string getDescription() = 0;
    virtual double getCost() = 0;
    virtual ~Beverage() {}
};

// Concrete base beverage
class Espresso : public Beverage {
public:
    string getDescription() override { return "Espresso"; }
    double getCost() override { return 50.0; }
};

// Abstract decorator for condiments
class CondimentDecorator : public Beverage {
protected:
    Beverage* beverage;
public:
    CondimentDecorator(Beverage* b) : beverage(b) {}
    ~CondimentDecorator() { delete beverage; }
};

// Concrete decorators
class Milk : public CondimentDecorator {
public:
    Milk(Beverage* b) : CondimentDecorator(b) {}
    string getDescription() override { return beverage->getDescription() + ", Milk"; }
    double getCost() override { return beverage->getCost() + 15.0; }
};

class Sugar : public CondimentDecorator {
public:
    Sugar(Beverage* b) : CondimentDecorator(b) {}
    string getDescription() override { return beverage->getDescription() + ", Sugar"; }
    double getCost() override { return beverage->getCost() + 5.0; }
};

// ===================================
// == STATE MACHINE HIERARCHY (STATE PATTERN) ==
// ===================================
class CoffeeMachine; // Forward declaration

class CoffeeMachineState {
public:
    virtual void insertMoney(CoffeeMachine* machine, double amount) = 0;
    virtual void selectBeverage(CoffeeMachine* machine, Beverage* beverage) = 0;
    virtual void dispense(CoffeeMachine* machine) = 0;
    virtual ~CoffeeMachineState() {}
};

class IdleState : public CoffeeMachineState {
public:
    void insertMoney(CoffeeMachine* machine, double amount) override;
    void selectBeverage(CoffeeMachine* machine, Beverage* beverage) override;
    void dispense(CoffeeMachine* machine) override;
};

class CollectingMoneyState : public CoffeeMachineState {
public:
    void insertMoney(CoffeeMachine* machine, double amount) override;
    void selectBeverage(CoffeeMachine* machine, Beverage* beverage) override;
    void dispense(CoffeeMachine* machine) override;
};
// ... (DispensingState, etc. can be added)


// ===================================
// == MAIN CONTROLLER CLASS (CONTEXT) ==
// ===================================
class CoffeeMachine {
private:
    CoffeeMachineState* currentState;
    double currentBalance;
    Beverage* selectedBeverage;
    // States
    CoffeeMachineState* idleState;
    CoffeeMachineState* collectingMoneyState;
public:
    CoffeeMachine();
    ~CoffeeMachine();

    // User actions delegate to the current state
    void insertMoney(double amount) { currentState->insertMoney(this, amount); }
    void selectBeverage(Beverage* beverage) { currentState->selectBeverage(this, beverage); }
    void dispense() { currentState->dispense(this); }

    // Helper methods for states to use
    void setState(CoffeeMachineState* state) { currentState = state; }
    void addToBalance(double amount) { currentBalance += amount; }
    double getBalance() { return currentBalance; }
    void setSelectedBeverage(Beverage* b) { selectedBeverage = b; }
    Beverage* getSelectedBeverage() { return selectedBeverage; }
    CoffeeMachineState* getIdleState() { return idleState; }
    CoffeeMachineState* getCollectingMoneyState() { return collectingMoneyState; }
};

// State implementations (simplified)
void IdleState::insertMoney(CoffeeMachine* machine, double amount) {
    cout << "Aapne " << amount << " rupaye daale." << endl;
    machine->addToBalance(amount);
    machine->setState(machine->getCollectingMoneyState());
}
void IdleState::selectBeverage(CoffeeMachine* machine, Beverage* beverage) {
    cout << "Pehle paise daalein." << endl;
    delete beverage; // Clean up unused beverage
}
void IdleState::dispense(CoffeeMachine* machine) {
    cout << "Pehle paise daalein aur beverage select karein." << endl;
}

void CollectingMoneyState::insertMoney(CoffeeMachine* machine, double amount) {
    cout << "Aapne aur " << amount << " rupaye daale." << endl;
    machine->addToBalance(amount);
}
void CollectingMoneyState::selectBeverage(CoffeeMachine* machine, Beverage* beverage) {
    cout << "Aapne " << beverage->getDescription() << " select kiya hai." << endl;
    machine->setSelectedBeverage(beverage);
}
void CollectingMoneyState::dispense(CoffeeMachine* machine) {
    Beverage* beverage = machine->getSelectedBeverage();
    if (!beverage) {
        cout << "Pehle beverage select karein." << endl;
        return;
    }
    if (machine->getBalance() >= beverage->getCost()) {
        cout << "Dispensing " << beverage->getDescription() << ". Anand lein!" << endl;
        // Logic to return change
        machine->setState(machine->getIdleState());
    } else {
        cout << "Kam paise hain. Aur paise daalein." << endl;
    }
}
// Note: Full implementation of constructor/destructor is omitted for brevity.


// main function jahan se program shuru hoga
int main() {
    cout << "Coffee Machine System Design Ready!" << endl;
    
    CoffeeMachine machine;
    
    // Scenario 1: Latte banana
    cout << "\n--- Latte ka Order ---" << endl;
    machine.insertMoney(100.0);
    
    // Decorator pattern in action
    Beverage* latte = new Espresso();
    latte = new Milk(latte);
    
    machine.selectBeverage(latte);
    machine.dispense();
    
    return 0;
}
```

---

Ek task management system jaise Trello ya Jira ka core design **Boards**, **Lists** (columns), aur **Tasks** (cards) par kendrit hota hai. Ismein `Board` ek container ki tarah kaam karta hai, jiske andar `TaskList` (jaise "To Do", "In Progress") hote hain. Har list ke andar alag-alag `Task` hote hain, jinhe ek `User` se doosre `User` ko assign kiya ja sakta hai aur ek list se doosri mein move kiya ja sakta hai.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * Users naye **Boards** bana sakte hain.
      * Har board mein multiple **Lists** (columns) ho sakti hain.
      * Users lists ke andar **Tasks** (cards) bana sakte hain.
      * Har task ka ek title, description, assignee, aur due date hota hai.
      * Users tasks ko ek list se doosri list mein drag-and-drop (move) kar sakte hain.
      * Alag-alag type ke tasks ho sakte hain, jaise `Story`, `Bug`, `SimpleTask`.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Collaboration:** Multiple users ko ek hi board par ek saath kaam karne ki suvidha honi chahiye.
      * **Data Persistence:** Boards aur tasks ka data save hona chahiye, taaki application band karke kholne par data delete na ho.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Hum system ke core backend logic par focus kar rahe hain, UI par nahi.
      * Ek user multiple boards ka hissa ho sakta hai.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`User`:**

      * **Attributes:** `userId`, `name`, `email`.

2.  **`Task` (Abstract Class):**

      * Yeh sabhi task types ke liye ek base class hai.
      * **Attributes:** `taskId`, `title`, `description`, `assignee` (User\*), `dueDate`.
      * **Methods:** `updateStatus()`, `assignTo()`. Ismein ek pure virtual method `getType()` hoga (**Abstraction**).

3.  **Concrete Tasks (`Story`, `Bug`):**

      * Yeh `Task` se inherit karenge (**Inheritance**).
      * Inke apne extra attributes ho sakte hain, jaise `Story` ke liye `storyPoints` ya `Bug` ke liye `severity`. Yeh `getType()` ko implement karenge (**Polymorphism**).

4.  **`TaskList` (Ya Column):**

      * **Attributes:** `listId`, `name` (jaise "To Do"), `vector<Task*> tasks`.
      * **Methods:** `addTask()`, `removeTask()`.

5.  **`Board`:**

      * **Attributes:** `boardId`, `name`, `vector<TaskList*> lists`, `vector<User*> members`.
      * **Methods:** `addList()`, `addUser()`, `moveTask()`.

6.  **`TaskManager` (Main Controller):**

      * Poore system ko manage karne ke liye ek central class.
      * **Attributes:** `map<int, Board*> boards`, `map<int, User*> users`.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Composition:**
      * `Board` **has-many** `TaskList`s.
      * `TaskList` **has-many** `Task`s.
  * **Inheritance:**
      * `Story` aur `Bug` **is-a** `Task`.
  * **Association:**
      * `User` ek `Board` ka **member** hota hai.
      * `Task` ek `User` ko **assign** hota hai.

-----

### \#\# 4. Data Storage

  * Ek real-world system ke liye **database** zaroori hai. Iske flexible nature ke kaaran NoSQL database (jaise MongoDB) ek accha vikalp ho sakta hai.
  * Is LLD mein, hum data ko in-memory store karenge.

-----

### \#\# 5. Concurrency

  * Yeh ek collaborative tool hai, isliye concurrency bahut zaroori hai. Agar do users ek hi task ko ek saath move karne ki koshish karte hain, toh system ko data inconsistency se bachna hoga.
  * `moveTask` jaise critical operations ko **atomic** banane ke liye **locks (`std::mutex`)** ya database transactions ka istemal kiya jaana chahiye.

-----

### \#\# 6. Scalability

  * System ko laakhon users aur boards ke liye scalable hona chahiye. Iske liye distributed architecture, **load balancers**, **database sharding**, aur **caching** ka istemal hoga.
  * Real-time updates (jab ek user card move karta hai aur doosre ko dikhta hai) ke liye **WebSockets** ka istemal kiya jaata hai.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * User ek aise task ko move karne ki koshish karta hai jo exist nahi karta.
  * User ek task aise user ko assign karta hai jo board ka member nahi hai.
  * Invalid state transition (jaise "Done" se wapas "To Do" mein task move karna, agar workflow allow na kare).

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Single Responsibility Principle (SRP):** Har class ka ek kaam hai. `Board` lists manage karta hai, `TaskList` tasks manage karti hai.
  * **Open/Closed Principle (OCP):** `Task` ki abstract class banane se hum भविष्य mein naye task types (jaise `Epic`) aasani se add kar sakte hain bina `Board` ya `TaskList` class ko badle.

-----

### \#\# 9. APIs

  * Ek real-world system mein REST APIs honge:
      * `POST /boards`: Naya board banane ke liye.
      * `POST /lists/{listId}/tasks`: Naya task banane ke liye.
      * `PUT /tasks/{taskId}`: Task ko update karne ke liye (jaise list badalna).

-----

### \#\# Task Management System ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class User;
class Task;
class TaskList;
class Board;

enum class TaskType { SIMPLE, STORY, BUG };

// ===================================
// == TASK HIERARCHY ==
// ===================================
// Task ek abstract class hai
class Task {
protected:
    int taskId;
    string title;
    string description;
    User* assignee;
public:
    Task(int id, string title, string desc);
    void assignTo(User* user);
    virtual void display() = 0; // Abstraction
    virtual TaskType getType() = 0;
    virtual ~Task() {}
};

class SimpleTask : public Task { // Inheritance
public:
    SimpleTask(int id, string title, string desc);
    void display() override; // Polymorphism
    TaskType getType() override;
};

class Story : public Task {
private:
    int storyPoints;
public:
    Story(int id, string title, string desc, int points);
    void display() override;
    TaskType getType() override;
};

// ===================================
// == CORE CLASSES ==
// ===================================
class User {
private:
    int userId;
    string name;
public:
    User(int id, string name);
    string getName();
};

class TaskList {
private:
    int listId;
    string name;
    vector<Task*> tasks;
public:
    TaskList(int id, string name);
    void addTask(Task* task);
    void removeTask(int taskId);
    void display();
};

class Board {
private:
    int boardId;
    string name;
    vector<TaskList*> lists;
    vector<User*> members;
public:
    Board(int id, string name);
    void addList(TaskList* list);
    void addUser(User* user);
    void moveTask(int taskId, int fromListId, int toListId); // Simplified
    void display();
};

// ===================================
// == MAIN CONTROLLER CLASS ==
// ===================================
class TaskManager {
private:
    map<int, Board*> boards;
    map<int, User*> users;
    // Concurrency ke liye yahan mutex lagega
    // mutex mtx;
public:
    ~TaskManager();
    void createBoard(int id, string name);
    void createUser(int id, string name);
    Board* getBoard(int boardId);
    void assignTask(int taskId, int userId);
};

// main function jahan se program shuru hoga
int main() {
    cout << "Task Management System (Trello/Jira) Design Ready!" << endl;
    
    // Yahan par TaskManager ka object banakar saare operations manage kiye ja sakte hain.
    // Example:
    TaskManager tm;
    tm.createBoard(1, "Project Alpha");
    tm.createUser(101, "Amit");
    
    Board* board = tm.getBoard(1);
    User* user = new User(101, "Amit"); // Simplified
    
    if (board) {
        board->addUser(user);
        TaskList* todoList = new TaskList(1, "To Do");
        TaskList* doneList = new TaskList(2, "Done");
        board->addList(todoList);
        board->addList(doneList);
        
        Task* task1 = new SimpleTask(1001, "Login Page banana", "UI/UX design ke saath");
        todoList->addTask(task1);
        
        cout << "\n--- Shuruaati Board State ---" << endl;
        board->display();
        
        // Task ko "To Do" se "Done" mein move karna
        board->moveTask(1001, 1, 2);
        
        cout << "\n--- Task Move Karne ke Baad ki State ---" << endl;
        board->display();
    }

    return 0;
}
```

----
Ek traffic signal control system ka sabse accha design **State Design Pattern** ka istemal karke banaya jaata hai. Iska mukhya concept yeh hai ki ek `TrafficLight` (object) ka behavior uski vartaman sthiti (current state), jaise `RedState`, `YellowState`, ya `GreenState` par nirbhar karta hai. Ek central `TrafficController` ek chaurahe (intersection) par lage sabhi `TrafficLight`s ko manage karta hai, taaki unke beech sahi samanjasya (coordination) bana rahe.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * Har traffic light teen states mein se ek mein ho sakti hai: **Red**, **Yellow**, ya **Green**.
      * Lights ek nirdharit kram (sequence) mein badalni chahiye: Green → Yellow → Red → Green...
      * Har state (rang) ek nishchit samay (duration) tak chalti hai.
      * System ko ek poore chaurahe ko control karna hoga, jismein aam taur par chaar traffic lights hoti hain.
      * System ko yeh sunishchit karna hoga ki aamne-saamne ke conflicting traffic (jaise North-South vs. East-West) ko ek hi samay par green light na mile.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Reliability:** System atyant vishvasneeya (reliable) aur fail-safe hona chahiye. Ek galti bhi badi durghatna ka kaaran ban sakti hai.
      * **Timing:** Lights ki timing bilkul sateek (precise) honi chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Hum ek saadharan (standard) char-rasta (four-way) chaurahe ke liye design bana rahe hain.
      * Lights ki timing fixed hai, yeh traffic ke anusaar badalti nahi hai (non-adaptive).

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`LightState` (Abstract Class - State Pattern ka base):**

      * Yeh kisi bhi light state ke liye ek blueprint hai.
      * **Methods:** `handleStateChange(TrafficLight* light)`, `getColor()`. Yeh **pure virtual** honge (**Abstraction**).

2.  **Concrete States (`RedState`, `YellowState`, `GreenState`):**

      * Yeh `LightState` se inherit karenge (**Inheritance**).
      * Har state in methods ko apne hisaab se implement karega. Jaise, `GreenState` ka `handleStateChange` method timer poora hone par light ko `YellowState` mein badal dega (**Polymorphism**).

3.  **`TrafficLight` (State Pattern ka Context):**

      * **Attributes:** `LightState* currentState`, `string id` (jaise "North").
      * **Methods:** `setState()`, `changeStateAfterDuration()`. Yeh apne `currentState` object ko kaam delegate karta hai.

4.  **`TrafficController` (Main Controller):**

      * **Attributes:** `map<string, TrafficLight*> lights`, `string currentGreenDirection`.
      * **Methods:** `start()`, `update()`. `update` method samay-samay par call hota hai aur poore intersection ke state ko aage badhata hai.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **State Pattern:** `TrafficLight` **has-a** `LightState`. Concrete states **are-a** `LightState`.
  * **Composition:** `TrafficController` **has-many** `TrafficLight`s.

-----

### \#\# 4. Data Storage

  * System ki configuration (jaise light ki timing) ek file se load ki ja sakti hai, lekin operation ke dauraan saari state **in-memory** rehti hai.

-----

### \#\# 5. Concurrency

  * Main control loop (`update`) ko ek hi dedicated, high-priority thread mein chalana chahiye taaki timing sateek rahe aur race conditions se bacha ja sake.

-----

### \#\# 6. Scalability

  * Ek intersection ka design scale kiya ja sakta hai. Ek `CityTrafficControlSystem` class banayi ja sakti hai jo bahut saare `TrafficController` objects ko manage kare aur shehar mein "green waves" (ek saath kai signals ka green hona) bana sake.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * **Fail-Safe State:** Agar controller crash ho jaaye, toh ek real-world system mein hardware watchdog lights ko ek safe state (jaise sabhi red ya flashing yellow) mein daal deta hai.
  * **Invalid State Transition:** State Pattern is tarah ki galtiyon ko rokta hai, kyunki har state sirf apne agle valid state ke baare mein jaanti hai.

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **State Design Pattern:** Yeh is samasya ke liye sabse behtareen pattern hai. Yeh ek traffic light ke behavior ko uski state ke andar encapsulate karta hai, jisse `TrafficLight` class ka code bahut saaf rehta hai aur `if-else`/`switch` ke jaal se bach jaata hai.
  * **Single Responsibility Principle (SRP):** `LightState` classes state-specific behavior, `TrafficLight` ek single light, aur `TrafficController` poore intersection ko manage karta hai.
  * **Open/Closed Principle (OCP):** Agar koi nayi state (jaise `FlashingRedState`) jodna ho, toh hum `LightState` se inherit karke ek nayi class bana sakte hain bina puraane code ko badle.

-----

### \#\# 9. APIs

  * System ka mukhya "API" internal hai: main loop `trafficController->update()` ko call karta hai.
  * Ek external API ho sakta hai jisse central city management system timings badal sake.

-----

### \#\# Traffic Signal Control System ka C++ Code

```cpp
#include <bits/stdc++.h>
#include <chrono>
#include <thread>
using namespace std;

// Forward Declarations
class TrafficLight;
class LightState;

// ===================================
// == STATE HIERARCHY (STATE PATTERN) ==
// ===================================
// LightState ek abstract class hai
class LightState {
public:
    // Yeh method batata hai ki samay poora hone par agla state kya hoga
    virtual void handleStateChange(TrafficLight* light) = 0;
    virtual string getColor() = 0;
    virtual ~LightState() {}
};

// TrafficLight (Context) ka forward declaration
class TrafficLight;

// Concrete States
class RedState : public LightState {
public:
    void handleStateChange(TrafficLight* light) override;
    string getColor() override { return "RED"; }
};

class YellowState : public LightState {
public:
    void handleStateChange(TrafficLight* light) override;
    string getColor() override { return "YELLOW"; }
};

class GreenState : public LightState {
public:
    void handleStateChange(TrafficLight* light) override;
    string getColor() override { return "GREEN"; }
};

// ===================================
// == CONTEXT CLASS (STATE PATTERN) ==
// ===================================
class TrafficLight {
private:
    LightState* currentState;
public:
    TrafficLight() {
        // Shuruaat mein har light red hoti hai
        currentState = new RedState();
    }
    ~TrafficLight() {
        delete currentState;
    }
    void setState(LightState* state) {
        if (currentState) delete currentState;
        currentState = state;
    }
    void changeStateAfterDuration() {
        // Current state ko aadesh do ki woh state change kare
        currentState->handleStateChange(this);
    }
    string getCurrentColor() {
        return currentState->getColor();
    }
};

// State change logic ko yahan define karte hain taaki circular dependency na ho
void RedState::handleStateChange(TrafficLight* light) {
    cout << "RED se GREEN ho raha hai..." << endl;
    light->setState(new GreenState());
}
void GreenState::handleStateChange(TrafficLight* light) {
    cout << "GREEN se YELLOW ho raha hai..." << endl;
    light->setState(new YellowState());
}
void YellowState::handleStateChange(TrafficLight* light) {
    cout << "YELLOW se RED ho raha hai..." << endl;
    light->setState(new RedState());
}


// ===================================
// == MAIN CONTROLLER CLASS ==
// ===================================
class TrafficController {
private:
    map<string, TrafficLight*> lights;
    // Timings (in seconds)
    int greenDuration = 5;
    int yellowDuration = 2;
    int redDuration = 7; // green + yellow
public:
    TrafficController() {
        lights["North"] = new TrafficLight();
        lights["South"] = new TrafficLight();
        lights["East"] = new TrafficLight();
        lights["West"] = new TrafficLight();
    }
    ~TrafficController() {
        for(auto const& [key, val] : lights) delete val;
    }

    // Chaurahe ko chalaane ka simulation
    void startSimulation() {
        cout << "Traffic Simulation Shuru!" << endl;
        // Shuruaat: North-South green, East-West red
        lights["North"]->setState(new GreenState());
        lights["South"]->setState(new GreenState());

        int time = 0;
        while (time < 30) { // 30 seconds tak simulate karo
            cout << "\n--- Samay: " << time << "s ---" << endl;
            cout << "North: " << lights["North"]->getCurrentColor() << endl;
            cout << "South: " << lights["South"]->getCurrentColor() << endl;
            cout << "East: " << lights["East"]->getCurrentColor() << endl;
            cout << "West: " << lights["West"]->getCurrentColor() << endl;
            
            // Logic to change lights based on timers (simplified)
            if (time == greenDuration) { // 5s
                lights["North"]->changeStateAfterDuration(); // Green -> Yellow
                lights["South"]->changeStateAfterDuration(); // Green -> Yellow
            }
            if (time == greenDuration + yellowDuration) { // 7s
                lights["North"]->changeStateAfterDuration(); // Yellow -> Red
                lights["South"]->changeStateAfterDuration(); // Yellow -> Red
                
                // Ab East-West ko green karo
                lights["East"]->changeStateAfterDuration(); // Red -> Green
                lights["West"]->changeStateAfterDuration(); // Red -> Green
            }
             if (time == greenDuration + yellowDuration + greenDuration) { // 12s
                lights["East"]->changeStateAfterDuration(); // Green -> Yellow
                lights["West"]->changeStateAfterDuration(); // Green -> Yellow
            }
            if (time == greenDuration + yellowDuration + greenDuration + yellowDuration) { // 14s
                lights["East"]->changeStateAfterDuration(); // Yellow -> Red
                lights["West"]->changeStateAfterDuration(); // Yellow -> Red
                // Ab wapas North-South ko green
                lights["North"]->changeStateAfterDuration(); // Red -> Green
                lights["South"]->changeStateAfterDuration(); // Red -> Green
            }
            
            this_thread::sleep_for(chrono::seconds(1));
            time++;
        }
    }
};


// main function jahan se program shuru hoga
int main() {
    TrafficController controller;
    controller.startSimulation();
    return 0;
}
```

---
Zaroor, pesh hain ATM aur LinkedIn ke liye Low-Level Designs (LLD), aapke diye gaye checklist ke anusaar.

-----

-----

## 🏧 Design ATM

Ek ATM system ka core design **State Design Pattern** par aadharit hota hai, jisse machine ki alag-alag avasthayein (states) jaise `IdleState`, `CardInsertedState`, `PinEnteredState` manage ki jaati hain. Iske alawa, alag-alag लेन-देन (transactions) ke liye **Strategy Design Pattern** ka istemal hota hai. System ka mukhya hissa `ATM` class hoti hai, jo in states aur transactions ko control karti hai aur `Bank` ke backend se communicate karti hai.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional:** User card aur PIN se authenticate kar sake, balance check kar sake, paise nikal (withdraw) sake, aur paise jama (deposit) kar sake.
  * **Non-Functional:** System surakshit (secure) aur vishvasneeya (reliable) hona chahiye. Transactions **atomic** honi chahiye (ya toh poori hon ya bilkul na hon).
  * **Assumptions:** ATM ek central `Bank` ke backend se juda hua hai.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`ATM` (Context Class):**

      * Poori machine ko represent karti hai.
      * **Attributes:** `ATMState* currentState`, `double cashInMachine`.
      * **Methods:** `insertCard()`, `enterPin()`, `selectTransaction()`. Yeh methods kaam ko `currentState` ko delegate karte hain.

2.  **`ATMState` (Abstract Class):**

      * Machine ki states ke liye ek blueprint.
      * **Methods:** `insertCard()`, `enterPin()`, `selectTransaction()`, etc. (sabhi **pure virtual**).

3.  **Concrete States (`IdleState`, `CardInsertedState`, `PinEnteredState`):**

      * Yeh `ATMState` se inherit karte hain aur har state ke anusaar alag-alag behavior define karte hain.

4.  **`Transaction` (Abstract Class - Strategy Pattern):**

      * Alag-alag transactions (withdraw, deposit) ke liye ek blueprint.
      * **Methods:** `execute()` (pure virtual).

5.  **Concrete Transactions (`Withdrawal`, `Deposit`, `BalanceInquiry`):**

      * Yeh `Transaction` se inherit karte hain aur `execute` method ko implement karte hain.

6.  **`Bank` (Facade):**

      * Ek service class jo bank ke complex backend system se communication ke liye ek simple interface deti hai.
      * **Methods:** `authenticateUser()`, `processTransaction()`.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **State Pattern:** `ATM` **has-a** `ATMState`. Concrete states **are-a** `ATMState`.
  * **Strategy Pattern:** `ATM` **uses-a** `Transaction` strategy. `Withdrawal` **is-a** `Transaction`.
  * **Association:** `ATM` `Bank` ke saath communicate karta hai.

-----

### \#\# 4. Data Storage

  * `Bank` ka backend ek surakshit, transactional **database** (jaise Oracle, SQL Server) ka istemal karega. ATM machine khud koi permanent data store nahi karti.

-----

### \#\# 5. Concurrency

  * Ek ATM ek samay par ek hi user istemal karta hai, lekin bank ka backend system **highly concurrent** hona chahiye taaki woh hazaron ATMs se aane wale transactions ko ek saath handle kar sake.

-----

### \#\# 6. Scalability

  * Bank ka backend system **highly scalable** hona chahiye. Yeh design ek single ATM machine ke liye hai.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * Galat PIN daalna.
  * Account mein kam paise hona (insufficient funds).
  * Machine mein cash khatm ho jaana.
  * State Pattern in sabhi error states ko manage karne mein madad karta hai.

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **State Pattern:** Machine ke flow ko manage karne ke liye.
  * **Strategy Pattern:** Alag-alag transaction types ko handle karne ke liye.
  * **Facade Pattern:** `Bank` class ek complex backend ke liye ek simple interface pradan karti hai.
  * **SRP:** Har class ka ek hi kaam hai.

-----

### \#\# 9. APIs

  * ATM `Bank` ke backend se ek surakshit internal API (jaise REST ya gRPC) ke zariye baat karega.
      * `POST /authenticate {card_details, pin}`
      * `POST /transactions {account_id, type, amount}`

-----

### \#\# ATM ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class ATM;
class ATMState;
class Transaction;

// ===================================
// == STATE HIERARCHY ==
// ===================================
class ATMState {
public:
    virtual void insertCard(ATM* machine) = 0;
    virtual void enterPin(ATM* machine, int pin) = 0;
    virtual void selectTransaction(ATM* machine, Transaction* tx) = 0;
    virtual ~ATMState() {}
};

class IdleState : public ATMState {
public:
    void insertCard(ATM* machine) override;
    void enterPin(ATM* machine, int pin) override;
    void selectTransaction(ATM* machine, Transaction* tx) override;
};
// ... (CardInsertedState, PinEnteredState, etc.)

// ===================================
// == TRANSACTION HIERARCHY (STRATEGY) ==
// ===================================
class Transaction {
public:
    virtual void execute() = 0;
    virtual ~Transaction() {}
};

class Withdrawal : public Transaction {
private: double amount;
public:
    Withdrawal(double amt);
    void execute() override;
};
// ... (Deposit, BalanceInquiry)

// ===================================
// == MAIN CONTROLLER (CONTEXT) ==
// ===================================
class ATM {
private:
    ATMState* currentState;
public:
    ATM();
    ~ATM();
    void setState(ATMState* state);
    void insertCard();
    void enterPin(int pin);
    void selectTransaction(Transaction* tx);
};

// main function jahan se program shuru hoga
int main() {
    cout << "ATM System Design Ready!" << endl;
    return 0;
}
```

-----

-----

## 🌐 Design LinkedIn (Basic Social Network)

Ek basic social network jaise LinkedIn ka core design `User` (ya `Member`) class par kendrit hota hai. Users ke beech **connections** ek **graph data structure** se represent kiye jaate hain. Users `Profile` bana sakte hain, `Post` daal sakte hain, aur doosre users se jud sakte hain. Ek central `SocialNetwork` class poore platform aur user interactions ko manage karti hai.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional:** Users profile bana sakein (experience, education ke saath). Users doosre users ko connection request bhej sakein aur accept kar sakein. Users text ya image post kar sakein. Users apni connections ki posts apni feed mein dekh sakein.
  * **Non-Functional:** System **highly scalable** aur **available** hona chahiye.
  * **Assumptions:** Hum core networking aur posting features par focus kar rahe hain, messaging ya jobs par nahi.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`User`:**

      * **Attributes:** `userId`, `name`, `Profile* profile`, `vector<Connection*> connections`.
      * **Methods:** `sendConnectionRequest()`, `createPost()`.

2.  **`Profile`:**

      * **Attributes:** `headline`, `summary`, `vector<Experience*> experiences`, `vector<Education*> educations`.

3.  **`Experience`, `Education`:**

      * Simple data classes jismein company/school name, title, duration jaisi jaankari ho.

4.  **`Connection`:**

      * Do users ke beech ke rishte ko represent karta hai.
      * **Attributes:** `User* user1`, `User* user2`, `ConnectionStatus status` (PENDING, ACCEPTED).

5.  **`Post` (Abstract Class):**

      * **Attributes:** `postId`, `author`, `text`, `likes`.
      * **Derived Classes:** `TextPost`, `ImagePost`.

6.  **`SocialNetwork` (Main Controller):**

      * **Attributes:** `map<int, User*> users` (poora user network).
      * **Methods:** `registerUser()`, `generateFeed()`.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Composition:** `User` **has-a** `Profile`. `Profile` **has-many** `Experience`s.
  * **Association:** `User` **has-many** `Connection`s, jo ek graph banata hai.
  * **Inheritance:** `ImagePost` **is-a** `Post`.

-----

### \#\# 4. Data Storage

  * Iske liye alag-alag databases ka combination best hai:
      * **Graph Database (jaise Neo4j):** Connections aur network ko manage karne ke liye.
      * **Relational/NoSQL Database:** User profiles aur posts ko store karne ke liye.

-----

### \#\# 5. Concurrency

  * System mein **extremely high concurrency** hogi. Connection request bhejna/accept karna jaise actions atomic hone chahiye. Iske liye database transactions aur locks zaroori hain.

-----

### \#\# 6. Scalability

  * **Microservices architecture** (profile service, connection service, feed service alag-alag).
  * **Database Sharding/Replication** aur **Caching** (Redis/Memcached) zaroori hai.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * Ek user ko dobara connection request bhejna jisse aap pehle se connected hain.
  * User ka maujood na hona (user not found).

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Single Responsibility Principle (SRP):** `User`, `Profile`, `Post` ke liye alag-alag classes.
  * **Open/Closed Principle (OCP):** `Post` ki abstract class se hum भविष्य mein naye post types (jaise `VideoPost`) aasani se add kar sakte hain.

-----

### \#\# 9. APIs

  * RESTful API ka istemal hoga:
      * `GET /users/{id}/profile`
      * `GET /users/{id}/connections`
      * `POST /connections/request`
      * `GET /feed`
      * `POST /posts`

-----

### \#\# LinkedIn ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class User;
class Profile;
class Post;

// ===================================
// == PROFILE RELATED CLASSES ==
// ===================================
class Experience { /* ... */ };
class Education { /* ... */ };

class Profile {
private:
    string headline;
    vector<Experience*> experiences;
    vector<Education*> educations;
public:
    void addExperience(Experience* exp);
    void addEducation(Education* edu);
};

// ===================================
// == POST HIERARCHY ==
// ===================================
class Post {
protected:
    int postId;
    User* author;
    string text;
public:
    Post(int id, User* author, string text);
    virtual void display() = 0;
    virtual ~Post() {}
};

class TextPost : public Post {
public:
    TextPost(int id, User* author, string text);
    void display() override;
};
// ... (ImagePost, etc.)

// ===================================
// == USER & NETWORK CLASSES ==
// ===================================
class User {
private:
    int userId;
    string name;
    Profile* profile;
    vector<User*> connections;
public:
    User(int id, string name);
    ~User();
    void sendConnectionRequest(User* recipient);
    void acceptConnection(User* sender);
    void createPost(string text);
    Profile* getProfile();
};

// ===================================
// == MAIN CONTROLLER ==
// ===================================
class SocialNetwork {
private:
    map<int, User*> users;
public:
    ~SocialNetwork();
    void registerUser(int id, string name);
    User* getUser(int id);
    void establishConnection(int userId1, int userId2);
    vector<Post*> generateFeed(int userId);
};

// main function jahan se program shuru hoga
int main() {
    cout << "LinkedIn (Basic Social Network) Design Ready!" << endl;
    return 0;
}
```

---
Ek Pub-Sub (Publish-Subscribe) system ka core design publishers (sandesh bhejne wale) aur subscribers (sandesh prapt karne wale) ko ek doosre se **decouple** karne par aadharit hai. Ismein publishers seedhe subscribers ko sandesh nahi bhejte. Balki, woh ek central **Broker** ke andar maujood **Topics** (vishay) par sandesh publish karte hain. Broker phir un sabhi subscribers ko woh sandesh bhejta hai jinhone us topic ko subscribe kiya hua hai. Is design ka mukhya aadhar **Observer Design Pattern** hai.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * **Publishers:** Ek specific `Topic` par `Message` bhej sakenge.
      * **Subscribers:** Ek ya ek se adhik `Topic`s ko subscribe kar sakenge.
      * Jab ek topic par message publish hota hai, toh uske sabhi subscribers ko woh message milna chahiye.
      * Subscribers topic se unsubscribe kar sakenge.
      * System mein multiple topics hone chahiye.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Scalability:** System ko bhaari maatra mein messages aur laakhon publishers/subscribers ko handle karne ke liye scalable hona chahiye.
      * **Reliability:** Sandesh (messages) kho nahi jaane chahiye (message delivery guarantees).
      * **Low Latency:** Messages ko tezi se deliver kiya jaana chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Hum ek basic, in-memory, single-broker system design kar rahe hain.
      * Messages ko durable (permanent) store karne ki abhi zaroorat nahi hai.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`Message`:**

      * Ek simple class jo bheje ja rahe data ko rakhti hai.
      * **Attributes:** `string topic`, `string payload` (asli content).

2.  **`Subscriber` (Abstract Class / Interface):**

      * Yeh Observer Pattern ka **Observer** hai. Koi bhi class jise message receive karna hai, use is interface ko implement karna hoga.
      * **Methods:** `onMessage(const Message& message)` (yeh ek **pure virtual** function hoga - **Abstraction**).

3.  **Concrete Subscribers (`EmailSubscriber`, `SmsSubscriber`):**

      * Yeh `Subscriber` se inherit karenge (**Inheritance**) aur `onMessage` method ko apne hisaab se implement karenge (**Polymorphism**).

4.  **`Topic`:**

      * Yeh Observer Pattern ka **Subject** hai. Yeh apne sabhi subscribers ki list manage karta hai.
      * **Attributes:** `string name`, `list<Subscriber*> subscribers`.
      * **Methods:** `addSubscriber()`, `removeSubscriber()`, `broadcast()`.

5.  **`Broker` (Main Controller / Singleton):**

      * Yeh poore system ka central hub hai.
      * **Attributes:** `map<string, Topic*> topics`.
      * **Methods:** `createTopic()`, `subscribe()`, `publish()`.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Observer Pattern:** `Topic` "Subject" hai aur `Subscriber` "Observer" hai. `Topic` apne sabhi subscribers ki list rakhta hai aur naya message aane par unhe notify karta hai.
  * **Composition:** `Broker` **has-many** `Topic`s. `Topic` **has-many** `Subscriber`s (pointer ke through).
  * **Association:** `Publisher` `Broker` ka istemal karke sandesh bhejta hai.

-----

### \#\# 4. Data Storage

  * Is basic design mein, saari jaankari (topics aur subscribers ki list) **in-memory** rahegi.
  * Ek real-world durable system jaise Kafka ya RabbitMQ mein, broker messages ko disk par **log file** ya queue mein save karta hai taaki crash hone par data na khoye.

-----

### \#\# 5. Concurrency

  * Yeh **bahut zaroori** hai. Multiple publishers aur subscribers ek saath Broker aur Topics ko access karenge.
  * `addSubscriber`, `removeSubscriber`, aur `publish` jaise methods **thread-safe** hone chahiye. Iske liye **`std::mutex`** jaise locks ka istemal zaroori hai taaki shared data (jaise subscribers ki list) corrupt na ho.

-----

### \#\# 6. Scalability

  * Ek single broker performance bottleneck ban sakta hai. Real-world systems (jaise Kafka) distributed hote hain.
  * Woh multiple broker nodes ka istemal karte hain aur topics ko in nodes par **partition** karte hain. Isse parallel processing aur fault tolerance milta hai.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * Ek aise topic par publish karna jo exist nahi karta (Broker ya toh use auto-create kar sakta hai ya error de sakta hai).
  * Agar kisi subscriber ka `onMessage` method crash ho jaaye, toh Broker ko isse handle karna chahiye taaki baaki subscribers ko delivery na ruke.

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Observer Pattern:** Yeh Pub-Sub model ka mool siddhant hai. Yeh publishers aur subscribers ko poori tarah se decouple karta hai.
  * **Single Responsibility Principle (SRP):** `Broker` topics manage karta hai, `Topic` subscribers manage karta hai, aur `Subscriber` message handle karta hai.
  * **Open/Closed Principle (OCP):** Hum naye prakar ke subscribers (jaise `PushNotificationSubscriber`) aasani se add kar sakte hain bina Broker ya Topic class ko badle.

-----

### \#\# 9. APIs

  * System ka public API Broker ke methods se define hota hai:
      * `void subscribe(string topicName, Subscriber* subscriber)`
      * `void publish(string topicName, Message message)`
      * `void unsubscribe(string topicName, Subscriber* subscriber)`

-----

### \#\# Pub-Sub System ka C++ Code

```cpp
#include <bits/stdc++.h>
#include <mutex> // For thread safety
using namespace std;

class Message {
public:
    string topic;
    string payload;
};

// ===================================
// == SUBSCRIBER INTERFACE (OBSERVER) ==
// ===================================
// Abstract class jise har subscriber implement karega
class Subscriber {
public:
    virtual void onMessage(const Message& message) = 0;
    virtual string getId() = 0;
    virtual ~Subscriber() {}
};

// ===================================
// == TOPIC CLASS (SUBJECT) ==
// ===================================
// Yeh class ek topic aur uske subscribers ko manage karti hai
class Topic {
private:
    string name;
    list<Subscriber*> subscribers;
    mutex mtx; // Thread safety ke liye

public:
    Topic(string name) : name(name) {}

    void addSubscriber(Subscriber* sub) {
        lock_guard<mutex> lock(mtx);
        subscribers.push_back(sub);
        cout << sub->getId() << " ne '" << name << "' topic ko subscribe kiya." << endl;
    }

    void removeSubscriber(Subscriber* sub) {
        lock_guard<mutex> lock(mtx);
        subscribers.remove(sub);
    }

    // Sabhi subscribers ko message bhejna
    void broadcast(const Message& message) {
        lock_guard<mutex> lock(mtx);
        for (auto sub : subscribers) {
            sub->onMessage(message);
        }
    }
};

// ===================================
// == BROKER (MAIN CONTROLLER) ==
// ===================================
// Yeh central class hai jo sabhi topics ko manage karti hai
class Broker {
private:
    map<string, Topic*> topics;
    mutex mtx; // Thread safety ke liye

    Broker() {} // Singleton ke liye private constructor

public:
    // Singleton pattern
    static Broker& getInstance() {
        static Broker instance;
        return instance;
    }

    void createTopic(const string& topicName) {
        lock_guard<mutex> lock(mtx);
        if (topics.find(topicName) == topics.end()) {
            topics[topicName] = new Topic(topicName);
            cout << "Topic '" << topicName << "' banaya gaya." << endl;
        }
    }

    void subscribe(const string& topicName, Subscriber* sub) {
        if (topics.find(topicName) != topics.end()) {
            topics[topicName]->addSubscriber(sub);
        } else {
            cout << "Error: Topic '" << topicName << "' maujood nahi hai." << endl;
        }
    }

    void publish(const Message& message) {
        if (topics.find(message.topic) != topics.end()) {
            cout << "\n'" << message.topic << "' par naya message publish hua: \"" << message.payload << "\"" << endl;
            topics[message.topic]->broadcast(message);
        }
    }
};

// ===================================
// == CONCRETE SUBSCRIBERS ==
// ===================================
// Ek example subscriber
class EmailSubscriber : public Subscriber {
private:
    string id;
public:
    EmailSubscriber(string id) : id(id) {}
    string getId() override { return id; }
    void onMessage(const Message& message) override {
        cout << "  -> [" << id << " - Email] Naya sandesh prapt hua: " << message.payload << endl;
    }
};

// Ek aur example subscriber
class SmsSubscriber : public Subscriber {
private:
    string id;
public:
    SmsSubscriber(string id) : id(id) {}
    string getId() override { return id; }
    void onMessage(const Message& message) override {
        cout << "  -> [" << id << " - SMS] Naya sandesh prapt hua: " << message.payload << endl;
    }
};


// main function jahan se program shuru hoga
int main() {
    // Broker ka instance pao
    Broker& broker = Broker::getInstance();
    
    // Topics banao
    broker.createTopic("NEWS");
    broker.createTopic("SPORTS");

    // Subscribers banao
    Subscriber* amit_email = new EmailSubscriber("Amit (Email)");
    Subscriber* babita_sms = new SmsSubscriber("Babita (SMS)");
    Subscriber* chandan_email = new EmailSubscriber("Chandan (Email)");

    // Subscribe karo
    broker.subscribe("NEWS", amit_email);
    broker.subscribe("NEWS", babita_sms);
    broker.subscribe("SPORTS", chandan_email);

    // Messages publish karo
    broker.publish({"NEWS", "Aaj mausam accha hai."});
    broker.publish({"SPORTS", "India ne match jeet liya!"});

    delete amit_email;
    delete babita_sms;
    delete chandan_email;

    return 0;
}
```

---
Ek elevator system ka core design ek central **`ElevatorController`** par nirbhar karta hai, jo ek ya ek se adhik **`Elevator`** cars ko manage karta hai. Har elevator ek state machine ki tarah kaam karta hai, jiski states `MOVING_UP`, `MOVING_DOWN`, aur `IDLE` ho sakti hain. Building ke floors se aane wale **external requests** aur elevator ke andar se aane wale **internal requests** ko controller ek scheduling algorithm (jaise SCAN) ka istemal karke anukoolit (optimize) karta hai aur elevators ko dispatch karta hai.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * Building mein multiple floors aur multiple elevators honge.
      * Kisi bhi floor se user upar (**Up**) ya neeche (**Down**) jaane ke liye elevator bula sakta hai (External Request).
      * Elevator ke andar user apni manzil (destination floor) select kar sakta hai (Internal Request).
      * Elevator ko floors ke beech move karna, darwaze kholna aur band karna aana chahiye.
      * System ko decide karna hoga ki kaun sa elevator kis request ko service dega.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Performance:** Yatriyon (passengers) ka intzaar ka samay (wait time) aur yatra ka samay (travel time) kam se kam hona chahiye.
      * **Safety & Reliability:** System fail-safe hona chahiye. Darwaze kisi par band nahi hone chahiye aur elevator khule darwazon ke saath nahi chalna chahiye.
      * **Concurrency:** Alag-alag floors aur elevators mein ek saath kai log buttons daba sakte hain.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Hum software logic design kar rahe hain, hardware control nahi.
      * Yeh design ek single building ke elevator system ke liye hai.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`Elevator` (ya `ElevatorCar`):**

      * Yeh ek single elevator car ko represent karta hai.
      * **Attributes:** `id`, `currentFloor`, `Direction direction` (UP, DOWN, IDLE), `DoorStatus doorStatus` (OPEN, CLOSED), `set<int> internalRequests` (andar se select kiye gaye floors).
      * **Methods:** `move()`, `openDoor()`, `closeDoor()`, `addInternalRequest()`.

2.  **`Request`:**

      * Yeh user ke button dabane ko represent karta hai.
      * **Types:** `InternalRequest` (sirf destination floor), `ExternalRequest` (origin floor aur direction).

3.  **`ElevatorController` (Main Controller):**

      * Yeh system ka dimaag (brain) hai.
      * **Attributes:** `vector<Elevator*> elevators`, `queue<ExternalRequest> pendingRequests`.
      * **Methods:** `handleExternalRequest()`, `handleInternalRequest()`, `step()` (jo system ko samay ke saath aage badhata hai), `dispatchElevator()`.

4.  **`ElevatorSchedulingStrategy` (Strategy Pattern):**

      * Elevator ko dispatch karne ke logic ko encapsulate karne ke liye.
      * **Abstract Class:** `ElevatorSchedulingStrategy`.
      * **Concrete Classes:** `LookSchedulingStrategy` (SCAN algorithm), `FcfsSchedulingStrategy` (First-Come, First-Served).

5.  **`Enums`:**

      * `Direction` (UP, DOWN, IDLE), `DoorStatus` (OPEN, CLOSED).

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Composition:** `ElevatorController` **has-many** `Elevator`s.
  * **Strategy Pattern:** `ElevatorController` **uses-a** `ElevatorSchedulingStrategy`.
  * **Association:** `Elevator` `InternalRequest`s ko process karta hai, jabki `ElevatorController` `ExternalRequest`s ko process karke `Elevator` ko assign karta hai.

-----

### \#\# 4. Data Storage

  * Elevators ki current state aur pending requests **in-memory** store hoti hain. Ek real-world system mein, trips aur errors ke logs ko database mein rakha jaata hai.

-----

### \#\# 5. Concurrency

  * Yeh **bahut zaroori** hai. Multiple requests ek saath aa sakti hain.
  * Pending requests ki queue thread-safe honi chahiye. Ek producer-consumer model yahan fit baithta hai, jahan user requests "producer" hain aur controller "consumer" hai. Iske liye **`std::mutex`** ka istemal zaroori hai.

-----

### \#\# 6. Scalability

  * System ko `ElevatorController` mein aur `Elevator` objects add karke scale kiya ja sakta hai.
  * Badi buildings mein, alag-alag zones (jaise low-rise aur high-rise elevators) ke liye alag-alag `ElevatorController` instances ho sakte hain.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * **Elevator Malfunction:** System ko ek kharab elevator ko pehchan kar use service se hata dena chahiye.
  * **Emergency Stop:** Emergency button ko handle karna.
  * **Overload:** Agar elevator mein zyada log hain, toh sensor use chalne se rokega.

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **State Pattern:** `Elevator` ka behavior (chalna, rukna) uski state (`Direction`, `DoorStatus`) par nirbhar karta hai.
  * **Strategy Pattern:** Scheduling algorithm ko controller se decouple karta hai. Isse hum aasaani se algorithm badal sakte hain (jaise FCFS se SCAN).
  * **Single Responsibility Principle (SRP):** `Elevator` apni movement aur state manage karta hai. `ElevatorController` poore system ko coordinate karta hai.

-----

### \#\# 9. APIs

  * System ka "API" uske buttons hain:
      * `ElevatorController::handleExternalRequest(int floor, Direction dir)`
      * `Elevator::addInternalRequest(int floor)`

-----

### \#\# Elevator System ka C++ Code

```cpp
#include <bits/stdc++.h>
#include <mutex>
#include <thread>
using namespace std;

// Enums for clarity
enum class Direction { UP, DOWN, IDLE };
enum class DoorStatus { OPEN, CLOSED };

// ===================================
// == REQUEST CLASSES ==
// ===================================
class Request {
public:
    int floor;
};
class InternalRequest : public Request {};
class ExternalRequest : public Request {
public:
    Direction direction;
};

// ===================================
// == ELEVATOR CAR CLASS ==
// ===================================
class Elevator {
private:
    int id;
    int currentFloor;
    Direction direction;
    DoorStatus doorStatus;
    set<int> internalRequests; // Use a set to avoid duplicate floor requests
public:
    Elevator(int id);
    void move();
    void addInternalRequest(int floor);
    void displayStatus();
    // Getters and setters
    int getCurrentFloor() const;
    Direction getDirection() const;
};

// ===================================
// == SCHEDULING STRATEGY ==
// ===================================
class ElevatorSchedulingStrategy {
public:
    virtual void schedule(const ExternalRequest& req, const vector<Elevator*>& elevators) = 0;
    virtual ~ElevatorSchedulingStrategy() {}
};

// Simple FCFS strategy for demonstration
class FcfsSchedulingStrategy : public ElevatorSchedulingStrategy {
public:
    void schedule(const ExternalRequest& req, const vector<Elevator*>& elevators) override;
};

// ===================================
// == MAIN CONTROLLER CLASS ==
// ===================================
class ElevatorController {
private:
    vector<Elevator*> elevators;
    queue<ExternalRequest> pendingExternalRequests;
    ElevatorSchedulingStrategy* strategy;
    mutex mtx; // For thread safety

public:
    ElevatorController(int numElevators, ElevatorSchedulingStrategy* strat);
    ~ElevatorController();

    // API methods called by users/buttons
    void handleExternalRequest(int floor, Direction dir);
    void handleInternalRequest(int elevatorId, int floor);

    // Main loop for the system
    void step();
};


// main function jahan se program shuru hoga
int main() {
    cout << "Elevator System Design Ready!" << endl;

    // System ko FCFS strategy ke saath initialize karna
    ElevatorSchedulingStrategy* strategy = new FcfsSchedulingStrategy();
    ElevatorController controller(2, strategy); // 2 elevators

    // Kuch requests simulate karna
    cout << "\n--- Simulation Shuru ---" << endl;
    controller.handleExternalRequest(5, Direction::UP);    // Floor 5 se upar jaana hai
    controller.handleInternalRequest(0, 7);              // Elevator 0 ke andar 7th floor ka button daba
    
    // Controller ka step function ek loop mein chalega
    // controller.step(); 

    cout << "Ek request floor 5 se upar jaane ke liye aur ek internal request floor 7 ke liye system mein daali gayi." << endl;

    delete strategy;
    return 0;
}
```


---

Ek car rental system ka core design **`User`**, **`Vehicle`**, aur **`Reservation`** ke ird-gird ghoomta hai. Ismein ek `User` kisi `Store` (location) par uplabdh (available) `Vehicle` ko ek nishchit samay avadhi (date range) ke liye search karta hai. Agar gaadi uplabdh hoti hai, toh ek `Reservation` banaya jaata hai, jo user, gaadi, aur kiraye ki avadhi ko jodta hai. Ek central **`CarRentalSystem`** class in sabhi operations ko manage karti hai.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * Users location, date, aur gaadi ke type ke aadhar par uplabdh gaadiyan search kar sakenge.
      * System alag-alag prakar ki gaadiyan (`Sedan`, `SUV`, `Hatchback`) dikhayega.
      * User ek gaadi book kar sakega, jisse ek **Reservation** banega.
      * System gaadiyon ki **Inventory** (kaun si gaadi uplabdh hai, kiraye par hai, ya maintenance mein hai) manage karega.
      * User gaadi ko pick up aur return kar sakega.
      * Gaadi return karne par, system kiraye ki avadhi aur extra charges ke aadhar par antim bill banayega.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Concurrency:** Kai users ek hi samay par aakhiri uplabdh gaadi ko book karne ki koshish kar sakte hain. Booking process **atomic** hona chahiye.
      * **Reliability:** System ko reservations aur gaadiyon ke status ko sateek roop se track karna chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * System multiple rental locations (stores) ko manage karta hai.
      * Kiraye ka daam gaadi ke type par nirbhar karta hai.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`User`:**

      * **Attributes:** `userId`, `name`, `driverLicenseNumber`.

2.  **`Vehicle` (Abstract Class):**

      * **Attributes:** `licensePlate`, `make`, `model`, `VehicleStatus status` (AVAILABLE, RENTED).
      * **Methods:** `getType()` (pure virtual - **Abstraction**).

3.  **Concrete Vehicles (`Sedan`, `SUV`):**

      * `Vehicle` se inherit karenge (**Inheritance**) aur `getType()` ko implement karenge (**Polymorphism**).

4.  **`Store` (ya `RentalLocation`):**

      * **Attributes:** `storeId`, `address`, `VehicleInventory* inventory`.

5.  **`VehicleInventory`:**

      * **Attributes:** `map<VehicleType, list<Vehicle*>> vehicles`. Har store par uplabdh gaadiyon ko manage karta hai.
      * **Methods:** `getAvailableVehicles()`, `bookVehicle()`.

6.  **`Reservation`:**

      * **Attributes:** `reservationId`, `user`, `vehicle`, `pickupStore`, `returnStore`, `startTime`, `endTime`, `Bill* bill`.

7.  **`Bill`:**

      * **Attributes:** `baseAmount`, `lateFee`, `totalAmount`.
      * **Methods:** `calculateBill()`.

8.  **`CarRentalSystem` (Main Controller / Facade):**

      * Poore system ka entry point.
      * **Attributes:** `vector<Store*> stores`, `vector<User*> users`.
      * **Methods:** `searchVehicles()`, `makeReservation()`, `completeReservation()`.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Composition:** `Store` **has-a** `VehicleInventory`. `Reservation` **has-a** `Bill`.
  * **Inheritance:** `Sedan` **is-a** `Vehicle`.
  * **Association:** `Reservation` ek `User`, `Vehicle`, aur `Store` ko aapas mein jodta hai.

-----

### \#\# 4. Data Storage

  * Is tarah ke system ke liye ek **Relational Database** (jaise MySQL, PostgreSQL) accha vikalp hai kyunki ismein users, vehicles, aur reservations ke beech structured relationships hote hain.

-----

### \#\# 5. Concurrency

  * Gaadi book karne ka process ek critical section hai. Jab kai users ek hi gaadi book karne ki koshish karte hain, toh data inconsistency ho sakti hai.
  * Isse bachne ke liye inventory mein gaadi ke status par **locking mechanism** ya **database transactions** ka istemal karna zaroori hai.

-----

### \#\# 6. Scalability

  * System ko naye `Store` locations add karke scale kiya ja sakta hai.
  * Ek bade, deshvyapi (nationwide) system ke liye, distributed architecture aur microservices (inventory ke liye alag, users ke liye alag) ki zaroorat hogi.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * Chuninda (selected) criteria ke liye koi gaadi uplabdh na hona.
  * Invalid user ya payment jaankari.
  * Gaadi ko galat location par return karna (agar anumati na ho).

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Single Responsibility Principle (SRP):** Har class ka ek kaam hai: `VehicleInventory` stock manage karti hai, `Reservation` booking details rakhta hai.
  * **Open/Closed Principle (OCP):** `Vehicle` ki abstract class se hum भविष्य mein nayi gaadi ke types (jaise `LuxuryCar`) aasani se add kar sakte hain bina maujooda code ko badle.
  * **Facade Pattern:** `CarRentalSystem` class ek facade ki tarah kaam karti hai, jo ek complex system ko istemal karne ke liye ek saral interface (`search`, `makeReservation`) deti hai.

-----

### \#\# 9. APIs

  * Ek real-world system mein REST APIs honge:
      * `GET /vehicles/search?location={loc}&type={type}`
      * `POST /reservations`: Nayi reservation banane ke liye.
      * `POST /reservations/{id}/return`: Gaadi return process karne ke liye.

-----

### \#\# Car Rental System ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Enums for clarity
enum class VehicleType { SEDAN, SUV, HATCHBACK };
enum class VehicleStatus { AVAILABLE, RENTED, MAINTENANCE };
enum class ReservationStatus { SCHEDULED, INPROGRESS, COMPLETED, CANCELLED };

// Forward Declarations
class Vehicle;
class User;
class Store;
class Reservation;

// ===================================
// == VEHICLE HIERARCHY ==
// ===================================
class Vehicle {
protected:
    string licensePlate;
    string make;
    VehicleStatus status;
public:
    Vehicle(string plate, string make) : licensePlate(plate), make(make), status(VehicleStatus::AVAILABLE) {}
    virtual VehicleType getType() = 0; // Abstraction
    void updateStatus(VehicleStatus newStatus) { status = newStatus; }
    string getLicensePlate() { return licensePlate; }
    virtual ~Vehicle() {}
};

class Sedan : public Vehicle { // Inheritance
public:
    Sedan(string plate, string make) : Vehicle(plate, make) {}
    VehicleType getType() override { return VehicleType::SEDAN; } // Polymorphism
};
// ... (SUV, Hatchback classes)

// ===================================
// == CORE BUSINESS CLASSES ==
// ===================================
class User {
private:
    int userId;
    string name;
public:
    User(int id, string name) : userId(id), name(name) {}
};

class Store {
private:
    int storeId;
    string location;
    // Har store ki apni inventory hogi
    map<VehicleType, list<Vehicle*>> vehicleInventory;
public:
    Store(int id, string loc);
    list<Vehicle*> getAvailableVehicles(VehicleType type);
    void addVehicle(Vehicle* vehicle);
};

class Bill {
private:
    Reservation* reservation;
    double amount;
public:
    Bill(Reservation* res, double amt) : reservation(res), amount(amt) {}
    void pay();
};

class Reservation {
private:
    int reservationId;
    User* user;
    Vehicle* vehicle;
    Store* pickupStore;
    Store* returnStore;
    time_t pickupTime;
    time_t returnTime;
    ReservationStatus status;
public:
    Reservation(int id, User* u, Vehicle* v, Store* pickup);
    Bill* completeReservation();
};


// ===================================
// == MAIN CONTROLLER (FACADE) ==
// ===================================
class CarRentalSystem {
private:
    vector<Store*> stores;
    vector<User*> users;
    vector<Reservation*> reservations;
public:
    // Yahan concurrency ke liye mutex lagega
    // mutex mtx;
    
    void addStore(Store* store);
    void addUser(User* user);
    
    // Core functionalities
    list<Vehicle*> searchVehicles(VehicleType type, string location);
    Reservation* makeReservation(User* user, Vehicle* vehicle, Store* pickupStore);
    void completeReservation(int reservationId);
};

// main function jahan se program shuru hoga
int main() {
    cout << "Car Rental System Design Ready!" << endl;
    
    // System setup karna
    CarRentalSystem rentalSystem;
    Store* store1 = new Store(1, "Prayagraj");
    User* user1 = new User(101, "Amit");
    Vehicle* sedan1 = new Sedan("UP70-CAR1", "Honda");
    
    rentalSystem.addStore(store1);
    rentalSystem.addUser(user1);
    store1->addVehicle(sedan1);

    // Flow:
    // 1. User gaadi search karta hai
    cout << "\nSedan search ki ja rahi hai..." << endl;
    list<Vehicle*> availableSedans = rentalSystem.searchVehicles(VehicleType::SEDAN, "Prayagraj");
    
    // 2. Reservation banata hai
    if (!availableSedans.empty()) {
        Vehicle* carToBook = availableSedans.front();
        Reservation* res = rentalSystem.makeReservation(user1, carToBook, store1);
        if (res) {
            cout << "Reservation safaltapurvak ho gaya!" << endl;
        }
    }
    
    // 3. Kuch samay baad reservation complete karta hai
    // rentalSystem.completeReservation(res->getId());
    
    return 0;
}
```

----
Ek online auction system jaise eBay ka core design **`User`**, **`Item`**, **`Auction`**, aur **`Bid`** (boli) par kendrit hota hai. Ismein ek `User` (seller) ek `Item` ko `Auction` ke liye list karta hai. Doosre `User`s (bidders) us auction par `Bid` lagate hain. Ek central **`AuctionPlatform`** class sabhi users, auctions, aur bids ko manage karti hai. Iska sabse zaroori kaam har auction ke liye highest bid ko track karna aur samay khatm hone par vijeta (winner) ghoshit karna hai.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * **Users:** System par register kar sakenge.
      * **Sellers:** Items ko auction ke liye list kar sakenge, jismein starting price aur end time hoga.
      * **Bidders:** Active auctions par boli (bid) laga sakenge.
      * Har nayi boli vartaman (current) highest boli se zyada honi chahiye.
      * Auction ka samay khatm hone par, sabse oonchi boli lagane wala bidder jeet jaayega.
      * System ko vijeta aur seller ko सूचना (notify) deni chahiye.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Concurrency:** Ek hi item par, khaas kar auction ke aakhiri palon mein, kai log ek saath boli laga sakte hain. Bidding process atomic aur thread-safe hona chahiye.
      * **Real-time Updates:** Bidders ko vartaman boli ka update turant milna chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Hum ek standard English auction (sabse oonchi boli wala jeetta hai) design kar rahe hain.
      * Payment system ek alag module hai.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`User`:**

      * **Attributes:** `userId`, `username`, `rating`.

2.  **`Item`:**

      * **Attributes:** `itemId`, `name`, `description`, `seller` (User\*).

3.  **`Bid`:**

      * **Attributes:** `bidder` (User\*), `amount`, `timestamp`.

4.  **`Auction`:**

      * Yeh ek single auction process ki mukhya class hai.
      * **Attributes:** `auctionId`, `item` (Item\*), `startTime`, `endTime`, `startPrice`, `Bid* currentHighestBid`, `AuctionStatus status` (ACTIVE, CLOSED).
      * **Methods:** `placeBid()`, `endAuction()`. `placeBid` method mein race conditions se bachne ke liye logic hoga.

5.  **`NotificationService`:**

      * Notifications bhejne ke liye ek alag service.
      * **Methods:** `sendOutbidNotification()` (jab koi aapse oonchi boli laga de), `sendWinnerNotification()`.

6.  **`AuctionPlatform` (Main Controller):**

      * Poore system ko manage karta hai.
      * **Attributes:** `map<int, User*> users`, `map<int, Auction*> auctions`.
      * **Methods:** `registerUser()`, `createAuction()`, `handleBid()`.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Composition:** `Auction` **has-an** `Item`. `Auction` **has-a** current `Bid`.
  * **Association:** `User` `Item` ka `seller` ho sakta hai ya `Bid` ka `bidder`. Ek `Auction` mein kai `User`s shaamil hote hain.

-----

### \#\# 4. Data Storage

  * Is system ke liye ek vishvasneeya (durable) **database** zaroori hai. **Relational Database** (jaise PostgreSQL) iske liye accha hai kyunki ismein users, items, aur bids ke beech structured relationships hote hain. Bids ko handle karne ke liye database ki **ACID properties** bahut mahatvapurna hain.

-----

### \#\# 5. Concurrency

  * `Auction` class ka `placeBid()` method sabse **critical section** hai. Ise atomically check karna hoga ki nayi boli sabse oonchi hai ya nahi aur phir `currentHighestBid` ko update karna hoga.
  * Iske liye code mein **`std::mutex`** jaise locks ya database level par transactions ka istemal karna anivarya hai taaki race conditions na hon.

-----

### \#\# 6. Scalability

  * Ek bade scale ke auction platform ke liye zaroori hai:
      * **Load Balancers** ke saath distributed servers.
      * High traffic handle karne ke liye **Database Replication/Sharding**.
      * Popular items ki details ke liye **Caching** (jaise Redis) ka istemal.
      * Real-time bid updates ke liye **WebSockets**.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * Lagayi gayi boli vartaman boli se kam hai.
  * Auction khatm hone ke baad boli lagana.
  * User ka apne hi item par boli lagana.

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Single Responsibility Principle (SRP):** Har class ka ek kaam hai: `Auction` ek auction ki state, `User` user data, aur `AuctionPlatform` poora system manage karta hai.
  * **Observer Pattern:** `NotificationService` ko Observer Pattern se implement kiya ja sakta hai. `Auction` (Subject) naya highest bid aane par apne observers (jaise pichhle highest bidder) ko notify karega.
  * **Open/Closed Principle (OCP):** Hum alag-alag prakar ke auctions (jaise Dutch Auction) ko `Auction` ki abstract class banakar aur nayi strategy implement karke jod sakte hain.

-----

### \#\# 9. APIs

  * Ek real-world system mein REST APIs honge:
      * `POST /auctions`: Naya auction banane ke liye.
      * `GET /auctions/{id}`: Auction ki details dekhne ke liye.
      * `POST /auctions/{id}/bids`: Nayi boli lagane ke liye.

-----

### \#\# Online Auction System ka C++ Code

```cpp
#include <bits/stdc++.h>
#include <mutex>
using namespace std;

// Forward Declarations
class User;
class Item;
class Bid;
class Auction;

// ===================================
// == CORE DATA CLASSES ==
// ===================================
class User {
public:
    int userId;
    string username;
    User(int id, string name) : userId(id), username(name) {}
};

class Item {
public:
    int itemId;
    string name;
    User* seller;
    Item(int id, string name, User* seller) : itemId(id), name(name), seller(seller) {}
};

class Bid {
public:
    User* bidder;
    double amount;
    time_t timestamp;
    Bid(User* b, double amt) : bidder(b), amount(amt) {
        timestamp = time(0);
    }
};

// ===================================
// == AUCTION CLASS ==
// ===================================
// Yeh class ek single auction ko manage karti hai.
class Auction {
private:
    int auctionId;
    Item* item;
    double startPrice;
    time_t endTime;
    Bid* currentHighestBid;
    mutex bidMutex; // Concurrency control ke liye

public:
    Auction(int id, Item* item, double price, int durationInSeconds) {
        this->auctionId = id;
        this->item = item;
        this->startPrice = price;
        this->endTime = time(0) + durationInSeconds;
        this->currentHighestBid = nullptr;
    }

    ~Auction() {
        delete currentHighestBid;
    }

    // Boli lagane ka thread-safe method
    bool placeBid(User* bidder, double amount) {
        lock_guard<mutex> lock(bidMutex); // Mutex lock

        if (time(0) > endTime) {
            cout << "Auction khatm ho chuka hai!" << endl;
            return false;
        }

        double currentBidAmount = (currentHighestBid == nullptr) ? startPrice : currentHighestBid->amount;

        if (amount > currentBidAmount) {
            delete currentHighestBid; // Purane bid ko delete karo
            currentHighestBid = new Bid(bidder, amount);
            cout << "Nayi highest boli: " << amount << " by " << bidder->username << endl;
            // Yahan notification service ko call kiya ja sakta hai
            return true;
        }
        
        cout << "Aapki boli (" << amount << ") vartaman highest boli (" << currentBidAmount << ") se kam hai." << endl;
        return false;
    }

    void endAuction() {
        cout << "\n--- Auction for '" << item->name << "' samapt! ---" << endl;
        if (currentHighestBid != nullptr) {
            cout << "Vijeta: " << currentHighestBid->bidder->username 
                 << " with a bid of " << currentHighestBid->amount << endl;
        } else {
            cout << "Koi boli nahi lagi." << endl;
        }
    }
};

// ===================================
// == MAIN CONTROLLER CLASS ==
// ===================================
class AuctionPlatform {
private:
    map<int, User*> users;
    map<int, Auction*> auctions;
public:
    ~AuctionPlatform() {
        for(auto const& [key, val] : users) delete val;
        for(auto const& [key, val] : auctions) delete val;
    }
    void registerUser(int id, string name) {
        users[id] = new User(id, name);
    }
    void createAuction(int auctionId, int itemId, string itemName, int sellerId, double startPrice, int duration) {
        if (users.count(sellerId)) {
            User* seller = users[sellerId];
            Item* item = new Item(itemId, itemName, seller);
            auctions[auctionId] = new Auction(auctionId, item, startPrice, duration);
            cout << "Auction '" << itemName << "' banaya gaya by " << seller->username << endl;
        }
    }
    void handleBid(int userId, int auctionId, double amount) {
        if (users.count(userId) && auctions.count(auctionId)) {
            auctions[auctionId]->placeBid(users[userId], amount);
        }
    }
    Auction* getAuction(int id) { return auctions[id]; }
};

// main function jahan se program shuru hoga
int main() {
    AuctionPlatform platform;
    platform.registerUser(101, "Amit (Seller)");
    platform.registerUser(201, "Babita (Bidder)");
    platform.registerUser(202, "Chandan (Bidder)");

    platform.createAuction(1, 1001, "Vintage Watch", 101, 5000.0, 10); // 10 sec auction

    cout << "\n--- Boli shuru! ---" << endl;
    platform.handleBid(201, 1, 5500.0);
    platform.handleBid(202, 1, 6000.0);
    platform.handleBid(201, 1, 5800.0); // Yeh fail hoga
    platform.handleBid(202, 1, 6500.0);

    platform.getAuction(1)->endAuction();

    return 0;
}

```

---
Ek hotel management system ka core design **`Room`** (kamre) aur **`Reservation`** (booking) ke ird-gird banta hai. Ismein alag-alag prakar ke `Room` (`SingleRoom`, `Suite`) aur unki uplabdhata (availability) ko manage kiya jaata hai. **`Guest`** (mehmaan) **`Reservation`** banate hain, jinhe **`Staff`** (jaise receptionist) handle karte hain. System ka mukhya kaam kamre ki availability check karna, booking banana, guest ka **check-in/check-out** manage karna, aur aakhir mein bill banana hai. Ek central **`Hotel`** class in sabhi cheezon ko aapas mein jodti hai.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * Hotel mein alag-alag prakar ke **kamre** (Rooms) honge.
      * **Mehmaan** (Guests) ek nishchit taareekh ke liye kamre ki **booking** (Reservation) kar sakenge.
      * **Staff** (jaise Receptionist) in reservations ko bana aur cancel kar sakenge.
      * System ko guest ka **check-in** aur **check-out** handle karna hoga.
      * System ko kamron ki **inventory** manage karni hogi (kaun sa kamra khaali hai, bhara hua hai, ya safai mein hai).
      * System ko extra **services** (jaise room service, laundry) ke charges jodna aana chahiye.
      * Check-out ke samay, system ko antim **bill** banakar **payment** process karna hoga.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Concurrency:** Multiple receptionists ek hi samay par aakhiri uplabdh kamre ko book karne ki koshish kar sakte hain. System ko ise handle karna aana chahiye.
      * **Reliability:** Reservation aur billing ka data hamesha sateek aur surakshit rehna chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Yeh design ek single hotel ke internal management ke liye hai.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`Person` (Abstract Class):**

      * **Attributes:** `personId`, `name`.
      * **Derived Classes:** `Guest` (jiske paas booking history hogi) aur `Staff` (jiska employee ID aur role hoga).

2.  **`Room` (Abstract Class):**

      * **Attributes:** `roomNumber`, `RoomStatus status` (AVAILABLE, OCCUPIED, CLEANING), `pricePerNight`.
      * **Methods:** `getType()` (pure virtual - **Abstraction**).
      * **Derived Classes:** `SingleRoom`, `DoubleRoom`, `Suite` (**Inheritance** & **Polymorphism**).

3.  **`Reservation`:**

      * **Attributes:** `reservationId`, `guest`, `room`, `checkInDate`, `checkOutDate`, `status`.

4.  **`Service`:**

      * Hotel dwara di jaane wali extra services (jaise Room Service).
      * **Attributes:** `description`, `cost`.

5.  **`Bill`:**

      * **Attributes:** `billId`, `reservation`, `vector<Service*> services`, `totalAmount`.
      * **Methods:** `addServiceCharge()`, `calculateTotal()`.

6.  **`Hotel` (Main Controller / Facade):**

      * Poore hotel ke operations ko manage karta hai.
      * **Attributes:** `vector<Room*> rooms`, `vector<Staff*> staff`, `map<int, Reservation*> reservations`.
      * **Methods:** `searchAvailableRooms()`, `createReservation()`, `checkIn()`, `checkOut()`.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Composition:** `Hotel` **has-many** `Room`s. `Bill` **has-many** `Service`s.
  * **Inheritance:** `Guest` aur `Staff` **is-a** `Person`. `Suite` **is-a** `Room`.
  * **Association:** `Reservation` ek `Guest` aur `Room` ko jodta hai.

-----

### \#\# 4. Data Storage

  * Is system ke liye ek **Relational Database** (jaise MySQL) sabse upyukt hai kyunki ismein rooms, guests, aur reservations ke beech structured data aur relationships hote hain.

-----

### \#\# 5. Concurrency

  * Jab do receptionists ek hi kamre ko ek saath book karne ki koshish karte hain, toh double booking ho sakti hai.
  * Isse bachne ke liye, kamre ki availability check karne aur use book karne ka operation **atomic** hona chahiye. Yeh aam taur par **database transactions** ke zariye kiya jaata hai.

-----

### \#\# 6. Scalability

  * Yeh design ek hotel ke liye hai. Agar hotel ki chain manage karni ho, toh ek `HotelChainManager` class banayi ja sakti hai jo multiple `Hotel` objects ko manage karegi.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * Maangi gayi (requested) date/type ke liye koi kamra uplabdh na hona.
  * Guest ka ek aise kamre mein check-in karne ki koshish karna jo saaf nahi hai.
  * Invalid reservation ID.

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Single Responsibility Principle (SRP):** Har class ka ek kaam hai: `Room` apni state, `Reservation` booking details, `Bill` paison ka hisaab, aur `Hotel` sabko coordinate karta hai.
  * **Open/Closed Principle (OCP):** `Room` aur `Person` ki abstract classes se hum भविष्य mein naye types (jaise `Penthouse`, `Manager`) aasani se add kar sakte hain.
  * **Facade Pattern:** `Hotel` class ek facade ki tarah kaam karti hai, jo staff ke liye ek saral interface (`checkIn`, `checkOut`) pradan karti hai.

-----

### \#\# 9. APIs

  * Yeh ek internal system hai, lekin yeh ek online booking website ke liye APIs de sakta hai:
      * `GET /rooms/availability?type={type}&date={date}`
      * `POST /reservations`: Nayi booking banane ke liye.
      * `POST /reservations/{id}/checkout`: Check-out aur billing ke liye.

-----

### \#\# Hotel Management System ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Enums for clarity
enum class RoomType { SINGLE, DOUBLE, SUITE };
enum class RoomStatus { AVAILABLE, OCCUPIED, CLEANING };
enum class ReservationStatus { CONFIRMED, CANCELLED, CHECKED_IN, CHECKED_OUT };

// Forward Declarations
class Room;
class Guest;
class Reservation;

// ===================================
// == PERSON HIERARCHY ==
// ===================================
class Person {
protected: int id; string name;
public:
    Person(int id, string name) : id(id), name(name) {}
    virtual ~Person() {}
};

class Guest : public Person {
public:
    Guest(int id, string name) : Person(id, name) {}
};

class Staff : public Person {
public:
    Staff(int id, string name) : Person(id, name) {}
};

// ===================================
// == ROOM HIERARCHY ==
// ===================================
class Room {
protected:
    int roomNumber;
    RoomStatus status;
    double pricePerNight;
public:
    Room(int num, double price) : roomNumber(num), pricePerNight(price), status(RoomStatus::AVAILABLE) {}
    virtual RoomType getType() = 0; // Abstraction
    void updateStatus(RoomStatus newStatus) { status = newStatus; }
    bool isAvailable() { return status == RoomStatus::AVAILABLE; }
    virtual ~Room() {}
};

class SingleRoom : public Room { // Inheritance
public:
    SingleRoom(int num, double price) : Room(num, price) {}
    RoomType getType() override { return RoomType::SINGLE; } // Polymorphism
};
// ... (DoubleRoom, Suite classes)

// ===================================
// == CORE BUSINESS CLASSES ==
// ===================================
class Reservation {
private:
    int reservationId;
    Guest* guest;
    Room* room;
    time_t checkInDate;
    time_t checkOutDate;
    ReservationStatus status;
public:
    Reservation(int id, Guest* g, Room* r);
    void checkIn();
    void checkOut();
};

class Bill {
    // ... Bill related details
};

// ===================================
// == MAIN CONTROLLER (FACADE) ==
// ===================================
class Hotel {
private:
    string name;
    vector<Room*> rooms;
    map<int, Reservation*> reservations;
    vector<Staff*> staff;
    // Concurrency ke liye yahan mutex lagega
    // mutex mtx;
public:
    Hotel(string name);
    ~Hotel();
    void addRoom(Room* room);
    
    // Core functionalities used by staff
    vector<Room*> searchAvailableRooms(RoomType type, time_t from, time_t to);
    Reservation* createReservation(Guest* guest, Room* room);
    void checkIn(int reservationId);
    Bill* checkOut(int reservationId);
};

// main function jahan se program shuru hoga
int main() {
    cout << "Hotel Management System Design Ready!" << endl;
    
    // System setup karna
    Hotel myHotel("Prayagraj Grand");
    myHotel.addRoom(new SingleRoom(101, 3000.0));
    myHotel.addRoom(new SingleRoom(102, 3000.0));

    Guest* guest1 = new Guest(1, "Suresh");

    // Staff ka workflow:
    // 1. Staff ek single room search karta hai.
    cout << "\nSingle room search kiye ja rahe hain..." << endl;
    vector<Room*> availableRooms = myHotel.searchAvailableRooms(RoomType::SINGLE, time(0), time(0) + 86400);

    // 2. Agar room milta hai, toh reservation banata hai.
    if (!availableRooms.empty()) {
        Room* roomToBook = availableRooms.front();
        Reservation* res = myHotel.createReservation(guest1, roomToBook);
        if (res) {
            cout << "Reservation safaltapurvak ho gaya!" << endl;
            // 3. Guest ko check-in karta hai.
            // myHotel.checkIn(res->getId());
        }
    } else {
        cout << "Is type ke kamre uplabdh nahi hain." << endl;
    }

    delete guest1;
    return 0;
}
```

---
Ek digital wallet system jaise Paytm ya Google Pay ka core design **`User`** aur uske **`Wallet`** par kendrit hota hai. System ka mukhya kaam **`Transaction`** (len-den) ko handle karna hai. In alag-alag transactions (jaise wallet-to-wallet transfer, bank-to-wallet transfer) ko handle karne ke liye **Strategy Design Pattern** sabse behtareen approach hai. Ek central **`WalletSystem`** class sabhi users, wallets, aur transactions ko manage karti hai, aur yeh sunishchit karti hai ki har len-den surakshit (secure) aur atomic ho.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * Users account bana sakenge aur unhe ek wallet milega.
      * Users apne link kiye hue bank account se wallet mein paise jod sakenge.
      * Users apne wallet se doosre user ke wallet mein paise bhej sakenge.
      * Har user apne saare len-den ka itihas (transaction history) dekh sakega.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Security:** Yeh sabse zaroori hai. Data encrypted hona chahiye aur transactions surakshit honi chahiye.
      * **Reliability & Consistency:** Transactions **ACID** (Atomic, Consistent, Isolated, Durable) honi chahiye. Ek fail hui transaction mein paisa kabhi "beech mein" nahi fasna chahiye.
      * **High Concurrency:** System ko ek hi samay par ho rahe laakhon transactions ko handle karna aana chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Hum core wallet-to-wallet aur bank-to-wallet transfer logic par focus kar rahe hain.
      * User authentication (login/password) ek alag module hai.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`User`:**

      * **Attributes:** `userId`, `name`, `phoneNumber`, `Wallet* wallet`.

2.  **`Wallet`:**

      * **Attributes:** `walletId`, `balance`.
      * **Methods:** `addMoney()`, `deductMoney()`. Yeh methods thread-safe hone chahiye.

3.  **`Transaction` (Abstract Class - Strategy Pattern):**

      * Yeh sabhi transaction types ke liye ek base class (blueprint) hai.
      * **Methods:** `execute()` (pure virtual - **Abstraction**).

4.  **Concrete Transactions (`WalletToWalletTransfer`, etc.):**

      * Yeh `Transaction` se inherit karenge (**Inheritance**).
      * **`WalletToWalletTransfer`:** Iske paas `fromWallet`, `toWallet`, aur `amount` hoga. Iska `execute()` method ek wallet se paise kaat kar doosre mein jodega, aur yeh poora kaam ek **atomic operation** mein hona chahiye (**Polymorphism**).
      * **`BankToWalletTransfer`:** Bank account se wallet mein paise add karega.

5.  **`WalletSystem` (Main Controller / Facade):**

      * Poore system ka entry point.
      * **Attributes:** `map<int, User*> users`.
      * **Methods:** `registerUser()`, `addMoneyToWallet()`, `sendMoney()`.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Composition:** `User` **has-a** `Wallet`.
  * **Strategy Pattern:** `WalletSystem` alag-alag kaam karne ke liye `Transaction` strategy ka istemal karta hai. `WalletToWalletTransfer` **is-a** `Transaction`.
  * **Association:** `User` ek ya ek se adhik `BankAccount` se juda ho sakta hai.

-----

### \#\# 4. Data Storage

  * Financial transactions ke liye **ACID properties** sunishchit karne ke liye ek atyant vishvasneeya **SQL database** (jaise PostgreSQL ya MySQL) anivarya hai. Balance aur transaction logs ko aise system mein store karna zaroori hai jo data consistency ki guarantee de.

-----

### \#\# 5. Concurrency

  * Yeh **atyant mahatvapurna** hai. Jab ek user paise bhejta hai, toh uske wallet se paise kaatna aur receiver ke wallet mein paise jodna, yeh dono kaam **atomically** hone chahiye.
  * Yeh **database transactions** ke zariye achieve kiya jaata hai. `BEGIN TRANSACTION -> DEBIT -> CREDIT -> COMMIT` ka kram yeh sunishchit karta hai ki agar koi bhi step fail hota hai, toh poora operation rollback ho jaata hai.

-----

### \#\# 6. Scalability

  * Paytm/Google Pay jaise system bade paimane par kaam karte hain. Iske liye zaroori hai:
      * **Microservices Architecture** (user service, wallet service, transaction service alag-alag).
      * **Database Sharding** (data ko user ID ke aadhar par alag-alag servers par baantna).
      * **Message Queues** (jaise Kafka) ka istemal karke transactions ko asynchronously handle karna.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * **Insufficient Balance:** Transaction ke `execute()` method ko aage badhne se pehle ise check karna chahiye.
  * **Invalid User/Recipient:** System ko receiver ke astitva (existence) ko validate karna chahiye.
  * **Bank API Failure:** Agar bank ka server down hai, toh `BankToWalletTransfer` ko ise handle karna chahiye.

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Strategy Pattern:** Yeh transaction logic ko main system se alag (decouple) karta hai, jisse भविष्य mein naye transaction types (jaise `WalletToMerchantPayment`) jodna aasan ho jaata hai.
  * **Single Responsibility Principle (SRP):** Har class ka ek kaam hai. `Wallet` sirf balance, `Transaction` classes transfer logic, aur `WalletSystem` high-level operations manage karta hai.
  * **Facade Pattern:** `WalletSystem` ek facade ki tarah kaam karta hai, jo `sendMoney` jaise saral API ke peeche ke complex actions (transaction object banana, use execute karna) ko chhipata hai.

-----

### \#\# 9. APIs

  * Ek surakshit RESTful API ka istemal hoga:
      * `POST /wallet/add-money`
      * `POST /wallet/transfer`
      * `GET /wallet/balance`
      * `GET /wallet/history`

-----

### \#\# Digital Wallet System ka C++ Code

```cpp
#include <bits/stdc++.h>
#include <mutex>
using namespace std;

// Forward Declarations
class User;
class Wallet;

// ===================================
// == TRANSACTION HIERARCHY (STRATEGY) ==
// ===================================
// Abstract class for all transactions
class Transaction {
public:
    virtual bool execute() = 0; // Abstraction
    virtual ~Transaction() {}
};

// Concrete strategy for wallet-to-wallet transfer
class WalletToWalletTransfer : public Transaction { // Inheritance
private:
    Wallet* fromWallet;
    Wallet* toWallet;
    double amount;
public:
    WalletToWalletTransfer(Wallet* from, Wallet* to, double amt);
    bool execute() override; // Polymorphism
};

// ===================================
// == CORE BUSINESS CLASSES ==
// ===================================
class Wallet {
private:
    int walletId;
    double balance;
    mutex balanceMutex; // Concurrency ke liye
public:
    Wallet(int id, double initialBalance);
    double getBalance();
    // Yeh methods thread-safe hone chahiye
    bool deductMoney(double amount);
    void addMoney(double amount);
};

class User {
private:
    int userId;
    string name;
    Wallet* wallet;
public:
    User(int id, string name, double initialBalance);
    ~User();
    Wallet* getWallet();
    string getName();
};

// ===================================
// == MAIN CONTROLLER (FACADE) ==
// ===================================
class WalletSystem {
private:
    map<int, User*> users;
public:
    ~WalletSystem();
    void registerUser(int id, string name, double initialBalance);
    User* getUser(int id);
    
    // Core functionalities
    bool sendMoney(int fromUserId, int toUserId, double amount);
    void addMoneyToWallet(int userId, double amount); // Bank se add karne ka simplified version
};

// Implementation of a transaction
bool WalletToWalletTransfer::execute() {
    // REAL-WORLD mein yeh ek DATABASE TRANSACTION ke andar hoga
    // BEGIN TRANSACTION;
    if (fromWallet->deductMoney(amount)) {
        toWallet->addMoney(amount);
        cout << "Transaction safal! " << amount << " transfer ho gaya." << endl;
        // COMMIT;
        return true;
    } else {
        cout << "Transaction fail! Insufficient balance." << endl;
        // ROLLBACK;
        return false;
    }
}
// Note: Other implementations are omitted for brevity.

// main function jahan se program shuru hoga
int main() {
    cout << "Digital Wallet System Design Ready!" << endl;

    WalletSystem paytm;
    paytm.registerUser(101, "Amit", 5000.0);
    paytm.registerUser(102, "Babita", 1000.0);

    User* amit = paytm.getUser(101);
    User* babita = paytm.getUser(102);

    cout << "\nShuruaati Balance:" << endl;
    cout << amit->getName() << ": " << amit->getWallet()->getBalance() << endl;
    cout << babita->getName() << ": " << babita->getWallet()->getBalance() << endl;

    cout << "\n--- Amit, Babita ko 2000 bhej raha hai ---" << endl;
    paytm.sendMoney(101, 102, 2000.0);

    cout << "\nAntim Balance:" << endl;
    cout << amit->getName() << ": " << amit->getWallet()->getBalance() << endl;
    cout << babita->getName() << ": " << babita->getWallet()->getBalance() << endl;

    cout << "\n--- Amit, Babita ko 4000 bhej raha hai (Fail hona chahiye) ---" << endl;
    paytm.sendMoney(101, 102, 4000.0);

    cout << "\nAntim Balance (koi badlav nahi):" << endl;
    cout << amit->getName() << ": " << amit->getWallet()->getBalance() << endl;
    cout << babita->getName() << ": " << babita->getWallet()->getBalance() << endl;

    return 0;
}
```

---

Ek airline management system ka core design ek central **`Airline`** class ke ird-gird banta hai, jo airline ki poori operations ko manage karti hai. Ismein airline ka **`Fleet`** (vimaanon ka Beda), uska **`Staff`** (pilots, crew), nirdharit \*\*`Flight`\*\*s ka schedule, aur yaatriyon (passengers) ki \*\*`Booking`\*\*s shaamil hoti hain. Yeh design alag-alag modules jaise flight scheduling, crew assignment, aur passenger reservation ko ek saath jodta hai.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * **Fleet Management:** Airline apne **`Aircraft`** (vimaan) ke bede ko manage karegi. Har vimaan ka model, capacity, aur status (active, maintenance mein) hoga.
      * **Staff Management:** Airline apne **`Staff`** (karmchaari), jaise `Pilot` aur `CabinCrew`, ko manage karegi.
      * **Flight Scheduling:** Airline alag-alag shehron ke beech \*\*`Flight`\*\*s ka schedule banayegi aur manage karegi.
      * **Passenger Reservation:** Yaatri (passengers) flights search karke **`Booking`** kar sakenge.
      * **Check-in:** System passenger check-in aur boarding pass generation ko handle karega.

  * **Non-Functional Requirements (Performance, etc.):**

      * **High Availability:** Booking aur flight status system hamesha online aur uplabdh rehna chahiye.
      * **Concurrency:** Hazaron users aur travel agents ek hi samay par flights book kar rahe honge; system ko ise handle karna aana chahiye.
      * **Data Consistency:** Seat availability aur flight schedule ki jaankari poore system mein hamesha sateek honi chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Hum airline ke internal management ke liye backend system design kar rahe hain.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`Person` (Abstract Class):**

      * **Attributes:** `personId`, `name`.
      * **Derived Classes:** `Passenger` aur `Staff`.

2.  **`Staff` (Abstract Class, Person se Inherited):**

      * **Attributes:** `employeeId`.
      * **Derived Classes:** `Pilot` (jiske paas license number hoga) aur `CabinCrew`.

3.  **`Aircraft`:**

      * **Attributes:** `tailNumber`, `model`, `seatLayout`.

4.  **`Flight`:**

      * Ek nirdharit yatra (scheduled journey).
      * **Attributes:** `flightNumber`, `origin`, `destination`, `departureTime`, `aircraft` (Aircraft\*), `vector<Staff*> crew`.

5.  **`Booking`:**

      * **Attributes:** `bookingId`, `passenger`, `flight`, `seatNumber`.

6.  **`Airline` (Main Controller / Facade):**

      * Poore system ko manage karta hai.
      * **Attributes:** `vector<Aircraft*> fleet`, `vector<Staff*> staff`, `vector<Flight*> flightSchedule`.
      * **Methods:** `addAircraft()`, `scheduleFlight()`, `assignCrewToFlight()`, `makeBooking()`.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Composition:** `Airline` **has-a** `Fleet` (vector of `Aircraft`).
  * **Inheritance:** `Pilot` **is-a** `Staff`, aur `Staff` **is-a** `Person`.
  * **Association:** `Flight` ko ek `Aircraft` aur `Crew` (staff) **assign** kiya jaata hai. `Booking` ek `Passenger` ko ek `Flight` se jodti hai.

-----

### \#\# 4. Data Storage

  * Is complex system ke liye ek vishvasneeya **Relational Database (SQL)** zaroori hai, taaki flights, schedules, bookings, aur staff ke beech ke complex rishton ko aasaani se manage kiya ja sake.

-----

### \#\# 5. Concurrency

  * **Booking:** Ek hi seat ko do logon dwara ek saath book hone se rokne ke liye booking process **atomic** hona chahiye. Yeh **database transactions** ke zariye kiya jaata hai.
  * **Crew/Aircraft Assignment:** Ek hi pilot ya vimaan ko do alag-alag overlapping flights par assign karne se rokne ke liye bhi transactional logic zaroori hai.

-----

### \#\# 6. Scalability

  * Ek global airline ka system bahut bada aur distributed hota hai. Iske liye zaroori hai:
      * **Microservices Architecture** (booking service, scheduling service, crew service alag-alag).
      * Poori duniya mein users ke liye latency kam karne ke liye **Data Replication**.
      * Flight search ko tez karne ke liye **Caching**.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * Flight mein koi seat uplabdh na hona.
  * Ek aise aircraft ya crew member ko schedule karna jo pehle se hi kisi doosri flight par assigned ho.
  * Flight ka cancel ya delay hona (jiske baad notification process shuru hoga).

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Single Responsibility Principle (SRP):** Har class ka ek kaam hai: `Aircraft` vimaan ka data, `Flight` schedule ka data, `Booking` reservation ka data, aur `Airline` sabko coordinate karta hai.
  * **Open/Closed Principle (OCP):** `Staff` ki hierarchy se hum naye employee types (jaise `GroundStaff`) jod sakte hain bina maujooda system ko badle.
  * **Facade Pattern:** `Airline` class ek facade ki tarah kaam karti hai, jo flight schedule karne jaise complex operations ke liye ek saral interface pradan karti hai.

-----

### \#\# 9. APIs

  * System ke paas multiple APIs honge:
      * **Public API** (travel websites ke liye): `GET /flights/search`, `POST /bookings`.
      * **Internal API** (airline staff ke liye): `POST /flights/schedule`, `POST /flights/{id}/assign-crew`.

-----

### \#\# Airline Management System ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class Flight;
class Aircraft;
class Staff;
class Passenger;
class Booking;

// ===================================
// == PERSON HIERARCHY ==
// ===================================
class Person {
protected: int id; string name;
public:
    Person(int id, string name) : id(id), name(name) {}
    virtual void displayDetails() = 0; // Abstraction
    virtual ~Person() {}
};

class Passenger : public Person {
public:
    Passenger(int id, string name) : Person(id, name) {}
    void displayDetails() override; // Polymorphism
};

class Staff : public Person { // Abstract class
protected: int employeeId;
public:
    Staff(int id, string name, int empId) : Person(id, name), employeeId(empId) {}
};

class Pilot : public Staff { // Inheritance
public:
    Pilot(int id, string name, int empId) : Staff(id, name, empId) {}
    void displayDetails() override;
};
// ... (CabinCrew class)

// ===================================
// == FLEET & FLIGHT CLASSES ==
// ===================================
class Aircraft {
private:
    string tailNumber;
    string model;
    int capacity;
public:
    Aircraft(string tailNum, string model, int cap);
};

class Flight {
private:
    string flightNumber;
    string origin;
    string destination;
    time_t departureTime;
    Aircraft* aircraft;
    vector<Staff*> crew;
public:
    Flight(string fNum, string orig, string dest, time_t depTime);
    void assignAircraft(Aircraft* ac);
    void assignCrew(const vector<Staff*>& crewMembers);
};

class Booking {
private:
    string bookingId;
    Passenger* passenger;
    Flight* flight;
    string seatNumber;
public:
    Booking(string id, Passenger* p, Flight* f, string seat);
};

// ===================================
// == MAIN CONTROLLER (FACADE) ==
// ===================================
class Airline {
private:
    string name;
    vector<Aircraft*> fleet;
    vector<Staff*> staffMembers;
    map<string, Flight*> flightSchedule;
    map<string, Booking*> bookings;
    // Concurrency ke liye yahan mutex lagega
    // mutex mtx;
public:
    Airline(string name);
    ~Airline();
    
    // Management Functions
    void addAircraft(Aircraft* aircraft);
    void hireStaff(Staff* staff);
    void scheduleFlight(string fNum, string orig, string dest, time_t depTime);
    
    // Operational Functions
    bool assignCrewToFlight(string flightNumber, vector<int> crewIds);
    Booking* makeBooking(Passenger* passenger, string flightNumber, string seatPref);
};

// main function jahan se program shuru hoga
int main() {
    cout << "Airline Management System Design Ready!" << endl;

    // System setup karna
    Airline myAirline("Prayag Air");
    myAirline.addAircraft(new Aircraft("VT-PGR", "Airbus A320", 180));
    myAirline.hireStaff(new Pilot(1, "Capt. Sharma", 101));
    myAirline.hireStaff(new Pilot(2, "Capt. Verma", 102));

    // Ek flight schedule karna
    time_t now = time(0);
    myAirline.scheduleFlight("PA-101", "IXD", "DEL", now + 3600*24);

    // Flight par crew assign karna
    myAirline.assignCrewToFlight("PA-101", {101, 102});
    
    // Ek passenger ke liye booking banana
    Passenger* passenger = new Passenger(1, "Amit");
    myAirline.makeBooking(passenger, "PA-101", "14A");

    cout << "\nFlight PA-101 schedule ho gayi hai aur ek booking bhi ho gayi hai." << endl;

    return 0;
}
```
---
Ek library management system ka core design ek central **`Library`** class par aadharit hai jo \*\*`Book`\*\*s (aur anya `LibraryItem`s) ke catalog aur panjeekrt (registered) \*\*`Member`\*\*s ki soochi ko manage karti hai. Iski mukhya prakriya (core process) ek `Member` dwara `Book` udhaar lena hai, jisse ek **`Loan`** (len-den) ka record banta hai. System due dates ko track karta hai aur der se lautayi gayi kitabon par **`Fine`** (jurmana) lagata hai.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * Library mein **Books** (aur anya items jaise magazines) ka ek catalog hoga.
      * **Members** library mein register kar sakenge.
      * Members kitabon ko khoj (search) aur udhaar (borrow) le sakenge.
      * System ko yeh track karna hoga ki kaun si kitab kis member ke paas hai aur uski due date kya hai.
      * System kitabon ki vapasi (return) ko handle karega.
      * System der se lautayi gayi kitabon par **jurmana (fine)** lagayega aur manage karega.
      * Librarian naye members aur kitabon ko jod ya hata sakenge.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Concurrency:** Ek hi samay par kai members aur librarians system ka istemal kar sakte hain.
      * **Data Persistence:** Catalog, members, aur loans ki jaankari sthayi roop se save honi chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Hum system ke backend logic par focus kar rahe hain.
      * Jurmana har din ke liye ek nishchit dar (fixed rate) par lagta hai.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`LibraryItem` (Abstract Class):**

      * Library ki sabhi udhaar di jaane wali vastuo ke liye ek base class.
      * **Attributes:** `itemId`, `title`.
      * **Methods:** `getLoanDuration()` (pure virtual - **Abstraction**).

2.  **`Book`, `Magazine` (Concrete Classes):**

      * Yeh `LibraryItem` se inherit karenge (**Inheritance**).
      * `Book` ke paas `author` aur `isbn` hoga. `Magazine` ke paas `issueNumber` hoga.
      * Yeh `getLoanDuration()` ko apne hisaab se implement karenge (**Polymorphism**).

3.  **`Member`:**

      * **Attributes:** `memberId`, `name`, `vector<Loan*> borrowedItems`.
      * **Methods:** `borrowItem()`, `returnItem()`.

4.  **`Loan`:**

      * Ek `Member` aur `LibraryItem` ko jodne wali class.
      * **Attributes:** `item`, `member`, `issueDate`, `dueDate`.

5.  **`Fine`:**

      * **Attributes:** `loan`, `amount`.
      * **Methods:** `calculateFine()`.

6.  **`Library` (Main Controller / Facade):**

      * Poore system ke operations ko manage karta hai.
      * **Attributes:** `map<int, LibraryItem*> catalog`, `map<int, Member*> members`, `map<int, Loan*> activeLoans`.
      * **Methods:** `addMember()`, `addBook()`, `checkoutItem()`, `returnItem()`.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Composition:** `Library` **has-a** `catalog`. `Member` **has-many** `Loan`s.
  * **Inheritance:** `Book` aur `Magazine` **is-a** `LibraryItem`.
  * **Association:** `Loan` ek `Member` aur ek `LibraryItem` ko jodta hai.

-----

### \#\# 4. Data Storage

  * Is system ke liye ek **Relational Database (SQL)** sabse upyukt hai, kyunki ismein books, members, aur loans ke beech structured data aur relationships hote hain.

-----

### \#\# 5. Concurrency

  * Jab do members ek hi kitab ki aakhiri copy ko ek saath udhaar lene ki koshish karte hain, toh system ko yeh sunishchit karna hoga ki sirf ek hi safal ho.
  * Kitab ki uplabdhata check karne aur use udhaar mark karne ka process **atomic** hona chahiye. Yeh **database transactions** ke zariye handle kiya jaata hai.

-----

### \#\# 6. Scalability

  * Agar library ki kai shaakhayein (branches) hain, toh database ko alag-alag locations ki inventory handle karne ke liye design karna hoga. `Library` class ek branch ko represent kar sakti hai aur ek `LibraryNetwork` class kai branches ko manage kar sakti hai.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * Kitab udhaar lene ke liye uplabdh nahi hai.
  * Member ne apni udhaar lene ki seema (limit) paar kar li hai.
  * Invalid member ID ya book ID.

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Single Responsibility Principle (SRP):** Har class ka ek kaam hai. `Loan` ek len-den, `Fine` jurmana, aur `Library` poore operations ko manage karta hai.
  * **Open/Closed Principle (OCP):** `LibraryItem` abstract class se hum भविष्य mein naye types ke items (jaise `DVD`, `AudioBook`) jod sakte hain bina `Library` class ko badle.
  * **Facade Pattern:** `Library` class ek facade ki tarah kaam karti hai, jo `checkoutItem` jaise saral interface ke peeche ke complex operations ko chhipati hai.

-----

### \#\# 9. APIs

  * Ek modern web-based library system ke liye REST APIs honge:
      * `GET /books/search?q={title}`
      * `POST /members/{memberId}/checkout`
      * `POST /loans/{loanId}/return`

-----

### \#\# Library Management System ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class LibraryItem;
class Member;
class Loan;

// ===================================
// == LIBRARY ITEM HIERARCHY ==
// ===================================
// Abstract class for all library items
class LibraryItem {
protected:
    int itemId;
    string title;
    bool isAvailable;
public:
    LibraryItem(int id, string title) : itemId(id), title(title), isAvailable(true) {}
    virtual void display() = 0; // Abstraction
    virtual int getLoanDuration() = 0;
    void setAvailability(bool status) { isAvailable = status; }
    bool checkAvailability() { return isAvailable; }
    virtual ~LibraryItem() {}
};

// Concrete item: Book
class Book : public LibraryItem { // Inheritance
private:
    string author;
public:
    Book(int id, string title, string author) : LibraryItem(id, title), author(author) {}
    void display() override { // Polymorphism
        cout << "Book: " << title << " by " << author << endl;
    }
    int getLoanDuration() override { return 14; } // 14 din
};

// Concrete item: Magazine
class Magazine : public LibraryItem {
public:
    Magazine(int id, string title) : LibraryItem(id, title) {}
    void display() override {
        cout << "Magazine: " << title << endl;
    }
    int getLoanDuration() override { return 7; } // 7 din
};

// ===================================
// == CORE BUSINESS CLASSES ==
// ===================================
class Member {
private:
    int memberId;
    string name;
    vector<Loan*> borrowedItems;
public:
    Member(int id, string name) : memberId(id), name(name) {}
    string getName() { return name; }
    int getId() { return memberId; }
};

class Loan {
private:
    LibraryItem* item;
    Member* member;
    time_t issueDate;
    time_t dueDate;
public:
    Loan(LibraryItem* i, Member* m) : item(i), member(m) {
        issueDate = time(0);
        // dueDate = issueDate + (item->getLoanDuration() * 24 * 60 * 60);
    }
    void display() {
        cout << "Loan Details: " << endl;
        item->display();
        cout << "Borrowed by: " << member->getName() << endl;
    }
};

class Fine {
    // ... Fine calculation logic
};

// ===================================
// == MAIN CONTROLLER (FACADE) ==
// ===================================
class Library {
private:
    map<int, LibraryItem*> catalog;
    map<int, Member*> members;
    vector<Loan*> activeLoans;
    // Concurrency ke liye yahan mutex lagega
    // mutex mtx;
public:
    ~Library() {
        for(auto const& [key, val] : catalog) delete val;
        for(auto const& [key, val] : members) delete val;
    }

    void addBook(int id, string title, string author) {
        catalog[id] = new Book(id, title, author);
        cout << "Kitab '" << title << "' library mein jodi gayi." << endl;
    }

    void addMember(int id, string name) {
        members[id] = new Member(id, name);
        cout << "Naya sadasya '" << name << "' joda gaya." << endl;
    }

    // Core functionality
    void checkoutItem(int memberId, int itemId) {
        if (members.count(memberId) && catalog.count(itemId)) {
            LibraryItem* item = catalog[itemId];
            if (item->checkAvailability()) {
                item->setAvailability(false);
                Member* member = members[memberId];
                Loan* loan = new Loan(item, member);
                activeLoans.push_back(loan);
                cout << member->getName() << " ne safaltapurvak kitab udhaar li." << endl;
                loan->display();
            } else {
                cout << "Maaf kijiye, yeh kitab abhi uplabdh nahi hai." << endl;
            }
        }
    }
    
    void returnItem(int itemId) {
         if (catalog.count(itemId)) {
            LibraryItem* item = catalog[itemId];
            item->setAvailability(true);
            cout << "Kitab '" << item->display() , "' safaltapurvak vapis ho gayi." << endl;
            // Yahan loan record hatane aur fine check karne ka logic aayega
         }
    }
};

// main function jahan se program shuru hoga
int main() {
    Library myLibrary;
    myLibrary.addMember(101, "Amit Kumar");
    myLibrary.addBook(1, "The C++ Programming Language", "Bjarne Stroustrup");

    cout << "\n--- Checkout Prakriya ---" << endl;
    myLibrary.checkoutItem(101, 1);

    cout << "\n--- Return Prakriya ---" << endl;
    myLibrary.returnItem(1);

    return 0;
}
```

---

Ek restaurant management system ka core design `Restaurant` class ke ird-gird hota hai, jo alag-alag components ko orchestrate karti hai. Iske mukhya hisse hain: **`Menu`** (jismein `MenuItem`s hote hain), \*\*`Table`\*\*s, aur **`Order`s**. Ek `Staff` member (jaise `Waiter`) kisi `Table` ke liye ek `Order` leta hai. Is `Order` mein kai `MenuItem`s ho sakte hain. Khana poora hone par, us `Order` ke liye ek **`Bill`** banaya jaata hai aur **`Payment`** process kiya jaata hai.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * System ko ek **Menu** manage karna hoga, jismein food items aur unke daam honge.
      * Restaurant ke **Tables** ko manage karna hoga, jismein unka status (`AVAILABLE`, `OCCUPIED`) shamil hai.
      * **Waiters** tables ke liye **Orders** bana, badal, aur close kar sakenge.
      * Kitchen ko naye orders ki soochana (notification) milni chahiye.
      * System ko order ke liye tax jodkar **Bill** banana aana chahiye.
      * System ko **Payments** process karna aana chahiye.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Concurrency:** Kai waiters ek hi samay par alag-alag tables par order le rahe honge.
      * **Reliability:** Order aur billing ki jaankari hamesha sateek honi chahiye aur kho nahi jaani chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Hum restaurant ke staff dwara istemal kiye jaane wale internal system ko design kar rahe hain.
      * Yeh design ek single restaurant location ke liye hai.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`MenuItem`:**

      * **Attributes:** `itemId`, `name`, `price`.

2.  **`Menu`:**

      * **Attributes:** `map<int, MenuItem*> items`.
      * **Methods:** `addItem()`, `getMenuItem()`.

3.  **`Table`:**

      * **Attributes:** `tableId`, `capacity`, `TableStatus status`.
      * **Methods:** `updateStatus()`.

4.  **`Person` / `Staff` (Hierarchy):**

      * Abstract base class `Person`.
      * Isse inherited `Staff` abstract class, jiske paas `employeeId` hoga.
      * `Staff` se inherited concrete classes jaise `Waiter`, `Chef`, `Manager`.

5.  **`Order`:**

      * **Attributes:** `orderId`, `table`, `waiter`, `map<MenuItem*, int> orderedItems` (item aur uski quantity), `OrderStatus status` (RECEIVED, PREPARING, COMPLETED).
      * **Methods:** `addItem()`, `updateStatus()`.

6.  **`Bill`:**

      * **Attributes:** `billId`, `order`, `subTotal`, `tax`, `totalAmount`.
      * **Methods:** `generateBill()`.

7.  **`Restaurant` (Main Controller / Facade):**

      * Poore system ke operations ko manage karta hai.
      * **Attributes:** `Menu* menu`, `vector<Table*> tables`, `vector<Staff*> staff`, `map<int, Order*> activeOrders`.
      * **Methods:** `takeOrder()`, `generateBillForTable()`, `processPayment()`.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Composition:** `Restaurant` **has-a** `Menu`. `Order` **has-many** `MenuItem`s.
  * **Inheritance:** `Waiter` **is-a** `Staff`, aur `Staff` **is-a** `Person`.
  * **Association:** Ek `Waiter` ek `Order` banata hai, jo ek `Table` se juda hota hai.

-----

### \#\# 4. Data Storage

  * Ek Point of Sale (POS) system ke liye **Relational Database (SQL)** upyukt hai, jismein menu, orders, aur staff ki jaankari ko structured tareeke se store kiya ja sakta hai.

-----

### \#\# 5. Concurrency

  * Jab kai waiters ek saath order le rahe hote hain, toh concurrency zaroori hai.
  * Ek `Table` ka status (`AVAILABLE` se `OCCUPIED`) update karna ek **atomic** operation hona chahiye taaki do waiter ek hi table ko assign na kar dein. Iske liye **locks** ya **database transactions** ka istemal hota hai.

-----

### \#\# 6. Scalability

  * Yeh design ek restaurant ke liye hai. Agar restaurants ki chain manage karni ho, toh ek `RestaurantChainManager` class banayi ja sakti hai jo multiple `Restaurant` objects ko manage karegi.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * Ek aisi table ke liye order lene ki koshish karna jo pehle se occupied hai.
  * Ek aisa item order karna jo menu mein nahi hai ya out of stock hai.
  * Payment fail ho jaana.

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Single Responsibility Principle (SRP):** Har class ka ek kaam hai: `Menu` food items, `Order` ek order ki life-cycle, aur `Bill` financial hisaab manage karta hai.
  * **Open/Closed Principle (OCP):** `Staff` ki hierarchy se hum भविष्य mein naye roles (jaise `Host`) jod sakte hain bina maujooda system ko badle.
  * **Facade Pattern:** `Restaurant` class ek facade ki tarah kaam karti hai, jo staff ke liye `takeOrder` jaise saral methods pradan karti hai.

-----

### \#\# 9. APIs

  * Ek modern system (jismein waiters tablet istemal karte hain) ke liye REST APIs honge:
      * `GET /menu`: Menu dekhne ke liye.
      * `POST /orders`: Naya order banane ke liye.
      * `PUT /orders/{id}`: Maujooda order mein item add karne ke liye.
      * `GET /tables/{id}/bill`: Bill generate karne ke liye.

-----

### \#\# Restaurant Management System ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Enums for clarity
enum class TableStatus { AVAILABLE, OCCUPIED, RESERVED };
enum class OrderStatus { RECEIVED, PREPARING, COMPLETED, PAID };

// Forward Declarations
class MenuItem;
class Table;
class Waiter;
class Order;

// ===================================
// == MENU & ITEMS ==
// ===================================
class MenuItem {
public:
    int id;
    string name;
    double price;
    MenuItem(int id, string name, double price) : id(id), name(name), price(price) {}
};

class Menu {
private:
    map<int, MenuItem*> items;
public:
    void addItem(MenuItem* item) { items[item->id] = item; }
    MenuItem* getItem(int id) { return items.count(id) ? items[id] : nullptr; }
};

// ===================================
// == PEOPLE & STAFF ==
// ===================================
class Person {
protected: int id; string name;
public:
    Person(int id, string name) : id(id), name(name) {}
};

class Waiter : public Person {
public:
    Waiter(int id, string name) : Person(id, name) {}
    Order* createOrder(Table* table);
};

// ===================================
// == CORE BUSINESS CLASSES ==
// ===================================
class Table {
public:
    int id;
    int capacity;
    TableStatus status;
    Table(int id, int cap) : id(id), capacity(cap), status(TableStatus::AVAILABLE) {}
    void updateStatus(TableStatus newStatus) { status = newStatus; }
};

class Order {
private:
    int id;
    Table* table;
    Waiter* waiter;
    map<MenuItem*, int> orderedItems; // Item aur uski quantity
    OrderStatus status;
public:
    Order(int id, Table* t, Waiter* w) : id(id), table(t), waiter(w), status(OrderStatus::RECEIVED) {}
    void addItem(MenuItem* item, int quantity) {
        orderedItems[item] += quantity;
        cout << quantity << "x " << item->name << " order mein joda gaya." << endl;
    }
    double calculateTotal() {
        double total = 0;
        for (auto const& [item, qty] : orderedItems) {
            total += item->price * qty;
        }
        return total;
    }
};

class Bill {
public:
    Order* order;
    double totalAmount;
    Bill(Order* o) : order(o) {
        totalAmount = order->calculateTotal(); // Simplified, tax etc. can be added
    }
    void print() {
        cout << "\n--- Bill ---" << endl;
        cout << "Total Amount: " << totalAmount << endl;
        cout << "------------" << endl;
    }
};

// ===================================
// == MAIN CONTROLLER (FACADE) ==
// ===================================
class Restaurant {
private:
    Menu* menu;
    vector<Table*> tables;
    vector<Waiter*> waiters;
    map<int, Order*> activeOrders;
public:
    Restaurant() {
        menu = new Menu();
    }
    void addTable(Table* t) { tables.push_back(t); }
    void hireWaiter(Waiter* w) { waiters.push_back(w); }
    Menu* getMenu() { return menu; }

    // Waiter ek order leta hai
    void takeOrder(Waiter* waiter, Table* table, const vector<pair<int, int>>& itemsToOrder) {
        if (table->status != TableStatus::AVAILABLE) {
            cout << "Yeh table abhi uplabdh nahi hai." << endl;
            return;
        }
        table->updateStatus(TableStatus::OCCUPIED);
        
        static int orderIdCounter = 1;
        Order* order = new Order(orderIdCounter++, table, waiter);
        activeOrders[table->id] = order;

        for (const auto& p : itemsToOrder) {
            MenuItem* item = menu->getItem(p.first);
            if (item) {
                order->addItem(item, p.second);
            }
        }
    }

    Bill* generateBillForTable(int tableId) {
        if (activeOrders.count(tableId)) {
            return new Bill(activeOrders[tableId]);
        }
        return nullptr;
    }
};

// main function jahan se program shuru hoga
int main() {
    // Restaurant setup karna
    Restaurant myRestaurant;
    myRestaurant.addTable(new Table(1, 4));
    myRestaurant.hireWaiter(new Waiter(101, "Ramesh"));
    
    Menu* menu = myRestaurant.getMenu();
    menu->addItem(new MenuItem(1, "Paneer Butter Masala", 250.0));
    menu->addItem(new MenuItem(2, "Butter Naan", 40.0));

    // Ek waiter order leta hai
    cout << "--- Naya Order ---" << endl;
    myRestaurant.takeOrder(
        new Waiter(101, "Ramesh"),  // Simplified
        new Table(1, 4),           // Simplified
        {{1, 2}, {2, 4}}           // 2 Paneer Butter Masala, 4 Butter Naan
    );
    
    // Us table ke liye bill generate karna
    Bill* bill = myRestaurant.generateBillForTable(1);
    if (bill) {
        bill->print();
    }

    return 0;
}
```
---
Ek concert ticket booking system ka core design ek central **`BookingPlatform`** par aadharit hai jo alag-alag **`Event`s** (concerts) ko manage karta hai. Har `Event` ek **`Venue`** (sthal) par hota hai, jiska apna ek seating layout hota hai. Is layout mein alag-alag prakar ki \*\*`Seat`\*\*s (jaise General Admission, VIP) hoti hain. Ek **`User`** events ko search karke, seats select karta hai, aur ek **`Booking`** banata hai, jo aakhir mein **`Payment`** ke baad confirm hoti hai. Is system ki sabse badi chunauti (challenge) seat inventory ko achanak aane wale high traffic (flash crowd) ke dauraan aane wali **concurrency** ko manage karna hai.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * System mein multiple **Events** (concerts) list honge.
      * Har event ki details hongi jaise artist, date, time, aur **Venue**.
      * Har venue ka ek seating map hoga jismein alag-alag **Seat** categories (`VIP`, `General Admission`) aur unke daam honge.
      * **Users** events search kar sakenge.
      * User ek event ke liye ek ya ek se adhik seats select kar sakenge.
      * System ko seat select karne par use thodi der (jaise 10 minute) ke liye **lock** karna hoga taaki user payment kar sake.
      * Payment safal hone par **Booking** confirm hogi aur ticket generate hoga.

  * **Non-Functional Requirements (Performance, etc.):**

      * **High Concurrency:** Mashhoor concerts ke liye, tickets sale shuru hote hi hazaron users ek saath tickets book karne ki koshish karenge. System ko is "flash crowd" ko handle karna aana chahiye.
      * **High Availability:** Peak booking time par system hamesha online aur responsive rehna chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Hum core booking flow design kar rahe hain.
      * Seat lock karne ka samay 10 minute hai.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`User`:**

      * **Attributes:** `userId`, `name`.

2.  **`Seat` (Abstract Class):**

      * **Attributes:** `seatId`, `price`, `SeatStatus status` (AVAILABLE, LOCKED, BOOKED).
      * **Methods:** `getType()` (pure virtual - **Abstraction**).

3.  **Concrete Seats (`GeneralAdmissionSeat`, `SeatedSeat`):**

      * `Seat` se inherit karenge (**Inheritance**).
      * `SeatedSeat` ke paas `row` aur `number` jaise extra attributes honge.

4.  **`Venue`:**

      * **Attributes:** `venueId`, `name`, `address`, `map<int, Seat*> seatingMap`.

5.  **`Event`:**

      * **Attributes:** `eventId`, `eventName`, `artist`, `venue` (Venue\*), `dateTime`.

6.  **`Booking`:**

      * **Attributes:** `bookingId`, `user`, `event`, `vector<Seat*> seats`, `totalAmount`, `BookingStatus status` (PENDING\_PAYMENT, CONFIRMED).

7.  **`BookingPlatform` (Main Controller / Facade):**

      * Poore system ke operations ko manage karta hai.
      * **Attributes:** `map<int, Event*> events`, `map<int, User*> users`.
      * **Methods:** `listEvents()`, `createBooking()`, `confirmBooking()`.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Composition:** `Venue` **has-many** `Seat`s. `Booking` **has-many** `Seat`s.
  * **Inheritance:** `SeatedSeat` **is-a** `Seat`.
  * **Association:** `Event` ek `Venue` par hota hai. `Booking` ek `User` aur ek `Event` ko jodta hai.

-----

### \#\# 4. Data Storage

  * Is tarah ke system ke liye databases ka combination istemal hota hai:
      * **Relational Database (SQL):** Confirmed bookings, users, aur events jaise structured data ke liye.
      * **In-memory Cache with TTL (jaise Redis):** Temporary seat locks ko manage karne ke liye. Jab user seat select karta hai, toh seat ka status `LOCKED` Redis mein 10 minute ki expiry ke saath set ho jaata hai. Yeh main database par load kam karta hai.

-----

### \#\# 5. Concurrency

  * Yeh is system ki **sabse badi chunauti** hai.
  * **Seat Locking:** Ek seat ko select karne aur use doosre users ke liye unavailable mark karne ka process **atomic** hona chahiye. Iske liye Redis jaise fast, distributed cache ke atomic operations (`SETNX` - set if not exists) ek standard solution hain.
  * Final booking ko confirm karne ke liye **database transactions** ka istemal hota hai.

-----

### \#\# 6. Scalability

  * System ko highly scalable aur distributed architecture par banana zaroori hai.
  * **Load Balancers** aane wale traffic ko alag-alag servers par baantne ke liye.
  * **Virtual Queue/Waiting Room:** High-demand events ke liye, users ko booking page par aane se pehle ek virtual line mein rakha jaata hai taaki backend par load manage ho sake.
  * **Microservices:** Event listing, booking, aur payment ke liye alag-alag services.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * Select ki gayi seats ab uplabdh nahi hain (kisi aur ne book kar li).
  * Payment fail ho jaana.
  * User dwara 10 minute mein payment na karne par seat lock ka expire ho jaana (system ko seats ko automatically release kar dena chahiye).

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Single Responsibility Principle (SRP):** Har class ka ek kaam hai: `Venue` apni seating, `Event` apni details, aur `Booking` transaction manage karta hai.
  * **Open/Closed Principle (OCP):** `Seat` ki hierarchy se hum भविष्य mein naye seat types (jaise `BoxSeat`) aasani se add kar sakte hain.
  * **Facade Pattern:** `BookingPlatform` class ek facade ki tarah kaam karti hai, jo events search karne aur booking karne jaise complex process ke liye ek saral interface pradan karti hai.

-----

### \#\# 9. APIs

  * Ek real-world system mein REST APIs honge:
      * `GET /events/search?artist={name}`
      * `GET /events/{id}/seats`: Ek event ke liye seating map aur availability dekhne ke liye.
      * `POST /bookings`: Ek temporary booking banane aur seats lock karne ke liye.
      * `POST /bookings/{id}/confirm`: Payment ke baad booking confirm karne ke liye.

-----

### \#\# Concert Ticket Booking System ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Enums for clarity
enum class SeatType { GENERAL_ADMISSION, SEATED, VIP };
enum class SeatStatus { AVAILABLE, LOCKED, BOOKED };
enum class BookingStatus { PENDING, CONFIRMED, CANCELLED };

// Forward Declarations
class User;
class Event;
class Seat;
class Booking;

// ===================================
// == SEAT HIERARCHY ==
// ===================================
class Seat {
protected:
    int id;
    double price;
    SeatStatus status;
public:
    Seat(int id, double price) : id(id), price(price), status(SeatStatus::AVAILABLE) {}
    virtual SeatType getType() = 0; // Abstraction
    void lock() { status = SeatStatus::LOCKED; }
    void book() { status = SeatStatus::BOOKED; }
    bool isAvailable() { return status == SeatStatus::AVAILABLE; }
    virtual ~Seat() {}
};

class SeatedSeat : public Seat { // Inheritance
private:
    string row;
    int number;
public:
    SeatedSeat(int id, double price, string row, int num) : Seat(id, price), row(row), number(num) {}
    SeatType getType() override { return SeatType::SEATED; } // Polymorphism
};
// ... (GeneralAdmissionSeat, VipSeat classes)


// ===================================
// == CORE BUSINESS CLASSES ==
// ===================================
class Venue {
private:
    int id;
    string name;
    map<int, Seat*> seatingMap;
public:
    Venue(int id, string name);
    void addSeat(Seat* seat);
    Seat* getSeat(int seatId);
};

class Event {
private:
    int id;
    string name;
    Venue* venue;
public:
    Event(int id, string name, Venue* v) : id(id), name(name), venue(v) {}
    Venue* getVenue() { return venue; }
    string getName() { return name; }
};

class User {
public:
    int id;
    string name;
    User(int id, string name) : id(id), name(name) {}
};

class Booking {
private:
    int id;
    User* user;
    Event* event;
    vector<Seat*> seats;
    BookingStatus status;
public:
    Booking(int id, User* u, Event* e, const vector<Seat*>& s);
    void confirmBooking();
};

// ===================================
// == MAIN CONTROLLER (FACADE) ==
// ===================================
class BookingPlatform {
private:
    map<int, Event*> events;
    map<int, User*> users;
    // Concurrency ke liye yahan mutex lagega
    // mutex mtx;
public:
    void addEvent(Event* event);
    void registerUser(User* user);
    
    // Core functionalities
    Event* searchEvent(string name);
    Booking* createBooking(int userId, int eventId, const vector<int>& seatIds);
    bool confirmBooking(int bookingId /*, PaymentDetails paymentDetails */);
};


// main function jahan se program shuru hoga
int main() {
    cout << "Concert Ticket Booking System Design Ready!" << endl;

    // System setup karna
    BookingPlatform platform;
    Venue* stadium = new Venue(1, "Prayagraj Stadium");
    stadium->addSeat(new SeatedSeat(101, 2000, "A", 1));
    stadium->addSeat(new SeatedSeat(102, 2000, "A", 2));
    
    Event* concert = new Event(1, "Arijit Singh Live", stadium);
    platform.addEvent(concert);
    platform.registerUser(new User(1, "Amit"));

    // User ka workflow:
    // 1. Event search karna
    cout << "\n'Arijit Singh Live' event search kiya ja raha hai..." << endl;
    Event* foundEvent = platform.searchEvent("Arijit Singh Live");

    // 2. Agar event milta hai, toh booking create karna
    if (foundEvent) {
        cout << "Event mil gaya! Seats 101 aur 102 ke liye booking banayi ja rahi hai..." << endl;
        Booking* booking = platform.createBooking(1, 1, {101, 102});
        if (booking) {
            cout << "Booking (ID: " << 123 << ") ban gayi hai, payment pending hai." << endl;
            // 3. Booking confirm karna (payment ke baad)
            platform.confirmBooking(123);
        }
    }

    return 0;
}
```

---
Ek social network jaise Facebook ka core design **`User`** class ke ird-gird hota hai, jo aapas mein judkar ek **social graph** banate hain. Users apni **`Profile`** banate hain aur **`Post`** (jaise text, images) share karte hain. System ka sabse complex hissa **News Feed** hai, jise ek algorithm user ke doston (friends) ke posts ko ikattha karke aur unhe relevance ke aadhar par rank karke generate karta hai. Ek central **`SocialNetwork`** class is poore platform ko manage karti hai.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * **Users:** Personal details ke saath `Profile` bana sakenge.
      * **Connections (Friends):** Users ek doosre ko friend request bhej aur accept kar sakenge.
      * **Posts:** Users content (text, images, videos) post kar sakenge.
      * **News Feed:** User ki homepage par uske doston dwara ki gayi posts ki ek feed dikhegi.
      * **Interactions:** Users posts par `Like` aur `Comment` kar sakenge.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Scalability:** System ko arbon (billions) users aur unke connections/posts ko handle karne ke liye banaya jaana chahiye.
      * **Availability:** System hamesha uplabdh (highly available) rehna chahiye.
      * **Low Latency:** News feed bahut tezi se load honi chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Hum core features (profiles, friends, posts, feed) par focus kar rahe hain. Groups, pages, aur messaging jaise features abhi scope se bahar hain.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`User`:**

      * **Attributes:** `userId`, `name`, `Profile* profile`, `map<int, User*> friends`.
      * **Methods:** `sendFriendRequest()`, `acceptFriendRequest()`, `createPost()`.

2.  **`Profile`:**

      * **Attributes:** `aboutMe`, `workExperience`, `education`.

3.  **`Content` (Abstract Class):**

      * Sabhi user-generated content (Post, Comment) ke liye ek base class.
      * **Attributes:** `contentId`, `author` (User\*), `timestamp`.

4.  **`Post` (Content se Inherited):**

      * **Attributes:** `text`, `vector<Like*> likes`, `vector<Comment*> comments`.

5.  **`Comment` (Content se Inherited):**

      * **Attributes:** Iske paas koi extra attribute nahi hoga.

6.  **`FeedGenerator` (Strategy Pattern):**

      * Feed generate karne ke algorithm ke liye.
      * **Abstract Class:** `FeedGenerationStrategy`.
      * **Concrete Classes:** `ChronologicalFeedStrategy` (samay ke anusaar) aur `RelevanceFeedStrategy` (complex algorithm).

7.  **`SocialNetwork` (Main Controller / Facade):**

      * Poore system ko manage karta hai.
      * **Attributes:** `map<int, User*> userGraph` (sabhi users ka network).
      * **Methods:** `registerUser()`, `establishFriendship()`, `generateNewsFeedForUser()`.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Composition:** `User` **has-a** `Profile`. `Post` **has-many** `Like`s aur `Comment`s.
  * **Inheritance:** `Post` aur `Comment` **is-a** `Content`.
  * **Association:** `User`s aapas mein `friends` ke roop mein jude hote hain, jo ek **graph** banata hai.

-----

### \#\# 4. Data Storage

  * Is bade system ke liye alag-alag databases ka istemal kiya jaata hai (**Polyglot Persistence**):
      * **Graph Database (jaise Neo4j):** Social graph (users aur unki dosti) ko store karne ke liye. Yeh "doston ke dost" jaisi queries ke liye bahut tez hota hai.
      * **NoSQL Database (jaise Cassandra):** Bhaari maatra mein user-generated content (posts, comments) ko store karne ke liye, jo high write speed ke liye anukoolit (optimized) hota hai.

-----

### \#\# 5. Concurrency

  * System mein **bade paimane par concurrency** hoti hai.
  * **Fan-out on write:** Jab ek user post karta hai, toh system ko us post ko uske sabhi doston ke feed tak pahunchana hota hai. Yeh ek bahut bada operation hai, jise aam taur par asynchronously **message queues** ka istemal karke kiya jaata hai. Post database mein likhi jaati hai, aur phir ek background job use doston ke cached feeds mein daal deta hai.

-----

### \#\# 6. Scalability

  * Yeh engineering ki sabse badi scalability chunautiyon mein se ek hai. Iske liye zaroori hai:
      * **Microservices Architecture:** Har cheez ek alag service hoti hai (user service, graph service, feed service).
      * **Caching:** Caching har jagah istemal hoti hai. User ki news feed aksar pehle se hi compute karke cache (jaise Redis) mein rakh di jaati hai taaki woh turant load ho.
      * **Content Delivery Network (CDN):** Images aur videos ko poori duniya mein tezi se serve karne ke liye.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * Microservices ke beech network failure.
  * Database mein data likhte samay failure.
  * Consistency ki samasyaayein (jaise aapko ek comment dikhta hai lekin uski post load nahi ho paati).

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Single Responsibility Principle (SRP):** Har microservice aur class ki ek hi zimmedari hai.
  * **Strategy Pattern:** `FeedGenerator` ke liye istemal hota hai, jisse ranking algorithm ko aasaani se badla ya test kiya ja sakta hai.
  * **Observer Pattern:** Notifications ke liye istemal kiya ja sakta hai (jaise jab koi aapki post like karta hai).

-----

### \#\# 9. APIs

  * System RESTful ya gRPC APIs par bana hota hai:
      * `GET /users/{id}`
      * `GET /users/{id}/friends`
      * `GET /feed`
      * `POST /posts`
      * `POST /posts/{id}/like`

-----

### \#\# Social Network Service ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class User;
class Content;
class Post;
class Comment;
class Profile;

// ===================================
// == CONTENT HIERARCHY ==
// ===================================
class Content {
protected:
    int id;
    User* author;
    time_t timestamp;
public:
    Content(int id, User* author) : id(id), author(author) { timestamp = time(0); }
    virtual void display() = 0; // Abstraction
    virtual ~Content() {}
};

class Post : public Content { // Inheritance
private:
    string text;
    vector<User*> likes;
    vector<Comment*> comments;
public:
    Post(int id, User* author, string text) : Content(id, author), text(text) {}
    void display() override; // Polymorphism
};

class Comment : public Content {
private:
    string text;
public:
    Comment(int id, User* author, string text) : Content(id, author), text(text) {}
    void display() override;
};


// ===================================
// == USER & PROFILE CLASSES ==
// ===================================
class Profile {
    // ... Profile details like work, education
};

class User {
private:
    int id;
    string name;
    Profile* profile;
    map<int, User*> friends;
    vector<Post*> posts;
public:
    User(int id, string name);
    void addFriend(User* user);

    // Factory method to create posts
    Post* createPost(int postId, string text);
    
    string getName() { return name; }
    map<int, User*> getFriends() { return friends; }
    vector<Post*> getPosts() { return posts; }
};


// ===================================
// == FEED GENERATION (STRATEGY PATTERN) ==
// ===================================
class NewsFeed {
public:
    vector<Post*> posts;
    void display() {
        cout << "\n--- News Feed ---" << endl;
        for (Post* post : posts) {
            post->display();
        }
        cout << "-----------------" << endl;
    }
};

class FeedGenerationStrategy {
public:
    virtual NewsFeed* generate(User* user) = 0;
    virtual ~FeedGenerationStrategy() {}
};

class ChronologicalFeedStrategy : public FeedGenerationStrategy {
public:
    NewsFeed* generate(User* user) override;
};


// ===================================
// == MAIN CONTROLLER ==
// ===================================
class SocialNetwork {
private:
    map<int, User*> users;
    FeedGenerationStrategy* feedStrategy;
public:
    SocialNetwork(FeedGenerationStrategy* strategy) : feedStrategy(strategy) {}
    ~SocialNetwork();
    void registerUser(int id, string name);
    void establishFriendship(int userId1, int userId2);
    void createPostForUser(int userId, int postId, string text);
    NewsFeed* getFeedForUser(int userId);
};


// main function jahan se program shuru hoga
int main() {
    // Ek simple chronological feed strategy ka istemal
    SocialNetwork* facebook = new SocialNetwork(new ChronologicalFeedStrategy());
    
    facebook->registerUser(1, "Amit");
    facebook->registerUser(2, "Babita");
    facebook->registerUser(3, "Chandan");

    facebook->establishFriendship(1, 2); // Amit and Babita are friends
    facebook->establishFriendship(1, 3); // Amit and Chandan are friends

    facebook->createPostForUser(2, 101, "Aaj mausam accha hai!"); // Babita's post
    facebook->createPostForUser(3, 102, "C++ LLD padh raha hoon.");  // Chandan's post
    facebook->createPostForUser(1, 103, "Yeh meri pehli post hai."); // Amit's post

    // Amit ki feed generate karo
    NewsFeed* amitsFeed = facebook->getFeedForUser(1);
    // Amit ki feed mein uske doston (Babita, Chandan) ki posts honi chahiye
    amitsFeed->display();

    delete facebook;
    
    return 0;
}
```

---

Ek live cricket commentary system jaise CricInfo ka core design **Observer Design Pattern** par aadharit hai. Ismein, ek central **`Match`** object (**Subject**) khel ki vartaman sthiti (current state) jaise score, overs, aur wickets ko hold karta hai. Alag-alag clients, jaise ek **`CommentaryPanel`** (text updates ke liye) ya ek **`ScorecardDisplay`** (score updates ke liye), **Observers** ki tarah kaam karte hain. Jab match mein koi ghatna (event) hoti hai, jaise ek ball phekna ya wicket girna, toh `Match` object apne sabhi registered observers ko soochit (notify) karta hai, jo phir nayi jaankari ke saath khud ko update kar lete hain.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * System ko ball-by-ball **commentary** pradan karni chahiye.
      * Ise ek real-time **scorecard** (runs, wickets, overs, player scores) dikhana chahiye.
      * Ise match ki jaankari (teams, venue, status) dikhani chahiye.
      * Kai users ko ek saath is jaankari ko dekhne mein saksham hona chahiye.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Low Latency / Real-time:** Updates clients tak bina kisi deri ke pahunchni chahiye. Yeh sabse zaroori requirement hai.
      * **High Concurrency:** Laakhon concurrent users ko ek hi match dekhte hue support karna chahiye.
      * **Scalability:** System ko ek saath chal rahe kai matches ko handle karna aana chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Hum backend system design kar rahe hain jo clients ko updates bhejta hai.
      * Commentary aur score ka data ek admin ya doosre data source se hamare system mein aa raha hai.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`Observer` (Abstract Class):**

      * Har us class ke liye ek blueprint jo updates prapt karna chahti hai.
      * **Methods:** `update(const Match& match)` (pure virtual - **Abstraction**).

2.  **`Match` (Concrete Subject):**

      * Yeh Observer Pattern ka **Subject** hai. Yeh khel ki saari state rakhta hai.
      * **Attributes:** `score`, `wickets`, `overs`, `list<Observer*> observers` (apne sabhi observers ki list).
      * **Methods:** `registerObserver()`, `removeObserver()`, `notifyObservers()`. Iske paas `updateAfterBall()` jaise methods bhi honge jo game state ko badalte hain aur phir `notifyObservers()` ko call karte hain.

3.  **Concrete Observers (`ScorecardDisplay`, `CommentaryDisplay`):**

      * Yeh `Observer` se inherit karenge (**Inheritance**).
      * `update` method ko implement karenge taaki jab `Match` se notification mile, toh woh apne specific data ko refresh kar sakein (**Polymorphism**).

4.  **Helper Classes:** `Player`, `Team`, `Commentary` (ek ball ki commentary text rakhne ke liye).

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Observer Pattern:** `Match` (Subject) **has-many** `Observer`s. `ScorecardDisplay` **is-an** `Observer`.
  * **Composition:** `Match` **has-two** `Team`s. `Team` **has-many** `Player`s.

-----

### \#\# 4. Data Storage

  * **In-memory Cache (jaise Redis):** Live match ke data ke liye. Sabhi active matches ka current score aur state yahan rakha jaayega taaki data tezi se access ho sake.
  * **Relational Database (SQL):** Match khatm hone ke baad uske data, player stats, aur results ko sthayi roop se store karne ke liye.

-----

### \#\# 5. Concurrency

  * **Write Concurrency:** Aam taur par, ek match ki state ko update karne ka source ek hi hota hai (jaise ek admin jo ball-by-ball data daal raha hai), isliye write-side concurrency saral hai.
  * **Read Concurrency:** Yeh sabse badi chunauti hai. Laakhon users score padh rahe hote hain.
  * **Fan-out Architecture:** `Match` object se update ko laakhon clients tak pahunchana hota hai. Iske liye **WebSockets** ya **Server-Sent Events (SSE)** jaisi technologies ka istemal hota hai. Backend se ek update sabhi jude hue clients ko real-time mein push kiya jaata hai.

-----

### \#\# 6. Scalability

  * System horizontally scalable hona chahiye.
  * **Load Balancers** user connections ko distribute karne ke liye.
  * **Distributed Messaging System** (jaise Kafka) updates ke fan-out ko handle karne ke liye. Ek `Match` object Kafka topic par update publish karega, aur kai servers us topic se updates lekar apne jude hue clients ko bhejenge.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * Client ka connection toot jaana aur dobara judna.
  * Data source se data aane mein deri hona.
  * System ko individual client failures se prabhavit nahi hona chahiye.

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Observer Pattern:** Yeh is samasya ke liye ekdam sahi pattern hai. Yeh core match logic (Subject) ko data display karne ke alag-alag tareekon (Observers) se decouple karta hai. Hum aasaani se ek naya display type (jaise `GraphicalWagonWheelDisplay`) jod sakte hain, bas ek nayi class banakar jo `Observer` interface ko implement karti ho.
  * **Single Responsibility Principle (SRP):** `Match` game state manage karta hai, `CommentaryDisplay` sirf commentary, aur `ScorecardDisplay` sirf scorecard display karta hai.

-----

### \#\# 9. APIs

  * Live data ke liye yeh ek traditional REST API system nahi hai. Yeh ek **push-based system** hai.
  * Ek client ek **WebSocket** connection banayega, jaise: `ws://api.cricinfo.com/live/matches/{matchId}`
  * Server phir is connection par har ball ke baad JSON format mein updates bhejega.
  * Non-live data (jaise aane wale matches) ke liye REST API ka istemal hoga: `GET /matches/upcoming`.

-----

### \#\# CricInfo Live Commentary System ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

class Match; // Forward declaration

// ===================================
// == OBSERVER PATTERN: OBSERVER INTERFACE ==
// ===================================
// Abstract class jise har display class implement karegi
class Observer {
public:
    virtual void update(const Match& match) = 0;
    virtual ~Observer() {}
};

// ===================================
// == OBSERVER PATTERN: SUBJECT (MATCH) ==
// ===================================
// Match class state rakhti hai aur observers ko notify karti hai
class Match {
private:
    list<Observer*> observers;
    // Match ki state
    int runs, wickets, overs;
    string commentary;

public:
    Match() : runs(0), wickets(0), overs(0) {}

    void registerObserver(Observer* o) {
        observers.push_back(o);
    }
    void removeObserver(Observer* o) {
        observers.remove(o);
    }
    void notifyObservers() {
        for (auto observer : observers) {
            observer->update(*this);
        }
    }

    // Jab match mein koi event hota hai
    void updateAfterBall(int runsScored, bool isWicket, string commentaryText) {
        this->runs += runsScored;
        if (isWicket) this->wickets++;
        // Overs ka logic yahan simplified hai
        this->overs++; 
        this->commentary = commentaryText;
        
        cout << "\n[MATCH UPDATE] Ek nayi ball phek di gayi hai!" << endl;
        // State badalne ke baad sabhi ko notify karo
        notifyObservers();
    }

    // Getters for observers to pull data
    int getRuns() const { return runs; }
    int getWickets() const { return wickets; }
    int getOvers() const { return overs; }
    string getCommentary() const { return commentary; }
};

// ===================================
// == OBSERVER PATTERN: CONCRETE OBSERVERS ==
// ===================================
// Yeh sirf scorecard display karta hai
class ScorecardDisplay : public Observer {
public:
    void update(const Match& match) override {
        cout << "--- SCORECARD ---" << endl;
        cout << "  Runs: " << match.getRuns() << endl;
        cout << "  Wickets: " << match.getWickets() << endl;
        cout << "  Overs: " << match.getOvers() << endl;
        cout << "-----------------" << endl;
    }
};

// Yeh sirf commentary display karta hai
class CommentaryDisplay : public Observer {
public:
    void update(const Match& match) override {
        cout << "--- COMMENTARY ---" << endl;
        cout << "  " << match.getCommentary() << endl;
        cout << "------------------" << endl;
    }
};

// main function jahan se program shuru hoga
int main() {
    // Match (Subject) banate hain
    Match match;

    // Alag-alag displays (Observers) banate hain
    ScorecardDisplay scorecard;
    CommentaryDisplay commentary;

    // Observers ko match ke saath register karte hain
    match.registerObserver(&scorecard);
    match.registerObserver(&commentary);

    cout << "Live match shuru ho gaya hai!" << endl;

    // Match mein kuch events simulate karte hain
    this_thread::sleep_for(chrono::seconds(1));
    match.updateAfterBall(4, false, "Sundar shot, gend boundary ke paar, 4 run!");

    this_thread::sleep_for(chrono::seconds(1));
    match.updateAfterBall(1, false, "Batsman ne ek run liya.");

    this_thread::sleep_for(chrono::seconds(1));
    match.updateAfterBall(0, true, "Bold! Kya gend thi, wicket gir gaya!");

    return 0;
}
```

---

Ek Splitwise jaise application ka core design **`User`s** aur unke beech share kiye gaye **`Expense`s** (kharchon) par aadharit hai. Iski mukhya chunauti yeh aakalan (calculate) karna hai ki kaun kise kitna paisa dega. Yeh ek **`SplittingStrategy`** ka istemal karke achieve kiya jaata hai, jo batata hai ki kharch ko kaise baanta jaayega (jaise `Equal`, `Exact`, `Percentage`). System ek **balance sheet** maintain karta hai jo har user ke "lena hai" (owed) ya "dena hai" (owes) ka hisaab rakhta hai. Ek central `SplitwiseApp` class sabhi users, groups, aur kharchon ko manage karti hai.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * Users account bana sakenge.
      * Users doosre users ke saath **Groups** bana sakenge.
      * Users ek **Expense** (kharch) add kar sakenge.
      * Ek kharch ko ek vyakti pay karega aur kai logon ke beech baanta jaayega.
      * Kharch ko alag-alag tareekon se baanta ja sakta hai:
          * **Equally:** Kharch sabhi mein barabar baanta jaayega.
          * **Exactly:** Har vyakti ka ek nishchit (specific) amount hoga.
          * **By Percentage:** Har vyakti kharch ka ek nishchit pratishat (percentage) dega.
      * System ko har user ka balance dikhana chahiye: unhe kisko paise dene hain aur kis-se lene hain.
      * Users aapas mein udhaar chukta (settle up) kar sakenge.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Data Consistency:** Balance ki calculation hamesha 100% sateek aur transactional honi chahiye.
      * **Concurrency:** Ek hi group mein kai log ek saath kharch jod sakte hain.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Hum core expense splitting aur balance calculation logic par focus kar rahe hain.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`User`:**

      * **Attributes:** `userId`, `name`.

2.  **`Expense`:**

      * **Attributes:** `description`, `totalAmount`, `User* paidBy`, `vector<Split*> splits`.

3.  **`Split`:**

      * Ek helper class jo batati hai ki ek `User` ko kitna hissa dena hai.
      * **Attributes:** `User* user`, `double amountOwed`.

4.  **`SplittingStrategy` (Abstract Class - Strategy Pattern):**

      * Yeh alag-alag split logic ke liye ek blueprint hai.
      * **Methods:** `calculateOwedAmounts(...)` (pure virtual - **Abstraction**).
      * **Derived Classes:** `EqualSplitStrategy`, `ExactSplitStrategy`, `PercentageSplitStrategy` (**Inheritance** & **Polymorphism**).

5.  **`BalanceSheet`:**

      * Woh data structure jo hisaab rakhta hai ki kaun kise kitna paisa dega.
      * **Attributes:** `map<User*, map<User*, double>> balances`. Jaise, `balances[Amit][Babita]` = 100 ka matlab hai "Amit Babita ko 100 rupaye dega".

6.  **`SplitwiseApp` (Main Controller):**

      * **Attributes:** `map<int, User*> users`, `map<int, Group*> groups`, `BalanceSheet* balanceSheet`.
      * **Methods:** `addUser()`, `addExpense()`, `showBalances()`.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Composition:** `Group` **has-many** `User`s aur `Expense`s.
  * **Strategy Pattern:** `SplitwiseApp` kharch add karte samay ek `SplittingStrategy` ka istemal karta hai.
  * **Association:** `Expense` ek `User` dwara pay kiya jaata hai aur kai `User`s ke beech baanta jaata hai.

-----

### \#\# 4. Data Storage

  * Is system ke liye ek **Relational Database (SQL)** behtareen hai, kyunki yeh kharchon ko add karne aur balance update karne jaise transactional kaamon ko **ACID guarantees** ke saath handle kar sakta hai.

-----

### \#\# 5. Concurrency

  * Jab ek hi group mein do log ek saath kharch jodte hain, toh balance sheet ko sahi se update karna zaroori hai.
  * Ek kharch ko jodna aur sabhi users ke balance ko update karne ka operation **atomic** hona chahiye. Iske liye **database transactions** ka istemal hota hai.

-----

### \#\# 6. Scalability

  * Ek bade user base ke liye, system ko zaroorat hogi:
      * **Database Sharding** (data ko `userId` ya `groupId` ke aadhar par baantna).
      * User balances ko **cache** karna taaki har baar calculate na karna pade.
      * Microservices architecture.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * Exact split mein, sabhi hisson ka jod total amount ke barabar nahi hai.
  * Percentage split mein, sabhi pratishat ka jod 100 nahi hai.
  * Ek user aise group mein kharch jod raha hai jiska woh sadasya nahi hai.

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Strategy Pattern:** Yeh is samasya ke liye mukhya pattern hai. Yeh expense creation ko alag-alag split karne ke tareekon se decouple karta hai. Isse भविष्य mein naya split type (jaise `ByShare`) jodna aasan ho jaata hai (**Open/Closed Principle**).
  * **Single Responsibility Principle (SRP):** `BalanceSheet` sirf balance, `SplittingStrategy` sirf split, aur `Expense` sirf ek kharch ka data rakhta hai.

-----

### \#\# 9. APIs

  * Ek real-world system mein REST APIs honge:
      * `POST /groups/{groupId}/expenses`: Group mein kharch jodna.
      * `GET /users/{userId}/balance`: User ka balance dekhna.
      * `POST /settle`: Udhaar chuktana.

-----

### \#\# Splitwise ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class User;
class Split;
class Expense;
class SplittingStrategy;

// ===================================
// == CORE BUSINESS CLASSES ==
// ===================================
class User {
public:
    int id; string name;
    User(int id, string name) : id(id), name(name) {}
};

class Split {
public:
    User* user;
    double amountOwed;
    Split(User* u, double amt) : user(u), amountOwed(amt) {}
};

class Expense {
public:
    int id;
    string description;
    double totalAmount;
    User* paidBy;
    vector<Split*> splits;
    Expense(int id, string desc, double amount, User* paidBy, const vector<Split*>& splits) : 
        id(id), description(desc), totalAmount(amount), paidBy(paidBy), splits(splits) {}
};


// ===================================
// == SPLITTING STRATEGY HIERARCHY ==
// ===================================
class SplittingStrategy {
public:
    virtual void calculateOwedAmounts(double totalAmount, vector<Split*>& splits) = 0; // Abstraction
    virtual ~SplittingStrategy() {}
};

class EqualSplitStrategy : public SplittingStrategy { // Inheritance
public:
    void calculateOwedAmounts(double totalAmount, vector<Split*>& splits) override { // Polymorphism
        double amountPerPerson = totalAmount / splits.size();
        for (auto& split : splits) {
            split->amountOwed = amountPerPerson;
        }
    }
};
// ... (ExactSplitStrategy, PercentageSplitStrategy classes)


// ===================================
// == MAIN CONTROLLER ==
// ===================================
class SplitwiseApp {
private:
    map<int, User*> users;
    map<pair<int, int>, double> balanceSheet; // {user1_id, user2_id} -> amount (user1 owes user2)

public:
    void addUser(User* user) {
        users[user->id] = user;
    }

    void addExpense(int expenseId, string desc, double amount, int paidById, 
                    const vector<Split*>& splits, SplittingStrategy* strategy) {
        
        // 1. Strategy ka istemal karke har user ka hissa calculate karo
        strategy->calculateOwedAmounts(amount, const_cast<vector<Split*>&>(splits));
        
        // 2. Expense object banao
        Expense expense(expenseId, desc, amount, users[paidById], splits);

        // 3. Balance sheet update karo
        // Yeh operation atomic hona chahiye (using transactions in real DB)
        for (const auto& split : expense.splits) {
            User* paidTo = expense.paidBy;
            User* paidFrom = split->user;
            
            if (paidTo->id != paidFrom->id) {
                // paidFrom owes paidTo
                balanceSheet[{paidFrom->id, paidTo->id}] += split->amountOwed;
                // paidTo is owed by paidFrom, so we subtract from the reverse entry
                balanceSheet[{paidTo->id, paidFrom->id}] -= split->amountOwed;
            }
        }
    }
    
    // Sirf simplified balances dikhao
    void showBalances() {
        cout << "\n--- Current Balances ---" << endl;
        for(auto const& [user_pair, amount] : balanceSheet) {
            if (amount > 0) {
                cout << users[user_pair.first]->name << " owes " 
                     << users[user_pair.second]->name << ": " << amount << endl;
            }
        }
    }
};

// main function jahan se program shuru hoga
int main() {
    SplitwiseApp app;

    // Users banao
    User* amit = new User(1, "Amit");
    User* babita = new User(2, "Babita");
    User* chandan = new User(3, "Chandan");
    app.addUser(amit);
    app.addUser(babita);
    app.addUser(chandan);

    // Expense 1: Amit ne 300 pay kiye, sab mein barabar baanta gaya
    cout << "--- Kharch 1 (Equal) ---" << endl;
    vector<Split*> splits1 = {new Split(amit, 0), new Split(babita, 0), new Split(chandan, 0)};
    app.addExpense(101, "Dinner", 300.0, 1, splits1, new EqualSplitStrategy());
    app.showBalances(); // Babita owes Amit 100, Chandan owes Amit 100

    // Expense 2: Babita ne 100 pay kiye, sirf Amit aur Babita mein baanta gaya
    cout << "\n--- Kharch 2 (Equal) ---" << endl;
    vector<Split*> splits2 = {new Split(amit, 0), new Split(babita, 0)};
    app.addExpense(102, "Movie Tickets", 100.0, 2, splits2, new EqualSplitStrategy());
    app.showBalances(); // Babita owes Amit 50 (100 - 50), Chandan owes Amit 100

    return 0;
}
```
---
Ek chess game ka core design ek abstract **`Piece`** class par aadharit hai, jiske concrete implementations jaise `King`, `Rook`, aadi hote hain, aur har ek apne movement ka logic khud define karta hai. Ek **`Board`** class `Spot`s ke grid ko manage karti hai, aur har `Spot` ek `Piece` ko hold kar sakta hai. Ek central **`Game`** class poore khel ke flow ko control karti hai, jismein khiladiyon ki bari (turns), piece-specific rules ke aadhar par moves ko validate karna (polymorphism ka istemal karke), aur check ya checkmate jaisi sthitiyon ki jaanch karna shamil hai.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * Ek 8x8 ka board hona chahiye.
      * Do khiladi (Players) honge: White aur Black.
      * Standard chess ke mohre (pieces) honge (King, Queen, Rook, Bishop, Knight, Pawn) jinki apni vishisht chaalein (moves) hongi.
      * Khel bari-bari (turn-based) se khela jaayega.
      * Jeetne, haarne, ya draw hone ki sthitiyan (checkmate, stalemate) honi chahiye.
      * Special moves jaise castling, en passant, aur pawn promotion shamil hone chahiye.

  * **Non-Functional Requirements (Performance, etc.):**

      * System responsive hona chahiye, move validation mein deri nahi honi chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Yeh ek do-khiladi, local console-based game hai.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`Piece` (Abstract Class):**

      * Yeh design ki neev (foundation) hai.
      * **Attributes:** `Color color` (WHITE ya BLACK).
      * **Methods:** `canMove(Board* board, Spot* start, Spot* end)` aur `getSymbol()` (dono **pure virtual** - **Abstraction**).

2.  **Concrete Pieces (`King`, `Queen`, `Rook`, etc.):**

      * Yeh `Piece` se inherit karenge (**Inheritance**).
      * Har piece apne `canMove()` method ko alag tarike se implement karega, jo uski legal chaalon ko define karega (**Polymorphism**).

3.  **`Spot`:**

      * Board ke ek single square ko represent karta hai.
      * **Attributes:** `x`, `y` coordinates, `Piece* piece` (us square par rakha mohra).

4.  **`Board`:**

      * 8x8 ke grid ko manage karta hai.
      * **Attributes:** `vector<vector<Spot>> board`.
      * **Methods:** `initializeBoard()`, `getSpot()`.

5.  **`Game` (Main Controller):**

      * Poore game ke flow aur rules ko manage karta hai.
      * **Attributes:** `Board* board`, `Player players[2]`, `Player* currentPlayer`.
      * **Methods:** `startGame()`, `makeMove()`, `isCheck()`, `isCheckmate()`.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Composition:** `Game` **has-a** `Board` aur do `Player`s. `Board` **has-many** `Spot`s.
  * **Association:** `Spot` **can have a** `Piece`.
  * **Inheritance:** `King`, `Rook`, etc. **are-a** `Piece`.

-----

### \#\# 4. Data Storage

  * Ek simple console game ke liye, saara data (board ki sthiti) **in-memory** rahega. Database ki koi zaroorat nahi hai.

-----

### \#\# 5. Concurrency

  * Yeh ek turn-based, local game hai, isliye concurrency ya synchronization ki zaroorat nahi hai.

-----

### \#\# 6. Scalability

  * Yeh design ek single game ke liye hai. Ise ek online platform (jaise chess.com) mein badalne ke liye client-server architecture, networking, aur database ki zaroorat padegi.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * **Invalid Move:** `Game` class ka `makeMove()` method moves ko validate karega. Agar koi chaal niyamon ke viruddh hai (jaise haathi ka tircha chalna, ya king ka check mein jaana), toh system us move ko reject kar dega aur player se dobara chalne ko kahega.
  * **Invalid Input:** User dwara galat coordinates (jaise "j9") daalne ko handle karna.

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Single Responsibility Principle (SRP):** Har class ka ek hi kaam hai. `Piece` classes apni chaalein jaanti hain, `Board` grid manage karta hai, aur `Game` niyam (rules) manage karta hai.
  * **Open/Closed Principle (OCP):** Hum ek naye prakar ka mohra (jaise fantasy chess ke liye) `Piece` se inherit karke ek nayi class bana kar jod sakte hain, bina `Game` ya `Board` class ko badle.
  * **Polymorphism:** Yeh is design ka mool siddhant hai. `Game` class mohron se `Piece*` pointer ke zariye interact karti hai. Woh `piece->canMove()` call karti hai bina yeh jaane ki woh kaun sa piece hai, aur runtime par us piece ka sahi `canMove` logic execute hota hai.

-----

### \#\# 9. APIs

  * Console application ke liye APIs relevant nahi hain. Iska "interface" command-line hai jahan user "e2 e4" jaisi chaalein input karta hai.

-----

### \#\# Chess Game ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class Board;
class Piece;
class Spot;

// Enums for clarity
enum class Color { WHITE, BLACK };

// ===================================
// == PIECE HIERARCHY ==
// ===================================
// Piece ek abstract class hai. Yeh har mohre ka blueprint hai.
class Piece {
protected:
    Color color;
public:
    Piece(Color c) : color(c) {}
    // Pure virtual functions (Abstraction).
    // Har piece ko batana hoga ki woh kaise move kar sakta hai.
    virtual bool canMove(Board* board, Spot* start, Spot* end) = 0;
    virtual char getSymbol() = 0;
    Color getColor() { return color; }
    virtual ~Piece() {}
};

// Concrete Pieces (Example: Rook)
class Rook : public Piece { // Inheritance
public:
    Rook(Color c) : Piece(c) {}
    bool canMove(Board* board, Spot* start, Spot* end) override {
        // Rook ke liye move validation logic yahan aayega (seedhi line mein).
        // Yeh ek simplified placeholder hai.
        return true; 
    }
    char getSymbol() override { // Polymorphism
        return (color == Color::WHITE) ? 'R' : 'r';
    }
};
// ... Isi tarah King, Queen, Bishop, Knight, aur Pawn ke liye bhi classes banengi.

// ===================================
// == BOARD & SPOT CLASSES ==
// ===================================
// Spot class, board ke ek single square ko represent karti hai.
class Spot {
private:
    int x, y;
    Piece* piece;
public:
    Spot(int x, int y, Piece* p) : x(x), y(y), piece(p) {}
    void setPiece(Piece* p) { piece = p; }
    Piece* getPiece() { return piece; }
};

// Board class, poore 8x8 chessboard ko manage karti hai.
class Board {
private:
    vector<vector<Spot>> board;
public:
    Board();
    void initializeBoard(); // Board par shuruaati pieces set karna
    void drawBoard();
    Spot* getSpot(int x, int y);
};

// ===================================
// == GAME & PLAYER CLASSES ==
// ===================================
class Player {
public:
    string name;
    Color color;
    Player(string name, Color c) : name(name), color(c) {}
};

// Game class poore game ke flow aur rules ko manage karti hai.
class Game {
private:
    Board* board;
    Player players[2];
    Player* currentPlayer;
    string status;
public:
    Game(string p1Name, string p2Name);
    void startGame();
    bool makeMove(Player* player, int startX, int startY, int endX, int endY);
    void changeTurn();
};

// main function jahan se program shuru hoga
int main() {
    cout << "Chess Game Design Ready!" << endl;

    // Yahan par Game class ka object banakar game shuru kiya ja sakta hai.
    // Game chess("Amit", "Babita");
    // chess.startGame();
    
    return 0;
}
```

---
Ek university course registration system ka core design **`Student`**, **`Course`**, aur ek particular **`Semester`** mein offer kiye ja rahe `Course` ke instance (jise **`CourseOffering`** kehte hain) ke ird-gird hota hai. Iski mukhya prakriya (core process) `Student` dwara `Course`s ke liye register karna hai. System is dauraan zaroori sharton (prerequisites), schedule conflicts, aur course ki capacity (seat limit) ki jaanch karta hai. Mukhya classes mein `Student`, `Course`, `CourseOffering`, `Professor`, aur in sabko manage karne wala ek central `RegistrationSystem` shamil hain.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * University kai **`Course`s** offer karegi.
      * Har `Course` ek vishisht `Semester` mein ek `Professor` dwara ek nishchit samay par offer kiya jaayega (**`CourseOffering`**).
      * **`Student`s** course catalog dekh sakenge.
      * `Student`s courses ke liye register kar sakenge.
      * System courses ke liye zaroori **prerequisites** (pehli yogyata) ko laagu karega.
      * System students ko aise courses ke liye register karne se rokega jinka samay aapas mein takra raha ho (**time conflicts**).
      * Har course offering ki ek seemit capacity (seat limit) hogi.
      * Students register kiye gaye courses ko **drop** bhi kar sakenge.

  * **Non-Functional Requirements (Performance, etc.):**

      * **High Concurrency:** Registration shuru hote hi hazaron students ek saath lokpriya (popular) courses ke liye register karne ki koshish karenge.
      * **Data Consistency:** Ek course mein uplabdh seats ki sankhya hamesha sateek honi chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Hum core registration logic design kar rahe hain, billing ya grading nahi.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`Person` (Hierarchy):**

      * Abstract base class `Person`.
      * Isse inherited `Student` (jiske paas `studentId` aur `transcript` hoga) aur `Professor` (jiske paas `employeeId` hoga).

2.  **`Course`:**

      * Ek course ke aam (abstract) idea ko represent karta hai.
      * **Attributes:** `courseCode` (jaise "CS101"), `title`, `credits`, `vector<Course*> prerequisites`.

3.  **`CourseOffering` (ya `CourseSection`):**

      * Ek `Course` ke vishisht instance ko represent karta hai jo ek semester mein padhaya ja raha hai.
      * **Attributes:** `sectionId`, `course` (Course\*), `professor` (Professor\*), `semester`, `schedule`, `capacity`, `vector<Student*> enrolledStudents`.
      * **Methods:** `addStudent()`, `removeStudent()`, `isFull()`.

4.  **`RegistrationSystem` (Main Controller / Facade):**

      * Poore system ke operations ko manage karta hai.
      * **Attributes:** `map<string, Course*> courseCatalog`, `map<int, CourseOffering*> semesterOfferings`.
      * **Methods:** `registerStudentForCourse()`, `dropCourse()`.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Inheritance:** `Student` aur `Professor` **is-a** `Person`.
  * **Association:** `CourseOffering` ek `Course`, ek `Professor`, aur kai `Student`s ko jodta hai.

-----

### \#\# 4. Data Storage

  * Is system ke liye ek **Relational Database (SQL)** aadarsh hai. Students, professors, courses, aur enrollments ke liye well-defined tables aur unke beech ke rishte relational model mein aasaani se fit ho jaate hain.

-----

### \#\# 5. Concurrency

  * Yeh is system ki **sabse badi chunauti** hai. Registration shuru hote hi lokpriya courses ki aakhiri kuch seats ke liye "race condition" paida ho jaati hai.
  * Uplabdh seats ki jaanch karne aur ek student ko enroll karne ka operation **atomic** hona chahiye.
  * Iske liye **database transactions** ka istemal hota hai, aksar **pessimistic locking** (`SELECT ... FOR UPDATE`) ke saath, taaki jab ek user seat book kar raha ho, toh doosre user ko galat seat count na dikhe.

-----

### \#\# 6. Scalability

  * Ek badi university ke liye, system ko scalable architecture par banana hoga.
  * Registration ke samay aane wale high traffic ko handle karne ke liye **Load Balancers**.
  * Course catalog browse karne wale students ke high read traffic ko handle karne ke liye **Database Read Replicas**.
  * Course catalog ke liye **Caching** (jaise Redis).

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * Course full ho chuka hai (capacity poori ho gayi).
  * Student ne zaroori prerequisites poore nahi kiye hain.
  * Doosre register kiye gaye course ke saath time conflict hai.
  * Student adhiktam (maximum) anumat (allowed) credits se zyada ke liye register kar raha hai.

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Single Responsibility Principle (SRP):** `Course` course ki jaankari, `CourseOffering` ek vishisht section ka enrollment, aur `RegistrationSystem` registration ke business logic ko manage karta hai.
  * **Facade Pattern:** `RegistrationSystem` class ek facade ki tarah kaam karti hai, jo prerequisites, conflicts, aur capacity jaise complex validation checks ke liye ek saral interface (`registerStudentForCourse`) pradan karti hai.

-----

### \#\# 9. APIs

  * Ek real-world system mein REST APIs honge:
      * `GET /courses?semester={sem}`: Ek semester ke sabhi course offerings ko prapt karna.
      * `POST /students/{id}/register`: Ek course section ke liye register karne ka prayaas karna.
      * `DELETE /students/{id}/register/{sectionId}`: Ek course drop karna.

-----

### \#\# Course Registration System ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class Student;
class Professor;
class Course;
class CourseOffering;

// ===================================
// == PERSON HIERARCHY ==
// ===================================
class Person {
protected: int id; string name;
public:
    Person(int id, string name) : id(id), name(name) {}
    virtual ~Person() {}
};

class Student : public Person {
private:
    vector<CourseOffering*> enrolledCourses;
public:
    Student(int id, string name) : Person(id, name) {}
    void enroll(CourseOffering* offering) { enrolledCourses.push_back(offering); }
};

class Professor : public Person {
public:
    Professor(int id, string name) : Person(id, name) {}
};

// ===================================
// == COURSE & OFFERING CLASSES ==
// ===================================
class Course {
public:
    string courseCode;
    string title;
    vector<Course*> prerequisites;
    Course(string code, string title) : courseCode(code), title(title) {}
};

class CourseOffering {
private:
    int sectionId;
    Course* course;
    Professor* professor;
    int capacity;
    vector<Student*> enrolledStudents;
public:
    CourseOffering(int id, Course* c, Professor* p, int cap) : 
        sectionId(id), course(c), professor(p), capacity(cap) {}

    bool isFull() { return enrolledStudents.size() >= capacity; }
    
    bool addStudent(Student* student) {
        if (!isFull()) {
            enrolledStudents.push_back(student);
            student->enroll(this);
            return true;
        }
        return false;
    }
};


// ===================================
// == MAIN CONTROLLER (FACADE) ==
// ===================================
class RegistrationSystem {
private:
    map<string, Course*> courseCatalog;
    map<int, CourseOffering*> semesterOfferings;
    map<int, Student*> students;
    // Concurrency ke liye yahan mutex lagega
    // mutex mtx;
public:
    void addCourseToCatalog(Course* course) { courseCatalog[course->courseCode] = course; }
    void addStudent(Student* student) { students[1] = student; } // Simplified ID
    void addCourseOffering(CourseOffering* offering) { semesterOfferings[1] = offering; } // Simplified ID

    // Core registration logic
    bool registerStudentForCourse(int studentId, int sectionId) {
        // Yeh operation thread-safe hona chahiye (using locks/transactions)
        // lock_guard<mutex> lock(mtx);
        
        if (students.count(studentId) && semesterOfferings.count(sectionId)) {
            Student* student = students[studentId];
            CourseOffering* offering = semesterOfferings[sectionId];
            
            // 1. Prerequisite check (simplified)
            // 2. Schedule conflict check (simplified)
            
            // 3. Capacity check
            if (!offering->isFull()) {
                offering->addStudent(student);
                cout << "Registration safal! Student " << studentId << " ne section " << sectionId << " mein enroll kiya." << endl;
                return true;
            } else {
                cout << "Registration fail! Course full hai." << endl;
                return false;
            }
        }
        cout << "Registration fail! Invalid student ya section ID." << endl;
        return false;
    }
};

// main function jahan se program shuru hoga
int main() {
    // System setup karna
    RegistrationSystem system;
    Student* amit = new Student(101, "Amit");
    Professor* prof = new Professor(201, "Dr. Verma");
    Course* cs101 = new Course("CS101", "Introduction to Programming");

    system.addStudent(amit);
    system.addCourseToCatalog(cs101);

    // Ek course offering banate hain jiski capacity sirf 1 hai
    CourseOffering* cs101_fall = new CourseOffering(1, cs101, prof, 1);
    system.addCourseOffering(cs101_fall);

    // Registration ka prayaas
    cout << "--- Pehla Registration ---" << endl;
    system.registerStudentForCourse(101, 1);

    cout << "\n--- Doosra Registration (Fail hona chahiye) ---" << endl;
    Student* babita = new Student(102, "Babita");
    system.addStudent(babita);
    system.registerStudentForCourse(102, 1); // Yeh fail hoga kyunki capacity 1 hai

    return 0;
}
```

---
Ek movie ticket booking system jaise BookMyShow ka core design **`Movie`**, **`Theater`**, aur **`Show`** par kendrit hota hai. Ek `Theater` ke andar alag-alag `Screen`s hoti hain, jinka apna ek `Seat` layout hota hai. Ek **`User`** movie search karke, ek `Show` aur `Seat`s chunta hai, jisse ek temporary **`Booking`** banti hai. Yeh booking **`Payment`** safal hone par confirm ho jaati hai. Is system ki sabse badi chunauti seat inventory ko high traffic ke dauraan aane wali **concurrency** ko manage karna hai.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * Users shehar (city) ke hisaab se **movies** search kar sakenge.
      * Users ek movie ko dikhane wale **theaters** ki list dekh sakenge.
      * Users ek **showtime** (khel ka samay) chun sakenge.
      * Users theater ka **seat layout** dekhkar seats chun sakenge.
      * System ko chuni gayi seats ko thodi der ke liye **lock** karna hoga taaki user payment kar sake.
      * Payment poora hone par booking confirm hogi.

  * **Non-Functional Requirements (Performance, etc.):**

      * **High Concurrency:** Nayi aur lokpriya filmon ki release par, hazaron users ek saath tickets book karne ki koshish karenge.
      * **High Availability:** System peak booking time par hamesha online aur responsive rehna chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Hum core booking flow design kar rahe hain.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`Movie`:**

      * **Attributes:** `movieId`, `title`, `genre`, `duration`.

2.  **`Theater`:**

      * **Attributes:** `theaterId`, `name`, `address`, `vector<Screen*> screens`.

3.  **`Screen`:**

      * Theater ke andar ek auditorium.
      * **Attributes:** `screenId`, `vector<Seat*> seats`.

4.  **`Seat`:**

      * **Attributes:** `seatId`, `row`, `number`, `SeatStatus status` (AVAILABLE, LOCKED, BOOKED).

5.  **`Show`:**

      * Ek `Movie` ka ek `Screen` par ek vishisht samay par screening. Yeh sabko jodta hai.
      * **Attributes:** `showId`, `movie`, `screen`, `startTime`.

6.  **`Booking`:**

      * Ek transaction ko represent karta hai.
      * **Attributes:** `bookingId`, `user`, `show`, `vector<Seat*> seats`, `totalAmount`, `BookingStatus status`.

7.  **`BookingPlatform` (Main Controller / Facade):**

      * Poore system (jaise BookMyShow) ko represent karta hai.
      * **Methods:** `searchMovies()`, `createBooking()`, `confirmBooking()`.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Composition:** `Theater` **has-many** `Screen`s. `Screen` **has-many** `Seat`s.
  * **Association:** `Show` ek `Movie` aur ek `Screen` ko jodta hai. `Booking` ek `User` aur ek `Show` ko jodta hai.

-----

### \#\# 4. Data Storage

  * Iske liye databases ka combination istemal hota hai:
      * **Relational Database (SQL):** Movies, theaters, users, aur confirmed bookings jaise structured data ke liye.
      * **In-memory Cache with TTL (jaise Redis):** Temporary seat locks ko tezi se manage karne ke liye.

-----

### \#\# 5. Concurrency

  * Yeh is system ki **sabse badi chunauti** hai.
  * **Seat Locking:** Ek seat ko select karne aur use doosre users ke liye unavailable mark karne ka process **atomic** hona chahiye. Iske liye Redis jaise fast, distributed cache ke atomic operations (`SETNX` - set if not exists) ek standard solution hain, jo do users ko ek hi samay par ek hi seat select karne se rokta hai.

-----

### \#\# 6. Scalability

  * System ko highly scalable aur distributed architecture par banana zaroori hai.
  * **Load Balancers** aane wale traffic ko alag-alag servers par baantne ke liye.
  * **Microservices:** Movie Service, Theater Service, Booking Service, aadi ke liye alag-alag services.
  * **Caching** ka bharpoor istemal (movie listings aur theater information ke liye).

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * Select ki gayi seats payment se pehle hi kisi aur ne book kar li.
  * Payment fail ho jaana.
  * Seat lock ka samay (e.g., 10 minute) khatm ho jaana (system ko seats ko automatically release kar dena chahiye).

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Single Responsibility Principle (SRP):** Har class ka ek kaam hai: `Movie` film data, `Show` screening data, aur `Booking` transaction manage karta hai.
  * **Facade Pattern:** `BookingPlatform` class ek facade ki tarah kaam karti hai, jo ticket book karne jaise complex process ke liye ek saral interface pradan karti hai.
  * **Open/Closed Principle (OCP):** Hum `Seat` ki hierarchy (`RegularSeat`, `ReclinerSeat`) bana sakte hain bina booking logic ko badle.

-----

### \#\# 9. APIs

  * Ek real-world system mein REST APIs honge:
      * `GET /movies/search?city=Prayagraj`
      * `GET /shows/{showId}/seats`: Ek show ke liye seat layout dekhne ke liye.
      * `POST /bookings`: Seat lock karne aur temporary booking banane ke liye.
      * `POST /bookings/{id}/confirm`: Payment ke baad booking confirm karne ke liye.

-----

### \#\# Movie Ticket Booking System ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Enums for clarity
enum class SeatStatus { AVAILABLE, LOCKED, BOOKED };
enum class BookingStatus { PENDING, CONFIRMED, CANCELLED };

// Forward Declarations
class User;
class Movie;
class Screen;
class Seat;
class Show;
class Booking;

// ===================================
// == CORE ENTITY CLASSES ==
// ===================================
class Movie {
public:
    int id; string title;
    Movie(int id, string title) : id(id), title(title) {}
};

class Seat {
public:
    int id; string row; int num; SeatStatus status;
    Seat(int id, string row, int num) : id(id), row(row), num(num), status(SeatStatus::AVAILABLE) {}
    void lock() { status = SeatStatus::LOCKED; }
    void book() { status = SeatStatus::BOOKED; }
    bool isAvailable() { return status == SeatStatus::AVAILABLE; }
};

class Screen {
public:
    int id; vector<Seat*> seats;
    Screen(int id) : id(id) {}
    void addSeat(Seat* s) { seats.push_back(s); }
};

class Theater {
public:
    int id; string name; vector<Screen*> screens;
    Theater(int id, string name) : id(id), name(name) {}
    void addScreen(Screen* s) { screens.push_back(s); }
};

class Show {
public:
    int id; Movie* movie; Screen* screen; time_t startTime;
    Show(int id, Movie* m, Screen* s, time_t t) : id(id), movie(m), screen(s), startTime(t) {}
};

// ===================================
// == BUSINESS LOGIC CLASSES ==
// ===================================
class User {
public:
    int id; string name;
    User(int id, string name) : id(id), name(name) {}
};

class Booking {
private:
    int id; User* user; Show* show; vector<Seat*> seats; BookingStatus status;
public:
    Booking(int id, User* u, Show* s, const vector<Seat*>& selectedSeats);
    void confirmBooking();
    void cancelBooking();
};

// ===================================
// == MAIN CONTROLLER (FACADE) ==
// ===================================
class BookingPlatform {
private:
    map<int, Theater*> theaters;
    map<int, Movie*> movies;
    map<int, Show*> shows;
    // Concurrency ke liye yahan mutex lagega
    // mutex mtx;
public:
    void addMovie(Movie* m) { movies[m->id] = m; }
    void addTheater(Theater* t) { theaters[t->id] = t; }
    void addShow(Show* s) { shows[s->id] = s; }
    
    // Core functionalities
    vector<Show*> searchShows(string movieName);
    Booking* createBooking(int userId, int showId, const vector<int>& seatIds);
    bool confirmBooking(int bookingId /*, PaymentDetails paymentDetails */);
};

// main function jahan se program shuru hoga
int main() {
    // System setup karna
    BookingPlatform bookMyShow;
    Movie* movie = new Movie(1, "Drishyam 3");
    Theater* pvr = new Theater(101, "PVR Prayagraj");
    Screen* screen1 = new Screen(1);
    screen1->addSeat(new Seat(1, "A", 1));
    screen1->addSeat(new Seat(2, "A", 2));
    pvr->addScreen(screen1);
    
    Show* show = new Show(1001, movie, screen1, time(0));
    
    bookMyShow.addMovie(movie);
    bookMyShow.addTheater(pvr);
    bookMyShow.addShow(show);

    // User ka workflow:
    cout << "--- 'Drishyam 3' ke shows search kiye ja rahe hain ---" << endl;
    vector<Show*> foundShows = bookMyShow.searchShows("Drishyam 3");
    
    if (!foundShows.empty()) {
        cout << "Show mil gaya! Seat A1 aur A2 book ki ja rahi hain..." << endl;
        
        // Booking create karna (seats lock ho jayengi)
        Booking* booking = bookMyShow.createBooking(1, foundShows[0]->id, {1, 2});

        if (booking) {
            cout << "Booking (ID: 12345) ban gayi hai, 10 minute mein payment karein." << endl;
            
            // Payment ke baad booking confirm karna
            bookMyShow.confirmBooking(12345);
            cout << "Booking confirm ho gayi!" << endl;
        }
    }
    
    return 0;
}
```

---
Ek ride-sharing system jaise Uber ka core design ek **`Rider`** (yatri) dwara ride request karne aur system dwara unhe ek nazdeeki **`Driver`** ke saath match karne par kendrit hota hai. Iske mukhya components hain `Rider`, `Driver`, `Trip` (safar), aur ek central **`RideSharingPlatform`**, jo sabse behtareen match dhoondhne ke liye location-based service ka istemal karta hai. Yeh system ek trip ke poore jeevan chakra (lifecycle) ko manage karta hai, request se lekar assignment, safar poora hone, aur payment tak.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * **Riders:** Ek pickup location se destination tak ke liye ride request kar sakenge.
      * **Drivers:** Ride requests ko accept ya reject kar sakenge.
      * System ko anumanit kiraya (estimated fare) calculate karna chahiye.
      * System ko driver ki location ko real-time mein track karna chahiye.
      * Payment process aakhir mein aasaani se ho jaana chahiye.
      * Riders aur drivers dono ek doosre ko rate kar sakenge.

  * **Non-Functional Requirements (Performance, etc.):**

      * **High Availability:** System hamesha uplabdh hona chahiye.
      * **Low Latency:** Driver matching aur location updates mein bahut kam deri honi chahiye.
      * **Scalability:** System ko ek hi shehar jaise Prayagraj se lekar poore desh mein laakhon users ke liye scale karna aana chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Hum core ride-matching aur trip management logic par focus kar rahe hain.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`User` (Hierarchy):**

      * Abstract base class `User`.
      * Isse inherited `Rider` aur `Driver`. `Driver` ke paas `vehicle`, `currentLocation`, aur `isAvailable` jaise extra attributes honge.

2.  **`Vehicle`:**

      * Driver ki gaadi ko represent karta hai.
      * **Attributes:** `licensePlate`, `model`, `type` (Sedan, SUV).

3.  **`Trip` (ya `Ride`):**

      * **Attributes:** `tripId`, `rider`, `driver`, `startLocation`, `endLocation`, `fare`, `TripStatus status` (REQUESTED, ACCEPTED, IN\_PROGRESS, COMPLETED).

4.  **`Location`:**

      * Geographical coordinates (latitude, longitude) store karne ke liye ek helper class.

5.  **`RideSharingPlatform` (Main Controller / Facade):**

      * Poore system ko manage karta hai.
      * **Methods:** `requestRide()`, `findNearbyDrivers()`, `assignDriverToTrip()`.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Inheritance:** `Rider` aur `Driver` **is-a** `User`.
  * **Association:** `Trip` ek `Rider` aur ek `Driver` ko jodta hai. `Driver` **has-a** `Vehicle`.

-----

### \#\# 4. Data Storage

  * **Geospatial Database (jaise PostGIS):** Nazdeeki drivers ko tezi se dhoondhne ke liye yeh bahut zaroori hai. Standard database is kaam ke liye dheeme hote hain.
  * **Relational/NoSQL Database:** User profiles, trip history, aur billing information store karne ke liye.

-----

### \#\# 5. Concurrency

  * **Matching:** Kai riders ek saath ride request kar rahe hote hain, aur kai drivers uplabdh hote hain. Ek driver ko dhoondhne aur assign karne ka process **atomic** hona chahiye taaki ek hi driver do alag-alag riders ko assign na ho jaaye.
  * **Location Updates:** System ko hazaron drivers se lagatar location updates milenge. Iske liye ek highly concurrent ingestion service zaroori hai.

-----

### \#\# 6. Scalability

  * Yeh ek bahut bada, distributed system hai.
  * **Microservices Architecture:** User management, driver matching, location tracking, billing, aadi ke liye alag-alag services.
  * **Message Queues (jaise Kafka):** Bhaari maatra mein ride requests aur location updates ko asynchronously handle karne ke liye.
  * **Spatial Indexing (Quadtrees):** "Nazdeeki driver dhoondho" ki samasya ko **Quadtrees** jaise spatial data structures ka istemal karke hal kiya jaata hai, jo geographical area ko baantkar search ko tez banate hain.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * Koi driver uplabdh nahi hai.
  * Rider trip cancel kar deta hai.
  * Driver request reject kar deta hai.
  * Payment fail ho jaana.

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Single Responsibility Principle (SRP):** Har class aur microservice ka ek hi kaam hai.
  * **Strategy Pattern:** Pricing model ek strategy ho sakta hai (`StandardPricing`, `SurgePricing`). Driver matching algorithm bhi ek strategy ho sakta hai.
  * **Facade Pattern:** `RideSharingPlatform` class `requestRide` jaise saral interface ke peeche ke complex backend logic ko chhipati hai.

-----

### \#\# 9. APIs

  * REST aur real-time APIs ka combination:
      * **REST API:** `POST /rides/request`, `GET /rides/{rideId}/status`.
      * **WebSockets:** Rider ke app par driver ki real-time location updates bhejne ke liye.

-----

### \#\# Ride-Sharing System ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Enums for clarity
enum class TripStatus { REQUESTED, ACCEPTED, IN_PROGRESS, COMPLETED, CANCELLED };
enum class VehicleType { SEDAN, SUV, AUTO };

// Forward Declarations
class Rider;
class Driver;
class Trip;
class Location;

// ===================================
// == CORE ENTITY CLASSES ==
// ===================================
class Location {
public:
    double latitude; double longitude;
    Location(double lat, double lon) : latitude(lat), longitude(lon) {}
};

class Vehicle {
public:
    string licensePlate; string model; VehicleType type;
    Vehicle(string plate, string model, VehicleType type) : 
        licensePlate(plate), model(model), type(type) {}
};

class User {
protected: int id; string name;
public:
    User(int id, string name) : id(id), name(name) {}
    virtual ~User() {}
};

class Rider : public User {
public:
    Rider(int id, string name) : User(id, name) {}
};

class Driver : public User {
private:
    Vehicle* vehicle;
    Location currentLocation;
    bool isAvailable;
public:
    Driver(int id, string name, Vehicle* v, Location loc) : 
        User(id, name), vehicle(v), currentLocation(loc), isAvailable(true) {}
};

// ===================================
// == BUSINESS LOGIC CLASS ==
// ===================================
class Trip {
private:
    int id;
    Rider* rider;
    Driver* driver;
    Location startLocation;
    Location endLocation;
    TripStatus status;
    double fare;
public:
    Trip(int id, Rider* r, const Location& start, const Location& end);
    void assignDriver(Driver* d);
    void completeTrip();
    void calculateFare();
};

// ===================================
// == MAIN CONTROLLER (FACADE) ==
// ===================================
class RideSharingPlatform {
private:
    map<int, Rider*> riders;
    map<int, Driver*> drivers;
    // Concurrency ke liye yahan mutex lagega
    // mutex mtx;
public:
    void registerRider(Rider* r);
    void registerDriver(Driver* d);

    // Core functionality
    Trip* requestRide(int riderId, const Location& start, const Location& end);
    vector<Driver*> findNearbyDrivers(const Location& pickupLocation); // Uses geospatial index
    void completeTrip(int tripId);
};


// main function jahan se program shuru hoga
int main() {
    cout << "Ride-Sharing (Uber) System Design Ready!" << endl;
    
    // System setup karna
    RideSharingPlatform uber;
    uber.registerRider(new Rider(1, "Amit"));
    uber.registerDriver(new Driver(101, "Ramesh", 
        new Vehicle("UP70-D1234", "Swift Dzire", VehicleType::SEDAN), 
        Location(25.43, 81.84) // Prayagraj location
    ));

    // Ek rider Prayagraj mein ride request karta hai
    cout << "\n--- Ride Request ---" << endl;
    Location pickup(25.44, 81.85); // Civil Lines, Prayagraj
    Location drop(25.47, 81.84); // Prayagraj Junction
    
    Trip* trip = uber.requestRide(1, pickup, drop);
    
    if (trip) {
        cout << "Ride request safal! Nazdeeki driver dhoondha ja raha hai..." << endl;
        // Backend mein driver assign hoga, trip start hogi, aur complete hogi.
    } else {
        cout << "Maaf kijiye, abhi koi driver uplabdh nahi hai." << endl;
    }

    return 0;
}
```

---

Bilkul\! Let's design an **Online Stock Brokerage System** using your checklist.

Here is the Low-Level Design (LLD) for an Online Stock Brokerage System in Hinglish.

-----

### 1\. **Requirements Gathering (Zarooraton ko Jama Karna)** 📋

#### **Functional Requirements (Kaam Kya Karna Hai?)**

  * **User Management**: Users ko register karna, login karna, aur apna profile manage karna.
  * **Account Management**: Har user ka ek trading account hoga jismein woh paise **deposit** (jama) aur **withdraw** (nikaal) kar sakega.
  * **Stock Discovery**: Users alag-alag stocks ko search kar sakte hain unke naam ya ticker symbol se (e.g., "RELIANCE", "TCS"). Real-time stock prices dikhne chahiye.
  * **Order Placement**: Users stocks ko **buy** (kharid) ya **sell** (bech) karne ke liye orders place kar sakte hain. Shuru mein hum **Market Orders** (jo current market price pe execute ho) aur **Limit Orders** (jo user ke set kiye gaye price pe execute ho) support karenge.
  * **Portfolio Viewing**: Users apna portfolio dekh sakte hain - unke paas kaunse stocks hain, kitni quantity mein hain, aur unki current value kya hai.
  * **Order History**: Users apne saare past orders (pending, completed, cancelled) dekh sakte hain.

#### **Non-Functional Requirements (System Kaisa Hona Chahiye?)**

  * **Low Latency**: Orders jaldi se jaldi place aur execute hone chahiye, kyunki stock prices seconds mein badalte hain.
  * **High Availability**: System hamesha available rehna chahiye, especially market hours ke dauraan. Downtime ka matlab financial loss ho sakta hai.
  * **Concurrency**: System ko ek saath hazaron users ke orders handle karna aana chahiye.
  * **Security**: User data aur financial transactions secure hone chahiye.
  * **Reliability**: Ek baar order place ho gaya, toh woh fail nahi hona chahiye unless koi valid reason ho (jaise insufficient funds).

#### **Assumptions (Hum Kya Maan Ke Chal Rahe Hain?)**

  * Stock market ka real-time data ek third-party service (jaise exchange APIs) se mil raha hai.
  * System shuru mein sirf equities (stocks) ko handle karega, options ya futures ko nahi.
  * Saare financial regulations aur compliance ka dhyan rakha gaya hai.

-----

### 2\. **Core Objects & Entities (Mukhya Classes aur Unke Hisse)** 🧱

Humaare system ke main building blocks yeh honge:

  * **`User`**: Jo insaan system use kar raha hai.

      * **Attributes**: `userId`, `name`, `email`, `password`
      * **Methods**: `register()`, `login()`

  * **`Account`**: User ka trading account.

      * **Attributes**: `accountId`, `userId`, `balance`, `portfolio`
      * **Methods**: `deposit(amount)`, `withdraw(amount)`

  * **`Portfolio`**: User ke saare stock holdings ka collection.

      * **Attributes**: `holdings` (a map of `Stock` to `quantity`)
      * **Methods**: `addStock(stock, quantity)`, `removeStock(stock, quantity)`

  * **`Stock`**: Ek company ka share.

      * **Attributes**: `tickerSymbol`, `companyName`, `currentPrice`
      * **Methods**: `updatePrice(newPrice)`

  * **`Order`**: Ek buy ya sell request.

      * **Attributes**: `orderId`, `userId`, `stock`, `orderType` (BUY/SELL), `quantity`, `status` (PENDING, EXECUTED, CANCELLED)
      * **Methods**: `placeOrder()`, `cancelOrder()`

-----

### 3\. **Relationships (Classes Ka Aapas Mein Rishta)** 🤝

  * **`User` and `Account`**: Ek **User** ka ek hi **Account** hoga. (One-to-One)
  * **`Account` and `Portfolio`**: Ek **Account** ka ek hi **Portfolio** hoga. (Composition - `Portfolio` `Account` ke bina exist nahi kar sakta).
  * **`Portfolio` and `Stock`**: Ek **Portfolio** mein bahut saare **Stocks** ho sakte hain. (One-to-Many through holdings).
  * **`User` and `Order`**: Ek **User** bahut saare **Orders** place kar sakta hai. (One-to-Many).
  * **Inheritance for Orders**: Hum `Order` ko ek base class bana sakte hain aur usse `MarketOrder` aur `LimitOrder` jaisi specific classes inherit kar sakti hain. Yeh system ko **extensible** banata hai.

-----

### 4\. **Data Storage (Data Kahan Rakhein?)** 🗄️

  * **User Data, Accounts, Portfolio, Order History**: Yeh sab data **relational database** (jaise PostgreSQL ya MySQL) mein store karna aasan aur reliable hoga kyunki transactions important hain (ACID properties).
  * **Real-time Stock Prices**: Stock prices bahut tezi se badalte hain. Inhe ek **in-memory cache** jaise **Redis** mein store karna behtar hai taaki read operations fast hon.
  * **Order Book**: Pending buy/sell orders ko bhi in-memory store karna zaroori hai taaki matching engine tezi se kaam kar sake.

-----

### 5\. **Concurrency & Synchronization (Ek Saath Kai Kaam Sambhalna)** ⚡

Yeh sabse critical part hai. Maan lijiye ek stock ke sirf 10 shares available hain aur 100 log ek saath unhe kharidne ki koshish karte hain.

  * **Problem**: Race Condition. Agar hum check aur deduct alag-alag karte hain, toh ho sakta hai hum 10 se zyada shares sell kar dein.
  * **Solution**: **Database Transactions with Locking**. Jab koi user order place karta hai, hum order processing ko ek transaction mein wrap karenge. Hum `SELECT ... FOR UPDATE` ka use kar sakte hain taaki jab tak ek transaction complete na ho, doosra transaction usi stock ke liye wait kare.
  * **Order Matching Engine**: Ek dedicated service (matching engine) hogi jo continuously buy aur sell orders ko match karegi. Ise thread-safe banana bahut zaroori hai. Iske liye hum producer-consumer pattern (using a message queue) ka use kar sakte hain.

-----

### 6\. **Scalability (System ko Bada Kaise Karein?)** 📈

Jab users 10 se 10 million ho jayenge, toh system slow nahi hona chahiye.

  * **Microservices**: System ko chhote-chhote, independent services mein tod denge: `UserService`, `OrderService`, `PortfolioService`, `NotificationService`. Har service ko independently scale kiya ja sakta hai.
  * **Message Queue**: User se order lene ke baad, `OrderService` use ek **Message Queue** (jaise RabbitMQ ya Kafka) mein daal dega. Ek alag `MatchingEngine` service wahan se orders utha kar process karegi. Isse system responsive rehta hai, bhale hi background mein load zyada ho.
  * **Load Balancer**: Incoming traffic ko alag-alag server instances par distribute karne ke liye load balancer ka use karenge taaki koi ek server overload na ho.
  * **Database Scaling**: Read replicas ka use karke database par read load ko distribute kar sakte hain.

-----

### 7\. **Error Handling (Galtiyon se Kaise NIPTEIN?)** ⚠️

  * **Insufficient Funds**: Agar user ke account mein paise kam hain, toh order reject ho jayega with a clear error message. `placeOrder` method pehle balance check karega.
  * **Invalid Stock**: Agar user kisi aise stock ko kharidne ki koshish karta hai jo exist nahi karta, toh error show hoga.
  * **Market Closed**: Agar user market hours ke baad order place karta hai, toh order `PENDING` state mein rahega aur market open hone par execute hoga.
  * **Third-party API Failure**: Agar stock price fetch karne wali external API down hai, toh user ko ek temporary error message dikhayenge aur system ko gracefully handle karenge.

-----

### 8\. **Design Principles (Achhe Design ke Usool)** 💡

  * **Single Responsibility Principle (SRP)**: `Order` class sirf order se related kaam karegi. User ko notification bhejne ka kaam `NotificationService` ka hoga.
  * **Open/Closed Principle (OCP)**: Humara design aisa hona chahiye ki naye features add karne ke liye existing code ko change na karna pade. Jaise, agar kal `StopLossOrder` add karna ho, toh hum sirf ek nayi class `StopLossOrder` banayenge jo `Order` se inherit karegi, `OrderService` mein zyada badlav nahi karna padega (Strategy Pattern).
  * **Separation of Concerns**: Business logic, data access, aur UI alag-alag layers mein honge.

-----

### 9\. **APIs & Interfaces (Baat-cheet ka Zariya)** 🌐

Hum REST APIs expose kar sakte hain:

  * **`POST /api/v1/orders`**: Naya order place karne ke liye.
      * **Request Body**: `{ "userId": "u123", "ticker": "TCS", "quantity": 10, "orderType": "MARKET", "transactionType": "BUY" }`
      * **Response**: `{ "orderId": "o987", "status": "PENDING" }`
  * **`GET /api/v1/portfolio/{userId}`**: User ka portfolio dekhne ke liye.
      * **Response**: `{ "holdings": [ { "ticker": "TCS", "quantity": 10, "currentValue": 35000 }, ... ], "totalValue": 35000 }`
  * **`DELETE /api/v1/orders/{orderId}`**: Pending order ko cancel karne ke liye.

-----

### **Sample Code (Hinglish Mein)**

#### **C++ Code Example**

Yeh ek basic structure hai core classes ka C++ mein.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward declaration
class User;

// Enum for different states and types
enum OrderType { BUY, SELL };
enum OrderStatus { PENDING, EXECUTED, CANCELLED };

class Stock {
public:
    string ticker;
    double price;

    Stock(string t, double p) : ticker(t), price(p) {}

    void updatePrice(double newPrice) {
        this->price = newPrice;
    }
};

class Order {
public:
    string orderId;
    User* user;
    Stock* stock;
    OrderType type;
    OrderStatus status;
    int quantity;

    Order(User* u, Stock* s, OrderType t, int qty) {
        this->orderId = "ORD" + to_string(rand() % 1000); // Simple ID generation
        this->user = u;
        this->stock = s;
        this->type = t;
        this->quantity = qty;
        this->status = PENDING;
    }

    void execute() {
        this->status = EXECUTED;
        cout << "Order " << orderId << " for " << stock->ticker << " executed!" << endl;
    }
};

class Portfolio {
public:
    map<Stock*, int> holdings; // Stock -> Quantity

    void addStock(Stock* s, int qty) {
        holdings[s] += qty;
        cout << qty << " shares of " << s->ticker << " added to portfolio." << endl;
    }

    void removeStock(Stock* s, int qty) {
        if (holdings.count(s) && holdings[s] >= qty) {
            holdings[s] -= qty;
            cout << qty << " shares of " << s->ticker << " removed from portfolio." << endl;
        } else {
            cout << "Not enough shares to sell." << endl;
        }
    }
    
    void display() {
        cout << "--- Portfolio ---" << endl;
        for(auto const& [stock, qty] : holdings) {
            cout << "Stock: " << stock->ticker << ", Quantity: " << qty << endl;
        }
        cout << "-----------------" << endl;
    }
};


class Account {
public:
    string accountId;
    double balance;
    Portfolio portfolio;

    Account(string id, double initialBalance) {
        this->accountId = id;
        this->balance = initialBalance;
    }

    bool placeOrder(Order* order) {
        if (order->type == BUY) {
            double requiredAmount = order->stock->price * order->quantity;
            if (balance >= requiredAmount) {
                balance -= requiredAmount;
                portfolio.addStock(order->stock, order->quantity);
                order->execute();
                return true;
            } else {
                cout << "Error: Insufficient funds!" << endl;
                return false;
            }
        } else { // SELL
            if (portfolio.holdings.count(order->stock) && portfolio.holdings[order->stock] >= order->quantity) {
                balance += order->stock->price * order->quantity;
                portfolio.removeStock(order->stock, order->quantity);
                order->execute();
                return true;
            } else {
                cout << "Error: You don't own enough shares to sell!" << endl;
                return false;
            }
        }
    }
};

class User {
public:
    string userId;
    string name;
    Account* account;

    User(string id, string n, double initialBalance) {
        this->userId = id;
        this->name = n;
        this->account = new Account("ACC_" + id, initialBalance);
    }
};


int main() {
    // Setup
    User* user1 = new User("U1", "Ramesh", 100000.0);
    Stock* tcs = new Stock("TCS", 3500.0);
    Stock* reliance = new Stock("RELIANCE", 2800.0);

    // Ramesh wants to buy 10 shares of TCS
    cout << "Ramesh is buying 10 shares of TCS..." << endl;
    Order* buyOrder = new Order(user1, tcs, BUY, 10);
    user1->account->placeOrder(buyOrder);
    
    cout << "\nCurrent Balance: " << user1->account->balance << endl;
    user1->account->portfolio.display();

    cout << "\n--------------------------------\n";

    // Ramesh wants to sell 5 shares of TCS
    cout << "\nRamesh is selling 5 shares of TCS..." << endl;
    Order* sellOrder = new Order(user1, tcs, SELL, 5);
    user1->account->placeOrder(sellOrder);

    cout << "\nCurrent Balance: " << user1->account->balance << endl;
    user1->account->portfolio.display();
    
    return 0;
}
```

---

Ek music streaming service jaise Spotify ka core design ek **`User`** ke ird-gird hota hai, jo **`Song`s** ke ek vishal catalog ke saath interact karta hai. Iske mukhya features hain music stream karna, **`Playlist`s** banana, aur **`Subscription`s** manage karna. Is design ka ek mahatvapurna hissa **Strategy Design Pattern** hai, jiska istemal alag-alag user subscription levels (jaise `Free` vs. `Premium`) ko handle karne ke liye kiya jaata hai, jo ad-free sunne aur download jaise features ko nirdharit karta hai. Ek central **`MusicStreamingService`** class poore platform ko manage karti hai.

-----

### \#\# 1. Zarooriyat (Requirements)

  * **Functional Requirements (Kaam kya karega?):**

      * Users gaane (songs) search aur play kar sakenge.
      * Users playlists bana aur manage kar sakenge.
      * System alag-alag subscription tiers offer karega (Free ads ke saath, Premium bina ads ke).
      * Premium users offline sunne ke liye gaane download kar sakenge.
      * Service users ko unke pasand ke aadhar par gaane recommend karegi.

  * **Non-Functional Requirements (Performance, etc.):**

      * **Low Latency:** Gaane stream karne mein deri bahut kam honi chahiye.
      * **High Availability:** Service hamesha uplabdh honi chahiye.
      * **Scalability:** System ko laakhon users ko support karne ke liye scalable hona chahiye.

  * **Assumptions (Hum kya maan kar chal rahe hain):**

      * Hum streaming, playlists, aur subscriptions ke core logic ko design kar rahe hain.

-----

### \#\# 2. Mukhya Objects (Core Objects)

1.  **`User`:**

      * **Attributes:** `userId`, `name`, `Subscription* subscription` (user ka current plan).

2.  **`Song`:**

      * **Attributes:** `songId`, `title`, `artist`, `album`, `duration`.

3.  **`Playlist`:**

      * Gaanon ka ek collection.
      * **Attributes:** `playlistId`, `name`, `owner` (User\*), `vector<Song*> songs`.

4.  **`Subscription` (Abstract Class - Strategy Pattern):**

      * Ek subscription plan ke liye ek blueprint.
      * **Methods:** `canPlayAdFree()`, `getDownloadLimit()` (dono **pure virtual** - **Abstraction**).

5.  **Concrete Subscriptions (`FreeSubscription`, `PremiumSubscription`):**

      * Yeh `Subscription` se inherit karenge (**Inheritance**) aur in methods ko apne-apne plan ke anusaar implement karenge (**Polymorphism**).

6.  **`MusicStreamingService` (Main Controller / Facade):**

      * Poore platform ko manage karta hai.
      * **Attributes:** `map<int, Song*> songCatalog`, `map<int, User*> users`.
      * **Methods:** `registerUser()`, `searchSong()`.

-----

### \#\# 3. Classes ke Beech Rishte (Relationships)

  * **Composition:** `User` **has-a** `Subscription`. `Playlist` **has-many** `Song`s.
  * **Strategy Pattern:** `User` class apni kshamataon (capabilities) ko nirdharit karne ke liye ek `Subscription` strategy ka istemal karti hai.
  * **Inheritance:** `PremiumSubscription` **is-a** `Subscription`.

-----

### \#\# 4. Data Storage

  * **Object Storage (jaise Amazon S3):** Asli audio files (MP3, AAC) ko store karne ke liye.
  * **Metadata Database (NoSQL ya SQL):** Gaanon ka metadata (title, artist), user data, aur playlists ko store karne ke liye.
  * **Caching (jaise Redis):** Aksar access kiye jaane wale data jaise user playlists aur popular gaanon ke metadata ke liye.

-----

### \#\# 5. Concurrency

  * Laakhon users dwara ek hi samay par streaming, searching, aur playlists update karne se high concurrency hoti hai. Isko handle karne ke liye backend ko stateless hona chahiye.

-----

### \#\# 6. Scalability

  * Yeh ek bahut bade paimane ka system hai.
  * **Microservices Architecture:** User authentication, search, streaming, playlist management, aadi ke liye alag-alag services.
  * **Content Delivery Network (CDN):** Yeh **atyant mahatvapurna** hai. Audio files ko duniya bhar mein faile CDN edge servers (jaise ek Prayagraj ke paas) par cache kiya jaata hai taaki har jagah ke users ko low-latency streaming mile.

-----

### \#\# 7. Galtiyon ko Sambhalna (Error Handling)

  * Streaming failure (network samasya).
  * Licensing ke kaaran kisi gaane ka kisi kshetra (region) mein uplabdh na hona.
  * Subscription renewal ke liye payment fail ho jaana.

-----

### \#\# 8. Design ke Siddhant (Principles)

  * **Strategy Pattern:** Alag-alag subscription tiers ko manage karne ke liye yeh ekdam sahi hai. Isse ek naya tier (jaise `FamilyPlan`) jodna aasan ho jaata hai, sirf ek nayi strategy class banakar (**Open/Closed Principle**).
  * **Facade Pattern:** `MusicStreamingService` class client application ke liye ek saral API pradan karti hai taaki woh complex backend services se interact kar sake.
  * **SRP:** Har class aur microservice ka ek hi, focused kaam hai.

-----

### \#\# 9. APIs

  * APIs ka combination istemal hota hai:
      * **REST API:** Zyada-tar interactions jaise searching, playlist manage karna, aur user profiles ke liye. `GET /search?q=...`, `GET /playlists/{id}`.
      * **Streaming Protocol (jaise HLS ya DASH):** Asli audio ek simple REST API par nahi bheji jaati. Yeh protocols audio ko chhote-chhote hisson (chunks) mein tod dete hain, jisse client unhe kram se (sequentially) request kar sakta hai aur badalte network conditions ke anusaar adapt kar sakta hai.

-----

### \#\# Music Streaming Service ka C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class User;
class Song;
class Subscription;

// ===================================
// == SUBSCRIPTION HIERARCHY (STRATEGY PATTERN) ==
// ===================================
// Abstract class for subscription plans
class Subscription {
public:
    virtual bool canPlayAdFree() = 0; // Abstraction
    virtual int getDownloadLimit() = 0;
    virtual string getPlanName() = 0;
    virtual ~Subscription() {}
};

class FreeSubscription : public Subscription { // Inheritance
public:
    bool canPlayAdFree() override { return false; } // Polymorphism
    int getDownloadLimit() override { return 0; }
    string getPlanName() override { return "Free Plan"; }
};

class PremiumSubscription : public Subscription {
public:
    bool canPlayAdFree() override { return true; }
    int getDownloadLimit() override { return 1000; }
    string getPlanName() override { return "Premium Plan"; }
};

// ===================================
// == CORE BUSINESS CLASSES ==
// ===================================
class Song {
public:
    int id; string title; string artist;
    Song(int id, string title, string artist) : id(id), title(title), artist(artist) {}
};

class Playlist {
private:
    int id; string name; User* owner; vector<Song*> songs;
public:
    Playlist(int id, string name, User* owner);
    void addSong(Song* song);
};

class User {
private:
    int id;
    string name;
    Subscription* subscription; // Strategy
public:
    User(int id, string name) : id(id), name(name) {
        // Har naya user free plan se shuru karta hai
        subscription = new FreeSubscription();
    }
    ~User() {
        delete subscription;
    }
    void playSong(Song* song) {
        cout << name << " is playing '" << song->title << "'." << endl;
        if (!subscription->canPlayAdFree()) {
            cout << "   > Playing an Ad for the free user." << endl;
        }
    }
    void upgradeSubscription(Subscription* newPlan) {
        delete subscription;
        subscription = newPlan;
        cout << name << " ne " << subscription->getPlanName() << " par upgrade kar liya hai." << endl;
    }
    string getName() { return name; }
};

// ===================================
// == MAIN CONTROLLER (FACADE) ==
// ===================================
class MusicStreamingService {
private:
    map<int, Song*> songCatalog;
    map<int, User*> users;
public:
    ~MusicStreamingService() {
        for(auto const& [key, val] : songCatalog) delete val;
        for(auto const& [key, val] : users) delete val;
    }
    void registerUser(int id, string name) {
        users[id] = new User(id, name);
    }
    void addSong(Song* song) {
        songCatalog[song->id] = song;
    }
    User* getUser(int id) { return users[id]; }
    Song* getSong(int id) { return songCatalog[id]; }
};

// main function jahan se program shuru hoga
int main() {
    MusicStreamingService spotify;
    spotify.registerUser(101, "Amit");
    spotify.addSong(new Song(1, "Kesariya", "Arijit Singh"));

    User* user = spotify.getUser(101);
    Song* song = spotify.getSong(1);

    cout << "--- " << user->getName() << " (Free User) Prayagraj mein gaana sun raha hai ---" << endl;
    user->playSong(song);

    cout << "\n--- Subscription Upgrade ---" << endl;
    user->upgradeSubscription(new PremiumSubscription());
    
    cout << "\n--- " << user->getName() << " (Premium User) ab gaana sun raha hai ---" << endl;
    user->playSong(song);

    return 0;
}
```

---
For a large, enterprise-level system like this, **Java** is generally preferable due to its strong ecosystem (Spring Framework), robustness, and platform independence. Isliye, code example Java mein hoga.

Here is the Low-Level Design (LLD) for an Online Shopping Service in Hinglish.

-----

### 1\. **Requirements Gathering (Zarooraton ko Jama Karna)** 📋

#### **Functional Requirements (Kaam Kya Karna Hai?)**

  * **User Management**: Users ko sign-up, login, aur profile manage karne ki suvidha. Users apni address book bhi manage kar sakte hain.
  * **Product Catalog**: Products ko search, browse by category, aur view karne ki functionality. Har product ka ek detailed page hoga (images, description, reviews, price).
  * **Shopping Cart**: Users products ko apne cart mein add, remove, aur quantity update kar sakte hain.
  * **Checkout Process**: User apne cart se checkout kar sakta hai, shipping address select kar sakta hai, aur payment method choose kar sakta hai.
  * **Payment Gateway Integration**: Alag-alag payment methods jaise Credit/Debit Card, UPI, Net Banking ko support karna.
  * **Order Management**: User apne past aur current orders ka status track kar sakta hai (Placed, Shipped, Delivered, Cancelled).
  * **Reviews and Ratings**: Users products par reviews aur ratings de sakte hain.

#### **Non-Functional Requirements (System Kaisa Hona Chahiye?)**

  * **High Availability**: Platform 24/7 available hona chahiye, kyunki users kabhi bhi shopping kar sakte hain.
  * **Scalability**: System ko sale events (jaise Big Billion Days) ke time high traffic handle karne ke liye scale hona chahiye.
  * **Low Latency**: Product search aur page load time bahut kam hona chahiye for a good user experience.
  * **Consistency**: Inventory (stock count) hamesha consistent rehna chahiye. Aisa na ho ki out-of-stock item order ho jaaye.
  * **Security**: User data aur payment information highly secure honi chahiye.

#### **Assumptions (Hum Kya Maan Ke Chal Rahe Hain?)**

  * Payment processing ke liye hum third-party payment gateways (jaise Razorpay, Stripe) ka use karenge.
  * Product delivery ke liye third-party logistics partners (jaise Delhivery, Blue Dart) honge.
  * Products alag-alag sellers list kar sakte hain (marketplace model).

-----

### 2\. **Core Objects & Entities (Mukhya Classes aur Unke Hisse)** 🧱

Humaare system ke main building blocks yeh honge:

  * **`User`**: Jo customer shopping kar raha hai.

      * **Attributes**: `userId`, `name`, `email`, `password`, `shippingAddresses`, `shoppingCart`
      * **Methods**: `register()`, `login()`, `addAddress()`, `addToCart()`

  * **`Product`**: Jo item becha jaa raha hai.

      * **Attributes**: `productId`, `name`, `description`, `price`, `category`, `seller`, `availableStock`
      * **Methods**: `updateStock(quantity)`

  * **`ShoppingCart`**: User ke selected items ka temporary collection.

      * **Attributes**: `cartId`, `items` (Map of `Product` to `quantity`)
      * **Methods**: `addItem(product, quantity)`, `removeItem(product)`, `updateItemQuantity(...)`, `checkout()`

  * **`Order`**: Ek confirmed purchase transaction.

      * **Attributes**: `orderId`, `user`, `orderedItems`, `totalAmount`, `shippingAddress`, `orderStatus` (e.g., `PLACED`, `SHIPPED`, `DELIVERED`)
      * **Methods**: `trackOrder()`, `cancelOrder()`

  * **`Payment`**: Order se जुड़ी payment details.

      * **Attributes**: `paymentId`, `orderId`, `amount`, `paymentStatus` (`PENDING`, `COMPLETED`, `FAILED`), `paymentMode`
      * **Methods**: `processPayment()`

-----

### 3\. **Relationships (Classes Ka Aapas Mein Rishta)** 🤝

  * **`User` and `ShoppingCart`**: Ek **User** ka ek hi **ShoppingCart** hota hai. (One-to-One Composition)
  * **`User` and `Order`**: Ek **User** ke multiple **Orders** ho sakte hain. (One-to-Many)
  * **`ShoppingCart` and `Product`**: Ek **ShoppingCart** mein multiple **Products** ho sakte hain. (Many-to-Many, usually handled through a `CartItem` class).
  * **`Order` and `Product`**: Ek **Order** mein multiple **Products** ho sakte hain. (Many-to-Many, handled through an `OrderItem` class).
  * **Strategy Pattern for Payment**: Hum ek `PaymentStrategy` interface bana sakte hain jisko `CreditCardPayment`, `UpiPayment` jaisi classes implement karengi. Yeh OCP ko follow karta hai.

-----

### 4\. **Data Storage (Data Kahan Rakhein?)** 🗄️

  * **Relational Database (e.g., PostgreSQL)**: User data, Orders, Payments, aur Product inventory jaise structured data ke liye best hai. Yahan ACID properties zaroori hain.
  * **NoSQL Database (e.g., MongoDB/Elasticsearch)**: Product Catalog, user reviews, aur search functionality ke liye aacha hai. Elasticsearch search ko bahut fast bana dega.
  * **In-Memory Cache (e.g., Redis)**: User sessions, shopping carts, aur frequently browsed products ke data ko cache karne ke liye. Isse database par load kam hota hai aur speed badhti hai.

-----

### 5\. **Concurrency & Synchronization (Ek Saath Kai Kaam Sambhalna)** ⚡

Sabse badi concurrency problem **inventory management** hai.

  * **Problem**: Maan lijiye ek phone ka last piece bacha hai. Do users (A aur B) ne use apne cart mein add kiya hai aur lagbhag ek hi time par 'Pay Now' button click karte hain.
  * **Solution**: **Database Transaction with Pessimistic Locking**. Jab user payment page par jaata hai, hum inventory table mein uss product ki row par ek lock (`SELECT ... FOR UPDATE`) laga denge. Jab user A ka payment successful ho jaayega, hum stock ko 1 se kam karke transaction commit kar denge aur lock release ho jaayega. Jab user B ka request aayega, use stock 0 milega aur order fail ho jaayega. Isse overselling nahi hogi.

-----

### 6\. **Scalability (System ko Bada Kaise Karein?)** 📈

  * **Microservices Architecture**: System ko independent services mein divide karna zaroori hai: `ProductService`, `UserService`, `CartService`, `OrderService`, `PaymentService`, `NotificationService`. Har service ko alag se scale kiya jaa sakta hai.
  * **Message Queue (e.g., Kafka)**: Services aapas mein communicate karne ke liye message queue ka use karengi. Jab ek order place hota hai, `OrderService` ek `ORDER_PLACED` event publish karta hai. `InventoryService` (stock kam karne ke liye) aur `NotificationService` (user ko email/SMS bhejne ke liye) uss event ko consume karke apna kaam karte hain. Yeh system ko **decoupled** aur resilient banata hai.
  * **CDN (Content Delivery Network)**: Product images aur videos jaisi static files ko CDN par host karna chahiye. Isse user ke nazdeeki server se files load hongi aur website fast ho jaayegi.
  * **Load Balancer**: Incoming user traffic ko multiple servers par distribute karne ke liye.

-----

### 7\. **Error Handling (Galtiyon se Kaise NIPTEIN?)** ⚠️

  * **Payment Failure**: Agar payment fail hota hai, toh order `FAILED` state mein jaayega. Agar humne stock pehle hi reserve kar liya tha, toh use revert karna hoga. User ko clear message dikhana hoga ki "Payment failed, please try again."
  * **Out of Stock during Checkout**: Agar user checkout karne jaata hai aur item out of stock ho jaata hai, use cart page par ek clear message ke saath redirect karna chahiye.
  * **Service Down**: Agar `PaymentService` down hai, toh checkout page par payment options disable kar dene chahiye aur ek message dikhana chahiye, "Payment service is temporarily unavailable." Iske liye **Circuit Breaker** pattern ka use hota hai.

-----

### 8\. **Design Principles (Achhe Design ke Usool)** 💡

  * **Single Responsibility Principle (SRP)**: `OrderService` sirf order create aur manage karega. Payment ke liye woh `PaymentService` ko call karega.
  * **Open/Closed Principle (OCP)**: Agar humein ek naya payment method jaise "Pay on Delivery" add karna hai, toh hum sirf ek nayi `PayOnDeliveryStrategy` class banayenge. Existing payment logic ko change nahi karna padega. (Strategy Pattern).
  * **Separation of Concerns**: UI (Frontend), business logic (Backend services), aur data storage (Databases) ko alag-alag layers mein rakha jaayega.

-----

### 9\. **APIs & Interfaces (Baat-cheet ka Zariya)** 🌐

System aapas mein aur client (web/mobile app) ke saath REST APIs ke through communicate karega:

  * **`GET /api/products/search?query={productName}`**: Products ko search karne ke liye.
  * **`POST /api/cart/{userId}/items`**: User ke cart mein item add karne ke liye.
      * **Body**: `{ "productId": "p123", "quantity": 1 }`
  * **`POST /api/orders`**: Cart se order create karne ke liye.
      * **Body**: `{ "userId": "u456", "addressId": "addr789", "paymentMode": "UPI" }`
  * **`GET /api/orders/{orderId}/status`**: Order ka current status janne ke liye.

-----

### **Java Code Example**

Yeh ek simplified Java code hai jo core concepts ko dikhata hai.

```java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

// Enums for status management
enum OrderStatus { CREATED, PLACED, SHIPPED, DELIVERED, CANCELLED }
enum PaymentStatus { PENDING, SUCCESS, FAILED }

// Core Entities
class Product {
    String productId;
    String name;
    double price;
    int availableStock;

    public Product(String id, String name, double price, int stock) {
        this.productId = id;
        this.name = name;
        this.price = price;
        this.availableStock = stock;
    }

    // A synchronized method to handle inventory safely in a concurrent environment
    public synchronized boolean reduceStock(int quantity) {
        if (availableStock >= quantity) {
            availableStock -= quantity;
            return true;
        }
        return false;
    }
}

class User {
    String userId;
    String name;
    ShoppingCart cart;
    List<Address> addresses;

    public User(String id, String name) {
        this.userId = id;
        this.name = name;
        this.cart = new ShoppingCart(this);
        this.addresses = new ArrayList<>();
    }
}

class Address {
    String street;
    String city;
    String pincode;
    // Constructor and other fields
}

class ShoppingCart {
    User user;
    // Product -> Quantity
    Map<Product, Integer> items = new HashMap<>();

    public ShoppingCart(User user) {
        this.user = user;
    }

    public void addItem(Product product, int quantity) {
        items.put(product, items.getOrDefault(product, 0) + quantity);
        System.out.println(quantity + " x " + product.name + " added to cart.");
    }

    public void removeItem(Product product) {
        items.remove(product);
    }
    
    public double calculateTotal() {
        double total = 0;
        for (Map.Entry<Product, Integer> entry : items.entrySet()) {
            total += entry.getKey().price * entry.getValue();
        }
        return total;
    }
}

class Order {
    String orderId;
    User user;
    Map<Product, Integer> orderedItems;
    double totalAmount;
    OrderStatus status;

    public Order(User user, Map<Product, Integer> items) {
        this.orderId = "ORD" + System.currentTimeMillis();
        this.user = user;
        this.orderedItems = new HashMap<>(items); // Create a copy
        this.totalAmount = calculateTotal(items);
        this.status = OrderStatus.CREATED;
    }

    private double calculateTotal(Map<Product, Integer> items) {
        return items.entrySet().stream()
                .mapToDouble(e -> e.getKey().price * e.getValue())
                .sum();
    }
}


// Service layer to handle business logic
class OrderService {
    // This method simulates the checkout process
    public Order placeOrder(User user) {
        ShoppingCart cart = user.cart;
        if (cart.items.isEmpty()) {
            System.out.println("Cart is empty. Cannot place order.");
            return null;
        }

        // --- THIS IS THE CRITICAL SECTION ---
        // In a real system, you'd start a DB transaction here.
        // We check stock availability for all items before creating an order.
        for (Map.Entry<Product, Integer> entry : cart.items.entrySet()) {
            if (entry.getKey().availableStock < entry.getValue()) {
                System.out.println("Error: " + entry.getKey().name + " is out of stock.");
                // Rollback transaction in a real system
                return null;
            }
        }
        
        // If all items are available, reduce stock and create order
        for (Map.Entry<Product, Integer> entry : cart.items.entrySet()) {
            entry.getKey().reduceStock(entry.getValue());
        }
        // --- END OF CRITICAL SECTION ---

        Order order = new Order(user, cart.items);
        order.status = OrderStatus.PLACED;
        
        // Clear the cart after placing order
        cart.items.clear();
        
        System.out.println("Order " + order.orderId + " placed successfully for user " + user.name);
        return order;
    }
}

// Main class to demonstrate the flow
public class ECommercePlatform {
    public static void main(String[] args) {
        // Setup
        User ramesh = new User("u123", "Ramesh");
        Product iphone = new Product("p001", "iPhone 15", 75000.0, 10);
        Product headphones = new Product("p002", "Sony WH-1000XM5", 25000.0, 20);

        // Ramesh shops
        ramesh.cart.addItem(iphone, 1);
        ramesh.cart.addItem(headphones, 1);
        
        System.out.println("Cart total: " + ramesh.cart.calculateTotal());
        
        // Ramesh checks out
        OrderService orderService = new OrderService();
        Order rameshOrder = orderService.placeOrder(ramesh);

        if (rameshOrder != null) {
            System.out.println("Order Status: " + rameshOrder.status);
            System.out.println("Remaining iPhone stock: " + iphone.availableStock);
            System.out.println("Ramesh's cart is now empty: " + ramesh.cart.items.isEmpty());
        }
    }
}
```

---

For a system with real-time tracking and high transaction volume, **Java** is an excellent choice because of its strong concurrency support and mature ecosystem for building scalable microservices. Isliye, the code example will be in Java.

Here's the Low-Level Design (LLD) for a Food Delivery System in Hinglish.

-----

### 1\. **Requirements Gathering (Zarooraton ko Jama Karna)** 📋

#### **Functional Requirements (Kaam Kya Karna Hai?)**

  * **Three Main Actors**: System ke 3 main users honge: **Customers**, **Restaurants**, and **Delivery Partners**.
  * **Restaurant Discovery**: Customers aas-paas ke restaurants search kar sakte hain, unka menu dekh sakte hain, aur unhe filter kar sakte hain (e.g., by cuisine, rating).
  * **Order Placement**: Customers menu items ko cart mein add karke order place kar sakte hain.
  * **Payment**: Multiple payment options (UPI, Card, COD) se payment karna.
  * **Real-time Order Tracking**: Customer apne order ko live track kar sakega - from "Order Placed" to "Delivered". Ismein delivery partner ki live location bhi dikhegi.
  * **Restaurant Dashboard**: Restaurants naye orders accept/reject kar sakte hain, menu manage kar sakte hain, aur order history dekh sakte hain.
  * **Delivery Partner App**: Delivery partners ko nearby order requests milengi, jise woh accept/reject kar sakte hain. Woh pickup aur delivery status update karenge.

#### **Non-Functional Requirements (System Kaisa Hona Chahiye?)**

  * **High Availability**: System lunch aur dinner jaise peak hours mein down nahi hona chahiye.
  * **Low Latency**: Restaurant search, order placement, aur especially location tracking bahut fast hona chahiye.
  * **Scalability**: System ko ek sheher se lekar poore desh tak scale karne ke liye design karna hoga.
  * **Consistency**: Order status (e.g., `ACCEPTED`, `PREPARING`) sabhi users (customer, restaurant, partner) ke liye consistent hona chahiye.
  * **Reliability**: Ek baar order accept ho gaya, toh system ko use reliably deliver karwana hai.

#### **Assumptions (Hum Kya Maan Ke Chal Rahe Hain?)**

  * Location aur maps ke liye hum third-party service jaise **Google Maps API** ka use karenge.
  * Payment processing ke liye **Payment Gateways** (e.g., Stripe, Razorpay) integrated honge.

-----

### 2\. **Core Objects & Entities (Mukhya Classes aur Unke Hisse)** 🧱

Humaare system ke main building blocks yeh honge:

  * **`Customer`**: Khana order karne wala user.

      * **Attributes**: `customerId`, `name`, `addressBook`, `cart`
      * **Methods**: `placeOrder()`, `trackOrder()`, `cancelOrder()`

  * **`Restaurant`**: Jahan se khana order kiya jaayega.

      * **Attributes**: `restaurantId`, `name`, `address`, `cuisineType`, `menu`, `isOpen`
      * **Methods**: `updateMenu()`, `acceptOrder()`, `markOrderReady()`

  * **`MenuItem`**: Restaurant ke menu ka ek item.

      * **Attributes**: `itemId`, `name`, `price`, `description`, `isAvailable`

  * **`DeliveryPartner`**: Jo order deliver karega.

      * **Attributes**: `partnerId`, `name`, `currentLocation` (GPS coordinates), `status` (`AVAILABLE`, `ON_DUTY`)

  * **`Order`**: Ek complete order ki details.

      * **Attributes**: `orderId`, `customer`, `restaurant`, `deliveryPartner`, `items`, `totalBill`, `deliveryAddress`, `orderStatus` (`PLACED`, `ACCEPTED_BY_RESTAURANT`, `PREPARING`, `READY_FOR_PICKUP`, `PICKED_UP`, `DELIVERED`)

-----

### 3\. **Relationships (Classes Ka Aapas Mein Rishta)** 🤝

  * **`Customer` and `Order`**: Ek **Customer** multiple **Orders** place kar sakta hai (One-to-Many).
  * **`Restaurant` and `MenuItem`**: Ek **Restaurant** ke **Menu** mein multiple **MenuItems** hote hain (One-to-Many Composition).
  * **`Restaurant` and `Order`**: Ek **Restaurant** ke paas multiple **Orders** aa sakte hain (One-to-Many).
  * **The `Order` Hub**: Ek **Order** hamesha 1 `Customer`, 1 `Restaurant`, aur (eventually) 1 `DeliveryPartner` se juda hota hai. Yeh in teeno actors ke beech ka central point hai.
  * **Strategy Pattern for Partner Assignment**: Hum alag-alag strategies use kar sakte hain partner assign karne ke liye, jaise `NearestPartnerStrategy` ya `BestRatedPartnerStrategy`.

-----

### 4\. **Data Storage (Data Kahan Rakhein?)** 🗄️

  * **Relational Database (e.g., PostgreSQL with PostGIS)**: Core data jaise Customer, Restaurant, aur Order details ke liye. PostgreSQL ka **PostGIS extension** geospatial data (locations) ko efficiently store aur query karne ke liye perfect hai.
  * **NoSQL Database (e.g., MongoDB)**: Restaurant menus aur user reviews ke liye accha hai, kyunki inka structure flexible ho sakta hai.
  * **In-Memory Data Grid/Cache (e.g., Redis)**: Delivery partners ki **live location** ko cache karne ke liye. Redis ke geospatial commands (`GEOADD`, `GEORADIUS`) iske liye bahut fast hain. Isse "mere 5km ke andar kitne partners available hain" jaisi queries milliseconds mein ho jaati hain. Ongoing orders ka status bhi yahan cache kar sakte hain.

-----

### 5\. **Concurrency & Synchronization (Ek Saath Kai Kaam Sambhalna)** ⚡

  * **Problem**: Ek order `READY_FOR_PICKUP` state mein hai. Restaurant ke paas 3 delivery partners available hain. Humein order sirf ek ko assign karna hai. Agar teeno ek saath order accept karte hain toh kya hoga?
  * **Solution**: **Distributed Locking aur Queues**.
    1.  Jab order ready ho, `OrderService` ek `DELIVERY_REQUEST` event ek **Message Queue** (e.g., RabbitMQ) mein publish karta hai.
    2.  `LogisticsService` is event ko sunta hai aur Redis se restaurant ke paas ke saare available partners ko dhoondta hai.
    3.  Yeh request un sabhi partners ko bheji jaati hai (fan-out).
    4.  Jo partner sabse pehle "Accept" karta hai, uski request `LogisticsService` tak aati hai.
    5.  Service uss `orderId` par ek **distributed lock** (e.g., using Redis's `SETNX` command) acquire karne ki koshish karti hai.
    6.  Jo pehla partner ka request lock acquire kar leta hai, use order assign ho jaata hai. Baaki sabki requests fail ho jaati hain kyunki lock pehle se acquired hai.
    7.  Finally, order ka status `PICKED_UP` update hota hai aur lock release ho jaata hai.

-----

### 6\. **Scalability (System ko Bada Kaise Karein?)** 📈

  * **Microservices**: Yeh architecture yahan bahut zaroori hai. Services honge: `AuthService`, `RestaurantService`, `OrderService`, `LogisticsService` (delivery partners aur live tracking ke liye), `PaymentService`, `NotificationService`.
  * **Asynchronous Communication**: Services aapas mein **Kafka** ya **RabbitMQ** jaise message broker ke through baat karenge. For example: `Order Placed` (event) -\> `RestaurantService` ko notification -\> `LogisticsService` partner dhoondhna shuru karega. Isse koi bhi service doosre ke response ka wait nahi karti aur system responsive rehta hai.
  * **Location Tracking**: Yeh sabse heavy part hai. Har partner har kuch seconds mein apni location update bhejega. In updates ko handle karne ke liye ek alag, highly scalable `LocationIngestionService` honi chahiye jo in events ko Kafka topic mein daale. Ek doosra service (`LocationProcessingService`) wahan se data consume karke Redis/PostGIS mein update karega.

-----

### 7\. **Error Handling (Galtiyon se Kaise NIPTEIN?)** ⚠️

  * **Restaurant Rejects Order**: Agar restaurant order accept nahi karta, order ko `CANCELLED` mark karo, customer ko `NotificationService` ke through inform karo aur `PaymentService` ko refund initiate karne ke liye event bhejo.
  * **No Delivery Partner Found**: Agar 5 minute tak koi delivery partner order accept nahi karta, order ko customer ki taraf se cancel karne ka option do ya automatically cancel karke refund process karo.
  * **Food Spill/Accident**: Delivery partner app mein ek "Help" button hona chahiye jisse woh support ko inform kar sake. Support team phir customer se coordinate karegi.
  * **Customer Unavailable**: Agar partner delivery location par hai aur customer available nahi hai, toh ek timer (e.g., 10 mins) ke baad order ko `DELIVERY_FAILED` mark kiya jaa sakta hai.

-----

### 8\. **Design Principles (Achhe Design ke Usool)** 💡

  * **Single Responsibility Principle (SRP)**: `LogisticsService` ka kaam sirf delivery partners ko manage karna aur unhe orders assign karna hai. Uska order ke payment se koi lena-dena nahi hai.
  * **Observer Pattern**: `Order` class ek "Subject" ho sakti hai. Customer, Restaurant, aur Delivery Partner "Observers" honge. Jab bhi `Order` ka status change hota hai (e.g., `PICKED_UP`), sabhi observers ko automatically update (via push notifications) mil jaayega.
  * **Decoupling**: Microservices aur Message Queues ka use karke hum services ko decouple karte hain. Agar `NotificationService` thodi der ke liye down ho jaaye, toh bhi order processing chalti rahegi.

-----

### 9\. **APIs & Interfaces (Baat-cheet ka Zariya)** 🌐

  * **Customer App APIs**:
      * `GET /api/v1/restaurants?lat={latitude}&long={longitude}`: Aas-paas ke restaurants dhoondne ke liye.
      * `POST /api/v1/orders`: Naya order place karne ke liye.
      * `GET /api/v1/orders/{orderId}/track`: Order aur delivery partner ki live location track karne ke liye.
  * **Delivery Partner App APIs**:
      * `GET /api/v1/partners/{partnerId}/orders/requests`: Naye order requests dekhne ke liye.
      * `POST /api/v1/orders/{orderId}/accept`: Order accept karne ke liye.
      * `POST /api/v1/partners/{partnerId}/location`: Apni live location update karne ke liye (WebSocket ya gRPC iske liye behtar hai).

-----

### **Java Code Example**

Yeh Java code core logic ko represent karta hai, especially order lifecycle aur partner assignment.

```java
import java.util.ArrayList;
import java.util.List;
import java.util.Optional;

// Enums for status management
enum OrderStatus {
    PLACED, ACCEPTED, PREPARING, READY_FOR_PICKUP, PICKED_UP, DELIVERED, CANCELLED
}
enum PartnerStatus {
    AVAILABLE, ON_DELIVERY
}

// Location class
class Location {
    double latitude;
    double longitude;
    // Constructor, getters
}

// Core Entities
class Customer { String customerId; String name; }
class Restaurant { String restaurantId; String name; Location location; }
class MenuItem { String itemId; String name; double price; }

class DeliveryPartner {
    String partnerId;
    String name;
    Location currentLocation;
    PartnerStatus status = PartnerStatus.AVAILABLE;
}

class Order {
    String orderId;
    Customer customer;
    Restaurant restaurant;
    List<MenuItem> items;
    DeliveryPartner assignedPartner;
    OrderStatus status = OrderStatus.PLACED;

    public Order(String id, Customer c, Restaurant r) {
        this.orderId = id;
        this.customer = c;
        this.restaurant = r;
    }

    public void setStatus(OrderStatus newStatus) {
        this.status = newStatus;
        System.out.println("Order " + orderId + " status updated to: " + newStatus);
        // This would trigger notifications to all observers (Customer, Restaurant etc.)
    }

    public void assignPartner(DeliveryPartner partner) {
        this.assignedPartner = partner;
        partner.status = PartnerStatus.ON_DELIVERY;
        setStatus(OrderStatus.PICKED_UP);
    }
}

// Service to find available partners (Logistics Service)
class DeliveryPartnerService {
    private List<DeliveryPartner> partners = new ArrayList<>(); // In real world, this comes from a DB/Cache

    public void addPartner(DeliveryPartner partner) {
        partners.add(partner);
    }

    // Simplified logic to find the nearest available partner
    public Optional<DeliveryPartner> findNearestAvailablePartner(Location restaurantLocation) {
        return partners.stream()
            .filter(p -> p.status == PartnerStatus.AVAILABLE)
            // In a real app, we'd calculate distance from restaurantLocation
            // and find the one with the minimum distance. Here we just take the first.
            .findFirst();
    }
}

// Main service handling the order flow
class OrderFulfillmentService {
    private DeliveryPartnerService partnerService;

    public OrderFulfillmentService(DeliveryPartnerService partnerService) {
        this.partnerService = partnerService;
    }

    // Restaurant marks order as ready for pickup
    public void markOrderReady(Order order) {
        order.setStatus(OrderStatus.READY_FOR_PICKUP);
        System.out.println("Searching for a delivery partner for order " + order.orderId);
        
        Optional<DeliveryPartner> availablePartner = partnerService.findNearestAvailablePartner(order.restaurant.location);
        
        // This is where the concurrent logic of assigning to only one partner would go
        availablePartner.ifPresentOrElse(
            partner -> {
                System.out.println("Assigning order to partner: " + partner.name);
                order.assignPartner(partner);
            },
            () -> {
                System.out.println("No delivery partner available right now. Order is waiting.");
                // Logic to retry or handle this failure
            }
        );
    }
}

// Main class to demonstrate the flow
public class FoodDeliverySystem {
    public static void main(String[] args) {
        // Setup
        Customer customer = new Customer();
        customer.name = "Ankit";
        
        Restaurant restaurant = new Restaurant();
        restaurant.name = "Pizza House";
        restaurant.location = new Location(); // Set some coordinates

        DeliveryPartner p1 = new DeliveryPartner();
        p1.name = "Raju";
        p1.status = PartnerStatus.AVAILABLE;

        DeliveryPartner p2 = new DeliveryPartner();
        p2.name = "Suresh";
        p2.status = PartnerStatus.ON_DELIVERY; // Suresh is busy
        
        DeliveryPartnerService partnerService = new DeliveryPartnerService();
        partnerService.addPartner(p1);
        partnerService.addPartner(p2);

        // 1. Customer places an order
        Order order = new Order("ORD123", customer, restaurant);
        System.out.println("New order placed: " + order.orderId);

        // 2. Restaurant accepts and prepares the order
        order.setStatus(OrderStatus.ACCEPTED);
        order.setStatus(OrderStatus.PREPARING);

        // 3. Restaurant marks the order as ready, triggering partner assignment
        OrderFulfillmentService fulfillmentService = new OrderFulfillmentService(partnerService);
        fulfillmentService.markOrderReady(order);
        
        System.out.println("Final order details: Order assigned to " + order.assignedPartner.name);
        System.out.println("Raju's status is now: " + p1.status);
    }
}
```

---