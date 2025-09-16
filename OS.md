## 📘 **OPERATING SYSTEM – COMPLETE PLACEMENT PREPARATION ROADMAP**

---


## **1. BASICS OF OPERATING SYSTEM**

### **Introduction to Operating Systems**

1.  **👨‍🏫 Definition:** Operating System (OS) ek system software hai jo computer **hardware** aur **user** ke beech ek interface ka kaam karta hai. Ye computer ke sabhi resources ko manage karta hai aur applications ko run karne ke liye ek environment provide karta hai.

2.  **🎯 Mukhya Uddeshya (Key Purposes):**

      * **Resource Management:** CPU, memory, disk space, I/O devices ko efficiently manage karna.
      * **Platform for Applications:** User applications (like Chrome, Word, Games) ko run hone ke liye ek base provide karna.
      * **User Interface:** User ko computer se interact karne ka ek zariya dena (Command Line Interface - CLI, ya Graphical User Interface - GUI).

### **Functions of Operating System**

  * **Process Management:** Processes ko create, delete, schedule aur synchronize karna. Ye decide karta hai ki kis process ko kab aur kitna CPU time milega.
  * **Memory Management:** Main memory (RAM) ko manage karna. Processes ko memory allocate aur deallocate karna. Ye track karta hai ki memory ka kaunsa hissa use me hai aur kaunsa free hai.
  * **File Management:** Files aur directories ko manage karna. Storage devices par files ko create, delete, read, write aur secure karna.
  * **Device Management:** Sabhi input/output devices (keyboard, mouse, printer, disk drives) ko manage karna. Unke drivers ke through communication ko handle karna.
  * **Security & Protection:** Unauthorized access ko rokna. Passwords, permissions aur access control ke zariye system ko protect karna.

### **Types of Operating Systems**

| OS Type | Definition | Use Case |
| :--- | :--- | :--- |
| **Batch OS** | Ek jaise jobs ka ek **batch** banakar, unhe ek-ek karke bina user interaction ke execute karta hai. | Payroll systems, Bank statement generation. |
| **Time-Sharing OS** | Har process ko CPU use karne ke liye thoda-thoda time (**quantum**) deta hai, jisse multitasking ka illusion create hota hai. | Modern desktop OS jaise Windows, macOS, Linux. |
| **Distributed OS** | Multiple independent computers ko ek network par connect karke, unhe ek single powerful system ki tarah present karta hai. | High-performance computing, Web servers (Google). |
| **Network OS** | Ek server par chalta hai aur network me jude hue clients ko shared resources (files, printers) provide karta hai. | Office environments me file/printer sharing. |
| **Real-Time OS (RTOS)**| Time-critical systems jahan tasks ko ek **strict deadline** ke andar poora karna zaroori hota hai. | Missile guidance systems, Car airbags, Medical devices. |

### **Kernel in OS**

1.  **👨‍🏫 Definition:** Kernel, OS ka **core component** hai jiska computer ke hardware par poora control hota hai. Ye OS ka sabse pehla program hai jo boot-up ke time memory (RAM) me load hota hai.

2.  **⚙️ Mechanism:** Ye `Kernel Mode` me chalta hai, jiske paas saare hardware resources ka direct access hota hai. User applications `User Mode` me chalti hain, jinke paas limited permissions hoti hain. Jab bhi kisi user application ko hardware ki zaroorat padti hai (e.g., file read karna), to wo **System Call** ke through Kernel se request karti hai.

### **System Calls**

1.  **👨‍🏫 Definition:** System call, user-level programs ke liye OS ki services ko request karne ka ek programmatic way hai. Ye **User Mode** se **Kernel Mode** me switch karne ka entry point hai.

2.  **🎯 Purpose:** Security. User programs ko direct hardware access nahi diya jaata taaki wo system ko corrupt na kar dein. System calls ek controlled aur safe way provide karte hain OS services use karne ka.

3.  **⚙️ How it Works:**

    1.  User program ek function call (e.g., `fopen()`) karta hai jo C library me hai.
    2.  Library function, system call number ko register me set karke ek `TRAP` instruction execute karta hai.
    3.  CPU, **User Mode** se **Kernel Mode** me switch hota hai aur OS ka system call handler execute hota hai.
    4.  Handler, system call number se corresponding service (e.g., file open karna) run karta hai.
    5.  Kaam poora hone par, CPU wapas **User Mode** me switch ho jaata hai aur control user program ko return kar deta hai.

4.  **💻 C++ Example (File I/O jo internally system calls use karta hai):**

    ```cpp
    #include <fstream> // For file operations
    #include <iostream>

    int main() {
        // ofstream object creation internally uses 'open' or 'create' system call
        std::ofstream file("data.txt");

        if (file.is_open()) {
            // '<<' operator internally uses 'write' system call
            file << "Hello from OS Notes!";
            file.close(); // Internally uses 'close' system call
            std::cout << "File written successfully." << std::endl;
        }
        return 0;
    }
    ```

### **System Boot and Initialization**

Ye computer ke **power on** hone se lekar OS ke **fully functional** hone tak ka process hai.

1.  **Power On:** System ko power supply milti hai.
2.  **BIOS/UEFI:** Motherboard par lagi ek chip (firmware) run hoti hai.
3.  **POST (Power-On Self-Test):** BIOS, saare basic hardware components (RAM, CPU, Keyboard) ko check karta hai.
4.  **Bootloader:** BIOS, storage device (HDD/SSD) ke MBR/GPT se **Bootloader** program ko dhundkar RAM me load karta hai.
5.  **Kernel Loading:** Bootloader ka kaam OS **Kernel** ko RAM me load karna aur use control dena hota hai.
6.  **Initialization:** Kernel, device drivers aur `init` process (systemd/init.d) ko start karta hai, jo baaki saari system services ko shuru karta hai.
7.  **Login:** Aakhir me, user ke liye login prompt ya GUI display hota hai.

-----

## **2. PROCESS MANAGEMENT**

### **Process**

1.  **👨‍🏫 Definition:** A **program in execution**. Jab ek executable file (jaise `chrome.exe`) disk se uthkar memory me load hoti hai aur CPU uspar kaam karna shuru karta hai, tab wo ek process kehlati hai.
2.  **🧠 Analogy:** Ek **Recipe book** ek `Program` hai (passive instructions). Jab ek **Chef** us recipe ko follow karke **asli me khana bana raha hai**, to wo ek `Process` hai (active execution).
3.  **Process Components:** Ek process ke memory space me ye sections hote hain: **Stack** (local variables), **Heap** (dynamic memory), **Data** (global variables), aur **Text** (program code).

### **Process States**

Ek process apne lifetime me in 5 states se guzarta hai:

1.  **New:** Process create ho raha hai.
2.  **Ready:** Process memory me loaded hai aur CPU ke allot hone ka wait kar raha hai. (Ready Queue me rehta hai).
3.  **Running:** Instructions CPU par execute ho rahi hain.
4.  **Waiting (or Blocked):** Process kisi event ke poora hone ka wait kar raha hai (jaise I/O operation ya signal). Is state me process CPU use nahi kar sakta, bhale hi CPU free ho.
5.  **Terminated:** Process ne apna execution poora kar liya hai aur uske resources OS dwara reclaim kiye ja rahe hain.

### **Process Control Block (PCB)**

1.  **👨‍🏫 Definition:** Har process se juda ek data structure jisme us process ki saari important information store hoti hai. OS, processes ko unke PCB ke through hi manage karta hai.
2.  **📌 Key Information in PCB:**
      * **Process ID (PID):** Unique identifier for the process.
      * **Process State:** New, Ready, Running, etc.
      * **Program Counter (PC):** Agli instruction ka address jo execute honi hai.
      * **CPU Registers:** Accumulator, base, index registers ki values.
      * **CPU Scheduling Info:** Process priority, pointers to scheduling queues.
      * **Memory Management Info:** Base/limit registers, page tables.
      * **I/O Status Info:** Process ko allocated devices, open files ki list.

### **Context Switching**

1.  **👨‍🏫 Definition:** Ye wo mechanism hai jiske zariye OS, CPU ka control ek process (P1) se lekar doosre process (P2) ko deta hai.
2.  **🎯 Purpose:** Time-sharing OS me multitasking achieve karne ke liye.
3.  **⚙️ Mechanism:**
    1.  Ek interrupt ya system call occur hota hai.
    2.  OS, current running process (P1) ka **context** (CPU registers, Program Counter, etc.) uske **PCB (PCB1)** me **save** karta hai.
    3.  OS, scheduler se agla process (P2) pick karta hai.
    4.  OS, P2 ka context uske **PCB (PCB2)** se **load/restore** karta hai.
    5.  P2 apna execution resume karta hai.
4.  **⚠️ Mukhya Baat:** Context switching ek **pure overhead** hai, kyunki is dauraan system koi useful kaam nahi kar raha hota.

### **Threads vs. Processes**

Ye ek behad important interview topic hai.

  * **Thread:** Ek process ka execution path. Ek process me multiple threads ho sakte hain, jo ek saath alag-alag kaam karte hain. Inhe **lightweight process** bhi kehte hain.

| Feature | Process | Thread |
| :--- | :--- | :--- |
| **Weight** | **Heavyweight**. Creation me time aur resources zyada lagte hain. | **Lightweight**. Creation fast aur less resource-intensive hai. |
| **Memory** | Har process ka apna **separate memory space** hota hai. | Ek hi process ke saare threads apna **memory space share** karte hain (Code, Data, Heap). Har thread ka apna alag **Stack** aur **Registers** hote hain. |
| **Communication**| Inter-Process Communication (IPC) complex hota hai (e.g., pipes, sockets). | Inter-Thread Communication aasan aur fast hota hai, kyunki wo direct shared memory se data access kar sakte hain. |
| **Isolation** | **Fully isolated.** Ek process ke crash hone se doosre process par asar nahi hota. | **Not isolated.** Ek thread ke crash hone se poora process crash ho sakta hai. |
| **Context Switching** | **Slow** hota hai, kyunki poora memory map change hota hai. | **Fast** hota hai, kyunki memory map same rehta hai, sirf stack aur register pointers change hote hain. |
| **Example** | `Google Chrome` ek process hai. | Chrome me har `Tab` ek alag thread ho sakta hai. |
---

### **What is Scheduling?**

1.  **👨‍🏫 Definition:** Scheduling, multiprogramming OS ka ek fundamental function hai. Ye **process** ko select karne ka kaam hai jise system resources (jaise CPU) allocate kiye jayenge.

2.  **🎯 Purpose:** CPU ko hamesha busy rakhkar **CPU Utilization** ko maximize karna. Ek multiprogramming environment me, jab ek process I/O ke liye wait karta hai, to OS CPU ko usse lekar kisi doosre ready process ko de deta hai. Ye decision **CPU Scheduler** leta hai.

-----

### **Process Scheduler and Dispatcher**

  * **Scheduler (Short-term Scheduler):** Ye **Ready Queue** me se ek process ko select karta hai jise CPU par run karna hai. Ye decision scheduling algorithm ke basis par liya jaata hai. Iska kaam sirf process ko *select* karna hai.

  * **Dispatcher:** Ye wo module hai jo Scheduler dwara select kiye gaye process ko CPU ka control **deta** hai. Iske 3 kaam hote hain:

    1.  Current process se naye process par **Context Switching** karna.
    2.  System ko **User Mode** me switch karna.
    3.  User program ke us location par jump karna jahan se use restart karna hai.

**Dispatcher Latency:** Dispatcher ko ek process ko rokkar doosra start karne me jo time lagta hai, use Dispatcher Latency kehte hain. Ye kam se kam hona chahiye.

-----

### **Types of Scheduling (Preemptive vs Non-preemptive)**

Ye scheduling ka sabse important classification hai.

| Feature | Non-Preemptive Scheduling | Preemptive Scheduling |
| :--- | :--- | :--- |
| **Meaning** | Ek baar process ko CPU mil gaya, to wo use tab tak nahi chhodega jab tak wo ya to **terminate** na ho jaaye ya **I/O wait** ke liye na chala jaaye. | OS, process se CPU ko **zabardasti** (forcibly) wapas le sakta hai aur kisi doosre, zyada important process ko de sakta hai. |
| **Flexibility** | Rigid. Ek high-priority process ko wait karna pad sakta hai agar ek low-priority process pehle se run ho raha hai. | Flexible. Priority aur time quantum ke basis par CPU re-allocate ho sakta hai. |
| **Overhead** | Kam overhead hota hai kyunki baar-baar context switching nahi hoti. | Zyada overhead hota hai kyunki baar-baar context switching ho sakti hai. |
| **Example Algorithms** | FCFS, Non-Preemptive SJF, Non-Preemptive Priority. | SRTF (Preemptive SJF), Round Robin, Preemptive Priority. |

-----

### **Scheduling Criteria (Performance Metrics)**

Scheduling algorithms ko compare karne ke liye in criteria ka use hota hai:

  * **CPU Utilization:** CPU kitne percentage time busy raha. Ise maximize karna goal hai. (e.g., 90%).
  * **Throughput:** Ek unit time me kitne processes **poore** (complete) hue. Ise maximize karna goal hai.
  * **Turnaround Time (TAT):** Process ke system me aane se lekar uske complete hone tak ka total time. Ise minimize karna goal hai.
      * `Turnaround Time = Completion Time - Arrival Time`
  * **Waiting Time (WT):** Ek process ne Ready Queue me total kitna time wait kiya. Ise minimize karna goal hai.
      * `Waiting Time = Turnaround Time - Burst Time`
  * **Response Time:** Request submit hone se lekar pehla response aane tak ka time. Interactive systems ke liye ye important hai.

-----

### **CPU Scheduling Algorithms**

#### **1. FCFS (First Come, First Serve)**

  * **Concept:** Jo process pehle aayega, use CPU pehle milega. Ye ek simple queue (FIFO - First-In, First-Out) ki tarah kaam karta hai.

  * **Mode:** Non-Preemptive.

  * **Advantage:** Bahut simple aur easy to implement hai.

  * **Disadvantage:** Average waiting time kaafi zyada ho sakta hai. Isme **Convoy Effect** ki problem aati hai (agar ek lamba process pehle aa jaaye to saare chhote processes uske peeche phase rehte hain).

  * **Example:**
    | Process | Arrival Time (AT) | Burst Time (BT) |
    | :--- | :--- | :--- |
    | P1 | 0 | 5 |
    | P2 | 1 | 3 |
    | P3 | 2 | 2 |

    **Gantt Chart:**

    ```
    | P1 (5) | P2 (3) | P3 (2) |
    0        5        8        10
    ```

      * **TAT:** P1=5-0=**5**, P2=8-1=**7**, P3=10-2=**8**
      * **WT:** P1=5-5=**0**, P2=7-3=**4**, P3=8-2=**6**
      * **Average WT:** (0+4+6)/3 = **3.33**

#### **2. SJF (Shortest Job First)**

  * **Concept:** Ready Queue me se us process ko select karta hai jiska next CPU burst sabse chhota ho.

  * **Mode:** Dono ho sakta hai:

    1.  **Non-Preemptive SJF:** Jab ek process run ho raha hai, to naya chhota process aane par bhi current process run karta rahega.
    2.  **Preemptive SJF (SRTF - Shortest Remaining Time First):** Agar ek naya process aata hai jiska burst time, current running process ke *bache hue time* se kam hai, to CPU naye process ko de diya jaata hai.

  * **Advantage:** Ye average waiting time ke liye **optimal** (sabse best) algorithm hai.

  * **Disadvantage:** Next CPU burst ko predict karna mushkil hai. Lambe processes ko **starvation** ho sakti hai.

  * **Example (SRTF - Preemptive):**
    | Process | Arrival Time (AT) | Burst Time (BT) |
    | :--- | :--- | :--- |
    | P1 | 0 | 8 |
    | P2 | 1 | 4 |
    | P3 | 2 | 9 |
    | P4 | 3 | 5 |

    **Gantt Chart:**

    ```
    | P1 | P2 (4) | P4 (5) | P1 (7) | P3 (9) |
    0    1        5        10       17       26
    ```

      * At time 1, P2 arrives (BT=4), P1 ka remaining time is 7. P2 is shorter, so P2 preempts P1.
      * **TAT:** P1=17-0=**17**, P2=5-1=**4**, P3=26-2=**24**, P4=10-3=**7**
      * **WT:** P1=17-8=**9**, P2=4-4=**0**, P3=24-9=**15**, P4=7-5=**2**
      * **Average WT:** (9+0+15+2)/4 = **6.5**

