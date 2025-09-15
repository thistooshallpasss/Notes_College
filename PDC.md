## Concurrent Programming ka Introduction

### Q: Concurrent programming kya hai aur iski zaroorat kyun hai?

**Answer**:
Concurrent programming ek aisi technique hai jismein ek bade problem ko chhote-chhote, **independent** (azaad) hisson mein toda jaata hai, taaki unhe alag-alag order mein ya ek saath chalaya ja sake.

Iski zaroorat isliye hai kyunki aajkal ke processors **multicore** hain (matlab ek chip mein kai CPUs). Purane (serial) program ek baar mein ek hi core istemal karte the. Apne software ki performance badhane ke liye aur in saare cores ka fayda uthane ke liye, hamein concurrent program likhne padte hain. Isse applications tezi se chalti hain. Ise **parallelization** bhi kehte hain.

### Q: "Thread Monkey" kise kehte hain?

**Answer**:
"Thread Monkey" ek aise skilled programmer ko kehte hain jo multithreaded, concurrent, aur parallel software ko design bhi kar sakta hai aur uske liye aacha, aasan aur aasan se chalne waala (efficient) code bhi likh sakta hai. Yeh ek tareef waala title hai, "code monkey" ki tarah negative nahi hai.

---

## Concurrency vs. Parallelism ka Faraq

### Q: Concurrency aur Parallelism mein kya antar (difference) hai?

**Answer**:
Yeh dono terms aksar ek jaise istemal hote hain, lekin inmein ek ahem (important) faraq hai:

* **Concurrency (Ek Saath Progress Mein):** Ek system concurrent tab hota hai jab woh ek hi samay par do ya do se zyada kaam ko **'in progress'** rakh sakta hai. Yeh single-core processor par bhi ho sakta hai, jahan Operating System tezi se alag-alag tasks ke beech switch karta hai. Aisa lagta hai ki kaam ek saath ho raha hai, par asal mein ek time par ek hi kaam hota hai.
    * **Example**: Aap ek hi browser window mein music sun rahe hain aur article padh rahe hain.

* **Parallelism (Ek Saath Chalna):** Ek system parallel tab hota hai jab woh ek hi samay par do ya do se zyada kaam ko **'simultaneously'** (sach mein ek saath) execute kar sakta hai. Iske liye hamesha **multiple cores** ki zaroorat hoti hai.
    * **Example**: Ek video editing software jo ek core par video render kar raha hai aur doosre core par audio process kar raha hai.

**Mukhya (Main) Point**: Har parallel system concurrent hota hai, lekin har concurrent system ka parallel hona zaroori nahi hai. Parallelism, concurrency ka hi ek subset hai.

---

## Performance aur Scalability

### Q: Concurrent programming se performance kitni behtar ho sakti hai?

**Answer**:
Theoretically, agar aapke paas 2 cores hain, toh application aadhe time mein chal sakti hai; 4 cores par, chauthai (one-fourth) time mein, aur isi tarah aage bhi. Yeh naye, tez processor se milne waale 20-30% improvement se kahin zyada behtar hai.

Lekin, hakeekat mein aisa 'perfect' speed-up haasil karna mushkil hai.

### Q: Scalability kya hai aur ismein kya challenges aate hain?

**Answer**:
Scalability ka matlab hai ki aapka concurrent program cores ki sankhya badhne par bhi utna hi accha performance de. Yaani, agar 2 se 4 core karne par performance double hui, toh 4 se 8 core karne par bhi double honi chahiye.

**Challenges**:
* **Overhead**: Threads banane, manage karne aur unhe synchronize karne mein extra time lagta hai, jise overhead kehte hain.
* **Synchronization**: Jab kai threads ek hi data ko access karte hain, toh unhe aapas mein coordinate karna padta hai, jisse program slow ho sakta hai.
* **Load Imbalance**: Agar ek thread ko bahut zyada kaam mil jaye aur doosre idle baithe rahein, toh multiple cores ka fayda nahi milta.

---

## Concurrent Programming ki Mushkilein aur Galtiyan (Bugs)

### Q: Kya concurrent programming sach mein mushkil hai?

**Answer**:
Yeh aasan nahi hai, par itni bhi डरावनी (scary) nahi hai jitna log sochte hain. Agar aap ise aaram se samajh kar karein, toh yeh ek nayi programming language seekhne jaisa hai. Iske liye logical soch ki zaroorat hoti hai, taaki aap imagine kar sakein ki kai threads ek saath kaise chalenge.

### Q: Concurrent programs mein serial programs se alag kis tarah ke bugs aate hain?

**Answer**:
Serial programs mein bugs ko dhundhna aasan hota hai kyunki code hamesha ek hi predictable raaste se chalta hai. Lekin concurrent programs mein **nondeterministic** (jiska anumaan na lagaya ja sake) nature ki wajah se naye tarah ke bugs aate hain:

1.  **Data Race**: Jab do ya do se zyada threads ek hi memory location ko ek saath access karne ki koshish karte hain, aur unmein se kam se kam ek thread us data ko **update** (write) kar raha ho. Isse galat results aa sakte hain.
    * **Example**: Do travel agent ek hi khali seat ko ek hi time par do alag-alag logon ko book kar dein.

2.  **Deadlock**: Jab do ya do se zyada threads ek doosre ka intezaar karte rehte hain aur koi bhi aage nahi badh paata.

3.  **Heisenbug**: Yeh aise bugs hote hain jo sirf kabhi-kabhi dikhte hain. Ek run mein program sahi chalega, doosre mein fail ho jayega. Inhe debug karna bahut mushkil hota hai kyunki debugger lagane se threads ka timing badal jaata hai aur bug gayab ho jaata hai.

---

## Threads istemal karne ke Fayde aur Nuksaan

### Q: Kya Threads istemal karna khatarnak (dangerous) hai?

**Answer**:
Haan aur na. Threads isliye khatarnak ho sakte hain kyunki:
* **Shared Memory Issues**: Saare threads ek hi memory share karte hain. Agar aache se manage na kiya jaye, toh data race jaise problems ho sakti hain.
* **Synchronization Problems**: Threads ko synchronize karne waale tools (jaise locks) agar galat istemal kiye jayein, toh deadlock ya performance issues aa sakte hain.

Lekin, threads abhi yahan hain aur aage bhi rahenge. Multicore processors ka poora fayda uthane ke liye yeh zaroori hain. Agar aapko iske khatron ke baare mein pata ho, toh aap unse bachne ke liye aacha code likh sakte hain.

---

## Code ko Concurrent Banane ke Steps (Threading Methodology)

### Q: Ek serial application ko concurrent banane ke 4 steps kya hain?

**Answer**:
Ek serial code ko aache se concurrent banane ke liye yeh 4-step methodology follow ki jaati hai:

1.  **Analysis (Vishleshan)**: Sabse pehle, application ke code mein un "hotspots" ko pehchano jahan sabse zyada time lagta hai. Fir analyse karo ki kya un hisson mein kaam ko azaad (independent) tukdon mein baanta ja sakta hai.

2.  **Design and Implementation (Design aur Code karna)**: Jab aapne independent kaam pehchan liya, toh ek concurrent design banao. Ismein decide karo ki kaam threads mein kaise baantna hai, data kaise share hoga, aur synchronization ki zaroorat kahan padegi. Fir is design ko code karo.

3.  **Test for Correctness (Sahi Chalne ki Jaanch)**: Threading add karne ke baad, aache se test karo ki program abhi bhi sahi results de raha hai ya nahi. Data race aur deadlock jaise threading errors ko dhundo aur theek karo.

4.  **Tune for Performance (Performance Behtar Karna)**: Jab program sahi se chalne lage, toh uski performance ko tune karo. Dekho ki kahin synchronization ki wajah se bottleneck toh nahi aa raha, ya threads ke beech kaam theek se balance hai ya nahi.

Yeh ek **cycle** hai. Performance theek karte waqt ho sakta hai aap koi naya bug daal dein, isliye aapko baar-baar Test aur Tune steps ke beech ghumna pad sakta hai.

---

## Parallel Algorithm Design ke Moolbhoot Siddhant (Basic Principles)

### Q: Sequential aur Parallel Algorithm mein kya fark hai?

**Answer**:
Ek **sequential algorithm** ek recipe jaisa hai jo batata hai ki ek serial computer (single processor) par problem ko solve karne ke liye steps ka sequence kya hoga Wahin, ek **parallel algorithm** batata hai ki ek hi problem ko multiple processors ka istemal karke kaise solve kiya jaaye Ismein sirf steps hi nahi, balki yeh bhi batana zaroori hota hai ki kaun se steps ek saath (concurrently) chal sakte hain

Ek parallel algorithm design karne mein aam taur par yeh shaamil hota hai:
* Kaam ke un hisson ko pehchan'na jo ek saath ho sakte hain
* Un concurrent hisson ko alag-alag processes par **map** karna
* Input, output, aur intermediate data ko distribute karna
* Shared data ke access ko manage karna
* Processors ko execution ke alag-alag stages par **synchronize** karna

---

## Decomposition: Kaam ko Baantna

### Q: Decomposition kya hai? Tasks aur Task-Dependency Graph se aap kya samajhte hain?

**Answer**:
* **Decomposition**: Yeh ek process hai jismein ek badi computation ko chhote-chhote hisson mein baanta jaata hai, jinhein **tasks** kehte hain. In tasks ko aage aur nahi toda jaa sakta Ek saath kai tasks ko execute karne se hi problem solve karne ka time kam hota hai
* **Tasks**: Yeh computation ki programmer-defined units hain Inka size chhota ya bada ho sakta hai Jaise, matrix-vector multiplication mein, product vector ke har element ki calculation ek alag task ho sakti hai
* **Task-Dependency Graph**: Yeh ek directed graph hota hai jo tasks ke beech dependencies (nirbharta) dikhata hai
    * **Nodes** tasks ko represent karte hain
    * **Directed edges** (teer) dikhate hain ki ek task doosre par nirbhar hai
    * Koi bhi task tabhi execute ho sakta hai jab uski saari incoming dependencies (jin tasks ke teer uski taraf aa rahe hain) poori ho chuki hon
    * **Example**: Database query mein, "Civic" aur "2001" model cars ki tables banane ke baad hi unka intersection (2001 Civics) nikalne wala task shuru ho sakta hai


---

## Granularity, Concurrency, aur Critical Path

### Q: Granularity aur Degree of Concurrency ka kya matlab hai?

**Answer**:
* **Granularity**: Yeh batata hai ki problem ko kitne aur kis size ke tasks mein toda gaya hai
    * **Fine-grained**: Jab problem ko bahut saare chhote-chhote tasks mein toda jaata hai
    * **Coarse-grained**: Jab problem ko kam sankhya mein bade-bade tasks mein toda jaata hai
* **Degree of Concurrency**: Yeh batata hai ki kisi bhi samay par kitne tasks ek saath chal sakte hain.
    * **Maximum Degree of Concurrency**: Kisi bhi samay par ek saath chal sakne wale tasks ki adhiktam (maximum) sankhya
    * **Average Degree of Concurrency**: Poore program ke execution ke dauran, average kitne tasks concurrently chal sakte hain Finer granularity se aam taur par concurrency badhti hai

### Q: Critical Path kya hota hai aur iska kya mahatva hai?

**Answer**:
Ek task-dependency graph mein, **critical path** kisi bhi start node (jiska koi incoming edge na ho) se kisi bhi finish node (jiska koi outgoing edge na ho) tak ka sabse lamba directed path hota hai.

* **Critical Path Length**: Is path par aane wale sabhi tasks ke kaam (weight) ka jod (sum) hota hai
* **Mahatva (Importance)**: Yeh parallel execution mein lagne wale minimum time ko tay karta hai. Critical path jitna chhota hoga, average degree of concurrency utni hi zyada hogi. Average degree of concurrency ka formula hai: (Total work) / (Critical path length)

---

## Tasks ka Aapas mein Interaction aur Mapping

### Q: Task-Interaction Graph kya hota hai?

**Answer**:
Yeh graph dikhata hai ki kaun se tasks aapas mein interact karte hain (data share karte hain)
* Ismein bhi **nodes** tasks ko represent karte hain
* **Edges** un tasks ko jodte hain jo aapas mein interact karte hain
* Task-interaction graph ka edge-set aam taur par task-dependency graph ke edge-set ka **superset** hota hai Aisa isliye kyunki jo tasks ek doosre par nirbhar nahi hain, woh bhi data share kar sakte hain.

### Q: Mapping kya hai aur Process aur Processor mein kya antar hai?

**Answer**:
* **Mapping**: Yeh woh tarika hai jisse tasks ko execution ke liye processes ko assign kiya jaata hai Ek achhi mapping ke teen mukhya lakshya (goals) hote hain
    1.  Independent tasks ko alag-alag processes par map karke **concurrency ko badhana**.
    2.  Processes ke beech **interaction ko kam karna**.
    3.  Critical path par maujood tasks ko jaldi se jaldi execute karke **total completion time ko kam karna**.
* **Processes vs. Processors**:
    * **Processors** physical hardware units hote hain jo asal mein computation karte hain
    * **Processes** logical computing agents hote hain jo tasks ko perform karte hain Aam taur par, hum ek process ko ek processor ke barabar maan sakte hain, lekin alag-alag sochna aasan rehta hai, khaas kar complex algorithms ke liye.

---

## Decomposition Techniques

### Q: Parallel algorithms banane ke liye kaun-kaun si mukhya decomposition techniques hain?

**Answer**:
Chaar mukhya decomposition techniques hain:

1.  **Recursive Decomposition**:
    * Yeh "divide-and-conquer" strategy par aadharit problems ke liye use hoti hai
    * Problem ko independent subproblems mein toda jaata hai, aur unhe recursively solve kiya jaata hai.
    * **Example**: Quicksort algorithm, jismein ek list ko pivot ke aadhar par do choti lists mein baanta jaata hai aur fir unhe alag-alag sort kiya jaata hai.

2.  **Data Decomposition**:
    * Yeh technique bade data structures par kaam karne wale algorithms ke liye bahut powerful hai
    * Ismein pehle data ko partition kiya jaata hai, aur fir us data partition ke aadhar par computations ko tasks mein baanta jaata hai
    * Data partition karne ke kai tarike ho sakte hain
        * **Output Data Partitioning**: Har task output data ke ek hisse ko compute karne ke liye responsible hota hai. Jaise matrix multiplication mein, output matrix C ke har block ko ek alag task calculate kar sakta hai.
        * **Input Data Partitioning**: Jab output ko partition karna aasan na ho (jaise kisi list ka minimum element dhundhna), tab input data ko partition kiya jaata hai.
        * **Intermediate Data Partitioning**: Kai baar, input ya output ke bajaye algorithm ke kisi beech ke stage mein banne wale data ko partition karke zyada concurrency mil sakti hai.

3.  **Exploratory Decomposition**:
    * Yeh un problems ke liye istemal hoti hai jahan solution ek search space mein dhundhna hota hai.
    * Ismein search space ko chhote-chhote hisson mein baant kar har hisse ko concurrently search kiya jaata hai.
    * **Example**: 15-puzzle problem, jahan initial state se alag-alag possible moves ko alag-alag tasks explore karte hain jab tak solution na mil jaye. Jaise hi ek task ko solution milta hai, woh baaki tasks ko rok sakta hai.

4.  **Speculative Decomposition**:
    * Yeh un situations mein use hota hai jahan program ka agla step pichle computation ke result par nirbhar karta hai.
    * Ismein, result aane se pehle hi, program ke possible future branches (raaston) ko parallel mein execute karna shuru kar diya jaata hai.
    * Jab aakhir mein sahi branch ka pata chalta hai, toh us branch ke result ko use kar liya jaata hai aur baaki branches ke kaam ko discard kar diya jaata hai. Isse kuch computation waste zaroor hoti hai.
    * **Example**: Discrete event simulation.

In techniques ko akele ya ek saath (hybrid decomposition) bhi istemal kiya jaa sakta hai.

---

## Load Balancing ke liye Mapping Techniques

### Q: Static aur Dynamic Mapping mein kya antar hai?

**Answer**:
Mapping ka mukhya uddeshya (objective) processes par kaam ka bojh (workload) balance karna hai taaki koi process idle na baithe. Iske liye do tarah ki mapping hoti hai:

* **Static Mapping**:
    * Ismein tasks ko algorithm ke execution se **pehle** hi processes par distribute kar diya jaata hai.
    * Yeh tabhi aacha kaam karti hai jab tasks pehle se pata hon (statically generated) aur unka size bhi anumaanit ho.
    * **Schemes**:
        * **Array Distribution**: Block, Cyclic, Block-Cyclic, aur Randomized block distributions.
        * **Graph Partitioning**: Mesh jaise irregular data structures ko is tarah partition karna ki har process ko lagbhag barabar kaam mile aur communication kam se kam ho.

* **Dynamic Mapping (Dynamic Load Balancing)**:
    * Ismein kaam ko algorithm ke execution ke **dauran** (at runtime) processes mein baanta jaata hai.
    * Yeh tab zaroori hai jab tasks dynamically generate hote hain ya unka size anumaanit nahi hota.
    * **Schemes**:
        * **Centralized**: Ek master process kaam ka pool maintain karta hai aur idle slave processes ko kaam deta hai.
        * **Distributed**: Sabhi processes aapas mein kaam exchange karke workload balance karte hain.

---

## Interaction Overheads ko Kam Karne ke Tarike

### Q: Processes ke beech interaction overheads ko kaise kam kiya jaa sakta hai?

**Answer**:
Interaction overheads ko kam karna ek aache parallel program ke liye bahut zaroori hai. Iske kuch pramukh (main) tarike hain:

1.  **Maximizing Data Locality**: Jitna ho sake, local data ka istemal karein taaki nonlocal data ko access karne ki zaroorat kam pade. Isse data exchange ka volume kam hota hai.
2.  **Minimizing Contention and Hot Spots**: Aisi situations se bachein jahan kai processes ek hi samay par ek hi resource (jaise memory block) ko access karne ki koshish karein .
3.  **Overlapping Computations with Interactions**: Jab ek process data ka intezaar kar raha ho, us waiting time mein koi aur useful computation kar le. Iske liye non-blocking communication ya hardware prefetching ki zaroorat pad sakti hai.
4.  **Replicating Data or Computations**: Agar kai processes ko ek hi read-only data ki baar-baar zaroorat padti hai, toh us data ki ek copy har process par replicate kar dena behtar ho sakta hai.
5.  **Using Optimized Collective Interaction Operations**: Broadcast ya reduction jaise common communication patterns ke liye pehle se optimized library functions (jaise MPI mein) ka istemal karein.

---

## Parallel Programs ki Performance ko Samjhna

### Q: Parallel programs ki performance ko aache se model karna kyun zaroori hai?

**Answer**:
Ek sequential (normal) program ki performance sirf uske execution time se naapi jaati hai. Lekin, ek parallel program ki performance **input size**, **processors ki sankhya (number of processing elements)**, aur unke beech **communication speed** jaise kai factors par nirbhar karti hai.

