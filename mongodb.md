

### ❓ What are some of the advantages of MongoDB?

✅ **Advantages:**

* Schema-less → flexible structure, fixed columns ki zaroorat nahi hoti.
* High performance → JSON/BSON format use karta hai jo fast parse hota hai.
* Scalability → sharding ke through horizontally scale hota hai.
* Rich queries + indexing → queries optimized hoti hain.

👉 **Reason:** MongoDB ka document-oriented design aur JSON-like storage fast data access aur schema flexibility deta hai, isliye big data aur rapidly changing applications ke liye best hai.

---

### ❓ When to use MongoDB?

✅ **Use cases:**

* Big Data apps
* Real-time analytics
* CMS, IoT, Mobile apps

👉 **Reason:** Jab data ka structure frequently change hota hai ya high volume / velocity ke data ko store karna hai, tab relational database rigid ho jata hai. MongoDB flexible schema aur distributed nature ke wajah se suitable hota hai.

---

### ❓ What are the data types in MongoDB?

✅ **Data Types:** String, Number (Int, Double, Decimal128), Boolean, Array, Document, Null, Date, ObjectId, Binary Data, Regex.

👉 **Reason:** Yeh types BSON format ka part hain, jo JSON ka binary extended form hai. Is wajah se complex aur hierarchical data ko easily represent kiya ja sakta hai.

---

### ❓ How to perform queries in MongoDB?

✅ Example Queries:

* `db.users.find()` → sab documents fetch karega.
* `db.users.find({age: 25})` → filter lagata hai.
* `db.users.find({}, {name:1, age:1})` → sirf selected fields dikhata hai.

👉 **Reason:** MongoDB ka query language JSON-like syntax use karta hai jo developers ke liye intuitive hota hai aur efficient indexes ke saath fast searching allow karta hai.

---

### ❓ How do you delete a document in MongoDB?

✅ Command:

* `db.users.deleteOne({name: "Rahul"})`
* `db.users.deleteMany({age: 25})`

👉 **Reason:** Delete operations query filter ke basis par documents ko remove karte hain. MongoDB internally indexes ka use karke matching documents ko locate karta hai.

---

### ❓ How do you update a document in MongoDB?

✅ Command:

* `db.users.updateOne({name: "Rahul"}, {$set: {age: 26}})`
* `db.users.updateMany({city: "Delhi"}, {$set: {status: "Active"}})`

👉 **Reason:** Update commands existing document ko modify karte hain bina pura record dobara likhe. `$set` operator sirf specific field ko change karta hai, jisse performance better hoti hai.

---

### ❓ How to add data in MongoDB?

✅ Command:

* `db.users.insertOne({name: "Rahul", age: 25})`
* `db.users.insertMany([{name: "Amit"}, {name: "Neha"}])`

👉 **Reason:** Insert operations BSON document ko collection mein store karte hain. Document-based nature ki wajah se har record independent hota hai aur schema constraints nahi hote.

---

### ❓ What are some features of MongoDB?

✅ Features:

* Document-oriented storage
* Replica sets (high availability)
* Auto-sharding (scalability)
* Aggregation framework

👉 **Reason:** MongoDB distributed system design ke saath aata hai jisme replication fault tolerance deta hai aur sharding scale-out enable karta hai.

---

### ❓ How does scale-out occur in MongoDB?

✅ **Scale-out:**

* Sharding use karta hai
* Data ko multiple servers (shards) pe distribute karta hai
* Query router (mongos) request ko sahi shard pe bhejta hai

👉 **Reason:** RDBMS mein scaling vertical hoti hai (ek hi machine strong banao), par MongoDB horizontally multiple servers pe workload distribute karke performance aur storage increase karta hai.

---

### ❓ What is the Mongo Shell?

✅ **Mongo Shell:**

* JavaScript-based interactive shell hai
* Query, CRUD, aur admin commands run karne ke liye use hota hai

👉 **Reason:** Developers ko directly database ke saath interact karne ka interface deta hai aur testing/debugging fast banata hai.

---

### ❓ What are databases in MongoDB?

✅ **Database:**

* Top-level container jisme multiple collections store hoti hain.
* Example: `use myDatabase`

👉 **Reason:** Database namespace define karta hai aur collections ko logically group karta hai taaki alag-alag applications ke data separate rahen.

---

### ❓ What is a collection in MongoDB?

✅ **Collection:**

* Group of documents
* Table ke barabar hota hai (RDBMS ke context mein)
* Example: `db.users`

👉 **Reason:** Collections documents ko logically group karte hain jisse related data ek saath manage ho sake, bina fixed schema ke.

---

### ❓ What is a document in MongoDB?

✅ **Document:**

* JSON/BSON format mein ek single record
* Example: `{name: "Rahul", age: 25, city: "Delhi"}`

👉 **Reason:** Document MongoDB ka basic unit hai. BSON format nested aur complex data structures ko efficiently store aur retrieve karne ki capability deta hai.

---
Perfect 👍
Main aapko wahi **Q\&A format (Hinglish + examples + reason)** mein answers deta hoon, taaki crisp bhi ho aur concept + example + reasoning bhi clear ho jaye.

---

### ❓ How is querying done in MongoDB?

✅ **Answer:**

* Queries JSON-like syntax mein hoti hain.
* Example:

  * `db.users.find({age: 25})` → sab users fetch karega jinki age 25 hai.
  * `db.users.find({city: "Delhi"}, {name:1, age:1})` → Delhi ke users ka sirf name aur age show karega.

👉 **Reason:** Query language JSON-based hai isliye easy to understand hai. Internally MongoDB indexing ka use karta hai taaki query fast execute ho sake.

---

### ❓ Explain the \$set modifier in MongoDB.

✅ **Answer:**

* `$set` kisi document ke specific field ko update karne ke liye use hota hai.
* Example:

  * `db.users.updateOne({name: "Rahul"}, {$set: {age: 26}})`
  * Yahaan sirf Rahul ki **age field update hogi**, baaki data same rahega.

👉 **Reason:** `$set` targeted update karta hai, pura document overwrite nahi karta. Isse performance improve hoti hai aur unnecessary writes avoid hote hain.

