
## 1. React Fundamentals

* Introduction to React
* Why React? Features & Advantages
* Import & Export in React
* Virtual DOM vs Real DOM
* JSX (syntax, rules, expressions, attributes)
* React Elements & Tags
* Inline Styles, Attributes
* React Fragments

---

## 2. Components

* Functional Components
* Class Components
* Props (passing data, default props, PropTypes)
* The `children` prop
* Component Composition
* Conditional Rendering
* Lists & Keys
* Prop Drilling problem & solutions

---

## 3. State Management (Core React)

* Component State (use in Class & Functional components)
* Updating & Managing State
* State vs Props
* Memoization with `React.memo`

---

## 4. React Events

* Handling Events in React
* Event Binding (`onClick`, `onChange`, etc.)
* Specific Events:

  * `onClickCapture`
  * `onMouseDown`
  * `onDoubleClick`
  * `onSubmit`
  * `onScroll`
  * `onBlur`

---

## 5. React Hooks (Functional Programming with React)

* Hooks Introduction & Rules of Hooks
* `useState`
* `useEffect` (side effects, cleanup functions)
* `useRef`
* `useLayoutEffect`
* `useMemo`
* `useCallback`
* `useContext`

---

## 6. Context & Advanced State

* Context API (Provider & Consumer)
* Avoiding Prop Drilling with Context
* Redux (State container for large apps)

  * Redux basics (actions, reducers, store)
  * Using Redux with React
  * Redux Toolkit (modern approach)

---

## 7. Lifecycle Methods (Class Components)

* `constructor`
* `componentDidMount`
* `componentDidUpdate`
* `componentWillUnmount`
* Error Handling:

  * Error Boundaries
  * `getDerivedStateFromError`
  * `componentDidCatch`
* `shouldComponentUpdate`

---

## 8. Routing in React

* Introduction to `react-router-dom`
* Types of Routers (BrowserRouter, HashRouter, MemoryRouter)
* Navigation & Routing
* Link & NavLink
* Route Parameters
* Nested Routes
* React Router Hooks (`useNavigate`, `useParams`, etc.)

---

## 9. Styling in React

* Inline Styling
* CSS Modules
* Styled Components
* Tailwind CSS
* Material UI
* React Bootstrap
* Framer Motion (animations)

---

## 10. Error Handling & Performance

* Error Boundaries
* Handling async errors
* React Strict Mode
* Performance optimization techniques

  * Code Splitting
  * Lazy Loading (`React.lazy` & `Suspense`)
  * Memoization (`React.memo`, `useMemo`, `useCallback`)

---

## 11. Building & Deploying React Apps

* Project structure best practices
* Environment Variables
* Working with APIs (fetch, axios)
* Form handling & validation
* Authentication (JWT, OAuth)
* State Persistence (localStorage/sessionStorage)
* Testing:

  * Unit Testing with Jest
  * Component Testing with React Testing Library
* Build & Deployment:

  * Vite / CRA builds
  * Hosting on Netlify, Vercel, GitHub Pages

----


-----

-----

## **1. Introduction to React (React ka Parichay)**

**React** ek powerful **JavaScript library** hai jise **Facebook** ne banaya hai. Iska mukhya kaam **User Interfaces (UIs)**, yaani jo screen par dikhta hai, use banana hai.

Yeh khaaskar **Single Page Applications (SPAs)** banane ke liye popular hai. SPAs aisi websites hoti hain jo poora page reload kiye bina content ko update karti hain (jaise Gmail ya Facebook).

React ka mool mantra hai - **"UI ko chhote-chhote, reusable tukdon mein todo"**. In tukdon ko hum **Components** kehte hain.

-----

-----

## **2. Why React? (React hi Kyun? Features & Fayde)**

React itna popular kyun hai, iske kuch khaas kaaran hain:

  * **Component-Based Architecture (Tukdon mein UI)**
    Ismein hum poore UI ko alag-alag, azaad components (jaise `Navbar`, `Button`, `Card`) mein tod dete hain. Yeh LEGO bricks 🧱 jaisa hai. Isse code saaf-suthra, manage karne mein aasan, aur reusable ho jaata hai.

  * **Virtual DOM (Tez Updates ke liye)**
    React asli DOM ko seedhe badalne ke bajaye, memory mein ek **Virtual DOM** (nakli DOM) banata hai. Jab bhi kuch update hota hai, React pehle Virtual DOM mein badlaav karta hai, phir use puraane Virtual DOM se compare karta hai, aur sirf jo zaroori badlaav hain, unhein hi asli DOM par ek saath update karta hai. Isse app ki **performance bahut tez** ho jaati hai.

  * **JSX (HTML jaisa Syntax)**
    Yeh aapko JavaScript ke andar hi HTML jaisa code likhne ki suvidha deta hai. Isse UI banana bahut aasan aur intuitive ho jaata hai.

  * **One-Way Data Flow (Ek Taraf Data ka Bahaav)**
    React mein data hamesha parent component se child component (upar se neeche) ki taraf jaata hai. Isse code ko samajhna aur debug karna aasan ho jaata hai kyunki data kahan se aa raha hai, yeh saaf pata chalta hai.

  * **Declarative UI (Bas Batao, Karo Mat)**
    Aap bas React ko yeh batate hain ki kisi state ke liye UI **kaisa dikhna chahiye**. React khud figure out kar leta hai ki us state tak pahunchne ke liye DOM mein **kya-kya badlaav karne hain**. Aapko `document.getElementById` jaise manual DOM manipulation se chhutkaara mil jaata hai.

-----

-----

## **3. Import & Export in React**

Yeh ES6 JavaScript ka feature hai, lekin React components ko organize karne ke liye bahut zaroori hai.

  * **`export` (Apni file se kuch bahar bhejna)**

    1.  **Named Export**: Jab aapko ek file se **kayi cheezein** export karni hon.

        ```javascript
        // helpers.js
        export const PI = 3.14;
        export function greet(name) {
          return `Hello, ${name}`;
        }
        ```

    2.  **Default Export**: Jab aapko ek file se sirf **ek mukhya cheez** (aam taur par component) export karni ho. Ek file mein sirf ek hi default export ho sakta hai.

        ```javascript
        // Button.js
        function Button() {
          return <button>Click Me</button>;
        }
        export default Button;
        ```

  * **`import` (Doosri file se kuch andar laana)**

    1.  **Named Import**: Named exports ko import karne ke liye. Aapko **curly braces `{}`** ka istemaal karna padta hai.

        ```javascript
        import { PI, greet } from './helpers.js';
        ```

    2.  **Default Import**: Default export ko import karne ke liye. Ismein curly braces nahi lagte.

        ```javascript
        import MyButton from './Button.js'; // Naam aap kuch bhi de sakte hain
        ```

-----

-----

## **4. Virtual DOM vs Real DOM**

| Feature          | Real DOM                                                                                         | Virtual DOM                                                                                         |
| :--------------- | :----------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------- |
| **Yeh Kya Hai?** | Yeh browser dwara banaya gaya asli, standard DOM hai.                                            | Yeh Real DOM ki ek in-memory, lightweight copy hai (JavaScript object).                             |
| **Updates**      | **Dheema (Slow)**. Ek chhota sa badlaav bhi poore UI ko recalculate aur repaint karwa sakta hai. | **Tez (Fast)**. Updates pehle yahan hote hain, jo ki bahut tez hai kyunki yeh memory mein hota hai. |
| **Manipulation** | Ise manually manipulate karna padta hai (`document.getElementById` etc.).                        | Ise React handle karta hai. Hamein seedhe ise chhedne ki zaroorat nahi padti.                       |
| **Fayda**        | Yeh web ka standard hai.                                                                         | Yeh performance ko behtar banata hai, bewajah ke DOM updates ko rok kar.                            |

-----

-----

## **5. JSX (JavaScript XML)**

JSX, JavaScript ka ek syntax extension hai. Yeh aapko JavaScript ke andar HTML jaisa UI code likhne deta hai.

### **JSX ke Niyam (Rules)**

1.  **Ek Root Element Zaroori**: Ek component hamesha ek hi root element return kar sakta hai. Agar aapko kayi elements return karne hain, toh unhein ek `<div>` ya Fragment (`<>`) mein wrap karein.

    ```jsx
    // Sahi ✅
    return (
      <div>
        <h1>Title</h1>
        <p>Paragraph</p>
      </div>
    );

    // Galat ❌
    // return (
    //   <h1>Title</h1>
    //   <p>Paragraph</p>
    // );
    ```

2.  **Attributes ke liye camelCase**: HTML attributes ko camelCase mein likha jaata hai.

      * `class` ban jaata hai `className`.
      * `for` ban jaata hai `htmlFor`.
      * `onclick` ban jaata hai `onClick`.

3.  **Har Tag ko Close Karein**: Har tag ko close karna zaroori hai. Jin tags ka closing tag nahi hota (jaise `<img>`, `<br>`), unke aage slash `/` laga dein.

    ```jsx
    <img src="..." alt="..." />
    <br />
    ```

### **JSX mein JavaScript Expressions**

Aap JSX ke andar JavaScript likhne ke liye **curly braces `{}`** ka istemaal kar sakte hain.

```jsx
const name = "Virat";
const element = <h1>Hello, {name}!</h1>; // Output: Hello, Virat!

function calculateScore(a, b) {
  return a + b;
}
const score = <p>Total Score: {calculateScore(50, 50)}</p>; // Output: Total Score: 100
```

-----

-----

## **6. React Elements & Tags**

  * **React Elements**
    React elements React apps ke sabse chhote building blocks hain. Yeh plain JavaScript objects hote hain jo batate hain ki screen par kya dikhna chahiye. Jab aap JSX likhte hain, toh Babel use `React.createElement()` calls mein badal deta hai, jo in objects ko banata hai.
    `const element = <h1>Hello</h1>;`

  * **Tags in JSX**

    1.  **Lowercase Tags**: Jab ek tag lowercase se shuru hota hai (jaise `<div>`, `<h1>`, `<p>`), toh React use ek standard **HTML tag** maanta hai.
    2.  **Uppercase Tags**: Jab ek tag uppercase se shuru hota hai (jaise `<Navbar>`, `<ProfileCard>`), toh React use ek **React Component** maanta hai. Yeh convention bahut zaroori hai.

-----

-----

## **7. Inline Styles aur Attributes**

  * **Inline Styles**
    JSX mein `style` attribute ek string nahi, balki ek **JavaScript object** leta hai.

      * Properties `camelCase` mein honi chahiye (`background-color` ban jaata hai `backgroundColor`).
      * Aapko do curly braces `{{...}}` ka istemaal karna padta hai: pehla JSX expression ke liye, aur doosra style object ke liye.

    <!-- end list -->

    ```jsx
    function MyComponent() {
      const myStyle = {
        color: 'white',
        backgroundColor: 'blue', // background-color -> backgroundColor
        padding: '10px'
      };

      return <div style={myStyle}>Styled Div</div>;
    }
    ```

  * **Attributes**
    JSX attributes aam taur par HTML jaise hi hote hain, bas `camelCase` niyam ka dhyaan rakhein (`className`, `onClick`, `htmlFor` etc.).

-----

-----

## **8. React Fragments**

**Samasya**: Har component ko ek single root element return karna hota hai. Is chakkar mein hum aksar ek faaltu `<div>` laga dete hain, jo DOM mein ek extra node jodta hai.

**Samadhaan**: **Fragments** aapko kayi elements ko group karne dete hain **bina DOM mein koi extra node jode**.

**Kaise Istemal Karein**:
Aap ya toh `<React.Fragment>` likh sakte hain, ya iska shortcut, khaali angle brackets `<>...</>`, istemaal kar sakte hain.

```jsx
import React from 'react';

function MyComponent() {
  return (
    <>
      <td>Item 1</td>
      <td>Item 2</td>
    </>
    // Upar ka code DOM mein koi extra div nahi joddta.
  );
}
```

----


-----

-----

## **1. Functional Components**

Yeh React components banane ka **modern aur sabse aam tareeka** hai.

**Yeh Kya Hain?**
Functional components simple JavaScript functions hote hain. Yeh `props` (data) ko as an argument lete hain aur UI (user interface) render karne ke liye JSX return karte hain.

**React Hooks** (jaise `useState`, `useEffect`) ke aane ke baad, yeh functional components state (data) aur doosre React features ko bhi handle kar sakte hain.

**Analogy**: Yeh ek recipe 📜 jaisa hai, jo ingredients (`props`) leta hai aur ek swadisht dish (UI) banakar deta hai.

**Syntax:**

```jsx
// props ek object hai jismein parent se bheja gaya data hota hai
function Welcome(props) {
  return <h1>Hello, {props.name}!</h1>;
}
```

-----

-----

## **2. Class Components**

Yeh components banane ka **puraana tareeka** hai. Naye projects mein iska istemaal kam hota hai, lekin puraane codebase mein yeh aapko zaroor milenge.

**Yeh Kya Hain?**
Class components ES6 classes hoti hain jo `React.Component` ko extend karti hain. Inka ek `render()` method hota hai jo JSX return karta hai. State aur lifecycle ko handle karne ke liye inka apna alag tareeka hota hai (`this.state`, `componentDidMount`).

**Syntax:**

```jsx
import React from 'react';

class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}
```

-----

-----

## **3. Props (Properties)**

Props ka istemaal data ko **parent component se child component tak** bhejne ke liye kiya jaata hai. Yeh components ke beech communication ka mukhya zariya hai.

**1. Data Pass Karna**
Aap props ko HTML attributes ki tarah paas karte hain. Child component inhein ek single `props` object ke roop mein receive karta hai.

**Zaroori Niyam**: Props **read-only** (sirf padhne ke liye) hote hain. Ek child component kabhi bhi apne props ko seedhe nahi badal sakta. Isse "one-way data flow" sunishchit hota hai.

**Code Example:**

```jsx
// Parent Component
function App() {
  return <Greeting name="Aisha" city="Mumbai" />;
}

// Child Component
function Greeting(props) {
  // props object: { name: "Aisha", city: "Mumbai" }
  return <p>Hello, {props.name} from {props.city}!</p>;
}
```

**2. Default Props**
Agar parent component koi prop bhejna bhool jaaye, toh aap child component ke liye ek default value set kar sakte hain.