#### **3. Round Robin (RR)**

  * **Concept:** Har process ko ek chhota time unit (time quantum/slice) diya jaata hai. Process utne time tak chalta hai. Agar wo poora nahi hota, to use Ready Queue ke end me laga diya jaata hai.

  * **Mode:** Preemptive.

  * **Advantage:** Interactive systems ke liye achha hai kyunki response time kam hota hai. Starvation nahi hoti.

  * **Disadvantage:** Performance **time quantum (TQ)** par depend karti hai.

      * Agar TQ bada hai -\> FCFS jaisa behave karta hai.
      * Agar TQ chhota hai -\> Context switching overhead badh jaata hai.

  * **Example (Time Quantum = 4):**
    | Process | Arrival Time (AT) | Burst Time (BT) |
    | :--- | :--- | :--- |
    | P1 | 0 | 10 |
    | P2 | 0 | 5 |
    | P3 | 0 | 8 |

    **Gantt Chart:**

    ```
    | P1 | P2 | P3 | P1 | P2 | P3 | P1 | P3 |
    0    4    8    12   16   17   21   23
    ```

      * **TAT:** P1=23-0=**23**, P2=17-0=**17**, P3=23-0=**23**
      * **WT:** P1=23-10=**13**, P2=17-5=**12**, P3=23-8=**15**
      * **Average WT:** (13+12+15)/3 = **13.33**

#### **4. Priority Scheduling**

  * **Concept:** Har process ko ek priority assign ki jaati hai. CPU hamesha highest priority waale process ko milta hai.
  * **Mode:** Dono ho sakta hai (Preemptive aur Non-Preemptive).
  * **Advantage:** Important tasks ko jaldi complete kiya ja sakta hai.
  * **Disadvantage:** **Starvation** ya Indefinite Blocking. Low priority waale process ko shayad kabhi CPU na mile.
  * **Solution:** **Aging**. Samay ke saath, wait kar rahe process ki priority dheere-dheere badha di jaati hai.

-----

### **Advanced Scheduling Algorithms**

#### **5. Multilevel Queue Scheduling**

  * **Concept:** Ready Queue ko multiple choti-choti queues me baant diya jaata hai. Jaise:
    1.  **Foreground (Interactive) Queue:** High priority, Round Robin use kar sakti hai.
    2.  **Background (Batch) Queue:** Low priority, FCFS use kar sakti hai.
  * Scheduling pehle queues ke beech hoti hai (e.g., pehle saare foreground processes, fir background).
  * **Disadvantage:** Inflexible. Ek baar process ko queue assign ho gayi, to wo use change nahi kar sakta.

#### **6. Multilevel Feedback Queue Scheduling**

  * **Concept:** Ye Multilevel Queue ka advanced version hai. Isme processes queues ke beech **move** kar sakte hain.
  * **Mechanism:**
      * Agar koi process bahut zyada CPU time le raha hai, to use lower-priority queue me **demote** kar diya jaata hai.
      * Agar koi process I/O-bound hai aur lamba wait kar raha hai, to use higher-priority queue me **promote** kar diya jaata hai.
  * **Advantage:** Zyada flexible aur starvation ko prevent karta hai. Ye sabse complex lekin sabse efficient algorithms me se ek hai.

-----

### **Starvation and Aging**

  * **Starvation:** Ek aisi situation jahan ek process ko indefinitely (anant kaal tak) wait karna padta hai aur use kabhi CPU nahi milta. Ye aam taur par Priority Scheduling me hota hai jab high-priority processes lagatar aate rehte hain.
  * **Aging:** Starvation ka solution. Ye ek technique hai jisme jo process bahut der se wait kar rahe hain, unki **priority samay ke saath badha di jaati hai**. Isse eventually, low-priority process ki priority itni badh jaati hai ki use CPU mil jaata hai.
---
### **3.1 Basics**

#### **Inter-Process Communication (IPC) Methods**

Jab processes ek doosre ke saath data share ya communicate karte hain, to use IPC kehte hain. Iske do mukhya tarike hain:

| Feature | 1. Shared Memory | 2. Message Passing |
| :--- | :--- | :--- |
| **Concept** | Ek memory area banaya jaata hai jo multiple processes ke address space me mapped hota hai. Processes is shared area me read/write karke communicate karte hain. | Processes ek doosre ko **messages** bhejkar communicate karte hain. OS, communication link (mailbox/port) ko manage karta hai. |
| **Speed** | **Fast**. Kyunki communication memory speed par hota hai, OS ka involvement (system calls) kam hota hai. | **Slow**. Kyunki har message send/receive karne ke liye system calls (`send()`, `receive()`) ki zaroorat padti hai, jisme kernel ka involvement hota hai. |
| **Synchronization** | Programmer ki **zimmedari** hoti hai. Agar theek se handle na kiya jaaye to race conditions ho sakti hain. | OS **khud handle** karta hai. Programmer ke liye aasan hota hai. |
| **Implementation** | Processes ke beech setup karna thoda complex ho sakta hai. | Implement karna aasan hai. |
| **Use Case** | Jab speed critical ho aur processes ek hi machine par hon. | Distributed systems (processes alag-alag machines par hon) aur jahan simplicity zaroori ho. |

#### **Race Condition**

1.  **👨‍🏫 Definition:** Race condition ek aisi unwanted situation hai jahan multiple processes ya threads ek shared resource/data ko access aur manipulate karte hain, aur operation ka final outcome is baat par depend karta hai ki kaunsa process kis order me execute hua. Isse result unpredictable aur galat ho jaata hai.

2.  **🧠 Analogy:** Socho ek bank account me ₹10,000 hain. Aap aur aapka dost, dono ek hi time par alag-alag ATM se ₹2,000 nikalne ki koshish karte ho.

      * **Ideal Case:** Balance ₹6,000 ho jaana chahiye.
      * **Race Condition Case:**
        1.  Aapka ATM balance read karta hai: ₹10,000.
        2.  Isse pehle ki aapka ATM balance update kare, aapke dost ka ATM bhi balance read kar leta hai: ₹10,000.
        3.  Aapka ATM ₹2,000 deduct karke balance update karta hai: ₹8,000.
        4.  Aapke dost ka ATM bhi ₹2,000 deduct karke balance update karta hai: ₹8,000.
      * **Final Result:** Account me ₹8,000 bache, jabki bachne ₹6,000 chahiye the. Yahan data inconsistent ho gaya.

3.  **Technical Example (`count++`):**
    `count++` operation assembly level par 3 steps me hota hai:

    1.  `LOAD` register, count (Register me count ki value lao)
    2.  `INCREMENT` register (Register ki value badhao)
    3.  `STORE` count, register (Register ki nayi value wapas count me daalo)

    Agar `count = 5` hai aur do threads (T1, T2) `count++` run karte hain, to galat interleaving ho sakti hai:

      * T1: `LOAD` (Register\_T1 = 5)
      * T2: `LOAD` (Register\_T2 = 5)  \<-- Context Switch
      * T1: `INCREMENT` (Register\_T1 = 6)
      * T2: `INCREMENT` (Register\_T2 = 6)
      * T1: `STORE` (count = 6)
      * T2: `STORE` (count = 6)  \<-- Context Switch
      * **Final Result:** `count` ki value `6` hai, jabki `7` honi chahiye thi.

#### **Critical Section Problem**

1.  **👨‍🏫 Definition:** **Critical Section** ek program ka wo hissa hai jahan shared resources (shared variables, common files) ko access kiya jaata hai.

2.  **The Problem:** Ek aisa mechanism (protocol) design karna jisse ye sunishchit (ensure) ho ki jab ek process apne critical section me hai, to koi doosra process apne critical section me enter na kar sake.

3.  **Solution Structure:** Har process ko apne critical section me enter karne se pehle **permission** leni padti hai.

    ```c++
    do {
        // Code to request entry
        entry_section();

            // <<< CRITICAL SECTION >>>

        // Code to signal exit
        exit_section();

            // <<< REMAINDER SECTION >>>

    } while (true);
    ```

#### **Requirements for a Solution**

Critical Section problem ke kisi bhi solution ko ye 3 conditions poori karni zaroori hain:

1.  **Mutual Exclusion:** Agar ek process P1 apne critical section me hai, to koi doosra process P2 apne critical section me enter nahi kar sakta. Ye sabse zaroori condition hai.
2.  **Progress:** Agar koi bhi process critical section me nahi hai aur kuch processes enter karna chahte hain, to unme se kisi ek ko select karke enter karne se roka nahi jaana chahiye. Selection anant kaal tak delay nahi ho sakta.
3.  **Bounded Waiting:** Jab ek process critical section me enter karne ke liye request karta hai, to ek limit honi chahiye ki uske baad kitne doosre processes enter kar sakte hain. Aisa na ho ki ek process hamesha wait hi karta reh jaaye (starvation na ho).

-----

### **3.2 Classical Synchronization Problems**

Ye standard problems hain jo synchronization concepts ko test karne ke liye use hote hain.

#### **1. Producer-Consumer Problem (Bounded Buffer Problem)**

  * **Problem Scenario:** Do tarah ke processes hain, **Producers** aur **Consumers**, jo ek fixed-size ke buffer (shared memory) ko share karte hain.
      * **Producer:** Data items generate karke buffer me daalta hai.
      * **Consumer:** Buffer se data items nikal kar unhe consume karta hai.
  * **Synchronization Challenge:**
    1.  Producer ko **bhare hue (full) buffer** me item nahi daalna chahiye.
    2.  Consumer ko **khaali (empty) buffer** se item nahi nikalna chahiye.
    3.  Producer aur Consumer ek hi time par buffer ko access na karein (mutual exclusion).
  * **Goal:** In teeno conditions ko handle karne ke liye ek synchronized solution banana. Ye problem aam taur par **Semaphores** ya **Monitors** ka use karke solve ki jaati hai.

#### **2. Readers-Writers Problem**

  * **Problem Scenario:** Ek shared data object (jaise file ya database) hai jise multiple processes access karte hain.
      * **Readers:** Sirf data ko read karte hain.
      * **Writers:** Data ko read aur write dono kar sakte hain.
  * **Synchronization Challenge:**
    1.  Ek saath kitne bhi **Readers** data ko read kar sakte hain (kyunki wo data change nahi karte).
    2.  Ek time par sirf **ek hi Writer** data ko write kar sakta hai.
    3.  Jab koi **Writer** write kar raha ho, tab koi bhi **Reader** read nahi kar sakta.
  * **Goal:** In rules ko follow karte hue access control mechanism banana. Is problem ke do variations hote hain:
      * **Reader's Priority:** Agar writer wait kar raha hai lekin readers aa rahe hain, to readers ko pehle access milega. Isse writer ko starvation ho sakti hai.
      * **Writer's Priority:** Agar writer wait kar raha hai, to naye aane waale readers ko writer ke baad access milega.

#### **3. Dining Philosophers Problem**

  * **Problem Scenario:** Paanch philosopher (processes) ek gol table par baithe hain. Table ke beech me khana hai. Har do philosopher ke beech me ek chopstick (resource) rakhi hai.
      * Ek philosopher ya to **sochta** hai ya **khaata** hai.
      * Khane ke liye, har philosopher ko **do chopsticks** ki zaroorat hoti hai - uske left waali aur right waali.
  * **Synchronization Challenge:** Aisa system design karna jisme philosopher khana kha sakein, lekin **Deadlock** na ho.
      * **Deadlock Scenario:** Agar saare paancho philosopher ek saath apni left waali chopstick utha lein, to ab koi bhi right waali chopstick nahi utha payega kyunki wo kisi aur ki left chopstick hai. Sab hamesha ke liye wait karte rahenge.
  * **Goal:** Ek **deadlock-free** aur **starvation-free** solution banana, jisse har philosopher ko khane ka mauka mile. Ye problem un situations ko represent karti hai jahan multiple processes limited resources ke liye compete karte hain.


---


### **3.3 Solutions to Synchronization**

#### **Software-Based Solutions**

Ye solutions process ke logic me hi implement kiye jaate hain aur inke liye koi special hardware instruction ki zaroorat nahi hoti. In sabhi solutions me **Busy Waiting** (process ek loop me CPU cycles waste karta hai) ek common samasya hai.

##### **1. Peterson’s Algorithm**

  * **Concept:** Ye 2 processes ke liye ek aasan aur popular solution hai. Ye do shared variables ka use karta hai:

      * `int turn;`: Batata hai ki kis process ki critical section me jaane ki baari hai.
      * `boolean flag[2];`: `flag[i] = true` ka matlab hai ki process `i` critical section me enter karne ke liye interested hai.

  * **Mechanism:** Process `i` critical section me tabhi enter kar sakta hai jab ya to process `j` interested na ho (`flag[j] == false`) ya fir `turn` `i` ka ho.

  * **📝 Pseudocode (for Process `i`):**

    ```c++
    // Initialization: flag[0]=false, flag[1]=false, turn can be 0 or 1
    do {
        // Entry Section
        flag[i] = true;     // I am interested
        turn = j;           // Let the other process go first

        // Busy wait until other is not interested OR it's my turn
        while (flag[j] && turn == j);

        // <<< CRITICAL SECTION >>>

        // Exit Section
        flag[i] = false;    // I am no longer interested

        // <<< REMAINDER SECTION >>>
    } while (true);
    ```

##### **2. Dekker’s Algorithm**

  * **Concept:** Ye do processes ke liye pehla provably correct software solution tha. Peterson's Algorithm ki tarah, ye bhi `flag` aur `turn` variables ka use karta hai taaki mutual exclusion ensure ho sake. Ye strict alternation se bachata hai.
  * **📝 Pseudocode (for Process `i`):**
    ```c++
    // Initialization: flag[0]=false, flag[1]=false, turn=0
    do {
        // Entry Section
        flag[i] = true; // I am interested

        while (flag[j]) { // While other is also interested
            if (turn == j) { // If it's other's turn
                flag[i] = false; // I will back off temporarily
                while (turn == j); // Wait for my turn
                flag[i] = true; // Re-assert my interest
            }
        }

        // <<< CRITICAL SECTION >>>

        // Exit Section
        turn = j; // Give turn to the other process
        flag[i] = false; // I am no longer interested

        // <<< REMAINDER SECTION >>>
    } while (true);
    ```

##### **3. Bakery Algorithm**

  * **Concept:** Ye 'n' processes ke liye kaam karta hai. Iska naam bakery me milne waale token system se inspired hai.

  * **Mechanism:**

    1.  Critical section me enter karne se pehle har process ek token number leta hai.
    2.  Jo process sabse chhota number leta hai, wo pehle enter karta hai.
    3.  Agar do processes same number le lein, to unki process ID ke basis par tie-break hota hai (chhoti ID wala pehle jaata hai).

  * **📝 Pseudocode (for Process `i`):**

    ```c++
    // Shared variables:
    // boolean choosing[n] = {false};
    // int number[n] = {0};

    do {
        // Entry Section: Get a token number
        choosing[i] = true;
        number[i] = max(number[0], ..., number[n-1]) + 1;
        choosing[i] = false;

        // Check all other processes
        for (j = 0; j < n; j++) {
            // Wait if process j is choosing its number
            while (choosing[j]);

            // Wait if process j has a smaller number,
            // or same number but a smaller process ID
            while ((number[j] != 0) &&
                   ((number[j], j) < (number[i], i)));
        }

        // <<< CRITICAL SECTION >>>

        // Exit Section
        number[i] = 0; // Reset my number

        // <<< REMAINDER SECTION >>>
    } while (true);
    ```

-----

#### **Hardware-Based Solutions**

Ye solutions special machine instructions ka use karte hain jo **atomically** (uninterruptibly) execute hote hain.

##### **1. Test-and-Set Instruction**

  * **Concept:** Ye instruction ek memory location (lock) ki value ko atomically test karti hai aur use `true` set kar deti hai. Ye uss memory location ki **purani (original)** value return karti hai.
  * **📝 Pseudocode:**
    ```c++
    // Atomic hardware instruction definition
    boolean TestAndSet(boolean *target) {
        boolean old_value = *target;
        *target = true;
        return old_value;
    }

    // Using it for critical section
    // Shared variable: boolean lock = false;
    do {
        // Entry Section (Busy Wait)
        while (TestAndSet(&lock)); // Wait until lock is false

        // <<< CRITICAL SECTION >>>

        // Exit Section
        lock = false;

        // <<< REMAINDER SECTION >>>
    } while (true);
    ```

##### **2. Compare-and-Swap (CAS) Instruction**

  * **Concept:** Ye `TestAndSet` se zyada powerful hai. Ye ek memory location `value` ko ek `expected` value se atomically compare karti hai. Agar dono same hain, to `value` ko `new_value` se update kar deti hai.
  * **📝 Pseudocode:**
    ```c++
    // Atomic hardware instruction definition
    int CompareAndSwap(int *value, int expected, int new_value) {
        int temp = *value;
        if (*value == expected) {
            *value = new_value;
        }
        return temp;
    }

    // Using it for critical section (lock=0 means free, 1 means busy)
    // Shared variable: int lock = 0;
    do {
        // Entry Section (Busy Wait)
        // Keep trying to set lock from 0 to 1
        while (CompareAndSwap(&lock, 0, 1) != 0);

        // <<< CRITICAL SECTION >>>

        // Exit Section
        lock = 0;

        // <<< REMAINDER SECTION >>>
    } while (true);
    ```