---

### ❓ Explain the process of sharding in MongoDB.

✅ **Answer:**

* **Sharding = Horizontal Partitioning of Data.**
* Steps:

  1. Data ko **shards** mein divide kiya jata hai (multiple servers).
  2. **Config servers** metadata store karte hain (kaha kya data hai).
  3. **Mongos (query router)** request ko sahi shard pe forward karta hai.
* Example: Agar 10 million users hain, MongoDB unhe `shard1` (Delhi), `shard2` (Mumbai) aur `shard3` (Bangalore) mein distribute kar dega.

👉 **Reason:** Sharding se workload multiple machines pe distribute hota hai → fast response time aur huge data handle karne ki capacity milti hai.

---

### ❓ What are geospatial indexes in MongoDB?

✅ **Answer:**

* Geospatial indexes location-based queries ke liye use hote hain.
* Types:

  * **2d index** (flat coordinates ke liye)
  * **2dsphere index** (Earth-like spherical surface ke liye)
* Example:

  * `db.places.createIndex({location: "2dsphere"})`
  * `db.places.find({location: {$near: {$geometry: {type: "Point", coordinates: [77.5946, 12.9716]}, $maxDistance: 1000}}})`
  * Yahaan Bangalore ke 1 km ke andar ke places return honge.

👉 **Reason:** Real-world applications jaise Ola, Zomato, Google Maps location search ke liye geospatial indexes use karte hain, jo fast and accurate results dete hain.

---

### ❓ Explain the term "indexing" in MongoDB.

✅ **Answer:**

* Index ek data structure hai jo searching ko fast banata hai.
* Example:

  * Agar `db.users.find({age: 25})` query baar-baar chalani hai, toh:
  * `db.users.createIndex({age: 1})`
  * Ab query bina pura collection scan kiye direct index ke through result la degi.

👉 **Reason:** Index ek shortcut banata hai, jaise dictionary ke index se word jaldi milta hai. MongoDB indexes ke bina query ko poore documents scan karne padte jo slow hoga.

---

## ❓ What are Geospatial Indexes in MongoDB?

✅ **Definition:**
Geospatial indexes MongoDB mein **location-based data** (latitude, longitude, coordinates) ko efficiently query karne ke liye use hote hain. Yeh indexes allow karte hain queries jaise:

* *“Is point ke paas kaunse places hain?”*
* *“Yeh user kis polygon (city boundary) ke andar hai?”*

---

### 🔹 Types of Geospatial Indexes

1. **2d Index** – Flat plane ke liye (x, y coordinates).
2. **2dsphere Index** – Earth ke spherical geometry ke liye (latitude, longitude in GeoJSON).

---

### 🔹 Example

```javascript
// Step 1: Index create karo
db.places.createIndex({location: "2dsphere"})

// Step 2: Query places near Bangalore within 1 km
db.places.find({
  location: {
    $near: {
      $geometry: { type: "Point", coordinates: [77.5946, 12.9716] },
      $maxDistance: 1000
    }
  }
})
```

👉 **Explanation:**

* Agar aap Ola/Uber app kholo aur “auto” book karo → system driver ke latitude/longitude ko index ke through check karega.
* MongoDB quickly nearest drivers return karega, bina poore city ke data ko scan kiye.

---

### 🔹 How companies use it?

* **Uber/Ola** → nearest driver search
* **Zomato/Swiggy** → nearby restaurants
* **Google Maps** → "restaurants near me" feature
* **E-commerce** → delivery available hai ya nahi check karna based on pincode/area

---

### 🔹 Output se kya milta hai?

* Location-based fast results (millisecond level response).
* Customer ke liye accurate suggestions (nearest restaurant, shop, driver).
* Company ke liye → efficiency (kam server load, better user experience).

👉 **Reason:** Agar index na ho, toh MongoDB ko sabhi documents scan karne padte (slow process). Geospatial index query ko sirf relevant area tak limit kar deta hai.

---

## ❓ Explain the term "Indexing" in MongoDB

✅ **Definition:**
Index ek **data structure (generally B-tree / B+ tree)** hota hai jo queries ko fast banata hai. Index ek “short-cut” jaisa hota hai.

---

### 🔹 Without Index Example

* Aapke paas **10 lakh users** hain.
* Query:

  ```javascript
  db.users.find({age: 25})
  ```
* MongoDB ko **har ek document scan** karna padega to check `age = 25`.
* Ye **COLLECTION SCAN** kehlata hai → slow.

---

### 🔹 With Index Example

* Pehle index banate hain:

  ```javascript
  db.users.createIndex({age: 1})
  ```
* Ab query `db.users.find({age: 25})`
* MongoDB directly **index tree** me `25` value search karega → related documents ke pointers mil jayenge → result instant aayega.

👉 Index ek “table of contents” ki tarah hai jo direct jump karne deta hai instead of poora book read karne ke.

---

### 🔹 How it works internally?

* Index ek **sorted B-tree** data structure hota hai.
* Nodes me field values + pointer to document hote hain.
* Jab query chalta hai, MongoDB B-tree traversal karta hai (logarithmic time complexity O(log n)) instead of full scan (O(n)).
* Example: Agar data sorted hai (B-tree), to age=25 directly leaf node se mil jata hai.

---

### 🔹 Real-world usage

* **E-commerce**: Searching products by price, category, rating → fast results.
* **Social Media**: Searching users by username/email.
* **Banking apps**: Transactions query by date range.

---

### 🔹 Benefits (Output ka maada):

* Fast query execution
* Low CPU usage
* Efficient memory utilization
* Better user experience (quick results)

---

## 1️⃣ What do you mean by transactions in MongoDB?

✅ **Answer:**

* Transactions allow multiple operations (insert/update/delete) to be executed **as a single unit**.
* If one operation fails → poora transaction rollback ho jaata hai (Atomicity).

👉 **Reason:** Transactions ensure **ACID properties** (Atomicity, Consistency, Isolation, Durability) → reliable data updates in multi-document operations.

👉 **Example:**

