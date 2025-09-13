

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