```jsx
function Greeting(props) {
  return <p>Hello, {props.name}!</p>;
}

Greeting.defaultProps = {
  name: "Guest" // Agar 'name' prop nahi mila, toh 'Guest' istemaal hoga
};
```

**3. PropTypes**
Yeh ek library (`prop-types`) hai jo development ke dauraan type checking karti hai. Yeh sunishchit karti hai ki component ko sahi data type ka prop mil raha hai ya nahi. Agar galat type ka data milta hai, toh console mein ek warning aati hai. Isse debugging aasan ho jaati hai.

```jsx
import PropTypes from 'prop-types';

function Greeting(props) { /* ... */ }

Greeting.propTypes = {
  name: PropTypes.string.isRequired, // 'name' ek string hona chahiye aur zaroori hai
  age: PropTypes.number // 'age' ek number hona chahiye
};
```

-----

-----

## **4. The `children` prop**

`props.children` ek khaas prop hai. Ismein woh saara content hota hai jo aap ek component ke **opening aur closing tag ke beech mein** daalte hain.

**Analogy**: Yeh ek khaali box 📦 jaisa hai. Aap ek `Card` component banate hain aur uske andar kuch bhi daal sakte hain (text, images, doosre components), aur `Card` component `props.children` ka istemaal karke us content ko render kar dega.

**Use Case**: Yeh reusable wrapper components (jaise `Card`, `Modal`, `Layout`) banane ke liye perfect hai.

**Code Example:**

```jsx
// Wrapper Component
function Card(props) {
  return <div className="card">{props.children}</div>;
}

// Istemal Kaise Karein
function App() {
  return (
    <Card>
      {/* Yeh sab kuch props.children ban jaayega */}
      <h1>Welcome</h1>
      <p>This is some content inside a card.</p>
    </Card>
  );
}
```

-----

-----

## **5. Component Composition**

Yeh React ka mool siddhant hai. Iska matlab hai **chhote-chhote, simple components ko milakar bade aur complex components banana**.

Har component ko ek hi kaam karna chahiye aur use acchi tarah karna chahiye (Single Responsibility Principle). Isse aapka code:

  * **Reusable** (dobara istemaal karne laayak)
  * **Maintainable** (sambhaalne mein aasan)
  * **Scalable** (bada karne mein aasan)
    banta hai.

**Example**: Ek `UserProfile` page alag-alag components se milkar ban sakta hai:

```jsx
function UserProfile() {
  return (
    <div>
      <Avatar user={...} />
      <UserInfo user={...} />
      <ContactDetails user={...} />
    </div>
  );
}
```

-----

-----

## **6. Conditional Rendering**

Iska matlab hai **conditions ke aadhar par alag-alag UI render karna**. Jaise, agar user login hai toh "Profile" button dikhao, nahi toh "Login" button dikhao.

Iske kuch aam tareeke hain:

**1. `if/else` Statement**
Aap `return` statement se pehle `if/else` ka istemaal karke decide kar sakte hain ki kaun sa JSX return karna hai.

```jsx
function Greeting({ isLoggedIn }) {
  if (isLoggedIn) {
    return <p>Welcome back!</p>;
  } else {
    return <p>Please log in.</p>;
  }
}
```

**2. Ternary Operator (`? :`)**
Yeh `if/else` ka ek inline shortcut hai. JSX ke andar istemaal karne ke liye yeh bahut accha hai.

```jsx
function Greeting({ isLoggedIn }) {
  return (
    <div>
      {isLoggedIn ? <p>Welcome back!</p> : <p>Please log in.</p>}
    </div>
  );
}
```

**3. Logical `&&` Operator**
Yeh tab istemaal hota hai jab aapko koi cheez sirf tab render karni ho jab condition `true` ho, warna kuch bhi nahi.

```jsx
function Mailbox({ unreadMessages }) {
  return (
    <div>
      {/* Agar unreadMessages > 0 hai, tabhi h2 render hoga */}
      {unreadMessages.length > 0 && 
        <h2>You have {unreadMessages.length} unread messages.</h2>
      }
    </div>
  );
}
```

-----

-----

## **7. Lists & Keys**

Jab aapko data ke ek array se UI elements ki list banani ho (jaise to-do items ya user list), toh aap **`.map()`** method ka istemaal karte hain.

**The `key` Prop**
Jab aap `.map()` se list banate hain, toh har list item ko ek **`key`** prop dena **bahut zaroori** hai.

  * **Yeh Kya Hai**: `key` ek special string attribute hai.
  * **Kyun Zaroori Hai**: React is `key` ka istemaal karke pehchanta hai ki list mein kaun sa item add hua, remove hua, ya reorder hua hai. Isse React UI ko **efficiently update** kar paata hai, jisse performance behtar hoti hai.
  * **Niyam**:
    1.  `key` list ke siblings (bhai-behan) ke beech mein **unique** hona chahiye.
    2.  `key` **stable** hona chahiye (woh render ke beech badalna nahi chahiye). Aam taur par data se aane waali `id` iske liye best hoti hai.

**Dhyaan Dein**: Array ke **`index` ko `key` ke roop mein istemaal karne se bachein**. Yeh tab samasya paida kar sakta hai jab list reorder ya filter hoti hai. Ise sirf tab istemaal karein jab aapke paas koi doosra option na ho.

**Code Example:**

```jsx
function TodoList({ todos }) {
  const listItems = todos.map(todo =>
    // 'todo.id' ek unique aur stable key hai
    <li key={todo.id}>
      {todo.text}
    </li>
  );
  return <ul>{listItems}</ul>;
}
```

-----

-----

## **8. Prop Drilling: Samasya aur Samadhaan**

**Samasya (The Problem)**
**Prop Drilling** woh samasya hai jab aapko props ko ek parent component se ek bahut neeche nested child tak, beech ke kayi aise components se guzarte hue bhejna padta hai jinhein un props ki koi zaroorat nahi hoti. 😥

**Samadhaan (Solutions)**

1.  **Component Composition**: Kai baar aap `props.children` ka istemaal karke is samasya se bach sakte hain. Ismein aap poora component hi "slot" ki tarah paas kar dete hain, data nahi.

2.  **Context API**: Yeh React ka **built-in solution** hai. Aap ek `Provider` banakar data ko ek jagah rakhte hain, aur phir koi bhi child component, chahe woh kitna bhi neeche ho, `useContext` hook ka istemaal karke us data ko seedhe access kar sakta hai, bina props ke. Yeh theme ya user info jaise global data ke liye perfect hai.

3.  **State Management Libraries (jaise Redux, Zustand)**: Badi aur complex applications ke liye, Redux jaisi libraries ek central "store" provide karti hain. Koi bhi component seedhe store se data le sakta hai, jisse prop drilling poori tarah khatm ho jaata hai.

-----


-----

-----

## **1. Component State**

**State Kya Hai?**
State ek plain JavaScript object hai jo ek component ke **private data** ko hold karta hai. Yeh woh data hai jo samay ke saath user ke interaction ya network responses ke kaaran **badal sakta hai**.

Jab bhi kisi component ka state badalta hai, React us component ko automatically **re-render** (UI ko update) kar deta hai.

**Analogy**: State ek component ki apni 'memory' ya 'yaaddasht' 🧠 jaisa hai, jise woh khud control aur update karta hai.

-----

### **Functional Components mein State (Modern Tareeka)**

Functional components mein state ko manage karne ke liye hum **`useState` Hook** ka istemaal karte hain.

  * **`useState(initialValue)`**: Yeh hook do cheezein return karta hai:
    1.  Current state value.
    2.  Ek function jisse us state value ko update kiya jaa sakta hai.

**Syntax:**

```jsx
import React, { useState } from 'react';

function Counter() {
  // Array destructuring ka istemaal
  // 'count' hai state variable, 'setCount' use update karne ka function
  // 0 initial value hai
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Aapne {count} baar click kiya hai.</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

-----

### **Class Components mein State (Puraana Tareeka)**

Class components mein state ko `this.state` object mein rakha jaata hai aur `this.setState()` method se update kiya jaata hai.

  * State ko `constructor` ke andar initialize kiya jaata hai.
  * State ko update karne ke liye hamesha `this.setState()` ka istemaal hota hai.

**Syntax:**

```jsx
import React from 'react';

class Counter extends React.Component {
  constructor(props) {
    super(props);
    // State ko constructor mein initialize kiya
    this.state = {
      count: 0
    };
  }

  render() {
    return (
      <div>
        <p>Aapne {this.state.count} baar click kiya hai.</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Click me
        </button>
      </div>
    );
  }
}
```

-----

-----

## **2. Updating & Managing State (State ko Update Karna)**

**Sunehra Niyam (The Golden Rule)**: **State ko kabhi bhi seedhe (directly) na badlein.** Hamesha `setState` ya `useState` se mile update function ka hi istemaal karein.

  * **Galat Tareeka ❌**: `this.state.count = this.state.count + 1;`
  * **Sahi Tareeka ✅**: `this.setState({ count: this.state.count + 1 });`

**Kyun?**
React state ke object reference ko compare karke pata lagata hai ki use re-render karna hai ya nahi. Agar aap seedhe object ko mutate karenge, toh reference nahi badlega aur React ko lagega ki kuch badla hi nahi, isliye UI update nahi hoga.

-----

### **Pichhle State ke Aadhar par State Update Karna**

Kai baar naya state pichhle state par nirbhar karta hai. Kyunki state updates asynchronous ho sakte hain, isliye hamesha **updater function** ka istemaal karna ek safe tareeka hai.

  * **Functional Components mein**:
    ```jsx
    // prevCount mein hamesha latest state value milegi
    setCount(prevCount => prevCount + 1);
    ```
  * **Class Components mein**:
    ```jsx
    this.setState((prevState) => {
      return { count: prevState.count + 1 };
    });
    ```

-----

### **Objects aur Arrays ko State mein Manage Karna**

Yaad rakhein, objects aur arrays ko bhi seedhe mutate nahi karna hai. Hamesha ek nayi copy banayein.

  * **Objects ke liye**: Spread syntax (`...`) ka istemaal karein.

    ```jsx
    const [user, setUser] = useState({ name: 'Ravi', age: 25 });

    function updateAge() {
      setUser({ ...user, age: 26 }); // 'user' ki copy banayi aur 'age' ko badla
    }
    ```

  * **Arrays ke liye**: Spread syntax ya non-mutating array methods (jaise `.map()`, `.filter()`) ka istemaal karein.

    ```jsx
    const [todos, setTodos] = useState(['Padhai karo']);

    function addTodo() {
      setTodos([...todos, 'Practice karo']); // 'todos' array ki copy banayi aur naya item joda
    }
    ```

-----

-----

## **3. State vs Props**

Yeh React ka sabse zaroori concept hai.

| Feature       | State                                                           | Props                                                         |
| :------------ | :-------------------------------------------------------------- | :------------------------------------------------------------ |
| **Kaam**      | Component ke **private data** ko manage karta hai.              | Parent se child tak data **pass karta hai**.                  |
| **Badlaav**   | **Badal sakta hai** (component ke andar se `setState` se).      | **Nahi badal sakta** (Read-only). Child ise nahi badal sakta. |
| **Maalik**    | Component **khud iska maalik hai**.                             | Iska maalik parent component hota hai.                        |
| **Data Flow** | Ek hi component ke andar rehta hai.                             | Parent se Child (upar se neeche) behta hai.                   |
| **Analogy**   | Ek insaan ki **umar (age)**, jo waqt ke saath khud badalti hai. | Ek insaan ka **naam**, jo use uske parents se milta hai.      |

-----

-----

## **4. Memoization with `React.memo`**

**Samasya**: By default, jab bhi ek parent component re-render hota hai, uske saare child components bhi re-render ho jaate hain, bhale hi unke props na badle hon. Isse bewajah ke re-renders hote hain aur performance par asar padta hai.

**Samadhaan**: `React.memo`

  * **Yeh Kya Hai**: `React.memo` ek **Higher-Order Component (HOC)** hai. Aasan shabdon mein, yeh ek function hai jo aapke component ko leta hai aur ek optimized version return karta hai.

  * **Kaam Kya Karta Hai**: Yeh aapke functional component ko wrap karta hai. Phir yeh us component ke props ka **shallow comparison** karta hai. Agar props pichhle render se same hain, toh React re-render ko **skip kar dega** aur pichhli baar ka render kiya hua result hi dobara istemaal kar lega.

**Memoization** ka matlab hi hai "kisi calculation ke result ko yaad rakhna taaki use dobara na karna pade."

**Ise Kab Istemal Karein?**
Jab aapke paas ek component ho jo aam taur par same props ke saath baar-baar render hota hai, tab iska istemaal karna faydemand hota hai.

**Code Example:**

```jsx
import React from 'react';

// Yeh ek "dumb" component hai jo sirf name display karta hai.
function Greeting({ name }) {
  console.log(`Greeting for ${name} is rendering!`);
  return <h1>Hello, {name}!</h1>;
}

// Humne Greeting component ko React.memo se wrap kar diya.
export default React.memo(Greeting);
```

Ab, agar is `Greeting` component ka parent re-render hota hai, lekin `name` prop ki value same rehti hai, toh console mein "Greeting for ... is rendering\!" message print nahi hoga, kyunki React re-render ko skip kar dega.

-----



-----

## **1. Handling Events in React (Events ko Handle Karna)**

React mein events handle karna lagbhag plain HTML jaisa hi hai, lekin kuch zaroori farkon ke saath.

**Mukhya Fark (Key Differences):**

1.  **`camelCase` Naming**: React events ke naam `camelCase` mein hote hain.

      * HTML: `onclick`
      * React: `onClick`

2.  **Function Pass Karna**: HTML mein aap string (`"myFunction()"`) paas karte the, lekin React mein aap seedhe ek **function** paas karte hain.

      * HTML: `<button onclick="showAlert()">`
      * React: `<button onClick={showAlert}>`

3.  **Default Behavior Rokna**: Default browser behavior (jaise form submit hone par page reload hona) ko rokne ke liye aap `return false;` nahi kar sakte. Aapko **`event.preventDefault()`** ko explicitly call karna padta hai.

Jab koi event hota hai, toh aapke handler function ko ek **SyntheticEvent** object milta hai. Yeh React ka banaya gaya ek cross-browser wrapper hai jo sabhi browsers mein event ko ek jaisa banata hai.

-----

-----

## **2. Event Binding (`onClick`, `onChange`, etc.)**

Event binding ka matlab hai ek event handler function ko ek JSX element se jodna.

**Handler Function ko Define Karne ke Tareeke:**

1.  **Inline Arrow Function**: Chhote-mote kaam ke liye seedhe JSX ke andar hi function likh dein.

    ```jsx
    <button onClick={() => console.log('Button clicked!')}>Click Me</button>
    ```

2.  **Alag se Function Banana (Recommended)**: Bade logic ke liye, component ke andar ek alag function banayein aur uska reference paas karein. Isse JSX saaf-suthra rehta hai.

**Code Example:**

```jsx
import React, { useState } from 'react';

