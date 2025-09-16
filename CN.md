
### **Computer Networking Fundamentals**

#### **Network Devices**
Ye wo hardware devices hain jo computer network ko banane aur usme communication ko aasan banane ke liye istemal hote hain.

* **Hub (हब):** 🔌
    * **Layer:** Physical Layer (Layer 1).
    * **Kaam:** Ye ek simple device hai jo ek port par aane waale data signal ko baaki sabhi ports par **broadcast (repeat)** kar deta hai. Ye "intelligent" nahi hota aur ye nahi jaanta ki data kiske liye hai.
    * **Analogy:** Ek power extension board jisme current har socket me jaata hai.
* **Switch (स्विच):** ↔️
    * **Layer:** Data Link Layer (Layer 2).
    * **Kaam:** Ye Hub se zyada intelligent hai. Ye har connected device ka **MAC address** yaad rakhta hai aur data packet ko sirf uske **intended destination port** par hi bhejta hai. Isse network me unnecessary traffic kam hota hai.
    * **Analogy:** Ek smart power strip jisme aap har socket ko alag-alag control kar sakte hain.
* **Router (राउटर):** 🌐
    * **Layer:** Network Layer (Layer 3).
    * **Kaam:** Router ka kaam **do ya do se zyada alag-alag networks** (jaise aapka ghar ka network aur Internet) ko aapas me jodna hai. Ye **IP address** ka istemal karke data packets ke liye **sabse aacha raasta (best path)** dhoondhta hai aur unhe aage forward karta hai.
    * **Analogy:** Ek chaurahe par khada **traffic police officer** jo alag-alag sadkon se aane waale traffic ko sahi disha me bhejta hai.
* **Repeater (रिपीटर):** 📶
    * **Layer:** Physical Layer (Layer 1).
    * **Kaam:** Ye kamzor ho chuke signal ko **regenerate ya amplify** karke aage bhejta hai taaki network ki range badh sake.
* **Bridge (ब्रिज):** 🌉
    * **Layer:** Data Link Layer (Layer 2).
    * **Kaam:** Ye do alag-alag LAN segments ko aapas me jodta hai. Ye ek Switch jaisa hi hai, lekin aam taur par isme kam ports hote hain.
* **Gateway (गेटवे):** 🏛️
    * **Layer:** Sabhi layers par kaam kar sakta hai.
    * **Kaam:** Ye do aise networks ko jodta hai jo **alag-alag protocols** ka istemal karte hain. Ye protocol translator ki tarah kaam karta hai.
    * **Analogy:** Ek **anuvadak (translator)** jo do alag-alag bhasha bolne waale logon ke beech communication karwata hai.

---
#### **Types of Networks**
Networks ko unke geographical area ke aadhar par classify kiya jaata hai:
* **LAN (Local Area Network):** 🏡 Ye ek chote area (jaise ek ghar, office, ya ek building) tak seemit rehta hai. Iski speed bahut tez hoti hai. **Example:** Aapke ghar ka Wi-Fi network.
* **MAN (Metropolitan Area Network):** 🏙️ Ye ek poore sheher (city) ko cover karta hai. Ye kai LANs ko aapas me jodkar banta hai. **Example:** Cable TV network.
* **WAN (Wide Area Network):** 🌍 Ye ek bahut bade geographical area (jaise ek desh ya poori duniya) ko cover karta hai. **Internet** sabse bada WAN hai. Iski speed LAN se kam hoti hai.

---
#### **Network Models**
Network models, communication process ko samjhne ke liye ek **framework** pradaan karte hain. Ye batate hain ki alag-alag devices aur protocols aapas me kaise interact karte hain.

* **OSI Model (Open Systems Interconnection)**
    * **Concept:** Ye ek **7-layer conceptual reference model** hai. Iska istemal asal me nahi hota, lekin ye networking ke concepts ko samjhne ke liye ek standard maana jaata hai.
    * **The 7 Layers (Bottom to Top):**
        * **Layer 7: Application Layer:** User ke sabse kareeb. Ye network services ko applications tak pahunchata hai. (e.g., HTTP, FTP, SMTP).
        * **Layer 6: Presentation Layer:** Data ko ek standard format me **translate** karta hai. Encryption aur compression bhi yahan hota hai.
        * **Layer 5: Session Layer:** Do devices ke beech **connection (session)** ko establish, manage, aur terminate karta hai.
        * **Layer 4: Transport Layer:** **End-to-end communication** aur error checking ke liye zimmedar hai. (e.g., TCP, UDP).
        * **Layer 3: Network Layer:** **Routing aur logical addressing (IP Address)** ka kaam karta hai. Data ko packets ke roop me bhejta hai.
        * **Layer 2: Data Link Layer:** **Physical addressing (MAC Address)** aur error-free data transfer ke liye zimmedar hai. Data ko frames ke roop me bhejta hai.
        * **Layer 1: Physical Layer:** Asli data (bits) ko **physical medium** (jaise cables, radio waves) par transmit karta hai.
    * **Mnemonic (Yaad karne ka tarika):** "Please Do Not Throw Sausage Pizza Away" (Physical, Data Link, Network, Transport, Session, Presentation, Application).

* **TCP/IP Model**
    * **Concept:** Ye ek **4-layer (ya 5-layer) practical model** hai jispar poora Internet kaam karta hai.
    * **The Layers (and comparison with OSI):**
        * **Application Layer:** (Corresponds to OSI Layers 5, 6, 7)
        * **Transport Layer:** (Corresponds to OSI Layer 4)
        * **Internet Layer:** (Corresponds to OSI Layer 3)
        * **Network Access Layer (or Link Layer):** (Corresponds to OSI Layers 1, 2)
    * Ye OSI model se zyada simple aur practical hai.

---
### **Physical Layer**

#### **Types of Network Topology**
* **Definition:** Topology, network me nodes (devices) aur connections ke **physical ya logical layout (arrangement)** ko kehte hain.

    | Topology | Description | Pros | Cons |
    | :--- | :--- | :--- | :--- |
    | **Bus** | Sabhi devices ek **single central cable (bus)** se jude hote hain. | Sasta aur aasan. | Agar central cable fail ho jaaye, to poora network band ho jaata hai. |
    | **Ring** | Sabhi devices ek **ring ya circle** me jude hote hain. Data ek hi disha me travel karta hai. | Traffic collision nahi hota. | Agar ek bhi device ya cable fail ho jaaye, to poora network band ho jaata hai. |
    | **Star** | Sabhi devices ek **central device (hub/switch)** se jude hote hain. | Reliable (agar ek cable fail ho, to baaki network chalta rehta hai). Manage karna aasan. | Central device par nirbhar. Agar wo fail ho jaaye, to poora network band. |
    | **Mesh** | Har device baaki sabhi devices se **directly juda** hota hai. | Bahut reliable aur fault-tolerant. | Bahut mehenga aur complex. |
    | **Tree** | Star aur Bus topologies ka **combination**. | Scalable, alag-alag segments ko jodna aasan. | Central bus par nirbhar. |
    | **Hybrid** | Do ya do se zyada alag-alag topologies ka **combination**. | Flexible aur reliable. | Design karna complex hai. |

---
#### **Modes of Transmission**
* **Definition:** Ye do devices ke beech information ke flow ki **disha (direction)** ko batata hai.
    1.  **Simplex:** 🚶‍♂️ Communication sirf **ek hi disha (one-way)** me hota hai.
        * **Analogy:** TV broadcast, Keyboard se computer me input.
    2.  **Half-Duplex:** 🚶‍♂️↔️🚶‍♀️ Communication **dono dishaon** me ho sakta hai, lekin **ek samay me ek hi taraf**.
        * **Analogy:** Walkie-Talkie.
    3.  **Full-Duplex:** 🚶‍♂️↔️🚶‍♂️ Communication **dono dishaon** me **ek saath (simultaneously)** ho sakta hai.
        * **Analogy:** Telephone par baat karna.

---
#### **Transmission Media**
* **Definition:** Ye wo **physical path** hai jiske through data sender se receiver tak travel karta hai.

    * **Guided Media (Wired):** 🔌
        * **Twisted Pair Cable:** Isme do insulated copper wires aapas me twisted hote hain. (LAN/Ethernet cables me use hota hai).
        * **Coaxial Cable:** Isme ek central copper wire hota hai jiske upar insulation aur shielding ki layers hoti hain. (Cable TV me use hota hai).
        * **Fiber Optic Cable:** Isme data, kaanch ya plastic ke patle dhaago (strands) ke through **light pulses** ke roop me travel karta hai. Ye sabse tez aur sabse zyada bandwidth wala medium hai.

    * **Unguided Media (Wireless):** 📡
        * **Radio Waves:** Wi-Fi, Bluetooth, aur mobile phones inka istemal karte hain.
        * **Microwaves:** Lambi doori ke point-to-point communication ke liye use hoti hain (jaise satellite communication).
        * **Infrared:** Choti doori ke communication ke liye use hoti hain (jaise TV remote).

---

### **Data Link Layer**
Data Link Layer (OSI Layer 2) ka mukhya kaam Network Layer se aane waale data packets ko **frames** me convert karna aur unhe ek physical link par **reliable tarike se** ek node se doosre node tak transfer karna hai.

#### **Switching Techniques**
* **Concept:** Switching, network me data ko source se destination tak pahunchane ke liye raasta (path) chunne ki technique hai.
    1.  **Circuit Switching:** ☎️
        * **Mechanism:** Isme data transfer shuru hone se pehle, sender aur receiver ke beech ek **dedicated physical path** banaya jaata hai. Ye path poore communication ke dauraan bana rehta hai.
        * **Analogy:** Ek purana **telephone call**. Jab tak aap baat karte hain, aapke beech ek dedicated line judi rehti hai, bhale hi aap chup kyun na hon.
        * **Pros:** Guaranteed bandwidth, koi delay nahi.
        * **Cons:** Inefficient. Agar data nahi bheja jaa raha hai to bhi line busy rehti hai.
    2.  **Packet Switching:** 📦
        * **Mechanism:** Isme data ko chote-chote, fixed-size ke **packets** me toda jaata hai. Har packet ko ek header (jisme destination address hota hai) diya jaata hai. Ye packets alag-alag raaston se jaakar destination par pahunchte hain aur wahan wapas reassemble hote hain. **Internet isi par kaam karta hai.**
        * **Analogy:** Ek badi si kitaab ko alag-alag pages me faad kar, har page ko alag-alag lifafe me daal kar post karna.
        * **Pros:** Efficient, reliable (agar ek raasta band ho to packet doosre raaste se jaa sakta hai).
        * **Cons:** Jitter (packets ke aane me aniyamit deri) ho sakti hai.

---
#### **Virtual LAN (VLAN)**
* **Definition:** 🏢 VLAN (Virtual Local Area Network) ek aisi technology hai jisse ek bade physical LAN ko logically **chote-chote virtual LANs** me baanta jaa sakta hai.
* **Purpose:** Iske do mukhya fayde hain:
    1.  **Security:** Ek VLAN ke devices doosre VLAN ke devices se direct communicate nahi kar sakte (bina router ke). Isse sensitive departments (jaise HR, Finance) ko alag rakha jaa sakta hai.
    2.  **Performance:** Har VLAN ek alag **broadcast domain** ban jaata hai, jisse network me unnecessary broadcast traffic kam ho jaata hai.
* **Analogy:** 🧠 Ek bahut bada open office hall (physical LAN) hai. Aap usme kaanch ki deewarein (VLANs) laga kar alag-alag departments (jaise Sales VLAN, Tech VLAN) bana dete hain. Sales waale aapas me aasaani se baat kar sakte hain, lekin Tech waalon se baat karne ke liye unhe receptionist (router) ke paas jaana padega.

---
#### **Link Aggregation**
* **Definition:** 🛣️ Link Aggregation, do ya do se zyada physical network connections (cables) ko aapas me milakar ek **single high-bandwidth logical link** banane ki technique hai. Ise **Port Trunking** ya **NIC Bonding** bhi kehte hain.
* **Purpose:**
    1.  **Increased Bandwidth:** Agar aapke paas 1 Gbps ke 3 links hain, to aap unhe milakar ek 3 Gbps ka link bana sakte hain.
    2.  **Fault Tolerance:** Agar ek link fail ho jaata hai, to traffic baaki links se jaata rehta hai.

---
#### **Framing**
* **Concept:** Framing, Network Layer se aane waali bit stream ko **manageable data units** me divide karne ka process hai. In units ko **Frames** kehte hain.
* **Purpose:** Data Link Layer har frame me ek **Header** (jisme source aur destination MAC address hota hai) aur ek **Trailer** (jisme error detection code hota hai) jodta hai. Isse receiver ko pata chalta hai ki frame kahan shuru ho raha hai, kahan khatam ho raha hai, aur usme koi error hai ya nahi.

---
#### **Error Detection, Correction, and Control**
* **Error Detection:** 🔎 Ye wo techniques hain jinka istemal ye pata lagane ke liye hota hai ki transmission ke dauraan data me koi galti (error) aayi hai ya nahi.
    * **Methods:** Parity Check, **Checksum**, **Cyclic Redundancy Check (CRC)**. CRC sabse powerful aur commonly used hai.
* **Error Correction:** ✍️ Ye wo techniques hain jo na sirf error ka pata lagati hain, balki unhe **theek (correct)** bhi karti hain, bina data ko dobara mangwaye.
    * **Methods:** Hamming Code.
* **Error Control:** 🔄 Ye ek overall mechanism hai jisme **error detection** aur **retransmission** (galtiyon waale frames ko dobara bhejna) dono shaamil hote hain. Ye **ARQ (Automatic Repeat Request)** protocols se achieve kiya jaata hai.

---
#### **Flow Control**
* **Concept:** 🚰 Flow Control ek aisi prakriya hai jo ye sunishchit karti hai ki ek **fast sender**, ek **slow receiver** ko data se "overwhelm" (bhar) na kar de.
* **Purpose:** Isse receiver ka buffer overflow hone se bachaya jaata hai. Receiver sender ko signal bhej kar bata sakta hai ki wo kitna data handle kar sakta hai.

---
#### **Automatic Repeat Request (ARQ) Protocols**

* **Stop and wait ARQ**
    * **Concept:** Ye sabse simple error aur flow control protocol hai.
    * **Mechanism:**
        1.  Sender ek frame bhejta hai.
        2.  Sender, receiver se **Acknowledgement (ACK)** milne ka **intezaar (wait)** karta hai.
        3.  ACK milne ke baad hi, sender agla frame bhejta hai.
        4.  Agar ek timeout tak ACK nahi milta (ya frame lost ho jaata hai), to sender ussi frame ko **dobara (retransmit)** bhejta hai.
    * **Disadvantage:** Bahut **inefficient** hai, kyunki sender zyadaatar samay intezaar karne me hi bita deta hai.

