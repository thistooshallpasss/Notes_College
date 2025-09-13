Bilkul\! Prayagraj ki is Saturday night mein, jab माहौल coding ke liye ekdam aacha hai, chaliye Node.js ke fundamentals ko bilkul interview-ready format mein samajhte hain. Hum har topic ko gehraai se, analogy, code examples, aur zaroori savdhaniyon ke saath cover karenge.

-----

## **Node.js Fundamentals**

### 1\. What is Node.js? (Runtime, V8 engine, Non-blocking I/O)

Yeh sabse common sawaal hai. Iska jawab aese de sakte hain:

"Node.js koi programming language ya framework nahi hai. **Node.js ek JavaScript Runtime Environment hai.**"

Is line ko todkar samjhate hain:

  * **JavaScript Runtime Environment:** Iska matlab hai ek aisa mahaul ya platform jo JavaScript code ko browser ke **bahar** (jaise ki aapke computer ke server par) chalaane ki taakat deta hai.

**Analogy (Sabse Aasan Tarika):**
Sochiye JavaScript ek "Recipe" (khaana banane ki vidhi) hai.

  * **Browser (like Chrome):** Ek special "Italian Kitchen" hai. Yeh kitchen sirf ek khaas tarah ki recipe (jo web pages se judi ho) hi bana sakta hai.
  * **Node.js:** Ek "Master Kitchen" hai. Is kitchen mein aap koi bhi recipe (JavaScript code) chala sakte hain—chahe woh server banana ho, files read/write karni ho, ya database se baat karni ho.

**Iske mukhya ansh (Key Components):**

1.  **V8 Engine:**

      * **Yeh Kya Hai?** Yeh Google ka banaya hua ek super-fast JavaScript engine hai, jo Chrome browser mein bhi istemal hota hai.
      * **Andar ka Mechanism:** Node.js V8 engine ko C++ mein likha gaya hai aur iska kaam aapke JavaScript code ko lena aur use blazingly fast Machine Code (jo computer seedha samajh sake) mein badalna hai. Isliye Node.js itna performant hai.

2.  **Non-blocking I/O (Input/Output):**

      * **Yeh Kya Hai?** Yeh Node.js ka "superpower" hai. I/O operations woh kaam hote hain jinmein time lagta hai, jaise file padhna, network request karna, ya database se query karna. Non-blocking ka matlab hai ki Node.js in kaamon ke poora hone ka **intezaar nahi karta**.
      * **Analogy (Restaurant Waiter):**
          * **Blocking (Doosri Technologies):** Ek waiter table 1 se order leta hai, kitchen mein jaata hai, aur **wahin khada rehta hai jab tak khaana ban na jaaye**. Jab khaana ban jaata hai, tab woh use serve karke table 2 ke paas jaata hai. Yeh bahut inefficient hai.
          * **Non-blocking (Node.js):** Waiter table 1 se order leta hai, kitchen ko order dekar **turant table 2 ka order lene chala jaata hai**. Jab table 1 ka khaana taiyaar hota hai, to kitchen se ek bell bajti hai (yeh **callback** hai), aur waiter aakar khaana serve kar deta hai. Is tarah woh ek hi samay mein kai tables ko handle kar paata hai.
      * **Kaise Kaam Hota Hai:** Jab Node.js ko ek I/O operation milta hai (e.g., file padhna), woh us kaam ko system ke kernel ko de deta hai aur kehta hai, "Jab yeh kaam ho jaaye, to mujhe bata dena." Aur fir woh agle kaam par chala jaata hai. Isse ek single thread par bhi hazaron connections handle ho jaate hain.

**Mukhya Baatein:**

  * Node.js JavaScript ko backend (server-side) programming ke liye istemal karta hai.
  * Yeh event-driven aur non-blocking model par kaam karta hai, jo isey I/O-heavy applications ke liye perfect banata hai.

**Kab Use Kare:** Real-time applications jaise Chat Apps, Streaming Apps, REST APIs, Microservices. Jahan bahut saare concurrent connections aur I/O operations hon.

**Kya Savdhani Rakhe:** Node.js CPU-intensive kaamon (jaise video encoding, complex calculations) ke liye aacha nahi hai. Kyunki iska ek hi main thread hota hai, agar ek heavy calculation us thread ko block kar degi, to poori application "freeze" ho jaayegi.

-----

### 2\. Node.js Architecture (Single-threaded event loop, libuv)

"Node.js ek **single-threaded, event-driven architecture** par kaam karta hai, jo **libuv** library ki madad se asynchronous operations ko handle karta hai."

Let's break it down:

  * **Single-threaded:** Node.js aapke code ko ek hi main thread mein chalaata hai. Iska matlab hai ki ek samay par woh ek hi kaam karta hai. (Yeh sunne mein kharab lagta hai, lekin aesa hai nahi).
  * **Event Loop:** Yeh Node.js ka dil hai. Yeh ek loop hai jo lagatar chalta rehta hai aur check karta hai ki "kya koi kaam poora hua?" ya "kya koi naya kaam aaya hai?".

**Andar Ka Mechanism (Yeh Diagram Interviewer ko zaroor batayein):**

1.  **Call Stack:** Jab aap koi function call karte hain, woh yahan aata hai.
2.  **Node API:** Jab aap `fs.readFile()` jaisa asynchronous function call karte hain, to Node.js us kaam ko **libuv** ko de deta hai.
3.  **libuv:** Yeh C++ mein likhi ek library hai jo Node.js ko asynchronous I/O ki shakti deti hai. Iske paas ek chota sa **thread pool** (default size 4) hota hai. Yeh file system, networking jaise kaamon ko is thread pool mein handle karta hai. Isliye, bhale hi Node.js single-threaded hai, parde ke peeche heavy I/O ka kaam multiple threads mein hota hai.
4.  **Callback Queue (or Event Queue):** Jab libuv mein kaam poora ho jaata hai, to usse juda function (callback) is queue mein aa jaata hai.
5.  **Event Loop:** Event Loop ka bas ek hi kaam hai: "Agar Call Stack khaali hai, to Callback Queue se pehle item ko uthao aur Call Stack mein daal do taaki woh run ho sake."

**Analogy (Busy CEO):**

  * **CEO (Node.js ka Main Thread):** Ek CEO hai jo bahut fast hai, lekin ek baar mein ek hi cheez par focus kar sakta hai.
  * **Assistants (libuv ka Thread Pool):** CEO ke paas 4 assistants hain.
  * **Kaam ka Flow:** Jab CEO ke paas ek time-consuming kaam aata hai (e.g., 500 page ki report padhna), to woh yeh kaam ek assistant ko de deta hai. Fir woh apne agle kaam par lag jaata hai. Jab assistant report padh leta hai, to woh CEO ke "in-tray" (Callback Queue) mein ek note rakh deta hai. Jab CEO free hota hai (Call Stack khaali hota hai), woh in-tray se note uthakar us par action leta hai.

-----

### 3\. Global Objects (`process`, `__dirname`, `__filename`)

"Node.js mein Global Objects woh objects hote hain jo har module mein bina `require()` kiye uplabdh hote hain."

  * **`process`**

      * **Yeh Kya Hai?** Yeh ek global object hai jo current Node.js process ke baare mein jaankari deta hai aur use control karne mein madad karta hai.
      * **Kab Use Kare:** Command-line arguments lene ke liye, environment variables access karne ke liye, ya process ko band karne ke liye.
      * **Code Example:**
        ```javascript
        // app.js
        console.log('Command-line arguments:', process.argv);
        // Run: node app.js user=prayagraj role=admin
        // Output: [ 'C:\\...\\node.exe', 'C:\\...\\app.js', 'user=prayagraj', 'role=admin' ]

        console.log('Current Path Env Variable:', process.env.PATH);

        // Process ko 1 second baad band kar do
        setTimeout(() => {
          process.exit(0); // 0 means success
        }, 1000);
        ```

  * **`__dirname` aur `__filename`**

      * **Yeh Kya Hai?** Yeh variables hain, objects nahi.
          * `__filename`: Current module (file) ka absolute path batata hai.
          * `__dirname`: Current module ki directory (folder) ka absolute path batata hai.
      * **Kab Use Kare:** File system ke saath kaam karte waqt reliable paths banane ke liye. Yeh best practice hai.
      * **Code Example:**
        Maan lijiye aapki file `D:\Projects\my-app\server.js` mein hai.
        ```javascript
        // D:\Projects\my-app\server.js
        const path = require('path');

        console.log('Filename:', __filename);
        // Output: D:\Projects\my-app\server.js

        console.log('Directory Name:', __dirname);
        // Output: D:\Projects\my-app

        // Ek file ka path banane ka sahi tarika
        const staticFilePath = path.join(__dirname, 'public', 'index.html');
        console.log('Reliable Path:', staticFilePath);
        // Output: D:\Projects\my-app\public\index.html
        ```
      * **Kya Savdhani Rakhe:** `__dirname` aur `.` (current working directory) mein fark hota hai. `__dirname` hamesha file ki location batata hai, jabki `.` wahan point karta hai jahan se aapne script run ki hai. Hamesha `__dirname` istemal karein.

-----

### 4\. REPL (Read Eval Print Loop)

  * **Yeh Kya Hai?** REPL Node.js ke saath aane wala ek simple, interactive command-line tool hai. Yeh aapko JavaScript code ke chhote tukde test karne ki suvidha deta hai.
  * **Kaise Kaam Hota Hai:** Iske naam mein hi iska kaam chhupa hai.
    1.  **Read:** Yeh aapke input (code) ko read karta hai.
    2.  **Eval:** Yeh us code ko evaluate (run) karta hai.
    3.  **Print:** Yeh result ko screen par print karta hai.
    4.  **Loop:** Yeh wapas step 1 par chala jaata hai aur aapke agle input ka intezaar karta hai.
  * **Kaise Use Kare:** Apne terminal ya command prompt mein bas `node` likhkar Enter dabayein.
  * **Input/Output:**
      * **Input:** Aap jo bhi valid JavaScript code type karte hain.
      * **Output:** Us code ka execution result.
  * **Code Example:**
    ```bash
    $ node
    Welcome to Node.js v18.17.1.
    Type ".help" for more information.
    > 10 + 20
    30
    > const city = "Prayagraj"
    undefined
    > city
    'Prayagraj'
    > city.toUpperCase()
    'PRAYAGRAJ'
    > .exit
    $
    ```
  * **Kab Use Kare:** Chhote JavaScript snippets ko test karne, library ke functions ko check karne, ya naye syntax ko explore karne ke liye. Yeh full-fledged development ke liye nahi hai.

---

Core Modules woh "in-built libraries" hain jo Node.js ke saath aati hain. Aapko inke liye `npm install` karne ki zaroorat nahi, bas apne code mein `require()` karna hota hai. Yeh Node.js ka "built-in toolbox" hai.

----

### **Core Modules**

#### 1\. `fs` (File System)

  * **Topic:** `fs` Module

  * **Yeh Kya Hai?:** Yeh module aapke program ko computer ke file system ke saath interact karne (baat-cheet karne) ki shakti deta hai. Aap files padh sakte hain, nayi files bana sakte hain, unmein data likh sakte hain, delete kar sakte hain, aur folders ke saath bhi yahi sab kar sakte hain.

  * **Analogy:** Yeh aapke program ka **"Librarian"** hai. Aap is librarian ko bol sakte hain ki "mujhe 'my\_notes.txt' file laakar do" (read), "is nayi 'story.txt' ko shelf mein rakh do" (write), ya "purani 'draft.txt' file ko hata do" (delete).

  * **Mukhya Methods (Code Example):**
    `fs` module ke zyadatar methods do flavors mein aate hain:

    1.  **Asynchronous (Non-blocking):** Yeh ek callback function lete hain aur event loop ko block nahi karte. **Hamesha ise use karna chahiye.**
    2.  **Synchronous (...Sync):** Yeh kaam poora hone tak event loop ko block kar dete hain. Inka istemal server-side par bilkul nahi karna chahiye.

    <!-- end list -->

    ```javascript
    const fs = require('fs');
    const path = require('path');

    // ASYNCHRONOUS (Sahi Tarika) - Non-blocking
    const filePath = path.join(__dirname, 'notes.txt');

    fs.readFile(filePath, 'utf8', (err, data) => {
      // Yeh callback function tabhi chalega jab file padhne ka kaam poora ho jaayega
      if (err) {
        console.error("Error! File nahi padh paaye:", err);
        return;
      }
      console.log("File ka content (Async):", data);
    });

    console.log("Yeh message file padhne se pehle print hoga!");

    // SYNCHRONOUS (Galat Tarika - Blocking)
    try {
      const data = fs.readFileSync(filePath, 'utf8');
      console.log("File ka content (Sync):", data);
    } catch (err) {
      console.error("Error! File nahi padh paaye:", err);
    }
    ```

  * **Kab Use Kare:** Jab bhi aapko server par files ya directories ke saath koi bhi kaam karna ho. Jaise user-uploaded files ko save karna, log files likhna, ya configuration files padhna.

  * **Kya Savdhani Rakhe:** **Hamesha, hamesha, hamesha asynchronous methods (`readFile`, `writeFile`, etc.) ka istemal karein.** Synchronous methods (`readFileSync`) aapke server ko "freeze" kar denge jab tak file operation poora nahi ho jaata. Is dauran aapka server koi aur request handle nahi kar paayega.

-----