function MyForm() {
  const [name, setName] = useState('');

  // 1. Alag se banaya gaya handler function
  function handleClick() {
    alert(`Hello, ${name}!`);
  }

  // 2. Ek aur handler function (jo event object ka istemaal kar raha hai)
  function handleInputChange(event) {
    setName(event.target.value);
  }

  return (
    <div>
      <input 
        type="text" 
        value={name} 
        onChange={handleInputChange} // onChange event
      />
      <button onClick={handleClick}> {/* onClick event */}
        Greet
      </button>
    </div>
  );
}
```

-----

-----

## **3. Specific Events (Kuch Khaas Events)**

-----

### **`onClickCapture`**

Event propagation ke do phases hote hain: **Capturing** aur **Bubbling**.

  * **Capturing Phase**: Event sabse bahar waale element (window) se shuru hokar, neeche target element tak jaata hai. (Upar se neeche 👇).
  * **Bubbling Phase (Default)**: Event target element se shuru hokar, upar apne parents ke zariye window tak jaata hai. (Neeche se upar 👆).

`onClick` bubbling phase mein chalta hai. Lekin **`onClickCapture`** capturing phase mein chalta hai. Iska matlab hai ki parent ka `onClickCapture` hamesha child ke `onClick` se **pehle** chalega.

**Use Case**: Yeh ek advanced feature hai. Iska istemaal aam taur par tab hota hai jab aapko kisi event ko uske target tak pahunchne se pehle hi "pakadna" ho.

-----

### **`onMouseDown`**

  * **Kab Chalta Hai**: Yeh tab chalta hai jab user kisi element par mouse ka button **dabata (presses down)** hai.
  * **`onClick` se Fark**: `onClick` tab chalta hai jab button daba kar **chhoda (released)** jaata hai. `onMouseDown` sirf dabane par hi chal jaata hai.
  * **Use Case**: Drag-and-drop functionality shuru karne ke liye, ya aise actions ke liye jo button dabate hi shuru ho jaane chahiye.

-----

### **`onDoubleClick`**

  * **Kab Chalta Hai**: Yeh tab chalta hai jab user kisi element par bahut kam samay mein **do baar click** karta hai.
  * **Use Case**: Ek file ya folder ko kholne ke liye (jaise computer ke file explorer mein), ya kisi text ko double click par editable banane ke liye.

-----

### **`onSubmit`**

  * **Kab Chalta Hai**: Yeh event tab chalta hai jab ek **`<form>`** ko submit kiya jaata hai. Form submit ya toh `type="submit"` waale button par click karke hota hai, ya kisi input field mein Enter dabane se.
  * **Zaroori Niyam**: Yeh event hamesha **`<form>`** tag par lagaya jaata hai, submit button par nahi.
  * **`event.preventDefault()`**: Is handler ke andar lagbhag hamesha `event.preventDefault()` ko call karna padta hai taaki browser form submit hone par **page ko reload na kare**.

**Code Example:**

```jsx
function LoginForm() {
  function handleSubmit(event) {
    event.preventDefault(); // Page reload hone se roka
    alert('Form submitted!');
  }

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" />
      <button type="submit">Login</button>
    </form>
  );
}
```

-----

### **`onScroll`**

  * **Kab Chalta Hai**: Yeh tab chalta hai jab user kisi element ke scrollbar ko **scroll** karta hai.
  * **Use Case**:
      * Infinite scrolling (jaise social media feeds mein).
      * "Back to top" button ko dikhana ya chhipana.
      * Scroll par आधारित animations (parallax effect).
  * **Performance Tip**: Yeh event bahut tezi se baar-baar fire hota hai. Isliye, behtar performance ke liye iske handler ko **debounce ya throttle** karna acchi practice maani jaati hai.

-----

### **`onBlur`**

  * **Kab Chalta Hai**: Yeh event tab chalta hai jab koi element **focus kho deta hai (loses focus)**.
  * **Analogy**: Jab aap ek input field ke andar click karte hain, toh woh "focus" mein aa jaata hai. Jab aap uske bahar kahin aur click karte hain, toh woh "blur" ho jaata hai, aur `onBlur` event chalta hai. Iska ulta `onFocus` hota hai.
  * **Use Case**:
      * Form validation ke liye (jaise, user ke email field se bahar nikalte hi check karna ki email valid hai ya nahi).
      * Form data ko auto-save karne ke liye.

-----


-----

-----

## **1. Hooks Introduction & Rules of Hooks (Hooks ka Parichay aur Niyam)**

### **Hooks Kya Hain?**

**Hooks** special JavaScript functions hain jo aapko **functional components ke andar se React ke features (jaise state aur lifecycle) mein "hook" karne (judne)** ki suvidha dete hain.

Inke aane se pehle, state aur lifecycle jaise features sirf Class Components mein hi istemaal ho sakte the. Hooks ne functional components ko utna hi powerful bana diya hai.

### **Hooks ke Niyam (Rules of Hooks)**

React ko theek se kaam karne ke liye aapko Hooks ke do zaroori niyam follow karne honge:

1.  **Hooks ko sirf Top Level par Call Karein**
    Hooks ko hamesha apne component ke **sabse upar** call karein. Unhein kabhi bhi loops, conditions (`if`/`else`), ya nested functions ke andar call na karein.

      * **Kyun?** React renders ke beech Hooks ke call order par nirbhar karta hai. Agar order badal jaata hai, toh React state ko galat component se jod sakta hai, jisse ajeeb bugs aa sakte hain.

2.  **Hooks ko sirf React Functions se Call Karein**
    Hooks ko sirf **React functional components** ya **custom hooks** ke andar se hi call karein. Unhein normal JavaScript functions se call na karein.

-----

-----

## **2. `useState`**

  * **Kaam**: Functional components mein **state** add karne ke liye.
  * **Syntax**: `const [state, setState] = useState(initialValue);`
  * **Yeh Kya Karta Hai**:
      * Yeh ek argument leta hai: `initialValue` (state ki shuruaati value).
      * Yeh ek array return karta hai jismein do cheezein hoti hain:
        1.  **`state`**: Current state ki value.
        2.  **`setState`**: Ek function jiska istemaal state ko update karne ke liye kiya jaata hai. Jab aap is function ko call karte hain, toh component **re-render** hota hai.

**Code Example:**

```jsx
import React, { useState } from 'react';