---
* **Sliding Window Protocol - Go-Back-N (GBN)**
    * **Concept:** 💨 Ye Stop-and-Wait se behtar hai. Sender, bina ACK ka intezaar kiye, ek saath **kai frames** (ek window size 'N' tak) bhej sakta hai.
    * **Mechanism:**
        * Receiver hamesha frames ko **in-order** accept karta hai.
        * Agar koi frame (e.g., Frame 3) lost ya corrupt ho jaata hai, to receiver Frame 3 aur uske baad aane waale **sabhi frames (4, 5, 6, ...)** ko **discard** kar deta hai.
        * Jab sender ka timer expire hota hai, to wo **wapas (Go-Back)** Frame 3 par jaata hai aur **Frame 3 aur uske baad ke sabhi frames** ko dobara bhejta hai.

---
* **Sliding Window Protocol - Selective Repeat (SR)**
    * **Concept:** ✨ Ye Go-Back-N se bhi zyada efficient hai.
    * **Mechanism:**
        * Receiver **out-of-order frames** ko bhi accept aur buffer kar sakta hai.
        * Agar koi frame (e.g., Frame 3) lost hota hai, to receiver sirf **usi frame** ke liye Negative Acknowledgement (NAK) bhejta hai.
        * Sender sirf ussi **ek frame (Frame 3)** ko dobara bhejta hai jiska NAK aaya hai. Wo uske baad ke frames (jo aache se pahunch chuke hain) ko dobara nahi bhejta.

---
#### **Piggybacking**
* **Concept:** 🐷 Piggybacking, bidirectional communication me efficiency badhane ki ek technique hai.
* **Mechanism:** Ek alag se Acknowledgement (ACK) frame bhejne ke bajaye, ACK ko **reverse direction me jaane waale data frame ke header me hi "piggyback" (jod)** kar bhej diya jaata hai.
* **Benefit:** Isse bheje jaane waale total frames ki sankhya kam ho jaati hai, jisse network bandwidth bachti hai.

---


### **Network Layer**
Network Layer (OSI Layer 3) ka mukhya kaam **logical addressing (IP addressing)** aur **routing** hai. Iska goal data packets ko source se destination tak, alag-alag networks ke through, sabse behtar raaste (best path) se pahunchana hai.

#### **IP Addressing**

* **Classful Network Addressing**
    * **Concept:** Ye IPv4 addresses ko classify karne ka purana tarika tha, jisme address space ko 5 fixed-size **classes** (A, B, C, D, E) me baanta gaya tha.
    * **Classes:**
| Class | Leading Bits | First Octet Range | Default Subnet Mask | Use |
| :--- | :--- | :--- | :--- | :--- |
| **A** | `0` | 1 - 126 | 255.0.0.0 | Bahut bade networks ke liye. |
| **B** | `10` | 128 - 191 | 255.255.0.0 | Medium se bade networks ke liye. |
| **C** | `110`| 192 - 223 | 255.255.255.0 | Chote networks ke liye. |
| **D** | `1110`| 224 - 239 | N/A | Multicasting. |
| **E** | `1111`| 240 - 255 | N/A | Experimental use. |
    * **Problem:** 😥 Isse IP addresses ki bahut **barbadi (wastage)** hoti thi. Agar kisi company ko sirf 500 IP chahiye, to use Class B network (jisme 65,534 hosts aa sakte hain) dena padta tha, jisse hazaron IPs waste ho jaate the.

---
* **Classless Network Addressing (CIDR)**
    * **Concept:** CIDR (Classless Inter-Domain Routing), classful addressing ki samasya ko door karta hai. Ye classes ke rigid boundaries ko khatam kar deta hai.
    * **Notation:** ✍️ Isme **slash notation** ka istemal hota hai (e.g., `192.168.1.0/24`). Slash ke baad ka number (`/24`) batata hai ki address ke kitne bits **network portion** ke liye hain. Isse IP address blocks ko zaroorat ke hisaab se flexible size me allocate kiya jaa sakta hai.

---
* **IPv4 Header Format**
    Har IPv4 packet ke shuru me ek header hota hai jisme routing ke liye zaroori jaankari hoti hai. Kuch important fields hain:
    
    * **Version:** Hamesha 4 hota hai.
    * **IHL (Header Length):** Header ki length batata hai.
    * **Total Length:** Header + Data ki poori length.
    * **Time To Live (TTL):** Ek counter jo har router par 1 se kam hota hai. Jab ye 0 ho jaata hai, to packet ko discard kar diya jaata hai. Isse packets network me hamesha ke liye loop hone se bach jaate hain.
    * **Protocol:** Batata hai ki data kis upper-layer protocol ka hai (e.g., **TCP=6, UDP=17**).
    * **Source IP Address:** Bhejne waale ka 32-bit IP address.
    * **Destination IP Address:** Paane waale ka 32-bit IP address.

---
* **IPv4 vs IPv6**
| Feature | IPv4 (Internet Protocol v4) | IPv6 (Internet Protocol v6) |
| :--- | :--- | :--- |
| **Address Size** | **32-bit** | **128-bit** |
| **Address Space**| Lagbhag 4.3 billion addresses. (Ab khatam ho rahe hain). | Lagbhag $3.4 \times 10^{38}$ addresses. (Lagbhag anant). |
| **Notation** | Dotted-Decimal (e.g., `192.168.1.1`) | Hexadecimal, Colon-separated (e.g., `2001:0db8:85a3::8a2e:0370:7334`) |
| **Security** | IPSec optional hai. | IPSec **built-in aur mandatory** hai. |
| **Configuration**| Aam taur par manual ya DHCP se. | **Stateless Autoconfiguration** support karta hai (device khud IP bana sakta hai). |
| **Header** | Complex header. | Simple aur efficient header. |

---
* **Private vs Public IP addresses**
    * **Public IP:** 🌎 Ye ek **globally unique** IP address hota hai jo Internet par communication ke liye istemal hota hai. Ye aapko aapka **ISP (Internet Service Provider)** deta hai.
    * **Private IP:** 🏠 Ye ek aisa IP address hai jo sirf ek **local/private network** (jaise aapke ghar ya office ka Wi-Fi) ke andar istemal hota hai. Ye addresses Internet par routable nahi hote.
    * **Private IP Ranges:**
        * Class A: `10.0.0.0` to `10.255.255.255`
        * Class B: `172.16.0.0` to `172.31.255.255`
        * Class C: `192.168.0.0` to `192.168.255.255`

---
#### **Subnetting**
* **Subnetting basics**
    * **Definition:** 🔪 Subnetting, ek bade network ko **multiple chote-chote logical networks (subnets)** me todne ka process hai.
    * **Purpose:**
        1.  **Improves Security:** Alag-alag departments ke liye alag subnet banakar unke beech access control lagaya jaa sakta hai.
        2.  **Reduces Network Traffic:** Har subnet ek alag broadcast domain ban jaata hai, jisse network me broadcast traffic kam hota hai.
    * **Mechanism:** Ye IP address ke **host portion** se kuch bits "udhaar" lekar unhe **subnet portion** ke liye istemal karke kiya jaata hai.

---
* **Subnet masks**
    * **Definition:** 🎭 Ek Subnet Mask ek 32-bit number hota hai jo ek IP address ke **network portion ko host portion se alag** karta hai.
    * **How it works:** Kisi bhi IP address aur uske subnet mask ke beech bitwise `AND` operation karne par uss IP ka **Network Address** mil jaata hai.

---
* **Calculate network, broadcast and host addresses**
    * **Example:** `IP Address: 192.168.1.75 /27`
    1.  **Analysis:**
        * `/27` ka matlab hai 27 bits network ke liye hain.
        * Total bits = 32. Host bits = 32 - 27 = 5.
        * Subnet Mask: 27 '1's -> `11111111.11111111.11111111.11100000` -> `255.255.255.224`
    2.  **Network Address:** `IP AND Mask`
        * `192.168.1.01001011` AND `255.255.255.11100000` = `192.168.1.01000000`
        * Network Address = **`192.168.1.64`**
    3.  **Broadcast Address:** Network Address me saare host bits ko `1` kar do.
        * `192.168.1.01011111`
        * Broadcast Address = **`192.168.1.95`**
    4.  **Host Addresses:**
        * First Usable Host: Network Address + 1 = **`192.168.1.65`**
        * Last Usable Host: Broadcast Address - 1 = **`192.168.1.94`**

---
* **Variable Length Subnet Masking (VLSM)**
    * **Concept:** 💡 VLSM ek aisi technique hai jisme ek network ko **alag-alag size ke subnets** me toda jaa sakta hai.
    * **Benefit:** Isse IP addresses ki barbadi (wastage) bahut kam ho jaati hai. Aap har subnet ko uski zaroorat ke hisaab se (e.g., ek bade department ko bada subnet, ek chote department ko chota subnet) size de sakte hain.

---
* **Supernetting**
    * **Concept:** 뭉 Supernetting, subnetting ka **ulta** hai. Isme, kai chote-chote contiguous network blocks ko milakar ek **bada network block** banaya jaata hai.
    * **Purpose:** Iska istemal Internet ke core routers me **routing table ke size ko kam karne** ke liye hota hai. Ise **Route Aggregation** ya **CIDR** bhi kehte hain.

---
#### **Routing**
* **What is Routing?**
    * **Definition:** 🗺️ Routing, data packets ko source se destination tak, ek ya ek se zyada networks ke through, bhejne ke liye **raasta (path) select karne** ka process hai. Ye kaam **Routers** karte hain, jo **routing tables** ka istemal karke forwarding decisions lete hain.

---
* **Static vs Dynamic Routing**

| Feature | Static Routing | Dynamic Routing |
| :--- | :--- | :--- |
| **Configuration**| Network administrator dwara **manually** configure kiya jaata hai. | Routers, routing protocols ka istemal karke **automatically** raaste seekhte hain. |
| **Scalability** | Chote networks ke liye aacha hai. | Bade networks ke liye aacha hai. |
| **Adaptability** | Network me change hone par manually update karna padta hai. | Network me change hone par apne aap adapt ho jaata hai. |
| **Security** | Zyada secure hai. | Kam secure hai. |
| **Example** | `ip route` command. | OSPF, EIGRP, RIP, BGP. |

---
* **Link State Routing**
    * **Concept:** Isme, network ka har router apne paas poore network ka ek **complete map (topology)** banata hai.
    * **Mechanism:** Har router apne "link state" (wo kin-kin routers se juda hai aur un tak pahunchne ki cost kya hai) ki information poore network me **broadcast** kar deta hai.
    * **Algorithm:** Is map ka istemal karke, har router **Dijkstra's algorithm** chalata hai aur har destination tak ka sabse chota raasta (shortest path) nikalta hai.
    * **Example Protocol:** **OSPF (Open Shortest Path First)**.

---
* **Distance Vector Routing**
    * **Concept:** Isme, har router ko sirf apne **direct padosiyon (neighbors)** aur unke through baaki networks tak ki **doori (distance)** ka pata hota hai.
    * **Mechanism:** Routers samay-samay par apni poori routing table apne padosiyon ko bhejte hain. Ise **"Routing by Rumor"** bhi kehte hain.
    * **Problem:** Isme slow convergence aur "count-to-infinity" jaisi samasyayein ho sakti hain.
    * **Example Protocol:** **RIP (Routing Information Protocol)**.

---
* **Network Address Translation (NAT)**
    * **Concept:** 🔄 NAT, router dwara istemal ki jaane waali wo prakriya hai jisme ek local network ke **private IP addresses** ko internet par communicate karne ke liye ek **public IP address** me translate kiya jaata hai. Ye private network aur public internet ke beech ka gateway hai.

---

---
### **Network Layer Protocols**

#### **Address Resolution Protocol (ARP)**
* **Layer:** ARP, Layer 3 (Network) aur Layer 2 (Data Link) ke beech kaam karta hai.
* **Purpose:** ARP ka mukhya kaam ek **local network** ke andar, kisi device ka **IP Address (Layer 3 Address)** pata hone par uska **MAC Address (Layer 2 Address)** dhoondhna hai. Data link layer par communication ke liye MAC address zaroori hota hai.
* **Mechanism:**
    1.  Ek computer (Host A) network par ek **ARP Request** broadcast karta hai, jisme likha hota hai, "Jiska bhi IP address `192.168.1.10` hai, wo mujhe apna MAC address bataye."
    2.  Network par maujood sabhi devices is request ko dekhte hain, lekin sirf wo device jiska IP `192.168.1.10` hota hai, wo ek **ARP Reply** (unicast) wapas Host A ko bhejta hai, "Mera IP `192.168.1.10` hai aur mera MAC address `AA:BB:CC:DD:EE:FF` hai."
* **Analogy:** 🧠 Aap ek kamre (LAN) me hain aur aapko kisi ka naam (IP Address) pata hai. Lekin use ek chitthi (data frame) dene ke liye aapko uski shakal (MAC Address) pehchanni hogi. Isliye aap zor se puchte hain, "Yahan Rohan kaun hai?" (ARP Request). Rohan haath utha kar kehta hai, "Main Rohan hu" (ARP Reply).

---
#### **Reverse Address Resolution Protocol (RARP)**
* **Purpose:** RARP, ARP ka **theek ulta** hai. Iska istemal ek device dwara tab kiya jaata hai jab use apna **MAC address** to pata ho, lekin apna **IP address** na pata ho.
* **Status:** 😥 Ye ek **purana (outdated)** protocol hai. Aajkal iski jagah **DHCP** ka istemal hota hai, jo isse kahin zyada advanced hai.

---
#### **Dynamic Host Configuration Protocol (DHCP)**
* **Purpose:** 🌐 DHCP ek client-server protocol hai jiska kaam network par devices ko **automatically IP address**, subnet mask, default gateway, aur DNS server jaisi zaroori information provide karna hai.
* **Mechanism (DORA):**
    1.  **Discover:** Client ek broadcast message bhej kar DHCP server ko dhoondhta hai.
    2.  **Offer:** Server, client ko ek IP address offer karta hai.
    3.  **Request:** Client uss offered IP address ke liye request karta hai.
    4.  **Acknowledge:** Server us IP address ko ek specific time (lease) ke liye client ko de deta hai.