Sirf wall-clock time dekhna kaafi nahi hai kyunki woh alag-alag problem size ya zyada processors par performance aacha hoga ki nahi, yeh nahi bata sakta. Isliye, humein aache analytical models aur metrics ki zaroorat padti hai taaki hum:
* Alag-alag parallel algorithms ko compare kar sakein.
* Hardware platforms ko evaluate kar sakein.
* Parallelism se hone wale asli fayde ko samajh sakein.

### Q: Parallel programs mein performance kam hone (overhead) ke mukhya (main) kaaran kya hain?

**Answer**:
Aadarsh roop se (Ideally), 2 processors lagane par program ko 2 guna tez chalna chahiye, lekin aisa hota nahi hai. Iske peeche kuch overheads hote hain:

1.  **Interprocess Interaction (Communication)**: Jab alag-alag processors ko aapas mein data (jaise intermediate results) share karna padta hai, toh is communication mein time lagta hai. Yeh aksar sabse bada overhead hota hai.
2.  **Idling (Processor ka khaali baithna)**: Processors kai kaarano se khaali (idle) baith sakte hain:
    * **Load Imbalance**: Agar ek processor ko zyada kaam mil gaya aur doosre ko kam, toh jiska kaam jaldi khatam ho gaya woh idle baitha rahega.
    * **Synchronization**: Kai baar, sabhi processors ko ek point par aakar ek doosre ka intezar karna padta hai. Jo pehle pahunch jaate hain, woh baakiyon ka wait karte hue idle rehte hain.
    * **Serial Components**: Agar program ka koi hissa parallel nahi ho sakta, toh usse sirf ek processor chalayega aur baaki sab idle rahenge.
3.  **Excess Computation**: Kai baar, sabse tez sequential algorithm ko parallel karna mushkil hota hai. Isliye, hum ek aise algorithm ka istemal karte hain jo parallel toh aacha ho jaata hai, lekin total kaam (computation) best sequential algorithm se zyada karta hai. Is extra kaam ko excess computation overhead kehte hain.

---

## Performance ko Naapne ke Tarike (Metrics)

### Q: Execution Time, Total Parallel Overhead, Speedup, aur Efficiency kya hote hain?

**Answer**:
Yeh parallel performance ko naapne ke liye sabse zaroori metrics hain:

* **Execution Time**:
    * **Serial Runtime ($T_S$)**: Program ko ek single processor par chalne mein laga total samay.
    * **Parallel Runtime ($T_P$)**: Parallel computation shuru hone se lekar aakhiri processor ke apna kaam khatam karne tak laga samay.

* **Total Parallel Overhead ($T_o$)**:
    * Yeh woh saara samay hai jo saare processors ne milakar "waste" kiya (yaani, communication, idling, aur excess computation mein lagaya).
    * **Formula**: $T_o = pT_P - T_S$ (jahan 'p' processors ki sankhya hai).

* **Speedup (S)**:
    * Yeh batata hai ki parallel version, sequential version se kitna guna tez hai.
    * **Formula**: $S = \frac{T_S}{T_P}$
    * **Zaroori Niyam**: Speedup calculate karte waqt, $T_S$ hamesha **best known sequential algorithm** ka runtime hona chahiye.
        * **Example**: Agar bubble sort (serial) 150 sec leta hai aur quicksort (serial) 30 sec leta hai, aur aapka parallel bubble sort 4 processors par 40 sec leta hai. Toh speedup $150/40 = 3.75$ **nahi** hoga. Sahi speedup $30/40 = 0.75$ hoga, kyunki quicksort behtar sequential algorithm hai.

* **Efficiency (E)**:
    * Yeh batata hai ki processors kitne prabhavi dhang se (effectively) istemal ho rahe hain. Yeh 0 aur 1 ke beech ki value hoti hai.
    * **Formula**: $E = \frac{S}{p}$
    * **Matlab**: Ideal case mein, $p$ processors par Speedup $p$ hona chahiye aur Efficiency 1 (ya 100%). Efficiency batata hai ki har processor apna kitna time useful kaam mein laga raha hai.

### Q: Superlinear Speedup kya hota hai? Kya speedup processors ki sankhya se zyada ho sakta hai?

**Answer**:
Theoretically, speedup processors ki sankhya ($p$) se zyada nahi ho sakta. Lekin, kabhi-kabhi **superlinear speedup** (jab $S > p$) dekhne ko milta hai. Iske do mukhya kaaran ho sakte hain:

1.  **Cache Effects**: Jab ek badi problem ko ek processor par solve karte hain, toh data uske cache mein fit nahi ho pata, jisse slow memory (DRAM) access badh jaata hai. Jab usi problem ko kai processors mein baant diya jaata hai, toh har processor ke hisse ka data uske apne cache mein aaram se fit ho jaata hai. Isse cache hit rate badhti hai aur har processor bahut tez kaam karta hai, jisse overall speedup $p$ se zyada ho jaata hai.
2.  **Exploratory Decomposition**: Search karne waale algorithms mein, ek serial algorithm shayad poora search space explore karega solution dhundhne ke liye. Lekin, parallel version mein, alag-alag processors alag-alag hisse search karte hain. Ho sakta hai ki ek processor shuru mein hi solution dhundh le. Is case mein, parallel algorithm ne serial algorithm se bahut kam kaam karke solution nikal liya, jisse speedup superlinear ho gaya.

### Q: Cost aur Cost-Optimal parallel system ka kya matlab hai?

**Answer**:
* **Cost**: Yeh parallel mein problem solve karne ka kul kharch (processor-time product) hai.
    * **Formula**: Cost = $p \times T_P$
* **Cost-Optimal System**: Ek parallel system ko cost-optimal tab kaha jaata hai jab uska parallel cost, best sequential algorithm ke runtime ($T_S$) ke barabar (asymptotically) ho.
    * **Matlab**: $p \times T_P = \Theta(T_S)$.
    * Ek cost-optimal system ki efficiency $\Theta(1)$ hoti hai. Yeh batata hai ki aap processors ko bahut aache se istemal kar rahe hain bina zyada overhead ke. Jo system cost-optimal nahi hai, woh bade problems par aacha scale nahi karega.

---

## Scalability: Performance ko Scale Karna

### Q: Ek parallel system "scalable" kab kehlata hai?

**Answer**:
Ek parallel system **scalable** tab kehlata hai jab hum processors ki sankhya ($p$) badhane par bhi uski **efficiency ko constant** (ya high) rakh sakte hain, bas shart yeh hai ki humein problem size ($W$) ko bhi uske anusaar badhana hoga.

* Agar hum problem size fix rakhein aur processors badhate jaayein, toh efficiency hamesha kam hogi.
* Agar hum processors fix rakhein aur problem size badhayein, toh scalable systems mein efficiency badhti hai.

Scalability yeh naapti hai ki ek system badhte hue processing resources ka kitna aacha fayda utha sakta hai.

### Q: Isoefficiency Function kya hai aur yeh scalability ke baare mein kya batati hai?

**Answer**:
**Isoefficiency Function** ek mathematical function hai jo batata hai ki efficiency ko constant rakhne ke liye, problem size ($W$) ko processors ki sankhya ($p$) ke saath kis rate se badhana padega.

* **Matlab**: Yeh `W` aur `p` ke beech ka relation hai jo $E = \text{constant}$ par nikalta hai. Iska formula `W = K * To(W,p)` se derive hota hai, jahan `K` efficiency par depend karne wala ek constant hai.
* **Scalability ka Pata Kaise Chalta Hai?**
    * **Chhota (Small) Isoefficiency Function** (jaise $\Theta(p)$ ya $\Theta(p \log p)$): Iska matlab hai ki problem size ko thoda sa badhane par hi hum bahut saare naye processors ko aache se istemal kar sakte hain. Aise systems **highly scalable** hote hain.
    * **Bada (Large) Isoefficiency Function** (jaise $\Theta(p^2)$ ya $\Theta(2^p)$): Iska matlab hai ki efficiency maintain karne ke liye problem size ko bahut tezi se badhana padega. Aise systems **poorly scalable** hote hain.
---

## Shared Address Space Programming aur Threads

### Q: Shared Address Space programming model kya hai aur ismein Threads ki kya bhumika (role) hai?

**Answer**:
**Shared Address Space** ek parallel programming model hai jahan sabhi processors ek common memory ko access kar sakte hain. Is model mein, processors ke beech communication **implicitly** (apne aap) ho jaata hai, kyunki ek processor dwara memory mein likha gaya data doosre processors ko seedhe available hota hai.

Is model mein, **Threads** programming ka sabse pasandida tarika hai.

  * **Thread kya hai?** Ek thread ek program ke andar control ka ek single stream hota hai. Yeh ek lightweight process jaisa hai jo doosre threads ke saath memory share karta hai.
  * **Logical Memory Model**: Threads ke model mein, saari memory sabhi threads ke liye **globally accessible** maani jaati hai. Lekin, har thread ka apna ek **private stack** hota hai, jo function calls aur local variables ke liye use hota hai. Isliye, ek thread ke stack variables ko doosre threads se share karna aacha practice nahi maana jaata.

### Q: Message Passing ke mukable Threads istemal karne ke kya fayde hain?

**Answer**:
Threads istemal karne ke message-passing par kai fayde hain:

  * **Software Portability**: Threaded applications ko serial machines par develop karke bina kisi badlav ke parallel machines par chalaya ja sakta hai.
  * **Latency Hiding**: Ek processor par multiple threads chala kar memory access ya I/O mein lagne wale time (latency) ko chhupaya ja sakta hai. Jab ek thread wait kar raha hota hai, toh doosra thread CPU ko istemal kar sakta hai, jisse overhead kam ho jaata hai.
  * **Scheduling and Load Balancing**: Programmer bahut saare concurrent tasks (threads) bana sakta hai, aur system unhe processors par dynamically map karke load balance kar sakta hai. Isse programmer ko explicit scheduling ki chinta nahi karni padti.
  * **Ease of Programming**: Upar diye gaye faydo ke kaaran, threaded programs likhna message-passing programs se kaafi aasan hota hai.

-----

## POSIX Threads (Pthreads) API - Kaam Karne ka Tarika

### Q: Pthreads mein ek naya Thread kaise banate (create) aur khatam (terminate) karte hain?

**Answer**:
**POSIX Threads** ya **Pthreads** ek standard API hai jo threads banane aur manage karne ke liye istemal hota hai.

  * **Thread Creation (`pthread_create`)**:
    Naye threads banane ke liye `pthread_create` function ka istemal hota hai. Yeh function ek naya thread banata hai jo diye gaye function (`thread_function`) ko execute karta hai. Iske mukhya parameters hain:

      * `thread_handle`: Naye bane thread ki unique ID store karne ke liye.
      * `attribute`: Thread ke attributes (jaise scheduling policy) set karne ke liye. NULL dene par default attributes use hote hain.
      * `thread_function`: Woh function jise naya thread execute karega.
      * `arg`: `thread_function` ko pass karne ke liye argument.

  * **Thread Termination (`pthread_join`)**:
    Main program ko kisi thread ke khatam hone ka intezar karwane ke liye `pthread_join` function ka istemal hota hai. Yeh function call karne wale thread (jaise main thread) ko tab tak rok deta hai jab tak di gayi ID wala thread apna kaam poora na kar le.

### Q: Race Condition aur Critical Section kya hote hain? Example ke saath samjhaiye.

**Answer**:

  * **Race Condition**: Yeh ek aisi anchaahi (undesirable) situation hai jab multiple threads ek hi shared data ko ek saath access aur manipulate karne ki koshish karte hain, aur program ka final result is baat par depend karta hai ki kaun sa thread pehle chala. Isse non-deterministic (har baar alag) aur galat results aa sakte hain.

      * **Example**: Maan lijiye do threads ek shared variable `best_cost` (initial value 100) ko update kar rahe hain. Thread 1 ka local cost 50 hai, aur Thread 2 ka 75. Agar dono ek saath `if (my_cost < best_cost)` condition check karte hain, toh dono hi condition ko 'true' paayenge aur `best_cost` ko update karne ki koshish karenge. Aakhir mein `best_cost` ki value 50 ya 75 kuch bhi ho sakti hai, jo ki galat hai.

  * **Critical Section**: Code ka woh hissa jo shared data ko access ya modify karta hai aur jise ek samay par sirf ek hi thread dwara execute kiya jaana chahiye, use critical section kehte hain. Upar diye gaye example mein `if...best_cost = my_cost;` wala block ek critical section hai.

### Q: Synchronization ke liye Pthreads mein kaun-kaun se tools (primitives) hain?

**Answer**:
Race conditions se bachne aur critical sections ko protect karne ke liye Pthreads kai synchronization primitives provide karta hai:

1.  **Mutex Locks (Mutual Exclusion)**:

      * Mutex ek lock jaisa hota hai jiske do states hote hain: **locked** aur **unlocked**.
      * Critical section mein ghusne se pehle, ek thread ko mutex **lock** karna padta hai. Ek samay par sirf ek hi thread mutex ko lock kar sakta hai.
      * Agar koi doosra thread ussi mutex ko lock karne ki koshish karta hai, toh woh **block** ho jaata hai (intezar karta hai).
      * Jab pehla thread critical section se bahar nikalta hai, toh woh mutex ko **unlock** kar deta hai, jisse koi doosra waiting thread use lock kar sake.

2.  **Condition Variables**:

      * Yeh threads ko kisi khaas condition ke poora hone tak efficiently wait karwane ka tarika hai, bina baar-baar check (polling) kiye.
      * Ek thread mutex lock karke condition check karta hai. Agar condition false hai, toh woh `pthread_cond_wait` call karta hai. Yeh function thread ko block kar deta hai aur mutex ko automatically **unlock** kar deta hai taaki doosre threads shared data ko modify kar sakein.
      * Jab koi doosra thread us condition ko true kar deta hai, toh woh `pthread_cond_signal` ya `pthread_cond_broadcast` call karke waiting thread(s) ko jagaata (wake up) hai.

### Q: False Sharing kya hai aur isse performance par kya asar padta hai?

**Answer**:
**False Sharing** ek bahut gambhir (serious) performance problem hai jo shared address space systems mein hota hai.

  * **Yeh Kab Hota Hai?** Yeh tab hota hai jab do alag-alag threads, jo alag-alag processors par chal rahe hain, alag-alag data items par kaam kar rahe hote hain, lekin woh data items ittefaq se **ek hi cache line** par maujood hote hain.
  * **Problem Kya Hai?** Jab ek processor apne data item ko update (write) karta hai, toh cache coherence protocol ke kaaran poori cache line doosre processor ke cache mein **invalidate** ho jaati hai. Jab doosra processor apne data ko access karna chahta hai, toh use woh poori cache line memory se ya pehle processor ke cache se dobara fetch karni padti hai.
  * **Asar (Impact)**: Agar dono threads baar-baar apne-apne data ko update karte hain, toh woh cache line processors ke beech ping-pong ki tarah "bounce" karti rehti hai. Isse bahut saari mehengi (expensive) memory traffic generate hoti hai aur program speedup ke bajaye **slowdown** ho jaata hai.

-----

## Pthreads mein Advanced Synchronization

### Q: Read-Write Locks kya hote hain aur inka istemal kab karna chahiye?

**Answer**:
**Read-Write Lock** ek special tarah ka lock hai jo normal mutex se behtar performance de sakta hai. Yeh is principle par kaam karta hai ki multiple threads ek hi data ko ek saath **read** kar sakte hain bina kisi problem ke, lekin **write** operations ek samay par ek hi thread ko karne chahiye.

  * **Kaise Kaam Karta Hai?**

      * **Read Lock**: Ek thread data padhne se pehle "read lock" leta hai. Kai threads ek saath read lock le sakte hain.
      * **Write Lock**: Ek thread data likhne se pehle "write lock" leta hai. Jab tak write lock laga hai, koi aur thread (na reader, na writer) us data ko access nahi kar sakta.

  * **Kab Istemal Karein?** Inka istemal tab karna chahiye jab kisi shared data structure ko **padha (read) bahut baar jaata ho, lekin likha (write) kam baar jaata ho**. Jaise ki ek database search mein, jahan 90% operations search (read) hote hain aur 10% insert/update (write) hote hain.

### Q: Barrier synchronization kya hota hai?

**Answer**:
**Barrier** ek synchronization point hai. Jab ek thread barrier par pahunchta hai, toh woh tab tak ruka rehta hai jab tak uss barrier mein participate karne wale saare threads wahan pahunch na jaayein. Jab aakhiri thread barrier par pahunchta hai, toh sabhi threads ek saath aage badhte hain.

Ise Pthreads mein mutex aur condition variables ka istemal karke banaya ja sakta hai. Yeh un algorithms mein bahut upyogi hai jo phases mein kaam karte hain, aur agle phase ko shuru karne se pehle sabhi threads ko pichla phase khatam karna zaroori hota hai.

-----

## OpenMP - Directive-based Programming

### Q: OpenMP kya hai aur yeh Pthreads se kaise alag hai?

**Answer**:
**OpenMP** ek API hai jo directive-based parallel programming ko support karta hai. Yeh Pthreads se is tarah alag hai:

  * **Pthreads (Low-Level)**: Ismein programmer ko threads banane (`pthread_create`), join karne (`pthread_join`), aur synchronize karne (mutex, etc.) ke liye **explicitly function calls** likhne padte hain. Yeh zyada flexible hai lekin likhne mein complex hai.
  * **OpenMP (High-Level)**: Ismein programmer ko function calls ke bajaye C/C++ ya Fortran code mein **`#pragma` directives** (compiler ko nirdesh) likhne padte hain. Compiler in directives ko dekhkar apne aap threaded code generate kar deta hai. Yeh likhne mein bahut aasan hai, khaas kar loops ko parallel karne ke liye.

### Q: OpenMP mein parallel kaam kaise shuru karte hain aur loops ko kaise baant'te hain?

**Answer**:

  * **Parallel Region Banana (`parallel` directive)**:
    OpenMP program serially chalta hai jab tak use `#pragma omp parallel` directive nahi mil jaata. Yeh directive threads ka ek group banata hai, aur har thread uske neeche diye gaye code block ko execute karta hai.

  * **Loops ko Baantna (`for` directive)**:
    Agar aapke paas ek `for` loop hai jiski har iteration independent hai, toh use threads mein baantne ke liye `#pragma omp for` ka istemal kiya jaata hai. Compiler apne aap loop ki iterations ko threads ke beech divide kar deta hai.

    ```c
    #pragma omp parallel
    {
        // Sabhi threads yeh code block execute karenge
        #pragma omp for
        for (i = 0; i < 100; i++) {
            // Loop ki iterations threads mein bant jaayengi
        }
    }
    ```

    In dono ko jodkar `#pragma omp parallel for` bhi likha ja sakta hai.