function Counter() {
  // 0 initial state hai.
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      {/* setCount function ko call karke state update kiya */}
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

-----

-----

## **3. `useEffect` (Side Effects ke liye)**

  * **Kaam**: Functional components mein **side effects** perform karne ke liye.
  * **Side Effects Kya Hain?** Woh koi bhi kaam jo component ke rendering flow se alag ho. Jaise:
      * API se data fetch karna 🌐
      * Timers ya subscriptions set up karna ⏰
      * DOM ko manually badalna

**Syntax**:

```jsx
useEffect(() => {
  // Side effect ka code yahan aayega
  
  return () => {
    // Yeh cleanup function hai (optional)
  };
}, [dependencyArray]); // Dependency Array
```

**Dependency Array ka Matlab**:

  * **`[ ]` (Khaali Array)**: Effect sirf **ek baar** chalta hai, pehle render ke baad (bilkul `componentDidMount` jaisa).
  * **`[value1, value2]`**: Effect pehli baar chalta hai, aur phir jab bhi `value1` ya `value2` mein se koi bhi badalta hai (bilkul `componentDidUpdate` jaisa).
  * **Koi Array Nahi**: Effect har render ke baad chalta hai (iska istemaal kam karein).

**Cleanup Function**:
`useEffect` se return kiya gaya function **cleanup** ka kaam karta hai. Yeh component ke DOM se hatne se pehle chalta hai (bilkul `componentWillUnmount` jaisa). Iska istemaal timers ya subscriptions ko hatane ke liye hota hai taaki memory leak na ho.

-----

-----

## **4. `useRef`**

  * **Kaam**: Yeh ek `ref` object return karta hai jiska `.current` property hota hai.

  * **Iske Do Mukhya Istemal Hain**:

    1.  **DOM Elements ko Access Karna**: Aap ek `ref` ko kisi JSX element se attach kar sakte hain taaki aap us DOM node ko seedhe access kar sakein.

          * **Use Case**: Ek input field ko programmatically focus karna.

    2.  **Ek Mutable Value ko Store Karna jo Re-render na Kare**: State se alag, `ref.current` ko update karne se component **re-render nahi hota**.

          * **Use Case**: Timer IDs ya pichhle state jaisi values ko store karne ke liye jinke badalne par UI update ki zaroorat nahi hai.

**Code Example (DOM Access):**

```jsx
import React, { useRef } from 'react';

function TextInputWithFocusButton() {
  const inputEl = useRef(null);
  
  const onButtonClick = () => {
    // `current` se asli input element milta hai
    inputEl.current.focus();
  };

  return (
    <>
      <input ref={inputEl} type="text" />
      <button onClick={onButtonClick}>Focus the input</button>
    </>
  );
}
```

-----

-----

## **5. `useLayoutEffect`**

  * **Kaam**: Iska kaam aur syntax bilkul `useEffect` jaisa hi hai.

  * **Mukhya Fark**: Yeh kab chalta hai.

      * `useEffect`: Browser ke screen par paint karne ke **baad** chalta hai (asynchronously).
      * `useLayoutEffect`: DOM updates ke theek **baad**, lekin browser ke screen par paint karne se **pehle** chalta hai (synchronously).

  * **Ise Kab Istemal Karein?**
    Ise sirf tab istemaal karein jab aapko DOM se kuch naapna (measure karna) ho aur phir uske aadhar par turant DOM ko dobara update karna ho, bina user ko koi jhalak (flicker) dikhe.
    **Warning**: 99% cases mein, aapko `useEffect` hi istemaal karna chahiye kyunki `useLayoutEffect` rendering ko block kar sakta hai.

-----

-----

## **6. `useMemo`**

  * **Kaam**: Ek **expensive calculation ke result ko yaad (memoize) karne ke liye**.
  * **Yeh Kya Karta Hai**: `useMemo` ek function aur ek dependency array leta hai. Yeh us function ko sirf tabhi dobara chalayega jab uski koi dependency badlegi. Warna, yeh pichhli baar ka calculate kiya hua result hi return kar dega.

**Analogy**: Ek mushkil math ke sawaal ko baar-baar solve karne ke bajaye, aap use ek baar solve karke jawab ko likh lete hain. Aap jawab ko tabhi dobara calculate karte hain jab sawaal ke numbers badalte hain. ✏️

**Use Case**: Performance ko behtar banane ke liye, taaki har render par bhaari-bharkam calculations dobara na hon.

```jsx
const expensiveResult = useMemo(() => {
  return calculateSomethingHeavy(a, b);
}, [a, b]); // Yeh tabhi dobara calculate hoga jab 'a' ya 'b' badlega
```

-----

-----

## **7. `useCallback`**

  * **Kaam**: Ek poore **function ko hi yaad (memoize) karne ke liye**.

  * **Yeh Kya Karta Hai**: `useCallback` ek function ka "yaad kiya hua" version return karta hai. Woh function dobara sirf tabhi create hota hai jab uski koi dependency badalti hai.

  * **Kyun Zaroori Hai?**
    Jab aap ek function ko prop ke roop mein `React.memo` se wrap kiye gaye child component ko bhejte hain, toh `useCallback` zaroori ho jaata hai. Iske bina, parent ke har render par function dobara banega (naya reference), jisse child component bewajah re-render ho jaayega. `useCallback` isse rokta hai.

**`useMemo` vs `useCallback`**:

  * `useMemo` ek **value** ko memoize karta hai.
  * `useCallback` ek **function** ko memoize karta hai.
  * `useCallback(fn, deps)` barabar hai `useMemo(() => fn, deps)`.

<!-- end list -->

```jsx
const memoizedCallback = useCallback(() => {
  doSomething(a, b);
}, [a, b]); // Yeh function tabhi dobara create hoga jab 'a' ya 'b' badlega
```

-----

-----

## **8. `useContext`**

  * **Kaam**: React Context se value ko **consume (read) karne ke liye**, bina prop drilling ke.
  * **Prop Drilling Kya Tha?**: Data ko kayi levels tak props ke zariye neeche bhejna.
  * **Kaise Istemal Karein**:
    1.  `React.createContext()` se ek context banayein.
    2.  Apne component tree ko us context ke `<Provider>` se wrap karein aur ek `value` paas karein.
    3.  Kisi bhi child component ke andar, `useContext(MyContext)` ko call karke us value ko seedhe access karein.

**Code Example**:

```jsx
// 1. Context banaya
const ThemeContext = React.createContext('light');

function App() {
  // 2. Provider se value di
  return (
    <ThemeContext.Provider value="dark">
      <Toolbar />
    </ThemeContext.Provider>
  );
}

function Toolbar() {
  // 3. useContext se value ko consume kiya
  const theme = useContext(ThemeContext);
  return <div>Current theme: {theme}</div>; // Output: Current theme: dark
}
```

-----



-----

## **1. Context API (Provider & Consumer)**

**Context API** React ka ek built-in feature hai jiska istemaal "global" state ko component tree mein neeche tak share karne ke liye kiya jaata hai, bina har level par props paas kiye.

Iske 3 mukhya hisse hain:

1.  **`React.createContext()`**:
    Yeh function ek `Context` object banata hai. Aap ise ek default value de sakte hain.

    ```javascript
    const ThemeContext = React.createContext('light'); // 'light' default value hai
    ```

2.  **`Context.Provider`**:
    Yeh ek component hai jisse aap apne component tree ke uss hisse ko wrap karte hain jahan aap data available karana chahte hain. Iske `value` prop mein aap woh data paas karte hain jise share karna hai.
    **Analogy**: Yeh ek Wi-Fi router 📡 jaisa hai, jo apne range ke andar sabhi components ko data (internet) broadcast karta hai.

    ```jsx
    <ThemeContext.Provider value="dark">
      <App />
    </ThemeContext.Provider>
    ```

3.  **Context ko Consume Karna**:
    Data ko consume karne ke do tareeke hain:

      * **`useContext` Hook (Modern aur Aasan Tareeka)**: Functional components ke andar context ki value ko padhne ka yeh sabse aasan tareeka hai.
        ```jsx
        import { useContext } from 'react';

        function MyComponent() {
          const theme = useContext(ThemeContext); // 'dark' value mil jaayegi
          return <div className={theme}>...</div>;
        }
        ```
      * **`Context.Consumer` (Puraana Tareeka)**: Class components ke andar istemaal hota hai.

-----

-----

## **2. Context se Prop Drilling se Bachna**

**Samasya (Prop Drilling)**: Data ko top-level component se ek bahut neeche nested component tak, beech ke kayi aise components se guzarte hue bhejna jinhein us data ki koi zaroorat nahi hoti.

**Samadhaan (Context API)**: Context data ke liye ek direct tunnel 🚇 bana deta hai.

**Example**:
Soch lijiye `App` component ke paas user ki info hai aur use sabse neeche waale `Avatar` component ko chahiye.

  * **Prop Drilling ke Saath**:
    `App` -\> `Layout (user prop paas kiya)` -\> `Header (user prop paas kiya)` -\> `Avatar (user prop istemaal kiya)`
    Yahan `Layout` aur `Header` ko `user` prop ki zaroorat nahi thi, phir bhi unhein use paas karna pada.

  * **Context API ke Saath**:

    1.  `UserContext` banayein.
    2.  `App` component ko `<UserContext.Provider value={user}>` se wrap karein.
    3.  Ab `Avatar` component ke andar, seedhe `useContext` ka istemaal karke `user` data ko access kar lein. Beech ke components ko kuch bhi paas karne ki zaroorat nahi.

    <!-- end list -->

    ```jsx
    // Avatar.js
    import { useContext } from 'react';
    import UserContext from './UserContext';

    function Avatar() {
      const user = useContext(UserContext);
      return <img src={user.avatarUrl} alt={user.name} />;
    }
    ```

-----

-----

## **3. Redux (Badi Apps ke liye State Container)**

**Redux** ek third-party library hai jiska istemaal JavaScript applications (khaaskar React) ke poore **application state** ko ek jagah, ek **central "store"** mein manage karne ke liye kiya jaata hai.

**Ise Kyun Istemal Karein?**
Yeh badi aur complex applications ke liye banaya gaya hai jahan state kayi components ke beech share hota hai aur ajeeb tareekon se badalta hai. Redux state changes ko **predictable (anumanit)** aur aasaani se **debug** karne laayak banata hai.

**Analogy**: Redux aapki application ke data ka ek **central bank ya ledger 🏦** jaisa hai. Saare state "transactions" iske zariye hi hote hain aur unka poora record rakha jaata hai.

-----

-----

## **4. Redux ke Basics (actions, reducers, store)**

Redux ek strict "one-way data flow" par kaam karta hai.

1.  **Store**:

      * Yeh **"single source of truth"** hai. Yeh ek bada JavaScript object hai jo aapki poori application ka state rakhta hai.

2.  **Action**:

      * Yeh ek plain JavaScript object hai jo batata hai ki **"kya hua"**. State ko badalne ka iraada (intent) actions ke zariye hi bheja jaata hai.
      * Har action mein ek `type` property (jaise `'todos/todoAdded'`) honi zaroori hai aur saath mein `payload` (data) bhi ho sakta hai.
      * State badalne ke liye aap ek action **dispatch** karte hain.

3.  **Reducer**:

      * Yeh ek **pure function** hai jo batata hai ki ek action ke jawaab mein **state kaise badlega**.
      * Ek reducer do cheezein leta hai: `(previousState, action)`. Yeh action ke `type` ko dekhta hai aur uske aadhar par ek **naya state object** return karta hai.
      * **Sunehra Niyam**: Reducer kabhi bhi original state ko **mutate (seedhe badalna) nahi karta**.

**Flow**: `UI event -> Action dispatch -> Reducer chalta hai -> Naya State Store mein update hota hai -> UI naye state ke hisaab se re-render hota hai.`

-----

-----

## **5. React ke Saath Redux ka Istemal**

React aur Redux ko aapas mein jodne ke liye `react-redux` library ka istemaal kiya jaata hai.

  * **`<Provider store={store}>`**:
    Yeh component `react-redux` se aata hai. Aap apni poori `<App />` ko isse wrap kar dete hain. Isse aapke Redux store poori application mein available ho jaata hai.

  * **`useSelector()` Hook**:
    Is hook ka istemaal component ke andar Redux store se **data padhne (select karne)** ke liye kiya jaata hai.

    ```jsx
    const count = useSelector(state => state.counter.value);
    ```

  * **`useDispatch()` Hook**:
    Yeh hook aapko store ka `dispatch` function deta hai. Iska istemaal aap component se **actions dispatch karne** (state badalne ka signal bhejne) ke liye karte hain.

    ```jsx
    
    const dispatch = useDispatch();
    // ...
    <button onClick={() => dispatch(increment())}>Increment</button>
    ```

-----

-----

## **6. Redux Toolkit (Modern Tareeka)**

**Samasya**: "Vanilla" (puraana) Redux likhne mein bahut zyada **boilerplate code** (faaltu code) lagta tha. Action types, action creators, reducers, sab kuch manually likhna padta tha.

**Samadhaan**: **Redux Toolkit (RTK)**

  * **Yeh Kya Hai**: RTK Redux likhne ka **official aur recommended tareeka** hai. Yeh ek library hai jo Redux ke zyadatar kaamon ko bahut aasan bana deti hai.
  * **Mukhya Features**:
    1.  **`configureStore()`**: Store setup ko aasan banata hai aur Redux DevTools ko automatically configure kar deta hai.
    2.  **`createSlice()`**: Yeh RTK ka sabse powerful feature hai. Aap ek "slice" of state ke liye reducers define karte hain, aur yeh uske liye **action creators aur action types apne aap generate kar deta hai\!**
    3.  **Immer Library**: `createSlice` parde ke peeche "Immer" naam ki library ka istemaal karta hai. Isse aap reducers ke andar state ko seedhe mutate karne jaisa code likh sakte hain (jaise `state.value++`), aur Immer use automatically immutable tareeke se handle kar lega.

**Nishkarsh**: Naye Redux projects ke liye hamesha **Redux Toolkit** ka hi istemaal karna chahiye. Yeh code ko kam karta hai, aam galtiyon se bachata hai, aur Redux ko istemaal karna bahut aasan bana deta hai. ✨

-----

**Zaroori Soochana**: Yeh lifecycle methods sirf **Class Components** mein istemaal hote hain. Modern **Functional Components** mein, in sabhi ka kaam `useEffect` Hook se kiya jaata hai.

-----

-----

## **Lifecycle Methods ka Parichay**

Lifecycle methods class component ke andar ke special functions hote hain jo component ki "zindagi" ke alag-alag stages par **apne aap (automatically)** chalte hain.

Yeh aapko mauka dete hain ki aap specific samay par specific kaam kar sakein, jaise component ke screen par aane par data fetch karna ya component ke hatne se pehle kuch saaf-safai karna.

**Analogy**: Yeh ek play (natak) 🎭 ke stages jaisa hai. `constructor` parde ke peeche taiyari hai, `componentDidMount` parde ka khulna hai, `componentDidUpdate` scene mein badlav hai, aur `componentWillUnmount` parde ka girna hai.

-----

-----

## **1. `constructor(props)`**

  * **Kab Chalta Hai**: Yeh component ke banne (create hone) aur screen par dikhne (mount hone) se bhi **pehla** method hai jo chalta hai. Yeh poori lifecycle mein sirf **ek baar** chalta hai.

  * **Iska Kya Kaam Hai**:

    1.  **State ko Initialize Karna**: `this.state` ko shuruaati (initial) value dene ke liye yeh sabse sahi jagah hai.
    2.  **Event Handlers ko Bind Karna**: `this` keyword ko aapke custom methods (event handlers) ke saath bind karna.

  * **Zaroori Niyam**:

      * Constructor ke andar sabse pehli line hamesha `super(props);` honi chahiye. Iske bina `this.props` kaam nahi karega.
      * Iske andar side effects (jaise API calls) nahi karne chahiye.

**Code Example**:

```jsx
import React from 'react';

class MyClock extends React.Component {
  constructor(props) {
    super(props); // Sabse pehle ise call karna zaroori hai
    
    // 1. State ko initialize kiya
    this.state = { date: new Date() };
    
    // 2. Method ko bind kiya (ab arrow functions se iski zaroorat kam padti hai)
    // this.tick = this.tick.bind(this); 
  }

  render() { /* ... */ }
}
```

-----

-----

## **2. `componentDidMount()`**

  * **Kab Chalta Hai**: Yeh method component ke **screen par dikhne (render hone) ke theek baad** chalta hai. Yeh bhi poori lifecycle mein sirf **ek baar** hi chalta hai.

  * **Iska Kya Kaam Hai**:
    Yeh **side effects** karne ke liye sabse behtareen jagah hai. Jaise:

    1.  **Data Fetching**: Server se data fetch karne ke liye API calls (`fetch` ya `axios`) yahan ki jaati hain.
    2.  **Subscriptions Set Up Karna**: Timers (`setInterval`) ya event listeners (`window.addEventListener`) yahan shuru kiye jaate hain.
    3.  **DOM Manipulation**: Agar DOM ko seedhe access karne ki zaroorat pade (jo kam hi hota hai).

  * **Functional Component mein Iske Jaisa**: `useEffect(() => {}, [])` (khaali dependency array ke saath).

**Code Example**:

```jsx
class UserProfile extends React.Component {
  state = { user: null };

  componentDidMount() {
    console.log('Component screen par aa gaya hai!');
    // API call karke data fetch kiya
    fetch(`https://api.example.com/users/${this.props.userId}`)
      .then(response => response.json())
      .then(data => this.setState({ user: data }));
  }

  render() {
    if (!this.state.user) {
      return <div>Loading...</div>;
    }
    return <h1>Hello, {this.state.user.name}</h1>;
  }
}
```

-----

-----

## **3. `componentDidUpdate(prevProps, prevState)`**

  * **Kab Chalta Hai**: Yeh method har **re-render ke baad** chalta hai, jab bhi component ka `state` ya `props` badalta hai. Yeh pehli baar (initial) render par **nahi** chalta.

  * **Iska Kya Kaam Hai**:
    Iska istemaal `props` ya `state` ke badlaav par side effects karne ke liye hota hai. Jaise, agar user ID badal gayi hai, toh naye user ka data fetch karna.

  * **Sabse Zaroori Niyam**:
    Iske andar `setState` ko hamesha ek **condition (`if`) ke andar hi call karein**. Agar aap bina condition ke `setState` call karenge, toh component baar-baar re-render hota rahega aur ek **infinite loop** ban jaayega\! 🔥

  * **Functional Component mein Iske Jaisa**: `useEffect(() => {}, [dependency])`.

**Code Example**:

```jsx
componentDidUpdate(prevProps, prevState) {
  console.log('Component update ho gaya hai!');
  // Hamesha condition ke andar check karein
  if (this.props.userId !== prevProps.userId) {
    // Agar userId prop badla hai, tabhi nayi API call karein
    this.fetchData(this.props.userId);
  }
}
```

-----

-----

## **4. `componentWillUnmount()`**

  * **Kab Chalta Hai**: Yeh method tab chalta hai jab ek component **DOM se hatne (unmount) waala hota hai**. Yeh lifecycle ka aakhri method hai.

  * **Iska Kya Kaam Hai**:
    Iska mukhya kaam **cleanup (saaf-safai)** karna hai taaki memory leaks na hon.

    1.  **Timers ko Clear Karna**: `setInterval` se banaye gaye timers ko `clearInterval()` se hatana.
    2.  **Event Listeners ko Hatana**: `addEventListener` se banaye gaye listeners ko `removeEventListener()` se hatana.
    3.  **Subscriptions ko Cancel Karna**: Kisi bhi data source se ki gayi subscription ko band karna.

  * **Functional Component mein Iske Jaisa**: `useEffect` se return kiya gaya cleanup function.

**Code Example**:

```jsx
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = { date: new Date() };
  }

  componentDidMount() {
    // Timer shuru kiya
    this.timerID = setInterval(() => this.tick(), 1000);
  }

  componentWillUnmount() {
    console.log('Component hatne waala hai! Timer saaf kar raha hoon.');
    // Component ke hatne se pehle timer ko saaf kiya
    clearInterval(this.timerID);
  }

  tick() {
    this.setState({ date: new Date() });
  }

  render() {
    return <div>{this.state.date.toLocaleTimeString()}</div>;
  }
}
```

-----



-----

-----

### **Samasya: React mein Errors**

By default, agar aapke kisi bhi component mein JavaScript error aa jaata hai, toh poori React app **crash ho jaati hai** aur user ko ek safed screen dikhti hai. Yeh ek bahut hi kharaab user experience hai. Isse bachne ke liye React ne Error Boundaries ka concept diya hai.

-----

## **1. Error Boundaries**

**Error Boundaries Kya Hain?**
Error Boundaries khaas React components hote hain jo apne neeche ke poore **child component tree mein hone waale JavaScript errors ko pakadte (catch karte) hain**.

Jab yeh kisi error ko pakadte hain, toh yeh:

1.  Error ko log kar sakte hain.
2.  Crashed component ki jagah ek **fallback UI** (jaise "Something went wrong" message) dikhaate hain.

**Analogy**: Yeh aapke ghar ke **fuse box (MCB)** Fuse box for electricity jaisa hai. Agar ek kamre (child component) mein short circuit (error) hota hai, toh poora ghar band hone ke bajaye sirf us kamre ka fuse udd jaata hai (error boundary error ko pakad leti hai), aur baaki ghar chalta rehta hai.

**Error Boundary Kaise Banayein?**
Ek **class component** tab Error Boundary banta hai jab woh in dono mein se kam se kam ek lifecycle method ko define karta hai:

  * `static getDerivedStateFromError()`
  * `componentDidCatch()`

**Zaroori Niyam**: Error Boundaries in jagahon par errors **nahi** pakadti:

  * Event Handlers (iske liye `try...catch` istemaal karein)
  * Asynchronous Code (jaise `setTimeout` ya API calls)
  * Server-Side Rendering
  * Khud Error Boundary component ke andar aane waale errors

-----

-----

## **2. `getDerivedStateFromError(error)`**

  * **Yeh Kya Hai**: Yeh ek **static** lifecycle method hai. Static hone ka matlab hai ki iske andar `this` keyword ka access nahi hota.
  * **Kab Chalta Hai**: Yeh "render phase" ke dauraan chalta hai, jab neeche ke kisi child component mein error aata hai.
  * **Kaam Kya Hai**: Iska ek hi kaam hai: **state ko update karke ek fallback UI dikhana**.
    Yeh ek object return karta hai jisse state update hota hai. Aap iske andar koi side effect (jaise API call) nahi kar sakte.

**Analogy**: Yeh "alarm bell" 🔔 jaisa hai jo bajkar component ko batata hai, "Kuch gadbad ho gayi hai, emergency mode mein switch ho jao\!"

-----

-----

## **3. `componentDidCatch(error, errorInfo)`**

  * **Yeh Kya Hai**: Yeh ek normal instance method hai (static nahi).
  * **Kab Chalta Hai**: Yeh "commit phase" ke dauraan chalta hai, error aane ke baad aur fallback UI ke render hone ke baad.
  * **Kaam Kya Hai**: Iska mukhya kaam **side effects** karna hai. Sabse aam side effect hai **error ko log karna**. Aap yahan se error aur uski details ko Sentry ya LogRocket jaisi error reporting service par bhej sakte hain.
      * `error`: Woh error jo throw hua tha.
      * `errorInfo`: Ek object jismein `componentStack` hota hai, jo batata hai ki error kis component mein aaya.

**Analogy**: Yeh "report banane" 📝 ka step hai. Alarm (`getDerivedStateFromError`) baj chuka hai, emergency UI dikh raha hai, aur ab yeh method poori ghatna ki detail report banakar authorities (logging service) ko bhej raha hai.

-----

### **Error Boundary ka Poora Code Example**

```jsx
import React from 'react';