#### 2\. `path`

  * **Topic:** `path` Module
  * **Yeh Kya Hai?:** Yeh module file paths ke saath kaam karne ke liye utility functions deta hai. Yeh file system ko access nahi karta, sirf path strings ko manipulate (jod-tod) karta hai.
  * **Analogy:** Yeh aapke program ka **"Google Maps for File Paths"** hai. Yeh aapko batata hai ki ek jagah se doosri jagah jaane ka sahi "raasta" (path) kaise banayein, chahe aap kisi bhi sheher (Operating System - Windows/Linux) mein hon.
  * **Mukhya Methods (Code Example):**
    ```javascript
    const path = require('path');

    const myPath = 'D:\\Projects\\my-app\\public\\index.html';

    // 1. path.join() - Paths ko jodne ka sabse sahi tarika
    const reliablePath = path.join(__dirname, 'views', 'about.html');
    console.log('Joined Path:', reliablePath); // Output OS ke hisab se hoga

    // 2. path.basename() - Path se file ka naam nikalna
    console.log('Basename:', path.basename(myPath)); // Output: index.html

    // 3. path.extname() - File ka extension nikalna
    console.log('Extension:', path.extname(myPath)); // Output: .html
    ```
  * **Kab Use Kare:** Jab bhi aapko code mein file ya directory ka path banana ho.
  * **Kya Savdhani Rakhe:** File paths ko kabhi bhi string concatenation (`+`) se na jodein (e.g., `__dirname + '/views/about.html'`). Yeh Windows mein fail ho sakta hai jahan separator `\` hota hai. **Hamesha `path.join()` ka istemal karein.**

-----

#### 3\. `os`

  * **Topic:** `os` Module
  * **Yeh Kya Hai?:** Yeh module aapke program ko us Operating System ke baare mein jaankari deta hai jis par woh chal raha hai.
  * **Analogy:** Yeh aapke program ka **"Doctor"** hai jo computer ki health report ya "kundli" (OS details) de sakta hai.
  * **Mukhya Methods (Code Example):**
    ```javascript
    const os = require('os');

    console.log('Platform (OS):', os.platform()); // Output: win32, linux, darwin (for macOS)
    console.log('CPU Architecture:', os.arch()); // Output: x64
    console.log('CPU Cores:', os.cpus().length); // Kitne cores hain
    console.log('Free Memory (bytes):', os.freemem());
    console.log('Home Directory:', os.homedir());
    ```
  * **Kab Use Kare:** Jab aapko system ki information log karni ho, ya system resources (like CPU cores) ke aadhar par kuch decision lena ho (jaise Node.js cluster banana).

-----

#### 4\. `http`

  * **Topic:** `http` Module
  * **Yeh Kya Hai?:** Yeh Node.js ka core module hai jo aapko ek web server banane ki shakti deta hai. Yeh HTTP protocol ke upar kaam karta hai.
  * **Analogy:** Yeh ek **"Digital Post Office"** hai. `http.createServer()` se aap post office kholte hain. Jab koi request (chitthi) aati hai, to aap use `request` object se padhte hain aur `response` object ka istemal karke jawab (response) bhejte hain.
  * **Code Example (Bina Express ke Server banana):**
    ```javascript
    const http = require('http');

    const PORT = 3000;

    // Ek server create karein. Har request ke liye yeh function chalega.
    const server = http.createServer((req, res) => {
      // req (request) object mein client ki bheji hui jaankari hoti hai
      // res (response) object se hum client ko jawab bhejte hain

      if (req.url === '/') {
        res.writeHead(200, { 'Content-Type': 'text/html' });
        res.end('<h1>Welcome to the Home Page!</h1>');
      } else if (req.url === '/about') {
        res.writeHead(200, { 'Content-Type': 'text/plain' });
        res.end('This is the About Page from Prayagraj.');
      } else {
        res.writeHead(404, { 'Content-Type': 'text/html' });
        res.end('<h2>404 - Page Not Found</h2>');
      }
    });

    // Server ko port 3000 par start karein
    server.listen(PORT, () => {
      console.log(`Server Prayagraj mein port ${PORT} par chal raha hai...`);
    });
    ```
  * **Kab Use Kare:** Web server banane ke liye. Lekin, **real-world applications mein log iske upar bane frameworks (jaise Express.js, Fastify) ka istemal karte hain**, kyunki woh routing, middleware, etc. ko bahut aasan bana dete hain. `http` module ko samajhna zaroori hai, par istemal zyadatar Express ke zariye hi hota hai.

-----

#### 5\. `events`

  * **Topic:** `events` Module (EventEmitter)
  * **Yeh Kya Hai?:** Yeh Node.js ke event-driven nature ki neenv hai. Yeh aapko custom events banane, unhe fire (emit) karne, aur unhe sunne (listen) ki anumati deta hai. Yeh Observer design pattern par आधारित hai.
  * **Analogy:** Yeh ek **"Radio Station" (EventEmitter)** hai. Aap `emit()` ka istemal karke ek gaana (event) broadcast karte hain. Jo log bhi us frequency (`on()`) par tuned hain, woh us gaane ko sun sakte hain.
  * **Mukhya Methods (Code Example):**
    ```javascript
    const EventEmitter = require('events');

    // Ek custom class banayein jo EventEmitter ko extend kare
    class MyLogger extends EventEmitter {}

    const logger = new MyLogger();

    // Event ke liye ek listener set karein
    logger.on('userLoggedIn', (user) => {
      console.log(`EVENT RECEIVED: User '${user.name}' from '${user.city}' has logged in at ${new Date().toLocaleTimeString()}`);
    });

    // Kuch samay baad event ko fire (emit) karein
    setTimeout(() => {
      console.log("Ek user ne login kiya...");
      logger.emit('userLoggedIn', { name: 'Ankit', city: 'Prayagraj' });
    }, 2000);
    ```
  * **Kab Use Kare:** Jab aap apne application ke alag-alag hisson ko decouple (ek doosre se aazad) karna chahte hain. Ek hissa sirf event `emit` karta hai, aur doosre hisse us event ko sunkar apna-apna kaam karte hain (e.g., email bhejna, database update karna). Isse code saaf aur maintainable rehta hai.

-----

#### 6\. `util`

  * **Topic:** `util` Module

  * **Yeh Kya Hai?:** Yeh module alag-alag utility functions ka ek collection hai jo developers ke kaam aate hain.

  * **Analogy:** Yeh aapke program ka **"Swiss Army Knife"** ya **"Toolkit"** hai jismein kai chhote-chhote, upyogi auzaar (tools) hain.

  * **Mukhya Methods (Code Example):**

      * **`util.promisify`:** Yeh iska sabse zaroori function hai. Yeh ek purane callback-style function ko ek naye Promise-based function mein badal deta hai.

    <!-- end list -->

    ```javascript
    const fs = require('fs');
    const util = require('util');

    // fs.readFile ek callback-style function hai
    // Hum use promisify karke ek naya function banayenge
    const readFilePromise = util.promisify(fs.readFile);

    // Ab hum async/await ka istemal kar sakte hain!
    async function readMyFile() {
      try {
        const data = await readFilePromise('notes.txt', 'utf8');
        console.log("Promisify se padha gaya data:", data);
      } catch (err) {
        console.error("Error:", err);
      }
    }

    readMyFile();
    ```

  * **Kab Use Kare:** `util.promisify` ka istemal tab karein jab aapko kisi aisi library ke saath kaam karna pade jo sirf callbacks support karti ho, aur aap apne code mein modern `async/await` syntax istemal karna chahte hon.
---



### **Asynchronous Programming in Node.js**

Node.js ki poori duniya Asynchronous Programming par tiki hai. Iska matlab hai, "tum apna kaam shuru karo, jab ho jaaye to bata dena, main tab tak doosra kaam kar raha hoon."

#### 1\. Event Loop & Phases (Gehraai Mein)

  * **Topic:** Event Loop & Phases
  * **Yeh Kya Hai?:** Humne pehle baat ki thi ki Event Loop ek manager jaisa hai. Lekin asal mein, yeh ek "Assembly Line" jaisa hai jiske kai alag-alag stations (phases) hain. Har ek "tick" (cycle) mein, Event Loop in phases se ek specific order mein guzarta hai.
  * **Andar Ka Mechanism (The Phases):** Har phase ki apni ek FIFO (First-In-First-Out) queue hoti hai jismein callbacks hote hain. Mukhya phases yeh hain:
    1.  **Timers Phase:** Is phase mein `setTimeout()` aur `setInterval()` ke callbacks execute hote hain jinka time poora ho chuka hai.
    2.  **Pending Callbacks (I/O) Phase:** Yahan zyadatar I/O operations (jaise file read complete, network response received) ke callbacks execute hote hain.
    3.  **Poll Phase (Sabse Zaroori):** Is phase mein do kaam hote hain:
          * Yeh dekhta hai ki I/O queue mein naye events hain ya nahi. Agar hain, to unhe turant execute karta hai.
          * Agar queue khaali hai, to yeh yahan **intezaar** karta hai. Agar is dauran `setImmediate()` ke liye koi callback schedule hua hai, to yeh agle phase mein jaata hai. Agar `setTimeout` ka time poora ho gaya hai, to yeh Timers phase mein jaata hai.
    4.  **Check Phase:** `setImmediate()` ke callbacks yahan execute hote hain. Yeh Poll phase ke theek baad chalta hai.
    5.  **Close Callbacks Phase:** `socket.on('close', ...)` jaise cleanup callbacks yahan execute hote hain.
  * **Analogy:** Ek **"Factory ka Assembly Line"**. Har product (program ka tick) in stations (phases) se guzarta hai. Pehle 'Painting' (Timers), fir 'Assembling' (I/O), fir 'Waiting for parts' (Poll), fir 'Final Check' (Check), aur aakhir mein 'Packaging' (Close).
  * **Mukhya Baatein (Interview Gem):** `setTimeout(fn, 0)` aur `setImmediate(fn)` ke beech kya fark hai?
      * `setTimeout(fn, 0)` Timers phase mein chalne ke liye schedule hota hai.
      * `setImmediate(fn)` Check phase mein chalne ke liye schedule hota hai.
      * Unka order **guaranteed nahi hota\!** Yeh is baat par depend karta hai ki Event Loop jab unhe dekhta hai, tab woh kis phase mein hai. Aam taur par I/O operations ke andar, `setImmediate` hamesha pehle chalta hai.
  * **Code Example:**
    ```javascript
    const fs = require('fs');

    fs.readFile(__filename, () => {
      console.log('I/O Callback');
      setTimeout(() => console.log('Timeout inside I/O'), 0);
      setImmediate(() => console.log('Immediate inside I/O'));
    });

    console.log('Top Level Code');
    // Output:
    // Top Level Code
    // I/O Callback
    // Immediate inside I/O  <-- Yeh hamesha pehle aayega
    // Timeout inside I/O
    ```

-----

#### 2\. Callback Patterns

  * **Topic:** Callback Patterns
  * **Yeh Kya Hai?:** Callback ek function hai jise hum doosre function ko as an argument dete hain. Yeh "asynchronous" kaam poora hone par "call back" (wapas bulaya) jaata hai. Yeh Node.js mein async kaam karne ka sabse purana aur fundamental tarika hai.
  * **"Callback Hell" (Pyramid of Doom):**
      * Jab hum kai async operations ek ke baad ek karte hain, to hum callbacks ke andar callbacks nest karte jaate hain. Isse code ek right-side-tilted pyramid jaisa dikhta hai.
      * **Code Example (Callback Hell):**
        ```javascript
        const fs = require('fs');

        fs.readFile('file1.txt', 'utf8', (err1, data1) => {
          if (err1) throw err1;
          console.log(data1);
          fs.readFile('file2.txt', 'utf8', (err2, data2) => {
            if (err2) throw err2;
            console.log(data2);
            fs.writeFile('newFile.txt', data1 + data2, (err3) => {
              if (err3) throw err3;
              console.log('File saved!');
            });
          });
        });
        ```
      * **Ise Kyun Bura Maana Jaata Hai:** Is code ko padhna, debug karna, aur error handle karna bahut mushkil hai.
  * **Error-First Callback Pattern:**
      * **Yeh Kya Hai?:** Yeh Node.js mein ek convention (niyam) hai. Kisi bhi callback function mein, **pehla argument hamesha error object (`err`) ke liye hota hai**. Agar koi error nahi hai, to yeh `null` hota hai. Asli data doosre argument se shuru hota hai.
      * **Example:** `(err, data) => { ... }`.
      * **Kyun Zaroori Hai:** Yeh poore Node.js ecosystem mein error handling ka ek standard tarika banata hai.

-----

#### 3\. Promises & async/await

  * **Topic:** Promises & async/await
  * **Yeh Kya Hai? (Promises):** Promise ek special object hai jo ek asynchronous operation ke "future result" ko represent karta hai. Yeh ek "vaada" hai ki ya to aapko data milega (fulfilled) ya ek error (rejected). Callback Hell ka solution Promises hain.
  * **Analogy (Promise):** Ek **"Domino's Pizza Tracker"**. Jab aap order karte hain, to aapko pizza nahi milta, ek tracker milta hai (yeh Promise hai). Iske 3 states hote hain:
    1.  **Pending:** Order place ho gaya hai, pizza ban raha hai.
    2.  **Fulfilled/Resolved:** Pizza deliver ho gaya\! (Success)
    3.  **Rejected:** Order cancel ho gaya. (Failure)
  * **Yeh Kya Hai? (async/await):** Yeh Promises ke upar bana ek "syntactic sugar" hai. Yeh aapko async code ko is tarah se likhne deta hai jaise ki woh synchronous (line-by-line) ho, jisse code bahut saaf-suthra ho jaata hai.
      * `async` function hamesha ek Promise return karta hai.
      * `await` ek Promise ke settle (resolve ya reject) hone ka intezaar karta hai. Yeh sirf `async` function ke andar hi istemal ho sakta hai.
  * **Code Example (Callback Hell se Mukti):**
    ```javascript
    const fs = require('fs').promises; // Node.js v10+ mein built-in promise version

    async function combineFiles() {
      try {
        console.log("File 1 padh rahe hain...");
        const data1 = await fs.readFile('file1.txt', 'utf8');
        
        console.log("File 2 padh rahe hain...");
        const data2 = await fs.readFile('file2.txt', 'utf8');
        
        console.log("Nayi file likh rahe hain...");
        await fs.writeFile('newFile.txt', data1 + data2);
        
        console.log('File saved successfully!');
      } catch (err) {
        console.error("Oops! Kuch gadbad ho gayi:", err);
      }
    }

    combineFiles();
    ```
    Dekhiye yeh code kitna saaf aur seedha hai\!
  * **Kab Use Kare:** **Hamesha.** Modern Node.js development mein async operations ke liye `async/await` ka hi istemal karna chahiye.
  * **Kya Savdhani Rakhe:** `await` calls ko hamesha `try...catch` block mein rakhein taaki aap rejected promises (errors) ko pakad sakein.

-----

#### 4\. Streams & Buffers

  * **Topic:** Streams & Buffers
  * **Yeh Kya Hai? (Buffer):** Buffer raw binary data (bytes) ko store karne ke liye Node.js ki ek memory location hai. JavaScript strings ke saath achha kaam karta hai, lekin binary data (jaise images, videos) ke saath nahi. Buffer is kami ko poora karta hai.
  * **Yeh Kya Hai? (Streams):** Streams data ko **chunks (chhote tukdon)** mein process karne ka ek tarika hai, bajaye poore data ko ek saath memory mein load karne ke.
  * **Analogy (Stream):** **"Netflix ya YouTube Dekhna."** Aap 2 ghante ki movie dekhne se pehle use poora download nahi karte. Movie aapke paas chhote-chhote chunks mein "stream" hoti hai. Isse aap turant dekhna shuru kar sakte hain aur aapke device ki memory bhi nahi bharti.
  * **Mechanism:** Streams `EventEmitter` par bane hote hain. Yeh `data`, `end`, aur `error` jaise events emit karte hain.
  * **Kab Use Kare:** Jab aapko **badi files** ya **bade data** ke saath kaam karna ho.
      * Badi file ko read/write karna.
      * Ek server se doosre server par data transfer karna.
      * User se file upload lena.
  * **Code Example (Ek Badi File ko Copy Karna):**
    ```javascript
    const fs = require('fs');

    // GALAT TARIKA (1 GB ki file par crash ho jaayega)
    // fs.readFile('large-video.mp4', (err, data) => {
    //   fs.writeFile('copy-of-large-video.mp4', data, ...);
    // });

    // SAHI TARIKA (Streams ke saath) - Bahut kam memory use karta hai
    const readStream = fs.createReadStream('large-video.mp4');
    const writeStream = fs.createWriteStream('copy-of-large-video.mp4');

    // .pipe() jaadu ki tarah kaam karta hai.
    // Yeh read stream se data ke chunks ko leta hai aur jaise hi woh aate hain,
    // unhe write stream mein bhejta jaata hai, bina poori file ko memory mein laaye.
    readStream.pipe(writeStream);

    readStream.on('end', () => {
      console.log('File copying finished!');
    });

    readStream.on('error', (err) => {
      console.error('Error copying file:', err);
    });
    ```
  * **Mukhya Baatein:** Streams Node.js ke sabse powerful concepts mein se ek hain. Yeh aapki application ko memory efficient aur performant banate hain. `.pipe()` method data flow aur backpressure (jab write stream read stream se dheemi ho) ko automatically handle karta hai.

---


### **Package Management**

#### 1\. `npm` & `yarn`

  * **Topic:** `npm` & `yarn`
  * **Yeh Kya Hai?:** Yeh dono **Package Managers** hain. Inka kaam aapke project ke liye zaroori third-party code (jise **package** ya **dependency** kehte hain) ko internet (NPM Registry se) download karna, install karna, update karna, aur manage karna hai.
  * **Analogy:** Yeh aapke project ke **"Librarian"** ya **"App Store"** hain. Aap librarian ko batate hain ki aapko "Express.js" naam ki kitaab chahiye. Librarian (`npm` ya `yarn`) us kitaab ko dhoondhta hai, use aapke project ke `node_modules` folder (library) mein laakar rakhta hai, aur `package.json` (register) mein iska hisaab likh leta hai.
  * **Mukhya Farak (Key Differences):**
      * **`npm` (Node Package Manager):** Yeh default package manager hai jo Node.js ke saath hi install hokar aata hai. Yeh original hai.
      * **`yarn`:** Ise Facebook ne banaya tha. Shuru mein yeh `npm` se kaafi tez aur reliable tha kyunki yeh packages ko parallel download karta tha aur iske paas ek behtar lock file system (`yarn.lock`) tha.
  * **Aaj ki Stithi (Current Scenario):**
      * **Speed:** `npm` ne (version 5 ke baad se) bahut sudhaar kiya hai aur ab speed mein `yarn` ke barabar ya usse bhi tez ho sakta hai.
      * **Lock File:** Dono ab reliable lock files (`package-lock.json` for npm, `yarn.lock` for yarn) ka istemal karte hain.
      * **Commands:** Commands thode alag hain:
        | Task | npm | yarn |
        | :--- | :--- | :--- |
        | Install all dependencies | `npm install` | `yarn install` or `yarn` |
        | Add a new package | `npm install express` | `yarn add express` |
        | Add a dev dependency | `npm install --save-dev nodemon` | `yarn add --dev nodemon` |
        | Remove a package | `npm uninstall express` | `yarn remove express` |
        | Run a script | `npm run dev` | `yarn dev` |
  * **Kab Kise Use Kare?:** Aaj ke samay mein yeh zyadatar personal ya team ki pasand par nirbhar karta hai. Sabse zaroori niyam hai **consistency**.
      * Agar aap ek project join karte hain jismein `package-lock.json` file hai, to aapko `npm` use karna chahiye.
      * Agar project mein `yarn.lock` file hai, to `yarn` use karein.
      * Naye project ke liye, aap dono mein se koi bhi chun sakte hain. `npm` ab kaafi behtar ho chuka hai.
  * **Mukhya Baatein:** `npm` ke saath `npx` naam ka ek tool aata hai, jo kisi package ko bina install kiye uski command-line utility run karne deta hai (e.g., `npx create-react-app my-app`). Yeh bahut upyogi hai.

-----

#### 2\. `package.json` & `package-lock.json`

  * **Topic:** `package.json` & `package-lock.json`
  * **`package.json`**
      * **Yeh Kya Hai?:** Yeh har Node.js project ka "Manifesto" ya "**Kundli**" hai. Yeh ek JSON file hai jo project ke baare mein saari metadata (jaankari) rakhti hai.
      * **Analogy:** Yeh ek recipe ki **"Ingredients List"** hai. Yeh batati hai ki is project ko banane ke liye kaun-kaun se packages (`dependencies`) chahiye.
      * **Mukhya Hisse (Key Parts):**
          * `name`, `version`, `description`: Project ki basic jaankari.
          * `main`: Aapki application ka entry point (e.g., `index.js`).
          * `scripts`: Command-line shortcuts define karne ke liye (e.g., `npm start`, `npm test`).
          * `dependencies`: Woh packages jo production mein zaroori hain (e.g., `express`, `mongoose`).
          * `devDependencies`: Woh packages jo sirf development ke time zaroori hain (e.g., `nodemon`, `jest`).
      * **Code Example:**
        ```json
        {
          "name": "my-prayagraj-app",
          "version": "1.0.0",
          "description": "A simple web server.",
          "main": "server.js",
          "scripts": {
            "start": "node server.js",
            "dev": "nodemon server.js"
          },
          "dependencies": {
            "express": "^4.17.1"
          },
          "devDependencies": {
            "nodemon": "^2.0.7"
          }
        }
        ```
  * **`package-lock.json`**
      * **Yeh Kya Hai?:** Yeh aapke `node_modules` folder ka **"Blueprint"** ya **"Fingerprint"** hai. Yeh file automatically generate hoti hai aur har ek package (aur uske sub-packages) ka **exact version** record karti hai jo install hua hai.
      * **Analogy:** Agar `package.json` "Ingredients List" hai, to `package-lock.json` **"Exact Shopping Bill"** hai. Yeh batata hai ki aapne Aashirvaad Atta ka 5kg wala pack, batch number \#XYZ wala kharida hai. Isse yeh sunishchit hota hai ki har cook (developer) jo is recipe ko banaye, woh **bilkul wahi ingredients** istemal kare, jisse result (application) hamesha same bane.
      * **Kaise Kaam Hota Hai?:** Jab aap `npm install` chalaate hain, `npm` is file ko dekhta hai. Agar yeh file hai, to woh `package.json` ko ignore karke is file mein likhe exact versions ko hi install karta hai. Isse "mere machine par to chalta hai" waali problem khatm ho jaati hai.
      * **Kya Savdhani Rakhe:** **Hamesha `package-lock.json` ko Git (version control) mein commit karein.** Ise kabhi bhi `.gitignore` mein na daalein. Ise kabhi bhi manually edit na karein.

-----

#### 3\. Semantic Versioning (SemVer)

  * **Topic:** Semantic Versioning (SemVer)
  * **Yeh Kya Hai?:** Yeh version numbers dene ka ek standard format (`MAJOR.MINOR.PATCH`) aur niyam hai. Jaise: `4.17.1`.
  * **Mechanism (The Rules):**
      * `MAJOR` (Pehla number): Tab badalta hai jab aap **breaking changes** karte hain (purana code naye version ke saath kaam nahi karega).
      * `MINOR` (Doosra number): Tab badalta hai jab aap **naye features** add karte hain, lekin purana code abhi bhi kaam karega (backward-compatible).
      * `PATCH` (Teesra number): Tab badalta hai jab aap **bug fixes** karte hain jo backward-compatible hon.
  * **`package.json` mein `^` aur `~` ka Matlab:**
      * `"express": "^4.17.1"`: Iska matlab hai ki `npm install` Express ka latest `4.x.x` version install kar sakta hai (jaise `4.18.0` ya `4.17.2`), lekin `5.0.0` (major version) install nahi karega. Isse aapko non-breaking updates mil jaate hain. Yeh default hai.
      * `"express": "~4.17.1"`: Iska matlab hai ki sirf patch updates hi allowed hain (jaise `4.17.2`, `4.17.3`), lekin minor update (`4.18.0`) nahi.

-----

#### 4\. Local vs. Global Packages

  * **Topic:** Local vs. Global Packages
  * **Local Packages:**
      * **Yeh Kya Hai?:** Yeh woh packages hain jo sirf ek particular project ke liye install kiye jaate hain. Yeh project ke andar `node_modules` folder mein rehte hain.
      * **Kaise Install Kare:** `npm install express`
      * **Kab Use Kare:** **99% of the time.** Aapke project ki sabhi dependencies (Express, Mongoose, React, etc.) hamesha local honi chahiye. Isse aapka project self-contained (aatmanirbhar) banta hai.
  * **Global Packages:**
      * **Yeh Kya Hai?:** Yeh woh packages hain jo aapke computer par ek central location par install hote hain aur aap unhe command line se kahin se bhi access kar sakte hain.
      * **Kaise Install Kare:** `npm install -g nodemon` (yahan `-g` ka matlab global hai).
      * **Kab Use Kare:** Sirf un packages ke liye jo command-line tools hain aur aap unhe kai projects mein istemal karte hain.
      * **Examples:** `nodemon`, `pm2` (process manager), `create-react-app`, `typescript`. Yeh sab utilities hain, project ki libraries nahi.
  * **Kya Savdhani Rakhe:** **Kabhi bhi project dependency ko globally install na karein.** Jaise, `npm install -g express` karna ek bahut badi galti hai. Isse aapka project aapki machine ke setup par nirbhar ho jaayega aur jab aap code kisi aur ke saath share karenge to woh nahi chalega.

---



### **Modules & Imports**

#### 1\. CommonJS (`require`) vs ES Modules (`import/export`)

  * **Topic:** CommonJS vs ES Modules
  * **Yeh Kya Hai?:** Yeh dono JavaScript mein code ko alag-alag files mein organize karne aur unhe ek-doosre ke saath share karne ke do alag-alag "module systems" ya "standards" hain.
  * **Analogy:** Inhe do alag-alag deshon ke **"Customs Department"** ki tarah samjhiye. Dono ka kaam samaan (code ko import/export karna) hai, lekin unke niyam (`syntax`) aur kaam karne ka tarika (mechanism) bilkul alag hai.

-----

  * **Sub-Topic: CommonJS (CJS)**
      * **Yeh Kya Hai?:** Yeh Node.js ka "classic" ya "purana" module system hai. Yeh `require()` function ka istemal karke modules ko import karta hai aur `module.exports` object ka istemal karke cheezein export karta hai.
      * **Kaise Kaam Hota Hai?:** `require` **synchronous** hota hai. Jab Node.js ek `require` statement dekhta hai, to woh wahan ruk jaata hai, file ko load karta hai, use execute karta hai, aur fir aage badhta hai. Yeh **runtime** par hota hai.
      * **Code Example:**
        ```javascript
        // 📁 math.js (Yeh hamara module hai)
        const add = (a, b) => a + b;
        const subtract = (a, b) => a - b;

        // Hum 'add' aur 'subtract' functions ko export kar rahe hain
        module.exports = { add, subtract };

        // 📁 app.js (Yahan hum module use kar rahe hain)
        // math.js module ko import kar rahe hain
        const math = require('./math.js');

        console.log("Addition:", math.add(10, 5));       // Output: 15
        console.log("Subtraction:", math.subtract(10, 5)); // Output: 5
        ```

-----

  * **Sub-Topic: ES Modules (ESM)**
      * **Yeh Kya Hai?:** Yeh JavaScript ka modern aur official standard module system hai. Yeh `import` aur `export` keywords ka istemal karta hai. Naye frontend frameworks (jaise React) aur ab Node.js bhi ise support karta hai.
      * **Kaise Kaam Hota Hai?:** `import` **asynchronous** hota hai aur **static** hota hai. "Static" ka matlab hai ki Node.js code run karne se **pehle hi** dekh leta hai ki kaun si file kya import/export kar rahi hai. Isse "tree shaking" jaisi optimizations sambhav hoti hain.
      * **Code Example:**
        ```javascript
        // 📁 math.mjs (Dhyan de, extension .mjs hai)
        export const add = (a, b) => a + b;
        export const subtract = (a, b) => a - b;

        // 📁 app.mjs
        import { add, subtract } from './math.mjs';

        console.log("Addition:", add(10, 5));       // Output: 15
        console.log("Subtraction:", subtract(10, 5)); // Output: 5
        ```
  * **Node.js mein ESM Kaise Use Karein?:**
      * By default, Node.js har `.js` file ko CommonJS maanta hai. ESM use karne ke liye, aapko inmein se ek kaam karna hoga:
    <!-- end list -->
    1.  Apni files ka extension `.mjs` (Module JavaScript) rakhein.
    2.  Ya, apne project ke `package.json` mein yeh line add karein: `"type": "module"`. Iske baad sabhi `.js` files ko ESM maana jaayega.
  * **Mukhya Farak (Comparison Table for Interview):**
    | Feature | CommonJS (`require`) | ES Modules (`import`) |
    | :--- | :--- | :--- |
    | **Loading** | Synchronous (Blocking) | Asynchronous (Non-blocking) |
    | **Syntax** | Dynamic (Runtime par resolve) | Static (Parse time par resolve) |
    | **Node.js Default** | Haan, classic standard | Nahi, configure karna padta hai |
    | **Keywords** | `require`, `module.exports` | `import`, `export`, `export default` |
  * **Kya Savdhani Rakhe:** Aap ek hi file mein `require` aur `import` syntax ko mix nahi kar sakte. Aapko project ki shuruaat mein hi ek system chun lena chahiye. Naye projects ke liye ESM behtar maana jaata hai.

-----

#### 2\. Creating Your Own Module

  * **Topic:** Apna Module Banana
  * **Yeh Kyun Zaroori Hai?:** Jab aapka code bada hone lagta hai, to saara code ek hi file mein rakhna "spaghetti code" ban jaata hai. Code ko alag-alag, reusable modules mein todne se woh saaf, organized, aur aasaani se maintain hone layak ban jaata hai.
  * **Analogy:** Yeh apna **"Toolkit"** banane jaisa hai. Agar aapke saare auzaar (functions) zameen par faile hon (ek file mein), to kaam karna mushkil hoga. Behtar hai ki aap plumbing ke tools ke liye ek alag toolbox (`plumbing.js`) aur electrical tools ke liye ek alag toolbox (`electric.js`) banayein.
  * **Kaise Banayein (Steps with Code):**
    1.  **Step 1: Module File Banayein** - Ek file banayein jismein aapka reusable code ho.
        ```javascript
        // 📁 logger.js
        const info = (message) => {
          console.log(`[INFO] [${new Date().toLocaleTimeString()}]: ${message}`);
        };

        const error = (message) => {
          console.error(`[ERROR] [${new Date().toLocaleTimeString()}]: ${message}`);
        };
        ```
    2.  **Step 2: Code ko Export Karein** - `module.exports` (CJS) ya `export` (ESM) ka istemal karein.
        ```javascript
        // logger.js (CommonJS way)
        module.exports = { info, error };
        ```
    3.  **Step 3: Module ko Doosri File mein Import/Use Karein**
        ```javascript
        // 📁 server.js
        const logger = require('./logger.js');

        logger.info("Server Prayagraj mein start ho raha hai...");
        // Output: [INFO] [11:15:57 PM]: Server Prayagraj mein start ho raha hai...

        // ...kuch kaam fail ho gaya...
        logger.error("Database se connect nahi ho paaya!");
        // Output: [ERROR] [11:15:57 PM]: Database se connect nahi ho paaya!
        ```
  * **Mukhya Baatein:** Node.js mein har file apne aap mein ek module hai. Us file ke andar ke variables aur functions by default **private** hote hain. Woh tabhi doosri files mein use ho sakte hain jab aap unhe explicitly **export** karein.

-----

#### 3\. Structuring a Modular Node Project

  * **Topic:** Modular Project Structure
  * **Yeh Kyun Zaroori Hai?:** Ek achha project structure aapke project ka "naksha" (map) hota hai. Yeh naye developers ko code samajhne mein madad karta hai, debugging aasan banata hai, aur project ko scale karna sambhav banata hai.
  * **Analogy:** Ek **"Sheher ki Planning"** karna. Ek achhe sheher mein residential areas (`models`), commercial districts (`routes`), industrial zones (`controllers`), aur unhe jodne waali sadkein (`server.js`) alag-alag aur organized hoti hain. Bina planning ke sheher ek aniyantrit (chaotic) jhopadpatti jaisa ban jaata hai.
  * **Ek Common Structure (Example for an Express.js App):**
    ```
    my-prayagraj-app/
    ├── node_modules/
    ├── config/         // Configuration files (DB URI, ports, API keys)
    │   └── db.js
    ├── controllers/    // Business logic (route hit hone par kya karna hai)
    │   ├── userController.js
    │   └── productController.js
    ├── models/         // Database schemas (e.g., Mongoose models)
    │   ├── User.js
    │   └── Product.js
    ├── public/         // Static files (CSS, images, client-side JS)
    ├── routes/         // API route definitions (e.g., /api/users)
    │   ├── userRoutes.js
    │   └── productRoutes.js
    ├── services/       // Reusable logic, third-party API calls
    │   └── emailService.js
    ├── .env            // Environment variables (secret keys)
    ├── .gitignore
    ├── package.json
    └── server.js       // App ka entry point, jahan sab kuch judta hai
    ```
  * **Har Folder ka Matlab:**
      * **`routes`:** Sirf URLs aur unse jude controller functions ko define karta hai.
      * **`controllers`:** Request aur response ko handle karne ka asli logic yahan hota hai.
      * **`models`:** Database ka structure (schema) define karta hai.
      * **`services`:** Woh logic jo kai controllers mein use ho sakta hai (jaise email bhejna).
      * **`config`:** Database connection jaisi configuration settings.
      * **`server.js`:** Express app ko initialize karta hai aur sabhi routes ko usse jodta hai.
  * **Mukhya Baatein:** Koi ek "perfect" structure nahi hota, lekin mukhya siddhant (principle) hai **"Separation of Concerns"**. Matlab, alag-alag kaam karne waale code ko alag-alag files/folders mein rakhein. Isse aapka project hamesha saaf-suthra aur manageable rahega.

---

### **Error Handling**

#### 1\. Try-catch in `async` functions

  * **Topic:** `try-catch` in `async` functions
  * **Yeh Kya Hai?:** Yeh modern JavaScript (`async/await`) mein asynchronous errors ko handle karne ka standard aur sabse saaf-suthra tarika hai. Yeh aapko async code mein errors ko usi tarah se pakadne deta hai jaise aap synchronous code mein pakadte hain.
  * **Analogy:** Yeh ek **"Safety Net"** jaisa hai. Aap apna "risky" kaam (jaise `await` karke database se data mangwana) `try` block (trapeze act) ke andar karte hain. Agar `await` kiya gaya Promise `reject` ho jaata hai (aap trapeze se gir jaate hain), to program crash nahi hota. Execution turant `catch` block (safety net) mein chala jaata hai, jo aapko pakad leta hai aur aapko situation ko gracefully handle karne ka mauka deta hai.
  * **Kaise Kaam Hota Hai?:** Jab aap `await` keyword ka istemal karte hain aur woh Promise `reject` ho jaata hai, to JavaScript engine ek error throw karta hai. `try...catch` block us thrown error ko pakad leta hai.
  * **Code Example:**
    ```javascript
    // Maan lijiye yeh function database se user laane ki koshish karta hai
    // Aur agar user nahi milta to Promise reject karta hai
    function findUser(id) {
      return new Promise((resolve, reject) => {
        setTimeout(() => {
          if (id === 1) {
            resolve({ id: 1, name: 'Aditya', city: 'Prayagraj' });
          } else {
            reject(new Error('User not found in database!'));
          }
        }, 1000);
      });
    }

    async function getUserDetails() {
      console.log('User details laane ki koshish kar rahe hain...');
      try {
        const user = await findUser(2); // Hum jaan boojh kar galat ID de rahe hain
        console.log('User mil gaya:', user.name);
      } catch (error) {
        // Safety net ne error pakad liya!
        console.error('Ek error aayi:', error.message);
        // Yahan aap user ko ek friendly message dikha sakte hain
      }
      console.log('Yeh line error ke baad bhi chalegi.');
    }

    getUserDetails();
    ```
  * **Kab Use Kare:** Jab bhi aap `async/await` syntax ka istemal kar rahe hon. Yeh `.catch()` promise chain se zyaada readable hai.

-----

#### 2\. Handling Uncaught Exceptions

  * **Topic:** Uncaught Exceptions ko Handle Karna
  * **Yeh Kya Hai?:** Yeh ek aisa **synchronous** error hai jise aapke code mein kahin bhi `try...catch` block se pakda nahi gaya. Jaise, `undefined` variable ki property access karna. By default, yeh aapki Node.js application ko turant crash kar deta hai.
  * **Analogy:** Yeh ek **"Earthquake"** jaisa hai jiska aapko andaza nahi tha. Isne aapke application ki neenv hila di hai. Agar aapke paas "Emergency Plan" nahi hai, to poori building (application) gir jaayegi (crash ho jaayegi).
  * **Mechanism:** Node.js ek global `process` object par `uncaughtException` event emit karta hai. Hum is event ko sun sakte hain.
  * **Code Example:**
    ```javascript
    // Emergency Plan
    process.on('uncaughtException', (err) => {
      console.error('EK UNCAUGHT EXCEPTION AAYI! Yeh ek bohot badi galti hai.');
      console.error(err.stack); // Poora error stack log karein
      // BEST PRACTICE: Yahan process ko band kar dein
      process.exit(1); // 1 ka matlab hai ki process error ke saath band hua
    });

    // Yeh code error throw karega
    const user = null;
    console.log(user.name); // TypeError: Cannot read properties of null
    ```
  * **Kya Savdhani Rakhe (Interview ka Sabse Zaroori Jawab):**
      * Official Node.js documentation ke anusaar, `uncaughtException` ke baad aapki application ek **unpredictable aur corrupt state** mein hoti hai.
      * **BEST PRACTICE:** Is event ko pakadne ke baad application ko chalate rehna (continue karna) behad khatarnak hai. Sahi tarika hai:
    <!-- end list -->
    1.  Error ko **synchronously** log karein (file mein ya logging service par).
    2.  Zaroori cleanup karein (jaise DB connection band karna).
    3.  **Process ko turant `process.exit(1)` se band kar dein.**
    4.  Ek process manager jaise **PM2** ya container orchestrator jaise **Kubernetes** ka istemal karein jo crash hone par application ko automatically restart kar de.

-----

#### 3\. Handling Unhandled Promise Rejections

  * **Topic:** Unhandled Promise Rejections ko Handle Karna
  * **Yeh Kya Hai?:** Yeh tab hota hai jab ek Promise `reject` hota hai, lekin us par error ko handle karne ke liye koi `.catch()` block ya `try...catch` (async/await ke saath) nahi laga hota.
  * **Analogy:** Yeh ek **"Registered Post"** jaisa hai jise kisi ne receive nahi kiya. Aapne ek zaroori error (rejected Promise) bheja, lekin use pakadne ke liye koi error handler nahi tha. Runtime pareshan ho jaata hai ki iska kya karein.
  * **Mechanism:** Iske liye bhi `process` object par `unhandledRejection` event hota hai.
  * **Code Example:**
    ```javascript
    process.on('unhandledRejection', (reason, promise) => {
      console.error('EK UNHANDLED REJECTION AAYA!');
      console.error('Reason:', reason.message);
      // Yahan bhi, best practice hai ki process ko gracefully exit karein
      process.exit(1);
    });

    function riskyPromise() {
      return Promise.reject(new Error("Database connection timeout!"));
    }

    // Humne is promise ko call kiya lekin .catch() nahi lagaya
    riskyPromise();
    ```
  * **Mukhya Baatein:** Node.js ke naye versions mein, by default ek unhandled rejection aapki application ko crash kar deta hai. Yeh achha hai, kyunki yeh developers ko majboor karta hai ki woh har promise rejection ko handle karein. **Global handler ek safety net hai, na ki local `try...catch` ka replacement.**

-----

#### 4\. Using Logging (`winston`, `pino`)

  * **Topic:** Logging ka Istemal
  * **Yeh Kyun Zaroori Hai?:** `console.log()` development ke liye theek hai, lekin production application ke liye yeh kaafi nahi. Jab aapki application live server par chalti hai, to aapko yeh jaanne ka ek vishwasniya (reliable) tarika chahiye ki andar kya ho raha hai, kaun se errors aa rahe hain, etc.
  * **Analogy:** Logging ek **"Flight ka Black Box"** jaisa hai. Jab plane (aapki application) crash hota hai, to investigators black box (log files) se hi pata lagate hain ki crash hone se theek pehle kya-kya hua tha. `console.log` ek casual baat-cheet hai; ek achha logger ek detailed, structured report hai.
  * **Ek Achhe Logger ki Visheshtayein:**
      * **Log Levels:** Alag-alag severity ke liye levels (e.g., `error`, `warn`, `info`, `debug`).
      * **Timestamps:** Har log ke saath samay.
      * **Structured Logging (JSON):** Logs ko JSON format mein likhna, taaki unhe aasani se search aur analyze kiya jaa sake.
      * **Transports:** Logs ko alag-alag jagah bhej sakna (console, file, ya Splunk/Datadog jaisi services).
  * **Popular Libraries:**
      * `winston`: Bahut popular, feature-rich, aur flexible hai.
      * `pino`: Apni high performance aur kam overhead ke liye jaana jaata hai.
  * **Code Example (Winston ke saath):**
    ```javascript
    // Pehle install karein: npm install winston
    const winston = require('winston');

    const logger = winston.createLogger({
      level: 'info', // Sirf 'info' ya usse upar ke level ke logs dikhao
      format: winston.format.json(), // Logs ko JSON format mein likho
      defaultMeta: { service: 'user-service' }, // Har log ke saath yeh meta add karo
      transports: [
        // Saare 'error' level ke logs ko 'error.log' file mein likho
        new winston.transports.File({ filename: 'error.log', level: 'error' }),
        // Saare logs ko 'combined.log' file mein likho
        new winston.transports.File({ filename: 'combined.log' }),
      ],
    });

    // Agar hum development environment mein hain, to console par bhi log karo
    if (process.env.NODE_ENV !== 'production') {
      logger.add(new winston.transports.Console({
        format: winston.format.simple(),
      }));
    }

    // Logger ko use karna
    logger.info('Server started in Prayagraj.');
    logger.warn('Database connection is a bit slow today.');
    logger.error('Failed to connect to payment gateway!');
    ```
  * **Kab Use Kare:** Har production-grade Node.js application mein.
  * **Kya Savdhani Rakhe:** Logs mein kabhi bhi sensitive data jaise passwords, API keys, ya user ki personal jaankari na daalein.


---

### **Node.js Advanced Concepts**

#### 1\. Child Processes & Worker Threads

  * **Topic:** Child Processes & Worker Threads
  * **Yeh Kyun Zaroori Hai?:** Hum jaante hain ki Node.js single-threaded hai, isliye yeh CPU-intensive kaamon ke liye aacha nahi hai. Child Processes aur Worker Threads, Node.js ko is seema (limitation) se bahar nikalne aur parallelism haasil karne ke do mukhya tareeke hain.
  * **Analogy (Busy CEO Revisited):**
      * **Child Process:** CEO (main process) ek kaam ke liye ek poori tarah se alag, independent **"Consultant"** (child process) ko hire karta hai. Consultant ka apna office, apne resources (memory) hote hain. CEO usse sirf formal letters (IPC - Inter-Process Communication) ke zariye baat karta hai. Yeh thoda bhaari (heavyweight) hai lekin bahut secure aur isolated hai.
      * **Worker Thread:** CEO apne hi office mein ek naya **"Assistant"** (worker thread) rakhta hai. Assistant, CEO ke saath office ke kuch resources (memory) share karta hai, jisse communication tez aur halka (lightweight) hota hai, lekin woh apna kaam alag se karta hai.

-----

  * **Sub-Topic: Child Processes**
      * **Yeh Kya Hai?:** Yeh aapko apne main Node.js process se ek naya, alag process shuru karne ki anumati deta hai. Iski apni alag memory aur event loop hota hai.
      * **Mukhya Functions (`child_process` module):**
          * `exec`: Ek shell command chalaane aur poora output buffer mein lene ke liye. Chhote-mote kaamon ke liye aacha hai.
          * `spawn`: Ek command chalaane aur data ko streams ke zariye handle karne ke liye. Lambe-samay tak chalne waale process (jaise video processing) ke liye behtar hai.
          * `fork`: `spawn` ka ek special version jo sirf doosre Node.js scripts ko chalaane ke liye hai. Ismein parent aur child ke beech communication ke liye ek built-in channel hota hai.
      * **Kab Use Kare?:** Jab aapko koi external command chalaani ho (jaise `git`, `python`, ya image processing tool) ya jab aapko tasks ke beech mazboot isolation chahiye ho.
      * **Code Example (`exec`):**
        ```javascript
        const { exec } = require('child_process');

        // 'dir' (Windows) ya 'ls -lh' (Linux/Mac) command chalaayein
        exec('dir', (error, stdout, stderr) => {
          if (error) {
            console.error(`exec error: ${error}`);
            return;
          }
          console.log(`Command ka Output:\n${stdout}`);
          if (stderr) {
            console.error(`Command ka Error Output:\n${stderr}`);
          }
        });
        ```

-----

  * **Sub-Topic: Worker Threads**
      * **Yeh Kya Hai?:** Yeh ek hi Node.js process ke andar, JavaScript code ko parallel mein alag-alag threads par chalaane ka tarika hai. Yeh Child Processes se halka (lightweight) hota hai.
      * **Kab Use Kare?:** Yeh **CPU-intensive JavaScript kaamon** ke liye banaya gaya hai. Jaise:
          * Complex calculations (Fibonacci, cryptography).
          * Badi JSON files ko parse karna.
          * Image processing.
      * **Code Example:**
        ```javascript
        // 📁 main.js (Main Thread)
        const { Worker } = require('worker_threads');
        const path = require('path');

        console.log("Main thread se kaam shuru...");

        // Ek naya worker banayein
        const worker = new Worker(path.join(__dirname, 'worker.js'));

        // Worker se message receive karein
        worker.on('message', (result) => {
          console.log(`Worker se result aaya: ${result}`);
        });

        worker.on('exit', (code) => console.log('Worker band ho gaya.'));

        // 📁 worker.js (Worker Thread)
        const { parentPort } = require('worker_threads');

        console.log("Worker thread ne kaam shuru kiya...");
        // Ek heavy, blocking calculation
        let result = 0;
        for (let i = 0; i < 10000000000; i++) {
          result += 1;
        }

        // Result main thread ko wapas bhejein
        parentPort.postMessage(result);
        ```
  * **Mukhya Farak (Interview Table):**
    | Feature | Child Process | Worker Thread |
    | :--- | :--- | :--- |
    | **Memory** | Alag Memory Space | Kuch Memory Share Kar Sakte Hain |
    | **Overhead** | High (Bhaari) | Low (Halka) |
    | **Best Use Case**| External Commands, OS tasks | CPU-Intensive JavaScript code |
    | **Communication**| Dheema (IPC) | Tez (Memory sharing) |

-----

#### 2\. Clustering & Scaling Node.js apps

  * **Topic:** Clustering & Scaling
  * **Yeh Kya Hai?:** Kyunki Node.js single-threaded hai, ek 16-core CPU waale server par bhi by default woh sirf **ek hi core** ka istemal karega. Baaki 15 cores bekar baithe rahenge. **Clustering** ek aisi technique hai jisse ek Node.js application apne hi jaise kai "clones" (worker processes) banakar server ke **sabhi CPU cores** ka istemal kar sakti hai.
  * **Analogy:** Ek **"Toll Plaza"**.
      * **Bina Clustering ke:** 16-lane ki highway par sirf **ek toll booth** khula hai. Saari gaadiyan ek hi line mein lagi hain. (Single Node.js Process).
      * **Clustering ke saath:** Aap har lane ke liye ek-ek toll booth khol dete hain. Ab traffic sabhi 16 lanes mein bant jaata hai aur aap 16 guna zyaada gaadiyan handle kar paate hain. (Cluster Module).
  * **Mechanism (`cluster` module):**
      * Node.js ka built-in `cluster` module `child_process.fork()` ka istemal karta hai.
      * Ek **Master Process** banta hai jo load balancer ki tarah kaam karta hai.
      * Master process har CPU core ke liye ek **Worker Process** fork karta hai.
      * Jab koi network request aati hai, to Master process use round-robin fashion mein kisi ek Worker ko de deta hai. Har worker ka apna event loop aur memory hota hai.
  * **Code Example:**
    ```javascript
    const cluster = require('cluster');
    const http = require('http');
    const numCPUs = require('os').cpus().length;

    if (cluster.isPrimary) { // Pehle isse isMaster kehte the
      console.log(`Master process ${process.pid} chal raha hai`);

      // Har CPU core ke liye ek worker fork karein
      for (let i = 0; i < numCPUs; i++) {
        cluster.fork();
      }

      cluster.on('exit', (worker, code, signal) => {
        console.log(`Worker ${worker.process.pid} mar gaya. Naya worker shuru kar rahe hain...`);
        cluster.fork(); // Agar worker crash ho jaaye to naya shuru kar do
      });
    } else {
      // Workers requests handle karenge
      http.createServer((req, res) => {
        res.writeHead(200);
        res.end(`Hello from Prayagraj! Handled by worker ${process.pid}\n`);
      }).listen(8000);

      console.log(`Worker ${process.pid} shuru hua`);
    }
    ```
  * **Mukhya Baatein & Savdhani:** `cluster` module ek hi machine par scaling (Vertical Scaling) ke liye hai. Real world mein, developers aksar `cluster` module ka code khud nahi likhte. Woh **PM2** jaise process manager ka istemal karte hain jo ek simple command se yeh sab automatically kar deta hai: `pm2 start server.js -i 0`. Yahan `-i 0` ka matlab hai "har available CPU core ke liye ek instance banao".

-----

#### 3\. Environment Variables & Config (`dotenv`)

  * **Topic:** Environment Variables & Config
  * **Yeh Kya Hai?:** Environment variables woh configuration settings hain jo aapke application code ke **bahar** rehti hain. Yeh us mahaul (environment) mein set ki jaati hain jahan aapka code chal raha hai (aapka local machine, server, ya Docker container).
  * **Yeh Kyun Zaroori Hai? (The 12-Factor App Principle):** **Configuration ko Code se alag rakho.** Aapko kabhi bhi sensitive information (jaise Database Password, API Keys) ya environment-specific settings (jaise `PORT`) ko seedhe apne code mein hardcode nahi karna chahiye.
  * **Analogy:** Ek **"Restaurant ka 'Special Instructions Board'"**. Recipe (`code`) sabke liye same hai. Lekin board (`.env` file) chef (`application`) ko aaj ke liye special instructions deta hai: "Aaj Oven \#2 istemal karna hai" (`PORT=8080`), "VIP guest ko peanuts se allergy hai" (`DB_PASSWORD=secret`).
  * **`dotenv` Package:**
      * **Yeh Kya Hai?:** Yeh ek bahut popular package hai jo ek `.env` file se environment variables ko `process.env` object mein load kar deta hai.
      * **Kaise Kaam Hota Hai?:**
        1.  `npm install dotenv`.
        2.  Project ke root mein ek `.env` file banayein.
        3.  Apni main file (`server.js`) mein sabse upar `require('dotenv').config()` likhein.
  * **Code Example:**
    **📁 `.env` file:**
    ```
    PORT=5000
    DB_URI="mongodb://localhost:27017/my-prayagraj-db"
    API_KEY="thisIsASecretKey123"
    ```
    **📁 `server.js` file:**
    ```javascript
    require('dotenv').config(); // Sabse upar hona chahiye

    const express = require('express');
    const app = express();

    const PORT = process.env.PORT || 3000;
    const dbUri = process.env.DB_URI;

    console.log(`Database URI: ${dbUri}`);

    app.listen(PORT, () => {
      console.log(`Server port ${PORT} par chal raha hai.`);
    });
    ```
  * **Kya Savdhani Rakhe:** **Hamesha apni `.env` file ko `.gitignore` mein add karein.** Secret keys aur passwords ko kabhi bhi Git repository par commit na karein, chahe woh private hi kyun na ho.

-----

#### 4\. Debugging in Node.js

  * **Topic:** Debugging
  * **Yeh Kyun Zaroori Hai?:** `console.log()` har jagah lagana debugging ka ek inefficient tarika hai. Ek professional developer proper debugging tools ka istemal karta hai taaki woh application ke execution ko line-by-line inspect kar sake.
  * **Analogy:** Ek **"Doctor ki X-Ray Machine"**. `console.log` karna patient se poochne jaisa hai, "kahan dard ho raha hai?". Ek debugger (X-Ray machine) aapko application ke andar (runtime state) jhaankne deta hai taaki aap problem (bug) ki astitv (exact) wajah aur jagah dhoondh sakein.
  * **Mukhya Tarike:**
    1.  **Built-in Node.js Inspector:**
          * **Kaise Use Kare:** Apni application ko `--inspect` flag ke saath run karein: `node --inspect server.js`. Agar aap chahte hain ki application pehli line par hi ruk jaaye, to `--inspect-brk` ka istemal karein.
          * **Mechanism:** Node.js ek debugging server shuru karta hai. Aap isse **Google Chrome browser** se connect kar sakte hain. Chrome mein `chrome://inspect` URL kholen, aur aapko apna Node.js process dikhega. Us par click karne se Chrome DevTools khul jaayega, jahan aap breakpoints laga sakte hain, variables dekh sakte hain, aur code ko step-by-step chala sakte hain.
    2.  **VS Code Debugger (Sabse Aasan aur Popular):**
          * **Kaise Use Kare:** VS Code mein ek shandaar built-in debugger hai.
            1.  Apne code mein jahan rukna hai, line number ke paas click karke ek **breakpoint** (laal dot) lagayein.
            2.  Side bar mein "Run and Debug" icon par click karein aur "Run and Debug" (Node.js) button dabayein (ya seedhe `F5` key dabayein).
            3.  Debugger shuru ho jaayega aur aapke breakpoint par aakar ruk jaayega. Ab aap variables inspect kar sakte hain, call stack dekh sakte hain, aur execution ko control kar sakte hain.
  * **Mukhya Baatein:** `console.log` ki jagah ek proper debugger ka istemal karna aapka ghanton ka samay bacha sakta hai aur aapko code ki gehri samajh deta hai. Professional development ke liye yeh ek anivarya skill hai.