---
#### **Internet Control Message Protocol (ICMP)**
* **Purpose:** ✉️ ICMP ka istemal network devices (jaise routers) dwara **error messages aur operational information** bhejne ke liye kiya jaata hai. Iska istemal normal data transfer ke liye nahi hota. Ye ek diagnostic protocol hai.
* **Common Uses:**
    * **Echo Request/Reply:** `ping` command iska istemal karke connectivity test karti hai.
    * **Destination Unreachable:** Jab ek router kisi packet ko deliver nahi kar paata.
    * **Time Exceeded:** Jab ek packet ka TTL (Time To Live) zero ho jaata hai. `traceroute` command iska istemal karti hai.
* **Analogy:** Ye Indian Post ke "Return to Sender" ya "Address Not Found" waale stamp jaisa hai. Ye chitthi nahi, balki chitthi ki delivery ke baare me ek message hai.

---
#### **Internet Group Management Protocol (IGMP)**
* **Purpose:** 👥 IGMP ka istemal hosts aur routers dwara **multicast group memberships** ko manage karne ke liye kiya jaata hai.
* **Concept:** Multicasting, ek hi data packet ko ek saath kai specific receivers ko bhejne ka tarika hai. IGMP ke zariye ek host apne local router ko batata hai ki, "Main is multicast group (e.g., ek live video stream) ko join karna chahta hu aur iska traffic receive karna chahta hu."

---
#### **Routing Information Protocol (RIP)**
* **Type:** Ye ek purana **Distance Vector** routing protocol hai.
* **Metric:** Ye raasta chunne ke liye **hop count** (routers ki sankhya) ka istemal karta hai. Sabse kam hops wala raasta sabse behtar maana jaata hai.
* **Mechanism:** Routers samay-samay par apni poori routing table apne padosi routers ko bhejte hain.
* **Limitations:** Iski maximum hop count 15 hai, ye dheere-dheere network changes par react karta hai (slow convergence), aur "count-to-infinity" problem se grasit ho sakta hai. Ab iski jagah OSPF ka istemal hota hai.

---
#### **Open Shortest Path First (OSPF)**
* **Type:** OSPF ek modern aur widely used **Link-State** routing protocol hai.
* **Metric:** Ye hop count ki jagah **cost** ka istemal karta hai, jo aam taur par link ki **bandwidth** par aadharit hoti hai.
* **Mechanism:** Har router poore network ka ek **map (topology)** banata hai. Is map ka istemal karke, har router **Dijkstra's algorithm** chalata hai aur har destination tak ka sabse chota raasta (shortest path) nikalta hai.
* **Advantage:** Ye RIP se zyada fast, scalable, aur efficient hai.

---
#### **Border Gateway Protocol (BGP)**
* **Type:** BGP wo protocol hai jispar **poora Internet** chalta hai. Ye ek **Exterior Gateway Protocol (EGP)** hai.
* **Purpose:** Iska istemal alag-alag **Autonomous Systems (AS)** ke beech routing information exchange karne ke liye hota hai. Ek AS ek bada network hota hai jise ek hi organization control karti hai (jaise Jio, Airtel, ya Google ek AS hai).
* **Mechanism:** BGP ek **Path Vector** protocol hai. Ye sirf doori nahi dekhta, balki policies, path, aur doosre attributes ke aadhar par complex routing decisions leta hai.

---
#### **Internet Protocol (IP)**
* **Purpose:** 💻 IP, TCP/IP suite ka mukhya protocol hai. Iska kaam data packets (datagrams) par **addressing** lagana aur unhe network boundaries ke paar **route** karke destination tak pahunchana hai.
* **Characteristics:**
    * **Connectionless:** Packet bhejne se pehle koi connection nahi banaya jaata. Har packet ko independently treat kiya jaata hai.
    * **Unreliable (Best-Effort):** Ye packet delivery ki guarantee nahi deta. Packet lost ho sakta hai, duplicate ho sakta hai, ya out-of-order pahunch sakta hai. Reliability ki zimmedari iske upar ke layer (jaise TCP) ki hoti hai.


---

### **Transport Layer**
Transport Layer (OSI Layer 4) ka mukhya kaam do alag-alag hosts par chal rahi **applications (processes) ke beech end-to-end communication** pradaan karna hai. Ye Network Layer ki "host-to-host" delivery ko "process-to-process" delivery me badalta hai. Iske do sabse mahatvapurn protocols TCP aur UDP hain.

#### **TCP Protocol**
* **Definition:** TCP (Transmission Control Protocol) ek **connection-oriented** aur **reliable** transport layer protocol hai. Ye Internet par data communication ka sabse common protocol hai.
* **Key Features (Mukhya Visheshtayein):**
    * **Connection-Oriented:** 🤝 Data bhejne se pehle, sender aur receiver ke beech ek connection (3-way handshake ke zariye) sthapit kiya jaata hai.
    * **Reliable (Vishvasniya):** ✅ Ye data delivery ki guarantee deta hai. Ye **acknowledgements** aur **retransmissions** ka istemal karke sunishchit karta hai ki data bina kisi loss ya error ke aur sahi order me pahunche.
    * **Flow Control:** 🚰 TCP, data transfer ki speed ko manage karta hai taaki ek fast sender, ek slow receiver ko data se overwhelm na kar de.
    * **Congestion Control:** 🚦 TCP network me bheed (congestion) ko control karta hai taaki network collapse na ho.
* **Use Cases:** Web browsing (HTTP/HTTPS), Email (SMTP, IMAP), File Transfer (FTP) - yaani har wo jagah jahan data ka 100% correct pahunchna zaroori hai.

---
#### **TCP 3-Way Handshake Process**
* **Purpose:** Client aur server ke beech ek reliable TCP connection sthapit karne ke liye is process ka istemal hota hai.
* **Analogy:** ☎️ Ye ek phone call jaisa hai.
    1.  Aap phone milate hain aur "Hello" kehte hain (SYN).
    2.  Saamne wala phone utha kar kehta hai, "Haan, main sun raha hu. Hello" (SYN-ACK).
    3.  Aap kehte hain, "Theek hai, mujhe aapki awaaz aa gayi" (ACK). Ab baat shuru ho sakti hai.
* **The 3 Steps:**
    1.  **Step 1: SYN (Synchronize):** Client, server ko ek TCP segment bhejta hai jisme **SYN flag '1'** set hota hai. Isse client connection shuru karne ki ichha jatata hai.
    2.  **Step 2: SYN-ACK (Synchronize-Acknowledge):** Server, client ki request ka jawaab ek segment se deta hai jisme **SYN aur ACK dono flags '1'** set hote hain. Isse server kehta hai ki wo connection ke liye taiyaar hai aur client ki request ko acknowledge karta hai.
    3.  **Step 3: ACK (Acknowledge):** Client, server ke SYN-ACK ka jawaab ek segment se deta hai jisme **ACK flag '1'** set hota hai. Iske baad, connection sthapit ho jaata hai aur data transfer shuru ho sakta hai.


---
#### **Services and Segment structure in TCP**
* **Services:** TCP process-to-process communication ke liye **port numbers** ka istemal karta hai. Saath hi, ye reliability, error control, flow control, aur congestion control jaisi services pradaan karta hai.
* **TCP Segment Structure:** TCP me data ki unit ko **Segment** kehte hain. Iske header me kai important fields hote hain:
    
    * **Source Port and Destination Port:** Bhejne aur paane waali application ko pehchante hain.
    * **Sequence Number:** Data ko sahi order me reassemble karne ke liye istemal hota hai.
    * **Acknowledgement Number:** Prapt hue data ko acknowledge karne ke liye istemal hota hai.
    * **Flags (Control Bits):** 6 control bits jo connection ko manage karti hain (e.g., **SYN, ACK, FIN, RST**).
    * **Window Size:** Flow control ke liye istemal hota hai; batata hai ki receiver aur kitna data accept kar sakta hai.
    * **Checksum:** Segment me errors ko detect karne ke liye.

---
#### **TCP Termination**
* **Purpose:** Ek sthapit (established) TCP connection ko dono taraf se aache se band karne ke liye is 4-step process ka istemal hota hai.
* **The 4 Steps:**
    1.  **Step 1 (FIN):** Jo side (client ya server) connection band karna chahti hai, wo ek **FIN (Finish) flag** waala segment bhejti hai.
    2.  **Step 2 (ACK):** Doosri side uss FIN ko **acknowledge (ACK)** karti hai. Is samay, connection half-closed ho jaata hai.
    3.  **Step 3 (FIN):** Jab doosri side bhi data bhejna band karne ke liye taiyaar ho jaati hai, to wo apni taraf se ek **FIN flag** waala segment bhejti hai.
    4.  **Step 4 (ACK):** Pehli side is doosre FIN ko **acknowledge (ACK)** karti hai, aur connection poori tarah se band ho jaata hai.

---
#### **Congestion Control in TCP**
* **Concept:** Ye wo mechanism hai jiska istemal TCP, network ko traffic se overload hone se bachane ke liye karta hai.
* **Mechanism:** TCP ek **congestion window (cwnd)** maintain karta hai, jo batata hai ki ek sender, ACK receive karne se pehle kitna data bhej sakta hai. TCP network ki sthiti ke anusaar is window ka size apne aap adjust karta hai:
    * **Slow Start:** Shuru me, window size tezi se (exponentially) badhta hai.
    * **Congestion Avoidance:** Ek threshold ke baad, window size dheere-dheere (linearly) badhta hai taaki congestion na ho.
    * **Congestion Detection:** Jab koi packet lost hota hai (timeout ya duplicate ACKs se pata chalta hai), to TCP maan leta hai ki network me congestion hai. Wo turant window size ko bahut kam kar deta hai aur fir se dheere-dheere badhana shuru karta hai.

---
#### **UDP Protocol**
* **Definition:** UDP (User Datagram Protocol) ek **connectionless** aur **unreliable** transport layer protocol hai.
* **Key Features:**
    * **Connectionless:** 🚫 Data bhejne se pehle koi handshake nahi hota. Data seedhe bhej diya jaata hai.
    * **Unreliable ("Fire and Forget"):** 👎 Ye data delivery, order, ya error-checking ki koi guarantee nahi deta. Packet lost ho sakta hai.
    * **Fast and Lightweight:** 🚀 Iska header bahut chota (sirf 8 bytes) hota hai aur isme koi extra overhead nahi hota, isliye ye bahut fast hai.
* **Use Cases:** Video/Audio Streaming, Online Gaming, DNS, DHCP - yaani har wo jagah jahan **speed, reliability se zyada zaroori** hai.

---
#### **TCP vs UDP Protocol**
Ye ek behad important interview question hai.

| Feature | TCP (Transmission Control Protocol) | UDP (User Datagram Protocol) |
| :--- | :--- | :--- |
| **Connection Type**| **Connection-Oriented** (Handshake zaroori) | **Connectionless** (Koi handshake nahi) |
| **Reliability** | **Reliable** (Guaranteed, in-order delivery) | **Unreliable** (Koi guarantee nahi) |
| **Speed** | **Slower** (ACKs, flow control ke kaaran) | **Faster** (Koi overhead nahi) |
| **Header Size** | Bada (20 bytes) | Chota (8 bytes) |
| **Flow Control** | Haan, flow control hai. | Nahi, flow control nahi hai. |
| **Error Checking** | Extensive error checking aur recovery. | Basic checksum hai. |
| **Use Cases** | Web (HTTP), Email (SMTP), File Transfer (FTP). | Video Streaming, Gaming, DNS, VoIP. |

---
#### **Other Transport Layer Protocols**

* **Stream Control Transmission Protocol (SCTP)**
    * **Concept:** SCTP ek naya protocol hai jo TCP aur UDP dono ke features ko combine karta hai.
    * **Features:** Ye **message-oriented** (UDP jaisa) hai, lekin **reliable aur ordered delivery** (TCP jaisa) bhi pradaan karta hai. Iski sabse badi khasiyat **multi-streaming** hai, jo "head-of-line blocking" ki samasya ko door karti hai.
* **Datagram Congestion Control Protocol (DCCP)**
    * **Concept:** DCCP, UDP jaise **unreliable service** ke saath TCP jaisa **congestion control** pradaan karta hai. Iska istemal un applications ke liye hota hai jinhe congestion control to chahiye, lekin reliability nahi (jaise streaming media).


---

### **Session Layer**
Session Layer (OSI Layer 5) ka mukhya kaam do applications ke beech ek **connection (session)** ko **sthapit karna (establish), manage karna, aur samapt karna (terminate)** hai. Ise network ka **"dialogue controller"** bhi kehte hain.

#### **Functions of Session Layer**

* **Session Establishment, Maintenance, and Termination (सेशन बनाना, चलाना और खत्म करना):** ☎️
    * Ye do alag-alag machines par chal rahi applications ke beech ek session banata hai, use communication ke dauraan banaye rakhta hai, aur kaam poora hone par use gracefully band kar deta hai.
    * **Analogy:** Ye ek phone call jaisa hai: number dial karna (establishment), baat karna (maintenance), aur phone kaatna (termination).

* **Dialog Control (संवाद नियंत्रण):** 🗣️
    * Ye communication ke flow ki disha (direction) ko manage karta hai. Ye decide karta hai ki communication **simplex** (one-way), **half-duplex** (one-way at a time), ya **full-duplex** (two-way simultaneously) me se kis mode me hoga.

* **Synchronization (सिंक्रनाइज़ेशन):** checkpoint
    * Ye is layer ka sabse mahatvapurn kaam hai. Ye ek lambe data stream ke beech me **checkpoints (synchronization points)** daal deta hai.
    * **Fayda:** Agar ek bahut badi file transfer ke dauraan network me koi gadbadi (crash) ho jaati hai, to poori file ko shuru se bhejne ki zaroorat nahi padti. Transfer ko aakhri safal (successful) checkpoint se **resume** kiya jaa sakta hai.
    * **Analogy:** Ek video game me checkpoints par **progress save** karna.

* **Token Management (टोकन मैनेजमेंट):** 🎟️
    * Kuch communication modes me, ye sunishchit karne ke liye ki dono parties ek hi samay par ek hi critical operation na karein, token management ka istemal hota hai. Jiss party ke paas "token" hota hai, sirf wahi uss operation ko perform kar sakti hai.

---
### **Presentation Layer**
Presentation Layer (OSI Layer 6) network ka **"translator"** kehlata hai. Iska mukhya kaam ye sunishchit karna hai ki ek system ke application layer dwara bheja gaya data doosre system ka application layer samajh sake.

#### **Services Provided by Presentation Layer**

* **Translation (अनुवाद):** 🔄
    * Alag-alag computers alag-alag character encoding schemes ka istemal kar sakte hain (jaise ASCII aur EBCDIC). Presentation Layer, data ko sender ke format se ek common network format me, aur fir receiver ke format me **translate** karta hai.