class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  // Step 1: getDerivedStateFromError se state update karke fallback UI dikhao
  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  // Step 2: componentDidCatch se error ko log karo
  componentDidCatch(error, errorInfo) {
    // Aap yahan error ko kisi error reporting service par bhej sakte hain
    console.error("Uncaught error:", error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      // Fallback UI
      return <h1>Oops! Something went wrong.</h1>;
    }

    // Agar koi error nahi hai, toh children ko render karo
    return this.props.children; 
  }
}

// Ise Aise Istemal Karein:
// <ErrorBoundary>
//   <MyRiskyComponent />
// </ErrorBoundary>
```

-----

-----

## **4. `shouldComponentUpdate(nextProps, nextState)`**

  * **Kaam**: Yeh ek **performance optimization** ke liye istemaal hone waala lifecycle method hai.
  * **Kab Chalta Hai**: Yeh har re-render se **pehle** chalta hai, jab naye `props` ya `state` milte hain. Yeh `render()` se bhi pehle chalta hai.
  * **Yeh Kya Karta Hai**: Yeh aapko React ko yeh batane ka mauka deta hai ki kya component ko re-render karne ki zaroorat hai ya nahi.
      * By default, yeh hamesha `true` return karta hai, jisse component hamesha re-render hota hai.
      * Agar aap is method ke andar `false` return kar dete hain, toh React us update ke liye **re-render ko skip kar dega**.

**Analogy**: Yeh ek club ke bahar khada bouncer 💂 jaisa hai. Kisi ko andar aane (re-render hone) se pehle, woh check karta hai ki kya uski zaroorat hai ya nahi. Agar koi zaroorat nahi hai, toh woh use bahar hi rok deta hai, jisse club ke andar bheed (performance issue) nahi hoti.

**Modern Context aur Zaroori Salah**:

  * Is method ko manually likhna mushkil aur error-prone ho sakta hai.
  * Zyadaatar cases mein, iski jagah aapko **`React.PureComponent`** ka istemaal karna chahiye. `PureComponent` yeh method aapke liye aam taur par implement kar deta hai (props aur state ka shallow comparison karke).
  * **Functional Components** mein yahi kaam **`React.memo`** HOC se kiya jaata hai.

Isliye, aajkal aapko yeh method haath se likhne ki zaroorat bahut kam padegi.

-----


-----

-----

## **1. `react-router-dom` ka Parichay**

**`react-router-dom`** React applications mein routing handle karne ke liye sabse popular **third-party library** hai.

**Routing Kya Hai?**
Single Page Applications (SPAs) mein, poora page kabhi reload nahi hota. Routing ek aisa tareeka hai jisse hum alag-alag URLs (jaise `/home`, `/about`) ke liye alag-alag components dikha sakte hain, bina page ko refresh kiye.

**Analogy**: React Router aapki app ka **Traffic Controller** 🚦 hai. Yeh URL ko dekhta hai aur user ko sahi component (page) tak pahunchata hai.

-----

-----

## **2. Routers ke Prakaar (Types of Routers)**

Apni application mein routing shuru karne ke liye, aapko apni poori app ko inmein se kisi ek router component se wrap karna padta hai.

1.  **`<BrowserRouter>` (Sabse Aam)**

      * **Kaise Kaam Karta Hai**: Yeh HTML5 History API ka istemaal karke URL ko manage karta hai.
      * **URL Kaisa Dikhta Hai**: Bilkul normal website jaisa, saaf-suthra URL (jaise `www.example.com/about`).
      * **Kab Istemal Karein**: Yeh **recommended tareeka** hai. Iska istemaal tab karein jab aapke paas ek server ho jo dynamic requests ko handle kar sake.

2.  **`<HashRouter>`**

      * **Kaise Kaam Karta Hai**: Yeh URL ke **hash (`#`)** hisse ka istemaal karke routing manage karta hai.
      * **URL Kaisa Dikhta Hai**: URL mein ek `#` hota hai (jaise `www.example.com/#/about`).
      * **Kab Istemal Karein**: Jab aap ek static website host kar rahe hon (jaise GitHub Pages par) jahan server configuration aapke control mein na ho.

3.  **`<MemoryRouter>`**

      * **Kaise Kaam Karta Hai**: Yeh URL history ko browser ke address bar mein nahi, balki memory mein rakhta hai.
      * **Kab Istemal Karein**: Mukhya roop se **testing** ke dauraan (Jest ke saath) ya non-browser environments (jaise React Native) mein.

-----

-----

## **3. Navigation & Routing (Routes Define Karna)**

Routing setup karne ke liye `react-router-dom` (version 6) ke do mukhya components hain:

  * **`<Routes>`**: Yeh aapke saare individual `<Route>` components ke liye ek container ka kaam karta hai.
  * **`<Route>`**: Yeh asli mapping ka kaam karta hai. Iske do zaroori props hain:
      * **`path`**: Woh URL path jise aap match karna chahte hain (jaise `"/about"`).
      * **`element`**: Woh component jo path match hone par dikhana hai (jaise `<AboutPage />`).

**Code Example (`App.js` mein):**

```jsx
import { Routes, Route } from 'react-router-dom';
import HomePage from './pages/Home';
import AboutPage from './pages/About';

function App() {
  return (
    <Routes>
      <Route path="/" element={<HomePage />} />
      <Route path="/about" element={<AboutPage />} />
    </Routes>
  );
}
```

-----

-----

## **4. `Link` & `NavLink`**

**Samasya**: Agar aap normal `<a>` tag (`<a href="/about">`) ka istemaal karenge, toh woh **poora page reload kar dega**, jo ek SPA ka mool siddhant tod deta hai.

**Samadhaan**:

  * **`<Link>` Component**:
    Yeh `react-router-dom` dwara diya gaya ek component hai. Yeh browser mein ek `<a>` tag hi banata hai, lekin jab ispar click hota hai, toh yeh page ko reload karne ke bajaye, sirf URL ko programmatically badal deta hai.

    ```jsx
    import { Link } from 'react-router-dom';

    <Link to="/contact">Contact Us</Link>
    ```

  * **`<NavLink>` Component**:
    Yeh `<Link>` ka ek special version hai jise yeh pata hota hai ki woh **"active"** hai ya nahi. Jab iska `to` prop current URL se match karta hai, toh yeh apne aap us `<a>` tag par ek `active` class jod deta hai.

      * **Use Case**: Navigation bar banane ke liye perfect hai, jahan aap current page ke link ko highlight karna chahte hain.

-----

-----

## **5. Route Parameters (Dynamic Routes)**

Kai baar aapko dynamic URLs ki zaroorat padti hai, jaise har user ke liye ek alag profile page (`/users/1`, `/users/2`, etc.). Iske liye Route Parameters ka istemaal hota hai.

**Kaise Banayein**:
Apne `<Route>` ke `path` mein, dynamic hisse ko **colon (`:`)** se mark karein.

```jsx
<Route path="/users/:userId" element={<UserProfile />} />
```

Yahan `:userId` ek parameter hai. Yeh `/users/123` ya `/users/ravi` jaise URLs ko match karega.

**Kaise Access Karein**:
Component ke andar, `useParams` hook ka istemaal karein.

```jsx
import { useParams } from 'react-router-dom';

function UserProfile() {
  const params = useParams(); // params ek object hoga, jaise { userId: "123" }
  
  return <h1>User Profile for ID: {params.userId}</h1>;
}
```

-----

-----

## **6. Nested Routes**

Nested Routes ka matlab hai ek route ke andar doosre routes. Yeh tab bahut upyogi hota hai jab aapko ek common layout (jaise dashboard ka sidebar) ko kayi pages par share karna ho.

**Kaise Kaam Karta Hai**:

1.  Aap parent route ke andar child routes define karte hain.
2.  Parent component ke andar, aap **`<Outlet />`** component ka istemaal karte hain. `<Outlet />` ek placeholder jaisa hai jo batata hai ki **child route ka content kahan render hoga**.

**Analogy**: Yeh Russian nesting dolls 🪆 jaisa hai. Ek badi doll (parent layout) ke andar aap chhoti dolls (child pages) rakhte hain.

**Code Example**:

```jsx
// Route Definition
<Route path="/dashboard" element={<Dashboard />}>
  <Route path="profile" element={<Profile />} />
  <Route path="settings" element={<Settings />} />
</Route>

// Parent Component (Dashboard.js)
import { Outlet, Link } from 'react-router-dom';

function Dashboard() {
  return (
    <div>
      <nav> {/* Yeh sidebar hamesha dikhega */}
        <Link to="profile">Profile</Link>
        <Link to="settings">Settings</Link>
      </nav>
      
      <main>
        {/* Child route (Profile ya Settings) yahan render hoga */}
        <Outlet />
      </main>
    </div>
  );
}
```

-----

-----

## **7. React Router Hooks**

Yeh hooks `react-router-dom` dwara diye jaate hain taaki aap functional components ke andar routing se judi cheezein aasaani se kar sakein.

  * **`useNavigate()`**:

      * **Kaam**: Programmatically (code ke zariye) ek route se doosre route par jaane ke liye.
      * **Kaise**: Yeh hook ek `Maps` function return karta hai.
      * **Use Case**: Form submit hone ke baad user ko dashboard par bhejna.
        ```jsx
        const navigate = useNavigate();
        // ...
        navigate('/dashboard');
        navigate(-1); // Pichhle page par jaane ke liye
        ```

  * **`useParams()`**:

      * **Kaam**: URL se dynamic parameters (jaise `:userId`) ko access karne ke liye. Yeh ek object return karta hai.

  * **`useLocation()`**:

      * **Kaam**: Current location object ko access karne ke liye.
      * **Kya Milta Hai**: Isse aapko `pathname` (jaise `/about`), `search` (query parameters jaise `?q=hello`), aur `hash` (`#section`) jaisi jaankari milti hai.

-----


-----

-----

## **React mein Styling ke Tareeke**

React mein components ko style karne ke kayi tareeke hain. Har tareeke ke apne fayde aur nuksaan hain.

-----

### **1. Inline Styling**

Yeh styles ko seedhe JSX element ke `style` attribute mein lagane ka tareeka hai.

  * **Syntax**: Ismein `style` attribute ek **JavaScript object** leta hai. CSS properties ko **`camelCase`** mein likha jaata hai (`background-color` ban jaata hai `backgroundColor`).
  * **Fayde**:
      * Dynamic styling (state ya props ke aadhar par) karna bahut aasan hai.
      * Quick prototyping ke liye accha hai.
  * **Nuksaan**:
      * Pseudo-classes (jaise `:hover`) ya media queries ka istemaal nahi kar sakte.
      * Code saaf-suthra nahi rehta.
      * Styles reusable nahi hote.

**Code Example**:

```jsx
function MyButton() {
  const buttonStyle = {
    color: 'white',
    backgroundColor: 'blue',
    padding: '10px',
    borderRadius: '5px'
  };

  return <button style={buttonStyle}>Click Me</button>;
}
```

-----

-----

### **2. CSS Modules**

Yeh CSS files likhne ka ek tareeka hai jisse styles automatically **locally scoped** ho jaate hain.

  * **Kaise Kaam Karta Hai**:

    1.  Aap apni CSS file ka naam `[ComponentName].module.css` rakhte hain (jaise `Button.module.css`).
    2.  Aap use apne component mein import karte hain: `import styles from './Button.module.css';`.
    3.  Build process ke dauraan, har class name ko ek unique hash de diya jaata hai (jaise `.button` ban jaata hai `.Button_button__123xyz`).

  * **Fayda**:

      * Yeh sabse badi samasya, **global namespace pollution**, ko solve karta hai. Ab aapko class name clash hone ki chinta nahi rehti. Do alag-alag files mein same class name ho sakta hai.

  * **Nuksaan**:

      * Kayi class names lagana thoda lamba ho sakta hai.