---
### **Testing & Best Practices**

#### 1\. Unit Testing with `Mocha`/`Jest`

  * **Topic:** Unit Testing with `Mocha`/`Jest`
  * **Yeh Kya Hai?:** Unit Testing, software testing ka woh level hai jahan aap apne code ke sabse chhote, isolated hisson ("units") ko test karte hain. Aam taur par, ek "unit" ek function ya ek method hota hai. Iska maqsad yeh sunishchit karna hai ki har chhota purza (part) akele mein sahi kaam kar raha hai.
  * **Analogy:** Yeh ek **"Car Mechanic"** jaisa hai jo poori car chalaane se pehle uske har ek purze ko alag-alag check karta hai. Jaise, woh battery, spark plug, aur tire pressure ko individually test karega. Yeh Unit Testing hai. Poori car ko road par chala kar dekhna Integration Testing kehlata hai.
  * **Mocha vs. Jest (Popular Test Frameworks):**
      * **`Mocha`:** Ek flexible aur purana testing **framework** hai. Yeh aapko test structure (`describe`, `it`) deta hai, lekin assertions (check karne ke liye, e.g., `expect(a).to.equal(b)`) ke liye aapko `Chai` jaisi alag library aur mocks ke liye `Sinon` jaisi library laani padti hai.
      * **`Jest`:** Facebook ka banaya hua ek **"All-in-one"** testing platform hai. Ismein test runner, assertion library (`expect`), aur mocking capabilities sab kuch pehle se hi shaamil hota hai. Iska setup bahut aasan (zero-config) hota hai.
  * **Kab Kise Use Kare?:** Naye projects aur zyadatar developers ke liye **Jest** behtar vikalp hai kyunki yeh aasan aur feature-rich hai. `Mocha` unke liye hai jinhe poora control chahiye aur woh apni pasand ki libraries ko jodkar apna testing suite banana chahte hain.
  * **Code Example (Jest ke saath):**
    1.  Pehle install karein: `npm install --save-dev jest`
    2.  `package.json` mein `scripts` ke andar yeh add karein: `"test": "jest"`
    3.  Ek file banayein:
        ```javascript
        // 📁 math.js
        const add = (a, b) => {
          if (typeof a !== 'number' || typeof b !== 'number') {
            throw new Error('Inputs must be numbers');
          }
          return a + b;
        };
        module.exports = add;
        ```
    4.  Usi ke saath ek test file banayein (`.test.js` ya `.spec.js` extension ke saath):
        ```javascript
        // 📁 math.test.js
        const add = require('./math');

        // 'describe' ka istemal karke related tests ko group karein
        describe('add function', () => {
          
          // 'it' ya 'test' ka istemal karke ek individual test case likhein
          it('should add two positive numbers correctly', () => {
            // Assertion: Hum expect kar rahe hain ki add(2, 3) ka result 5 ho
            expect(add(2, 3)).toBe(5);
          });

          it('should throw an error if inputs are not numbers', () => {
            // Hum expect kar rahe hain ki yeh function ek error throw karega
            expect(() => add('2', 3)).toThrow('Inputs must be numbers');
          });

        });
        ```
    5.  Ab terminal mein `npm test` run karein. Jest automatically `.test.js` files ko dhoondh kar chala dega.