-----

#### **Semaphores**

  * **Concept:** Semaphore ek integer variable hai jo busy waiting ki problem ko solve karta hai. Ise sirf do atomic operations ke through access kiya ja sakta hai: `wait()` aur `signal()`.

  * **Mechanism:** Jab ek process `wait()` call karta hai aur resource available nahi hota, to OS use **block/sleep** kar deta hai (waiting queue me daal deta hai). Jab doosra process `signal()` call karke resource free karta hai, to OS waiting queue se ek process ko **wakeup** karke ready queue me daal deta hai.

  * **Types:**

    1.  **Counting Semaphore:** Iski value koi bhi non-negative integer ho sakti hai. Ye un resources ko count karne ke kaam aata hai jinke multiple instances hote hain (e.g., ek system me 5 printer hain).
    2.  **Binary Semaphore:** Iski value sirf **0** ya **1** ho sakti hai. Ise **Mutex** bhi kehte hain aur ye mutual exclusion ke liye use hota hai.

  * **📝 Pseudocode:**

    ```c++
    // Wait Operation (also called P operation)
    wait(Semaphore S) {
        S.value--;
        if (S.value < 0) {
            // add this process to S.list (waiting queue)
            block();
        }
    }

    // Signal Operation (also called V operation)
    signal(Semaphore S) {
        S.value++;
        if (S.value <= 0) {
            // remove a process P from S.list
            wakeup(P);
        }
    }

    // Using a binary semaphore for critical section
    // Semaphore mutex = 1; (Initialized to 1)
    do {
        wait(mutex);
        // <<< CRITICAL SECTION >>>
        signal(mutex);
        // <<< REMAINDER SECTION >>>
    } while (true);
    ```

-----

#### **Mutex vs. Semaphore**

Ye ek behad common interview question hai.

| Feature | Mutex (Mutual Exclusion) | Semaphore |
| :--- | :--- | :--- |
| **Main Purpose** | Locking mechanism. Sirf ek thread ko critical section me allow karna. | Signaling mechanism. Resource availability ka signal dena. |
| **Ownership** | **Owned.** Jo thread mutex ko lock karta hai, sirf wahi use unlock kar sakta hai. | **Not Owned.** Ek thread `wait()` kar sakta hai aur doosra thread `signal()` kar sakta hai. |
| **Type** | Hamesha **Binary** hota hai (locked/unlocked). | **Counting** ya **Binary** ho sakta hai. |
| **Operation** | Thread, resource acquire karke use **lock** karta hai aur release karne par **unlock** karta hai. | Thread, semaphore par `wait()` karta hai aur resource release hone par `signal()` karta hai. |
| **Analogy** | Ek **Toilet ki Key**. Jiske paas key hai (lock hai), wahi use kar sakta hai aur wahi key wapas rakhega (unlock karega). | Ek **Hall me 5 free chairs**. `wait()` ka matlab hai ek chair lena. `signal()` ka matlab hai ek chair khaali karna. Koi bhi chair khaali kar sakta hai. |

-----

#### **Monitors**

  * **Concept:** Monitor ek high-level synchronization tool hai jo programming language dwara support kiya jaata hai (e.g., Java `synchronized` keyword). Ye ek **class** jaisa hota hai jiske andar shared data aur uspar kaam karne waale methods hote hain.
  * **Mechanism:** Monitor ye guarantee karta hai ki ek time par **sirf ek hi thread** uske andar ke kisi method ko execute kar sakta hai. Isse mutual exclusion automatically achieve ho jaata hai.
  * **Condition Variables:** Monitor ke andar threads ko wait aur signal karne ke liye condition variables ka use hota hai.
      * `c.wait()`: Current thread ko suspend kar deta hai.
      * `c.signal()`: Wait kar rahe threads me se kisi ek ko resume karta hai.

-----

#### **Priority Inversion and Priority Inheritance**

  * **Priority Inversion (The Problem):** ☢️

      * **Definition:** Ye ek aisi problem hai jahan ek **high-priority task (H)**, ek **low-priority task (L)** ke kaaran ruka rehta hai, kyunki ek **medium-priority task (M)**, L ko preempt kar leta hai. Isse H ka kaam ruk jaata hai.
      * **Scenario:**
        1.  Low-priority task **L** ek shared resource (e.g., mutex lock) acquire karta hai.
        2.  High-priority task **H** ko run karna hai, lekin use wahi resource chahiye jo L ke paas hai, to H block ho jaata hai.
        3.  Ab ek Medium-priority task **M** aata hai. Kyunki M ki priority L se zyada hai, wo L ko preempt kar leta hai aur run hone lagta hai.
      * **Result:** H, L ka wait kar raha hai, aur L, M ke kaaran chal nahi paa raha. Effectively, ek medium priority task ne high priority task ko block kar diya.

  * **Priority Inheritance (The Solution):** ✅

      * **Definition:** Ye Priority Inversion ko solve karne ka ek protocol hai.
      * **Mechanism:** Jab ek high-priority task (H) kisi aise resource ke liye wait karta hai jo ek low-priority task (L) ne hold kar rakha hai, to L ki priority ko **temporarily H ki priority tak badha diya jaata hai**.
      * **Result:** Ab L ki priority M se zyada ho jaati hai, isliye M use preempt nahi kar pata. L apna kaam jaldi poora karke resource release kar deta hai, jiske baad H use acquire kar leta hai aur L apni original priority par wapas aa jaata hai.

---
### **4.1 Deadlock Basics**

#### **Introduction to Deadlocks**

1.  **👨‍🏫 Definition:** Deadlock ek aisi situation hai jahan do ya do se zyada processes anant kaal (indefinitely) ke liye block ho jaate hain. Har process ek aise resource ka intezaar kar raha hota hai jo kisi doosre waiting process ke paas hold kiya hua hai.
2.  **🧠 Analogy:** Ek **traffic jam** jahan chaar raaston ke intersection par chaar gaadiyan aamne-saamne aa gayi hain. Har gaadi (process) aage badhne ke liye saamne waali jagah (resource) ka intezaar kar rahi hai, jo doosri gaadi ne hold kar rakhi hai. Jab tak koi gaadi peeche nahi hatti (resource release nahi karti), koi bhi aage nahi badh sakta.

#### **Necessary Conditions for Deadlock**

Deadlock hone ke liye, ye **chaaron conditions** ek saath poori honi zaroori hain. Inhe **Coffman Conditions** bhi kehte hain.

1.  **Mutual Exclusion:** Kam se kam ek resource aisa hona chahiye jo non-sharable ho, yaani ek time par sirf ek hi process use kar sakta hai (e.g., Printer).
2.  **Hold and Wait:** Ek process kam se kam ek resource ko **hold** kiye hue ho aur doosre resources ke liye **wait** kar raha ho jo kisi aur process ke paas hain.
3.  **No Preemption:** Resource ko process se zabardasti (forcibly) nahi cheena ja sakta. Process apna kaam poora karne ke baad hi resource ko voluntarily (apni marzi se) release karega.
4.  **Circular Wait:** Processes ka ek set {P0, P1, ..., Pn} is tarah se wait kar raha ho ki P0 us resource ka wait kar raha hai jo P1 ke paas hai, P1 us resource ka wait kar raha hai jo P2 ke paas hai, ..., aur Pn us resource ka wait kar raha hai jo P0 ke paas hai.

#### **Resource Allocation Graph (RAG)**

  * **Concept:** Ye ek directed graph hai jo processes aur resources ke beech allocation aur requests ko visually represent karta hai. Isse deadlock ko detect karna aasan hota hai.

  * **Components:**

      * **Vertices:** Do tarah ke hote hain:
          * Processes (Circles - `P`)
          * Resources (Squares - `R`). Square ke andar dots resource ke instances ko represent karte hain.
      * **Edges:** Do tarah ke hote hain:
          * **Request Edge:** `P → R` (Process P, resource R ko request kar raha hai).
          * **Assignment Edge:** `R → P` (Resource R ka ek instance, process P ko allocated hai).

  * **Deadlock Detection using RAG:**

      * Agar graph me **koi cycle nahi hai**, to system me **deadlock nahi hai**.
      * Agar graph me **cycle hai**:
          * Aur har resource ka **sirf ek instance** hai, to system me **pakka deadlock hai**.
          * Aur resources ke **multiple instances** hain, to system me **deadlock ho bhi sakta hai aur nahi bhi**.

#### **Starvation vs. Deadlock vs. Livelock**

| Feature | Deadlock | Starvation | Livelock |
| :--- | :--- | :--- | :--- |
| **State** | Processes **Blocked** state me hote hain. | Process **Ready** state me hota hai, lekin use kabhi CPU nahi milta. | Processes **Running** state me hote hain, lekin koi useful kaam nahi kar paate. |
| **Progress** | Koi progress nahi hota. | Koi progress nahi hota. | Koi progress nahi hota. |
| **Reason**| Circular wait for resources. | Scheduler (e.g., low priority) ya resource manager continuously process ko ignore karta hai. | Processes ek doosre ko respond karte rehte hain, lekin aage badhne ki bajaye wahi actions repeat karte hain. |
| **Analogy**| Chaar-raaste ka traffic jam. | Ek line me khada bhola aadmi jise doosre log baar-baar kaat kar aage nikal jaate hain. | Corridor me do log jo ek-doosre ko raasta dene ke liye ek hi direction me baar-baar move karte hain. |

-----

### **4.2 Handling Deadlocks**

Deadlocks ko handle karne ke liye chaar approaches hain:

#### **1. Deadlock Prevention**

  * **Concept:** System ko is tarah design karna ki deadlock ki chaaron necessary conditions me se kam se kam ek kabhi poori na ho. Ye ek bahut hi strict approach hai.
  * **Methods:**
      * **Break Mutual Exclusion:** Resources ko sharable bana do. (Har resource ke liye possible nahi hai, e.g., printer).
      * **Break Hold and Wait:** Process ko start hone se pehle hi saare zaroori resources allocate kar do. Ya, jab process naya resource request kare, to pehle apne paas ke saare resources release kar de. (Resource utilization kam ho jaata hai).
      * **Break No Preemption:** Agar ek process kisi resource ko request karta hai jo available nahi hai, to uske paas jo pehle se resources hain, unhe preempt (cheen) kar liya jaaye.
      * **Break Circular Wait:** Sabhi resource types ko ek numerical order de do. Har process ko resources hamesha **increasing order** me hi request karne ke liye force karo. (e.g., agar R1\<R2\<R3, to R3 request karne ke baad R1 request nahi kar sakte).

#### **2. Deadlock Avoidance**

  * **Concept:** Is approach me, system har resource request ko analyze karta hai. Agar request ko grant karne se system **unsafe state** (jahan deadlock ho sakta hai) me jaa sakta hai, to request ko delay kar diya jaata hai. Iske liye system ko pehle se pata hona chahiye ki har process ko maximum kitne resources ki zaroorat padegi.

  * **Safe State:** Ek state safe tab kehlati hai jab processes ka ek aisa sequence (`<P1, P2, ... Pn>`) exist karta ho jisme har process `Pi` apne zaroori resources (jo abhi available hain + jo usse pehle ke processes release karenge) lekar apna kaam poora kar sake.

  * **Banker’s Algorithm**

      * Ye sabse famous deadlock avoidance algorithm hai.
      * **Data Structures:**
          * `Allocation`: Har process ko currently kitne resources allocated hain.
          * `Max`: Har process ko maximum kitne resources ki zaroorat pad sakti hai.
          * `Available`: Har resource ke kitne instances abhi free hain.
          * `Need`: Har process ko aur kitne resources ki zaroorat hai. (`Need = Max - Allocation`).
      * **Safety Algorithm (Checks if system is in a safe state):**
        1.  `Work = Available` aur `Finish[i] = false` for all `i`.
        2.  Ek aisa process `Pi` dhundo jiske liye `Finish[i] == false` aur `Need[i] <= Work`. Agar aisa koi process nahi milta, to step 4 par jao.
        3.  `Work = Work + Allocation[i]`, `Finish[i] = true`, aur step 2 par wapas jao.
        4.  Agar sabhi processes ke liye `Finish[i] == true` hai, to system **safe state** me hai.

#### **3. Deadlock Detection**

  * **Concept:** Is approach me system me deadlock hone diya jaata hai. System ek **detection algorithm** ko samay-samay par chalakar check karta hai ki deadlock hua hai ya nahi.
  * **Mechanism:** Detection algorithm, Banker's Algorithm ke safety algorithm jaisa hi hota hai. Ye check karta hai ki current `Allocation` aur `Available` resources ke saath kya koi safe sequence possible hai. Agar nahi, to matlab deadlock hai.

#### **4. Deadlock Recovery**

  * **Concept:** Jab deadlock detect ho jaata hai, to system ko usse recover karna hota hai.
  * **Methods:**
    1.  **Process Termination:**
          * **Abort all deadlocked processes:** Sabse aasan lekin sabse drastic. Bahut saara computation waste ho jaata hai.
          * **Abort one process at a time:** Ek-ek karke process ko tab tak terminate karo jab tak deadlock cycle toot na jaaye. Victim process ko chunna ek challenge hai.
    2.  **Resource Preemption:**
          * Kisi process se resource ko zabardasti cheen kar doosre process ko de do.
          * **Challenges:**
              * **Victim Selection:** Kis process se resource cheena jaaye?
              * **Rollback:** Victim process ko ek safe state me wapas kaise laya jaaye?
              * **Starvation:** Ho sakta hai hamesha ek hi process victim banta rahe aur kabhi apna kaam poora na kar paaye.

#### **Program for Deadlock-Free Condition**

Deadlock se bachne ka ek aam tarika hai **Resource Ordering** (Circular Wait ko break karna).

  * **Deadlock Prone Code:** Do threads, do mutex (m1, m2).

    ```cpp
    // Thread 1
    lock(m1);
    lock(m2);
    // ... Critical Section ...
    unlock(m2);
    unlock(m1);

    // Thread 2
    lock(m2);
    lock(m1); // <-- Problem yahan hai
    // ... Critical Section ...
    unlock(m1);
    unlock(m2);
    ```

      * Agar Thread 1 `m1` lock karta hai aur Thread 2 `m2` lock karta hai, to dono ek doosre ka wait karte rahenge -\> Deadlock.

  * **Deadlock-Free Code (Using Lock Ordering):** Hamesha ek fixed order me locks acquire karo.

    ```cpp
    // Thread 1
    lock(m1);
    lock(m2);
    // ... Critical Section ...
    unlock(m2);
    unlock(m1);

    // Thread 2
    lock(m1); // <-- Order theek kiya
    lock(m2);
    // ... Critical Section ...
    unlock(m2);
    unlock(m1);
    ```

      * Ab kyunki dono threads pehle `m1` ko lock karne ki koshish karenge, jo bhi pehle lock karega wo aage badhega, doosra wait karega. Circular wait ki condition kabhi nahi banegi.

---


### **5. Threads & Multithreading**

#### **What is a Thread?**
1.  **👨‍🏫 Definition:** Thread, jise **lightweight process** bhi kehte hain, CPU utilization ki basic unit hai. Ek process ke andar multiple threads ho sakte hain, jo ek saath alag-alag tasks perform karte hain.

2.  **Components:** Ek thread ke paas apni private (khud ki) aur shared (doosre threads ke saath baanti hui) cheezein hoti hain:
    * **Private to each Thread:**
        * Thread ID
        * Program Counter (PC)
        * Register Set
        * Stack
    * **Shared among all Threads of a Process:**
        * Code Section (Text)
        * Data Section (Global variables)
        * Heap (Dynamic Memory)
        * Open Files, Signals

3.  **🧠 Analogy:** Ek **Restaurant** ek `Process` hai. Us restaurant me kaam karne waale alag-alag **Chefs** `Threads` hain. Sabhi chefs ek hi kitchen (Code, Data, Heap) share karte hain, lekin har chef apni alag recipe (Program Counter) par kaam kar raha hai aur apne private tools (Stack, Registers) use kar raha hai.

#### **User-Level vs. Kernel-Level Threads**
Ye ek behad important interview topic hai.