* **Encryption and Decryption (एन्क्रिप्शन और डिक्रिप्शन):** 🔐
    * Ye communication ko secure banane ke liye data ko **encrypt** (sender side par) aur **decrypt** (receiver side par) karta hai. Isse data ki confidentiality bani rehti hai.

* **Compression and Decompression (संपीड़न):** 📦
    * Ye network par bheje jaane waale bits ki sankhya ko kam karne ke liye data ko **compress** karta hai. Isse bandwidth bachti hai aur data transfer tez hota hai. Receiver side par data ko wapas decompress kar diya jaata hai.

---
#### **Secure Socket Layer (SSL)**
* **Concept:** SSL ek cryptographic protocol hai jiska istemal internet par bheje jaane waale data ko **encrypt** karne ke liye kiya jaata tha. Ye **TLS (Transport Layer Security)** ka purana version hai.
* **OSI Layer:** Waise to iska kaam (encryption) Presentation Layer ka hai, lekin TCP/IP model me ye Application aur Transport layer ke beech me kaam karta hai.
* **Status:** 😥 SSL ab **purana (outdated) aur insecure** maana jaata hai. Iski jagah ab hamesha **TLS** ka istemal hota hai. Ye HTTPS me 'S' ka kaaran hai.

---
#### **Remote Procedure Call (RPC)**
* **Concept:** 📞 RPC ek protocol hai jiske zariye ek program, network par maujood kisi doosre computer par chal rahe ek **procedure (function)** ko aise call kar sakta hai jaise wo ek **local function** ho.
* **OSI Layer:** RPC ek Application Layer protocol hai, lekin iska data representation (jaise alag-alag machine architectures ke beech `int` ya `float` ko aaps me samjhana) ka kaam Presentation Layer se juda hai.

---
#### **Point-to-Point Tunneling Protocol (PPTP)**
* **Concept:** PPTP, **Virtual Private Networks (VPNs)** banane ka ek purana network protocol hai.
* **Mechanism:** Ye ek public network (jaise Internet) par ek private, encrypted **"tunnel"** banata hai jiske through data securely travel karta hai.
* **Security Status:** 👎 PPTP me kai security kamzoriyan paayi gayi hain, isliye ab ise **insecure** maana jaata hai. Modern VPNs iski jagah OpenVPN ya IPSec jaise protocols ka istemal karte hain.

---
#### **Multipurpose Internet Mail Extensions (MIME)**
* **Concept:** 📧 MIME ek internet standard hai jo email ke format ko extend karta hai taaki wo simple ASCII text ke alawa doosre tarah ke data ko bhi support kar sake.
* **Functions:** MIME ki vajah se hi hum emails me:
    * Alag-alag languages (character sets) me text bhej sakte hain.
    * **Attachments** (jaise images, audio, video, PDF files) bhej sakte hain.
    * Ek hi message me multiple parts bhej sakte hain.
* **OSI Layer:** Data ko present karne ke liye ek standard format define karna, Presentation Layer ka hi kaam hai.

---

### **Application Layer**
Application Layer (OSI Layer 7) OSI model ki **sabse upar (topmost)** wali layer hai, jo end-user ke sabse kareeb hoti hai. Ye layer user applications (jaise web browser, email client) ko network services access karne ke liye ek **interface** pradaan karti hai. Hum network ka istemal isi layer ki vajah se kar paate hain.

#### **Client-Server Model**
* **Concept:** 🏢 Ye ek application architecture hai jisme kaam ko do hisso me baanta jaata hai:
    1.  **Server:** Ek powerful computer jo ek resource ya service (jaise website ya database) ko provide karta hai aur requests ka intezaar karta hai.
    2.  **Client:** Ek computer ya program jo server se service ke liye **request** karta hai.
* **Mechanism:** Client hamesha communication shuru karta hai, aur server us request ka **response** deta hai. Internet ki zyadaatar services (jaise web, email) isi model par kaam karti hain.
* **Analogy:** 🧠 Ek **restaurant**. Customers (`Clients`) order (request) karte hain, aur restaurant (`Server`) unhe khana (response) serve karta hai.

---
#### **World Wide Web (WWW)**
* **Definition:** 🕸️ World Wide Web (ya Web), internet par maujood aapas me jude hue (interlinked) **hypertext documents** aur doosre web resources ka ek global system hai.
* **Important Point:** Internet aur WWW ek cheez nahi hain. **Internet** ek global network (infrastructure) hai, jabki **WWW** us infrastructure par chalne waali ek **application/service** hai.
* **Key Components:**
    * **Web Browser (Client):** Jaise Chrome, Firefox.
    * **Web Server:** Jaha websites host ki jaati hain.
    * **HTTP/HTTPS (Protocol):** Browser aur server ke beech communication ke niyam.
    * **URL (Address):** Har web resource ka unique address.

---
#### **E-Mail**
* **Concept:** 📧 Email (Electronic Mail) internet ki sabse purani aur sabse popular services me se ek hai. Ye users ko electronic messages bhejne aur prapt karne ki suvidha deta hai.
* **Components:**
    * **User Agent:** Wo software jiska istemal karke user email likhta aur padhta hai (e.g., Microsoft Outlook, Gmail ka web interface).
    * **Mail Server:** Ye server emails ko store aur aage forward karne ka kaam karte hain.
    * **Protocols:** SMTP, POP3, IMAP.

---
#### **Content Distribution Network (CDN)**
* **Definition:** 🚀 CDN, poori duniya me faile hue proxy servers ka ek **geographically distributed network** hota hai.
* **Purpose:** Iska mukhya kaam websites ki **performance aur availability** ko badhana hai.
* **How it works:** Jab aap kisi website ka content (jaise image ya video) request karte hain, to CDN us request ko uss server ke paas bhejta hai jo aapke **geographically sabse nazdeek** ho. Isse data ko kam doori tay karni padti hai, jisse **latency (deri) kam** ho jaati hai aur website jaldi load hoti hai.
* **Analogy:** 🚚 Amazon ka ek central warehouse hone ke bajaye, har bade sheher me chote-chote warehouses hona. Jab aap order karte hain, to saaman aapke sabse nazdeek waale warehouse se aata hai, jisse delivery fast ho jaati hai.

---
### **Application Layer Protocols**

#### **Domain Name System (DNS)**
* **Purpose:** 📖 DNS ko **"Internet ka Phonebook"** kehte hain. Iska kaam human-readable **domain names** (jaise `www.google.com`) ko computer-readable **IP addresses** (jaise `172.217.167.78`) me **translate** karna hai.

---
#### **File Transfer Protocol (FTP)**
* **Purpose:** 📂 FTP ek standard network protocol hai jiska istemal ek client aur server ke beech computer **files ko transfer** karne ke liye hota hai.
* **Mechanism:** Ye do alag-alag connections ka istemal karta hai: ek **control connection** (commands ke liye) aur ek **data connection** (asal file transfer ke liye).
* **Security:** FTP data ko **cleartext** me bhejta hai, isliye ye insecure hai. Iske secure alternatives **SFTP** aur **FTPS** hain.

---
#### **Simple Mail Transfer Protocol (SMTP)**
* **Purpose:** 📤 SMTP ka istemal sirf email **bhejne (sending)** ke liye hota hai - ek email client se mail server tak, aur ek mail server se doosre mail server tak.

---
#### **Simple Network Management Protocol (SNMP)**
* **Purpose:** 📡 SNMP ka istemal network administrators dwara network par maujood devices (jaise routers, switches, servers) ko **monitor aur manage** karne ke liye kiya jaata hai. Isse network ki health check ki jaa sakti hai aur problems ko dhoondha jaa sakta hai.

---
#### **HyperText Transfer Protocol (HTTP)**
* **Purpose:** 🌐 HTTP, World Wide Web par data communication ki neev (foundation) hai. Ye batata hai ki web browsers aur web servers aapas me kaise request aur response messages exchange karenge.
* **Characteristic:** Ye ek **stateless** protocol hai, yaani server har request ko ek nayi request maanta hai aur pichli requests ko yaad nahi rakhta.

---
#### **HyperText Transfer Protocol Secure (HTTPS)**
* **Purpose:** 🔒 HTTPS, HTTP ka **secure version** hai.
* **Mechanism:** Ye browser aur server ke beech ke communication ko **SSL/TLS (Secure Sockets Layer/Transport Layer Security)** protocol ka istemal karke **encrypt** kar deta hai. Isse aapka data (jaise passwords, credit card details) network par safe rehta hai.

---
#### **Post Office Protocol v3 (POP3)**
* **Purpose:** 📥 POP3 ek email protocol hai jiska istemal email client dwara mail server se emails ko **retrieve (prapt)** karne ke liye hota hai.
* **Mechanism:** Aam taur par, POP3 emails ko aapke local computer par **download** kar leta hai aur fir unhe **server se delete** kar deta hai. Ye "offline" email access ke liye aacha hai.

---
#### **Internet Message Access Protocol (IMAP)**
* **Purpose:** 📨 IMAP bhi emails ko mail server se **retrieve** karne ke liye hi use hota hai.
* **Mechanism:** POP3 ke vipreet, IMAP emails ko **server par hi manage** karta hai. Jab aap email padhte ya delete karte hain, to changes seedhe server par hote hain. Iska fayda ye hai ki aapke saare emails aapke sabhi devices (phone, laptop) par **synchronized** rehte hain. Gmail aur Outlook jaisi modern services IMAP ka istemal karti hain.

---

### **Network Security and Quality of Service**

#### **Authentication**
* **Definition:** 👤 Authentication, kisi user ya device ki **pehchaan ko verify (satyapit)** karne ka process hai. Ye is sawaal ka jawaab deta hai, "Kya aap wahi hain jo aap hone ka dawa kar rahe hain?"
* **Factors of Authentication (Pramanikaran ke Kaarak):**
    1.  **Something you know (Jo aap jaante hain):** 🧠 Jaise **Password** ya PIN.
    2.  **Something you have (Jo aapke paas hai):** 📱 Jaise **OTP token**, smart card, ya aapka mobile phone.
    3.  **Something you are (Jo aap hain):** 🖐️ Jaise **Fingerprint**, Face ID, ya Retina scan (Biometrics).
* **Multi-Factor Authentication (MFA):** Inme se do ya do se zyada factors ka ek saath istemal karne ko MFA kehte hain. Ye single-factor authentication (jaise sirf password) se kahin zyada secure hota hai.

---
#### **Encryption**
* **Definition:** 🔐 Encryption, readable data (**Plaintext**) ko ek unreadable format (**Ciphertext**) me convert karne ka process hai taaki uski **confidentiality (gopniyata)** bani rahe.
* **Purpose:** Iska mukhya uddeshya (goal) data ko unauthorized logon se bachana hai, khaas kar jab data ek network par travel kar raha ho. Sirf jiske paas sahi **decryption key** hoti hai, wahi use wapas readable format me laa sakta hai.
* **Analogy:** Ek secret code me message bhejna, jise sirf wahi samajh sakta hai jiske paas code ko decode karne ki key ho.

---
#### **Firewalls**
* **Definition:** 🛡️ Firewall ek network security device hai jo ek **trusted internal network** aur ek **untrusted external network** (jaise Internet) ke beech ek **barrier (deewar)** ki tarah kaam karta hai.
* **Function:** Ye pehle se define kiye gaye security rules ke aadhar par aane aur jaane waale network traffic ko monitor karta hai aur use **allow ya block** karta hai.

---
#### **MAC Address Filtering**
* **Definition:** 💻 MAC Address Filtering ek security method hai jisme ek network device (jaise Wi-Fi router) ko is tarah configure kiya jaata hai ki wo sirf **specific MAC addresses** waale devices ko hi network se judne de.
* **How it works:** Administrator ek list banata hai:
    * **Whitelist:** Sirf is list me maujood MAC addresses ko network access milega.
    * **Blacklist:** Is list me maujood MAC addresses ko block kar diya jaayega.
* **Limitation:** 😥 Ye ek basic security layer hai, lekin poori tarah se surakshit nahi hai kyunki attackers **MAC address ko spoof (nakal)** kar sakte hain.

---
### **QoS (Quality of Service)**

#### **What is QoS and Multimedia?**
* **QoS (Quality of Service):** 🏆 QoS, network me istemal hone waali un technologies ka set hai jinka kaam network traffic ko **manage karna** aur **prioritize karna** hai. Iska goal zaroori aur time-sensitive applications ke liye ek certain level ki performance guarantee karna hai.
* **Why for Multimedia?** 🎬 Multimedia applications (jaise Video Streaming, Online Gaming, VoIP calls) network ki samasyaon ke prati bahut **sensitive** hoti hain:
    * **Delay (Latency):** Data ko source se destination tak pahunchne me lagne waala samay.
    * **Jitter:** Delay me hone wala utaar-chadhav (variation).
    * **Packet Loss:** Transmission ke dauraan packets ka gum ho jaana.
    * QoS in samasyaon ko kam karke in applications ke liye ek **smooth user experience** sunishchit karta hai.

---
#### **Techniques for achieving QoS**
* **Classification and Marking:** Alag-alag tarah ke traffic ko pehchanna aur unhe priority ke hisaab se "mark" karna (e.g., voice traffic ko high priority mark karna).
* **Queuing:** Jab ek router par congestion hota hai, to wo packets ko queues me daal deta hai. QoS, **Priority Queuing (PQ)** ya **Weighted Fair Queuing (WFQ)** jaise algorithms ka istemal karke ye decide karta hai ki kis queue ke packet ko pehle bhejna hai.
* **Congestion Avoidance:** Queue ke poori tarah bhar jaane se pehle hi, kam zaroori packets ko proactively drop karna taaki congestion se bacha jaa sake (e.g., **Random Early Detection - RED**).
* **Traffic Shaping/Policing:** Network me bheje jaane waale traffic ki speed (rate) ko control karna.

---
#### **Congestion Control in Computer Networks**
* **Definition:** 🚦 Congestion Control wo mechanism hai jiska istemal network me enter hone waale data ki maatra ko control karne ke liye hota hai, taaki network **overload (congested)** na ho jaaye.
* **Congestion Control vs. Flow Control:**
    * **Flow Control:** Ek **single sender aur single receiver** ke beech kaam karta hai.
    * **Congestion Control:** **Poore network** ke liye kaam karta hai.

---
#### **Token Bucket**
* **Concept:** 🪣 Ye traffic shaping ka ek algorithm hai.
* **Analogy:** Ek baalti (bucket) jisme ek fixed rate se tokens girte rehte hain.
* **Mechanism:**
    1.  Ek "bucket" tokens ko hold karta hai. Tokens ek constant rate se bucket me add hote rehte hain.
    2.  Ek packet ko transmit karne ke liye, system ko us packet ke size ke anusaar bucket se tokens nikalne padte hain.
    3.  Agar bucket me paryaapt (sufficient) tokens nahi hain, to packet ko intezaar karna padta hai.