* Banking app: Agar ek account se ₹500 debit aur dusre account me credit karna hai, toh dono ek transaction me honge. Agar credit fail ho jaye → debit bhi cancel ho jaayega.

---

## 2️⃣ What are MongoDB Charts?

✅ **Answer:**

* MongoDB Charts ek **data visualization tool** hai jo directly MongoDB data se charts, graphs, dashboards banata hai.
* No need for external ETL (Extract Transform Load).

👉 **Reason:** Companies real-time MongoDB data ko directly visualize kar sakti hain → better decision-making.

👉 **Example:**

* E-commerce site apne orders collection se MongoDB Charts use karke real-time “Daily Sales” aur “Top 5 Products” ka dashboard bana sakti hai.

---

## 3️⃣ What is the Aggregation Framework in MongoDB?

✅ **Answer:**

* Aggregation framework data ko transform aur compute karne ke liye use hota hai (jaise SQL mein GROUP BY, SUM, AVG).
* It works in stages.

👉 **Reason:** Large datasets par calculations efficiently karne ke liye built-in operators provide karta hai (sum, avg, count, group, sort).

👉 **Example:**

```javascript
db.orders.aggregate([
  {$group: {_id: "$customerId", totalSpent: {$sum: "$amount"}}}
])
```

* Yahaan har customer ne kitna paisa kharch kiya hai uska total nikal ke dega.

---

## 4️⃣ Explain the concept of pipeline in the MongoDB aggregation framework.

✅ **Answer:**

* Aggregation works as a **pipeline** → data ek stage se guzarta hai, transform hota hai, aur agle stage me pass hota hai.
* Multiple stages chain ki tarah lagte hain.

👉 **Reason:** Pipeline approach modular aur efficient hoti hai → complex queries ko tod kar chhote manageable steps me solve karti hai.

👉 **Example:**

```javascript
db.orders.aggregate([
  {$match: {status: "Completed"}},        // Stage 1: filter orders
  {$group: {_id: "$customerId", total: {$sum: "$amount"}}},  // Stage 2: group + sum
  {$sort: {total: -1}}                    // Stage 3: sort descending
])
```

* Pehle sirf completed orders filter honge, fir customer ke hisaab se total calculate hoga, aur last me unhe sorting kar diya jaayega.

---

## 5️⃣ What is a Replica Set in MongoDB?

✅ **Answer:**

* Replica Set = ek hi data ka **multiple servers** pe copy (replication).
* Ek primary aur multiple secondary nodes hote hain.

👉 **Reason:** Replica set high availability aur fault tolerance provide karta hai. Agar primary fail ho jaye, secondary automatically primary ban jata hai.

👉 **Example:**

* Agar ek MongoDB server crash ho gaya toh doosra replica (secondary) uska role le lega → application bina rukhe chalta rahega.

---

## 6️⃣ Explain the Replication Architecture in MongoDB.

✅ **Answer:**

* **Primary Node:** Writes and reads (by default) handle karta hai.
* **Secondary Nodes:** Primary se data copy (replicate) karte hain.
* **Arbiter Node (optional):** Vote karta hai ki naya primary kaun hoga (khud data store nahi karta).

👉 **Reason:** Replication architecture ensures **automatic failover** aur **read scalability** (reads secondary se bhi kar sakte hain).

👉 **Example:**

* 1 Primary + 2 Secondary setup: Agar primary down ho jaaye, secondary nodes election karke naya primary bana dete hain → downtime nahi hota.

---

## 7️⃣ What are some utilities for backup and restore in MongoDB?

✅ **Answer:**

* **mongodump:** Collection ya database ka snapshot (BSON format) banata hai.
* **mongorestore:** `mongodump` ka backup restore karta hai.
* **mongoexport:** Data ko JSON/CSV format me export karta hai.
* **mongoimport:** JSON/CSV file se data import karta hai.
* **Ops Manager / Atlas Backup:** Cloud-based backup aur restore solution.

👉 **Reason:** Backup/restore utilities accidental data loss, corruption ya migration ke time essential hote hain.

👉 **Example:**

```bash
# Backup
mongodump --db ecommerce --out /backup/

# Restore
mongorestore --db ecommerce /backup/ecommerce/
```

* Yahaan `ecommerce` DB ka poora backup ban jayega aur restore bhi easily ho jayega.

---

## 1️⃣ What is MongoDB and what are its main features?

* MongoDB ek **NoSQL, document-oriented database** hai.
* **Features:**

  * Schema-less (flexible structure)
  * JSON/BSON document storage
  * High availability via replica sets
  * Horizontal scalability via sharding
  * Rich query language + aggregation framework

---

## 2️⃣ How does MongoDB differ from relational databases?

* MongoDB → NoSQL, documents store karta hai (JSON-like).
* RDBMS → Tables/rows store karta hai (fixed schema).
* MongoDB → Horizontal scaling (sharding).
* RDBMS → Usually vertical scaling.
* MongoDB → Flexible schema (har document alag ho sakta hai).
* RDBMS → Rigid schema (fixed columns).

---

## 3️⃣ Can you describe the structure of data in MongoDB?

* Data → BSON (Binary JSON) format me store hota hai.
* Hierarchy:

  * **Database → Collection → Document → Fields.**

---

## 4️⃣ What is a Document in MongoDB?

* MongoDB ka **basic unit of data**.
* JSON-like structure: key-value pairs.
* Example:

  ```json
  { "name": "Rahul", "age": 25, "city": "Delhi" }
  ```

---

## 5️⃣ How is data stored in collections in MongoDB?

* Documents ko logically **collections** me group kiya jata hai.
* Equivalent to tables in RDBMS, but **schema-free**.

---

## 6️⃣ Describe what a MongoDB database is.

* Database = **top-level container** jisme multiple collections store hoti hain.
* Example: `ecommerce` DB → `users`, `orders`, `products` collections.

---

## 7️⃣ What is the default port on which MongoDB listens?

* Default port: **27017**.

---

## 8️⃣ How does MongoDB provide high availability and disaster recovery?

