
## 1. Difference between **Library** and **Framework**

### Library

* Aap library ko **zarurat ke time call karte ho**.
* Control programmer ke paas hota hai → aap decide karte ho kaunsi function kab call karna hai.
* Example: **React** ek library hai.

  * React ke andar `useState`, `useEffect`, ya `createElement` jaise tools hain.
  * Aap decide karte ho state kaise change karni hai, component kaise render karna hai.
  * React sirf **UI banane** mein madad karta hai, baki ka structure (routing, data fetching) aapke haath mein hai.

👉 Example:

```js
function Counter() {
  const [count, setCount] = React.useState(0); // yeh "state" hai
  return (
    <div>
      <p>{count}</p>
      <button onClick={() => setCount(count + 1)}>Increase</button>
    </div>
  );
}
```

* Jab `setCount` call karte ho, **state change hoti hai** → React automatically **UI ko dobara render** karta hai (react karta hai).
* Aapne manually DOM ko update nahi kiya, React ne automatically kar diya.

---

### Framework

* Framework **poora structure aur rules** provide karta hai.
* Control framework ke paas hota hai (isse kehte hain **Inversion of Control**).
* Example: **Angular** ek framework hai.

  * Angular lifecycle, dependency injection, routing sab handle karta hai.
  * Aapko uske structure ke hisaab se code likhna padta hai.
  * Aap control se zyada Angular ke rules follow karte ho.

👉 Simple analogy:

* Library = **Restaurant menu** (aap decide karte ho kya order karna hai).
* Framework = **Thali system** (poora framework decide karega kya aur kaise milega).

---

## 2. Difference between **React** and **ReactDOM**

* **DOM (Document Object Model)** – ek tree-like structure jo browser HTML ko banata hai.

  * Example:

  ```html
  <html>
    <body>
      <h1>Hello</h1>
    </body>
  </html>
  ```

  Yeh browser ke andar ek **DOM tree** ban jata hai.

* **React** – components banane ke liye. (sirf logic aur UI ka description hota hai).

* **ReactDOM** – React components ko actual **webpage (DOM)** par render karne ke liye.

👉 Example:

```js
import React from "react";
import ReactDOM from "react-dom";

function App() {
  return <h1>Hello React</h1>;
}

// yeh line React component ko DOM ke "root" element ke andar daalti hai
ReactDOM.render(<App />, document.getElementById("root"));
```

* Agar **React** hota aur ReactDOM na hota → aap component bana lete, lekin woh browser mein kabhi show nahi hota.
* Agar **ReactDOM** hota aur React na hota → aapke paas render karne ke liye components hi nahi hote.

👉 Simple analogy:

* React = **design/blueprint**
* ReactDOM = **construction worker jo design ko ghar mein badal de**

---

## 3. What is **async** and **defer**?

Jab aap `<script>` tag likhte ho external JS ke liye, woh HTML parsing ke sath interfere karta hai.

### Normal Script (without async/defer)

```html
<script src="app.js"></script>
```

* HTML parsing ruk jaati hai jab tak script download + execute na ho jaye.
* Page load slow ho jaata hai.

---

### async

```html
<script src="app.js" async></script>
```

* Script parallel download hoti hai HTML ke sath.
* Jaise hi download complete hoti hai, **turant execute hoti hai** (chahe HTML parsing complete hua ya nahi).
* Isse order guarantee nahi hota agar multiple async scripts ho.

👉 Use case: Analytics, Ads scripts (jinka order matter nahi karta).

---

### defer

```html
<script src="app.js" defer></script>
```

* Script bhi parallel download hoti hai HTML ke sath.
* Lekin **execute tab hoti hai jab HTML parsing complete ho jaye**.
* Multiple defer scripts order mein hi run hoti hain.

👉 Use case: Page ka main JS code (kyunki HTML parse hone ke baad execute hona safe hai).

---
---

### 4. Why is React known as React?

👉 React ka naam **UI mein “reactive updates”** ke concept se aaya.
👉 State change hone par UI automatically react karta hai (re-render hota hai).

---


### 3. What is CDN? Why do we use it?

👉 **CDN (Content Delivery Network)** – distributed servers jo static files (JS, CSS, images) ko fast deliver karte hain.
👉 **Use**:

* Faster load (nearby server se file milti hai).
* Bandwidth kam lagti hai.
* Caching better hota hai.
* Example:

```html
<script src="https://cdn.jsdelivr.net/npm/react@18/umd/react.production.min.js"></script>
```

---

### 1. What is Emmet?