* **Benefit:** Ye **bursty traffic** (achanak se aane waale high traffic) ko allow karta hai. Agar bucket tokens se bhara hua hai, to ek bada data burst ek saath bheja jaa sakta hai.

---
#### **Leaky Bucket**
* **Concept:** 💧 Ye bhi traffic shaping ka ek algorithm hai, jiska focus ek constant output rate banana hota hai.
* **Analogy:** Ek baalti jiske neeche ek chota sa chhed (hole) hai.
* **Mechanism:**
    1.  Aane waale packets (paani) ko ek finite queue (bucket) me daala jaata hai.
    2.  Bucket se data ek **constant rate** se "leak" hota hai, chahe data kitni bhi tezi se aa raha ho.
    3.  Agar packet aane par bucket pehle se hi bhara hua hai, to packet ko **discard** kar diya jaata hai (paani baahar gir jaata hai).
* **Benefit:** Ye ek bilkul **smooth, constant output rate** sunishchit karta hai aur burstiness ko khatam kar deta hai.

---
----
### **I. Network Fundamentals**

**Q: What is a computer network and what are its benefits? (Computer network kya hai aur iske fayde kya hain?)**
A: Ek **computer network** 💻, aapas me jude hue (interconnected) computing devices ka ek collection hai jo data exchange kar sakte hain aur resources share kar sakte hain.
**Iske mukhya fayde (benefits) hain:**
* **Resource Sharing:** 📠 Printer, scanner, aur storage jaise hardware ko share karna.
* **Information Sharing:** 📂 Files aur data ko centrally store karke aasaani se access karna.
* **Communication:** 💬 Email, video conferencing, aur instant messaging ke zariye aasaan communication.
* **Cost Saving:** Mehenge software aur hardware ko share karke paiso ki bachat karna.

---
**Q: What are nodes and links? (Nodes aur links kya hain?)**
A:
* **Nodes (नोड्स):** 🌐 Network se jude hue individual devices **nodes** kehlate hain. **Example:** Computer, printer, switch, router.
* **Links (लिंक्स):** 🔗 Wo communication pathways (raaste) jo nodes ko aapas me jodte hain, **links** kehlate hain. Ye **wired** (jaise Ethernet cable) ya **wireless** (jaise Wi-Fi) ho sakte hain.

---
**Q: What are the different types of networks (LAN, MAN, WAN)? (Alag-alag prakaar ke networks kya hain?)**
A: Networks ko unke geographical area ke aadhar par mukhya roop se teen prakaar me baanta jaata hai:
1.  **LAN (Local Area Network):** 🏡 Ek chote area (jaise ek ghar, office, ya ek building) tak seemit rehta hai. Iski speed bahut tez hoti hai.
2.  **MAN (Metropolitan Area Network):** 🏙️ Ek poore sheher (city) ko cover karta hai. Ye kai LANs ko aapas me jodkar banta hai.
3.  **WAN (Wide Area Network):** 🌍 Ye ek bahut bade geographical area (jaise ek desh ya poori duniya) ko cover karta hai. **Internet** sabse bada WAN hai.

---
**Q: What is internetworking? (Internetworking kya hai?)**
A: **Internetworking**, do ya do se zyada alag-alag computer networks ko aapas me jodkar ek bada network (an internetwork) banane ka process hai. Ye kaam **routers** ki madad se kiya jaata hai. **Internet**, internetworking ka sabse bada aur sabse prasiddh (famous) example hai.

---
**Q: What is network topology? Define different types of network topology. (Network topology kya hai? Iske prakaar batao.)**
A: **Network Topology**, network me nodes (devices) aur links (connections) ke **physical ya logical arrangement (layout)** ko kehte hain.
* **Bus Topology:** Sabhi devices ek single central cable (bus) se jude hote hain.
* **Star Topology:** Sabhi devices ek central device (hub ya switch) se jude hote hain. Ye aajkal sabse common LAN topology hai.
* **Ring Topology:** Sabhi devices ek circle (ring) me jude hote hain.
* **Mesh Topology:** Har device baaki sabhi devices se directly juda hota hai. Ye sabse reliable hai.
* **Tree Topology:** Ye star aur bus topologies ka combination hai.

---
**Q: What is the difference between synchronous and asynchronous transmission? (Synchronous aur asynchronous transmission me kya antar hai?)**
A:
* **Synchronous Transmission:** ⏱️ Isme data, **blocks ya frames** ke roop me ek **continuous stream** me bheja jaata hai. Sender aur receiver ke beech ek common clock signal hota hai jisse data ko synchronize kiya jaata hai. Ye **fast** hota hai aur bade amount of data ke liye aacha hai.
* **Asynchronous Transmission:** ➡️ Isme data **ek samay me ek byte** bheja jaata hai. Har byte ke saath ek **start bit** aur ek **stop bit** hoti hai taaki receiver ko pata chale ki byte kahan shuru aur khatam ho raha hai. Ye **slow** hai lekin simple hai.

---
**Q: What is latency and how can it be minimized? (Latency kya hai aur ise kaise kam kiya jaa sakta hai?)**
A: **Latency** 🕒, ek data packet ko uske source se destination tak travel karne me lagne waale **time delay** ko kehte hain. Ise aam bhasha me "ping time" bhi kaha jaata hai.
**Ise kam karne ke tarike:**
* Tez transmission media ka istemal karna (jaise fiber optics).
* Beech ke network devices (routers) ki sankhya kam karna.
* Content Delivery Network (CDN) ka istemal karke data ko user ke geographically nazdeek laana.

---
**Q: Explain the term Jitter. (Jitter shabd ko samjhaiye.)**
A: **Jitter** 📉, packets ke aane me hone waale **delay (latency) me aniyamit utaar-chadhav (variation)** ko kehte hain.
**Example:** Agar ek video call me kuch data packets 20ms me aa rahe hain aur kuch 100ms me, to is variation (jitter) ke kaaran audio aur video **choppy (kat-kat kar)** aayegi. Ye real-time applications (jaise online gaming, VoIP) ke liye ek badi samasya hai.

---
**Q: What are clients and servers in a network? (Network me clients aur servers kya hain?)**
A:
* **Server (सर्वर):** 🖥️ Ek server ek powerful computer ya program hota hai jo network par doosre devices ko **service pradaan (provide)** karta hai. **Example:** Web server (websites host karta hai), File server (files store karta hai).
* **Client (क्लाइंट):** 💻 Ek client ek computer ya program hota hai jo server se **service ke liye request** karta hai. **Example:** Aapka web browser ek client hai jo web server se webpage request karta hai.

---
**Q: What is a server farm? (Server farm kya hai?)**
A: Ek **server farm** 🏢, computer servers ka ek bahut bada collection hota hai jo aam taur par ek **data center** me rakha jaata hai. Iska istemal bade paimane par computing power aur storage pradaan karne ke liye hota hai, jo ek single server ke bas ki baat nahi hai.

---
**Q: What are unicasting, multicasting, broadcasting, and anycasting? (Ye sab kya hain?)**
A: Ye data transmission ke alag-alag tarike hain:
* **Unicasting (One-to-One):** 🚶‍♂️→🚶‍♀️ Ek sender se ek single receiver tak.
* **Broadcasting (One-to-All):** 📢 Ek sender se network par maujood **sabhi** devices tak.
* **Multicasting (One-to-Many):** 🗣️→👥 Ek sender se ek **specific group** of interested receivers tak.
* **Anycasting (One-to-Nearest):** 📍 Ek sender se receivers ke ek group me se **sabse nazdeek (geographically ya network-wise)** waale receiver tak.

---
**Q: What is the difference between Circuit Switching and Packet Switching? (Circuit Switching aur Packet Switching me kya antar hai?)**

| Feature | Circuit Switching | Packet Switching |
| :--- | :--- | :--- |
| **Path (रास्ता)** | Data bhejne se **pehle** ek **dedicated physical path** banaya jaata hai. | Koi dedicated path nahi hota. Data ko **packets** me tod kar bheja jaata hai. |
| **Resources**| Resources (bandwidth) poore session ke liye **reserved** rehte hain. | Resources ko kai users ke beech **share** kiya jaata hai. |
| **Use Case** | Traditional Telephone Network (PSTN). | **Internet** (Web, Email, etc.). |
| **Efficiency**| **Kam efficient**, kyunki resources idle reh sakte hain. | **Bahut efficient**, kyunki resources hamesha use hote rehte hain. |

---


### **II. Network Models (OSI & TCP/IP)**

**Q: Describe the OSI Reference Model. Why is it important? (OSI Reference Model ka varnan karein. Ye zaroori kyun hai?)**
A: **OSI (Open Systems Interconnection) Model** 🌐, International Organization for Standardization (ISO) dwara develop kiya gaya ek **7-layer conceptual framework** hai. Ye ek communication system ke functions ko standard tarike se describe karta hai.
Ye isliye zaroori hai kyunki:
* **Reference Model:** Ye ek **reference model** hai, na ki ek practical implementation. Ye networking ke concepts ko aasaani se **samjhne aur sikhane** me madad karta hai.
* **Standardization:** Ye alag-alag manufacturers ke network devices ke beech **interoperability (aapsi talmel)** sunishchit karne ke liye ek standard pradaan karta hai.
* **Troubleshooting:** Ye network problems ko **chote-chote, manageable hisso (layers)** me todkar troubleshoot karna aasan bana deta hai.

---
**Q: Define the 7 different layers of the OSI Reference Model. (OSI Model ke 7 layers ko define karein.)**
A: OSI model ke 7 layers (top to bottom) hain:
* **Layer 7: Application Layer:** 👩‍💻 User ke sabse kareeb. Ye applications ko network services pradaan karta hai. (e.g., HTTP, FTP).
* **Layer 6: Presentation Layer:** 🎨 Data ko ek standard format me **translate** karta hai. Encryption aur compression bhi yahan hota hai.
* **Layer 5: Session Layer:** 📞 Do devices ke beech **connection (session)** ko sthapit, manage, aur terminate karta hai.
* **Layer 4: Transport Layer:** 🚚 **End-to-end reliable data delivery** aur error control ke liye zimmedar hai. (e.g., TCP, UDP).
* **Layer 3: Network Layer:** 🗺️ **Routing aur logical addressing (IP Address)** ka kaam karta hai.
* **Layer 2: Data Link Layer:** 🔗 **Physical addressing (MAC Address)** aur frames me data ko organize karta hai.
* **Layer 1: Physical Layer:** 🔌 Raw bits ko **physical medium** (jaise cables, radio waves) par transmit karta hai.

---
**Q: Name the software layers (User support layers) in the OSI model. (OSI model me software layers ke naam batao.)**
A: Upper layers ko software layers kaha jaata hai kyunki ye software me implement hoti hain aur user se zyada interact karti hain.
* **Application Layer (Layer 7)**
* **Presentation Layer (Layer 6)**
* **Session Layer (Layer 5)**

---
**Q: Name the hardware layers (Network support layers) in the OSI model. (OSI model me hardware layers ke naam batao.)**
A: Lower layers ko hardware layers kaha jaata hai kyunki ye data ke physical transmission se zyada deal karti hain.
* **Network Layer (Layer 3)**
* **Data Link Layer (Layer 2)**
* **Physical Layer (Layer 1)**

**Note:** Transport Layer (Layer 4) in dono groups ke beech ek **bridge** ka kaam karta hai.

---
**Q: In which OSI layer are the header and trailer added? (OSI ki kis layer me header aur trailer joda jaata hai?)**
A: **Data Link Layer (Layer 2)** me. Ye Network Layer se aane waale packet ko leta hai aur uske aage ek **Header** (jisme source aur destination MAC address hota hai) aur peeche ek **Trailer** (jisme error-checking code jaise CRC hota hai) jod kar ek **Frame** banata hai.

---
**Q: What is the use of the Data Link Layer? (Data Link Layer ka kya istemal hai?)**
A: Data Link Layer ka mukhya kaam ek physical link par **node-to-node reliable data transfer** pradaan karna hai. Iske functions hain:
* **Framing:** Bits ko frames me organize karna.
* **Physical Addressing:** Frames me MAC addresses jodna.
* **Error Control:** Transmission me hui galtiyon ka pata lagana.
* **Flow Control:** Data transfer ki speed ko manage karna.
* **Access Control:** Shared media par ye decide karna ki kaun sa device kab data bhejega.

---
**Q: Define the functionality of the OSI session layer. (OSI session layer ki functionality define karein.)**
A: Session Layer ka mukhya kaam do applications ke beech ek **session (connection)** ko **sthapit karna (establish), manage karna, aur samapt karna (terminate)** hai. Iske alawa, ye **dialog control** (communication one-way hoga ya two-way) aur **synchronization** (data me checkpoints lagana) ka kaam bhi karta hai.

---
**Q: What is the position of the transmission media in the OSI model? (OSI model me transmission media ki position kya hai?)**
A: Transmission media (jaise cables, fiber optics, ya radio waves) OSI model me **Physical Layer (Layer 1) ke neeche** aate hain. Layer 1, data ko in media par *kaise* transmit karna hai, ye define karta hai, lekin media khud model ka hissa nahi hai, balki wo physical infrastructure hai jispar model kaam karta hai.

---
**Q: Describe the TCP/IP Reference Model. (TCP/IP Reference Model ka varnan karein.)**
A: **TCP/IP (Transmission Control Protocol/Internet Protocol) model** ek **practical model** hai jispar poora **Internet** aadharit hai. OSI model ke vipreet, ye ek conceptual framework nahi, balki ek working protocol suite hai. Isme aam taur par **4 layers** hoti hain.

---
**Q: Define the 4 different layers of the TCP/IP Reference Model. (TCP/IP model ke 4 layers ko define karein.)**
A:
1.  **Application Layer:** Ye OSI model ki Application, Presentation, aur Session layers ke kaam ko combine karti hai. (e.g., HTTP, FTP, SMTP).
2.  **Transport Layer:** Ye process-to-process communication aur reliability ke liye zimmedar hai. (e.g., TCP, UDP).
3.  **Internet Layer:** Ye logical addressing (IP) aur routing ke liye zimmedar hai. (e.g., IP, ICMP).
4.  **Network Access Layer (ya Link Layer):** Ye OSI model ki Data Link aur Physical layers ke kaam ko combine karti hai.

---
**Q: Differentiate the OSI Reference Model from the TCP/IP Reference Model. (OSI aur TCP/IP model me antar batao.)**