**Code Example**:

```css
/* Button.module.css */
.error {
  background-color: red;
  color: white;
}
```

```jsx
// Button.js
import styles from './Button.module.css';

function Button() {
  // styles.error ek unique class name ban jaayega
  return <button className={styles.error}>Error Button</button>;
}
```

-----

-----

### **3. Styled Components**

Yeh ek bahut popular **CSS-in-JS** library hai. Yeh aapko JavaScript ke andar hi actual CSS likh kar React components banane deti hai.

  * **Kaise Kaam Karta Hai**:
    Aap tagged template literals (`` `...` ``) ka istemaal karke styles define karte hain. Yeh library parde ke peeche ek React component banati hai jiske saath ek unique class name aur aapke styles jude hote hain.

  * **Fayde**:

      * **Scoped Styles**: Class name clash hone ka koi dar nahi.
      * **Dynamic Styling**: Props ke aadhar par styles badalna bahut aasan hai.
      * **Co-location**: Component ka logic aur style ek hi file mein rehta hai.
      * **No Unused Styles**: Sirf wahi CSS final bundle mein jaati hai jo istemaal ho rahi hai.

  * **Nuksaan**:

      * Ek extra library install karni padti hai.
      * Thoda sa learning curve hai.

**Code Example**:

```jsx
import styled from 'styled-components';

// Ek naya <Button> component banaya jo asal mein ek styled <button> hai
const Button = styled.button`
  background-color: ${props => (props.primary ? 'blue' : 'grey')};
  color: white;
  padding: 10px;
  border-radius: 5px;

  &:hover {
    background-color: darkblue;
  }
`;

function App() {
  return (
    <div>
      <Button>Normal Button</Button>
      <Button primary>Primary Button</Button>
    </div>
  );
}
```

-----

-----

### **4. Tailwind CSS**

Yeh ek **utility-first** CSS framework hai.

  * **Kaise Kaam Karta Hai**:
    Yeh aapko pehle se bane-banaye components (jaise Bootstrap) nahi deta. Iski jagah, yeh aapko hazaaron chhoti-chhoti, single-purpose **utility classes** (jaise `flex`, `pt-4`, `text-center`, `bg-blue-500`) deta hai. Aap in classes ko seedhe apne JSX mein milakar apna design banate hain.

  * **Analogy**: Yeh aapko LEGO ke pre-built models (Bootstrap) dene ke bajaye, bahut saare alag-alag LEGO bricks (utility classes) deta hai taaki aap kuch bhi bana sakein. 🧱

  * **Fayde**:

      * **Highly Customizable**: Aap koi bhi design bana sakte hain.
      * **No Unused CSS**: Production build mein sirf wahi classes jaati hain jo aapne istemaal ki hain, isliye file size chhota rehta hai.
      * **Tez Development**: Ek baar classes yaad ho jaayein, toh development bahut tez ho jaata hai.

  * **Nuksaan**:

      * JSX bahut saari classes se "ganda" ya "bhara hua" lag sakta hai.
      * Shuruaat mein classes ke naam yaad karne padte hain.

**Code Example**:

```jsx
function MyCard() {
  return (
    <div className="p-6 max-w-sm mx-auto bg-white rounded-xl shadow-lg flex items-center space-x-4">
      <div className="text-xl font-medium text-black">My Card</div>
      <p className="text-slate-500">This is a card built with Tailwind!</p>
    </div>
  );
}
```

-----

-----

### **5. Material UI (MUI)**

  * **Yeh Kya Hai**: Yeh ek bahut hi popular **component library** hai jo Google ke **Material Design** system ko implement karti hai.
  * **Yeh Kya Deta Hai**: Yeh aapko pehle se bane-banaye, khoobsurat, aur accessible React components ka ek poora set deta hai (jaise `Button`, `TextField`, `AppBar`, `Drawer`).
  * **Fayde**:
      * Professional looking UI bahut tezi se ban jaata hai.
      * Behtareen documentation.
      * Theming ke zariye highly customizable.
  * **Nuksaan**:
      * Thoda heavy ho sakta hai (bundle size bada ho sakta hai).
      * Aapki app ka look "Material Design" jaisa hi lagega.

-----

-----

### **6. React Bootstrap**

  * **Yeh Kya Hai**: Yeh ek library hai jo popular Bootstrap framework ke saare components ko asli **React components** ke roop mein dobara banati hai.
  * **Fark**: Normal Bootstrap mein jQuery aur DOM manipulation hota hai, jo React ke saath theek se kaam nahi karta. React Bootstrap in components ko React ke state aur props se control hone laayak banata hai.
  * **Fayde**:
      * Aapko Bootstrap ka jaana-pechana look and feel milta hai, React ke ecosystem ke andar.
      * jQuery par koi dependency nahi.

-----

-----

### **7. Framer Motion (Animations ke liye)**

  * **Yeh Kya Hai**: Yeh React ke liye ek bahut hi popular aur powerful **animation library** hai.

  * **Kaam**: Isse complex, production-ready animations banana bahut aasan ho jaata hai. 🎞️

  * **Kaise Kaam Karta Hai**:
    Yeh aapko simple, declarative components (jaise `<motion.div>`) aur props (`animate`, `initial`, `whileHover`) deta hai jinka istemaal karke aap animations describe kar sakte hain.

  * **Fayde**:

      * Gestures (hover, tap) par आधारित animations.
      * Enter aur exit animations (component ke aane-jaane par).
      * Physics-based animations.
      * React mein animations banane ke complex process ko bahut aasan bana deta hai.

**Code Example**:

```jsx
import { motion } from 'framer-motion';

function Box() {
  return (
    <motion.div
      animate={{ scale: 1.5, rotate: 90 }} // Animate to this state
      transition={{ duration: 0.5 }} // Animation duration
    />
  );
}
```

-----


-----

## **1. Error Boundaries**

### **Samasya (The Problem)**

By default, agar aapke kisi bhi component ke rendering logic mein JavaScript error aa jaata hai, toh poori React app **crash ho jaati hai** aur user ko ek safed screen dikhti hai. Yeh ek bahut hi kharaab user experience hai. 👎

### **Samadhaan (The Solution): Error Boundaries**

**Error Boundaries** khaas React components hote hain jo apne neeche ke poore **child component tree mein hone waale JavaScript errors ko pakadte (catch karte) hain**.

Jab yeh kisi error ko pakadte hain, toh yeh crashed component ki jagah ek **fallback UI** (jaise "Something went wrong" message) dikhaate hain, jisse poori app crash hone se bach jaati hai.

**Analogy**: Yeh aapke ghar ke **fuse box (MCB)** ⚡ jaisa hai. Agar ek kamre (child component) mein short circuit (error) hota hai, toh poora ghar band hone ke bajaye sirf us kamre ka fuse udd jaata hai, aur baaki ghar chalta rehta hai.

**Kaise Banayein aur Istemal Karein**:

  * Error Boundary hamesha ek **Class Component** hota hai.
  * Yeh tab banta hai jab aap ismein `static getDerivedStateFromError()` ya `componentDidCatch()` lifecycle methods ka istemaal karte hain.
  * Phir aap apne component ko is `<ErrorBoundary>` se wrap kar dete hain.

**Code Example**:

```jsx
// ErrorBoundary.js
import React from 'react';

class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  // State update karke fallback UI dikhata hai
  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  // Error ko log karta hai
  componentDidCatch(error, errorInfo) {
    console.error("Error Boundary ne error pakda:", error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      return <h1>Oops! Kuch gadbad ho gayi.</h1>;
    }
    return this.props.children;
  }
}

// App.js
// <ErrorBoundary>
//   <MyRiskyComponent />
// </ErrorBoundary>
```

-----

-----

## **2. Handling Async Errors (Asynchronous Errors ko Handle Karna)**

**Samasya**: Error Boundaries sirf rendering ke dauraan hone waale synchronous errors ko hi pakadti hain. Woh **asynchronous code** (jaise `setTimeout`, Promises, ya `fetch` API calls) mein hone waale errors ko **nahi pakad sakti**.

Kyunki async code rendering phase ke **baad** chalta hai, tab tak Error Boundary ka kaam poora ho chuka hota hai.

**Samadhaan**: Aapko async errors ko manually `try...catch` (agar `async/await` use kar rahe hain) ya `.catch()` block (agar `.then` use kar rahe hain) se pakadna hoga aur error dikhane ke liye ek state set karna hoga.

**Code Example (`async/await` ke saath):**

```jsx
import React, { useState, useEffect } from 'react';

function UserProfile() {
  const [user, setUser] = useState(null);
  const [error, setError] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    async function fetchData() {
      // try block ke andar API call
      try {
        const response = await fetch('https://api.example.com/user/123');
        if (!response.ok) {
          throw new Error('Network response theek nahi tha!');
        }
        const data = await response.json();
        setUser(data);
      } catch (err) {
        // catch block mein error state set kiya
        setError(err.message);
      } finally {
        setLoading(false);
      }
    }
    
    fetchData();
  }, []);

  if (loading) {
    return <div>Loading...</div>;
  }
  
  // Conditional rendering
  if (error) {
    return <div>Error: {error}</div>;
  }

  return <h1>Welcome, {user.name}</h1>;
}
```

-----

-----

## **3. React Strict Mode**

  * **Yeh Kya Hai**: `<React.StrictMode>` ek helper component hai jo development ke dauraan aapki application mein potential problems ko highlight karne mein madad karta hai.
  * **Yeh UI par Kuch Bhi Render Nahi Karta**. Yeh sirf development ke liye ek tool hai.

**Kaam Kya Karta Hai**:
Yeh apne andar wrap kiye gaye components ke liye extra checks aur **console warnings** on kar deta hai. Yeh aapko aisi cheezein dhundhne mein madad karta hai:

  * Unsafe lifecycle methods ka istemaal.
  * Puraane ya deprecated APIs ka istemaal.
  * Unexpected side effects.

**Double Invoking ka Concept**:
Bugs dhundhne ke liye, Strict Mode development mein kuch functions ko **jaan-boojhkar do baar call karta hai**, jaise:

  * Component ka render function
  * `useEffect` ka setup aur cleanup function

Isse yeh sunishchit hota hai ki aapke functions "pure" hain aur unka cleanup theek se ho raha hai.

**Zaroori Soochana**: Strict Mode sirf **development mode** mein chalta hai. Production build par iska **koi asar nahi padta**.

**Ise Kaise Istemal Karein**:
Aap bas apni poori App ko `index.js` file ke andar `<React.StrictMode>` se wrap kar dein.

```jsx
// index.js
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

-----
-----

-----

## **Performance Optimization Kyun Zaroori Hai?**

Ek fast aur responsive application behtar user experience deti hai. Performance optimization do cheezon par focus karti hai:

1.  **Initial Load Time**: Application pehli baar mein kitni tezi se khulti hai.
2.  **Runtime Performance**: Application istemaal karte waqt kitni smooth aur responsive hai.

-----

-----

## **1. Code Splitting**

  * **Yeh Kya Hai**: Code splitting ek aisi technique hai jiska istemaal bundlers (jaise Webpack ya Vite) karte hain. Ismein aapki badi JavaScript bundle file ko **chhote-chhote logical tukdon (chunks)** mein tod diya jaata hai.

  * **Samasya**: By default, bundler aapki poori application ke code ko milakar ek hi badi `bundle.js` file bana deta hai. User ko yeh poori file pehle download karni padti hai, jisse initial load time badh jaata hai.

  * **Samadhaan**: Code splitting is badi file ko kayi chhoti files mein baant deta hai. Shuruaat mein sirf wahi code load hota hai jo pehle page ke liye zaroori hai. Baaki code "on-demand" (jab user us feature ko istemaal karta hai) load hota hai.

  * **Fayda**: Isse application ka **initial page load time kaafi behtar** ho jaata hai. 🚀

-----

-----

## **2. Lazy Loading (`React.lazy` & `Suspense`)**

**Lazy loading** React mein code splitting ko implement karne ka tareeka hai. Iska matlab hai ek component ke code ko tab tak **load nahi karna, jab tak uski zaroorat na pade**.

Ise implement karne ke liye React do cheezein deta hai:

1.  **`React.lazy()`**:

      * Yeh ek function hai jo aapko ek dynamic `import()` ko ek normal component ki tarah render karne deta hai.
      * Yeh ek special component return karta hai jo zaroorat padne par apna code chunk network se fetch karna jaanta hai.
      * **Syntax**: `const MyComponent = React.lazy(() => import('./MyComponent'));`

2.  **`<Suspense>`**:

      * Kyunki lazy component ka code network se aata hai, ismein kuch samay lag sakta hai.
      * `Suspense` ek built-in component hai jiske `fallback` prop mein aap ek **loading indicator** (jaise "Loading..." ya ek spinner ⏳) de sakte hain.
      * Yeh fallback UI tab tak dikhega jab tak lazy component ka code download ho raha hai.

**Analogy**: Yeh ek restaurant 🧑‍🍳 jaisa hai. Chef shuruaat mein hi saara menu nahi bana deta. Woh dish tabhi banata hai jab customer order karta hai. Jab tak dish ban rahi hai (code load ho raha hai), customer ko paani (fallback UI) de diya jaata hai.

**Code Example**:

```jsx
import React, { Suspense } from 'react';

// About component ka code tabhi load hoga jab user /about page par jaayega
const AboutPage = React.lazy(() => import('./pages/About'));