| Feature | User-Level Threads (ULTs) | Kernel-Level Threads (KLTs) |
| :--- | :--- | :--- |
| **Management** | User-space me ek **thread library** (e.g., POSIX Pthreads, Java Threads) ke dwara manage hote hain. Kernel ko inke baare me nahi pata hota. | Operating System (Kernel) dwara directly manage hote hain. |
| **Creation Speed**| **Fast**. Inhe banane ke liye system call ki zaroorat nahi hoti. | **Slow**. Inhe create karne ke liye system call lagti hai, jo ek overhead hai. |
| **Blocking Issue** | **Major Drawback:** Agar ek user-level thread koi blocking system call (e.g., I/O) karta hai, to poora **process block** ho jaata hai. | **No Issue:** Agar ek kernel-level thread block hota hai, to kernel usi process ke doosre thread ko schedule kar sakta hai. |
| **Multiprocessing**| Multiple cores par ek saath nahi chal sakte, kyunki kernel poore process ko ek single thread of control maanta hai. | Multiple cores par parallel me chal sakte hain. |
| **Example**| Green Threads in early Java. | Threads in Windows, Linux, macOS. |

#### **Multithreading Models**
Ye models User-Level Threads (ULTs) aur Kernel-Level Threads (KLTs) ke beech ke relationship ko define karte hain.

1.  **Many-to-One Model**
    * **Mapping:** Kai saare User-Level threads ko ek single Kernel-Level thread par map kiya jaata hai.
    * **Pros:** Thread management fast hota hai kyunki sab kuch user-space me hota hai.
    * **Cons:**
        * Ek blocking system call poore process ko block kar deti hai.
        * True parallelism possible nahi hai kyunki ek time par sirf ek hi thread kernel me ja sakta hai.
    * 

2.  **One-to-One Model**
    * **Mapping:** Har User-Level thread ko ek dedicated Kernel-Level thread se map kiya jaata hai.
    * **Pros:**
        * True parallelism achieve hota hai.
        * Ek thread ke block hone se doosre threads par asar nahi padta.
    * **Cons:** Har ULT ke liye ek KLT banana padta hai, jisse system par overhead badh jaata hai.
    * **Used In:** Windows, Linux.
    * 

3.  **Many-to-Many Model**
    * **Mapping:** Kai saare User-Level threads ko usse kam ya barabar (smaller or equal) number of Kernel-Level threads par multiplex kiya jaata hai.
    * **Pros:** Dono models ke best features ko combine karta hai. Efficient bhi hai aur true parallelism bhi allow karta hai.
    * **Cons:** Implement karna kaafi complex hai.
    * 

#### **Process-Based vs. Thread-Based Multitasking**

| Feature | Process-Based Multitasking | Thread-Based Multitasking |
| :--- | :--- | :--- |
| **Concept**| OS, alag-alag **processes** (e.g., Chrome, VS Code) ke beech switch karta hai. | OS, ek hi process ke andar alag-alag **threads** (e.g., Chrome ke tabs) ke beech switch karta hai. |
| **Weight**| Heavyweight | Lightweight |
| **Context Switch** | **Slow** aur resource-intensive. | **Fast** aur less resource-intensive. |
| **Resource Sharing**| Processes ke beech memory shared nahi hoti. IPC mechanisms use karne padte hain. | Threads aapas me memory aur resources (code, data) by default share karte hain. |

#### **Benefits of Multithreading**
1.  **Responsiveness:** Agar ek application ka ek thread block ya lamba operation kar raha hai, to doosre threads chalte rehte hain, jisse application responsive rehti hai (UI hang nahi hota).
2.  **Resource Sharing:** Threads ek hi process ki memory aur resources share karte hain, jisse code likhna aasan hota hai.
3.  **Economy:** Processes ke muqable threads ko create karna aur unke beech context-switch karna sasta (kam resource-consuming) aur fast hota hai.
4.  **Scalability:** Multithreaded applications, multiprocessor architectures ka poora faayda utha sakti hain, jahan har thread alag-alag core par parallel me chal sakta hai.

#### **Remote Procedure Call (RPC)**
* **Definition:** RPC ek mechanism hai jisse ek program, network par maujood kisi doosre computer par chal rahe program ka ek function (procedure) aise call kar sakta hai jaise wo local function ho.
* **Mechanism:**
    1.  **Client:** Local machine par ek function call karta hai. Ye call asal me **Client Stub** ko jaati hai.
    2.  **Client Stub:** Function ke parameters ko pack (marshal) karke network par **Server Stub** ko bhejta hai.
    3.  **Server Stub:** Network se message receive karke parameters ko unpack (unmarshal) karta hai.
    4.  **Server:** Server Stub, server machine par actual function ko call karta hai.
    5.  Result, reverse path se client ko wapas bhej diya jaata hai.

---

### **6. Memory Management**

#### **6.1 Basics**

* **Introduction to Memory:** Main Memory (RAM) ek volatile (power off hone par data erase) storage hai. Ye ek large array of bytes jaisa hai, jahan har byte ka ek unique address hota hai. CPU kisi bhi program ko execute karne ke liye pehle use Hard Disk se Main Memory me laata hai.

* **Memory Units:**
    * **Bit:** Smallest unit (0 or 1).
    * **Byte:** 8 Bits.
    * **Kilobyte (KB):** 1024 Bytes.
    * **Megabyte (MB):** 1024 KB.
    * **Gigabyte (GB):** 1024 MB.
    * **Terabyte (TB):** 1024 GB.

* **Logical vs. Physical Address**
    * **Logical Address (Virtual Address):** Ye wo address hai jo **CPU generate karta hai**. Har process ka apna alag logical address space hota hai, jo 0 se shuru hota hai.
    * **Physical Address:** Ye wo address hai jo **Main Memory (RAM)** me actual location ko point karta hai.
    * **Memory Management Unit (MMU):** Ye ek hardware device hai jo run-time par **Logical Address ko Physical Address me translate (map) karti hai**. Aam taur par ye `Physical Address = Logical Address + Base Register` formula ka use karti hai.



* **Memory Management Techniques:**
    * **Contiguous Allocation:** Process ko memory me ek single continuous block allot kiya jaata hai.
    * **Non-Contiguous Allocation:** Process ko memory ke alag-alag hisso (non-contiguous blocks) me store kiya jaata hai. Iske types hain: **Paging** aur **Segmentation**.

#### **6.2 Contiguous Memory Allocation**

Isme free memory partitions (holes) me se process ke liye jagah dhundhi jaati hai.

* **First Fit, Best Fit, Worst Fit, Next Fit Algorithms**
    | Algorithm | Strategy | Pro | Con |
    | :--- | :--- | :--- | :--- |
    | **First Fit** | Shuru se scan karo, jo **pehla** hole process ko fit kar de, use allocate kar do. | Sabse **fast** hai. | Zaroori nahi ki best allocation ho. |
    | **Best Fit** | Poori list scan karo aur wo **sabse chhota** hole dhundo jo process ko fit kar de. | Memory waste kam hota hai, bahut chhota leftover hole banta hai. | **Slow** hai, kyunki poori list search karni padti hai. |
    | **Worst Fit** | Poori list scan karo aur **sabse bada** hole allocate kar do. | Leftover hole bada hota hai, jo kisi doosre process ke kaam aa sakta hai. | **Slow** hai; memory ka fragmentation jaldi hota hai. |
    | **Next Fit** | First Fit jaisa hi hai, lekin search wahan se shuru karta hai jahan pichli baar allocation **chodi** thi. | First Fit se thoda better performance, memory ke end me bade holes bache rehte hain. | First Fit jaisi hi problems hain. |

* **Internal and External Fragmentation**
    * **External Fragmentation:** Total free memory to available hai, lekin wo **non-contiguous** (alag-alag टुकड़ों me bikhri hui) hai, isliye kisi process ko allocate nahi ki jaa sakti. Ye **First Fit, Best Fit** jaise algorithms me hoti hai.
    * **Internal Fragmentation:** Jab process ko uski zaroorat se **bada memory block** allocate kar diya jaata hai. Allocated block ke andar ka unused space waste ho jaata hai. Ye fixed-size partitioning me hota hai.

* **Buddy System**
    * **Concept:** Ye ek memory allocation technique hai jo fragmentation ko kam karne ki koshish karti hai.
    * **Mechanism:**
        1.  Memory ko **2 ki power (power-of-2)** me aane waale size ke blocks me manage kiya jaata hai (e.g., 64KB, 128KB, 256KB).
        2.  Jab `n` size ke process ke liye request aati hai, to use `2^k` (jahan `2^k >= n`) ke block me allocate kiya jaata hai.
        3.  Agar us size ka block nahi hai, to usse bade block ko do hisso (**buddies**) me recursively toda jaata hai jab tak zaroori size ka block na mil jaaye.
        4.  Jab ek block free hota hai, to system check karta hai ki kya uska "buddy" (jisse wo bana tha) bhi free hai. Agar haan, to dono ko **merge karke** wapas ek bada block bana diya jaata hai.

---


### **6.3 Non-Contiguous Memory Allocation**
External fragmentation ki samasya ko solve karne ke liye, processes ko memory me alag-alag jagah par rakha jaata hai.

#### **Paging**
1.  **Concept:** Ye ek memory management scheme hai jo **external fragmentation** ko poori tarah se khatam kar deti hai.
    * **Logical Memory** (process) ko fixed-size ke blocks me toda jaata hai, jinhe **Pages** kehte hain.
    * **Physical Memory** (RAM) ko bhi same size ke blocks me toda jaata hai, jinhe **Frames** kehte hain.
2.  **Mechanism:** Jab ek process ko execute karna hota hai, uske pages ko RAM ke kisi bhi available frames me load kar diya jaata hai. Wo frames contiguous hon, ye zaroori nahi hai.
    * Logical Address ko CPU do hisso me baant'ta hai: **Page Number (p)** aur **Page Offset (d)**.
    * **Page Number (p):** Ye **Page Table** me ek index ka kaam karta hai.
    * **Page Table:** Har process ka apna ek page table hota hai. Ye page number ko frame number se map karta hai.
    * **Physical Address:** `(Frame Number * Frame Size) + Offset`.

    

3.  **Page Table Entries (PTE):** Page table ke har entry me frame number ke alawa kuch extra bits bhi hoti hain:
    * **Present/Absent Bit (Valid/Invalid Bit):** Batata hai ki page, memory me hai (1) ya nahi (0).
    * **Protection Bits:** Page par konse operations allowed hain (Read, Write, Execute).
    * **Dirty/Modified Bit:** Batata hai ki page me load hone ke baad koi change hua hai ya nahi.
    * **Referenced Bit:** Batata hai ki page haal hi me access hua hai ya nahi. (Page replacement algorithms me use hota hai).

#### **Segmentation**
1.  **Concept:** Ye memory management scheme, user ke view of memory ko support karti hai. Isme logical address space ko variable-size ke blocks me baanta jaata hai, jinhe **Segments** kehte hain. Har segment ek logical unit ko represent karta hai, jaise:
    * Main Program (Code Segment)
    * Global variables (Data Segment)
    * Stack (Stack Segment)
2.  **Mechanism:**
    * Logical Address ek pair hota hai: **<segment-number, offset>**.
    * **Segment Table:** Har segment ke liye isme do entries hoti hain:
        * **Base:** Segment ka starting physical address.
        * **Limit:** Segment ki length.
    * Jab bhi koi logical address generate hota hai, to check kiya jaata hai ki `offset < limit`. Agar haan, to Physical Address = `Base + offset`.

3.  **Paging vs. Segmentation:**

| Feature | Paging | Segmentation |
| :--- | :--- | :--- |
| **Block Size**| Fixed-size (Pages) | Variable-size (Segments) |
| **User View** | User ko nahi dikhta, OS manage karta hai. | User-friendly, program ke logical parts se match karta hai. |
| **Fragmentation**| **Internal Fragmentation** hota hai, External nahi. | **External Fragmentation** hota hai, Internal nahi. |
| **Data Structure**| Page Table | Segment Table |
| **Speed**| Fast, kyunki address translation simple hai. | Slow, kyunki offset ko limit se compare karna padta hai. |

---

### **6.4 Advanced Memory Concepts**

#### **Virtual Memory**
1.  **Concept:** Virtual Memory ek aisi technique hai jo programmer ko ek bahut bade logical memory space ka **illusion** deti hai, bhale hi physical RAM utni badi na ho. Ye program ke sirf zaroori hisso ko hi main memory me rakhti hai.
2.  **Implementation:** Ise aam taur par **Demand Paging** ke zariye implement kiya jaata hai.
3.  **Benefits:**
    * **Larger Programs:** Aap RAM se bade programs chala sakte hain.
    * **Higher Multiprogramming:** RAM me zyada programs ek saath fit ho sakte hain.
    * **Faster Loading:** Program ka sirf zaroori hissa load hota hai, isliye program jaldi start hota hai.

#### **Demand Paging**
* **Concept:** Ye Virtual Memory ko implement karne ka tarika hai jisme ek page ko main memory me tab tak nahi laaya jaata jab tak uski **zaroorat na pade**. Isse "lazy swapper" bhi kehte hain.
* **Mechanism:** Jab CPU ek aise page ko access karne ki koshish karta hai jo memory me nahi hai (jiska Present/Absent bit '0' hai), to ek **Page Fault** generate hota hai.

#### **Page Fault Handling**
Ye ek behad important interview question hai. Jab Page Fault hota hai, to OS ye steps follow karta hai:
1.  CPU ek address access karta hai, MMU dekhta hai ki page table me is page ke liye entry **invalid** hai.
2.  MMU, CPU ko ek **trap** (internal interrupt) bhejta hai. Control, OS ke paas chala jaata hai.
3.  OS, Page Fault Handler ko run karta hai.
4.  OS check karta hai ki address valid hai ya nahi.
5.  OS, disk se zaroori page ko physical memory ke ek **free frame** me load karta hai.
6.  Agar koi frame free nahi hai, to OS ek **page replacement algorithm** chala kar ek victim page chunta hai aur use swap out karta hai.
7.  Page ke memory me aane ke baad, OS **page table ko update** karta hai (frame number daalta hai aur valid bit ko '1' karta hai).
8.  OS us instruction ko **restart** karta hai jisne fault generate kiya tha.



#### **Swap Space**
* **Concept:** Ye Hard Disk ka ek reserved area hai jo RAM ke extension ki tarah kaam karta hai. Jab RAM bhar jaati hai, to inactive pages ko RAM se utha kar Swap Space me daal diya jaata hai (swapped out), aur zaroori pages ko Swap Space se utha kar RAM me laaya jaata hai (swapped in).

---

### **6.5 Page Replacement & Thrashing**

Jab page fault hota hai aur koi frame free nahi hota, to OS ko ek victim page chunna padta hai jise memory se hataya ja sake.

#### **Page Replacement Algorithms**
* **1. FIFO (First-In, First-Out):**
    * **Strategy:** Jo page sabse pehle memory me aaya tha, use hi sabse pehle replace karo.
    * **Pro:** Implement karna sabse aasan hai.
    * **Con:** Performance achhi nahi hoti. Isme **Belady's Anomaly** ho sakti hai.

* **2. Optimal Page Replacement (OPT):**
    * **Strategy:** Us page ko replace karo jiski zaroorat **future me sabse der me padegi**.
    * **Pro:** Sabse kam page faults deta hai. Ye best possible algorithm hai.
    * **Con:** Ise implement karna **impossible** hai, kyunki OS ko future nahi pata hota. Ise sirf doosre algorithms ko compare karne ke liye as a benchmark use karte hain.

* **3. LRU (Least Recently Used):**
    * **Strategy:** Us page ko replace karo jo **sabse lambe samay se use nahi hua hai**.
    * **Pro:** Optimal ka achha approximation hai aur performance kaafi achhi hoti hai.
    * **Con:** Implement karna mushkil aur costly hai. Hardware support (counters ya stack) ki zaroorat padti hai.

* **4. Second Chance / Clock Algorithm:**
    * **Strategy:** Ye LRU ka ek efficient approximation hai. Ye FIFO ki tarah kaam karta hai, lekin ek page ko replace karne se pehle uska **Reference Bit** check karta hai.
    * **Mechanism:**
        1.  Agar Reference Bit `1` hai, to page ko ek "second chance" milta hai. Bit ko `0` kiya jaata hai aur pointer aage badh jaata hai.
        2.  Agar Reference Bit `0` hai, to us page ko replace kar diya jaata hai.

#### **Belady’s Anomaly**
Ye ek ajeeb phenomenon hai jahan **frames ka number badhaane par page faults kam hone ki jagah badh jaate hain**. Ye anomly sirf **FIFO** jaise kuch algorithms me hi dekhi jaati hai. LRU aur Optimal isse immune hain.

#### **Thrashing**
* **Definition:** Thrashing ek aisi situation hai jahan ek process execute hone se zyada time **paging** (pages ko disk se lane aur le jaane) me waste kar raha hota hai. Isse system ka performance achanak se gir jaata hai aur CPU utilization bahut kam ho jaati hai.
* **Cause:** Aisa tab hota hai jab ek process ke paas itne kam frames hote hain ki wo apne **working set** (currently active pages) ko bhi memory me nahi rakh paata.
* **Working Set Model:** Ek process ka working set un pages ka collection hai jinhe wo haal hi me (ek time window `Δ` me) access kar raha hai. Thrashing se bachne ke liye, ek process ka poora working set memory me hona chahiye.