| Feature | OSI Model | TCP/IP Model |
| :--- | :--- | :--- |
| **Layers** | Isme **7 layers** hain. | Isme **4 layers** hain. |
| **Model Type**| Ye ek **conceptual aur reference model** hai. | Ye ek **practical aur implementation model** hai. |
| **Development** | Ise ISO (International Standard Organization) ne banaya. | Ise DoD (U.S. Department of Defense) ne banaya. |
| **Approach** | Ye **"model-first"** approach hai (model pehle bana, protocols baad me). | Ye **"protocol-first"** approach hai (protocols pehle bane, model baad me). |
| **Protocol Dependency**| Protocol-independent hai. | Protocol-dependent hai. |
| **Usage** | Networking ko samjhne aur sikhane ke liye use hota hai. | **Internet** ispar aadharit hai. |

---

### **III. IP Addressing & Subnetting**

**Q: What is an IP address? What are its different types? (IP address kya hai? Iske prakaar kya hain?)**
A: Ek **IP (Internet Protocol) address** 📍, ek computer network se jude har device ko assign kiya gaya ek unique **numerical label** hota hai. Iske do mukhya kaam hain:
1.  **Identification:** Device ki pehchaan karna.
2.  **Location Addressing:** Network me device ki location batana.

Iske do mukhya prakaar (versions) hain:
* **IPv4 (Internet Protocol version 4):** Ye 32-bit ka address hota hai.
* **IPv6 (Internet Protocol version 6):** Ye 128-bit ka address hota hai.

---
**Q: What is an IPv4 address? What are the different classes of IPv4? (IPv4 address kya hai? Iske classes kya hain?)**
A: Ek **IPv4 address** 32-bit ka numeric address hota hai, jise aam taur par 4 octets (8-bit numbers) ke roop me, dots se alag karke likha jaata hai (e.g., `192.168.1.1`).
Purane samay me, IPv4 addresses ko 5 classes me baanta jaata tha (Classful Addressing):
* **Class A:** Bahut bade networks ke liye (e.g., bade multinational corporations).
* **Class B:** Medium se bade networks ke liye (e.g., universities).
* **Class C:** Chote networks ke liye (e.g., small businesses).
* **Class D:** Multicasting ke liye reserved.
* **Class E:** Experimental (prayogik) use ke liye reserved.

**Note:** Aajkal **Classless Addressing (CIDR)** ka istemal hota hai, jisse IP addresses ki barbadi kam hoti hai.

---
**Q: What are Private and Special IP addresses? (Private aur Special IP addresses kya hain?)**
A:
* **Private IP Addresses:** 🏠 Ye IP addresses ke aise blocks hain jinhe **private networks (LAN)**, jaise aapke ghar ya office ke network, me istemal karne ke liye reserve kiya gaya hai. Ye addresses Internet par routable nahi hote. Inke ranges hain:
    * `10.0.0.0` to `10.255.255.255`
    * `172.16.0.0` to `172.31.255.255`
    * `192.168.0.0` to `192.168.255.255`
* **Special IP Addresses:** ⭐️ Ye kuch aise IP addresses hain jinka khaas matlab hota hai:
    * **`127.0.0.1` (Loopback Address):** Ye hamesha **local machine (localhost)** ko refer karta hai. Iska istemal network applications ko usi machine par test karne ke liye hota hai.
    * **`0.0.0.0` (Unspecified Address):** Ye ek non-routable address hai jo aam taur par ek device tab use karta hai jab use abhi tak koi IP address assign nahi hua ho.

---
**Q: What is the difference between a static and a dynamic IP address? (Static aur dynamic IP address me kya antar hai?)**
A:
* **Static IP:** ⚙️ Ek static IP address, ek device ko **manually assign** kiya jaata hai aur ye **kabhi badalta nahi**. Iska istemal aam taur par servers, printers, aur routers ke liye hota hai, jinhe hamesha ek hi address par available rehna hota hai.
* **Dynamic IP:** 🔄 Ek dynamic IP address, ek **DHCP server** dwara ek device ko **automatically aur temporarily** assign kiya jaata hai. Jab aap apne ghar ke Wi-Fi se connect hote hain, to aapke phone ya laptop ko aam taur par ek dynamic IP milta hai.

---
**Q: What is a MAC address and how is it related to a NIC (Network Interface Card)? (MAC address kya hai aur ye NIC se kaise juda hai?)**
A:
* **MAC Address (Media Access Control Address):** 💳 Ye ek **48-bit ka unique hardware identifier** hai jo kisi bhi network device ke **NIC (Network Interface Card)** ko uske manufacturer dwara assign kiya jaata hai. Ye ek **physical address** hai.
* **Relation to NIC:** MAC address, NIC ke hardware me **permanently burn (embed)** kiya jaata hai. Duniya me har NIC ka ek unique MAC address hota hai. Ye Data Link Layer (Layer 2) par kaam karta hai.

---
**Q: Differentiate the MAC address from the IP address. (MAC address aur IP address me antar batao.)**

| Feature | MAC Address | IP Address |
| :--- | :--- | :--- |
| **Layer** | Layer 2 (Data Link Layer) | Layer 3 (Network Layer) |
| **Address Type**| **Physical / Hardware** Address | **Logical** Address |
| **Size** | 48-bit (e.g., `00:1A:2B:3C:4D:5E`) | 32-bit (IPv4) or 128-bit (IPv6) |
| **Scope** | Ek hi **local network (LAN)** me kaam karta hai. | Alag-alag networks ke beech (**Internet**) kaam karta hai. |
| **Changeability**| **Permanent** hota hai (hardware me burned-in). | **Temporary** ho sakta hai (dynamic IP). |
| **Assignment** | Manufacturer dwara assign kiya jaata hai. | Network administrator ya ISP dwara assign kiya jaata hai. |

---
**Q: What is a subnet? (Subnet kya hai?)**
A: Ek **subnet** (sub-network) 🔪, ek bade IP network ka ek **chota, logical subdivision** hota hai. Ek bade network ko kai chote subnets me todne se network management aasan ho jaata hai, security behtar hoti hai, aur unnecessary network traffic kam hota hai.

---
**Q: What is a subnet mask and how is it used? (Subnet mask kya hai aur iska istemal kaise hota hai?)**
A: Ek **Subnet Mask** 🎭 ek 32-bit ka number hai jo ek IP address ke **network portion** ko **host portion** se alag karne ke liye istemal hota hai.
* **How it's used:** Ek computer, apne IP address aur subnet mask ke beech ek bitwise **`AND`** operation karke ye pata lagata hai ki wo kis network se juda hai. Isse use ye decide karne me madad milti hai ki data packet ko local network me hi bhejna hai ya default gateway (router) ko.

---
**Q: What is CIDR (Classless Inter-Domain Routing)? (CIDR kya hai?)**
A: **CIDR** ✍️, IP addresses ko allocate aur route karne ka modern tarika hai. Isne purane classful system ko replace kar diya hai. CIDR me **slash notation** (e.g., `/24`) ka istemal hota hai, jo network prefix ki length batata hai. Isse IP address blocks ko zaroorat ke hisaab se **flexible size** me baanta jaa sakta hai, jisse IP addresses ki barbadi kam hoti hai.

---
**Q: Given the IP address 192.168.10.0/24, how many subnets and hosts per subnet can be created if you use a subnet mask of 255.255.255.192? (Diye gaye IP aur subnet mask se kitne subnets aur hosts banenge?)**
A: Aaiye isse step-by-step solve karte hain.

1.  **Analyze the Information (Jaankari ka vishleshan):**
    * Original Network: `192.168.10.0/24`. Yahan `/24` ka matlab hai ki shuru ke 24 bits network ke liye hain.
    * New Subnet Mask: `255.255.255.192`. Iska binary hota hai:
      `11111111.11111111.11111111.11000000`.
    * Is naye mask me **26** ones (`1`s) hain. Iska matlab naya prefix `/26` hai.

2.  **Calculate Number of Subnets (Subnets ki sankhya):**
    * Original network bits = 24.
    * Naye network bits = 26.
    * Subnetting ke liye udhaar (borrow) liye gaye bits = $26 - 24 = 2$ bits.
    * Subnets ki sankhya ka formula hai $2^{\text{subnet bits}}$.
    * Calculation: $2^2 = 4$.
    * **Answer:** Aap **4 subnets** bana sakte hain.

3.  **Calculate Hosts per Subnet (Har subnet me hosts ki sankhya):**
    * IPv4 me total bits = 32.
    * Naye network/subnet ke liye istemal hue bits = 26.
    * Hosts ke liye bache hue bits = $32 - 26 = 6$ bits.
    * Usable hosts ki sankhya ka formula hai $2^{\text{host bits}} - 2$. (Hum 2 isliye minus karte hain kyunki ek address Network Address aur ek Broadcast Address ke liye reserve hota hai).
    * Calculation: $2^6 - 2 = 64 - 2 = 62$.
    * **Answer:** Har subnet me **62 usable hosts** ho sakte hain.

---

### **IV. Network Devices & Hardware**

**Q: What is the difference between a hub, a switch, and a router? (Hub, switch, aur router me kya antar hai?)**
A: Ye teeno network devices hain, lekin inka kaam aur intelligence level alag-alag hai.

| Feature | Hub (हब) | Switch (स्विच) | Router (राउटर) |
| :--- | :--- | :--- | :--- |
| **OSI Layer** | Layer 1 (Physical Layer) | Layer 2 (Data Link Layer) | Layer 3 (Network Layer) |
| **Kaam** | Data ko sabhi connected devices par **broadcast** karta hai. | Data ko sirf **specific destination device** tak bhejta hai. | **Alag-alag networks** ko aapas me jodta hai aur best path chunta hai. |
| **Addressing** | Koi address use nahi karta. | **MAC Address** ka istemal karta hai. | **IP Address** ka istemal karta hai. |
| **Intelligence** | "Dumb" device hai. | "Intelligent" device hai. | "Highly Intelligent" device hai. |
| **Collision Domain**| Ek single, bada collision domain banata hai. | Har port ek alag collision domain hota hai. | Har port ek alag broadcast domain hota hai. |

---
**Q: What is the difference between a router and a gateway? (Router aur gateway me kya antar hai?)**
A:
* **Router (राउटर):** 🗺️ Ek router ek aisa device hai jo **ek jaise (similar) protocol** ka istemal karne waale alag-alag networks ke beech data packets ko forward karta hai. Iska mukhya kaam IP addresses ke aadhar par raasta (path) chunna hai.
* **Gateway (गेटवे):** 🏛️ Gateway ek **zyada broad term** hai. Ye ek aisa network node hai jo **alag-alag (dissimilar) protocol** ka istemal karne waale do networks ko jodta hai. Ye ek "protocol converter" ki tarah kaam karta hai.

**Mukhya Baat:** Har router ek gateway ki tarah kaam karta hai (aapke LAN ko internet se jodta hai), lekin har gateway ek router nahi hota. Ek proxy server ya ek firewall bhi gateway ho sakta hai.

---
**Q: What is the difference between Layer 2 and Layer 3 switches? (Layer 2 aur Layer 3 switches me kya antar hai?)**
A:
* **Layer 2 Switch:**
    * Ye ek standard switch hai jo **Data Link Layer (Layer 2)** par kaam karta hai.
    * Ye data frames ko forward karne ke liye **MAC addresses** ka istemal karta hai.
    * Iska kaam ek hi LAN ya VLAN ke andar devices ko aapas me jodna hota hai.
* **Layer 3 Switch (Multilayer Switch):**
    * Ye ek advanced switch hai jisme **router ki capabilities** bhi hoti hain.
    * Ye Layer 2 (MAC address) ke saath-saath **Network Layer (Layer 3) (IP address)** par bhi kaam kar sakta hai.
    * Iska mukhya fayda ye hai ki ye **alag-alag VLANs ya subnets ke beech routing** kar sakta hai, aur ye kaam wo ek traditional router se **zyada tezi** se karta hai.

---
**Q: Which device operates at the Data Link layer of the OSI model? (OSI model ke Data Link layer par kaun sa device kaam karta hai?)**
A: Data Link Layer (Layer 2) par mukhya roop se ye devices kaam karte hain:
* **Switch (स्विच)**
* **Bridge (ब्रिज)**
* **Network Interface Card (NIC)**

---
**Q: What is a transparent bridge? (Transparent bridge kya hai?)**
A: Ek **transparent bridge** 👻 ek aisa bridge hota hai jo network par maujood doosre devices ke liye **adrishya (invisible)** hota hai. Devices ko ye pata hi nahi chalta ki unke beech me koi bridge laga hua hai.
Ye apne aap (automatically) network ke dono taraf ke devices ke MAC addresses ko "seekhta" (learns) hai aur ek table bana leta hai. Fir ye traffic ko tabhi aage forward karta hai jab zaroori ho, jisse network me unnecessary traffic kam ho jaata hai.

---
**Q: What is the importance of twisting in twisted-pair cable? (Twisted-pair cable me taaron ke ghumav (twisting) ka kya mahatva hai?)**
A: Taaron ko aapas me twist karne ka mukhya kaaran **electromagnetic interference (EMI)** aur **crosstalk** (paas ki taaron se aane waala interference) ko **kam karna** hai.
* **Kaise kaam karta hai:** Ek pair ki dono taarein equal aur opposite signals le jaati hain. Unhe twist karne se, dono taarein bahari noise source ke aage barabar roop se expose hoti hain. Iski vajah se ek taar me paida hua noise doosri taar me paida hue noise se **cancel out** ho jaata hai, jisse asli data signal surakshit rehta hai.

---
**Q: What is the maximum data rate of an Ethernet LAN using twisted-pair cabling (like Cat 6)? (Cat 6 cable ka istemal karke Ethernet LAN ki maximum data rate kya hai?)**
A:
* **Category 6 (Cat 6)** cabling, **10 Gigabits per second (Gbps)** tak ki speed ko support kar sakti hai, lekin ye aam taur par **55 meter** tak ki chhoti dooriyon ke liye hi seemit hai.
* Lambi dooriyon (100 meter tak) ke liye, Cat 6 **1 Gigabit per second (Gbps)** ki speed ko aaram se support karti hai.
* **Category 6a (Cat 6a)**, iska ek behtar version hai jo 100 meter tak 10 Gbps ki speed ko reliably support karne ke liye design kiya gaya hai.

---


### **V. Network Protocols**

#### **Core Protocols (TCP/UDP)**