function App() {
  return (
    <div>
      {/* Routes setup... */}
      <Suspense fallback={<div>Loading page, please wait...</div>}>
        <Routes>
          <Route path="/about" element={<AboutPage />} />
        </Routes>
      </Suspense>
    </div>
  );
}
```

-----

-----

## **3. Memoization (`React.memo`, `useMemo`, `useCallback`)**

**Memoization** ek optimization technique hai jismein aap ek **expensive calculation ke result ko cache (yaad) kar lete hain**. Woh calculation dobara sirf tabhi hoti hai jab uske inputs badalte hain.

React mein iska istemaal **bewajah ke re-renders aur re-calculations** ko rokne ke liye hota hai, jisse runtime performance behtar hoti hai.

-----

### **`React.memo()` - Component ko Memoize Karna**

  * **Kaam**: Yeh ek **functional component** ko bewajah re-render hone se rokta hai.
  * **Kaise**: Yeh ek Higher-Order Component (HOC) hai jisse aap apne component ko wrap karte hain. Yeh props ka shallow comparison karta hai. Agar props pichhle render se **same** hain, toh yeh re-render ko **skip kar dega** aur pichhla render kiya hua result hi istemaal kar lega.

**Analogy**: Yeh component ki photo kheench kar rakh leta hai. Agar props nahi badle, toh nayi photo kheenchne ke bajaye purani hi dikha deta hai. 📸

**Code Example**:

```jsx
function UserAvatar({ username }) {
  console.log(`${username}'s avatar is rendering`);
  return <img src={`/avatars/${username}`} alt={username} />;
}

// UserAvatar ko memoize kiya
export default React.memo(UserAvatar);
```

Ab agar `UserAvatar` ka parent re-render hota hai lekin `username` prop nahi badalta, toh "rendering" message console mein nahi aayega.

-----

### **`useCallback()` - Function ko Memoize Karna**

  * **Kaam**: Yeh ek **function ko memoize karta hai**.
  * **Kyun Zaroori Hai?**: Jab aap ek function ko prop ke roop mein `React.memo` waale child component ko bhejte hain, toh `useCallback` zaroori ho jaata hai. Iske bina, parent ke har render par function dobara create hota hai (naya reference), jisse child component bewajah re-render ho jaata hai. `useCallback` isse rokta hai.

**Analogy**: Yeh function ki "original copy" bana kar rakhta hai. Agar dependency nahi badli, toh photocopy karne ke bajaye original copy hi de deta hai. 📄

**Code Example**:

```jsx
const MyComponent = React.memo(({ onButtonClick }) => {
  // ...
});

function Parent() {
  const [count, setCount] = useState(0);

  // Yeh function tabhi dobara create hoga jab count badlega.
  const handleButtonClick = useCallback(() => {
    console.log('Button clicked! Current count:', count);
  }, [count]); 

  return <MyComponent onButtonClick={handleButtonClick} />;
}
```

-----

### **`useMemo()` - Value ko Memoize Karna**

  * **Kaam**: Yeh ek **expensive calculation ke result (value) ko memoize karta hai**.
  * **Kaise**: Yeh ek function aur dependency array leta hai. Yeh us function ko sirf tabhi dobara chalayega jab uski koi dependency badlegi. Warna, yeh pichhli baar ka calculate kiya hua result hi return kar dega.

**Analogy**: Ek mushkil math ke sawaal ke jawab ko aek diary 📓 mein likh kar rakhta hai. Agar sawaal nahi badla, toh dobara solve karne ke bajaye diary se dekh kar jawab de deta hai.

**Code Example**:

```jsx
function MyComponent({ numbers }) {
  // Yeh calculation bahut heavy hai aur sirf tabhi honi chahiye jab 'numbers' array badle.
  const sum = useMemo(() => {
    console.log('Calculating sum...');
    return numbers.reduce((acc, num) => acc + num, 0);
  }, [numbers]);

  return <div>Sum is: {sum}</div>;
}
```

-----



-----

## **1. Project Structure Best Practices (Project ko Organize Karna)**

Ek accha project structure code ko dhoondhne, samajhne, aur maintain karne mein aasan banata hai. Badi applications ke liye, **feature-based structure** sabse accha maana jaata hai.

**Feature-based Structure Kya Hai?**
Ismein aap files ko unke type (jaise `components`, `pages`) ke aadhar par nahi, balki unke **feature** ke aadhar par group karte hain.

**Example**:

  * **Type-based (Chhote projects ke liye theek hai)**:
    ```
    /src
      /components
      /pages
      /hooks
    ```
  * **Feature-based (Bade projects ke liye best hai)**:
    ```
    /src
      /features
        /authentication
          - Login.js
          - Login.css
          - authAPI.js
        /dashboard
          - Dashboard.js
          - Dashboard.css
      /components  // Yahan shared, reusable components aate hain (jaise Button, Modal)
      /hooks       // Shared custom hooks
      /lib         // Shared libraries ya API setup
    ```

**Fayda**: Ek feature se juda saara code ek hi jagah mil jaata hai, jisse use manage karna aasan ho jaata hai.

-----

-----

## **2. Environment Variables**

  * **Yeh Kya Hain**: Environment variables aise variables hote hain jinki value aapke code ke bahar, uss environment mein set ki jaati hai jahan app chal rahi hai (jaise development ya production).

  * **Kyun Istemal Karte Hain**: **Sensitive ya environment-specific jaankari** ko store karne ke liye jo aap apne source code mein seedhe nahi likhna chahte.

      * **Udaharan**: API keys, database URLs, feature flags.

  * **Create React App mein Istemal**:

    1.  Project ke root mein ek `.env` file banayein.
    2.  Variable ka naam hamesha `REACT_APP_` se shuru hona chahiye.
        ```
        REACT_APP_API_URL=https://api.my-app.com
        REACT_APP_API_KEY=xyz123abc
        ```
    3.  Code mein inhein `process.env.REACT_APP_VARIABLE_NAME` se access karein.

**Security Warning ⚠️**: Browser mein `process.env` se access hone waale variables **secret nahi hote**. Inhein koi bhi dekh sakta hai. Asli secret keys hamesha backend server par hi rakhni chahiye.

-----

-----

## **3. APIs ke Saath Kaam Karna (fetch, axios)**

React apps aam taur par backend server se data laane (fetch) ya bhejne (send) ke liye API calls karti hain. Iske do popular tareeke hain:

  * **`fetch` API**:

      * **Kya hai**: Yeh browser mein **built-in** hai. Kuch alag se install karne ki zaroorat nahi.
      * **Fayde**: Koi dependency nahi. Simple `GET` requests ke liye aasan hai.
      * **Nuksaan**:
          * HTTP errors (jaise 404, 500) par apne aap error throw nahi karta.
          * JSON data paane ke liye do steps (`.then()`) lagte hain.
          * Interceptors jaise advanced features nahi hain.

  * **`axios` Library**:

      * **Kya hai**: Yeh ek bahut popular **third-party library** hai (`npm install axios`).
      * **Fayde**:
          * HTTP errors par apne aap error throw karta hai. ✅
          * Response ko automatically JSON mein convert kar deta hai.
          * Interceptors jaise powerful features hain (request ya response ko beech mein rokne ke liye).
          * `POST`, `PUT` jaise complex requests ke liye iska syntax aasan hai.

**Nishkarsh**: Chhote projects ke liye `fetch` theek hai, lekin zyadatar real-world applications ke liye **axios** behtar choice hai.

-----

-----

## **4. Form Handling & Validation**

React mein forms handle karne ka matlab hai form inputs ke state ko manage karna aur user ke input ko validate karna.

**Tareeka (Controlled Components)**:

1.  Har input field ke liye ek **state** (`useState`) banayein.
2.  Input ke `value` ko us state se jodein.
3.  `onChange` event par state ko update karein.
4.  `<form>` ke `onSubmit` event par data ko process karein.

**Validation**:

  * **Manual**: Aap `if/else` ka istemaal karke apne handler functions ke andar validation logic likh sakte hain.
  * **Libraries (Recommended)**: Bade aur complex forms ke liye, libraries ka istemaal karna sabse accha hai.
      * **React Hook Form**: Bahut hi performant aur modern library jo hooks ka istemaal karti hai. Isse re-renders kam hote hain.
      * **Formik**: Ek poora solution jo form state management aur validation dono handle karta hai.
      * **Yup**: Ek schema validation library jo in dono ke saath bahut acchi tarah kaam karti hai, jisse validation rules likhna aasan ho jaata hai.

-----

-----

## **5. Authentication (JWT, OAuth)**

Authentication user ki pehchan ko verify karne ka process hai. SPAs mein yeh aam taur par tokens se handle hota hai.

  * **JWT (JSON Web Token)**:

      * **Yeh Kya Hai**: Yeh ek standard hai jisse do parties ke beech information ko securely transfer kiya jaata hai. Yeh ek token hota hai jise server digitally sign karta hai.
      * **Flow Kaise Kaam Karta Hai**:
        1.  User username/password server ko bhejta hai.
        2.  Server credentials verify karke ek **JWT** generate karta hai aur user ko bhejta hai.
        3.  Client (React app) us JWT ko `localStorage` ya secure cookie mein store kar leta hai.
        4.  Har agli protected API request ke saath, client is JWT ko `Authorization` header mein bhejta hai.
        5.  Server is JWT ko verify karke request ko authenticate karta hai.

  * **OAuth 2.0**:

      * **Yeh Kya Hai**: Yeh ek **authorization framework** hai, authentication nahi. Yeh ek application ko doosri service (jaise Google, Facebook) par user ke account ka limited access lene ki anumati deta hai.
      * **Use Case**: "Login with Google" ya "Login with Facebook" jaise buttons. Ismein aap apna Google password us app ko nahi dete, balki Google ko batate hain ki "is app ko meri basic info access karne do".

-----

-----

## **6. State Persistence (localStorage/sessionStorage)**

**Samasya**: By default, React ka state memory mein rehta hai. Jab user page ko **refresh** karta hai ya browser band karta hai, toh saara state **kho jaata hai**.

**Samadhaan**: Web Storage APIs ka istemaal karke state ko browser mein **persist (save)** karna.

  * **`localStorage`**:

      * **Kab**: Jab aapko data ko **lambi avadhi tak** store karna ho. Ismein store kiya gaya data tab tak rehta hai jab tak use manually delete na kiya jaaye.
      * **Use Case**: User ki theme preference (dark/light mode), ya user ko logged in rakhne ke liye auth token store karna.

  * **`sessionStorage`**:

      * **Kab**: Jab aapko data sirf **ek session tak** hi store karna ho. Jaise hi user browser tab ko band karta hai, data delete ho jaata hai.
      * **Use Case**: Ek multi-step form ka data store karna. Agar user galti se page refresh kar de, toh data bana rahega, lekin tab band karne par chala jaayega.

**Kaise Istemal Karein**:
Storage mein data hamesha string format mein save hota hai, isliye objects/arrays ko save karne se pehle **`JSON.stringify()`** aur nikalne ke baad **`JSON.parse()`** ka istemaal karein.

-----



-----

## **1. Testing in React**

### **Testing Kyun Zaroori Hai?**

Testing ka mool uddeshya yeh sunishchit karna hai ki aapka code waisa hi kaam kar raha hai jaisa use karna chahiye. Isse:

  * **Confidence Milta Hai**: Aap nishchint ho jaate hain ki aapka code sahi hai.
  * **Bugs se Bachata Hai**: Code mein badlaav karte waqt, tests aapko batate hain ki kahin kuch toot toh nahi gaya.
  * **Code Quality Behtar Hoti Hai**: Testable code likhne se code ka structure apne aap behtar ho jaata hai.

-----

### **Unit Testing with Jest**

  * **Unit Testing Kya Hai?**
    Ismein hum code ke sabse **chhote aur isolated hisse (units)** ko test karte hain. Aam taur par, yeh ek individual function hota hai.
    **Analogy**: Yeh ek dish banane se pehle har ek masale (ingredient) ko chakhne jaisa hai, ki namak theek hai ya nahi, cheeni meethi hai ya nahi.

  * **Jest Kya Hai?**
    Jest ek bahut hi popular **JavaScript Testing Framework** hai jise Facebook ne banaya hai. Yeh Create React App mein by default shaamil hota hai. Yeh ek "all-in-one" package hai jismein test runner, assertion library (`expect`), aur mocking sab kuch shaamil hai.

  * **Jest Test ka Structure**:

    1.  **`describe()`**: Related tests ko ek group mein daalne ke liye.
    2.  **`it()` ya `test()`**: Ek individual test case ko define karne ke liye.
    3.  **`expect()`**: Jis value ko aap test karna chahte hain, use ismein wrap karte hain.
    4.  **Matchers**: Yeh `expect()` ke baad aane waale functions hain jo asli comparison karte hain (jaise `.toBe()`, `.toEqual()`, `.toBeTruthy()`).

**Code Example (Ek simple `sum` function ka test):**

```javascript
// sum.js
function sum(a, b) {
  return a + b;
}
export default sum;

// sum.test.js
import sum from './sum';

describe('sum function', () => {
  it('should add two numbers correctly', () => {
    // Expect (ummeed) hai ki sum(1, 2) ka result 3 ho
    expect(sum(1, 2)).toBe(3);
  });
});
```

-----

### **Component Testing with React Testing Library (RTL)**

  * **Component Testing Kya Hai?**
    Ismein hum poore React components ko test karte hain ki woh sahi se render ho rahe hain ya nahi aur user ke interaction par waisa hi behave kar rahe hain jaisa karna chahiye.

  * **React Testing Library (RTL) Kya Hai?**
    Yeh React components ko test karne ke liye ek library hai.

      * **Mool Mantra**: *"The more your tests resemble the way your software is used, the more confidence they can give you."*
        (Aapke tests jitna zyada user ke istemaal karne ke tareeke jaise honge, utna hi zyada bharosa woh aapko denge.)

  * **RTL ka Tareeka**:
    RTL aapko component ke **implementation details** (jaise state ya props) ko test karne se rokta hai. Iski jagah, yeh is baat par zor deta hai ki aap woh test karein jo **user dekhta hai aur karta hai**.

  * **Core Functions**:

      * **`render()`**: Component ko ek virtual DOM mein render karne ke liye.
      * **Queries (`getBy...`, `findBy...`, `queryBy...`)**: Screen par elements ko dhoondhne ke liye (jaise `getByText('Submit')`).
      * **`fireEvent` / `user-event`**: User ke actions (jaise `click`, `type`) ko simulate karne ke liye. (`user-event` behtar maana jaata hai).

**Analogy**: Ek car 🚗 ko test karte waqt, aap yeh check nahi karte ki engine ke andar piston theek se upar-neeche ho raha hai ya nahi (implementation detail). Aap car ko chala kar dekhte hain (user perspective) ki woh aage badh rahi hai ya nahi.

**Code Example (Ek Counter component ka test):**

```jsx
import { render, screen, fireEvent } from '@testing-library/react';
import Counter from './Counter';