#### **Techniques to Handle Thrashing**
1.  **Working Set Model:** OS har process ke working set ko monitor kare aur use utne frames de jitne zaroori hain.
2.  **Page-Fault Frequency (PFF):** OS har process ke page fault rate ko monitor kare.
    * Agar rate bahut **high** hai -> Process ko aur frames do.
    * Agar rate bahut **low** hai -> Process se frames wapas le lo.

---
### **6.6 Kernel & System-Level Memory**

#### **Kernel Memory Allocation**
User processes ki tarah, Kernel ko bhi apne data structures (jaise PCB, page tables, file objects) ke liye memory ki zaroorat padti hai. Kernel memory allocation user allocation se alag hota hai kyunki kernel ke liye memory contiguous honi chahiye aur fragmentation afford nahi kar sakte.
* **Buddy System:** Kernel, memory ko power-of-2 size ke chunks me manage karne ke liye Buddy System ka use karta hai.
* **Slab Allocator:** Ye Buddy System ke upar kaam karta hai. Kernel me jo objects baar-baar create aur destroy hote hain (e.g., `task_struct`), unke liye ye **caches (slabs)** bana leta hai. Isse baar-baar memory allocate/deallocate aur object initialize karne ka overhead bach jaata hai.

#### **Memory Interleaving**
Ye ek hardware technique hai jisse memory access speed badhti hai. Isme RAM ko multiple **memory banks** me divide kar diya jaata hai. Isse CPU ek saath alag-alag banks se data access kar sakta hai, jisse memory bandwidth badh jaati hai.

#### **OS-Level Virtualization**
* **Hypervisors (Virtual Machine Monitors - VMM):**
    * **Type 1 (Bare-Metal):** Ye seedhe hardware par install hota hai. Guest OS iske upar chalte hain. (e.g., VMware ESXi, Xen). Ye zyada efficient hote hain.
    * **Type 2 (Hosted):** Ye ek normal OS (Host OS) ke upar as an application chalta hai. (e.g., VMware Workstation, VirtualBox).
* **Containers:**
    * Ye ek lightweight virtualization technique hai. Containers **host OS ka kernel share karte hain**, lekin unka apna isolated user-space (libraries, file system) hota hai.
    * **Containers vs. Virtual Machines (VMs):**
        * VMs poore hardware ko virtualize karte hain aur har VM me ek poora Guest OS hota hai. Ye heavyweight hote hain.
        * Containers sirf OS ko virtualize karte hain. Ye lightweight, fast, aur kam resource use karte hain. **Docker** iska sabse popular example hai.
---


### **7.1 File Systems**

#### **File Concepts and Attributes**

1.  **File Concept:** 📁
    * Ek **file**, related information ka collection hai jise user ek naam deta hai aur secondary storage (like Hard Disk) par store karta hai.
    * Operating System ke liye, file aam taur par **bytes ka sequence** hoti hai. OS file ke content se matlab nahi rakhta, bas use manage karta hai.

2.  **File Attributes:**
    * Ye file ke baare me metadata (information) hai jo directory me store hota hai.
    * **Name:** File ka human-readable naam (e.g., `resume.pdf`).
    * **Identifier:** File system ke andar file ka unique number (e.g., inode number in Linux).
    * **Type:** File kis prakaar ki hai (e.g., executable, text, image).
    * **Location:** Device par file kahan store hai, iska pointer.
    * **Size:** File ka current size (bytes, KB, MB me).
    * **Protection:** Access control information - kaun read, write, ya execute kar sakta hai (e.g., `rwx` permissions in Linux).
    * **Timestamps:** File kab banayi gayi (**Creation**), kab aakhri baar badli gayi (**Modification**), aur kab aakhri baar access ki gayi (**Last Access**).

---
#### **File Access Methods**
Ye batata hai ki file ke andar ke data ko kaise access kiya ja sakta hai.

1.  **Sequential Access:**
    * **Concept:** File ke data ko **order me** (ek ke baad ek) access kiya jaata hai. Ye sabse simple aur common method hai.
    * **Mechanism:** Ek read/write head hota hai jo file me current position maintain karta hai. Har read/write operation ke baad, ye head aage badh jaata hai.
    * **Analogy:** 🧠 Ek **cassette tape** par gaane sunna, jahan agle gaane par jaane ke liye aapko beech ke saare gaane forward karne padte hain.

2.  **Direct Access (or Relative Access):**
    * **Concept:** File ke kisi bhi block ko **directly** (bina sequence follow kiye) access kiya ja sakta hai.
    * **Mechanism:** File ko fixed-size logical records me dekha jaata hai. Aap seedhe record number bata kar uss location par jump kar sakte hain.
    * **Analogy:** 🧠 Ek **CD/DVD** par gaane sunna, jahan aap track number select karke seedhe uss gaane par jump kar sakte hain. Databases me ye method bahut use hota hai.

3.  **Indexed Sequential Access:**
    * **Concept:** Ye sequential aur direct access ka combination hai. File ke records ko sequentially store kiya jaata hai, lekin ek **index** bhi maintain kiya jaata hai jisse specific records tak jaldi pahuncha ja sake.
    * **Analogy:** 🧠 Ek **kitaab ka index** (piche ke pages me). Aap index me topic dhundh kar seedhe uss page number par jaate hain (Direct Access), aur fir uss page par line by line padhte hain (Sequential Access).

---
#### **File Allocation Methods**
Ye batata hai ki disk par files ke liye blocks (space) kaise allocate kiye jaate hain.

1.  **Contiguous Allocation:**
    * **Concept:** Har file ko disk par **lagatar (contiguous)** blocks ka ek set allocate kiya jaata hai. Directory entry me file ka starting block address aur length store hoti hai.
    * **Pros:** 👍
        * Sequential aur Direct access dono ke liye **fast** hai.
    * **Cons:** 👎
        * **External Fragmentation** ki samasya hoti hai.
        * File ka size badhana (grow karna) mushkil hai.
    * 

2.  **Linked Allocation:**
    * **Concept:** Har file disk blocks ki ek **linked list** hoti hai. Blocks disk par kahin bhi ho sakte hain. Har block me data ke saath agle block ka pointer hota hai. Directory entry me sirf starting block ka pointer hota hai.
    * **Pros:** 👍
        * **External Fragmentation nahi** hota.
        * File ko grow karna aasan hai.
    * **Cons:** 👎
        * **Direct Access support nahi** karta (kisi block tak pahunchne ke liye poori list traverse karni padti hai).
        * Pointers ke liye har block me space waste hota hai.
        * Agar ek bhi pointer corrupt ho gaya, to file ka data lost ho sakta hai.
    * 

3.  **Indexed Allocation:**
    * **Concept:** File ke saare block pointers ko ek special block me ikattha kar diya jaata hai, jise **Index Block** kehte hain. Directory entry me is index block ka address hota hai.
    * **Pros:** 👍
        * **Direct Access support** karta hai.
        * **External Fragmentation nahi** hota.
    * **Cons:** 👎
        * Agar file choti hai to poora index block waste ho sakta hai.
        * Badi files ke liye ek index block kaafi nahi hota, jiske liye multilevel indexing jaisi schemes use karni padti hain.
    * 

---
#### **Directory Structure**
Directory files ko logically organize karne ka ek tarika hai.

1.  **Single-Level Directory:**
    * **Concept:** Sabhi files ek hi directory me hoti hain.
    * **Pros:** Simple to implement.
    * **Cons:** File naming problem (do files ka same naam nahi ho sakta). Bahut saari files hone par manage karna mushkil.

2.  **Two-Level Directory:**
    * **Concept:** Ek **Master File Directory (MFD)** hoti hai, jiske andar har user ki apni alag **User File Directory (UFD)** hoti hai.
    * **Pros:** Alag-alag users apni files ka naam same rakh sakte hain.
    * **Cons:** Users ke beech file sharing aasan nahi hai.

3.  **Hierarchical (Tree-Structured) Directory:**
    * **Concept:** Ye sabse common structure hai. Isme directories ke andar sub-directories ho sakti hain, jo ek tree jaisa structure banati hain.
    * **Pros:** Bahut flexible hai. Users files ko logical groups (folders) me organize kar sakte hain.
    * **Analogy:** 🧠 Aapke computer me folders ke andar folders ka system.

---
#### **Pathnames**
* **Definition:** Pathname ek string hai jo hierarchical directory structure me kisi file ya directory ki unique location batata hai.
* **Absolute Pathname:** Wo path jo hamesha **root directory** se shuru hota hai. Ye location par depend nahi karta.
    * *Example (Linux):* `/home/user/project/file.txt`
    * *Example (Windows):* `C:\Users\Admin\Documents\file.doc`
* **Relative Pathname:** Wo path jo **current working directory** se shuru hota hai.
    * *Example:* Agar aap `/home/user/` me hain, to `project/file.txt` ek relative path hai.

---
#### **Free Space Management Techniques**
Ye batata hai ki OS disk par khali blocks (free space) ka hisaab kaise rakhta hai.

1.  **Bit Vector (or Bitmap):**
    * **Concept:** Disk ke har block ke liye ek bit use hoti hai. Agar bit `1` hai, to block free hai; agar `0` hai, to block allocated hai (ya iska ulta).
    * **Pros:** Simple hai aur contiguous free blocks dhundhna aasan hai.
    * **Cons:** Badi disk ke liye bitmap ka size bhi bada ho jaata hai.

2.  **Linked List:**
    * **Concept:** Saare free blocks ko ek linked list me jod diya jaata hai. OS sirf list ke head (pehla free block) ka pointer rakhta hai.
    * **Pros:** Bitmap ke liye extra space ki zaroorat nahi padti.
    * **Cons:** Free blocks ko traverse karna slow ho sakta hai.

3.  **Grouping:**
    * **Concept:** Linked List ka ek modification. Yahan pehla free block, agle `n-1` free blocks ke addresses store karta hai. Un `n-1` blocks me se aakhri block, agle `n` free blocks ke addresses store karta hai, and so on.

4.  **Counting:**
    * **Concept:** Isme OS contiguous free blocks ke group ka address aur group ka size store karta hai. For example, ek entry ho sakti hai: `(Start Block: 250, Count: 15)`, jiska matlab hai ki block number 250 se lekar agle 15 blocks free hain.

---


### **7.2 Unix File System**

#### **Structure**

Unix-like operating systems (jaise Linux) ek hierarchical (tree-like) file system structure ka use karte hain, jo **root (`/`)** directory se shuru hota hai. Kuch standard directories hain:

  * **`/` (Root):** Hierarchy ka starting point.
  * **`/bin`:** Essential user command binaries (e.g., `ls`, `cp`, `cat`).
  * **`/etc`:** System configuration files (e.g., password files, network settings).
  * **`/home`:** Users ki personal directories (e.g., `/home/username`).
  * **`/dev`:** Device files (e.g., `/dev/sda` for hard disk, `/dev/null`).
  * **`/usr`:** User programs, libraries, documentation.
  * **`/var`:** Variable files - jinka size badhta rehta hai (e.g., logs, spools).
  * **`/tmp`:** Temporary files.

#### **Inode (Index Node)**

  * **Concept:** Inode Unix file system ka fundamental concept hai. Ye ek **data structure** hai jo file ya directory ke baare me saari metadata store karta hai, siwaye uske naam aur actual data ke.

  * **Har Inode me kya hota hai:**

      * **Mode:** File ka type (regular, directory, etc.) aur permissions (read, write, execute).
      * **Owner ID & Group ID:** File ke owner aur group ki IDs.
      * **Size:** File ka size bytes me.
      * **Timestamps:** Creation, last modification, last access time.
      * **Link Count:** Kitni hard links is inode ko point kar rahi hain.
      * **Pointers to Data Blocks:** File ka actual data jin disk blocks me hai, unke addresses. Ye aam taur par 15 pointers hote hain:
          * **12 Direct Pointers:** Shuru ke 12 data blocks ko direct point karte hain.
          * **1 Single Indirect Pointer:** Ek aise block ko point karta hai jisme data block ke addresses hote hain.
          * **1 Double Indirect Pointer:** Ek aise block ko point karta hai jo single indirect pointers ko point karta hai.
          * **1 Triple Indirect Pointer:** Bahut badi files ke liye.

  * **⚠️ Important Interview Point:** Inode me file ka **naam nahi** hota hai. File ka naam **directory entry** me store hota hai, jo filename ko inode number se map karti hai.

#### **Shell Scripting for Directory Management**

  * **Concept:** Shell script, commands ki ek file hoti hai jise command-line interpreter (shell) execute karta hai. Isse repetitive tasks ko automate kiya ja sakta hai.
  * **Basic Commands:**
      * `mkdir directory_name`: Nayi directory banana.
      * `rmdir directory_name`: Khali directory ko delete karna.
      * `ls`: Directory ke contents list karna.
      * `cd directory_name`: Directory change karna.
      * `pwd`: Current working directory ka path print karna.
  * **Example Script (Directory check and create):**
    ```sh
    #!/bin/bash

    # Script to create a directory if it does not exist
    DIR_NAME="my_project"

    # Check if directory exists
    if [ -d "$DIR_NAME" ]; then
      echo "Directory '$DIR_NAME' already exists."
    else
      echo "Directory '$DIR_NAME' does not exist. Creating it now."
      mkdir "$DIR_NAME"
      echo "Directory created successfully."
    fi
    ```

-----

### **7.3 Disk Management**

#### **Secondary Storage (HDD, SSD Basics)**

  * **HDD (Hard Disk Drive):**
      * Ye ek **mechanical** storage device hai.
      * Isme **spinning platters** (disks) hote hain jinpar data magnetically store hota hai.
      * Ek **read/write head** arm par laga hota hai jo move karke data ko access karta hai.
      * Speed, **RPM** (Revolutions Per Minute) me maapi jaati hai.
      * SSD se sasta hota hai, lekin slow aur physical shock se damage ho sakta hai.
  * **SSD (Solid-State Drive):**
      * Isme **koi moving parts nahi** hote.
      * Ye **flash memory (NAND)** ka use karta hai data store karne ke liye.
      * HDD se bahut **fast**, zyada durable, aur kam power consume karta hai.
      * Aam taur par HDD se mehenga hota hai.

#### **Disk Structure (HDD)**

  * **Platter:** Ek circular disk jiske dono taraf data store hota hai.
  * **Track:** Har platter par concentric circles, jinhe tracks kehte hain.
  * **Sector:** Har track chote-chote arcs me divided hota hai, jinhe sectors kehte hain (ye smallest physical storage unit hai).
  * **Cylinder:** Sabhi platters par same track number ka collection ek cylinder banata hai. Read/write head ek saath poore cylinder ko access kar sakta hai bina arm move kiye.

#### **Disk Scheduling Algorithms**

Inka mukhya uddeshya (goal) **Seek Time** (head ko correct track tak le jaane ka time) ko kam karna hai.

**Example Scenario:**

  * Request Queue: `98, 183, 37, 122, 14, 124, 65, 67`
  * Current Head Position: `53`
  * Total Tracks: 0-199

| Algorithm | Strategy | Pros | Cons | Total Head Movement |
| :--- | :--- | :--- | :--- | :--- |
| **FCFS** | First Come, First Serve. Jis order me requests aayi hain, usi me service karo. | Fair, simple. | Inefficient, seek time zyada hota hai. | `(98-53)+(183-98)+(183-37)+...` = **640** |
| **SSTF** | Shortest Seek Time First. Current head position se sabse nazdeek request ko pehle service karo. | Throughput FCFS se behtar hota hai. | **Starvation** ho sakti hai (door ki requests wait karti reh sakti hain). | `53->65->67->37->14->98->...` = **236** |
| **SCAN** | "Elevator Algorithm". Head ek direction me end tak jaata hai, raaste me aane waali sabhi requests ko service karta hai, fir direction reverse karta hai. | Starvation nahi hoti. | Disk ke middle tracks ko zyada service milti hai. | `53->37->14->0->65->67->...` = **208** |
| **C-SCAN**| Circular SCAN. SCAN jaisa hi, lekin ek end tak jaane ke baad, head wapas starting end par jump karta hai bina return me koi request service kiye. | Uniform waiting time provide karta hai. | SCAN se zyada seek movements ho sakte hain. | `53->65->67->...->199->0->14->...` = **382** (Approx) |
| **LOOK** | SCAN ka optimized version. Head sirf last request tak jaata hai, na ki disk ke end tak. | SCAN se zyada efficient. | SCAN jaise hi. | `53->37->14->65->67->...` = **208** (varies) |
| **C-LOOK**| C-SCAN ka optimized version. C-SCAN ki tarah hi, lekin head sirf last request tak jump karta hai. | C-SCAN se zyada efficient. | C-SCAN jaise hi. | `53->65->67->...->183->14->...` = **322** (Approx) |