**Q: What is the TCP protocol? (TCP protocol kya hai?)**
A: **TCP (Transmission Control Protocol)** ek **connection-oriented** aur **reliable** transport layer protocol hai. "Connection-oriented" ka matlab hai ki data bhejne se pehle ek connection banaya jaata hai. "Reliable" ka matlab hai ki ye data ke **error-free, in-order delivery** ki guarantee deta hai. Ye web browsing (HTTP), email (SMTP), aur file transfer (FTP) jaisi zaroori services me istemal hota hai.

---
**Q: What is the UDP protocol? (UDP protocol kya hai?)**
A: **UDP (User Datagram Protocol)** ek **connectionless** aur **unreliable** transport layer protocol hai. "Connectionless" ka matlab hai ki data bhejne se pehle koi connection nahi banaya jaata. "Unreliable" ka matlab hai ki ye data delivery ki koi guarantee nahi deta. Iska mukhya fayda iski **speed** aur **low overhead** hai. Ye video streaming, online gaming, aur DNS me istemal hota hai.

---
**Q: What is the difference between TCP and UDP? (TCP aur UDP me kya antar hai?)**
A: Ye ek bahut hi common interview question hai.

| Feature | TCP (Transmission Control Protocol) | UDP (User Datagram Protocol) |
| :--- | :--- | :--- |
| **Connection Type**| **Connection-Oriented** (Handshake zaroori) | **Connectionless** (Koi handshake nahi) |
| **Reliability** | **Reliable** (Guaranteed delivery) | **Unreliable** (Best-effort delivery) |
| **Speed** | **Slower** (Overhead ke kaaran) | **Faster** (Low overhead) |
| **Header Size** | Bada (20 bytes) | Chota (8 bytes) |
| **Flow Control** | Haan, flow control hai. | Nahi, flow control nahi hai. |
| **Use Cases** | Web (HTTP), Email (SMTP), File Transfer (FTP). | Video Streaming, Gaming, DNS, VoIP. |

---
**Q: How does the TCP three-way handshake work? (TCP three-way handshake kaise kaam karta hai?)**
A: TCP three-way handshake, client aur server ke beech ek reliable connection sthapit karne ka process hai. Ye 3 steps me hota hai:
1.  **SYN:** ➡️ Client, server ko ek `SYN` (Synchronize) packet bhejta hai taaki connection shuru kiya jaa sake.
2.  **SYN-ACK:** ⬅️ Server, client ke request ka jawaab ek `SYN-ACK` (Synchronize-Acknowledge) packet se deta hai.
3.  **ACK:** ➡️ Client, server ke response ko acknowledge karne ke liye ek `ACK` (Acknowledge) packet bhejta hai.
Iske baad, connection sthapit ho jaata hai aur data transfer shuru ho sakta hai.

---
**Q: Explain how congestion control works in TCP. (TCP me congestion control kaise kaam karta hai?)**
A: **Congestion control**, network ko overload hone se bachane ka ek TCP mechanism hai. TCP iske liye ek **congestion window (cwnd)** ka istemal karta hai, jo batata hai ki ek sender bina acknowledgement ke kitna data bhej sakta hai.
* **Slow Start:** Shuru me, `cwnd` tezi se badhta hai.
* **Congestion Avoidance:** Ek threshold ke baad, `cwnd` dheere-dheere badhta hai taaki congestion na ho.
* **Congestion Detection:** Jab packet loss hota hai, to TCP ise congestion ka sanket maanta hai aur `cwnd` ko turant kam kar deta hai.

---
#### **Application & Support Protocols**

**Q: What is the DNS and what is its main purpose? (DNS kya hai aur iska mukhya kaam kya hai?)**
A: **DNS (Domain Name System)** 📖 ko **"Internet ka Phonebook"** kehte hain. Iska mukhya kaam human-readable **domain names** (jaise `www.google.com`) ko computer-readable **IP addresses** (jaise `172.217.167.78`) me **translate** karna hai.

---
**Q: What is the protocol and port number of DNS? (DNS ka protocol aur port number kya hai?)**
A: DNS aam taur par fast queries ke liye **UDP** protocol ka istemal karta hai. Bade data transfers (jaise zone transfers) ke liye ye **TCP** ka bhi istemal kar sakta hai. Iska standard port number **53** hai.

---
**Q: What do you mean by the DHCP Protocol? (DHCP Protocol se aap kya samajhte hain?)**
A: **DHCP (Dynamic Host Configuration Protocol)** 💻 ek network management protocol hai jiska istemal network par devices ko **automatically IP address**, subnet mask, default gateway, aur DNS server jaisi zaroori information assign karne ke liye hota hai.

---
**Q: What are the HTTP and HTTPS protocols? (HTTP aur HTTPS protocols kya hain?)**
A:
* **HTTP (HyperText Transfer Protocol):** 🌐 Ye World Wide Web par data (jaise webpages) ko transfer karne ke liye istemal hone wala protocol hai.
* **HTTPS (HyperText Transfer Protocol Secure):** 🔒 Ye HTTP ka **secure version** hai. Ye **SSL/TLS** ka istemal karke browser aur server ke beech communication ko **encrypt** karta hai taaki data surakshit rahe.

---
**Q: What is the FTP protocol? Which protocol is used for securely transferring files? (FTP protocol kya hai? Files ko securely transfer karne ke liye kaun sa protocol use hota hai?)**
A: **FTP (File Transfer Protocol)** 📂 ek standard protocol hai jiska istemal network par client aur server ke beech **files ko transfer** karne ke liye hota hai.
FTP insecure hai kyunki ye data cleartext me bhejta hai. Files ko securely transfer karne ke liye in protocols ka istemal hota hai:
* **SFTP (SSH File Transfer Protocol)**
* **FTPS (FTP over SSL/TLS)**

---
**Q: What is the SMTP protocol? (SMTP protocol kya hai?)**
A: **SMTP (Simple Mail Transfer Protocol)** 📧, email **bhejne (sending)** ke liye istemal hone wala standard protocol hai. Ye ek email client se server tak aur ek server se doosre server tak email pahunchata hai.

---
**Q: What is the ARP protocol and what is its role? (ARP protocol kya hai aur iska role kya hai?)**
A: **ARP (Address Resolution Protocol)** ↔️ ka kaam ek **local network** ke andar, kisi device ka **IP Address (Layer 3)** pata hone par uska **MAC Address (Layer 2)** dhoondhna hai. Ye logical addresses ko physical addresses se map karta hai, jo ek hi LAN segment me communication ke liye zaroori hai.

---
**Q: What is the ICMP protocol? (ICMP protocol kya hai?)**
A: **ICMP (Internet Control Message Protocol)** ✉️ ek network layer support protocol hai jiska istemal network devices dwara **error messages aur operational information** bhejne ke liye kiya jaata hai. Iska istemal normal data transfer ke liye nahi hota. **`ping`** aur **`traceroute`** commands ICMP ka istemal karti hain.

---
**Q: Name some services provided by the application layer in the Internet model. (Internet model me application layer dwara pradaan ki jaane waali kuch services ke naam batao.)**
A: Application layer dwara pradaan ki jaane waali kuch mukhya services hain:
* **World Wide Web** (HTTP/HTTPS ke zariye)
* **Email** (SMTP, POP3, IMAP ke zariye)
* **File Transfer** (FTP/SFTP ke zariye)
* **Domain Name Resolution** (DNS ke zariye)
* **Remote Access** (SSH, Telnet ke zariye)
* **Network Management** (SNMP ke zariye)
---


### **Routing & Advanced Protocols**

**Q: What is BGP (Border Gateway Protocol)? (BGP kya hai?)**
A: **BGP (Border Gateway Protocol)** 🌐 wo routing protocol hai jispar poora **global Internet** chalta hai. Ye ek **Exterior Gateway Protocol (EGP)** hai, jiska kaam alag-alag **Autonomous Systems (AS)** ke beech routing information ko exchange karna hota hai. (Ek AS ek bada network hota hai, jaise Jio ya Airtel). BGP sirf sabse chota raasta nahi dekhta, balki policies ke aadhar par complex routing decisions leta hai.

---
**Q: What is MPLS (Multiprotocol Label Switching)? (MPLS kya hai?)**
A: **MPLS (Multiprotocol Label Switching)** 🏷️ ek high-performance network routing technique hai. Isme, data packets ko lambe network addresses ke bajaye chote **labels** ke aadhar par ek node se doosre node tak forward kiya jaata hai.
**Analogy:** Ye ek package par ek special sticker (label) lagane jaisa hai. Har sorting center par, workers ko poora address padhne ke bajaye sirf sticker dekh kar hi pata chal jaata hai ki package ko aage kahan bhejna hai. Isse delivery (data transfer) bahut fast ho jaati hai.

---
**Q: Define piggybacking. What are its advantages and disadvantages? (Piggybacking ko define karein. Iske fayde aur nuksaan kya hain?)**
A: **Piggybacking** 🐷, two-way communication me efficiency badhane ki ek technique hai. Isme, ek received data frame ke liye **acknowledgement (ACK)** ko ek alag frame me bhejne ke bajaye, use **reverse direction me jaane waale data frame ke header me hi "piggyback" (jod)** kar bhej diya jaata hai.
* **Advantages (फायदे):**
    * **Improves Efficiency:** Network par bheje jaane waale total frames ki sankhya kam ho jaati hai.
    * **Saves Bandwidth:** Network resources ka behtar istemal hota hai.
* **Disadvantages (नुकसान):**
    * **Delay:** Agar receiver ke paas wapas bhejne ke liye koi data nahi hai, to use ACK bhejne ke liye intezaar karna pad sakta hai, jisse sender ka timer expire ho sakta hai.

---
### **6. Network Security**

**Q: What is a firewall? What is a zone-based firewall? (Firewall kya hai? Zone-based firewall kya hai?)**
A:
* **Firewall (फ़ायरवॉल):** 🛡️ Ek firewall ek network security device hai jo ek trusted network aur ek untrusted network (jaise internet) ke beech ek **barrier (deewar)** ki tarah kaam karta hai. Ye security rules ke aadhar par network traffic ko filter (allow ya block) karta hai.
* **Zone-based Firewall:** Ye firewall configure karne ka ek modern tarika hai. Isme, network interfaces ko alag-alag **zones** (jaise `Trust-Zone`, `Untrust-Zone`, `DMZ-Zone`) me group kiya jaata hai. Fir, interfaces ke bajaye, in **zones ke beech** traffic par rules lagaye jaate hain. Ye zyada flexible aur manage karne me aasan hota hai.

---
**Q: What is the difference between an IPS (Intrusion Prevention System) and a firewall? (IPS aur firewall me kya antar hai?)**
A:
* **Firewall:** Ye mukhya roop se IP addresses aur ports (Layer 3/4) ke aadhar par traffic ko filter karta hai. Iska kaam access control karna hai.
* **IPS (Intrusion Prevention System):** Ye traffic ke **content (Layer 7)** ko deeply analyze karke known attacks, exploits, aur malware patterns ko pehchanta hai aur unhe **actively block** karta hai.

**Mukhya Antar:** Firewall darwaze par bouncer ki tarah ID check karta hai. IPS ID check karne ke saath-saath bag bhi check karta hai taaki koi khatarnak cheez andar na aa sake.

---
**Q: What is an IDS (Intrusion Detection System)? (IDS kya hai?)**
A: Ek **IDS (Intrusion Detection System)** 🚨 ek **passive monitoring** system hai jo network ya system ko malicious activity ke liye monitor karta hai. Jab ise koi khatra dikhta hai, to ye sirf ek **alert** generate karta hai; ye us khatre ko **rokta nahi** hai.
**Analogy:** Ye ek chor alarm (burglar alarm) jaisa hai jo chor ke aane par shor machata hai, lekin use pakadta nahi hai.

---
**Q: What is a VPN (Virtual Private Network)? What are its advantages and different types? (VPN kya hai? Iske fayde aur prakaar kya hain?)**
A:
* **VPN (वर्चुअल प्राइवेट नेटवर्क):** tunneling Ek VPN ek aisi technology hai jo internet jaise public network par ek **secure aur encrypted connection (tunnel)** banati hai. Isse users data ko is tarah bhej aur receive kar sakte hain jaise unke devices ek private network se jude hon.
* **Advantages (फायदे):**
    * **Security:** Aapke internet traffic ko encrypt karta hai.
    * **Privacy:** Aapka asli IP address chupata hai.
    * **Remote Access:** Kisi corporate network ko remote location se securely access karne ki suvidha deta hai.
* **Types:**
    * **Remote Access VPN:** Ek individual user ko private network se jodta hai.
    * **Site-to-Site VPN:** Do ya do se zyada alag-alag networks (jaise ek company ke branch office aur head office) ko aapas me jodta hai.

---
**Q: What is IP Spoofing? (IP Spoofing kya hai?)**
A: **IP Spoofing** 🎭 ek cyber attack hai jisme attacker, IP packets ko ek **nakli (spoofed) source IP address** ke saath bhejta hai taaki wo apni asli pehchaan chupa sake ya kisi doosre system hone ka dikhawa kar sake.

---
**Q: What is a DDoS (Distributed Denial-of-Service) attack and how can it be mitigated? (DDoS attack kya hai aur isse kaise bacha jaa sakta hai?)**
A:
* **DDoS Attack:** 🌊 Ye ek aisa cyber attack hai jisme attacker hazaron ya lakhon compromised computers (ek **botnet**) ka istemal karke ek target server ya network par itna zyada traffic bhejta hai ki wo server overload hokar **crash ya unavailable** ho jaata hai.
* **Mitigation (बचाव):**
    * **Filtering:** Malicious sources se aane waale traffic ko block karna.
    * **Rate Limiting:** Ek single source se aane waali requests ki sankhya ko limit karna.
    * **DDoS Mitigation Services:** Cloudflare ya Akamai jaisi special services ka istemal karna jo attack traffic ko aapke server tak pahunchne se pehle hi absorb aur filter kar deti hain.

---
**Q: What is the meaning of threat, vulnerability, and risk? (Threat, vulnerability, aur risk ka kya matlab hai?)**
A:
* **Threat (खतरा):** 💣 Koi bhi aisi cheez jo security ko nuksaan pahuncha sakti hai. (e.g., ek virus, ek hacker).
* **Vulnerability (कमज़ोरी):** 🔓 System me koi aisi kamzori ya galti jiska threat fayda utha sakta hai. (e.g., ek purana, unpatched software).
* **Risk (जोखिम):** 💥 Nuksaan hone ki sambhavna jab ek threat, ek vulnerability ka fayda uthata hai. (`Risk = Threat x Vulnerability`).