### Q: OpenMP mein data ko threads ke beech kaise handle kiya jaata hai?

**Answer**:
OpenMP directives ke saath `clauses` ka istemal karke data ka scope (daayra) bataya jaata hai:

  * **`private(variable_list)`**: Is list mein diye gaye variables ki har thread ke liye ek alag, private copy ban jaati hai.
  * **`shared(variable_list)`**: Is list ke variables sabhi threads ke beech share kiye jaate hain. Inhe access karte waqt synchronization ka dhyan rakhna padta hai.
  * **`reduction(operator:variable)`**: Yeh bahut upyogi hai. Har thread variable ki ek private copy par kaam karta hai (jaise local sum nikalna). Jab saare threads apna kaam khatam kar lete hain, toh un sabki private copies ko diye gaye operator (jaise `+`, `*`) se combine karke final shared variable mein daal diya jaata hai.

### Q: OpenMP mein synchronization ke liye kaun se directives hote hain?

**Answer**:
OpenMP synchronization ke liye aasan directives deta hai:

  * **`#pragma omp critical`**: Yeh ek critical section banata hai. Ek samay par sirf ek hi thread is section ke code ko execute kar sakta hai.
  * **`#pragma omp atomic`**: Yeh sirf ek single statement (jaise `x++` ya `sum += value`) ko atomic banata hai. Yeh `critical` se halka (lightweight) hota hai aur aisi simple updates ke liye behtar hai.
  * **`#pragma omp barrier`**: Yeh ek explicit barrier lagata hai. Sabhi threads yahan ruk kar ek doosre ka intezar karte hain.

---

### Parallel vs. Distributed Computing

#### Q: Parallel aur Distributed Computing mein kya fark hai?

**Answer**:
Yeh dono hi multiple processors ka istemal karte hain, lekin unke memory model mein mukhya (main) antar hai:

* **Parallel Computing**: Ismein computation ko kai processors ke beech baanta jaata hai jo sabhi ek **shared memory** ka istemal karte hain. Sabhi processors ek hi memory ko seedhe access kar sakte hain.
* **Distributed Computing**: Is model mein har processor ki apni **private memory** hoti hai. Processors aapas mein information exchange karne ke liye network par **messages** bhejte hain.

---

### High-Performance Computing (HPC) ke Applications

#### Q: High-Performance Computing (HPC) ka istemal kahan-kahan hota hai?

**Answer**:
HPC ka istemal un complex problems ko solve karne ke liye hota hai jo normal computer nahi kar sakte. Iske kuch mukhya applications hain:
* **Bahut Bade Scale Par (Very Large)**: Mausam aur climate ki modeling, brahmand (cosmology) ki study, bade data sets ka analysis.
* **Bahut Chhote Scale Par (Very Small)**: Nayi dawaiyan design karna (drug design), silicon chip design, biological structures ko samajhna.
* **Bahut Complex Systems**: Fluid dynamics, bhukamp/tsunami ki bhavishyavani (prediction), nuclear tests ki simulation, aur car crash analysis.

---

### Alag-Alag Tarah ke Distributed Systems

#### Q: Cluster, Grid, aur Cloud Computing mein kya antar hai?

**Answer**:
Yeh teeno distributed computing ke hi roop hain, lekin inke characteristics alag-alag hain:

| Feature | **Cluster Computing** | **Grid Computing** | **Cloud Computing** |
| :--- | :--- | :--- | :--- |
| **Coupling** | **Tightly Coupled** (computers aapas mein bahut aache se jude hote hain) | **Loosely Coupled** (computers aapas mein dheele-dhaale jude hote hain) | Internet par आधारित services |
| **Ownership** | Aam taur par **ek hi organization** ke computers hote hain. | **Kai alag-alag organizations** ke resources ko milakar banta hai. | Resources service provider (jaise Amazon, Google) ke hote hain. |
| **System Image** | **Single System Image** (poora cluster ek single computer jaisa dikhta hai). | **No Single System Image** (har resource alag dikhta hai). | Resources ko virtual machines ke roop mein provide kiya jaata hai. |
| **Management** | **Centralized** job management hota hai. | **Distributed** job management hota hai. | User self-service portal se resources manage karta hai. |
| **Mukhya Uddeshya** | High performance aur availability. | Bade-bade common problems ko solve karne ke liye resources share karna. | Internet par computing services (servers, storage, software) deliver karna. |

---

### Supercomputing

#### Q: Supercomputing kya hai?

**Answer**:
Supercomputing mein **hazaron processors** ka istemal karke bade aur compute-intensive problems (jinmein bahut zyada calculation ki zaroorat hoti hai) ko solve kiya jaata hai. Yeh 1960s mein shuru hua tha.

June 2024 tak, duniya ka sabse tez supercomputer **Frontier** hai, jo America ki Oak Ridge National Laboratory mein hai. Ismein 8 million se bhi zyada cores hain.

#### Q: Aaj ke samay mein AI aur Machine Learning, supercomputing ko kaise badal rahe hain?

**Answer**:
AI aur Machine Learning (ML) modern High-Performance Computing (HPC) ke liye ek bahut bade driver ban gaye hain. Iske kuch mukhya pehlu hain:

* **Specialized Hardware**: AI/ML tasks ke liye khaas hardware banaye ja rahe hain, jaise:
    * **Nvidia Tensor Cores**: Chhote matrices (tensors) ki multiplication ko tez karne ke liye design kiye gaye hain.
    * **Google TPU (Tensor Processing Unit)**: AI/ML ke liye specialized processor.
    * **Graphcore IPU (Intelligence Processing Unit)**: Machine intelligence ko accelerate karne ke liye banaya gaya ek massively parallel processor.
* **Transprecision Units**: AI/ML ko aksar 32-bit floating point jitni high precision ki zaroorat nahi hoti. Kam precision ka istemal karke computations ko tez kiya ja sakta hai.
* **Near-Memory Computing**: Data ko processor tak laane mein bahut time aur energy lagti hai. Isliye, ab processing ko data ke paas (jahan data store hai) le jaane par zor diya ja raha hai, taaki data transfer kam se kam ho.

---

### Computing ka Bhavishya (Future of Computing)

#### Q: Neuromorphic Computing kya hai?

**Answer**:
Neuromorphic Computing ek naya approach hai jo traditional **Von-Neumann architecture se alag** hai. Iska lakshya insaani dimaag (human brain) ki tarah kaam karne wale computer banana hai.
* Yeh **analog chips** ka istemal karke dimaag ke neurons aur synapses ki nakal (mimic) karta hai.
* Insaani dimaag lagbhag 20 watts ki power mein kaam karta hai. Isi tarah, neuromorphic chips bahut **kam power consume** karte hain.
* **Example**: IBM ka **TrueNorth** chip ek neuromorphic processor hai.

#### Q: Quantum Computing ka basic idea kya hai aur iske applications kya hain?

**Answer**:
Quantum Computing bhi **Von-Neumann architecture se ekdum alag** hai. Yeh classical bits (0 ya 1) ke bajaye **Qubits** par kaam karta hai.
* **Qubit**: Yeh quantum physics ke principles ka istemal karta hai aur ek hi samay par **0, 1, ya dono ki superposition** mein ho sakta hai.
* **Entanglement**: Do qubits aapas mein "entangled" (jude hue) ho sakte hain. Ek qubit par operation karne se doosre entangled qubit par bhi turant asar padta hai.
* **Fayda**: 'n' qubits ka istemal karke $2^n$ units of information store ki ja sakti hai, jo ise kuch khaas problems ke liye classical computers se bahut zyada powerful banata hai.

**Applications**: Iska istemal optimization problems, cryptography (code todne), aur machine learning jaise fields mein ho sakta hai.

#### Q: FPGAs kya hote hain aur HPC mein unka kya role hai?

**Answer**:
**FPGAs (Field Programmable Gate Arrays)** aise electronic circuits hote hain jinhe khareedne ke baad user apni zaroorat ke hisaab se **program kar sakta hai**.
* **HPC mein Role**: Inmein HPC community ka interest isliye badh raha hai kyunki yeh bahut **kam energy** consume karte hain.
* **Nuksaan**: Inhe program karna bahut mushkil hota hai.

---

### PDC ke Zaroori Concepts (Important Concepts)

#### Q: Latency aur Bandwidth mein kya fark hai?

**Answer**:
* **Latency**: Data ko point A se point B tak pahunchne mein lagne wala samay (delay). Ise aam taur par milliseconds (ms) mein naapa jaata hai.
* **Bandwidth**: Ek nishchit samay mein kitna data point A se point B tak transfer kiya ja sakta hai. Ise aam taur par Gigabytes per second (GB/s) mein naapa jaata hai.

*Analoggy*: Ek paani ke pipe mein, **latency** paani ko tap on karne se lekar pipe ke doosre sire se nikalne tak ka samay hai. **Bandwidth** pipe ki motai hai, jo batati hai ki ek second mein kitna paani nikal sakta hai.

#### Q: Cores, Nodes, Threads, aur Processes ka kya matlab hai?

**Answer**:
* **Cores**: Ek CPU (Central Processing Unit) ke andar ki individual processing units. Ek modern CPU mein kai cores ho sakte hain (jaise dual-core, quad-core).
* **Node**: Ek cluster mein ek single, independent computer. Ek cluster kai nodes se milkar banta hai.
* **Process**: Operating system dwara chalaya ja raha ek program. Har process ki apni private memory space hoti hai.
* **Thread**: Ek process ke andar chalne wala ek "lightweight process". Ek process ke andar kai threads ho sakte hain jo aapas mein memory share karte hain.

#### Q: Speedup, Efficiency, Strong Scaling, aur Weak Scaling kya hote hain?