#### **Program for SSTF Scheduling (C++)**

```cpp
#include <iostream>
#include <vector>
#include <cmath>
#include <algorithm>

using namespace std;

void sstf_scheduling(vector<int>& requests, int head) {
    int seek_count = 0;
    int current_head = head;
    int n = requests.size();

    cout << "Seek Sequence is:" << endl;
    cout << current_head;

    for (int i = 0; i < n; i++) {
        int min_seek = INT_MAX;
        int next_req_index = -1;

        // Find the request with the shortest seek time from the current head
        for (int j = 0; j < requests.size(); j++) {
            if (abs(current_head - requests[j]) < min_seek) {
                min_seek = abs(current_head - requests[j]);
                next_req_index = j;
            }
        }

        int next_req = requests[next_req_index];
        seek_count += min_seek;
        current_head = next_req;

        cout << " -> " << current_head;

        // Remove the serviced request from the vector
        requests.erase(requests.begin() + next_req_index);
    }

    cout << "\nTotal number of seek operations = " << seek_count << endl;
}

int main() {
    vector<int> requests = {98, 183, 37, 122, 14, 124, 65, 67};
    int head = 53;

    sstf_scheduling(requests, head);

    return 0;
}
```

#### **Disk Formatting and Boot Block**

  * **Disk Formatting:** Ye ek naye disk ko use ke liye taiyaar karne ka process hai. OS isme do cheezein karta hai:
    1.  **Low-level formatting (Physical formatting):** Disk ko sectors me divide karna aur har sector me data structures (like header, data area, trailer) create karna.
    2.  **High-level formatting (Logical formatting):** Disk par **file system** create karna (e.g., creating boot block, free space management structures, root directory).
  * **Boot Block:** Har bootable disk ka pehla sector (sector 0). Isme ek chota program, **bootstrap loader**, hota hai. Jab computer start hota hai, to firmware (BIOS/UEFI) is bootstrap loader ko run karta hai, jiska kaam memory me poore Operating System ko load karna hota hai.

-----

### **7.4 Spooling and Buffering**

#### **What is Spooling?**

  * **Full Form:** **S**imultaneous **P**eripheral **O**perations **O**n-**L**ine.
  * **Concept:** Spooling ek aisi process hai jahan I/O-bound jobs ka data ek buffer me (aam taur par **disk** par) store kiya jaata hai. Jab device (jaise printer) free hota hai, to wo is buffer se data le leta hai.
  * **Purpose:** Ye CPU aur slow I/O devices ko decouple (alag) kar deta hai. CPU, data ko spool (disk) par bhej kar doosre tasks par kaam karne lagta hai, use slow printer ka wait nahi karna padta.
  * **Analogy:** 🧠 **Printer Queue.** Jab aap 10 documents print karte hain, to wo sabhi ek saath printer ko nahi jaate. Wo disk par ek queue me lag jaate hain (spooling), aur printer apni speed se ek-ek karke unhe print karta hai.

#### **Difference Between Spooling and Buffering**

| Feature | Spooling | Buffering |
| :--- | :--- | :--- |
| **Storage Area**| Disk par ek bada area. | Main Memory (RAM) me ek chhota area. |
| **Data Handling**| Poore **job** ya **multiple jobs** ka data store karta hai. | Data ke **chote hisse (chunks)** ko store karta hai. |
| **Purpose** | CPU aur I/O device ke beech speed mismatch ko handle karna, aur multiple processes ko device access allow karna. | Do devices (e.g., NIC aur CPU) ya device aur application ke beech speed mismatch ko handle karna. |
| **Operation** | Multiple processes ke liye kaam karta hai. Ye ek **OS feature** hai. | Ek single I/O operation ke liye kaam karta hai. Ye ek **technique** hai. |
| **Example**| Printer spooling, Email queue. | Data streaming from network, Disk I/O buffer. |

---


---
### **Operating System Fundamentals**

#### **OS and its Main Functions**

**Q: What is an Operating System (OS)? (Operating System kya hai?)**
A: Operating System (OS) ek **system software** hai jo computer **hardware** aur **user** ke beech ek **interface** (pul ya bridge) ka kaam karta hai. Ye computer ke saare resources, jaise CPU, memory, aur storage, ko manage karta hai. Windows, macOS, Linux, Android, aur iOS iske popular examples hain.

---
**Q: Why is the operating system important? / What's the main purpose of an OS? (Operating system zaroori kyun hai? Iska mukhya kaam kya hai?)**
A: Operating system ke do mukhya kaam hain:
1.  **Provide an Environment (Platform Dena):** OS, user applications (jaise Chrome, games, MS Word) ko run hone ke liye ek platform aur zaroori services provide karta hai. Bina OS ke aap koi bhi application nahi chala sakte.
2.  **Act as a Resource Manager (Resource Manager ki Tarah Kaam Karna):** OS computer ke saare hardware resources (CPU, RAM, hard disk, printer) ko efficiently manage karta hai. Ye decide karta hai ki kis program ko kab aur kitna resource milega.

---
**Q: What are the basic functions of the operating system? (Operating system ke basic functions kya hain?)**
A: Operating System ke kuch zaroori functions niche diye gaye hain:
* **Process Management:** Programs ko kab CPU milega, unhe create karna, aur delete karna.
* **Memory Management:** Main memory (RAM) ko alag-alag programs ke beech baantna aur track karna.
* **File Management:** Files aur directories ko banana, delete karna, aur storage par manage karna.
* **Device Management:** Sabhi input/output devices (keyboard, mouse, printer) ko control karna.
* **Security:** Unauthorized access se system ko bachana.
* **User Interface:** User ko computer se interact karne ka ek tarika dena (GUI ya CLI).

---
**Q: List some of the standard services provided by an OS. (OS dwara di jaane waali kuch standard services batao.)**
A: OS, programs aur users ko ye services provide karta hai:
* **Program Execution:** Program ko memory me load karke use run karna.
* **I/O Operations:** Keyboard se input lena ya screen par output dikhana jaisi operations ko handle karna.
* **File-System Manipulation:** Files ko read karna, write karna, create karna, aur delete karna.
* **Communication:** Processes ke beech information share karne ke liye Inter-Process Communication (IPC) provide karna.
* **Error Detection:** Hardware ya software me aane waali errors ko detect karke unhe handle karna.
* **Resource Allocation:** Multiple users ya jobs ke beech resources ko aavantit (allocate) karna.

---
**Q: What problem do we face in a computer system without an OS? (Bina OS ke computer system me kya samasya aayegi?)**
A: Bina Operating System ke, computer sirf ek **khaali metal ka box** (dumb machine) hai. User ko har chote se chote kaam ke liye direct hardware se interact karna padega, jaise:
* Screen par kuch print karne ke liye display controller ko program karna padega.
* Keyboard se input lene ke liye keyboard controller ke liye code likhna padega.
* Ek saath multiple programs nahi chalaye ja sakte.
* Koi standard user interface nahi hoga.
Kul milakar, computer ko use karna behad mushkil aur impractical ho jaayega.

---
#### **Process, Program, and Thread**

**Q: What is the difference between a program and a process? (Program aur process me kya antar hai?)**
A: Ye ek bahut important concept hai:
* **Program:** Ek **passive** entity hai. Ye disk par rakhi hui ek executable file hai jisme set of instructions hote hain (jaise `chrome.exe`).
* **Process:** Ek **active** entity hai. Jab aap kisi program par double-click karke use run karte hain, to wo memory me load ho jaata hai aur ek process ban jaata hai. Aasaan shabdon me, a **"program in execution"** is a process.

**Analogy:** 🧠 Ek **Recipe book** ek `Program` hai. Jab ek **Chef** us recipe ko padhkar **khana bana raha hai**, to wo ek `Process` hai.

---
**Q: What is a Thread? (Thread kya hai?)**
A: Thread ek **lightweight process** hai. Ye CPU execution ki sabse choti unit hai. Ek single process ke andar multiple threads ho sakte hain, jo ek saath alag-alag kaam karte hain aur process ke resources (jaise memory aur files) ko aapas me share karte hain.

**Example:** Google Chrome browser ek process hai. Uska har tab (jo alag-alag website khol sakta hai) ek alag thread ho sakta hai.

---
**Q: What is the difference between a process and a thread? (Process aur thread me kya antar hai?)**
A: Ye ek bahut hi common interview question hai.

| Feature | Process (Heavyweight) | Thread (Lightweight) |
| :--- | :--- | :--- |
| **Memory** | Har process ka apna **alag (separate)** memory space hota hai. | Ek hi process ke saare threads **shared** memory space use karte hain. |
| **Creation** | Process ko create karna **slow** aur resource-intensive hota hai. | Thread ko create karna **fast** aur kam resource-consuming hota hai. |
| **Communication**| Processes ke beech communication (IPC) **complex** hota hai. | Threads ke beech communication **aasan** hota hai (shared variables ke through). |
| **Isolation** | Processes **isolated** hote hain. Ek process ke crash hone se doosre par asar nahi hota. | Threads **isolated nahi** hote. Ek thread ke crash hone se poora process crash ho sakta hai. |

---
**Q: What are the benefits of multithreaded programming? (Multithreaded programming ke kya fayde hain?)**
A: Multithreading ke kai fayde hain:
1.  **Responsiveness (Jaldi Jawab Dena):** Agar ek application ka ek thread kisi lambe kaam me busy hai (jaise file download karna), to doosre threads chalte rehte hain. Isse application ka User Interface (UI) "freeze" ya "hang" nahi hota.
2.  **Resource Sharing (Sansadhan Share Karna):** Threads by default ek hi memory space share karte hain, isliye unke beech data share karna aasan aur efficient hota hai.
3.  **Economy (Kifayati):** Naye processes banane ke muqable naye threads banana bahut sasta (kam resource wala) aur tez hai. Threads ke beech context switching bhi fast hoti hai.
4.  **Scalability (Vistar Kshamata):** Multithreaded applications **multicore processors** ka poora faayda utha sakti hain. Alag-alag threads alag-alag CPU cores par parallel me chal sakte hain, jisse performance badh jaati hai.


---

### **Types of OS**

**Q: What are the different types of operating systems? (Operating systems ke alag-alag prakaar kya hain?)**
A: Operating systems ke kai prakaar hain, jinme se kuch pramukh hain:
* **Batch Operating System**
* **Time-Sharing (or Multitasking) Operating System**
* **Distributed Operating System**
* **Network Operating System**
* **Real-Time Operating System (RTOS)**

---
**Q: What is a Batch Operating System? (Batch Operating System kya hai?)**
A: Batch OS me, ek jaise jobs (kaam) ka ek group ya **"batch"** banaya jaata hai. Computer in jobs ko ek ke baad ek, bina kisi user interaction ke, automatically execute karta hai. Iska mukhya uddeshya (goal) computer ke free time ko kam karna hota hai.
**Analogy:** 🧠 Ye ek dhobi ki tarah hai jo saare kapde (jobs) ikatthe karke ek batch banata hai aur fir washing machine me ek saath dhota hai.

---
**Q: What is a time-sharing system? (Time-sharing system kya hai?)**
A: Time-sharing system ek aisi OS technique hai jisme CPU ka time multiple users ya tasks ke beech share kiya jaata hai. Har task ko run hone ke liye thoda sa time (**time quantum**) milta hai. CPU itni tezi se tasks ke beech **switch** karta hai ki har user ko lagta hai ki poora computer sirf unhi ka kaam kar raha hai. Ise **multitasking OS** bhi kehte hain.

---
**Q: Describe the objective of multi-programming. (Multi-programming ka uddeshya batao.)**
A: Multi-programming ka mukhya uddeshya **CPU utilization ko maximize karna** hai. Isme main memory me ek se zyada programs rakhe jaate hain. Jab bhi ek program ko I/O operation ke liye wait karna padta hai, to CPU idle (khaali) baithne ki jagah doosre program par kaam karna shuru kar deta hai. Isse CPU hamesha busy rehta hai.

---
**Q: What is the difference between multitasking and multiprocessing OS? (Multitasking aur multiprocessing OS me kya antar hai?)**
A: Ye dono alag concepts hain:
* **Multitasking:** Isme **ek hi CPU** par multiple tasks ke beech tezi se switch kiya jaata hai, jisse ek saath kaam hone ka **illusion** create hota hai. Ye **concurrent execution** hai.
* **Multiprocessing:** Isme system me **ek se zyada CPUs (ya cores)** hote hain. Ye multiple tasks ko सचमुच (truly) ek hi samay par alag-alag CPUs par chala sakta hai. Ye **parallel execution** hai.

---
**Q: What do you mean by RTOS (Real-Time Operating System)? (RTOS se aap kya samajhte hain?)**
A: RTOS (Real-Time Operating System) ek aisa OS hai jo time-critical applications ke liye design kiya gaya hai. Isme har task ko ek **strict time deadline** ke andar poora karna zaroori hota hai. Iske do prakaar hain:
1.  **Hard RTOS:** Yahan deadline miss karna bilkul bhi acceptable nahi hai. (e.g., Car Airbag System, Missile Guidance).
2.  **Soft RTOS:** Yahan kabhi-kabhi deadline miss ho jaaye to system fail nahi hota, bas quality thodi kam ho jaati hai. (e.g., Video Streaming).

---
**Q: What are the benefits of a multiprocessor system? (Multiprocessor system ke kya fayde hain?)**
A: Multiprocessor system (jisme ek se zyada CPU hote hain) ke kai fayde hain:
* **Increased Throughput:** Ek hi samay me zyada kaam ho sakta hai, jisse system ki performance badh jaati hai.
* **Economy of Scale:** Multiple single-processor systems khareedne se sasta padta hai kyunki ye power supply aur peripherals share karte hain.
* **Increased Reliability (Fault Tolerance):** Agar ek processor fail ho jaata hai, to doosre processors kaam jaari rakhte hain. Isse system poori tarah se band nahi hota.

---
**Q: What is SMP (Symmetric Multiprocessing)? (SMP kya hai?)**
A: SMP (Symmetric Multiprocessing) ek aisi multiprocessor architecture hai jisme sabhi **processors barabar (peers)** hote hain. Koi bhi processor master ya slave nahi hota. Har processor OS ke saare kaam kar sakta hai aur sabhi processors ek hi main memory ko share karte hain. Aajkal ke zyadaatar multi-core systems (jaise Intel Core i5/i7) SMP architecture par hi based hain.

---
**Q: What do you mean by asymmetric clustering? (Asymmetric clustering se aap kya samajhte hain?)**
A: **Clustering** me, multiple computers ko ek saath joda jaata hai taaki wo ek single system ki tarah kaam karein. **Asymmetric clustering** me, ek server **hot-standby mode** me rehta hai jabki doosra server (main server) applications ko run karta hai. Hot-standby server sirf main server ko monitor karta hai aur jaise hi main server fail hota hai, hot-standby server uski jagah le leta hai.

---
### **Kernel and User Modes**

**Q: What is a kernel? (Kernel kya hai?)**
A: Kernel, Operating System ka **core (dil ya dimaag)** hota hai. Ye wo pehla program hai jo computer ke boot hone par memory me load hota hai. Kernel ka hardware ke upar poora control hota hai aur ye applications aur hardware ke beech communication ko manage karta hai.

---
**Q: What are the main functions of a Kernel? (Kernel ke mukhya kaam kya hain?)**
A: Kernel ke mukhya kaam hain:
* **Process Management:** Processes ko schedule karna.
* **Memory Management:** Memory ko allocate aur deallocate karna.
* **Device Management:** Hardware devices ko control karna.
* **System Call Control:** User programs se aane waali requests ko handle karna.

---
**Q: What is the difference between the Operating System and the kernel? (Operating System aur kernel me kya antar hai?)**
A: * **Kernel** OS ka sabse zaroori aur central part hai.
* **Operating System** ek poora package hai jisme **kernel** ke saath-saath doosre system programs jaise **shell (command interpreter), GUI, file manager, system utilities** bhi shaamil hote hain.

**Analogy:** 🚗 Agar Operating System ek poori **car** hai, to **engine** uska `Kernel` hai.

---
**Q: What are the different types of Kernel? (Kernel ke alag-alag prakaar kya hain?)**
A: Kernel ke mukhya prakaar hain:
1.  **Monolithic Kernel:** Sabhi OS services ek hi address space me chalti hain. (e.g., Linux).
2.  **Microkernel:** Sirf basic services (jaise IPC, memory management) kernel me chalti hain, baaki sab user-space me.
3.  **Hybrid Kernel:** Monolithic aur Microkernel ka combination. (e.g., Windows, macOS).
4.  **Exokernel:** Hardware resources ko securely multiplex karta hai.

---
**Q: Write the difference between a microkernel and a monolithic kernel. (Microkernel aur monolithic kernel me antar likho.)**