* Via **Replica Sets**: ek primary + multiple secondary nodes.
* Automatic **failover** → agar primary fail ho jaye, secondary new primary ban jata hai.

---

## 9️⃣ What are indexes in MongoDB, and why are they used?

* Index = data structure (B-tree) jo queries ko fast banata hai.
* Without index → full collection scan.
* With index → direct lookup (O(log n)).

---

## 🔟 What is the role of the id field in MongoDB documents?

* Every document ka unique identifier = **\_id field**.
* Default automatically generated ObjectId.
* Acts like **Primary Key** (ensures uniqueness).
---

## 1️⃣ How do you create a new MongoDB collection?

* Collection **automatically ban jata hai** jab pehli baar document insert karte ho.
* Manually create karna ho:

  ```js
  db.createCollection("students")
  ```
* **Reason:** MongoDB schema-less hai, isliye pehle insert pe bhi collection create ho jata hai.

---

## 2️⃣ What is the syntax to insert a document into a MongoDB collection?

* Example:

  ```js
  db.students.insertOne({ name: "Amit", age: 22 })
  ```
* **Reason:** `insertOne` ek document dalta hai aur agar collection exist nahi karti toh automatically create kar deta hai.

---

## 3️⃣ Describe how to read data from a MongoDB collection.

* Example:

  ```js
  db.students.find({ age: 22 })
  ```
* **Reason:** `find()` filter condition ke saath documents ko fetch karta hai. Agar condition na do toh saare records return karega.

---

## 4️⃣ Explain how to update documents in MongoDB.

* Example:

  ```js
  db.students.updateOne(
    { name: "Amit" },
    { $set: { age: 23 } }
  )
  ```
* **Reason:** `$set` modifier sirf specified fields ko update karta hai bina pura document overwrite kiye.

---

## 5️⃣ What are the MongoDB commands for deleting documents?

* Example:

  ```js
  db.students.deleteOne({ name: "Amit" })     // ek document
  db.students.deleteMany({ age: 22 })         // multiple documents
  ```
* **Reason:** `deleteOne` pehle matching document hataata hai, `deleteMany` sab matching documents.

---

## 6️⃣ Can you join two collections in MongoDB? If so, how?

* Yes, via **\$lookup** in aggregation.
* Example:

  ```js
  db.orders.aggregate([
    {
      $lookup: {
        from: "customers",
        localField: "customer_id",
        foreignField: "_id",
        as: "customerDetails"
      }
    }
  ])
  ```
* **Reason:** `$lookup` join jaisa kaam karta hai RDBMS ke `JOIN` ki tarah.

---

## 7️⃣ How do you limit the number of documents returned by a MongoDB query?

* Example:

  ```js
  db.students.find().limit(5)
  ```
* **Reason:** `limit()` cursor ke result me se sirf specified count ke documents return karta hai (useful for pagination, dashboards).

---

## 8️⃣ What is the difference between find() and findOne() in MongoDB?

* `find()` → multiple documents return karta hai (cursor).
* `findOne()` → sirf **pehla matching document** return karta hai.
* Example:

  ```js
  db.students.find()        // all docs
  db.students.findOne()     // only first doc
  ```

---

## 9️⃣ How can you achieve pagination in MongoDB?

* Example:

  ```js
  db.students.find().skip(10).limit(5)
  ```
* **Reason:** `skip()` kuch documents ko chhod deta hai aur `limit()` ek fixed number return karta hai → combined use = pagination.

---

## 🔟 What are the differences between MongoDB's insertOne and insertMany methods?

* `insertOne()` → ek single document insert karta hai.
* `insertMany()` → ek array of documents insert karta hai.
* Example:

  ```js
  db.students.insertOne({ name: "Amit", age: 22 })

  db.students.insertMany([
    { name: "Rahul", age: 25 },
    { name: "Sneha", age: 21 }
  ])
  ```
* **Reason:** `insertMany` batch insert ke liye zyada efficient hota hai, kyunki ek hi request me multiple documents save kar deta hai.

---



## 1️⃣ Describe a compound index in MongoDB.

* **Definition:** Compound index ek se zyada fields par banaya jata hai.
* **Example:**

  ```js
  db.users.createIndex({ age: 1, name: -1 })
  ```
* Is index se queries jaise `{ age: 25, name: "Amit" }` ya sirf `{ age: 25 }` fast ho jaate hain.
* **Reason:** MongoDB left-to-right order follow karta hai, toh pehle `age` field aur phir `name` field ke basis par search optimize hoti hai.

---

## 2️⃣ What is the aggregation pipeline in MongoDB?

* Aggregation pipeline ek **framework hai data transform aur analyze karne ke liye**.
* Data ek ke baad ek **stages** se pass hota hai jaise `$match`, `$group`, `$sort`.
* **Example:**

  ```js
  db.sales.aggregate([
    { $match: { status: "A" } },
    { $group: { _id: "$item", total: { $sum: "$amount" } } }
  ])
  ```
* **Reason:** Ye SQL ke `WHERE + GROUP BY + ORDER BY` ka equivalent hai NoSQL world me.

---

## 3️⃣ How can you create an index in MongoDB and when should you do it?

* **Create:**

  ```js
  db.products.createIndex({ price: 1 })
  ```
* **When:** Jab query kisi field pe repeatedly chal rahi ho (e.g., `find({price: 500})`).
* **Reason:** Index queries ko fast banata hai by avoiding full collection scan.

---

## 4️⃣ Explain how MongoDB's \$match, \$group and \$sort operators work in an aggregation pipeline.

* **\$match** → filters documents (SQL: `WHERE`).

  ```js
  { $match: { age: { $gt: 18 } } }
  ```
* **\$group** → groups data aur aggregates banata hai (SQL: `GROUP BY`).

  ```js
  { $group: { _id: "$city", total: { $sum: 1 } } }
  ```
* **\$sort** → results ko sort karta hai (SQL: `ORDER BY`).

  ```js
  { $sort: { total: -1 } }
  ```
* **Reason:** Ye 3 sabse common stages hain jo saath me use hote hain analytics aur reporting ke liye.

---

## 5️⃣ What is the purpose of the explain() method?

