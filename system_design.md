# Content of System Design:-

### **Part 1: Foundations of System Design**

This section covers the absolute basics, defining the scope and fundamental concepts you'll need for everything that follows.

* **1.1. Introduction to System Design**
    * Why study System Design?
    * What is System Design?
    * System Design Introduction - HLD & LLD
    * Difference between HLD and LLD
    * What is the goal of High-Level Design (HLD)?
    * What is a Server?

* **1.2. Core Concepts & Metrics**
    * Functional and Non-Functional Requirements
    * Latency and Throughput
    * Concurrency and Parallelism
    * What are Threads?
    * Memory vs. Latency - [Post Link]
    * Throughput vs. Latency - [Post Link]
    * Latency vs. Accuracy - [Post Link]

* **1.3. Capacity and Estimation**
    * What is Capacity Estimation? - [YouTube Link]
    * Back-of-the-envelope Estimation
        * Load Estimation
        * Storage Estimation
        * Resource Estimation

* **1.4. Networking Fundamentals**
    * What is HTTP? - [Post Link]
    * What is the Internet TCP/IP stack? - [Post Link]
    * Communication Protocols
    * Network Protocols and Proxies
    * What happens when you enter Google.com? - [Post Link]
    * Domain Name System (DNS)
        * DNS Caching
        * Time to Live (TTL)
    * WebSockets
    * Pull vs. Push - [Post Link]

### **Part 2: Core Components & Building Blocks**

These are the individual tools and technologies that form the backbone of any large-scale system.

* **2.1. Load Balancing**
    * What is Load Balancing? - [YouTube Link]
    * Why do we need the Load Balancer?
    * Load Balancer Algorithms (any 4 popular)
    * Consistent Hashing - [YouTube Link]

* **2.2. Databases**
    * **Database Fundamentals**
        * What are Relational Databases? - [Post Link]
        * What are NoSQL databases? - [YouTube Link]
        * SQL vs. NoSQL databases - [Post Link]
        * When to use which Database?
        * What are Location-based Databases? - [YouTube Link]
    * **Database Performance & Scaling**
        * What are Database Indexes? - [YouTube Link]
        * SQL Query Optimization
        * How are NoSQL databases optimized? - [YouTube Link]
        * Scaling of Database
            * Database Replication in System Design - [YouTube Link]
            * Master-Slave Architecture
            * Multi-master Setup
        * Database Sharding / Partitioning
            * What is Sharding?
            * Sharding Strategies
            * Disadvantage of Sharding
        * Denormalization in Databases
    * **Database Management**
        * Normalization Process in DBMS
        * Database Migrations
        * Transaction Isolation Levels

* **2.3. Caching**
    * What is a Cache? - [Post Link]
    * Caching in System Design
    * Benefits of Caching
    * What is Thrashing? - [Post Link]
    * Types of Caches
    * Distributed Caching - [YouTube Link]
    * Cache Write Policies - [Post Link]
    * Cache Replacement Policies
    * Intro to Redis / Redis Deep Dive

* **2.4. Storage**
    * File and Database Storage Systems
    * Block, Object, and File Storage
    * Blob Storage
        * What is a Blob, and why do we need Blob Storage?
        * AWS S3

* **2.5. Content Delivery Network (CDN)**
    * What are Content Delivery Networks? - [YouTube Link]
    * CDN Introduction
    * How does CDN work?
    * Key Concepts in CDNs

* **2.6. Messaging Systems**
    * Asynchronous Programming
    * What is a Message Queue? - [YouTube Link]
    * Why did we put a message broker in between?
    * Message Stream
    * When do we use Message Broker
    * What is the publisher-subscriber model? (Pub/Sub) - [YouTube Link]
    * Apache Kafka Deep Dive
        * When to use Kafka
        * Kafka Internals
    * Realtime Pubsub
    * Database as a Message Queue

* **2.7. API Gateway & Proxies**
    * How are APIs designed? - [YouTube Link]
    * What are asynchronous APIs?
    * What is API Gateway?
    * What is Proxy?
    * Proxies in System Design
        * Forward Proxy
        * Reverse Proxy
        * Forward Proxy vs Reverse Proxy
        * Building our own Reverse Proxy

### **Part 3: High-Level Design Principles & Trade-offs**

This section covers the guiding principles and theoretical frameworks that inform high-level architectural decisions.

* **3.1. Scalability**
    * Scalability and How to achieve it
    * Scaling and its types
        * Horizontal vs. Vertical Scaling - [YouTube Link]
    * Which Scalability approach is right for our Application?
    * Auto Scaling
    * Primary Bottlenecks that Hurt the Scalability of an Application

* **3.2. Availability, Reliability & Fault Tolerance**
    * Availability in System Design
    * How to achieve High Availability?
    * Reliability in System Design
    * Fault Tolerance in System Design
    * What is a Single Point of Failure? - [YouTube Link]
    * How to avoid Cascading Failures? - [YouTube Link]
    * Data Redundancy and Data Recovery
        * Why do we make databases redundant?
        * Different ways of doing data backup
        * Continuous Redundancy

* **3.3. Consistency**
    * What is Data Consistency? - [YouTube Link]
    * Consistency in System Design
    * Consistency pattern
    * Data Consistency Levels - [Post Link]
    * Consistency Deep Dive
        * Strong Consistency & When to choose it
        * Eventual Consistency & When to choose it
        * Ways to achieve strong consistency
        * Ways to achieve eventual consistency

* **3.4. The CAP Theorem**
    * CAP Theorem
    * Why can we only achieve CP or AP and not CAP?
    * Why not choose CA?
    * What to choose, CP or AP?
    * Consistency vs. Availability - [Post Link]

* **3.5. Other Core Principles**
    * Maintainability
    * Performance Optimization Techniques for System Design
    * Cost & Performance Optimizations
    * Software Cost Estimation

### **Part 4: Architectures & Patterns**

This section explores common high-level blueprints for structuring an entire system.

* **4.1. Architectural Styles**
    * Monolithic Architecture
    * Microservices Architecture - [YouTube Link]
    * Microservices vs. Monoliths
    * How monoliths are migrated
    * Event-Driven Architecture (EDA) - [YouTube Link]
        * Introduction to EDA
        * Why use EDA?
        * Simple Event Notification
        * Event-Carried State Transfer
    * Client-Server Architecture
    * Peer-to-Peer (P2P) Architecture
    * Serverless Architecture
    * Stateful vs. Stateless Architecture
    * Pub/Sub Architecture

* **4.2. Architectural Patterns**
    * Circuit Breaker Pattern
    * Event Sourcing Pattern
    * CQRS (Command Query Responsibility Segregation) Design Pattern

### **Part 5: Advanced Topics & Distributed Systems**

Diving deeper into the complexities of building modern, distributed applications.

* **5.1. Distributed Systems Concepts**
    * Distributed Systems
    * Consensus Algorithms in Distributed System
    * Auto-Recoverable System using Leader Election
    * What is Service Discovery and Heartbeats? - [YouTube Link]
    * Anomaly Detection in Distributed Systems - [YouTube Link]
    * Distributed Tracing
    * What are Containers? - [YouTube Link]
    * CI/CD Pipeline

* **5.2. Specialized Tools & Concepts**
    * Distributed Rate Limiting
        * Rate Limiting
        * Rate Limiting Algorithm
    * What are Bloom Filters? - [YouTube Link]
    * Big Data Tools

* **5.3. Security**
    * Security Measures in System Design
    * Authentication and Authorization
        * OAuth - [YouTube Link]
        * Token Based Auth - [Post Link]
        * Access Control Lists and Rule Engines
    * Secure Socket Layer (SSL) and Transport Layer Security (TLS)
    * Secure Communication in Distributed System
    * Secure Software Development Life Cycle (SSDLC)

* **5.4. Testing & Recovery**
    * Unit Testing
    * Integration Testing
    * Data Backup and Disaster Recovery

* **5.5. Design Process**
    * How to solve any System Design Problem?
    * How to Draw High Level Design Diagram?
    * **Types of HLD Diagrams**
        * Component Based Diagram
        * Sequence Diagrams
        * What is DFD (Data Flow Diagram)?
        * Deployment Diagram

---

### **Part 6: Low-Level Design (LLD)**

This section focuses on the design of individual components and classes within the larger system.

* **6.1. Core Concepts**
    * What is Low Level Design or LLD?
    * Object-Oriented Programming (OOP) Concepts
    * Modularity and Interfaces

* **6.2. Design Principles**
    * SOLID Principles
    * DRY (Don't Repeat Yourself) Principle
    * KISS (Keep It Simple, Stupid) Principle
    * YAGNI (You Ain't Gonna Need It) Principle

* **6.3. UML (Unified Modeling Language)**
    * Unified Modeling Language (UML)

* **6.4. Design Patterns**
    * **Creational Patterns**
        * Singleton Pattern
        * Factory Method Pattern
        * Abstract Factory Pattern
        * Builder Pattern
        * Prototype Pattern
    * **Structural Patterns**
        * Adapter Pattern
        * Decorator Pattern
        * Composite Pattern
        * Proxy Pattern
        * Facade Pattern
    * **Behavioral Patterns**
        * Observer Pattern
        * Strategy Pattern
        * Command Pattern
        * State Pattern
        * Template Method Pattern

---

### **Part 7: System Design Interview Case Studies**

This section contains the practical application questions, allowing you to synthesize and apply the knowledge from the previous sections.

* **7.1. Social & Communication Apps**
    * Design Twitter / Instagram - [YouTube Link]
    * Design Tinder - [YouTube Link]
    * Design WhatsApp Messenger - [YouTube Link]
    * Design TikTok - [YouTube Link]
    * Designing Facebook Messenger
    * System Design of Gmail - [Post Link]

* **7.2. Media & Entertainment**
    * System Design of a Live-Streaming App - [YouTube Link]
    * Design BookMyShow

* **7.3. E-commerce & Service Apps**
    * System Design of Uber App – Uber System Architecture - [YouTube Link], [Post Link]
    * System Design of Doordash - [YouTube Link]
    * System Design of Amazon Online Shops - [YouTube Link]
    * Designing Airbnb
    * System Design of IRCTC - [YouTube Link]
    * Designing Airline Management System

* **7.4. Utility & Productivity Tools**
    * URL Shortening Service
    * Design Dropbox
    * System Design of an Online Coding Judge - Part 1 & 2 - [YouTube Link]
    * System Design of UPI Payments - [YouTube Link]
    * System Design of Google Maps - [Post Link]
    * System Design of Google Docs

* **7.5. Niche & Gaming**
    * System Design of a Chess Website - [Post Link]

---

# 📌 Twitter System Design

### We'll cover the following:

* What is Twitter?
* Problem Statement
* Low Level Design
* Architecture and Components
* User Timeline
* Home Timeline
* Trending Hashtags
* Searching
* Databases
* Additional Interview Questions

---

# 📌 Netflix System Design – Complete Architecture / Video Onboarding Pipeline

### We'll cover the following:

* What is Netflix?
* Problem Statement
* Architecture and Components
* Onboarding Content
* Database Design
* How Search Works and Data Processing
* Additional Interview Questions
* Additional Quips

---

# 📌 Uber System Design

### We'll cover the following:

* Problem Statement
* Introduction
* Architecture
* Uber Challenges
* Demystification of Uber System Design
* How Uber Map Works and ETA Calculation
* Interview Questions

---

# 📌 Instagram System Design

### We'll cover the following:

* Problem Statement
* Introduction and Features
* Requirements and Approximations
* Low-Level Design
* Architecture and Components
* Newsfeed Generation
* Databases
* More Interview Problems

---

# 📌 BookMyShow System Design

### We'll cover the following:

* What is BookMyShow?
* Problem Statement
* Low Level Design
* Architecture and Components
* How Does the System Talk with Theatres?
* How to Sync Ticket Availability with Theatres?
* Database Design
* Additional Interview Questions

---

# 📌 Zomato System Design

### We'll cover the following:

* What is Zomato?
* Problem Statement
* Requirements
* Architecture and Components
* Services
* Database Schema
* Working Flow

---

# 📌 Dropbox System Design

### We'll cover the following:

* What is Dropbox?
* Problem Statement
* Low Level Design
* Architecture and Components

---

# 📌 Pastebin System Design

### We'll cover the following:

* What is Pastebin?
* Problem Statement
* Low Level Design
* Architecture and Components

---

# 📌 Elevator System Design (OOD)

### We'll cover the following:

* What is Elevator?
* Problem Statement
* Introduction
* Object Oriented Design

---

### **Topic: Introduction to System Design**

#### **1. Definition / Introduction (Ye Hai Kya?)**

**System Design** basically ek **blueprint** banane ka process hai. Jaise ek ghar banane se pehle architect ek detailed plan (naksha) banata hai, waise hi ek software application ya service banane se pehle engineers ek system design banate hain.

Is blueprint mein hum decide karte hain ki:

  * Application ke alag-alag **components** kya honge (e.g., database, servers, messaging system).
  * Ye components aapas mein **kaise baat karenge**.
  * User ka data **kahan aur kaise store hoga**.
  * System लाखों users ka load **kaise handle karega**.

In simple words, **"System Design is the art of defining the architecture, components, modules, interfaces, and data for a system to satisfy specified requirements."**

-----

#### **2. Why it matters (Kyun Zaroori Hai?)**

Soch ke dekho, agar aap bina plan ke ek badi building banana shuru kar do, toh kya hoga? Wo shayad aage jaakar gir jaayegi, ya usme aag lagne par bahar nikalne ka raasta nahi hoga. Same cheez software mein hoti hai.

Companies system design isliye use karti hain taaki:

  * **Scalability:** Application future mein **millions of users** ko support kar sake. Aaj 100 users hain, kal 10 lakh ho gaye toh system crash na ho.
  * **Availability & Reliability:** System **24/7 chalta rahe** (e.g., Google search kabhi down nahi hota). Agar ek server fail ho bhi jaaye, toh users ko pata na chale.
  * **Performance:** Application **fast aur responsive** ho. User ko page load ya result ke liye wait na karna pade.
  * **Maintainability:** Future mein naye features add karna ya bugs fix karna **aasan** ho. Code aapas mein uljha hua (spaghetti code) na ho.
  * **Cost-Effectiveness:** System ko chalane ka kharcha (server cost, etc.) control mein rahe.

**Problem Solved:** Ye "bas code likh do" wali thinking se aage jaakar ek robust, scalable, aur reliable product banane mein help karta hai.

-----

#### **3. How it works (Kaise Kaam Karta Hai?)**

System Design ek step-by-step process hai:

**Step 1: Requirement Gathering (Zaroorat Samajhna)**
Sabse pehle hum ye samajhte hain ki banana kya hai. Isme do tarah ki requirements hoti hain:

  * **Functional Requirements:** System ko *kya karna chahiye*. (e.g., User should be able to upload a photo).
  * **Non-Functional Requirements (NFRs):** System ko *kaise perform karna chahiye*. (e.g., Photo 2 second mein upload ho jaani chahiye, system 99.99% time available hona chahiye). **System design ka main focus NFRs par hota hai.**

**Step 2: High-Level Design (HLD) - The Bird's-Eye View**
Ye ek Mota-mota design hai. Hum system ka ek block diagram banate hain.

  * "Ek Load Balancer hoga."
  * "Uske peeche 5 web servers honge."
  * "Ek User database hoga aur ek Photos ka database hoga."
  * "Photos store karne ke liye S3 jaisa storage use karenge."

<!-- end list -->

```
           [User]
             |
      [Load Balancer]
             |
    /--------|--------\
 [Web Svr] [Web Svr] [Web Svr]
    \--------|--------/
             |
    /--------+--------\
[User DB]         [Photo Storage]
(MySQL)               (S3)
```

Is level par hum technology (e.g., MySQL vs. Cassandra) aur major components decide karte hain. **Yahi HLD ka goal hai: ek macro-level architecture define karna jo scalability, availability jaisi requirements poori kar sake.**

**Step 3: Low-Level Design (LLD) - Zooming In**
Ab hum har component ke andar jaate hain.

  * Database ka schema kya hoga? (Tables, columns, relationships).
  * Kis class mein kaun se functions honge?
  * APIs ke request aur response format kya honge? (e.g., `POST /api/v1/users/create`).

Ye design actual code ke bahut close hota hai.

-----

#### **4. Key Concepts & Variants (Important Baatein)**

Is introduction mein 3 cheezein samajhna sabse zaroori hai:

  * **High-Level Design (HLD):**

      * **What:** System ka overall architecture (macro-view).
      * **Focus:** Big picture, components aur unke interactions.
      * **Also called:** Architectural Design.
      * **Analogy:** Sheher ka map (Map of the city).

  * **Low-Level Design (LLD):**

      * **What:** Har ek component ka internal working (micro-view).
      * **Focus:** Class diagrams, database schemas, API contracts.
      * **Also called:** Detailed Design.
      * **Analogy:** Ghar ke ek kamre ka interior design plan.

  * **Server:**

      * **What:** Server ek powerful computer hai jo hamesha (24/7) on rehta hai aur internet se connected hota hai.
      * **Job:** Uska kaam "serve" karna hai - yaani client (aapka phone, laptop) ke requests ko process karke response (data, webpage) bhejna. Jab aap `google.com` kholte ho, toh aapka browser Google ke server ko ek request bhejta hai.

-----

#### **5. Trade-offs (Samjhaute)**

System Design mein koi bhi "perfect" solution nahi hota. Har decision ke apne fayde aur nuksaan hote hain. Ise hi **trade-off** kehte hain. Ek achha designer in trade-offs ko samajhta hai.

  * **Consistency vs. Availability (CAP Theorem):** Kya aapko hamesha latest data chahiye (strong consistency) ya system hamesha available rahe, bhale hi data thoda purana dikhe (eventual consistency)?
  * **Performance vs. Cost:** System ko super-fast banane ke liye aapko mehnge servers lene padenge, jisse cost badhega.
  * **Read vs. Write Performance:** Ek database design read operations ke liye fast ho sakta hai, par write ke liye slow, and vice-versa. Aapko choose karna padega ki aapke use case ke liye kya zyada important hai.

-----

#### **6. Real-world usage (Asli Duniya Mein Istemal)**

  * **Netflix:** Jab aap video dekhte hain, unka system design (HLD) ensure karta hai ki video aapke sabse paas wale server (CDN) se aaye taaki buffering na ho.
  * **Uber:** Unka HLD real-time mein laakhon drivers aur riders ki location ko manage karta hai aur unhe low latency mein match karta hai.
  * **Amazon:** Unka HLD Black Friday sale jaise events par aane wale massive traffic ko handle karne ke liye auto-scaling use karta hai, aur LLD har product ki inventory ko manage karta hai.

-----


#### **8. Crisp Summary Table (Revision Ke Liye)**

| Concept | Why needed (Kyun Zaroori Hai) | Example (Udahaaran) | Trade-off (Samjhauta) |
| :--- | :--- | :--- | :--- |
| **High-Level Design (HLD)** | To create a scalable & reliable architecture (bada naksha banana). | Deciding to use a Load Balancer, 3 Web Servers, and a PostgreSQL DB. | Choosing a NoSQL DB for scalability might sacrifice ACID properties. |
| **Low-Level Design (LLD)** | To detail the implementation of each component (chhoti details). | Designing the `User` table schema; defining the `/login` API endpoint. | Normalizing a DB schema for data integrity might make read queries slower. |
| **Server** | To process requests and serve data to clients 24/7. | A computer running Apache web server software to host a website. | Using more powerful servers increases performance but also costs more. |

----

### **Topic: Capacity and Estimation (Andaaza Lagana)**

#### **1. Definition / Introduction (Ye Hai Kya?)**

**Capacity Estimation** (jise **Back-of-the-envelope Estimation** bhi kehte hain) ek aisi technique hai jisse hum system ki zarooraton ka ek **rough idea** lagate hain. Isme hum precise calculations nahi karte, balki **smart assumptions** (samajhdari bhare anumaan) aur **simple math** ka use karke andaza lagate hain ki:

* System par kitna **load** aayega (kitne users request bhejenge)?
* Kitna **storage** lagega (data save karne ke liye kitni jagah chahiye)?
* Kitne **resources** lagenge (kitne servers, kitna network bandwidth)?

Socho aap ek party plan kar rahe ho. Aap pehle andaza lagaoge, "Lagbhag 50 log aayenge, har koi 2 plate khana khayega, toh mujhe 100 plate ka order dena hai." Yeh party ke liye capacity estimation hai. Software mein hum users, data, aur servers ke liye same cheez karte hain.

---

#### **2. Why it matters (Kyun Zaroori Hai?)**

Interviewers yeh aapse isliye puchte hain kyunki isse aapki **scale-thinking ability** test hoti hai. Yeh do badi problems solve karta hai:

1.  **Under-provisioning (Kam Taiyaari):** Agar aapne socha 100 users aayenge aur 10,000 aa gaye, toh aapka system crash ho jaayega. Jaise party mein khana kam pad gaya.
2.  **Over-provisioning (Fizool Kharchi):** Agar aapne 10,000 users ke liye servers khareed liye aur aaye sirf 100, toh company ka bahut paisa barbaad hoga. Jaise party mein dher saara khana bach gaya.

Capacity estimation in dono extremes ke beech ek **sweet spot** find karne mein help karta hai, taaki system reliable bhi ho aur cost-effective bhi.

---

#### **3. How it works (Kaise Kaam Karta Hai?)**

Ise "Back-of-the-envelope" isliye kehte hain kyunki yeh calculations itni simple honi chahiye ki aap unhe ek tissue paper ya envelope ke peeche likh sako.

**Example: Let's estimate for a simple Photo Sharing App (like basic Instagram).**

**Step 1: Ask Clarifying Questions & Make Assumptions (Sawaal Pucho aur Maan Lo)**
* Total users kitne hain? **Maan lo, 10 Million users.**
* Daily Active Users (DAU) kitne hain? **Maan lo, 1 Million (10%).**
* Ek user din mein kitni photos upload karta hai? **Maan lo, average 0.2 photos/day (yaani 5 din mein 1 photo).**
* Ek user din mein kitni photos dekhta hai (scrolls feed)? **Maan lo, 100 photos/day.**
* Ek photo ka average size kya hai? **Maan lo, 1 MB.**

**Step 2: Load Estimation (Requests ka Andaza)**
* **Write Load (Uploads):**
    * 1 Million DAU * 0.2 photos/day = 200,000 photos uploaded per day.
    * Queries Per Second (QPS) = 200,000 / (24 hours * 3600 sec) ≈ **2.3 QPS.** (Yeh average hai, peak isse 2x ya 3x ho sakta hai).
* **Read Load (Feed Scroll):**
    * 1 Million DAU * 100 photos/day = 100 Million photos viewed per day.
    * Read QPS = 100,000,000 / (24 * 3600) ≈ **1160 QPS.**
* **Read to Write Ratio:** 1160 / 2.3 ≈ 500:1. Yeh system **Read-Heavy** hai.

**Step 3: Storage Estimation (Jagah ka Andaza)**
* Daily new storage = 200,000 photos/day * 1 MB/photo = 200,000 MB/day = **200 GB/day.**
* Yearly storage = 200 GB/day * 365 days ≈ **73 TB/year.**
* Storage for 5 years = 73 TB/year * 5 years ≈ **365 TB.**

**Step 4: Resource Estimation (Bandwidth ka Andaza)**
* **Egress (Data Out):** Jab users photos dekhte hain.
    * 100 Million reads/day * 1 MB/photo = 100 TB of data served per day.
    * Bandwidth = 100 TB / (24 * 3600s) ≈ 1.16 GB/s.
* **Ingress (Data In):** Jab users photos upload karte hain.
    * 200 GB of data uploaded per day.
    * Bandwidth = 200 GB / (24 * 3600s) ≈ 2.3 MB/s.

In numbers se hum andaza laga sakte hain ki humein kitne servers aur kitna network chahiye.

---

#### **4. Key Concepts & Variants (Important Baatein)**

* **Load Estimation:** Iska goal hota hai **QPS (Queries Per Second)** nikalna. Hamesha **Read QPS** aur **Write QPS** alag-alag calculate karo. Yeh bhi dhyan rakho ki **peak QPS** (din ke sabse busy time ka load) average QPS se 2-5 guna zyada ho sakta hai.
* **Storage Estimation:** Isme hum calculate karte hain ki text, images, videos, etc. ko store karne ke liye kitni disk space chahiye. Hamesha **5-10 saal ke growth** ke liye plan karo.
* **Resource Estimation:**
    * **Bandwidth:** Network traffic ka andaza (Ingress/Egress).
    * **Compute (Servers):** Load (QPS) ko handle karne ke liye kitne servers chahiye. Example: Agar ek server 500 QPS handle kar sakta hai aur hamara peak load 2000 QPS hai, to humein 2000/500 = 4 servers chahiye (plus extra for backup).

---

#### **5. Trade-offs (Samjhaute)**

* **Peak Load vs. Average Load:** Agar aap peak load (e.g., New Year's Eve traffic) ke liye servers khareedte hain, toh woh saal ke baaki din khaali rahenge (high cost). Agar average load ke liye plan karte hain, toh peak time par system crash ho jaayega (bad reliability). Solution: **Auto-scaling**.
* **Accuracy vs. Speed:** Aap ghanton laga kar ekdum precise estimation kar sakte hain, ya 5 minute mein ek rough idea le sakte hain. Interview mein, aapse **speed aur smart assumptions** expect ki jaati hai, perfect accuracy nahi.
* **Planning for Growth (Future Proofing vs. Cost):** 5 saal ke growth ke liye planning karna safe hai, par iska matlab hai shuru mein zyada paisa invest karna padega.

---

#### **6. Real-world usage (Asli Duniya Mein Istemal)**

* **YouTube:** Har minute 500+ ghante ka video upload hota hai. Unhe constantly estimate karna padta hai ki itne video ko store karne, process karne (transcode), aur stream karne ke liye kitna storage, compute power aur bandwidth lagega.
* **Hotstar:** IPL final match ke time, woh pehle se capacity plan karte hain ki crores of concurrent users ko handle karne ke liye kitne servers aur CDN capacity chahiye.
* **Cloud Providers (AWS, Azure, GCP):** Inka poora business hi capacity estimation par chalta hai. Woh estimate karte hain ki duniya bhar ke clients ko kitne resources ki zaroorat padegi aur usi hisaab se data centers banate hain.

---

#### **7. Interview Angle (Interview Ke Liye)**

**How to approach an estimation question:**

1.  **Don't panic and jump to calculations.** Hamesha clarifying questions pucho.
2.  State your assumptions clearly. Bolo, "Let's assume the DAU is 10 Million... Is that a reasonable assumption to start with?"
3.  Calculations ko simple rakho. `1,048,576` ki jagah `1 Million` use karo. `24*3600` ko `86,400` ya seedhe `~85,000` likh do.
4.  Break the problem down into Load, Storage, and Bandwidth.
5.  End mein apne result ko summarize karo aur possible bottlenecks (kahan dikkat aa sakti hai) batao.

**Sample Q&A:**
* **Interviewer:** "Design Twitter's backend."
* **You:** "Okay. Before diving into the components, let's do a quick capacity estimation to understand the scale we are dealing with. Can I assume around 300 Million DAU and each user tweets about twice a week on average?"
    * *This shows you think about scale first.*

**Numbers to remember (Approximate):**
* 1 character = 1 byte
* 1 Integer = 4 bytes
* URL = ~100 bytes
* Small Image = 100s of KB
* HD Image / Short Video = 1-5 MB
* 1 Million = 10^6
* 1 Billion = 10^9

---

#### **8. Crisp Summary Table (Revision Ke Liye)**

| Concept | Why needed (Kyun Zaroori Hai) | Example (Udahaaran) | Key Metric |
| :--- | :--- | :--- | :--- |
| **Load Estimation** | To calculate how many servers we need. (Server ki ginti) | Calculating requests for Twitter's timeline feed. | **QPS** (Queries Per Second) |
| **Storage Estimation** | To calculate how much disk space is needed. (Data ki jagah) | Calculating storage for 5 years of YouTube video uploads. | **TB / PB** (Terabytes / Petabytes) |
| **Resource Estimation** | To calculate network usage and other infra needs. (Network aur baaki cheezein) | Calculating bandwidth needed for Netflix streaming. | **GB/s** (Gigabytes per second) |

---

### **Topic: Networking Fundamentals (System Ki Baatcheet Ke Niyam)**

#### **1. Definition / Introduction (Ye Hai Kya?)**

**Networking Fundamentals** woh rules (niyam) aur methods hain jinko use karke ek system ke alag-alag computers ya components aapas mein communicate (baat) karte hain.

Socho, agar aapko kisi doosre desh mein चिट्ठी bhejni hai. Aapko unka address likhne ka format, pin code, aur postal service ke rules pata hone chahiye. Agar nahi pata, toh चिट्ठी kabhi nahi pahuchegi.

Bilkul waise hi, networking protocols (jaise HTTP, TCP/IP) woh **common language aur rules** hain jinko follow karke aapka browser (client) Google ke server se baat kar paata hai. Ye fundamentals inhi rules ki padhai hai.

---

#### **2. Why it matters (Kyun Zaroori Hai?)**

System design mein, aap components ko boxes mein draw karte hain. Lekin un boxes ko aapas mein jodne wali lines (communication) sabse zaroori hain. Agar yeh communication efficient aur reliable nahi hai, toh system fail ho jaayega.

Yeh isliye matter karta hai:
* **Interoperability:** Alag-alag companies (Google, Apple) aur alag-alag technologies (Java, Python) se bane systems aapas mein aaram se baat kar paate hain.
* **Reliability:** Yeh ensure karta hai ki bheja hua data sahi salamat, bina corrupt hue, receiver tak pahuche (jaise TCP).
* **Scalability:** Sahi protocol choose karke hi aap apne system ko millions of users tak scale kar sakte hain.
* **Performance:** Yeh decide karta hai ki aapka system kitna fast aur responsive hoga.

Bina networking ke, har application ek isolated island ki tarah hota. Networking hi unhe jodkar "internet" banata hai.

---

#### **3. How it works (Kaise Kaam Karta Hai?)

Isko samajhne ka sabse achha tareeka hai classic interview question: **"What happens when you enter Google.com in your browser?"**

Yeh poori story networking fundamentals ko action mein dikhati hai:

**Step 1: DNS Lookup (Address Pata Karna)**
* Aapne browser mein `google.com` type kiya. Computer ko `google.com` samajh nahi aata, use **IP Address** chahiye (e.g., `142.250.195.46`), jaise aapko kisi ke ghar jaane ke liye naam nahi, address chahiye.
* Browser pehle apni **cache** mein dekhta hai. Address nahi mila toh OS se poochta hai. Wahan bhi nahi mila toh internet par ek **DNS Server** (Internet's Phonebook) se `google.com` ka IP address poochta hai.

**Step 2: TCP Connection (Connection Banana)**
* IP address milne ke baad, aapka browser Google ke server ke saath ek connection banata hai. Yeh **TCP (Transmission Control Protocol)** ka use karke hota hai.
* Is process ko **Three-Way Handshake** kehte hain:
    1.  **SYN:** Aapka browser kehta hai, "Hi, main aapse baat karna chahta hoon."
    2.  **SYN-ACK:** Server kehta hai, "Okay, main taiyaar hoon. Kya aap bhi ho?"
    3.  **ACK:** Browser kehta hai, "Haan, main bhi taiyaar hoon. Chalo shuru karein."
* Ab ek reliable connection ban gaya hai.

**Step 3: HTTP Request (Jaankari Maangna)**
* Connection banne ke baad, browser server ko ek **HTTP (Hypertext Transfer Protocol)** `GET` request bhejta hai. Request mein likha hota hai, "Mujhe `google.com` ka homepage do."

**Step 4: HTTP Response (Jaankari Dena)**
* Google ka server request ko process karta hai aur ek **HTTP Response** wapas bhejta hai. Is response mein `200 OK` status code (sab a
chha hai) aur homepage ka HTML content hota hai.

**Step 5: Rendering (Page Dikhana)**
* Browser us HTML ko process karke aapko sundar sa Google ka page dikha deta hai.



---

#### **4. Key Concepts & Variants (Important Baatein)**

* **Communication Protocols:** Ye bas set of rules hain. Jaise insanon ke liye "Namaste" ya "Hello" bolne ka rule hai, waise hi computers ke liye protocols hain.
* **TCP/IP Stack:** Yeh internet ka core rulebook hai. Isme 4 layers hoti hain, par system design ke liye 2 sabse important hain:
    * **TCP (Transmission Control Protocol):** Iska kaam hai **reliable delivery**. Ye data ko chote-chote packets mein todta hai, un par number likhta hai, aur ensure karta hai ki saare packets sahi order mein receiver tak pahuche. Agar koi packet kho jaaye, toh ye use dobara bhejta hai.
    * **IP (Internet Protocol):** Iska kaam hai **addressing**. Ye har packet par sender aur receiver ka IP address lagata hai, taaki routers ko pata chale ki packet ko kahan bhejna hai.
* **Domain Name System (DNS):** Ye **internet ki phonebook** hai. Ye human-readable domain names (`google.com`) ko machine-readable IP addresses (`142.250.195.46`) mein translate karta hai.
    * **DNS Caching:** Speed badhane ke liye, aapka browser aur OS haal hi mein visit ki gayi sites ke IP addresses ko kuch der ke liye save kar lete hain.
    * **Time To Live (TTL):** Ye ek value hai jo batati hai ki ek DNS record ko cache mein kitni der tak rakhna hai. TTL ke baad, cache ko record dobara fetch karna padega.
* **HTTP (Hypertext Transfer Protocol):** Yeh web ka protocol hai. Ye ek **request-response** model par kaam karta hai. Client hamesha request shuru karta hai aur server response deta hai. Ye **stateless** hota hai, yaani server har request ko ek nayi request maanta hai aur pichli request ko yaad nahi rakhta.
* **WebSockets:** Yeh ek modern protocol hai jo **full-duplex** (two-way) communication allow karta hai. Client aur server ke beech ek connection hamesha khula rehta hai, aur dono taraf se koi bhi kabhi bhi data bhej sakta hai. Isme server client ko **push** kar sakta hai.
* **Pull vs. Push:**
    * **Pull (Client-driven):** Client server se data "kheenchta" (pull) hai. HTTP iska perfect example hai. (e.g., Aap browser refresh karke naya score poochte ho).
    * **Push (Server-driven):** Server client ko data "dhakelta" (push) hai jab bhi kuch naya aata hai. WebSockets iska perfect example hai. (e.g., Cricbuzz ka live score apne aap update ho jaata hai).

---

#### **5. Trade-offs (Samjhaute)**

* **HTTP vs. WebSockets:**
    * **HTTP:** Simple, har jagah supported hai, aur short interactions ke liye a
chha hai. Lekin real-time updates ke liye inefficient hai kyunki client ko baar-baar server se poochna padta hai ("kuch naya aaya?"). Isse overhead badhta hai.
    * **WebSockets:** Real-time updates (chat, gaming, live data) ke liye bahut efficient hai. Par ye hamesha ek connection open rakhta hai, jisse server par resource usage badh jaata hai.
* **TCP vs. UDP (A related trade-off):**
    * **TCP:** **Reliable** but slower. File download, email ke liye a
chha hai jahan har bit important hai.
    * **UDP:** **Fast** but unreliable (packets kho sakte hain). Video streaming, online gaming ke liye a
chha hai jahan speed zaroori hai aur ek-do frame ka loss chal jaayega.

---

#### **6. Real-world usage (Asli Duniya Mein Istemal)**

* **HTTP:** Aap jo bhi website browse karte hain (Facebook, Amazon, Google).
* **DNS:** Internet par har ek connection ka pehla step.
* **WebSockets:** **WhatsApp Web** (messages instantly aate hain), **Google Docs** (aap doosre logon ko live type karte hue dekhte hain), **Zerodha/Upstox** (live stock prices automatically update hote hain).
* **TCP/IP:** The backbone of the entire internet. Har email, web page, file transfer ise use karta hai.

---



### **Communication Protocols (Baatcheet Ke Niyam)**

* **Yeh Hai Kya? (What it is)**
    A protocol, yaani ek niyam-pustika. Ye नियमों (rules) ka ek set hai jo define karta hai ki do ya do se zyada devices aapas mein data kaise exchange karenge. Ye computers ki "grammar" aur "vocabulary" hai.

* **Kyun Zaroori Hai? (Why it's important)**
    Bina protocol ke, communication mein chaos (gadbadi) ho jaayegi. Apple ka banaya iPhone, Google ke server se isliye baat kar paata hai kyunki dono ek common protocol (jaise HTTP, TCP/IP) follow karte hain. Ye interoperability (aapsi taal-mel) sunishchit karta hai.

* **Mukhya Baatein (Key Characteristics)**
    Ek protocol teen cheezein define karta hai:
    1.  **Syntax:** Data ka format kya hoga (e.g., pehle 8 bits mein sender ka address hoga).
    2.  **Semantics:** Har data block ka matlab kya hoga (e.g., address wale block ka matlab hai "ye data yahan se aaya hai").
    3.  **Timing:** Data kab aur kitni tezi se bheja jayega.

---

### **The Internet TCP/IP Stack**

* **Yeh Hai Kya? (What it is)**
    Yeh protocols ka ek collection (suite) hai jo internet ki buniyad hai. Isko internet ki "Rulebook" bhi keh sakte hain. Ye communication ko 4 logical layers mein todta hai, jahan har layer ka apna ek kaam hota hai.

* **Kyun Zaroori Hai? (Why it's important)**
    Ye poore internet ke liye ek standard model pradaan karta hai. Iski wajah se hi data reliably ek jagah se doosri jagah ja paata hai, chahe network kitna bhi bada ya complex kyun na ho.

* **Kaise Kaam Karta Hai? (How it works)**
    Iske do sabse zaroori protocols hain:
    1.  **IP (Internet Protocol):** Iska kaam hai **addressing aur routing**. Har data packet par ye sender aur receiver ka IP address lagata hai, taaki routers ko pata chale ki packet ko kis raaste se bhejna hai. Ye ek postman ki tarah hai jo address padh kar चिट्ठी deliver karta hai.
    2.  **TCP (Transmission Control Protocol):** Iska kaam hai **reliable delivery**. Ye bade data ko chote-chote packets mein todta hai, un par sequence number lagata hai, aur guarantee deta hai ki saare packets sahi-salamat, sahi order mein receiver tak pahunche. Agar koi packet kho jaata hai, to TCP use dobara bhejta hai. Ye ek registered post ki tarah hai jo delivery confirmation bhi leta hai.

---

### **HTTP (Hypertext Transfer Protocol)**

* **Yeh Hai Kya? (What it is)**
    Yeh World Wide Web ka protocol hai. Isko use karke browser web server se resources (jaise web pages, images) maangta hai. Ye ek restaurant ke waiter ki tarah hai: aap order (request) dete hain, aur woh khana (response) laata hai.

* **Kaise Kaam Karta Hai? (How it works)**
    Ye ek **Request-Response** model par chalta hai.
    1.  **Client (Browser)** ek request bhejta hai (e.g., `GET /page.html`).
    2.  **Server** us request ko process karke ek response bhejta hai (e.g., `200 OK` status code aur page ka HTML).

* **Mukhya Baatein (Key Characteristics)**
    * **Stateless (Yaaddasht Kamzor):** Server har request ko ek naya maanta hai aur pichle requests ke baare mein kuch yaad nahi rakhta.
    * **Methods:** `GET` (data paane ke liye), `POST` (data submit karne ke liye), `PUT` (data update karne ke liye), `DELETE` (data hatane ke liye).

* **Kahan Istemal Hota Hai? (Use Cases)**
    Aap internet par jo bhi website kholte hain, ya jo REST APIs use karte hain, woh sab HTTP par chalta hai. Iska trade-off ye hai ki ye real-time communication ke liye a
chha nahi hai.

---

### **Domain Name System (DNS)**

* **Yeh Hai Kya? (What it is)**
    Yeh internet ki **Phonebook** hai. Iska kaam hai aasan-se-yaad-hone-waale domain names (jaise `google.com`) ko computers ke samajhne laayak IP addresses (jaise `142.250.195.46`) mein translate karna.

* **Kyun Zaroori Hai? (Why it's important)**
    Insaan naam yaad rakhne mein a
chhe hain, aur computers number. DNS iske beech ka pul hai. Agar DNS na hota, to humein har website ke liye lambe-lambe IP addresses yaad karne padte.

* **Mukhya Baatein (Key Characteristics)**
    * **DNS Caching:** DNS lookups ko fast karne ke liye, aapka browser, Operating System, aur routers haal hi mein khoje gaye IP addresses ko kuch der ke liye save (cache) kar lete hain. Isse baar-baar phonebook dekhne ki zaroorat nahi padti.
    * **Time To Live (TTL):** Ye ek value hai jo batati hai ki ek DNS record ko cache mein kitni der tak rakhna hai. TTL expire hone ke baad, cache ko IP address dobara se confirm karna padega.

---

### **WebSockets**

* **Yeh Hai Kya? (What it is)**
    Yeh ek advanced protocol hai jo client aur server ke beech ek **lagatar, do-tarfa (two-way)** communication channel banata hai. Iski tulna ek phone call se kar sakte hain jo hamesha connected rehta hai, jahan koi bhi kabhi bhi bol sakta hai.

* **Kyun Zaroori Hai? (Why it's important)**
    Ye HTTP ki us kami ko door karta hai jahan server client se khud baat shuru nahi kar sakta. WebSockets se server client ko data **push** kar sakta hai, jo real-time applications ke liye zaroori hai.

* **Kaise Kaam Karta Hai? (How it works)**
    Connection ek normal HTTP request se shuru hota hai jise "upgrade" karke WebSocket connection bana diya jaata hai. Ek baar banne ke baad, ye TCP connection hamesha khula rehta hai.

* **Kahan Istemal Hota Hai? (Use Cases & Trade-offs)**
    Chat applications (WhatsApp Web), live collaboration tools (Google Docs), online gaming, aur live stock tickers mein. Iska trade-off ye hai ki har open connection server par memory aur resources use karta hai.

---

### **Pull vs. Push Communication**

* **Yeh Hai Kya? (What it is)**
    Ye data exchange ke do alag-alag models hain:
    1.  **Pull (Kheenchna):** Client ek set interval par server se poochta rehta hai, "Kya koi naya data hai?". Isko **Polling** bhi kehte hain. **HTTP** ek pull-based protocol hai.
    2.  **Push (Dhakelna):** Server, jab bhi uske paas naya data aata hai, khud se client ko bhej deta hai. Client ko poochne ki zaroorat nahi padti. **WebSockets** isko aasan banate hain.

* **Kyun Zaroori Hai? (Why it's important)**
    Sahi model chunna system ki efficiency aur performance par bahut bada asar daalta hai.

* **Samjhaute (Trade-offs)**
    * **Pull** implement karna aasan hai, lekin isme delay ho sakta hai aur bekaar ki requests bhi jaati hain (jab koi naya data na ho).
    * **Push** real-time hai aur efficient hai, lekin implement karna thoda complex hai aur server par lagatar connection ka bojh rehta hai.

---

### **Network Proxies**

* **Yeh Hai Kya? (What it is)**
    Proxy ek **beech ka server (intermediary)** hai jo client aur end-server ke beech baithta hai. Aapki request pehle proxy ke paas jaati hai, fir proxy use aage bhejta hai. Ye ek company ke receptionist ki tarah hai.

* **Kyun Zaroori Hai? (Why it's important)**
    Proxies ko Security, Caching, Load Balancing, aur anonymity (pehchan chupane) ke liye istemal kiya jaata hai.

* **Mukhya Prakaar (Key Types)**
    1.  **Forward Proxy:** Ye **client ke behalf par** kaam karta hai. Ye client ke network ke andar hota hai, jaise school ya company ka internet gateway jo content filter karta hai.
    2.  **Reverse Proxy:** Ye **server ke behalf par** kaam karta hai. Ye server ke aage baithta hai aur saare incoming client requests ko handle karta hai. Ye Load Balancing, SSL termination, aur caching ke liye istemal hota hai. Jab aap `amazon.in` visit karte hain, to aap seedhe application server se nahi, balki ek reverse proxy se baat karte hain.

---

### **What happens when you enter Google.com? (Sab Kuch Ek Saath)**

Ye ek process hai jo upar bataye gaye kai concepts ko ek saath jodta hai:

1.  **Aap `google.com` type karte hain.**
2.  **DNS Lookup:** Browser `google.com` ka IP address dhoondne ke liye DNS protocol ka istemal karta hai. Is dauraan, ye pehle **DNS Caches** check karta hai.
3.  **TCP Connection:** IP address milne par, browser TCP/IP stack ka istemal karke Google ke server (ya uske **Reverse Proxy**) ke saath ek reliable TCP connection banata hai.
4.  **HTTP Request:** Connection banne par, browser **HTTP** protocol ka istemal karke ek `GET` request bhejta hai.
5.  **Server Response:** Server request ko process karke ek HTTP response (HTML, CSS, JavaScript files ke saath) bhejta hai.
6.  **Page Render:** Browser us content ko render karke aapko search page dikha deta hai.

---



### **What is Load Balancing? (Traffic Ko Baantna)**

  * **Yeh Hai Kya? (What it is)**
    Load Balancer ek traffic police-wala ya ek receptionist ki tarah hai jo incoming network traffic (user requests) ko aage multiple servers ke beech mein **divide (baant)** deta hai. Iska kaam ye sunishchit karna hai ki koi ek server akele saare requests ke bojh tale dab na jaaye.

    Soch lijiye, ek supermarket mein 10 checkout counters hain, lekin saare customers sirf counter \#1 par line laga rahe hain. Counter \#1 par bahut bheed ho jaayegi aur baaki 9 khaali rahenge. Ek smart manager (Load Balancer) aayega aur customers ko alag-alag counters par bhejega, taaki sabka kaam jaldi ho jaaye.

    ```
                [User Requests]
                      |
              [LOAD BALANCER]
                      |
        /-------------+-------------\
        |             |             |
    [Server 1]    [Server 2]    [Server 3]
    (Handles      (Handles      (Handles
     some load)    some load)    some load)
    ```

  * **Kyun Zaroori Hai? (Why do we need it)**
    Load Balancer do mukhya (main) problems solve karta hai:

    1.  **High Availability & Fault Tolerance (System Hamesha Chalta Rahe):**
        Agar aapke paas sirf ek server hai aur woh crash ho jaaye, toh aapki poori application band ho jaayegi. Isse **Single Point of Failure** kehte hain.
        Load Balancer lagatar servers ki "health check" karta rehta hai. Agar koi server down ya unhealthy ho jaata hai, toh Load Balancer uss par traffic bhejna band kar deta hai aur requests ko sirf healthy servers par bhejta hai. Isse users ko pata bhi nahi chalta ki backend mein koi server fail ho gaya hai.

    2.  **Scalability & Performance (Zyada Load Sambhalna):**
        Ek akele server ki traffic handle karne ki ek limit hoti hai. Jab users badhte hain, toh aapko **horizontally scale** karna padta hai, yaani system mein aur servers add karne padte hain.
        Load Balancer is naye server ko apne pool mein shaamil kar leta hai aur us par bhi traffic bhejna shuru kar deta hai. Isse aap asani se millions of users ka traffic handle kar sakte hain aur sabhi users ko fast response time milta hai.

-----

### **Load Balancer Algorithms (Traffic Baantne Ke Tareeke)**

Load Balancer ye kaise decide karta hai ki agla request kis server ko bhejna hai? Iske liye woh kuch algorithms use karta hai. Yahan 4 popular algorithms hain:

1.  **Round Robin (Sabko Ek-Ek Karke Mauka)**

      * **Kaise Kaam Karta Hai:** Ye sabse simple tareeka hai. Load Balancer servers ki ek list banata hai aur requests ko ek-ek karke har server ko bhejta hai. Pehla request Server 1 ko, doosra Server 2 ko, teesra Server 3 ko, aur fir wapas Server 1 ko. Ye process chalta rehta hai.
      * **Kab Use Karein:** Jab saare servers lagbhag ek jaise powerful hon aur har request ko process karne mein lagbhag same time lagta ho.
      * **Kami (Limitation):** Ye server ki current load ya health ko nahi dekhta. Agar Server 1 already busy hai, toh bhi ye usko naya request bhej dega.

2.  **Least Connections (Jo Sabse Free Hai, Uske Paas Jao)**

      * **Kaise Kaam Karta Hai:** Ye algorithm har server ke active connections (kitne requests abhi handle kar raha hai) ka track rakhta hai. Jab naya request aata hai, toh ye use uss server ko bhejta hai jiske paas uss samay sabse kam active connections hote hain.
      * **Kab Use Karein:** Jab requests ko process karne ka time alag-alag ho sakta hai. Ye ensures karta hai ki koi server aalsi na baithe jabki doosra over-loaded ho. Ye Round Robin se zyada intelligent hai.

3.  **IP Hash (Client Ko Hamesha Ek Hi Server Se Jodo)**

      * **Kaise Kaam Karta Hai:** Ye client ki IP address ka ek "hash" (ek unique number) nikalta hai aur uss hash ke basis par decide karta hai ki request kis server par jaayegi. Iska fayda ye hai ki ek particular client (same IP address) ki saari requests hamesha ek hi server par jaayegi.
      * **Kab Use Karein:** Jab aapko **session persistence** (ya "sticky sessions") chahiye ho. For example, ek e-commerce site mein, agar user ne apna shopping cart ek server par banaya hai, toh uski agali request bhi usi server par jaani chahiye taaki uska cart data na kho jaaye.
      * **Kami (Limitation):** Agar koi server down ho jaata hai, toh uss server se jude saare users ka session data chala jaayega. Also, agar kuch IP addresses se bahut zyada traffic aa raha hai (e.g., ek bade office se), toh distribution uneven ho sakta hai.

4.  **Least Response Time (Jo Sabse Jaldi Jawab De Raha Hai)**

      * **Kaise Kaam Karta Hai:** Ye ek advanced tareeka hai. Ye na sirf active connections ko dekhta hai, balki har server ke average response time ko bhi measure karta hai. Ye naye request ko uss server par bhejta hai jo currently sabse kam loaded hai aur sabse fast respond kar raha hai.
      * **Kab Use Karein:** Jab aapko best possible performance (lowest latency) chahiye ho. Ye server ki current health aur load dono ko consider karta hai.

-----

### **Consistent Hashing**

  * **Yeh Hai Kya? (What it is)**
    Consistent Hashing ek special tarah ka hashing algorithm hai. Normal hashing (jaise IP Hash) mein ek badi problem hoti hai: agar aap ek naya server add karte hain ya ek purana server hataate hain, toh bahut saari existing keys (ya users) ko naye servers par re-map karna padta hai. Isse system mein ek bada disruption hota hai.

    **Consistent Hashing** is problem ko solve karta hai. Ye ek aisi technique hai jismein server add ya remove karne par sirf ek chota sa fraction of keys ko hi move karne ki zaroorat padti hai, baaki sab apni jagah par rehte hain.

  * **Kyun Zaroori Hai? (Why it's important)**
    Ye distributed caching systems (jaise Memcached, Redis), databases (Cassandra, Riak), aur load balancers mein bahut zaroori hai. Iske bina, server pool ko scale up ya scale down karna (server add/remove karna) ek bahut mehenga aur disruptive operation ban jaata hai.

  * **Kaise Kaam Karta Hai? (Analogy)**
    Imagine kijiye ek clock (ghadi) hai.

    1.  Hum servers (S1, S2, S3) ko is ghadi par alag-alag points par rakh dete hain (e.g., S1 @ 2 baje, S2 @ 6 baje, S3 @ 10 baje).
    2.  Jab ek naya request (key) aata hai, hum usko bhi ghadi par kahin place karte hain (e.g., Key K1 @ 4 baje).
    3.  Us key ko handle karne ke liye, hum ghadi par **clockwise** (seedhi disha mein) chalte hain aur jo server sabse pehle milta hai, woh uss key ko handle karta hai. Is case mein, K1 (4 baje) ke baad clockwise chalne par S2 (6 baje) sabse pehle aayega. Toh K1, Server S2 ko assign ho jaayega.

    **Fayda (The Magic):**
    Ab socho hum ek naya server **S4 @ 8 baje** add karte hain. Isse sirf woh keys prabhavit hongi jo S2 (6 baje) aur S4 (8 baje) ke beech mein aati hain. Baaki saari keys (jo S1, S3, ya S2 ke paas thi) apni jagah par hi rahengi. Isse **disruption minimize** ho jaata hai.

---

### **Database Fundamentals**

#### **Relational Databases (SQL)**

* **Yeh Hai Kya? (What it is)**
    A Relational Database, jise SQL (Structured Query Language) database bhi kehte hain, data ko ek bahut hi **structured tareeke** se store karta hai, bilkul ek Excel spreadsheet ki tarah. Data **tables** mein store hota hai, jismein **rows** (records) aur **columns** (attributes) hote hain. Har table ka ek pehle se defined **schema** (structure) hota hai. 
* **Kyun Zaroori Hai? (Why it's important)**
    Ye data ki **consistency** aur **integrity** (shuddhta) ko banaye rakhte hain. Inmein **ACID properties** (Atomicity, Consistency, Isolation, Durability) hoti hain, jo transactions ke liye bahut zaroori hain. Jaise bank transfer mein, ya to poora transaction (paisa katna aur jama hona) hoga, ya kuch bhi nahi hoga.
* **Examples:** MySQL, PostgreSQL, Microsoft SQL Server, Oracle Database.

***

#### **NoSQL Databases**

* **Yeh Hai Kya? (What it is)**
    NoSQL ("Not Only SQL") databases un data ke liye banaye gaye hain jinka structure fixed nahi hota ya jo bahut tezi se badalta hai (**unstructured** ya **semi-structured** data). Ye ek file cabinet ki tarah hain jismein aap alag-alag tarah ke documents (text files, images, JSON files) ek saath rakh sakte hain.
* **Mukhya Prakaar (Key Types)**
    1.  **Document Databases:** Data ko JSON/BSON documents mein store karte hain (e.g., MongoDB).
    2.  **Key-Value Stores:** Data ko simple key-value pairs mein store karte hain, ek dictionary ki tarah (e.g., Redis, DynamoDB).
    3.  **Column-Family Stores:** Data ko columns ke groups mein store karte hain, jo big data ke liye a
        chha hai (e.g., Cassandra, HBase).
    4.  **Graph Databases:** Data ko nodes aur relationships ke form mein store karte hain, social networks ke liye perfect (e.g., Neo4j).
* **Kyun Zaroori Hai? (Why it's important)**
    Ye **horizontal scaling** (naye servers add karna) ke liye behtareen hote hain aur inki performance bahut high hoti hai, khaas kar ke jab aapko
    bade paimane par data handle karna ho. Ye aam taur par **BASE properties** (Basically Available, Soft state, Eventual consistency) follow karte hain.

***

#### **SQL vs. NoSQL Databases**

| Feature | SQL (Relational) | NoSQL (Non-relational) |
| :--- | :--- | :--- |
| **Data Model** | Structured (Tables, Rows, Columns) | Semi-structured/Unstructured (Documents, Key-Value, etc.) |
| **Schema** | **Fixed Schema:** Pehle se defined, strict. | **Dynamic Schema:** Flexible, on-the-fly. |
| **Scalability** | **Vertical Scaling** (server ko powerful banana). | **Horizontal Scaling** (aur servers add karna). |
| **Consistency** | **Strong Consistency** (ACID). Data hamesha latest hota hai. | **Eventual Consistency** (BASE). Data thode time baad consistent ho sakta hai. |
| **Query Language** | **SQL** (Structured Query Language). | Har database ki apni alag query language hoti hai (NoSQL). |

***

#### **When to use which Database? (Kab Kaunsa Use Karein)**

* **SQL Use Karein Jab:**
    * Aapke data ka structure well-defined aur fixed hai (e.g., user profiles, products).
    * Aapko **ACID compliance** bahut zaroori hai (e.g., banking systems, e-commerce transactions, reservation systems).
    * Aapko complex queries aur JOINS ki zaroorat hai.

* **NoSQL Use Karein Jab:**
    * Aapke paas **big data** hai jo bahut tezi se badh raha hai (e.g., social media feeds, IoT sensor data).
    * Aapko **high write throughput** aur **horizontal scalability** chahiye.
    * Schema flexible hona chahiye (e.g., user generated content, analytics data).
    * Thodi der ke liye data inconsistent rehna a
        chha hai (eventual consistency).

***

#### **Location-based Databases (Geospatial Databases)**

* **Yeh Hai Kya? (What it is)**
    Ye ek special type ke database hain jo geographical data (latitude, longitude) ko store, query, aur analyze karne ke liye optimized hote hain. Ye "spatial data" ko efficiently handle karte hain.
* **Kyun Zaroori Hai? (Why it's important)**
    Ye aise complex sawalon ka jawab tezi se de sakte hain: "Mere 1 kilometer ke daayre mein saare restaurants dhoondo" ya "Kaun si taxi mere sabse paas hai?".
* **Kaise Kaam Karta Hai? (How it works)**
    Ye special indexing techniques jaise **R-trees** ya **Quadtrees** ka istemal karte hain taaki location-based searches bahut fast ho sakein.
* **Examples:** PostGIS (PostgreSQL ka extension), MongoDB (geospatial indexes ke saath), Elasticsearch.

---
---

### **Database Performance & Scaling**

#### **Database Indexes**

* **Yeh Hai Kya? (What it is)**
    Ek database index, ek kitaab ke aakhri panno mein diye gaye index ki tarah hota hai. Jaise aap kitaab ke index se seedhe uss page par pahunch jaate hain jahan aapka topic hai, waise hi database index, data ko tezi se dhoondne (lookup) mein madad karta hai.
* **Kaise Kaam Karta Hai? (How it works)**
    Ye ek ya ek se zyada columns par banaya jaata hai. Index uss column ke data ki ek sorted copy rakhta hai jismein original row ka pointer hota hai. Jab aap uss column par `WHERE` clause use karke query karte hain, to database poori table scan karne ke bajaye seedhe index se data dhoond leta hai.
* **Samjhaute (Trade-offs)**
    * **Fayda:** Data retrieval (`SELECT` queries) ko **bahut fast** kar deta hai.
    * **Nuksaan:** Data modification (`INSERT`, `UPDATE`, `DELETE`) ko **thoda slow** kar deta hai, kyunki har change ke saath index ko bhi update karna padta hai. Indexes disk space bhi lete hain.

***

#### **SQL Query Optimization**

* **Yeh Hai Kya? (What it is)**
    Ye ek query ko is tarah se likhne ya modify karne ka process hai taaki woh kam se kam time aur resources mein execute ho.
* **Mukhya Tareeke (Key Techniques)**
    1.  **Use Indexes Correctly:** Sabse zaroori. `WHERE` aur `JOIN` clauses mein use hone wale columns par index banayein.
    2.  **Avoid `SELECT *`:** Sirf unhi columns ko select karein jinki aapko zaroorat hai.
    3.  **Analyze Query Plan:** `EXPLAIN` command ka use karke dekhein ki database aapki query ko kaise execute kar raha hai aur kahan bottleneck hai.
    4.  **Appropriate JOINS:** Complex queries mein tables ko sahi tareeke se join karein.

***

#### **How are NoSQL databases optimized?**

NoSQL databases ko scale aur performance ke liye zameen se hi design kiya gaya hai.
* **Horizontal Scaling (Sharding):** Data ko multiple servers mein baant diya jaata hai, isliye load bhi bant jaata hai.
* **Denormalization:** Data ko redundant (duplicate) rakha jaata hai taaki baar-baar `JOIN` karne ki zaroorat na pade, jisse read speed badh jaati hai.
* **Specific Data Models:** Har NoSQL database apne data model ke liye optimized hota hai. Jaise ek Key-Value store mein key se value dhoondna (O(1)) bahut fast hota hai.

***

#### **Scaling of Database: Replication & Sharding**

Jab database par load badhta hai, toh use scale karne ke do tareeke hain: **Replication** aur **Sharding**.

* **Database Replication (Data Ki Copy Banana)**
    * **Yeh Hai Kya? (What it is):** Isme hum database ki ek exact copy (replica) ek ya ek se zyada doosre servers par banate hain.
    * **Master-Slave Architecture:**
        * **Kaise Kaam Karta Hai:** Ek server **Master** hota hai aur baaki sab **Slaves**. Saare **write operations** (INSERT, UPDATE, DELETE) sirf Master par hote hain. Master fir in changes ko saare Slaves par copy (replicate) kar deta hai. Saare **read operations** Slaves se kiye jaa sakte hain.
        * **Fayda:** Read traffic ko multiple slaves mein baant kar read performance badha sakte hain. Agar Master fail ho jaaye to ek Slave ko Master banakar system ko available rakha jaa sakta hai (High Availability for reads).
    * **Multi-master Setup:**
        * **Kaise Kaam Karta Hai:** Isme ek se zyada Master server hote hain. Write operations kisi bhi Master par kiye jaa sakte hain. Har Master apne changes ko doosre Masters ke saath sync karta hai.
        * **Fayda:** Write operations ke liye High Availability. Agar ek Master down ho jaaye, to doosre par writes jaari reh sakti hain.
        * **Chunauti (Challenge):** Write conflicts ho sakte hain (agar do users ek hi time par alag-alag master par same data change karein). In conflicts ko resolve karna complex hota hai.

* **Database Sharding (Data Ko Baantna)**
    * **Yeh Hai Kya? (What it is):** Sharding, yaani **Horizontal Partitioning**, ek badi database table ko chote-chote hisson (shards) mein todkar alag-alag database servers par store karna hai. Ye ek moti phonebook ko A-M aur N-Z do alag-alag kitabon mein baantne jaisa hai. 
    * **Sharding Strategies (Baantne Ke Tareeke):**
        1.  **Range-based Sharding:** Data ko ek range ke hisaab se baanta jaata hai (e.g., Pincode 100000-199999 Shard 1 par, 200000-299999 Shard 2 par).
        2.  **Hash-based Sharding:** Shard key (e.g., User ID) ka hash nikalkar uske basis par data ko alag-alag shards mein daala jaata hai. Ye data ko evenly distribute karta hai.
    * **Disadvantages of Sharding:**
        * **Complexity:** System ko manage karna bahut complex ho jaata hai.
        * **Cross-shard Joins:** Alag-alag shards mein pade data ko join karna bahut mushkil aur slow hota hai.
        * **Hotspots:** Agar sharding key a
            chhe se nahi chuni gayi, to saara traffic ek hi shard par jaa sakta hai.

***

#### **Denormalization in Databases**

* **Yeh Hai Kya? (What it is)**
    Denormalization ek aisi prakriya hai jismein hum jaan boojhkar ek database mein **redundant data (duplicate data)** add karte hain.
* **Kyun Zaroori Hai? (Why it's important)**
    Iska mukhya uddeshya **read performance** ko badhana hai. Aisa karke hum complex `JOIN` operations se bach jaate hain. For example, ek `orders` table mein `product_name` ko baar-baar store karna, bajaye `products` table se join karke laane ke.
* **Samjhaute (Trade-offs):** Read toh fast ho jaata hai, par write slow hota hai kyunki ab aapko data ko kai jagah update karna padega. Data inconsistency ka risk bhi badh jaata hai.

---
---

### **Database Management**

#### **Normalization Process in DBMS**

* **Yeh Hai Kya? (What it is)**
    Normalization, denormalization ka ulta hai. Ye ek relational database ko is tarah se organize karne ka process hai jisse **data redundancy (duplication)** kam se kam ho.
* **Kyun Zaroori Hai? (Why it's important)**
    Ye data modification anomalies (INSERT, UPDATE, DELETE karte waqt hone wali problems) ko kam karta hai aur data integrity ko badhata hai.
* **Mukhya Prakaar (Key Types):** Iske kai levels hain jinhe Normal Forms (NF) kehte hain, jaise 1NF, 2NF, 3NF. Aam taur par 3NF tak database ko normalize karna a
    chha maana jaata hai.

***

#### **Database Migrations**

* **Yeh Hai Kya? (What it is)**
    Ye database ke schema (structure) mein kiye jaane waale badlavon (changes) ko control aur version karne ka ek systematic tareeka hai. Jaise aap code ko version control (Git) mein rakhte hain, waise hi database changes ko migrations mein rakhte hain.
* **Kaise Kaam Karta Hai? (How it works)**
    Har change (jaise ek naya table banana, ya ek column add karna) ek migration file mein likha jaata hai. Ye files versioned hoti hain. Isse aap database ke structure ko aasani se upgrade (naye version par le jaana) ya downgrade (purane version par wapas laana) kar sakte hain.
* **Kyun Zaroori Hai? (Why it's important)**
    Jab ek team mein kai developers kaam karte hain, to migrations ensure karti hain ki sabke local database ka schema production database ke saath synchronized rahe.

***

#### **Transaction Isolation Levels**

* **Yeh Hai Kya? (What it is)**
    Ek **transaction** kaam ki ek single logical unit hai (e.g., bank transfer). **Isolation Level** ye control karta hai ki ek transaction dwara kiye gaye badlav doosre concurrent (ek saath chal rahe) transactions ko kab aur kaise dikhenge.
* **Kyun Zaroori Hai? (Why it's important)**
    Ye data consistency ko maintain karta hai jab kai users ek saath database par kaam kar rahe hon. Sahi isolation level chunna performance aur consistency ke beech ek trade-off hai.
* **Mukhya Levels (Key Levels)** (Simplest to Strictest)
    1.  **Read Uncommitted:** Sabse weak. Ek transaction doosre transaction ka uncommitted (bina save kiya hua) data bhi padh sakta hai. Isse **Dirty Reads** ho sakti hain.
    2.  **Read Committed:** Ek transaction sirf committed (save kiya hua) data hi padh sakta hai. Ye Dirty Reads ko rokta hai. (Ye default hota hai kai databases mein).
    3.  **Repeatable Read:** Ek transaction ke dauraan agar ek row ko baar-baar padha jaaye, to wahi data milega. Ye **Non-Repeatable Reads** ko rokta hai.
    4.  **Serializable:** Sabse strict level. Ye aisa anubhav deta hai jaise saare transactions ek ke baad ek, akele-akele chal rahe hon. Ye **Phantom Reads** ko bhi rokta hai, par performance par sabse zyada asar daalta hai.

---

### **2.3. Caching (Baar-Baar Use Hone Wali Cheezon Ko Paas Rakhna)**

#### **What is a Cache? / Benefits of Caching**

* **Yeh Hai Kya? (What it is)**
    Cache ek choti, lekin bahut hi **tez (high-speed)** temporary storage layer hai. Iska kaam hai unn data ko store karna jinki zaroorat baar-baar padti hai.

    **Analogy:** Isko aap apne study desk ki tarah sochiye. Aapki saari kitabein ek badi almari (database/disk) mein rakhi hain. Almari se kitab nikalne mein time lagta hai. Lekin jo kitab aap abhi padh rahe hain ya baar-baar refer karte hain, use aap apni desk (cache) par rakh lete hain taaki use turant utha saken.

* **Kyun Zaroori Hai? (Benefits)**
    1.  **Performance Badhata Hai:** Cache, data ko slow disk ya database se laane ke bajaye, tez RAM se serve karta hai. Isse application ki latency (response time) kaafi kam ho jaati hai aur woh super-fast feel hoti hai.
    2.  **Backend Load Kam Karta Hai:** Jab request ka jawab cache hi de deta hai, toh request aapke main database tak jaati hi nahi. Isse aapka database kam requests handle karta hai aur overload hone se bach jaata hai.
    3.  **Cost Bachata Hai:** Kam load ka matlab hai ki aapko kam powerful (aur saste) database servers ki zaroorat padegi.

#### **What is Thrashing?**

* **Yeh Hai Kya? (What it is)**
    Thrashing ek aisi situation hai jahan system apna zyada tar samay data ko cache mein laane aur hatane mein hi barbaad kar deta hai, aur asal kaam (processing) kam kar paata hai. Aisa tab hota hai jab cache ka size, zaroori data (working set) ko rakhne ke liye bahut chota hota hai.

    **Analogy:** Aapki study desk (cache) bahut choti hai. Aapko ek nayi kitab rakhne ke liye ek purani kitab wapas almari mein rakhni padti hai. Par agle hi pal aapko uss purani kitab ki fir se zaroorat pad jaati hai. Ab aap poora din kitabon ko desk par laane aur almari mein wapas rakhne mein hi nikal dete hain, padhai bilkul nahi kar paate. Yahi thrashing hai.

#### **Types of Caches**

Caches alag-alag jagah ho sakte hain:
1.  **Client-Side Cache (Browser Cache):** Ye user ke browser mein hota hai. Jab aap ek website visit karte hain, to browser uske images, CSS, JS files ko cache kar leta hai taaki agli baar visit karne par page jaldi load ho.
2.  **Application Server Cache:** Ye cache application ke andar hi hota hai (in-memory). Har application server apni RAM mein ek chota cache bana leta hai. Iski problem ye hai ki agar aapke paas 5 server hain, to sabka cache alag-alag hoga aur unmein data inconsistent ho sakta hai.
3.  **Distributed Cache:** Ye ek alag se caching layer hoti hai jise kai application servers milkar use karte hain. Ye ek central cache ki tarah kaam karta hai.

#### **Distributed Caching**

* **Yeh Hai Kya? (What it is)**
    Ye ek external caching system hai jo kai servers ki memory ko milakar ek bada, shared cache banata hai. Saare application servers is shared cache se network par baat karte hain.
* **Kyun Zaroori Hai? (Why it's important)**
    Jab aapke paas multiple application servers hote hain (horizontal scaling), to ye unke beech cache consistency ki problem solve karta hai. Sab servers ek hi jagah se data padhte aur likhte hain, isliye data hamesha consistent rehta hai.

#### **Cache Write Policies (Cache Mein Data Likhne Ke Tareeke)**

Jab data change hota hai, to use cache aur database dono mein update karna padta hai. Iske 3 tareeke hain:
1.  **Write-Through:** Data ko **pehle cache mein aur usi samay database mein** likha jaata hai. Write operation tabhi successful maana jaata hai jab data dono jagah likh jaaye.
    * **Fayda:** Data hamesha consistent rehta hai, data loss ka risk nahi hota.
    * **Nuksaan:** Write operation slow hota hai kyunki database mein likhne mein time lagta hai.
2.  **Write-Back (Write-Behind):** Data ko **sirf cache mein** turant likh diya jaata hai. Cache us data ko kuch der baad (e.g., har 5 minute mein) dheere-dheere database mein likhta hai.
    * **Fayda:** Write operation bahut fast hota hai.
    * **Nuksaan:** Agar cache server crash ho gaya database mein likhne se pehle, to data loss ho sakta hai.
3.  **Write-Around:** Data ko **seedhe database mein** likha jaata hai, cache ko bypass karke. Data cache mein tabhi aata hai jab use koi padhne ke liye request karta hai (on a read miss).
    * **Fayda:** Unn data ke liye a
        chha hai jo likha toh jaata hai par turant padha nahi jaata. Cache ko faltu data se nahi bharta.

#### **Cache Replacement (Eviction) Policies (Jab Cache Bhar Jaaye)**

Jab cache full ho jaata hai, to naya data daalne ke liye purana data hatana padta hai. Ye decide karne ke liye kaun sa data hatana hai, kuch policies use hoti hain:
1.  **LRU (Least Recently Used):** Uss item ko hatao jo sabse lambe samay se use nahi hua hai. Ye sabse common aur effective policy hai.
2.  **LFU (Least Frequently Used):** Uss item ko hatao jise sabse kam baar access kiya gaya hai.
3.  **FIFO (First-In, First-Out):** Uss item ko hatao jo sabse pehle cache mein aaya tha, jaise ek line (queue) mein hota hai.

#### **Intro to Redis**

* **Yeh Hai Kya? (What it is)**
    Redis ek bahut hi popular, open-source, in-memory data store hai. Ye ek distributed cache ka sabse famous example hai.
* **Kyun Zaroori Hai? (Why it's important)**
    1.  **Extremely Fast:** Kyunki ye saara data RAM mein rakhta hai.
    2.  **Rich Data Structures:** Ye sirf simple key-value hi nahi, balki Lists, Sets, Hashes jaise complex data structures ko bhi support karta hai.
    3.  **More than a Cache:** Log ise database, message broker, aur session store ki tarah bhi use karte hain.

---
---

### **2.4. Storage (Data Ko Rakhne Ki Jagah)**

#### **Block, Object, and File Storage**

Ye data ko store karne ke 3 buniyadi tareeke hain:
1.  **File Storage:** Data ko files aur folders ke hierarchy (jaise C: Drive -> My Documents) mein organize kiya jaata hai. Ise istemal karna aasan hai. (Used in: NAS - Network Attached Storage).
2.  **Block Storage:** Data ko fixed size ke "blocks" mein toda jaata hai, aur har block ka apna ek unique address hota hai. Ye bahut fast aur efficient hota hai, isliye databases iska istemal karte hain. (Used in: SAN - Storage Area Network).
3.  **Object Storage:** Data ko "object" ki tarah store kiya jaata hai. Har object mein data, usse judi jaankari (metadata), aur ek unique ID hoti hai. Ye behad scalable hota hai.
    * **Analogy:** Ye ek valet parking jaisa hai. Aap apni car (data) attendant ko dete hain, woh aapko ek ticket (unique ID) deta hai. Aapko ye chinta karne ki zaroorat nahi ki usne car kahan park ki, aap ticket dikhakar use wapas le sakte hain.

#### **Blob Storage**

* **Yeh Hai Kya? (What is a Blob?)**
    Blob ka matlab hai **Binary Large Object**. Ye bas data ka ek anstructured chunk hai, jaise ek image file, video file, audio file, ya log file.
* **Kyun Zaroori Hai? (Why do we need Blob Storage?)**
    Blob storage, Object Storage ka hi ek type hai, jo khaas taur par badi-badi unstructured files ko saste mein aur reliably store karne ke liye banaya gaya hai. Ye internet-scale applications ke liye perfect hai.
* **AWS S3 (Simple Storage Service):** Ye duniya ka sabse popular Blob/Object storage service hai. Iske features hain:
    * **Massive Scalability:** Aap ismein lagbhag unlimited data store kar sakte hain.
    * **High Durability:** AWS guarantee deta hai ki aapka data 99.999999999% safe rahega (yaani data loss ka chance na ke barabar hai).
    * **API Access:** Data ko HTTP API ke through access kiya jaata hai.

---
---

### **2.5. Content Delivery Network (CDN)**

#### **What is a CDN?**

* **Yeh Hai Kya? (What it is)**
    CDN poori duniya mein faile hue servers ka ek distributed network hai. Iska mukhya kaam hai aapki website ke **static content** (images, videos, CSS, JS files) ki copy apne paas rakhna aur use user ko uske **sabse nazdeeki location** se serve karna.

    **Analogy:** Maan lijiye Dilli mein ek famous mithai ki dukaan (Origin Server) hai. Ab Chennai mein baithe logon ko bhi woh mithai chahiye. Har baar Dilli se mithai mangwana slow aur mehenga hai. To dukaan wala Chennai mein ek choti branch (Edge Server) khol deta hai. Ab Chennai ke log seedhe local branch se mithai le lete hain, jo ki bahut fast hai. Ye local branch hi CDN hai.

#### **How does CDN work?**

1.  Ek user (Chennai mein) aapki website (`my-mithai-shop.com`, jiska server Dilli mein hai) se ek image request karta hai.
2.  Request Dilli jaane ke bajaye, DNS use user ke sabse nazdeeki CDN server (Chennai waali branch) par bhej deta hai. Is server ko **Edge Server** ya **PoP (Point of Presence)** kehte hain.
3.  **Case 1: Cache Hit.** Agar Chennai waale server ke paas uss image ki copy pehle se hai, to woh use turant user ko bhej dega. Bahut fast!
4.  **Case 2: Cache Miss.** Agar Chennai waale server ke paas image nahi hai, to woh Dilli waale main server (Origin Server) se image mangwayega, uski ek copy apne paas future ke liye save karega, aur fir user ko dega. Pehli baar thoda slow hoga, par uske baad Chennai region ke sabhi users ke liye woh image fast load hogi.

#### **Key Concepts in CDNs**

* **Origin Server:** Aapka main web server jahan original content rakha hai.
* **Edge Server / PoP:** Duniya bhar mein faile hue CDN ke chote-chote servers jo users ke paas hote hain.
* **Pull vs. Push CDN:**
    * **Pull CDN:** Ye "on-demand" kaam karta hai. Jab koi user kisi file ko pehli baar request karta hai, tabhi CDN use Origin se "pull" karke apne paas cache karta hai. (Ye sabse common hai).
    * **Push CDN:** Isme aap (website owner) apni files ko pehle se hi CDN ke saare edge servers par "push" kar dete hain, bina kisi user ke request kiye. Ye badi files (jaise software updates, video files) ke liye a
        chha hai.


---
### **2.6. Messaging Systems (Services Ke Beech Sandesh-Vahan)**

#### **Asynchronous Programming**

* **Yeh Hai Kya? (What it is)**
    Ye programming ka ek model hai jahan aap ek kaam (task) shuru karke uske poora hone ka intezaar nahi karte. Aap us kaam ko background mein chalne dete hain aur aage apna doosra kaam karne lag jaate hain. Jab background wala kaam poora ho jaata hai, to aapko ek notification mil jaata hai.

    **Analogy:** Aap ek restaurant mein buzzer system sochiye. Aap counter par order (task 1) dete hain aur aapko ek buzzer mil jaata hai. Aapko counter par khade rehkar intezaar nahi karna padta. Aap jaakar table dhoondh sakte hain (task 2). Jab aapka order ready ho jaata hai (task 1 complete), to buzzer vibrate karta hai aur aap jaakar order le aate hain.

* **Kyun Zaroori Hai? (Why it's important)**
    Ye long-running tasks (jaise video upload karke process karna, ya email bhejna) ke liye zaroori hai. Isse aapka application "block" ya "hang" nahi hota aur user ko hamesha ek responsive experience milta hai.

#### **What is a Message Queue? (Sandeshon Ki Kataar)**

* **Yeh Hai Kya? (What it is)**
    Ye ek "post office" ki tarah hai jo do software services ke beech baithta hai. Ek service (Producer) message likhkar queue mein daal deti hai. Doosri service (Consumer) jab free hoti hai, to queue se us message ko uthakar process karti hai.

    `[Producer Service] ---> [Message Queue] ---> [Consumer Service]`

* **Kyun Zaroori Hai? (Why a message broker in between?)**
    1.  **Decoupling (Rishta Todna):** Producer ko ye janne ki zaroorat nahi ki consumer kaun hai, ya wo abhi online hai bhi ya nahi. Wo bas apna message queue ko de deta hai. Isse services aapas mein loosely coupled rehti hain.
    2.  **Load Balancing (Bojh Kam Karna):** Agar producer bahut tezi se messages bhej raha hai, to queue unhe store kar leti hai. Consumer apni speed se ek-ek karke unhe process karta rehta hai. Isse consumer par achanak se load nahi badhta.
    3.  **Resilience (Majbooti):** Agar consumer service crash ho jaati hai, to messages queue mein safe rehte hain. Jab service wapas online aati hai, to wo wahin se kaam shuru kar sakti hai jahan chhoda tha.

#### **Message Stream**

* **Yeh Hai Kya? (What it is)**
    Message Stream, messages (ya events) ka ek **lagatar aur ordered** behta hua dhara hai. Ek message queue se alag, jahan message consume hone ke baad delete ho jaata hai, stream mein messages hamesha ke liye store ho jaate hain (ek log file ki tarah) aur unhe kai alag-alag consumers baar-baar padh sakte hain.

    **Analogy:** Queue ek To-Do list hai jismein aap kaam poora karke use kaat dete hain. Stream ek Diary ki tarah hai jismein aap purane panno ko bhi jab chahe wapas padh sakte hain.

#### **Publisher-Subscriber Model (Pub/Sub)**

* **Yeh Hai Kya? (What it is)**
    Ye ek messaging pattern hai jahan message bhejne wala (**Publisher**) kisi specific receiver ko message nahi bhejta. Wo message ko ek **"topic"** (ek channel ki tarah) par publish kar deta hai. Jin-jin services (**Subscribers**) ne uss topic ko subscribe kiya hota hai, un sabko uss message ki ek copy mil jaati hai.

    **Analogy:** Ek YouTube creator (**Publisher**) jab video upload karta hai, to wo har ek viewer ko alag-alag nahi bhejta. Wo use apne channel (**Topic**) par daal deta hai. Jin-jin logon ne channel ko "subscribe" kiya hota hai, un sabko video mil jaati hai.

* **Queue vs. Pub/Sub:** Queue mein 1 message aam taur par 1 hi consumer ko milta hai. Pub/Sub mein 1 message kai subscribers ko mil sakta hai.

#### **Apache Kafka Deep Dive**

* **Yeh Hai Kya? (What it is)**
    Kafka sirf ek message queue nahi hai, ye ek **distributed event streaming platform** hai. Ise high-volume, real-time data feeds (jaise user clicks, log messages, financial transactions) ko handle karne ke liye banaya gaya hai.

* **Kab Use Karein? (When to use Kafka)**
    Jab aapko प्रति सेकंड laakhon messages handle karne hon. Jaise:
    * Website par user activity ko real-time mein track karna.
    * Saare servers se log messages ko ek jagah collect karna.
    * IoT devices se aa rahe data ko process karna.
    * Real-time analytics.

* **Kafka Internals (Andar Ki Baatein)**
    * **Topic:** Messages ki ek category (e.g., `user_clicks`).
    * **Partition:** Performance aur scalability ke liye, har topic ko kai partitions mein baanta jaata hai. Ek partition mein messages ordered rehte hain.
    * **Producer:** Jo topics par data likhta hai.
    * **Consumer:** Jo topics se data padhta hai.
    * **Broker:** Ek Kafka server. Kai brokers milkar ek Kafka cluster banate hain.

#### **Database as a Message Queue**

* **Yeh Hai Kya? (What it is)**
    Aap ek database table ko bhi ek simple message queue ki tarah use kar sakte hain. Producer table mein ek naya row `INSERT` karta hai (status='PENDING'). Consumer har kuch seconds mein table ko check (`SELECT`) karta hai, PENDING rows ko process karke unka status `UPDATE` kar deta hai.
* **Kyun Bura Idea Hai? (Why it's an Anti-pattern)**
    Ye bahut hi inefficient hai. Consumer ka baar-baar database ko check karna (**polling**) database par faltu ka load daalta hai aur ye high traffic ke liye bilkul scale nahi karta. Isse sirf bahut hi chote, internal tasks ke liye use karna chahiye.

---
---

### **2.7. API Gateway & Proxies (System Ke Darwaze)**

#### **What is an API Gateway?**

* **Yeh Hai Kya? (What it is)**
    Ye ek server hai jo aapke saare backend microservices ke liye ek **single entry point (eklauta darwaza)** ki tarah kaam karta hai. Client (mobile app ya browser) seedhe microservices se baat nahi karta, wo API Gateway se baat karta hai.

    **Analogy:** API Gateway ek bade mall ka main entrance aur security guard hai. Sabko usi darwaze se aana padta hai. Guard aapka ID check kar sakta hai (**Authentication**), aapko bata sakta hai ki kaun si dukaan kahan hai (**Routing**), aur bheed ko control kar sakta hai (**Rate Limiting**), isse pehle ki aap kisi specific dukaan (microservice) tak pahunche.

* **Kaam Kya Karta Hai? (Responsibilities)**
    * **Request Routing:** Request ko sahi microservice tak bhejna.
    * **Authentication & Authorization:** Check karna ki user kaun hai aur kya use ye kaam karne ki permission hai.
    * **Rate Limiting:** Ek user/client ko bahut zyada requests karne se rokna.
    * **Logging & Monitoring:** Saare requests ko log karna.
    * **Caching:** Common requests ke response ko cache karna.

#### **What is a Proxy?**

* **Yeh Hai Kya? (What it is)**
    Proxy ek beech ka server (intermediary) hai jo kisi doosre computer ke behalf par kaam karta hai.

#### **Forward Proxy vs Reverse Proxy**

Ye proxy ke do mukhya prakaar hain, aur inka fark is baat par nirbhar karta hai ki wo **kiske liye kaam kar rahe hain**.

* **Forward Proxy (Client Ka Dost)**
    * Ye **client ke behalf par** kaam karta hai aur client ke network ke andar hota hai.
    * **Kaam:** Aap (client) internet se baat karne ke liye iska istemal karte hain. Ye aapki asli IP address chupa sakta hai aur company/school ke internet rules (jaise website block karna) ko laagoo kar sakta hai. Aap proxy se baat karte hain, proxy aapke liye internet se baat karta hai.
    * `You ---> Forward Proxy ---> Internet`

* **Reverse Proxy (Server Ka Guard)**
    * Ye **server ke behalf par** kaam karta hai aur server ke network ke aage khada hota hai.
    * **Kaam:** Internet (client) isse baat karta hai, ye nahi jaante hue ki peeche aur bhi kai servers hain. Ye **Load Balancing**, security, aur caching ke liye istemal hota hai. **API Gateway ek tarah ka special Reverse Proxy hi hai.**
    * `Internet ---> Reverse Proxy ---> Your Servers`

| Feature | Forward Proxy | Reverse Proxy |
| :--- | :--- | :--- |
| **Kiske Liye Kaam Karta Hai?** | Client | Server |
| **Kiski Pehchan Chupata Hai?** | Client ki | Server ki |
| **Kahan Hota Hai?** | Client ke network mein | Server ke network mein |
| **Use Case** | Internet access control, Anonymity | Load Balancing, Security, Caching |

#### **Asynchronous APIs**

* **Yeh Hai Kya? (What it is)**
    Ye ek aisi API hai jahan aap request bhejte hain aur server turant "Aapka kaam shuru kar diya hai" (`202 Accepted` response) keh kar jawab de deta hai, lekin wo kaam background mein dheere-dheere hota hai. Aapko final result ke liye intezaar nahi karna padta.
* **Result Kaise Milta Hai?**
    1.  **Polling:** Client thodi-thodi der mein ek doosre status endpoint ko call karke poochta rehta hai, "Kaam poora hua kya?".
    2.  **Webhook:** Server, kaam poora hone par, client ke diye hue ek URL (callback URL) par khud se request bhej kar bata deta hai ki "Kaam ho gaya".



---


### **3.1. Scalability (Badhte Load Ko Sambhalne Ki Taqat)**

#### **Scalability and How to achieve it**

  * **Yeh Hai Kya? (What it is)**
    Scalability kisi system ki woh kaabiliyat hai jisse woh badhte hue load (zyada users ya zyada data) ko efficiently handle kar sake. Ek scalable system woh hai jo 100 users ke liye jaisa perform karta hai, waisa hi 1 million users ke liye bhi kare, bas resources badha kar.

    **Analogy:** Ek choti pizza ki dukaan jo 10 customer ko handle kar sakti hai, scalable tab kehlayegi jab woh zaroorat padne par 1000 customer ko bhi utni hi a
    chhi service de paaye.

  * **Kaise Haasil Karein? (How to achieve it)**
    Scalability haasil karne ke liye hum components ko `decouple` karte hain, system ko `stateless` banate hain, `asynchronous` operations ka istemal karte hain, aur sabse zaroori, do scaling strategies ka istemal karte hain: Horizontal aur Vertical scaling.

#### **Horizontal vs. Vertical Scaling**

Ye system mein "aur power" add karne ke do alag-alag tareeke hain.

  * **Vertical Scaling (Scaling Up)**

      * **Yeh Hai Kya?** Iska matlab hai apne **maujooda server ko aur powerful banana**. Jaise usmein zyada RAM laga dena, ek faster CPU laga dena, ya ek behtar storage disk laga dena.
      * **Analogy:** Ye ek weightlifter ko aur training dekar use aur zyada taqatwar banane jaisa hai taaki woh aur zyada wajan utha sake. Sirf ek hi weightlifter hai, bas woh pehle se zyada strong ho gaya hai.

    <!-- end list -->

    ```
    Before: [Server: 8GB RAM, 4-core CPU]
    After:  [Server: 32GB RAM, 16-core CPU]  <-- Same server, just more powerful
    ```

  * **Horizontal Scaling (Scaling Out)**

      * **Yeh Hai Kya?** Iska matlab hai load ko baantne ke liye **system mein aur servers add karna**. Aap ek server ko powerful banane ke bajaye, us jaise hi kai aur servers khareed lete hain.
      * **Analogy:** Ye ek weightlifter ko strong banane ke bajaye, uski team mein aur weightlifters ko shaamil karne jaisa hai. Ab poori team milkar zyada wajan utha sakti hai.

    <!-- end list -->

    ```
    Before: [Server A]
    After:  [LB] -> [Server A] [Server B] [Server C] <-- More servers added
    ```

#### **Which Scalability approach is right for our Application?**

| Feature | Vertical Scaling (Up) | Horizontal Scaling (Out) |
| :--- | :--- | :--- |
| **Complexity** | **Aasan:** Manage karna simple hai, kyunki ek hi machine hai. | **Mushkil:** Load Balancers, network communication ki zaroorat padti hai. |
| **Cost** | **Mehenga:** Ek point ke baad bahut zyada powerful server bahut mehenga ho jaata hai. | **Sasta:** Kai chote, commodity servers khareedna ek supercomputer se sasta padta hai. |
| **Limit** | **Limit Hai:** Ek server ko aap ek had tak hi upgrade kar sakte hain (e.g., maximum RAM/CPU). | **Lagbhag Unlimited:** Aap zaroorat ke hisaab se hazaaron servers add kar sakte hain. |
| **Fault Tolerance** | **Kam:** Agar woh ek server fail ho gaya, to poora system down (Single Point of Failure). | **Zyada:** Agar ek server fail hota hai, to Load Balancer traffic doosre servers par bhej deta hai. |

**Nishkarsh (Conclusion):**

  * Shuruaati stage mein ya stateful applications (jaise traditional databases) ke liye **Vertical Scaling** a
    chha ho sakta hai.
  * Lekin modern, large-scale web applications ke liye **Horizontal Scaling** hi aage badhne ka raasta hai.

#### **Auto Scaling**

  * **Yeh Hai Kya? (What it is)**
    Ye ek aisi prakriya hai jisse system apne aap (automatically) zaroorat ke hisaab se servers ko **add (scale out)** ya **remove (scale in)** karta hai.

    **Analogy:** Ye ek supermarket jaisa hai jo rush hour mein apne aap naye checkout counters khol deta hai aur jab bheed kam ho jaati hai to unhe band kar deta hai. Isse customers ko zyada intezaar nahi karna padta aur company ka staff par faltu kharcha bhi nahi hota.

  * **Kaise Kaam Karta Hai?**
    Aap kuch rules (policies) define karte hain. Jaise: "Agar sabhi servers ka average CPU usage 70% se upar chala jaaye, to 2 naye server add kar do." Aur "Agar CPU usage 20% se neeche aa jaaye, to 1 server hata do." Cloud platforms jaise AWS is feature ko out-of-the-box dete hain.

#### **Primary Bottlenecks that Hurt the Scalability of an Application**

Bottleneck system ka woh hissa hota hai jo load badhne par sabse pehle "choke" ho jaata hai aur poore system ki speed dheemi kar deta hai.

1.  **Database:** Aksar sabse bada bottleneck. Bahut zyada connections, slow queries, ya disk I/O (padhne/likhne ki speed) system ko slow kar dete hain.
2.  **Single Point of Failure (SPOF):** Koi bhi aisa component jo akele hai (jaise ek single database ya load balancer). Agar woh fail hota hai, poora system ruk jaata hai.
3.  **Network Bandwidth:** Servers ke beech ya user tak data bhejne ki network capacity ka kam hona.
4.  **Inefficient Code:** Ek kharab algorithm jo load badhne par exponentially zyada CPU ya memory use karne lagta hai.

-----

-----

### **3.2. Availability, Reliability & Fault Tolerance (Bharosa Aur Majbooti)**

#### **Availability in System Design**

  * **Yeh Hai Kya? (What it is)**
    Availability ka matlab hai ki aapka system kitne time tak **chalu aur users ke liye uplabdh** rehta hai. Ise percentage mein naapa jaata hai, jise "nines" kehte hain.
      * **99%** (2 nines): Saal mein \~3.65 din down. (Theek nahi hai)
      * **99.9%** (3 nines): Saal mein \~8.77 ghante down. (Theek-thaak)
      * **99.99%** (4 nines): Saal mein \~52.6 minute down. (A
        chha)
      * **99.999%** (5 nines): Saal mein \~5.26 minute down. (Bahut a
        chha - ye aam taur par goal hota hai)

#### **How to achieve High Availability?**

High Availability (HA) paane ke liye, aapko ye maankar chalna hoga ki "failure hoga hi hoga".

1.  **Redundancy (Har Cheez Ki Ek Extra Copy):** Kisi bhi critical component ki ek se zyada copy rakhein. Agar ek server fail ho, to doosra kaam sambhal le. Iske liye Load Balancers (servers ke liye) aur Database Replication (data ke liye) ka istemal hota hai.
2.  **Eliminate Single Points of Failure (SPOF):** System mein koi bhi aisi cheez na rakhein jiske fail hone se poora system band ho jaaye. Har component redundant hona chahiye.
3.  **Automatic Failover (Apne Aap Switch Karna):** Ek aisi mechanism banayein jo automatically detect kar le ki ek component fail ho gaya hai aur traffic ko turant uske healthy backup par switch kar de, bina kisi insaan ke a
    chhe.

#### **Reliability vs. Availability**

  * **Availability:** Kya system **ON** hai? (Can I use it?)
  * **Reliability:** Jab system ON hai, to kya woh **sahi kaam** kar raha hai? (Does it do the right thing?)

**Analogy:** Ek ATM machine 24 ghante ON hai (**Available**). Lekin jab aap ₹1000 nikalne ki koshish karte hain, to woh ₹500 deti hai aur account se ₹1000 kaat leti hai. Machine **Available** hai, par **Reliable** nahi hai.

#### **Fault Tolerance**

  * **Yeh Hai Kya? (What it is)**
    Fault tolerance, system ki woh kaabiliyat hai jisse woh apne ek ya ek se zyada components ke **fail hone ke bawajood** bhi kaam karta rehta hai. Ho sakta hai performance thodi kam ho jaaye, par system poori tarah se band nahi hota. Ye High Availability paane ka ek tareeka hai.

    **Analogy:** Ek car jismein 4 tires ke alawa ek spare tire (stepney) bhi hai, woh ek tire ke puncture hone ke fault ko tolerate kar sakti hai.

#### **What is a Single Point of Failure (SPOF)?**

  * **Yeh Hai Kya? (What it is)**
    System ka koi bhi aisa component jiske fail hone se poora system kaam karna band kar de.
  * **Examples:**
      * Ek web application jismein sirf 1 web server hai.
      * Ek system jismein sirf 1 database hai (bina replica ke).
      * Ek system jismein 1 hi Load Balancer hai.
  * **Solution:** Har SPOF ko dhoondho aur uski **redundancy** (extra copy) add karo.

#### **How to avoid Cascading Failures?**

  * **Yeh Hai Kya?**
    Ye ek chain reaction hota hai jahan ek chote se component ka failure, doosre dependent components ko fail kar deta hai, aur dheere-dheere poora system down ho jaata hai. Jaise dominoes girte hain.

  * **Rokne Ke Tareeke (Techniques to Avoid):**

    1.  **Timeouts:** Ek service, doosri service ke jawab ka anantkaal tak intezaar na kare. Agar 500ms mein jawab nahi aaya, to request ko fail maan kar aage badho.
    2.  **Retries (with Exponential Backoff):** Agar ek request fail ho, to use dobara try karo. Lekin har try ke beech ka gap badhate jao (e.g., pehle 1 sec, fir 2 sec, fir 4 sec...). Isse failing service ko recover hone ka time milta hai.
    3.  **Circuit Breaker Pattern:** Agar ek service lagatar fail ho rahi hai, to us par requests bhejna hi band kar do (circuit "open" kar do). Thodi der baad ek test request bhej kar dekho, agar woh paas ho gayi to fir se normal traffic shuru karo. Isse aap apni service ko ek failing service se bachate hain.

#### **Data Redundancy and Data Recovery**

  * **Why do we make databases redundant?**

    1.  **To Prevent Data Loss:** Hardware fail ho sakta hai, data corrupt ho sakta hai, ya insaan se galti ho sakti hai. Redundancy (backup/replica) aapke data ko in cheezon se bachata hai.
    2.  **To Ensure Availability:** Agar aapka primary database maintenance ke liye down hai ya crash ho gaya hai, to aap read traffic ko uske replica par bhej kar application ko chalu rakh sakte hain.

  * **Different ways of doing data backup**

    1.  **Periodic Snapshots:** Roz/hafte mein ek baar poore database ka backup (dump) le kar kahin aur store karna.
    2.  **Database Replication:** Live data ki copies banana.

  * **Continuous Redundancy**
    Ye replication ka hi doosra naam hai. Iska matlab hai ki data lagatar (continuously) ek se zyada jagah par copy ho raha hai. Isse **RPO (Recovery Point Objective)** - kitna data aap kho sakte hain - bahut kam ho jaata hai, aur **RTO (Recovery Time Objective)** - system ko wapas laane mein kitna time lagega - bhi bahut kam ho jaata hai. Master-Slave replication iska ek a
    chha example hai.

---


### **3.3. Consistency (Data Ka Ekroop Hona)**

#### **What is Data Consistency?**

* **Yeh Hai Kya? (What it is)**
    Consistency ka seedha sa matlab hai ki system mein har user ko, har samay, data ka **ek hi, sabse updated version** dikhna chahiye. Agar ek user ne data update kiya hai, to doosre user ko read karne par wahi naya data milna chahiye, purana nahi.

    **Analogy:** Ek shared Google Doc sochiye. Jab aap kuch type karte hain, to aapke saathi ko bhi woh change turant dikhta hai. Document sabke liye **consistent** hai. Agar aapke saathi ko aapke type karne ke 5 minute baad tak purana text hi dikhta rahe, to document **inconsistent** hoga.

#### **Consistency Patterns / Levels**

Distributed systems mein consistency ke mukhya roop se do patterns hote hain:

1.  **Strong Consistency (Sakht Anushasan):** Isme koi compromise nahi hota. Ek baar write operation successful ho gaya, to uske baad aane waali har read request ko wahi naya data milega. Guarantee hai.
2.  **Eventual Consistency (Dheela Anushasan):** Isme system guarantee deta hai ki "aaj nahi to kal" saare servers par data same ho jaayega. Kuch samay ke liye (milliseconds ya seconds), alag-alag users ko purana data dikh sakta hai. Lekin ant mein sab aapas mein sync ho jaayenge.

#### **Consistency Deep Dive**

* **Strong Consistency & When to choose it**
    * **Kab Chunein?** Jab data ki accuracy sabse zyada zaroori ho aur galat ya purana data dikhana bilkul bhi manzoor na ho. Aise systems jahan har transaction mayne rakhta hai.
    * **Examples:**
        * **Banking Systems:** Aapke account ka balance hamesha correct dikhna chahiye.
        * **E-commerce Order Systems:** Jab aap ek product order karte hain, to uska stock count turant update hona chahiye.
        * **Reservation Systems:** Ek hi train seat do logon ko book nahi honi chahiye.

* **Eventual Consistency & When to choose it**
    * **Kab Chunein?** Jab high availability (system ka hamesha on rehna) aur performance (speed) zyada zaroori ho, aur kuch seconds ke liye purana data dikhna a
        chha ho.
    * **Examples:**
        * **Social Media Likes/Comments:** Agar aapko ek post par naya like 5 second baad dikhe to koi problem nahi hai.
        * **YouTube View Count:** View count turant update nahi hota, thoda time lagta hai.
        * **DNS:** Jab aap ek domain ki IP badalte hain, to poori duniya mein us change ko propagate hone mein time lagta hai.

* **Ways to achieve Strong Consistency**
    * **Synchronous Replication:** Master-Slave model mein, Master database write operation ko successful tabhi batata hai jab saare (ya zyadatar) Slaves se confirmation aa jaata hai ki unhone bhi data likh liya hai.
    * **Quorum:** Likhte (write) aur padhte (read) waqt, server ke nodes ke ek majority (quorum) se confirm karna ki sabke paas same data hai.

* **Ways to achieve Eventual Consistency**
    * **Asynchronous Replication:** Master database client ko turant "OK" bol deta hai aur background mein dheere-dheere Slaves ko data replicate karta rehta hai.
    * **Gossip Protocol:** Servers aapas mein ek doosre se "gossip" karke (information exchange karke) naye data ko poore system mein failaate hain.

---
---

### **3.4. The CAP Theorem (System Design Ka Trilemma)**

#### **What is the CAP Theorem?**

* **Yeh Hai Kya? (What it is)**
    CAP Theorem distributed systems ka ek buniyadi siddhant hai. Ye kehta hai ki koi bhi distributed system in teen guarantees mein se ek saath **sirf do** hi de sakta hai, teesri ko compromise karna hi padega.
    * **C - Consistency:** Sabhi nodes par ek hi samay par same data dikhna.
    * **A - Availability:** System hamesha har request ka jawab dega (bhale hi data thoda purana ho). System hamesha ON rahega.
    * **P - Partition Tolerance:** Network mein problem (partition) aane par bhi system kaam karta rahega. Yaani agar do servers aapas mein baat nahi kar paa rahe, to bhi system chalna chahiye.

#### **Why only CP or AP? Why not CA?**

Ye is theorem ka sabse zaroori hissa hai.
Real world mein, network fail hote hain. Servers ke beech communication toot sakta hai. Isse **Network Partition (P)** kehte hain. Ye ek aisi sachai hai jise aap ignore nahi kar sakte. Isliye, har modern distributed system ko **Partition Tolerant (P)** hona hi padta hai.

Jab aapne **'P'** ko chun liya, to aapke paas sirf do hi vikalp bachte hain: **CP** ya **AP**.

**Scenario Socho:** Aapke paas do server (S1, S2) hain jo ek doosre ka data copy karte hain. Beech mein network fail ho gaya (partition ho gaya). Ab S1 aur S2 aapas mein baat nahi kar sakte.
* **Agar aap Availability (A) chunte hain (AP System):**
    * Aap kahenge, "Koi baat nahi, system available rehna chahiye." Aap S1 aur S2 dono ko client se write requests lene ki permission denge.
    * **Nateeja:** System **Available** hai, par ab S1 aur S2 ke paas alag-alag data hai. Aapne **Consistency (C)** ko qurbaan kar diya. Jab network theek hoga, tab aapko data aapas mein sync karna padega.
* **Agar aap Consistency (C) chunte hain (CP System):**
    * Aap kahenge, "Galat data bilkul nahi dikhna chahiye." Aap S1 ko Master banakar sirf us par write allow karenge aur S2 par aane wali sabhi write requests ko error de denge ya intezaar karayenge.
    * **Nateeja:** System **Consistent** hai, par ab aapka aadha system (S2) write requests ke liye **Available** nahi hai. Aapne **Availability (A)** ko qurbaan kar diya.

**CA (Consistent & Available) System** sirf ek aisi aadarsh duniya mein ho sakta hai jahan network kabhi fail na ho. Asli duniya mein aisa nahi hota, isliye CA ek practical choice nahi hai.

#### **What to choose, CP or AP?**

Ye aapke business ki zaroorat par nirbhar karta hai.

* **CP Chunein:** Jab data ki shuddhta (correctness) sabse upar ho.
    * **Use Case:** Banking, Payments, Stock Trading. (Galat balance dikhane se behtar hai, error dikha do).
    * **Examples:** MongoDB, Redis (in some configurations), HBase.
* **AP Chunein:** Jab system ka "always ON" rehna sabse upar ho.
    * **Use Case:** Social media, content delivery, status updates. (Ek like thodi der baad dikhe to a
        chha hai, par poori site down nahi honi chahiye).
    * **Examples:** Cassandra, DynamoDB, CouchDB.

---
---

### **3.5. Other Core Principles**

#### **Maintainability (System Ki Dekhbhal)**

* **Yeh Hai Kya? (What it is)**
    Maintainability ka matlab hai ki ek software system ko aage chalkar manage karna, usmein badlav karna, bugs theek karna, ya naye features jodna kitna aasan hai.
* **Kaise Haasil Karein? (How to achieve it)**
    * Saaf-suthra aur well-documented code likhna.
    * Modular architecture (jaise microservices) ka istemal karna.
    * A
        chhe automated tests likhna.
    * System ko aasan aur samajhne laayak rakhna.

#### **Performance Optimization Techniques**

Ye un techniques ka sangrah hai jisse system ko tez banaya jaata hai:
* **Caching:** Har jagah cache ka istemal karna (browser, CDN, server, database).
* **Database Indexing:** Database mein reads ko tez karne ke liye.
* **Load Balancing:** Traffic ko servers ke beech baantna.
* **Asynchronous Operations:** Lambe tasks ke liye message queues ka istemal karna.
* **CDN:** Static files (images, videos) ko users ke nazdeek se serve karna.
* **Right Tool for the Right Job:** Har kaam ke liye sahi database ya technology chunna.

#### **Cost & Performance Optimizations**

Aksar behtar performance zyada paison mein aati hai. Inke beech balance banana zaroori hai.
* **Auto Scaling:** Sirf utne hi resources ke liye pay karna jitne aap use kar rahe hain.
* **Reserved Instances (Cloud):** Lambe samay (1-3 saal) ke liye server book karke discount paana.
* **Choosing Right Storage Tiers:** Kam use hone wale data ko saste "cold storage" mein rakhna.
* **Code Optimization:** Ek a
    chha algorithm aapko kam powerful (aur saste) hardware par chalne de sakta hai.

#### **Software Cost Estimation**

* **Yeh Hai Kya? (What it is)**
    Ye ek software ko banane mein lagne wale samay aur paise (effort) ka anumaan lagane ki prakriya hai.
* **Kyun Zaroori Hai? (Why it's important)**
    Business planning, budget banane, aur project management ke liye ye bahut zaroori hai.
* **Mukhya Tareeke (Key Techniques)**
    * **Expert Judgment:** Anubhavi developers se unka anumaan poochna.
    * **Bottom-up Estimation:** Project ko chote-chote tasks mein todna, har task ka anumaan lagana aur fir sabko jod dena. Ye sabse a
        chha par sabse time-consuming tareeka hai.

---
### **Monolithic Architecture (Sab Kuch Ek Saath)**

* **Yeh Hai Kya? (What it is)**
    Monolithic, yaani "ek bada patthar". Ye ek traditional tareeka hai jismein poori application ek **single unit** ki tarah banayi jaati hai. User Interface (UI), Business Logic, aur Data Access Layer—sab kuch ek hi codebase mein tightly coupled hota hai aur ek hi process mein chalta hai.

* **Analogy**
    Ye ek **Swiss Army Knife** ki tarah hai. Saare tools (chaku, scissors, screwdriver) ek hi unit mein bandhe hue hain. Ya phir ye ek aisi multi-story building hai jahan saare departments (HR, Sales, Marketing) ek hi chhat ke neeche kaam karte hain.

* **Kab Use Karein?**
    Jab application choti ho, team choti ho, ya aap project ke shuruaati phase mein ho (jaise ek MVP - Minimum Viable Product banana). Shuru mein isse develop, test, aur deploy karna aasan hota hai.

---

### **Microservices Architecture (Chote-Chote Tukde)**

* **Yeh Hai Kya? (What it is)**
    Is approach mein ek badi application ko kai **chote-chote, independent services** ke collection ke roop mein banaya jaata hai. Har service ka apna ek specific kaam hota hai, uska apna codebase aur database hota hai, aur woh doosri services se network (APIs) ke through baat karti hai.

* **Analogy**
    Ye ek **shopping mall** jaisa hai. Mall (poori application) ke andar har dukaan (microservice) apne aap mein independent hai. Jooton ki dukaan ka kapdon ki dukaan se seedha koi lena-dena nahi. Har dukaan ka apna staff, apna stock, aur apna kaam karne ka tareeka hai. Aap ek dukaan ko renovate kar sakte hain bina poore mall ko band kiye.

* **Kab Use Karein?**
    Badi, complex applications ke liye. Isse alag-alag teams alag-alag services par aazadi se kaam kar sakti hain, har service ko uski zaroorat ke hisaab se alag se scale kiya jaa sakta hai, aur aap alag-alag services ke liye alag-alag technology (language/database) bhi use kar sakte hain.

---

### **Microservices vs. Monoliths**

| Feature | Monolithic Architecture | Microservices Architecture |
| :--- | :--- | :--- |
| **Deployment** | Poori application ek saath deploy hoti hai. Ek chota sa change bhi poore system ki deployment maangta hai. | Har service ko alag-alag, aazadi se deploy kiya jaa sakta hai. |
| **Scalability** | Poori application ko scale karna padta hai, bhale hi load sirf ek feature par ho. (Mehenga) | Sirf uss service ko scale kiya jaata hai jis par load hai. (Sasta aur efficient) |
| **Development** | Shuru mein aasan. Sab kuch ek jagah hai. Par jaise-jaise bada hota hai, complex ho jaata hai. | Kai teams ek saath alag-alag services par tezi se kaam kar sakti hain. |
| **Complexity** | Kam complex (shuru mein). | Bahut complex. Ye ek distributed system hai jismein network latency, service discovery jaise issues aate hain. |
| **Fault Tolerance** | Ek hisse mein bug poori application ko crash kar sakta hai. | Ek service ke fail hone se zaroori nahi ki poori application down ho jaaye. |

---

### **How Monoliths are Migrated (Monolith Se Microservices Mein Kaise Jaayein)**

Iska sabse popular tareeka hai **Strangler Fig Pattern**.

* **Analogy**
    Ek "strangler fig" ka paudha ek purane, bade ped par ugta hai. Dheere-dheere uski jadein purane ped ko jakad leti hain aur apna ek naya, mazboot structure bana leti hain. Ek din purana ped andar hi andar sad jaata hai aur sirf naya, mazboot paudha bachta hai.

* **Steps**
    1.  **Identify:** Monolith mein se koi ek feature (jaise 'Payment processing') chuno jise alag karna hai.
    2.  **Build:** Uss feature ko ek nayi, independent microservice ke roop mein banao.
    3.  **Redirect (Strangle):** Ek **Proxy** (router) ko monolith ke aage rakho. Ab jab bhi payment ki request aayegi, to proxy use nayi microservice par bhej dega. Baaki saari requests abhi bhi purane monolith par jaayengi.
    4.  **Repeat:** Dheere-dheere ek-ek karke baaki features ke liye bhi yahi process dohrao, jab tak poora monolith microservices se replace na ho jaaye.

---

### **Event-Driven Architecture (EDA) (Ghatna-Aadharit)**

* **Yeh Hai Kya? (What it is)**
    Ye ek aisi architecture hai jismein services aapas mein **events** (ghatnaayein) ke through communicate karti hain. Ek 'event' state mein hue kisi bhi zaroori badlav ko kehte hain, jaise "Order Placed", "User Registered", ya "Payment Failed". Services ek doosre ko seedhe call karne ke bajaye, events bhejti aur sunti hain.

* **Kyun Use Karein?**
    Isse services **loosely coupled** (aapas mein kam nirbhar) aur **asynchronous** ho jaati hain. "Order Service" ko ye janne ki zaroorat nahi ki "Notification Service" hai ya nahi. Woh bas "Order Placed" event publish kar deti hai. Jisko bhi is event mein interest hai (jaise Notification Service, Inventory Service), woh ise sunkar apna kaam karega.

* **Iske Prakaar**
    1.  **Simple Event Notification:** Event mein sirf basic jaankari hoti hai (e.g., `{"orderId": "123"}`). Jisko ye event milta hai, use poori detail ke liye producer service ko wapas call karna padta hai.
    2.  **Event-Carried State Transfer:** Event mein hi saari zaroori jaankari hoti hai (e.g., `{"orderId": "123", "product": "Laptop", "amount": 50000}`). Isse consumer ko wapas call karne ki zaroorat nahi padti, jisse decoupling aur behtar hoti hai.

---

### **Client-Server Architecture**

* **Yeh Hai Kya? (What it is)**
    Ye internet ki sabse buniyadi architecture hai. Isme do players hote hain:
    * **Client:** Jo services ya data ke liye request karta hai (e.g., aapka web browser, mobile app).
    * **Server:** Jo us request ko poora karta hai aur data/service provide karta hai (e.g., Google ka web server).
    * **Analogy:** Restaurant mein customer (Client) khane ka order (request) deta hai aur kitchen (Server) us order ko banakar serve (response) karta hai.

---

### **Peer-to-Peer (P2P) Architecture**

* **Yeh Hai Kya? (What it is)**
    Ye ek aisi architecture hai jismein koi central server nahi hota. Har computer ya node ek **"peer"** hota hai. Har peer barabar hota hai aur woh client aur server, dono ki tarah kaam kar sakta hai.

* **Analogy**
    Ye ek **potluck party** jaisa hai. Sab log apna-apna khana laate hain aur ek doosre ke saath share karte hain. Koi ek host ya central kitchen nahi hota.

* **Use Cases:** BitTorrent (file sharing), Blockchain/Cryptocurrencies (Bitcoin).

---

### **Serverless Architecture**

* **Yeh Hai Kya? (What it is)**
    Ye cloud computing ka ek model hai jahan aapko servers manage karne ki chinta nahi karni padti. Aap apna code **functions** ke roop mein likhte hain, aur cloud provider (jaise AWS) un functions ko zaroorat padne par apne aap chalata hai aur scale karta hai.

* **Galatfehmi:** Iska naam "serverless" hai par iska matlab ye nahi ki server hote hi nahi. Server hote hain, par unhe aap nahi, cloud provider manage karta hai.

* **Analogy**
    Ye **taxi (Serverless)** use karne jaisa hai, apni **car khareedne (traditional server)** ke muqable. Taxi mein aap sirf utne hi paise dete hain jitna aap safar karte hain. Aapko car ki maintenance, insurance ya parking ki chinta nahi karni padti.

* **Use Cases:** AWS Lambda, Google Cloud Functions.

---

### **Stateful vs. Stateless Architecture**

* **Stateless (Jise Kuch Yaad Nahi Rehta)**
    * Isme server client ki pichli requests ke baare mein koi jaankari store nahi karta. Har request ko ek naye request ki tarah treat kiya jaata hai. Saari zaroori jaankari (state) client khud bhejta hai.
    * **Analogy:** Ek vending machine. Aap har baar sikka daalte hain aur ek nayi transaction karte hain. Machine ko yaad nahi rehta ki aap pehle bhi aaye the. **Zyadatar modern web applications stateless hoti hain taaki unhe aasani se scale kiya jaa sake.**

* **Stateful (Jise Sab Yaad Rehta)**
    * Isme server client ke session ki jaankari (state) yaad rakhta hai.
    * **Analogy:** Ek insaan se baat-cheet. Use yaad rehta hai ki aapne ek minute pehle kya kaha tha.
    * **Use Cases:** Online multiplayer games (server ko har player ki position yaad rakhni padti hai), shopping cart (jahan server aapke cart ka data session mein rakhta hai).

---

### **Pub/Sub Architecture**

* **Yeh Hai Kya? (What it is)**
    Ye **Event-Driven Architecture (EDA)** ko laagoo karne ka ek pattern hai. Iske components vahi hain:
    * **Publisher (Prakashak):** Jo event/message bhejta hai.
    * **Topic (Vishay):** Ek channel jahan message publish hota hai.
    * **Subscriber (Grahak):** Jo topic ko sunta hai aur message receive karta hai.
    Ye pattern services ko ek doosre se poori tarah se decouple kar deta hai.

---
### **4.2. Architectural Patterns**

#### **Circuit Breaker Pattern**

* **Yeh Hai Kya? (What it is)**
    Ye ek design pattern hai jo ek aisi service ko baar-baar call karne se rokta hai jo fail ho rahi ho. Iska maqsad failing service ko recover hone ka time dena aur client application ko bekaar ki koshishon se bachana hai.

* **Analogy**
    Ise aap apne ghar ke **electrical circuit breaker** ki tarah sochiye. Jab power surge (bahut saari failed requests) hota hai, to breaker "trip" kar jaata hai aur us appliance tak power jaana band ho jaati hai. Isse aapka appliance (calling service) aur ghar ki wiring (network) dono bach jaate hain.

* **Kaise Kaam Karta Hai? (Iske 3 States Hote Hain)**
    1.  **Closed:** Sab kuch theek hai. Requests failing service tak jaa rahi hain.
    2.  **Open:** Jab kuch requests lagatar fail ho jaati hain, to circuit "Open" ho jaata hai. Ab agle kuch samay tak, koi bhi request us service tak nahi jaayegi; woh turant fail ho jaayegi. Isse failing service ko aaram milta hai.
    3.  **Half-Open:** Ek timeout ke baad, circuit "Half-Open" state mein jaata hai. Ye ek test request ko aage jaane deta hai. Agar woh request pass ho gayi, to circuit wapas "Closed" ho jaata hai. Agar fail ho gayi, to wapas "Open" ho jaata hai.

---

#### **Event Sourcing Pattern**

* **Yeh Hai Kya? (What it is)**
    Is pattern mein hum kisi cheez ki **current state** (abhi ki sthiti) ko store nahi karte. Iske bajaye, hum us cheez par hue saare **events (ghatnaaon)** ki series ko ek-ke-baad-ek store karte hain. Current state ko jab bhi jaanna ho, hum shuru se saare events ko replay (dobara chala kar) calculate kar lete hain.

* **Analogy**
    Sochiye, aap apne bank account ka sirf current balance (`₹10,000`) store karne ke bajaye, har ek transaction (`+₹15000 salary`, `-₹2000 rent`, `-₹3000 shopping`) ko store kar rahe hain. Jab bhi aapko current balance jaanna ho, aap shuru se saare transactions ko jod-ghata kar nikal sakte hain.

* **Kyun Zaroori Hai?**
    Isse aapko ek poora **audit trail** mil jaata hai ki system mein kab, kya hua. Aap system ki state ko kisi bhi purane point-in-time par reconstruct kar sakte hain, jo debugging aur analytics ke liye bahut powerful hai.

---

#### **CQRS (Command Query Responsibility Segregation) Design Pattern**

* **Yeh Hai Kya? (What it is)**
    CQRS ka matlab hai **Command Query Responsibility Segregation**. Ye ek pattern hai jismein hum data ko **likhne (write)** ke model ko data ko **padhne (read)** ke model se bilkul alag kar dete hain.

* **Analogy**
    Ek library sochiye.
    * **Likhne ka Kaam (Command):** Ek nayi kitab ko library mein add karne ka process complex hota hai. Use catalog karna, stamp lagana, sahi shelf par rakhna. Ye write operation hai.
    * **Padhne ka Kaam (Query):** Ek kitab ko dhoondne ka process bahut aasan aur fast hota hai. Aap seedhe computer mein search karte hain aur aapko pata chal jaata hai ki kitab kahan hai.
    Library mein likhne (librarian ka model) aur padhne (visitor ka model) ke kaam alag-alag hain aur apne-apne liye optimized hain.

* **Kaise Kaam Karta Hai?**
    * **Command Side:** `Create`, `Update`, `Delete` operations ko handle karta hai. Iska focus data consistency aur validation par hota hai. (Aksar ek hi master database hota hai).
    * **Query Side:** Sirf `Read` operations ko handle karta hai. Iska focus high performance par hota hai. (Aksar iske liye kai saare read-replica databases hote hain jo denormalized hote hain).

---
---

### **5.1. Distributed Systems Concepts**

#### **What are Distributed Systems?**

* **Yeh Hai Kya? (What it is)**
    Ye ek aisa system hai jiske components alag-alag computers par chalte hain, jo ek network se jude hote hain. Ye saare components aapas mein message bhej kar communicate karte hain aur ek saath milkar ek kaam ko poora karte hain. User ko aisa lagta hai jaise woh ek hi system se baat kar raha hai.

* **Analogy**
    Ek bade restaurant ki kitchen. Har chef (computer/node) ka apna ek kaam hai (sabzi kaatna, grill karna, plating karna). Sab aapas mein communicate karke ek poora meal (final task) taiyaar karte hain. Customer ko sirf final meal dikhta hai, kitchen ke andar ka complex coordination nahi. **Poora internet ek bahut bada distributed system hai.**

---

#### **Consensus Algorithms**

* **Yeh Hai Kya? (What it is)**
    Ye ek aisi prakriya hai jisse ek distributed system ke saare nodes (computers) kisi ek value ya decision par **sehmat (agree)** hote hain, bhale hi network mein kuch nodes fail ho jaayein ya messages late ho jaayein.

* **Kyun Zaroori Hai?**
    Distributed systems mein "sach" kya hai, is par sehmati banana bahut zaroori hai. For example: "Kaun sa server abhi Leader hai?" ya "Kya is transaction ko commit karna hai?". Consensus algorithms is sehmati ko paane mein madad karte hain.

* **Analogy**
    Kai generals ki fauj ko ek saath attack karna hai. Sabko "attack at dawn" ya "retreat" par agree karna hoga. Wo aapas mein messengers bhejte hain. Bhale hi kuch messengers pakde jaayein (message loss) ya kuch generals gaddar hon (faulty nodes), ye algorithm ensure karta hai ki saare wafadar generals ek hi decision lein.
* **Examples:** Paxos, Raft.

---

#### **Auto-Recoverable System using Leader Election**

* **Yeh Hai Kya? (What it is)**
    Ye system ko fault-tolerant banane ka ek tareeka hai. Servers ke ek group (cluster) mein, ek server ko **Leader** chuna jaata hai. Leader hi saare zaroori kaam ko coordinate karta hai. Baaki saare servers **Followers** hote hain.

* **Auto-Recovery Kaise Hoti Hai?**
    Followers lagatar Leader par nazar rakhte hain (heartbeats ke through). Agar Leader crash ho jaata hai ya response dena band kar deta hai, to saare Followers aapas mein milkar ek **election** shuru karte hain aur apne mein se hi ek naye Leader ko chun lete hain. Ye sab apne aap hota hai, bina kisi insaan ke. Isse system Leader ke fail hone se recover kar jaata hai.

---

#### **Service Discovery and Heartbeats**

* **Service Discovery:** Microservices environment mein, servers aate-jaate rehte hain (auto-scaling ke kaaran). Unke IP addresses badalte rehte hain. Service Discovery ek aisi mechanism hai jisse ek service (e.g., Order Service) doosri service (e.g., Payment Service) ka current address apne aap dhoondh sakti hai. Ye ek "automatic phonebook" jaisa hai jo hamesha updated rehti hai.

* **Heartbeats:** Ye ek "main zinda hoon" signal hai. Ek service lagatar thodi-thodi der mein ek central system (ya doosri service) ko ek chota sa message (heartbeat) bhejti rehti hai. Agar uss service se heartbeat aana band ho jaata hai, to system maan leta hai ki woh service crash ho gayi hai.

---

#### **Distributed Tracing**

* **Yeh Hai Kya? (What it is)**
    Microservices mein, ek user request kai alag-alag services se hokar guzarti hai. Distributed tracing uss request ki poori journey ko **trace (track)** karne ka ek tareeka hai.

* **Kaise Kaam Karta Hai?**
    Jab request system mein enter karti hai, use ek unique **Trace ID** de di jaati hai. Request jitni bhi services se guzarti hai, ye ID uske saath chalti hai. Isse aap dekh sakte hain ki request ne kis service mein kitna time bitaya.

* **Kyun Zaroori Hai?**
    Isse debugging bahut aasan ho jaati hai. Agar ek request slow hai ya fail ho rahi hai, to aap tracing se aaram se pata laga sakte hain ki problem kis service mein hai.

---

#### **What are Containers?**

* **Yeh Hai Kya? (What it is)**
    Container, software ka ek **lightweight, standalone package** hota hai jismein us software ko chalane ke liye zaroori har cheez hoti hai: code, runtime (e.g., Java, Node.js), system libraries, settings.

* **Analogy**
    Ek **shipping container**. Aap uske andar kuch bhi pack kar sakte hain (furniture, electronics) aur woh container kisi bhi jahaz, train, ya truck se transport ho sakta hai. Transport company ko ye chinta nahi karni padti ki andar kya hai. Bilkul waise hi, ek software container kisi bhi machine par (developer ke laptop, cloud server) chal sakta hai, bas us machine par container runtime (jaise Docker) hona chahiye.

* **Famous Technology:** **Docker** containers banane ke liye sabse popular tool hai. **Kubernetes** un hazaaron containers ko bade scale par manage karne (orchestrate) ke liye use hota hai.

---

#### **CI/CD Pipeline**

* **Yeh Hai Kya? (What it is)**
    Ye software ko banane se lekar users tak pahunchane ke process ko **automate** karne ka ek tareeka hai.
* **Iske Do Hisse Hain:**
    * **CI (Continuous Integration):** Is practice mein, developers apna code baar-baar ek central repository (jaise Git) mein merge karte rehte hain. Har merge ke baad, code apne aap build aur test hota hai. Isse bugs jaldi pakde jaate hain.
    * **CD (Continuous Delivery / Deployment):**
        * **Continuous Delivery:** Code har test pass karne ke baad, release ke liye apne aap taiyaar ho jaata hai. Ek click par use production mein daala jaa sakta hai.
        * **Continuous Deployment:** Isme, har passed code apne aap, bina kisi ke click kiye, seedhe production mein deploy ho jaata hai.
* **Kyun Zaroori Hai?**
    Isse software release karna tez, bharosemand, aur kam risky ho jaata hai.

---

### **5.2. Specialized Tools & Concepts**

#### **Distributed Rate Limiting**

* **Rate Limiting (Raftaar Par Niyantran)**
    * **Yeh Hai Kya?** Ye ek technique hai jisse hum control karte hain ki koi user ya client ek diye gaye samay mein hamari service ko kitni baar request kar sakta hai.
    * **Analogy:** Ye ek sarkari rashan ki dukaan jaisa hai jo kehti hai, "Ek aadmi ek mahine mein sirf 5kg cheeni le sakta hai." Isse koi ek aadmi saara stock jama nahi kar paata aur sabko fayda milta hai. Rate limiting bhi yahi karti hai: ye kisi ek user ko saare server resources istemal karne se rokti hai.
    * **Kyun Zaroori Hai?** Isse hum apne system ko bure niyat wale users (hackers), bots se bachate hain, Denial-of-Service (DoS) attacks rokte hain, aur sabhi users ke liye ek fair experience sunishchit karte hain.

* **Rate Limiting Algorithms (Niyantran Ke Tareeke)**
    1.  **Token Bucket:** Ek baalti (bucket) sochiye jismein lagatar ek nishchit dar se tokens gir rahe hain. Har request karne ke liye, user ko ek token istemal karna padta hai. Agar bucket mein token nahi hai, to request reject ho jaati hai. Ye achanak aane wale traffic bursts ko a
        chhe se handle karta hai.
    2.  **Leaky Bucket:** Ek aisi baalti sochiye jiske neeche ek chota sa chhed hai. Requests paani ki tarah upar se girti hain, aur chhed se ek nishchit dar par process hokar nikalti hain. Agar baalti bhar jaati hai (bahut saari requests ek saath aa jaati hain), to nayi requests gir jaati hain (reject ho jaati hain). Ye request rate ko smooth karta hai.
    3.  **Fixed Window Counter:** Sabse aasan. Ek time window (e.g., 1 minute) mein aane wali requests ko gina jaata hai. Agar ginti limit se paar ho jaati hai, to requests reject ho jaati hain. Agle minute mein counter reset ho jaata hai.

* **Distributed Rate Limiting (Jab Kai Servers Hon)**
    * **Chunauti (Challenge):** Jab aapke paas 10 web servers hon, to rate limit kaise laagoo karein? Agar har server apni alag ginti rakhega, to user 10 server par limit se 10 guna zyada requests bhej sakta hai.
    * **Samadhan (Solution):** Ek **centralized data store** jaise **Redis** ka istemal kiya jaata hai. Har server, request process karne se pehle, Redis mein jaakar count check aur update karta hai. Isse limit poore system (cluster) par ek saath laagoo hoti hai.

#### **What are Bloom Filters?**

* **Yeh Hai Kya? (What it is)**
    Ye ek bahut hi space-efficient (kam jagah lene wala), probabilistic (sambhavna par aadharit) data structure hai jiska istemal ye check karne ke liye hota hai ki koi element ek set (samuh) ka hissa hai ya nahi.

* **Analogy**
    Ise ek bahut hi kushal (efficient) par thoda bhulakkad security guard samjhiye. Guard ke paas approved guests ki list hai.
    * Jab aap guard se puchte hain, "Kya 'Amit' list mein hai?" aur guard kehta hai "**Nahi**", to aap **100% sure** ho sakte hain ki Amit list mein nahi hai (**No False Negatives**).
    * Jab aap puchte hain, "Kya 'Sumit' list mein hai?" aur guard kehta hai "**Haan**", to is baat ki **sambhavna zyada hai** ki woh list mein hai, par ek chota sa chance hai ki guard ko galatfehmi hui ho (**Can have False Positives**). Ho sakta hai Sumit jaisa dikhne wala koi aur list mein ho.

* **Kahan Istemal Hota Hai?**
    Jab aapko ek "shayad" wala jawab a
    chha ho par ek "pakka nahi" wala jawab 100% a
    chha chahiye ho. Jaise:
    * Ye check karne ke liye ki koi username pehle se liya jaa chuka hai ya nahi.
    * Google Chrome iska istemal malicious (khatarnak) URLs ko block karne ke liye karta hai.
    * Iska mukhya fayda hai ki ye ek mehenge operation (jaise database lookup) ko karne se bachata hai agar element "pakka nahi" hai.

#### **Big Data Tools**

* **Yeh Hai Kya? (What is Big Data)**
    Big Data us data ko kehte hain jo itna **bada (Volume)**, itni **tez (Velocity)**, aur itni **tarah ka (Variety)** hota hai ki use traditional tools se process karna mushkil hota hai.
* **Mukhya Tools Ka Ecosystem**
    * **Storage:** **HDFS (Hadoop Distributed File System)**. Ye ek aisi file system hai jo bahut bade data ko kai saste computers ke cluster mein baant kar store karti hai.
    * **Processing:** **MapReduce** (purana) aur **Apache Spark** (naya aur tez). Ye aise frameworks hain jo uss bade data ko parallel mein, kai computers par ek saath process karte hain. Spark tez hai kyunki ye in-memory processing karta hai.
    * **Querying:** **Apache Hive**, jo HDFS par rakhe data par SQL jaisi query chalane deta hai.

---
---

### **5.3. Security (Suraksha)**

#### **Security Measures in System Design**

Security ek feature nahi, balki system ki **neenv (foundation)** hai. Iske kuch buniyadi siddhant hain:
* **Defense in Depth (Kai Staron Ki Suraksha):** Sirf ek lock par nirbhar na rehna. Jaise ek kile mein pehle paani ki khaai, fir oonchi deewar, fir pehredaar, aur fir tijori hoti hai.
* **Principle of Least Privilege (Kam Se Kam Adhikaar):** Har user ya service ko sirf utni hi permissions do jitni uska kaam karne ke liye zaroori hai, usse zyada nahi.
* **Encrypt Everything (Sab Kuch Encrypt Karein):** Data ko network par bhejte samay (**in-transit**) aur disk par store karte samay (**at-rest**), dono time encrypt karke rakhein.

#### **Authentication and Authorization**

Ye security ke do alag-alag par zaroori concept hain.
* **Authentication (AuthN - Aap Kaun Hain?):** Ye pehchan pramanit karne ki prakriya hai.
    * **Analogy:** Ek building mein enter karte waqt apna ID card dikhana **Authentication** hai.
    * **Examples:** Username/Password, OTP, Biometrics.
* **Authorization (AuthZ - Aap Kya Kar Sakte Hain?):** Ye pramanit hone ke baad, ye check karne ki prakriya hai ki aapko kya-kya karne ki anumati hai.
    * **Analogy:** Guard ka ID card dekhne ke baad, ek list check karna ki kya aapko server room mein jaane ki permission hai ya nahi, ye **Authorization** hai.
    * **Examples:** Admin user vs. Normal user.

* **OAuth:** Ye ek **Authorization** framework hai. Ye ek user ko anumati deta hai ki woh kisi third-party app ko apne data (jo kisi aur service par hai) ka limited access de sake, bina apna password share kiye. "Login with Google" iska sabse a
    chha example hai.

* **Token Based Authentication:** Isme user login karne ke baad, server use ek digitally signed **token** (ek temporary, encrypted ID card jaisa, e.g., JWT) deta hai. Client apni har agli request ke saath is token ko bhejta hai. Server ko bas token ki validity check karni padti hai, baar-baar database mein user dhoondhne ki zaroorat nahi padti.

* **Access Control Lists (ACLs) and Rule Engines:**
    * **ACL:** Ek simple list jo batati hai ki kis user ko kis resource par kya permission hai (e.g., `File_A`: `Amit` can `Read`, `Priya` can `Read/Write`).
    * **Rule Engine:** Ek zyada flexible system jo "rules" ke aadhar par decision leta hai (e.g., "Ek manager ₹50,000 tak ka kharcha approve kar sakta hai, par sirf apne hi department ka").

#### **SSL/TLS (Secure Socket Layer / Transport Layer Security)**

* **Yeh Hai Kya? (What it is)**
    Ye cryptographic protocols hain jo internet par secure communication pradaan karte hain. TLS, SSL ka naya aur zyada secure version hai. Jab aap browser mein `https://` aur ek taale (padlock) ka icon dekhte hain, to woh TLS hi hai.
* **Ye Kya Pradaan Karta Hai?**
    1.  **Encryption:** Data ko scramble kar deta hai taaki koi beech mein use padh na sake.
    2.  **Authentication:** Sunishchit karta hai ki aap sahi server se hi baat kar rahe hain.
    3.  **Integrity:** Sunishchit karta hai ki data ke saath raaste mein koi chhed-chhad nahi hui hai.

#### **Secure Software Development Life Cycle (SSDLC)**

* **Yeh Hai Kya? (What it is)**
    Ye software banane ke poore process (SDLC) mein, har phase mein security activities ko jodne ki practice hai. Security ko aakhri step na maankar, shuru se hi dhyan mein rakha jaata hai.
* **Mukhya Activities**
    * **Design:** Threat Modeling karna (kahan-kahan se attack ho sakta hai, ye sochna).
    * **Development:** Secure coding practices ka istemal karna.
    * **Testing:** Penetration Testing (system ko hack karne ki koshish karna) aur security scanning karna.
    * **Deployment:** Server ko a
        chhe se configure karna.
    * Iska maqsad hai security issues ko jaldi se jaldi pakadna aur theek karna, kyunki development ke shuruaat mein ek bug theek karna, release ke baad theek karne se kahin zyada sasta aur aasan hota hai.

---



### **5.4. Testing & Recovery**

#### **Unit Testing**

* **Yeh Hai Kya? (What it is)**
    Ye software testing ka sabse pehla aur sabse buniyadi star (level) hai. Isme hum software ke sabse **chote, individual hisse (units)** ko alag se test karte hain. Ek "unit" aam taur par ek akela function ya method hota hai.

* **Analogy**
    Ek car engine banane se pehle, mechanic har ek chote part (jaise spark plug, piston) ko alag se check karta hai ki woh theek se kaam kar raha hai ya nahi. Yahi unit testing hai.

* **Kyun Zaroori Hai?**
    Ye bugs ko bahut shuruaati stage mein hi pakad leta hai, jisse unhe theek karna aasan aur sasta hota hai. Ye tez hote hain aur developers ko confidence dete hain ki unka likha hua code sahi kaam kar raha hai.

#### **Integration Testing**

* **Yeh Hai Kya? (What it is)**
    Jab saare individual parts (units) akele-akele sahi kaam kar rahe hon, to agla kadam unhe **jodkar (integrate karke)** test karna hota hai. Integration testing ye check karta hai ki alag-alag modules ek saath milkar sahi dhang se kaam kar rahe hain ya nahi.

* **Analogy**
    Car mechanic ne saare parts alag-alag check kar liye (unit testing). Ab woh spark plug aur piston ko jodkar engine ke ek chote hisse ko chala kar dekhta hai ki woh theek se kaam kar rahe hain ya nahi.

* **Kyun Zaroori Hai?**
    Ye un bugs ko pakadta hai jo alag-alag modules ke beech communication mein aate hain. Jaise ek module se doosre module mein galat data jaana, ya API calls mein mismatch hona.

#### **Data Backup and Disaster Recovery**

* **Data Backup (Data Ki Copy Banana)**
    * **Yeh Hai Kya?** Ye aapke data ki copies banane ka process hai taaki agar original data kho jaaye (delete ho jaaye, corrupt ho jaaye), to aap in copies ka istemal karke use **restore** kar sakein.
    * **Analogy:** Apne zaroori documents (jaise passport, degree) ki photocopy karwake ek alag file mein rakhna data backup hai.

* **Disaster Recovery (DR) (Aapda Se Ubharna)**
    * **Yeh Hai Kya?** Ye ek poora plan aur set of procedures hai jisse aap ek badi aapda (jaise aag, bhukamp, ya bada cyberattack) ke baad apne poore IT system aur business ko wapas chalu kar sakein. **Data backup, Disaster Recovery plan ka ek hissa hai.**
    * **Analogy:** Agar aapka poora ghar jal jaata hai (disaster), to DR plan mein likha hoga ki aap kahan rahenge, naye kapde kahan se aayenge, aur un photocopied documents (backup) ka istemal karke naye ID cards kaise banwayenge.
    * **Mukhya Metrics:**
        * **RPO (Recovery Point Objective):** Aap kitna data kho sakte hain? (e.g., agar aap har 24 ghante mein backup lete hain, to RPO 24 ghante hai).
        * **RTO (Recovery Time Objective):** Aapda ke baad aapko kitni der mein wapas online aana hai? (e.g., 2 ghante).

---
---

### **5.5. Design Process (Interview Mein Kaise Approach Karein)**

#### **How to solve any System Design Problem?**

System design interview ko solve karne ke liye ek structured approach follow karna bahut zaroori hai. Isse aap kuch bhi miss nahi karenge.

* **Step 1: Requirements Clarification (4-5 mins)**
    * **Sawaal Puchiye!** Kabhi bhi assume mat kijiye. Interviewer se functional requirements (e.g., "Kya users ko video upload karne ki anumati hai?") aur non-functional requirements (e.g., "System kitna available hona chahiye?", "Response time kitna tez hona chahiye?") clear kijiye. Scope ko define kijiye.

* **Step 2: Back-of-the-envelope Estimation (2-3 mins)**
    * Ek **rough andaza** lagaiye. Kitne users honge (DAU)? Kitna traffic aayega (QPS)? Kitna storage lagega (TB/PB)? Kitni bandwidth chahiye hogi? Isse aapko system ke scale ka idea lag jaata hai.

* **Step 3: High-Level Design (HLD) (10-15 mins)**
    * **Bade-bade dabbe (boxes) banaiye.** Whiteboard par main components jaise Load Balancer, Web Servers, Application Servers, Databases, Cache, CDN ko draw kijiye. Unke beech arrows banakar data flow dikhaiye. Basic APIs (e.g., `uploadVideo()`, `getVideo()`) define kijiye.

* **Step 4: Deep Dive (15-20 mins)**
    * Ab interviewer aapse kisi ek component par **zoom in** karne ko kahega. Jaise, "Database ko kaise scale karoge?" ya "Video upload hone ka poora flow detail mein samjhao." Yahan aapko Sharding, Replication, Caching policies, Message Queues jaise concepts discuss karne honge.

* **Step 5: Identify Bottlenecks & Discuss Trade-offs (5 mins)**
    * Apne design ki kamiyon (bottlenecks) ko khud pehchaniye. Jaise, "Database yahan par ek bottleneck ban sakta hai."
    * Apne decisions ko **justify** kijiye. "Maine yahan NoSQL database chuna kyunki humein horizontal scaling ki zaroorat hai aur eventual consistency se kaam chal jaayega." Har design choice ek trade-off hota hai, use zaroor discuss karein.

#### **How to Draw High Level Design Diagram?**

* **Saaf aur Saral Rakhein:** Ye ek communication tool hai, isse complex na banayein.
* **Standard Shapes Use Karein:** Services ke liye **Rectangles**, Databases ke liye **Cylinders**.
* **Arrows Banayein:** Data ya request ke flow ko dikhane ke liye arrows ka istemal karein aur un par label likhein (e.g., "HTTP Request").
* **Label Karein:** Har component ka naam saaf-saaf likhein (e.g., "API Gateway", "User DB (MySQL)").
* **Left to Right Flow:** User/Client se shuru karke (left mein) backend (right mein) ki taraf design banayein.

#### **Types of HLD Diagrams**

* **Component-Based Diagram**
    * **Yeh Hai Kya?** Ye sabse common HLD diagram hai. Isme system ke mukhya components (services, databases, caches) aur unke beech ke rishte (dependencies) dikhaye jaate hain. Ye system ka **static structure** batata hai.
        

* **Sequence Diagram**
    * **Yeh Hai Kya?** Ye diagram dikhata hai ki ek specific kaam ko poora karne ke liye alag-alag components aapas mein samay ke saath kaise interact karte hain. Isme messages ka sequence (kram) dikhaya jaata hai.
    * **Analogy:** Ye ek film ke scene ki script jaisa hai. Kaun sa character (component) kab, kisko, kya kehta hai (message bhejta hai). Ye system ka **dynamic behavior** batata hai.

* **Data Flow Diagram (DFD)**
    * **Yeh Hai Kya?** Ye diagram system mein **data ke bahaav (flow)** par focus karta hai, na ki control ke flow par. Ye dikhata hai ki data kahan se aata hai, kahan jaata hai, aur beech mein kaise process ya store hota hai.

* **Deployment Diagram**
    * **Yeh Hai Kya?** Ye diagram software components ka **physical deployment** hardware par dikhata hai. Yaani, kaun sa software (e.g., User Service) kaun se server (physical machine) par chal raha hai, aur kitne servers kis data center mein hain. Ye **infrastructure view** deta hai.

---


### **6.1. Core Concepts (Buniyadi Baatein)**

#### **What is Low-Level Design or LLD?**

* **Yeh Hai Kya? (What it is)**
    Low-Level Design (LLD) ek aisi prakriya hai jismein hum software ke **individual components ya modules ki internal details** ko design karte hain. Agar HLD system ka "bird's-eye view" (upar se dekhna) hai, to LLD "microscopic view" (zoom karke dekhna) hai. Isme hum har chote hisse ki working ko define karte hain.

* **Analogy**
    Sochiye, HLD mein aapne decide kiya ki aap ek ghar banayenge jismein ek kitchen, do bedroom, aur ek living room hoga.
    LLD mein aap kitchen ke andar jaakar ye decide karenge ki:
    * Sink kahan lagega?
    * Cabinets ka design kaisa hoga?
    * Fridge rakhne ki jagah kahan hogi?
    * Electrical switchboards kahan-kahan honge?

* **Iska Focus Kahan Hota Hai?**
    Class diagrams, methods ke naam aur unke parameters, data members, aur har function ke andar ka logic. LLD ka output actual code likhne ke liye ek detailed blueprint jaisa hota hai.

---

#### **Object-Oriented Programming (OOP) Concepts**

LLD ka base OOP hi hai. Ye ek programming style hai jo "objects" par aadharit hai. Iske 4 mukhya stambh (pillars) hain:

1.  **Encapsulation (Capsule Mein Band Karna)**
    * **Yeh Hai Kya?** Data (variables) aur uss data par kaam karne wale methods (functions) ko ek saath ek single unit (jise "class" kehte hain) mein baandh dena. Isse class ki internal complexity bahar ki duniya se chhip jaati hai.
    * **Analogy:** Ek dawai ka **capsule**. Capsule ke andar kya-kya chemicals hain (data) aur woh kaise kaam karte hain (methods), ye aapse chhipa rehta hai. Aapko bas capsule ko istemal karna (uska public method call karna) aana chahiye.

2.  **Abstraction (Sirf Zaroori Cheezein Dikhana)**
    * **Yeh Hai Kya?** Complex implementation details ko chhipana aur user ko sirf zaroori functionality hi dikhana.
    * **Analogy:** Ek car ka **steering wheel**. Aapko car modne ke liye bas steering ghumaana hai (ye interface hai). Steering ke peeche ki complex machinery (gears, axle) kaise kaam karti hai, ye aapse chhipa rehta hai (ye implementation hai). Abstraction "kya karna hai" batata hai, "kaise karna hai" nahi.

3.  **Inheritance (Virasat)**
    * **Yeh Hai Kya?** Ek aisi mechanism jisse ek class (Child Class) doosri class (Parent Class) ki properties aur methods ko virasat mein le sakti hai. Isse code ko dobara likhne (code reuse) ki zaroorat kam ho jaati hai.
    * **Analogy:** Aapko apne **parents** se kuch gun (jaise aankhon ka rang, height) virasat mein milte hain. Aapko unhe dobara se "banana" nahi padta.

4.  **Polymorphism (Ek Roop, Anek Kaam)**
    * **Yeh Hai Kya?** Iska shabdik arth hai "anek roop". Iska matlab hai ki koi cheez (method ya object) alag-alag situations mein alag-alag tarah se behave kar sakti hai.
    * **Analogy:** Ek `shape` object ka `draw()` method sochiye. Agar object `Circle` hai, to `draw()` method ek gola banayega. Agar object `Square` hai, to wahi `draw()` method ek square banayega. Naam ek (`draw`), par kaam alag-alag.

---

#### **Modularity and Interfaces**

* **Modularity (Tukdon Mein Todna)**
    * **Yeh Hai Kya?** Ek bade software system ko chote-chote, independent, aur aapas mein badle jaa sakne waale hisson (modules) mein todne ki practice.
    * **Analogy:** **Lego blocks** se kuch banana. Har block ek module hai. Aap in blocks ko jodkar kuch bhi bana sakte hain aur agar ek block kharab ho jaaye to use aasani se nikaal kar doosra laga sakte hain. Modularity se code ko manage karna aasan ho jaata hai.

* **Interfaces (Samjhauta / Contract)**
    * **Yeh Hai Kya?** Ek interface ek "contract" ki tarah hota hai. Ye batata hai ki ek class **kya-kya kar sakti hai**, par ye nahi batata ki **kaise karegi**. Ye sirf method ke naam batata hai, unki body (implementation) nahi.
    * **Analogy:** Ek **TV ka remote**. Remote (interface) par buttons hote hain jaise "Power", "Volume Up" (methods). Ye contract hai. Koi bhi company (Sony, Samsung) jo is remote ko support karna chahti hai, use in buttons ki functionality deni padegi. Sony TV volume kaise badhata hai aur Samsung TV kaise, ye unka internal mamla (implementation) hai. Interfaces abstraction aur modularity paane ka zaroori zariya hain.

---
---

### **6.2. Design Principles (Ache Design Ke Niyam)**

Ye kuch mashhoor niyam hain jo ek a
chha, maintainable LLD banane mein madad karte hain.

#### **SOLID Principles**

Ye 5 principles ka ek group hai:
* **S - Single Responsibility Principle (SRP):** Ek class ka badalne ka sirf **ek hi kaaran** hona chahiye. Yaani, ek class ko sirf ek hi kaam ki zimmedari leni chahiye.
* **O - Open/Closed Principle (OCP):** Software **extension ke liye open** hona chahiye, par **modification ke liye closed**. Yaani, aap naya feature add karne ke liye naya code likhein, purane, chalte hue code ko na badlein.
* **L - Liskov Substitution Principle (LSP):** Ek child class ko apne parent class ki jagah istemal kiya jaa sakna chahiye, bina kisi problem ke.
* **I - Interface Segregation Principle (ISP):** Ek bada, general-purpose interface banane se behtar hai, kai chote-chote, specific interfaces banayein. Client ko aise methods par depend karne ke liye force na karein jinki use zaroorat nahi.
* **D - Dependency Inversion Principle (DIP):** High-level modules ko low-level modules par depend nahi karna chahiye. Dono ko abstractions (interfaces) par depend karna chahiye.

---

#### **DRY (Don't Repeat Yourself) Principle**

* **Yeh Hai Kya?** "Apne aap ko dohrao mat". Code ya logic ko copy-paste mat karo. Har jaankari ya logic system mein sirf ek hi jagah honi chahiye.
* **Kyun?** Agar aapko us logic ko badalna pada aur woh 10 jagah copy kiya hua hai, to aap shayad 9 jagah badal denge aur ek jagah bhool jayenge, jisse bug aayega.

---

#### **KISS (Keep It Simple, Stupid) Principle**

* **Yeh Hai Kya?** "Cheezon ko saral rakho, bewakoof". Zyadatar systems tabhi a
    chhe se kaam karte hain jab unhe simple rakha jaata hai, na ki complex. Bewajah ki complexity se bachein.
* **Kyun?** Simple code ko samajhna, maintain karna, aur debug karna aasan hota hai.

---

#### **YAGNI (You Ain't Gonna Need It) Principle**

* **Yeh Hai Kya?** "Aapko iski zaroorat nahi padegi". Koi bhi functionality tab tak mat banao jab tak uski sach mein zaroorat na ho.
* **Kyun?** Future ke liye andaza lagakar features banane se bachein. Ho sakta hai unki kabhi zaroorat hi na pade aur aapka time barbaad ho. Ye over-engineering se bachata hai.

---


### **6.3. UML (Unified Modeling Language) (in detail)**

  * **Yeh Hai Kya? (What it is)**
    UML ek standard **graphical language** hai. Ye code nahi hai, balki code ke design ko **visualize** karne (tasveeron mein dikhane) ka ek tareeka hai. Ise software ke blueprint (naksha) ki tarah samjhiye. Jaise ek building banane se pehle architect uska naksha banata hai, waise hi software likhne se pehle developer uska UML diagram bana sakta hai.

  * **Kyun Zaroori Hai?**
    Isse alag-alag developers, managers, aur clients ke beech communication aasan ho jaata hai. Ek complex design ko shabdon mein samjhane se behtar hai, uska ek saaf-suthra diagram bana diya jaaye.

  * **LLD Mein Zaroori UML Diagrams**

    #### 1\. Class Diagram

    Ye LLD ka sabse zaroori diagram hai. Ye system ki classes, unke attributes (data members), operations (methods), aur unke beech ke rishton ko dikhata hai.

      * **Components:**
          * **Class:** Ek box jiske 3 hisse hote hain:
            1.  **Name:** Class ka naam (e.g., `Car`).
            2.  **Attributes:** Class ke variables (e.g., `-color: String`, `-speed: int`). (`-` ka matlab private, `+` ka matlab public).
            3.  **Operations:** Class ke methods (e.g., `+accelerate()`, `+brake()`).
      * **Relationships (Classes Ke Beech Ke Rishte):**
          * **Inheritance (Virasat):** Ek "is-a" rishta. (e.g., `Car` **is-a** `Vehicle`). Ise ek khaali teer (hollow arrow) se dikhaya jaata hai jo Parent class ki taraf point karta hai.
          * **Association:** Ek "has-a" rishta. Jab ek class doosri class ke objects ko use karti hai. (e.g., `Driver` **has-a** `Car`). Ise ek seedhi line se dikhaya jaata hai.
          * **Aggregation:** Ek kamzor "has-a" rishta. Jismein child object parent ke bina bhi exist kar sakta hai. (e.g., Ek `Department` ke paas `Professor` hote hain. Agar department band ho jaaye, to professor fir bhi exist karte hain). Ise ek khaali heere (hollow diamond) se dikhaya jaata hai.
          * **Composition:** Ek mazboot "owns-a" rishta. Jismein child object parent ke bina exist nahi kar sakta. (e.g., Ek `House` ke paas `Rooms` hote hain. Agar ghar toot jaaye, to kamre bhi khatam ho jaate hain). Ise ek bhare hue heere (filled diamond) se dikhaya jaata hai.

    **Example ASCII Diagram:**

    ```
    +----------------+       +-------------------+
    |    Vehicle     |<>-----|       Engine      |  // Composition
    +----------------+       +-------------------+
    | -maxSpeed: int |       | -horsepower: int  |
    +----------------+       +-------------------+
    | +start()       |       | +start()          |
    +----------------+       +-------------------+
            ^
            | (Inheritance)
    +----------------+
    |      Car       |
    +----------------+
    | -numDoors: int |
    +----------------+
    | +openTrunk()   |
    +----------------+
    ```

    #### 2\. Sequence Diagram

    Ye diagram, jaisa pehle discuss kiya, ye dikhata hai ki ek specific kaam (use case) ko poora karne ke liye alag-alag objects aapas mein kis sequence mein message bhejte hain. Ye system ke dynamic behavior ko dikhata hai.

-----

-----

### **6.4. Design Patterns (Samasya Suljhane Ke Bane-Banaye Tareeke)**

Design patterns, software engineering mein baar-baar aane wali common problems ke liye test kiye hue, reusable solutions hote hain. Ye 3 categories mein aate hain:

-----

#### **A. Creational Patterns (Objects Banane Ke Tareeke)**

1.  **Singleton Pattern**

      * **Kaam:** Ye sunishchit karta hai ki ek class ka **sirf ek hi object (instance)** ban sake aur uss object ko poore application mein kahin se bhi access kiya jaa sake.
      * **Analogy:** Ek desh ka **Pradhan Mantri**. Ek samay par ek hi Pradhan Mantri ho sakta hai. PM ka office ek singleton hai.

2.  **Factory Method Pattern**

      * **Kaam:** Ye object banane ke liye ek interface deta hai, par kaun si class ka object banana hai, ye subclasses ko decide karne deta hai.
      * **Analogy:** Ek logistics company. Uska kaam hai transport arrange karna. `RoadLogistics` factory `Truck` object banayegi, jabki `SeaLogistics` factory `Ship` object banayegi. Aap factory se transport maangte hain, woh aapko sahi type ka de deti hai.

3.  **Abstract Factory Pattern**

      * **Kaam:** Ye ek doosre se related objects ki ek **poori family** banane ke liye ek interface deta hai.
      * **Analogy:** Ek **IKEA** store. Aap wahan se ek poora furniture set (chair, table, sofa) khareed sakte hain jo aapas mein match karta ho. `ModernFurnitureFactory` aapko modern style ka poora set degi, jabki `VintageFurnitureFactory` vintage style ka set degi.

4.  **Builder Pattern**

      * **Kaam:** Ye ek complex object ke banane ke process ko uske representation se alag kar deta hai. Isse ek hi banane ke process se alag-alag tarah ke objects banaye jaa sakte hain.
      * **Analogy:** Ek **Subway** sandwich banana. Banane wala aapse step-by-step poochta hai: kaun si bread? Kaun si sabzi? Kaun si sauce? Ye process (builder) a
        chha hai aur isse aap kai tarah ke sandwiches (objects) bana sakte hain.

5.  **Prototype Pattern**

      * **Kaam:** Naye objects ko ek maujooda object (prototype) ki **copy** karke banana.
      * **Analogy:** Ek **rubber stamp (mohar)**. Aap ek hi stamp (prototype) se uski kai identical copies bana sakte hain. Ya phir, biology mein cell division.

-----

#### **B. Structural Patterns (Objects Ko Jodne Ke Tareeke)**

1.  **Adapter Pattern**

      * **Kaam:** Do alag-alag, incompatible interfaces waali classes ko ek saath kaam karne laayak banana.
      * **Analogy:** Ek **travel power adapter**. Aapka Indian mobile charger US ke socket mein fit nahi hota. Adapter beech mein lagkar dono ko compatible bana deta hai.

2.  **Decorator Pattern**

      * **Kaam:** Ek object mein, bina uski class badle, nayi functionality dynamically (runtime par) add karna.
      * **Analogy:** Ek **pizza**. Aap ek plain pizza base se shuru karte hain. Fir aap uspar cheese, mushrooms, olives jaise toppings (decorators) add karke uske feature (taste) badhate jaate hain.

3.  **Composite Pattern**

      * **Kaam:** Objects ko ek tree structure mein arrange karna. Isse aap ek akele object aur objects ke group (composition) ko ek hi tarah se treat kar paate hain.
      * **Analogy:** Ek computer ka **file system**. Ek folder (composite) ke andar files (leaf) aur doosre folders ho sakte hain. Aap `delete` operation ek akele file par bhi kar sakte hain aur ek poore folder par bhi.

4.  **Proxy Pattern**

      * **Kaam:** Ek object ke liye ek substitute ya placeholder pradaan karna, taaki uske access ko control kiya jaa sake.
      * **Analogy:** Ek **credit card**. Ye aapke bank account (asli object) ka proxy hai. Aap har jagah cash le jaane ke bajaye card use karte hain. Card security aur access control pradaan karta hai.

5.  **Facade Pattern**

      * **Kaam:** Ek bahut hi complex system ke liye ek simple, unified interface pradaan karna.
      * **Analogy:** Ek car ko start karne ka ek button (**facade**). Jab aap us button ko dabate hain, to peeche kai complex kaam hote hain (fuel pump start, ignition, sensors check). Facade is saari complexity ko aapse chhipa leta hai.

-----

#### **C. Behavioral Patterns (Objects Ke Beech Baatcheet Ke Tareeke)**

1.  **Observer Pattern**

      * **Kaam:** Jab ek object (Subject) ki state badalti hai, to us par depend karne wale saare objects (Observers) ko apne aap notify aur update kar dena.
      * **Analogy:** Ek **YouTube channel ko subscribe karna**. Creator (Subject) jab bhi nayi video daalta hai (state change), to saare subscribers (Observers) ko notification aa jaata hai.

2.  **Strategy Pattern**

      * **Kaam:** Algorithms ki ek family banana, har ek ko alag-alag class mein rakhna, aur unhe aapas mein interchangeable banana.
      * **Analogy:** **Google Maps**. Jab aap directions poochte hain, to aap strategy chun sakte hain: "Driving", "Walking", ya "Public Transport". App aapki chuni hui strategy ke hisaab se route batata hai.

3.  **Command Pattern**

      * **Kaam:** Ek request ko ek standalone object mein badal dena jismein us request se judi saari jaankari ho.
      * **Analogy:** Ek restaurant mein **order dena**. Aap waiter ko order batate hain. Waiter use ek slip (`Command Object`) par likhta hai. Ye slip fir kitchen (`Receiver`) ko de di jaati hai. Is slip ko queue mein lagaya jaa sakta hai, log kiya jaa sakta hai, ya undo bhi kiya jaa sakta hai.

4.  **State Pattern**

      * **Kaam:** Ek object ko apna behavior badalne ki anumati dena jab uski internal state badalti hai. Aisa lagta hai jaise object ne apni class hi badal li ho.
      * **Analogy:** Ek **ceiling fan ki switch**. Agar fan **Off** (state) hai, to switch dabane par **Low** (state) ho jaata hai. Agar **Low** hai, to **Medium** ho jaata hai. Action (switch dabana) same hai, par result state par depend karta hai.

5.  **Template Method Pattern**

      * **Kaam:** Ek algorithm ka basic structure (skeleton) ek base class mein define karna, par uske kuch steps ko subclasses ko override karne dena.
      * **Analogy:** **Chai banane ki recipe**. Basic steps (template) fix hain: 1. Paani ubalo, 2. Chai patti daalo, 3. Doodh daalo, 4. Cheeni daalo. `BlackTea` class step 3 aur 4 ko skip kar degi. `MasalaChai` class step 2 mein patti ke saath masala bhi daalegi. Main recipe wahi rehti hai, bas kuch steps badal jaate hain.
---

### ## Problem Statement Twitter System Design (Humein Banana Kya Hai?)

Kisi bhi system design ka pehla step requirements ko saaf-saaf samajhna hota hai.

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* **Post Tweet:** User 280 characters tak ka tweet publish kar sake, jismein text, image, ya video ho sakta hai.
* **Follow User:** User kisi doosre user ke content ko subscribe kar sake.
* **User Timeline:** User apne dwara post kiye gaye saare tweets ki ek list dekh sake.
* **Home Timeline:** User jin logon ko follow karta hai, un sabke tweets ki ek chronological feed dekh sake.
* **Search:** User tweets ya doosre users ko search kar sake.
* **Trending:** Platform trending topics ya hashtags ko pehchane aur dikhaye.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **High Availability:** Service 24/7 chalu aur uplabdh honi chahiye.
* **Low Latency:** Timelines bahut tezi se load honi chahiye (e.g., 200 milliseconds se kam mein).
* **Scalability:** System ko daily millions of active users aur billions of tweets handle karna hoga. Ek khaas baat ye hai ki system **read-heavy** hai. Timeline reads ki sankhya, tweet posts ki sankhya se kahin zyada hai (lagbhag 1000:1 ka ratio).
* **Durability:** Ek baar tweet post ho gaya, to woh kabhi khona (lost) nahi chahiye.
* **Eventual Consistency:** Ye a
    chha hai ki ek tweet ko sabhi followers ki timeline par aane mein kuch seconds lag jaayein. Timeline feature ke liye strong consistency zaroori nahi hai.

---

### ## Low Level Design (Data Models)

Architecture design karne se pehle, core data models ko define karna faydemand hota hai.

* **User Table:** User ki jaankari store karti hai.
    * `UserID` (Primary Key)
    * `Username`, `DisplayName`
    * `PasswordHash`, `Email`
    * `ProfileInfo`, `CreatedAt`
    * `FollowerCount`, `FollowingCount`
* **Tweet Table:** Sabhi tweets ka data store karti hai.
    * `TweetID` (Primary Key)
    * `AuthorID` (ForeignKey to User)
    * `Content` (Text, MediaURLs)
    * `Timestamp`
    * `LikeCount`, `RetweetCount`
* **Follows Table:** Social graph ko represent karti hai.
    * `FollowerID` (ForeignKey to User)
    * `FollowingID` (ForeignKey to User)
    * Ye table bas ye map karti hai ki kaun kisko follow karta hai.

---

### ## Architecture and Components (System Ka Naksha)

Twitter apne bade scale ko handle karne ke liye ek **microservices architecture** ka istemal karta hai. Client ki request sabse pehle ek load balancer par aati hai jo use ek **API Gateway** par bhejta hai. Gateway fir request ko sahi backend service ke paas bhej deta hai.

Do sabse zaroori workflows hain: tweet post karna (**write path**) aur timeline dekhna (**read path**).

#### Write Path (Tweet Post Karna)
1.  User ka client "post tweet" request API Gateway ko bhejta hai.
2.  Request ko **Tweet Posting Service** par bheja jaata hai.
3.  Ye service tweet ka data ek primary **Tweet Database** mein store karti hai (jo fast writes ke liye optimized hai).
4.  Fir, service ek message (jismein `TweetID` aur `AuthorID` hota hai) ko ek **Message Queue** (jaise Kafka) mein push kar deti hai.
5.  Is asynchronous approach se user ke liye write operation bahut fast ho jaata hai, aur use turant "OK" response mil jaata hai. Tweet ko distribute karne ka bhaari kaam background mein hota hai.

---

### ## User Timeline

* **Goal:** Ek single user ke saare tweets dikhana.
* **Solution:** Ye ek simple read operation hai. **Timeline Service** seedhe **Tweet Database** se un saare tweets ko query karti hai jahan `AuthorID` user ki ID se match karta hai, aur unhe timestamp ke hisaab se sort kar deti hai. `AuthorID` column par index laga kar isse bahut fast banaya jaa sakta hai.

---

### ## Home Timeline

Ye system ka sabse complex aur zaroori hissa hai. Goal hai ki user ko un sabhi logon ke tweets ki ek combined, sorted list dikhana jinhe woh follow karta hai.

#### The Challenge: Naive Approach Kyun Fail Hoga
Ek simple "pull" approach ye hoga ki pehle followed users ki list nikalo, fir har ek ke recent tweets nikalo, aur aakhir mein unhe merge karke sort karo. Agar ek user 1,000 logon ko follow karta hai, to ek timeline refresh ke liye hazaaron database queries lagengi, jo ki bahut slow hai aur scale nahi karega.

#### Optimized Solution: Pre-computed Timelines (Fanout on Write)
Twitter ek "push" model use karta hai jahan timeline pehle se hi compute karke cache mein store kar di jaati hai.

1.  **Fanout Service:** Kuch workers ka ek group lagatar **Message Queue** ko sunta rehta hai.
2.  Jab `Fanout Service` ko `User A` ke naye tweet ka message milta hai, to woh `User A` ke saare followers ko dhoondhta hai.
3.  Har follower ke liye, service naye `TweetID` ko ek data structure mein insert karti hai jo unki home timeline ko represent karta hai. Ye pre-computed timeline ek fast, in-memory distributed cache jaise **Redis** mein store hoti hai. Redis Lists ya Sorted Sets iske liye perfect hain.
4.  **Timeline Serve Karna:** Jab ek user apni home timeline request karta hai, to **Timeline Service** bas uski dedicated Redis list se `TweetID`s ki list fetch kar leti hai. Ye ek single, behad fast query hai. Fir service un IDs ke liye poora tweet data fetch karti hai (ise hydration kehte hain) aur client ko bhej deti hai.


#### The "Celebrity" Problem aur Hybrid Approach
Kya hoga jab 50 million followers wala user tweet karega? Tweet ko 50 million Redis lists mein fanout karna slow aur resource-intensive hai.

* **Solution:** Ek hybrid model istemal kiya jaata hai.
    * **Normal Users:** Kuch hazaar followers wale users ke liye, standard **push model** (fanout on write) istemal hota hai.
    * **Celebrities:** Millions of followers wale users ke tweets ko **fanout nahi kiya jaata**.
    * Jab kisi user ki home timeline generate ki jaati hai, to service Redis se uski pre-computed list (jismein normal users ke tweets hain) fetch karti hai **AUR** alag se un celebrities ke recent tweets ke liye direct query karti hai jinhe woh follow karta hai. In dono lists ko client ko bhejne se pehle read-time par merge kiya jaata hai.

---

### ## Trending Hashtags

1.  **Data Stream:** Jaise hi tweets create hote hain, unke hashtags nikaal kar ek real-time data stream (e.g., Kafka) mein push kiye jaate hain.
2.  **Stream Processor:** Ek stream processing engine jaise **Apache Spark** ya **Flink** is stream ko consume karta hai. Ye ek sliding time window (e.g., pichle 5 minute) mein hashtags ke counts ko jodta hai.
3.  **Analysis:** Processor algorithms ka istemal karke un hashtags ko dhoondhta hai jinki frequency ya badalne ki dar (rate of change) zyada hai.
4.  **Storage:** Top trending results ko quick access ke liye **Redis** jaise cache mein store kiya jaata hai.

---

### ## Searching

Is scale par text search karne ke liye standard database queries (`LIKE` ke saath) bahut slow hoti hain.

* **Solution:** Ek dedicated search index jaise **Elasticsearch** ka istemal karein.
    1.  Jab ek tweet create hota hai, to use ek **Search Service** ko bhi bheja jaata hai.
    2.  Ye service tweet ke text ko process karke use Elasticsearch cluster mein add karti hai, jo ek efficient inverted index banata hai.
    3.  Jab user search karta hai, to query Elasticsearch cluster ko hit karti hai, jo lagbhag turant relevant results lauta deta hai.

---

### ## Databases

Twitter "polyglot persistence" approach use karta hai, yaani alag-alag kaamon ke liye alag-alag database.
* **Tweet/User/Follows Data:** Ek distributed relational database jaise sharded **MySQL** ya **PostgreSQL** kaam kar sakta hai. **Cassandra** jaise NoSQL databases bhi unke high write throughput ke kaaran ek a
    chha fit hain.
* **Timeline Cache:** **Redis** is use case ke liye industry standard hai kyunki iski speed aur versatile data structures hain.
* **Search:** **Elasticsearch** apni powerful full-text search capabilities ke liye.
* **Media Storage:** Media files (images, videos) database mein store nahi hoti hain. Woh **Object Storage** service jaise **AWS S3** mein store hoti hain, aur sirf unka URL tweet data mein store hota hai. Ek **Content Delivery Network (CDN)** ka istemal is media ko duniya bhar ke users tak tezi se serve karne ke liye kiya jaata hai.

---

### ## Additional Interview Questions

* **Aap notification system kaise design karenge?**
    Ek Pub/Sub model ka istemal karein. Jab koi zaroori event hota hai (like, mention, follow), to ek message ek topic par publish kiya jaata hai. Ek **Notification Service** in topics ko subscribe karti hai, ek notification generate karti hai, aur use push notification services (Apple ke liye APNS, Google ke liye FCM) ke zariye user ko bhejti hai.
* **Aap "Like" button ko kaise handle karenge?**
    Ye ek aur high-write, high-read operation hai. Ek alag `Likes` table (`UserID`, `TweetID`) ki zaroorat hogi. Cassandra jaisa ek scalable NoSQL database upyukt hoga. Tweet object par `LikeCount` ko update kiya jayega, jismein caching aur eventual consistency ka istemal hoga.
* **Aapke timeline design mein mukhya trade-off kya hai?**
    Hybrid timeline approach bade paimane par scalability aur performance laabh paane ke liye application-level par kaafi complexity (read-time par lists ko merge karna) jodta hai. Ye efficiency ke liye simplicity ko qurbaan karta hai. Eventual consistency ka chunaav ek aur mahatvapurna trade-off hai jo turant, perfect consistency ke upar availability aur speed ko prathmikta deta hai.

---



# 📌 Netflix System Design

---

### ## What is Netflix?

Netflix ek subscription-based streaming service hai jo users ko internet-connected devices par movies, TV shows, documentaries, aur anya content dekhne ki anumati deta hai. Iski sabse badi khaasiyat iska vishaal content library aur high-quality, buffer-free streaming experience hai.

---

### ## Problem Statement (Humein Banana Kya Hai?)

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* **User Management:** Users sign up, log in, aur apne account ko manage kar sakein.
* **Browsing and Searching:** Users content library ko browse kar sakein aur specific movies ya shows ko search kar sakein.
* **Video Streaming:** Users content ko high-quality mein stream kar sakein.
* **Profiles:** Ek account ke andar multiple user profiles (e.g., Kids, Adults) bana sakein.
* **Viewing History:** System har user ki viewing history track kare.
* **Recommendations:** Users ko unke viewing history ke aadhar par personalized content suggest kare.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **High Availability:** Netflix hamesha "ON" rehna chahiye. Downtime bilkul bhi manzoor nahi hai.
* **Low Latency:** User jab play button par click kare, to video turant (e.g., 1-2 seconds mein) shuru ho jaana chahiye.
* **Scalability:** System ko vishvabhar mein (globally) millions of concurrent users ko handle karna hoga. Ye ek **READ-HEAVY** system hai, log content dekhte zyada hain, naya content upload kam hota hai.
* **Consistency:** Eventual consistency a
    chha hai. Agar aapki viewing history ko update hone mein kuch seconds lag jaayein, to koi problem nahi.

---

### ## Architecture and Components (System Ka Naksha)

Netflix poori tarah se **AWS (Amazon Web Services)** par chalta hai aur iska architecture **microservices** par aadharit hai.

**User Flow:**
1.  Jab aap Netflix app kholte hain, to request sabse pehle AWS ke **Load Balancer** par jaati hai.
2.  Wahan se request Netflix ke apne **API Gateway (Zuul)** par jaati hai, jo ek single entry point ki tarah kaam karta hai.
3.  Zuul request ko sahi microservice ke paas bhej deta hai. Kuch mukhya microservices hain:
    * **User Service:** Login, profile management, aur user ki saari jaankari handle karti hai.
    * **Recommendation Service:** Har user ke liye personalized suggestions generate karti hai.
    * **Metadata Service:** Movies/shows ki saari jaankari (title, cast, description) rakhti hai.
    * **Playback/Streaming Service:** Sabse zaroori service, jo actual video streaming ko handle karti hai. Ye decide karti hai ki user ko kaun se CDN se aur kaun si quality ki video file bhejni hai.



---

### ## Onboarding Content (Video Processing Pipeline)

Ye Netflix ka sabse complex backend process hai. Jab ek film studio Netflix ko ek movie deta hai, to use users tak pahunchane se pehle kai steps se guzarna padta hai.

* **Step 1: Upload (Ingestion):** Studio ek **single, high-quality master video file** (source file) ko Netflix ke secure AWS S3 bucket mein upload karta hai. Ye file kai terabytes ki ho sakti hai.

* **Step 2: Validation & QC:** File upload hone ke baad, ek process shuru hota hai jo check karta hai ki file corrupt to nahi hai, uska format sahi hai ya nahi, aur usmein koi visual/audio glitches to nahi hain.

* **Step 3: Transcoding (Sabse Zaroori Step):**
    * **Yeh Hai Kya?** Ye us ek master video file ko **hundreds of different files** mein convert karne ka process hai. Ye alag-alag files alag-alag **resolutions** (SD, HD, 4K) aur **formats** (mp4, mkv, etc.) mein hoti hain.
    * **Kyun Zaroori Hai?** Taaki Netflix har user ko uske device (mobile, laptop, 4K TV) aur internet speed ke hisaab se best possible video de sake. Ise **Adaptive Bitrate Streaming** kehte hain.
    * **Kaise Hota Hai?** Ye kaam parallel mein hota hai. Badi video file ko chote-chote chunks mein toda jaata hai, aur har chunk ko alag-alag formats mein convert karne ke liye hazaaron servers (AWS EC2 instances) ek saath kaam karte hain.

* **Step 4: Push to CDNs:** Jab saari video files taiyaar ho jaati hain, to unhe poori duniya mein faile hue **Content Delivery Networks (CDNs)** par push kar diya jaata hai. Netflix ka apna CDN hai jise **Open Connect** kehte hain. Ye video files ko physically users ke kareeb le jaata hai.

---

### ## Database Design

Netflix "polyglot persistence" ka istemal karta hai, yaani har kaam ke liye uske anusaar best database chuna jaata hai.

* **User/Profile Data:** Iske liye ek highly scalable NoSQL database jaise **Cassandra** ya **DynamoDB** istemal hota hai. Ye millions of users ka data aasaani se handle kar sakta hai.

* **Content Metadata:** Movies/shows ki jaankari (title, cast, genre) ke liye **Elasticsearch** (search ke liye) aur **Cassandra** (main data store ke liye) ka combination use hota hai.

* **Viewing History:** Har user kya dekh raha hai, kahan pause kar raha hai, ye data bahut vishaal hota hai. Iske liye ek column-family NoSQL database jaise **Cassandra** perfect hai.

* **Important Note:** **Video files kabhi bhi database mein store nahi hoti hain!** Woh hamesha **Object Storage (AWS S3)** mein store hoti hain aur **CDNs** ke through serve ki jaati hain.

---

### ## How Search Works and Data Processing

* **Search:**
    * Jab bhi koi naya show ya movie Netflix mein add hota hai, uski metadata (title, cast, description) ko **Elasticsearch** cluster mein index kiya jaata hai.
    * Jab aap search bar mein kuch type karte hain, to query seedhe is Elasticsearch cluster ko hit karti hai, jo behad tezi se relevant results lauta deta hai.

* **Data Processing (for Recommendations):**
    * Netflix apne users ka bahut saara data (viewing history, ratings, clicks, scroll time) collect karta hai.
    * Is vishaal data par **Apache Spark** jaise big data tools ka istemal karke Machine Learning models chalaye jaate hain.
    * Ye models har user ke liye personalized recommendations (e.g., "Top picks for you") calculate karte hain.
    * Ye pre-calculated results ek fast-access database ya cache mein store kiye jaate hain, taaki jab aap app kholen to recommendations turant load ho sakein.

---

### ## Additional Interview Questions

* **Aap "Top 10 in your country" feature kaise design karenge?**
    * Ye ek real-time analytics problem hai. Ek stream processor (jaise Flink/Spark) "video started" events ko consume karega. Ye har desh ke liye pichle 24 ghante mein unique views ko count karega. Top 10 list ko calculate karke har kuch minute mein **Redis** jaise cache mein daal dega, jahan se app use tezi se fetch kar sake.

* **Adaptive Bitrate Streaming kaise kaam karta hai?**
    * Video chote-chote chunks (kuch seconds ke) mein store hota hai. Netflix player (client side) user ki current internet speed ko detect karta hai. Agar speed a
        chhi hai, to woh CDN se high-quality (e.g., 1080p) chunk request karta hai. Agar speed kam ho jaati hai, to woh agla chunk low-quality (e.g., 480p) mein request karta hai. Isse video bina ruke (buffer hue) chalta rehta hai.

* **Aap piracy kaise rokenge?**
    * **DRM (Digital Rights Management)** technologies ka istemal karke. Video content ko encrypt kiya jaata hai, aur sirf authorized users aur devices ko hi use decrypt karne ki key di jaati hai.

---

### ## Additional Quips (Kuch Rochak Baatein)

* **Chaos Monkey:** Netflix ne ek tool banaya jise "Chaos Monkey" kehte hain. Ye unke live production system mein jaakar jaan boojhkar servers ko randomly band kar deta hai. Isse engineers hamesha aise systems banane ke liye taiyaar rehte hain jo failures ko aasaani se jhel sakein.
* **Cost of Data:** Netflix ka sabse bada kharcha content license par aur doosra sabse bada kharcha data transfer (AWS egress cost) aur CDN par hota hai. Unka poora business model is data ko efficiently manage karne par tika hai.
* **Trade-off:** Netflix video onboarding mein **bahut saara kaam pehle hi (upfront)** kar leta hai (transcoding, pushing to CDN). Ismein time aur paisa lagta hai, par iske badle user ko ek **behad fast aur smooth streaming experience** milta hai.

---


# 📌 Uber System Design

---

### ## Introduction (Parichay)

Uber ek ride-hailing service hai jo ek mobile app ke zariye **riders** (yatri) ko **drivers** ke saath jodti hai. Ye users ko on-demand transportation, food delivery (Uber Eats), aur anya services pradaan karti hai. Iska core business model riders aur drivers ko real-time mein efficiently match karna hai.

---

### ## Problem Statement (Humein Banana Kya Hai?)

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* **Ride Request:** Rider apni location se destination tak ke liye ride request kar sake.
* **Driver Accept:** Driver uss ride request ko accept ya reject kar sake.
* **Real-time Tracking:** Rider aur driver dono ek doosre ki location ko map par live track kar sakein.
* **Fare & ETA Calculation:** System ko ride ka anumanit kiraya (estimated fare) aur driver ke aane ka samay (ETA - Estimated Time of Arrival) calculate karna chahiye.
* **Payment:** Ride poori hone par payment automatically handle ho jaana chahiye.
* **User Profile & History:** User aur driver apne profiles aur purani trips ki history dekh sakein.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **High Availability:** Service hamesha, 24/7, uplabdh honi chahiye. Ek ride request kabhi fail nahi honi chahiye.
* **Low Latency:** Location updates aur driver-rider matching behad tezi se hone chahiye.
* **Scalability:** System ko vishvabhar mein millions of users (riders aur drivers) aur concurrent rides ko handle karna hoga.
* **Consistency:** Critical operations jaise ride book karna aur payment ke liye **strong consistency** zaroori hai. Lekin map par driver ki location thodi (1-2 seconds) purani dikhe to chalega, yaani yahan **eventual consistency** a
    chha hai.

---

### ## Architecture (System Ka Naksha)

Uber ek **microservices architecture** ka istemal karta hai taaki woh apne complex aur vishaal operations ko manage kar sake.

**High-Level Flow:**
1.  Rider aur Driver apps backend se communicate karte hain.
2.  Saari requests pehle ek **Load Balancer** par aati hain, jo traffic ko distribute karta hai.
3.  Wahan se request ek **API Gateway** par jaati hai jo use sahi microservice tak pahunchata hai.

**Mukhya Microservices:**
* **Rider Service:** Rider ke profile, payment methods, aur trip history ko manage karta hai.
* **Driver Service:** Driver ke profile, documents, ratings, aur current state (available, on-trip) ko manage karta hai.
* **Location Service:** Rider aur driver apps se lagatar aa rahi real-time GPS location data ko ingest aur process karta hai.
* **Dispatch Service (System Ka Dimaag):** Ye sabse zaroori service hai. Iska kaam hai ek rider ke liye sabse behtar, nazdeeki driver ko dhoondhna aur unhe match karna.
* **Trip Service:** Ek ride ki poori lifecycle (requested, accepted, started, ended, canceled) ko manage karta hai.
* **Billing/Payment Service:** Kiraya calculate karta hai aur payment gateways ke through transactions ko handle karta hai.

---

### ## Uber Challenges (Mukhya Chunautiyan)

1.  **Real-time Location Tracking:** Har second laakhon users se GPS data (pings) ko handle karna aur use process karna ek badi chunauti hai.
2.  **Driver-Rider Matching:** Ek rider ke liye sirf sabse nazdeeki driver nahi, balki sabse **behtar** driver (jo jaldi pahunche, jiski rating a
    chhi ho) ko dhoondhna ek complex optimization problem hai.
3.  **Scalability:** Demand achanak se bahut badh jaati hai (jaise rush hour mein, ya baarish ke samay). Is "spiky" traffic ko handle karne ke liye system ka elastic hona zaroori hai.

---

### ## Demystification of Uber System Design (Ride Ka Poora Flow)

Chaliye ek ride ke poore process ko shuru se ant tak dekhte hain:

1.  **Driver Online Aata Hai:** Driver app har 3-4 second mein apni GPS location **Location Service** ko bhejta hai. **Driver Service** driver ka status "available" update kar deti hai. Location Service is location ko ek geospatial database mein index kar leti hai.

2.  **Rider Ride Request Karta Hai:** Rider app rider ki location aur destination backend ko bhejta hai. Request **Trip Service** ke paas jaati hai jo ek nayi trip request banata hai.

3.  **Matching Ka Jaadu (Dispatch Service):**
    * Trip Service, **Dispatch Service** ko ek driver dhoondhne ke liye kehta hai.
    * Dispatch Service, **Location Service** se poochta hai ki rider ke 5 km ke daayre mein kitne "available" drivers hain. Ye ek **geospatial query** hai.
    * Dispatch Service fir ek algorithm chalakar un drivers mein se kuch sabse behtar drivers (kam ETA, a
        chhi rating) ko chunta hai aur unhe ride request bhejta hai.

4.  **Driver Accept Karta Hai:** Jo driver sabse pehle request accept karta hai, ride use assign ho jaati hai. **Trip Service** trip ka status "accepted" update karti hai. Dono (rider aur driver) ko notification jaata hai.

5.  **Ride Shuru Hoti Hai:** Trip ke dauraan, dono apps lagatar apni location **Location Service** ko bhejte rehte hain. Isse rider aur driver ek doosre ko map par live dekh paate hain.

6.  **Payment:** Ride poori hone par, **Trip Service**, **Payment Service** ko batata hai. Payment Service kiraya calculate karke user ke default payment method se charge kar leti hai.

---

### ## How Uber Map Works and ETA Calculation

* **Map Data:** Uber apne khud ke maps nahi banata. Woh map data ke liye **Google Maps**, **TomTom** jaise providers ya apne collect kiye hue data par nirbhar karta hai.

* **Location Tracking:**
    * GPS pings ke vishaal volume ko handle karne ke liye, Location Service ek high-throughput message queue jaise **Kafka** ka istemal karti hai.
    * Is location data ko ek **geospatial database** (jaise **PostGIS**) ya ek aise NoSQL DB mein store kiya jaata hai jo geospatial queries ko support karta ho. Ye databases **Quadtrees** ya **S2 geometry** jaise special indexes ka istemal karke "nazdeeki drivers dhoondho" jaisi queries ko behad fast bana dete hain.

* **ETA Calculation:**
    * Jab ek rider request karta hai, to Dispatch Service ko rider aur nazdeeki drivers ki location mil jaati hai.
    * Fir woh ek **Routing Service** ko call karta hai. Ye service map data aur real-time traffic ka istemal karke har driver ko rider tak pahunchne ka anumanit samay (ETA) calculate karti hai. Ye seedhi line ki doori nahi, balki asli sadkon par lagne wala samay hota hai.

---

### ## Interview Questions

* **Aap 'Surge Pricing' feature kaise design karenge?**
    * Ek particular geographical area (jaise Connaught Place) mein real-time mein supply (available drivers) aur demand (ride requests) ko analyze karenge. Agar demand, supply se bahut zyada ho jaati hai, to kiraye par ek multiplier laga denge. Iske liye real-time data aggregation ki zaroorat padegi.

* **Aap location service ke liye kis tarah ka database istemal karenge?**
    * Ek aisa database jiski geospatial indexing capabilities mazboot hon. Data ingest karne ke liye (write-heavy part), **Cassandra** jaisa database a
        chha hai. Data query karne ke liye (read-heavy part), **Elasticsearch** (geo-queries ke saath) ya **PostGIS** jaisa specialized DB behtar hai.

* **Aap kaise sunishchit karenge ki driver app se location data efficiently bheja jaaye?**
    * Sirf tabhi update bhejein jab location mein ahem badlav ho (e.g., > 50 meter).
    * Updates ko batch karke ek saath bhejein.
    * Chatty HTTP requests ke bajaye, **MQTT** ya **Protobuf over WebSockets** jaise efficient protocols ka istemal karein taaki network usage kam ho.

---




# 📌 Instagram System Design

---

### ## Introduction and Features (Parichay Aur Visheshtayein)

Instagram ek social media platform hai jo **photo aur video sharing** par kendrit hai. Iske mukhya features hain:
* **Photo/Video Upload:** Users media upload kar sakte hain, us par filters laga sakte hain, aur caption jod sakte hain.
* **Newsfeed:** Users jin logon ko follow karte hain, unka content ek scrollable feed mein dekhte hain.
* **Following:** Users ek doosre ko follow karke unke content ko subscribe karte hain.
* **Stories:** Short-lived (24-ghante) photos ya videos.
* **Likes & Comments:** Users doosre posts ke saath interact kar sakte hain.
* **Explore Page:** Users ko unke interests ke aadhar par naya content discover karne mein madad karta hai.

---

### ## Problem Statement: Requirements and Approximations

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* Users register aur login kar sakein.
* Users media (photo/video) upload kar sakein.
* Users doosre users ko follow kar sakein.
* Users ko ek chronological newsfeed dikhe.
* Users content ya doosre users ko search kar sakein.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **High Availability:** System hamesha on rehna chahiye.
* **Low Latency:** Newsfeed aur images behad tezi se load hone chahiye.
* **Durability:** Upload kiya gaya photo ya video kabhi bhi khona (lost) nahi chahiye. **100% durability** zaroori hai.
* **Scalability:** System ko hundreds of millions of users aur unke content ko handle karna hoga. Ye ek **READ-HEAVY** system hai (log content dekhte zyada hain, upload kam karte hain).
* **Eventual Consistency:** Agar ek naya post ya like aapke dost ko kuch seconds baad dikhe to chalega.

#### Approximations (Thoda Andaza Lagayein)
* **Daily Active Users (DAU):** Maan lijiye 500 million.
* **Uploads per user per day:** Maan lijiye har user average 0.1 photos/day upload karta hai.
    * Total uploads/day = 500M * 0.1 = 50 million uploads/day.
    * Write QPS = 50,000,000 / (24 * 3600s) ≈ **600 QPS**.
* **Feed views per user per day:** Maan lijiye har user 10 baar feed dekhta hai.
    * Total feed views/day = 500M * 10 = 5 billion views/day.
    * Read QPS = 5,000,000,000 / (24 * 3600s) ≈ **60,000 QPS**.
* **Nateeja:** Read QPS >> Write QPS. Hamara system reads ke liye highly optimized hona chahiye.
* **Storage:** Agar ek photo ka average size 2MB hai, to daily 50M * 2MB = **100 TB** naya data aayega. 5 saal mein ye **182.5 Petabytes** ho jaayega. Storage capacity vishaal honi chahiye.

---

### ## Low-Level Design (Data Models)

* **User Table:**
    * `UserID`, `Username`, `PasswordHash`, `ProfilePhotoURL`, `Bio`
* **Post Table:**
    * `PostID`, `UserID` (author), `MediaURL`, `Caption`, `Timestamp`, `LikeCount`
* **Follows Table:** Social graph ke liye.
    * `FollowerID`, `FollowingID` (Dono UserID hain)
* **Likes Table:**
    * `PostID`, `UserID` (Kisne kis post ko like kiya)

---

### ## Architecture and Components (System Ka Naksha)

Instagram ek **microservices architecture** par chalta hai.

#### Write Path (Photo Upload Karna)
Ye ek critical flow hai.
1.  User app se photo upload karta hai. Request **Load Balancer** se hote hue **API Gateway** tak jaati hai.
2.  Gateway request ko ek dedicated **Media Service** par bhejta hai.
3.  **Important:** Media Service photo ko apne server par save nahi karti. Woh use seedhe ek **Object Storage** jaise **AWS S3** ya Facebook ke apne **Haystack** par upload karti hai. Ye storage behad durable aur scalable hota hai.
4.  Jab photo S3 par successfully upload ho jaati hai, to S3 use ek URL lautaata hai.
5.  Media Service uss photo ka metadata (jaise `PostID`, `UserID`, `Caption`, aur S3 ka `MediaURL`) ek **Post Database** mein save karti hai.
6.  Aakhir mein, Media Service ek message (`newPost: {postID, userID}`) ek **Message Queue** (jaise Kafka ya RabbitMQ) mein daal deti hai. Ye message aage newsfeed generate karne ke kaam aayega. Is asynchronous process se user ko upload ka confirmation turant mil jaata hai.

#### Read Path (Photo Dekhna)
1.  Jab aap feed scroll karte hain, to app ko `MediaURL` milta hai.
2.  Ye URL S3 ka direct URL nahi hota. Ye ek **Content Delivery Network (CDN)** ka URL hota hai.
3.  Request CDN ke **edge server** (jo user ke sabse nazdeeki location par hota hai) par jaati hai.
4.  CDN image ko apne cache se turant serve kar deta hai, jisse image bahut tezi se load hoti hai. Agar image cache mein na ho, to CDN use S3 se fetch karke user ko deta hai aur future ke liye cache kar leta hai.

---

### ## Newsfeed Generation (Feed Kaise Banti Hai)

Ye Instagram ka sabse challenging part hai, bilkul Twitter ki tarah.
* **Problem:** Har baar feed dekhne par, aap jin 1000 logon ko follow karte hain un sabke posts database se laakar sort karna behad slow hoga.

* **Solution: Fan-out on Write (Push Model)**
    1.  Ek **Newsfeed Service** Message Queue ko sun rahi hoti hai.
    2.  Jaise hi use `User A` ke naye post ka message milta hai, woh `User A` ke saare followers ki list nikalta hai.
    3.  Har follower ke liye, Newsfeed Service us naye `PostID` ko us follower ki personal feed mein daal deti hai. Ye personal feed ek **Redis** jaise in-memory cache mein `List` ke roop mein store hoti hai. Redis mein har user ke liye uski `UserID` se ek feed-list mapped hoti hai.
    4.  **Feed Dekhna:** Jab koi user apni app kholta hai, to backend ko bas uski `UserID` ke corresponding Redis list se `PostID`s nikalne hote hain. Ye ek single, behad fast operation hai.
    5.  **Hydration:** `PostID`s ki list milne ke baad, un IDs ke corresponding poori post details (MediaURL, caption, user details) ko ek doosre cache ya database se laakar client ko bheja jaata hai.

* **"Celebrity" Problem & Hybrid Model:** Wahi Twitter wali problem. Agar 100 million followers wala user post karega to fan-out bahut mehenga hoga. Isliye, celebrities ke posts ko fan-out nahi kiya jaata. User ki feed banate samay, uski Redis list (normal users se) aur celebrities ke posts (direct query se) ko read-time par merge kiya jaata hai.

---

### ## Databases

* **User/Post Metadata:** Instagram famously **PostgreSQL** ko bahut zyada shard karke use karta hai. Is scale ke liye **Cassandra** jaisa NoSQL DB bhi ek a
    chha vikalp hai.
* **Social Graph (Follows):** Iske liye ek Graph Database (jaise Neo4j) aadarsh hai, par bade scale par ise ek simple Key-Value store (jaise **Redis** ya **DynamoDB**) se bhi model kiya jaa sakta hai (e.g., `Key: UserID`, `Value: List of FollowingIDs`).
* **Newsfeed Cache:** **Redis** is kaam ke liye best hai.
* **Media Storage:** **Object Storage** (AWS S3, Haystack).

---

### ## More Interview Problems

* **Aap Instagram Stories kaise design karenge?**
    * Stories 24 ghante ke liye hi rehti hain. Ise implement karne ka sabse aasan tareeka hai ki story ke metadata par **TTL (Time To Live)** set kar diya jaaye. **Redis** aur **Cassandra** jaise databases TTL feature out-of-the-box dete hain. 24 ghante baad data apne aap expire ho jaayega.

* **Aap 'Explore' page ya recommendation system kaise design karenge?**
    * Ye ek Machine Learning problem hai.
    * **Data Collection:** User ki activity (likes, saves, follows, search history) ko collect karein.
    * **Model Training:** Is data par **collaborative filtering** ("jin users ko aapki tarah cheezein pasand hain, unhe aur kya pasand aaya?") aur **content-based filtering** ("aapko kutte ki photos pasand hain, to ye rahi aur kutte ki photos") jaise algorithms chalayein.
    * **Serving:** Pre-computed recommendations ko Redis jaise cache mein store karein taaki explore page turant load ho.

* **Aap search/hashtags kaise handle karenge?**
    * Iske liye ek dedicated search index jaise **Elasticsearch** ka istemal karein. Jab bhi koi post upload hota hai, uske caption aur hashtags ko Elasticsearch cluster mein index kar dein. Search queries seedhe is cluster par jaayengi.
---

# 📌 BookMyShow System Design

---

### ## What is BookMyShow?

BookMyShow ek online ticketing platform hai jo users ko movies, events, concerts, plays, aur sports events ke liye ticket book karne ki suvidha deta hai. Iska sabse core feature hai ek specific show ke liye real-time mein seat select karke book karna.

---

### ## Problem Statement (Humein Banana Kya Hai?)

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* User sheher (city) ke hisaab se movies aur events browse kar sake.
* User ek theatre aur showtime chun sake.
* User theatre ka seating layout (kaun si seat kahan hai) dekh sake.
* User ek ya ek se zyada seats select kar sake.
* User chuni hui seats ko book kar sake (payment karke).
* System ko ek hi seat ke liye ek hi samay par aane wali multiple requests ko sahi dhang se handle karna chahiye (double booking nahi honi chahiye).

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **High Consistency:** Ye sabse zaroori requirement hai. Ek hi seat do alag-alag users ko kabhi bhi book nahi honi chahiye. Transactions **ACID compliant** hone chahiye.
* **High Availability:** System hamesha online rehna chahiye, khaas kar ke jab koi nayi, badi film release ho.
* **Low Latency:** Seat layout tezi se load hona chahiye aur booking ka process fast hona chahiye.
* **Scalability:** Jab kisi blockbuster movie ki ticket sale shuru ho, to achanak aane wale vishaal traffic ko handle karne ke liye system scalable hona chahiye.

---

### ## Low Level Design (Data Models)

* **City Table:** `CityID`, `Name`
* **Theatre Table:** `TheatreID`, `Name`, `CityID`
* **Screen Table:** `ScreenID`, `TheatreID`, `Capacity`
* **Movie Table:** `MovieID`, `Title`, `Description`
* **Show Table:** `ShowID`, `MovieID`, `ScreenID`, `StartTime`
* **Booking Table:** `BookingID`, `UserID`, `ShowID`, `Status` (PENDING, CONFIRMED, FAILED)
* **Show_Seats Table (Sabse Zaroori Table):** Ye table har show ke liye har seat ka status rakhti hai.
    * `ShowSeatID`, `ShowID`, `SeatNumber`, `Status` (AVAILABLE, LOCKED, BOOKED), `LockedUntil` (timestamp), `BookingID`

---

### ## Architecture and Components (System Ka Naksha)

BookMyShow ek **microservices architecture** ka istemal karega.

**Mukhya Microservices:**
* **Movie Service:** Movies, theatres, aur showtimes ki jaankari manage karta hai.
* **Booking Service:** Ye system ka dimaag hai. Ye ticket booking ke poore workflow ko handle karta hai.
* **Payment Service:** Payment gateways ke saath integrate karta hai.
* **Notification Service:** Booking confirmation (Email/SMS) bhejta hai.

#### The Booking Flow (Sabse Zaroori Hissa)
Ye flow concurrency ko handle karne ke liye banaya gaya hai:

1.  **Seat Selection:** User ek show select karke seat layout dekhta hai. Ye request **Movie Service** se handle ho sakti hai. User seats (e.g., D4, D5) chunta hai.

2.  **Seat Locking:** User "Pay" button par click karta hai. Request **Booking Service** ke paas jaati hai.

3.  **CRITICAL STEP (Transaction & Locking):**
    * Booking Service ek **database transaction** shuru karta hai.
    * Ye `Show_Seats` table mein un seats (`ShowID`='XYZ', `SeatNumber` in ['D4', 'D5']) ko check karta hai jinka status `AVAILABLE` hai.
    * SQL mein, iske liye `SELECT ... FOR UPDATE` query ka istemal hota hai. Ye query database ko batati hai ki in rows ko **lock** kar do, jab tak ye transaction poora na ho jaaye, koi aur isse chhed nahi sakta.
    * Agar seats available milti hain, to service unka status `AVAILABLE` se `LOCKED` mein update karti hai, ek `BookingID` assign karti hai, aur ek `LockedUntil` timestamp set karti hai (e.g., ab se 10 minute tak).
    * Agar seats pehle se `LOCKED` ya `BOOKED` hain, to transaction fail ho jaata hai aur user ko error dikhaya jaata hai.

4.  **Payment:** Agar seats successfully lock ho jaati hain, to user ko payment page par bheja jaata hai. User **Payment Service** ke through payment karta hai.

5.  **Confirmation:** Payment successful hone par, Payment Service, Booking Service ko notify karta hai. Booking Service database transaction ko **commit** karta hai aur seat ka status `LOCKED` se `BOOKED` mein badal deta hai.

6.  **Failure/Timeout:** Agar user 10 minute mein payment nahi karta ya payment fail ho jaati hai, to ek background job ya scheduler in "expired" locked seats ko dhoondhta hai aur unka status wapas `AVAILABLE` kar deta hai, taaki doosre log unhe book kar sakein.

---

### ## How to Sync Ticket Availability with Theatres?

Ye ek real-world chunauti hai kyunki theatres apni tickets offline (box office) bhi bechte hain.

* **Samasya:** BookMyShow ki inventory theatre ki asli inventory se hamesha sync mein rehni chahiye.
* **Samadhan: API Integration**
    1.  **Aggregator APIs:** Zyadatar cinema chains (PVR, INOX) ek third-party aggregator service ka istemal karte hain jo ek central API pradaan karti hai. BookMyShow har theatre se alag-alag baat karne ke bajaye, is central API se integrate karta hai.
    2.  **Real-time Communication:** Jab BookMyShow par ek user seat lock karne ki koshish karta hai (Step 3 mein), to hamari **Booking Service** pehle theatre ke system par ek real-time API call karke us seat ko wahan bhi lock karti hai. Ye ek **distributed transaction** ban jaata hai.
    3.  **Webhooks:** Jab theatre mein box office par koi ticket bikti hai, to unka system BookMyShow ke ek **webhook** (ek special API endpoint) ko call karke bata deta hai ki "ye seat ab bik gayi hai", jisse BookMyShow apni inventory turant update kar leta hai.

---

### ## Database Design

* **Database Ka Chunav:** Core booking system ke liye ek **Relational Database (jaise PostgreSQL ya MySQL)** hi sabse a
    chha vikalp hai. Iska kaaran hai ki data highly structured hai aur double-booking rokne ke liye **ACID transactions** ki sakht zaroorat hai.
* **Scalability:**
    * **Read Replicas:** Movie aur showtime browse karne jaisi read-heavy operations ke liye read replicas ka istemal karein taaki primary database par load kam ho.
    * **Sharding:** Database ko **City** ke aadhar par shard karein. Ek sheher ka saara data (theatres, shows, bookings) ek hi shard par rahega. Isse zyadatar transactions ek hi shard ke andar poore ho jaayenge aur cross-shard communication ki zaroorat kam padegi.

---

### ## Additional Interview Questions

* **Aap us race condition ko kaise handle karenge jahan do users ek hi millisecond par ek hi seat ke liye 'Book' click karte hain?**
    * Yahi core samasya hai jise database transactions aur row-level locking solve karte hain. `SELECT ... FOR UPDATE` query ye sunishchit karti hai ki jo bhi request database tak pehle pahunchi, sirf wahi us seat ki row par lock laga payegi. Doosri request ko intezaar karna padega, aur jab tak use mauka milega, pehli request seat ka status `LOCKED` kar chuki hogi.

* **Aap 'Offers/Discounts' feature kaise design karenge?**
    * Ek alag `Offers Service` banayenge. Jab user payment karne wala hoga, to Booking Service is service ko UserID, MovieID, payment type jaisi details bhejegi. Offers Service saare rules check karke applicable discount lauta degi, jise Payment Service final amount se ghata degi.

* **Agar aapki service seat lock kar de par theatre ki API call fail ho jaaye to kya hoga?**
    * Poora transaction **rollback** ho jaana chahiye. Aapke database mein lock ki gayi seat ko wapas `AVAILABLE` kar dena chahiye aur user ko ek saaf error message dikhana chahiye ("Sorry, we couldn't connect with the theatre. Please try again."). Ye distributed transactions ki complexity ko darshata hai.
---
# 📌 Zomato System Design

---

### ## What is Zomato?

Zomato ek multi-faceted platform hai jo mukhya roop se **food discovery aur delivery** par kendrit hai. Ye ek **three-sided marketplace** hai jo teen alag-alag tarah ke users ko jodta hai:
1.  **Users/Customers:** Jo khana dhoondhte aur order karte hain.
2.  **Restaurants:** Jo khana banakar bechte hain.
3.  **Delivery Partners:** Jo restaurants se khana uthakar users tak pahunchate hain.

---

### ## Problem Statement (Humein Banana Kya Hai?)

Humein ek aisa system design karna hai jo users ko nazdeeki restaurants se khana order karne, use real-time mein track karne, aur ek delivery partner dwara use deliver karwane ki suvidha de.

---

### ## Requirements (Zarooratein)

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* **Restaurant Search:** Users restaurants ko naam, cuisine, ya location ke aadhar par search kar sakein.
* **Menu & Cart:** Users restaurant ka menu dekh sakein aur items ko cart mein add kar sakein.
* **Order Placement & Payment:** Users order place kar sakein aur online payment kar sakein.
* **Order Management (Restaurant):** Restaurant order accept ya reject kar sake.
* **Partner Assignment:** Ek delivery partner ko order ke liye assign kiya jaana chahiye.
* **Live Tracking:** User, restaurant, aur delivery partner, teeno order ka status aur partner ki live location track kar sakein.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **High Availability:** System hamesha on rehna chahiye, khaas kar ke lunch aur dinner ke peak hours mein.
* **Low Latency:** Search results, order placement, aur location updates behad tezi se hone chahiye.
* **Reliability:** Orders, payments, aur notifications vishvasniya roop se process hone chahiye. Ek bhi order miss nahi hona chahiye.
* **Scalability:** System ko kai shehron mein peak hours ke dauraan aane wale high traffic ko handle karna hoga.

---

### ## Architecture and Components (System Ka Naksha)

Zomato jaise complex system ke liye ek **microservices architecture** anivarya hai.

**Mukhya Components:**
* **Clients:** Teen alag-alag apps - **User App**, **Restaurant App**, aur **Delivery Partner App**.
* **API Gateway:** Saare client apps se aane wali requests ke liye ek single entry point. Ye requests ko authenticate aur sahi service par route karta hai.
* **Backend Microservices:** Har service ka ek specific kaam hota hai.
* **Databases:** Har service ka apna alag database ho sakta hai (Polyglot Persistence).
* **Real-time Communication:** Live tracking ke liye WebSockets ya MQTT jaise protocols ka istemal.

---

### ## Services (Mukhya Microservices)

1.  **User Service:** User ke profile, addresses, aur payment details ko manage karta hai.
2.  **Restaurant Service:** Restaurant ki details, menu, operating hours, aur ratings ko manage karta hai.
3.  **Order Service (System Ka Dil):** Ye ek orchestrator ki tarah kaam karta hai. Ye ek order ki poori lifecycle ko (place hone se lekar deliver hone tak) manage karta hai.
4.  **Payment Service:** Payment gateways ke saath integrate karke saare transactions ko handle karta hai.
5.  **Delivery Partner Service:** Delivery partners ke profile, availability (online/offline), aur current location ko manage karta hai.
6.  **Dispatch Service (Matching Engine):** Iska kaam hai ek naye order ke liye sabse behtar (nazdeeki, available) delivery partner ko dhoondhna aur assign karna.
7.  **Live Tracking Service:** Delivery partners se aa rahi real-time location data ko ingest karta hai aur use user aur restaurant tak broadcast karta hai.
8.  **Notification Service:** Har order update par (e.g., "Order Accepted", "Food is on the way") push notifications, SMS, ya email bhejta hai.

---

### ## Database Schema (Data Models)

* **Users Table:** `UserID`, `Name`, `Phone`, `Email`, `Address`
* **Restaurants Table:** `RestaurantID`, `Name`, `Address`, `CuisineType`, `AvgRating`
* **MenuItems Table:** `ItemID`, `RestaurantID`, `ItemName`, `Price`, `IsAvailable`
* **Orders Table:** `OrderID`, `UserID`, `RestaurantID`, `PartnerID`, `TotalPrice`, `OrderStatus` (e.g., PLACED, ACCEPTED, PREPARING, PICKED_UP, DELIVERED), `OrderTimestamp`
* **DeliveryPartners Table:** `PartnerID`, `Name`, `Phone`, `CurrentLocation` (Geo-coordinate), `Status` (AVAILABLE, ON_DELIVERY)

---

### ## Working Flow (Ek Order Ka Poora Safar)

1.  **User Order Place Karta Hai:** User app se cart final karke "Place Order" par click karta hai. Request **Order Service** ke paas jaati hai. **Payment Service** payment process karti hai. Order Service ek naya order banata hai jiska `OrderStatus` hota hai `PLACED`.

2.  **Restaurant Ko Notification:** Order Service uss restaurant ke app par naye order ki detail bhejti hai. Restaurant ke paas order ko **accept** ya **reject** karne ke liye kuch minute hote hain.

3.  **Restaurant Order Accept Karta Hai:** Restaurant se confirmation aane par, Order Service `OrderStatus` ko `ACCEPTED` aur fir `PREPARING` mein badal deti hai. User ko "Your order has been accepted" ka notification jaata hai.

4.  **Delivery Partner Ki Talash (Dispatch Service):**
    * Ab Order Service, **Dispatch Service** ko ek partner dhoondhne ke liye kehti hai.
    * Dispatch Service, **Delivery Partner Service** se poochta hai ki restaurant ke nazdeek (e.g., 3km ke daayre mein) kitne partners `AVAILABLE` hain. Ye ek **geospatial query** hoti hai.
    * Ek algorithm ke zariye, sabse behtar partner (jo sabse paas ho, jiski rating a
        chhi ho) ko chuna jaata hai aur use delivery request bheji jaati hai.

5.  **Partner Delivery Accept Karta Hai:** Jo partner request accept karta hai, use order assign ho jaata hai. Order Service, `OrderID` ke saath `PartnerID` ko link kar deta hai aur restaurant aur user, dono ko notify karta hai ("A delivery partner has been assigned").

6.  **Live Tracking Shuru:**
    * Delivery partner ka app har kuch seconds mein apni GPS location **Live Tracking Service** ko bhejna shuru kar deta hai.
    * Live Tracking Service is location data ko **WebSockets** ke zariye user ke app aur restaurant ke app par **push** karti hai, jisse unhe map par live movement dikhti hai.

7.  **Pickup aur Delivery:** Partner restaurant se khana uthata hai (`OrderStatus` = `PICKED_UP`) aur customer tak pahunchata hai (`OrderStatus` = `DELIVERED`). Order Service in sabhi state changes ko manage karti hai aur har step par sabko notifications bhejti hai.

---

# 📌 Dropbox System Design

---

### ## What is Dropbox?

Dropbox ek **cloud storage** aur **file synchronization** service hai. Iska mool vichaar (core idea) hai ki user ke computer par ek "magic folder" hota hai. User is folder mein jo kuch bhi rakhta hai, woh apne aap cloud par upload ho jaata hai aur uske baaki saare devices (jaise phone, tablet, doosra computer) ke saath **sync** ho jaata hai.

---

### ## Problem Statement (Humein Banana Kya Hai?)

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* **File Upload/Download:** User Dropbox folder mein files ko upload aur download kar sake.
* **Synchronization:** Ek device par file mein kiya gaya koi bhi badlav (add, update, delete) baaki sabhi connected devices par apne aap reflect hona chahiye.
* **File Sharing:** User files ya folders ko doosre logon ke saath share kar sake.
* **Offline Editing:** User offline hone par bhi files ko edit kar sake. Jab user wapas online aaye, to saare changes sync ho jaane chahiye.
* **Version History:** System ko files ke purane versions ko track karna chahiye taaki user unhe restore kar sake.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **High Durability:** Files **KABHI BHI** khoni (lost) nahi chahiye. Ye sabse zaroori requirement hai. Data loss is not an option.
* **High Availability:** Service hamesha uplabdh honi chahiye.
* **Scalability:** System ko millions of users aur exabytes (1 exabyte = 1 million terabytes) of data ko support karna hoga.
* **Efficiency:** Bandwidth aur storage ka kushal (efficient) istemal karna. Agar file mein ek chota sa badlav ho, to poori file dobara upload nahi honi chahiye.

---

### ## Low Level Design (Data Models)

Yahan focus files ke data par nahi, balki uske **metadata** (jaankari) par hai.

* **User Table:** `UserID`, `Username`, `Email`, `StorageQuota`
* **Device Table:** `DeviceID`, `UserID`, `DeviceType`, `LastSyncTime`
* **FileMetadata Table:** `FileID`, `UserID` (owner), `FileName`, `FilePath`, `Size`, `ModifiedAt`
* **FileChunk Table:** `ChunkID` (chunk ka hash), `S3_ObjectKey` (actual data kahan hai), `Size`, `ReferenceCount` (deduplication ke liye)
* **FileVersion Table:** `FileID`, `VersionNumber`, `ListOfChunkIDs` (ordered list)

---

### ## Architecture and Components (System Ka Naksha)

Dropbox ka design do mukhya hisson mein toota hua hai: **Client** (aapke computer/phone par chalta hai) aur **Backend** (cloud servers).

### A. The Client (The Real Magic)

Dropbox ki asli jaadoogari uske client application mein hai.

1.  **Chunking (Tukdon Mein Todna):**
    * Client ek file ko ek poori cheez ki tarah nahi dekhta. Woh file ko chote-chote, fixed size ke blocks ya **chunks** mein tod deta hai (e.g., har chunk 4MB ka).

2.  **Hashing (Har Tukde Ko Pehchan Dena):**
    * Har chunk ke liye, client ek unique hash (jaise SHA-256) calculate karta hai. Ye hash us chunk ka ID ban jaata hai.

3.  **Watcher (Nigrani Rakhna):**
    * User ke computer par background mein ek process chalta hai jo lagatar Dropbox folder par **nazar** rakhta hai ki koi file add, modify, ya delete to nahi hui.

4.  **Indexer (Badlavon Ko Index Karna):**
    * Jab Watcher ko koi badlav milta hai, to Indexer kaam par lag jaata hai. Woh badli hui file ko dobara se chunks mein todta hai, unke naye hash nikalta hai, aur purane hashes se compare karta hai. Ye **sirf unhi chunks ko pehchanta hai jo asal mein badle hain**.

5.  **Synchronizer (Backend Se Baat Karna):**
    * Ye component backend se baat karta hai. Ye poori file dobara upload karne ke bajaye, **sirf naye ya badle hue chunks** ko hi upload karta hai. Yahi bandwidth bachane ka raaz hai.


### B. The Backend (Cloud Servers)

1.  **Load Balancer / API Gateway:** Saare client requests ke liye entry point.

2.  **Metadata Service & Database:**
    * Ye system ka dimaag hai. Ye saare metadata (users, files, chunks, versions) ko manage karta hai. Ise hi pata hota hai ki kis user ki kaun si file kaun-kaun se chunks se milkar bani hai.
    * Iske liye ek highly scalable, sharded database (Relational ya NoSQL) ka istemal hota hai.

3.  **Synchronization Service:**
    * Client ka Synchronizer is service se baat karta hai. Jab naye chunks upload hote hain, to ye service metadata database ko update karti hai ki "iss file ka version 2 ab in naye chunks se bana hai".

4.  **Block Storage (Files Ka Godown):**
    * Ye woh jagah hai jahan asal file chunks store hote hain. Ye ek vishaal **Object Storage** system (jaise **AWS S3**) hota hai.
    * Har chunk uske **hash ko key banakar** ek object ki tarah store kiya jaata hai.
    * **Deduplication:** Iska ek bada fayda hai. Agar aap aur aapka dost, dono ek hi file (e.g., ek movie) upload karte hain, to uske saare chunks ka hash same hoga. Dropbox us chunk ko sirf **ek hi baar** store karega aur dono users ke metadata mein bas uska reference daal dega. Isse bahut saari storage space bachti hai.

5.  **Notification Service (Changes Ki Soochna Dena):**
    * Ye system ka "push" hissa hai. Jab `User A` apne laptop par ek file badalta hai, to backend ko uske phone aur tablet ko batana padta hai ki "kuch badla hai, aakar download kar lo".
    * **Kaise Kaam Karta Hai?**
        * Sync Service, change process karne ke baad, Notification Service ko ek message bhejti hai.
        * Notification Service ne user ke baaki sabhi **online clients** ke saath ek lagatar connection (jaise **long polling** ya **WebSockets**) banakar rakha hota hai.
        * Ye unhe ek chota sa message bhejti hai: "Sync zaroori hai."
        * Phone aur tablet ke clients is message ko paakar, Synchronization Service se contact karte hain, badle hue chunks ki jaankari lete hain, aur unhe Block Storage se download kar lete hain.

---

# 📌 Pastebin System Design

---

### ## What is Pastebin?

Pastebin ek web service hai jo users ko plain text (jaise code snippets, notes, ya logs) store karne aur share karne ki anumati deti hai. User text paste karta hai, aur service uss text ke liye ek **unique URL** generate karti hai, jise woh doosre logon ke saath share kar sakta hai.

---

### ## Problem Statement (Humein Banana Kya Hai?)

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* User text ka ek block paste kar sake.
* System har paste ke liye ek unique aur chota URL generate kare.
* User paste ke liye ek optional custom URL set kar sake (e.g., `pastebin.com/my-config`).
* User paste ke liye ek optional expiration time (samapti samay) set kar sake (e.g., 10 minute, 1 din, 1 saal).
* Registered users apne purane pastes ki list dekh sakein.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **High Availability:** Service hamesha uplabdh honi chahiye.
* **Low Latency:** Text paste karna aur use URL se wapas prapt karna (retrieve) behad tezi se hona chahiye.
* **Durability:** Paste kiya gaya data expire hone tak kabhi khona (lost) nahi chahiye.
* **Scalability:** System ka core **write-heavy** hai, kyunki har naya paste ek write operation hai. Halaanki, kuch viral pastes **read-heavy** ho sakte hain.

---

### ## Low Level Design (Data Models)

* **Users Table:**
    * `UserID`, `Username`, `PasswordHash`, `Email`, `CreatedAt`

* **Pastes Table:** (Ye sabse zaroori table hai)
    * `PasteID` (PRIMARY KEY): Ye hamara unique short URL hoga (e.g., "aX8bZc1d").
    * `Content`: Asli text jo paste kiya gaya hai. Bade text ko handle karne ke liye `TEXT` ya `BLOB` data type.
    * `UserID` (ForeignKey): Anonymous pastes ke liye ye NULL ho sakta hai.
    * `ExpirationTimestamp`: Paste kab expire hoga, uska time. NULL agar kabhi expire na ho.
    * `CustomURL`: User dwara diya gaya custom URL. NULL agar nahi diya gaya. Is par ek UNIQUE constraint hona chahiye.
    * `CreatedAt`: Paste kab banaya gaya tha.

---

### ## Architecture and Components (System Ka Naksha)

System ke do mukhya workflows hain: naya paste banana (Write Path) aur ek paste ko dekhna (Read Path).



### A. The Write Path (Naya Paste Banana)

1.  **Request:** User browser se text submit karta hai. Request **Load Balancer** se hote hue ek **Application Server** tak pahunchti hai.

2.  **Unique URL Generation (Sabse Zaroori Step):**
    * Application Server ko ek unique, chota URL (key) banana hai.
    * **Approach 1 (Simple but slow):** Ek 6-8 character ka random string (e.g., `aX8bZc1d`) generate karo. Fir database mein check karo ki ye key pehle se exist to nahi karti. Agar karti hai (collision), to ek naya string generate karke fir se check karo. Ye har write par ek extra DB read maangta hai, jo slow hai.
    * **Approach 2 (Scalable):** Ek alag **URL Generation Service** banao.
        * Ye service pehle se hi laakhon-karodon unique keys generate karke ek alag database ya **Redis** jaise fast key-value store mein rakh leti hai.
        * Jab Application Server ko ek key chahiye hoti hai, to woh is service se bas ek key maang leta hai. Isse main write path par "check-if-exists" wala database call bach jaata hai.

3.  **Data Storage:**
    * Application Server is unique key (`PasteID`) aur user ke `Content` ko **Database** mein store kar deta hai.
    * Agar content bahut bada hai, to use database ke bajaye ek **Object Storage (jaise AWS S3)** mein store karna behtar hai aur database mein sirf uska pointer (S3 URL) rakhna chahiye.

4.  **Response:** Server user ko poora URL (e.g., `https://mypastebin.com/aX8bZc1d`) response mein bhej deta hai.

### B. The Read Path (Paste Dekhna)

1.  **Request:** User browser mein URL (`.../aX8bZc1d`) daalta hai. Request **Load Balancer** se hote hue **Application Server** tak pahunchti hai.

2.  **Caching (Performance Ke Liye Zaroori):**
    * Application Server, `PasteID` (`aX8bZc1d`) ko URL se nikalta hai.
    * Database mein jaane se pehle, woh ek **Distributed Cache (jaise Redis ya Memcached)** mein check karta hai ki kya is `PasteID` ka content pehle se cache mein hai ya nahi.
    * **Cache Hit:** Agar content cache mein mil jaata hai, to use wahin se turant user ko lauta diya jaata hai. Ye behad fast hota hai.
    * **Cache Miss:** Agar content cache mein nahi milta, tabhi server aage database ke paas jaata hai.

3.  **Database Query:**
    * Server `Pastes` table mein us `PasteID` ke corresponding content ko dhoondhta hai.

4.  **Populate Cache:**
    * Database se content milne ke baad, server use future requests ke liye **Cache mein daal deta hai**.

5.  **Response:** Server content ko user ke browser par dikha deta hai.

### C. Expiration (Purane Pastes Ko Hatana)

* Ek **background worker/script** (cron job) banani hogi jo niyamit roop se (e.g., har ghante) chale.
* Ye script `Pastes` table ko scan karegi aur un sabhi rows ko dhoondhegi jinka `ExpirationTimestamp` vartaman samay se purana ho chuka hai.
* Ye un expired rows ko database se **delete** kar degi taaki space free ho sake.

### Database Ka Chunav

* Is system ke liye ek **NoSQL Key-Value Database** jaise **Cassandra** ya **Amazon DynamoDB** ek behtareen vikalp hai.
* **Kyun?** Kyunki Zomato ka core use case ek key (`PasteID`) ke aadhar par ek value (`Content`) ko store karna aur retrieve karna hai. Cassandra aur DynamoDB high write throughput (jo hamari zaroorat hai) aur horizontal scaling ke liye banaye gaye hain.
* Ek **sharded SQL database** bhi kaam kar sakta hai, jise `PasteID` ke hash par shard kiya jaa sakta hai.

---


# 📌 Elevator System Design (OOD)

---

### ## What is Elevator? / Introduction

Ek elevator (ya lift) ek vertical transport vehicle hai jo ek building mein logon ya saaman ko alag-alag floors (manzilon) ke beech le jaati hai. Hamara kaam iske piche ke software control system ko design karna hai, jo in elevators ko efficiently manage karta hai.

---

### ## Problem Statement (Humein Banana Kya Hai?)

Humein ek multi-elevator, multi-floor building ke liye ek software control system design karna hai.

**Mukhya Zarooratein (Core Requirements):**
1.  Building mein 'N' elevators aur 'M' floors hain.
2.  Ek user kisi bhi floor se elevator bula sakta hai (Up ya Down button daba kar).
3.  Elevator ke andar, user apne destination floor ka button daba sakta hai.
4.  System ko efficiently passengers ko pick up aur drop karna chahiye, taaki unka **intezaar ka samay (wait time)** aur **safar ka samay (travel time)** kam se kam ho.

---

### ## Object Oriented Design (OOD)

OOD ka maqsad hai real-world cheezon ko software objects ke roop mein model karna. Chaliye iske steps follow karte hain:

### Step 1: Core Objects/Classes Ko Pehchanein

System ke mukhya "nouns" (sangyaayein) kya hain?
* **`Elevator`**: Asli lift car.
* **`ElevatorControlSystem`**: Poora system ka "dimaag", jo saare elevators ko manage karta hai.
* **`Floor`**: Building ki ek manzil.
* **`Button`**: Alag-alag tarah ke buttons (floor par aur lift ke andar).
* **`Request`**: User dwara ki gayi ek request.
* **`Building`**: Poora structure jismein sab kuch hai.



### Step 2: Har Class Ke Attributes Aur Methods Ko Define Karein

#### `Elevator` Class
Ye lift car ko represent karta hai.
* **Attributes (Gunn):**
    * `id`: Elevator ka unique ID.
    * `currentFloor`: Abhi lift kis floor par hai.
    * `direction`: Lift ki disha (UP, DOWN, IDLE).
    * `state`: Lift ki sthiti (MOVING, STOPPED, IDLE).
    * `door`: Darwaze ki sthiti (OPEN, CLOSED).
    * `requests`: Destination floors ki ek list jahan lift ko jaana hai.
* **Methods (Kaam):**
    * `move()`: Lift ko agle floor par le jaana.
    * `stop()`: Lift ko rokna.
    * `openDoor()`: Darwaza kholna.
    * `closeDoor()`: Darwaza band karna.
    * `addDestination(floorNumber)`: Andar se dabaye gaye button ki request add karna.

#### `ElevatorControlSystem` Class (The Brain)
Ye sabse zaroori class hai.
* **Attributes:**
    * `elevators`: Building ke saare `Elevator` objects ki ek list.
    * `pickupRequests`: Bahar se (floors se) aayi hui requests ki ek queue.
* **Methods:**
    * `requestElevator(floor, direction)`: Jab koi bahar se button dabata hai, to ye method call hota hai.
    * `findBestElevator(floor, direction)`: Ek nayi request ke liye sabse behtar lift dhoondhne wala algorithm.
    * `step()`: Ek master method jo lagatar chalta hai aur poore system ki state ko aage badhata hai (har lift ko ek step aage badhana).

#### `Button` Class
* **Attributes:**
    * `isPressed`: Button daba hua hai ya nahi.
* **Methods:**
    * `press()`: Button ko dabana.
    * (Ise aage `FloorButton` aur `ElevatorButton` mein inherit kiya jaa sakta hai).

#### `Floor` Class
* **Attributes:**
    * `floorNumber`: Manzil ka number.
    * `upButton`, `downButton`: Uss floor par lage buttons.

### Step 3: Classes Ke Beech Rishte Banayein

* Ek **`Building`** ke paas kai **`Floors`** aur ek **`ElevatorControlSystem`** hota hai (**Composition**).
* **`ElevatorControlSystem`** kai **`Elevators`** ko manage karta hai (**Aggregation/Composition**).
* Ek **`Floor`** ke paas **`Button`** hote hain. Ek **`Elevator`** ke paas bhi **`Button`** hote hain.
* User **`Floor`** par lage **`Button`** ko dabata hai, jo **`ElevatorControlSystem`** ko ek request bhejta hai.
* **`ElevatorControlSystem`** us request ko sabse behtar **`Elevator`** ko assign karta hai.

### Step 4: Core Logic (Algorithm) Ko Design Karein

#### Ek Request Ko Kaise Handle Karein?
1.  Ek user `Floor 5` par `UP` button dabata hai.
2.  `Floor 5` ka `upButton` object `ElevatorControlSystem` ko notify karta hai.
3.  `ElevatorControlSystem` ke paas ek nayi pickup request aati hai: `{floor: 5, direction: UP}`.
4.  Ab `ElevatorControlSystem` ka scheduling algorithm, `findBestElevator()`, kaam par lag jaata hai.

#### Elevator Scheduling Algorithm
System ka maqsad hai sabse jaldi service dena. To, `findBestElevator()` kya check karega?

1.  **Sabse Nazdeeki IDLE Lift:** Kya koi lift khaali khadi hai? Agar haan, to sabse nazdeeki waali ko bhej do.
2.  **Request Ki Taraf Aa Rahi Lift:** Ek aisi lift jo pehle se hi request ki disha mein (UP) chal rahi hai aur abhi request wale floor (5) se neeche hai (e.g., floor 2 par). Ye ek a
    chha candidate hai kyunki ye raaste mein hi user ko pick kar sakti hai.
3.  **Request Se Aage Nikal Chuki Lift:** Ek aisi lift jo request ki disha mein (UP) hi chal rahi hai par request wale floor (5) ko paar kar chuki hai (e.g., floor 7 par). Ye ek bura candidate hai, par jab ye apna upar ka kaam poora karke neeche aayegi, tab is request ko poora kar sakti hai.

Algorithm har lift ke liye ek "cost" (kitna time lagega) calculate karta hai aur sabse kam cost wali lift ko request assign kar deta hai.

#### Ek Elevator Kaise Chalta Hai? (SCAN Algorithm)
* Har lift apni destination requests ki ek list maintain karti hai.
* Woh ek disha mein (e.g., UP) chalti rehti hai aur raaste mein aane wale saare requested floors par rukti hai.
* Jab woh apne upar ke sabse aakhri destination par pahunch jaati hai, to woh apni disha badal leti hai (DOWN) aur neeche aate hue baaki requests ko poora karti hai.
* Isse bewajah upar-neeche jaana kam ho jaata hai aur efficiency badh jaati hai.
---




# 📌 WhatsApp Messenger System Design

---

### ## What is WhatsApp?

WhatsApp ek free, cross-platform instant messaging (IM) service hai. Yeh users ko internet ke zariye text messages, voice messages, images, videos, documents bhejne aur voice/video calls karne ki anumati deta hai. Iski sabse badi khaasiyat iski simplicity aur end-to-end encryption hai.

---

### ## Problem Statement (Humein Banana Kya Hai?)

Humein ek scalable messaging system design karna hai jo billions of users ke liye 1-on-1 aur group chats ko support kar sake.

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* User 1-on-1 (personal) chat kar sake.
* User group chat kar sake (kai logon ke saath).
* Message ke status dikhne chahiye: Sent (✓), Delivered (✓✓), Read (blue ✓✓).
* User ka online status ya "last seen" timestamp dikhna chahiye.
* Media files (photos, videos, documents) share karne ki suvidha honi chahiye.
* End-to-end encryption honi chahiye (halanki hum isko high-level par hi discuss karenge).

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **High Availability:** Service hamesha on rehni chahiye, 24/7.
* **Low Latency:** Messages turant (real-time mein) deliver honi chahiye.
* **Durability:** Bheja gaya message network failure ya kisi aur dikkat ke bawajood kabhi khona (lost) nahi chahiye.
* **Scalability:** System ko achanak badhne wale users aur messages ke load ko aasani se handle karna aana chahiye.
* **Efficiency:** Battery aur data ka istemal kam se kam hona chahiye, khaaskar mobile devices par.

---

### ## Low Level Design (Data Models)

* **Users Table:**
    * `UserID` (PRIMARY KEY)
    * `PhoneNumber` (UNIQUE): User ko identify karne ka mukhya zariya.
    * `Username`
    * `ProfilePictureURL`: Profile photo ka link (Object storage mein stored).
    * `StatusText`
    * `LastSeenTimestamp`: User kab aakhri baar online tha.
    * `CreatedAt`

* **Chats Table:**
    * `ChatID` (PRIMARY KEY): Har 1-on-1 ya group chat ke liye ek unique ID.
    * `IsGroupChat` (Boolean): Yeh batane ke liye ki chat group hai ya personal.
    * `GroupName` (NULL for 1-on-1 chats)
    * `GroupIconURL`
    * `CreatedAt`

* **User_Chats_Mapping Table:** (Many-to-Many relationship ke liye)
    * `UserID` (ForeignKey)
    * `ChatID` (ForeignKey)

* **Messages Table:** (Ye sabse zaroori aur write-heavy table hai)
    * `MessageID` (PRIMARY KEY): Har message ke liye ek unique ID.
    * `ChatID` (ForeignKey): Message kis chat ka hissa hai.
    * `SenderID` (ForeignKey): Message kisne bheja hai.
    * `Content`: Asli text message. Encrypted hoga.
    * `MessageType`: (e.g., TEXT, IMAGE, VIDEO, DOC).
    * `MediaURL`: Agar media hai, to uska link (Object Storage, jaise S3 mein).
    * `Timestamp`: Message kab bheja gaya tha.

---

### ## Architecture and Components (System Ka Naksha)

WhatsApp ek normal web service jaisa nahi hai jo sirf HTTP request/response par chale. Real-time chat ke liye, client (mobile app) aur server ke beech ek **persistent (lagatar) connection** zaroori hai. Iske liye **WebSockets** ka istemal kiya jaata hai.

### A. Core Connection Management

1.  **Client Se Connection:** Jab user WhatsApp open karta hai, to app ek **WebSocket connection** hamare **Chat Server** ke saath banata hai. Yeh connection tab tak active rehta hai jab tak app background mein chalta rehta hai.
2.  **Session Management:** Kaun sa user kis Chat Server se connected hai, iski information ek fast **Key-Value Store (jaise Redis)** mein rakhi jaati hai.
    * *Mapping:* `UserID` -> `ChatServer_IP`
    * Isse ek server doosre server ko aasani se message bhej sakta hai.

### B. The Message Sending Path (1-on-1 Chat)

Sochiye, User A, User B ko message bhej raha hai.

1.  **Request:** User A apne phone par message type karke 'Send' dabata hai. Message uske phone se uske designated **Chat Server (Server 1)** tak WebSocket connection ke zariye jaata hai.

2.  **Server Ka Kaam:**
    * **Store Message:** Server 1 message ko turant **Database** mein store karta hai. Yeh **Durability** sunishchit karta hai. Message ab safe hai.
    * **Find Receiver:** Server 1, Redis se poochta hai, "User B kis server se connected hai?".

3.  **Deliver Message (2 Scenarios):**
    * **Case 1: User B is Online:** Redis batata hai ki User B, **Chat Server 2** se connected hai. Server 1 message ko Server 2 ko bhej deta hai. Server 2 us message ko User B ke phone par unke WebSocket connection ke zariye turant bhej deta hai.
    * **Case 2: User B is Offline:** Redis batata hai ki User B ka koi active connection nahi hai. Is case mein, Server 1 ek **Push Notification Service** (jaise Google's FCM ya Apple's APNS) ko bolta hai ki User B ko ek notification bheje ("You have a new message"). Jab User B app kholega, to app server se saare pending messages sync kar lega.

4.  **Acknowledgment (✓, ✓✓, Blue ✓✓):**
    * **Sent (✓):** Jaise hi Server 1 ko User A se message milta hai aur woh use DB mein store kar leta hai, woh User A ko ek `ACK` (acknowledgment) bhejta hai. User A ko **ek tick** dikhta hai.
    * **Delivered (✓✓):** Jab User B ka phone message receive kar leta hai, to woh apne server (Server 2) ko `ACK` bhejta hai. Server 2 is `ACK` ko Server 1 tak pahunchata hai, aur Server 1 ise User A ko bhejta hai. User A ko **do ticks** dikhte hain.
    * **Read (Blue ✓✓):** Jab User B, User A ka chat window kholta hai, to uska app ek `MessageRead` event server ko bhejta hai. Ye event aakhir mein User A tak pahunchta hai, aur use **blue ticks** dikhte hain.

### C. Media Sharing (Photos/Videos)

Bade files ko WebSocket par bhejna aklmandi nahi hai. Iske liye ek alag flow hai:
1.  User A ek photo select karta hai.
2.  App pehle us photo ko direct ek **Object Storage (jaise AWS S3)** par upload karta hai.
3.  Upload hone ke baad, S3 ek unique URL deta hai.
4.  Ab User A ka app us URL ko ek normal text message ki tarah User B ko bhejta hai (upar bataye gaye message flow ke zariye).
5.  User B ke phone par jab yeh URL wala message aata hai, to uska app us URL se photo ko download karke display kar deta hai.

### Database Ka Chunav

* Is system ke liye ek **NoSQL Database** jaise **Cassandra** ya **DynamoDB** behtareen hai.
* **Kyun?**
    * **Massive Write Load:** Har second laakhon-karodon messages likhe ja rahe hain. Cassandra high write throughput ke liye design kiya gaya hai.
    * **Scalability:** Users badhne par hum aasani se aur server add kar sakte hain (Horizontal Scaling).
    * **Data Model:** Hamara primary query pattern hai: "Ek `ChatID` ke saare messages de do". Ye key-value type query NoSQL databases mein behad fast hoti hai.

---
# 📌 Facebook Messenger System Design

---

### ## What is Facebook Messenger?

Facebook Messenger (ya Messenger) Meta ka ek instant messaging platform hai jo Facebook ke social graph se juda hua hai. WhatsApp ke विपरीत, jahan aapki pehchaan aapka phone number hota hai, Messenger mein aapki pehchaan aapka Facebook account hota hai. Ye users ko apne Facebook friends aur doosre logon ke saath chat karne, media share karne, aur voice/video calls karne ki suvidha deta hai. Yeh ek standalone app ke roop mein aur Facebook website ke andar bhi kaam karta hai.

---

### ## Problem Statement (Humein Banana Kya Hai?)

Humein ek messaging system design karna hai jo Facebook ke astitv (existing) social graph par kaam kare aur users ko multiple devices (web, mobile) par ek seamless (nirbaadh) chat anubhav pradaan kare.

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* User apne Facebook friends ke saath 1-on-1 chat kar sake.
* User kai logon ke saath group chat bana sake.
* Message ke status dikhne chahiye: Sent, Delivered, Seen (dekha gaya).
* User ka "Active Now" status dikhna chahiye.
* Media files (photos, videos, GIFs, stickers) share karne ki suvidha honi chahiye.
* **Sabse Zaroori:** Chat history sabhi devices (e.g., phone, laptop, tablet) par poori tarah se sync honi chahiye. Ek device par bheja ya padha gaya message doosre device par bhi waisa hi dikhna chahiye.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **High Availability:** Service hamesha upalbdh honi chahiye.
* **Low Latency:** Real-time mein messages ki delivery honi chahiye.
* **Consistency:** User ka data sabhi devices par consistent (ek samaan) hona chahiye. Ye behad zaroori hai.
* **Scalability:** System ko Facebook ke arabon (billions) users ke message load ko handle karne ke liye scalable hona chahiye.
* **Durability:** Ek baar bheja gaya message kabhi khona nahi chahiye.

---

### ## Low Level Design (Data Models)

Ye WhatsApp jaisa hi hai, lekin yahan user ki pehchaan Facebook `UserID` se hoti hai.

* **Users Table:** (Ye Facebook ka main user table ho sakta hai)
    * `UserID` (PRIMARY KEY)
    * `Username`
    * `ProfilePictureURL`
    * `LastActiveTimestamp`: User kab aakhri baar active tha.

* **Threads Table:** (Har chat (1-on-1 ya group) ko ek "thread" ya "conversation" kaha jaa sakta hai)
    * `ThreadID` (PRIMARY KEY)
    * `IsGroupThread` (Boolean)
    * `ThreadName`, `ThreadIconURL` (Groups ke liye)
    * `LastMessageTimestamp`: Is thread mein aakhri message kab aaya tha (chats ko sort karne ke liye).

* **User_Threads_Mapping Table:** (Many-to-Many relationship ke liye)
    * `UserID` (ForeignKey)
    * `ThreadID` (ForeignKey)

* **Messages Table:** (Sabse active table)
    * `MessageID` (PRIMARY KEY): Har message ke liye ek unique ID.
    * `ThreadID` (ForeignKey): Message kis conversation ka hissa hai.
    * `SenderID` (ForeignKey): Message kisne bheja.
    * `Content`: Asli text message (encrypted).
    * `MessageType`: (TEXT, IMAGE, STICKER, etc.).
    * `MediaURL`: Agar media hai to uska S3/Object Storage link.
    * `Timestamp`

* **Seen_Status Table:** (Track karne ke liye kisne kab tak message dekha hai)
    * `ThreadID`
    * `UserID`
    * `LastSeenMessageID`: Is user ne is thread mein kaunsa aakhri message dekha hai.

---

### ## Architecture and Components (System Ka Naksha)

Messenger ka core bhi **WebSockets** par chalta hai taaki real-time communication ho sake. Mukhya chunauti (challenge) multiple devices ko sync mein rakhna hai.

### A. Core Connection Management (Multi-Device Support)

Ek user ek hi samay mein apne phone aur laptop dono par online ho sakta hai. Iska matlab hai ki ek `UserID` ke liye **multiple WebSocket connections** ho sakte hain.

1.  **Multiple Connections:** Jab user apne phone se login karta hai, to ek WebSocket connection banta hai. Jab woh apne laptop par Facebook kholta hai, to ek aur WebSocket connection banta hai.
2.  **Session Management (Redis):** Hamara session store ab thoda complex hoga. Humein har user ke saare active connections ko store karna hoga.
    * *Mapping:* `UserID` -> `[ {deviceId: 'phone123', server: 'Server1_IP'}, {deviceId: 'laptop456', server: 'Server2_IP'} ]`
    * Isse pata chalta hai ki ek user ke kaun-kaun se device kis-kis server se jude hain.

### B. The Message Sending Path (Syncing is Key)

Sochiye, User A apne **laptop** se User B ko message bhej raha hai.

1.  **Request:** User A ke laptop se message WebSocket ke zariye uske connected **Chat Server (Server 1)** tak jaata hai.

2.  **Server Ka Kaam:**
    * **Store Message:** Server 1 message ko **Database** mein store karta hai. (Durability)
    * **Sync Sender's Other Devices:** Server 1, Redis se User A ke doosre active devices ki list nikalta hai (e.g., uska phone, jo Server 3 se connected hai). Server 1, Server 3 ko message bhejta hai taaki User A ke phone par bhi "sent" message dikh jaaye. **Yeh seamless sync ka pehla kadam hai.**
    * **Find Receiver:** Server 1, Redis se User B ke saare active devices ki list nikalta hai. Maan lijiye User B ka phone Server 4 par aur tablet Server 5 par active hai.

3.  **Deliver Message to Receiver:**
    * Server 1 message ko **Server 4** aur **Server 5** dono ko bhej deta hai.
    * Server 4 use User B ke phone par bhejta hai.
    * Server 5 use User B ke tablet par bhejta hai.
    * Agar User B ka koi device offline hai, to uss device ke liye ek **Push Notification** bhej di jaati hai.

### C. Handling "Seen" Status

Ye status bhi sabhi devices par sync hona chahiye.

1.  User B apne **phone** par message padhta hai. Uska phone `MessageSeen` event **Server 4** ko bhejta hai.
2.  Server 4, `Seen_Status` table mein update karta hai ki User B ne is thread mein yahan tak padh liya hai.
3.  Ab is information ko sab jagah sync karna hai:
    * Server 4 is "seen" update ko **User A ke sabhi active devices** tak bhejta hai (via Server 1 & 2), taaki User A ko "Seen" dikh jaaye.
    * Server 4 is update ko **User B ke doosre active devices** (jaise tablet, via Server 5) tak bhi bhejta hai, taaki wahan par message "unread" na dikhe.

### Database Ka Chunav

* **NoSQL (Cassandra/DynamoDB):** WhatsApp ki tarah hi, Messenger ka data bhi NoSQL ke liye ek perfect fit hai. Write load bahut zyada hai, data model simple (key-value jaisa) hai, aur horizontal scaling ki sakht zaroorat hai. Facebook ne apne messaging platform ke liye shuru mein HBase aur baad mein custom solutions ka istemal kiya, jo NoSQL ke hi principles par aadhaarit hain.

---
# 📌 Gmail System Design

---

### ## What is Gmail?

Gmail (ya Google Mail) Google dwara di jaane wali ek free email service hai. Jab ise 2004 mein launch kiya gaya tha, to isne 1 GB storage dekar email industry mein kranti la di thi, jo uss samay anokha tha. Gmail apni shaktishali (powerful) search capabilities, conversation view (ek hi subject waale emails ko ek saath group karna), aur behad prabhavi (effective) spam filtering ke liye jaana jaata hai. Yeh ek web-based platform hai, lekin saath hi IMAP aur POP3 jaise standard email protocols ko bhi support karta hai.

---

### ## Problem Statement (Humein Banana Kya Hai?)

Humein ek atyant vishwasniya (highly reliable), scalable, aur tezi se search karne wala email system design karna hai jo arabon users aur unke petabytes (1 PB = 1000 TB) data ko sambhal sake.

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* User email bhej sake (To, CC, BCC ke saath).
* User email prapt (receive) kar sake.
* User apne emails ki list dekh sake (Inbox, Sent, Drafts, Spam, etc.).
* **Sabse Zaroori:** User apne saare emails (jo saalon purane ho sakte hain) mein se kuch bhi **bahut tezi se search** kar sake.
* User emails ko manage kar sake (delete, archive, label lagana, spam mark karna).
* Attachments (files) bhejne aur receive karne ki suvidha honi chahiye.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **Durability (Ati-Vishwasniyata):** Ek user ka email khona (lost) bilkul bhi swikar nahi kiya jaa sakta. Data ko kai jagah replicate aur backup karna anivarya hai. Yeh system ki sabse badi zaroorat hai.
* **High Availability:** Email service hamesha upalbdh honi chahiye. Downtime na ke barabar hona chahiye.
* **Low Latency (for UI and Search):** Email delivery mein thodi deri ho sakti hai, lekin user ka inbox load karna ya search results dikhana secondon mein hona chahiye.
* **Scalability:** System ko users aur unke data ki badhti sankhya ke saath aasaani se scale hona chahiye.

---

### ## Low Level Design (Data Models)

Gmail ke scale par, ek single `Emails` table mein sab kuch store karna asambhav hai. Humein data ko uske upyog ke aadhar par alag-alag store karna hoga. Ek email jo 10 logon ko bheja jaata hai, use 10 baar store nahi kiya jaata; use ek baar store karke, 10 jagah reference kiya jaata hai.

* **Users Table:**
    * `UserID`, `EmailAddress` (PRIMARY KEY), `PasswordHash`, `StorageQuota`, `CreatedAt`

* **Emails Table (The Core Content):**
    * `EmailID` (PRIMARY KEY): Har unique email ke liye.
    * `Subject`, `Body`: Email ka asli content.
    * `FromAddress`
    * `Timestamp`
    * *Note:* Is table mein `To` ya `CC` ki list nahi hoti. Yeh sirf email ka raw content store karta hai.

* **Email_Recipients Table:**
    * `EmailID` (ForeignKey): Kaunsa email.
    * `RecipientAddress`: Kisko bheja gaya.
    * `RecipientType`: (TO, CC, BCC).

* **User_Mailbox Table (The Index):** *Yeh sabse zaroori table hai.* Yeh har user ka "view" represent karta hai. Ismein email ka content nahi hota, sirf metadata aur pointers hote hain.
    * `UserID` (Indexed)
    * `EmailID` (ForeignKey)
    * `MailboxFolder`: (INBOX, SENT, DRAFTS, SPAM, TRASH).
    * `IsRead` (Boolean)
    * `Labels`: (e.g., ['work', 'important']). Array ya ek alag mapping table ho sakta hai.
    * Jab aap apna inbox kholte hain, to system isi table se query karke aapko emails ki list dikhata hai.

* **Attachments Table:**
    * `AttachmentID` (PRIMARY KEY)
    * `EmailID` (ForeignKey)
    * `FileName`, `FileSize`, `FileType`
    * `StorageURL`: File kahan store hai, uska pointer (e.g., Google Cloud Storage ka link).

---

### ## Architecture and Components (System Ka Naksha)

Gmail ka architecture kai alag-alag, specialized microservices se bana hai.

### A. The Email Receiving Path (Email Kaise Aata Hai)

1.  **SMTP Servers:** Jab koi aapko email bhejta hai, to woh pehle Gmail ke **SMTP Servers** par aata hai. Ye internet se email receive karne ke liye standard entry point hain.

2.  **Processing Pipeline & Queue:** SMTP server email ko ek **Message Queue** (jaise Pub/Sub ya Kafka) mein daal deta hai. Isse aage ka process asynchronous (background mein) ho jaata hai.

3.  **Spam Filtering Service:** Ek worker is email ko queue se uthata hai aur sabse pehle use ek advanced **ML-based Spam Filter** se guzarta hai.

4.  **Data Storage:**
    * **Content Store:** Agar email spam nahi hai, to uske `Body` aur `Subject` ko ek bade **NoSQL Database / Object Store (jaise Google Bigtable)** mein store kiya jaata hai aur ek unique `EmailID` generate hota hai. Attachments ko **Google Cloud Storage (GCS)** jaise object storage mein daala jaata hai.
    * **Metadata Store:** Ab, har recipient ke liye, `User_Mailbox` table (jo ek sharded SQL ya Spanner jaise distributed database mein hai) mein ek entry banayi jaati hai. Jaise, `(UserID: 'userB', EmailID: 'email123', MailboxFolder: 'INBOX', IsRead: false)`.

5.  **Indexing for Search:** Isi dauran, email ka content (subject, body, sender) ek **Asynchronous Worker** ko bheja jaata hai, jo use **Search Index** mein daal deta hai.

6.  **Notification:** User ko ek push notification bheji jaati hai ki "You have a new email".

### B. The Search Magic (Search Itna Tez Kaise Hai?)

Gmail har baar search karne par aapke saare emails ko scan nahi karta. Woh Google Search ki tarah hi ek **Inverted Index** ka istemal karta hai.

* **Inverted Index Kya Hai?** Yeh ek data structure hai jo aam index ka ulta hota hai.
    * *Normal Index:* `EmailID` -> `[word1, word2, word3]`
    * *Inverted Index:* `word` -> `[EmailID1, EmailID5, EmailID99]` (ye word kin-kin emails mein hai)

* **Kaise Kaam Karta Hai?**
    1.  Jab ek naya email aata hai, to background workers uske saare shabdon (words) ko nikaal kar is Inverted Index ko update kar dete hain.
    2.  Jab aap "yearly report" search karte hain, to system 'yearly' ke aage likhi `EmailID` list aur 'report' ke aage likhi `EmailID` list ko uthata hai.
    3.  Fir woh dono lists ka **intersection** (common IDs) nikalta hai. Result aapko turant mil jaata hai.
    4.  Yeh poora Search Index itna bada hota hai ki use `UserID` ke aadhar par kai hazaar servers mein **shard (baant)** kar rakha jaata hai. Har user ke paas ek tarah se uska apna chota Google Search engine hota hai.

### C. The Email Sending Path

Yeh receiving path ka ulta hai.
1.  Aap browser mein 'Send' click karte hain. Request **Web Server** par jaati hai.
2.  System content ko **Content Store** mein save karta hai, `EmailID` generate karta hai.
3.  Aapke `User_Mailbox` mein 'SENT' folder ke liye ek entry banata hai.
4.  Agar recipient bhi Gmail user hai, to uske `User_Mailbox` mein 'INBOX' ke liye ek entry banata hai.
5.  Agar recipient bahar ka hai (e.g., @yahoo.com), to email ko ek **outbound SMTP server** ko de diya jaata hai, jo use internet par aage bhej deta hai.

---


# 📌 Chess.com System Design

---

### ## What is Chess.com?

Chess.com ek online chess platform hai jo duniya bhar ke chess khiladiyon ko aapas mein jodata hai. Yeh sirf chess khelne ka ek madhyam nahi hai, balki ek poora community platform hai. Users yahan live chess khel sakte hain (alag-alag time controls ke saath jaise blitz, rapid, classical), daily puzzles solve kar sakte hain, lessons se seekh sakte hain, aur bade tournaments mein hissa le sakte hain ya unhe live dekh sakte hain.

---

### ## Problem Statement (Humein Banana Kya Hai?)

Humein ek scalable online platform design karna hai jahan laakhon users ek saath (concurrently) live chess games khel sakein. System ko efficiently players ko match karna, game state ko manage karna, aur game ke baad analysis pradaan karna chahiye.

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* User doosre user ke khilaaf ek live chess game khel sake.
* System ko user ke skill level (rating) ke aadhar par ek uchit pratidvandi (opponent) se **match** karna chahiye.
* System ko chess ke niyamon ke anusaar har move ko **validate** karna chahiye (illegal moves ko rokna).
* Har game ke liye player ke time clocks ko manage karna chahiye.
* Game ke result (jeet, haar, draw) ko record karna aur uske aadhar par players ki rating ko update karna.
* Users apni pichli (past) games ko review aur analyze kar sakein.
* Users doosre logon ke (khaaskar top players ke) live games dekh sakein.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **Low Latency (Behad Zaroori):** Ek player dwara ki gayi move doosre player ke screen par turant (milliseconds mein) dikhni chahiye. Blitz jaise fast games mein delay bilkul bhi swikar nahi kiya jaa sakta.
* **High Availability:** Platform hamesha khelne ke liye uplabdh hona chahiye.
* **Stateful Service:** Har chal rahe game ka state (board position, kiska turn hai, clock time) server par maintain karna anivarya hai. Yeh ek stateless web app se bilkul alag hai.
* **Scalability:** System ko ek saath chal rahe laakhon games ko handle karne ke liye scalable hona chahiye.
* **Fair Play:** Cheating (engine ka istemal) ko rokne ke liye mechanisms hone chahiye (halanki yeh ek advanced feature hai).

---

### ## Low Level Design (Data Models)

* **Users Table:**
    * `UserID` (PRIMARY KEY)
    * `Username`, `PasswordHash`, `Email`
    * `RatingBlitz`, `RatingRapid`, `RatingClassical`: Alag-alag time formats ke liye alag ELO ratings.
    * `Country`, `JoinedAt`

* **Games Table (Completed Games):**
    * `GameID` (PRIMARY KEY)
    * `WhitePlayerID` (ForeignKey to Users)
    * `BlackPlayerID` (ForeignKey to Users)
    * `Result`: (e.g., '1-0' for white win, '0-1' for black win, '1/2-1/2' for draw).
    * `EndReason`: (e.g., 'Checkmate', 'Timeout', 'Resignation').
    * `GamePGN`: Poore game ki moves ko Portable Game Notation (PGN) format mein store karna. Yeh text-based hota hai aur bahut efficient hai.
    * `EndTime`, `TimeFormat`

* **Live Game State (In-Memory Store, e.g., Redis):**
    Active games ko SQL database mein baar-baar update karna bahut slow hoga. Iske liye Redis jaise in-memory database ka istemal hota hai.
    * **Key:** `GameID`
    * **Value:** Ek JSON object ya Hash jismein saari live information ho:
        * `BoardState`: FEN (Forsyth–Edwards Notation) string mein board ki current position.
        * `WhoseTurn`: ('white' or 'black').
        * `WhitePlayerID`, `BlackPlayerID`
        * `WhiteTimeLeft`, `BlackTimeLeft` (milliseconds mein).
        * `LastMoveTimestamp`

---

### ## Architecture and Components (System Ka Naksha)

Is system ka core real-time aur stateful hai. Iske liye **WebSockets** technology anivarya hai.

### A. The Matchmaking Flow (Game Shuru Kaise Hota Hai)

1.  **Request:** User "Play 5 min Blitz" par click karta hai. Request **API Gateway** se hote hue ek stateless **Web Server** tak jaati hai.
2.  **Queue:** Web Server user ki request (`UserID`, `Rating`, `TimeFormat`) ko ek **Matchmaking Service** ko bhejta hai. Yeh service user ko ek **Queue** mein daal deti hai, jo rating aur time format ke aadhar par alag-alag hoti hai. Yeh queues **Redis** mein manage ki jaa sakti hain.
3.  **Pairing:** Matchmaking Service lagatar in queues ko scan karti hai aur do compatible players (jinki rating lagbhag samaan ho) ko dhoondhti hai.
4.  **Game Server Assignment:** Jaise hi ek match milta hai (User A vs User B), Matchmaking Service ek available **Game Server** (jo stateful hai aur jiske paas capacity hai) ko chunti hai.
5.  **Connection Info:** Matchmaking Service dono players (User A aur B) ke clients ko us chune gaye Game Server ka address (`IP:Port`) aur ek unique `GameID` bhejti hai.

### B. The Gameplay Flow (Asli Khel)

1.  **WebSocket Connection:** Dono players ke client (browser/app) ab us specific **Game Server** ke saath ek **persistent WebSocket connection** banate hain. Ab saara communication isi connection par hoga.
2.  **Game Initialization:** Game Server us `GameID` ke liye ek naya game instance apni memory mein (ya Redis mein) banata hai, jismein shuruaati board position (FEN), clocks, aur player info hoti hai.
3.  **Move Execution:**
    * User A (White) ek move chalta hai (e.g., `e2e4`). Yeh move data WebSocket ke zariye Game Server ko bheja jaata hai.
    * **Server Validation:** Game Server check karta hai ki kya yeh move chess ke niyamon ke anusaar **legal** hai, kya yeh User A ka hi turn hai, etc.
    * **State Update:** Agar move legal hai, to server game ke state ko update karta hai: FEN string badalta hai, User A ke clock se time kam karta hai, aur turn User B ko de deta hai.
    * **Broadcast:** Game Server is nayi state (move `e2e4`, naye clock times) ko WebSocket ke zariye **dono players** ko bhejta hai. User B ke client ko move screen par dikhta hai.
4.  Yeh **Move -> Validate -> Update -> Broadcast** ka loop tab tak chalta rehta hai jab tak game khatm na ho jaaye.

### C. The Post-Game Flow (Game Khatm Hone Ke Baad)

1.  **Game Over:** Game Server game ke khatm hone ki sthiti (checkmate, timeout, resignation) ko detect karta hai. Woh dono clients ko "Game Over" ka final message bhejta hai. Ab WebSocket connection band ho sakta hai.
2.  **Asynchronous Processing:** Game Server, game ka poora data (final PGN, result, players) ko ek **Message Queue** (like RabbitMQ/SQS) mein daal deta hai.
3.  **Background Worker:** Ek **worker** is message ko queue se uthata hai aur do kaam karta hai:
    * Poore game ko permanent storage ke liye main **SQL Database** (`Games` table) mein save karta hai.
    * Ek **Rating Service** ko call karke dono players ki ELO rating ko `Users` table mein update karta hai.
    * Yeh sab background mein hota hai taaki Game Server turant agle game ko handle karne ke liye free ho jaaye.
---
# 📌 IRCTC System Design

---

### ## What is IRCTC?

IRCTC (Indian Railway Catering and Tourism Corporation) Indian Railways ki ek sahayak company hai jo online ticket booking, catering, aur tourism services pradaan karti hai. Iski website, `irctc.co.in`, duniya ki sabse zyada transaction waali websites mein se ek hai. Iski sabse badi chunauti hai ek seemit inventory (train ki seats) ke liye laakhon-karodon concurrent requests ko handle karna, khaaskar **Tatkal booking** ke samay jab traffic achanak se hazaar guna badh jaata hai.

---

### ## Problem Statement (Humein Banana Kya Hai?)

Humein ek atyant vishwasniya (highly reliable) aur scalable online ticket booking platform design karna hai jo Indian Railways ke vishaal network ke liye kaam kare. System ko race conditions (ek hi seat ke liye do logon ki booking) ko rokna aur transactions ki dridhta (integrity) sunishchit karni chahiye.

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* User do stations ke beech, ek vishisht (specific) taarikh par trains khoj (search) sake.
* System ko trains ki list, unki timing, seat ki uplabdhta (availability), aur kiraya (fare) dikhana chahiye.
* User ek ya ek se adhik yaatriyon (passengers) ke liye ticket book kar sake.
* System ko alag-alag quotas (General, Tatkal, Ladies, Premium Tatkal) ko handle karna chahiye.
* User book kiye gaye ticket ko cancel kar sake, jiske baad refund process ho.
* System ko vibhinn (various) payment gateways ke maadhyam se payment process karna chahiye.
* User apni purani aur aane waali bookings ka itihas (history) dekh sake.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **High Consistency (Sabse Zaroori):** Yeh system ki sabse mukhya zaroorat hai. Ek seat galti se bhi do alag logon ko book nahi honi chahiye. Sabhi booking transactions **ACID compliant** (Atomicity, Consistency, Isolation, Durability) hone chahiye.
* **High Availability:** System, khaaskar peak hours (Tatkal time) mein, hamesha uplabdh hona chahiye.
* **Scalability:** System ko Tatkal aur tyohaaron (festivals) ke samay aane waale achanak traffic spikes ko handle karne ke liye design kiya jaana chahiye.
* **Fault Tolerance:** Payment failure ya server crash jaisi sthiti mein data inconsistent nahi hona chahiye (paisa kat gaya par ticket nahi mila). System ko aisi sthitiyon se gracefully recover karna chahiye.
* **Low Latency (for Search):** Train search ka anubhav bahut tez hona chahiye. Booking process thoda dheema ho sakta hai kyunki usmein complex transactions hote hain.

---

### ## Low Level Design (Data Models)

Is system ke liye ek **Relational Database (SQL)** jaise PostgreSQL ya Oracle anivarya hai kyunki humein strong transactional support (ACID) chahiye.

* **Users Table:** `UserID`, `Username`, `PasswordHash`, `FullName`, `Age`, `Gender`, `MobileNumber`.
* **Trains Table:** `TrainID` (PK), `TrainNumber`, `TrainName`, `SourceStationID`, `DestinationStationID`.
* **Stations Table:** `StationID` (PK), `StationName`, `StationCode`.
* **Train_Schedule Table:** `TrainID`, `StationID`, `ArrivalTime`, `DepartureTime`, `Distance`, `StopNumber`.
* **Availability Table (The Core Inventory):** Har train, har din, har class, har route segment ke liye available seats ka count store karna.
    * `TrainID`, `Class` (Sleeper, 3A, etc.), `Quota` (General, Tatkal), `TravelDate`
    * `SourceStationID`, `DestinationStationID`
    * `AvailableSeatsCount`
    * *Note:* Yahi table hai jo sabse zyada read aur write jhelegi.
* **Bookings Table (PNR Info):**
    * `PNR` (PRIMARY KEY)
    * `UserID`, `TrainID`, `TravelDate`
    * `SourceStationID`, `DestinationStationID`
    * `BookingStatus` (CONFIRMED, WAITING, CANCELLED)
    * `TotalFare`, `TransactionID`
* **Passengers Table:**
    * `PNR` (ForeignKey)
    * `PassengerName`, `Age`, `Gender`
    * `SeatNumber`, `CoachNumber`, `BerthType` (Upper, Lower, etc.)
    * `BookingStatus` (CONFIRMED, WAITING)

---

### ## Architecture and Components (System Ka Naksha)

IRCTC ke architecture ka mukhya siddhant (principle) hai **read-heavy search traffic** ko **write-heavy booking traffic** se alag karna.

### A. The Train Search Flow (Read-Intensive)

1.  **Request:** User Source, Destination aur Date enter karta hai. Request **Load Balancer** se hote hue **Web Servers** tak jaati hai.
2.  **Dedicated Search Service:** Request ek alag **Search Service** ko bheji jaati hai. Yeh service sirf train khojne ke liye optimized hai.
3.  **Caching:** Search Service sabse pehle **Distributed Cache (jaise Redis)** mein check karti hai ki kya is query (e.g., `Prayagraj -> Delhi, 13-Sep-2025`) ka result pehle se मौजूद hai. Agar haan, to wahin se result bhej diya jaata hai.
4.  **Read-Replica DB:** Agar cache mein nahi milta, to Search Service database ke **Read Replica** (main database ki ek copy jo sirf read operations ke liye hoti hai) se query karti hai. Yeh `Train_Schedule` aur `Availability` tables se data nikal kar user ko dikha deti hai. Isse main database par load nahi padta.

### B. The Ticket Booking Flow (Write-Intensive & Transactional)

Yeh sabse critical hissa hai aur ismein **race conditions** ko rokna zaroori hai.

1.  **Request:** User "Book Now" par click karta hai. Request ek alag **Booking Service** ko jaati hai.
2.  **Transaction & Locking (Sabse Zaroori Kadam):**
    * Booking Service ek **DATABASE TRANSACTION** shuru karti hai.
    * Yeh `Availability` table mein check karti hai ki seats hain ya nahi.
    * Agar seats hain, to yeh **`AvailableSeatsCount` ko ghatati hai** aur un seats par ek **temporary lock** laga deti hai. Yeh lock ek alag `Seat_Locks` table mein entry daalkar ya row ko `LOCKED` state mein mark karke kiya jaa sakta hai. Is lock ka ek expiry time hota hai (e.g., 10 minutes).
    * Is lock ke kaaran, usi samay koi doosra user unhi seats ko book nahi kar sakta.
3.  **Payment:** User ko payment page par bheja jaata hai. Woh apni details daalkar payment karta hai. Request **Payment Gateway Service** ke zariye bank tak jaati hai.
4.  **Transaction Outcome:**
    * **Case 1: Payment Successful:** Payment Gateway success ka response bhejta hai. Booking Service database transaction ko **COMMIT** kar deti hai. Lock ek permanent booking mein badal jaata hai, PNR generate hota hai, aur `Bookings`/`Passengers` tables mein data daal diya jaata hai. User ko confirmation dikha diya jaata hai. Ek confirmation message **Message Queue (jaise Kafka)** mein daal diya jaata hai taaki background worker user ko SMS/Email bhej sake.
    * **Case 2: Payment Failed ya Timeout:** Agar user 10 minute mein payment nahi kar paata ya payment fail ho jaata hai, to Booking Service database transaction ko **ROLLBACK** kar deti hai. Temporary lock hatt jaata hai, aur `AvailableSeatsCount` wapas badha diya jaata hai. Woh seats ab doosre users ke liye available ho jaati hain.

---
# 📌 UPI System Design

---

### ## What is UPI?

UPI (Unified Payments Interface) ek instant real-time payment system hai jise National Payments Corporation of India (NPCI) ne develop kiya hai. Yeh ek "system" ya "platform" hai, na ki ek wallet ya bank account. Yeh alag-alag banks ko ek single mobile application ke zariye aapas mein jodata hai, jisse users turant paisa bhej aur prapt kar sakte hain.

Iska jaadu iske VPA (Virtual Payment Address) jaise `naam@okbank` mein hai, jo users ko apni bank account details (account number, IFSC) share kiye bina transactions karne ki anumati deta hai. Apps jaise Google Pay, PhonePe, Paytm, etc., isi UPI platform par bane Third-Party App Providers (TPAPs) hain.

---

### ## Problem Statement (Humein Banana Kya Hai?)

Humein ek aisi interoperable (jo alag-alag systems ke saath kaam kar sake), surakshit (secure), aur atyant vishwasniya (highly reliable) payment network design karna hai jo 24/7 kaam kare aur secondon mein inter-bank fund transfers ko poora kar sake.

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* User apne mobile number ke zariye apne bank account ko link kar sake.
* User apne liye ek unique VPA (Virtual Payment Address) bana sake.
* User doosre VPA, Account Number, ya QR code par paisa bhej sake (Push Payment).
* User doosre VPA se paisa anurodh (request) kar sake (Pull Payment).
* Har transaction ko ek surakshit UPI PIN se authenticate karna anivarya hai.
* User apne linked account ka balance check kar sake.
* Transaction history dekhne ki suvidha honi chahiye.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **Security (Sarvoch Prathmikta - Highest Priority):** End-to-end encryption, secure PIN handling, aur financial regulations (jaise PCI DSS) ka paalan karna anivarya hai. Data leak ya fraud ki gunjaish nahi honi chahiye.
* **Reliability & Atomicity:** Transactions atomic hone chahiye. Ya to paisa poori tarah se transfer ho (sender se debit, receiver ko credit), ya transaction poori tarah se fail ho (aur paisa roll back ho). "Paisa beech mein fans gaya" wali sthiti nahi honi chahiye.
* **Low Latency:** Ek transaction shuru se ant tak kuch hi secondon mein poora ho jaana chahiye.
* **High Availability:** System 24/7/365, bina kisi downtime ke, kaam karna chahiye.
* **High Scalability:** System ko pratidin (per day) arabon (billions) transactions ko handle karne ke liye scalable hona chahiye.

---

### ## Low Level Design (Data Models / API Payloads)

Kyunki UPI ek single application nahi, balki ek network hai, isliye hum database tables ke bajaye system ke beech ghoomne waale data objects (API Payloads) par dhyaan denge.

* **User/Account Object:**
    * `UserID`, `MobileNumber`, `DeviceID`
    * `LinkedBankAccounts`: [ { `AccountNumber`, `IFSC`, `BankName`, `VPA` } ]

* **Transaction Object (The Core Data Packet):**
    * `TransactionID`: Har transaction ke liye ek unique ID (TPAP dwara generate).
    * `PayerVPA`: Bhejne waale ka VPA.
    * `PayeeVPA`: Paane waale ka VPA.
    * `Amount`: Kitna paisa.
    * `Timestamp`: Kab shuru hua.
    * `TransactionType`: (P2P, P2M).
    * `Status`: (INITIATED, PENDING, SUCCESS, FAILED).
    * `Remarks`: Transaction ka vivaran (description).
    * `EncryptedPINBlock`: User dwara daala gaya PIN, jo device par encrypt kiya gaya ho.

---

### ## Architecture and Components (System Ka Naksha)

UPI ka architecture distributed hai, jismein kai alag-alag kirdaar (players) ek saath kaam karte hain.

#### The Key Players (Mukhya Kirdaar)
1.  **TPAP (Third-Party App Provider):** Yeh aapka app hai (Google Pay, PhonePe). Yeh sirf User Interface (UI) pradaan karta hai.
2.  **PSP (Payment Service Provider) Bank:** Yeh woh bank hai jo TPAP ko UPI infrastructure pradaan karta hai (e.g., `@okhdfcbank` handle HDFC Bank ka PSP hai).
3.  **NPCI UPI Switch:** Yeh poore system ka "dimaag" ya "router" hai. Yeh sabhi PSPs ko aapas mein jodta hai.
4.  **Remitter Bank (Payer's Bank):** Paisa bhejne waale ka bank.
5.  **Beneficiary Bank (Receiver's Bank):** Paisa paane waale ka bank.

### The Transaction Flow (Paisa Bhejne Ka Pura Safar)

Chaliye ek transaction ko trace karte hain: **User A (Google Pay, SBI account)**, **User B (PhonePe, ICICI account)** ko ₹100 bhej raha hai.

1.  **Initiation (TPAP App):**
    * User A, Google Pay mein User B ka VPA (`userb@okicici`) aur ₹100 daalta hai.
    * App UPI PIN maangta hai. User A apna 4 ya 6 digit ka PIN daalta hai.
    * Google Pay app transaction details aur PIN ko **encrypt** karta hai aur ise apne **PSP Bank** (maan lijiye HDFC Bank) ke server ko bhejta hai.

2.  **Request to NPCI (PSP Bank):**
    * HDFC Bank ka server is request ko receive karta hai, uski jaanch karta hai, aur use aage **NPCI UPI Switch** ko bhej deta hai.

3.  **Routing (NPCI):**
    * NPCI poore network ka central router hai.
    * Yeh Payer ke VPA (`usera@oksbi`) ko dekhta hai aur pata lagata hai ki Remitter Bank **SBI** hai.
    * NPCI ab SBI ke server ko ek "debit request" bhejta hai.

4.  **Debit from Remitter Bank:**
    * SBI ka server is debit request ko receive karta hai.
    * Woh **PIN ko verify karta hai**, check karta hai ki User A ke account mein **sufficient balance** hai ya nahi.
    * Sab theek hone par, SBI User A ke account se ₹100 **debit** kar deta hai aur NPCI ko "debit successful" ka response bhejta hai.

5.  **Credit to Beneficiary Bank (via NPCI):**
    * Jaise hi NPCI ko debit success ka confirmation milta hai, woh Payee ke VPA (`userb@okicici`) ko dekhta hai aur pata lagata hai ki Beneficiary Bank **ICICI** hai.
    * NPCI ab ICICI ke server ko ek "credit request" bhejta hai.

6.  **Credit Confirmation:**
    * ICICI ka server is credit request ko receive karta hai aur User B ke account mein ₹100 **credit** kar deta hai.
    * ICICI, NPCI ko "credit successful" ka response bhejta hai.

7.  **Final Confirmation (The Reverse Path):**
    * NPCI ab jaanta hai ki transaction poori tarah se safal ho gaya hai.
    * Yeh success message Payer ke PSP (HDFC Bank) ko bhejta hai.
    * HDFC Bank is message ko User A ke Google Pay app ko bhejta hai, aur User A ko screen par "Payment Successful" dikhta hai.
    * Saath hi, Beneficiary Bank (ICICI) bhi User B ko SMS/notification bhejta hai ki uske account mein paise aa gaye hain.

**Failure Handling:** Agar is poore process mein kahin bhi koi gadbad hoti hai (e.g., SBI "insufficient balance" bolta hai, ya ICICI ka server down hai), to NPCI transaction ko fail kar deta hai. Agar paisa debit ho chuka tha, to Remitter Bank (SBI) ko use **roll back (reverse)** karne ka nirdesh diya jaata hai. Isse atomicity sunishchit hoti hai.


---


# 📌 URL Shortening Service System Design

---

### ## What is a URL Shortening Service?

Ek URL Shortening Service (jaise Bitly ya TinyURL) ek online tool hai jo ek lambe web address (URL) ko ek chote, aasani se share kiye jaa sakne wale link mein badal deta hai. Jab koi user us chote link par click karta hai, to service use automatically asli (original) lambe URL par bhej (redirect kar) deti hai. Yeh khaaskar social media (jaise Twitter, jahan character limit hoti hai) aur marketing campaigns mein bahut upyogi hai.

---

### ## Problem Statement (Humein Banana Kya Hai?)

Humein ek atyant uplabdh (highly available) aur tezi se kaam karne waali URL shortening service banani hai jo arabon (billions) URLs ko handle kar sake.

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* User ek lamba URL input kar sake aur uske badle mein ek chota, unique URL prapt kar sake.
* Jab koi user chote URL par click kare, to use asli lambe URL par redirect kiya jaana chahiye.
* User ek optional **custom URL** bhi bana sake (e.g., `short.ly/my-portfolio`).
* Har link ke liye ek optional **samapti tithi (expiration date)** set karne ki suvidha honi chahiye.
* System ko har link ke clicks ki sankhya ko track karna chahiye (analytics ke liye).

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **High Availability:** Redirect service kabhi bhi down nahi honi chahiye. Agar yeh down hoti hai, to internet par maujood laakhon-karodon links kaam karna band kar denge.
* **Low Latency:** Redirect ka process behad tez (ideally < 50 milliseconds) hona chahiye. User ko pata bhi nahi chalna chahiye ki woh redirect ho raha hai.
* **Read-Heavy System:** Ek link banaya (write) ek baar jaata hai, lekin us par click (read) hazaaron ya laakhon baar ho sakta hai. Isliye, system ko fast reads ke liye optimize karna zaroori hai.
* **Scalability:** System ko badhte hue URLs aur clicks ke load ko aasaani se handle karna aana chahiye.
* **Uniqueness:** Har generate kiya gaya chota URL poore system mein unique hona chahiye.

---

### ## Low Level Design (Data Models)

Is system ka core ek simple mapping hai: chota URL -> lamba URL. Iske liye ek **NoSQL Key-Value Database** jaise **DynamoDB** ya **Cassandra** ek behtareen vikalp hai.

* **URLs Table / Collection:**
    * `ShortKey` (PRIMARY KEY / Partition Key): Yeh hamara 6-8 character ka unique string hoga (e.g., "aX8bZc"). Is par index hoga taaki lookup behad tez ho.
    * `LongURL`: Asli lamba URL jo user ne diya tha.
    * `UserID`: Link kisne banaya (registered users ke liye).
    * `CreatedAt`: Kab banaya gaya.
    * `ExpirationTimestamp`: Link kab expire hoga.
    * `ClickCount`: Analytics ke liye, kitni baar click hua.

**Database Ka Chunav:** Ek Key-Value store isliye achha hai kyunki hamara 99% use case ek `ShortKey` dekar uski value (`LongURL`) nikalna hai. Yeh NoSQL databases is kaam ke liye banaye gaye hain aur horizontal scaling (naye servers add karna) inmein bahut aasan hota hai.

---

### ## Architecture and Components (System Ka Naksha)

System ke do mukhya workflows hain: naya link banana (Write Path) aur link ko redirect karna (Read Path). **Read Path ki performance sabse zaroori hai.**

### A. The Write Path (Naya Link Banana)

1.  **Request:** User lamba URL submit karta hai. Request **Load Balancer** se hote hue ek **Application Server** tak pahunchti hai.

2.  **Unique Short Key Generation (Sabse Zaroori Step):** Application server ko ek unique key banani hai.
    * **Approach 1 (Dheema Tarika):** Ek random string generate karo aur DB mein check karo ki woh exist karti hai ya nahi. Agar karti hai (collision), to fir se try karo. Yeh har write ke liye ek extra DB read maangta hai, jo slow hai.
    * **Approach 2 (Behtar Tarika - Base62 Encoding):** Ek counter service se ek unique incrementing number lo (jaise 1001). Is number ko **Base62** (`[0-9a-zA-Z]`) mein convert kar do. Yeh hamesha unique hoga.
    * **Approach 3 (Sabse Scalable - Key Generation Service):** Ek alag **Key Generation Service (KGS)** banao.
        * Yeh service pehle se hi laakhon unique keys generate karke ek fast queue (jaise **Redis**) mein store kar leti hai.
        * Jab Application Server ko ek nayi key chahiye hoti hai, to woh KGS se bas ek key maang leta hai. Isse "check-if-exists" wala DB call bach jaata hai aur write path behad tez ho jaata hai.

3.  **Data Storage:** Application Server us unique `ShortKey` aur user ke `LongURL` ko **Database** mein store kar deta hai.

4.  **Response:** Server user ko poora chota URL (e.g., `https://short.ly/aX8bZc`) response mein bhej deta hai.

### B. The Read Path (Redirect Karna - Yahan Performance Hi Sab Kuch Hai)

1.  **Request:** User `https://short.ly/aX8bZc` par click karta hai. Request **Application Server** tak pahunchti hai.

2.  **Caching (Sabse Pehle):**
    * Server, database mein jaane se pehle, ek **Distributed Cache (jaise Redis ya Memcached)** mein check karta hai ki kya `aX8bZc` key ka data pehle se cache mein hai.

3.  **Cache Hit (Aam Taur Par Yahi Hoga):**
    * Agar `LongURL` cache mein mil jaata hai, to use wahin se turant utha liya jaata hai. Yeh behad fast hota hai.

4.  **Cache Miss (Kabhi Kabhaar):**
    * Agar key cache mein nahi milti hai, **tabhi** server aage **Database** ke paas jaata hai.
    * Database se `LongURL` milne ke baad, server use future requests ke liye **Cache mein daal deta hai**.

5.  **Redirect:** Server user ke browser ko ek **`301 Permanent Redirect`** HTTP response bhejta hai. Is response ke `Location` header mein asli `LongURL` hota hai. Browser is response ko dekhte hi user ko automatically uss lambe URL par le jaata hai.

6.  **Analytics (Asynchronously):**
    * Redirect ko dheema na karne ke liye, click count ko usi samay update nahi kiya jaata.
    * Server click event (ki `aX8bZc` click hua hai) ko ek **Message Queue (jaise Kafka ya SQS)** mein daal deta hai.
    * Background mein chalne wale **Workers** is queue se messages ko batches mein uthate hain aur database mein `ClickCount` ko update karte hain. Isse critical redirect path par koi extra load nahi padta.


---

# 📌 Online Coding Judge System Design

---

### ## What is an Online Coding Judge?

Ek Online Coding Judge (jaise LeetCode, HackerRank, ya Codeforces) ek online platform hai jahan programming ke students aur professionals coding problems ko solve karte hain. Users ek problem statement padhte hain, apni pasand ki programming language (jaise C++, Java, Python) mein code likhte hain, aur use submit karte hain. Platform is code ko automatically compile karta hai, chalaata hai, aur use kai chhupe hue (hidden) test cases ke khilaaf jaanchta hai. Ant mein, yeh ek faisla (verdict) deta hai, jaise 'Accepted', 'Wrong Answer', ya 'Time Limit Exceeded'.

---

### ## Problem Statement (Humein Banana Kya Hai?)

Humein ek scalable aur surakshit (secure) platform design karna hai jo users dwara submit kiye gaye code ko automatically judge kar sake.

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* Users ko coding problems ki ek list dikhni chahiye.
* Users C++, Java, Python jaisi vibhinn (various) languages mein code submit kar sakein.
* System ko submit kiye gaye code ko chhupe hue test cases ke khilaaf run karna chahiye.
* System ko har submission ke liye **samay seema (Time Limit)** aur **memory seema (Memory Limit)** laagu karni chahiye.
* System ko user ke code ke output ki tulna sahi (expected) output se karni chahiye.
* User ko antim faisla (final verdict) dikhna chahiye (e.g., Accepted, Wrong Answer, TLE).
* Users apne pichle submissions ka itihas (history) dekh sakein.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **Security (Sabse Zaroori):** User dwara submit kiya gaya code "untrusted" hota hai. Use ek **surakshit sandbox** mein chalana anivarya hai taaki woh main system ko koi nuksaan na pahuncha sake (e.g., `rm -rf /` jaisi commands se bachav).
* **Scalability:** System ko ek saath aane waale hazaaron submissions (khaaskar live contests ke dauran) ko handle karne ke liye scalable hona chahiye.
* **Reliability:** Agar ek judging server crash ho jaata hai, to submission lost nahi hona chahiye. Use kisi doosre server dwara process kiya jaana chahiye.
* **Fairness & Consistency:** Sabhi submissions ko ek samaan (identical) environment mein judge kiya jaana chahiye taaki result nishpaksh (fair) ho.

---

### ## Low Level Design (Data Models)

* **Users Table:** `UserID`, `Username`, `PasswordHash`, `Email`, `Rating`.
* **Problems Table:**
    * `ProblemID` (PRIMARY KEY)
    * `Title`, `Description` (Problem statement in Markdown/HTML)
    * `Difficulty` (Easy, Medium, Hard)
    * `TimeLimit` (in seconds), `MemoryLimit` (in MB)
* **TestCases Table:**
    * `TestCaseID` (PRIMARY KEY)
    * `ProblemID` (ForeignKey)
    * `InputData` (`TEXT` or File Path)
    * `ExpectedOutput` (`TEXT` or File Path)
* **Submissions Table:** (Ye sabse active table hai)
    * `SubmissionID` (PRIMARY KEY)
    * `UserID`, `ProblemID`, `Language`
    * `Code` (`TEXT`)
    * `Status` (Enum: PENDING, JUDGING, ACCEPTED, WRONG_ANSWER, TLE, MLE, COMPILATION_ERROR)
    * `ExecutionTime` (in ms), `ExecutionMemory` (in KB)
    * `Timestamp`

---

### ## Architecture and Components (System Ka Naksha)

Is system ka sabse zaroori design principle hai **web servers** ko **judging process** se poori tarah se alag (decouple) karna. Iske liye ek **Message Queue** ka istemal kiya jaata hai.

#### The Key Components
1.  **Web Servers:** Yeh stateless servers hain jo user ke requests handle karte hain—jaise problem dikhana, submission accept karna, aur result dikhana.
2.  **Database:** Upar diye gaye saare data models ko store karta hai (e.g., PostgreSQL, MySQL).
3.  **Message Queue (System ka Dil):** Ek service jaise **RabbitMQ** ya **AWS SQS**. Yeh Web Servers aur Judge Workers ke beech ek buffer ka kaam karta hai.
4.  **Judge Workers:** Yeh servers (ya containers) ka ek fleet (samooh) hai jinka ek hi kaam hai: submissions ko evaluate karna.
5.  **Sandbox Environment:** Har Judge Worker ke andar ek surakshit, isolated environment. Iske liye **Docker Containers** industry standard hain.

### The Submission & Judging Flow

1.  **Submission from User:**
    * User website par code likhta hai aur "Submit" button par click karta hai.
    * Request, jismein `Code`, `Language`, `ProblemID`, etc., hota hai, ek **Web Server** tak pahunchti hai.

2.  **Queuing the Submission:**
    * Web Server code ko **run nahi karta**. Yeh ek bahut bada security risk hoga.
    * Iske bajaye, Web Server `Submissions` table mein ek nayi entry banata hai jiska status `PENDING` hota hai, aur use ek `SubmissionID` mil jaata hai.
    * Fir, Web Server is `SubmissionID` ko ek message ke roop mein **Message Queue** mein daal deta hai. Ab is submission ke liye web server ka kaam khatm. User ko screen par "In Queue..." dikhta hai.

3.  **The Judging Process (Backend mein):**
    * Ek khaali (idle) **Judge Worker** Message Queue se ek `SubmissionID` uthata hai.
    * Worker, DB mein us submission ka status `PENDING` se `JUDGING` kar deta hai.
    * Fir woh DB se `SubmissionID` ke aadhar par poora code aur us problem se jude saare test cases ko fetch karta hai.

4.  **Sandboxed Execution (Suraksha Kavach):**
    * Judge Worker ek naya, saaf-suthra **Docker Container** shuru karta hai. Yahi hamara sandbox hai.
    * User ka code (`solution.cpp`) aur ek test case ki input file (`input.txt`) is container ke andar copy ki jaati hai.
    * Worker container ke andar command chala kar code ko compile karta hai (e.g., `g++ solution.cpp`). Agar compile fail hota hai, to "Compilation Error" record karke process rok diya jaata hai.
    * Agar compile safal hota hai, to worker program ko run karta hai, use `input.txt` deta hai, aur uske output (`output.txt`) ko capture karta hai.
    * **Sabse Zaroori:** Is Docker container ko **resource limits** ke saath shuru kiya jaata hai (e.g., 1 second CPU time, 256 MB RAM) taaki TLE aur MLE ko laagu kiya jaa sake.

5.  **Verdict Calculation:**
    * Worker, program ke `output.txt` ki tulna test case ke `ExpectedOutput` se karta hai.
    * **Match Nahi Hua:** Verdict -> `Wrong Answer`. Judging yahin ruk jaati hai.
    * **Samay Seema Paar:** Verdict -> `Time Limit Exceeded (TLE)`. Judging ruk jaati hai.
    * **Memory Seema Paar:** Verdict -> `Memory Limit Exceeded (MLE)`. Judging ruk jaati hai.
    * **Match Ho Gaya:** Worker agle test case ke liye Step 4 aur 5 doharata hai.
    * **Saare Test Cases Pass:** Verdict -> `Accepted (AC)`.

6.  **Final Update:**
    * Judge Worker antim verdict, execution time, aur memory usage ko `Submissions` table mein update kar deta hai.
    * User ka browser, jo result ka intezaar kar raha tha (polling ya WebSocket ke zariye), naya result display kar deta hai. Judge Worker us Docker container ko nasht (destroy) kar deta hai aur agle submission ke liye taiyaar ho jaata hai.

---

# 📌 Amazon (E-commerce Platform) System Design

---

### ## What is Amazon?

Amazon ek vishv-vyapi (global) e-commerce company hai jo "sab kuch" bechne ke liye jaani jaati hai—kitaabon aur electronics se lekar grocery aur cloud computing (AWS) tak. Yeh ek marketplace model par kaam karti hai, jahan Amazon khud bhi saaman bechta hai aur laakhon anya (third-party) sellers ko bhi apna saaman bechne ke liye platform pradaan karta hai. Iska technology stack duniya ke sabse bade aur sabse complex stacks mein se ek hai.

---

### ## Problem Statement (Humein Banana Kya Hai?)

Humein ek atyant scalable, vishwasniya (reliable), aur pradarshan-kushal (performant) e-commerce platform design karna hai jo laakhon-karodon products aur users ko handle kar sake. Hum core shopping anubhav (experience) par dhyaan denge: product khojna, dekhna, cart mein add karna, aur order place karna.

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* Users products ko **search** aur **browse** kar sakein.
* Users product details page dekh sakein, jismein description, images, reviews, aur price ho.
* Users items ko **shopping cart** mein add/remove kar sakein.
* Users **order place** kar sakein aur online payment kar sakein.
* Users apni order history dekh sakein.
* Third-party sellers apne products list kar sakein aur apni inventory manage kar sakein.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **High Availability:** Platform 24/7 chalna chahiye. Downtime ka matlab seedha revenue ka nuksaan hai.
* **Scalability:** System ko rozana ke traffic ke saath-saath tyohaaron (Diwali, Black Friday) ke dauran aane waale achanak traffic spikes ko bhi handle karna aana chahiye.
* **Low Latency:** Product pages aur search results turant (200ms ke andar) load hone chahiye.
* **Strong Consistency:** **Inventory** aur **Orders** se juda data hamesha consistent hona chahiye. Ek out-of-stock item kabhi bhi bikna nahi chahiye.
* **Durability:** Ek baar place kiya gaya order ya user ka data kabhi bhi khona (lost) nahi chahiye.
* **Security:** User ki personal information aur payment details poori tarah se surakshit honi chahiye.

---

### ## Architecture: The Microservices Approach

Amazon jaise vishaal system ko ek single application (monolith) mein banana asambhav hai. Isliye, yeh **Microservices Architecture** par bana hai. Iska matlab hai ki poore system ko chhote-chhote, independent services mein toda gaya hai. Har service ka ek hi kaam hota hai, uski apni dedicated database hoti hai, aur use alag se develop aur scale kiya jaa sakta hai.

#### Key Microservices (Mukhya Services)
1.  **Product Catalog Service:** Sabhi products ki jaankari (naam, description, price, images) manage karta hai.
2.  **Search Service:** User ke search queries ko handle karta hai. Yeh Elasticsearch jaise search engine par bana hota hai.
3.  **Inventory Service:** Har product ke stock (kitne items bache hain) ko track karta hai. Yeh behad critical service hai.
4.  **Cart Service:** Har user ke shopping cart ko manage karta hai.
5.  **Order Service:** Order place hone ke baad uski poori lifecycle (payment, shipping, delivery) ko manage karta hai.
6.  **User Service:** User accounts, addresses, aur profiles ko manage karta hai.
7.  **Payment Service:** Payment gateways ke saath interact karta hai.
8.  **Recommendation Service:** "Customers who bought this also bought..." jaise recommendations generate karta hai.

---

### ## Low Level Design (Har Service Ka Apna Database)

* **Product Catalog DB (NoSQL like DynamoDB/Cassandra):**
    * `Products Table`: `ProductID`, `Title`, `Description`, `SellerID`, `Attributes` (JSON).
    * Yeh read-heavy hota hai, isliye NoSQL achha hai.

* **Inventory DB (Strongly Consistent SQL like PostgreSQL):**
    * `Inventory Table`: `ProductID`, `WarehouseID`, `Quantity`.
    * Yahan **ACID transactions** anivarya hain taaki stock count kabhi galat na ho.

* **Order DB (SQL like PostgreSQL/MySQL):**
    * `Orders Table`: `OrderID`, `UserID`, `OrderDate`, `TotalAmount`, `ShippingAddress`, `OrderStatus`.
    * `Order_Items Table`: `OrderID`, `ProductID`, `Quantity`, `PriceAtPurchase`.
    * Yeh bhi transactional hota hai.

* **Cart DB (In-memory DB like Redis):**
    * `Key`: `UserID`
    * `Value`: A list of `{ProductID, Quantity}`.
    * Cart data temporary hota hai aur fast access chahiye, isliye Redis perfect hai.

---

### ## Core Workflow: The Checkout Process (Order Place Karna)

Yeh ek complex process hai jismein kai microservices ek saath kaam karte hain.

1.  **Initiation:** User "Place Order" par click karta hai. Browser se request ek **API Gateway** par jaati hai, jo use **Order Service** ko bhej deta hai.

2.  **Orchestration by Order Service:** Order Service is poore process ka "conductor" hai. Yeh ek **transaction** ya **SAGA pattern** shuru karta hai.

3.  **Step 1: Check & Reserve Inventory:**
    * Order Service, cart mein maujood har item ke liye **Inventory Service** ko call karta hai.
    * "Kya `ProductID-123` ke 2 pieces available hain?"
    * Inventory Service stock check karti hai aur agar available hai, to un 2 pieces ko **temporarily reserve** kar leti hai (quantity ko `on_hold` state mein daal deti hai).
    * Agar koi bhi item out of stock hai, to process yahin fail ho jaata hai aur user ko error dikha diya jaata hai.

4.  **Step 2: Process Payment:**
    * Agar inventory reserve ho gayi hai, to Order Service **Payment Service** ko call karta hai.
    * Payment Service, user ko payment gateway par redirect karti hai aur payment ka status dekhti hai.
    * Agar payment fail ho jaata hai, to Order Service **Inventory Service** ko bolkar reserve kiye gaye items ko **release** kar deti hai (rollback).

5.  **Step 3: Finalize the Order (Payment Successful):**
    * Payment safal hone par, Order Service apne **Order Database** mein ek permanent entry banata hai (`OrderStatus` = `CONFIRMED`).
    * Yeh **Inventory Service** ko ek final confirmation bhejta hai ki "stock ko permanently kam kar do".
    * Iske baad, Order Service ek `Order_Placed` event ko ek **Message Queue (jaise AWS SQS ya Kafka)** mein daal deta hai.

6.  **Asynchronous Events (Background Mein Hone Wale Kaam):**
    * Queue mein event daalne ke baad Order Service ka kaam poora ho jaata hai aur woh user ko success response bhej deta hai.
    * Ab, doosri services is event ko sunti hain:
        * **Notification Service:** User ko confirmation email/SMS bhejti hai.
        * **Shipping/Logistics Service:** Seller ke warehouse ko inform karti hai ki "yeh order pack karke ship karo".
        * **Cart Service:** User ke cart ko khaali kar deti hai.

Is microservices approach se har hissa independent rehta hai, jisse Amazon jaise vishaal system ko manage karna, scale karna, aur update karna aasan ho jaata hai.
---
# 📌 Google Maps System Design

---

### ## What is Google Maps?

Google Maps Google dwara develop ki gayi ek web mapping service hai. Yeh sirf ek digital atlas nahi hai, balki ek comprehensive tool hai jo satellite imagery, street maps, 360° panoramic views (Street View), real-time traffic conditions, aur turn-by-turn navigation pradaan karta hai. Yeh duniya bhar mein laakhon-karodon logon ke liye rozmarra ki zindagi ka ek abhinna ang ban chuka hai, jise log jagah dhoondhne, raasta pata karne, aur apni yaatra plan karne ke liye istemal karte hain.

---

### ## Problem Statement (Humein Banana Kya Hai?)

Humein ek atyant vishwasniya (highly reliable), scalable, aur kam latency wala mapping system design karna hai jo users ko nimnlikhit mukhya suvidhaayein de sake:

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* User poori duniya ka interactive map dekh sakein (pan, zoom).
* User kisi bhi jagah (Points of Interest - POI) ya address ko **search** kar sakein.
* System ko ek jagah se doosri jagah jaane ke liye alag-alag transport modes (car, bike, walking, public transport) ke liye **sabse behtar raasta (route)** dikhana chahiye.
* System ko sadkon par **real-time traffic** ki sthiti dikhani chahiye (e.g., laal, peela, hara rang).
* System ko yaatra ke liye ek sateek **anumani pahunchne ka samay (Estimated Time of Arrival - ETA)** batana chahiye.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **High Availability:** Maps hamesha uplabdh hone chahiye. Log ispar navigation ke liye nirbhar karte hain.
* **Low Latency:** Map tiles, search results, aur routes turant load hone chahiye.
* **Scalability:** System ko poore vishwa se aane waale arabon (billions) requests ko handle karna aana chahiye.
* **Accuracy:** Map data, locations, aur ETAs bilkul sateek (accurate) hone chahiye.
* **Data Freshness:** Real-time traffic data har kuch minute mein update hona chahiye.

---

### ## High-Level Architecture & Key Components

Google Maps ek monolithic application nahi hai. Yeh kai specialized microservices ka ek jatil (complex) sangathan hai.

1.  **Data Collection & Processing Layer:** Yeh neenv (foundation) hai. Data kai sroton (sources) se aata hai: satellite imagery companies, Street View cars, sarkari data, aur sabse zaroori, laakhon-karodon Android phones se aane waala **anonymized GPS location data**. Is saare data ko process karke base map, road network, aur POI database banaya jaata hai.

2.  **Map Rendering Service:**
    * Yeh service map dikhane ke liye zimmedaar hai.
    * Yeh **Map Tiles** ke concept par kaam karti hai. Poori duniya ke map ko alag-alag zoom levels par chhote-chhote square images (tiles) mein pehle se hi render karke rakh liya jaata hai.
    * Jab aap map dekhte hain, to aapka phone ya browser sirf unhi tiles ko request karta hai jo aapki screen par dikh rahi hain. Isse map bahut tezi se load hota hai.

3.  **Search & Geocoding Service:**
    * **Geocoding:** Yeh ek text address (e.g., "Civil Lines, Prayagraj") ko geographical coordinates (latitude, longitude) mein badalta hai.
    * **Search:** Yeh "mere paas ke restaurants" jaisi queries ko handle karta hai. Yeh ek normal database search nahi hai, balki ek **geospatial search** hai. Iske liye specialized data structures jaise **Quadtrees** ya **Geohashing** ka istemal hota hai.

4.  **Routing/Navigation Service:**
    * Yeh raasta dhoondhne wala "dimaag" hai.
    * Yeh poore road network ko ek vishaal **Graph** ke roop mein dekhta hai (sadkein = edges, chauraahe = nodes).
    * Kisi bhi sadak (edge) ka 'weight' ya 'cost' sirf doori nahi, balki `samay = doori / gati` hota hai. Aur `gati` (speed) **Real-Time Traffic Service** se aati hai.
    * Yeh **Dijkstra's** ya **A*** (A-star) jaise graph traversal algorithms ka istemal karke sabse tez raasta dhoondhta hai.

5.  **Real-Time Traffic Service:**
    * **Data Ingestion:** Laakhon Android phones se lagatar anonymized GPS pings (location + speed) aate rehte hain.
    * **Data Processing:** Ek real-time streaming pipeline (jaise Kafka, Spark Streaming) is data ko process karti hai aur har chote-chote road segment ke liye average speed calculate karti hai.
    * Yeh calculated speed ek fast database mein store hoti hai.

6.  **ETA Prediction Service:**
    * Yeh Routing Service se route leta hai.
    * Route ke har segment ke liye, yeh Traffic Service se current speed nikalta hai.
    * Saath hi, yeh **historical data** ("Prayagraj mein Shanivaar shaam ko Civil Lines mein traffic hamesha zyada hota hai") aur Machine Learning models ka istemal karke antim ETA ka sateek anuman lagata hai.

---

### ## Core Workflow: Ek Jagah Se Doosri Jagah Navigation

Chaliye dekhte hain ki jab aap "Prayagraj Junction" se "New Yamuna Bridge" ka direction dhoondhte hain to parde ke peeche kya hota hai.

1.  **Geocoding:** Aapka phone "Prayagraj Junction" aur "New Yamuna Bridge" ko **Geocoding Service** ke paas bhejta hai taaki inke latitude aur longitude coordinates mil sakein.

2.  **Route Request:** Yeh coordinates ab **Routing Service** ko bheje jaate hain.

3.  **Pathfinding on Graph:** Routing Service in coordinates ko apne road network graph ke sabse nazdeeki nodes se map karti hai.

4.  **Real-Time Cost Calculation:** Ab, yeh A* algorithm chalaati hai. Jab bhi algorithm kisi sadak (edge) par jaane ka "cost" (samay) calculate karta hai, to woh turant **Real-Time Traffic Service** se us sadak ki current average speed poochta hai. Isse use pata chalta hai ki ek 2km lambi sadak par abhi 5 minute lagenge ya traffic jam ke kaaran 20 minute.

5.  **Best Path Found:** Algorithm sabse kam samay wala raasta (kai sadkon ka sequence) dhoondh nikalta hai.

6.  **ETA Calculation:** Yeh poora route ab **ETA Prediction Service** ke paas jaata hai. Yeh service har segment ke liye real-time samay ko jodti hai aur usmein historical patterns ke aadhar par thoda adjustment karke ek final, sateek ETA batati hai.

7.  **Display to User:** Yeh poora route (map par line ke saath) aur final ETA aapke phone par bhej diya jaata hai.

8.  **Real-Time Updates:** Jaise-jaise aap gaadi chalaate hain, aapka phone lagatar apni nayi location bhejta rehta hai. Agar aap galat mud jaate hain ya aage traffic badal jaata hai, to yeh poora process (Step 2 se) doharaya jaata hai taaki aapko hamesha sabse behtar route aur updated ETA milta rahe.


---


# 📌 Google Docs System Design

---

### ## What is Google Docs?

Google Docs ek free, web-आधारित (web-based) word processor hai jo Google Drive suite ka ek hissa hai. Microsoft Word jaise traditional software se alag, iski sabse badi aur krantikari (revolutionary) visheshta iska **real-time collaboration** hai. Iska matlab hai ki kai users ek hi samay mein, ek hi document par kaam kar sakte hain, aur ek doosre ke changes (jaise typing karna, text delete karna) ko turant, live dekh sakte hain. Sabhi badlav automatically cloud mein save ho jaate hain.

---

### ## Problem Statement (Humein Banana Kya Hai?)

Humein ek highly responsive aur vishwasniya (reliable) web-based document editor design karna hai jiska mukhya focus real-time, multi-user collaboration par ho.

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* User text documents create, edit, aur format kar sakein (bold, italics, etc.).
* **Sabse Zaroori:** Kai users ek saath ek hi document ko edit kar sakein aur ek doosre ke cursors aur changes ko live dekh sakein.
* System ko document ka ek poora **sanshodhan itihas (version history)** save karna chahiye, jisse users purane versions ko dekh aur restore kar sakein.
* Users **offline** bhi document par kaam kar sakein, aur online aane par unke changes automatically sync ho jaayein.
* Users document mein comments add kar sakein aur doosre logon ke saath vishisht anumatiyon (specific permissions - view, comment, edit) ke saath share kar sakein.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **Low Latency:** Collaborative edits (keystrokes) doosre users ki screen par lagbhag turant (near-instantly) dikhne chahiye.
* **Consistency:** Ant mein (eventually), sabhi users ko document ka bilkul aakhri aur astitv (identical) version dikhna chahiye, chahe edits kisi bhi kram (order) mein kiye gaye hon.
* **High Availability & Durability:** Service hamesha uplabdh honi chahiye aur user ka document kabhi bhi khona (lost) ya corrupt nahi hona chahiye.
* **Scalability:** System ko laakhon-karodon concurrent editing sessions ko handle karne ke liye scalable hona chahiye.

---

### ## High-Level Architecture & The Core Algorithm

Google Docs ka jaadu iske collaboration algorithm mein chhupa hai. Ek simple client-server model yahan poori tarah se kaam nahi karega kyunki server ko clients tak changes "push" karne ki zaroorat hoti hai.

#### Key Components:
1.  **Client (Browser):** Yeh user ka interface hai. Iske paas document ki ek local copy hoti hai aur yeh user ke actions ko "operations" mein badalta hai.
2.  **Server (Collaboration Service):** Yeh system ka "dimaag" hai. Yeh document ki authoritative (pramanik) copy rakhta hai, saare operations ka ek log maintain karta hai, aur conflicts ko aane se rokta hai.
3.  **Persistent Connection (WebSocket):** Real-time communication ke liye client aur server ke beech ek lagatar bana rehne wala connection zaroori hai. Iske liye **WebSockets** ek behtareen technology hai, jo server ko clients ko data bhejne ki anumati deti hai.

### The Core Algorithm: Operational Transformation (OT)

Yeh woh algorithm hai jo Google Docs ko "live" banata hai. Iska mukhya kaam concurrent edits se paida hone waale conflicts ko resolve karna hai.

**OT ko aasan shabdon mein samjhein:**

Sochiye, document mein text hai "Prayagraj". Server aur dono users (A aur B) abhi **version 1** par hain.

* **User A** position 9 par '!' insert karna chahta hai: `Prayagraj!`
* **User B** usi samay position 0 par 'Hello ' insert karna chahta hai: `Hello Prayagraj`

**Scenario (bina OT ke):**
Agar A ka operation (`insert '!' at 9`) pehle server tak pahunchta hai, to document ban jaata hai "Prayagraj!". Ab jab B ka operation (`insert 'Hello ' at 0`) pahunchta hai, to woh apply ho jaata hai aur document banta hai "Hello Prayagraj!". Yeh sahi hai.

**Conflict (bina OT ke):**
Lekin, agar B ka operation pehle pahunchta hai, to document ban jaata hai "Hello Prayagraj". Ab jab A ka operation (`insert '!' at 9`) pahunchta hai, to woh galat jagah apply hoga. Position 9 ab 'g' hai, to result hoga "Hello Prayag!raj". **Yeh galat hai!**

**OT ka Jaadu:**
Jab B ka operation pehle pahunch jaata hai, to server document ko "Hello Prayagraj" bana deta hai aur version ko **2** kar deta hai. Jab A ka operation (jo **version 1** par kiya gaya tha) server par aata hai, to server dekhta hai ki document ka version badal chuka hai. OT algorithm A ke operation ko "transform" karta hai. Woh samajh jaata hai ki shuru mein 6 naye characters (`Hello `) aa gaye hain, isliye `insert '!' at 9` ko ab `insert '!' at 15` (9+6) hona chahiye. Server is transformed operation ko apply karta hai, aur result banta hai "Hello Prayagraj!". **Yeh sahi hai!**

OT sunishchit karta hai ki operations chahe kisi bhi kram mein aayein, unhe transform karke antim result hamesha consistent rakha jaata hai.

---

### ## Core Workflow: Ek User Ke Type Karne Par Kya Hota Hai?

1.  **Client-Side Action:** User A ek character 'k' type karta hai. Yeh character uski screen par **turant** dikh jaata hai taaki use lag na mehsoos ho.

2.  **Operation Creation:** Client ka browser poora document nahi bhejta. Woh ek chota sa "operation" banata hai, jaise: `{ action: 'insert', char: 'k', position: 50, doc_version: 10 }`.

3.  **Send to Server:** Yeh operation **WebSocket** ke zariye **Collaboration Server** ko bheja jaata hai.

4.  **Server-Side Processing:** Server operation receive karta hai.
    * Woh check karta hai ki operation ka version (`10`) uske current document version se match karta hai ya nahi.
    * Agar haan, to woh operation ko document par apply karta hai, document ka version `11` kar deta hai, aur is operation ko ek log (version history ke liye) mein save kar leta hai.
    * Agar versions match nahi karte, to woh upar bataye gaye **OT algorithm** se operation ko transform karta hai.

5.  **Broadcast to Others:** Server is naye, astitv (validated) operation ko document se jude **baaki sabhi clients** (User B, User C) ko broadcast kar deta hai.

6.  **Update Other Clients:** Doosre clients (User B, C) is operation ko receive karte hain aur use apne local document copy par apply karte hain. Ab 'k' character unki screen par bhi dikhne lagta hai.

### Offline Editing Kaise Kaam Karta Hai?
* Jab user offline jaata hai, to uske saare changes (operations) uske device par ek list mein save hote rehte hain.
* Jab woh wapas online aata hai, to client us poori list of operations ko server ko bhej deta hai.
* Server OT ka istemal karke in saare offline operations ko un sabhi changes ke khilaaf transform karta hai jo doosre users ne us dauran kiye the, aur ant mein sabke documents ko sync kar deta hai.
---
# 📌 Airline Management System Design

---

### ## What is an Airline Management System?

Ek Airline Management System (AMS) ek vishaal software suite hai jo ek airline company ke sabhi operations ko manage karne ke liye design kiya gaya hai. Yeh sirf ticket booking website nahi hai; iske kai mukhya bhaag (modules) hote hain:

* **Airline Reservation System (ARS):** Jise hum design karenge. Yeh customer-facing system hai jo flight search, booking, aur payments ko handle karta hai.
* **Flight Scheduling System:** Yeh airline ke routes, flight timings, aur kaun sa aircraft kis route par udega, yeh tay karta hai.
* **Crew Management System:** Pilots aur cabin crew ko flights par assign karna, unke working hours aur rest periods ka dhyan rakhna.
* **Inventory Management System:** Har flight ki seats ka hisaab-kitaab rakhna.
* **Check-in & Boarding System:** Airport par check-in, boarding pass issue karne, aur boarding process ko manage karne wala system.

Is design mein, hum mukhya roop se **Airline Reservation System (ARS)** par dhyaan denge, kyunki Prayagraj se Delhi ki flight book karne se lekar payment tak ka anubhav isi par nirbhar karta hai.

---

### ## Problem Statement (Reservation System Ke Liye)

Humein ek global, 24/7 chalne wala flight reservation system design karna hai jo real-time mein seat availability aur dynamic pricing ko handle kar sake.

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* User one-way, round-trip, ya multi-city flights **search** kar sakein.
* System ko flight options, unki timings, duration, aur alag-alag classes (Economy, Business, First) ke liye **dynamically calculate kiye gaye fares** dikhane chahiye.
* User flight select kar sakein, passenger details bhar sakein, aur apni pasand ki seat (agar available ho) chun sakein.
* User credit card, UPI, ya anya methods se **payment** karke booking poori kar sakein.
* Safal booking par system ko ek **PNR (Passenger Name Record)** aur e-ticket generate karna chahiye.
* User flight se pehle **web check-in** kar sakein.
* User booking ko (niyamon ke anusaar) **cancel** kar sakein.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **High Availability:** System 24/7, poore vishwa mein, bina downtime ke uplabdh hona chahiye.
* **Strong Consistency (Behad Zaroori):** Seat inventory aur booking data bilkul consistent hona chahiye. Ek seat do baar book nahi ho sakti. **ACID compliance** anivarya hai.
* **Scalability:** System ko chhuttiyon (holidays) aur sales ke dauran aane waale bhaari traffic ko aasani se handle karna aana chahiye.
* **Reliability & Fault Tolerance:** Payment failure jaisi sthiti mein system ko gracefully recover karna chahiye, bina user ke paise ya booking ko khatre mein daale.
* **Low Latency:** Flight search results bahut tezi se aane chahiye.

---

### ## Low Level Design (Data Models for ARS)

Is system ke core transactional hisse ke liye ek **Relational Database (SQL)**, jaise PostgreSQL, anivarya hai.

* **Airports Table:**
    * `AirportCode` (PRIMARY KEY, e.g., 'IXD' for Prayagraj), `AirportName`, `City`, `Country`.
* **Aircrafts Table:**
    * `AircraftID` (PK), `ModelName`, `TotalEconomySeats`, `TotalBusinessSeats`.
* **Flights Table (Master Schedule):**
    * `FlightID` (PK), `FlightNumber` (e.g., '6E-2025'), `AircraftID` (FK), `SourceAirportCode`, `DestinationAirportCode`.
* **Flight_Instances Table (Rozana ki Udaanein):**
    * `InstanceID` (PK), `FlightID` (FK), `FlightDate`, `DepartureTime`, `ArrivalTime`, `Status` (ON_TIME, DELAYED, CANCELLED).
* **Seat_Inventory Table:**
    * `InstanceID` (FK), `FareClass` (Economy, Business), `TotalSeats`, `BookedSeats`.
* **Bookings Table:**
    * `PNR` (PRIMARY KEY), `UserID`, `InstanceID` (FK), `BookingDate`, `TotalFare`, `Status` (CONFIRMED, CANCELLED).
* **Passengers Table:**
    * `PassengerID` (PK), `PNR` (FK), `FullName`, `Age`, `SeatNumber`.

---

### ## Architecture and Components (System Ka Naksha)

Yeh system **Microservices Architecture** par आधारित hoga taaki alag-alag functionalities ko independently manage aur scale kiya jaa sake.

#### Key Microservices
1.  **Search Service:** Flight search queries ko handle karta hai. Yeh read-heavy hai.
2.  **Pricing Service:** Har flight ke liye real-time mein dynamic fare calculate karta hai (demand, bachi hui seats, aur din ke aadhar par).
3.  **Booking Service:** Booking workflow ka transactional core hai.
4.  **Inventory Service:** Seat availability ko manage karta hai aur double-booking ko rokta hai.
5.  **Payment Service:** Payment gateways ke saath communication handle karta hai.
6.  **Check-in Service:** Web check-in aur seat assignment ko manage karta hai.
7.  **Notification Service:** Booking confirmation, delays, cancellations ke liye Email/SMS bhejta hai.

### Core Workflow 1: Flight Search (Read-Heavy)

1.  User Prayagraj (IXD) se Delhi (DEL) ke liye 15 October 2025 ki flight search karta hai. Request **API Gateway** se **Search Service** ko jaati hai.
2.  Search Service `Flights` aur `Flight_Instances` tables se us route aur date ki sabhi flights nikalta hai.
3.  Har flight ke liye, yeh doosri services ko call karta hai:
    * **Pricing Service** se us flight ka current fare poochta hai.
    * **Inventory Service** se us flight mein bachi hui seats ki jaankari leta hai.
4.  Search Service saari jaankari ko ek saath laakar user ko flight options ki ek list dikha deta hai. Popular routes ke results ko **Cache** kiya jaata hai taaki performance behtar ho.

### Core Workflow 2: Flight Booking (Write-Heavy & Transactional)

Yeh bilkul IRCTC ke Tatkal booking jaisa critical process hai.

1.  User ek flight select karke "Book Now" par click karta hai. Request **Booking Service** ko jaati hai.
2.  **Transaction & Lock:** Booking Service ek **DATABASE TRANSACTION** shuru karti hai.
3.  Yeh **Inventory Service** se seats ki availability confirm karti hai. Agar seats available hain, to Inventory Service un seats par ek **temporary lock** laga deti hai (e.g., `BookedSeats` ko increment karke `OnHoldSeats` ko badha deti hai). Yeh lock 15 minute ke liye valid hota hai. **Yeh double-booking rokne ka sabse zaroori kadam hai.**
4.  **Payment:** User ko **Payment Service** par redirect kiya jaata hai taaki woh payment poora kar sake.
5.  **Transaction Outcome:**
    * **Payment Successful:** Payment Gateway se success ka confirmation milne par, Booking Service database transaction ko **COMMIT** karti hai. Yeh PNR generate karti hai, booking details save karti hai, aur Inventory Service ko lock ko permanent `BookedSeats` mein convert karne ko bolti hai. Ek `Booking_Successful` event **Message Queue** (jaise Kafka) mein daal diya jaata hai jise **Notification Service** sunkar user ko ticket bhej deti hai.
    * **Payment Failed / Timeout:** Agar 15 minute mein payment nahi hota ya fail ho jaata hai, to Booking Service transaction ko **ROLLBACK** kar deti hai. Yeh Inventory Service ko nirdesh deti hai ki woh temporary lock ko hata de, taaki woh seats doosre users ke liye available ho jaayein.


---
# 📌 Airbnb System Design

---

### ## What is Airbnb?

Airbnb ek online marketplace hai jo logon ko apni property ya ghar ka koi kamra kiraye par dene ki suvidha deta hai. Yeh ek **two-sided marketplace** hai jo do tarah ke users ko jodta hai:
1.  **Hosts (Mezbaan):** Woh log jo apni property (ghar, apartment, villa) ko rent ke liye list karte hain.
2.  **Guests (Mehmaan):** Woh log jo kahin ghoomne ya rehne ke liye anokhi jagah (accommodations) dhoondh rahe hain.

Yeh traditional hotels se alag hai kyunki yeh users ko local anubhav (experience) aur zyaada variety pradaan karta hai. Iska poora business model **vishwas (trust)** par aadhaarit hai, jo reviews aur secure payments ke zariye banaya jaata hai.

---

### ## Problem Statement (Humein Banana Kya Hai?)

Humein ek scalable aur vishwasniya (reliable) platform design karna hai jo Hosts ko apni properties list karne aur Guests ko unhe search, book, aur review karne ki anumati de.

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)

**Guest Side:**
* Location, dates, aur mehmaano ki sankhya ke aadhar par properties **search** kar sakein.
* Advanced filters ka istemal kar sakein (e.g., price range, property type, suvidhaayein jaise WiFi, Pool).
* Property ki details, photos, reviews, aur host ki profile dekh sakein.
* Stay **book** kar sakein aur online payment kar sakein.
* Host ke saath platform ke zariye **message** par baat kar sakein.
* Stay ke baad Host ko **review** kar sakein.

**Host Side:**
* Apni property ki **listing** create aur manage kar sakein.
* Apni property ka **availability calendar** manage kar sakein (kaun si dates booked hain ya available hain).
* Apni property ki **pricing** set kar sakein.
* Booking requests ko accept ya decline kar sakein.
* Guest ko **review** kar sakein.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **High Availability:** Platform hamesha, duniya bhar ke users ke liye, uplabdh hona chahiye.
* **Strong Consistency:** Booking aur availability calendar ke liye yeh behad zaroori hai. Ek hi property ek hi date par do baar book nahi honi chahiye.
* **Low Latency:** Geo-spatial search (map par properties dhoondhna) bahut tez hona chahiye.
* **Scalability:** System ko laakhon-karodon listings aur user traffic ko handle karna aana chahiye.
* **Trust & Security:** User data, payments, aur communication surakshit hone chahiye.

---

### ## Low Level Design (Data Models)

Core data ke liye ek **Relational Database (SQL)**, jaise PostgreSQL (jismein PostGIS jaisa powerful geospatial extension hai), ek achha vikalp hai.

* **Users Table:**
    * `UserID` (PK), `Name`, `Email`, `PasswordHash`, `ProfilePictureURL`, `Bio`, `IsHost`.
* **Properties (Listings) Table:**
    * `PropertyID` (PK), `HostID` (FK to Users), `Title`, `Description`, `PropertyType`, `Address`, `Latitude`, `Longitude`, `PricePerNight`, `MaxGuests`.
* **Bookings Table (Transactional Core):**
    * `BookingID` (PK), `GuestID` (FK), `PropertyID` (FK), `CheckInDate`, `CheckOutDate`, `TotalAmount`, `BookingStatus` (PENDING, CONFIRMED, CANCELLED).
* **Availability Table (For Fast Search):**
    * `PropertyID`, `Date`, `IsAvailable` (Boolean), `Price`. (Yeh table denormalized hoti hai taaki search ke waqt availability check karna tez ho).
* **Reviews Table (Two-way reviews):**
    * `ReviewID` (PK), `BookingID` (FK), `ReviewerID` (FK), `RevieweeID` (FK), `Rating`, `CommentText`.
* **Messages Table:**
    * `MessageID` (PK), `BookingID` (FK), `SenderID` (FK), `ReceiverID` (FK), `MessageText`, `Timestamp`.

---

### ## Architecture and Components (System Ka Naksha)

Airbnb jaise complex system ke liye **Microservices Architecture** sabse behtar hai.

#### Key Microservices
1.  **Search Service:** Yeh read-heavy service hai jo geospatial queries handle karti hai. Iske liye **Elasticsearch** jaisa search engine behtareen hai.
2.  **Listings Service:** Hosts dwara properties ki saari jaankari (CRUD operations) ko manage karta hai.
3.  **Booking Service:** Booking workflow ka transactional core hai. Yeh strong consistency par focus karta hai.
4.  **Availability Service:** Sabhi properties ke calendars ko manage karta hai. Double-booking ko rokna iski mukhya zimmedari hai.
5.  **User Service:** User profiles aur authentication ko manage karta hai.
6.  **Messaging Service:** Host aur guest ke beech chat ko power karta hai (WebSockets ka istemal kar sakta hai).
7.  **Payment Service:** Payments ko process karta hai, guest se paise leta hai, aur check-in ke baad host ko payout manage karta hai.
8.  **Review Service:** Two-way review system ko manage karta hai.

### Core Workflow 1: Ek Guest Stay Search Kar Raha Hai

1.  Guest search karta hai: "Civil Lines, Prayagraj", "15-20 October", "2 mehmaan". Request **API Gateway** se **Search Service** ko jaati hai.
2.  Search Service apni **Elasticsearch** index par ek complex query chalaati hai:
    * **Geo Filter:** "Civil Lines, Prayagraj" ke aas-paas ke area mein saari properties dhoondho.
    * **Availability Filter:** Ab inmein se un properties ko hata do jo **Availability Service** ke anusaar 15 se 20 October ke beech kisi bhi din booked hain.
    * **Attribute Filter:** Bachi hui properties ko `MaxGuests >= 2` aur anya filters (price, amenities) ke aadhar par filter karo.
3.  Search Service in filtered `PropertyID`s ki list lautaati hai. Fir, `Listings Service` se in properties ki poori details (photos, title) mangwa kar user ko dikha di jaati hai.

### Core Workflow 2: Ek Guest Property Book Kar Raha Hai

Yeh ek critical, transactional workflow hai.

1.  Guest "Reserve" par click karta hai. Request **Booking Service** ko jaati hai.
2.  **Transaction & Lock:** Booking Service ek **DATABASE TRANSACTION** shuru karti hai.
3.  **Step 1: Double-Check Availability (Race Condition se bachav):** Booking Service, **Availability Service** ko ek final call karti hai: "Kya Property XYZ 15-20 Oct ke liye abhi bhi available hai?". Availability Service un dates par ek **temporary lock** (e.g., 10 minute ke liye `PENDING` status) laga deti hai. Agar lock fail hota hai (kyunki kisi aur ne usi second book kar liya), to user ko error dikha diya jaata hai.
4.  **Step 2: Process Payment:** Agar lock safal hota hai, to Booking Service **Payment Service** ko guest se payment lene ke liye kehti hai. Airbnb aam taur par is paise ko apne paas rakhta hai.
5.  **Step 3: Finalize Booking (Commit):**
    * Agar payment safal hota hai, to Booking Service transaction ko **COMMIT** karti hai.
    * Yeh `Bookings` table mein ek `CONFIRMED` entry banati hai.
    * Yeh **Availability Service** ko nirdesh deti hai ki woh temporary lock ko permanent **`BOOKED`** status mein badal de.
    * Ek `Booking_Confirmed` event **Message Queue (jaise Kafka)** mein daal diya jaata hai.
6.  **Asynchronous Actions:**
    * Is event ko sunkar **Notification Service** guest aur host dono ko confirmation email/SMS bhejti hai.
    * **Messaging Service** un dono ke beech ek naya message thread shuru kar deti hai.
7.  **Failure/Rollback:** Agar payment fail ho jaata hai ya lock expire ho jaata hai, to transaction **ROLLBACK** ho jaata hai aur Availability Service lock ko hata deti hai, jisse woh dates fir se available ho jaati hain.

---

# 📌 Live-Streaming App System Design

---

### ## What is a Live-Streaming App?

Ek Live-Streaming App (jaise Twitch, YouTube Live, Instagram Live) ek aisa platform hai jo users (jinhe **Streamers** ya Creators kehte hain) ko apne computer ya mobile se live video aur audio content ko internet par broadcast karne ki anumati deta hai. Doosre users (jinhe **Viewers** kehte hain) is broadcast ko real-time mein dekh sakte hain. Iska sabse zaroori hissa iski interactivity hoti hai, khaaskar **live chat** ke zariye, jisse viewers aur streamer aapas mein baat kar sakte hain.

---

### ## Problem Statement (Humein Banana Kya Hai?)

Humein ek scalable aur kam-latency wala platform design karna hai jo duniya bhar mein laakhon-karodon viewers ko high-quality live video streams pradaan kar sake.

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* Ek user (Streamer) live video broadcast shuru aur band kar sake.
* Users (Viewers) live streams ko khoj (discover) aur dekh sakein.
* Viewers ko video kam se kam delay (latency) ke saath milna chahiye.
* Har stream ke liye ek **real-time chat** uplabdh honi chahiye.
* Video stream alag-alag quality settings mein uplabdh hona chahiye (e.g., 1080p, 720p, 480p) taaki alag-alag internet speeds par chal sake.
* Stream khatm hone ke baad, use ek normal video (Video on Demand - VOD) ke roop mein save karne ka vikalp hona chahiye.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **Low Latency (Glass-to-Glass Delay):** Yeh sabse zaroori hai. Streamer ke camera mein jo ho raha hai aur viewer ki screen par jo dikh raha hai, uske beech ka samay (delay) kam se kam hona chahiye (aam taur par 5-10 seconds se kam).
* **High Scalability:** Ek single stream par laakhon concurrent viewers ho sakte hain. System ko is "fan-out" load ko handle karna aana chahiye.
* **High Availability:** Streaming infrastructure vishwasniya (reliable) honi chahiye. Stream beech mein rukni nahi chahiye.
* **Adaptive Bitrate Streaming (ABR):** Viewer ke internet connection ke aadhar par video quality automatically adjust honi chahiye taaki video ruke (buffer) nahi.

---

### ## High-Level Architecture & Core Technologies

Live streaming ka process ek pipeline jaisa hota hai. Ismein kai kadam (steps) hote hain.

#### Key Components:
1.  **Ingestion Service:** Yeh platform ka entry point hai. Streamer ka raw video stream sabse pehle yahan aata hai.
2.  **Transcoding Service:** Yeh pipeline ka sabse zaroori aur compute-intensive hissa hai. Yeh streamer se aayi ek single high-quality stream ko leta hai aur use alag-alag qualities (1080p, 720p, 480p) aur formats mein convert karta hai. Yahi ABR ko sambhav banata hai.
3.  **Stream Distribution Network (CDN):** Transcode ki hui video streams ko ek global **Content Delivery Network (CDN)** par push kiya jaata hai. CDN ke servers poori duniya mein faile hote hain.
4.  **Metadata Service:** Yeh ek normal web service hai jo baaki sab kuch handle karti hai: user profiles, stream titles, viewer count, etc. Yeh ek standard database (SQL/NoSQL) ka istemal karti hai.
5.  **Chat Service:** Ek alag, real-time service jo WebSockets ka istemal karke live chat ko power karti hai.

#### Core Protocols:
* **Ingestion Protocol (Streamer se Server tak):** **RTMP (Real-Time Messaging Protocol)** industry standard hai. Streamer ka software (jaise OBS) RTMP ka istemal karke video server ko bhejta hai.
* **Delivery Protocol (Server se Viewer tak):** **HLS (HTTP Live Streaming)** aur **DASH (Dynamic Adaptive Streaming over HTTP)** modern standards hain. Yeh video stream ko chhote-chhote (2-6 second ke) video "chunks" mein tod dete hain aur unhe normal HTTP par serve karte hain. Isse yeh behad scalable ho jaata hai aur CDN ke saath achhe se kaam karta hai.

---

### ## Core Workflow 1: The Streaming Pipeline (Streamer se Viewer tak)

Chaliye, ek streamer jo Prayagraj mein hai aur ek viewer jo Delhi mein hai, unke beech ke data flow ko dekhte hain.

1.  **Capture & Ingest:** Prayagraj mein baitha streamer apne PC par "Go Live" click karta hai. Uska software (OBS) video/audio capture karke use **RTMP** protocol ke zariye hamare sabse nazdeeki **Ingestion Server** (e.g., Mumbai mein) par bhejta hai.

2.  **Transcoding (The Video Factory):** Mumbai ka server us stream ko **Transcoding Service** ko bhejta hai. Yeh service us high-quality stream ko ek saath kai qualities mein badalti hai (1080p, 720p, etc.). Har quality ke stream ko chhote-chhote `.ts` video chunks mein toda jaata hai aur ek `playlist.m3u8` (manifest file) banayi jaati hai jismein in chunks ki list hoti hai.

3.  **Distribution (CDN par bhejna):** Yeh saare video chunks aur manifest files turant **CDN** par upload ho jaate hain.

4.  **Playback (Viewer ka Anubhav):**
    * Delhi mein baitha viewer stream par click karta hai. Uska video player sabse pehle CDN se `playlist.m3u8` manifest file request karta hai. CDN apne sabse nazdeeki server (Delhi edge server) se yeh file bhej deta hai.
    * Manifest file player ko batati hai ki kaun-kaun si qualities available hain. Player viewer ki internet speed check karta hai aur ma लीजिए 720p se shuru karne ka faisla karta hai.
    * Ab player 720p waali manifest file maangta hai, jismein 720p ke saare video chunks ki list hoti hai.
    * Player ek-ek karke in chunks ko download aur play karna shuru kar deta hai.
    * Agar viewer ka internet dheema ho jaata hai, to player agla chunk 480p waali stream se maangega. Isse video ki quality thodi kam ho jaayegi lekin woh rukega nahi. Isi ko **Adaptive Bitrate Streaming** kehte hain.

### Core Workflow 2: The Real-Time Chat System

Video pipeline se alag, chat system alag se kaam karta hai.

1.  Jab viewer stream join karta hai, to uska browser/app ek dedicated **Chat Server** ke saath ek **WebSocket connection** banata hai.
2.  Jab viewer message type karke bhejta hai, to woh WebSocket ke zariye turant Chat Server tak pahunch jaata hai.
3.  Chat Server us message ko us stream se jude **baaki sabhi viewers** ko unke respective WebSocket connections ke zariye **broadcast** kar deta hai.

Isse chat ka anubhav behad tez aur real-time rehta hai, chahe viewers laakhon mein hi kyun na hon. Chat servers ko stream ID ya channel ke aadhar par shard (baanta) jaa sakta hai.

---

# 📌 Tinder System Design

---

### ## What is Tinder?

Tinder ek location-based social discovery aur dating application hai. Iska istemal karke users apne aas-paas ke doosre users ke profiles ko like (swipe right) ya dislike (swipe left) kar sakte hain. Iski sabse badi khaasiyat iska **"double opt-in"** system hai: do users ke beech chat tabhi shuru ho sakti hai jab dono ne ek doosre ko like kiya ho. Isse ek **"match"** banta hai, jo unwanted messages ko rokta hai.

---

### ## Problem Statement (Humein Banana Kya Hai?)

Humein ek highly available aur responsive dating app design karna hai, jiska mukhya focus user ko uski pasand aur location ke aadhar par personalized recommendations dena aur mutual likes ko real-time mein match karna hai.

#### Functional Requirements (System Ko Kya-Kya Karna Chahiye?)
* User apni profile (photos, bio, interests, preferences) create aur manage kar sake.
* System ko har user ke liye unke location, age/gender preferences ke aadhar par potential matches ka ek **personalized stack (deck)** dikhana chahiye.
* User profiles par right (like) ya left (pass) swipe kar sake.
* Agar do users ek doosre ko like karte hain, to system ko turant ek **"match"** create karna chahiye aur dono ko notify karna chahiye.
* Matched users aapas mein **chat** kar sakein.

#### Non-Functional Requirements (System Ko Kaisa Perform Karna Chahiye?)
* **High Availability:** App hamesha on rehna chahiye, khaaskar peak hours (jaise weekend nights) mein.
* **Low Latency:** Profile deck ka load time aur swipe ka response time bahut kam hona chahiye. Match notification real-time mein aani chahiye.
* **Scalability:** System ko laakhon-karodon users aur pratidin (daily) arabon (billions) swipes ko handle karna aana chahiye.
* **Data Privacy & Security:** User ki location aur personal data atyant surakshit (secure) honi chahiye.

---

### ## Low Level Design (Data Models)

* **Users Table (SQL ya NoSQL - Document DB):**
    * `UserID` (PK), `Name`, `Age`, `Gender`, `Bio`
    * `Photos`: [URL1, URL2, ...] (JSON Array)
    * `LastLocation_Lat`, `LastLocation_Lon`: User ki aakhri location (geospatial queries ke liye indexed).
    * `Preferences`: { `minAge`, `maxAge`, `genderPreference`, `maxDistance` } (JSON Object).
    * `DesirabilityScore`: Ek internal score jo recommendation engine use karta hai.

* **Swipes Table (Write-heavy - NoSQL jaise Cassandra/DynamoDB):**
    * `SwiperID` (Partition Key)
    * `SwipedID` (Clustering Key)
    * `SwipeType`: (LIKE / PASS)
    * `Timestamp`
    * Yeh table behad badi hogi, isliye high write throughput wala NoSQL database iske liye perfect hai.

* **Matches Table (SQL ya NoSQL):**
    * `MatchID` (PK)
    * `User1_ID`, `User2_ID` (sorted to create a unique key, e.g., (smaller_id, larger_id))
    * `Timestamp`

* **Chat Messages Table (NoSQL jaise Cassandra):**
    * `MatchID` (Partition Key)
    * `MessageID` (Timestamp-based UUID, Clustering Key)
    * `SenderID`, `MessageText`

---

### ## Architecture and Components (System Ka Naksha)

Tinder ka system **Microservices Architecture** par chalta hai.

#### Key Microservices
1.  **User Service:** User profiles (CRUD operations) ko manage karta hai.
2.  **Recommendation Service (System ka "Dimaag"):** Har user ke liye personalized profile deck generate karta hai.
3.  **Swipe Service:** User ke swipes ko record karne wala ek high-throughput service.
4.  **Match Service:** Mutual likes ko detect karke match create karta hai.
5.  **Chat Service:** Matched users ke beech real-time chat ko power karta hai (WebSockets ka istemal karke).

### Core Workflow 1: Profile Deck Generate Karna (Recommendations)

Yeh sabse zaroori aur computationally intensive kaam hai. Ek live DB query ("mere 10km ke daayre mein 25-30 saal ke sabhi users dikhao jinhe maine swipe nahi kiya hai") bahut dheemi hogi. Isliye, yeh process **asynchronously (background mein)** hota hai.

1.  **Offline Pre-computation:** Ek **background worker** har active user ke liye recommendations ko pehle se hi compute karke ek **Cache (jaise Redis)** mein store kar deta hai.
    * **Key:** `UserID`
    * **Value:** A list of recommended `UserID`s [ID_X, ID_Y, ID_Z, ...]

2.  **Yeh Worker Kaam Kaise Karta Hai?**
    * **Step A (Geo-Spatial Query):** Sabse pehle, yeh ek specialized database (jismein geospatial index ho, jaise PostGIS ya Elasticsearch) se user ke `maxDistance` ke andar aane waale sabhi users ko nikalta hai.
    * **Step B (Filtering):** Is list ko user ki `Preferences` (age, gender) ke aadhar par filter kiya jaata hai. Un logon ko bhi hata diya jaata hai jin par user pehle hi swipe kar chuka hai.
    * **Step C (Ranking):** Bachi hui profiles ko kai factors ke aadhar par **rank** kiya jaata hai—jaise `DesirabilityScore`, user ki activity, common interests, etc.
    * **Step D (Caching):** Top N (e.g., 200) ranked profiles ki ID ko Redis mein store kar diya jaata hai.

3.  **Serving the Deck:** Jab user app kholta hai, to client **Recommendation Service** se deck maangta hai. Service ko bas **Redis se pre-computed list** nikalni hoti hai, jo behad tez hai. Fir woh list mein se pehle 10-20 profiles ki poori details `User Service` se mangwa kar client ko bhej deti hai.

### Core Workflow 2: Swiping aur Real-Time Matching

1.  User A, User B ki profile par **right swipe** karta hai. App `(Swiper: A, Swiped: B, Type: LIKE)` ka event **Swipe Service** ko bhejta hai.

2.  Swipe Service do kaam karti hai:
    a. Is swipe ko `Swipes` database mein likhti hai (persistence ke liye).
    b. Saath hi, is event ko ek **Message Queue (jaise Kafka ya SQS)** mein publish karti hai.

3.  **Match Service** is Message Queue ko sun rahi hoti hai. Use `A -> LIKE -> B` ka event milta hai.

4.  **The Magic Check:** Match Service turant `Swipes` database mein ek ulta (reverse) lookup karti hai: **"Kya B ne kabhi A ko LIKE kiya hai?"** (`SELECT 1 FROM Swipes WHERE SwiperID='B' AND SwipedID='A' AND SwipeType='LIKE'`). Yeh query behad fast hoti hai kyunki database iske liye optimized hota hai.

5.  **Scenario 1: No Match:** Agar B ne A ko like nahi kiya hai, to kuch nahi hota. Process yahin khatm ho jaata hai.

6.  **Scenario 2: It's a Match!**
    * Agar B ne A ko pehle hi like kiya hua hai, to yeh ek match hai!
    * **Match Service**, `Matches` table mein ek nayi entry create karti hai.
    * Iske baad, woh ek **Notification Service** (jaise Firebase Cloud Messaging) ko bolti hai ki User A aur User B dono ke devices par push notification bheje: **"It's a Match!"**.
    * Yeh poora process kuch hi milliseconds mein ho jaata hai, jisse user ko instant experience milta hai.

---