-----

#### 2\. Supertest for API Testing

  * **Topic:** Supertest for API Testing
  * **Yeh Kya Hai?:** Supertest ek library hai jo khaas taur par Node.js ke HTTP servers (APIs) ko test karne ke liye banayi gayi hai. Yeh aapko apne code se hi API endpoints par request maarne aur unke response ko check karne ki suvidha deti hai. Yeh ek tarah ki **Integration Testing** hai.
  * **Analogy:** Yeh ek **"Food Inspector"** jaisa hai jo restaurant (`API`) mein jaakar ek poora meal (`request`) order karta hai. Woh check karta hai ki:
      * Order sahi se deliver hua ya nahi (`status code 200 OK`).
      * Dish sahi dikh rahi hai ya nahi (`Content-Type: application/json`).
      * Dish ka swaad waisa hi hai jaisa expect kiya tha (`response body mein sahi data`).
  * **Kaise Kaam Hota Hai?:** Yeh aapke Express `app` object ke upar ek wrapper ki tarah kaam karta hai. Iske liye aapko apna server manually start karne ki zaroorat nahi hoti.
  * **Code Example:**
    ```javascript
    // Maan lijiye aapke paas ek Express app hai
    // 📁 app.js
    const express = require('express');
    const app = express();
    app.get('/user', (req, res) => {
      res.status(200).json({ name: 'Aditya', city: 'Prayagraj' });
    });
    module.exports = app;

    // 📁 app.test.js
    const request = require('supertest');
    const app = require('./app');

    describe('GET /user', () => {
      it('should respond with user data in JSON format', async () => {
        const response = await request(app)
          .get('/user')
          .expect('Content-Type', /json/) // Check header
          .expect(200); // Check status code

        // Check response body
        expect(response.body.name).toBe('Aditya');
        expect(response.body.city).toBe('Prayagraj');
      });
    });
    ```
  * **Kab Use Kare:** Apne API routes aur controllers likhne ke baad, unki functionality ko end-to-end test karne ke liye.