---
**Q: What are Confidentiality, Integrity, & Availability (the CIA Triad)? (CIA Triad kya hai?)**
A: Ye information security ke teen mool siddhant (core principles) hain:
* **Confidentiality (गोपनीयता):** 🤫 Sunishchit karna ki data sirf authorized users ko hi accessible ho.
* **Integrity (अखंडता):** ✍️ Sunishchit karna ki data accurate hai aur usme koi anadhikrit badlav nahi hua hai.
* **Availability (उपलब्धता):** ✅ Sunishchit karna ki data aur services authorized users ke liye zaroorat padne par hamesha uplabdh hon.

---
**Q: What is Symmetric and Asymmetric Encryption? (Symmetric aur Asymmetric Encryption kya hai?)**
A:
* **Symmetric Encryption:** 🔑 Isme encryption aur decryption dono ke liye **ek hi secret key** ka istemal hota hai. Ye **fast** hota hai. (e.g., AES).
* **Asymmetric Encryption:** 🔑🗝️ Isme keys ka ek **pair** use hota hai - ek **public key** (encryption ke liye) aur ek **private key** (decryption ke liye). Ye **slow** hota hai. (e.g., RSA).

---
**Q: At what layer does IPsec work? What is Tunnel mode? (IPsec kis layer par kaam karta hai? Tunnel mode kya hai?)**
A:
* **Layer:** IPsec, OSI model ke **Network Layer (Layer 3)** par kaam karta hai.
* **Tunnel Mode:** Ye IPsec ka ek mode hai. Isme, **poore original IP packet (header + payload)** ko encrypt karke ek naye IP packet ke andar daal diya jaata hai. Is mode ka istemal do networks ke beech **VPNs** banane ke liye hota hai.

---
**Q: Define Digital Signatures. (Digital Signatures ko define karein.)**
A: Ek **Digital Signature** ✍️, ek mathematical technique hai jiska istemal kisi digital message ki **authenticity (pramanikta)** aur **integrity (akhandata)** ko saabit karne ke liye hota hai. Ye message ka hash nikal kar use sender ki **private key** se encrypt karke banaya jaata hai.

---
**Q: Name the three means of user authentication. (User authentication ke teen saadhan batao.)**
A:
1.  **Something you know (Jo aap jaante hain):** Password, PIN.
2.  **Something you have (Jo aapke paas hai):** OTP, Smart card.
3.  **Something you are (Jo aap hain):** Fingerprint, Face ID.

---
**Q: What is Authorization? (Authorization kya hai?)**
A: **Authorization** ✅, ye tay karne ka process hai ki ek **authenticated** (jiski pehchaan saabit ho chuki hai) user ko kisi specific resource ko access karne ya koi specific action perform karne ki **permission** hai ya nahi.
**Antar:** Authentication puchta hai, **"Aap kaun hain?"**. Authorization puchta hai, **"Aapko kya karne ki anumati hai?"**.
---

### **VII. Modern & Advanced Networking**

**Q: What is NAT (Network Address Translation) and how does it work? (NAT kya hai aur ye kaise kaam karta hai?)**
A:
* **NAT (नेटवर्क एड्रेस ट्रांसलेशन):** 🏠 NAT ek aisi method hai jiska istemal router, ek local network ke **multiple private IP addresses** ko internet par communicate karne ke liye ek **single public IP address** me translate karne ke liye karta hai.
* **How it works (कैसे काम करता है):** Jab aapke computer (jiska private IP hai) se koi packet internet par jaata hai, to router us packet se aapka private IP hata kar apna public IP laga deta hai. Is mapping ko wo ek **NAT table** me store kar leta hai. Jab internet se response wapas router ke public IP par aata hai, to wo is table ko dekh kar packet ko sahi computer tak pahuncha deta hai.

---
**Q: What is a VLAN and how is it used to segment a network? (VLAN kya hai aur iska istemal network ko segment karne ke liye kaise hota hai?)**
A:
* **VLAN (वर्चुअल लोकल एरिया नेटवर्क):** 🏢 VLAN ek aisi technology hai jisse ek single physical LAN ko logically **kai alag-alag, isolated virtual LANs** me baanta jaa sakta hai.
* **How it segments:** VLAN, devices ko unki physical location ke bajaye unke function ke aadhar par group karta hai. Ek switch par alag-alag VLANs ke devices aapas me direct communicate nahi kar sakte, bhale hi wo ek hi switch se jude hon. Unke beech communication ke liye ek Layer 3 device (jaise router) ki zaroorat padti hai. Isse network ko **secure aur manageable** banana aasan ho jaata hai.

---
**Q: What is QoS (Quality of Service)? (QoS kya hai?)**
A: **QoS (क्वालिटी ऑफ़ सर्विस)** 🏆, network me istemal hone waali un technologies ka set hai jinka kaam network traffic ko **manage karna aur prioritize karna** hai. Iska goal zaroori aur time-sensitive applications ke liye ek certain level ki performance guarantee karna hai.
**Example:** QoS ye sunishchit karta hai ki aapki **video call** (high priority) bina ruke chalti rahe, bhale hi usi network par koi aur ek badi file (low priority) download kar raha ho.

---
**Q: What is a load balancer? (Load balancer kya hai?)**
A: Ek **load balancer** ⚖️ ek aisa device ya software hai jo incoming network traffic ko **multiple servers** ke beech **distribute (baant)** karta hai.
* **Purpose:**
    1.  **High Availability:** Agar ek server fail ho jaata hai, to load balancer traffic ko baaki bache hue healthy servers par bhej deta hai.
    2.  **Scalability:** Traffic badhne par naye servers add karke system ki capacity ko aasaani se badhaya jaa sakta hai.
    3.  **Performance:** Kisi ek server ko overload hone se rokta hai.

---
**Q: What is SD-WAN (Software-Defined WAN) and what are its benefits? (SD-WAN kya hai aur iske fayde kya hain?)**
A:
* **SD-WAN (सॉफ्टवेयर-डिफाइंड WAN):** SD-WAN, ek Wide Area Network (WAN) ko manage karne ka ek software-based approach hai. Ye network ke **control plane (brain)** ko **data plane (hardware)** se alag kar deta hai.
* **Benefits (फायदे):**
    * **Cost Savings:** Ye mehengi dedicated MPLS lines ki jagah saste broadband internet connections ka istemal karne ki suvidha deta hai.
    * **Improved Performance:** Ye automatically traffic ke liye us samay ka sabse behtar raasta (best available path) chun sakta hai.
    * **Simplified Management:** Poore WAN ko ek central dashboard se aasaani se manage kiya jaa sakta hai.

---
**Q: What is SDN (Software-Defined Networking)? (SDN kya hai?)**
A: **SDN (सॉफ्टवेयर-डिफाइंड नेटवर्किंग)** 🧠, networking ke liye ek architectural approach hai jo network ko **programmable aur flexible** banata hai. Iska mool siddhant (core idea) **control plane ko data plane se alag karna** hai. Isse network administrators ko har ek device ko alag-alag configure karne ke bajaye, poore network ko ek central controller se manage karne ki power milti hai. SD-WAN, SDN ka hi ek specific use case hai.

---
**Q: What is network virtualization? (Network virtualization kya hai?)**
A: **Network Virtualization** ☁️, hardware aur software network resources ko milakar ek **single, software-based virtual network** banane ka process hai. Isse, ek hi physical network infrastructure ke upar kai **isolated virtual networks** banaye jaa sakte hain. **VLANs** iska ek simple example hai.

---
**Q: What is a VPC (Virtual Private Cloud)? (VPC kya hai?)**
A: Ek **VPC (वर्चुअल प्राइवेट क्लाउड)** ☁️, ek public cloud (jaise AWS, Azure) ke andar host kiya gaya ek **secure aur isolated private cloud** hota hai. Ye aapko public cloud provider ke infrastructure ka ek private hissa deta hai, jahan aap apne virtual network environment (jaise IP address range, subnets, route tables) par poora control rakhte hain.

---
**Q: Explain what VoIP is. (VoIP kya hai, samjhaiye.)**
A: **VoIP (Voice over Internet Protocol)** 📞 ek aisi technology hai jiske zariye aap regular phone line ke bajaye **broadband internet connection** ka istemal karke **voice calls** kar sakte hain. Ye aapki awaaz (analog signal) ko digital data packets me convert karke internet par bhejta hai. WhatsApp calls, Skype calls, sabhi VoIP ke examples hain.

---
**Q: What is a reverse proxy? (Reverse proxy kya hai?)**
A: Ek **reverse proxy** 🛡️ ek aisa server hota hai jo client aur ek ya ek se zyada web servers ke beech me baithta hai. Jab client koi request bhejta hai, to wo pehle reverse proxy par jaati hai, jo fir use aage aakhri (backend) server tak bhejta hai.
* **Forward Proxy vs. Reverse Proxy:** Ek forward proxy, **client** ko chupata hai. Ek reverse proxy, **server** ko chupata hai.
* **Use Cases:** Load balancing, security (Web Application Firewall), SSL termination, aur caching.

---
**Q: Define the term OFDM. (OFDM ko define karein.)**
A: **OFDM (Orthogonal Frequency-Division Multiplexing)** 📶 ek digital signal modulation ki technique hai. Isme, ek single data stream ko kai **chote-chote, aapas me overlapping (orthogonal) sub-carrier frequencies** par baant diya jaata hai.
* **Benefit:** Ye technique interference aur signal fading ke prati bahut **mazboot (resilient)** hai.
* **Use Case:** Ye modern wireless standards jaise **4G/5G LTE, Wi-Fi (Wi-Fi 6 sahit)**, aur digital TV broadcasting ki core technology hai.

---

### **VIII. Practical Knowledge & Troubleshooting**

**Q: What happens when you enter a website address (e.g., google.com) in your web browser? (Jab aap browser me koi website address daalte hain to kya hota hai?)**
A: Jab aap browser me `google.com` type karke Enter dabaate hain, to parde ke peeche ye detailed process hota hai:

1.  **DNS Lookup (IP Address Dhoondhna):** 🌐
    * Browser pehle apne cache me dekhta hai ki kya use `google.com` ka IP address pehle se pata hai.
    * Agar nahi, to wo OS se puchta hai. OS, **DNS (Domain Name System)** server ko ek query bhejta hai taaki `google.com` ko uske IP address (e.g., `142.251.42.78`) me translate kiya jaa sake.

2.  **TCP Handshake (Connection Banana):** 🤝
    * IP address milne ke baad, browser us IP address waale server ke saath ek reliable connection sthapit karne ke liye **TCP 3-way handshake** shuru karta hai (SYN, SYN-ACK, ACK).

3.  **TLS Handshake (Connection ko Secure Karna):** 🔒
    * Agar website `https` hai, to TCP handshake ke baad ek **TLS (Transport Layer Security) handshake** hota hai. Isme browser aur server certificates exchange karke communication ke liye ek encrypted channel banate hain.

4.  **HTTP Request (Webpage Maangna):** 📤
    * Connection ban jaane ke baad, browser server ko ek **HTTP `GET` request** bhejta hai. Is request me likha hota hai, "Mujhe `google.com` ka webpage chahiye."

5.  **HTTP Response (Server ka Jawaab):** 📥
    * Server request ko process karta hai aur ek **HTTP response** wapas bhejta hai. Is response me ek status code (jaise `200 OK`, matlab sab theek hai) aur webpage ka content (HTML, CSS, JavaScript files) hota hai.

6.  **Rendering (Webpage Dikhana):** 🖼️
    * Browser, server se mile HTML, CSS, aur JavaScript ko **render (process)** karta hai aur aapko aapki screen par Google ka homepage dikha deta hai.

---
**Q: What is the difference between `ipconfig` and `ifconfig`? (`ipconfig` aur `ifconfig` me kya antar hai?)**
A:
* **`ifconfig` (interface configuration):**
    * **OS:** Ye **Unix-like operating systems** (jaise Linux, macOS) me istemal hone wali ek command-line utility hai.
    * **Kaam:** Iska istemal network interfaces ko dekhne aur configure karne ke liye hota hai. Ise ab thoda purana maana jaata hai.
* **`ipconfig` (IP configuration):**
    * **OS:** Ye **Windows** operating systems me istemal hone wali ek command-line utility hai.
    * **Kaam:** Iska istemal current TCP/IP network configuration (jaise IP address, subnet mask, gateway) ko dekhne ke liye hota hai.

**Note:** Modern Linux systems me `ifconfig` ki jagah ab `ip` command (`ip addr show`) ko prefer kiya jaata hai.

---
**Q: What is a packet analyzer? (Packet analyzer kya hai?)**
A: Ek **packet analyzer** 🕵️‍♂️ (jise packet sniffer ya network analyzer bhi kehte hain) ek aisa tool hai jo network par travel kar rahe data packets ko **capture (pakadta) aur analyze** karta hai.
Iska istemal network troubleshooting, performance analysis, aur security monitoring ke liye hota hai. **Wireshark** sabse popular packet analyzer hai.

---
**Q: What kind of error is undetectable by the checksum? (Checksum dwara kis prakaar ki galti ka pata nahi lagaya jaa sakta?)**
A: **Checksum** ka mukhya kaam transmission ke dauraan data me aayi aam galtiyon (corruption) ka pata lagana hai. Lekin, ye un galtiyon ka pata nahi laga pata jahan **multiple bit errors ek doosre ko cancel out** kar dete hain.
**Example:** Agar data ke ek hisse me value `1` se ghat jaati hai aur doosre hisse me `1` se badh jaati hai, to data ka overall sum (aur isliye checksum) same reh sakta hai, aur galti pakdi nahi jaayegi. Isliye CRC jaise behtar error detection methods ka istemal kiya jaata hai.

---
**Q: Can a routing table have two entries with the same destination address in a datagram network? (Kya ek routing table me ek hi destination ke liye do entries ho sakti hain?)**
A: **Haan, bilkul ho sakti hain.** Aisa kai valid scenarios me hota hai:
* **Load Balancing:** ⚖️ Agar ek destination tak pahunchne ke liye do barabar cost waale raaste (equal-cost paths) hain, to router dono raaston ko apni table me rakh sakta hai aur traffic ko unke beech baant (distribute) sakta hai. Ise **Equal-Cost Multi-Path (ECMP)** routing kehte hain.
* **Redundancy (Failover):** 🔄 Ek router ek **primary route** aur ek **secondary (backup) route** rakh sakta hai. Backup route ka istemal tabhi kiya jaata hai jab primary route fail ho jaata hai.
* **Specific vs. General Routes:** Ek table me ek specific route (e.g., `10.1.1.0/24`) aur ek general route (e.g., `10.1.0.0/16`) dono ho sakte hain. Router **"longest prefix match"** rule ka istemal karke sabse specific route ko chunta hai.

---