👉 Emmet ek **plugin** hai jo HTML/CSS likhne ko fast banata hai.
👉 Shortcut likhne par woh full code expand kar deta hai.

* Example: `div.container>ul>li*3` → expand ho kar:

```html
<div class="container">
  <ul>
    <li></li>
    <li></li>
    <li></li>
  </ul>
</div>
```

---


## 1. What is **crossorigin in script tag**?

👉 Jab aap `<script>` tag me external resource load karte ho (CDN, 3rd party), toh browser ko pata hona chahiye ki credentials (cookies/auth headers) bhejne hain ya nahi.
👉 Iske liye `crossorigin` attribute use hota hai.

* `crossorigin="anonymous"` → credentials send nahi hote (default case).
* `crossorigin="use-credentials"` → cookies/auth bhi send hote hain.

Example:

```html
<script src="https://cdn.example.com/lib.js" crossorigin="anonymous"></script>
```

---

## 2. What is **CORS**? Why is it used?

👉 **CORS (Cross-Origin Resource Sharing)** ek **browser security mechanism** hai.
👉 Yeh decide karta hai ki ek website (domain A) dusre domain (domain B) ke resources ko access kar sakti hai ya nahi.

📌 Example:

* Aapki site: `https://myapp.com`
* API server: `https://api.example.com`
* Agar API ne `Access-Control-Allow-Origin: *` header bheja → koi bhi domain usko access kar sakta hai.
* Agar API ne `Access-Control-Allow-Origin: https://myapp.com` bheja → sirf `myapp.com` use kar sakta hai.

👉 **CORS Policy**:

* Browser default me **same-origin policy** lagata hai (sirf apne domain ka data access karne deta hai).
* Agar aapko dusre domain ka data chahiye toh server ko proper CORS headers bhejne padte hain.

---

## 3. What is **Vite**?

👉 Vite ek **next-gen frontend build tool** hai (Evan You ne banaya, Vue.js creator).
👉 Features:

* **Super fast dev server** (native ES modules ka use karta hai).
* **Hot Module Replacement (HMR)** → code change karte hi browser update ho jata hai without reload.
* **Production build** ke liye internally Rollup use karta hai.

📌 Example:

```bash
npm create vite@latest my-app
cd my-app
npm install
npm run dev
```

---

## 4. What is **Create React App (CRA)**?

👉 Facebook team ne banaya ek **tool** jo React project ko quickly setup karta hai.
👉 Features:

* Babel + Webpack already configured.
* Development server, hot reloading, testing setup included.
* Ek command se poora ready-made React environment milta hai.

---

## 5. What is **npx create-react-app**?

👉 `npx` ek npm tool hai jo packages ko **temporarily install karke run** karta hai (globally install karne ki zarurat nahi).
👉 Jab aap likhte ho:

```bash
npx create-react-app my-app
```

* `create-react-app` package download hota hai, run hota hai, aur React project ban jata hai.
* Aapko manually `npm install -g create-react-app` karne ki zarurat nahi.

---

## 6. What is **npm**?

👉 **npm (Node Package Manager)** → Node.js ka official package manager.
👉 Use:

* Libraries install karna (`npm install react`)
* Dependencies manage karna (package.json ke through).
* Scripts run karna (`npm run start`)

---

## 7. What is **Yarn**?

👉 Yarn ek **alternative package manager** hai jo Facebook ne banaya tha (npm ke flaws fix karne ke liye).
👉 Features:

* Faster dependency installation (caching use karta hai).
* Lockfile system better tha (npm v5 ke pehle).
* Commands npm se thode different hote hain.

📌 Example:

```bash
yarn add react
yarn start
```

---

✅ Short Summary (revision style):

* **crossorigin** → external resource load karte waqt credentials bhejne/na bhejne ka control.
* **CORS** → ek security policy jo cross-domain requests control karti hai.
* **Vite** → fast build tool (modern alternative to CRA).
* **CRA** → React app banane ka boilerplate setup tool.
* **npx CRA** → ek hi command se CRA run ho jata hai without global install.
* **npm** → Node.js ka package manager.
* **Yarn** → npm ka fast alternative.

---
## 1. What is **Parcel / Webpack**? Why do we need it?

👉 **Bundlers** hote हैं jo alag-alag files (JS, CSS, images) ko ek saath bundle karke optimize karte hain.
👉 Why needed?

* Browser ko directly multiple JS modules samajhna mushkil hota hai.
* Bundlers help:

  * Minification (size chhota karna)
  * Tree Shaking (unused code hataana)
  * Hot Module Replacement (fast reload)
  * Different assets ko ek bundle banana.