-----

#### 3\. Linting with ESLint

  * **Topic:** Linting with ESLint
  * **Yeh Kya Hai?:** Linting code ko automatically analyze karke programmatic aur stylistic errors dhoondhne ka process hai. **ESLint** JavaScript/Node.js ke liye sabse popular linter hai.
  * **Analogy:** Yeh aapke code ke liye ek **"Grammar Teacher"** hai. Teacher yeh check nahi karta ki aapki story achhi hai ya nahi (woh kaam Testing ka hai). Teacher spelling mistakes (`typos`), grammatical errors (`bugs like unused variables`), aur formatting rules (`coding style`) check karta hai.
  * **Fayde (Benefits):**
    1.  **Bugs Pakadta Hai:** Jaise, `if (x = 5)` (assignment) ko pakad lega jab aap `if (x == 5)` (comparison) likhna chahte the.
    2.  **Consistent Style:** Poori team ek hi coding style follow karti hai, jisse code readable rehta hai.
    3.  **Best Practices Laagu Karta Hai:** Jaise, `var` ki jagah `const`/`let` use karne ko bolna.
  * **Kaise Setup Kare:**
    1.  `npm install --save-dev eslint`
    2.  `npx eslint --init` (Yeh aapse kuch sawaal pooch kar ek `.eslintrc.json` config file bana dega).
    3.  `package.json` mein script add karein: `"lint": "eslint ."`

-----

#### 4\. Prettier for Formatting

  * **Topic:** Prettier for Formatting
  * **Yeh Kya Hai?:** Prettier ek **"opinionated code formatter"** hai. Iska sirf ek hi kaam hai: aapke code ko lena aur use ekdam consistent style mein format kar dena. Use is baat se koi matlab nahi ki aapka code sahi hai ya galat.
  * **ESLint vs. Prettier (Interview ka zaroori sawaal):**
      * **ESLint (Code Quality):** Code mein potential bugs aur "code smells" dhoondhta hai.
      * **Prettier (Code Style):** Sirf code ki formatting (indentation, spacing, semicolons, line length) theek karta hai.
  * **Analogy:** Agar ESLint "Grammar Teacher" hai, to Prettier ek **"Automatic Typewriter"** hai. Aap use apni handwritten copy dete hain, aur woh use bilkul saaf-suthri, consistent margin aur spacing ke saath type kar deta hai, bina aapke shabdon ko badle.
  * **Kaise Kaam Hota Hai?:** Yeh aapke code ko parse karke ek AST (Abstract Syntax Tree) banata hai aur fir us tree se code ko "re-print" karta hai, apne sakt (strict) niyamon ke anusaar.
  * **Kab Use Kare:** Har project mein\! Ise apne code editor (jaise VS Code) mein integrate karein taaki har baar file save karne par code automatically format ho jaaye. Isse team mein code style ko lekar hone waali behes (arguments) khatm ho jaati hai.
  * **Mukhya Baatein:** Industry standard hai **ESLint aur Prettier ko ek saath istemal karna**. ESLint code quality ke liye aur Prettier code formatting ke liye. Yeh dono milkar aapke codebase ko professional aur maintainable banate hain.