* **Definition:** Query execution plan dikhata hai → index use ho raha hai ya collection scan.
* **Example:**

  ```js
  db.users.find({ age: 25 }).explain("executionStats")
  ```
* **Reason:** Performance debugging ke liye use hota hai.

---

## 6️⃣ How does MongoDB perform automatic failover?

* **Replica set** me agar primary crash ho jaye → election process hota hai.
* Ek secondary node automatically new primary ban jata hai.
* **Reason:** Ye high availability ensure karta hai bina manual intervention ke.

---

## 7️⃣ How does MongoDB handle large data volumes?

* **Sharding** ke through data horizontally multiple servers me split hota hai.
* Query `mongos` route karta hai right shard tak.
* **Reason:** Scale-out karke billions of documents handle karne ka capability.

---

## 8️⃣ What strategies can you use to diagnose and address performance issues in MongoDB?

* Use `explain()` → query optimization check.
* Indexing → ensure right indexes exist.
* Monitor memory usage (indexes should fit in RAM).
* Use sharding for big datasets.
* **Reason:** Ye steps query slowness aur bottlenecks ko remove karte hain.

---

## 9️⃣ How do you ensure that indexes fit into RAM?

* Monitor via `db.collection.stats()` aur `db.serverStatus()`.
* Keep **working set (indexes + frequently accessed data)** < available RAM.
* **Reason:** Agar index RAM me hai toh lookups O(log n), otherwise disk read slow.

---

## 🔟 Can you explain MongoDB's write concern?

* Write concern = MongoDB ko kitna strong acknowledgement chahiye write ke liye.
* Example:

  ```js
  db.users.insertOne({ name: "Amit" }, { writeConcern: { w: "majority" } })
  ```
* **Reason:** Higher write concern = more safety, but slower writes.

---

## 1️⃣1️⃣ What is a covered query in MongoDB?

* Jab query + projection dono ek hi index se satisfy ho jaaye → no need to access document.
* Example: Agar index `{ name: 1, age: 1 }` hai aur query:

  ```js
  db.users.find({ name: "Amit" }, { age: 1, _id: 0 })
  ```
* **Reason:** Query super-fast hoti hai kyunki sirf index hi access hota hai, document read nahi.

---

## 1️⃣2️⃣ What are the security features available in MongoDB?

* Authentication (username/password, LDAP, Kerberos).
* Authorization (role-based access control).
* TLS/SSL encryption in transit.
* Data at rest encryption.
* **Reason:** Secure DB access aur compliance ke liye.

---

## 1️⃣3️⃣ How do you enable authentication in MongoDB?

* Start mongod with:

  ```bash
  mongod --auth --port 27017
  ```
* Create admin user:

  ```js
  db.createUser({ user: "admin", pwd: "pass", roles: ["root"] })
  ```
* **Reason:** Authentication ke bina koi bhi connect karke data access kar sakta hai.

---

## 1️⃣4️⃣ Describe role-based access control in MongoDB.

* MongoDB me har user ko **role** diya jata hai (e.g., read, readWrite, dbAdmin).
* Example:

  ```js
  db.createUser({ user: "rahul", pwd: "123", roles: ["readWrite"] })
  ```
* **Reason:** RBAC ensures least privilege → user ko sirf required permissions milti hain.

---

## 1️⃣5️⃣ Explain how to encrypt MongoDB data.

* **In-transit:** TLS/SSL.
* **At rest:** Encrypted storage engine (AES-256).
* Example: Enable `--enableEncryption` in mongod.conf.
* **Reason:** Protect data leaks if someone steals DB files or sniffs network.

---

## 1️⃣6️⃣ Can you set up MongoDB to use TLS/SSL for connections?

* Yes → configure certificates in `mongod.conf`:

  ```yaml
  net:
    ssl:
      mode: requireSSL
      PEMKeyFile: /etc/ssl/mongodb.pem
  ```
* **Reason:** Encrypts communication between client & server.

---

## 1️⃣7️⃣ How do you use the \$lookup operator in MongoDB?

* Joins collections.
* Example:

  ```js
  db.orders.aggregate([
    { $lookup: {
      from: "customers",
      localField: "cust_id",
      foreignField: "_id",
      as: "customerInfo"
    }}
  ])
  ```
* **Reason:** SQL-style JOINs ko support karta hai NoSQL me.

---

## 1️⃣8️⃣ Can you explain the role of a mongos server in a sharded MongoDB architecture?

* `mongos` = query router.
* Client se queries leta hai aur correct shard(s) ko forward karta hai.
* **Reason:** Application ko shards ka structure nahi pata hota, mongos hide karta hai complexity.

---

## 1️⃣9️⃣ What is journaling in MongoDB and why is it important?

* **Journaling** = recovery log jo ensure karta hai ki crash hone ke baad bhi last writes recover ho sakein.
* Example: Agar crash write ke time hua → journal replay hota hai aur consistency restore hoti hai.
* **Reason:** Data durability guarantee.

---

## 2️⃣0️⃣ How does schema design impact performance in MongoDB?

* **Good design:** Optimized indexes, less joins, fast queries.
* **Bad design:** Redundant data, large documents, slow performance.
* **Reason:** MongoDB schema-less hai, toh design responsibility developer ki hai.

---

## 2️⃣1️⃣ Compare embedding vs. linking documents in MongoDB.

* **Embedding:** Store related data in same document.

  * Fast reads, single query.
  * Example: User + Address inside one doc.
* **Linking (referencing):** Store reference IDs to another collection.

  * Saves space, avoids duplication.
  * Example: Orders refer to `user_id`.
* **Reason:** Choose embedding for **one-to-few**, referencing for **one-to-many**.

---

## 2️⃣2️⃣ What factors do you consider when designing a schema for MongoDB?

* Query patterns (read-heavy vs write-heavy).
* Data relationships (embed or reference).
* Document size (16MB limit).
* Indexing strategy.
* Sharding key selection.
* **Reason:** Schema directly impact karta hai query speed and scalability.

---

## 2️⃣3️⃣ How do you handle one-to-many relationships in MongoDB data modeling?