📌 **Webpack** → sabse purana & highly configurable.
📌 **Parcel** → zero-config, fast, built-in optimizations.

---

## 2. What is `.parcel-cache`?

👉 Parcel build ke waqt ek hidden folder `.parcel-cache/` banata hai.
👉 Isme **cached info** hoti hai taaki agla build fast ho.
👉 Agar delete kar doge toh next build slow hoga (Parcel dobara sab cache karega).

---

## 3. What is **npx**?

👉 **npx (npm execute)** ek npm tool hai jo **temporary download karke package run** karta hai.
👉 Isse aapko package ko globally install karna nahi padta.

📌 Example:

```bash
npx create-react-app my-app
```

* CRA package download hota hai → execute hota hai → project create hota hai.

---

## 4. Difference between **dependencies vs devDependencies**

👉 Yeh dono `package.json` me likhe hote hain.

* **dependencies** → jo code **production** me bhi chahiye.

  * Example: `react`, `axios`.
* **devDependencies** → jo sirf **development/test** ke time chahiye.

  * Example: `webpack`, `jest`, `eslint`.

---

## 5. What is **Tree Shaking**?

👉 Dead code elimination technique.
👉 Matlab jo code **use nahi ho raha** usko final bundle se remove karna.

📌 Example:

```js
// utils.js
export function add(a, b) { return a+b }
export function sub(a, b) { return a-b }

// index.js
import { add } from "./utils";
console.log(add(2,3));
```

👉 Final bundle me sirf `add` function aayega, `sub` remove ho jayega.

---

## 6. What is **Hot Module Replacement (HMR)**?

👉 Ek feature jisme code change karne par **poore page reload nahi hota**, sirf badle huye module update hote hain.
👉 Isse development super fast ho jaata hai.

📌 Example: React app me button text badal ke save kiya → page reload nahi hota, bas wahi component update ho jata hai.

---

## 7. Parcel ki 5 Superpowers (Features)

1. **Zero Config** → koi extra setup nahi chahiye, out-of-box kaam karta hai.
2. **Hot Module Replacement (HMR)** → fast reloads.
3. **Tree Shaking** → unused code remove.
4. **Code Splitting** → large code ko chhote bundles me todta hai.
5. **Asset Optimization** → images, CSS, HTML, JS sab optimize.

👉 Explain 3 in my words:

* **Zero Config** → Webpack me config likhna padta hai, Parcel me kuch nahi likho aur project run ho jata hai.
* **HMR** → Developer productivity boost, page reload nahi hota.
* **Tree Shaking** → Final bundle me sirf zarurat ka code hota hai, size chhoti ho jaati hai.

---

## 8. What is `.gitignore`?

👉 Ek file jisme likhte ho kaunsi files/folders Git ko track nahi karni.
👉 Should Add:

* `node_modules/`
* `dist/`
* `.parcel-cache/`
* `.env` (sensitive configs)

👉 Should NOT Add:

* Source code (`src/`)
* `package.json` / `package-lock.json`
* Config files (webpack.config.js)

---



## 11. What is **node\_modules**? Should I push it to Git?

👉 Folder jisme npm/yarn install ki hui libraries hoti hain.
👉 Iska size bahut bada hota hai.
👉 Isko push karna **galat idea** hai, kyunki `package.json + lock file` ke base par kisi bhi machine pe `npm install` se node\_modules dobara ban jaayega.

---

## 14. Different Bundlers (summary)

* **Webpack** → very powerful, configurable, but complex.
* **Parcel** → zero-config, fast, beginner-friendly.
* **Vite** → dev server super fast (uses ES modules), build Rollup ke through.

---

## 15. What is `^` (caret) and `~` (tilde) in npm versions?

* `^1.2.3` → update allowed for minor + patch (`1.x.x`) but not major.
* `~1.2.3` → update allowed only for patch (`1.2.x`) but not minor/major.

📌 Example:

* `^1.2.3` → can install `1.5.0` but not `2.0.0`.
* `~1.2.3` → can install `1.2.8` but not `1.3.0`.

---

## 16. Script types in HTML (from MDN Docs)

* `<script>` → default JS script.
* `<script type="module">` → ES6 modules (supports `import/export`).
* `<script type="text/javascript">` → legacy, same as default JS.
* `<script nomodule>` → browsers that don’t support modules run this.

📌 Example:

```html
<script type="module" src="main.js"></script>
<script nomodule src="fallback.js"></script>
```