---
### **Deployment & DevOps**

#### 1\. Environment-based Configs

  * **Topic:** Environment-based Configs
  * **Yeh Kya Hai?:** Yeh ek aisi practice hai jahan aap apni application ke liye alag-alag environments (mahaul) ke liye alag-alag configuration settings rakhte hain. Aam taur par 3 environments hote hain:
    1.  **Development:** Aapka local machine, jahan aap code likhte hain.
    2.  **Staging/Testing:** Production jaisa ek testing server, jahan aap code ko live karne se pehle test karte hain.
    3.  **Production:** Asli live server, jahan aapke users application ko istemal karte hain.
  * **Yeh Kyun Zaroori Hai?:** Aap apne local machine par development ke liye ek alag database (local MongoDB) istemal karna chahenge, jabki production mein aap ek alag, powerful database (Atlas MongoDB) istemal karenge. Har environment ke liye API keys, ports, aur doosri settings alag hoti hain.
  * **Analogy:** Yeh ek **"Actor ke alag-alag Costumes"** jaisa hai.
      * **Development (Rehearsal):** Actor practice karte waqt casual kapde pehenta hai (local DB, test API keys).
      * **Staging (Dress Rehearsal):** Actor stage par aane se pehle poora costume pehenkar practice karta hai (testing DB, real-jaisi settings).
      * **Production (Live Show):** Actor audience ke saamne apna final, best costume pehenta hai (live DB, real API keys).
        Actor (`code`) wahi rehta hai, lekin uska costume (`config`) environment ke hisab se badal jaata hai.
  * **Kaise Kaam Hota Hai?:** Standard tarika `NODE_ENV` environment variable ka istemal karna hai.
  * **Code Example:**
    ```javascript
    // 📁 config/index.js
    const env = process.env.NODE_ENV || 'development';

    const configs = {
      development: {
        db_uri: 'mongodb://localhost:27017/dev_db',
        port: 3000
      },
      production: {
        db_uri: process.env.PROD_DB_URI,
        port: process.env.PORT
      }
    };

    module.exports = configs[env];

    // 📁 server.js
    const config = require('./config');
    // Ab 'config' object mein current environment ki settings hongi
    console.log(`Application port ${config.port} par chal rahi hai.`);
    console.log(`Database se ${config.db_uri} par connect kar rahe hain.`);
    ```
    Aap server is tarah chalaate hain: `NODE_ENV=production node server.js`.

-----

#### 2\. PM2 for Process Management

  * **Topic:** PM2 for Process Management
  * **Yeh Kya Hai?:** PM2 (Process Manager 2) Node.js applications ke liye ek production-ready process manager hai. Yeh ek command-line tool hai jo live server par aapki Node.js app ko chalane, monitor karne, aur manage karne ke kaam ko bahut aasan bana deta hai.
  * **`node server.js` Production mein Kyun Kaafi Nahi Hai?**
      * Agar aapki app crash hoti hai, to woh band ho jaati hai aur apne aap restart nahi hoti.
      * Agar server reboot hota hai, to aapko app manually start karna padta hai.
      * Yeh server ke sirf ek CPU core ka istemal karta hai.
  * **Analogy:** PM2 aapki application ke liye ek **"Intelligent Babysitter"** ya **"Manager"** hai.
      * `node server.js` (Akela Chhod Dena): Aap apne bachhe (`app`) ko ghar par akela chhod dete hain. Agar bachha girta hai (`crash`), to use uthane wala koi nahi.
      * `pm2 start server.js` (Babysitter): Aap ek hoshiyar babysitter (`PM2`) ko kaam par rakhte hain. Agar bachha girta hai, to babysitter use turant utha deta hai (**auto-restart**). Babysitter bachhe ki health par nazar rakhta hai (**monitoring**), uska diary likhta hai (**logging**), aur ek saath kai bachhon ko sambhal sakta hai (**clustering**).
  * **Mukhya Features (Key Features):**
      * **Auto Restart:** App crash hone par automatically restart karna.
      * **Clustering:** Ek hi command se aapke app ko cluster mode mein chalana taaki saare CPU cores ka istemal ho.
      * **Log Management:** Aapke app ke saare logs (errors, console.log) ko manage karna.
      * **Monitoring:** CPU aur Memory usage ko monitor karna.
      * **0-Downtime Reloads:** App ko update karte waqt bina band kiye restart karna.
  * **Mukhya Commands:**
    ```bash
    # App start karna
    pm2 start server.js --name "my-prayagraj-app"

    # Saare apps ki list dekhna
    pm2 list

    # App ko cluster mode mein (sabhi cores par) start karna
    pm2 start server.js -i 0

    # App ke logs dekhna
    pm2 logs my-prayagraj-app

    # App ko restart karna
    pm2 restart my-prayagraj-app
    ```
  * **Kab Use Kare:** Har Node.js application ke liye jo production server par chal rahi ho.

-----

#### 3\. Node.js in Docker

  * **Topic:** Node.js in Docker
  * **Yeh Kya Hai? (Docker):** Docker applications ko **containers** mein banane, deploy karne, aur chalaane ka ek platform hai. Ek container ek halka-phulka (lightweight), standalone package hota hai jismein ek application ko chalaane ke liye zaroori har cheez hoti hai—code, runtime (Node.js), system tools, libraries, sab kuch.
  * **Yeh Kyun Zaroori Hai?:** Yeh "**mere machine par to chalta hai**" waali problem ko hamesha ke liye solve kar deta hai. Ek container bilkul astitv (identical) tarike se chalta hai, chahe woh aapke laptop par ho, testing server par ho, ya AWS ke production server par.
  * **Analogy:** Ek **"Magical Shipping Container"**.
      * **Bina Docker ke:** Aap ek naazuk kursi (`aapka app`) ko seedhe truck mein rakh dete hain. Raaste mein sadak kharab ho sakti hai, mausam badal sakta hai, aur kursi toot sakti hai (`app crash ho jaata hai kyunki server par Node.js ka version alag hai`).
      * **Docker ke saath:** Aap us kursi ke liye ek custom, padded, climate-controlled box (`Docker image`) banate hain. Box ke andar aap kursi, use assemble karne ke saare auzaar, aur instruction manual (`Dockerfile`) rakhte hain. Ab aap is box (`Docker container`) ko kahin bhi bhej sakte hain, aur aapko 100% vishwas hai ki kursi bilkul sahi-salamat pahunchegi aur kaam karegi.
  * **`Dockerfile` (Instruction Manual):**
    ```dockerfile
    # Step 1: Ek base image chunein (OS + Node.js)
    FROM node:18-alpine

    # Step 2: Container ke andar working directory set karein
    WORKDIR /app

    # Step 3: Dependencies install karein
    COPY package*.json ./
    RUN npm install --production

    # Step 4: Apna poora application code copy karein
    COPY . .

    # Step 5: Apne app ka port expose karein
    EXPOSE 3000

    # Step 6: Container start hone par kya command chalani hai
    CMD ["node", "server.js"]
    ```
  * **Mukhya Baatein:** Docker modern DevOps aur microservices ki neenv hai. Ise seekhna behad zaroori hai.

-----

#### 4\. CI/CD Pipeline Basics

  * **Topic:** CI/CD Pipeline
  * **Yeh Kya Hai?:**
      * **CI (Continuous Integration):** Ek aisi practice jahan developers lagatar apne code changes ko ek central repository (GitHub) mein merge karte rehte hain. Har merge ke baad, ek automated process code ko build aur test karta hai.
      * **CD (Continuous Delivery/Deployment):** CI stage pass hone ke baad, application ko automatically testing ya production environment mein deploy karne ki practice.
  * **Analogy:** Ek **"Automated Food Factory"**.
    1.  **Developer (Kisaan):** Kisaan factory mein kachha maal (`naya code`) laata hai.
    2.  **CI (Automated Kitchen):** Jaise hi maal aata hai, automated machines uski quality check karti hain (`linting`), use mix karti hain (`build`), ek sample banakar taste karti hain (`testing`). Agar sample kharab nikla, to poora batch reject ho jaata hai aur kisaan ko khabar kar di jaati hai.
    3.  **CD (Automated Delivery):** Agar sample perfect hai, to machines poore maal ko pack karti hain (`Docker image build`), aur use delivery truck (`deployment script`) par load karke restaurant (`production server`) tak bhej deti hain. Yeh sab kuch apne aap hota hai.
  * **Kaise Kaam Hota Hai?:** Tools jaise **GitHub Actions**, Jenkins, ya CircleCI ka istemal karke. Aap ek YAML file mein poora workflow define karte hain.
  * **Ek Sample GitHub Actions Workflow:**
    1.  Developer `git push` karta hai.
    2.  GitHub is push ko detect karke ek virtual machine start karta hai.
    3.  **CI:** Machine `npm install` chalaati hai, fir `npm run lint`, aur fir `npm test`. Agar koi bhi step fail hota hai, to process ruk jaata hai.
    4.  **CD:** Agar sab kuch pass ho jaata hai, to machine ek Docker image build karti hai, use Docker Hub par push karti hai, aur fir aapke server (e.g., AWS) par login karke us naye image ko deploy kar deti hai.
  * **Mukhya Baatein:** CI/CD manual deployments se hone waali galtiyon ko khatm karta hai aur process ko bahut tez bana deta hai. Isse developers naye features ko users tak jaldi aur surakshit roop se pahuncha paate hain.

---
### **1. What is Node.js and why is it used?**

👉 **Answer:**

* Node.js ek **JavaScript runtime environment** hai jo Chrome ke **V8 engine** par based hai.
* Ye JavaScript ko **server-side** run karne deta hai.
* Iska use mainly **scalable, fast, non-blocking I/O based applications** banane ke liye hota hai jaise APIs, real-time chat apps, streaming services.

---

### **2. How does Node.js handle child threads?**

👉 **Answer:**

* Node.js **single-threaded event loop** par kaam karta hai, but internally wo **libuv library** ke through multiple threads use karta hai background tasks ke liye.
* Heavy tasks (I/O, file operations, crypto, compression) ko ye background threads mein bhejta hai aur jab result ready hota hai to event loop ko notify karta hai.
* Agar developer ko alag thread banana ho to **child\_process module** ya **worker\_threads** module use hota hai.

---

### **3. Describe the event-driven programming in Node.js.**

👉 **Answer:**

* Event-driven ka matlab hai ki program **events** (jaise request aayi, data mila, error hua) ke base par respond karega.
* Node.js mein **EventEmitter** module hota hai jisme `on` (listen) aur `emit` (trigger) methods use hote hain.
* Example: Server request aayi → event trigger → callback function execute ho gaya.

---

### **4. What is the event loop in Node.js?**

👉 **Answer:**

* Event loop ek **mechanism** hai jo non-blocking I/O ko manage karta hai.
* Ye continuously check karta hai ki koi pending operation complete hua hai ya koi new event aaya hai.
* Ye hi reason hai ki Node.js **asynchronous** aur **high-performance** hota hai.

---

### **5. What is the difference between Node.js and traditional web server technologies?**

👉 **Answer:**

* Traditional servers (jaise Apache, PHP) **multi-threaded** hote hain → har request ke liye ek naya thread.
* Node.js **single-threaded + event-driven** hai → ek hi thread multiple requests ko handle karta hai.
* Is wajah se Node.js **lightweight aur scalable** hota hai, especially I/O intensive apps ke liye.

---

### **6. Explain what “non-blocking” means in Node.js.**

👉 **Answer:**

* Non-blocking ka matlab hai ki ek request complete hone ka wait nahi karna padta.
* Example: Agar file read ho rahi hai, to dusra code uske saath parallel run kar sakta hai. Jab file read complete hogi tab callback execute hoga.
* Is wajah se Node.js fast aur efficient hai.

---

### **7. How do you update Node.js to the latest version?**

👉 **Answer:**

* Different ways:

  * **Using nvm (Node Version Manager):**

    ```bash
    nvm install latest
    nvm use latest
    ```
  * **Manual download** from official Node.js website.
  * **On Linux/Ubuntu:**

    ```bash
    sudo apt update
    sudo apt install -y nodejs npm
    ```

---

### **8. What is “npm” and what is it used for?**

👉 **Answer:**

* **npm (Node Package Manager)** ek tool hai jo Node.js ke sath aata hai.
* Ye **open-source packages/modules** ko install, manage aur update karne ke liye use hota hai.
* Example: `npm install express`

---

### **9. How do you manage packages in a Node.js project?**

👉 **Answer:**

* Packages ko **npm** ya **yarn** ke through manage karte hain.
* Example:

  * Install → `npm install package-name`
  * Remove → `npm uninstall package-name`
  * Global install → `npm install -g package-name`
* Saare installed packages aur dependencies ka record **package.json** file me store hota hai.

---

### **10. What is a package.json file?**

👉 **Answer:**

* `package.json` ek configuration file hai jo har Node.js project ka part hoti hai.
* Isme project ka **metadata** (name, version, author) aur **dependencies** (konse packages chahiye) likhe hote hain.
* Example:

  ```json
  {
    "name": "my-app",
    "version": "1.0.0",
    "dependencies": {
      "express": "^4.18.0"
    }
  }
  ```

---

### **1. Describe some of the core modules of Node.js.**

👉 **Answer:**
Node.js mein kuch built-in **core modules** hote hain jo bina install kiye use ho jaate hain:

* **http** → server banane ke liye
* **fs (File System)** → files read/write karne ke liye
* **path** → file/directory path manage karne ke liye
* **url** → URL parse aur format karne ke liye
* **events** → event-driven programming ke liye
* **os** → system related info (CPU, memory, hostname) ke liye

---

### **2. How do you create a simple server in Node.js using the HTTP module?**

👉 **Answer:**

* **http module** import karo, server banao aur listen karao.
* Example:

```js
const http = require('http');

const server = http.createServer((req, res) => {
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Hello World from Node.js server!');
});

server.listen(3000, () => {
  console.log('Server running on port 3000');
});
```

---

### **3. Explain the purpose of the File System (fs) module.**

👉 **Answer:**

* `fs` module ka use **files aur directories handle karne** ke liye hota hai.
* Operations:

  * Read → `fs.readFile`
  * Write → `fs.writeFile`
  * Delete → `fs.unlink`
  * Rename → `fs.rename`
* Synchronous aur asynchronous dono methods provide karta hai.

---

### **4. What is the Buffer class in Node.js?**

👉 **Answer:**

* **Buffer class** raw binary data handle karne ke liye use hoti hai.
* Useful jab data **stream hota hai** (like video, audio, network packets).
* Example: File read karte waqt data pehle Buffer me aata hai.

---

### **5. What are streams in Node.js and what types are available?**

👉 **Answer:**

* Streams ka use **large data** efficiently handle karne ke liye hota hai bina pura data ek saath memory me load kiye.
* Types of Streams:

  1. **Readable** → data read karne ke liye (e.g., file read)
  2. **Writable** → data likhne ke liye (e.g., file write)
  3. **Duplex** → read aur write dono (e.g., sockets)
  4. **Transform** → data ko modify karte waqt (e.g., compression, encryption)

---