**Answer**:
* **Speedup**: Batata hai ki parallel program, serial program se kitne guna tez hai. ($S = T_{serial} / T_{parallel}$)
* **Efficiency**: Batati hai ki processors ko kitna aache se istemal kiya ja raha hai. ($E = S / \text{processors ki sankhya}$)
* **Strong Scaling (Amdahl's Law)**: Ismein **problem size ko constant** rakha jaata hai aur processors ki sankhya badha kar dekha jaata hai ki runtime kitna kam hota hai.
* **Weak Scaling (Gustafson's Law)**: Ismein **har processor ke liye problem size ko constant** rakha jaata hai. Yaani, jab hum processors ki sankhya badhate hain, toh hum total problem size ko bhi badha dete hain. Isse dekha jaata hai ki runtime constant rehta hai ya nahi.

---

### Software Development ka Safar (History of Software Crises)

#### Q: Software development mein ab tak kaun-kaun se "Software Crises" aaye hain?

**Answer**:
Software development mein samay ke saath 3 bade "crisis" (sankat) aaye hain, jinhone programming ke tarike ko badla hai:

1.  **First Software Crisis (1960s-70s)**:
    * **Problem**: Program **Assembly Language** mein likhe jaate the, jo bahut mushkil tha. Jaise-jaise computer powerful hote gaye, bade aur complex program likhna aur maintain karna asambhav (impossible) ho gaya.
    * **Solution**: **High-Level Languages** jaise FORTRAN aur C ka vikas hua. Inhone programmers ko abstraction aur portability di.

2.  **Second Software Crisis (1980s-90s)**:
    * **Problem**: Applications itni badi aur complex ho gayi (multi-million lines of code) ki unhe manage karna, maintain karna aur unmein naye features jodna bahut mushkil ho gaya.
    * **Solution**: **Object-Oriented Programming (OOP)** jaise C++ aur Java ka uday hua. Saath hi, behtar software engineering methodologies (design patterns, code reviews, testing) apnai gayi. Is dauran performance ki chinta nahi thi, kyunki Moore's Law ke kaaran hardware apne aap tez hota ja raha tha.

3.  **Emerging/Third Software Crisis (2002 - Aaj Tak)**:
    * **Problem**: Sequential performance (single-core speed) badhna band ho gaya hai. Moore's Law ab single-core ko tez nahi kar raha hai. Ab performance badhane ka "free lunch" khatam ho gaya hai.
    * **Solution**: **Multi-core architectures** aur **Parallel Programming**. Ab software ko performance badhane ke liye ek saath kai cores ka istemal karna padega.

---

### Uniprocessor Performance ki Deewarein (Performance Walls)

#### Q: Single-core processors ki performance badhna kyu ruk gayi? Power, Memory, aur ILP Wall kya hain?

**Answer**:
Single-core processors ki speed badhna 3 mukhya "deewaron" (walls) ke kaaran ruk gayi:

1.  **Power Wall**: Jaise-jaise processor ki clock speed badhti hai, uski power consumption aur heat generation exponentially badhti hai. Ek point ke baad, is heat ko manage karna aur chip ko thanda rakhna practical nahi raha.
2.  **Memory Wall**: Processor ki speed memory (DRAM) ki speed se bahut zyada tezi se badhi hai. Is "Processor-Memory Performance Gap" ke kaaran, processor ko aksar data ke liye memory ka intezar karna padta hai, jisse uski poori क्षमता (capability) ka istemal nahi ho paata.
3.  **ILP Wall (Instruction-Level Parallelism Wall)**: ILP ka matlab hai ek hi clock cycle mein kai instructions ko execute karna. Processors mein iski bhi ek seema (limit) aa gayi hai. Ek single instruction stream se aur zyada parallelism nikalna bahut mushkil aur inefficient ho gaya hai.

In teeno "walls" ko milakar ek **"Brick Wall"** ban gayi, jisne single-core processors ko aur tez hone se rok diya. Iska nateeja yeh hua ki ab Moore's Law processors ki speed badhane ke bajaye, har 2 saal mein chip par **cores ki sankhya double** kar raha hai.

---

### Multi-core Processors ka Istemal (Harnessing Multi-cores)

#### Q: Parallelism ke alag-alag forms kaun se hain?

**Answer**:
Multi-core processors ka fayda uthane ke liye, hum alag-alag tarah ke parallelism ka istemal karte hain:

1.  **Instruction-Level Parallelism (ILP)**: Ek hi samay par kai instructions ko execute karna. **Superscalar architectures** iska istemal karti hain, jinke paas multiple computational units hote hain.
2.  **Data-Level Parallelism (DLP)**: Ek hi instruction ko ek saath kai alag-alag data par apply karna. **GPUs** iska bharpoor istemal karte hain. **CUDA** jaisa programming framework DLP ko support karta hai.
3.  **Thread-Level Parallelism (TLP)**: Kai alag-alag threads (chhote programs) ko ek saath parallel mein execute karna. **Multi-core processors** TLP ka fayda uthane ke liye hi banaye gaye hain.

---

### Parallel Programming ki Chunautiyan (Challenges)

#### Q: Concurrency kya hai aur Amdahl's Law speedup ko kaise limit karta hai?

**Answer**:
**Concurrency** ka matlab hai ki ek problem ke kitne hisson ko ek saath parallel mein chalaya ja sakta hai.

**Amdahl's Law** ek bahut zaroori niyam hai jo batata hai ki ek program mein thoda sa sequential (non-parallel) hissa hone par bhi total speedup kitna limit ho jaata hai.

**Formula**:
$Speedup = \frac{1}{(1-p) + \frac{p}{n}}$

* Jahan, **p** = Program ka parallel hissa (jaise 0.9 agar 90% parallel hai).
* **(1-p)** = Program ka sequential hissa.
* **n** = Processors ki sankhya.

**Example**: Agar aapke paas 10 processor hain aur aapka program 90% parallel hai (aur 10% sequential):
$Speedup = \frac{1}{(1-0.9) + \frac{0.9}{10}} = \frac{1}{0.1 + 0.09} = \frac{1}{0.19} \approx 5.26$

Iska matlab hai ki 10 processor istemal karne par bhi aapko sirf **5.26 guna speedup** milega, 10 guna nahi. Yeh dikhata hai ki program ka **sequential hissa speedup ke liye sabse bada bottleneck** hai.

#### Q: Load Balancing ka kya matlab hai? Primality testing ke example se samjhaiye.

**Answer**:
**Load Balancing** ka matlab hai sabhi processors ke beech kaam ko barabar-barabar baantna, taaki koi bhi processor khaali (idle) na baithe aur kaam jaldi se jaldi poora ho.

**Primality Testing Example**:
Maan lijiye humein 1 se $10^{10}$ tak ke prime numbers print karne hain aur hamare paas 10 processor hain.

* **Galat Tarika (Static Load Balancing)**: Hum kaam ko barabar hisson mein baant dete hain. Processor 0 ko 1 se $10^9$ tak, Processor 1 ko $10^9$ se $2 \times 10^9$ tak, aur isi tarah aage.
* **Problem**: Yeh load balancing aacha nahi hai. Kyunki:
    1.  Bade numbers ko prime hai ya nahi, yeh check karna chote numbers se zyada mushkil aur time-consuming hota hai.
    2.  Higher ranges mein prime numbers kam hote hain.
* **Nateeja**: Jinn processors ko bade numbers mile hain (jaise Processor 9), unhe bahut zyada kaam karna padega, jabki shuruwati processors (jaise Processor 0) apna kaam jaldi khatam karke khaali baith jayenge.
* **Solution**: Aisi situations ke liye **Dynamic Load Balancing** ki zaroorat padti hai, jahan kaam runtime par zaroorat ke hisaab se baanta jaata hai.

#### Q: Synchronization mein kya-kya problems aati hain?

**Answer**:
Jab kai threads ek saath shared data par kaam karte hain, toh unhe synchronize karna padta hai. Ismein kai problems aati hain:
* **Programming Mushkil**: Locks aur conditions ka sahi istemal karna complex hota hai.
* **Deadlocks**: Aisi situation jahan do ya do se zyada threads ek doosre ka intezar karte reh jaate hain aur program aage nahi badh paata.
* **Granularity**: Yeh decide karna ki kitne chhote ya bade code segment ko lock karna hai, ek challenge hai. Chote locks se overhead badhta hai, bade locks se parallelism kam hota hai.
* **Not Composable**: Do alag-alag aache se synchronize kiye gaye code fragments ko jab joda jaata hai, toh ho sakta hai woh milkar sahi se kaam na karein.

---

### Parallel Programming Mushkil Kyun Hai?

#### Q: Parallel programming ko itna difficult kyu maana jaata hai?

**Answer**:
Parallel programming kai kaarano se mushkil hai:

1.  **Parallelism Dhundhna**: Har problem ko aasaani se parallel hisson mein nahi toda ja sakta.
2.  **Debugging**: Parallel programs ko debug karna bahut mushkil hota hai. Bugs (jaise Race Conditions) har baar nahi aate, jisse unhe **reproduce karna** aur fix karna mushkil ho jaata hai.
    * **Example (Race Condition)**: Jab do threads ek hi samay par `X = X + 1` operation karte hain. Iske 3 steps hote hain: (A) Load X, (B) Increment, (C) Store X. Agar threads ke steps aapas mein mix ho jaate hain (jaise ek thread Load kare, fir doosra thread Load kare), toh final result galat aa sakta hai (X ki value 2 ke bajaye 1 ho sakti hai).
3.  **Scalability**: Aisa program banana jo 2 cores par aacha chale, zaroori nahi ki woh 200 cores par bhi aacha chalega. Program ko "scalable" hona chahiye.
4.  **Memory Speed**: Program ki speed aksar memory access speed se limit ho jaati hai (Memory Wall).
5.  **Input Data Par Nirbharta**: Program ki execution speed input data ke characteristics par bhi depend kar sakti hai, jisse load balancing mushkil ho jaata hai.

---

### Pthreads ka Introduction

#### Q: Pthreads kya hai aur ismein program likhne ke liye kya-kya zaroori hai?

**Answer**:
**Pthreads (POSIX Threads)** C language mein multi-threaded applications likhne ke liye ek standard API (set of functions) hai. Yeh programmers ko threads banane, manage karne, aur unke beech synchronization (taal-mel) sthapit karne ke liye tools deta hai.

**Program likhne ke liye zaroori cheezein**:
1.  **Header File**: Apne C code mein `#include <pthread.h>` include karna zaroori hai.
2.  **Compilation**: Program ko compile karte waqt `gcc` ke saath `-pthread` flag lagana zaroori hai (jaise `gcc my_program.c -o my_program -pthread`). Yeh Pthreads library ko link karta hai.

---

### Thread Lifecycle Management

#### Q: Ek Pthread ko kaise banaya (create), khatam hone ka intezar (join), aur khud se terminate (exit) kiya jaata hai?

**Answer**:
Ek thread ke lifecycle mein 3 mukhya steps hote hain:

1.  **Thread Banana (`pthread_create`)**:
    Yeh function ek naya thread shuru karta hai. Iske 4 mukhya arguments hote hain:
    * `thread`: Ek `pthread_t` type ka pointer, jismein naye bane thread ki ID store hoti hai.
    * `attr`: Thread ke attributes (properties) set karne ke liye. Aam taur par ise `NULL` rakha jaata hai default settings ke liye.
    * `start_routine`: Us function ka naam jise yeh naya thread chalayega.
    * `arg`: `start_routine` function ko pass karne ke liye argument.

2.  **Thread ka Intezar Karna (`pthread_join`)**:
    Yeh function ek thread ko doosre thread ke khatam hone ka intezar karwata hai. Aam taur par, `main` thread ise call karta hai taaki woh child threads ke kaam poora karne ka intezar kar sake. Iske do arguments hain:
    * `thread`: Jis thread ka intezar karna hai uski ID.
    * `retval`: Ek pointer jahan child thread ka return value store kiya jayega. Agar return value nahi chahiye, toh `NULL` pass kar sakte hain.

3.  **Thread ko Terminate Karna (`pthread_exit`)**:
    Yeh function ek thread khud call karta hai jab uska kaam poora ho jaata hai. Yeh thread ko terminate kar deta hai.
    * `retval`: Is argument se thread ek value return kar sakta hai, jise `pthread_join` call karne wala thread receive kar sakta hai.

---

### Synchronization - Saath Milkar Kaam Karna

#### Q: Threads ke beech synchronization ki zaroorat kyun padti hai? Critical Section kya hota hai?

**Answer**:
Jab kai threads ek hi shared data (jaise global variable) par kaam karte hain, toh **Race Conditions** ho sakti hain, jisse program ka output galat aur unpredictable ho jaata hai. Isse bachne ke liye synchronization zaroori hai.

**Critical Section** code ka woh hissa hota hai jahan shared data ko access ya modify kiya jaata hai. Synchronization ka mukhya lakshya (goal) yeh sunishchit (ensure) karna hai ki ek samay par sirf ek hi thread critical section mein enter kare.

#### Q: Mutex Locks (`pthread_mutex_lock`, `pthread_mutex_unlock`) ka istemal kaise karte hain?

**Answer**:
**Mutex (Mutual Exclusion) Lock** ek taale (lock) ki tarah kaam karta hai.
1.  **Initialize**: Sabse pehle, ek mutex variable ko initialize karna padta hai:
    `pthread_mutex_t lock = PTHREAD_MUTEX_INITIALIZER;`
    Ya dynamically: `pthread_mutex_init(&lock, NULL);`
2.  **Lock**: Critical section mein enter karne se pehle, thread `pthread_mutex_lock(&lock);` call karta hai.
    * Agar lock free hai, toh thread lock haasil kar leta hai aur aage badhta hai.
    * Agar lock pehle se hi kisi aur thread ke paas hai, toh yeh thread block ho jaata hai (intezar karta hai).
3.  **Unlock**: Critical section ka kaam poora hone ke baad, thread `pthread_mutex_unlock(&lock);` call karke lock ko chhod (release) deta hai, taaki koi waiting thread use haasil kar sake.

#### Q: Condition Variables (`pthread_cond_wait`, `pthread_cond_signal`) ka istemal kab aur kaise karte hain? Yeh Mutex se kaise alag hai?

**Answer**:
**Condition Variables (CVs)** ka istemal threads ke beech signaling ke liye hota hai. Yeh ek thread ko "sone" (block) aur doosre thread dwara "jagaye" (unblock) jaane ki suvidha deta hai jab koi khaas condition poori ho.

**Istemal**: Inka istemal tab hota hai jab ek thread ko doosre thread dwara produce kiye gaye data ya event ka intezar karna hota hai. Yeh busy-waiting (baar-baar flag check karna) se behtar hai, kyunki ismein CPU cycles waste nahi hote.

**Kaise Kaam Karta Hai**:
1.  Ek thread mutex ko lock karta hai aur condition check karta hai.
2.  Agar condition false hai, toh woh `pthread_cond_wait(&cond, &lock);` call karta hai. Yeh function do kaam karta hai:
    * Thread ko sula (block) deta hai.
    * Mutex ko **automatically unlock** kar deta hai, taaki doosre threads condition ko badal sakein.
3.  Jab koi doosra thread condition ko true kar deta hai, toh woh `pthread_cond_signal(&cond);` call karke waiting thread ko jagata hai.
4.  Jaga hua thread `wait` se return hone se pehle mutex ko dobara **automatically lock** kar leta hai aur अपना kaam aage badhata hai.

#### Q: Barrier (`pthread_barrier_wait`) synchronization kya hota hai?

**Answer**:
**Barrier** ek meeting point jaisa hai. Sabhi threads `pthread_barrier_wait()` call karke is point par ruk jaate hain. Koi bhi thread barrier se aage nahi badhta jab tak ki sabhi participating threads us barrier tak na pahunch jaayein. Jab aakhiri thread pahunch jaata hai, toh sabhi threads ek saath release ho jaate hain aur apna-apna kaam aage badhate hain.

Yeh un algorithms mein bahut upyogi hai jo phases mein kaam karte hain, jahan agla phase shuru karne se pehle sabhi threads ka pichla phase poora karna zaroori hota hai.

---

### Pthreads Programming ke Zaroori Niyam (Guidelines)

#### Q: Pthreads mein program likhte waqt kaun si aam galtiyon (common pitfalls) se bachna chahiye?

**Answer**:
* **Stack se Pointer Return Karna**: Kisi thread se uske apne stack par banaye gaye variable ka pointer kabhi return na karein. Jab thread ka function khatam hota hai, toh uska stack destroy ho jaata hai aur woh pointer invalid ho jaata hai, jisse unpredictable behavior hota hai.
* **Initialization na Karna**: Locks aur condition variables ko istemal karne se pehle initialize karna bahut zaroori hai. Bina initialize kiye code kabhi-kabhi kaam karega aur kabhi-kabhi ajeeb tarike se fail ho jayega.
* **Deadlocks**: Locks ko galat order mein acquire karne se deadlock ho sakta hai, jahan threads ek doosre ka hamesha ke liye intezar karte reh jaate hain.
* **Return Codes Check na Karna**: Pthread ke har function (jaise `pthread_create`, `pthread_mutex_lock`) ka return code check karna zaroori hai. Agar aap aesa nahi karte, toh failure silently ho sakta hai aur aapka program galat kaam kar sakta hai.

#### Q: Ek aacha multi-threaded program likhne ke liye kuch best practices kya hain?

**Answer**:
* **Keep it Simple**: Thread interactions ko jitna ho sake saral (simple) rakhein.
* **Initialize Everything**: Hamesha locks aur condition variables ko initialize karein.
* **Check Return Codes**: Har library call ke return value ko check karein.
* **Use Condition Variables for Signaling**: Threads ke beech signal ke liye simple flags aur spinning ke bajaye hamesha condition variables ka istemal karein. Yeh zyada efficient aur kam error-prone hai.
* **Data Sharing**: Threads ke beech data share karne ke liye heap (jaise `malloc`) ka istemal karein, stack ka nahi. Yaad rakhein, har thread ka apna alag stack hota hai.

---

### Pthreads se Kaun si Problems Solve ki Jaa Sakti hain?

#### Q: Pthreads ka istemal karke kis tarah ki problems ko aasaani se solve kiya ja sakta hai?

**Answer**:
Pthreads un sabhi problems ke liye aacha hai jinhe independent tasks mein toda ja sakta hai. Kuch aam examples hain:
* **Parallel Summation**: Ek bade array ke alag-alag hisson ka sum alag-alag threads nikalte hain aur aakhir mein unhe jod diya jaata hai.
* **Parallel Matrix Multiplication**: Output matrix ke alag-alag rows ya columns ko alag-alag threads calculate karte hain.
* **Finding Max/Min in an Array**: Array ko threads mein baant kar har thread apne hisse ka local max/min nikalta hai.
* **Producer-Consumer Problems**: Ek ya ek se zyada threads data (tasks) produce karte hain aur unhe ek queue mein daalte hain, jabki doosre threads us queue se data nikal kar process karte hain.
---

### OpenMP ka Introduction

#### Q: OpenMP kya hai aur yeh Pthreads se kaise alag hai?

**Answer**:
**OpenMP (Open Multi-Processing)** ek API hai jo shared-memory parallel programming ko aasan banane ke liye design kiya gaya hai. Yeh Pthreads se is tarah alag hai:

  * **High-Level vs. Low-Level**: OpenMP **high-level** hai. Ismein aap compiler ko **directives** (`#pragma omp ...`) ke zariye batate hain ki code ka kaun sa hissa parallel karna hai. Jabki, Pthreads **low-level** hai, jismein aapko threads banane, manage karne aur synchronize karne ke liye **explicitly functions** (jaise `pthread_create`) call karne padte hain.
  * **Aasani (Ease of Use)**: OpenMP se serial code ko parallel mein badalna bahut aasan hai, aksar sirf kuch lines add karke. Pthreads mein zyada coding aur management lagta hai.

#### Q: OpenMP program ka basic structure kaisa hota hai? (`parallel` directive)

**Answer**:
OpenMP "fork-join" model par kaam karta hai. Program shuru mein ek single thread (master thread) se chalta hai.

1.  **Fork**: Jab master thread ko `#pragma omp parallel` directive milta hai, toh woh threads ki ek team "fork" (create) karta hai.
2.  **Parallel Execution**: Iske baad, `parallel` block ke andar ka code sabhi threads (master + new threads) dwara ek saath execute kiya jaata hai. Master thread ka ID hamesha `0` hota hai.
3.  **Join**: Jab block khatam hota hai, toh wahan ek **implicit barrier** hota hai. Sabhi threads yahan ruk kar ek doosre ka intezar karte hain. Jab sabhi threads kaam poora kar lete hain, toh woh "join" ho jaate hain aur sirf master thread hi aage ka program execute karta hai.

-----

### Kaam ko Threads mein Baantna (Work-Sharing)

#### Q: `for` directive ka istemal karke loops ko parallel kaise karte hain?

**Answer**:
Agar aapke paas ek `for` loop hai jiski har iteration independent hai, toh use threads mein baantne ke liye `#pragma omp for` ka istemal kiya jaata hai. Yeh directive `parallel` region ke andar lagaya jaata hai. OpenMP apne aap loop ki iterations ko team ke sabhi threads ke beech distribute kar deta hai.

**Syntax (Combined):**

```c
#pragma omp parallel for
for (int i = 0; i < N; i++) {
    // Yeh code parallel mein chalega.
    // Har thread ko 'i' ki alag-alag values milengi.
}
```

#### Q: Alag-alag tarah ke kaam (tasks) ko threads mein baantne ke liye `sections` directive ka istemal kaise hota hai?

**Answer**:
Jab aapke paas alag-alag, independent code blocks hon (jo loop na hon) aur aap unhe alag-alag threads ko dena chahte hon, tab `sections` directive ka istemal hota hai.

  * Har `#pragma omp section` ke andar likha code block ek thread ko assign kar diya jaata hai.
  * Yeh functional parallelism ke liye upyogi hai.

**Syntax:**

```c
#pragma omp parallel sections
{
    #pragma omp section
    {
        // Task A yahan likha jayega
    }
    #pragma omp section
    {
        // Task B yahan likha jayega
    }
}
```

#### Q: `single` aur `master` directives ka kya kaam hai?

**Answer**:
Yeh dono directives parallel region ke andar code ke ek block ko sirf ek thread se chalwane ke liye hote hain.

  * **`single`**: Code block ko team ka **koi bhi ek thread** (jo pehle pahunche) execute karega. Iske aakhir mein ek implicit barrier hota hai, yaani baaki threads aage badhne se pehle iska kaam khatam hone ka intezar karte hain.
  * **`master`**: Code block ko **sirf master thread (thread ID 0)** hi execute karega. Iske aakhir mein **koi barrier nahi hota**, yaani baaki threads bina intezar kiye aage badh jaate hain.

-----

### Data ko Threads ke Beech Handle Karna (Data Scoping)

#### Q: `private` aur `firstprivate` clauses mein kya fark hai?

**Answer**:

  * **`private(x)`**: Har thread ke liye variable 'x' ki ek nayi, **uninitialized** (khali) copy ban jaati hai. Parallel region ke bahar original 'x' ki value par koi asar nahi padta.
  * **`firstprivate(x)`**: Har thread ke liye variable 'x' ki ek nayi copy banti hai, lekin yeh copy parallel region mein enter hone se theek pehle original 'x' ki value se **initialize** hoti hai.

#### Q: `reduction` clause kya hai aur yeh itna zaroori kyun hai?

**Answer**:
**Reduction Clause** parallel loops mein aane wali ek bahut common problem ka aasan solution hai. Iska istemal tab hota hai jab aap sabhi threads ke results ko combine karke ek single value banana chahte hain (jaise sum, product, max, min nikalna).

**Yeh Kaise Kaam Karta Hai**:

1.  Har thread ke liye reduction variable (jaise `sum`) ki ek private copy ban jaati hai aur use operator ke hisaab se initialize kar diya jaata hai (jaise `+` ke liye 0).
2.  Har thread sirf apni private copy par kaam karta hai. Isse race condition nahi hoti.
3.  Jab loop khatam hota hai, OpenMP sabhi threads ki private copies ko diye gaye operator se **combine** karta hai aur final result ko original global variable mein store kar deta hai.

**Syntax**:

```c
int total_sum = 0;
#pragma omp parallel for reduction(+:total_sum)
for (int i = 0; i < N; i++) {
    total_sum += array[i]; // Har thread apni private copy mein jodega
}
// Loop ke baad, total_sum mein final combined result hoga.
```

-----

### Load Balancing - `schedule` Clause

#### Q: Loop iterations ko threads mein baantne ke liye `schedule` clause ke kaun-kaun se options hain?

**Answer**:
`schedule` clause batata hai ki `for` loop ki iterations ko threads ke beech kaise baanta jayega. Iske 3 mukhya types hain:

  * **`schedule(static, chunk_size)`**: Iterations ko `chunk_size` ke blocks mein toda jaata hai aur threads ko round-robin fashion mein statically (shuru mein hi) assign kar diya jaata hai.
      * **Fayda**: Sabse kam overhead.
      * **Nuksaan**: Agar har iteration mein alag-alag time lagta hai, toh load imbalance ho sakta hai.
  * **`schedule(dynamic, chunk_size)`**: Har thread ko `chunk_size` iterations ka ek block milta hai. Jab koi thread apna kaam khatam kar leta hai, toh use agla available block de diya jaata hai.
      * **Fayda**: Load balancing ke liye bahut aacha hai.
      * **Nuksaan**: Overhead zyada hota hai.
  * **`schedule(guided, chunk_size)`**: Yeh dynamic jaisa hi hai, lekin shuru mein bade chunks diye jaate hain aur dheere-dheere chunks ka size kam hota jaata hai. Yeh static aur dynamic ke beech ka ek compromise hai.

**Rule of Thumb**: Hamesha **static** se shuru karein. Agar performance aachi nahi hai (load imbalance ke kaaran), tabhi **dynamic** ya **guided** ka istemal karein.

-----

### Synchronization - Threads mein Taal-mel

#### Q: `critical` aur `atomic` directives ka istemal kab aur kyun karte hain?

**Answer**:
Yeh dono directives critical sections banane ke liye hote hain, taaki shared data ko race conditions se bachaya ja sake.

  * **`critical`**: Yeh code ke ek **poore block** ko protect karta hai. Ek samay par sirf ek hi thread `#pragma omp critical` block ke andar enter kar sakta hai. Iska istemal tab karein jab aapko multiple statements ko protect karna ho.
  * **`atomic`**: Yeh sirf **ek single statement** ko protect karta hai, jismein memory location ko update kiya ja raha ho (jaise `x++`, `sum += 1`). Yeh `critical` se halka (lightweight) hota hai aur aisi simple updates ke liye bahut tez ho sakta hai, khaas kar agar hardware ise support karta ho.

#### Q: `barrier` aur `ordered` directives ka kya kaam hai?

**Answer**:

  * **`barrier`**: Yeh ek synchronization point hai. `#pragma omp barrier` par sabhi threads ruk jaate hain aur tab tak aage nahi badhte jab tak team ke sabhi threads us point tak na pahunch jaayein.
  * **`ordered`**: Yeh `for` loop ke andar use hota hai. `#pragma omp ordered` block ke andar ka code usi kram (order) mein execute hota hai jis kram mein woh ek serial loop mein hota. Iske liye `for` directive mein `ordered` clause lagana zaroori hai.

-----

### OpenMP ke Zaroori Functions

#### Q: OpenMP mein commonly use hone wale runtime functions kaun se hain?

**Answer**:
OpenMP kuch useful library functions bhi deta hai:

  * **`int omp_get_thread_num();`**:
      * **Input**: Kuch nahi.
      * **Output**: Current thread ki ID return karta hai (0 se lekar `num_threads-1` tak).
  * **`int omp_get_num_threads();`**:
      * **Input**: Kuch nahi.
      * **Output**: Current parallel region mein active threads ki total sankhya return karta hai.
  * **`double omp_get_wtime();`**:
      * **Input**: Kuch nahi.
      * **Output**: Wall-clock time (seconds mein) return karta hai. Iska istemal code ke sections ko time karne ke liye kiya jaata hai.

---
### Flynn’s Taxonomy, Modern CPUs, aur GPUs

#### Q: Flynn’s taxonomy modern multicore CPU aur GPU architectures par kaise apply hoti hai?

**Answer**:
Flynn's taxonomy thodi purani hai, isliye modern architectures par yeh seedhe-seedhe apply nahi hoti, balki yeh hybrid models hain:

* **Modern Multicore CPU**: Yeh **MIMD (Multiple Instruction, Multiple Data)** architecture hai, kyunki har core apna alag instruction stream alag data par chala sakta hai. Lekin, har core ke andar **SIMD (Single Instruction, Multiple Data)** units bhi hoti hain (jaise Intel ka AVX). Yeh units ek hi instruction (jaise 'add') ko ek saath data ke ek poore vector par apply kar sakti hain. Isliye, modern CPUs **MIMD + SIMD** ka hybrid hote hain.

* **GPU (Graphics Processing Unit)**: GPUs ko aksar **SIMT (Single Instruction, Multiple Threads)** architecture kaha jaata hai. Yeh SIMD ka hi ek advanced roop hai. Ismein, hazaron threads ek hi instruction ko ek saath execute karte hain, lekin har thread alag data par kaam karta hai. SIMT, SIMD se zyada flexible hai kyunki yeh threads ko thodi azaadi deta hai ki woh zaroorat padne par alag-alag code path le sakein (jise 'thread divergence' kehte hain).

---

### Distributed Systems mein Load Balancing

#### Q: Distributed systems mein load balancing itna zaroori kyun hai? Do examples dijiye.

**Answer**:
Distributed systems mein, jahan kaam kai alag-alag computers (nodes) par baanta jaata hai, load balancing bahut zaroori hai. Iske mukhya kaaran hain:

1.  **Resource Utilization**: Yeh sunishchit (ensure) karta hai ki sabhi nodes barabar kaam karein aur koi bhi node khaali (idle) na baithe, jabki doosre overloaded hon.
2.  **Bottleneck se Bachna**: Agar saara kaam ek hi node par aa jaye, toh woh node ek bottleneck ban jayega aur poore system ki performance ko slow kar dega.
3.  **Response Time aur Throughput Behtar Karna**: Kaam ko barabar baantne se users ko response jaldi milta hai aur system ek samay mein zyada requests handle kar paata hai.

**Examples**:
1.  **Web Server Load Balancing**: Jab kisi website (jaise Amazon ya Google) par bahut zyada traffic aata hai, toh ek **load balancer** aane wali requests ko kai alag-alag web servers ke beech baant deta hai. Isse koi ek server overload nahi hota aur website fast chalti rehti hai.
2.  **Big Data Processing (Hadoop)**: Hadoop jaise framework mein, ek badi processing job ko chhote-chhote tasks mein toda jaata hai. Ek master node in tasks ko cluster ke alag-alag worker nodes par distribute karta hai, taaki data processing parallel mein ho aur sabhi nodes ka sahi istemal ho.

---

### Programming Models ki Tulna (Comparison)

#### Q: Pthreads, OpenMP, aur MPI mein kya antar hai aur inka istemal kab karna chahiye?

**Answer**:
Yeh teeno parallel programming ke liye alag-alag models hain:

| Feature | **Pthreads (POSIX Threads)** | **OpenMP** | **MPI (Message Passing Interface)** |
| :--- | :--- | :--- | :--- |
| **Model** | Library-based, low-level | Directive-based, high-level | Library-based, message passing |
| **Memory** | **Shared Memory** (ek hi machine ke andar) | **Shared Memory** (ek hi machine ke andar) | **Distributed Memory** (alag-alag machines ke beech) |
| **Programming** | **Explicit & Complex**: Threads banana, join karna, synchronize karna, sab kuch manually karna padta hai. | **Implicit & Easy**: Code mein `#pragma` directives lagakar compiler ko bataya jaata hai ki kya parallel karna hai. | **Explicit & Complex**: Processors ke beech data bhejne (`send`) aur receive karne ke liye manually code likhna padta hai. |
| **Control** | Bahut zyada, fine-grained control milta hai. | Kam control, compiler par zyada nirbhar. | Data movement aur communication par poora control. |
| **Istemal Kab Karein?** | Jab aapko ek single machine par threads par poora, low-level control chahiye. | Jab aapko ek single machine par, khaas kar loops, ko jaldi se parallel karna ho. Yeh existing serial code ko parallel banane ke liye best hai. | Jab aapko bade-bade applications (scientific simulations) ko ek cluster ya supercomputer (kai machines) par chalana ho. |

---

### GPU Performance Concepts

#### Q: GPU performance par Cache Locality aur Memory Coalescing ka kya prabhav padta hai?

**Answer**:
GPU performance ke liye yeh dono concepts bahut zaroori hain:

* **Cache Locality**: Yeh CPU jaisa hi hai. Agar GPU ke threads us data ko access kar rahe hain jo pehle se hi L1 ya L2 cache mein hai, toh unhe slow global memory tak nahi jaana padta. Isse latency kam hoti hai aur performance badhti hai. Aache se locality ka istemal karne wale algorithms GPU par bahut tez chalte hain.

* **Memory Coalescing**: Yeh GPU ka ek khaas feature hai. GPU mein threads **warps** (aam taur par 32 threads ka group) mein kaam karte hain.
    * Jab ek warp ke sabhi threads memory mein **ek-ke-baad-ek (contiguous)** locations ko access karte hain, toh GPU hardware un 32 chhote-chhote memory requests ko ek **single, bade memory transaction** mein "coalesce" (jod) deta hai.
    * Yeh ek single transaction, 32 alag-alag transactions se kai guna tez hota hai.
    * Agar threads random memory locations ko access karte hain, toh access **uncoalesced** ho jaata hai, jisse performance bahut zyada gir jaati hai. Isliye, GPU programming mein memory coalescing haasil karna bahut zaroori hai.

---

### Amdahl's Law vs. Gustafson's Law

#### Q: Gustafson’s Law, Amdahl’s Law se zyada aashawadi (optimistic) kyun hai?

**Answer**:
Dono laws parallel speedup ko naapte hain, lekin unke moolbhoot anumaan (assumptions) alag-alag hain, jisse unke nateeje bhi alag aate hain.

* **Amdahl's Law (Pessimistic - Niraashawadi)**:
    * **Anumaan**: Yeh maanta hai ki **problem ka size hamesha fixed rehta hai** (Strong Scaling).
    * **Logic**: Jab aap processors badhate hain, toh program ka parallel hissa toh tez ho jaata hai, lekin sequential hissa utna hi time leta hai. Ek samay ke baad, yeh sequential hissa bottleneck ban jaata hai aur speedup badhna band ho jaata hai. Yeh batata hai ki speedup ki ek seema (limit) hai.

* **Gustafson's Law (Optimistic - Aashawadi)**:
    * **Anumaan**: Yeh maanta hai ki jab humare paas zyada processors hote hain, toh hum **problem ka size bhi bada kar dete hain** (Weak Scaling).
    * **Logic**: Is case mein, jaise-jaise processors badhte hain, parallel kaam bhi badhta jaata hai, lekin sequential kaam ka *samay* lagbhag utna hi rehta hai. Isliye, total kaam ke muqable sequential hisse ka *pratishat (percentage)* chhota hota jaata hai. Yeh batata hai ki agar problem ko scale kiya jaye, toh speedup processors ke saath lagbhag linearly badh sakta hai.

Isliye, Gustafson's Law bade-bade scientific problems ke liye zyada aashawadi aur practical view deta hai.

---

### Caches, Latency, aur Bandwidth

#### Q: Caches, latency aur bandwidth ke sandarbh (context) mein, kyun mahatvapurna hain?

**Answer**:
Caches ka mukhya kaam **latency ko kam karna (ya chhupana)** hai, na ki bandwidth badhana.

* **Latency Gap**: CPU bahut tez hai aur use data nanoseconds mein chahiye. Lekin, Main Memory (RAM) data dene mein kai guna zyada samay (latency) leti hai. Is "Processor-Memory Gap" ke kaaran CPU ko khaali baithna padta hai.
* **Cache ka Role**: Cache ek bahut tez, choti memory hai jo CPU ke paas hoti hai. Yeh un data ko rakhti hai jinki zaroorat baar-baar padti hai (Principle of Locality). Jab CPU ko data chahiye hota hai, toh woh pehle cache mein dekhta hai. Agar data wahan mil jaata hai (cache hit), toh use bahut kam latency mein data mil jaata hai.
* **Nateeja**: Cache, Main Memory ki high latency ko "hide" (chhupa) leta hai, jisse CPU ko intezar nahi karna padta. Jabki caches ki bandwidth bhi bahut high hoti hai, unka sabse bada fayda **average memory access time (latency)** ko kam karna hai.

----

**1. Task = 80s on 1 core → estimate runtime on 4 cores (perfect parallelism).**

Perfect parallelism mein, parallel runtime serial time ko cores ki sankhya se divide karke nikala jaata hai.

Parallel Time ($T_P$) = $\frac{80 \text{ seconds}}{4} = 20 \text{ seconds}$.

**Conclusion**: Perfect parallelism ke saath, 4 cores par runtime theek 4 guna kam hokar **20 seconds** ho jayega.

---

**2. Task graph: total work = 100, critical path = 25 → average concurrency.**

Average concurrency, total work ko critical path length se divide karke milti hai.

Average Concurrency = $\frac{100}{25} = 5$.

**Conclusion**: Iska matlab hai ki program ke dauran, average **5 tasks** ek saath parallel mein chal sakte hain.

---

**3. Program 100s sequential, 25s on 4 processors → compute speedup & efficiency.**

Speedup (S) = $\frac{\text{Sequential Time}}{\text{Parallel Time}} = \frac{100s}{25s} = 4$.

Efficiency (E) = $\frac{\text{Speedup}}{\text{Processors}} = \frac{4}{4} = 1$.

**Conclusion**: Program ne perfect linear speedup (**4**) aur 100% efficiency haasil ki hai, jiska matlab hai ki koi parallel overhead nahi tha.

---

**4. Parallel π-estimation → speedup = 3.2 on 4 processors → efficiency.**

Efficiency (E) = $\frac{\text{Speedup}}{\text{Processors}} = \frac{3.2}{4} = 0.8$.

**Conclusion**: Efficiency **80%** hai. Iska matlab hai ki processors apna 80% samay useful kaam mein laga rahe the, aur 20% samay parallel overheads mein kharch hua.

---

**5. Program 60s sequential, 35s on 2 cores → compute speedup & efficiency.**

Speedup (S) = $\frac{60s}{35s} \approx 1.71$.

Efficiency (E) = $\frac{1.71}{2} \approx 0.855$.

**Conclusion**: Speedup lagbhag **1.71** hai aur efficiency **85.5%** hai. Performance behtar hui hai lekin perfect nahi hai, kyunki kuch parallel overhead maujood tha.

---

**6. Amdahl’s law: 10% serial part → maximum speedup infinite processors.**

Amdahl's Law ke anusaar, maximum speedup program ke serial fraction se limited hota hai. Jab processors infinite ho jaate hain, toh parallel hisse mein lagne wala time zero ho jaata hai.

Maximum Speedup = $\frac{1}{\text{Serial Fraction}} = \frac{1}{0.10} = 10$.

**Conclusion**: Chahe aap kitne bhi processors istemal kar lein, yeh program kabhi bhi **10 guna** se zyada tez nahi ho sakta.

---

**7. Task graph: total work = 200, critical path = 40 → average concurrency.**

Average Degree of Concurrency = $\frac{\text{Total Work}}{\text{Critical Path Length}} = \frac{200}{40} = 5$.

**Conclusion**: Iska matlab hai ki poore program ke execution ke dauran, average **5 tasks** ko ek saath parallel mein chalaya ja sakta hai.

---

**8. Divide 1000 tasks among 10 processors → granularity.**

Granularity kaam ke size ko batati hai. Yahan, har processor ke hisse mein $\frac{1000 \text{ tasks}}{10 \text{ processors}} = 100$ tasks aayenge.

**Conclusion**:
* Agar yeh 1000 tasks khud bahut chhote-chhote kaam hain, toh ise **fine-grained** parallelism kehte hain.
* Agar har task apne aap mein ek bada kaam hai, toh ise **coarse-grained** parallelism kehte hain.

---

**9. DB query with 8 tables: 4 parallel + rest sequential → maximum concurrency.**

Maximum Degree of Concurrency uss point par dekhi jaati hai jahan sabse zyada kaam ek saath ho sakta hai. Is case mein, 4 tables ko ek saath parallel mein process kiya ja sakta hai.

**Conclusion**: Maximum Concurrency **4** hai. Yeh program ek samay par sabse zyada 4 processors ka hi fayda utha sakta hai.

---

**10. Program 200s sequential, 60s on 5 processors → speedup & efficiency.**

Speedup (S) = $\frac{200s}{60s} \approx 3.33$.

Efficiency (E) = $\frac{3.33}{5} \approx 0.666$.

**Conclusion**: Speedup lagbhag **3.33** hai, lekin **66.6%** ki efficiency batati hai ki lagbhag ek-tihai (one-third) samay parallel overheads mein kharch ho gaya.

----

**11. Overhead: TS = 200, total overhead time = 80 → compute To using formula.**

Total Parallel Overhead ($T_o$) ka matlab hai sabhi processors dwara milakar waste kiya gaya kul samay. Yeh samay communication, idling, ya extra computation mein kharch hota hai. Is sawaal mein, overhead ki value seedhe **80 units** di gayi hai.

**Conclusion**: Overhead Function ($T_o$) ki value **80** hai. Iska matlab hai ki 200 units ke useful kaam ke alawa, parallel system ne 80 units ka samay overheads mein kharch kiya.

---

**12. 1024 elements, 16 processors: serial = 512s, parallel = 40s → speedup & efficiency.**

Speedup (S) = $\frac{\text{Sequential Time}}{\text{Parallel Time}} = \frac{512s}{40s} = 12.8$.

Efficiency (E) = $\frac{\text{Speedup}}{\text{Processors}} = \frac{12.8}{16} = 0.8$.

**Conclusion**: 16 processors par program **12.8 guna** tez hua, aur processors **80%** efficient the.

---

**13. 2 processors: 30s → 15s runtime → is it superlinear speedup? Why/why not?**

Pehle speedup nikalte hain. Yahan 1 processor ka time 30s aur 2 processor ka time 15s hai.

Speedup (S) = $\frac{30s}{15s} = 2$.

**Conclusion**: Yeh superlinear speedup **nahi hai**. Yeh **perfect linear speedup** hai, kyunki speedup (2) processors ki sankhya (2) ke barabar hai. Superlinear speedup tab hota jab speedup 2 se *zyada* hota.

---

**14. Threaded π program: 35s seq, 10s on 4 threads → speedup & efficiency.**

Speedup (S) = $\frac{\text{Sequential Time}}{\text{Parallel Time}} = \frac{35s}{10s} = 3.5$.

Efficiency (E) = $\frac{\text{Speedup}}{\text{Threads}} = \frac{3.5}{4} = 0.875$.

**Conclusion**: Speedup **3.5** hai aur efficiency **87.5%** hai, jo batata hai ki parallel overhead kam tha aur threads ka istemal prabhavi dhang se (effectively) hua.

---

**15. False sharing: runtime grows from 8s → 20s on 8 threads → efficiency in both.**

Efficiency nikalne ke liye humein sequential time ($T_S$) chahiye. Maan lete hain ki ideal case mein (bina false sharing ke) 8 threads par 8s ka runtime milta hai, toh $T_S = 8 \times 8s = 64s$ hoga.

* **Case 1 (Bina False Sharing)**: $T_P = 8s$. Speedup = $\frac{64}{8} = 8$. Efficiency = $\frac{8}{8} = 1$ (100%).
* **Case 2 (False Sharing ke Saath)**: $T_P = 20s$. Speedup = $\frac{64}{20} = 3.2$. Efficiency = $\frac{3.2}{8} = 0.4$ (40%).

**Conclusion**: False sharing ke kaaran efficiency **100% se girkar 40%** ho gayi, jo iske gambhir performance prabhav ko darshata hai.

---

**16. 16 threads on 4 cores: sequential = 40s, parallel = 12s → efficiency.**

Efficiency hamesha physical cores ke aadhar par nikali jaati hai, threads ki sankhya par nahi.

Speedup (S) = $\frac{40s}{12s} \approx 3.33$.

Efficiency (E) = $\frac{\text{Speedup}}{\text{Cores}} = \frac{3.33}{4} \approx 0.833$.

**Conclusion**: 4 cores par program ki efficiency lagbhag **83.3%** hai.

---

**17. Cache example: 80% → 90% hit ratio with 2 processors. Cache=2ns, DRAM=100ns, remote=400ns → effective speedup.**

Pehle dono cases mein Effective Memory Access Time (EMAT) nikalte hain.

* **EMAT (1 processor)** = $(0.80 \times 2ns) + (0.20 \times 100ns) = 1.6 + 20 = 21.6 \text{ ns}$.
* **EMAT (2 processors)** = $(0.90 \times 2ns) + (0.08 \times 100ns) + (0.02 \times 400ns) = 1.8 + 8 + 8 = 17.8 \text{ ns}$.

Total Speedup = (Total Parallel Performance) / (Total Serial Performance) = $\frac{2 \times (1/17.8)}{1/21.6} = 2 \times \frac{21.6}{17.8} \approx 2.43$.

**Conclusion**: Cache hit ratio badhne ke kaaran, speedup 2 se zyada ($\approx$ **2.43**) ho gaya, jo ek superlinear speedup hai.

---

**18. DRAM: access time=70ns, cycle time=120ns → transfer rate.**

Transfer rate memory cycle time par nirbhar karta hai.

Transfer Rate = $\frac{1}{\text{Cycle Time}} = \frac{1}{120 \text{ ns}} = \frac{1}{120 \times 10^{-9} s} \approx 8.33 \times 10^6$ transfers/second.

**Conclusion**: Is DRAM ka transfer rate **8.33 MHz** hai.

---

**19. Memory hierarchy: L1=1ns (90%), L2=10ns (8%), main=100ns → average access time.**

Average access time har level ke access time aur uski probability ka weighted sum hota hai. Yahan, 90% access L1 mein, 8% L2 mein, aur baaki 2% main memory mein jaate hain.

Average Time = $(0.90 \times 1ns) + (0.08 \times 10ns) + (0.02 \times 100ns) = 0.9 + 0.8 + 2.0 = 3.7 \text{ ns}$.

**Conclusion**: Memory hierarchy ke kaaran, average memory access time 100ns se ghatkar sirf **3.7 ns** reh gaya.

---

**20. OpenMP loop: 100 iterations, 4 threads static scheduling → iterations per thread.**

Static scheduling (bina chunk size ke) iterations ko barabar aur lagatar (contiguously) hisson mein baant deta hai.

$100 \text{ iterations} / 4 \text{ threads} = 25$ iterations per thread.
* **Thread 0**: 0-24
* **Thread 1**: 25-49
* **Thread 2**: 50-74
* **Thread 3**: 75-99

**Conclusion**: Har thread ko **25 lagatar (contiguous) iterations** ka ek block milega.

---

**21. Same loop dynamic scheduling, chunk=5 → explain assignment.**

Dynamic scheduling mein, iterations ka ek pool (yahan 100/5 = 20 chunks) ban jaata hai. Jab bhi koi thread free hota hai, woh us pool se agla available 5 iterations ka chunk utha leta hai.

**Conclusion**: Kaun sa thread kaun sa chunk karega, yeh **non-deterministic** hai aur har run mein badal sakta hai. Yeh load balancing ke liye upyogi hai.

---

**22. OpenMP program: 40s seq → 12s parallel on 4 threads → speedup & efficiency.**

Speedup (S) = $\frac{40s}{12s} \approx 3.33$.

Efficiency (E) = $\frac{3.33}{4} \approx 0.833$.

**Conclusion**: Program ka speedup **3.33** aur efficiency **83.3%** hai.

---

**23. Amdahl’s law: 85% parallel, n=8 → speedup. Repeat for n=16.**

Program ka serial hissa (s) = 1 - 0.85 = 0.15.

* **For n=8**: Speedup = $\frac{1}{0.15 + \frac{0.85}{8}} = \frac{1}{0.15 + 0.10625} \approx 3.90$.
* **For n=16**: Speedup = $\frac{1}{0.15 + \frac{0.85}{16}} = \frac{1}{0.15 + 0.053125} \approx 4.92$.

**Conclusion**: Processors ko double (8 se 16) karne par bhi speedup double nahi hua. Yeh dikhata hai ki serial hissa performance gain ko limit karta hai.

---

**24. Gustafson’s law: 32 processors, sequential fraction=0.03 → scaled speedup.**

Gustafson's Law (Scaled Speedup) = $s + p \times (1 - s)$, jahan s serial fraction aur p processors ki sankhya hai.

Scaled Speedup = $0.03 + 32 \times (1 - 0.03) = 0.03 + 32 \times 0.97 = 0.03 + 31.04 = 31.07$.

**Conclusion**: Gustafson's Law ke anusaar, jab problem size ko processors ke saath badhaya jaata hai, toh **31.07 guna** ka speedup mil sakta hai, jo lagbhag linear hai.

---

**25. Latency vs bandwidth: transfer 8GB/s, latency 100ns → how many bytes transferred?**

Yeh sawaal pooch raha hai ki latency period (100 ns) ke dauraan kitna data transfer ho sakta tha.

Bytes Transferred = Bandwidth $\times$ Time
Bytes Transferred = $(8 \times 10^9 \text{ bytes/s}) \times (100 \times 10^{-9} \text{ s}) = 800 \text{ bytes}$.

**Conclusion**: 100 nanoseconds ke latency period mein, is channel se **800 bytes** data transfer ho sakta tha. Yeh darshata hai ki chhote data transfers ke liye latency ek bada factor hai.

---
## **Basic Revison opemMP**
### 1. `#pragma omp for`

* **Kya hai?**
  Loop iterations ko multiple threads mein divide karne ke liye use hota hai.

* **Kab use karte hain?**
  Jab aap chahte ho ki ek loop ki iterations parallel run ho, har thread ko kuch iterations mil jayein.

* **Kaise use karte hain?**

  ```cpp
  #pragma omp for
  for (int i = 0; i < N; i++) {
      // loop body
  }
  ```

  * Yeh directive **sirf parallel region ke andar hi** use karte hain.
  * Loop ke iterations automatically threads mein divide ho jaate hain.

---

### 2. `omp_get_thread_num()`

* **Kya hai?**
  Yeh function current thread ka ID number return karta hai.

* **Use case:**
  Agar tumhe pata karna hai ki kaunsa thread kaam kar raha hai, ya debugging/printing ke liye.

* **Example:**

  ```cpp
  int tid = omp_get_thread_num();
  printf("Thread %d\n", tid);
  ```

---

### 3. `#pragma omp parallel num_threads(4)`

* **Kya hai?**
  Yeh ek **parallel region** start karta hai jisme 4 threads run karenge.

* **Use:**

  ```cpp
  #pragma omp parallel num_threads(4)
  {
      // Yeh code 4 threads se parallel execute hoga
  }
  ```

---

### 4. `#pragma omp parallel for num_threads(4) reduction(+:total_sum)`

* **Kya hai?**

  * Yeh **parallel region** aur **for loop parallelization** dono ko combine karta hai.
  * `num_threads(4)` matlab 4 threads banenge.
  * `reduction(+:total_sum)` matlab `total_sum` variable ko safely har thread ke partial sum ko add karne ke liye use karo, taaki race condition na ho.

* **Example:**

  ```cpp
  int total_sum = 0;
  #pragma omp parallel for num_threads(4) reduction(+:total_sum)
  for (int i = 0; i < N; i++) {
      total_sum += i;
  }
  ```

  * Har thread apna partial `total_sum` rakhega.
  * Loop ke baad ye values safely combine ho jayengi.

---

### 5. `#pragma omp critical`

* **Kya hai?**
  Critical section declare karta hai — matlab jo code block uske andar hai, woh **ek time pe sirf ek thread execute karega**.

* **Kab use karna chahiye?**
  Jab shared resource ko update karna ho without race condition.

* **Kaise use karna hai?**

  ```cpp
  #pragma omp critical
  {
      // Yeh block ek time pe sirf ek thread execute karega
      shared_var++;
  }
  ```

---

### 6. `#pragma omp atomic`

* **Kya hai?**
  Atomic directive se ek **simple update operation** ko atomic banaya jata hai (jaise increment).

* **Kab use karein?**
  Jab ek chhota sa statement (like increment, addition) safe karna ho without full critical section overhead.

* **Kaise use karein?**

  ```cpp
  #pragma omp atomic
  shared_var++;
  ```

* **Note:** Atomic sirf simple statements ke liye hota hai, complex operations ke liye `critical` chahiye.

---

### Summary Table for Quick Reference:

| Directive/Function                                         | Use Case / Meaning                                    |
| ---------------------------------------------------------- | ----------------------------------------------------- |
| `#pragma omp for`                                          | Loop iterations ko threads mein divide karna          |
| `omp_get_thread_num()`                                     | Current thread ID lena                                |
| `#pragma omp parallel num_threads(4)`                      | 4 threads ka parallel region start karna              |
| `#pragma omp parallel for num_threads(4) reduction(+:var)` | Parallel for with 4 threads + safe variable reduction |
| `#pragma omp critical`                                     | Critical section for exclusive access                 |
| `#pragma omp atomic`                                       | Atomic operation (e.g., increment)                    |

---




**1. Two threads update shared counter without synchronization → issue.**

```cpp
#include <iostream>
#include <pthread.h>

#define NUM_THREADS 2
#define LOOPS 1000000

// Yeh ek shared variable hai jise dono threads access karenge
int counter = 0;

void* worker(void* arg) {
    // Har thread counter ko 1 million baar increment karega
    for (int i = 0; i < LOOPS; i++) {
        // --- RACE CONDITION YAHAN HOTI HAI ---
        // counter++ operation atomic nahi hai. Iske 3 steps hote hain:
        // 1. Memory se counter ki value ko register mein padhna.
        // 2. Register ki value ko increment karna.
        // 3. Register ki nayi value ko memory mein wapas likhna.
        // Agar OS ek thread ko in 3 steps ke beech mein rok de, toh "lost updates" ho sakte hain.
        counter++;
    }
    return NULL;
}

int main() {
    pthread_t threads[NUM_THREADS];

    for (int i = 0; i < NUM_THREADS; i++) {
        pthread_create(&threads[i], NULL, worker, NULL);
    }

    for (int i = 0; i < NUM_THREADS; i++) {
        pthread_join(threads[i], NULL);
    }

    std::cout << "Expected counter value: " << NUM_THREADS * LOOPS << std::endl;
    std::cout << "Actual counter value:   " << counter << std::endl;

    return 0;
}
```


```cpp

//updated code where now mutex is also used
#include <iostream>
#include <pthread.h>

#define NUM_THREADS 2
#define LOOPS 1000000

int counter = 0;
pthread_mutex_t lock;  // Mutex declaration

void* worker(void* arg) {
    for (int i = 0; i < LOOPS; i++) {
        pthread_mutex_lock(&lock);   // Lock before updating counter
        counter++;
        pthread_mutex_unlock(&lock); // Unlock after updating counter
    }
    return NULL;
}

int main() {
    pthread_t threads[NUM_THREADS];

    pthread_mutex_init(&lock, NULL);  // Initialize mutex

    for (int i = 0; i < NUM_THREADS; i++) {
        pthread_create(&threads[i], NULL, worker, NULL);
    }

    for (int i = 0; i < NUM_THREADS; i++) {
        pthread_join(threads[i], NULL);
    }

    pthread_mutex_destroy(&lock);  // Destroy mutex

    std::cout << "Expected counter value: " << NUM_THREADS * LOOPS << std::endl;
    std::cout << "Actual counter value:   " << counter << std::endl;

    return 0;
}

```

### `pthread_mutex_t lock;` - **Mutex variable declare karta hai jo lock/unlock ke liye use hoga.**

### `pthread_mutex_init(&lock, NULL);` - **Mutex ko initialize karta hai, ready kar deta hai use karne ke liye.**

### `pthread_mutex_lock(&lock);` - **Lock lagata hai — dusre threads ko rokta hai jab tak current thread kaam khatam nahi karta.**

### `pthread_mutex_unlock(&lock);` - **Lock hata deta hai — dusre threads ko access dene ke liye.**

### `pthread_mutex_destroy(&lock);` - **Mutex ko clean-up karta hai, use free kar deta hai program ke end mein.**

**Expected Conclusion:**
Program ka output har baar alag-alag aa sakta hai, aur `Actual counter value` hamesha `Expected counter value` (2,000,000) se kam hoga. Yeh **Race Condition** ke kaaran hota hai, jahan threads ke read-modify-write operations aapas mein galat tarike se interleave ho jaate hain, jisse kuch increments "lost" ho jaate hain.

-----

**2. Divide loop of 100 iterations equally among 4 processes.(both pthread and openmp seperately)**

**Pthreads Version (Manual Division)**

```cpp
#include <iostream>
#include <pthread.h>

#define NUM_THREADS 4
#define NUM_ITERATIONS 100

void* worker(void* arg) {
    long thread_id = (long)arg;

    // Har thread ke liye loop ka start aur end index manually calculate karna.
    int iterations_per_thread = NUM_ITERATIONS / NUM_THREADS;
    int start = thread_id * iterations_per_thread;
    int end = start + iterations_per_thread;

    // Har thread apne hisse ki iterations par kaam karega.
    for (int i = start; i < end; i++) {
        printf("Thread %ld is processing iteration %d\n", thread_id, i);
    }
    return NULL;
}

int main() {
    pthread_t threads[NUM_THREADS];
    for (long i = 0; i < NUM_THREADS; i++) {
        // Har thread ko uski unique ID (0, 1, 2, 3) pass ki ja rahi hai.
        pthread_create(&threads[i], NULL, worker, (void*)i);
    }
    for (int i = 0; i < NUM_THREADS; i++) {
        pthread_join(threads[i], NULL);
    }
    return 0;
}
```

**OpenMP Version (Automatic Division)**

```cpp
#include <iostream>
#include <omp.h>

#define NUM_ITERATIONS 100

int main() {
    // OpenMP ko bataya gaya hai ki 4 threads ka istemal karna hai.
    #pragma omp parallel num_threads(4)
    {
        // '#pragma omp for' directive loop ki iterations ko
        // threads ke beech apne aap, barabar baant dega.
        #pragma omp for
        for (int i = 0; i < NUM_ITERATIONS; i++) {
            printf("Thread %d is processing iteration %d\n", omp_get_thread_num(), i);
        }
    } // Implicit barrier yahan hai, sabhi threads intezar karenge.
    return 0;
}
```

**Expected Conclusion:**
Dono hi cases mein, 100 iterations ko 4 threads ke beech 25-25 ke group mein baanta jayega. Pthreads mein yeh kaam manually karna padta hai, jismein galti ho sakti hai. Jabki OpenMP mein `#pragma omp for` directive yeh kaam apne aap kar deta hai, jo ki zyada aasan aur surakshit hai.

-----

**3. Parallel summation of 8 numbers using 4 processors (binary tree reduction).(both pthread and openmp seperately)**

**Pthreads Version (Manual Reduction with Barriers)**

```cpp
#include <iostream>
#include <pthread.h>

#define NUM_THREADS 4
#define NUM_ELEMENTS 8

int data[NUM_ELEMENTS] = {1, 2, 3, 4, 5, 6, 7, 8};
int partial_sums[NUM_THREADS];
pthread_barrier_t barrier;

void* worker(void* arg) {
    long id = (long)arg;
    int chunk_size = NUM_ELEMENTS / NUM_THREADS;
    int start = id * chunk_size;
    int end = start + chunk_size;

    // Step 1: Har thread apne hisse ka local sum nikalega.
    int local_sum = 0;
    for (int i = start; i < end; i++) {
        local_sum += data[i];
    }
    partial_sums[id] = local_sum;

    // Barrier: Sabhi threads ko local sum calculate karne tak intezar karwayega.
    pthread_barrier_wait(&barrier);

    // Step 2: Binary tree fashion mein sums ko combine karna.
    // Sirf aadhe threads (0 aur 2) agle level par kaam karenge.
    if (id % 2 == 0) {
        partial_sums[id] += partial_sums[id + 1];
    }
    pthread_barrier_wait(&barrier);

    // Step 3: Aakhiri combination. Sirf thread 0 final sum nikalega.
    if (id == 0) {
        partial_sums[0] += partial_sums[2];
    }

    return NULL;
}

int main() {
    pthread_t threads[NUM_THREADS];
    pthread_barrier_init(&barrier, NULL, NUM_THREADS); // 4 threads ke liye barrier.

    for (long i = 0; i < NUM_THREADS; i++) {
        pthread_create(&threads[i], NULL, worker, (void*)i);
    }
    for (int i = 0; i < NUM_THREADS; i++) {
        pthread_join(threads[i], NULL);
    }

    // Final result thread 0 ke partial_sums[0] mein hoga.
    std::cout << "Final Sum: " << partial_sums[0] << std::endl;
    pthread_barrier_destroy(&barrier);
    return 0;
}
```

**OpenMP Version (Using Reduction Clause)**

```cpp
#include <iostream>
#include <omp.h>

#define NUM_ELEMENTS 8

int main() {
    int data[NUM_ELEMENTS] = {1, 2, 3, 4, 5, 6, 7, 8};
    int total_sum = 0;

    // OpenMP ka 'reduction' clause jaadu jaisa kaam karta hai.
    // 1. Yeh har thread ke liye 'total_sum' ka ek private (local) copy banata hai.
    // 2. Har thread apne hisse ke numbers ko apni private copy mein jodta hai.
    // 3. Loop khatam hone ke baad, OpenMP sabhi private copies ko '+' operator
    //    se jodkar final result original 'total_sum' mein daal deta hai.
    #pragma omp parallel for num_threads(4) reduction(+:total_sum)
    for (int i = 0; i < NUM_ELEMENTS; i++) {
        total_sum += data[i];
    }

    std::cout << "Final Sum: " << total_sum << std::endl;
    return 0;
}
```

**Expected Conclusion:**
Dono programs 8 numbers ka jod (36) nikalenge. Pthreads version mein reduction ko manually implement karna padta hai, jiske liye complex synchronization (barriers) ki zaroorat hoti hai. OpenMP ka `reduction` clause isi kaam ko sirf ek line mein, bina galti ke, aur bahut efficiently kar deta hai.

-----

**4. C++ style pseudocode with `pthread_create` launching 2 threads.**

```cpp
#include <iostream>
#include <pthread.h> // Pthreads library

// Yeh function naye threads execute karenge.
// void* return type aur void* argument Pthread standard hai.
void* worker_function(void* arg) {
    long thread_id = (long)arg;
    std::cout << "Hello from worker thread ID: " << thread_id << std::endl;

    // Thread apna kaam yahan karega.

    // Kaam khatam hone par thread exit ho jayega.
    return NULL;
}

int main() {
    // Threads ke liye identifiers.
    pthread_t thread1, thread2;

    std::cout << "Main thread: Creating worker threads." << std::endl;

    // Pehla thread banana, use ID 1 pass karna.
    pthread_create(&thread1, NULL, worker_function, (void*)1);

    // Doosra thread banana, use ID 2 pass karna.
    pthread_create(&thread2, NULL, worker_function, (void*)2);

    // Main thread worker threads ke khatam hone ka intezar karega.
    // Agar join nahi karenge, toh main thread pehle exit ho sakta hai.
    pthread_join(thread1, NULL);
    pthread_join(thread2, NULL);

    std::cout << "Main thread: Both worker threads have finished." << std::endl;

    return 0;
}
```

**Expected Conclusion:**
Yeh code C++ mein Pthreads ka basic structure dikhata hai. `main` function do worker threads banata hai, unhe ek unique ID pass karta hai, aur fir `pthread_join` ka istemal karke unke kaam poora karne ka intezar karta hai. Isse yeh sunishchit hota hai ki main program worker threads ke kaam poora karne se pehle band na ho.

-----

**5. Two threads increment global variable without lock → problem.**

**Pthreads Version**

```cpp
#include <pthread.h>
#include <stdio.h>

long long global_var = 0;

void* worker(void* arg) {
    for (int i = 0; i < 1000000; i++) {
        // PROBLEM: Race condition.
        // Yeh operation atomic nahi hai, isliye lost updates honge.
        global_var++;
    }
    return NULL;
}

// Main function (threads banayega aur join karega)...
```

**OpenMP Version**

```cpp
#include <omp.h>
#include <stdio.h>

long long global_var = 0;

int main() {
    // global_var shared hai, isliye race condition hogi.
    #pragma omp parallel num_threads(2)
    {
        for (int i = 0; i < 1000000; i++) {
            // PROBLEM: Race condition.
            // Dono threads ek hi samay par is variable ko update karne ki koshish karenge.
            global_var++;
        }
    }
    printf("Final value: %lld\n", global_var); // Expected 2,000,000
    return 0;
}
```

**Expected Conclusion:**
Dono hi cases mein, `global_var` ki final value expected value (2,000,000) se kam hogi. Aisa isliye hai kyunki dono threads ek hi shared variable ko bina kisi lock ya synchronization ke update kar rahe hain, jisse **race condition** paida hoti hai aur kuch increments overwrite ho jaate hain.

-----

**6. Modify with mutex lock to solve above.**

**Pthreads Version (with Mutex)**

```cpp
#include <pthread.h>
#include <stdio.h>

long long global_var = 0;
pthread_mutex_t lock; // Mutex declare karna.

void* worker(void* arg) {
    for (int i = 0; i < 1000000; i++) {
        // Lock lagana taaki ek samay par ek hi thread andar aa sake.
        pthread_mutex_lock(&lock);
        global_var++; // Yeh ab ek critical section hai, jo safe hai.
        pthread_mutex_unlock(&lock); // Kaam hote hi lock chhod dena.
    }
    return NULL;
}

int main() {
    pthread_mutex_init(&lock, NULL); // Mutex ko initialize karna.
    // ... threads create aur join karne ka code ...
    printf("Final value: %lld\n", global_var);
    pthread_mutex_destroy(&lock);
    return 0;
}
```

**OpenMP Version (with Critical Section)**

```cpp
#include <omp.h>
#include <stdio.h>

long long global_var = 0;

int main() {
    #pragma omp parallel num_threads(2)
    {
        for (int i = 0; i < 1000000; i++) {
            // #pragma omp critical batata hai ki neeche ka block
            // ek samay par sirf ek hi thread chala sakta hai.
            #pragma omp critical
            {
                global_var++; // Yeh ab safe hai.
            }
        }
    }
    printf("Final value: %lld\n", global_var);
    return 0;
}
```

**Expected Conclusion:**
Ab dono hi cases mein, `global_var` ki final value hamesha correct (2,000,000) aayegi. Pthreads mein `pthread_mutex_lock` aur OpenMP mein `#pragma omp critical` ka istemal karke humne update operation ko ek **critical section** bana diya hai, jisse race condition khatam ho jaati hai.

-----

**7. Splitting 1D array addition problem into 4 tasks for 4 processors.**

**Pthreads Version (Manual Splitting)**

```cpp
#include <pthread.h>
#define SIZE 1024
#define NUM_THREADS 4

int A[SIZE], B[SIZE], C[SIZE]; // Assume A aur B initialized hain.

void* add_vectors(void* arg) {
    long id = (long)arg;
    int chunk_size = SIZE / NUM_THREADS;
    int start = id * chunk_size;
    int end = start + chunk_size;

    // Har thread array ke apne hisse par C[i] = A[i] + B[i] karega.
    for (int i = start; i < end; i++) {
        C[i] = A[i] + B[i];
    }
    return NULL;
}

// Main function 4 threads banayega aur unhe 0, 1, 2, 3 ID dega.
```

**OpenMP Version (Automatic Splitting)**

```cpp
#include <omp.h>
#define SIZE 1024

int A[SIZE], B[SIZE], C[SIZE]; // Assume A aur B initialized hain.

int main() {
    // OpenMP apne aap loop ko 4 threads mein baant dega.
    #pragma omp parallel for num_threads(4)
    for (int i = 0; i < SIZE; i++) {
        C[i] = A[i] + B[i];
    }
    return 0;
}
```

**Expected Conclusion:**
Yeh ek "embarrassingly parallel" problem hai kyunki har calculation (`C[i]`) doosre se poori tarah independent hai. Dono hi tareeke sahi result denge. OpenMP ka istemal code ko bahut chhota aur saaf-suthra rakhta hai, jabki Pthreads mein kaam ko manually baantna padta hai.


---

**8. Pseudocode for DB query (`MODEL="Civic" AND YEAR=2001`) in parallel using 2 subtasks.**

**Pthreads Version (Pseudocode)**

```cpp
#include <iostream>
#include <vector>
#include <pthread.h>
#include <algorithm> // for set_intersection

// Assume 'full_database' ek global vector hai jismein sabhi cars ka data hai.
vector<Car> civics_list;
vector<Car> year_2001_list;
pthread_mutex_t civics_lock, year_lock; // Results list ko protect karne ke liye locks

void* find_civics(void* arg) {
    // Database ko scan karke sirf "Civic" model ki cars dhundna.
    for (const auto& car : full_database) {
        if (car.model == "Civic") {
            pthread_mutex_lock(&civics_lock);
            civics_list.push_back(car);
            pthread_mutex_unlock(&civics_lock);
        }
    }
    return NULL;
}

void* find_2001_cars(void* arg) {
    // Database ko scan karke sirf 2001 model ki cars dhundna.
    for (const auto& car : full_database) {
        if (car.year == 2001) {
            pthread_mutex_lock(&year_lock);
            year_2001_list.push_back(car);
            pthread_mutex_unlock(&year_lock);
        }
    }
    return NULL;
}

int main() {
    pthread_t thread1, thread2;
    // ... mutex init ...

    // Dono tasks ko parallel mein launch karna.
    pthread_create(&thread1, NULL, find_civics, NULL);
    pthread_create(&thread2, NULL, find_2001_cars, NULL);

    // Dono threads ke khatam hone ka intezar karna.
    pthread_join(thread1, NULL);
    pthread_join(thread2, NULL);

    // Step 3: Dono results ka intersection nikalna (yeh sequential hai).
    vector<Car> final_result;
    std::sort(civics_list.begin(), civics_list.end()); // Intersection ke liye sort karna zaroori hai
    std::sort(year_2001_list.begin(), year_2001_list.end());
    
    std::set_intersection(civics_list.begin(), civics_list.end(),
                          year_2001_list.begin(), year_2001_list.end(),
                          back_inserter(final_result));

    std::cout << "Found " << final_result.size() << " cars matching the criteria." << std::endl;
    // ... mutex destroy ...
    return 0;
}
```

**OpenMP Version (Pseudocode)**

```cpp
#include <iostream>
#include <vector>
#include <omp.h>
#include <algorithm>

// ... Car struct aur full_database ...

int main() {
    vector<Car> civics_list;
    vector<Car> year_2001_list;

    // 'sections' directive ka istemal karke dono tasks ko parallel chalana.
    #pragma omp parallel sections
    {
        #pragma omp section
        {
            // Task 1: Sirf "Civic" model ki cars dhundna.
            for (const auto& car : full_database) {
                if (car.model == "Civic") {
                    // Critical section, kyunki vector thread-safe nahi hai.
                    #pragma omp critical
                    civics_list.push_back(car);
                }
            }
        }

        #pragma omp section
        {
            // Task 2: Sirf 2001 model ki cars dhundna.
            for (const auto& car : full_database) {
                if (car.year == 2001) {
                    #pragma omp critical
                    year_2001_list.push_back(car);
                }
            }
        }
    } // Implicit barrier yahan hai, dono sections khatam hone tak intezar karega.

    // Step 3: Dono results ka intersection nikalna.
    vector<Car> final_result;
    // ... sorting aur set_intersection ka code ...
    
    std::cout << "Found " << final_result.size() << " cars matching the criteria." << std::endl;
    return 0;
}
```

**Expected Conclusion:**
Yeh "functional parallelism" ka example hai. Query ke do independent hisson (`MODEL="Civic"` aur `YEAR=2001`) ko parallel mein execute kiya jaata hai. Jab dono kaam poore ho jaate hain, tab unke results ko combine (`AND` operation) karke final answer nikala jaata hai. OpenMP ka `sections` directive is kaam ke liye Pthreads se zyada aasan aur saaf-suthra hai.

-----

**9. Binary tree reduction for summing numbers using 8 processors.**

**Pthreads Version (Pseudocode with Barriers)**

```cpp
#include <pthread.h>
#include <iostream>

#define NUM_THREADS 8
int data[NUM_THREADS] = {10, 20, 30, 40, 50, 60, 70, 80}; // Har processor ke liye ek number
pthread_barrier_t barrier;

void* reduce_sum(void* arg) {
    long id = (long)arg;

    // Total 3 steps (log2(8) = 3)
    // Step 1: Har 2 threads ka pair aapas mein sum karega.
    if (id % 2 == 0) {
        data[id] += data[id + 1];
    }
    pthread_barrier_wait(&barrier); // Sabhi ke Step 1 khatam hone ka intezar.

    // Step 2: Naye pairs aapas mein sum karenge.
    if (id % 4 == 0) {
        data[id] += data[id + 2];
    }
    pthread_barrier_wait(&barrier); // Sabhi ke Step 2 khatam hone ka intezar.

    // Step 3: Aakhiri 2 results aapas mein sum karenge.
    if (id == 0) {
        data[0] += data[4];
    }
    return NULL;
}

int main() {
    pthread_t threads[NUM_THREADS];
    pthread_barrier_init(&barrier, NULL, NUM_THREADS);

    for (long i = 0; i < NUM_THREADS; i++) pthread_create(&threads[i], NULL, reduce_sum, (void*)i);
    for (int i = 0; i < NUM_THREADS; i++) pthread_join(threads[i], NULL);

    std::cout << "Final sum is: " << data[0] << std::endl; // Result data[0] mein hoga.
    pthread_barrier_destroy(&barrier);
    return 0;
}
```

**OpenMP Version (Using `reduction`)**

```cpp
#include <iostream>
#include <omp.h>
#include <numeric> // for std::accumulate

#define NUM_ELEMENTS 8

int main() {
    int data[NUM_ELEMENTS] = {10, 20, 30, 40, 50, 60, 70, 80};
    int total_sum = 0;

    // OpenMP ka reduction clause yeh sabse aasan tarike se kar deta hai.
    // Underlying implementation efficient hoti hai, jaise binary tree reduction.
    #pragma omp parallel for num_threads(8) reduction(+:total_sum)
    for (int i = 0; i < NUM_ELEMENTS; i++) {
        total_sum += data[i];
    }
    
    // Sirf verification ke liye sequential sum.
    // int expected_sum = std::accumulate(data, data + NUM_ELEMENTS, 0);

    std::cout << "Final sum is: " << total_sum << std::endl;
    return 0;
}
```

**Expected Conclusion:**
Dono hi program sahi sum (360) nikalenge. Pthreads mein binary tree reduction ko manually implement karna padta hai, jiske liye kai stages par barriers ki zaroorat hoti hai. Yeh complex aur error-prone ho sakta hai. OpenMP ka `reduction` clause isi concept ko bahut aasaani se aur efficiently implement kar deta hai, jisse programmer ko complexity se bachaya jaata hai.

-----

**10. Pseudocode for measuring parallel execution time `TP` of sorting algorithm.**

**Pthreads Version**

```cpp
#include <pthread.h>
#include <sys/time.h> // for gettimeofday

// ... Sorting function 'parallel_sort' ke liye worker function ...

int main() {
    // ... Data initialize karna ...
    pthread_t threads[NUM_THREADS];
    struct timeval start_time, end_time;

    // --- Timing shuru karna ---
    gettimeofday(&start_time, NULL);

    // Sabhi sorting threads ko launch karna.
    for (long i = 0; i < NUM_THREADS; i++) {
        pthread_create(&threads[i], NULL, sort_worker, (void*)i);
    }

    // Sabhi threads ke khatam hone ka intezar karna.
    for (int i = 0; i < NUM_THREADS; i++) {
        pthread_join(threads[i], NULL);
    }

    // --- Timing khatam karna ---
    gettimeofday(&end_time, NULL);

    // Total time calculate karna seconds mein.
    double tp = (end_time.tv_sec - start_time.tv_sec) +
                (end_time.tv_usec - start_time.tv_usec) / 1000000.0;
    
    printf("Parallel Execution Time (TP): %f seconds\n", tp);
    return 0;
}
```

**OpenMP Version**

```cpp
#include <omp.h>
#include <stdio.h>

// ... Data initialize karna ...

int main() {
    double start_time, end_time;

    // --- Timing shuru karna OpenMP ke function se ---
    start_time = omp_get_wtime();

    #pragma omp parallel
    {
        // Parallel sorting ka logic yahan aayega.
        // For example, #pragma omp for ...
    }

    // --- Timing khatam karna ---
    end_time = omp_get_wtime();

    double tp = end_time - start_time;
    printf("Parallel Execution Time (TP): %f seconds\n", tp);
    return 0;
}
```

**Expected Conclusion:**
Parallel execution time ($T\_P$) ko naapne ke liye, hum parallel kaam shuru hone se theek pehle time note karte hain aur sabhi parallel kaam ke khatam hone ke theek baad. Pthreads mein, yeh `pthread_create` se pehle aur `pthread_join` ke baad kiya jaata hai. OpenMP `omp_get_wtime()` function deta hai jo is kaam ke liye standard aur aasan tarika hai.

-----

**11. Create 3 threads using `pthread_create`.**

```cpp
#include <iostream>
#include <pthread.h>

void* worker(void* arg) {
    long id = (long)arg;
    std::cout << "Thread " << id << " is running." << std::endl;
    // ... thread apna kaam karega ...
    return NULL;
}

int main() {
    pthread_t thread_handles[3]; // 3 threads ke liye handles

    std::cout << "Main: Creating 3 threads." << std::endl;
    
    // Ek loop mein 3 threads banana.
    for (long i = 0; i < 3; i++) {
        pthread_create(&thread_handles[i], NULL, worker, (void*)i);
    }

    // Unke khatam hone ka intezar karna.
    for (int i = 0; i < 3; i++) {
        pthread_join(thread_handles[i], NULL);
    }
    
    std::cout << "Main: All 3 threads finished." << std::endl;
    return 0;
}
```

**Expected Conclusion:**
Yeh code 3 worker threads banata hai. `main` thread `pthread_create` ka istemal karke unhe launch karta hai aur fir `pthread_join` ka istemal karke yeh sunishchit karta hai ki program tabhi band ho jab sabhi 3 threads apna kaam poora kar chuke hon.

-----

**12. Modify above to ensure mutual exclusion using mutex when updating shared var.**

```cpp
#include <iostream>
#include <pthread.h>

int shared_counter = 0; // Shared variable
pthread_mutex_t my_mutex; // Mutex

void* worker(void* arg) {
    long id = (long)arg;
    std::cout << "Thread " << id << " is running." << std::endl;
    
    // Shared variable ko update karne se pehle lock lagana.
    pthread_mutex_lock(&my_mutex);
    
    // --- Critical Section Start ---
    shared_counter++;
    std::cout << "Thread " << id << " updated counter to " << shared_counter << std::endl;
    // --- Critical Section End ---

    // Lock ko chhod dena taaki doosre threads use kar sakein.
    pthread_mutex_unlock(&my_mutex);
    
    return NULL;
}

int main() {
    pthread_t thread_handles[3];

    // Mutex ko istemal karne se pehle initialize karna zaroori hai.
    pthread_mutex_init(&my_mutex, NULL);
    
    std::cout << "Main: Creating 3 threads." << std::endl;
    for (long i = 0; i < 3; i++) {
        pthread_create(&thread_handles[i], NULL, worker, (void*)i);
    }
    for (int i = 0; i < 3; i++) {
        pthread_join(thread_handles[i], NULL);
    }
    
    std::cout << "Main: All threads finished. Final counter: " << shared_counter << std::endl;
    
    // Mutex ko destroy karna.
    pthread_mutex_destroy(&my_mutex);
    
    return 0;
}
```

**Expected Conclusion:**
`pthread_mutex_lock` aur `pthread_mutex_unlock` ka istemal karke humne `shared_counter++` operation ko ek critical section bana diya hai. Isse yeh sunishchit hota hai ki ek samay par sirf ek hi thread shared variable ko update kar sakta hai, jisse race condition khatam ho jaati hai aur final result hamesha correct (3) aata hai.

-----

**13. Pseudocode showing race condition on `best_cost`.**

```cpp
// Global shared variable
int best_cost = 100;

// Yeh code do alag-alag threads mein chal raha hai.
// Thread 1:
void thread1_function() {
    int my_cost = 50;

    // Step 1: Thread 1 best_cost (100) ko padhta hai.
    // Condition (50 < 100) true hoti hai.
    if (my_cost < best_cost) {
        // <<<<< CONTEXT SWITCH: OS Thread 1 ko yahan rok deta hai >>>>>

        // Step 4: Thread 1 aakhir mein likhta hai.
        best_cost = my_cost; // best_cost ko 50 kar deta hai.
    }
}

// Thread 2:
void thread2_function() {
    int my_cost = 75;

    // Step 2: Thread 2 best_cost (abhi bhi 100) ko padhta hai.
    // Condition (75 < 100) true hoti hai.
    if (my_cost < best_cost) {
        // Step 3: Thread 2 pehle likhta hai.
        best_cost = my_cost; // best_cost ko 75 kar deta hai.
    }
}
```

**Expected Conclusion:**
Is execution scenario mein:

1.  Thread 1 condition check karta hai (50 \< 100 is true).
2.  OS Thread 1 ko rok kar Thread 2 ko chalata hai.
3.  Thread 2 condition check karta hai (75 \< 100 is true, kyunki Thread 1 ne abhi tak likha nahi hai).
4.  Thread 2 `best_cost` ko 75 kar deta hai.
5.  Baad mein, Thread 1 dobara chalta hai aur `best_cost` ko 50 kar deta hai.

Is case mein final result 50 (sahi) hai. Lekin, agar Step 3 aur 4 ka order badal jaaye (Thread 1 pehle likhe), toh `best_cost` pehle 50 hoga, fir Thread 2 uspar 75 overwrite kar dega, jisse final result 75 (galat) aayega. Yahi **race condition** hai, jahan final result threads ke execution order par depend karta hai.


---
**14. Pseudocode for caching (temporal locality).(both pthread and openmp seperately)**

**Pthreads Version**

```cpp
#include <iostream>
#include <map>
#include <pthread.h>
#include <unistd.h> // for sleep

// Cache ko represent karne ke liye ek map (Key -> Value)
std::map<int, std::string> cache;
pthread_mutex_t cache_lock; // Cache ko protect karne ke liye mutex

// Slow main memory se data fetch karne ka simulation
std::string read_from_db(int key) {
    sleep(1); // Assume 1 second ki latency
    return "data_for_" + std::to_string(key);
}

// Thread-safe get_data function
std::string get_data(int key) {
    pthread_mutex_lock(&cache_lock); // Cache access se pehle lock lagana

    // Step 1: Cache mein data dhundna
    if (cache.find(key) != cache.end()) {
        // --- CACHE HIT ---
        // Data cache mein mil gaya, tezi se return karna.
        // Yahi hai temporal locality ka fayda.
        std::cout << "Thread " << pthread_self() << ": Cache HIT for key " << key << std::endl;
        std::string data = cache[key];
        pthread_mutex_unlock(&cache_lock);
        return data;
    }

    // --- CACHE MISS ---
    // Data cache mein nahi mila.
    std::cout << "Thread " << pthread_self() << ": Cache MISS for key " << key << std::endl;
    // Step 2: Slow DB se data fetch karna
    std::string data = read_from_db(key);
    // Step 3: Future ke liye data ko cache mein store karna
    cache[key] = data;

    pthread_mutex_unlock(&cache_lock); // Kaam khatam hone par lock chhodna
    return data;
}

// ... main function to launch threads that call get_data() ...
```

**OpenMP Version**

```cpp
#include <iostream>
#include <map>
#include <omp.h>
#include <unistd.h>

std::map<int, std::string> cache;
// Ismein explicit mutex ke bajaye OpenMP ka critical directive use karenge.

std::string read_from_db(int key) { /* ... same as above ... */ }

std::string get_data_omp(int key) {
    std::string data;
    bool found_in_cache = false;

    // Critical section sirf cache ko read karne ke liye.
    #pragma omp critical
    {
        if (cache.find(key) != cache.end()) {
            data = cache[key];
            found_in_cache = true;
        }
    }

    if (found_in_cache) {
        std::cout << "Thread " << omp_get_thread_num() << ": Cache HIT for key " << key << std::endl;
        return data;
    }

    // Cache miss, DB se read karna (yeh critical section ke bahar hai).
    std::cout << "Thread " << omp_get_thread_num() << ": Cache MISS for key " << key << std::endl;
    data = read_from_db(key);

    // Cache ko update karne ke liye dobara critical section.
    #pragma omp critical
    {
        cache[key] = data;
    }
    return data;
}

// ... main function with #pragma omp parallel for to call get_data_omp() ...
```

**Expected Conclusion:**
Temporal locality ka fayda uthane ke liye caching ek powerful technique hai. Jab ek data item baar-baar access hota hai, toh use slow memory se laane ke bajaye fast cache se serve kiya jaata hai. Parallel environment mein, cache ek shared resource ban jaata hai, isliye uske access ko **thread-safe** banana zaroori hai. Pthreads mein yeh `pthread_mutex_t` se hota hai aur OpenMP mein `#pragma omp critical` se.

-----

**15. Pseudocode for spatial locality (loop through array sequentially).(both pthread and openmp seperately)**

**Pthreads Version**

```cpp
#include <pthread.h>
#define SIZE 1000
#define NUM_THREADS 4

int array[SIZE];

void* worker(void* arg) {
    long id = (long)arg;
    int chunk_size = SIZE / NUM_THREADS;
    int start = id * chunk_size;
    int end = start + chunk_size;

    // Har thread array ke ek lagatar (contiguous) block par kaam kar raha hai.
    // Jab thread array[i] ko access karta hai, toh cache system array[i+1], array[i+2], etc.
    // ko pehle se hi fetch kar leta hai (prefetching). Yahi spatial locality hai.
    for (int i = start; i < end; i++) {
        array[i] *= 2; // Process the element
    }
    return NULL;
}

// ... main function to launch 4 threads ...
```

**OpenMP Version**

```cpp
#include <omp.h>
#define SIZE 1000

int array[SIZE];

int main() {
    // OpenMP 'for' directive by default (static schedule) loop ko
    // lagatar (contiguous) chunks mein baant deta hai.
    // Isse har thread ko array ka ek a-ke-baad-ek hissa milta hai,
    // jisse spatial locality maintain rehti hai.
    #pragma omp parallel for num_threads(4)
    for (int i = 0; i < SIZE; i++) {
        array[i] *= 2;
    }
    return 0;
}
```

**Expected Conclusion:**
Spatial locality ka matlab hai ki agar ek memory location access hua hai, toh uske aas-paas ke locations bhi jald hi access honge. Arrays par sequentially loop karna iska sabse aacha example hai. Parallel programs mein performance ke liye zaroori hai ki har thread ko array ka ek **contiguous chunk** diya jaaye. Aisa karne se CPU ka cache aur hardware prefetcher aache se kaam karte hain, jisse memory access tez ho jaata hai.

-----

**16. OpenMP code for array sum using reduction.**

```cpp
#include <iostream>
#include <omp.h>

#define SIZE 1000

int main() {
    int array[SIZE];
    long long total_sum = 0;

    // Array ko initialize karna (e.g., sabhi elements 1 hain)
    for (int i = 0; i < SIZE; i++) {
        array[i] = 1;
    }

    // reduction(+:total_sum) OpenMP ko batata hai:
    // 1. Har thread ke liye 'total_sum' ka ek private, zero-initialized copy banao.
    // 2. Har thread apne hisse ke array elements ko apni private copy mein jode.
    // 3. Loop khatam hone par, sabhi private copies ko jodkar original 'total_sum' mein daal do.
    #pragma omp parallel for reduction(+:total_sum)
    for (int i = 0; i < SIZE; i++) {
        total_sum += array[i];
    }

    std::cout << "The total sum is: " << total_sum << std::endl;
    return 0;
}
```

**Expected Conclusion:**
OpenMP mein `reduction` clause parallel sum, product, max, min, etc., nikalne ka sabse aasan, surakshit aur prabhavi (efficient) tarika hai. Yeh race condition se bachata hai aur programmer ko manual locking ki complexity se mukt karta hai.

-----

**17. OpenMP code for running `task1()` and `task2()` in parallel using sections.**

```cpp
#include <iostream>
#include <omp.h>
#include <unistd.h> // for sleep

void task1() {
    std::cout << "Task 1 starting on thread " << omp_get_thread_num() << std::endl;
    sleep(2); // Maan lijiye Task 1 ko 2 seconds lagte hain
    std::cout << "Task 1 finished." << std::endl;
}

void task2() {
    std::cout << "Task 2 starting on thread " << omp_get_thread_num() << std::endl;
    sleep(2); // Maan lijiye Task 2 ko bhi 2 seconds lagte hain
    std::cout << "Task 2 finished." << std::endl;
}

int main() {
    double start = omp_get_wtime();

    // 'parallel sections' ek team banata hai aur har 'section' ko
    // ek alag available thread ko de deta hai.
    #pragma omp parallel sections
    {
        #pragma omp section
        {
            task1();
        }

        #pragma omp section
        {
            task2();
        }
    }
    // Is block ke end mein ek implicit barrier hai.

    double end = omp_get_wtime();
    std::cout << "Total time taken: " << (end - start) << " seconds." << std::endl;

    return 0;
}
```

**Expected Conclusion:**
Yeh program `task1()` aur `task2()` ko alag-alag threads par ek saath chalayega. Kyunki dono tasks parallel mein chal rahe hain aur dono 2 seconds lete hain, isliye total execution time bhi lagbhag **2 seconds** hoga (4 seconds nahi). Yeh functional parallelism ka ek aacha example hai, jahan alag-alag kaam ek saath kiye jaate hain.

-----

**18. OpenMP code ensuring only one thread prints "Hello World" using single directive.**

```cpp
#include <iostream>
#include <omp.h>

int main() {
    #pragma omp parallel num_threads(4)
    {
        // Yeh line sabhi 4 threads print karenge.
        printf("Thread %d says: I am in the parallel region.\n", omp_get_thread_num());

        // '#pragma omp single' sunishchit karta hai ki neeche ka block
        // team ka sirf koi bhi EK thread hi execute karega.
        // Baaki threads is block ko skip kar denge.
        #pragma omp single
        {
            printf("\nThread %d says: Hello World (from inside the single block)!\n\n", omp_get_thread_num());
        }

        // 'single' block ke aakhir mein ek implicit barrier hota hai,
        // isliye sabhi threads yahan ruk kar intezar karenge.
        printf("Thread %d says: I am after the single block.\n", omp_get_thread_num());
    }
    return 0;
}
```

**Expected Conclusion:**
Output mein "Hello World" sirf ek baar print hoga. `single` directive ka istemal tab kiya jaata hai jab parallel region ke andar koi aisa kaam ho (jaise file I/O ya shared variable ko initialize karna) jise sirf ek baar, ek hi thread dwara kiya jaana chahiye.


---
**19. Parallel Sum (C++ with threads): split array into n chunks, sum in threads, combine.**

**Pthreads Version**

```cpp
#include <iostream>
#include <vector>
#include <pthread.h>

#define NUM_THREADS 4
#define ARRAY_SIZE 1000000

// Har thread apna partial sum is array mein store karega.
long long partial_sums[NUM_THREADS];
std::vector<int> data(ARRAY_SIZE, 1); // 1 million elements, sabhi 1 hain.

void* sum_worker(void* arg) {
    long id = (long)arg;
    int chunk_size = ARRAY_SIZE / NUM_THREADS;
    int start = id * chunk_size;
    int end = start + chunk_size;

    // Har thread apne hisse (chunk) ka sum calculate karega.
    long long local_sum = 0;
    for (int i = start; i < end; i++) {
        local_sum += data[i];
    }
    
    // Local sum ko global partial_sums array mein store karna.
    partial_sums[id] = local_sum;
    
    return NULL;
}

int main() {
    pthread_t threads[NUM_THREADS];

    // Threads create karna.
    for (long i = 0; i < NUM_THREADS; i++) {
        pthread_create(&threads[i], NULL, sum_worker, (void*)i);
    }

    // Sabhi threads ke khatam hone ka intezar karna.
    for (int i = 0; i < NUM_THREADS; i++) {
        pthread_join(threads[i], NULL);
    }
    
    // Main thread sabhi partial sums ko jodkar final result nikalega.
    long long total_sum = 0;
    for (int i = 0; i < NUM_THREADS; i++) {
        total_sum += partial_sums[i];
    }

    std::cout << "Final Sum: " << total_sum << std::endl;
    return 0;
}
```

**OpenMP Version**

```cpp
#include <iostream>
#include <vector>
#include <omp.h>

#define ARRAY_SIZE 1000000

int main() {
    std::vector<int> data(ARRAY_SIZE, 1);
    long long total_sum = 0;

    // 'reduction(+:total_sum)' clause apne aap local sums banata hai
    // aur aakhir mein unhe jod deta hai. Yeh sabse aasan aur efficient tarika hai.
    #pragma omp parallel for reduction(+:total_sum)
    for (int i = 0; i < ARRAY_SIZE; i++) {
        total_sum += data[i];
    }

    std::cout << "Final Sum: " << total_sum << std::endl;
    return 0;
}
```

**Expected Conclusion:**
Parallel sum ek common problem hai. Pthreads mein, iske liye manual kaam (chunk banana, partial sums store karna, aur aakhir mein unhe combine karna) zaroori hai. OpenMP ka `reduction` clause is poore process ko automate kar deta hai, jisse code chhota, saaf, aur kam error-prone ho jaata hai.

-----

**20. Parallel Matrix Multiplication (Pthreads).**

```cpp
#include <iostream>
#include <vector>
#include <pthread.h>

#define SIZE 256 // Matrix ka dimension
#define NUM_THREADS 4

// Matrices ko represent karne ke liye 2D vectors
std::vector<std::vector<int>> A(SIZE, std::vector<int>(SIZE, 1));
std::vector<std::vector<int>> B(SIZE, std::vector<int>(SIZE, 2));
std::vector<std::vector<int>> C(SIZE, std::vector<int>(SIZE, 0));

void* multiply_worker(void* arg) {
    long id = (long)arg;
    int rows_per_thread = SIZE / NUM_THREADS;
    int start_row = id * rows_per_thread;
    int end_row = start_row + rows_per_thread;

    // Har thread C matrix ki kuch rows ko calculate karega.
    // Yeh "row-wise" partitioning hai.
    for (int i = start_row; i < end_row; i++) { // Rows par loop
        for (int j = 0; j < SIZE; j++) { // Columns par loop
            for (int k = 0; k < SIZE; k++) { // Dot product ke liye loop
                C[i][j] += A[i][k] * B[k][j];
            }
        }
    }
    return NULL;
}

int main() {
    pthread_t threads[NUM_THREADS];

    for (long i = 0; i < NUM_THREADS; i++) {
        pthread_create(&threads[i], NULL, multiply_worker, (void*)i);
    }
    for (int i = 0; i < NUM_THREADS; i++) {
        pthread_join(threads[i], NULL);
    }

    std::cout << "Matrix multiplication complete." << std::endl;
    // Yahan aap C matrix ke kuch elements print karke result verify kar sakte hain.
    // std::cout << "C[0][0] = " << C[0][0] << std::endl; // Expected: 512

    return 0;
}
```

**Expected Conclusion:**
Matrix multiplication ko parallel karne ka yeh ek aam tarika hai, jahan output matrix (C) ki rows ko threads ke beech baant diya jaata hai. Kyunki har element `C[i][j]` ki calculation doosre se independent hoti hai, isliye yeh problem parallelization ke liye bahut aacha hai. Yahan Pthreads ka istemal karke humne kaam ko manually chunks (rows ke group) mein toda hai.

-----

**21. Producer–Consumer with Condition Variables.**

**Pthreads Version**

```cpp
#include <iostream>
#include <queue>
#include <pthread.h>
#include <unistd.h>

#define BUFFER_SIZE 5

std::queue<int> buffer;
pthread_mutex_t mutex;
pthread_cond_t cond_not_full;  // Signal jab buffer full na ho
pthread_cond_t cond_not_empty; // Signal jab buffer khali na ho

void* producer(void* arg) {
    for (int i = 0; i < 20; ++i) {
        pthread_mutex_lock(&mutex);
        
        // Agar buffer full hai, toh producer intezar karega.
        while (buffer.size() >= BUFFER_SIZE) {
            std::cout << "Producer waiting, buffer full..." << std::endl;
            pthread_cond_wait(&cond_not_full, &mutex);
        }
        
        // Item produce karke buffer mein daalna.
        buffer.push(i);
        std::cout << "Produced: " << i << std::endl;
        
        // Consumer ko signal bhejna ki buffer ab khali nahi hai.
        pthread_cond_signal(&cond_not_empty);
        pthread_mutex_unlock(&mutex);
        sleep(0.1); // Thoda delay
    }
    return NULL;
}

void* consumer(void* arg) {
    for (int i = 0; i < 20; ++i) {
        pthread_mutex_lock(&mutex);
        
        // Agar buffer khali hai, toh consumer intezar karega.
        while (buffer.empty()) {
            std::cout << "Consumer waiting, buffer empty..." << std::endl;
            pthread_cond_wait(&cond_not_empty, &mutex);
        }
        
        // Buffer se item nikal kar consume karna.
        int item = buffer.front();
        buffer.pop();
        std::cout << "Consumed: " << item << std::endl;
        
        // Producer ko signal bhejna ki buffer ab full nahi hai.
        pthread_cond_signal(&cond_not_full);
        pthread_mutex_unlock(&mutex);
        sleep(0.2); // Thoda delay
    }
    return NULL;
}

// ... main function to init mutex/cond_vars and create/join threads ...
```

**OpenMP Version**

```cpp
#include <iostream>
#include <queue>
#include <omp.h>
#include <unistd.h>

#define BUFFER_SIZE 5

std::queue<int> buffer;
omp_lock_t buffer_lock; // OpenMP ka lock

int main() {
    omp_init_lock(&buffer_lock);

    // 'sections' ka istemal karke producer aur consumer ko parallel chalana.
    #pragma omp parallel sections
    {
        #pragma omp section // Producer Section
        {
            for (int i = 0; i < 20; ++i) {
                bool produced = false;
                while (!produced) {
                    omp_set_lock(&buffer_lock);
                    if (buffer.size() < BUFFER_SIZE) {
                        buffer.push(i);
                        std::cout << "Produced: " << i << std::endl;
                        produced = true;
                    }
                    omp_unset_lock(&buffer_lock);
                    if (!produced) usleep(1000); // Agar full hai, toh thoda wait karo.
                }
            }
        }

        #pragma omp section // Consumer Section
        {
            for (int i = 0; i < 20; ++i) {
                bool consumed = false;
                while (!consumed) {
                    omp_set_lock(&buffer_lock);
                    if (!buffer.empty()) {
                        int item = buffer.front();
                        buffer.pop();
                        std::cout << "Consumed: " << item << std::endl;
                        consumed = true;
                    }
                    omp_unset_lock(&buffer_lock);
                     if (!consumed) usleep(1000); // Agar khali hai, toh thoda wait karo.
                }
            }
        }
    }
    omp_destroy_lock(&buffer_lock);
    return 0;
}
```

**Expected Conclusion:**
Producer-Consumer problem synchronization ka ek classic example hai. Pthreads mein `condition variables` iske liye sabse aacha solution hain, kyunki woh threads ko "sone" (`wait`) aur "jagne" (`signal`) ki suvidha dete hain, jisse CPU cycles waste nahi hote (busy-waiting nahi hoti). OpenMP mein, ise `omp_lock_t` aur `critical` sections se implement kiya ja sakta hai, lekin yeh Pthreads ke condition variables jitna efficient nahi hota kyunki ismein polling (baar-baar check karna) shaamil ho sakti hai.

-----

**22. Parallel Prime Finder using T threads.**

**Pthreads Version (Dynamic Load Balancing)**

```cpp
#include <iostream>
#include <pthread.h>
#include <cmath>

#define NUM_THREADS 4
#define MAX_NUM 100000

int next_num_to_check = 2; // Global counter for next number
pthread_mutex_t num_lock; // Counter ko protect karne ke liye lock

bool is_prime(int n) {
    if (n <= 1) return false;
    for (int i = 2; i <= sqrt(n); i++) {
        if (n % i == 0) return false;
    }
    return true;
}

void* prime_worker(void* arg) {
    while (true) {
        int current_num;
        
        // Dynamically agla number check karne ke liye lena.
        pthread_mutex_lock(&num_lock);
        current_num = next_num_to_check;
        next_num_to_check++;
        pthread_mutex_unlock(&num_lock);

        if (current_num > MAX_NUM) {
            break; // Kaam khatam.
        }
        
        if (is_prime(current_num)) {
            // Printing ko bhi lock karna aacha hai, taaki output mix na ho.
            // (Yahan simplicity ke liye lock nahi kiya gaya hai).
            printf("%d ", current_num);
        }
    }
    return NULL;
}

// ... main function to init mutex and create/join threads ...
```

**OpenMP Version (Dynamic Scheduling)**

```cpp
#include <iostream>
#include <omp.h>
#include <cmath>

#define MAX_NUM 100000

bool is_prime(int n) { /* ... same as above ... */ }

int main() {
    // 'schedule(dynamic)' batata hai ki iterations ko threads mein dynamically baanta jaaye.
    // Jab ek thread free hota hai, use agla available number check karne ko mil jaata hai.
    // Yeh uneven workload (bade numbers ko check karne mein zyada time lagta hai)
    // ke liye sabse aacha hai.
    #pragma omp parallel for schedule(dynamic)
    for (int i = 2; i <= MAX_NUM; i++) {
        if (is_prime(i)) {
            // Printing ko critical section mein daalna aacha practice hai.
            #pragma omp critical
            {
                printf("%d ", i);
            }
        }
    }
    printf("\n");
    return 0;
}
```

**Expected Conclusion:**
Prime numbers dhundne mein load balancing ek badi chunauti hai kyunki bade numbers ko check karne mein chote numbers se kahin zyada time lagta hai. Pthreads mein, iske liye ek shared work queue (yahan ek simple counter) ka istemal karke dynamic load balancing implement ki ja sakti hai. OpenMP is kaam ko `schedule(dynamic)` clause se bahut aasan bana deta hai, jo uneven workloads ko handle karne ke liye hi design kiya gaya hai.

---