* **Options:**

  * Embed array (if small).
  * Reference via foreign keys (if large).
* Example:

  ```js
  { name: "Rahul", orders: [101, 102, 103] }
  ```
* **Reason:** Optimize based on access pattern.

---

## 2️⃣4️⃣ How do you perform backups in MongoDB?

* `mongodump` → BSON dump.
* File system snapshots (for large DB).
* Cloud backup services (Ops Manager, Atlas).
* **Reason:** Protect against accidental data loss.

---

## 2️⃣5️⃣ What techniques can be used to restore a MongoDB database?

* `mongorestore` → restore from dump.
* Import JSON/CSV → `mongoimport`.
* Point-in-time restore (from journal / oplog).
* **Reason:** Restore helps recover from corruption or crashes.

---

## 2️⃣6️⃣ How would you monitor the performance of a MongoDB instance?

* MongoDB tools: `mongostat`, `mongotop`.
* Cloud: Atlas monitoring dashboard.
* Third-party: Prometheus + Grafana.
* **Reason:** Monitor queries, memory, replication lag, locks.

---

## 2️⃣7️⃣ How does MongoDB handle DateTime data types?

* Uses `ISODate` object.
* Example:

  ```js
  { createdAt: ISODate("2025-09-10T10:00:00Z") }
  ```
* **Reason:** Stored as BSON Date (64-bit int = ms since epoch).

---

## 2️⃣8️⃣ Can you store multimedia files directly in MongoDB?

* Yes, via **GridFS**.
* Splits file into chunks (default 255KB) and stores in collections.
* Example: `fs.files` + `fs.chunks`.
* **Reason:** Allows storing large files > 16MB document limit.

---


## 1️⃣ How do you connect to a MongoDB database from a Python script?

* Use **PyMongo** library.

```python
from pymongo import MongoClient
client = MongoClient("mongodb://localhost:27017/")
db = client["testDB"]
```

* **Reason:** `MongoClient` ek bridge hai Python aur MongoDB ke beech.

---

## 2️⃣ What is Mongoose and how does it relate to MongoDB?

* **Mongoose** ek ODM (Object Data Modeling) library hai for Node.js.
* Example:

```js
const mongoose = require("mongoose");
mongoose.connect("mongodb://localhost:27017/testDB");
```

* **Reason:** MongoDB documents ko schema-based models me convert karta hai.

---

## 3️⃣ Can you create and use stored procedures in MongoDB?

* Stored procedures **direct nahi**, but **JavaScript functions** Mongo Shell me store aur run kar sakte ho.

```js
db.system.js.save({ _id: "addNumbers", value: function(x, y){ return x+y; } })
db.eval("addNumbers(5,10)")
```

* **Reason:** Limited support, not like RDBMS stored procedures.

---

## 4️⃣ Describe how to use the Mongo Shell for database operations.

* Example commands:

```bash
mongo
use testDB
db.users.insertOne({name:"Amit"})
db.users.find()
```

* **Reason:** Mongo Shell ek interactive CLI hai queries aur admin tasks ke liye.

---

## 5️⃣ How can you perform MongoDB operations using Node.js?

* Use **MongoDB driver**.

```js
const { MongoClient } = require("mongodb");
const client = new MongoClient("mongodb://localhost:27017");
await client.db("testDB").collection("users").insertOne({name:"Rahul"});
```

* **Reason:** Node.js async operations ko MongoDB ke non-blocking model ke sath integrate karta hai.

---

## 6️⃣ List some popular libraries for integrating MongoDB with web applications.

* **Python:** PyMongo, Motor (async).
* **Node.js:** Mongoose, Official MongoDB driver.
* **Java:** Spring Data MongoDB, Morphia.
* **Reason:** Ye ORMs/ODMs coding ko simplify karte hain.

---

## 7️⃣ How is MongoDB used in big data analytics?

* MongoDB + Aggregation + Spark Connector = real-time big data pipelines.
* **Reason:** Horizontal scaling aur flexible schema large unstructured data ke liye best hai.

---

## 8️⃣ Can MongoDB handle real-time analytics workloads?

* Yes, via **aggregation pipelines + in-memory storage engine**.
* Example: Fraud detection, IoT dashboards.
* **Reason:** Query + analyze simultaneously without batch ETL.

---

## 9️⃣ How do you stream large quantities of data into and out of MongoDB?

* Use **Change Streams, Kafka Connector, or bulkWrite API**.

```js
db.collection.bulkWrite([{ insertOne: { document: { name: "x" }}}])
```

* **Reason:** Efficient streaming without overloading.

---

## 🔟 How does MongoDB handle locking and concurrency?

* Uses **document-level locking** (not table-level).
* **Reason:** Parallel writes possible → high concurrency.

---

## 1️⃣1️⃣ What is the relationship between BSON and MongoDB?

* **BSON** = Binary JSON → format in which MongoDB stores data internally.
* **Reason:** Fast parsing, supports extra types like Date, ObjectId.

---

## 1️⃣2️⃣ Can you explain the concept of a cursor in MongoDB?

* Cursor = pointer to result set of a query.

```js
let cursor = db.users.find();
cursor.forEach(doc => print(doc.name));
```

* **Reason:** Allows batch processing without loading all docs at once.

---

## 1️⃣3️⃣ How does MongoDB manage memory?

* Uses **WiredTiger cache** (default) = \~50% of RAM.
* **Reason:** Keeps hot data + indexes in RAM for fast access.

---

## 1️⃣4️⃣ What are some best practices for securing a MongoDB instance?

* Enable authentication, role-based access, TLS/SSL, IP whitelisting, disable `bindIp: 0.0.0.0`.
* **Reason:** Prevents unauthorized access and data leaks.

---

## 1️⃣5️⃣ How do you scale a MongoDB deployment?

* **Vertical:** Add more RAM/CPU.
* **Horizontal:** Sharding.
* **Reason:** Sharding distributes load across servers.

---

## 1️⃣6️⃣ What is Ops Manager in MongoDB?

* Ops Manager = enterprise tool for deployment, monitoring, backups.
* **Reason:** Automates MongoDB cluster management.