---
## 1. Difference between **package.json vs package-lock.json**

* **package.json**

  * Project ka **metadata** (name, version, scripts, dependencies list).
  * Dependencies ko **range (caret ^, tilde \~)** ke saath specify karta hai.
  * Human-readable.

* **package-lock.json**

  * Auto-generated file hai.
  * Dependencies ka **exact version + integrity hash** store hota hai.
  * Machine-readable → ensure karta hai ki sab developers ke system par **same version install ho**.

📌 Example:

```json
// package.json
"dependencies": {
  "react": "^18.0.0"
}
```

```json
// package-lock.json
"node_modules/react": {
  "version": "18.0.2",
  "resolved": "https://registry.npmjs.org/react/-/react-18.0.2.tgz",
  "integrity": "sha512-..."
}
```

👉 Matlab `package.json` bolta hai → mujhe React ka **18.x.x** chahiye.
👉 Aur `package-lock.json` bolta hai → install hua **18.0.2 exact version**.

---

## 2. Why should I not modify **package-lock.json**?

* Ye file npm/yarn khud generate karta hai.
* Agar manually change karoge → dependencies mismatch ho sakti hai.
* Worst case: Project kisi machine par chale, kisi par na chale.

✅ Best practice → kabhi manually edit na karo, sirf `npm install`, `npm update` run karo.

---

## 3. What is **dist folder**?

👉 **dist = distribution** folder.
👉 Jab aap project ko **build** karte ho (production ready banate ho), uska optimized output **dist** me save hota hai.

* Yeh **aapka source code (src/)** nahi hota.
* Yeh **compiled + minified + optimized code** hota hai jo **browser ko diya jata hai**.

📌 Example:

* Local pe code (`src/`):

```js
import React from "react";
console.log("Hello Developer Mode");
```

* Build ke baad (`dist/` file minified):

```js
console.log("Hello Developer Mode");
```

aur saari files ek bundle me merge ho jati hain (CSS, images, JS sab optimize).

👉 **dist folder woh hissa hai jo server par deploy hota hai, na ki aapka raw code**.

---

## 4. What is **Build**?

👉 Build = aapke **raw source code (src)** ko ek **optimized production code** me convert karna.
👉 Build ke steps:

* JS → transpile (Babel use karke ES6 → ES5 for browser support).
* Code → minify (spaces, comments remove).
* Tree Shaking (unused code remove).
* Assets (images, CSS) → compress.

📌 Example:

* Development (raw code) → easy to debug.
* Build (dist) → fast load, optimized for users.

---

## 5. What is **.parcel-cache**? (Detail mein)

👉 Jab aap Parcel bundler use karte ho, woh har build me ek folder `.parcel-cache/` banata hai.

### Purpose:

* Build process **fast banane ke liye** cache store karta hai.
* Parcel compile karte waqt intermediate results save karta hai.
* Next build me woh dobara sab compile nahi karta, cache se use karta hai.

### Kab banta hai?

* Jab aap first time `parcel build` ya `parcel serve` run karte ho.

### Kya hota hai isme?

* AST (Abstract Syntax Tree), transpiled code, optimized assets ke cached versions.
* Taaki repeat build fast ho.

### Repository mein kaha hota hai?

* Ye **frontend project** ke root folder me hota hai (backend me nahi).
* Backend tools (like Node.js, Express) generally `.parcel-cache` nahi use karte.

👉 Agar delete kar do → Parcel next build me dubara banayega (bas thoda slow hoga).

---

## 6. What is **browserslist**? (Simplified Explanation)

👉 **Browserslist** ek config hai jo batata hai → “Mere project ko kaunse browsers support karne chahiye?”

### Kyu?

* Har browser alag features support karta hai (Chrome new features, IE old).
* Tools like **Babel** (JS transpiler) aur **Autoprefixer** (CSS prefixes) is config ko padte hain.
* Uske hisaab se code transpile karte hain.

📌 Example:

```json
"browserslist": [
  ">0.5%",        // worldwide 0.5% se zyada users wale browsers
  "last 2 versions", // har browser ke last 2 versions
  "not dead"     // purane browsers (jaise IE) exclude
]
```

### Use case:

* Agar aap `last 2 versions` likhte ho → Babel JS ko aise transpile karega ki Chrome last 2 versions, Firefox last 2 versions, etc. pe chale.
* Agar aap `>5%` likhte ho → sirf un browsers ke liye optimize karega jinka usage >5% hai.

👉 Matlab: Browserslist = “Mere users ke browsers ke hisaab se code compatibility bana do.”