### **6. How do you read and write files in Node.js?**

👉 **Answer:**

* **Read file:**

```js
const fs = require('fs');
fs.readFile('file.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data);
});
```

* **Write file:**

```js
fs.writeFile('file.txt', 'Hello Node.js', (err) => {
  if (err) throw err;
  console.log('File written successfully!');
});
```

---

### **7. How do you use the EventEmitter in Node.js?**

👉 **Answer:**

* `events` module ka `EventEmitter` class use hota hai custom events ke liye.
* Example:

```js
const EventEmitter = require('events');
const emitter = new EventEmitter();

emitter.on('greet', () => {
  console.log('Hello from EventEmitter!');
});

emitter.emit('greet');
```

---

### **8. What is the QueryString module?**

👉 **Answer:**

* `querystring` module ka use **URL query parameters** ko parse aur format karne ke liye hota hai.
* Example:

```js
const querystring = require('querystring');
const parsed = querystring.parse('name=Harsh&age=21');
console.log(parsed); // { name: 'Harsh', age: '21' }
```

---

### **9. How do you manage path operations in Node.js?**

👉 **Answer:**

* `path` module ka use file aur directory paths manage karne ke liye hota hai.
* Useful methods:

  * `path.join()` → safe tarike se paths jodna
  * `path.basename()` → file ka naam lena
  * `path.dirname()` → parent directory lena
  * `path.extname()` → file extension lena

---



### **1. What are callbacks in Node.js?**

👉 **Answer:**

* Callback ek **function hota hai jo kisi doosre function ko argument ke roop me diya jata hai** aur wo tab execute hota hai jab operation complete ho jata hai.
* Node.js me callbacks mainly **asynchronous tasks** ke liye use hote hain (e.g., file read, DB query).

**Example:**

```js
fs.readFile('file.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data);
});
```

---

### **2. What is callback hell and how can it be avoided?**

👉 **Answer:**

* **Callback Hell** tab hota hai jab multiple asynchronous tasks ke liye nested callbacks ban jaate hain, code unreadable aur difficult ho jaata hai.
* Example:

```js
doSomething(() => {
  doSomethingElse(() => {
    doAnotherThing(() => {
      // nested callbacks → messy
    });
  });
});
```

✅ **Avoid karne ke ways:**

1. Code ko modular aur functions me todna.
2. **Promises** ka use karna.
3. **Async/Await** ka use karna.

---

### **3. Explain promises in Node.js.**

👉 **Answer:**

* Promise ek **object** hai jo asynchronous operation ka result represent karta hai (success ya failure).
* States: **Pending → Fulfilled → Rejected**
* Promise ke saath `.then()` aur `.catch()` use hota hai.

**Example:**

```js
const fs = require('fs').promises;

fs.readFile('file.txt', 'utf8')
  .then(data => console.log(data))
  .catch(err => console.error(err));
```

---

### **4. How do async/await functions work in Node.js?**

👉 **Answer:**

* `async/await` Promises ke upar ek **syntactic sugar** hai jo asynchronous code ko **synchronous jaisa dikhata hai**.
* `async` function hamesha ek Promise return karta hai.
* `await` keyword promise ke resolve hone ka wait karta hai.

**Example:**

```js
const fs = require('fs').promises;

async function readFile() {
  try {
    const data = await fs.readFile('file.txt', 'utf8');
    console.log(data);
  } catch (err) {
    console.error(err);
  }
}

readFile();
```

---

### **5. What is the difference between synchronous and asynchronous methods in the fs module?**

👉 **Answer:**

* **Synchronous methods (`fs.readFileSync`)** → Execution ko block karte hain jab tak task complete na ho. Fast nahi hote, single-thread ko block kar dete hain.
* **Asynchronous methods (`fs.readFile`)** → Non-blocking hote hain, callback/promise return karte hain. Ye recommended hai scalable applications ke liye.

**Example:**

* Sync:

```js
const data = fs.readFileSync('file.txt', 'utf8');
console.log(data); // Blocks until file is read
```

* Async:

```js
fs.readFile('file.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data); // Non-blocking
});
```

---



### **Q1. Yeh code kaise kaam karta hai?**

👉 **Answer:**

```js
const fs = require('fs').promises;

async function readFile() {
  try {
    const data = await fs.readFile('file.txt', 'utf8');
    console.log(data);
  } catch (err) {
    console.error(err);
  }
}

readFile();
```

* **Step 1:** `require('fs').promises` → Ye `fs` module ka **promises version** import karta hai, jisme har function ek **Promise return** karta hai.
* **Step 2:** `async function readFile()` → Jab bhi ek function `async` hota hai, wo hamesha ek **Promise return** karega.
* **Step 3:** `await fs.readFile('file.txt', 'utf8')` → Ye line file ko **asynchronously read** karti hai. `await` ensure karta hai ki jab tak Promise resolve/reject na ho, agla code execute na ho.
* **Step 4:** Agar file successfully read ho gayi to data console me print hoga. Agar koi error aayi (jaise file na mili) to `catch` block execute hoga.

📌 Yaani ye code **asynchronous, non-blocking, aur readable** tarike se file ko read karta hai.

---

### **Q2. Synchronous aur Asynchronous methods `fs` module me kaise kaam karte hain?**

👉 **Answer:**

#### **Synchronous (`fs.readFileSync`)**

* Execution **block ho jata hai** jab tak file read na ho jaye.
* Example:

```js
const fs = require('fs');
const data = fs.readFileSync('file.txt', 'utf8');  
console.log(data);  
console.log("Ye tabhi chalega jab file puri read ho jaye.");
```

* Yahan **dusra code wait karega** jab tak file read complete na ho.

---

#### **Asynchronous (`fs.readFile`)**

* Execution **block nahi hota**. File read background me hota hai aur baaki code chal sakta hai.
* Example:

```js
const fs = require('fs');
fs.readFile('file.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data);  // Ye baad me chalega jab file read ho jaye
});
console.log("Ye turant print hoga (non-blocking)");
```

* Yahan file read hone ke liye wait nahi kiya gaya.

---

### **Q3. Sync aur Async methods me problem aur advantage kya hai?**

👉 **Answer:**

#### **Synchronous (Problem + Advantage):**

* **Advantage:** Simple aur easy to understand code.
* **Problem:** Blocking behavior. Agar ek file bada hai to pura thread block ho jayega, aur dusre clients wait karenge. **Scalability problem**.

#### **Asynchronous (Problem + Advantage):**

* **Advantage:** Non-blocking → ek hi time par multiple requests handle kar sakta hai. Ye Node.js ka sabse bada strength hai.
* **Problem:** Callback hell, difficult to manage code flow.

---

### **Q4. In problems ko kaise solve kiya jaata hai?**

👉 **Answer:**

1. **Callbacks:**

   * Pehle solution callbacks the. Ye asynchronous tasks ke complete hone ke baad chal jaate hain.
   * Problem: Nested callbacks → "Callback Hell".

2. **Promises:**

   * Callbacks ki jagah **Promise** aya. Ye `then()` aur `catch()` ke saath clean code likhne me help karta hai.
   * Example:

   ```js
   fs.promises.readFile('file.txt', 'utf8')
     .then(data => console.log(data))
     .catch(err => console.error(err));
   ```

3. **Async/Await:**

   * Promises ko aur simple aur readable banane ke liye `async/await` introduce hua.
   * Ye asynchronous code ko **synchronous jaisa** dikhata hai, aur error handling `try/catch` se ho jaati hai.

---

### **Q5. Callback, Promise aur Async/Await actually kaise kaam aate hain?**

👉 **Answer:**

* **Callback:** Function ko parameter ke roop me pass kar dete hain, jo operation complete hone par call hota hai.
* **Promise:** Ek object return hota hai jo ya to **resolve** hoga (success) ya **reject** (error). Isse asynchronous flow predictable ho jaata hai.
* **Async/Await:** Promise ke upar syntactic sugar hai jo code ko aur readable aur maintainable banata hai.

---

✅ **Summary for Interview:**

* **Sync:** Easy but blocking.
* **Async:** Non-blocking but callback hell ka risk.
* **Solution:** Promises aur Async/Await.
* Ye hi reason hai ki Node.js **highly scalable** hota hai.

---

### **1. How does Node.js handle HTTP requests and responses?**

👉 **Answer:**

* Node.js me `http` core module hota hai jo **server create** karke incoming **HTTP requests handle** karta hai aur **responses send** karta hai.
* Jab ek request aati hai, server ek **callback function** ko trigger karta hai jisme `req` (request) aur `res` (response) objects pass hote hain.

**Example:**

```js
const http = require('http');

const server = http.createServer((req, res) => {
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Hello, this is a Node.js server response!');
});

server.listen(3000, () => console.log('Server running on port 3000'));
```

---

### **2. What is Express.js and why is it important for Node.js?**

👉 **Answer:**

* **Express.js** ek **web application framework** hai jo Node.js ke upar bana hai.
* Ye HTTP handling ko **simple, fast aur structured** banata hai.
* Features:

  * Routing (GET, POST, PUT, DELETE easily handle karna)
  * Middleware support
  * REST API development easy
  * Scalability aur maintainability

📌 Express ke bina raw Node.js HTTP module use karna **tedious aur verbose** hota hai.

---

### **3. How do you create a RESTful API with Node.js?**

👉 **Answer:**

* REST API banane ke liye generally **Express.js** use hota hai.
* Example: CRUD API (Users ke liye):

```js
const express = require('express');
const app = express();
app.use(express.json()); // middleware to parse JSON

// GET route
app.get('/users', (req, res) => {
  res.json([{ id: 1, name: 'Harsh' }]);
});

// POST route
app.post('/users', (req, res) => {
  const user = req.body;
  res.status(201).json(user);
});

app.listen(3000, () => console.log('API running on port 3000'));
```

---

### **4. What is middleware in the context of Node.js?**

👉 **Answer:**

* Middleware ek **function hota hai jo request-response cycle ke beech me execute hota hai.**
* Ye request ko modify kar sakta hai, response me changes kar sakta hai ya agle middleware ko pass kar sakta hai.
* Types:

  * Application-level (custom middleware)
  * Built-in (e.g., `express.json()`)
  * Third-party (e.g., `morgan` for logging, `cors` for CORS handling)

**Example:**

```js
app.use((req, res, next) => {
  console.log('Middleware executed');
  next(); // next middleware ya route handler me jao
});
```

---

### **5. How do you ensure security in HTTP headers with Node.js?**

👉 **Answer:**

* Security ke liye **Helmet.js middleware** commonly use hota hai. Ye HTTP headers ko secure bana deta hai.
* Example:

```js
const express = require('express');
const helmet = require('helmet');
const app = express();

app.use(helmet()); // secure HTTP headers

app.get('/', (req, res) => {
  res.send('Secure app with Helmet!');
});

app.listen(3000, () => console.log('Server running securely'));
```

* Helmet kya karta hai?

  * Clickjacking se bachata hai (`X-Frame-Options`)
  * Cross-site scripting (XSS) risk kam karta hai (`X-XSS-Protection`)
  * Content Security Policy (CSP) set karta hai
  * Secure headers like `Strict-Transport-Security`

---

✅ **Summary for Interview:**

* Node.js `http` module handle karta hai request/response.
* Express.js simplify karta hai web app aur API development.
* REST API CRUD operations ke liye Express best hai.
* Middleware request-response ke beech ka function hai (auth, logging, parsing, etc.).
* HTTP security ke liye **Helmet.js** + HTTPS recommended hai.

---

### **1. How do you handle errors in Node.js?**

👉 **Answer:**

* Node.js me error handling ke main 3 tarike hote hain:

  1. **Error-first callbacks** (traditional way)
  2. **Promises + .catch()**
  3. **Async/Await + try/catch**
* Saath hi, **process.on('uncaughtException')** aur **error events** ka use bhi hota hai unexpected errors handle karne ke liye.

---

### **2. Describe some error-first callback patterns in Node.js.**

👉 **Answer:**

* Error-first callback pattern ka matlab: **pehla argument hamesha error hota hai, aur doosra result.**
* Example:

```js
fs.readFile('file.txt', 'utf8', (err, data) => {
  if (err) {
    console.error('Error:', err); // pehle error check karte hain
    return;
  }
  console.log('Data:', data); // result
});
```

📌 Is pattern ka fayda: Har async operation ke sath error handle karna easy ho jaata hai.

---

### **3. What are some common debugging techniques for Node.js applications?**

👉 **Answer:**

* **console.log() debugging** (sabse basic)
* **Debugger module** ya `node inspect app.js`
* **Chrome DevTools** ke sath attach karke debug karna
* **VS Code debugger** (breakpoints set karke)
* **Logging libraries** (e.g., `winston`, `morgan`)

---

### **4. Explain process.nextTick().**

👉 **Answer:**

* `process.nextTick()` ek function hai jo callback ko **event loop ke next phase se pehle hi execute** kar deta hai.
* Matlab: “abhi kaam complete karo, lekin baaki current code execute hone ke baad.”

**Example:**

```js
console.log("Start");

process.nextTick(() => {
  console.log("Inside nextTick");
});

console.log("End");
// Output: Start → End → Inside nextTick
```

---

### **5. What is the global object in Node.js?**

👉 **Answer:**

* Node.js me **`global` object** hota hai (browser me `window` ki tarah).
* Isme har jagah available cheezein hoti hain jaise:

  * `console`
  * `setTimeout`, `setInterval`
  * `process`
* Matlab, bina import kiye directly use kar sakte ho.

---

### **6. What is a RESTful API?**

👉 **Answer:**

* RESTful API ek **architecture style** hai jisme **HTTP methods** use karke CRUD operations hote hain.
* Example:

  * GET → Data fetch
  * POST → Data create
  * PUT → Data update
  * DELETE → Data delete
* RESTful APIs lightweight hote hain aur web + mobile dono clients ke liye best hote hain.

---

### **7. What is middleware, where it is used, why it is called middleware?**

👉 **Answer:**

* Middleware ek **function** hai jo **request aur response ke beech me chalta hai.**
* Ye request ko modify kar sakta hai, validate kar sakta hai ya extra logic add kar sakta hai.
* Example: `express.json()`, authentication check, logging, security headers.
* Isko **middleware** isliye bolte hain kyunki ye **req aur res ke beech “middle” me kaam karta hai.**

---

### **8. What is request, response, and why are they passed as input?**

👉 **Answer:**

* **Request (req):** Client ki taraf se aane wali info (URL, headers, body, params).
* **Response (res):** Server ka jawab (HTML, JSON, status code).
* Server function me `req` aur `res` pass hote hain taki aapko **client ki request mil sake aur uska response bhej sako.**

---

### **9. What is CORS and how is it related with middleware? (Analogy)**

👉 **Answer:**

* **CORS (Cross-Origin Resource Sharing):** Ek security mechanism jo decide karta hai ki ek **domain ka frontend** dusre **domain ke backend** ko request kar sakta hai ya nahi.
* Example: Agar `http://frontend.com` request bhej raha hai `http://api.com` pe → CORS decide karega allowed hai ya nahi.

**Analogy:**

* Socho aap hostel me ho. Sirf registered students hi hostel ka khana khate hain. Agar bahar ka banda aaya to guard (CORS) check karega ki allow karna hai ya nahi.

**Middleware Relation:**

* Node.js me `cors` middleware use karte hain CORS headers set karne ke liye.