describe('Counter component', () => {
  it('should increment count when button is clicked', () => {
    // 1. Component ko render kiya
    render(<Counter />);

    // 2. Button ko uske role aur naam se dhoondha
    const button = screen.getByRole('button', { name: /increment/i });
    
    // 3. Button par click simulate kiya
    fireEvent.click(button);

    // 4. Check kiya ki screen par text "Count: 1" dikh raha hai ya nahi
    const countElement = screen.getByText('Count: 1');
    expect(countElement).toBeInTheDocument();
  });
});
```

-----

-----

## **2. Build & Deployment**

-----

### **Vite / CRA builds**

**Build Process Kya Hai?**
Build process ka mool kaam aapke development code (jismein kayi files, JSX, modern JS, aur unoptimized assets hote hain) ko **static, optimized files** ke ek set mein badalna hai, jo ek web server par deploy hone ke liye taiyaar hon.

  * **Create React App (CRA)**:

      * **Command**: `npm run build`
      * **Kaise**: Yeh parde ke peeche **Webpack** ka istemaal karta hai. Yeh code ko transpile, bundle, aur minify karke saari final files ko ek `/build` folder mein daal deta hai.

  * **Vite**:

      * **Command**: `npm run build`
      * **Kaise**: Yeh production build ke liye **Rollup** ka istemaal karta hai. Vite apne behad tez development server ke liye jaana jaata hai. Iska production build bhi highly optimized hota hai aur saari files ko ek `/dist` folder mein daal deta hai.

Dono hi tools ka output ek folder hota hai jise aap kisi bhi static hosting service par daal sakte hain.

-----

### **Hosting on Netlify, Vercel, GitHub Pages**

**Hosting Kya Hai?**
Apni website ki static files ko ek public web server par daalna taaki koi bhi use ek URL ke zariye access kar sake.

  * **Netlify & Vercel**:
    Yeh modern frontend apps ko host karne ke liye sabse popular platforms hain.

      * **Kaise Kaam Karte Hain**: Aap apne GitHub/GitLab repository ko inse connect kar dete hain.
      * **Mukhya Feature (Continuous Deployment)**: Jab bhi aap apne main branch mein `git push` karte hain, yeh platforms **apne aap** aapka build command (`npm run build`) chalate hain aur nayi site ko deploy kar dete hain, bina kisi downtime ke.
      * **Vercel**: Next.js ke creators ne banaya hai, isliye Next.js ke saath iska integration sabse accha hai.

  * **GitHub Pages**:

      * **Yeh Kya Hai**: GitHub dwara di jaane waali ek free static site hosting service.
      * **Kaise Kaam Karta Hai**: Aap apni repository se seedhe static files serve kar sakte hain.
      * **Use Case**: Simple static sites, project documentation, aur portfolios ke liye bahut accha hai. SPAs ke liye ismein routing setup karna Netlify/Vercel ke muqable thoda manual ho sakta hai.

-----



-----

## **React Cheat Sheet (Hinglish)** 🚀

### **Class Component Lifecycle Methods**

Yeh methods class components ke alag-alag stages par apne aap chalte hain.

  * `shouldComponentUpdate(newProps, newState)`
      * Agar yeh `false` return karta hai, toh `render()` ko skip kar diya jaata hai. [cite\_start]Yeh performance optimization ke liye hai. [cite: 1]
  * `render()`
      * UI ko render karta hai.
  * `componentDidUpdate(prevProps, prevState)`
      * Component ke update hone ke baad chalta hai. [cite\_start]Yahan aap DOM par operations kar sakte hain. [cite: 1]
      * [cite\_start]**Zaroori**: State update karne se pehle props ko zaroor compare karein (`if (newProps.someValue !== this.props.someValue)`) taaki infinite loop se bach sakein. [cite: 1]

-----

### **React Hooks (Functional Components ka Naya Tareeka)**

[cite\_start]Hooks React 16.8 mein aaye naye additions hain jo aapko functional components mein state aur doosre React features istemaal karne dete hain. [cite: 5]

#### **1. State Hook (`useState`)**

Component mein state (data jo badal sakta hai) add karne ke liye.

```javascript
import React, { useState } from 'react';

function Example() {
  // "count" naam ka ek naya state variable banaya
  const [count, setCount] = useState(0); [cite_start]// 0 initial value hai [cite: 3]

  return (
    <div>
      <p>Aapne {count} baar click kiya</p>
      {/* Button click par setCount function se count ko update kiya */}
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

[cite\_start]*Hinglish Comment: Upar diye gaye code mein `useState` ek state variable (`count`) aur use update karne waala ek function (`setCount`) return karta hai.* [cite: 3, 4]

  * **Ek se zyada State Variables Banana:**
    [cite\_start]Aap ek hi component mein `useState` ko kayi baar call karke alag-alag state variables bana sakte hain. [cite: 6, 7]
    ```javascript
    function ExampleWithManyStates() {
      const [age, setAge] = useState(42);
      const [fruit, setFruit] = useState('banana');
      const [todos, setTodos] = useState([{ text: 'Learn Hooks' }]);
      // ...
    }
    ```

#### **2. Effect Hook (`useEffect`)**

[cite\_start]Yeh `componentDidMount`, `componentDidUpdate`, aur `componentWillUnmount` ka combination hai. [cite: 10] Iska istemaal side effects (jaise data fetching, subscriptions) ke liye hota hai.

```javascript
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  // componentDidMount aur componentDidUpdate jaisa kaam karta hai
  useEffect(() => {
    // Browser API ka istemaal karke document ka title update kiya
    document.title = `Aapne ${count} baar click kiya`;
  }, [count]); [cite_start]// Dependency array: Effect sirf tab chalega jab 'count' badlega [cite: 8]

  return (
    <div>
      <p>Aapne {count} baar click kiya</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

*Hinglish Comment: Upar `useEffect` ka istemaal kiya gaya hai. [cite\_start]Yeh har render ke baad chalta hai. [cite: 9, 11] Dependency array (`[count]`) batata hai ki effect ko sirf tabhi dobara chalana hai jab `count` ki value badle.*

  * **Cleanup Effect**: `useEffect` se ek function return karke aap "cleanup" kar sakte hain. [cite\_start]Yeh component ke unmount hone se pehle chalta hai. [cite: 15]

#### **3. Custom Hooks Banana**

Aap stateful logic ko reusable banane ke liye apne khud ke Hooks bana sakte hain.

```javascript
// Yeh ek custom hook hai
function useFriendStatus(friendID) {
  const [isOnline, setIsOnline] = useState(null);

  useEffect(() => {
    function handleStatusChange(status) {
      setIsOnline(status.isOnline);
    }
    ChatAPI.subscribeToFriendStatus(friendID, handleStatusChange);
    // Cleanup function
    return () => {
      ChatAPI.unsubscribeFromFriendStatus(friendID, handleStatusChange);
    };
  }, [friendID]); // Sirf tab re-subscribe karein jab friendID badle

  return isOnline;
}

// Custom hook ka istemaal
function FriendStatus(props) {
  const isOnline = useFriendStatus(props.friend.id);

  if (isOnline === null) {
    return 'Loading...';
  }
  return isOnline ? 'Online' : 'Offline';
}
```

*Hinglish Comment: `useFriendStatus` ek custom hook hai jo friend ke online status ko track karne ka logic rakhta hai. [cite\_start]Isse hum kisi bhi component mein reuse kar sakte hain.* [cite: 13, 14, 16, 17]

#### **Hooks API Reference**

  * **Basic Hooks**:
      * `useState()`: State add karne ke liye.
      * `useEffect()`: Side effects ke liye.
      * `useContext()`: Context se value lene ke liye.
  * **Additional Hooks**:
      * `useReducer()`: Complex state management ke liye `useState` ka alternative.
      * `useCallback()`: Functions ko memoize karne ke liye.
      * `useMemo()`: Expensive calculations ke result ko memoize karne ke liye.
      * `useRef()`: DOM node ko access karne ya ek mutable value store karne ke liye.
      * `useLayoutEffect()`: `useEffect` jaisa hi hai, lekin yeh DOM mutations ke baad synchronously chalta hai.

-----

### **DOM ke Saath Kaam Karna**

#### **1. References (`ref`)**

[cite\_start]Refs aapko DOM nodes ya React elements ko seedhe access karne dete hain. [cite: 19]

```javascript
class MyComponent extends Component {
  componentDidMount () {
    // Component ke mount hone par input field ko focus kiya
    [cite_start]this.input.focus(); [cite: 18]
  }
  
  render () {
    return (
      <div>
        {/* 'ref' ka istemaal karke input element ko 'this.input' se joda */}
        <input ref={el => this.input = el} />
      </div>
    );
  }
}
```

#### **2. DOM Events**

[cite\_start]Events (jaise `onChange`, `onClick`) ko handle karne ke liye attributes ko function paas karein. [cite: 20]

```javascript
class MyComponent extends Component {
  onChange (event) {
    // Input ki value badalne par state ko update kiya
    this.setState({ value: event.target.value });
  }

  render () {
    <input type="text"
        value={this.state.value}
        onChange={event => this.onChange(event)} />
  }
}
```

-----

### **JSX Patterns**

#### **1. Styles**

[cite\_start]`style` attribute ek JavaScript object leta hai. [cite: 22]

```jsx
// Pehla Tareeka: Ek variable ke saath
const style = { height: 10 };
return <div style={style}></div>;

// Doosra Tareeka: Inline double curly braces ke saath
return <div style={{ margin: 0, padding: 0 }}></div>;
```

#### **2. Inner HTML**

[cite\_start]HTML string ko render karne ke liye `dangerouslySetInnerHTML` ka istemaal karein, lekin isse XSS attacks ka khatra ho sakta hai. [cite: 23]

```jsx
function markdownify() { return "<p>Hello World!</p>"; }
<div dangerouslySetInnerHTML={{__html: markdownify()}} />
```

#### **3. Lists (Soochi)**

[cite\_start]List render karte waqt har item ko ek unique `key` prop zaroor dein. [cite: 24]

```jsx
class TodoList extends Component {
  render () {
    const { items } = this.props;
    return (
      <ul>
        {items.map(item =>
          <TodoItem item={item} key={item.key} />
        )}
      </ul>
    );
  }
}
```

#### **4. Conditionals (Shart ke Aadhar par Rendering)**

  * **Ternary Operator (`? :`)**:

    ```jsx
    <Fragment>
      {showMyComponent ? <MyComponent /> : <OtherComponent />}
    </Fragment>
    ```

  * **Short-circuit (`&&`)**:

    ```jsx
    <Fragment>
      {showPopup && <Popup />}
    </Fragment>
    ```

-----

### **React 16+ ke Naye Features**

#### **1. Ek se Zyada Elements Return Karna**

[cite\_start]Aap arrays ya fragments ka istemaal karke ek se zyada elements return kar sakte hain. [cite: 25]

  * **Arrays**:

    ```jsx
    render () {
      // Keys dena na bhoolein!
      return [
        <li key="A">Pehla item</li>,
        <li key="B">Doosra item</li>
      ];
    }
    ```

  * **Fragments**:

    ```jsx
    render () {
      return (
        <Fragment>
          <li>Pehla item</li>
          <li>Doosra item</li>
        </Fragment>
      );
    }
    ```

#### **2. Sirf String Return Karna**

[cite\_start]Ab aap ek component se sirf ek string bhi return kar sakte hain. [cite: 26]

```jsx
render() {
  return 'Dekho, koi span nahi!';
}
```

#### **3. Error Handling**

[cite\_start]`componentDidCatch` ka istemaal karke aap child components mein hone waale errors ko pakad sakte hain. [cite: 27]

```jsx
class MyComponent extends Component {
  componentDidCatch (error, info) {
    this.setState({ error });
  }
}
```

#### **4. Portals**

[cite\_start]Portals aapko children ko DOM ke kisi bhi hisse mein render karne dete hain, bhale hi woh parent ke DOM hierarchy se bahar ho. [cite: 28]

```jsx
render () {
  return React.createPortal(
    this.props.children,
    document.getElementById('menu')
  );
}
```

#### **5. Hydration**

[cite\_start]Server-Side Rendering ke output par React ko attach karne ke liye `ReactDOM.hydrate` ka istemaal karein. [cite: 29]

```jsx
const el = document.getElementById('app');
ReactDOM.hydrate(<App />, el);
```

-----

### **Property Validation (`PropTypes`)**

Development ke dauraan props ke type check karne ke liye.

#### **PropTypes ki Alag-Alag Types**

  * **Basic**: `string`, `number`, `func`, `bool`, `any`
  * [cite\_start]**Enum**: `oneOf(['left', 'right'])` [cite: 30]
  * **Union**: `oneOfType([PropTypes.string, PropTypes.number])`
  * **Array**: `array`, `arrayOf(PropTypes.number)`
  * [cite\_start]**Object**: `object`, `objectOf(PropTypes.number)`, `instanceOf(Message)`, `shape({ name: PropTypes.string })` [cite: 31]
  * **Elements**: `element` (React element), `node` (Kuch bhi jo render ho sake)
  * **Required**: Kisi bhi type ke aage `.isRequired` laga dein.

#### **Udaharan**

```javascript
import PropTypes from 'prop-types';

MyComponent.propTypes = {
  // Basic Types
  email:      PropTypes.string,
  seats:      PropTypes.number,
  
  // Required Type
  name:  PropTypes.string.isRequired,

  // Enum Type
  direction: PropTypes.oneOf(['left', 'right']),
  
  // Array of numbers
  ages: PropTypes.arrayOf(PropTypes.number),
  
  // Object with a specific shape
  user: PropTypes.shape({
    name: PropTypes.string,
    age:  PropTypes.number
  }),

  // Custom Validation
  customProp: (props, key, componentName) => {
    if (!/matchme/.test(props[key])) {
      return new Error('Validation fail ho gayi!');
    }
  }
};
```



----




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