---

## 1️⃣7️⃣ How do you troubleshoot a slow-running query in MongoDB?

* Use `explain("executionStats")`.
* Add/optimize indexes.
* **Reason:** Helps identify collection scan vs index scan.

---

## 1️⃣8️⃣ What are some MongoDB cloud-hosted solutions?

* MongoDB Atlas, AWS DocumentDB, Azure CosmosDB (API compatible).
* **Reason:** Provide managed DB with scaling + backups.

---

## 1️⃣9️⃣ How does MongoDB Atlas enhance MongoDB capabilities?

* Atlas = fully managed cloud MongoDB with monitoring, global clusters, auto-backup.
* **Reason:** Saves devops effort.

---

## 2️⃣0️⃣ Can you work with MongoDB using the command line? If so, how?

* Yes, via `mongo` shell or `mongosh`.

```bash
mongosh
use testDB
db.users.find()
```

* **Reason:** CLI for quick queries/admin.
---



### 1. How to Handle Schema Design and Data Modeling in MongoDB?

👉 **Ans:**

* MongoDB schema **flexible hota hai** (document-based), lekin achhi design ke liye:

  * **Embed** karo (nested docs) agar relationship tight hai.
  * **Reference** karo (ObjectId link) agar relationship loose hai ya data huge hai.
* Example: User aur Address embed ho sakte hain, par User aur Orders ko reference karna better hai.
* Reason: Yeh query performance, data consistency aur storage optimize karta hai.

---

### 2. What is GridFS, and When is it Used in MongoDB?

👉 **Ans:**

* GridFS ek **file storage system** hai MongoDB ka jo **16MB se badi files** ko chunks (255KB blocks) mein tod kar store karta hai.
* Example: Images, audio, video store karna.
* Reason: BSON ka size limit 16MB hai, GridFS usse bypass karta hai.

---

### 3. How to Handle Transactions in MongoDB?

👉 **Ans:**

* MongoDB **multi-document ACID transactions** support karta hai.
* Example (Python):

  ```python
  with session.start_transaction():
      coll1.insert_one({"x": 1}, session=session)
      coll2.update_one({"y": 2}, {"$set": {"z": 3}}, session=session)
  ```
* Reason: Banking systems jisme multiple collection updates ek saath karne hote hain, wahan zaruri hai.

---

### 4. What is MongoDB Atlas, and How Does it Differ From Self-Hosted MongoDB?

👉 **Ans:**

* **MongoDB Atlas** = Cloud service (AWS, Azure, GCP par) jo auto-scaling, backups, monitoring provide karta hai.
* **Self-hosted** = Aapko khud server setup, scaling, backup karna padta hai.
* Reason: Atlas maintenance-free hai aur production ke liye fast deploy hota hai.

---

### 5. How to Implement Access Control and User Authentication in MongoDB?

👉 **Ans:**

* **Enable authentication** → `--auth` flag.
* **Create roles and users** → `db.createUser({user:"admin", pwd:"123", roles:["root"]})`.
* Reason: Security ke liye RBAC (Role Based Access Control) use hota hai.

---

### 6. What are Capped Collections, and When are They Useful?

👉 **Ans:**

* Capped collection = Fixed size collection jo **FIFO (first-in-first-out)** overwrite karta hai.
* Example: Logs ya sensor data store karne ke liye.
* Reason: Space controlled hota hai, aur write/read bahut fast hoti hai.

---

### 7. What are Change Streams in MongoDB, and How are They Used?

👉 **Ans:**

* Change Streams real-time notifications dete hain jab data insert/update/delete hota hai.
* Example: Real-time dashboards, chat apps.
* Code (Node.js):

  ```js
  coll.watch().on("change", data => console.log(data));
  ```
* Reason: Polling ki zarurat nahi, direct event-driven system ban jata hai.

---

### 8. Explain the Use of Hashed Sharding Keys in MongoDB

👉 **Ans:**

* Hashed shard key mein field ka **hash value** use hota hai data distribute karne ke liye.
* Example: `_id: "user123"` ko hash karke alag-alag shard pe bhejna.
* Reason: Data evenly distribute hota hai aur load balancing improve hoti hai.

---

### 9. Describe the Map-Reduce Functionality in MongoDB

👉 **Ans:**

* MapReduce = Aggregation ke liye JS-based custom logic.
* Example:

  ```js
  db.orders.mapReduce(
    function() { emit(this.cust_id, this.amount); },
    function(key, values) { return Array.sum(values); },
    { out: "total_spent" }
  )
  ```
* Reason: Complex analytics (e.g., sales report) ke liye useful.

---

### 10. How to Implement Full-Text Search in MongoDB?

👉 **Ans:**

* Create **text index**:

  ```js
  db.articles.createIndex({content: "text"})
  db.articles.find({$text: {$search: "mongodb"}})
  ```
* Reason: Keywords search karna fast ho jata hai documents ke andar.

---

### 11. What are the Considerations for Deploying MongoDB in a Production Environment?

👉 **Ans:**

* Question ka matlab hai: **Production (live users ke liye run karte waqt)** MongoDB kaise deploy karna chahiye?
* Key points:

  * Replica sets enable karo (high availability).
  * Indexes properly design karo (performance).
  * Authentication/TLS enable karo (security).
  * Backups + monitoring setup karo.
* Reason: Ye sab ensure karte hain ki MongoDB reliable, secure aur scalable rahe live environment mein.

---


### 1) Explain the Basic Syntax of MongoDB CRUD Operations.

**Answer (detailed):**

* **Create (Insert):**

  ```js
  db.collection.insertOne({name: "Amit", age: 22})
  db.collection.insertMany([{name:"Rahul"}, {name:"Neha"}])
  ```

  *Explanation:* `insertOne` single document insert karta hai; `insertMany` batch insert — efficient for multiple docs.

* **Read (Query):**

  ```js
  db.users.find({age: 25})                  // cursor (multiple)
  db.users.findOne({name: "Amit"})          // single doc
  db.users.find({}).projection({name:1, _id:0}).limit(5).skip(10).sort({age:-1})
  ```

  *Explanation:* `find()` returns cursor (iterate karo), `projection` select fields, `limit/skip/sort` pagination & ordering.