```js
const cors = require('cors');
app.use(cors());
```

---

### **10. What is Clickjacking?**

👉 **Answer:**

* **Clickjacking** ek attack hai jisme hacker ek **hidden iframe** use karta hai aur user ko force karta hai ki wo unknowingly malicious action perform kare (jaise kisi button pe click).
* Example: Ek button “Play Video” dikh raha hai but actually wo “Transfer Money” ka hidden button hai.

---

### **11. What is Cross-site scripting (XSS)?**

👉 **Answer:**

* XSS ek attack hai jisme hacker malicious **JavaScript code inject** karta hai web page me.
* Example: Agar koi comment section me `<script>alert("Hacked")</script>` daal de aur wo sab users ke browser me run ho jaye.

---

### **12. What is CSRF (Cross-Site Request Forgery)?**

👉 **Answer:**

* CSRF ek attack hai jisme user ko **bina pata chale** unke authenticated session ka use karke unwanted request karwa di jaati hai.
* Example: Agar aap bank site me login ho aur hacker ek malicious link bhej de → click karte hi aapke session se “transfer money” ho jaye.

---

✅ **Summary for Interview Revision:**

* Errors → callback pattern, promises, async/await.
* Debugging → console.log, debugger, DevTools, VS Code.
* `process.nextTick()` → current phase complete hone ke turant baad callback run.
* Global object → globally available variables/functions.
* RESTful API → CRUD using HTTP methods.
* Middleware → req-res ke beech ka function.
* CORS → guard between frontend-backend requests.
* Clickjacking → hidden iframe trick.
* XSS → malicious JS injection.
* CSRF → forceful action using valid session.

---
### **Q1: What frameworks are available for testing Node.js applications?**

👉 Node.js ke liye kaafi testing frameworks available hain:

* **Mocha** → sabse popular testing framework, asynchronous testing ke liye achha.
* **Jest** → Facebook ka framework, snapshot testing aur mocking support deta hai.
* **Jasmine** → behavior-driven development (BDD) style testing ke liye use hota hai.
* **AVA** → minimal aur fast testing framework.
* **Supertest** → HTTP servers (APIs) ko test karne ke liye use hota hai.

✅ **Importance**: Ye frameworks tests likhne ko easy aur structured banate hain.

---

### **Q2: Explain the concept of mocking in Node.js.**

👉 **Mocking** ka matlab hai kisi external dependency (database, API, file system) ko **fake version se replace karna** testing ke time.

* Example: Agar code MySQL se data fetch karta hai, to test ke time real DB hit na karke ek mock function return karwa dete hain.
* **Benefit** → Faster testing, predictable results, aur external failures se isolated testing.

---

### **Q3: Why is benchmarking important in Node.js?**

👉 **Benchmarking** ka matlab hai performance measure karna.

* Node.js ka main strength hai **speed aur scalability**, to hume check karna hota hai ke:

  * Kitne requests per second handle kar raha hai?
  * Memory usage kitni hai?
  * Response time kaisa hai?
* **Importance** → Benchmarking se bottlenecks samajh aate hain aur optimization ke liye direction milti hai.

---

### **Q4: How do you test an HTTP server in Node.js?**

👉 HTTP server ko test karne ke liye hum:

* **Supertest** + **Mocha/Jest** ka combination use karte hain.
* Steps:

  1. `supertest` se ek request bhejte hain server ko.
  2. Response check karte hain (status code, headers, body).
  3. Assertions likhte hain ke result expected hai ya nahi.

Example:

```js
const request = require("supertest");
const app = require("./app"); // Express app

describe("GET /users", () => {
  it("should return all users", async () => {
    const res = await request(app).get("/users");
    expect(res.statusCode).toBe(200);
    expect(res.body.length).toBeGreaterThan(0);
  });
});
```

---

### **Q5: How do you connect a MySQL database with Node.js?**

👉 MySQL connect karne ke steps:

1. `mysql` ya `mysql2` package install karo.
2. Connection establish karo credentials ke saath.
3. Queries run karo (select, insert, update).

Example:

```js
const mysql = require('mysql2');

const connection = mysql.createConnection({
  host: 'localhost',
  user: 'root',
  password: 'password',
  database: 'testdb'
});

connection.connect(err => {
  if (err) throw err;
  console.log("Connected to MySQL!");
});
```

---

### **Q6: Explain how NoSQL databases like MongoDB can be used with Node.js.**

👉 MongoDB ek **document-based NoSQL DB** hai.

* Node.js ke saath use karne ke liye hum **Mongoose** library ya official `mongodb` driver use karte hain.
* Example workflow:

  1. Mongoose install karo.
  2. MongoDB ke saath connect karo.
  3. Schema define karo.
  4. CRUD operations perform karo.

Example:

```js
const mongoose = require('mongoose');

mongoose.connect('mongodb://localhost:27017/mydb');

const UserSchema = new mongoose.Schema({ name: String, age: Number });
const User = mongoose.model('User', UserSchema);

User.create({ name: "Harsh", age: 22 });
```
---
## **Q1: What's the role of ORM in Node.js? (with Analogy)**

👉 **ORM (Object Relational Mapping)** ek **bridge** hai jo tumhare Node.js code (objects) ko database ke queries (SQL/NoSQL commands) mein convert karta hai.

### **Analogy (Restaurant Example 🍽️):**

* Tum ek restaurant ke customer ho (Node.js developer).
* Tum waiter ko simple order dete ho: *“Mujhe ek Veg Burger chahiye.”* (ye tumhara **object code** hai).
* Waiter tumhara order translate karta hai aur kitchen staff ko deta hai in detail (*“2 buns, 1 veg patty, lettuce, mayo”*). (ye **SQL Query** hai).
* Kitchen khana banata hai (Database query run hota hai).
* Waiter tumhe ready burger le aata hai (Database result tumhe object ke form mein milta hai).

✅ Without ORM → Tumhe directly kitchen (database) se baat karni padti aur detail commands deni padti (SQL likhna).
✅ With ORM → Tum waiter se baat karte ho (ORM), aur tumhe object ke form mein results mil jaate hain.

**Popular ORMs in Node.js:**

* **Sequelize** (SQL ke liye)
* **Mongoose** (MongoDB ke liye)
* **TypeORM** (multi-database support)

---

## **Q2: How can you monitor the performance of a Node.js app?**

👉 Monitoring ka matlab hai **check karna ki app slow to nahi ho rahi, memory leak to nahi hai, CPU usage kaisa hai**.

**Ways:**

1. **Built-in tools**: `process.memoryUsage()`, `console.time()`
2. **Node Clinic** (diagnostics tool)
3. **PM2** (process manager with monitoring dashboard)
4. **New Relic / Datadog / AppDynamics** (3rd party tools)

✅ Monitoring se tumhe bottlenecks aur optimization points samajh aate hain.

---

## **Q3: What is clustering in Node.js and how does it work?**

👉 Node.js by default **single-threaded** hota hai, ek CPU core hi use karta hai. Agar system mein 8 cores hain to baaki idle rahenge.

**Clustering** → Ek hi Node.js app ke multiple instances (workers) ban jaate hain jo har core pe run hote hain.

* Ye workers ek **master process** ke under hote hain.
* Master incoming requests ko workers ke beech distribute karta hai.

✅ Advantage → Multi-core system ka full use hota hai, performance boost milta hai.

---

## **Q4: How can you prevent memory leaks in a Node.js application?**

👉 **Memory leaks** ka matlab hai app continuously memory consume karta rahe aur release na kare.

**Causes:**

* Global variables ka improper use
* Event listeners ka remove na karna
* Large arrays/objects ko clear na karna

**Prevention:**

1. Always remove unused event listeners (`removeListener`)
2. Global variables avoid karo
3. Use tools → Chrome DevTools, `clinic heap-profiler`
4. Optimize caching

✅ Agar memory leak ho jaaye to app slow aur crash ho jaata hai.

---

## **Q5: Explain the use of the `--inspect` flag in Node.js.**

👉 `--inspect` ek flag hai jo tumhare Node.js app ko **debug mode** mein run karta hai.

* Tum Chrome DevTools ya VS Code debugger attach karke step-by-step code debug kar sakte ho.

Example:

```bash
node --inspect app.js
```

✅ Isse tum real-time mein variables, stack traces, aur performance profile dekh sakte ho.

---

## **Q6: How does Node.js handle concurrency?**

👉 Node.js **single-threaded** hai lekin concurrency ko handle karta hai **event loop** aur **non-blocking I/O** ke through.

* Ek request aati hai → Event loop usko queue mein dal deta hai.
* Jo I/O (like DB query, file read) hai wo background thread pool (libuv) mein chala jata hai.
* Jab task complete hota hai → callback queue mein response aa jata hai.
* Event loop response ko execute kar deta hai.

✅ Is wajah se Node.js ek saath thousands of requests handle kar sakta hai bina block hue.

---

## **Q7: What is the difference between `process` and `child_process` modules?**

* **process** → Current running Node.js process ko represent karta hai. Tum isse environment variables, memory usage, PID etc. access kar sakte ho.
  Example:

  ```js
  console.log(process.pid); // current process id
  ```

* **child\_process** → Ek naya process (child) spawn karne ke liye use hota hai jo current process ke parallel run hota hai.
  Example:

  ```js
  const { exec } = require('child_process');
  exec('ls', (err, stdout) => console.log(stdout));
  ```

✅ Difference → `process` = tumhara app ka environment, `child_process` = new external process run karna.

---

## **Q8: How do worker threads work in Node.js?**

👉 Worker Threads ek module hai jo **multi-threading** support deta hai Node.js mein (specially CPU-intensive tasks ke liye).

* Normally Node.js ek thread pe hi kaam karta hai.
* Agar tumhe heavy computation karna hai (like image processing, ML), to tum ek **worker thread** bana sakte ho.
* Worker thread main thread ke parallel run karta hai.

Example:

```js
const { Worker } = require('worker_threads');

new Worker(`
  const { parentPort } = require('worker_threads');
  let sum = 0;
  for (let i=0; i<1e9; i++) sum += i;
  parentPort.postMessage(sum);
`, { eval: true });
```

✅ **Difference from clustering:**

* **Clustering** → Multi-core ke liye multiple app instances.
* **Worker Threads** → Ek hi process ke andar multiple threads for heavy computation.

---

# 🏢 Analogy: Ek Software Company (Office Example)

Socho tumhari ek software company hai jisme ek **CEO** (Node.js main thread) hai. Ab projects zyada ho gaye to CEO eklauta sab kaam nahi kar sakta. Uske paas teen options hain:

---

## **1. Clustering (Multiple Offices with Same Work)**

* CEO decide karta hai ki ek hi project (app) ke liye **multiple branches (offices)** khol deta hai har ek city mein.
* Har branch (worker process) same kaam karti hai aur apne-apne staff se requests handle karti hai.
* Ek **Head Office (Master process)** decide karta hai ki kounsi request kis branch ko bhejni hai.

👉 **Node.js mein**:

* Ek hi app ke multiple **instances (workers)** ban jaate hain.
* Har worker apne **own memory space** ke saath independent hota hai.
* Zyada CPU cores utilize hote hain.

✅ **Use case** → Jab tumhe ek server ko scale karna hai aur zyada traffic handle karna hai (like e-commerce app).

---

## **2. Worker Threads (Team Members within One Office)**

* Ab maan lo ek hi office (process) ke andar ek project bahut heavy hai (like video rendering).
* CEO alag-alag **specialized employees (worker threads)** hire karta hai jo ek hi office mein baith ke parallel kaam karte hain.
* Sab same **resources (memory)** share karte hain, lekin apna-apna task karte hain.

👉 **Node.js mein**:

* Worker threads ek hi process ke andar hote hain.
* Same memory share karte hain → fast communication possible hai.
* Useful for **CPU-heavy tasks** jo event loop ko block karte.

✅ **Use case** → Image processing, Machine Learning computation, data encryption, mathematical calculations.

---

## **3. Child Process (Temporary Freelancers/Contractors)**

* CEO sochta hai ki kuch tasks ke liye mujhe office ke bahar se **freelancers (child processes)** hire karne padenge.
* Ye freelancers ekdum alag hote hain, apna laptop aur setup use karte hain (independent memory).
* CEO unko ek task deta hai aur jab wo complete karte hain to result bhej dete hain.

👉 **Node.js mein**:

* Child process alag se ek external process run karta hai.
* Worker threads ki tarah memory share nahi hoti.
* Useful jab tumhe **external command** chalani ho (like running Python script, shell commands).

✅ **Use case** → File compression, shell commands (`ls`, `grep`), alag programming language ka code run karna.

---

✅ **Easy way to remember**:

* **Clustering** → Zyada **branches** banao load handle karne ke liye.
* **Worker Threads** → Ek hi branch mein zyada **team members** hire karo heavy kaam ke liye.
* **Child Process** → Bahar ke **freelancers** hire karo temporary kaam ke liye.

---
1. **Clustering** → multiple worker processes banane ka demo
2. **Worker Threads** → ek heavy CPU task parallel chalane ka demo
3. **Child Process** → ek external command run karne ka demo

---

## **1. Clustering Example**

```js
// cluster-demo.js
const cluster = require("cluster");
const http = require("http");
const os = require("os");

if (cluster.isMaster) {
  const numCPUs = os.cpus().length;
  console.log(`Master ${process.pid} is running`);

  // Har CPU ke liye ek worker banao
  for (let i = 0; i < numCPUs; i++) {
    cluster.fork();
  }

  cluster.on("exit", (worker) => {
    console.log(`Worker ${worker.process.pid} died, starting a new one...`);
    cluster.fork(); // crash hone par new worker
  });
} else {
  // Worker apna HTTP server chalata hai
  http
    .createServer((req, res) => {
      res.writeHead(200);
      res.end(`Hello from Worker ${process.pid}\n`);
    })
    .listen(3000);

  console.log(`Worker ${process.pid} started`);
}
```

👉 Run:

```bash
node cluster-demo.js
```

* Har CPU core ek **worker process** run karega.
* Agar 8 cores hain → 8 workers banenge.
* Har worker alag request handle karega.

---

## **2. Worker Threads Example**

```js
// worker-thread-demo.js
const { Worker, isMainThread, parentPort } = require("worker_threads");

if (isMainThread) {
  console.log("Main thread started");

  const worker = new Worker(__filename); // ek new worker thread
  worker.on("message", (msg) => {
    console.log("Message from worker:", msg);
  });

} else {
  // Heavy task worker thread mein
  let sum = 0;
  for (let i = 0; i < 1e9; i++) sum += i;

  parentPort.postMessage(`Sum = ${sum}`); // result main thread ko bheja
}
```

👉 Run:

```bash
node worker-thread-demo.js
```

* Heavy calculation (`1e9` loop) background mein worker thread karega.
* Main thread block nahi hoga → yehi advantage hai worker threads ka.

---

## **3. Child Process Example**

```js
// child-process-demo.js
const { exec } = require("child_process");

exec("ls", (err, stdout, stderr) => {
  if (err) {
    console.error("Error:", err);
    return;
  }
  console.log("Output:\n", stdout);
});
```

👉 Run:

```bash
node child-process-demo.js
```

* Ye code OS ka `ls` command run karega (Linux/Mac pe).
* Windows pe `dir` likhna padega.
* Output terminal mein print hoga.

---