---

✅ **Quick Recap:**

* **package.json vs lock** → range vs exact version.
* **Don’t edit lock file** → npm manage karta hai.
* **dist** → production optimized output.
* **Build** → process to create dist.
* **.parcel-cache** → Parcel ka fast-build helper folder (frontend only).
* **browserslist** → browsers ke support target define karta hai (Babel/PostCSS use karte hain).

---
## 1. What is **JSX**?

👉 **JSX (JavaScript XML)** ek syntax extension hai jo HTML jaise dikhता hai lekin actually JavaScript ke andar hota hai.
👉 Yeh developer ko UI code likhne ka simple tareeka deta hai.

📌 Example (JSX):

```jsx
const element = <h1>Hello, JSX!</h1>;
```

📌 Without JSX (plain JS):

```js
const element = React.createElement("h1", null, "Hello, JSX!");
```

👉 Analogy: JSX = **shorthand language**, jaise Hindi-English mix bolna easy hota hai.

---

## 2. **React.createElement vs JSX**

* **React.createElement()**

  * Pure JS method hai jo ek React element banata hai.
  * Syntax lamba hota hai.

📌 Example:

```js
const heading = React.createElement("h1", { className: "title" }, "Hello World");
```

* **JSX**

  * Cleaner, HTML-like syntax.
  * Yeh internally `React.createElement` me convert hota hai (Babel ke through).

📌 Example:

```jsx
const heading = <h1 className="title">Hello World</h1>;
```

👉 Analogy:

* `React.createElement` = **mathematics ki full derivation likhna**.
* `JSX` = **formula shortcut use karna**.

---

## 3. **Benefits of JSX**

1. **Readable & Declarative** → Code HTML jaisa lagta hai, easy to understand.
2. **Compile to JS** → Pure JS me convert hota hai, so fast.
3. **Power of JS + HTML** ek saath → curly braces `{}` ke andar JS likh sakte ho.

📌 Example:

```jsx
const user = "Amit";
const element = <h2>Welcome, {user}!</h2>;
```

👉 Curly braces `{}` = JavaScript expression inside HTML.

---

## 4. **Behind the Scenes of JSX**

👉 JSX khud browser samajhta nahi.
👉 **Babel** compiler JSX ko convert karta hai into `React.createElement`.
👉 React phir us element ko **Virtual DOM** me rakhta hai aur DOM ko efficiently update karta hai.

📌 Example:

```jsx
const el = <h1 id="main">Hello</h1>;
```

👉 Babel converts into:

```js
const el = React.createElement("h1", { id: "main" }, "Hello");
```

---

## 5. **Babel & Parcel role in JSX**

* **Babel**

  * JSX ko plain JS me transpile karta hai.
  * ES6+ features ko old JS (ES5) me convert karta hai for browser compatibility.

* **Parcel**

  * Build tool hai jo Babel ko run karta hai.
  * Saare assets (JSX, CSS, images) bundle + optimize karta hai.
  * Hot Module Replacement provide karta hai (dev fast hota hai).

👉 Analogy:

* JSX = Hindi-English mix.
* Babel = **translator** jo isko pure English (JS) me convert kare.
* Parcel = **delivery guy** jo final package bana ke browser tak pahunchaye.

---

## 6. **Components in React**

👉 Components = **building blocks** of React apps.
👉 Ek component = ek **function** ya **class** jo JSX return karta hai.

📌 Example:

```jsx
function Welcome() {
  return <h1>Hello World!</h1>;
}
```

---

## 7. **Functional Components**

👉 Yeh **functions** hote hain jo ek React element return karte hain.
👉 Recommended way hai (simple aur fast).

📌 Example:

```jsx
function Greeting(props) {
  return <h2>Hello, {props.name}!</h2>;
}
```

Use:

```jsx
<Greeting name="Rahul" />
```

👉 Output: `Hello, Rahul!`

---

## 8. **Composing Components**

👉 Matlab ek component ke andar dusre components use karna.
👉 Yeh React ka sabse bada superpower hai → reusability.

📌 Example:

```jsx
function Header() {
  return <h1>My Website</h1>;
}

function Footer() {
  return <p>© 2025 All rights reserved</p>;
}

function App() {
  return (
    <div>
      <Header />
      <p>Main content goes here...</p>
      <Footer />
    </div>
  );
}
```

👉 Output: Page with header, content, footer.

👉 Analogy: Components = **LEGO blocks** 🧱 → chhote pieces milkar bada structure banate hain.
---