| Feature | Monolithic Kernel | Microkernel |
| :--- | :--- | :--- |
| **Architecture** | Sabhi OS services (drivers, file system, etc.) ek hi **bade kernel** me chalti hain. | Sirf **basic services** (IPC, scheduling) kernel me chalti hain. Baaki services user-space me chalti hain. |
| **Size** | Bada hota hai. | Chhota hota hai. |
| **Performance** | **Fast**, kyunki services ke beech communication function calls se ho jaata hai. | **Slow**, kyunki services ke beech communication ke liye IPC (Inter-Process Communication) use hota hai, jisme overhead zyada hai. |
| **Security** | Kam secure. Agar ek driver fail ho gaya, to poora system crash ho sakta hai. | Zyada secure aur reliable. Agar ek service (e.g., file system) fail hoti hai, to system chalta rehta hai. |
| **Extensibility**| Nayi service add karna mushkil hai. Poora kernel recompile karna padta hai. | Nayi service add karna aasan hai. |

---
### **System Calls**

**Q: What is the difference between a normal function call and a System Call in OS? (Normal function call aur System Call me kya antar hai?)**
A: * **Normal Function Call:** Ye user program ke andar hi hota hai. Control program ke ek hisse se doosre hisse me jaata hai. Ye **User Mode** me hi rehta hai aur fast hota hai.
* **System Call:** Ye user program dwara OS **kernel** ko ki gayi ek request hoti hai. Isme control **User Mode se Kernel Mode me switch** hota hai, jisse overhead badh jaata hai aur ye slow hota hai. System calls ka use privileged operations (jaise file read/write, process create) ke liye hota hai.

---
**Q: What is a bootstrap program in OS? (Bootstrap program kya hai?)**
A: Bootstrap program wo **pehla program** hai jo computer ke **power on** hone par chalta hai. Ye aam taur par computer ke firmware (ROM ya UEFI/BIOS) me store hota hai. Iska mukhya kaam system hardware ko initialize karna aur fir Operating System ke **kernel** ko disk se utha kar **main memory (RAM) me load karna** aur use control de dena hai.

---
**Q: What is a GUI? (GUI kya hai?)**
A: GUI ka poora naam **Graphical User Interface** hai. Ye ek visual tarika hai jisse users computer se interact kar sakte hain. Text-based commands likhne ki bajaye, users **icons, windows, menus, aur pointer (mouse)** ka use karke computer ko operate karte hain. Windows aur macOS popular GUI-based OS hain.
---

### **Process Management**

#### **Process and its States**

**Q: What is a process? (Process kya hai?)**
A: Ek process **"a program in execution"** hai. Jab aap koi program (jaise `chrome.exe`) disk se utha kar memory me load karke run karte hain, to wo ek **active entity** ban jaata hai, jise process kehte hain. Har process ke paas apna memory space, program counter, registers, aur system resources hote hain.

---
**Q: What is a process table? (Process table kya hai?)**
A: Process table, operating system dwara maintain kiya jaane wala ek **data structure** hai. Isme system me chal rahe sabhi active processes ki information store hoti hai. Is table ki har entry ek **Process Control Block (PCB)** hoti hai, jisme process ki saari zaroori jaankari (jaise Process ID, state, CPU registers) hoti hai.

---
**Q: What are the different states of a process? (Process ke alag-alag states kya hain?)**
A: Ek process apne life cycle me in 5 mukhya states se guzarta hai:
1.  **New (Naya):** Process abhi banaya ja raha hai.
2.  **Ready (Taiyaar):** Process execute hone ke liye taiyaar hai aur CPU milne ka intezaar kar raha hai.
3.  **Running (Chal Raha Hai):** Process ki instructions CPU par execute ho rahi hain.
4.  **Waiting (Intezaar Kar Raha Hai):** Process kisi event (jaise I/O operation) ke poora hone ka intezaar kar raha hai.
5.  **Terminated (Khatm):** Process ne apna execution poora kar liya hai.

---
**Q: What are the various sections of a process? (Ek process ke alag-alag sections kya hote hain?)**
A: Ek process ki memory aam taur par in chaar sections me bati hoti hai:
* **Stack:** Isme temporary data store hota hai, jaise function parameters, return addresses, aur local variables.
* **Heap:** Isme program ke runtime ke dauraan dynamically memory allocate ki jaati hai (jaise C++ me `new` ya C me `malloc`).
* **Data Section:** Isme global aur static variables store hote hain.
* **Text Section:** Isme program ka executable code (machine instructions) hota hai.

---
**Q: What is Context Switching? (Context Switching kya hai?)**
A: Context switching wo mechanism hai jiske zariye OS, CPU ka control ek process se lekar doosre process ko deta hai. Is process me:
1.  Current running process ki **state (context)** ko uske **PCB (Process Control Block)** me save kiya jaata hai.
2.  Naye process ki state ko uske PCB se **load** kiya jaata hai.

Ye multitasking achieve karne ke liye zaroori hai, lekin ye ek **pure overhead** hai kyunki is dauraan system koi useful kaam nahi kar raha hota.

---
**Q: Explain zombie process. (Zombie process ko samjhaiye.)**
A: Ek **zombie process** wo process hota hai jo apna execution **poora kar chuka hai**, lekin process table me uski entry abhi bhi maujood hai. Aisa isliye hota hai kyunki uske **parent process** ne abhi tak `wait()` system call ka use karke uska exit status read nahi kiya hai. Ye processes koi resource use nahi karte, siwaye process table me ek entry ke. Inhe "defunct" process bhi kehte hain.

---
**Q: What do you mean by cascading termination? (Cascading termination se aap kya samajhte hain?)**
A: **Cascading termination** ka matlab hai ki agar ek **parent process** terminate hota hai, to uske saare **child processes** bhi automatically terminate kar diye jaate hain. Zyadaatar operating systems is rule ko follow karte hain taaki koi bhi "orphan process" (aisa child jiska parent terminate ho chuka hai) system me chalta na reh jaaye.

---
#### **Process Scheduling**

**Q: What is a Scheduling Algorithm? (Scheduling Algorithm kya hai?)**
A: Scheduling Algorithm wo policy ya set of rules hai jise OS ka **scheduler** use karta hai ye decide karne ke liye ki **ready queue** me maujood processes me se kis process ko agla CPU allocate kiya jaayega. In algorithms ka goal system ki performance ko optimize karna hota hai.

---
**Q: What are the different scheduling algorithms? (Alag-alag scheduling algorithms kya hain?)**
A: Kuch popular scheduling algorithms hain:
* **First-Come, First-Served (FCFS)**
* **Shortest Job First (SJF)**
* **Round Robin (RR)**
* **Priority Scheduling**
* **Shortest Remaining Time First (SRTF)**
* **Multilevel Queue Scheduling**

---
**Q: Briefly explain FCFS (First-Come, First-Served). (FCFS ko sankshep me samjhaiye.)**
A: FCFS sabse simple scheduling algorithm hai. Iska rule hai - **"jo pehle aayega, wo pehle paayega"**. Jis process ki request pehle aati hai, use CPU pehle allocate kiya jaata hai.
* Ye ek simple **FIFO (First-In, First-Out) queue** ki tarah kaam karta hai.
* Ye **non-preemptive** hai (ek baar CPU mil gaya to process use poora karke hi chhodega).
* Iska sabse bada disadvantage **"Convoy Effect"** hai, jahan ek lamba process apne peeche kai chote processes ko wait karwa sakta hai.

---
**Q: What is the RR (Round Robin) scheduling algorithm? (Round Robin scheduling algorithm kya hai?)**
A: Round Robin ek **preemptive** scheduling algorithm hai jo khaas taur par time-sharing systems ke liye design kiya gaya hai.
* Isme har process ko CPU par run hone ke liye ek chhota aur fixed time slot milta hai, jise **time quantum** ya **time slice** kehte hain (e.g., 10 milliseconds).
* Agar process us time quantum me poora nahi hota, to use preempt karke ready queue ke **end** me laga diya jaata hai, aur CPU agle process ko de diya jaata hai.
* Ye starvation ko rokta hai aur achha response time provide karta hai.

---
**Q: What is starvation and aging in OS? (OS me starvation aur aging kya hai?)**
A:
* **Starvation (Bhukhmari):** 😧 Ye wo situation hai jahan ek high-priority process ke lagatar aane ke kaaran ek **low-priority process** ko **indefinitely (anant kaal tak)** CPU nahi mil paata, bhale hi wo ready state me ho. Ise "indefinite blocking" bhi kehte hain.

* **Aging (Umra Badhna):** ✨ Ye **starvation ka solution** hai. Is technique me, jo process bahut der se ready queue me wait kar rahe hote hain, unki **priority samay ke saath dheere-dheere badha di jaati hai**. Isse eventually, wait kar rahe process ki priority itni badh jaati hai ki use CPU mil jaata hai.


---

### **Process Synchronization and Concurrency**

**Q: What do you mean by process synchronization? (Process synchronization se aap kya samajhte hain?)**
A: Process synchronization ek mechanism hai jiska upyog cooperating processes (jo shared resources use karte hain) ke execution ko control karne ke liye kiya jaata hai. Iska mukhya uddeshya **race conditions** ko rokna aur shared data ki **consistency** ko banaye rakhna hai.

---
**Q: What is the Critical Section Problem? (Critical Section Problem kya hai?)**
A:
* **Critical Section:** Ek program ka wo hissa jahan shared resources (jaise shared variables ya files) ko access kiya jaata hai, use critical section kehte hain.
* **The Problem:** Critical Section Problem ek aisi protocol design karne ki samasya hai jo ye sunishchit (ensure) kare ki jab ek process apne critical section me execute kar raha ho, to koi doosra process apne critical section me enter na kar sake. Is property ko **Mutual Exclusion** kehte hain.

---
**Q: What is the producer-consumer problem? (and other classic synchronization problems) (Producer-consumer problem kya hai?)**
A:
* **Producer-Consumer Problem:** Ye ek classic synchronization problem hai. Isme do tarah ke processes hote hain - **Producer** aur **Consumer**, jo ek fixed-size ke shared buffer ko use karte hain.
    * Producer ka kaam data create karke buffer me daalna hai.
    * Consumer ka kaam buffer se data nikal kar use consume karna hai.
    * Samasya ye hai ki Producer bhare hue buffer me data na daale aur Consumer khaali buffer se data na nikaale.
* **Other Classic Problems:** Iske alawa do aur classic problems hain:
    1.  **Readers-Writers Problem:** Multiple readers aur writers ek shared data ko kaise safely access karein.
    2.  **Dining Philosophers Problem:** Deadlock aur starvation se bachne ke liye limited resources ko processes ke beech kaise allocate karein.

---
**Q: What is a Semaphore? What are its types? (Semaphore kya hai? Iske prakaar kya hain?)**
A: Semaphore ek integer variable hai jo process synchronization ke liye use hota hai. Ye busy waiting ki samasya ko solve karta hai. Ise sirf do atomic (uninterruptible) operations se hi access kiya ja sakta hai.
Iske do prakaar hain:
1.  **Counting Semaphore:** Iski value koi bhi non-negative integer ho sakti hai. Ye un resources ko manage karne ke kaam aata hai jinke multiple instances hote hain (e.g., 5 free printers).
2.  **Binary Semaphore:** Iski value sirf **0** ya **1** ho sakti hai. Ise aam taur par mutual exclusion ke liye use kiya jaata hai aur ise **mutex** bhi kehte hain.

---
**Q: What are the different kinds of operations that are possible on a semaphore? (Semaphore par kaun-kaun se operations kiye ja sakte hain?)**
A: Semaphore par do mukhya atomic operations kiye ja sakte hain:
1.  **`wait()` (ya `P`):** Ye operation semaphore ki value ko **ek se kam (decrement)** karta hai. Agar value 0 se kam ho jaati hai, to process block ho jaata hai (wait karne lagta hai).
2.  **`signal()` (ya `V`):** Ye operation semaphore ki value ko **ek se badha (increment)** deta hai. Agar koi process wait kar raha ho, to usme se ek ko unblock kar diya jaata hai.

---
**Q: What is IPC (Inter-Process Communication)? (IPC kya hai?)**
A: IPC (Inter-Process Communication) un mechanisms ka set hai jinke through alag-alag processes ek doosre se communicate kar sakte hain aur apne actions ko synchronize kar sakte hain. Iske do mukhya models hain:
* **Shared Memory:** Multiple processes ek common memory area ko share karte hain. Ye fast hota hai.
* **Message Passing:** Processes ek doosre ko messages bhejkar communicate karte hain. Ye slow hota hai lekin implement karna aasan hai.

---
**Q: What is a Pipe and when is it used? (Pipe kya hai aur iska istemal kab hota hai?)**
A: Ek **pipe**, IPC ke liye use hone wala ek **unidirectional** communication channel hai. Isme ek process dwara likha gaya data doosre process dwara padha ja sakta hai.
Iska sabse common use command-line me hota hai, jahan ek command ke output ko doosre command ka input banaya jaata hai.
**Example:** `ls -l | grep ".txt"` - Yahan `|` symbol ek pipe create karta hai jo `ls -l` ke output ko `grep` command ke input me bhejta hai.

---
**Q: What are Sockets in OS? (OS me Sockets kya hain?)**
A: Ek **socket**, network par data bhejne ya receive karne ke liye ek **endpoint** (chhor) hai. Ye network communication ke liye ek **API (Application Programming Interface)** hai. Ek socket ko **IP address** aur **port number** ke combination se pehchana jaata hai. Internet par chalne waali sabhi applications, jaise web browsers aur servers, communication ke liye sockets ka hi istemal karti hain.

---
**Q: What is Reentrancy? (Reentrancy kya hai?)**
A: Reentrancy ek function ki property hai, jiske anusaar wo function apne execution ke beech me interrupt hone ke baad bhi, safely dobara call kiya ja sakta hai (re-entered), isse pehle ki uska pehla call poora ho. Aisa karne ke liye, function ko koi bhi **static ya global modifiable data** use nahi karna chahiye. Sara data function ke local variables (stack par) me hi hona chahiye. Multi-threaded programming me ye concept bahut zaroori hai.

---
### **Deadlock**

**Q: What is a deadlock in OS? (OS me deadlock kya hai?)**
A: Deadlock ek aisi sthiti (situation) hai jahan do ya do se zyada processes anant kaal ke liye **block** ho jaate hain. Aisa isliye hota hai kyunki har process ek aise resource ko **hold** karke baitha hota hai jise doosra process **request** kar raha hota hai, aur wo doosra process pehle process dwara hold kiye gaye resource ka wait kar raha hota hai. Is circular waiting ke kaaran koi bhi process aage nahi badh paata.
**Analogy:** 🧠 Ek traffic jam jahan chaar raaston ke intersection par chaar gaadiyan aamne-saamne aa kar ek doosre ke raaste me khadi ho jaati hain.

---
**Q: What are the methods for preventing deadlock? (Deadlock ko rokne ke kya tarike hain?)**
A: Deadlock ko rokne ke liye, hum deadlock ki chaar zaroori sharton (necessary conditions) me se kisi ek ko hone se rokte hain:
1.  **Break Mutual Exclusion:** Agar ho sake to resources ko sharable banaya jaaye (lekin ye hamesha possible nahi hai, jaise printer).
2.  **Break Hold and Wait:** Process ko start hone se pehle hi saare zaroori resources allocate kar diye jaayein.
3.  **Break No Preemption:** Agar koi process naye resource ke liye wait kar raha hai, to OS uske paas maujood resources ko zabardasti (preempt) kar le.
4.  **Break Circular Wait:** Sabhi resources ko ek numerical order de diya jaaye aur har process ko resources hamesha **increasing order** me hi request karne ke liye force kiya jaaye.

---
**Q: What is the Banker's algorithm? (Banker's algorithm kya hai?)**
A: Banker's algorithm ek **deadlock avoidance** algorithm hai. Ye algorithm system ko hamesha ek **safe state** me rakhne ki koshish karta hai.
Jab bhi koi process naye resource ke liye request karta hai, to Banker's algorithm pehle ye check karta hai ki kya us request ko poora karne ke baad bhi system **safe state** me rahega (yaani, kya abhi bhi processes ko poora karne ka koi safe sequence maujood hai). Agar haan, to request poori ki jaati hai. Agar nahi, to process ko wait karaya jaata hai.


---
### **Core Concepts (Memory Management, Virtual Memory, Paging)**

**Q: What is the difference between main memory and secondary memory? (Main memory aur secondary memory me kya antar hai?)**
A:

| Feature | Main Memory (RAM) | Secondary Memory (HDD/SSD) |
| :--- | :--- | :--- |
| **Nature** | **Volatile** (power off hone par data delete ho jaata hai). | **Non-Volatile** (power off hone par bhi data save rehta hai). |
| **Speed** | Bahut **fast** hoti hai. | Bahut **slow** hoti hai. |
| **Size** | Chhoti hoti hai (GBs me). | Badi hoti hai (TBs me). |
| **Cost** | Mehengi hoti hai. | Sasti hoti hai. |
| **CPU Access**| CPU isse **directly** access kar sakta hai. | CPU isse directly access nahi kar sakta; data pehle RAM me laaya jaata hai. |

---
**Q: What are memory management techniques (First Fit, Best Fit, Worst Fit)? (Memory management ki techniques kya hain?)**
A: Ye **contiguous memory allocation** me use hone waali techniques hain jo ye decide karti hain ki ek naye process ko free memory holes me se kaun sa hole allocate karna hai:
* **First Fit:** Shuru se scan karo aur jo **pehla** hole process ko fit karne ke liye kaafi bada ho, use allocate kar do.
* **Best Fit:** Poori list scan karo aur wo **sabse chhota** hole dhundo jo process ko fit kar de.
* **Worst Fit:** Poori list scan karo aur **sabse bada** hole allocate kar do, taaki bacha hua hole bhi use ho sake.

---
**Q: What is virtual memory? (Virtual memory kya hai?)**
A: Virtual memory ek aisi technique hai jo user ko ek bahut bade, private, aur contiguous memory space ka **illusion (bhram)** deti hai, bhale hi physical RAM (main memory) usse kaafi choti ho. Iski vajah se hum RAM se bade programs chala sakte hain aur ek saath kai programs ko memory me rakh sakte hain.

---
**Q: What is the basic function of paging? (Paging ka basic function kya hai?)**
A: Paging ka basic function **external fragmentation** ki samasya ko poori tarah se khatam karna hai. Ye logical memory ko fixed-size **pages** me aur physical memory ko same size ke **frames** me baantkar karta hai. Isse ek process ke alag-alag hisse memory me kahin bhi (non-contiguously) store ho sakte hain.

---
**Q: Explain demand paging. (Demand paging ko samjhaiye.)**
A: Demand paging, virtual memory ko implement karne ka ek tarika hai. Isme, ek page ko secondary memory (disk) se main memory (RAM) me **tabhi laaya jaata hai jab uski zaroorat padti hai (on-demand)**. Jab program shuru hota hai, to koi bhi page load nahi hota. Jaise-jaise program ko pages ki zaroorat padti hai, wo "page fault" ke through memory me laaye jaate hain. Ise **lazy loading** bhi kehte hain.

---
**Q: What is the difference between paging and segmentation? (Paging aur segmentation me kya antar hai?)**
A:

| Feature | Paging | Segmentation |
| :--- | :--- | :--- |
| **Block Size** | Blocks ka size **fixed** hota hai (Pages). | Blocks ka size **variable** hota hai (Segments). |
| **User View** | User (programmer) ko iske baare me nahi pata hota. | Ye programmer ke view se match karta hai (code, stack, heap segments). |
| **Fragmentation**| Isme **Internal Fragmentation** hota hai. | Isme **External Fragmentation** hota hai. |
| **Speed** | Address translation fast hota hai. | Address translation slow hota hai. |

---
**Q: State the main difference between logical and physical address space. (Logical aur physical address space me mukhya antar batao.)**
A:
* **Logical Address Space:** Ye wo set of addresses hai jo **CPU generate karta hai**. Har process ka apna alag logical address space hota hai. Ise **virtual address** bhi kehte hain.
* **Physical Address Space:** Ye wo set of addresses hai jo **main memory (RAM)** me maujood hain.

In dono ke beech translation ka kaam hardware (MMU - Memory Management Unit) karta hai.

---
**Q: How does swapping result in better memory management? (Swapping se memory management behtar kaise hota hai?)**
A: **Swapping** wo process hai jisme ek process (ya uske pages) ko temporarily main memory se **backing store (disk)** par move kar diya jaata hai taaki doosre processes ke liye jagah ban sake. Isse OS, physical RAM se zyada processes ko handle kar sakta hai, jisse **degree of multiprogramming** badh jaati hai aur system ka overall utilization behtar hota hai.

---
### **Memory Allocation and Utilization**

**Q: What is fragmentation? (Fragmentation kya hai?)**
A: Fragmentation, memory me wasted space ko kehte hain jise use nahi kiya ja sakta. Ye do tarah ka hota hai:
1.  **External Fragmentation:** Jab memory me kaafi free space to hota hai, lekin wo **chote-chote, non-contiguous (alag-alag) tukdo** me bikhra hota hai, jisse kisi bade process ko allocate nahi kiya ja sakta.
2.  **Internal Fragmentation:** Jab ek process ko uski zaroorat se **zyada bada memory block** de diya jaata hai. Us block ke andar ka bacha hua unused space waste ho jaata hai.

---
**Q: What are overlays? (Overlays kya hain?)**
A: Overlays ek purani memory management technique hai jo RAM se bade programs ko chalaane ke liye use hoti thi. Isme, programmer khud program ko logical pieces (**overlays**) me divide karta tha. Ek samay par sirf zaroori overlays hi memory me rakhe jaate the. Ye **manual** process tha, jabki aajkal virtual memory ye kaam **automatically** karti hai.

---
**Q: How does dynamic loading aid in better memory space utilization? (Dynamic loading se memory space ka behtar upyog kaise hota hai?)**
A: **Dynamic loading** me, program ka koi function ya routine tab tak memory me load nahi hota jab tak use **call na kiya jaaye**. Iska fayda ye hai ki jo functions kabhi use hi nahi hote, wo memory me jagah nahi gherte. Isse memory space ka behtar utilization hota hai.

---
**Q: What is a Page Fault? (Page Fault kya hai?)**
A: Page fault ek **trap (interrupt)** hota hai jo hardware dwara tab generate kiya jaata hai jab CPU ek aise memory page ko access karne ki koshish karta hai jo uss samay **main memory (RAM) me maujood nahi hai**. Page fault hone par OS, zaroori page ko disk se RAM me laata hai.

---
**Q: What are page replacement algorithms (LRU, Optimal, FIFO)? (Page replacement algorithms kya hain?)**
A: Jab page fault hota hai aur RAM me koi free frame nahi hota, to OS ko kisi purane page ko RAM se hatana padta hai. Ye decision lene ke liye Page Replacement Algorithms ka use hota hai:
* **FIFO (First-In, First-Out):** Jo page sabse pehle RAM me aaya tha, use hi replace karo.
* **Optimal (OPT):** Us page ko replace karo jiski zaroorat future me sabse der me padegi. (Ye best hai par practical nahi).
* **LRU (Least Recently Used):** Us page ko replace karo jo sabse lambe samay se use nahi hua hai.

---
**Q: What do you mean by Belady's Anomaly? (Belady's Anomaly se aap kya samajhte hain?)**
A: Belady's Anomaly ek ajeeb phenomenon hai jahan **memory frames ka number badhaane par page faults kam hone ki jagah ulta badh jaate hain**. Ye anomly khaas taur par **FIFO** page replacement algorithm me dekhi jaati hai.

---
**Q: What is Thrashing? (Thrashing kya hai?)**
A: Thrashing ek aisi sthiti hai jahan system **execute karne se zyada samay paging** (pages ko disk se RAM me laane aur RAM se disk par le jaane) me waste kar raha hota hai. Isse system ki performance achanak se bahut gir jaati hai aur CPU utilization lagbhag zero ho jaata hai.

---
### **Cache and Mapping**

**Q: What is a Buffer? (Buffer kya hai?)**
A: Buffer, memory (aam taur par RAM) me ek **temporary storage area** hota hai. Iska istemal data ko tab hold karne ke liye kiya jaata hai jab wo ek jagah se doosri jagah transfer ho raha ho. Ye khaas taur par do alag-alag speed waale devices (jaise fast CPU aur slow printer) ke beech data transfer ko smooth banane ke kaam aata hai.

---
**Q: What are direct and associative mapping? (Direct aur associative mapping kya hain?)**
A: Ye CPU Cache me main memory ke data ko map karne ki techniques hain:
* **Direct Mapping:** Isme, main memory ka har block, cache ki sirf **ek specific line** par hi jaa sakta hai. Ye simple aur fast hai, lekin isme conflict misses zyada hote hain.
* **Associative Mapping (Fully Associative):** Isme, main memory ka koi bhi block, cache ki **kisi bhi line** par jaa sakta hai. Ye bahut flexible hai, lekin slow aur mehenga hai kyunki poore cache ko ek saath search karna padta hai.

---
### **Disk Scheduling**

**Q: What are disk scheduling algorithms? (Disk scheduling algorithms kya hain?)**
A: Disk scheduling algorithms ka istemal OS karta hai ye decide karne ke liye ki disk par aane waali multiple I/O requests ko kis order me service kiya jaaye. Inka mukhya uddeshya **disk arm ke movement ko kam karna** hota hai, jisse **seek time** ghataaya jaa sake aur disk ki performance behtar ho. Iske kuch examples hain: FCFS, SSTF, SCAN, C-SCAN, LOOK.

---


### **File Systems**

**Q: What is a file system, and what are its components? (File system kya hai, aur iske components kya hain?)**
A: Ek **file system**, operating system ka wo hissa hai jo storage devices (jaise hard disk, SSD) par data ko **store, organize, aur retrieve** karne ke tarike ko control karta hai. Ye files aur directories ko manage karta hai.
Iske mukhya components hain:
* **Files:** Wo actual data jise hum store karte hain.
* **Directory Structure:** Files ko organize karne ka tarika (e.g., folders aur sub-folders ka tree).
* **Metadata:** Files ke baare me jaankari (jaise size, permissions, creation date), jo aam taur par **inodes** me store hoti hai.
* **File System APIs:** Wo set of functions (jaise `open()`, `read()`, `write()`, `close()`) jinke through applications file system se interact karti hain.

---
**Q: What are the types of file systems? (File systems ke prakaar kya hain?)**
A: Alag-alag operating systems alag-alag file systems ka istemal karte hain. Kuch popular file systems hain:
* **Windows ke liye:** **FAT32** (File Allocation Table), **NTFS** (New Technology File System).
* **Linux ke liye:** **ext4** (Fourth Extended Filesystem), **XFS**, **Btrfs**.
* **macOS ke liye:** **APFS** (Apple File System).
* **Network/Distributed ke liye:** **NFS** (Network File System).

---
**Q: How are files allocated and deallocated? (Files ko allocate aur deallocate kaise kiya jaata hai?)**
A:
* **Allocation:** Jab ek file banayi jaati hai, to OS use disk par store karne ke liye free blocks allocate karta hai. Iske 3 mukhya tarike hain:
    1.  **Contiguous Allocation:** File ko lagatar (contiguous) blocks diye jaate hain.
    2.  **Linked Allocation:** File ke blocks ek linked list ki tarah jude hote hain.
    3.  **Indexed Allocation:** Ek **index block** file ke saare data blocks ka address rakhta hai.
* **Deallocation:** Jab ek file delete ki jaati hai, to OS us file dwara use kiye gaye saare blocks ko **free** mark kar deta hai. Ye jaankari OS apne **free-space management** system (jaise bitmap ya free list) me update kar deta hai, taaki un blocks ko dobara use kiya jaa sake.

---
**Q: What is fragmentation in the context of file systems? (File systems me fragmentation kya hai?)**
A: Fragmentation ka matlab hai disk par wasted space jo istemal nahi ho paa raha hai. Ye do tarah ka hota hai:
1.  **External Fragmentation:** Jab disk par kaafi free space to hota hai, lekin wo **chote-chote, non-contiguous (alag-alag) tukdo** me bikhra hota hai. Is vajah se kisi badi file ke liye jagah nahi mil paati.
2.  **Internal Fragmentation:** Jab ek file ko uski zaroorat se **bada block** allocate kar diya jaata hai. Us block ke andar ka bacha hua unused space waste ho jaata hai.

---
**Q: What is the Direct Access Method? (Direct Access Method kya hai?)**
A: Direct Access ek file access method hai jisme file ke kisi bhi block ko **directly (seedhe)**, bina shuru se sequentially padhe, access kiya jaa sakta hai. Ye method un applications ke liye bahut upyogi hai jinhe data ko random order me access karna hota hai, jaise **databases**. Contiguous aur Indexed allocation methods direct access ko support karte hain.

---
### **I/O Systems**

**Q: What is the difference between blocking vs. non-blocking I/O? (Blocking aur non-blocking I/O me kya antar hai?)**
A:
* **Blocking I/O:** Jab ek process I/O operation (jaise `read()`) ke liye request karta hai, to wo **block (suspend)** ho jaata hai jab tak ki wo operation poora na ho jaaye. Is dauraan process koi aur kaam nahi kar sakta.
* **Non-blocking I/O:** Jab ek process I/O request karta hai, to system call **turant return** ho jaati hai, bhale hi operation poora na hua ho. Process doosre kaam jaari rakh sakta hai aur use baar-baar check karna padta hai ki I/O poora hua ya nahi.

---
**Q: What is the difference between synchronous vs. asynchronous I/O? (Synchronous aur asynchronous I/O me kya antar hai?)**
A:
* **Synchronous I/O:** Is model me, application I/O operation shuru karne ke baad **wait** karti hai (bhale hi wo actively wait kare ya block ho jaaye) jab tak ki wo operation poora na ho jaaye. **Blocking I/O** iska ek type hai.
* **Asynchronous I/O:** Is model me, application I/O operation shuru karti hai aur **apna kaam jaari rakhti hai**. Jab I/O operation poora ho jaata hai, to OS application ko **notify** karta hai (ek signal ya callback ke zariye). Application ko wait ya check karne ki zaroorat nahi padti.

---
**Q: What is spooling in OS? (OS me spooling kya hai?)**
A: **Spooling** (Simultaneous Peripheral Operations On-Line) ek aisi prakriya (process) hai jahan ek dheeme (slow) device (jaise printer) ke liye data ko pehle ek tez (fast) device (jaise **disk**) par ek buffer me store kiya jaata hai. Isse CPU slow device ka intezaar karne ke bajaye doosre kaam kar sakta hai.
**Example:** Jab aap kai documents print karte hain, to wo disk par ek printer queue (spool) me chale jaate hain, jahan se printer unhe apni speed se print karta hai.

---
### **Storage Management and Data Protection**

**Q: What is RAID (Redundant Array of Independent Disks) and what are its types/levels? (RAID kya hai aur iske types/levels kya hain?)**
A: **RAID** ek aisi technology hai jo multiple physical hard disks ko milakar ek ya ek se zyada **logical unit** banati hai. Iska mukhya uddeshya data **redundancy** (data loss se bachav) aur/ya **performance** ko badhana hota hai.
Iske kuch common levels hain:
* **RAID 0 (Striping):** Data ko multiple disks par "stripes" me baant diya jaata hai. Isse **performance** badhti hai, lekin isme **koi redundancy nahi** hoti (ek disk fail to saara data lost).
* **RAID 1 (Mirroring):** Data ko ek disk par likhne ke saath-saath doosri disk par uski **exact copy** banayi jaati hai. Isse **redundancy** badhti hai.
* **RAID 5 (Striping with Parity):** Isme data aur "parity" (error-checking info) ko teen ya usse zyada disks par baanta jaata hai. Ye **performance aur redundancy** ka achha balance deta hai aur ek disk ke fail hone ko jhel sakta hai.
* **RAID 6:** RAID 5 jaisa hi, lekin isme do alag-alag parity blocks hote hain. Ye **do disk ke fail** hone ko jhel sakta hai.
* **RAID 10 (1+0):** Ye mirroring (RAID 1) aur striping (RAID 0) ka combination hai. Ye **high performance aur high redundancy** dono deta hai.

---
**Q: What are security threats and vulnerabilities in an OS? (OS me security threats aur vulnerabilities kya hain?)**
A:
* **Vulnerability (Kamzori):** System me koi aisi kamzori jiska fayda uthaya jaa sake.
* **Threat (Khatra):** Koi bhi aisi cheez jo vulnerability ka fayda utha kar system ko nuksaan pahuncha sakti hai.

Kuch aam security threats hain:
* **Malware (Virus, Worms, Trojan Horse, Ransomware):** Ye malicious software hote hain jo data chura sakte hain, files corrupt kar sakte hain, ya system ka control le sakte hain.
* **Denial of Service (DoS) Attack:** Is attack ka maqsad system ya network ko itna busy kar dena hota hai ki asli users use access na kar paayein.
* **Phishing:** Users ko dhokha dekar unse unki sensitive information (jaise password ya credit card details) nikalwana.
* **Privilege Escalation:** Jab ek attacker kam access waale account se system me ghus kar zyada access waale (jaise admin) account ka control haasil kar leta hai.
* **Man-in-the-Middle (MITM) Attack:** Jab ek attacker do parties ke beech ho rahe communication ko chupke se sunta hai ya badal deta hai.

---