* **Update:**

  ```js
  db.users.updateOne({name:"Amit"}, {$set:{age:23}})
  db.users.updateMany({city:"Delhi"}, {$inc:{visits:1}})
  db.users.replaceOne({name:"Amit"}, {name:"Amit", age:24, city:"Noida"})
  ```

  *Explanation:* `$set`, `$inc` jaise operators partial updates karte hain; `replaceOne` pura doc replace karta hai.

* **Delete:**

  ```js
  db.users.deleteOne({name:"Amit"})
  db.users.deleteMany({age: {$gt: 60}})
  ```

  *Explanation:* `deleteOne` pehla match delete karega, `deleteMany` sab matching docs.

**Reason (1-line):** CRUD commands JSON-like syntax use karte hain jo developers ke liye intuitive hai; operators allow targeted modifications without full-document overwrite.

---

### 2) How to Perform Data Import and Export in MongoDB?

**Answer (detailed):**

* **Export (for JSON/CSV):** `mongoexport`

  ```bash
  mongoexport --db mydb --collection users --out users.json
  mongoexport --db mydb --collection users --type=csv --fields name,age --out users.csv
  ```
* **Import (JSON/CSV):** `mongoimport`

  ```bash
  mongoimport --db mydb --collection users --file users.json
  mongoimport --db mydb --collection users --type=csv --headerline --file users.csv
  ```
* **Full binary backup / restore:** `mongodump` / `mongorestore`

  ```bash
  mongodump --db mydb --out /backups/mydb
  mongorestore --db mydb /backups/mydb/mydb
  ```
* **GUI / Atlas:** MongoDB Compass / Atlas UI bhi import/export options provide karte hain (point-and-click).

**Reason (1-line):** `mongoexport/mongoimport` textual interchange ke liye, `mongodump/mongorestore` binary snapshot/restore ke liye — performance aur fidelity ke hisaab se choose karte hain.

---

### 3) Explain the Concept of Write Concern and Its Importance in MongoDB

**Answer (detailed):**

* **What:** Write concern defines **how many replicas** ya kaunsa acknowledgement chahiye before a write ko “successful” maana jaye.
* **Common options:**

  * `w:0` — no acknowledgment (fast but unsafe)
  * `w:1` — primary acknowledged (default)
  * `w:"majority"` — majority replicas acknowledge (safer)
  * `j: true` — journaled to disk before ack
  * `wtimeout` — wait timeout for ack
* **Example:**

  ```js
  db.users.insertOne({name:"A"}, {writeConcern: { w: "majority", j: true, wtimeout: 5000 }})
  ```
* **Importance:** Higher write concern → stronger durability & consistency but higher latency and lower throughput; lower write concern → faster but risk data loss on failure.

**Reason (1-line):** Write concern trade-off hai between **safety (durability)** aur **performance (latency)** — choose per application SLA.

---

### 4) What are TTL Indexes, and How are They Used in MongoDB?

**Answer (detailed):**

* **What:** TTL (Time-To-Live) index automatically **removes documents** after a specified time from a Date field.
* **Create example:**

  ```js
  db.sessions.createIndex({ createdAt: 1 }, { expireAfterSeconds: 3600 })
  ```

  (Yahaan `createdAt` field 1 hour ke baad expire ho jayega.)
* **Use cases:** Session storage, temporary caches, event logs, OTP tokens.
* **Behavior:** TTL monitor background job periodical check karta hai; deletion exact real-time nahi hota — small delay ho sakta hai.

**Reason (1-line):** TTL indexes automatic cleanup enable karte hain jisse application-level cron jobs ki zarurat kam hoti aur storage manage rehata hai.

---



## 1) **How are B-tree indexes implemented in MongoDB?**

**Answer (detailed):**

* **Index type:** MongoDB uses a **B-tree–like data structure** (technically a B+Tree) for indexes.
* **Structure:**

  * Index nodes arranged in a tree form.
  * Internal nodes → guide traversal.
  * Leaf nodes → point to actual documents (by `_id` and collection data).
* **Balanced nature:** Always balanced, so insertion, deletion, search take **O(log n)** time.
* **Clustered vs non-clustered:** MongoDB `_id` index is *clustered* (organizes collection order). Other indexes are non-clustered but still reference docs.
* **Example:**

  ```js
  db.users.createIndex({ age: 1 })
  db.users.find({ age: 25 })
  ```

  🔎 Internally → MongoDB hashes through B-tree → finds all leaf nodes where `age=25` stored → directly fetch docs. Without index → full collection scan.
* **Use cases:** fast lookups, range queries (`$lt`, `$gt`), sorting (because B-tree keeps keys sorted).

**Reason (1-liner):**
B-tree index maintain sorted keys in balanced form → ensures **logarithmic search time** and supports **range queries + sorting** efficiently.

---

## 2) **Explain the role of the Profiler in MongoDB.**

**Answer (detailed):**

* **What:** Profiler = in-built tool in MongoDB that logs information about **slow queries, write operations, and their performance**.
* **Levels:**

  * `0` → off
  * `1` → only slow operations logged (default: >100ms, configurable via `slowOpThresholdMs`)
  * `2` → all operations logged
* **Enable example:**

  ```js
  db.setProfilingLevel(1, { slowms: 50 })
  db.system.profile.find().pretty()
  ```

  → Yahaan har query jo 50ms se zyada lagti hai woh `system.profile` collection mein store hogi.
* **Data captured:** query shape, index used or not, execution time, number of documents scanned vs returned.
* **Use case:**

  * Identify **slow queries**
  * Detect **missing indexes**
  * Debug **performance bottlenecks**
* **Why important:** Without profiler, aapko pata nahi chalega ki queries background mein kitna time le rahi hain; profiler help karta hai optimize karne ke liye.

**Reason (1-liner):**
Profiler = **performance microscope** of MongoDB — slow queries, index usage aur latency issues track karta hai so that developers can tune schema & indexes.

---
