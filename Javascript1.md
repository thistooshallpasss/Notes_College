# 01 : JavaScript Introduction

### What is a programming language ?

Programming language set of instructions, symbols, and syntax hote hain jinka use software develop karne ka leya kia jata hai. Ye coding instructions kisi device/computer ke behaviour ko control krte hain. For example: C++, Java, Python. Har language ke apne features and benefits hote hain aur particular language ko particular tasks, projects ke lie kia jata hai.

### What is high level programming language?

High level programming language vah programming language hoti hai jise is trah se design kia gya hai ki us language ko asani se likha, pdha vah smja ja skta hai. High level language ek english like nature language ke equal hi hoti hai. High level language ko sikhna asan hota hai. High level language kafi sare actions aise hote hain jo vo khud manage kr leti hai aur hume ni krne hote hain.. for example :

1. memory managemant.
2. communication with hardware.

### What is machine level language or Low level languages?

Machine language jise ki machine code ya assembly language bhi jana jata hai, set of instructors hote hain jinhe CPU direct execute kr skta hai. Ye instructions 0 or 1 ki form me hote hain. Machine level language ki computer ki native language b kha jata hai. Low level language ka ek type hai assembly language jisme ki code likha ja skta hai. Assembly language me assembler hota hai jo ki assembly language ke code ko machine language ke code me convert krta hai.

### What is front-end ?

front-end web development ka ek hissa hota hai jo ki kisi website, application ke user interface, user experience se deal krta hai. Other way me khe to front-end kisi be software ke vah part hota hai jise hm dekh skte hain, interact kr skte hain. Front-end me development krne ke lie HTML, CSS, JavaScript and JavaScript based libraries/frameworks ka use hota hai.

### What is back-end ?

Back-end development ka vah part hota hai jisme kisi b website ya application ka server-side ka code likha jata hai. Backend me service side logics, database ka management etc hota hai.

Other language me khte to back-end software ka vah part hota jo behind the seen work krta hai. Aur vah front-end se jo requests aati hai unhe handle krta hain aur jo b required response hota hai vah return krta hai.
for eample:

1. Data save
2. Data trasfer
3. Data update
4. Get data

### Introduction of HTML

HTML stand for Hyper Text Markup Language.jo ki web page banane ka liye use hoti
hai. web page ek html file hoti hai jo kisi bhi web site me ek page ko repersant
karti hai. HTML ka use website bnane ke lie kia jata hai. Ek website kafi sare html pages ka group hota hai.

### Introduction of CSS

CSS stands for cascading style sheet. CSS ka use html page me styling krne ke liye kia jata hai like color, text formatting, responsiveness etc.

### Introduction of JavaScript

Javascript ek high level programming language hai jisko hum web me use karta hai. Javascript ki help se hum website ko intractive bana sakta hai for example button pr click krne pr koi action lena, animation etc. Phle javascript only web me use hoti thi lakin ab hum javascript ko beck-end me bhi use kar sakta hai. Javascript ko back-end me use karna ka leya node.js use me li jati hai.

### History of javascript

Brendan Eich ne 1995 me JavaScript ko bnaya tha. Javascript ko phle mocha name se jana tha, bad me iska naam live script hua or last ma Javascript hua kyo ki java language us time popular thi. ECMA is JavaScript ko 1997 me standar bnaya tha.

### What is ECMA ?

ECMA stands for European computer manufacture Association. ECMA script ek organization hai jo scripting language jaise ki javascript vah other scripting language jo ki web ke liye use hoti hai un ke liye standard banati hai. Koi bhi scripting language jise ki web ke lie bnaya jayega vah ECMAScript ke rules/standards follow kregi. ECMAScript ko short form me ES bhi bolte hain.

6 versions tak ES1, ES2, ES3, ES5, and ES6 kha jata hai pr bad vale versions ko year se jana jata hai like ECMAScript 2016, 2017, 2018, 2019, 2020.

Koi b web browser sare features ko support krta hai ya nhi iska b hume idea hona chaiye like kafi old browers latest features ko support ni krte hain.
versions :

1. es1=1997
2. es5=2009 ES5 ECMAScript ka first major version tha jisme ki kafi important features release kie gye. like use strict feature ES5 me release kia gya tha.
3. es6=2015 ES6 ECMAScript ka second major version tha. Jisme features like let, const, arrow fuctions etc release kiye gye the.
# 02 : JavaScript Features

### What is High level language?

High level programming language vah programming language hoti hai jise is trah se design kia gya hai ki us language ko asani se likha, pdha vah smja ja skta hai. High level language ek english like nature language ke equal hi hoti hai. High level language ko sikhna asan hota hai. High level language kafi sare actions aise hote hain jo vo khud manage kr leti hai aur hume ni krne hote hain. for example : 1) memory managemant. 2) communication with hardware

### What is Garbage Collected ?

Javascript ek garbage collected language hai. Garbage collected ka yha ye matlab hai ki Javascript engine me ek utility chalti hai jise garbage collector khte hain. Garbage collector unused memory ko free karta hai. yah automatically run hota hai. Garbage collector aise objects ko identify krta hai jinko program me ab access ni kia ja skta un objects ko memory se remove kr deta hai.

Memory size agar kam ho to garbage collector fast run hoga, aur agar memory size jyada hai to slow run hoga.

### What is Interpreted Language (JIT)-> (Just in time commpiler) ?

compiler: yeh ak utility hai jo kisi bhi code ko compile karti hai. Vah compile karne ka bad ek new file generate karta hai vah us file ko run karta hai.
Interpreter: Yeh ek utility hoti hai jo Java script ke code ko line by line run karti hai.
JIT: JavaScript compiler and Interpreter dono ka mixture hai. Yeh ek technique hai jise ki JavaScript engine ke dwara code ki performance improve krne ke lie kia jata hai. Code ko runtime pr compile krke uski performance ko improve krta hai. JIT vah code jo jyada use ho rha hai us code ka optimized machine code generate krta hai. Isse JavaScript ki performance kafi imporve hoti hai kuki optimized code original Interpreted JavaScript code se fast run hota hai.

### What is Multi Paradigm ?

Multi Paradigm ka matlb hai ki javascript different style of programming support karti hai. for example : 1) Object orinted programming 2) functional programming 3) event driven programming

### What Prototype based functions ?

Advanced topic. Will be covered in later files in detail.

### What is First Class Function ?

Advanced topic. Will be covered in later files in detail.

### What is Dynamically Typed/ Dynamic ?

Javascript ek Dynamically based language hai.iska mtlb yaha hai ki hum kisi variable me kisi b type ka data assign kar skte hain. Jis b type ka data hm variable me assign krte hain variable ki vahi type ho jati hai.

for example:

```
let x = 10; // type will be number
x = "learnjavascript"; //type will be string
x = false; //type will be boolean
```

### What is Single Threaded ?

JavaScript ek single threaded language hai. Thread ek process ka part hota hai. Jo ki independently within process run hota hai. Javascript ek sath ek sa jyada thread run nahi kar sakti iska mtlb hai ki javascript engine me kisi bhi time par ek hi thread run hogi.

### What is Non-Blocking Event Loop ?

Advanced topic. Will be covered in later files in detail.
# Separation of Concerns

### What is separation of concerns principle?

"Separation of Concerns" ek programming principle hai jisme developers ko apne code ko alag-alag sections mein divide karne ki salah di jati hai, jisme har section ka apna alag kaam hota hai. JavaScript mein ye principle alag-alag levels par apply kiya ja sakta hai jaise presentation aur content ko alag rakhna aur business logic ko user interface se separate karna.

Ek udaharan ke roop mein, maan lo ki aap ek web application bana rahe hain jisme users notes create aur edit kar sakte hain. Separation of concerns principle ko apply karne ke liye, aap apna code in sections mein divide kar sakte hain:

1. User interface: Is section mein application ke sabhi visual aspects handle kiye jaate hain jaise notes ko screen par dikhana aur unse interaction karne ki suvidha dena. Isme user input validation bhi handle ki jaati hai.

2. Business logic: Is section mein application ke behind-the-scenes logic ko handle kiya jaata hai jaise notes create, update, aur delete karna. Isme data validation bhi handle ki jaati hai.

3. Data storage: Is section mein notes ko database ya local storage mein store aur retrieve karna handle kiya jaata hai.

In concerns ko alag-alag rakhne se, har section ko independently develop aur maintain kar sakte hain, jisse code ko samajhna, test karna aur modify karna aasaan ho jata hai.

### How to link JavaScript file in html ?

JavaScript ko HTML mein link karne ke liye aapko <script> tag ka upyog karna hota hai. Yahan par main ek example share kar raha hoon jis mein main ek JavaScript file ko HTML page ke sath link kar raha hoon:

1. Sabse pehle aapko apna JavaScript file ko create karna hoga. Aap iske liye notepad, Visual Studio Code ya kisi bhi text editor ka upyog kar sakte hain.

2. Jab aap apna JavaScript file create kar lete hain, tab aapko usko save karna hoga. Aapko file name ke end mein ".js" extension add karna hoga. Jaise ki "script.js".

3. Ab HTML page ko open karein aur head section mein <script> tag ka upyog karein. Iske baad src attribute mein apne JavaScript file ka path dena hoga. Yeh path relative ho sakta hai ya absolute bhi ho sakta hai.

4.Yahan par maine ek JavaScript file "script.js" banaya hai aur use "index.html" mein link kiya hai.

```javascript
<!DOCTYPE html>
<html>
<head>
	<title>JavaScript file ko HTML se link kaise karein</title>
	<script src="script.js"></script>
</head>
<body>
	<h1>Welcome to my website</h1>
</body>
</html>
```

Is example mein, humne <script> tag ka upyog kiya aur usmein src attribute mein "script.js" ka path diya hai. Agar script.js file index.html file se alag folder mein hai toh aapko path ko accordingly update karna hoga.
# 03 : Value, Variable and Data Types

### What is Data type:

Data type kisi bhi data ki type btata hai ki vah data kis type ka hai. Data type two type ka hota hai. Data types 2 type ki hoti hain:
primitive data type
non-primitive data type

### Primitive data types (inbuilt data types):

Primitive data type vah data type hoti hai jo kisi bhi programming language me pre define data type hoti hai. Yeh data types Javascript ke building blocks and direct memory me store hoti hain. Primitive data types immutable hoti hain it means inhe change ni kia ja skta hai.

1. number: Javascript me kisi bhi number ka liye number data type use hoti hai.
2. String: Javascript me kisi bhi word, text, ya paragraph/sentence ka liye string data type ka use hota hai.
3. undefined: kisi bhi variable ko koi bhi data nhi assign kiya hai to us variable
   ki data type undefined hogi
4. boolean: boolean data type vah data store krane ke kaam aati hai jiski value true/false ho. true aur false ko 1 and 0 se b represent krte hain.
5. BigInt: BigInt vah data type hota hai jo bahut big number ka leya use hota hai. Aise numbers jo number datatype me store ni hote hain.

### Non primitve (reference types) data types:

Non primitive data type ko reference data types b kha jata hai. Ye data types primitive data type se hi bni hoti hai. But in Non primitive data type ko user khud define karta hai. Non primitve data type me hum different type ka data store kar saktay hai.

1. object
2. array
3. functions
4. Dates
5. Regular expressions
6. Maps
7. Sets
8. WeakMap

### Value and Variable:

Value ka matlab data hota hai. Jise hum kisi variable me store krate hain. Variable ek place holder ki trah hota hai jisme ki hum value store krte hain and jha b vo value use krni ho to value ki jgah variable use kr skte hain. variable ek identifire hota hain. identifier ek unique name hota hai.

for example:

```javascript
let x = 10; //10 is value and x is variable
```

### Primitive Data Types Examples:

- Number

```javascript


let value = 10; `

```

- Boolean

```javascript
let flag = false;
```

- String

```

let str = "learnjavascript";

```

- undefined

```

let val; //value will be undefined here
val = undefined; //we can also assign undefined to a variable

```

- Symbol

```javascript
let sym = Symbol("A");
```

- BigInt

```javascript
let num = BigInt(10);
num = 10n;
```

### Non Primitive Data Type Examples:

- Object

```javascript
let obj = {
  myName: "learnjavascript",
  age: 21,
};
```

- Array

```javascript
let arr = [1, 2, 3, 4, 5];
```

- function

```javascript
function sum() {
  console.log(1 + 2);
}
```

- Date

```javascript
let date = new Date();
```

- Regex example

```javascript
let str =
  "I love learning javascript, it's one of my favorite programming languages!";
let regex = /javascript/gi;
let result = str.match(regex);
console.log(result);
// Output: ["javascript", "javascript"]
```

- Maps

```javascript
let map = new Map();
```

- Set

```javascript
let set = new Set();
```

- WeakMap

```javascript
let wm = new WeakMap();
let obj1 = {};
let obj2 = {};

wm.set(obj1, "value1");
wm.set(obj2, "value2");

console.log(wm.get(obj1)); // Output: "value1"
console.log(wm.get(obj2)); // Output: "value2"
```
# 04 : Identifiers

### Identifiers:

JavaScript me Identifiers names hote hain jo ki kisi variables, functions, class ko name dene ke lie use kia jata await.

for example:

```javascript
let value = 10; //value is an identifer

//sum is an identifier here
function sum(a, b) {
  console.log(a + b);
}
```

### Rules for creating identifier:

JavaScript me identifiers case sensitive hote hain. Case sensitive ka matlab ye hai ki small ya capital letter agar identifier me use kia hai to vhi name fir hum aage use krenge. for example abc and ABC same ni hai.

indentifier bnane ke lie $, \_, and digits (0-9) ka use hota hai but variable name digit se start ni ho skta hai.

- Invalid Identifier examples

```javascript
let 12x = 10;
let &value = 10;
```

- Valid Identifier examples

```javascript
let x12 = 10;
let _value = 20;
let $_value = 100;
```
# 05 : Comments

### Comment

kisi bhi code ke bare me notes/detail likhne ke lie ya explanation likhne ke lie comment ka use karte hain. for example code kis date ko likha gya, code kisne likha, yeh code kis lie likha gya etc comments me likha jata hai.

Code ko explain krne se other developers ko complext logic/code samaj aa jata hai. Koi b commented code run ni hota hai and interpreter b us code ko ignore krta hai. Isi trah yadi hum testing krte time kisi code ko comment krna chahte hain to kr skte hain.

Comments 2 types ke hote hain:

- Single-line comments (Jo ki kisi line ko ya line ke kisi hisse ko comment krne ke kaam aata hai)
- multi-line comments (Jiska use kisi code block ko comment krne ke lie hota hai).

Example of Single line Comment: Single line comment 2 forward slashes / ke sath start hota hai and aur us puri line ko end tak comment kr deta hai

```javascript
// This is a single-line comment
```

Example of Multi line comment: Multi comment forward slash and _ asterisk ke sath start hota hai aur _ asterisk and forward slash ke sath end hota hai.

```javascript
/* This is a
multi-line comment */
```
# Statement

### What is Statement

जावास्क्रिप्ट में स्टेटमेंट एक आदेश होता है जो कंप्यूटर को बताता है कि क्या अपने कोड में करना है। यह एक लाइन में हो सकता है या एक ब्लॉक में, जो एक समूह के रूप में काम करते हैं।

कुछ स्टेटमेंट उदाहरण निम्नलिखित हैं:

```javascript
let x = 5; // एक वेरिएबल बनाना और उसे 5 के बराबर सेट करना।
console.log("Hello world!"); // "Hello world!" कंसोल पर प्रिंट करना।
if (x > 3) {
  // अगर x 3 से बड़ा है तो निम्नलिखित कोड को चलाना।
  console.log("x is greater than 3");
}
```

इस उदाहरण में, `let` एक स्टेटमेंट है जो `x` नाम की एक वेरिएबल बनाता है और उसे 5 के बराबर सेट करता है। `console.log()` भी एक स्टेटमेंट है जो "Hello world!" स्ट्रिंग को कंसोल पर प्रिंट करता है। `if` स्टेटमेंट एक ब्लॉक में होता है जो अगर `x` 3 से बड़ा है तो `console.log()` स्टेटमेंट को चलाता है जो "x is greater than 3" स्ट्रिंग को कंसोल पर प्रिंट करता है।

### What is Semicolon

Semicolon ka matlab hai 'sentence khatam'. Javascript mein, semicolon ek punctuation mark hai jo batata hai ki ek sentence khatam ho gaya aur dusra shuru ho raha hai. Semicolon ka upyog statements ko samapt karne ke liye hota hai. Jab bhi hum ek statement ko likhte waqt uski ant mei semicolon laga dete hai, toh woh statement complete hoti hai. Yeh interpreter ko batata hai ki ab ek naya statement shuru hone wala hai.

For example, consider the following code:

```javascript
var x = 5;
var y = 7;
console.log(x + y);
```

```javascript
var x = 5;
var y = 7;
console.log(x + y);
```

Explicitly using semicolons is considered good practice because it makes the code more readable and less prone to errors.

### What is WhiteSpace in statement

WhiteSpace refers to the space characters, tabs, and newline characters in a piece of code that don't have any effect on the functionality of the code. In JavaScript, WhiteSpace can be used to improve the readability and organization of code.

Let's take an example:

```javascript
let name = "John";
if (name === "John") {
  console.log("Hello, John!");
}
```

In this example, there are spaces and new lines between the code that don't have any effect on its functionality. We can remove those whitespaces and rewrite the same code as follows:

```javascript
let name = "John";
if (name === "John") {
  console.log("Hello, John!");
}
```

This code works exactly the same way as the code with white spaces, but it's harder to read and understand.

Whitespace can also be helpful for aligning code and making it more visually appealing. For example:

```javascript
function addNumbers(num1, num2) {
  return num1 + num2;
}

let sum = addNumbers(5, 7);
console.log(sum);
```

In this example, we use whitespace to align the parameters in the function definition and to separate the different statements. This makes the code easier to read and understand.

To summarize, Whitespaces are unnecessary characters in the code that don't affect its functionality but make it more readable and organized.

### What is Code block or Multi-line statement?

Code block ya multi-line statement ek ese code ka group hota hai jisme multiple statements (commands) ko ek sath likha ja sakta hai. Iska use complex tasks ko simplify karne ke liye kiya jata hai taki aapko bar-bar same code likhne ki jarurat na pade.

Iska format aam tor par curly brackets { } se define kiya jata hai, jaha ek bracket se code block start hota hai aur dusre bracket se end hota hai. Jaise:

```javascript
if (x > 5) {
  print("x is greater than 5");
  x = x + 1;
}
```

Upar wale example me, `if` statement ke andar code block define kiya gaya hai, jisme do statements hain: "x is greater than 5" ko print karna aur variable `x` ko 1 se zyada kar dena.

Code block ka use loops, functions, conditional statements jaise bahut se programming concepts me hota hai.
# 06 : Use strict

### What is use strict ?

by defult javascriot non strict way ma run hota hai.iska mtlb yaha hai ki javascript non strict mood ma kuch error ko ignore kar ta hai.for example:

```javascript
x = 10;
console.log(x);
```

hum same code ko strict mood ma run kartay hai to error ayagi code strict mood ma
run karnay ka leya "use strict" ka use hota hai

use strict ko hama frist line ma use kar na hota hai.
```javascript
let x = 10;

const y = 20;

var z = 30;
```

# ==========let==========

let:iska use variable declertion ka leya kiya jata hai.let variable ko declertion sa phala use nahi kar sktay.let ma value re assign kar sktay hai.let ko redeclere nahi kar sktay.for example:

- for example

```javascript
let x = 10;
x = 20;
console.log(x);
```

- SyntaxError: 'x' has already been declared

# ==========const==========

const keyword ka use constand variable bananay ka leya kiya jata hai hai.const vha variable hota hai jis ki value change nahi kar sktay hai.const variable ko declertion sa phala use nahi kar sktay.

- for example

```javascript
const x = 10;
x = 20;
console.log();
```

- typeErroe:this will also give an error

# ==========var==========

var variable let variable ki trha hi kam karta hai.lakin var or let ma kuch defrience hai.
var ko decleration sa phala use kar sktay hai.var ko redecler bhi kar sktay hai.

- for example

```javascript
console.log(val);
var val = 300;
```

- allowed and value will be undefined here
# Operators

Operators JavaScript mein aise symbols hote hain jo values ko manipulate karne ke liye use kiye jaate hain. Kuch common operators include arithmetic, comparison, logical, bitwise, assignment, and ternary operators.

Arithmetic operators math calculations ke liye use kiye jaate hain jaise:

```js
let x = 10;
let y = 3;

console.log(x + y); // Addition
console.log(x - y); // Subtraction
console.log(x * y); // Multiplication
console.log(x / y); // Division
console.log(x % y); // Remainder
console.log(x ** y); // Exponentiation
```

Comparison operators values ko compare karne ke liye use kiye jaate hain jaise:

```js
let x = 10;
let y = 3;

console.log(x > y); // Greater than
console.log(x < y); // Less than
console.log(x >= y); // Greater than or equal to
console.log(x <= y); // Less than or equal to
console.log(x == y); // Equal to
console.log(x != y); // Not equal to
console.log(x === y); // Strict equal to
console.log(x !== y); // Strict not equal to
```

Logical operators boolean values ke saath kaam karte hain jaise:

```js
let x = 10;
let y = 3;

console.log(x > 5 && y < 7); // AND
console.log(x > 5 || y > 7); // OR
console.log(!(x > y)); // NOT
```

Bitwise operators binary representation of numbers ke liye use kiye jaate hain jaise:

```js
let x = 10; // Binary representation: 1010
let y = 3; // Binary representation: 0011

console.log(x & y); // Bitwise AND
console.log(x | y); // Bitwise OR
console.log(x ^ y); // Bitwise XOR
console.log(~x); // Bitwise NOT
console.log(x << 1); // Left shift
console.log(x >> 1); // Right shift
console.log(x >>> 1); // Unsigned right shift
```

Assignment operators variables ko assign karne ke liye use kiye jaate hain jaise:

```js
let x = 10;

x += 5; // Same as x = x + 5;
x -= 5; // Same as x = x - 5;
x *= 5; // Same as x = x * 5;
x /= 5; // Same as x = x / 5;
x %= 5; // Same as x = x % 5;
x **= 5; // Same as x = x ** 5;
x &= 5; // Same as x = x & 5;
x |= 5; // Same as x = x | 5;
x ^= 5; // Same as x = x ^ 5;
x <<= 5; // Same as x = x << 5;
x >>= 5; // Same as x = x >> 5;
x >>>= 5; // Same as x = x >>> 5;
```

Ternary operator if-else statement ka ek shorthand version hai jaise:

```js
let age = 18;

let status = age >= 18 ? "Adult" : "Minor";

console.log(status); // Adult
```

Is tarah se, JavaScript mein bahut saare operators hote hain jo values ko manipulate karne ke liye use kiye jaate hain.

### Arithmetic Operators

Arithmetic operators in JavaScript are symbols or characters used to perform mathematical operations on numeric values.

There are five arithmetic operators in JavaScript:

1. Addition operator (+) - This operator adds two or more values and returns the sum.

Example:

```
let x = 10;
let y = 5;
let z = x + y;   // z will be 15
```

2. Subtraction operator (-) - This operator subtracts one value from another and returns the difference.

Example:

```
let x = 10;
let y = 5;
let z = x - y;   // z will be 5
```

3. Multiplication operator (\*) - This operator multiplies two or more values and returns the product.

Example:

```
let x = 10;
let y = 5;
let z = x * y;   // z will be 50
```

4. Division operator (/) - This operator divides one value by another and returns the quotient.

Example:

```
let x = 10;
let y = 5;
let z = x / y;   // z will be 2
```

5. Remainder operator (%) - This operator returns the remainder of a division operation.

Example:

```
let x = 10;
let y = 3;
let z = x % y;   // z will be 1
```

Arithmetic Operators JavaScript mein wo symbol ya character hote hain jinka prayog sankhyatmak maan ko ganitik karyon ke liye kiya jaata hai. Ismein paanch operators hote hain - Jodne ka operator (+), Ghataane ka operator (-), Gunank ka operator (\*), Bhag ka operator (/) aur Shesh ka operator (%). Inka prayog sankhyatmak maano ko jodne, ghataane, guna karne, bhag karne aur shesh nikalne ke liye kiya jaata hai.

### Comparison Operators

Comparison Operators in JavaScript are used to compare two values and return a Boolean value (true or false) depending on whether the comparison is true or false. There are several comparison operators in JavaScript, including:

1. == : This operator checks if two values are equal to each other, regardless of their data types.
   Example:

```
var x = 10;
console.log(x == '10'); // Output: true
```

2. === : This operator checks if two values are equal to each other AND have the same data type.
   Example:

```
var x = 10;
console.log(x === '10'); // Output: false
```

3. != : This operator checks if two values are not equal to each other, regardless of their data types.
   Example:

```
var x = 10;
console.log(x != '5'); // Output: true
```

4. !== : This operator checks if two values are not equal to each other OR do not have the same data type.
   Example:

```
var x = 10;
console.log(x !== '10'); // Output: true
console.log(x !== 10); // Output: false
```

5. > : This operator checks if one value is greater than another.
   > Example:

```
var x = 10;
console.log(x > 5); // Output: true
```

6. < : This operator checks if one value is less than another.
   Example:

```
var x = 10;
console.log(x < 5); // Output: false
```

7. > = : This operator checks if one value is greater than or equal to another.
   > Example:

```
var x = 10;
console.log(x >= 10); // Output: true
```

8. <= : This operator checks if one value is less than or equal to another.
   Example:

```
var x = 10;
console.log(x <= 5); // Output: false
```

Comparison Operators can be explained as "bandhu-tulyakari sangathan" or "samanta-kari sangathan" that help you compare two values and give a response in the form of "haan" (true) ya "na" (false) depending on the comparison being true or false.

### Logical Operators

Logical operators in JavaScript are used to combine multiple conditions and evaluate them as a single expression. There are three logical operators in JavaScript:

1. && (AND) operator: This operator returns true if both conditions are true, otherwise, it returns false.

Example:

```javascript
let num = 5;
if (num > 0 && num < 10) {
  console.log("The number is between 0 and 10.");
}
```

In this example, the condition inside if statement will return true if `num` is greater than 0 AND less than 10, so the message "The number is between 0 and 10." will be printed.

2. || (OR) operator: This operator returns true if at least one of the conditions is true, otherwise, it returns false.

Example:

```javascript
let name = "";
let age = 20;
if (name || age > 18) {
  console.log("You can enter the site.");
}
```

In this example, the condition inside if statement will return true if `name` is not empty OR `age` is greater than 18, so the message "You can enter the site." will be printed.

3. ! (NOT) operator: This operator reverses the boolean value of the condition. If the condition is true, then it returns false, and vice versa.

Example:

```javascript
let loggedIn = false;
if (!loggedIn) {
  console.log("Please login first.");
}
```

In this example, the condition inside if statement will return true if `loggedIn` is false (i.e. NOT true), so the message "Please login first." will be printed.

logical operators JavaScript mein use hote hain multiple conditions ko ek hi expression ke roop me milane ke liye aur unhe evaluate karne ke liye. Ismein teen operators hote hain: AND (&&), OR (||) aur NOT (!). AND operator true tab return karta hai agar dono conditions true hain, nahi toh false. OR operator true tab return karta hai agar kam se kam ek condition true hai, nahi toh false. NOT operator boolean value ko reverse karta hai, agar condition true hai toh false return karta hai aur agar false hai toh true.

### Assignment Operators

Assignment Operators in JavaScript are used to assign values to variables. These operators combine the assignment operation with another operation, such as addition, subtraction, multiplication, or division.

For example, consider the following code:

```
let x = 5;
x += 3;
console.log(x);
```

In the above example, the `+=` operator is an assignment operator that combines the addition operation with the assignment operation. It adds 3 to the value of `x` (which is 5), and then assigns the result (8) back to `x`. So, when we log `x` to the console, it prints 8.

Similarly, we can use other assignment operators like `-=` for subtraction, `*=` for multiplication, `/=` for division, etc.

Example:

```
let a = 10;
a -= 2; // Subtract 2 from a and assign the result back to a
console.log(a); // Output: 8

let b = 5;
b *= 3; // Multiply b by 3 and assign the result back to b
console.log(b); // Output: 15

let c = 20;
c /= 4; // Divide c by 4 and assign the result back to c
console.log(c); // Output: 5
```

Assignment operators are a shorthand way of writing more readable and concise code. They save us from having to write repetitive code and make it easier to perform arithmetic operations on variables.

### Typeof operators

Typeof ka operator JavaScript mein data type ko identify karne ke liye istemal hota hai. Isse hum yeh pata laga sakte hain ki kisi bhi variable ki value kis data type mei hai.

Iska syntax hai: `typeof operand`

Jahan 'operand' kisi variable ya expression ho sakta hai jo check karna hai uska data type.

For example:

```
let num = 10;
let str = "Hello";
let bool = true;

console.log(typeof num); // output: "number"
console.log(typeof str); // output: "string"
console.log(typeof bool); // output: "boolean"
```

Iss code mei humne `typeof` ka operator use kiya hai jisse humne `num`, `str`, aur `bool` variables ke data types determine kiye hain. Jaise ki hum dekh sakte hain, `num` ka data type number hai, `str` ka data type string hai, aur `bool` ka data type boolean hai.

Agar hum `typeof` ka operator non-existent variable par use karenge toh uska output `"undefined"` hoga.

For example:

```
console.log(typeof x); // output: "undefined"
```

Iss code mei humne `x` naam ka koi bhi variable define nahi kiya hai, isliye `typeof x` ka output `"undefined"` hai.

### Operator precedence

JavaScript Operator Precedence refers to the order in which operators are evaluated in an expression. It is important to understand this order because it can affect the outcome of an expression.

Operators with higher precedence are evaluated first, followed by those with lower precedence. For example, multiplication has higher precedence than addition, so the expression `3 + 4 * 5` will be evaluated as `3 + (4 * 5)` which equals 23.

Here's a table showing the operator precedence in JavaScript, from highest to lowest:

| Precedence | Operator                                | Description              |
| ---------- | --------------------------------------- | ------------------------ |
| 1          | ()                                      | Parentheses              |
| 2          | ! ~ + - ++ -- typeof void               | Unary operators          |
| 3          | \* / %                                  | Multiplicative operators |
| 4          | + -                                     | Additive operators       |
| 5          | << >> >>>                               | Bitwise shift operators  |
| 6          | < <= > >= instanceof                    | Relational operators     |
| 7          | == != === !==                           | Equality operators       |
| 8          | &                                       | Bitwise AND operator     |
| 9          | ^                                       | Bitwise XOR operator     |
| 10         | &#124;                                  | Bitwise OR operator      |
| 11         | &&                                      | Logical AND operator     |
| 12         | &#124;&#124;                            | Logical OR operator      |
| 13         | ? :                                     | Conditional operator     |
| 14         | = += -= \*= /= %= <<= >>= &= ^= &#124;= | Assignment operators     |

Let's consider an example:

```
var num1 = 10;
var num2 = 5;

var result = num1 + num2 * 2; // here the multiplication has higher precedence than addition

console.log(result); // Output: 20
```

In this example, the expression `num2 * 2` is evaluated first (giving us 10), and then added to num1, giving a result of 20.
# Why use conditinol statement:

Conditional statements different conditions ke base pr different actions perform krne ke lie use me aate hain

JavaScript me niche diye hue conditional statements use hote hain:

- if block ka use koi condition true hone pr jo code execute krna hai uske lie kia jata hai.

- else block ka use koi condition false hone pr jo code execute krna hai uske lie kia jata hai.

- Use else if to specify a new condition to test, if the first condition is false

```
let i = 10;
if (i < 20) {
  console.log("Yes");
}
```

For a conditional statement if block is mandatory, without if block we can not
write else if or else block. It means else if and else block are not mandatory.

```
if (i < 20) {
  console.log("Yes");
} else if (i === 10) {
  console.log("Yes 10");
} else {
  console.log("No");
}
```

- Grouping multiple conditions using logical operator && and ||

```
let j = 10;
let k = 20;
if ((j < 20 && k > 10) || j + 10 === 20) {
  console.log(true);
} else {
  console.log(false);
}
```

# ==========if==========

if statemant ka use tab hota jad hum sure ho ki condition true ha.false bhi ho skti
hai but normally true ka leya he use hota hai.

- Sayntax:

```
if (condition) {
console.log(true);
}

let marks = 100;
if (marks == 100) {
console.log("pass");
}
```

Conditional statements bananay ka leya if condition jaruri hai.if condition ka bad hum ak ya ak sa jyada else if add kar sktay hai.or last ma else add kar sktay hai.else if or else jaruri nahi hai.

# ==========if......else==========

else statemant ka use tab hota jad hum sure ho ki condition true ha.

- Sayntax:

```
if (condition) {
console.log(true);
} else {
console.log(false);
}
```

```
let x = 20;
if (x > 10) {
console.log(true);
} else {
console.log(false);
}
```
# Output

### What is console.log

"console.log" ek pre-defined method hai JavaScript mein, jo developers ko allow karta hai ki wo messages ya values ko console mein display kar sakein. Console jaisa ek command-line interface hota hai jahan se aap apne code ke output ko dekh sakte hain aur koi bhi error debug kar sakte hain. Jaise ki agar aapke paas ek variable hai "name" ke naam se jo ki string value "John" ko contain karta hai. Agar aap is value ko console mein display karna chahte hain to aap console.log ka upyog is tarah se kar sakte hain:

```
const name = "John";
console.log(name);
```

This will print the value "John" to the console.

```
const name = "John";
console.log(name);
```

Isse "John" ki value console mein print ho jayegi.

### What is document.write

Document.write ek JavaScript function hai jo kisi text ya HTML code ko webpage par display karne ke liye istemal kiya jaata hai. Is function ki madad se aap dinamically webpage par content add kar sakte hai jab user page ko load karta hai.

Example:
Agar aapko apne webpage par "Hello, World!" message show karna hai to aap document.write('Hello, World!'); likh sakte hai. Jab user aapke webpage ko load karega to usme yeh message display hoga.

Document.write ek JavaScript ka function hai jiski madad se hum kuchh bhi text ya HTML code ko website par dikha sakte hain. Yeh function tab kaam karta hai jab website load hota hai. Jaise agar hum "Hello, World!" ka message website mein dikhana chahte hain to hum document.write('Hello, World!'); likhenge aur jab website load hoga to yeh message dikhayi dega.

### What is window.alert

"Window.alert" is a function in JavaScript that displays an alert message box on the web page. The purpose of this function is to inform the user about certain actions or events occurring on the webpage.

For example, let's say you are developing a website where users need to fill out a form. You can use the "window.alert" function to inform them if they have left any field empty.

Here's how you can use window.alert in Hinglish language:

Suppose, you want to inform the user that they have successfully submitted a form. You can use the following code:

```
window.alert("Sukriya! Aapka form submit ho gaya hai.");
```

This will display an alert message box displaying the message "Sukriya! Aapka form submit ho gaya hai." and the user will have to click on the "OK" button to dismiss the message box.

Similarly, if you want to inform the user that they have left a field empty, you can use the following code:

```
window.alert("Kripya sabhi fields ko bharein.");
```

This will display an alert message box displaying the message "Kripya sabhi fields ko bharein." and the user will have to fill out all the required fields before submitting the form.

### What is innerHTML

InnerHTML ek JavaScript property hai jo ki kisi HTML element ke andar ke content ko access karne aur modify karne ke liye use kiya jata hai.

Jab hum innerHTML ka use karte hai, tab hum ek HTML element ke andar ke text, HTML tags aur attributes ko change kar sakte hai. Hum isko aise bhi samajh sakte hai ki innerHTML property ek element ke andar ka HTML code hi represent karta hai.

Ab ek example se samajhte hai - agar humein ek paragraph tag me text ko badalna hai to hum uss paragraph tag ke innerHTML property ko set kar sakte hai. Jaise:

```html
<p id="my-para">Hello World!</p>
```

```javascript
document.getElementById("my-para").innerHTML = "Namaste Duniya!";
```

Is example me humne `document.getElementById` method ka use kiya jisse hum my-para id wale paragraph tag ko select kar rahe hai, aur fir uske innerHTML property ko set karke uske text ko badal diya hai.

Iss tareeke se hum HTML elements ke content ko dynamically update kar sakte hai. Lekin dhyan rahe ki isse XSS (Cross-Site Scripting) attack ka risk bhi hota hai, isliye humein humesha sanitization aur validation ka dhyan rakhna chahiye.
### type conversion

implicit type conversion /automatic type conversion
implicit type conversion me javascript automatic ak type se dusri type me convert karte hain.

- for example
  number se string me conversion
  string se number me convrsion

```
let x = "20";
console.log(x / 2);
```

### Explicit type and manual type conversion is process me hum manualy type conversion karte hain.

```
let x = "20";
console.log(Number(x) + 20); // //string to number
```

```
let y = 10;
console.log(string(y) + 200); //number to string
```
### window.alert

yaha ak alert box declear karta hain.

- for example:

```
alert("hello world");
```

### prompt.alert

prompt.alert me ak value box hota hain.or 2 button hote hain ok or  cancel ka.
in value ko hum store krva skte hain.yadi value enter karne ke bad ok click karne ke
bajaye cancel pr click karte hain to value null hogi.

- for example:

```
let answer = prompt("What is your name ?");
console.log(answer);
```

### confirm box

confirm box me do button hote hain ok or cancel. ok button me click karne pr true answer
ata hain or cancel pr false ata hain.

- for example:

```
confirm("Are you sure?");
```
### loose equality operator(==)

Yaha do variable ko compair karta hain.pr compair karte time data type strictly check
nahi karta hain.or jha bhi possibal hota hain vaha automatic type conversion karke value
compair karta hain.

```
var x = 20;
var y = "20";
if (x == y) {
console.log(true);
} else {
console.log(false);
}
```

### strict equality operator(====)

Yaha 2 value ko strictly check karta hain.iska mtlb hain ke value ka sath sath data type
bhi check karta hain.

```
var x = "20";
var y = 20;
if (x === y) {
console.log(true);
} else {
console.log(false);
}
```

### type of operator

Yaha data type btata hain.data ke kon se type hai.

```
var x = 10;
console.log(typeof x); //number
x = "learnjavascript";
console.log(typeof x); //string
```

### ternory operator

Yadi if else me single line ka code hain to use ternory operator ke help se karte
hain

```
let x = 10;
x < 20 ? console.log("yes") : console.log("no");
```
### What is truthy and falsy value:

truthy value vah value hoti hain. jinka answer true hota hain.
falsy vah value hoti hain.jinka answer false hota hain.

- false
- 0 or -0 or 0n
- ""
- null
- undefined
- NaN

```
if (NaN) {
  console.log("Yes");
} else {
  console.log("No"); //answer because NaN is a falsy value
}
```

```
if (10) {
  console.log("Yes"); //answer because 10 is a truthy value
} else {
  console.log("No");
}
```
### What is loop

Loop ek programming construct hai jo ek block of code ko baar-baar execute karne ki permission deta hai. Ye ek aisa mechanism hai jiska use hum repetitive tasks ko asaani se solve karne ke liye karte hai.

Javascript mein 3 types ke loops hote hai: for loop, while loop, aur do-while loop.

For loop ka use jab karna hota hai jab humein ek list ya array ko iterate karna hota hai. For loop ke andar hum ek counter variable ka use karte hai jo humein bata hai ki loop kitni baar repeat hona hai. Yeh loop syntax ke andar 3 expressions hoti hai: initialization, condition, and update.

Example:

```
for (var i = 0; i < 5; i++) {
  console.log("Hello " + i);
}
```

Iss example mein, hum for loop ka use kar rahe hai jisse "Hello" string 0 se 4 tak print ho raha hai. Loop ke andar, humne ek counter variable "i" initialize kiya hai jiska starting value 0 hai, aur humne yeh bhi decide kiya hai ki yeh loop tab tak chalega jab tak "i" ki value 5 se kam hai, iske baad humne "i" ko increment kiya hai.

While loop ka use jab karna hota hai jab humein kisi task ko perform karte waqt ek condition ko check karna hota hai. While loop ke andar hum sirf ek condition statement dete hai jisse hum yeh decide karte hai ki loop continue hoga ya nahi.

Example:

```
var num = 0;
while (num < 5) {
  console.log("World " + num);
  num++;
}
```

Iss example mein, hum while loop ka use kar rahe hai jisse "World" string 0 se 4 tak print ho raha hai. Humne "num" variable ko initialize kiya hai, aur uski value zero rakhi hai. While loop ke andar, humne yeh decide kiya hai ki jab tak "num" ki value 5 se kam hai, tab tak loop continue kare. Har baar loop execute hone par hum "num" ko increment karte hai.

Do-while loop bhi while loop ki tarah hi hota hai, bas ek chhota sa difference hai ki do-while loop mei pehle code block execute hota hai phir condition check ki jaati hai. Iska matlab hai ki do-while loop ke andar ke code block atleast ek baar to execute hoga.

Example:

```
var i = 0;
do {
  console.log("Welcome " + i);
  i++;
} while (i < 3);
```

Iss example mein, hum do-while loop ka use kar rahe hai jisse "Welcome" string 0 se 2 tak print ho raha hai. Do-while loop ke andar, hum pehle "Welcome" string ko print karte hai, aur phir "i" variable ki value ko increment karte hai. Fir humne condition check ki hai ki kya "i" ki value 3 se kam hai ya nahi. Agar humara answer "true" hai to loop wapas se start hoga aur agar "false" hai to loop stop ho jayega.

Is tarah se loops ka use karke hum repetitive programming tasks ko asaani se solve kar sakte hai.

### What is for loop

For loop JavaScript mein ek tarah ka loop hai jiske dwara hum kisi array ya object ke andar ke har element ko access kar sakte hain. For loop ke ander ek counter variable hoti hai jo ki shuruat se lekar loop ke ant tak badhti rahti hai aur uske dwara hum har ek element ko access kar sakte hain.

For loop ka syntax yeh hai:

```
for (let i = 0; i < array.length; i++) {
  // code block to be executed
}
```

Yahan `let i = 0` ek counter variable hai jiska initial value 0 hai, `array.length` array ke length se compare kiya jaata hai aur `i++` loop ke har iteration ke baad counter ko increment karta hai.

Ab ek example lete hain jismein hum ek array ke saare elements ko console par print karenge:

```
const fruits = ["Apple", "Banana", "Orange"];

for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}
```

Yahan `fruits` ek array hai jismein hum 3 strings store kar rahe hain. For loop ke ander counter variable `i` hai jo 0 se shuruat karta hai aur `fruits.length` (yani 3) tak chalta hai. Har iteration ke baad hum `console.log(fruits[i])` ka use karke current index ki value console par print karte hain.

```
Apple
Banana
Orange
```

### What is for...of loop

"for...of" loop in JavaScript is a way to iterate over iterable objects like Arrays, Strings, Maps, Sets, etc. It is similar to the "for...in" loop, but it provides more concise and readable syntax for looping through elements in an array or other iterable objects.

To use the "for...of" loop, we first declare a variable to hold each element in the iterable object. Then, we use the "of" keyword followed by the iterable object to loop through its elements.

Here's an example of using "for...of" loop to loop through an array of numbers:

```javascript
const numbers = [1, 2, 3, 4];

for (const num of numbers) {
  console.log(num); // Output: 1, 2, 3, 4
}
```

In this example, we declared a constant variable "numbers" that holds an array of numbers. We then used "for...of" loop to iterate over each element of the "numbers" array, assigning each element to the variable "num", and logging it to the console.

Another example is to loop through a string:

```javascript
const str = "Hello World";

for (const char of str) {
  console.log(char); // Output: H, e, l, l, o, , W, o, r, l, d
}
```

In this example, we declared a constant variable "str" that holds a string value. We then used "for...of" loop to iterate over each character of the string, assigning each character to the variable "char", and logging it to the console.

In summary, "for...of" loop is a convenient way to iterate over the elements of an iterable object in JavaScript.

### What is for...in loop

"for...in" loop is a type of loop in JavaScript that allows you to iterate over the properties of an object. In simple terms, it helps you to loop through each key-value pair of an object and perform some action on them.

Here's an example in Hinglish:

Suppose you have a dictionary (object) with multiple words and their meanings. You want to loop through every word and print its meaning. Here's how you can use "for...in" loop to achieve this:

```
// Define the dictionary object
var dictionary = {
  "apple": "seb",
  "banana": "kela",
  "orange": "santara"
};

// Loop through each word in the dictionary object
for (var word in dictionary) {

  // Print the word and its meaning
  console.log(word + " ka arth hai " + dictionary[word]);
}
```

In this example, we define an object called "dictionary" with three key-value pairs. We then use a "for...in" loop to loop through each key-value pair in the object. Inside the loop, we print the word and its meaning using the "console.log()" function. The output of this program will be:

```
apple ka arth hai seb
banana ka arth hai kela
orange ka arth hai santara
```

So, the "for...in" loop is a very useful construct in JavaScript for iterating over the properties of an object. It is particularly helpful when you need to work with data stored in objects.

### What is while loop

While loop JavaScript mein ek aisa loop hai jo ek shart ko check karta hai aur jab tak wo shart true rahe, tab tak loop chalta rehta hai.

Is loop ke andar code block ko ek baar bhi nahi chalaya jata hai agar shart hi false hoti hai. While loop ka syntax neeche diya gaya hai:

```
while (shart) {
  // Code Block
}
```

Yahan "shart" ek boolean expression hai, jo true ya false ho sakta hai. Aur "Code Block" ek set of statements hai jo execute hote rahtey hai jab tak shart true rahti hai.

Example:

```
let i = 1;
while (i <= 5) {
  console.log(i);
  i++;
}
```

Iss example mein humne ek variable "i" create kiya aur ek while loop ka use kiya jo "i" ki value 5 se kam hone tak chalta rehta hai. Har baar "i" ki value print hoti hai aur phir "i" ki value 1 se badhaya jaata hai. Jab "i" ki value 6 ho jaati hai to loop khatam ho jaata hai.

Iska output hoga:

```
1
2
3
4
5
```

### What is do...while loop

Do...while loop ek aisa loop hai jo kisi bhi code block ko baar-baar execute karta hai jab tak ki uske condition ka result true na ho. Yeh loop pehle code block ko execute karta hai aur phir condition check karta hai. Agar condition true hoti hai to loop continue rahta hai, lekin agar condition false hoti hai tab bhi code block ko kam se kam ek baar execute kar diya jaata hai.

Ek example ke through samajhte hain:

```
var i = 1;
do {
  console.log(i);
  i++;
} while (i <= 5);
```

Is code mein `i` ki value 1 se start hogi aur do..while loop ke andar code block ko execute karne ke baad `i` ki value 1 se 2 ho jayegi. Phir condition check hoti hai ki kya `i` ki value 5 se choti ya barabar hai? Kyunki yeh condition abhi true hai, isliye loop 2nd iteration ke liye chalta rahega aur `i` ki value 3 ho jayegi. Iss tarah se loop ke har iteration mein `i` ki value badhti rahegi jab tak ki `i` ki value 5 na ho jaye. Jab `i` ki value 6 ho jati hai, to condition false ho jati hai aur loop se bahar nikal jata hai.

Iss tarah se do..while loop ek baar to code block ko execute karta hi hai chahe condition true ho ya false ho.

### What is Switch Statment

Switch statement in JavaScript is a conditional statement that allows you to evaluate an expression and execute different code blocks based on the value of that expression. It's a way to simplify writing multiple if/else statements.

For example, let's say you have a variable called "dayOfWeek" that contains a string representing the day of the week. You want to perform different actions depending on the value of "dayOfWeek". Instead of using multiple if/else statements, you can use a switch statement:

```
var dayOfWeek = "Monday";

switch (dayOfWeek) {
  case "Monday":
    console.log("It's Monday, time to start the week!");
    break;
  case "Tuesday":
    console.log("It's Tuesday, still a long way to go...");
    break;
  case "Wednesday":
    console.log("It's Wednesday, halfway there!");
    break;
  case "Thursday":
    console.log("It's Thursday, almost done!");
    break;
  case "Friday":
    console.log("It's Friday, yay weekend!");
    break;
  default:
    console.log("Invalid day of the week.");
}
```

In this example, the switch statement evaluates the value of the "dayOfWeek" variable and executes the code block corresponding to the matching case label. If there is no match, the default case is executed.

So, if "dayOfWeek" is "Monday", the output will be "It's Monday, time to start the week!". If "dayOfWeek" is "Saturday", the output will be "Invalid day of the week." because there is no matching case label.

Switch statements are useful when you have a large number of conditions to check and want to avoid writing nested if/else statements.

### What is case clause

"Case clause" (केस क्लॉज) जावास्क्रिप्ट में एक संरचना है जो switch ब्लॉक के अंदर इस्तेमाल की जाती है। यह एक conditional statement है, जो switch block में निर्दिष्ट value को evaluate करती है और शर्तों के आधार पर उपयुक्त code block को execute करती है।

जब switch block की expression की value किसी एक case के value से match करती है, तो उस case के अंदर का code block execute होता है। अगर कोई case match नहीं होता है, तो default case का code block execute होता है।

इसका syntax निम्नलिखित है:

```
switch (expression) {
  case value1:
    //code block
    break;
  case value2:
    //code block
    break;
  case value3:
    //code block
    break;
  default:
    //code block
}
```

यहाँ expression value को evaluate करने के लिए है जो case के values से match करती हैं। अगर expression किसी bhi case value से match करता है, तो उस case का code block execute होता है। इसके बाद break statement से execution control switch block से बाहर निकल जाता है।

example

```
let day = "Monday";
switch (day) {
  case "Sunday":
    console.log("Today is Sunday");
    break;
  case "Monday":
    console.log("Today is Monday");
    break;
  case "Tuesday":
    console.log("Today is Tuesday");
    break;
  default:
    console.log("Today is some other day");
}
```

इस example में, variable 'day' की value "Monday" है, इसलिए switch block में वह "Monday" case से match होती है। इसलिए उस case के अंदर का code block execute होता है और निम्न output print होता है:

```
Today is Monday
```

### What is break

Break ka matlab hai ek code block se bahar nikalna. Jab tak hum break na use karein, tab tak loop ya switch statement continue hote rahenge.

Ek example ke through samjhate hain:

```
for (let i = 1; i <= 5; i++) {
  console.log(i);
  if (i === 3) {
    break;
  }
}
```

Iss code mein, hum for loop ka use karke 1 se 5 tak ke numbers ko print kar rahe hai. Lekin jab `i` ki value 3 ho jaati hai toh humne `break` ka use kiya hai, jisse ki loop uss point pe hi stop ho jaata hai aur aage nahi chalta.

Agar hum issi code ke bina break ka use karte toh output yeh hota:

```
1
2
3
4
5
```

Lekin humne break ka use kiya hai jab `i` ki value 3 ho jaati hai, isliye output yeh hoga:

```
1
2
3
```

### What is default case in a Switch Statement ?

Switch Statements are used in programming languages to execute different blocks of code based on the value of an expression.

The default case is a branch in a switch statement that is executed when no other case matches the value of the expression. It is like a catch-all clause in a try-catch block.

For example, let's say we have a variable called "dayOfWeek" which represents the day of the week (1 for Sunday, 2 for Monday, and so on) and we want to print a message depending on the day of the week:

```
int dayOfWeek = 3;
switch(dayOfWeek){
    case 1:
        System.out.println("Today is Sunday");
        break;
    case 2:
        System.out.println("Today is Monday");
        break;
    //... cases for other days of the week
    default:
        System.out.println("Invalid day of the week");
}
```

we could say that the default case is like a "baki sab" option in a switch statement. It is executed when none of the other options match the given value.
### What is String

Javascript mein, String ek primitive data type hai jo text ko represent karta hai. Har string ek sequence of characters hoti hai aur ek quotation mark (' ' aur " ") ke beech mein define ki jati hai.

Jaise ki,

```
var naam = 'Amit'; // single quotes mein string ko define kiya gaya hai
var message = "Main aaj khush hoon."; // double quotes mein string ko define kiya gaya hai
```

Ismein, `naam` aur `message` variables string values store kar rahe hai.

String mein characters indexes ke dwara access kiye ja sakte hai. Index 0 se start hota hai aur string.length - 1 tak chalta hai. Iske alawa, hum strings ko concatenate (combine) kar sakte hai `+` operator se.

Jaise ki,

```
var firstName = 'Amit';
var lastName = 'Kumar';
var fullName = firstName + ' ' + lastName; // Concatenate karne ke liye '+'' operator ka use kiya gaya hai.
console.log(fullName); // Output: Amit Kumar
```

Yahan, `fullName` variable `firstName` aur `lastName` strings se combined hai. Hum yeh bhi dekh sakte hai ki space `" "` concatenate karne ke liye bhi use kiya gaya hai.

In summary, String ek primitive data type hai jo text ko represent karta hai. Har string ek sequence of characters hoti hai aur quotation marks ke beech mein define ki jaati hai. Strings ko index ke dwara access kiya ja sakta hai aur concatenate karne ke liye `+` operator ka use kiya jaa sakta hai.

### How to create String

JavaScript mein ek string banane ke liye hum " " ya fir ' ' (single quotes) ka use karte hain. Jaise ki:

```
var str1 = "Hello";
var str2 = 'world';
```

Yahan humne do variables `str1` aur `str2` banaye hain jo ek-ek string hai. `str1` mein "Hello" string hai aur `str2` mein "world".

Agar aapko kuch bhi double quote (" ") ke andar likhna hai jaisa ki `"I'm a string"` toh aap use single quote (' ') ke andar wrap kar sakte hain. Jaise ki:

```
var str3 = 'I\'m a string';
```

Yahan humne `\` ka use kiya hai taaki string mein single quote ka use kar sakein.

Hum multiple strings ko concatenate bhi kar sakte hain, jisse ek naya string banega. Jaise ki:

```
var greeting = str1 + ', ' + str2 + '!'; // Output: Hello, world!
```

Yahan `+` operator ka use kiya gaya hai do strings ko concatenate karne ke liye. `greeting` variable mein ab "Hello, world!" string hai.

Is tarah se hum JavaScript mein strings create kar sakte hain.

### String Literal vs String Object ?

String Literal aur String Object dono tarah ke string hote hai, lekin unke banane ka tarika alag hota hai.

String Literal ek aisa string hai jo code mein directly declare kiya jata hai, aur use double quotes (" ") ya single quotes (' ') ke beech mein likha jata hai. Jab hum isse banate hai to iska ek reference bhi ban jata hai. Jaise:

```
String literal = "Hello World!";
```

String Object ek aisa string hai jo hum new keyword se create karte hai. Ismein humein ek object banaana padta hai jo ki String class ka object hota hai. Jaise:

```
String object = new String("Hello World!");
```

Dono hi tareeke se banaye gaye string mein same value hai, lekin inki memory allocation aur usage mein antar hota hai. Jab hum string literal banate hai to uska reference pool me store ho jaata hai (jise String Constant Pool kehte hai) aur jab hum dusri jagah se usi literal ko use karte hai to woh phele se stored reference ko point karta hai. Lekin jab hum string object banate hai to har baar naya object ban jata hai aur alag-alag memory allocation hoti hai.

Upar diye gaye examples ko hinglish mein likhenge to yeh aise dikhega:

```
// String Literal
String literal = "Hello World!";

//String Object
String object = new String("Hello World!");
```

### String length property

"String length property" refers to the number of characters in a string. It is a built-in property of the String object in JavaScript and can be accessed using the ".length" syntax.

For example, consider the following code:

```
var name = "sajid";
console.log(name.length); // Output: 5
```

In this code, we have defined a variable "name" with the value "sajid". We then use the ".length" property to find out the length of the string "name", which is 5.

Similarly, we can use the ".length" property to find out the length of any string, as shown below:

```
var message = "Namaste dosto!";
console.log(message.length); // Output: 14
```

Here, we have defined a variable "message" with the value "Namaste dosto!". We then use the ".length" property to find out the length of the string "message", which is 14.

इसका मतलब होता है कि "String length property" एक स्ट्रिंग में उपलब्ध वर्णों की संख्या को दर्शाता है। यह JavaScript में String ऑब्जेक्ट की बिल्ट-इन property होती है और ".length" का syntax उपयोग करके इसे एक्सेस किया जा सकता है।

एक उदाहरण के रूप में, निम्नलिखित कोड का विवरण दिया गया है:

```
var name = "ChatGPT";
console.log(name.length); // Output: 7
```

इस कोड में, हमने एक वेरिएबल "name" को "ChatGPT" के साथ परिभाषित किया है। फिर हम ".length" property का उपयोग करके "name" स्ट्रिंग की लंबाई पता लगाते हैं, जो 7 है।

इसी तरह, हम किसी भी स्ट्रिंग की लंबाई का पता लगाने के लिए ".length" property का उपयोग कर सकते हैं, जैसा कि निम्नलिखित में दिखाया गया है:

```
var message = "Namaste dosto!";
console.log(message.length); // Output: 14
```

यहाँ, हमने "message" वेरिएबल को "Namaste dosto!" के साथ परिभाषित किया है। फिर हम ".length" property का उपयोग करके "message" स्ट्रिंग की लंबाई पता लगाते हैं, जो 14 है।

### String functions

String functions in JavaScript are built-in functions that allow you to manipulate and modify strings. Here's a list of commonly used string functions in JavaScript:

1. length(): This function returns the length of the string.

Example:
var str = "Hello World";
console.log(str.length); // Output: 11

2. toUpperCase(): This function converts all characters in a string to uppercase.

Example:
var str = "hello world";
console.log(str.toUpperCase()); // Output: HELLO WORLD

3. toLowerCase(): This function converts all characters in a string to lowercase.

Example:
var str = "HELLO WORLD";
console.log(str.toLowerCase()); // Output: hello world

4. indexOf(): This function returns the index of the first occurrence of a specified substring in a string.

Example:
var str = "Hello World";
console.log(str.indexOf("o")); // Output: 4

5. slice(): This function extracts a part of a string and returns a new string.

Example:
var str = "Hello World";
console.log(str.slice(0, 5)); // Output: Hello

6. replace(): This function replaces the first occurrence of a specified substring with another substring.

Example:
var str = "Hello World";
console.log(str.replace("Hello", "Hi")); // Output: Hi World

7. trim(): This function removes whitespace from both ends of a string.

Example:
var str = " Hello World ";
console.log(str.trim()); // Output: Hello World

8. concat(): This function joins two or more strings and returns a new string.

Example:
var str1 = "Hello";
var str2 = "World";
console.log(str1.concat(" ", str2)); // Output: Hello World

In Hindi (Devanagari script):
JavaScript में स्ट्रिंग फंक्शंस वह बिल्ट इन फंक्शंस हैं जो आपको स्ट्रिंग को मैनिपुलेट और मॉडिफाई करने की अनुमति देते हैं। यहाँ जावास्क्रिप्ट में उपयोग में आने वाले स्ट्रिंग फंक्शंस की सूची है:

1. length(): यह फंक्शन स्ट्रिंग की लंबाई लौटाता है।

उदाहरण:
var str = "Hello World";
console.log(str.length); // आउटपुट: 11

2. toUpperCase(): यह फंक्शन स्ट्रिंग के सभी अक्षरों को अपरकेस में रूपांतरित करता है।

उदाहरण:
var str = "hello world";
console.log(str.toUpperCase()); // आउटपुट: HELLO WORLD

3. toLowerCase(): यह फंक्शन स्ट्रिंग के सभी अक्षरों को लोअरकेस में रूपांतरित करता है।

उदाहरण:
var str = "HELLO WORLD";
console.log(str.toLowerCase()); // आउटपुट: hello world

4. indexOf(): यह फंक्शन स्ट्रिंग में एक निर्दिष्ट उपस्थिति से पहले उपस्थिती के आधार पर एक सबस्ट्रिंग का इंडेक्स लौटाता है।

उदाहरण:
var str = "Hello World";
console.log(str.indexOf("o")); // आउटपुट: 4
# Scoping:

yeh batati hain ke hamare code ma banaye huaa variable function and object kha kha use keya ja skta hain.

- type of scope
  1.Global scope.
  2.Functional scope.
  3.Block scope.

### Global scope:

vah variable function va objrct jo ki top level par likhe gaye hain. mtlb ke koi function if else ke ander nahi hain to unhae khai par bhi exice keya ja skta hain.is scope ko Globla scope khate hain.

- for example:

```
let ab = "hello";
function check() {
  let i = 10;
  console.log(ab); //hello
}
check();
```

### Functional scope:

functional scope ma vah variable and function ata hai jo ki function ke ander banaye gyae hain.in variable funaction va object ko function ke bhar use nahi kar skte hain.

```
function firstfunction() {
  Name = "learnjavascript";
  document.getElementById("value1").innerHTML = Name;
}
firstfunction();
document.getElementById("value2").innerHTML = typeof Name;

```
### ==========Functions==========

function wo code hota hain.jise hum bar bar reuse kar skte hain.function ki help sa bahut
bade se bada code ko chote chote parts ma divide kar deya jata hain.

- javascript m function 3 type se bana skte hain.
  1.function declaration.
  2.function expression.
  3.arrow function

### What is function declaration:

function decleration me function ka name dena jaruri hain.function decleration ko jis line par declar kiya hai.us line sa phele call kar skte hain. function decleration ki hoisting hoti hain.

- function declaration syntex:

```
function sum(a, b) {
return a + b;
}
var ans = sum(10, 20);
```

Parametar vah variables hota hain. jinhe hum function me brackets ka andr likte hain. parametar ka kuch bhi name ho skta hain.Ek function yadi kuch bhi return nhi kar raha hain.to undefine return hoga.otherwise jo value return ki hain voh value return hogi.

Argument or paremetar ki mapping left to right hoti hain.yadi kisi parametar ki value pass nahi ki hain. to us parametar ki value undefine hogi.function ki return value ko hum kisi variable m store krva skte hain.

### What is function expression:

function expression bhi function decleration ki trha hota hain.lakin in dono me kuch difference hain.jese ki function expression ka name nahi hota hain.is liye is ko variable m store kiya jata hain.function expression ko jis line par banaya gaya hain.us line se
phele use nahi kar skte hain. function expression ki hoisting nahi hoti hain.

- function expression syntex:

```
var sum = function (a, b) {
return a, b;
};
var ans = sum(10, 20);
console.log(ans);
```

### What is arrow function:

Arrow function me function keyword ka use nahi hota hota. yadi arrow function me single line ka code hain or us code ma hum kuch return kar rahe hain to crlibresh or return likhne ki jaruri nahi hain sirf jo retrun karenge wo value likh dnege sirf or arrow function automatic khud return karega.yadi arrow function ma hum
kuch bhi return nahi kar rahe hain. and code ak line se jyada hain.to crliresh lagna jaruri hain.arrow function ko bhi hum phala call nahi kar skte hain.arrow function ki hoisting nhi hoti hain.

- arrow function syntex:

```
let test = () => expression;
var sum = (a, b) => {
return a + b;
};
console.log(sum(20, 10));
```

Anonymous function vah function jiska koi name nahi hota.us ko anonymous function khate hain.

- syntex :

```
let test = function(param1, param2)
{
//write your logic here
}
```

```
let ex_var = "A Variable";
let test = function () {
document.write(`Full Name : ${arguments[0]} <br>`);
document.write(`External Variable : ${ex_var}`);
};
test("Rahul Rajput");
```

- function inside function (function ka andr function)

### What is function inside function:

Yadi koi function kisi dusrye function ke andr bnaya gaya hai. to us function ko sirf bahar vale function ke andr hi use kiya ja skta hain.andr vale function ko hum bahar se call nahi kar skte hain.

- for example

```
function sum(a, b) {
console.log(a + b);
hello();
function hello() {
console.log("hello");
}
}
sum(10, 20);
```

- Arguments object function ko pass keya gaya arguments ko btata hain.

```
function sum(a, b, c) {
console.log(arguments);
}
sum(1, 2, 3, 4, 5);
```
### What is default parameter ?

Default parameter ek programming concept hai jismein ek function ka argument deafult value se initialize kiya jaata hai. Jaise ki, agar hum kisi function mein ek argument ko default value assign karte hain toh jab bhi uss function ko call kiya jaata hai aur uss argument ka value nahi diya jaata hai, toh woh argument default value ke saath initialize ho jaata hai.

For example, agar hum ek function define karte hain jiska naam hai print_name aur usmein ek argument hai name, toh hum uska default value "Guest" rakh sakte hain. Iska matlab hai ki agar hum print_name function ko call karte hain aur usmein koi Name nahi dete hain toh "Guest" as a default value use ho kar print ho jayega.

Yehi concept Hinglish mein samjhaya jaaye toh - agar tumhein koi party mein invite kiya gaya hai aur invitation mein likha hai ki RSVP pe apna naam dena zaruri hai, lekin agar tumne RSVP mein naam nahi diya toh tum automatically "Guest" ke roop mein count kiye jaoge.

### What is passing arguments: value vs reference in JavaScript ?

JavaScript mein, argument pass karna do tariko se kiya jata hai - value aur reference ke dwara. Value-based argument mein, argument ka copy function ke andar banaya jata hai aur ismein koi bhi changes function se bahar visible nahi hote hain. Jabki reference-based argument mein, original object ya array ko function ke through modify kiya ja sakta hai aur yeh changes function ke bahar bhi visible hote hain.

Value-based argument ka ek example hai:

```
function addOne(num) {
  num = num + 1;
  console.log(num); // output: 6
}

let myNum = 5;
addOne(myNum);
console.log(myNum); // output: 5
```

Is example mein, `addOne` function ko `myNum` variable ke value ke sath call kiya jata hai, jo ki initially 5 hai. Function mein, `num` variable ko `myNum` ki value se assign kiya jata hai. Iske baad, `num` variable mein 1 add kar diya jata hai. Lekin `myNum` variable ki value function ke bahar waise hi rehti hai jaise pahle thi, yaani 5.

Reference-based argument ka ek example hai:

```
function addToArr(arr, val) {
  arr.push(val);
  console.log(arr); // output: [1, 2, 3, 4]
}

let myArr = [1, 2, 3];
addToArr(myArr, 4);
console.log(myArr); // output: [1, 2, 3, 4]
```

Is example mein, `addToArr` function ko `myArr` variable ke sath call kiya jata hai, jo `[1, 2, 3]` hai. Function mein, `arr` variable ko `myArr` ki reference se assign kiya jata hai. Iske baad, `val` variable ko 4 se assign kiya jata hai. Fir, `push()` method ka use karke `arr` array mein `val` value add kiya jata hai. Ab, `myArr` variable ki value bhi `addToArr` function ke through modify ho jati hai aur ismein `[1, 2, 3, 4]` ho jata hai.

Is tarah se, value-based argument mein original variable/function ke copy banaya jata hai aur modifications us copy pe kiye jate hain. Jabki reference-based arguments mein original variable ko hi modify kiya jata hai aur changes function ke bahar bhi visible hote hain.

### What is First Class function/Citizen ?

First Class functions (FCF) refer to the ability of a programming language to treat functions as variables or first-class citizens. This means that functions can be assigned to variables, passed as arguments to other functions, and returned as values from functions.

For example, let's consider the following code:

```
function add(x, y) {
    return x + y;
}
let result = add(3, 4);
console.log(result);
```

In this code, `add` is a function that takes two arguments `x` and `y`, and returns their sum. We then assign the value returned by `add(3, 4)` to the variable `result`, which is then printed to the console.

Now, let's see an example of treating a function as a first-class citizen:

```
function add(x, y) {
    return x + y;
}

function apply(func, x, y) {
    return func(x, y);
}

let result = apply(add, 3, 4);
console.log(result);
```

In this code, we have defined a new function `apply` that takes three arguments: a function `func`, and two arguments `x` and `y`. The `apply` function then applies the function `func` to the arguments `x` and `y`.

We then call the `apply` function with the `add` function as the `func` argument, and `3` and `4` as the `x` and `y` arguments. The result of calling `apply` is the same as calling `add(3, 4)`, which is `7`.

So, in summary, first-class functions allow us to treat functions as data, which gives us more flexibility and power when writing code.

### What is High Order function ?

High order function ek aisa function hota hai jo doosre functions ko argument ke roop mein le sakta hai, ya fir ek function ko return kar sakta hai. Iss tarah ke functions ka upyog kisi specific kaam ke liye kaafi flexible aur powerful hota hai.

Ek udaharan ke roop mein, hum ek high order function likh sakte hain jo kisi list ke har item pe apply ho sakta hai aur use double kar sake. Is function ko hum "map" kehte hain:

```javascript
function double(x) {
    return x * 2;
}

let my_list = [1, 2, 3, 4, 5]'

let new_list = map(double, my_list);

console.log(list(new_list)) # Output: [2, 4, 6, 8, 10]
```

Yahaan, `double` function ko `map` function ke argument ke roop mein pass kiya gaya hai. `Map` function ne phir `my_list` ke har item pe `double` function ko apply kiya aur ek naye list mein un values ko store kar diya jismein har value original list ke corresponding value ka double tha.

Iss example mein, `map` function ek high order function hai kyunki usne ek doosre function (`double`) ko apna argument ke roop mein liya hai.

### What is Callback function ?

Callback function ek programming concept hai jisme ek function ko dusre function mein argument ke taur par pass kiya jaata hai aur yeh function baad mein call kiya jaata hai. Yeh kaam karke asynchronous programming mein kaafi help karta hai.

Let's take an example: Suppose humare paas ek function hai jo do numbers ka sum calculate karta hai:

```javascript
function add_numbers(a, b) {
    return a + b;
}
```

Ab humein ek aur function banana hai jo kisi bhi do numbers ka product calculate karega, lekin ismein hum chaahte hai ki agar iska calculation complete hua toh humare paas ek message aa jaaye. Iske liye hum callback function ka use karenge:

```javascript
function multiply_numbers(a, b, callback) {
    let result = a * b;
    callback(result);
}

# Ab hum apna callback function bana sakte hain
def print_result(result):
    print("Product is:", result)

multiply_numbers(5, 6, print_result)
```

Yahaan humne `multiply_numbers` mein `callback` parameter add kiya jisse hum uss function mein bhejte hain. Fir `multiply_numbers` function mein hum result ko calculate karte hain aur `callback` function ko call kar dete hain jisse wo message print kar sake.

Upar diye gaye example mein humne javascript ka use kiya hai, lekin callback functions ka concept kisi bhi programming language mein istemaal kiya ja sakta hai.

### What is setTimeOut ?

setTimeOut ek JavaScript function hai jiske through hum apne code ko delay kar sakte hai. Iske liye, setTimeOut function ko call kiya jata hai aur ismein pehle argument mein ek function define kiya jata hai jo hum delay karna chahte hai, aur dusre argument mein delay time (milliseconds) specify kiya jata hai.

For example:

```
setTimeout(function() {
  console.log("Hello, world!");
}, 3000);
```

Is code mein, setTimeout function ko call kiya gaya hai jismein pehla argument ek anonymous function hai jo "Hello, World!" console.log statement print karega, aur dusra argument hai 3000 milliseconds ka delay time hai.

Iss code ko Hinglish mein explain karte hai:
"setTimeout" ek JavaScript function hai jisse hum code mein delay laga sakte hain. Jaise ki agar humein 3 second ke baad "Hello, World!" console mein print karna hai to hum "setTimeout" function use karenge. Ismein hum pehle argument mein "Hello, World!" print karne wali function ko define karenge aur dusre argument mein 3000ms (3 seconds) ka time specify karenge."

### What is setInterval ?

setInterval ek JavaScript function hai jo humein time-based actions ko perform karne mein help karta hai. Iske through, hum ek function ko specific interval ke baad repeatedly call kar sakte hain.

Iske liye sabse pehle hum setInterval() function ko call karte hain aur usmein do parameters pass karte hain:

1. Ek function jo humein har interval ke baad call karna hai.
2. Interval ka duration milliseconds mein kitna hona chahiye.

Jab hum is function ko call karte hain, woh turant ek ID return karta hai jo humare setInterval loop ko stop karne ke liye use kar sakte hain.

Example:

Agar humein 1 second ke interval ke baad "Hello World" print karna hai, to hum is tarah ka code likh sakte hain:

```javascript
let count = 0;
const intervalId = setInterval(() => {
  console.log("Hello World");
  count++;
  if (count === 5) {
    clearInterval(intervalId);
  }
}, 1000);
```

Iss code mein, humne `count` variable ki madad se 5 iterations ke baad setInterval loop ko stop karne ka condition set kiya hai. Humne `setInterval()` function ko call kiya aur usmein ek anonymous function pass kiya jo 1 second ke interval ke baad "Hello World" print karega.

### what is Function returning a function ?

Function returning a function is when a function returns another function as its output instead of a regular value. The returned function can be stored in a variable and called later.

For example, let's say we want to create a function that adds a given number to any input. We can define this function like this:

```
def add_number(number):
    def add_to_input(input_num):
        return input_num + number
    return add_to_input
```

this would be something like "function jo ek aur function return karta hai". Iska matlab hai ki hum ek aisi function bana sakte hain jismein hum ek number ko diya hai aur ye function ek aur function return karta hai. Ye returned function input number ko liya aur usmein diye hue number ko add karke output dega.

In the above example, `add_number` function takes in a `number` argument and defines an inner function `add_to_input` that takes a single input `input_num`. This inner function adds the `number` passed to it to the `input_num` and returns the result.

The `add_number` function then returns the `add_to_input` function as its output. Now, we can store the returned function in a variable and call it with different inputs like this:

```
add_five = add_number(5)
add_ten = add_number(10)

print(add_five(3))  # Output: 8
print(add_ten(3))   # Output: 13
```

Here, we created two new functions, `add_five` and `add_ten`, by calling the `add_number` function with arguments 5 and 10 respectively. These new functions add 5 and 10 to their inputs, respectively. Calling these new functions with different inputs gives us the desired output.

I hope this helps!

### What are the call and apply methods ?

Call and Apply methods are functions in JavaScript that allow you to invoke a function with a specific context (or "this" value) and arguments.

The difference between the two is that call takes individual arguments separated by commas, while apply takes arguments as an array.

For example, let's say we have a function named "printFullName" which takes two arguments: firstName and lastName. We also have an object named "person" with properties "firstName" and "lastName". We can use the Call method to invoke the "printFullName" function with the "person" object as the context:

```
function printFullName(firstName, lastName) {
  console.log(this.firstName + " " + this.lastName);
}

var person = {
  firstName: "John",
  lastName: "Doe"
}

printFullName.call(person); // Output: John Doe
```

In this example, we used the Call method to invoke the printFullName function with the "person" object as the context. The "this" keyword inside the function now refers to the "person" object, and we get the output "John Doe".

Similarly, to use the Apply method, we can pass the arguments as an array:

```
printFullName.apply(person, ["Jane", "Doe"]); // Output: Jane Doe
```

Here, we passed an array containing two values - "Jane" and "Doe" - as the arguments for the function. The Apply method allows us to pass arguments as an array instead of individual arguments.

So, in summary, Call and Apply methods are used to invoke a function with a specific context (or "this" value) and arguments.

### What is the bind method ?

Bind method ek JavaScript function ka method hai jo humein ek naya function return karta hai. Bind method se hum apne original function ko ek naya "this" value aur arguments ke saath connect kar sakte hai.

Bind method ka syntax aisa hota hai: `function.bind(thisArg, arg1, arg2, ...)`

Ismein `thisArg` ek object hota hai jise hum bind karna chahte hai aur `arg1`, `arg2`, ... baki ke arguments hote hai jo humare original function mein pass kiye jaate hai.

Ek example dekh lete hai:

```
const person = {
  firstName: "John",
  lastName: "Doe",
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
}

const printName = person.fullName.bind(person);

console.log(printName()); // Output: John Doe
```

Is example mein humne `person` object ka `fullName` method banaya hai jo `this.firstName` aur `this.lastName` ki madad se full name return karta hai. Fir humne `bind()` method ka use karke `printName` variable mein `person.fullName` ko bind kiya hai. Ab hum `printName()` ko call karte hai toh yeh `person.fullName()` ko call karega lekin `this` ka value `person` hi hoga.

Mujhe ummeed hai ki ab aapko bind method samajh mein aa gaya hoga!

### What is Immediately invoked function expression ?

Immediately Invoked Function Expression (IIFE) is a JavaScript function that is executed as soon as it's defined. In simple terms, it's a function that runs right away.

Example in JavaScript:

(function(){
// Code to be executed immediately
})();

In Hinglish language:

Immediately invoked function expression (IIFE) ek JavaScript function hai jo ki define hote hi execute ho jata hai. Saral bhasha me samjhe to ye ek function hai jo turant chal jata hai.

Udaharan JavaScript me:

(function(){
// Code jo immediate taur par execute hoga
})();

### What is Closure in javascript ?

Closure in JavaScript refers to the ability of a function to access variables from its outer lexical scope, even after the outer function has returned.

Ek closure tab hota hai jab ek function bahar ke variables aur functions ke references ko lekar apne andar use karta hai, aur phir wo function ussi state mein rehta hai jis mein usko define kiya gaya tha. Yeh bahar ke variables aur functions ke liye private scope create karta hai.

For example:

```
function counter() {
  let count = 0;
  return function increment() {
    count++;
    console.log(count);
  }
}

const c = counter();
c(); // logs 1
c(); // logs 2
```

Iss code mein, `counter` function ek function `increment` ko return karta hai. `increment` function `count` variable ko access kar sakta hai, jo `counter` function ke lexical scope mein define kiya gaya hai. Jab `c` ko `counter` se invoke kiya jata hai, wo `increment` function ko return karta hai jismein `count` variable ki value increment ho jaati hai. Har baar jab `increment` function call kiya jata hai, wo `count` variable ki updated value ko print karta hai.

Iss tarah se, closure ka upyog karke hum private variables aur functions ko create kar sakte hai, jinka access sirf unhi functions ke through possible hai jismein wo define kiye gaye hai.
# Destrcutring :

Destrcutring ek syntax hota hai jiski help se hm Array/Object me se values
easily nikal ke variables me store kr skte hain.

### Destructuring Arrays

- Destrcutring of array values :

```
let arr  = [1,2,3,4,5];
let [a,b,c] = [arr];
console.log(a, b, c); // 1 2 3
```

- Yadi hume koi value skip krni hai to uske lie keval comma lgana hoga

```
let arr  = [1,2,3,4,5];
let [, , b, c] = [arr];
console.log(b, c); // 3 4
```

### Reverse values using destructuring :

- normal way

```
let a = 10;
let b = 20;
let c = a; //10
a = b; // a=20
b = c; //b = 10
console.log(a, b);
```

### reverse two numbers using destructring

```
let a = 10;
let b = 20;
[b, a] = [a, b];
console.log(a, b);
```

### Return two values from function:

Yadi hume kisi function se ek se jyada value return krni hai
to ye possible ni hai. But iske lie hum ek array function se return kr skte hain aur us
array me ek se jyada values push krke return kr skte hain

- return more than one value from function using array

```
function getvalues() {
  return [1, 2];
}

console.log(getvalues()); // [1,2]
```

### Destructuring of nested array:

Yadi array ke nested array hai to us nested array ki values ko
destructure krne ke lie hume b nested array bnana pdega

- for example :

- Nested Array destructuring

```
let arr = [1, 2, [3, 4, [6, 7, 8], 5], 6, 7];
let [, , [, , [, a]]] = arr;
console.log(a);

```

```
let arr = [1, 2, [3, 4, 5], 6, 7];
let [, , [, a]] = arr;
console.log(a);
```

### Setting default values:

Yadi hum ye chahte hai ki agar koi element array se hm nikal rhe hain aur vo element us array me ni hai to value undefined hogi. is case me hum kuch default value de skte hain. Yadi value array me hai to vo value pick hogi otherwise default value pick hogi

- default values

```
let arr = [1, 2];
let [a, b, c = 20] = arr;
console.log(a, b, c);
```

```
let arr = [1, 2, 5];
let [a, b, c = 20, d = 1000] = arr;
console.log(a, b, c, d);
```

### Destructuring Objects:

Destructuring objects ki help se hm object ko destructure kr
skte hain.

```
let obj  = {
    name : "learnjavascript",
    age : 21,
    address : {
        colony : "Madina Colony",
        pincode : 302012
    }
}
```

Extract value:
Value ko extract krne ke lie left side me curly braces me key ka nam
dena hota hai. Yea key ka naam exactly same hona chahiye otherwise error aayegi.Jo key ka naam hm dete hain vhi variable ka nam hota hai aur us key me jo value hai vo us variable ko assign ho jati hai\*/

```
let {name, age} = obj;
console.log(name, age); //learnjavascript 21
```

Different property name:
Yadi hume koi property ko extract krke use kisi variable me
store krana hai to hm use variable ko rename b kr skte hain. rename krne ke lie property ka naam ke bad colon lgana hota hai.

```
let {name:myName, age : myAge} = obj;
console.log(myName, myAge); //learnjavascript 21
```

Default values:
Yadi kisi Key ke lie object me koi value ni hai to us key ki value
undefined hogi. Is case me yadi hum koi default value chahte hai to de skte hain. Default value dene ke lie key ke bad equal to lgake value deni hoti hai.Default value tabi assign hogi jab us key ke lie object me koi b value ni hai

```
let obj  = {
    name : "learnjavascript"
}
let {name, age} = obj; //learnjavascript undefined
let {name, age= 30}; //learnjavascript 30 default value hai age ki

let obj  = {
    name : "learnjavascript",
    age : 50
}

let {name, age= 30}; //learnjavascript 50 default value hai age ki
```

Nested Object:
Destructuring me hum nested objects ko b extract kr skte hain. Aisa
krne ke lie hume nested object vala tarika use krna hoga

- for example:

```
let obj  = {
    name : "learnjavascript",
    age : 21,
    address : {
        colony : "Madina Colony",
        pincode : 302012
    }
}

let {name, address : {pincode}} = obj;
console.log(name, pincode); //learnjavascript 302012
console.log(name, address); //learnjavascript {address object}
```

In Function:
Yadi hum object kisi function ko pass kr rhe hain to is case me
hum complete object us function ko pass krte hain. Pr ye tarika tab hi shi hai jab hm pura object use me le rhe hain. Yadi hum us object me se kuch specific values hi pick kr rhe hain to aise case me hm function me object Destructuring ki help se values ko us object se destructure kr skte hain.

- for example

- Without Destructring

```
let obj  = {
    name : "learnjavascript",
    age : 21,
    address : {
        colony : "Madina Colony",
        pincode : 302012
    }
}
printDetails(obj);
function printDetails(obj){
    console.log(obj.name, obj.address.pincode);
}
```

- With Destructring

```
function printDetails({name, address : {pincode}}){
    console.log(name, pincode);
}
```

Shallow Copy:
Shallow copy ka matlab yeh hai ki jab b hm ek non primitive data type ko dusre variable me store krte hain vah kisi ek me b change krte hain to dono me change hota hai pr yeh change sirf Non Primitive data ke lie hai hota hai. Primitive data jo ki top level pr hai usme kuch b change krenge to dono me change ni hoga.

-for example:

```
let obj = {
  name: "learnjavascript",
  age: 21,
};

let obj1 = Object.assign({}, obj);
obj1.name = "Sajid"; //obj.name me change ni hoga kuki name field ki value ek string hai
console.log(obj, obj1);//learnjavascript Sajid
```

- 2nd example:

```
let obj = {
  name: "learnjavascript",
  age: 21,
  address: {
    pincode: 302012,
  },
};

let obj1 = Object.assign({}, obj);
obj1.address.pincode = 302020; //Kuki address ki value ek object hai islie change krne pr dono variables me change hoga
console.log(obj.address.pincode, obj1.address.pincode);
```

Deep Copy:
Yadi hum ye chahte hai ki object me koi value chahe primitive ho ya non primitive usme change kren to dono jgah change ni hona chahiye. Iske lie fir hm shallow copy krne ki bjay deep copy krenge
Deep copy krne ka asan tarika yeh hai ki hm Object ko phle string me convert krne vah fir us string ko dubara se Object me convert kren

- for example:

```
let obj = {
  name: "learnjavascript",
  age: 21,
  address: {
    pincode: 302012,
  },
};

let obj1 = JSON.parse(JSON.stringify(obj));
obj1.address.pincode = 302020;
console.log(obj.address.pincode, obj1.address.pincode); //302012 302020
```

Spread Operator:
Spread operator ki madad se hm aisa koi b data jo iterable type
ka hai like Array, Set, Object etc ko extract/unpack kr skte hain

- Spread operator 3 dots se bnta hai ...

- Assigning values : Yadi hume ek array dusre array me assign krna hai to hm direct assign kr skte hain.

- for example:

```
let arr = [1, 2, 3, 4, 5];
let arr2 = arr;
arr2.push(100);
console.log(arr, arr2);
```

Upar vale case me is trah se assignment krne pr dono array me se yadi kisi b array me change krte hain to dono array me change hoga.
Yadi hum ye behaviour ni chahte hai to hm spread opeator ki madad se assignment kr skte hain. Jab spread opeator ki madad se assignment hota hai to normal copy na hoke shallow copy hoti hai.

- for example:

```
let arr = [1, 2, 3, 4, 5];
let arr2 = [...arr];
arr2.push(100);
console.log(arr, arr2);
```

- Is case me arr2 me change krne pr arr me koi change ni hoga

- Copy Array :

```
let arr = [1, 2, 3, 4, 5];
let arr2 = [...arr];
```

### Join 2 Arrays\_:

Yadi hume ek se jyada arrays ko join krna hai to hum comma
seperated arrays deke join kr skt hain

- for example

```
let arr = [1, 2];
let arr2 = [6,7];
let arr3 = [...arr, ...arr2];
console.log(arr3); // 1 2 6 7
```

### String to array using spread:

Yadi String ko characters ke array me convert krna hai
to hum spread operator ki help se kr skte hain

- for example

```
let str = "learnjavascript";
let arr = [...str];
console.log(arr); // ['W', 'e' , 'C', 'o', 'd', 'e']
```

Passing arguments in function:
Yadi hum kisi fuction ko array pas kr rhe hain aur us function ek andar array se index ka use krke values nikal rhe hain to aisa
na krke hum ye kaam spread operator ki help se easily kr skte hain

- Without spread operator

```
let arr = [1, 2, 34, 4, 5, 56, 7, 7];
sum(arr);
function sum(arr) {
console.log(arr[0] + arr[1] + arr[2]); //37
}
```

- With Spread operator

```
sum(...arr);
function sum(a, b, c) {
console.log(a + b + c); //37
}
```

- Shallow copy :

```
let obj = {
name : "learnjavascript",
age : 21
}

let obj1 = {...obj};
```

The Rest Parameter:
Rest parameter ka symbol spread opeartor ki trah hi hota hai
lekin rest parameter ka kaam different hota hai. Rest parameter hm rest/bachi hui values ko extract krne ke lie kaam me lete hain

### Assign values:

Rest opeartor equal to ke left side me use hota hai. Rest operator
last elemt hona chahiye. Vah rest parameter bachi hui jitni b values hain un sbko is rest parameter vale variable me store kra dega.

- For example:

```
let arr = [1,2,3,4,5];
let [a, ...b] = arr;
console.log(a, b); //1 [2,3,4,5]
```

Rest element last element:
Rest element last element hona chahiye otherwise error aayegi.

- For example:

```
let arr = [1,2,3,4,5];
let [a, ...b, c] = arr;
console.log(a, b, c); //error
```

### Assign values in object:

Yadi array ki trah hi hum bachi hui sari values kisi
variable me dalna chah rhe hai to hm spread operator ka use kr skte hain. Spread operator bachi hui sari key, values ko ek object bnake us rest paramater vale variable me store kra dega

- for example:

```
let obj = {
name :"learnjavascript",
age : 21,
address : "Jhotwara"
}

let {name, ...obj1} = obj;
console.log(name, obj1); //learnjavascript {age : 21, address : "Jhotwara"}
```

### Variable arguments in function:

Yadi koi aisi situation hai ki jisme function ko variable arguments lene hai means argument ka count fix ni hai to aise case ko handle
krne ke lie hum rest parameter use me le skte hain. Rest parameter us function ko pass kie gye sare arguments ka ek array bnake us array me store kr dega

- for example

```
for 2 arguments
let a = 1;
let b = 2;
sum(a, b);
function sum(a, b) {
console.log(a+b);
}
```

- for 3 arguments

```
let a = 1;
let b = 2;
let c = 3
sum(a, b, c);
function sum(a, b,c ) {
console.log(a+b+c);
}
```

Upar vali approach se yadi hum code likhenge to hume bar bar code change krna pdega Islie hm rest parameter ka use krenge

```
let a = 1;
let b = 2;
sum(a, b); //3
sum(a, b, 10); //13
sum(12, 20 , 19, 40, 50, 60); //201
function sum(...arr) {
let sm = 0;
for(let val of arr) {
sm = sm + val;
}
console.log(sm);
}
```

### Short Circuiting:

Short circuting hm || operator ya && operator ki madad se
kr skte hain. Short circuiting falsy values ke lie kaam ni krta hain
jaise ki 0, false etc. Yadi hume inke lie b chlana hai to Nullish Coalescing Operator ?? ka use lenege.

- Example of ||:
  || me jab tak true value ni mil jati check kia jayega. Jaise hi true value milegi search krna band ho jayega. Aur yadi last tak true value ni mili to last value hi answer hoga

```
let a = 0 || 10; // 10
let b = 0 || null || 30 || 10; //30

```

### Example of &&:

&& me jab tak value true hai search krega. Jaise hi false value milegi search krna band ho jayega aur answer vah false value ayegi. But other case me yadi flow last elemlent tak jata hai to fir last element hi answer hoga chahe vo true ho ya false.

```
a = 0 && 10; // 0
b = 0 && null && 30 && 10; //0
let c = 10 && 20 && null; // null
let d = 20 && 30 && 50; // 50
```

### Calling function using && :

&& Operator ki help hm function ko b call kr skte hain` function tabi call hoga jab phli conditon true hogi

- for example:

```
30 && printHello(); //Hello
0 && printHello(); //No output
function printHello() {
  console.log("Hello");
}
```

### Nullish Coalescing Operator ?? \*:

Yeh operator Short circuiting operator || ki trah hi kaam krega lekin yeh operator keval null and undefined ke lie ni chlta hai. Baki sari values ke lie chlega

### for example:

```
let a  = 0 ?? 10;  //0
let b  = false ?? 30; // false
let c = null ?? undefined ?? 50; //50
let d  = null ?? undefined; //undefined
```

### Logical Assignment operator:

Hm short circuiting and equal opeator ka use krke
ek short way me values assgin kr skte hain. Logical assignment operator ka yeh negative point hai ki hm ise sirf single condtion ke lie use kr skte hain.

### for example:

```
let x  = 10;
if(!x) {
  x = 20;
}
```

- Same example Logical assignment operator ki madad se b likh skte hain

```
let x  = 10;
x ||= 20; // 10

```

let y = 0;
y ||= 30; //30

```

- Same hm && and ?? operator ke sath b use kr skte hain

```

let x = 10;
x &&= 20; // 20

```


```

let y = 0;
y &&= 30; //0

```

```

let x = 0;
x ||= 20; // 20
x ??=20; //0

```

```

let y = false;
y ||= 30; //30
y ??= 30; //false

```

```

let z = null;
z ||= 40; //40
z ??= 40; //40

```

### Enhanced Object literals:
Modern features me object literals likhne ke ways me kuch
changes hue hain. aise 3 changes niche explain kie hain

- Exactly same name:
Yadi hm object me kisi variable ke through value dal rhe hain
aur hm ye b chahte hain ki key ka naam vhi hoga jo variable ka naam hai to hume aise case me sirf variable ka naam likhna hota. Value automatic assign ho jayegi. Yeh value vhi value hogi jo us varible ki value hai.

```

let myName = "learnjavascript";

let obj = {
myName,
};
console.log(obj); // {myName: 'learnjavascript'}

```

### function in object:
Yadi hum object me function bna rhe hain to hume : vah function
likhne ki jrurat ni hai.

- for example :

- Old way

```

let obj = {
sum: function (a, b) {
console.log(a + b);
},
};

```

- New way
- Upar vale function ko niche vale function ki trah b likh skte hain

```

obj = {
sum(a, b) {
console.log(a + b);
},
};

```

### Computed Property names:

Generally object me keys ka name fix hota hai but agar humari aisi requirement hai ki hm key ko calculate/compute krna chahte hai to kr skte hain. Aisa krne ke lie hume array brackets ka use krna hoga vah in brackets ke andar jo b expression likhni hai vah likh skte hain

- for example :

```

let a = "age";
obj = {
[a + 2]: "learnjavascript",
[10+20] : 100
};
console.log(obj); //{age2: 'learnjavascript', 30 : 100}

```

### Optional Chaining:

Yadi object ke andar nested object hai aur hm us nested object se koi value extract kr rhe hain to is case me type error aa skti hai. Ye case tabi hoga jab jo key humne likhi vah key last key na ho aur object me vo key available na ho Yadi vah key last key hai to error ni ayegi, undefined aayega.

- for example :

```

let obj = {
address: {
otherAddress: {
pincode: 302012,
},
},
};
console.log(obj.address.otherAddress.pincode); //302012
console.log(obj.address.otherAddress.pincodes); //undefined
console.log(obj.address.address.pincode); //type error

obj = {
address: {},
};

console.log(obj.address.otherAddress.pincode); //TypeError: Cannot read properties of undefined (reading 'pincode')
console.log(obj?.address?.otherAddress?.pincode); ///undefined

```

- Optional chaingin ko hm khi jgah pr use kr skte hain

- for example: Hum ye check kr skte hain ki array empty hai ya nhi

- Checking array is empty

```

let arr = [1, 2, 4, 5];
console.log(arr[2]?.address?.pincode); //undefined

let arr = [1, 2, { address: { pincode: 302012 } }, 4, 5];
console.log(arr[2]?.address?.pincode); //302012

```

### Calling function:

Yadi functiion bna hua ni hai aur hum use call kr rhe hain to error aayegi. But is error ko htane ke lie hum optional Chaining ka use kr skte hain

- for example :

```

let obj = {};
obj?.printHello?.(); //No error

let obj = {};
obj?.printHello(); //Error

```

- Using optional Chaining in conditon :

```

let obj = {
name: "Sajid",
age: 21,
myAddress: {
pincode: 302012,
address: {
city: "Jaipur",
state: "Rajasthan",
},
},
};

```

- Without optional chaining

```

if (
obj &&
obj.myAddress &&
obj.myAddress.address &&
obj.myAddress.address.city
) {
console.log("Hello");
} else {
console.log("City Not present");
}

```

- With optional chaining

```

if (obj?.myAddress?.other?.city) {
console.log("Hello");
} else {
console.log("City Not present");
}

```

```
### Temporal Dead Zone (TDZ)

TDZ ek period hai jahan hum ek varibale ko declare kar dete hain par usse pehle use access nahi kar sakte jab tak usse value assign nahi karte. Yeh ek error hai jo aata hai agar hum uss variable ko TDZ ke dauran access karte hain.

Temporal Dead Zone (TDZ) is a period in JavaScript where a declared variable cannot be accessed before it is assigned a value.

Let me explain this with an example: Suppose you declare a variable "x" using the keyword "let" inside a function:

```
function myFunction() {
  console.log(x);
  let x = 5;
}
```

Now, when you call the function `myFunction()`, you will get an error that says "Cannot access 'x' before initialization". This is because `x` is still in the TDZ and has not been assigned a value yet.

To avoid this error, you need to move the console.log statement after the assignment of the variable:

```
function myFunction() {
  let x = 5;
  console.log(x);
}
```

TDZ ek period hai jahan hum ek varibale ko declare kar dete hain par usse pehle use access nahi kar sakte jab tak usse value assign nahi karte. Yeh ek error hai jo aata hai agar hum uss variable ko TDZ ke dauran access karte hain.
### Debugging

Debugging ek process hai jahan hum apne code me errors ko dhoondte hai aur unhe fix karte hai. JavaScript me debugging ka matlab hota hai ki hum apne code ke errors ko dhoondh kar unhe solve karein taaki hamara code properly work kare.

Bahut se tools hote hai jaise console.log(), Chrome DevTools, aur Visual Studio Code debugger jo humein JavaScript code me error ko find karne me help karte hai.

Ek example ke liye, agar hum ek variable ko undefined value se initialize karte hai:

```javascript
let name;
console.log(name);
```

Is case me console par "undefined" print hoga kyunki humne variable `name` ko koi value assign nahi ki hai. Is tarah se hum apne code me errors ko identify kar sakte hai aur unhe fix kar sakte hai.

Agar hum Visual Studio Code ka use karte hai toh hum break points laga kar debugger ka use kar sakte hai. Break points lagane ke baad jab hum apna code run karenge toh wo execution ke time pe break ho jayega aur hum uss point se aage execute kar sakte hai. Isse hum apne code ke errors ko easily findout kar sakte hai.

Ummid hai ki ye samajh me aa gaya hoga ki JavaScript debugging kya hota hai aur iska importance kya hai.

### Developer Tool

JavaScript Developer Tools are a set of features provided by web browsers to help developers debug and optimize their JavaScript code. These tools include a range of functions such as managing console logs, inspecting code execution, profiling performance, and analyzing network traffic.

For example, Google Chrome's DevTools provides a comprehensive set of developer tools that you can access by pressing the F12 key or right-clicking on any element in the page and selecting "Inspect." Once open, you will see several tabs that allow you to inspect the DOM, CSS, Network, Console, and more.

Using the Console tab, you can execute JavaScript code directly in the browser and log out the output. This is helpful for quickly testing code snippets and debugging issues. The Network tab shows all the HTTP requests made by the browser, allowing you to see which resources are being loaded and how long they take to load.

Additionally, DevTools has a Sources tab where you can insert breakpoints in your code to stop it at specific points, examine variable values and step through the code line by line.

Overall, these DevTools provide a powerful set of features that can help developers build and troubleshoot complex JavaScript applications more efficiently.

### Fixing errors

JavaScript mein errors ki shikayat aksar hoti hai, aur iske sahi karne ke liye kuch steps hote hain jo neeche bataye gaye hain:

1. Error message padhein: Jab bhi aapka code execute hone se pehle ya during execution mein error aata hai, toh console mein ek error message show hota hai. Is error message ko padhkar aapko pata chal jayega ki kis line mein error hai aur uski wajah kya hai.

2. Code ko review karein: Error message padhne ke baad aapko woh line of code dekhna chahiye jisme error hai. Us line of code ko carefully review karein aur dekhein ki kya galat likha hai.

3. Syntax ki sahiyta check karein: JavaScript ek syntax-based language hai, isliye aapki code mein sahi syntax hona bahut zaroori hai. Syntax error ko fix karne ke liye, aapko code ko carefully check karna hoga aur galti ko theek karna hoga.

4. Variables aur functions ki spelling ki jaanch karein: Aksar kabhi-kabhi variables aur functions ki spelling mistakes ho jati hai, jiske wajah se code mein error aata hai. Isliye, code mein use kiye gaye variables aur functions ki spelling ko carefully check karein.

5. Debugging tools ka istemaal karein: JavaScript mein debugging tools available hote hain jaise ki Chrome DevTools, Firefox Debugger, etc. In tools ka istemaal karke aap apne code mein errors ko easily trace kar sakte hain aur unhe sahi kar sakte hain.

Example:
Maan lete hain ki aapne ek JavaScript function likha hai jo dono numbers ko add karta hai:

function addNumbers(a, b) {
var sum = a + b;
console.log(sum);
}

Lekin agar aap is function ko call karte hain aur sirf ek number pass karte hain, toh error message show ho jayega:

addNumbers(5);

Error: Uncaught ReferenceError: b is not defined

Is error message se pata chalta hai ki kyonki aapne sirf ek parameter pass kiya hai, isliye 'b' variable undefined hai. Is error ko fix karne ke liye, aapko function call ko do parameters ke saath update karna hoga:

addNumbers(5, 10);

Output: 15

Is tarah se aap JavaScript mein errors ko fix kar sakte hain aur apne code ko smooth functioning karwa sakte hain.

### different types of errors .

Javascript mein kai prakar ke errors hote hai. Kuch common errors hain jaise Syntax errors, Reference errors, Type errors aur Range errors.

1. Syntax error: Ye error jab aata hai jab aapka code javascript language ke rules ke khilaaf hota hai. Jaise ki agar aapne ek statement ko likhne ke liye semi-colon (;) nahi lagaya to ye error aayega.

Example:

```
// Invalid syntax
let x = 5
console.log(x)
```

Ismein semi-colon missing hai statement ke end mein.

2. Reference error: Jab aap kisi varibale ko access karte hai jo exist nahi karta ya fir usko define nahi kiya gaya hai to ye error aata hai.

Example:

```
// Accessing undefined variable
console.log(x);
```

Ismein variable x ka value define nahi kiya gaya hai.

3. Type error: Ye error tab hota hai jab aapka code ki type mismatch ho jati hai. Jaise ki aapne string ka operation number pe apply kiya ho.

Example:

```
// Trying to use string method on a number
let x = 123;
console.log(x.toUpperCase());
```

Ye error isliye aaya kyunki humne uppercase() method ko number mein use kiya hai, lekin ye method sirf string ke liye hota hai.

4. Range error: Jab aapka code range se bahar ho jata hai, jaise ki ek array ke element ke index ke bahar ho jaye ya fir ek number ki range se bahar ho jaye to ye error aata hai.

Example:

```
// Trying to access an element outside the array
let arr = [1, 2, 3];
console.log(arr[3]);
```

Ismein hum 4th index element ko access karne ki koshish kar rahe hai, jo ki array ke range se bahar hai.

In prakaron ke alawa bhi kai errors hote hai, par inmein se ye sabse common errors hai. Aapko javascript mein aane wale errors ka pata hona zaruri hai taaki aap unhe avoid kar sake aur apna code efficient tarike se likh sake.
### Number

Number in JavaScript is a data type that represents numeric values. It includes both integers and floating-point numbers (decimal numbers). In Hinglish, we can say "Number" ko JavaScript mein ek prakar ka data type hai jo sankhyaaon ko darshata hai. Yeh poori tarah se digit ya decimal number ho sakta hai.

Example:
var num1 = 10; // integer
var num2 = 3.14; // floating-point number

In this example, we have two variables num1 and num2 of the Number data type, where num1 holds an integer value of 10 and num2 holds a floating-point (decimal) value of 3.14.

JavaScript provides various mathematical operations that can be performed on Number values such as addition, subtraction, multiplication, division, and more. For example:

var sum = num1 + num2; // addition
var diff = num1 - num2; // subtraction
var product = num1 \* num2; // multiplication
var quotient = num1 / num2; // division

Apart from these basic arithmetic operations, there are many other built-in functions and methods available in JavaScript for working with Number values, such as Math.round(), Math.floor(), and Math.random().

Overall, Number is a fundamental data type in JavaScript that plays a crucial role in many programming tasks, particularly those that involve numerical calculations and manipulations.

### Converting numbers

JavaScript provides several methods to convert numbers from one format to another. Here are some examples:

1. parseInt()
   The parseInt() method converts a string to an integer. It parses a string argument and returns an integer value. If the string starts with a non-numeric character, it returns NaN (not-a-number).

parseInt("123") // Returns 123
parseInt("123.45") // Returns 123
parseInt("abc123") // Returns NaN

2. parseFloat()
   The parseFloat() method converts a string to a floating-point number. It works similar to parseInt() but returns a floating-point number instead of an integer.

Example in Hinglish:
parseFloat("123.45") // Returns 123.45
parseFloat("123") // Returns 123
parseFloat("abc123") // Returns NaN

3. Number()
   The Number() function converts a value to a number. It can be used to convert strings, boolean values, or objects into a number. If the argument cannot be converted into a number, it returns NaN.

Example in Hinglish:
Number("123") // Returns 123
Number("123.45") // Returns 123.45
Number("abc123") // Returns NaN

4. toString()
   The toString() method converts a number to a string. It takes an optional parameter that specifies the radix (base) of the number system to use for representing the number as a string.

Example in Hinglish:
(123).toString() // Returns "123"
(123).toString(16) // Returns "7b" (hexadecimal representation)
(123).toString(2) // Returns "1111011" (binary representation)

These are some basic ways of converting numbers in JavaScript.

### NaN

NaN stands for "Not a Number" in JavaScript. It is a special value that represents an invalid or unrepresentable numeric result.

NaN ka matlab hai "kuch bhi nahi", yani ki agar koi number expected hai lekin usme koi invalid operations hote hai toh NaN return hota hai.

For example:

```
let result = 10 / "hello";
console.log(result); // Output: NaN
```

Is example mein humne ek string ko number ke saath divide karne ki koshish ki hai jo ki possible nahi hai. Isliye, JavaScript NaN return karega.

NaN can also result from mathematical operations like dividing zero by zero, multiplying infinity by zero, or taking the square root of a negative number.

It is important to note that NaN is not equal to anything, including itself. So, the following comparison will always return false:

```
console.log(NaN === NaN); // Output: false
```

### Infinity

Infinity in JavaScript is a special numeric value that represents the concept of mathematical infinity, which means a number that is larger than any other number. Infinity is a global property in JavaScript and is represented by the keyword "Infinity".

In JavaScript, you can get Infinity by dividing a number by zero or by using the Infinity keyword directly. For example:

```js
console.log(1 / 0); // Output: Infinity

console.log(Infinity + 1); // Output: Infinity
```

The Infinity value is also used when a mathematical operation exceeds the largest possible value that JavaScript can represent. For example:

```js
console.log(Math.pow(2, 1024)); // Output: Infinity
```

Infinity in JavaScript can be described as अनंत (anant) or असीम (aseem) which means limitless or boundless. It represents a mathematical concept of a number that is larger than any other number and is used in JavaScript to indicate values that are too large to represent in memory.

### Number System

Number System in JavaScript refers to the way numbers are represented and manipulated in the programming language. In JavaScript, there are two main types of number systems: decimal (base 10) and binary (base 2).

Decimal numbers are the familiar numbers we use in our everyday lives. These numbers have ten digits (0-9) and are used in arithmetic operations such as addition, subtraction, multiplication, and division. Here's an example of how decimal numbers work in JavaScript:

```
// Decimal Example
let x = 10; // Assigning value 10 to the variable 'x'
let y = 5; // Assigning value 5 to the variable 'y'

console.log(x + y); // Output: 15
console.log(x - y); // Output: 5
console.log(x * y); // Output: 50
console.log(x / y); // Output: 2
```

On the other hand, binary numbers use only two digits, 0 and 1, and are commonly used in computer systems since they are easier for machines to manipulate. Binary numbers are represented using the prefix "0b" in JavaScript. Here's an example of how binary numbers work in JavaScript:

```
// Binary Example
let a = 0b1010; // Assigning binary value 1010 (which is equivalent to decimal 10) to variable 'a'
let b = 0b0110; // Assigning binary value 0110 (which is equivalent to decimal 6) to variable 'b'

console.log(a + b); // Output: 16 (binary 10000)
console.log(a - b); // Output: 4 (binary 0100)
console.log(a * b); // Output: 60 (binary 111100)
console.log(a / b); // Output: 1.6666666666666667 (binary 1.10100110100110100110...)
```

JavaScript provides built-in methods to convert between decimal and binary number systems, such as `parseInt()` and `toString()`. For example:

```
// Converting Binary to Decimal
console.log(parseInt('1010', 2)); // Output: 10

// Converting Decimal to Binary
console.log((10).toString(2)); // Output: "1010"
```

In summary, number system in JavaScript refers to the way numbers are represented and manipulated in the programming language. Decimal numbers have ten digits (0-9) and are used in everyday life, while binary numbers use only two digits (0 and 1) and are commonly used in computer systems.

### Hoisting in numbers

Hoisting in JavaScript is a behavior where variable and function declarations are moved to the top of their respective scopes during the compilation phase, before the code is executed. This means that a variable or function can be used before it is declared in the code.

Let's take an example to understand this concept:

```javascript
console.log(a); // Output: undefined
var a = 10;
```

In the above code snippet, even though we have not declared the variable `a` before using it in the `console.log` statement, the code still runs without any error and outputs `undefined`. This is because during the compilation phase, the variable `a` is hoisted to the top of the scope and assigned a default value of `undefined`. Therefore, when we try to access the value of `a` before its declaration, we get the value `undefined`.

Similarly, let's take an example with functions:

```javascript
foo(); // Output: 'Hello, World!'

function foo() {
  console.log("Hello, World!");
}
```

In the above code snippet, even though we are calling the `foo()` function before its declaration, the code still runs without any error and outputs `'Hello, World!'`. This is because during the compilation phase, the function declaration is hoisted to the top of the scope, so the `foo()` function is already available when we call it.

In simpler terms, hoisting in JavaScript means that variable and function declarations are moved to the top of their respective scopes, making them available for use before they are actually declared in the code.

### Math and Rounding

Math and Rounding are important concepts in JavaScript that deal with mathematical operations and rounding off numbers.

Math is a built-in object in JavaScript that provides various mathematical functions such as finding the square root, calculating trigonometric values, etc. These functions can be accessed using the Math object and the dot notation. For example, to find the square root of a number in JavaScript, we can use the Math.sqrt() function:

```
let num = 25;
let sqrtNum = Math.sqrt(num);
console.log(sqrtNum); // Output: 5
```

Rounding is the process of converting a number to its nearest whole number or a specified number of decimal places. In JavaScript, there are several methods to round numbers, including Math.round(), Math.ceil(), and Math.floor().

- Math.round() function rounds a number to the nearest whole number. If the fractional part is .5 or greater, the number is rounded up, otherwise, it is rounded down. Here's an example:

```
let num = 3.6;
let roundedNum = Math.round(num);
console.log(roundedNum); // Output: 4
```

- Math.ceil() function always rounds a number up to the nearest whole number. Here's an example:

```
let num = 3.2;
let roundedNum = Math.ceil(num);
console.log(roundedNum); // Output: 4
```

- Math.floor() function always rounds a number down to the nearest whole number. Here's an example:

```
let num = 3.8;
let roundedNum = Math.floor(num);
console.log(roundedNum); // Output: 3
```

Math aur Rounding JavaScript mein mathematical operations aur numbers ko round karne ke important concepts hai. Math ek built-in object hai jo ki bahut se mathematical functions provide karta hai jaise ki square root find karna, trigonometric values calculate karna, etc. Ye functions Math object aur dot notation ka use karke access kiye ja sakte hai. Rounding ek process hai jisme ham ek number ko uske nearest whole number ya specified number of decimal places me convert karte hai. JavaScript me rounding ke liye kuch methods hote hai jaise ki Math.round(), Math.ceil(), aur Math.floor().

### The Reminder operator

The Reminder operator in JavaScript is represented by the percent sign (%). It is also known as the modulo operator. It returns the remainder of a division operation between two numbers.

For example, when we divide 10 by 3, the quotient is 3 with a remainder of 1. In JavaScript, we can use the reminder operator to get the remainder:

```
10 % 3 // returns 1
```

Another example would be dividing 15 by 5, which gives a quotient of 3 with no remainder:

```
15 % 5 // returns 0
```

the reminder operator as "bacha hua" or "shesh". When we perform division, sometimes there is a leftover amount that doesn't divide evenly. The reminder operator gives us that leftover amount. For example, agar hum 10 ko 3 se divide karein toh humein teen ka quotient aur ek ka bacha hua milega. Aur yeh bacha hua, jo ki 1 hai, hum reminder operator ke zariye hasil kar sakte hai:

```
10 % 3 // 1 dega
```

Ek aur udahran hota hai jab hum 15 ko 5 se divide karte hai, jismein quotient 3 hai aur koi bacha hua nahi hai:

```
15 % 5 // 0 dega
```

### Numeric Separators

Numeric separators are characters that can be used to separate groups of digits in a number in JavaScript. This helps improve the readability of large numbers and makes it easier to understand them.

For example, consider the number 1000000. It can be difficult to quickly determine how many zeroes there are without counting them one by one. With numeric separators, we can write this number as 1_000_000, making it much easier to read at a glance.

Numeric separators are represented by an underscore (\_) character and can be placed anywhere within a number, except at the beginning or end.

Here's an example:

```
const bigNumber = 1_234_567_890;
console.log(bigNumber); // Output: 1234567890
```

In this example, we've used numeric separators to make `bigNumber` more readable. The underscores have no effect on the actual value of the number, but they make it easier to read and understand.

अंक विभाजक जावास्क्रिप्ट में उन वर्णों को कहते हैं जो कि एक संख्या में अंकों के समूहों को अलग करने के लिए उपयोग किए जाते हैं। यह बड़ी संख्याओं की पठनीयता में सुधार करता है और इन्हें समझने में आसान बनाता है।

उदाहरण के रूप में, एक संख्या 1000000 को ध्यान में रखते हुए लिखना काफी मुश्किल हो सकता है जब आप इसमें शून्यों की संख्या को गिनते हुए जानने की कोशिश करते हैं। अंक विभाजक का उपयोग करके, हम इस संख्या को 1_000_000 के रूप में लिख सकते हैं, जिससे इसे एक नजर में पढ़ना बहुत आसान हो जाता है।

अंक विभाजक अंडरस्कोर (\_) वर्ण द्वारा प्रतिनिधित होते हैं और एक संख्या के भीतर कहीं भी रखे जा सकते हैं, शुरुआत या अंत में नहीं।

निम्नलिखित उदाहरण में, हमने अंक विभाजक का उपयोग करके `bigNumber` जैसी संख्या को और पठनीय बनाया है। अंडरस्कोर का कोई भी प्रभाव संख्या के वास्तविक मान पर नहीं होता है, लेकिन वह इसे पढ़ने और समझने में आसान बनाता है।

```
const bigNumber = 1_234
```

### Working with BigInt

BigInt ek JavaScript data type hai jo normal integers se bade numbers ko store karne ki suvidha deta hai. BigInt ka use tab kiya jata hai jab hume bahut bade numeric values handle karne hote hai jo ki JavaScript ke normal Number data type ki capacity se jyada hai.

JavaScript me, jab hum kisi variable ko declare karte hai to wah by default Number data type ka hota hai. Lekin agar hume kisi bade number ko store karna hai to uske liye hume BigInt data type ka use karna padta hai.

BigInt ko declare karne ke liye hume number ke end me 'n' lagana hota hai. Iske alawa hume BigInt ke saath normal numbers ka use nahi karna chahiye, jaise ki 1 + 2n likhna theek hai lekin 1n + 2n likhna galat hai.

Yeh ek example hai jisme hum ek bada number store karenge aur uska square root nikalenge:

```
const bigNumber = 1234567890123456789012345678901234567890n;
const bigSqrt = Math.sqrt(bigNumber); // Error: cannot convert BigInt to number
console.log(bigSqrt);
```

Is code me humne `bigNumber` variable me ek bada number store kiya hai. Fir hum `Math.sqrt()` function ka use karke is number ka square root calculate karne ki koshish karenge, lekin yaha error aayega kyunki ye function BigInt ko handle nahi kar sakta.

Iske bajaye, hum `"big-integer"` ya `"bignumber.js"` jaise third-party libraries ka use kar sakte hai jiske through hum bade numbers ko handle kar sakte hai. Upar diye hue example ko agar hum `"bignumber.js"` library ke saath rewrite kare to ye is tarah se dikhega:

```
const BigNumber = require("bignumber.js");
const bigNumber = new BigNumber('1234567890123456789012345678901234567890');
const bigSqrt = bigNumber.sqrt();
console.log(bigSqrt.toString()); // "1.1102230246251561122324293051892e+24"
```

Is code me humne `"bignumber.js"` library ko import karke `BigNumber` class ka instance banaya hai jisme hum apna bada number store kiya hai. Fir hum `sqrt()` function ka use karke is number ka square root calculate karenge aur usko console me print karenge.

Mujhe ummeed hai ki yeh samajhne me aapki madad karega ki JavaScript me BigInt data type ka use kaise kiya jata hai.

### Number class functions

Number class functions in javascript are a set of built-in functions that can be used to perform various operations on numbers in javascript. These functions are part of the Number data type and can be accessed using dot notation.

For example, let's say we have a number variable called `num` which has a value of 5. We can use the following Number class functions:

1. `toString()`: This function converts a number to its string representation.

Example: `num.toString();` // Returns "5" as a string

2. `toFixed()`: This function formats a number with a fixed number of decimal places.

Example: `num.toFixed(2);` // Returns "5.00" as a string

3. `parseInt()`: This function parses a string and returns an integer.

Example: `parseInt("10");` // Returns 10 as an integer

4. `parseFloat()`: This function parses a string and returns a floating point number.

Example: `parseFloat("10.5");` // Returns 10.5 as a floating point number

5. `isNaN()`: This function checks if a value is NaN (not a number).

Example: `isNaN(num);` // Returns false since num is a number and not NaN

6. `isFinite()`: This function checks if a value is finite (not Infinity or -Infinity).

Example: `isFinite(num);` // Returns true since num is finite

Number class functions javascript mein uss set ke functions hote hai jo ki numbers par various operations perform karne ke liye use kiye jaate hai. Ye functions Number data type ke hisse hote hai aur dot notation se access kiye ja sakte hai. Inmein se kuch common functions jaise ki toString(), toFixed(), parseInt(), parseFloat(), isNaN() aur isFinite() hai. Ye functions numbers ko string representation me convert karna, decimal places ke sath format karna, integer ya floating point number me parse karna, NaN aur finite check karna jaisi operations perform karne ke liye use kiye jaate hai.
### Creating Dates and different ways of creating Date object

Date object ek built-in object hai jo JavaScript mein available hota hai aur isse hum date aur time ko represent kar sakte hain. Date object ke use se hum current date, specific date ya phir time ki calculations kar sakte hain.

JavaScript mein Date object ko create karne ke kuch different tarike hain:

1. Current date ka use karke:
   Hum simply Date() function ka use karke current date and time ko generate kar sakte hain.

Example:

```
const currentDate = new Date();
console.log(currentDate); // output: Mon Apr 05 2023 16:23:34 GMT+0530 (India Standard Time)
```

2. Specific date ka use karke:
   Agar humein kisi specific date ko JavaScript mein represent karna hai to hum String format mein date ko pass kar sakte hain.

Example:

```
const specificDate = new Date("2023-04-10");
console.log(specificDate); // output: Sun Apr 09 2023 18:30:00 GMT+0530 (India Standard Time)
```

3. Number of milliseconds ka use karke:
   Hum Date object ko create kar sakte hain by passing the number of milliseconds since January 1, 1970, 00:00:00 UTC.

Example:

```
const dateInMs = new Date(1657209000000);
console.log(dateInMs); // output: Fri Jul 07 2022 02:30:00 GMT+0530 (India Standard Time)
```

4. Specific year, month, day, hour, minute, second aur millisecond ka use karke:
   Hum Date object ko aise bhi create kar sakte hain jismein humein specific year, month, day, hour, minute, second aur millisecond ki values pass karni hoti hai.

Example:

```
const specificDateTime = new Date(2023, 3, 10, 11, 30, 0, 0);
console.log(specificDateTime); // output: Fri Apr 10 2023 11:30:00 GMT+0530 (India Standard Time)
```

Is tarah se hum JavaScript mein Date object create kar sakte hain aur apne kaam ke according uska use bhi kar sakte hain.

### Understanding milliseconds and other units of time

Javascript me time ka istemal hum kabhi bhi kar sakte hai, lekin iske units ki samajh jaruri hai, jaise milliseconds. Milliseconds ek bahut chota unit hai, jo 1 second ke 1000 parts ko represent karta hai. Isi tarah, dusre units hai jaise seconds, minutes, hours, days.

Jab hamara program chalta hai to hume kabhi kabhi time tracking ki zarurat padti hai, jaise ek timer ya animation ke liye. In cases me hum milliseconds ka use karte hai. Javascript me time tracking ke liye hume `Date` object use karna hota hai.

Example: Agar aapko ek function banana hai jo 5 seconds ke baad kuchh execute kare, to iska code kuchh is tarah se hoga:

```javascript
setTimeout(function () {
  console.log("Function executed after 5 seconds");
}, 5000);
```

setTimeout() function ka use kiya hai, jo ek callback function ke sath ek time interval deta hai. Time interval milliseconds me specify kiya jata hai. Is example me, humne setTimeout() me 5000 pass kiya hai, matlab ki 5 seconds (5000 milliseconds) ke baad callback function execute hoga.

Isi tarah, setInterval() function ka use bhi kiya ja sakta hai. setInterval() function callback function ko specified time interval ke baad repeated tarike se call karta hai. Example ke liye:

```javascript
setInterval(function () {
  console.log("Function executed every 2 seconds");
}, 2000);
```

Is example me, setInterval() function 2000 milliseconds me callback function ko repeat tarike se call karega, matlab ki har 2 seconds baad.

Javascript me time units ki samajh bahut zaruri hai, kyunki isse hum animations aur timers ke liye sahi logic banane me madad milti hai.

### what is Operations with Dates in javasript ? Explain in detail with example and in Hinglish language.

JavaScript provides built-in support for performing operations with dates. You can create, manipulate, and format dates using Date objects and various methods available in JavaScript's Date API.

To create a new date object, you can use the `new Date()` constructor. For example, to create a date object representing the current date and time, you can simply call `new Date()`.

```
const today = new Date();
```

You can also create a date object by passing in a string representing the desired date and time. The string should be formatted in a specific way, such as "YYYY-MM-DDTHH:mm:ss.sssZ". For example:

```
const christmas = new Date('2022-12-25T00:00:00.000Z');
```

Once you have a date object, you can perform various operations on it. For example, you can get the year, month, day, hour, minute, and second of a date using various getter methods.

```
const year = today.getFullYear(); // returns the current year
const month = today.getMonth(); // returns the current month (0-11)
const day = today.getDate(); // returns the current day of the month (1-31)
const hour = today.getHours(); // returns the current hour (0-23)
const minute = today.getMinutes(); // returns the current minute (0-59)
const second = today.getSeconds(); // returns the current second (0-59)
```

You can also set the year, month, day, hour, minute, and second of a date using various setter methods.

```
today.setFullYear(2023); // sets the year to 2023
today.setMonth(3); // sets the month to April (0-based)
today.setDate(5); // sets the day of the month to 5
today.setHours(12); // sets the hour to 12
today.setMinutes(30); // sets the minute to 30
today.setSeconds(0); // sets the second to 0
```

You can perform arithmetic operations on dates using various methods, such as `getTime()`, which returns the number of milliseconds since January 1, 1970.

```
const christmas = new Date('2022-12-25T00:00:00.000Z');
const now = new Date();
const differenceInMilliseconds = christmas.getTime() - now.getTime();
const differenceInDays = differenceInMilliseconds / (1000 * 60 * 60 * 24);
```

Finally, you can format a date object into a string using various methods, such as `toLocaleDateString()` or `toLocaleTimeString()`. For example:

```
const formattedDate = today.toLocaleDateString('hi-IN'); // formats the date as "dd/MM/yyyy"
const formattedTime = today.toLocaleTimeString('hi-IN'); // formats the time as "hh:mm:ss AM/PM"
```

Yadi aap kisi specific date ko represent karna chahte hai toh aap 'new Date()' constructor ka use kar sakte hai. Jaise ki humne upar diya hai. Iske baad aap date ke year, month, day, hour, minute aur second ka pata laga sakte hai getters ka use karke. Iske alawa aap setters ka use karke bhi ye values set kar sakte hai. Aap getTime() method ka use karke dates ke beech me arithmetic operations kar sakte hai. Finally, aap dates ko string me convert karke display kar sakte hai by using toLocaleDateString() aur toLocaleTimeString() methods.

### what is Date setter methods

Date setter methods in JavaScript are functions that allow you to set specific parts of a Date object, such as the year, month, day, hour, minute, and second.

For example, let's say you want to create a Date object for April 5th, 2023 at 9:30 AM. You can use the following code:

```
var myDate = new Date();
myDate.setFullYear(2023);
myDate.setMonth(3); // Note: Months start from 0 in JavaScript, so 3 represents April
myDate.setDate(5);
myDate.setHours(9);
myDate.setMinutes(30);
myDate.setSeconds(0);
```

In this example, we first create a new Date object using the `new Date()` constructor, which creates a Date object with the current date and time. Then, we use the various Date setter methods to set the year, month, day, hour, minute, and second to the desired values.

Using these setter methods allows you to easily modify specific parts of a Date object without having to create a new Date object from scratch.

### what is Internationalization Dates

Internationalization of dates in JavaScript refers to the process of displaying and formatting dates according to the conventions followed by people in different regions of the world. This ensures that the date representation is easily understandable and readable by people from different cultures and languages.

For example, in the United States, the date format is typically MM/DD/YYYY (month/day/year), whereas in many European countries, the format is DD/MM/YYYY (day/month/year). Similarly, the way days and months are abbreviated, the use of 12-hour or 24-hour clock, and the inclusion or exclusion of leading zeros may differ between regions.

To handle these variations, JavaScript provides a built-in object called "Intl" that includes various properties and methods for internationalizing dates. Here's an example of how to use the "Intl.DateTimeFormat()" method to format a date in Hinglish, which is a mixture of Hindi and English:

```
// Create a new date object
const date = new Date('2022-07-15');

// Create a formatter object with the desired language and options
const formatter = new Intl.DateTimeFormat('hi-IN', {
  weekday: 'long',
  year: 'numeric',
  month: 'long',
  day: 'numeric',
  hour: 'numeric',
  minute: 'numeric',
  timeZoneName: 'short'
});

// Format the date using the formatter object
const formattedDate = formatter.format(date);

// Output the formatted date
console.log(formattedDate);
```

In this example, we create a new date object representing July 15th, 2022. We then create a formatter object using the "Intl.DateTimeFormat()" method and pass in the language code for Hindi (hi) and India (IN), as well as several options for how we want the date to be formatted. Finally, we call the "format()" method on the formatter object to convert the date into a string using the specified format.

The resulting output might look something like this:

```
शुक्रवार, १५ जुलाई २०२२, २:३० PM GMT+5:30
```

This represents the date and time in a way that is familiar and easily understandable to someone who speaks Hinglish. The weekday is spelled out in full (शुक्रवार), the month is spelled out in full (जुलाई), and the time includes the AM/PM indicator as well as the time zone (GMT+5:30).

### what is setTimeOut and setInterval

setTimeout aur setInterval dono JavaScript mein time-based functions hote hai jo code ko delay karne ya phir repeat karna kaam karte hai.

setTimeout ek function hai jo ek delay ke baad ek baar code ko chalata hai. Yeh function do arguments leta hai - ek callback function aur ek time duration in milliseconds. Callback function, jo ki chalaya jayega jab delay complete ho jayega, setTimeout function se ek unique identifier return karta hai jo hum cancel kar sakte hai agar chahiye.

Iska ek example hai:

```
setTimeout(function() {
  console.log("Hello, world!");
}, 3000);
```

Yahan pe, setTimeout function `function()` ko 3 seconds (3000 milliseconds) ke baad run karega. Iske baad "Hello, world!" console pe print hoga.

setInterval bhi ek function hai jo code ko delay karne ke saath-saath regularly repeat karta hai. setInterval bhi do arguments leta hai - ek callback function aur ek time duration in milliseconds. setInterval function se bhi unique identifier return hota hai jo hum cancel kar sakte hai.

Iska ek example hai:

```
var count = 0;
var intervalId = setInterval(function() {
  console.log(count);
  count++;
  if (count === 5) {
    clearInterval(intervalId);
  }
}, 1000);
```

Yahan pe, setInterval function `function()` ko 1 second (1000 milliseconds) ke baad run karega. Jaise hi wo chalega, yeh `count` variable ko 1 increase karega aur usko console pe print karega. Agar `count` 5 ke equal ho jata hai, to setInterval ko clearInterval se cancel kar diya jayega.
### what is (DRY) principle in javascript ? Explain in detail with example and in Hinglish language.

DRY principle kehta hai ki humein ek hi jaga kaam karne wale code ko baar-baar likhna nahi chahiye balki uska use alag alag jagao pe karne ke liye functions ya classes bana kar karna chahiye. Isse code ki length kam hoti hai aur future mein code maintenance aur modification bhi aasaan hoti hai.
The DRY principle in JavaScript stands for "Don't Repeat Yourself". It is a software development principle that encourages developers to avoid duplicating code and instead promote code reuse.

In simpler words, DRY principle tells us to not write the same code over and over again, but rather create functions or classes that can be reused throughout the codebase. This helps reduce code redundancy, improves maintainability, and makes it easier to update and modify the code in the future.

For example, let's say we have a web application that needs to calculate the area of a rectangle in multiple places. Instead of writing the same calculation logic every time, we can define a function to handle it:

```javascript
function calculateRectangleArea(width, height) {
  return width * height;
}
```

Now, whenever we need to calculate the area of a rectangle, we can simply call this function instead of rewriting the same code:

```javascript
const area = calculateRectangleArea(10, 20);
console.log(area); // Output: 200
```
### What is Array:

Array ek Data Structure hota hai jiska use ek se jyada items ko store krane ke lie kia jata hai. Array me kisi b type ka data store kraya ja skta hai. Array me sare element contigous (memory me pas pas) memory block me save hote hain.

Arrays index based hote hai. Iska matlab ye hai ki hm array me elements ko index se access kr skte hain. Array ki index 0 se start hoti hai.

Javascript me array ek non primitive type hai. Array ek object hota hain. Yadi hume ek se jyada value store karvani hai to hume utne variable bnane pdenge jitni values hain. Is problem ko solve karne ke liye hum Array ka use karte hain.

Array me jis order me value insert ki hain usi oder me value niklegi. Yadi hum ko random order me value nikalni hain to index ka use kar skte hain.

Array dynamic nature ka hota hai. It means iski size dynamically apne aap badhegi ya kam hogi jaise jaise hum elements ko add/remove krenge.

-Array two type se bana skte hain:

- Literal way

  ```
  let arr= [1,2,3];
  ```

- Object way

```
  let arr = new array();
  console(arr[1]);
```

- Yadi hume Array ki size check krni hai to length property use kr skte hain

```
  console.log(arr.length);
```

### What is Looping Array:

Array ka nature iterable type ka hota hain. iska matlab yeh hain ki array par loop chlaya ja skta hain. yadi arrya par hum for loop, while loop, do while loop ka use karte hain to 0 se lekar array ki length se 1 kam tak loop chla skte hain. array par hum for of loop b chla skte hain.

- Javascript me set, map, string, etc by default Array support karte hain.

Array me kafi built-in functions hain jinhe use krke hm Array pr kaam kr skte hain

- Array functions:

# push():

push array function se array के end me एक या एक से ज्यादा elements को जोड़ा जाता है और उसके बाद array की length return करता है |

- Syntax for push():
  arr.push(addElement1,...addElementN)
- for example:

  ```
  var arr = [15, 20, 30, 50, 55];
  document.write("Array : " + arr + "<br />");
  document.write("Length of Array : " + arr.push(65) + "<br />");
  document.write("Array : " + arr + "<br />");
  document.write("Length of Array : " + arr.push(75, 70) + "<br />");
  document.write("Array : " + arr + "<br />");

  ```

  output:

Array : 15,20,30,50,55
Length of Array : 6
Array : 15,20,30,50,55,65
Length of Array : 8
Array : 15,20,30,50,55,65,75,70

# sort():

sort array method में alphabet और numeric array को sort किया जाता है | sort() method ख़ास string array के लिए बनाया गया है | sort function diye gye Array ko natural sorting order me sort krta hai. For example A, B se phle aayega. Isi trah 10, 2 se phle aayega. Numbers ko sort krne ke lie hm compare function bna skte hain.

- Syntax for sort():

  ```
  arr.sort(function(a,b) {
    return a-b; //ascending order
  });
  ```

- for example:
  ```
  var names = ["Rakesh", "Mukesh", "Ramesh", "Kamalesh"];
  document.write(names.sort() + "<br />");
  ```

output: Kamalesh,Mukesh,Rakesh,Ramesh

let num = [1, 2, 3, 4, 10, 100, 20, 50, 31];
console.log(
num.sort(function (a, b) {
return b - a;
})
);

output: [100, 50, 31, 20, 10, 4, 3, 2, 1]

```
let num = [1, 2, 3, 4, 10, 100, 20, 50, 31];
 console.log(
   num.sort(function (a, b) {
     return a - b;
   })
 );

 output: [1, 2, 3, 4, 10, 20, 31, 50, 100]
```

### pop():

pop() array method में array के last element को array से remove
करके return किया जाता है |

- Syntax for pop():
  arr.pop()

- for example:

```
 var arr = [15, 20, 30, 50, 55];

 document.write("Array : " + arr + "<br />");
 document.write("Removed Element : " + arr.pop() + "<br />");
 document.write("Array : " + arr + "<br />");
 document.write("Removed Element : " + arr.pop() + "<br />");
 document.write("Array : " + arr + "<br />");
 document.write("Removed Element : " + arr.pop() + "<br />");
 document.write("Array : " + arr + "<br />");

output:
 Array : 15,20,30,50,55
 Removed Element : 55
 Array : 15,20,30,50
 Removed Element : 50
 Array : 15,20,30
 Removed Element : 30
 Array : 15,20
```

### unshift():

unshift() method से array ki starting में एक या एक से ज्यादा element(s) को add किया जाता है और नए array की length को return किया जाता है |

- Syntax for unshift():
  arr.unshift(element1,...,elementN)

-for example:

```
 var arr = [1, 2, 3, 4, 5];
 document.write(
   "Length of Array after adding Elements: " + arr.unshift(6, 7, 8) + "<br />"
 );
 document.write(arr);

output:
 Length of Array after adding Elements: 8
 6,7,8,1,2,3,4,5
```

### shift():

shift() array method में array के शुरुआत के element को remove किया जाता है |

- Syntax for shift():
  arr.shift()

- for example:
  ```
  var arr = [15, 20, 30, 50, 55];
  document.write("Array : " + arr + "<br />");
  document.write("Removed Element : " + arr.shift() + "<br />");
  document.write("Array : " + arr + "<br />");
  document.write("Removed Element : " + arr.shift() + "<br />");
  document.write("Array : " + arr + "<br />");
  document.write("Removed Element : " + arr.shift() + "<br />");
  document.write("Array : " + arr + "<br />");
  ```

output:
Array : 15,20,30,50,55
Removed Element : 15
Array : 20,30,50,55
Removed Element : 20
Array : 30,50,55
Removed Element : 30
Array : 50,55

```

```

### toString():

toString() array method से array को string में convert किया जाता है |

- Syntax for toString():
  arr.toString()

- for example:
  ```
  var arr = [1, 2, 3, 4, 5];
  document.write("Type : " + typeof arr + "<br />");
  document.write(arr + "<br /><br />");
  document.write("Type : " + typeof arr.toString() + "<br />");
  document.write(arr.toString() + "<br />");
  ```

output:
Type : object
1,2,3,4,5

Type : string
1,2,3,4,5

```

```

### join():

join() array method में दिए हुए seperator से हर element को seperate किया जाता है |

- Syntax for join():
  arr.join(object_name)

- for example:

```
var arr = [10, 20, 30, 40, 50];
document.write(arr.join() + "<br />");
document.write(arr.join("."));

output:
10,20,30,40,50
10.20.30.40.50
```

### concat():

concat() array method में एक या एक से ज्यादा arrays को जोड़ा जाता है |

- Syntax for concat():
  arr1.concat(arr2, arr3, arrN)

- for example:

```
var arr1 = [1, 2, 3, 4];
var arr2 = [5, 6, 7, 8];
var arr3 = [9, 10, 11, 12];
document.write(arr1.concat(arr2, arr3) + "<br />");
document.write(arr2.concat(arr2, arr3) + "<br />");

output:
1,2,3,4,5,6,7,8,9,10,11,12
5,6,7,8,5,6,7,8,9,10,11,12
```

### splice():

splice() array method में array में elements add(s) या remove(s) किये जाते है और removed किये गए element को return करता है |

- Syntax for splice():
  arr.splice(startIndex, howMany, element1,..,elementN)

### Parameter :

startIndex : यहाँ पर जो index दी जाती है वहा से array के element(s) add या remove किये जाते है | अगर index array की length से बड़ा होता है तो कोई element remove नहीं होता बल्कि array के elements end पर add किये जाते है |

howMany : ये optional होता है | अगर कोई value दी नहीं जाती तो इसकी default value '0' होती है | मतलब कोई element remove नहीं होता | अगर कोई number दिया जाता है तो startIndex से इस number तक elements को remove किया जाता है |

(element1,..elementN) : यहाँ पर add किये जानेवाले element(s) को दिया जाता है |

- for example:

```
var arr1 = [1, 2, 3, 4, 5];
document.write("Removed Element(s) : " + arr1.splice(2, 3) + "<br />");
document.write("splice() Returned Array : " + arr1 + "<br /><br />");
var arr2 = [1, 2, 3, 4, 5];
document.write("Removed Element(s) : " + arr2.splice(2, 3, 5, 6, 5) + "<br />");
document.write("splice() Returned Array : " + arr2 + "<br");

output:
Removed Element(s) : 3,4,5
```

### splice() Returned Array : 1,2

Removed Element(s) : 3,4,5
splice() Returned Array : 1,2,5,6,5

### slice():

slice() array method में start और end index से नए array को return किया जाता है |

- Syntax for slice():
  arr.slice(start, end)

start : इस index से slice की शुरुआत होती है | यहाँ पर अगर negative index होता है तो array के end से slice किया जाता है |

end : इस index पर slice का end होता है | ये optional होता है | यहाँ ये दिया नहीं जाता तो start से array के सभी elements return किये जाते है |

- for example:

```
var arr = [15, 20, 30, 50, 55];
document.write(arr.slice(2) + "<br />");
document.write(arr.slice(2, 3) + "<br />");
document.write(arr.slice(2, -1) + "<br />");

output:
30,50,55
30
30,50
```

### sort():

sort() array method में alphabet और numeric array को sort किया जाता है | sort() method ख़ास string array के लिए बनाया गया है |

- Syntax for sort():
  arr.sort(compare_func)

compare_func : इस function से sort order define किया जाता है | ये optional होता है | अगर दिया नहीं जाता तो natural ascending order से sort किया जाता है |

- for example:
  Syntax for sort():

```
arr.sort(function(a,b) {
return a-b; //ascending order
});

arr.sort(function(a,b) {
return a-b; //descending order
});
```

- for example:

```
var names = ["Rakesh", "Mukesh", "Ramesh", "Kamalesh"];
document.write(names.sort() + "<br />");
output: Kamalesh,Mukesh,Rakesh,Ramesh

let num = [1, 2, 3, 4, 10, 100, 20, 50, 31];
console.log(
num.sort(function (a, b) {
return b - a;
})
);

output: [100, 50, 31, 20, 10, 4, 3, 2, 1]

```

```
let num = [1, 2, 3, 4, 10, 100, 20, 50, 31];
console.log(
num.sort(function (a, b) {
return a - b;
})
);

output: [1, 2, 3, 4, 10, 20, 31, 50, 100]
```

### reverse():

### reverse()

array method में दिए हुए array के elements को reverse किया जाता है |

- Syntax for reverse():
  arr.reverse()

- for example:

```
var arr = [15, 20, 30, 30, 50];
document.write(arr.reverse() + "<br />");

output:
50,30,30,20,15
```

### forEach():

forEach() array method में हर एक array element के लिए function execute किया जाता है |

- Example for forEach():

```
var arr = [10, 20, 30, 40, 50];
arr.forEach(function (element, index) {
document.write("[" + index + "]: " + element + "<br />");
});

output:
[0]: 10
[1]: 20
[2]: 30
[3]: 40
[4]: 50
```

### map():

map function , एक callback function या arrow function accept करता है , callback function में value और index number दोनों मिलते हैं जबकि arrow function में सिर्फ value मिलती है।

map() function Array के प्रत्येक value को user defined callback function में send करता है , और एक Array नई values के साथ return करता है।

- for example:

```
let arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
let table_of_two = arr.map(function (value) {
return value \* 2;
});
document.write(table_of_two);

output:
2,4,6,8,10,12,14,16,18,20
```

### filter():

filter() array method में दिए हुए function से हर एक array के element को check करके उनका array return करता है | अगर array में से एक भी element function के statement के विरुद्ध होता है तो उस array के element को remove किया जाता है |

filter() function से original array पर कोई फर्क नहीं पड़ता |

- Example for filter():

```
function checkPositive(checkvalue) {
return checkvalue >= 0;
}
```

```
var arr1 = [1, 2, 3, 4, 5];
document.write(arr1.filter(checkPositive) + "<br />");
var arr2 = [1, 2, -3, 4, 5];
document.write(arr2.filter(checkPositive));

output:
1,2,3,4,5
1,2,4,5
```

### find():

find() array method में दिए हुए function के statement से related अगर कोई पहला index find होता है तो उसकी value return होती है |

- Example for find():

function checkfunc(checkvalue) {
return checkvalue > 1;
}

```
var arr1 = [1, 2, 3, 4, 5];
document.write(arr1.find(checkfunc) + "<br />");
var arr2 = [10, 5, 9, 3, 1];
document.write(arr2.find(checkfunc) + "<br />");
var arr3 = [0, -1, 2, 1, 0];
document.write(arr3.find(checkfunc));

output:
2
10
2
```

### findIndex():

findIndex() array में दिए हुए function के statement से related अगर कोई पहला index find होता है तो उसकी index return होती है |

- Example for find():
  function checkfunc(checkvalue) {
  return checkvalue > 1;
  }

```
var arr1 = [1, 2, 3, 4, 5];
document.write(arr1.findIndex(checkfunc) + "<br />");
var arr2 = [10, 5, 9, 3, 1];
document.write(arr2.findIndex(checkfunc) + "<br />");
var arr3 = [0, -1, 2, 1, 0];
document.write(arr3.findIndex(checkfunc));

output:
1
0
2
```

### some():

some() array method में अगर एक भी element function के statement से related हो तो ये 'true' return करता है | अगर function के statement से related नहीं होता तो 'false' return होता है |

some() method, every() method के विरुद्ध होता है |

- Example for some():

function checkNegative(checkvalue) {
return checkvalue < 0;
}

```
var arr1 = [1, 2, 3, 4, 5];
document.write(arr1.some(checkNegative) + "<br />");
var arr2 = [1, 2, -3, 4, 5];
document.write(arr2.some(checkNegative));

output:
false
true
```

### every():

every() array method से दिए हुए function से हर एक array के element को check करके boolean value return करता है | अगर array में से एक भी element function के statement के विरुद्ध होता है तो 'false' value return होती है |

- Example for every():

function checkPositive(checkvalue) {
return checkvalue >= 0;
}

```
var arr1 = [1, 2, 3, 4, 5];
document.write(arr1.every(checkPositive) + "<br />");
var arr2 = [1, 2, -3, 4, 5];
document.write(arr2.every(checkPositive));

output:
true
false
```

### at():

at() function di gyi index pr jo element hota hai use return krta hai. at function ki ye speciality ki hai ki ye negative index b leta hai. Negative index ke case me ye array se item last se return krta hai. Last element ke lie -1 index deni hoti hai. Isi trah second last element ke lie -2 index deni hoti hai

- for example:

```
var arr = [10, 20, 30, 40, 50];
console.log(arr.at(1));
console.log(arr.at(2));
console.log(arr.at(-1));
console.log(arr.at(-2));

output:
20
30
50
40
```

### reduce():

reduce() function array ke sare elements ko iterate krta hai aur ek single value return krta hai. reduce() function 2 arguments leta hai :

- callback function
- initial value (ise accumulator b kha jata hai )

callback function array ke sare elements ke lie call hota hai aur ye 2 arguments leta hai :

- the accumulator
- current element
  callback function fir updated value return krna chahiye

for example below function array ke elements ka sum calcualte krega:

```
let myArray = [1, 2, 3, 4, 5];
let sum = myArray.reduce((accumulator, currentValue) => accumulator + currentValue, 0);
console.log(sum); // 15
```

### reduce():

function ka use array ko ek object bnane ya kisi other type ka data structure bnane me kia ja skta hai. Iske lie hume ek accumulator object dena hoga and callback function us object ko each iteration me update krega

- for example:

```
let myArray = [{x: 1, y:2}, {x: 3, y: 4}]
let result = myArray.reduce( (acc, cur) => {
acc[cur.x] = cur.y;
return acc;
}, {})
console.log(result); // {1: 2, 3: 4}
```

### reduce()

function me yadi initial value ni di gyi hai to array ka first element ko initial value mana jayega. Is case accumulator first value hoga and current value second value hogi.

- for example:

```
var arr = [10, 20, 30, 40, 50];
let sum = arr.reduce(function (total, val) {
return total + val;
}, 100);
console.log(sum); // 250
let sum = arr.reduce(function (total, val) {
return total + val;
});
console.log(sum); // 150
```

### flat():

flat() function yadi array ke inside array hai to unko ek single one dimensional array bnane ke kaam aata hai. flat() ek optional parameter number leta hai jaise b depth b khte hai jo ye decide krta hai ki Array kitni depth tak merge hoke ek single array bnega.

For example, following code arrays ko merge krke ek single array me return krta hai:

```
let myArray = [[1, 2], [3, 4], [5, 6]];
let flatArray = myArray.flat();
console.log(flatArray); // [1, 2, 3, 4, 5, 6]

let myArray = [[1, 2], [3, [4,5]], [6]];
let flatArray = myArray.flat(2); //depth 2
console.log(flatArray); // [1, 2, 3, 4, 5, 6]

```

### flatMap():

flatMap() function, 2 functions flat and map functions ka combination hai. Ye function phle sare elements ko diye hue function ke according map krta hai fir sare elements ko merge krke ek single array bnata hai. flatMap() ek single argument leta hai jisme hume mapping function deta hai jo ki sare elements ke lie call hota hai.

for example niche diye hue code me sare elements ko merge krke ek single array bnayega and har value ko 2 se multiply b krega.

```
let myArray = [[1, 2], [3, 4], [5, 6]];
let flatMappedArray = myArray.flatMap((subArray) => subArray.map((x) => x\*2));
console.log(flatMappedArray); // [2, 4, 6, 8, 10, 12]
```

### flatMap()

us condition me useful hai jha array ke andar nested arrays ho. Kuki hm single step me hi array ko flat and map dono kr skte hai.
### ==========object==========

object ak datastructure hain. jiska use hum data store karne me karte hain.object me data
key value ki form me store hoti hian.

Yadi hum same kam array se kar na chahye to kar skte hain. lakin array me humye index
mainten kar ne padyegi.index yad kar pana kafi tuff hota hain.isleye hum index ki jgha
key ka use karte hain. issye key humasa same rahate hain.par value change ho skte hain.

- Object literal syntax

```
var obj={
    name:"learnjavascript"
}
```

- object using new key word

```
var obj=new object();
```

- annotation

```
var obj={
    name:"learnjavascript"
    age:30
}
```

- dot annotation

```
var age =obj.age;
var name=obj.name;
```

- Bracket annotation;

```
var age = obj['age'];
var name=obj['name'];
```

Defference between brecket annotation and dot annotation

dot annotation me hum actual key ka name likna hota hain.iske leye hum koi variable etc
use nahi kar skte hain.pr brecket annotationme hum variable bhi use kar skte hain.
variable ki jo value hogi vo value object ke andr key ke form me search hogi or vahi
answer hoga.

- for example:

```

let obj ={
    name:"learnjavascript"
    age:20
}

var a ="age";
console.log(obj.age);//correct
console.log(obj.a);// wrong because a name ke koi property nahi hain
console.log(obj["age"]);//correct
console.log(obj['a']);//brecket annotation me a variable ke value age hain.to object me
//age key search hogi na ke a.
```
### Set:

Set b ek datastructure jiska use unique values ke lie kia jata hai
iska matlab yah hai ki set duplicate values ko remove kr deta hai vah keval unique
values hi rkhta hai

- Creating set :

```
var set = new Set(); //Syntax

//Insert elements in set :
//Set me add function ki madad se data dala ja skta hai
set.add(1);
set.add(3);
set.add(5);
set.add(3);
set.add(1);

answer: {
  1, 3, 5;
} //3 or 1 repeat hue hai islie unhe dubara add nhi kia jayega

```

### Elements Order in Set:

Set me jis order me humne data dala hai usi order me data print b hoga lekin yadi koi value repeat hoti hai to vah value us order me ni hogi

- for example

```
set.add(1);
set.add(3);
set.add(5);
set.add(3);
set.add(1);
set.add(6);
{
  1, 3, 5, 6;
}
```

- Set size function:
  size function set ki size ke bare me btata hai.Size function sirf unique values ka count hi btata hai

```
set.add(1);
set.add(3);
set.add(5);
set.add(3);
set.add(1);
set.add(6);

set.size(); // 4
```

### Set has function:

has function argument me ek value vara hai vah us value ko set me check krta hai. Yadi set me vah value hai to true return krega otherwise false return hoga

```
set.add(1);
set.add(3);
set.add(5);
set.add(3);
set.add(1);
set.add(6);

set.has(6); //true
set.has(9); //false
```

### Set devare function:

Set devare function ek argument vara hai vah
us argument ki value ko set me check krta hai. yadi vah value set me
hai to use devare kr dega otherwise devare ni krega

```
set.add(1);
set.add(3);
set.add(5);
set.add(3);
set.add(1);
set.add(6);

set.devare(6); //6 set se remove ho jayega
```

### Index in Set:

Kuki set me se data remove hota hai islie set me data ki
position fix ni hoti. Isi reason se set me index support ni krti hai\*/

- for example

```
set.add(1);
set.add(3);
set.add(5);
set.add(3);
set.add(1);
set.add(6);

set[1]; //kaam ni krega
```

Ise kaam krane ke lie hume set ko array me convert krna pdega tabi
index kaam kregi

```
for example : */
var arr = [...set];
arr[0]; //Ye chlega

//Printing values using for of loop :

set.add(1);
set.add(3);
set.add(5);
set.add(3);
set.add(1);
set.add(6);

//Print values
for (var value of set) {
  console.log(value);
}

//Creating set to Array  :

set.add(1);
set.add(3);
set.add(5);
set.add(3);
set.add(1);
set.add(6);

var arr = [...set]; //Set to Array

//Foreach method on Set :

set.foreach(function (value) {
  console.log(value);
});

```
### Map:

Map bhi ek datastructure hai jiska use key value form me data store krne ke kaam aata hai. Key ke according data map hota hai islie is datastructure ko Map khte hai.

- Creating a new map:
- syntax :

```
var map = new Map();
```

- Adding a value in map :

```
map.set(1, 100);
map.set("A", "hello");
```

left side me key hoti hai vah right side me value hoti hai. Yadi
hum same key pr dubara value add krte hain to purani value new value
se replace ho jati hai

- for example:

```
map.set(1, 100);
map.set("A", "hello");
map.set(1, 1000);
```

to is example me 1 key pr value 1000 hogi na ki 100 kuki humne value
ko replace kr dia hai.

### Chaining in Map:

Chaining ka matlab yeh hai ki bar bar map variable ka reference use krne ki bjay hum set function pr direct next set function call kr skte hai. Kuki set function vah map hi return krta hai.

- for example

```
var map = new Map();
map.set(1,100);
map.set('A', "hello");
```

- Isko hum Chaining ki through kr skte hain.

```
map.set(1,100).set('A', "hello");
```

### Get function:

Map ka get function argument me key vara hai vah us key se mapped value return krta hai

- for example

```
map.get(1); //100 return krega
map.get('A'); //Hello return krega
```

### has function:

Map ka has function argument me key vara hai aur check krta hai ki vah key map me hai ya nhi. agar vah key map me hai to true return krta hai otherwise false return krta hai.

- for example:

```
map.has(1); //true return krega kuki 1 key hai
map.has(12); //false return krega kuki 12 key ni hai
```

### size function:

map ka size function map me kitni key hain unka count return
krta hai.

- for example:

```
var map = new Map();
map.set(1,100);
map.set('A', "hello");

map.size(); //2 return krega kuki is map me 2 keys hain
```

### clear function:

map ka clear function map ko khali kr deta hai. Khali ka matlab yah hai ki map se sare key, value entries remove ho jayengi

```
var map = new Map();
map.set(1,100);
map.set('A', "hello");
{1:100, 'A':'hello'}
map.clear(); // {} map khali ho jayega
```

### Iteration of Map:

1. Using for of loop :

```
var map = new Map();
map.set(1,100);
map.set('A', "hello");

for(var value of map) {
    console.log(value); // [1, 100] ['A', 'Hello']
}
```

Yadi hum map ko for of loop se iterate krte hain to value me hume
ek array milta hai vah us array me 2 values hoti hai. 0 index pr key
hoti hai vah 1 index pr value hoti hai. Yadi hume key aur value ko separate use krna hai to array me se index ki madad se use krna hoga

- for example:

```
for(var value of map) {
    console.log(value[0]); //key
    console.log(value[1]); //value
}
```

2. forEach function

```
var map = new Map();
map.set(1,100);
map.set('A', "hello");
map.forEach(function(value, key) {
    console.log(value, key);
});
```

Yadi hume map ko foreach function se iterate krna hai to hume foreach function ko ek function expression pass krni hoti hai vah us function me 2 argument lene hote hai. first argument me value pass hogi vah 2nd arugment me key pass hogi

### Map to Array:

Map to array krne ke lie hum ... 3 dots ki madad se kr skte hain
3 dots ko spread operator bolte hain.

```
var map = new Map();
map.set(1,100);
map.set('A', "hello");
var arr  = [...map]; //Map to Array
```

### Array to Map:

Yadi hume array to map me convert krna hai to ek bda array bnana hoga vah us bde array me hume chote chote arrays bnane honge. har array me 2 elements honge. 1st index pr key hogi vah 2nd index pr value hogi.first is array ko Map me pass krna hota hai

```
var map = new Map([
    [1, 100],
    ['A', 'Hello']
]); //Array to Map
```

### Object to map:

Yadi hume Object se map me convert krna hai to hum Object.entries function ki madad se kr skte hain.

```
var obj  = {
    name : "learnjavascript",
    age : 21
}

var map = new Map(Object.entries(obj));
```

### Array as key:

Yadi hum map me array as a key use kr rhe hain to hume us array ka reference rkhna hota hai otherwise hum us array pr jo value hai use get ni kr skte hain. JavaScript me Array ke object hota hai islie Array ka reference rkhna jruri hai.

- For example:

```
var map = new Map();
map.set([1, 2, 3], 10000);
console.log(map);
console.log(map.get([1, 2, 3])); //undefined
```

Yeh work ni krega kuki dono array ek alag alag object hain. Iska matlab yeh hai ki dono ek jaise dhik rhe hain lekin fir b internally Javascript inko alag alag man rha hai. Yadi hume ise work krvana hai to hume array ko ek variable m dalke rkhna hoga. aur bad me value get krte time same variable use krna hoga

- For example:

```
var map = new Map();
var arr = [1, 2, 3];
map.set(arr, 10000);
console.log(map);
console.log(map.get(arr)); //10000
```
### destructuring and destructuring Arrays

Destructuring refers to a technique in which we can extract values from arrays or objects and assign them to variables in a more concise manner.

To destructure an array, we use square brackets [] and assign each variable name to the corresponding value at the same position in the array.

For example:

```
const arr = [1, 2, 3];
const [a, b, c] = arr;
console.log(a); // output: 1
console.log(b); // output: 2
console.log(c); // output: 3
```

In the above example, we first declared an array called `arr` with three values. Then, we used destructuring to assign the first value of the array to the variable `a`, the second value to variable `b`, and the third value to variable `c`. When we log each variable, we get the corresponding value from the array.

Destructuring ka matlab hota hai ki hum ek array ke values ko variables mein assign kar sakte hain ek concise tareeke se. Iske liye hum square brackets [] ka istemaal karte hain aur har variable ka naam uss value se assign karte hain jo array mein uski position ke corresponding hai.

example ke liye:

```
const arr = [1, 2, 3];
const [a, b, c] = arr;
console.log(a); // output: 1
console.log(b); // output: 2
console.log(c); // output: 3
```

Upar ke example mein, humne pehle ek array `arr` declare kiya jismein teen values hain. Fir humne destructuring ka istemaal karke pehli value ko variable `a`, dusri value ko variable `b`, aur teesri value ko variable `c` mein assign kiya. Jab hum har variable ka output log karte hain, toh humein corresponding array ke value mil jaata hai.

### reverse values using destructuring

Destructuring in JavaScript is a way to extract values from objects and arrays into separate variables. To reverse values using destructuring in JavaScript, you can use the array destructuring syntax along with the `reverse()` method.

Here's an example code snippet that demonstrates how to reverse values using destructuring in JavaScript:

```
// Original array
const numbers = [1, 2, 3, 4, 5];

// Reverse values using destructuring
let [a, b, c, d, e] = numbers.reverse();

// Output reversed values
console.log(e, d, c, b, a);
```

yadi aap kisi array ke values ko reverse karna chahte hai to aap JavaScript mein destructuring ka use kar sakte hai. Iske liye aap array destructuring syntax aur `reverse()` method ka use kar sakte hai. Jaisa ki humne upar ke example mein dekha, hum ek numbers array se shuruwat karte hai aur fir usse reverse karke alag alag variables `a`, `b`, `c`, `d`, aur `e` mein assign karte hai. Ant mein, hum reversed values ko log karke output karte hai.

### How to return two values from function

Function se do values return karne ke liye aap ek array bana sakte hai jo multiple values ko store karta hai. Isme aap ek se zyada values ko comma (,) separated brackets mein daal sakte hai.

Yaha ek example di gayi hai JavaScript language mein:

```javascript
function calculate(a, b) {
    let sum = a + b
    let diff = a - b
    return [sum, diff];
}
let result = calculate(5, 3)
console.log(result);
```

Iss code mein `calculate()` function `a` aur `b` ke sum aur difference ko calculate karke ek array mein return karta hai. Fir `result` variable mein iss array ko assign kiya jata hai aur print kiya jata hai. Output niche diya gaya hai:

```javascript
calculate(8, 2);
```

Jaise ki aap dekh sakte hai, `result` array mein dono values `sum` aur `diff` available hai. Aap inhe separate variables mein assign kar sakte hai bhi:

```javascript
let [s, d] = result;
console.log(s);
console.log(d);
```

Output:

```javascript
8
2
```

Iss tarah se aap ek se zyada values ko return kar sakte hai function se.

### Destructure a nested array

Destructuring a nested array in JavaScript means extracting values from an array that is itself nested inside another array. This can be done using the square bracket syntax ([ ]) and assigning variable names to each of the values being extracted.

Let's take an example:

```javascript
const arr = [1, 2, [3, 4]];
const [a, b, [c, d]] = arr;
console.log(a); // Output: 1
console.log(b); // Output: 2
console.log(c); // Output: 3
console.log(d); // Output: 4
```

In the above example, we have an array `arr` which contains three elements - `1`, `2`, and another array `[3, 4]`. We want to extract each value and assign it to a separate variable, so we use destructuring syntax to do so.

We declare variables `a`, `b`, `c` and `d` and assign them the values of `arr[0]`, `arr[1]`, `arr[2][0]` and `arr[2][1]` respectively.

So `a` will be assigned `1`, `b` will be assigned `2`, `c` will be assigned `3` and `d` will be assigned `4`.

imagine an array as a box containing smaller boxes inside it. The outermost box represents the main array and the smaller boxes inside it represent the nested arrays. To extract the contents of the nested boxes, we need to open each one and take out what's inside. Similarly, in JavaScript, we use destructuring to extract the values from the nested array by assigning them to separate variables.

### How to set default values in destructuring

Destructuring in JavaScript is a way to extract values from objects or arrays and assign them to variables. It allows you to write less code and make it more readable.

To set default values in destructuring, you can use the "default value" syntax. This syntax allows you to specify a default value for a variable if the value extracted from the object or array is undefined.

Here's an example:

```
// Object Destructuring with Default Values
const { name = 'Anonymous', age = 18 } = { name: 'John' };
console.log(name); // Output: John
console.log(age); // Output: 18

// Array Destructuring with Default Values
const [fruit = 'apple', vegetable = 'carrot'] = ['banana'];
console.log(fruit); // Output: banana
console.log(vegetable); // Output: carrot
```

In the above example, we are using object and array destructuring with default values. In object destructuring, we are extracting the values of "name" and "age" from an object. If "name" is not defined in the object, then the default value "Anonymous" will be used. Similarly, if "age" is not defined, then the default value "18" will be used.

In array destructuring, we are extracting the values of "fruit" and "vegetable" from an array. If "fruit" is not defined in the array, then the default value "apple" will be used. Similarly, if "vegetable" is not defined, then the default value "carrot" will be used.

Hope that helps!

### destructuring Objects

Destructuring objects in JavaScript is a way to extract individual properties or values from an object and assign them to variables in a more concise manner. It allows you to destructure (or break apart) an object into smaller pieces, which can be useful when you need to work with only certain parts of an object.

For example, let's say we have an object `person` with properties `name`, `age`, and `city`. We can use destructuring to extract these properties into separate variables like so:

```javascript
const person = {
  name: "John",
  age: 30,
  city: "New York",
};

const { name, age, city } = person;

console.log(name); // Output: John
console.log(age); // Output: 30
console.log(city); // Output: New York
```

In the above code, we used the curly braces `{}` to create a variable for each property we want to extract from the `person` object. The variable names correspond with the property names, and their values are assigned accordingly.

We could also rename the variables using colon `:` syntax like this:

```javascript
const { name: fullName, age: personAge, city: homeCity } = person;

console.log(fullName); // Output: John
console.log(personAge); // Output: 30
console.log(homeCity); // Output: New York
```

In this case, we've renamed the extracted properties to `fullName`, `personAge`, and `homeCity`.

Destructuring can also be used to extract nested properties. For example:

```javascript
const user = {
  id: 1,
  name: "Joe",
  address: {
    street: "123 Main St",
    city: "Anytown",
    state: "CA",
    zip: "12345",
  },
};

const {
  name,
  address: { city },
} = user;

console.log(name); // Output: Joe
console.log(city); // Output: Anytown
```

In this example, we've extracted the `name` property and the `city` property from the nested `address` object.

Overall, destructuring objects is a useful feature in JavaScript that can simplify your code by allowing you to extract properties from an object in a more concise way.

### How to extract any value from object using destructring

Destructuring in JavaScript is a way to extract values from objects or arrays and assign them to variables. To extract a value from an object, you can use the following syntax:

```
const { key } = object;
```

Here, `key` is the property you want to extract and `object` is the object that contains the property.

For example, suppose you have an object `person` like this:

```javascript
const person = {
  name: "John",
  age: 30,
  address: {
    street: "123 Main St",
    city: "New York",
    state: "NY",
    zip: "10001",
  },
};
```

To extract the `name` property of the `person` object, you can use destructuring like this:

```javascript
const { name } = person;
console.log(name); // Output: John
```

You can also extract nested properties using destructuring. For example, to extract the `city` property of the `address` object inside the `person` object, you can do this:

```javascript
const {
  address: { city },
} = person;
console.log(city); // Output: New York
```

In this case, the `{ address: { city } }` syntax is used to extract the `city` property from the `address` object inside the `person` object.

Destructuring is a powerful feature in JavaScript that allows you to write more concise and readable code. By extracting values from objects and assigning them to variables, you can avoid cluttering your code with long object references and make it easier to work with complex data structures.

### How to rename Object property name in destrcutring

Destructuring allows you to extract values from an object and assign them to variables. In JavaScript, if you want to rename a property while destructuring, you can use the colon ':' syntax.

Example:
Suppose we have an object `person` with properties `name`, `age`, and `gender`. We want to rename the property `gender` to `sex` while destructuring the object.

```
const person = {
  name: "John",
  age: 30,
  gender: "male"
};

// destructuring with property renaming
const { name, age, gender: sex } = person;

console.log(name); // output: John
console.log(age); // output: 30
console.log(sex); // output: male
```

In the above example, we used the colon ':' syntax to rename the `gender` property as `sex`. Now, `sex` variable will contain the value of `gender` property from `person` object.

Hinglish Explanation:

Destructuring se hum object ke properties ko variables mein assign kar sakte hai. Agar aap property ka naam change karna chahte hai to aap colon ':' syntax ka use kar sakte hai. Iske liye hum ek example lete hai - Suppose humare paas `person` naam ka object hai jisme `name`, `age` aur `gender` properties hai. Hum chahte hai ki `gender` property ka naam `sex` ho jaaye jab hum object ko destructuring karte hai. Aise karne ke liye, hum colon ':' syntax ka use karenge.

example:

```
const person = {
  name: "John",
  age: 30,
  gender: "male"
};

// destructuring with property renaming
const { name, age, gender: sex } = person;

console.log(name); // output: John
console.log(age); // output: 30
console.log(sex); // output: male
```

Upar diye gaye example mein humne colon ':' syntax ka use karke `gender` property ka naam `sex` kar diya hai. Ab `sex` variable `person` object ki `gender` property ke value ko store karega.

### Setting Default values in destructuring in javascript

Destructuring is a feature introduced in ES6 (ECMAScript 2015) that allows developers to extract data from arrays, objects and assign them to variables in a concise syntax. Default values in destructuring allow you to provide a fallback value in case the extracted value is undefined or null. Let's understand this with an example:

```javascript
// Without default values
const person = { name: "John", age: 30 };
const { name, occupation } = person;

console.log(name); // "John"
console.log(occupation); // undefined

// With default values
const person = { name: "John", age: 30 };
const { name, occupation = "unemployed" } = person;

console.log(name); // "John"
console.log(occupation); // "unemployed"
```

In the above example, we are destructuring the `person` object and extracting the `name` and `occupation` properties. Since the `occupation` property does not exist in the `person` object, its value is assigned `undefined`. In the second example, we have provided a default value for the `occupation` property as `"unemployed"`, which will be used in case the extracted value is `undefined`.

The syntax for providing default values in destructuring is to use the `=` operator followed by the desired default value, as shown below:

```javascript
const { variableName = defaultValue } = objectName;
```

we can say that setting default values in destructuring allows us to provide a backup value if the extracted value from an object or array is not present, similar to how we keep a backup plan in case our original plan fails.

### Destructuring of Nested Object

Destructuring of nested objects in JavaScript means extracting values from an object and assigning them to variables in a more concise way. This technique can be used to access deeply nested properties of an object.

For example, let's say we have an object `person` with nested properties like this:

```
const person = {
  name: "John",
  age: 30,
  address: {
    city: "New York",
    state: "NY",
    zip: "10001"
  }
};
```

If we want to extract the values of `city`, `state`, and `zip` properties of `address` object, we can use destructuring like this:

```
const { name, age, address: { city, state, zip } } = person;
```

This will create new variables `name`, `age`, `city`, `state`, and `zip`, and assign the corresponding values from the `person` object.

Here's what each part of the destructuring syntax means:

- `{ name, age, address: { city, state, zip } }` is the pattern that specifies which properties we want to extract from the `person` object.
- `name` and `age` are simple properties that we extract directly.
- `address: { city, state, zip }` is a nested pattern that specifies that we want to extract the `city`, `state`, and `zip` properties of the `address` object.

We can then use these variables as needed:

```
console.log(name); // "John"
console.log(age); // 30
console.log(city); // "New York"
console.log(state); // "NY"
console.log(zip); // "10001"
```

Destructuring of nested objects can be a powerful tool for working with complex data structures in JavaScript.

### How to use destrcutring in Function

Destructuring का उपयोग javascript में विभिन्न तरीकों से किया जाता है, इसमें हम एक फंक्शन के पैरामीटर में डिफॉल्ट वैल्यूज और विभिन्न प्रकार की डेटा संरचनाओं (data structures) को बहुत सरल तरीके से अनपैक (unpack) करते हैं।

example

```
function printUserDetails({name, age, location}) {
   console.log(`Name: ${name}, Age: ${age}, Location: ${location}`);
}

const user = { name: 'John', age: 30, location: 'New York' };

printUserDetails(user);
```

इस उदाहरण में, हमने `printUserDetails` नामक एक फंक्शन बनाया है जो एक object के properties को डिस्ट्रक्चर इस्तेमाल करके अनपैक करता है। फंक्शन के पैरामीटर में हमने एक object जिसके properties `name`, `age`, और `location` को डिस्ट्रक्चरिंग से अलग-अलग वेरिएबल में अनपैक कर लिया है।

आखिर में, हमने `user` नामक एक object बनाया जिसमें उपयोगकर्ता का नाम, उम्र और स्थान हैं और इस object को `printUserDetails` फंक्शन में पास कर दिया है।

फंक्शन को कॉल करने पर, फंक्शन पैरामीटर में अनपैक किए गए वेरिएबल की मदद से उपयोगकर्ता की जानकारी को प्रिंट करता है।

इस तरह, डिस्ट्रक्चरिंग का उपयोग करके, हम फंक्शन पैरामीटर में विभिन्न डेटा संरचनाओं (data structures) को आसानी से अनपैक कर सकते हैं।
### The Spread Operator

The Spread Operator in JavaScript is denoted by three dots (...) and it allows an iterable object, such as an array or string, to be expanded into individual elements. This means that you can use the spread operator to pass the elements of an array as individual arguments to a function or to create a new array by combining existing arrays.

Let me explain this with an example in Hinglish:

Suppose you have an array of fruits:

```
const fruits = ['apple', 'banana', 'orange'];
```

Now let's say you want to create a new array that contains all the elements of the `fruits` array plus some additional fruits. You can use the spread operator to achieve this like so:

```
const moreFruits = [...fruits, 'grape', 'kiwi'];
console.log(moreFruits); // Output: ['apple', 'banana', 'orange', 'grape', 'kiwi']
```

Here we used the spread operator to expand the `fruits` array and then added two additional fruits (`'grape'` and `'kiwi'`) to create a new array called `moreFruits`.

Similarly, you can also use the spread operator to pass the elements of an array as individual arguments to a function like so:

```
function add(a, b, c) {
  return a + b + c;
}

const nums = [1, 2, 3];

console.log(add(...nums)); // Output: 6
```

Here we used the spread operator to pass the elements of the `nums` array (i.e., `1`, `2`, and `3`) as individual arguments to the `add` function, which then returns their sum.

So, in summary, the spread operator is a handy feature in JavaScript that allows you to easily manipulate arrays and pass their elements as individual arguments to functions.

### assign values using spread operator

Spread operator se hum ek array ya object ke values ko dusre array ya object mein assign kar sakte hain. Ye operator '...' ka use karta hai aur ye new version of JavaScript (ES6) mein aaya hai.

Ek example ke through samjhate hain:

```
let numbers = [1, 2, 3];
let moreNumbers = [4, 5, 6];

let allNumbers = [...numbers, ...moreNumbers];

console.log(allNumbers); // Output: [1, 2, 3, 4, 5, 6]
```

Is example mein humne do array banaye hain `numbers` aur `moreNumbers`. Fir humne unke values ko combine karke ek naya array `allNumbers` mein store kiya hai spread operator ka use karke.

Ek aur example dekhte hain object ke saath:

```
let person = { name: 'John', age: 30 };
let details = { country: 'USA', hobby: 'Reading' };

let completeDetails = {...person, ...details};

console.log(completeDetails);
// Output: { name: 'John', age: 30, country: 'USA', hobby: 'Reading' }
```

Is example mein humne do objects banaye hain `person` aur `details`. Fir humne unke properties ko combine karke ek naya object `completeDetails` mein store kiya hai spread operator ka use karke.

Spread operator ka istemaal array ya object ke values ko easily combine karne ke liye kiya ja sakta hai.

### How to copy Array spread operator

Array spread operator in JavaScript is used to copy an array or merge multiple arrays into a single array. To use the spread operator, we use three dots (...) followed by the name of the array.

Here's an example of how to copy an array using the spread operator:

```
const arr1 = [1, 2, 3];
const arr2 = [...arr1];

console.log(arr2); // Output: [1, 2, 3]
```

In this example, we have created an array `arr1` with three elements. We then create another array `arr2` and use the spread operator to copy the elements from `arr1` into `arr2`.

Now, `arr2` is a separate array that contains the same elements as `arr1`. If we modify `arr2`, it will not affect `arr1`. Similarly, if we modify `arr1`, it will not affect `arr2`.

To summarize, the spread operator in JavaScript is a convenient way to copy an array without modifying the original array.

Hinglish Explanation:
JavaScript mein Array spread operator ka upyog ek array ko copy karne yaad phir doosre arrays ko ek hi array mein milane ke liye kiya jaata hai. Spread operator ka upyog karne ke liye, hum teen dots (...) ka upyog karte hain aur uske baad array ke naam ka upyog karte hain.

Yahaan ek udaharan diya gaya hai ki kis tarah se spread operator ka upyog karke ek array ko copy kiya jaa sakta hai:

```
const arr1 = [1, 2, 3];
const arr2 = [...arr1];

console.log(arr2); // Output: [1, 2, 3]
```

Is udaharan mein, humne teen elements ke saath ek array `arr1` banaya hai. Phir humne doosra array `arr2` banaya aur spread operator ka upyog karke `arr1` ke elements ko `arr2` mein copy kiya hai.

Ab, `arr2` ek alag array hai jismein `arr1` ke samaan elements hain. Agar hum `arr2` ko modify karte hain, to yah `arr1` ko influence nahi karega. Isi tarah, agar hum `arr1` ko modify karte hain, to yah `arr2` ko influence nahi karega.

Saaransh mein, JavaScript mein spread operator ek saral tareeka hai ek array ko copy karne ke liye jo ki original array ko modify na kare.

### How to Join 2 Arrays using spread operator

Spread operator ka use karke JavaScript mein 2 arrays ko merge ya join karna bahut hi asaan hai. Spread operator "..." ke dwara ham Arrays, Objects aur Strings ko easily manipulate kar sakte hain.

Ab samjhein ki spread operator se 2 arrays ko join karne ke liye kaise karenge:

1. Sabse pehle, humein 2 arrays kaafi hain jo humein join karna hai.
   Example:

   ```javascript
   const firstArray = [1, 2, 3];
   const secondArray = [4, 5, 6];
   ```

2. Ab hum spread operator ka use karenge aur dono arrays ko combine karenge. Hum ise mergeArray variable mein store karenge.

   ```javascript
   const mergeArray = [...firstArray, ...secondArray];
   ```

3. Yeh ho gaya! Hamari dono arrays merge ho chuki hain aur mergeArray mein store ho chuki hai.

   ```javascript
   console.log(mergeArray); // Output: [1, 2, 3, 4, 5, 6]
   ```

Is tarah se hum spread operator ka use karke 2 arrays ko join kar sakte hain.

### How to convert String to array using spread

Hinglish mein samajhane ke liye, sabse pehle "string" ka arth hai ek text ya sentence, aur "array" ka arth hai ki kuch values ko ek list mein rakhna. Ab aap spread operator ka upyog karke ek string ko array mein convert kar sakte hain.

Iske liye, aapko pehle ek string banana padega. Maan lo ki aapka string hai "Hello World". Ab aap ise array mein badalne ke liye, niche diye gaye code ko follow karein:

```
const str = "Hello World";
const arr = [...str];
console.log(arr);
```

Upar vala code aapki string ko `arr` naam ki nayi ek list mein badal dega, jisme har ek character alag-alag element hote hain. Spread operator `...` isliye use kiya jata hai taaki string ke har ek character ko alag element ke roop mein list mein daala ja sake.

Jab aap is code ko run karenge, to console par ye output dekhne ko milega:

```
["H", "e", "l", "l", "o", " ", "W", "o", "r", "l", "d"]
```

Is tarah se aap spread operator ka upyog karke ek string ko array mein badal sakte hain.

### Passing arguments in function using spread

Spread operator in JavaScript is represented by three dots (...) followed by the array or object name. It allows you to expand an iterable (an array, string, etc.) into individual elements when calling a function or constructing an array.

Let's understand it with an example:

```
function addNumbers(num1, num2, num3) {
  return num1 + num2 + num3;
}

const numbers = [1, 2, 3];

console.log(addNumbers(...numbers));
```

In this example, we have defined a function called "addNumbers" which takes three arguments "num1", "num2", and "num3". Then, we have created an array called "numbers" containing three elements [1, 2, 3].

We can pass these three elements as arguments to the addNumbers function using spread operator: "...numbers". This will expand the array into individual elements and pass them as separate arguments to the function.

So, when we call the addNumbers function with "...numbers", it will be equivalent to calling the function like this:

```
addNumbers(1, 2, 3);
```

and it will return the sum of all three numbers, which is 6.

Hope that helps!

### Shallow copy

Shallow copy in JavaScript means creating a new object or array that shares the same references to the original object's properties. This means any changes made to the original object will also reflect in the copied object.

For example, consider the following code:

```
// Creating an original object
let originalObj = { name: "John", age: 30 };
console.log(originalObj); // Output: { name: "John", age: 30 }

// Creating a shallow copy of the original object
let copiedObj = Object.assign({}, originalObj);
console.log(copiedObj); // Output: { name: "John", age: 30 }

// Modifying the original object
originalObj.age = 31;
console.log(originalObj); // Output: { name: "John", age: 31 }
console.log(copiedObj); // Output: { name: "John", age: 30 }
```

In this example, we create an `originalObj` object with two properties (`name` and `age`). We then create a shallow copy of the `originalObj` using `Object.assign()` method, which creates a new object and copies the properties of the original object into it.

When we modify the `age` property of the `originalObj`, we can see that only the `originalObj` is changed, but the `copiedObj` remains unchanged because the copied object only contains a reference to the original object's properties.

Shallow copy ka matlab hai ki ek new object ya array ko banaya jata hai jo original object ke properties ka same reference share karta hai. Ye matlab hai ki agar original object mein koi bhi changes kiye jayein to wo copied object mein bhi reflect honge.

### Deep copy

Deep copy in JavaScript refers to creating a new object or array with a completely separate memory reference from the original one. This means that any changes made to the copied object will not affect the original object, and vice versa.

For example, suppose we have an object called `originalObj`:

```
let originalObj = {
  name: "John",
  age: 30,
  hobbies: ["reading", "music"]
};
```

Now if we make a shallow copy of this object using the spread operator:

```
let shallowCopyObj = { ...originalObj };
```

Any changes made to `shallowCopyObj` will also be reflected in `originalObj` because it only creates a new reference to the same memory location.

However, if we want to create a deep copy of `originalObj`, we can use JSON.parse() and JSON.stringify() methods as follows:

```
let deepCopyObj = JSON.parse(JSON.stringify(originalObj));
```

This creates a completely separate memory reference for the copied `deepCopyObj`, which means that any changes made to it will not affect `originalObj`.

Suppose humare paas ek object hai `originalObj` jis mein kuchh key-value pairs aur ek array hai. Ab agar hum `originalObj` ko copy karna chahte hain toh hum `shallowCopyObj` ko spread operator ka use karke create kar sakte hain. Lekin agar hum yeh ensure karna chahte hain ki copied object `originalObj` se bilkul alag memory space mein store ho, toh hum `deepCopyObj` ko JSON.parse() aur JSON.stringify() methods ka use karke create kar sakte hain. Isse, copied object mein koi bhi changes original object mein reflect nahi honge aur vice versa.
### The Rest Parameter

The Rest parameter is a feature in JavaScript that allows you to represent an indefinite number of arguments as an array. It is denoted by three dots (...) followed by the name of the array that will contain the rest of the parameters.

Here's an example:

```
function sum(...numbers) {
  let result = 0;
  for (let i = 0; i < numbers.length; i++) {
    result += numbers[i];
  }
  return result;
}

console.log(sum(1, 2, 3)); // Output: 6
console.log(sum(1, 2, 3, 4, 5)); // Output: 15
```

In this example, the `sum` function takes any number of arguments and uses the rest parameter `...numbers` to collect them into an array. The function then iterates over the array and adds up all the values before returning the result.

the Rest parameter ko hum ek feature kehte hain jo JavaScript mein hota hai aur jiski madad se ham indefinite number of arguments ko ek array ke roop mein represent kar sakte hain. Yah teen dots (…) ke dwara represent kiya jaata hai aur phir uss array ka naam diya jaata hai jismein baaki ke parameters store ho jaayenge.

### How to Assign values using rest parameter

Rest parameter ke dwara values assign kaise karte hain? Example ke saath detail mein samjhaaiye.

Rest parameter JavaScript mein ek feature hai jo ki humein allow karta hai multiple arguments ko ek variable mein store karne ke liye. Isse hum functions ko flexible bana sakte hain, jisse ki humein aane wale future changes ke liye tayaar rehna hota hai.

Iska use karne ke liye, function ke last argument ke pahle three dots (...) lagaate hain, jise rest parameter kahte hain. Yeh sabhi arguments ko ek array mein store karega.

Let's take an example:

```javascript
function sum(...numbers) {
  let result = 0;
  for (let i = 0; i < numbers.length; i++) {
    result += numbers[i];
  }
  return result;
}

console.log(sum(1, 2, 3)); // Output: 6
console.log(sum(1, 2, 3, 4, 5)); // Output: 15
```

Iss code mein, `sum()` function ke andar rest parameter `...numbers` ka use kiya gaya hai. Isse hum chahe jitne bhi arguments pass kar sake hain, aur unhe `numbers` naam ke ek array mein store kara skate hain. Fir hum `for` loop se unke sum ko calculate kar rahe hain.

Iss code se aap yeh dekh sakte hain ki humne rest parameter ka use karke function ko flexible banaya hai, jisse future mein arguments add karna bahut hi aasan ho jaayega.

### Rest element last element concept

Rest element is a feature of JavaScript that allows you to represent an indefinite number of arguments as an array. The syntax for the rest element is three dots followed by a variable name, like so: `...variableName`.

The rest element must be the last parameter in a function's parameter list, and it collects all remaining arguments passed to the function into an array assigned to the variable.

Let me give you an example in Hinglish:

```
function printNames(first, second, ...names) {
  console.log("First name: " + first);
  console.log("Second name: " + second);
  console.log("Remaining names: " + names);
}

printNames("Amitabh", "Abhishek", "Aishwarya", "Jaya", "Shweta");

// Output:
// First name: Amitabh
// Second name: Abhishek
// Remaining names: Aishwarya,Jaya,Shweta
```

In this example, we have defined a function called `printNames` which takes in two mandatory parameters (`first` and `second`) followed by the rest element `...names`. When we call the function with five arguments, the first two are assigned to `first` and `second` variables respectively, and the rest of the arguments (`"Aishwarya"`, `"Jaya"`, and `"Shweta"`) are collected into an array assigned to `names`.

Finally, the function prints out the values of all three variables using `console.log()`. As you can see, the output shows the values assigned to `first` and `second` along with the array containing the remaining arguments.

### How to Assign values using rest operator in object

Rest operator is a JavaScript feature that allows you to assign multiple values to an object or an array. Using the rest operator, you can easily assign multiple values to an object in a single line of code.

Here's an example of how you can use the rest operator to assign values to an object:

```
// Example Object
const student = {
  name: 'John Doe',
  age: 25,
  address: '123 Main Street',
  phone: '555-555-5555'
};

// Using Rest Operator to set new key-value pairs in the same object
const updatedStudent = {...student,
                         age: 26,
                         email: 'johndoe@example.com'
                       };

console.log(updatedStudent) // { name: 'John Doe', age: 26, address: '123 Main Street', phone: '555-555-5555', email: 'johndoe@example.com' }
```

In this example, we have an object `student` with four key-value pairs. We want to update the `age` and add a new key-value pair for `email`.

Using the rest operator (`...student`), we are creating a copy of the `student` object and adding any additional key-value pairs necessary. The `updatedStudent` object now has five key-value pairs, including the updated `age` and the new `email`.

Rest operator ka upyog karke aap ek hi line mein object ke kai key-value pairs ko set kar sakte hain. Iska upyog karke, aap asaani se ek object mein kai value ko assign kar sakte hain. Upar diye gaye udaharan mein hamne ek student naam ka object banaya hai jismein char key-value pairs hain. Ham usmein age ko update karna chahte hain aur ek naya key-value pair email ke liye bhi add karna chahte hain.

Rest operator ka upyog karke (`...student`), hum student object ka copy banakar kisi extra key-value pairs ko add kar rahe hain. `updatedStudent` object mein ab panch key-value pairs hain, jismein updated age aur naya email shamil hain.

### How to pass Variable arguments in function using rest parameter

Rest parameter allows you to pass an indefinite number of arguments as an array to a function. This feature is denoted by "..." before the last parameter name in a function declaration. Here's an example:

```
function sum(...numbers) {
  let total = 0;
  for (let num of numbers) {
    total += num;
  }
  return total;
}

console.log(sum(1, 2, 3)); // Output: 6
console.log(sum(1, 2, 3, 4, 5)); // Output: 15
```

In the above example, the `...numbers` parameter is the rest parameter that allows us to pass any number of arguments to the `sum` function. The passed arguments are collected into an array called `numbers`. Then, we use a loop to iterate over the array and add up all the values to get the total sum.

Rest parameters are useful when you need to work with functions that can take a variable number of arguments. It eliminates the need to specify exactly how many arguments a function should expect, making your code more flexible and concise.

Rest parameter ka use karke aap ek function mein anant sankhya mein arguments ko array ke roop mein pass kar sakte hain. Is feature ko `...` last parameter ke naam se declare kiya jata hai. Yahan ek udaharan hai:

```
function sum(...numbers) {
  let total = 0;
  for (let num of numbers) {
    total += num;
  }
  return total;
}

console.log(sum(1, 2, 3)); // Output: 6
console.log(sum(1, 2, 3, 4, 5)); // Output: 15
```

Upar diye hue udaharan mein `...numbers` parameter rest parameter hai, jo humein `sum` function mein kisi bhi sankhya ke arguments ko pass karne ki anumati deta hai. Ye passed arguments `numbers` naam ke array mein sanchit kiye jaate hain. Phir, hum ek loop ka upyog karke array par aavarti hote hain aur sabhi maan ko jodkar kul yog prapt karte hain.

Rest parameters ka upyog tab kiya jaata hai jab aap functions ke saath kaam kar rahe hote hain jismein variable number of arguments liye jaate hain. Isse function mein kitne arguments hona chahiye yah specify karne ki zaroorat nahi hoti hai, jisse aapka code flexible aur laghu ho jata hai.
### What is Short Circuiting

Short circuiting refers to the behavior of logical operators such as "AND" and "OR", where the evaluation of the second operand is skipped if the result can be determined based on the value of the first operand alone.

For example, in the expression "A OR B", if A is true, then the entire expression will be true regardless of the value of B. In this case, the evaluation of B is skipped because it is not necessary to determine the final result.

Similarly, in the expression "A AND B", if A is false, then the entire expression will be false regardless of the value of B. Again, the evaluation of B is skipped because it will not affect the final result.

short circuiting as "Chhota Circuit". It means that when there is a shortcut available to reach the final answer without evaluating all the operands, the program takes that shortcut to save time and resources.

### What is Use of || in short cicuiting ?

|| is called the OR operator in programming, and it's used for short-circuiting. Short-circuiting means that if the first operand in the expression is true, then the second operand isn't even evaluated because the result of the entire expression will be true regardless of the second operand.

For example, let's say we have an expression like this:

```
if (x > 0 || y > 0) {
    // do something
}
```

In this expression, if x is greater than 0, then the second operand (y > 0) won't even be evaluated because the entire expression will be true. This saves us from having to evaluate unnecessary code and can make our programs run faster.

ki "||" ko "OR operator" kehte hai aur ye short-circuiting ke liye use hota hai. Agar expression ke first operand mein hi true condition hai, toh dusre operand ko evaluate karne ki zaroorat nahin hai kyunki poora expression true hi hoga. Isse bahut time aur code ki bachat hoti hai.

Udahran ke liye, agar humare paas ye expression hai:

```
if (x > 0 || y > 0) {
    // kuch kaam karo
}
```

Is expression mein agar x zero se bada hai toh dusra operand (y > 0) evaluate hi nahin hoga kyunki poora expression true ho jaayega. Isse hamara program tez chalega aur unnecessary code evaluate nahin karna padega.

### How to Replace short circuit || with ternary operator

Short circuit operator || is used to check if either of two conditions is true, and if it is, the entire expression is considered true. The ternary operator, on the other hand, is a shorthand way of writing an if-else statement.

To replace short circuit || with a ternary operator, you can write your expression using the following syntax:

```
condition1 || condition2 ? value1 : value2
```

Here, `condition1` and `condition2` are the two conditions you want to check, `value1` is the result if either condition is true, and `value2` is the result if both conditions are false.

For example, let's say you have the following code using the short circuit operator:

```java
int x = 5;
if (x < 3 || x > 7) {
    System.out.println("x is not between 3 and 7");
}
```

You can replace the short circuit operator with a ternary operator like this:

```java
int x = 5;
String result = x < 3 || x > 7 ? "x is not between 3 and 7" : "x is between 3 and 7";
System.out.println(result);
```

Here, we're checking if `x` is less than 3 or greater than 7 using the short circuit operator. If either condition is true, we print "x is not between 3 and 7". Otherwise, we print "x is between 3 and 7".

Using the ternary operator, we can condense this into a single line of code by assigning the result to a variable called `result`. We then print the value of `result` using `System.out.println()`.

### Using || short cicuit with non nullish values

|| (logical OR) short circuiting is a way of evaluating a series of values and returning the first non-nullish value. In simpler terms, if the first value is truthy, it will be returned, otherwise the next value in the series will be checked until a non-nullish value is found.

For example, let's say you have 3 variables: a, b, and c. You want to check which one of these variables is not null or undefined, and use that in your code. You could write the following:

```
const result = a || b || c;
```

This code will evaluate the variables in order from left to right. If a is truthy (i.e., not null, undefined, false, 0, NaN, or an empty string), it will be returned and assigned to `result`. Otherwise, if a is falsy, it will move on to check b. If b is truthy, it will be returned and assigned to `result`. If b is also falsy, it will move on to check c. If c is truthy, it will be returned and assigned to `result`. If all three variables are falsy, `result` will be assigned the value of c (which will be falsy in this case).

Here's an example in Hinglish language:

```
// Define three variables
const naam = 'John';
const umar = 25;
const gaon = '';

// Use || to find the first truthy value
const kuchNaamSunao = naam || umar || gaon;

// Output the result
console.log(kuchNaamSunao); // Output: John
```

In this example, the variable `naam` is truthy because it has a non-empty string value. So when we use the `||` operator to evaluate the three variables, `naam` is returned and assigned to `kuchNaamSunao`.

### How to Use of && short circuit ?

&& is a logical operator in many programming languages, including C++, Java, and JavaScript. It is also known as the "AND" operator.

The && operator works by evaluating two expressions and returning true only if both expressions are true. However, if the first expression is false, then there is no need to evaluate the second expression because the overall result will always be false. This behavior is called short-circuiting.

Here's an example:

Let's say you have two variables, x and y, and you want to make sure that both of them are positive before proceeding with a calculation. You could use the && operator to check this condition:

```
if (x > 0 && y > 0) {
    // Do the calculation
    ...
}
else {
    // Display an error message
    ...
}
```

In this code, if x is not greater than 0 (i.e., it is negative or zero), then the second expression (y > 0) will not be evaluated because the overall result will always be false. This saves unnecessary computation time and can help optimize your code.

Short-circuiting can also be useful for avoiding errors. For example, let's say you want to access a property of an object, but you're not sure if the object exists. You could use the && operator to check both conditions:

```
if (myObject && myObject.property) {
    // Access the property
    ...
}
else {
    // Handle the error
    ...
}
```

In this code, if myObject does not exist (i.e., it is null or undefined), then the second expression (myObject.property) will not be evaluated because it would cause an error. By using the && operator, you can avoid this error and handle it more gracefully.

I hope this explanation helps!

### How to call a function using && in short circuit

AND operator (&&) uses short circuit evaluation in JavaScript, which means that if the left operand is false, then the right operand won't be evaluated at all.

For example, consider the following code:

```
let x = 5;

if (x > 3 && x < 10) {
  console.log("x is greater than 3 and less than 10");
}
```

In this code, the `if` statement checks if `x` is greater than 3 AND less than 10 using the && operator. Since the left operand `x > 3` is true, the right operand `x < 10` is also evaluated. Therefore, the message "x is greater than 3 and less than 10" will be printed to the console.

Now, let's change the value of `x` to 2 and see what happens:

```
let x = 2;

if (x > 3 && x < 10) {
  console.log("x is greater than 3 and less than 10");
}
```

In this case, the left operand `x > 3` is false, so the right operand `x < 10` is not evaluated at all. Therefore, nothing is printed to the console.

This short circuit behavior can be used to call a function conditionally. For example,

```
function showMessage() {
  console.log("Hello world!");
}

let shouldShowMessage = true;

shouldShowMessage && showMessage();
```

In this code, the `&&` operator checks if `shouldShowMessage` is true. Since it is true, the right operand `showMessage()` is also evaluated, and the function is called, printing "Hello world!" to the console. If `shouldShowMessage` were false, the function would not be called at all.

### What is The Nullish Coalescing Operator

`Nullish Coalescing Operator` is a JavaScript feature that helps to check if a value is null or undefined, and provides a fallback value in such cases.

In simpler terms, it allows you to check for the existence of a value and use a default value if it does not exist or is null/undefined.

The syntax for `Nullish Coalescing Operator` is `??`.

Here’s an example:

```
const name = null;
const defaultName = 'Guest';

const greeting = 'Hello ' + (name ?? defaultName);

console.log(greeting);
// Output: Hello Guest
```

In this example, we have a variable called `name` which is set to `null`. We also have a variable called `defaultName` which is set to `'Guest'`.

We then use the `Nullish Coalescing Operator` to check if the value of `name` exists. Since `name` is `null`, it does not exist, so the operator returns the value of `defaultName` instead.

Finally, we concatenate the result of the `Nullish Coalescing Operator` with the string `'Hello '`, resulting in the string `'Hello Guest'`.

`Nullish Coalescing Operator` ek JavaScript feature hai jo ki ek value ko check karne ke liye use hota hai ki wo null ya undefined hai ya nahi, aur agar wo null ya undefined hai to uske jagah hum koi dusri value ka use kar sakte hai. Isko istemaal karke hum kisi value ke existence ko check kar sakte hai aur agar wo null/undefined hoti hai to hum uski jagah koi default value ka use kar sakte hai. Iska syntax `??` hai.

### What is Logical Assignment Operators ||= &&= ??=

Logical assignment operators (||=, &&=, and ??=) are compound operators that combine logical operators with assignment operators in a single operation.

The ||= operator is known as the "OR" logical assignment operator. It assigns a value to a variable only if it is currently falsy (e.g., null, undefined, false, 0, or ''). If the variable already has a truthy value, it will not be reassigned.

For example:

```
let x = null;
x ||= 'hello';
console.log(x); // Output: 'hello'

let y = 'world';
y ||= 'hello';
console.log(y); // Output: 'world'
```

In the first example, x starts off as null, which is falsy. The `x ||= 'hello'` expression checks if x is falsy, which it is, so it assigns the value 'hello' to x. In the second example, y already has a truthy value ('world'), so `y ||= 'hello'` does nothing.

The &&= operator is known as the "AND" logical assignment operator. It assigns a value to a variable only if it is currently truthy. If the variable already has a falsy value, it will not be reassigned.

For example:

```
let x = 'hello';
x &&= 'world';
console.log(x); // Output: 'world'

let y = null;
y &&= 'hello';
console.log(y); // Output: null
```

In the first example, x starts off as 'hello', which is truthy. The `x &&= 'world'` expression checks if x is truthy, which it is, so it assigns the value 'world' to x. In the second example, y starts off as null, which is falsy, so `y &&= 'hello'` does nothing.

The ??= operator is known as the "nullish coalescing" logical assignment operator. It assigns a value to a variable only if it is currently null or undefined.

For example:

```
let x = null;
x ??= 'hello';
console.log(x); // Output: 'hello'

let y = 'world';
y ??= 'hello';
console.log(y); // Output: 'world'
```

In the first example, x starts off as null, which is nullish (i.e., null or undefined). The `x ??= 'hello'` expression checks if x is nullish, which it is, so it assigns the value 'hello' to x. In the second example, y already has a truthy value ('world'), so `y ??= 'hello'` does nothing.

Logical assignment operators (||=, &&=, and ??=) ek compound operator hai jo logical operators ko assignment operators ke saath combine karta hai aur ek hi operation mein use karta hai.

||= operator ko "OR" logical assignment operator kaha jata hai. Yah ek variable mai sirf tabhi value assign karta hai jab woh currently falsy hai (e.g., null, undefined, false, 0, ya ''). Agar variable mein pehle se hi truthy value hai to ise reassign nahi kiya jaega.

&&= operator ko "AND" logical assignment operator kaha jata hai. Yah ek variable mai sirf tabhi value assign karta hai jab woh currently truthy hai. Agar variable mein pehle se hi falsy value hai to ise reassign nahi kiya jaega.

??= operator ko "nullish coalescing" logical assignment operator kaha jata hai. Yah ek variable mai sirf tabhi value assign karta hai jab woh currently null ya undefined hai.

For example:

||= operator ke liye:

```
let x = null;
x ||= 'hello';
console.log(x); // Output: 'hello'

let y = 'world';
y ||= 'hello';
console.log(y); // Output: 'world'
```

&&= operator ke liye:

```
let x = 'hello';
x &&= 'world';
console.log(x); // Output: 'world'

let y = null;
y &&= 'hello';
console.log(y); // Output: null
```

??= operator ke liye:

```
let x = null;
x ??= 'hello';
console.log(x); // Output: 'hello'

let y = 'world';
y ??= 'hello';
console.log(y); // Output: 'world'
```
### What is the Enhanced Object literals

Enhanced Object literals is a feature in JavaScript that allows developers to create objects with more concise and expressive syntax.

Basically, instead of writing properties and methods of an object one by one, you can just write them directly inside curly braces {} while creating the object.

For example:

```
const name = 'John';
const age = 30;

// without Enhanced Object literals
const person = {
  name: name,
  age: age,
  greet: function() {
    console.log('Hello!');
  }
};

// with Enhanced Object literals
const person = {
  name,
  age,
  greet() {
    console.log('Hello!');
  }
};
```

In the above example, we have created an object `person` with two properties - `name` and `age` - and a method called `greet`.

In the first version, we had to write the property names and values separately using the colon (:), and the method was defined using the keyword `function`. In the second version, we could use the shorthand syntax of just writing the variable names for the properties and define the method using arrow function syntax.

Overall, Enhanced Object literals can make your code more concise and easier to read, especially when dealing with complex objects.

### What is Enhanced Object literals Function in object

Enhanced Object literals is a feature in JavaScript that allows developers to create and manipulate objects in a more concise and flexible way.

Let me explain with an example in Hinglish language:

Suppose you want to create an object to represent a person's information, traditionally you would write something like this:

```javascript
var person = {
  name: "John",
  age: 30,
  gender: "male",
  occupation: "engineer",
};
```

With Enhanced Object literals, you can do the same thing in a more concise way by writing:

```javascript
var name = "John";
var age = 30;
var gender = "male";
var occupation = "engineer";

var person = {
  name,
  age,
  gender,
  occupation,
  greet() {
    console.log(
      `Hello, my name is ${this.name} and I am a ${this.gender} ${this.occupation}.`
    );
  },
};
```

Notice how we can use the variable names directly as property names in the object, without having to repeat them. We can also define methods within the object using the same syntax.

Enhanced Object literals also allow us to compute property names dynamically, like this:

```javascript
var propName = "email";

var person = {
  name: "John",
  age: 30,
  [propName]: "john@example.com",
};
```

In this example, the `propName` variable is used to compute the property name for the email address. The resulting object will have a property called `email`.

Overall, Enhanced Object literals provide a more concise and readable syntax for creating and manipulating objects in JavaScript.

### Enhanced Object literals compute property name

"Enhanced object literals" ki madad se hum object ke properties ko define aur initialize karne mein zyada flexibility paate hain. Ismein ek behetar tarika hai "computed property names", jiske through hum dynamic property names create kar sakte hain.

Computed property name ka matlab hai ki object ke property ke naam ko runtime mein calculate karke define kiya ja sakta hai. Iske liye hum square brackets [] ka use karte hain. Yeh feature JavaScript mein ES6 version mein introduce kiya gaya tha.

Jaise ki maan lijiye aapko ek program likhna hai jismein users ki information store karni hai. Har user ke pass unique ID hai, aur aap unki information ko us ID ke hisaab se access karna chahte hain. Tab aap computed property names ka use kar sakte hain.

Chaliye is concept ko ek udaharan se samjhe:

```
// without computed property name
let userId = 123;
let user = {
  id: userId,
  name: 'John',
  email: 'john@example.com'
};

// with computed property name
let users = {
  [userId]: {
    name: 'John',
    email: 'john@example.com'
  }
};
```

Yahan pe, humne pahle `userId` variable mein `123` assign kiya hai. Fir hum ek object `user` ko define kiya hai, jismein humne `id`, `name` aur `email` properties set ki hain. Lekin agar hum multiple users ki information store karna chahte hain, tab `user` object ko dubara dubara define karna hoga multiple baar, jiski wajah se code ki length badh jayegi.

Iske liye, hum `users` object mein computed property name ka use kar sakte hain. Yahan pe `[userId]` square brackets ke andar humne `userId` variable ko include kiya hai. Isse hum runtime mein `userId` ki value (`123`) ke hisaab se property name create kar sakte hain.

Overall, enhanced object literals aur computed property names ki madad se hum JavaScript mein objects ko define aur initialize karte samay zyada flexibility paate hain. Yeh feature code ko concise aur maintainable banane mein bhi help karta hai.
### Optional Chaining

Optional Chaining, also known as Optional Property Access, is a feature in JavaScript that allows you to access properties of an object without causing an error if the property doesn't exist. It uses the question mark (?) operator to check if the property exists before accessing it.

For example, let's say you have an object called `person`, which has a property called `address`. If you want to access the `street` property of the `address` object, you would normally do:

```
const street = person.address.street;
```

However, if the `address` property doesn't exist on the `person` object, this will result in an error. With optional chaining, you can write the same code like this:

```
const street = person?.address?.street;
```

The `?.` operator checks if the `address` property exists before attempting to access the `street` property. If `address` doesn't exist, `street` will be set to `undefined`.

Here's another example. Let's say you have an array of objects called `users`, and each user object has a `profile` property which may or may not exist. You want to loop through the array and print out the `username` property of each user's profile, but only if the `profile` property exists. You can do this with optional chaining like so:

```
users.forEach((user) => {
  const username = user?.profile?.username;
  if (username) {
    console.log(username);
  }
});
```

Optional Chaining ek aise feature hai jo JavaScript mein upyog hota hai aur jo apko object ke properties ko access karne deta hai bina kisi error ke agar wo property exist nahi karti hai. Ye feature question mark (?) operator ka use karta hai jisse ki wo check kar sake ki property exist karta hai ya nahi before accessing it. Ye code likhne mein aasani paida karta hai aur errors se bachata hai.

### Multiple condition in if condition using optional chaining

Multiple condition in if condition using optional chaining in javascript allows you to check if multiple nested properties or methods exist before accessing them, without causing an error if any of them are undefined or null.

Here's an example:

```javascript
if (obj?.prop1?.prop2?.method()) {
  // do something
}
```

In this example, `obj` is an object that may or may not have a property `prop1`, which in turn may or may not have a property `prop2`, which may or may not have a method called `method()`. Using the optional chaining operator (`?.`) between each property and method ensures that the code will not throw an error if any of these properties or methods are undefined or null.

If all the properties and method exist, the condition will evaluate to true and the code inside the block `{}` will execute.

In simpler terms, this code checks if `obj` has `prop1` which has `prop2` which has a method called `method()`, and if all of these things exist, then it will execute the code inside the if block.

Note that the optional chaining operator (`?.`) is supported in modern browsers and environments, but not in older versions of JavaScript or in some legacy environments.

### How to check if method exist in javascript using optional chaining

Optional chaining is a powerful feature introduced in ES2020 that allows you to safely access properties and methods of an object without worrying about it being null or undefined. To check if a method exists in JavaScript using optional chaining, you can use the following syntax:

```
object?.methodName()
```

Here, the `object` represents the object on which you want to call the method, and `methodName` is the name of the method you want to call. The `?.` before the method name checks if the object exists before trying to call the method. If the object is null or undefined, the code will not throw an error and the method will not be called.

Let's take an example to understand this better. Suppose you have an object `person` with a property `name` and a method `sayHello()`:

```
const person = {
  name: "John",
  sayHello() {
    console.log(`Hello, my name is ${this.name}`);
  }
};
```

Now, let's say you want to call the `sayHello()` method on the `person` object, but you're not sure if the `person` object exists. You can use optional chaining like this:

```
person?.sayHello();
```

This code will first check if the `person` object exists, and if it does, it will call the `sayHello()` method on it.

But what if the `person` object is null or undefined? In that case, the code will simply do nothing and not throw an error.

```
const person = null;
person?.sayHello(); // This code will do nothing
```

So, to summarize, to check if a method exists in JavaScript using optional chaining, you can use the `object?.methodName()` syntax. This will safely call the method if the object exists, and do nothing if it does not.

### How to check if array is empty or not using optional chaining

Optional chaining in JavaScript is a handy feature that allows you to check if a property or method exists on an object without causing an error if the object is null or undefined.

To check if an array is empty or not using optional chaining, you can use the length property with the optional chaining operator '?.'.

Here's an example:

```javascript
const arr = [];

if (arr?.length === 0) {
  console.log("Array is empty");
} else {
  console.log(`Array has ${arr?.length} element(s)`);
}
```

In the above example, we first use the optional chaining operator '?.' to check if the array exists. If it does, then we access its length property using the dot operator '.' and again use the optional chaining operator '?.' to make sure that the length property exists on the array.

If the array is empty, then its length will be 0, and we print "Array is empty." Otherwise, we print the number of elements in the array.

Optional chaining ek aisi JavaScript ki suvidha hai jisse aap ek object ke upar maujood kisi property ya method ko bina error ke check kar sakte hain agar woh null ya undefined hai.

Ek array khali hai ya nahi check karne ke liye, aap optional chaining ka upayog karke uski length property ka istemaal kar sakte hain. `?.` operater ka use karke aap dekh sakte hain ki array hai ya nahi.

example

```javascript
const arr = [];

if (arr?.length === 0) {
  console.log("Array khali hai");
} else {
  console.log(`Array mein ${arr?.length} element(s) hain`);
}
```

Upar die gye udahran mein humne pahle optional chaining operater '?.' ka upayog karke dekha hai ki kya array maujood hai ya nahi. Agar hai, toh hum uski length property tak pahunchte hain '.' operater ka istemaal karke aur phir dobara optional chaining operater '?.' ka use karke dekhate hain ki kya length property array ke upar maujood hai ya nahi.

Agar array khali hai toh uski length 0 hogi aur hum 'Array khali hai' print karenge. Varna, hum array mein kitne element hai woh print karenge.
### DOM

DOM stands for Document Object Model. It is a hierarchical tree-like structure that represents the HTML or XML document as an object in JavaScript. The DOM provides a way for JavaScript to interact with and modify the content and structure of web pages.

For example, consider the following HTML code:

```
<!DOCTYPE html>
<html>
<head>
	<title>My Page</title>
</head>
<body>
	<h1>Welcome!</h1>
	<p>This is my first webpage.</p>
	<button id="my-button">Click me!</button>
	<script src="script.js"></script>
</body>
</html>
```

In JavaScript, we can access and manipulate elements of this page using the DOM. For instance, we can add an event listener to the button element like this:

```javascript
const button = document.getElementById("my-button");
button.addEventListener("click", function () {
  alert("Hello world!");
});
```

This code uses the `document` object to locate the button element by its `id` attribute, and then adds an event listener to it. When the button is clicked, the anonymous function passed to `addEventListener` is executed, which displays an alert box with the message "Hello world!".

Overall, the DOM provides a powerful way for JavaScript to manipulate the content and structure of web pages dynamically, enabling rich user interactions and responsive web applications.

### Explain all DOM functions like write, getElementById, getElementsByClassName, getElementsByTagName, querySelector, querySelectorAll

DOM (Document Object Model) functions are used to manipulate HTML elements on a web page. Here's a brief explanation of some commonly used DOM functions:

1. write(): Allows you to write text or HTML directly onto the page, overwriting its current contents. For example:

```javascript
document.write("Hello World!");
```

This will replace the current page content with "Hello World!".

2. getElementById(): Allows you to get an HTML element by its ID attribute. For example:

```javascript
var myElement = document.getElementById("my-id");
```

This will retrieve the element with the ID "my-id".

3. getElementsByClassName(): Allows you to get a collection of HTML elements by their class name. For example:

```javascript
var myElements = document.getElementsByClassName("my-class");
```

This will retrieve all elements with the class "my-class".

4. getElementsByTagName(): Allows you to get a collection of HTML elements by their tag name. For example:

```javascript
var myElements = document.getElementsByTagName("h1");
```

This will retrieve all h1 elements in the page.

5. querySelector(): Allows you to select the first matching element using a CSS selector. For example:

```javascript
var myElement = document.querySelector("#my-id .my-class");
```

This will retrieve the first element that matches the selector "#my-id .my-class".

6. querySelectorAll(): Allows you to select all matching elements using a CSS selector. For example:

```javascript
var myElements = document.querySelectorAll(".my-class");
```

This will retrieve all elements that match the selector ".my-class".

### Explain DOM useful Properties like innerHTML, attribute, style.property,

DOM ke kuchh useful properties hain jaise ki innerHTML, attribute, style.property, aur textContent. Ye sabhi properties ek HTML element ke alag-alag parts ko manipulate karne mein madad karte hain.

1. innerHTML: Ye property ek HTML element ke andar ke HTML content ko retrieve ya set karne ke liye use hota hai. Agar aap HTML element ke andar ka content badalna chahte hain, to innerHTML property ka upyog kar sakte hain.
   Example:

```
// HTML element ko select karein
var myElem = document.querySelector("#myElement");

// innerHTML ka upyog karke content ko badle
myElem.innerHTML = "<h2>Hello world!</h2>";
```

2. Attribute: Hum HTML tags ke attributes mein se kisi bhi attribute ko access aur manipulate kar sakte hain. Isko hum DOM tree ki is tarah se refer karte hain `element.attributeName`, jahaan `attributeName` koi bhi attribute ho sakta hai jaise ki `id`, `class`, `src`, etc.
   Example:

```
// HTML element ko select karein
var myImg = document.querySelector("#myImage");

// attribute mein change karein
myImg.src = "new-image.jpg";
```

3. style.property: Ye property ek HTML element ke inline CSS styles ko access aur manipulate karne ke liye use hota hai. Inline CSS styles wo styles hote hain jo HTML tag ke "style" attribute mein define kiye jaate hain.
   Example:

```
// HTML element ko select karein
var myPara = document.querySelector("#myParagraph");

// inline CSS styles ko change karein
myPara.style.color = "red";
myPara.style.fontSize = "20px";
```

4. textContent: Ye property ek HTML element ke andar ka plain text content ko retrieve ya set karne ke liye use hota hai. Agar aap HTML element ke andar ka text content badalna chahte hain, to textContent property ka upyog kar sakte hain.
   Example:

```
// HTML element ko select karein
var myElem = document.querySelector("#myElement");

// textContent ka upyog karke content ko badle
myElem.textContent = "Hello world!";
```

Yeh sabhi properties bahut hi useful hote hain aur hum inka upyog karke dynamic web pages bana sakte hain.

### what is DOM Forms

DOM Forms are a way to collect data from users through web forms using JavaScript and the Document Object Model (DOM). When a user submits a form, the browser sends the data to the server for processing.

For example, let's say you have a login page where users enter their username and password. You can use DOM Forms to retrieve the input values and validate them before sending them to the server.

In Hinglish, DOM Forms ke dwara hum log web forms se users se data collect karte hai JavaScript aur Document Object Model (DOM) ka use karke. Jab user ek form submit karta hai, toh browser data ko server pe process karne ke liye bhejta hai.

Jaise ki, maan lo aapke paas ek login page hai jaha users apna username aur password daalte hai. Aap DOM Forms ka use karke input values ko retrieve kar sakte hai aur unhe validate karke server pe send kar sakte hai.

### Forms

Forms validation ka matlab hai ki jab bhi koi user ek form fill kar raha hai, tab us form ke andar diye gaye inputs ko sahi tarike se validate karna. Agar koi input sahi nahi hai toh user ko error message dikhai dega aur woh form submit nahi kar paayega jab tak ki sahi tarike se validate na ho jaaye.

Ek example lete hain - agar hum ek user registration form banate hain jismein user apna naam daalega, apna email address daalega, apna password daalega aur confirm password bhi daalega. Toh is form mein humko kuch validations lagaani padegi:

1. Naam mein sirf alphabets hone chahiye, agar numbers ya special characters hote hain toh error message show karein.
2. Email address valid hona chahiye (jaise: abc@xyz.com), agar invalid hai toh error message show karein.
3. Password kam se kam 8 characters ka hona chahiye aur ek uppercase letter, ek lowercase letter aur ek number hona chahiye. Agar nahi hai toh error message show karein.
4. Confirm password password se match karna chahiye, agar nahi hai toh error message show karein.

In validations ko JavaScript language mein implement kiya jaa sakta hai. Jab user form submit karta hai, tab Javascript code form inputs ko check karta hai aur agar koi validation fail hota hai toh error message display karta hai. Agar sab validations pass hote hain tabhi form submit ho jaata hai.

### Forms Properties like Disabled,Max,Min,Pattern,Required

Forms mein kuch properties hoti hai jaise ki Disabled, Max, Min, Pattern aur Required.

1. Disabled: Ye property aise cases mein use hoti hai jab humein ek field ko disable karna hota hai, yani usko user dwara edit nahi kiya ja sakta. Is property ko hum is tarah se set kar sakte hain:

   ```
   <input type="text" name="username" disabled>
   ```

   Is example mein, "username" field disabled ho gaya hai aur user usko edit nahi kar sakta.

2. Max: Ye property input fields ke liye use hoti hai jismein maximum value limit set karni hoti hai. Jaise ki:

   ```
   <input type="number" name="age" max="100">
   ```

   Is example mein, "age" field ka maximum value 100 rakha gaya hai, yani user 100 se badi value enter nahi kar sakta.

3. Min: Is property ki madad se hum input field mein minimum value limit set kar sakte hain. Jaise ki:

   ```
   <input type="number" name="marks" min="0">
   ```

   Is example mein, "marks" field ka minimum value 0 rakha gaya hai, yani user -ve value enter nahi kar sakta.

4. Pattern: Ye property input field ke liye use hoti hai jahan par humein specific pattern ke according data enter karna hota hai. Jaise ki:

   ```
   <input type="text" name="phone" pattern="[0-9]{10}">
   ```

   Is example mein, "phone" field mein sirf 10 digit numeric characters hi enter kiye ja sakte hain.

5. Required: Ye property input field ke liye use hoti hai jahan par humein ye zaroori karna hota hai ki user us field mein data enter kare. Jaise ki:

   ```
   <input type="email" name="email" required>
   ```

   Is example mein, "email" field ko required kiya gaya hai, yani user is field mein kuch na kuch zaroor enter karna hoga.

### Explain Type of Events

Aaj main aapko events ke kuch pramukh prakar ke baare mein batane ja raha hoon:

1. Cultural Events: Ye aise events hote hain jahan par kisi sanskritik activity ko promote kiya jaata hai. Jaise ki, dance night, music concert, theatre plays ya phir poetry recitals. Is tarah ke events mein desh aur sanskriti ka pratinidhitva kiya jata hai.

2. Sports Events: Ye events khel-kood se related hote hain jaise ki cricket match, football game, ya phir marathon race. In events mein athletes apne skills dikhate hain aur apne desh ke liye jeetna prayaas karte hain.

3. Corporate Events: Ye events companies aur businesses dwara organize kiye jaate hain. Inmein launch parties, product releases, award ceremonies aur annual meetings shamil hote hain. Is tarah ke events mein businesses apne brand ko promote karte hain aur employees ko reward dete hain.

4. Social Events: Ye aise events hote hain jinke mukhya uddeshya logon ko ek saath laana hota hai. Jaise ki weddings, birthdays, anniversaries aur family reunions. Inmein khushi aur pyaar ka mahaul banaaya jaata hai.

5. Educational Events: Ye events education aur learning se related hote hain. Examples include seminars, workshops, guest lectures aur conferences. Is tarah ke events mein knowledge aur information ka exchange hota hai.

Ummid hai ki ye samajhne mein aasaan hoga!

### Explain event functions like Onclick,Onchange etc

Event Functions (इवेंट फंक्शन) का उपयोग वेब पेज पर यूजर के एक्शन को ट्रैक करने के लिए किया जाता है। ये फंक्शन मौजूदा HTML या JavaScript कोड में एक्सेक्यूट होते हैं और यूजर के कुछ कार्यों, जैसे बटन क्लिक या इनपुट बदलाव, के नतीजे के रूप में चलते हैं।

ये हैं कुछ Event Functions जो हम अक्सर उपयोग करते हैं:

1. Onclick (ऑन-क्लिक): जब यूजर किसी बटन, लिंक या इमेज पर क्लिक करता है तो यह फंक्शन कॉल होता है। इसका उदाहरण निम्नलिखित है:

```
<button onclick="alert('Hello World!')">Click Me!</button>
```

इसका अर्थ है कि जब यूजर बटन पर क्लिक करता है, तो "Hello World!" अलर्ट दिखाई देगा।

2. Onchange (ऑन-चेंज): जब यूजर कुछ इनपुट (input) फील्ड को बदलता है तो यह फंक्शन कॉल होता है। इसका उदाहरण निम्नलिखित है:

```
<input type="text" onchange="alert('Text Changed!')">
```

इसका अर्थ है कि जब यूजर इस इनपुट फ़ील्ड को बदलता है, तो "Text Changed!" अलर्ट दिखाई देगा।

3. Onload (ऑन-लोड): जब वेब पेज सही ढंग से लोड होता है तो यह फंक्शन कॉल होता है। इसका उदाहरण निम्नलिखित है:

```
<body onload="alert('Page Loaded!')">
```

इसका अर्थ है कि जब वेब पेज सही ढंग से लोड होता है, तो "Page Loaded!" अलर्ट दिखाई देगा।

ये Event Functions कुछ उदाहरण हैं, जिन्हें हम HTML या JavaScript में उपयोग करते हैं।

### Explain Mouse events like Onmousedown, Onmouseup

Mouse events are actions that occur when a user interacts with a computer mouse. There are several types of mouse events, including Onmousedown and Onmouseup.

Onmousedown is an event that occurs when a user presses down on a mouse button. For example, if you click and hold down the left mouse button, an Onmousedown event will be triggered. This can be used to perform various actions, such as selecting text or dragging an object.

Onmouseup is an event that occurs when a user releases a mouse button after pressing it down. For instance, if you release the left mouse button after holding it down, an Onmouseup event will be triggered. This is often used in conjunction with Onmousedown to perform actions like drag and drop.

In Hinglish language:

Mouse events woh actions hai jo hotey hai jab koi user computer mouse se interact karta hai. Kai tarah ke mouse events hotey hai jaise Onmousedown aur Onmouseup.

Onmousedown event tab hota hai jab koi user mouse button ko press karta hai. Maan lijiye ki agar aap left mouse button ko click karke hold karte hai toh ek Onmousedown event trigger hoga. Iska use alag alag actions ke liye kiya ja sakta hai, jaise ki text select karna ya phir kisi object ko drag karna.

Onmouseup event tab hota hai jab koi user mouse button ko press karne ke baad usey release karta hai. Jaisa ki agar aap left mouse button ko hold karke rakhte hai aur uskay baad usey release karte hai toh ek Onmouseup event trigger hoga. Yah bahut baar Onmousedown ke saath istemal kiya jaata hai jaise ki drag and drop actions karne ke liye.

### Explain Event Listener with example and also explain addEventListener

Event Listener ek programming concept hai jo allows hota hai ki aap apne code me event ko detect kar saken. Event ka matlab hota hai koi action jaise button click, mouse hover ya keyboard press. Jab koi event occur hota hai to Event Listener usse detect karta hai aur uske baad specified action ko perform karta hai.

addEventListener() ek JavaScript method hai jo element ke liye ek event listener add karta hai. Ye method 3 parameters leta hai - event type, function aur optional capturing/bubbling boolean value.

Example: Agar hum ek button pe click karte hain to kuch text display hona chahiye. To iske liye humein event listener add karna hoga.

HTML Code:

```
<button id="myBtn">Click Me</button>
<p id="demo"></p>
```

JavaScript Code:

```
const btn = document.getElementById("myBtn");
btn.addEventListener("click", function() {
  document.getElementById("demo").innerHTML = "Button Clicked!";
});
```

Is code me, humne `getElementById()` method se button element ko select kiya hai. Fir `addEventListener()` method use kiya hai jisme `click` event type aur function pass kiya hai jo execute hoga jab button click hoga. Function me humne `getElementById()` method use kiya hai aur `innerHTML` property ke zariye `demo` paragraph tag ke andar "Button Clicked!" text display kiya hai.

AddEventListener() ek bohot hi important JavaScript method hai aur iske zariye aap event-based programming me proficient ho sakte hain.

### Explain Event bubbling

Event bubbling (ईवेंट बबलिंग) होता है जब कोई DOM तत्व (जैसे HTML एलीमेंट) पर कोई इवेंट हुआ तो, उस इवेंट को देखने के लिए सबसे पहले उस तत्व के सबसे निचले बच्चों में ढूंढा जाता है और फिर उसके ऊपर के तत्वों की ओर बढ़ते जाते हैं। अंत में, उस तत्व के सभी बच्चों के ऊपर से गुजरने के बाद, उसके प्रारंभिक तत्व के लिए इवेंट हैंडलर को ढूंढा जाता है।

जैसे कि, यदि हमारे पास एक HTML तालिका है जिसमें एक <td> तत्व है जिस पर क्लिक करने पर एक इवेंट हुआ, तो इसमें ईवेंट बबलिंग का उदाहरण है। जब हम <td> पर क्लिक करते हैं, तो सबसे पहले इसके सबसे निचले बच्चों में से (अगर कोई होते हैं) ढूंढा जाता है, जैसे <span>, <img> या कोई अन्य तत्व। फिर, ऊपर की तरफ बढ़ते जाते हैं और उस तालिका के अन्य तत्वों के ऊपर से भी गुजरते हैं, जैसे <tr> और <table>। इस प्रक्रिया के बाद, इवेंट हैंडलर को <td> में ढूंढा जाता है जिसने यह इवेंट हासिल किया था।

इस प्रकार, Event bubbling (ईवेंट बबलिंग) नेस्टेड HTML तत्वों में एक साधारण इवेंट हैंडलिंग मॉडल है, जो कि अनुकूलित होने में मदद करता है।

### Explain Event capturing

Event capturing, also known as event propagation, is the process by which an event that occurs on a particular HTML element is propagated or passed down to its child elements or up to its parent elements in the DOM tree.

For example, suppose we have a webpage with a div element containing a button element:

```html
<div id="myDiv">
  <button id="myButton">Click me!</button>
</div>
```

If we attach a click event listener to both the div and the button elements using JavaScript, and then click the button, the event will be triggered first on the button and then on the div, as it propagates up the DOM tree:

```javascript
const button = document.getElementById("myButton");
const div = document.getElementById("myDiv");

button.addEventListener("click", () => {
  console.log("Button clicked!");
});

div.addEventListener("click", () => {
  console.log("Div clicked!");
});
```

Event capturing yeh hota hai ki jab humare paas kisi HTML element par ek event hota hai toh wah iss element ke child elements ko bhi propagate karta hai, ya phir uske parent elements tak bhi pahunch sakta hai. Jaise ki agar humare paas ek div element hai jisme ek button element hai, aur hum JavaScript mein dono elements par click event listeners add karte hai, toh agar hum button par click karte hai toh pehle button par event trigger hoga aur phir div par, kyunki wah DOM tree ke upar propagate ho raha hai.

### Explain Navigation and parentNode,childNodes,firstChild,lastChild,nextSibling,previousSibling

Navigation की बात करें, यह एक महत्वपूर्ण प्रक्रिया है जो वेब साइट या एप्लिकेशन में उपयोग की जाती है ताकि हम एलिमेंट्स को प्राप्त कर सकें और उसके साथ कुछ अभिक्रियाएँ कर सकें।

parentNode, childNodes, firstChild, lastChild, nextSibling, previousSibling विभिन्न एलिमेंट्स के साथ नेविगेशन करने के लिए उपयोग किए जाने वाले DOM properties हैं।

parentNode property किसी एलिमेंट के parent element को दर्शाता है। यदि हम किसी एलिमेंट के parentNode property को एक वेरिएबल में स्टोर करते हैं तो हम उस parent element का उपयोग करके उस परिवर्तन को कर सकते हैं।

उदाहरण के रूप में, हम एक div element को स्थानांतरित करना चाहते हैं जो कि उसके parent element के भीतर है। हम इस दिशा में सफल होने के लिए इस div element के parentNode property का उपयोग करके उसके parent element का पता लगा सकते हैं।

childNodes property एक NodeList object को वापस देता है, जो कि एक एलिमेंट के सभी child elements को दर्शाता है। इसे उपयोग करके हम अद्यतन और delete करने के लिए किसी एलिमेंट के सभी child elements को धुंड सकते हैं।

उदाहरण के रूप में, हम एक unordered list (ul) में सभी list items (li) को delete करना चाहते हैं। हम childNodes property का उपयोग करके ul element के सभी li elements को धुंड सकते हैं और उन्हें delete कर सकते हैं।

firstChild property किसी element का पहला child element दर्शाता है। इसे उपयोग करके हम किसी element के सबसे पहले child element का पता लगा सकते हैं।

lastChild property किसी element का अंतिम child element दर्शाता है। इसे उपयोग करके हम किसी element के सबसे अंतिम child element का पता लगा सकते हैं।

nextSibling property किसी element के समान

### Explain DOM Nodes and createElement,createTextNode,appendChild

Doston, DOM Nodes ek aisa concept hai jo web development mein bahut important hota hai. DOM (Document Object Model) ek tree-like structure hoti hai jisme har ek HTML element, text, comment ya fir attribute ko ek node ke roop mein represent kiya jaata hai.

createElement, createTextNode aur appendChild ye teeno methods DOM Nodes ke creation aur manipulation mein use kiye jaate hain. createElement method se hum naye DOM element nodes create kar sakte hain. createTextNode method se hum naye text nodes create kar sakte hain. Aur appendChild method se hum kisi existing DOM element mein dusre DOM element ya fir text node ko add kar sakte hain.

Ab ek example se samjhte hain:

```
<!DOCTYPE html>
<html>
  <body>
    <div id="example"></div>

    <script>
      // Create a new DOM element
      var newElement = document.createElement("p");

      // Create a new text node
      var newText = document.createTextNode("Hello World!");

      // Append the new text node to the new element
      newElement.appendChild(newText);

      // Append the new element to an existing element
      var parentElement = document.getElementById("example");
      parentElement.appendChild(newElement);
    </script>
  </body>
</html>
```

Is example mein humne createElement method se ek naya &lt;p&gt; element banaya hai. Uske baad humne createTextNode method se "Hello World!" text ka naya node banaya hai. Phir humne appendChild method se is text node ko newly created &lt;p&gt; element ke andar daal diya hai. Finally, humne appendChild method se is new &lt;p&gt; element ko exist karne wale div ("#example") ke andar add kar diya hai.
### BOM Window object

BOM Window object in Javascript एक global object होता है जो ब्राउज़र के विंडो को represent करता है। यह ऑब्जेक्ट सभी विंडो-related methods और properties जैसे alert(), confirm() आदि को support करता है।

इस ऑब्जेक्ट में बहुत सारी मेथड और प्रॉपर्टी होती हैं। कुछ उनमें से हैं:

- alert(): यह message box show करता है जिसमें Ok button होता है।
- confirm(): यह message box show करता है जिसमें Ok और Cancel button होते हैं।
- prompt(): यह message box show करता है जिसमें user से input लेता है।
- window.open(): यह एक नयी विंडो open करता है।
- window.close(): यह current विंडो को close करता है।
- setInterval(): यह function को specific time interval में repeat करता है।
- setTimeout(): यह function को specific time interval के बाद run करता है।

एक example के रूप में, यदि हमें उपयोगकर्ता से confirm message box के माध्यम से confirmation लेनी हो तो हम निम्नलिखित code का उपयोग कर सकते हैं:

```
if (confirm("Are you sure you want to delete this item?")) {
    // delete the item
} else {
    // do nothing
}
```

इस code में, confirm() method का उपयोग message box show करने के लिए किया गया है जो user से confirmation के बारे में पूछता है। उपयोगकर्ता जब Ok button को click करता है, तब if block में वहाँ कुछ code execute होता है और जब Cancel button को click करता है तब else block में कुछ code execute होता है।

### BOM History object

Iska upyog aap kisi bhi webpage ke history se sambandhit kaam karne ke liye kar sakte hain, jaise ki pichhli webpage par jaana ya agle webpage par jaana.

Here is an example of how to use the BOM History object in JavaScript:

```
// Add a new entry to the browser history
history.pushState({page: 1}, "Page 1", "?page=1");

// Navigate back to the previous page
history.back();

// Navigate forward to the next page
history.forward();

// Replace the current entry in the history with a new one
history.replaceState({page: 2}, "Page 2", "?page=2");

// Get the number of entries in the browser history
var numOfEntries = history.length;
```

Is example mein, `pushState()` method ka upyog kiya gaya hai ek naye entry ko browser history mein add karne ke liye, `back()` method ka upyog kiya gaya hai pichhle webpage par jaane ke liye, `forward()` method ka upyog kiya gaya hai agle webpage par jaane ke liye, `replaceState()` method ka upyog kiya gaya hai current entry ko nayi entry se replace karne ke liye, aur `length` property ka upyog kiya gaya hai browser history mein maujood entries ki sankhya ko jaanne ke liye.
### Regular Expression

Regular Expressions (also known as regex or regexp) are a tool used in JavaScript to match and manipulate text patterns. They are essentially search patterns that describe a certain set of strings.

For example, you can use a regular expression to find all email addresses in a block of text, or to ensure that a password meets certain criteria (such as containing at least one uppercase letter and one number).

Here's an example of a simple regular expression in JavaScript that matches any string that contains the word "hello":

```javascript
var regex = /hello/;
```

This regex can be used with the `test()` method to see if a particular string matches:

```javascript
regex.test("hello world"); // true
regex.test("goodbye"); // false
```

Another common use of regular expressions is to replace certain parts of a string, like replacing all occurrences of a word or character with another value. This can be done using the `replace()` method:

```javascript
var str = "Hello, World!";
var regex = /Hello/;

str = str.replace(regex, "Hi");

console.log(str); // "Hi, World!"
```
### what is JSON

JSON (JavaScript Object Notation) ek format hain jiske use se data ko exchange karne ke liye web applications mein istemaal kiya jaata hai. Yeh ek lightweight format hain jo human-readable bhi hota hain aur easily parse bhi ho jaata hain.

JSON ka use JavaScript mein data transmit karne ke liye kiya jaata hain, jaise ki server se client tak ya phir client se server tak. JSON format mein data key-value pairs ke form mein hota hain. Har key ek unique identifier hoti hain aur uske saath associated value hoti hain. Key aur value dono hi double quotes ke bich mein likhe jaate hain aur colon in dono ko separate karta hain.

Example ke taur par, agar hum ek student ki information ko JSON format mein store karna chahte hain toh woh is tarah se dikhega:

```
{
  "name": "Rohan",
  "age": 21,
  "gender": "male",
  "marks": [80, 85, 90],
  "contact": {
    "email": "rohan@example.com",
    "phone": "1234567890"
  }
}
```

Is example mein, `name`, `age`, `gender`, `marks`, aur `contact` keys hain aur unke corresponding values hain. `marks` array format mein hain, aur `contact` ek object hain, jiska inner key-value pair hai.

Iss JSON data ko JavaScript mein use karne ke liye, hum `JSON.parse()` method ka use karte hain jisse isse JavaScript objects mein convert kiya ja sakta hain:

```
const studentData = '{ "name": "Rohan", "age": 21, "gender": "male", "marks": [80, 85, 90], "contact": { "email": "rohan@example.com", "phone": "1234567890" } }';

const student = JSON.parse(studentData);

console.log(student.name); // Output: Rohan
```

Iss code snippet mein, `JSON.parse()` method ka use karke hum `studentData` ko JavaScript objects mein convert karte hain. Phir hum `console.log()` se `student` object ke `name` property ko print karte hain jismein `"Rohan"` output aayega.

Yehi JSON format ko use karke data exchange karne ka basic example hain.

### XML

XML (Extensible Markup Language) is a way to store and exchange data in a structured format, using tags similar to HTML. In JavaScript, XML can be used to transfer data between different systems or applications that may not share the same programming language or database technology.

For example, let's say you have a web application that needs to get data from an external API (Application Programming Interface). The response from this API may come back in XML format, containing information about products, customers, or some other data. You can parse this XML response in JavaScript using built-in methods such as `XMLHttpRequest` or `fetch`.

Here's an example of XML data:

```xml
<bookstore>
  <book category="cooking">
    <title>Everyday Italian</title>
    <author>Giada De Laurentiis</author>
    <year>2005</year>
    <price>30.00</price>
  </book>
  <book category="children">
    <title>Harry Potter and the Philosopher's Stone</title>
    <author>J.K. Rowling</author>
    <year>1997</year>
    <price>10.99</price>
  </book>
</bookstore>
```

In this example, we have an XML document representing a bookstore, with two books in different categories, each with its own title, author, year, and price.

You can access the data in this XML document using JavaScript by first creating an instance of the `DOMParser` object, which allows you to parse the XML data into an object that you can work with:

```javascript
const xmlData = `
<bookstore>
  <book category="cooking">
    <title>Everyday Italian</title>
    <author>Giada De Laurentiis</author>
    <year>2005</year>
    <price>30.00</price>
  </book>
  <book category="children">
    <title>Harry Potter and the Philosopher's Stone</title>
    <author>J.K. Rowling</author>
    <year>1997</year>
    <price>10.99</price>
  </book>
</bookstore>
`;

const parser = new DOMParser();
const xmlDoc = parser.parseFromString(xmlData, "text/xml");
```

In this example, we first define the XML data as a string. We then create a new `DOMParser` object and use its `parseFromString` method to parse the XML data into an `XMLDocument` object called `xmlDoc`.

Once you have parsed the XML data into an `XMLDocument` object, you can access its elements and attributes using JavaScript:

```javascript
const books = xmlDoc.getElementsByTagName("book");

for (let i = 0; i < books.length; i++) {
  const book = books[i];
  const title = book.getElementsByTagName("title")[0].textContent;
  const author = book.getElementsByTagName("author")[0].textContent;
  const year = book.getElementsByTagName("year")[0].textContent;
  const price = book.getElementsByTagName("price")[0].textContent;

  console.log(`${title} by ${author}, published in ${year}, costs $${price}`);
}
```

In this example, we use the `getElementsByTagName` method to get an array of all the `book` elements in the XML document. We then loop over each `book` element and extract its `title`, `author`, `year`, and `price` elements using the `getElementsByTagName` method again. Finally, we log the information about each book to the console.
### JavaScript Engine

JavaScript Engine ek computer program hota hai jo JavaScript code ko samajhne aur execute karne ke liye banaya jata hai. Ye engine web browsers jaise Google Chrome, Firefox, Safari, etc. ke andar hota hai aur web pages par JavaScript code ko chalata hai.

JavaScript engine ka kaam hota hai ki jab browser me koi webpage load hoti hai jisme JavaScript code likha gaya ho to vo engine us code ko padhta hai aur use machine language me convert karta hai jo ki computer samajh sakte hai. Is process ko "compilation" kehte hai.

Ek example ke roop me, Google Chrome ka V8 JavaScript engine bahut popular hai. Ye engine Node.js, Electron aur nw.js jaise tools ke saath bhi istemaal kiya ja sakta hai. Ye engine JavaScript code ko optimized tarike se compile karta hai, jisse ki code ki speed improve ho aur execution time kam ho.
### what is Call Stack

Call Stack ek aisi jagah hai jahan JavaScript engine apne functions ko track karta hai. Jab bhi hum koi function call karte hai, toh wo function call stack pe add ho jaata hai. Aur jab ye function execute ho jaata hai, tab ye call stack se hata diya jaata hai.

Ek example ke through samjhaate hain. Maan lijiye aapke paas do functions hain - `greet()` aur `hello()`. Ab aap `greet()` function ko call karte hain. Toh uss samay `greet()` function Call Stack me add ho jaata hai. Phir `greet()` function me se `hello()` function ko call karte hain. Tab `hello()` function bhi Call Stack me add ho jaata hai.

Ab `hello()` function execute hota hai aur call stack se hat jaata hai. Phir `greet()` function bhi execute ho jaata hai aur woh bhi call stack se hat jaata hai. Is tarah se Call Stack ka use karke JavaScript engine apna flow control maintain karta hai.
### what is Execution Context

Execution Context in JavaScript refers to the environment where JavaScript code is executed. It consists of the scope chain, variable objects, and this keyword.

Let me give you an example in Hinglish Language: Imagine that you are a chef in a kitchen. You have your recipe (JavaScript code), but you need some ingredients (variables) and tools (functions) to execute it. The kitchen itself would be your execution context, which provides you with all the necessary resources to cook your dish.

In JavaScript, each time a function is called, a new execution context is created. This context has access to its own set of variables and functions, as well as those defined in outer scopes. This creates a hierarchy of nested execution contexts, known as the call stack.

For example, let's say we have a simple function:

```
function greet(name) {
  console.log("Hello " + name);
}
```

And we call this function:

```
greet("John");
```

When the function is called, a new execution context is created, with its own variable object and scope chain. In this case, the variable object would contain a single property, `name`, with a value of `"John"`. The scope chain would include the global scope and any outer scopes, but since there are none in this example, it's just the global scope.

The function then executes, printing `"Hello John"` to the console. Once it's finished executing, the execution context is removed from the call stack, and control returns to the previous execution context.

In conclusion, Execution Context in JavaScript is a way of organizing and managing the execution of code by providing an isolated environment for each function call. It ensures that each function can access the variables and functions it needs to execute, without interfering with other parts of the program.

### what is Variable Environment

Variable Environment जावास्क्रिप्ट में एक ऐसा माहौल है जो हमारे कोड में उपलब्ध सभी वेरिएबल्स को store करता है। यह एक object होता है जिसमें हमारे code block के लिए local variables, functions और global variables के references होते हैं। इन references की मदद से, जब हम अपने code block को execute करते हैं, तो जावास्क्रिप्ट engine उन values को lookup करता है।

इसे एक example के through explain किया जा सकता है।

```
let a = 5;

function foo() {
  let b = 10;
  console.log(a + b);
}

foo(); // Output: 15
```

जैसा कि ऊपर दिखाया गया है, `a` global variable है जो `foo()` function में reference किया जा सकता है। अब, `foo()` function का execution start होने पर उसका own variable environment create हुआ, जिसमें `b` variable की reference होती है। जब `console.log(a+b)` line execute हुई, तो जावास्क्रिप्ट engine ने `b` की value lookup करने के लिए `foo()` function के variable environment में देखा और इसके बाद `a` की value lookup करने के लिए global scope में देखा।

### what is Type of execution context ? Global and Functional

JavaScript mein execution context ka matlab hota hai ki code kaise execute hoga. JavaScript 2 type ke execution context support karta hai:

1. Global Execution Context - Yah execution context sabse pehle run hota hai aur ek hi baar run hota hai jab browser mein page load hota hai. Is execution context mein, sabhi variables, functions aur objects global scope mein define hote hai.

Example:

```
var a = 10;
function foo() {
   console.log("Hello World!");
}
console.log(a); // Output: 10
foo(); // Output: Hello World!
```

2. Functional Execution Context - Yah execution context function ke andar create hota hai aur har baar call hone par create hota hai. Is execution context mein, sabhi variables, functions aur objects function scope mein define hote hai.

Example:

```
function foo() {
   var a = 10;
   function bar() {
      console.log(a);
   }
   bar();
}

foo(); // Output: 10
```
### what is Memory/Heap

JavaScript is a programming language that is commonly used to build interactive web applications. In JavaScript, the memory is divided into two main regions: the Stack and the Heap.

The Stack is a region of memory that stores function calls and their local variables. Each time a function is called, a new frame is added to the top of the stack, and when the function returns, the frame is removed from the stack. This allows for efficient memory management and prevents memory leaks.

The Heap, on the other hand, is a larger region of memory that stores objects and their data. Objects are created in the heap, and references to those objects can be stored on the stack or in other objects. Memory management in the heap is not automatic, so it's important for developers to manually manage the creation and destruction of objects to prevent memory leaks.

Let's take an example to understand this better:
Suppose we want to create an object called "person" with properties like name, age, and address. We would create this object in the heap using the following code:

```
let person = {
  name: "John",
  age: 30,
  address: "123 Main St"
};
```

Now, if we want to access the "name" property of the person object, we can use the following code:

```
console.log(person.name);
```

This will print "John" to the console.

It's important to note that when we create an object in the heap, we need to make sure to properly manage its memory. If we no longer need the "person" object, we should remove it from memory using the `delete` keyword like this:

```
delete person;
```

This will free up the memory used by the "person" object and prevent memory leaks.

we can say that memory/heap ko Javascript me do hisso me divide kiya jata hai: Stack aur Heap. Stack me function calls aur unke local variables store hote hai, jabki Heap me objects aur unke data store hote hai. Objects ko heap me create kiya jata hai aur references unke stack ya dusre objects me store kiye ja sakte hai. Memory management heap me automatic nahi hoti hai, isliye developers ko manually object creation aur destruction manage karna padta hai memory leaks se bachne ke liye.
### what is Compiler

Compiler ek aisa software hai jo humari code (jaise ki JavaScript) ko machine-readable format (jaise ki binary code) mein badalta hai. Is process ke baad, computer asani se humari code ko samajh sakta hai aur uss par execution kar sakta hai.

Compiler ka basic kaam hota hai code ki syntax aur grammar ko check karna aur use machine-readable instructions mein convert karna. Ye process source code aur object code ke beech mein hoti hai.

Jab hum apne JavaScript code ko likhte hain, to wo human-readable hota hai aur computer ko samajhne mein mushkil hoti hai. Iss liye, humein apne code ko compiler ke through translate karna padta hai.

For example, agar hum ye JavaScript code likhte hain:

```
let x = 5;
let y = 10;
let z = x + y;
console.log(z);
```

To compiler usse machine-readable format mein convert karega, jaise ki:

```
0101010110101101...
```

Iss tarah se, humari code ki execution speed bhi fast ho jaati hai, kyunki computer ko binary code ko execute karna bahut hi asaan hota hai.

Isliye hum apne JavaScript code ko browser ya server par run karne se pehle compiler ke through translate karte hain takki computer unhe asani se samajh sakein.

### what is Interpreter

Interpreter JavaScript ka ek hissa hai jo code ko line-by-line execute karta hai. Yah ek runtime environment ke roop mein kam karta hai aur code ko interpret karta hai jab wah run kiya jata hai.

Jab aap apna JavaScript code banate hain, to Interpreter usko ek programming language se dusre programming language mein convert karta hai. Yah code ko execute karne ke liye tarika taiyar karta hai, jise browser mein execute kiya ja sakta hai.

Interpreter ek bahut hi important role nibhata hai JavaScript programming mein. Interpreter code ko debug karne mein bhi kaafi madad karta hai, kyonki wah error messages generate karta hai jab aapka code sahi nahi hota hai.

example

```
var x = 5;
var y = 10;
var z = x + y;
console.log(z);
```

Is code mein `var` keyword se tino variables define kiye gaye hain – `x`, `y`, aur `z`. Phir `z` mein `x` aur `y` ka sum store kiya gaya hai. Finally, `console.log()` function se `z` ki value console par print ki gayi hai.

Jab aap is code ko chalate hain, tab Interpreter sabse pehle `var x = 5;` line ko interpret karta hai aur `x` variable ko `5` se assign karta hai. Phir wah `var y = 10;` line ko interpret karta hai aur `y` variable ko `10` se assign karta hai. Isi tarah Interpreter `var z = x + y;` line ko bhi interpret karta hai aur `z` variable mein `15` ka sum store karta hai. Finally, `console.log(z);` line ko interpret karke `z` ki value (`15`) console par print karta hai.

Is tarah Interpreter JavaScript mein code ko interpret karta hai aur runtime environment ke andar execute karta hai.

### Difference Compiler and Interpreter

Compiler aur Interpreter dono programming languages ke liye use hote hai, lekin inka kaam aur tareeka alag hota hai. Ek Compiler program ko puri tarah se ek baar compile karta hai, jabki ek Interpreter code ko line by line read karke execute karta hai.

JavaScript me bhi Compiler aur Interpreter dono ka upyog kiya jaata hai:

Compiler: Jab hum JavaScript code likhte hai to usko sabse pahle ek Compiler ke through Compile kiya jaata hai, jisme code ki syntax check ki jati hai aur use byte code me convert kiya jaata hai. Byte code CPU ke liye samajhne me aasan hota hai. Ye Compiler time ke dauraan hi hota hai. Jaise hi hamara JavaScript code run karna hota hai, is compiled code ko directly CPU ko provide kiya jata hai.

Interpreter: Ye interpreter runtime par hota hai, matlab ki jab hamara code execution ke dauraan run karta hai tab. Ye JavaScript code ko line-by-line read karta hai aur usko machine-readable language me translate karta hai. Is process ko "Just-in-time (JIT)" compilation kehte hai.

Ek udaharan se samjhe to Compiler ka kaam ek teacher ke jaisa hota hai jo kisi student ke sare notes ko pehle se check karke unke mistakes ko sudhaar leta hai. Lekin Interpreter ka kaam ek translator ki tarah hota hai jo Foreign language me baat kar rahe vyakti ke vichaar ko dusre vyakti ko samjhane me madad karta hai.

.
### what is Event Loop

Event Loop JavaScript में एक महत्वपूर्ण concept है, जो की इसका रनटाइम environment द्वारा प्रबंधित किया जाता है।

Event Loop उन events को track करता है जो queue में आ गए हैं और उन्हें handle करता है। Event Loop एक infinite loop होता है जो की constantly running रहता है।

जब कोई event, जैसे की click event, timer event या HTTP request की response, trigger होता है तो उसे callback function में डाला जाता है। फिर Event Loop उन callbacks को execute करता है जो queue में हैं।

यदि कोई callback long-running हो तो Event Loop नॉन-ब्लॉकिंग होने की guarantee देता है।

यहां एक example है:

```javascript
console.log("Start");

setTimeout(() => {
  console.log("Timeout 1");
}, 2000);

setTimeout(() => {
  console.log("Timeout 2");
}, 1000);

console.log("End");
```

इस example में, सबसे पहले "Start" print होगा। फिर setTimeout function के callbacks को queue में डाला जाएगा। 2 seconds बाद, "Timeout 1" print होगा और 1 second बाद "Timeout 2" print होगा। अंत में, "End" print होगा।

इस example में, Event Loop ने callbacks को queue में FIFO (First-In-First-Out) order में execute किया है।
### what is Creation Phase

Creation Phase ya "Srishti Avastha" software development life cycle ka pehla charan hota hai, jahan par ham naye software ke liye design aur planing karte hai. Is avastha mein hum requirements ko gather karte hai aur unke according software ki architecture taiyaar karte hai.

Is phase mein ek project manager, business analyst, software architect aur team ke members involved hote hai. In sabhi logon ko apne roles aur responsibilities ki puri jaankari honi chahiye.

Ek udaharan se samajhte hai- Maan lo humne ek E-commerce website banane ka decision liya hai to Creation phase mein hum yeh decide karenge ki konse features hone chahiye jaise ki product listing, add-to-cart, checkout, payment gateway integration etc. Iske saath hi hum decide karenge ki kaunsa programming language aur framework use karna hai aur kaise database structure taiyar karna hai.

Creation phase mein software ka initial blueprint taiyar hota hai jiske baad ise further develop kiya jata hai.

### what is Code Phase

Code phase kya hai?

Code phase ek term hai jo GPS (Global Positioning System) mein use hoti hai. Jab GPS receiver location determine karne ke liye satellite signals ka use karta hai, toh wo ek timing code ka upyog karta hai jo satellite dwara transmit kiya gaya hai. Ye timing code, GPS signal ke saath ek saath chalta hai aur jab GPS receiver us signal ko capture karta hai, tab wo signal ke starting point se kitni doori par hai, uska pata lagata hai.

Is process mein, GPS receiver ek internal clock ka upyog karta hai jo satellite dwara transmit kiya gaya timing code ke saath syncronize hota hai. Agar in dono clocks ke beech mein koi bhi difference hai, toh receiver us time delay ko calculate karke apni position determine karta hai.

Example ke liye, imagine karo ki tum ek GPS receiver lekar jungle mein ho aur apni exact location pata karna chahte ho. Jab tum GPS receiver ko on karte ho, toh wo satellite signals ko receive karna shuru karta hai. Har signal ke saath ek timing code bhi hota hai jo GPS receiver ke andar ki clock ke saath syncronize hota hai. Is tarah se, receiver calculate kar sakta hai ki us signal ke capture hone ke baad, usmein kitni der ka time delay tha. Aise hi, receiver multiple satellites se signals capture karta rahta hai aur un signals ke time delays ko calculate karke apni accurate position find out karta hai.
### what is Prototypal inheritance and prototype chain

Prototypal Inheritance एक तरीका है जिससे JavaScript में एक Object से दूसरे Object को inherit किया जाता है।

जब आप एक Object को create करते हैं, तो उस Object के पास एक prototype link होता है, जिससे वह अन्य Objects से properties एवं methods inherit करता है। इस prototype link को Prototype Chain कहा जाता है।

जैसे कि, आप निम्नलिखित कोड का उपयोग करके Object को create कर सकते हैं।

```
// parent object
var person = {
  name: 'John Doe',
  greet: function() {
    console.log('Hello, my name is ' + this.name);
  }
};

// child object
var employee = Object.create(person);
employee.id = 123;
employee.getEmployeeDetails = function() {
  console.log('ID: ' + this.id);
  this.greet();
};

employee.getEmployeeDetails(); // ID: 123, Hello, my name is John Doe
```

इस code में, `person` Object में `name` property एवं `greet()` method होते हैं। `employee` Object में `id` property एवं `getEmployeeDetails()` method होते हैं। `employee` Object एक child object है, जो कि `person` Object से inherit किया गया है।

जब `getEmployeeDetails()` method को call किया जाता है, तो `this.greet()` line द्वारा `greet()` method भी call किया जाता है। इसके लिए, JavaScript runtime `employee` Object पर search करता है, फिर उसके prototype link के माध्यम से `person` Object पर search करता है, जहां `greet()` method मौजूद होता है। इस रूप में, `employee` Object `person` Object से properties एवं methods inherit करता है, और यह Prototype Chain के माध्यम से होता है।

### what is Prototypal inheritance on Built-in objects

Prototypal inheritance in JavaScript refers to the mechanism by which objects can inherit properties and methods from other objects, known as their prototypes. In JavaScript, every object has a prototype, which acts as a template for that object's properties and methods.

Let's take an example of a built-in object in JavaScript, the Array object. Suppose we want to create a new array that has some additional methods beyond those provided by the built-in Array object. We can do this by creating a new object that inherits from Array's prototype.

Here's an example:

```
// Define our custom object
const myArray = Object.create(Array.prototype);

// Add a custom method to our object
myArray.customMethod = function() {
  console.log('This is a custom method.');
};

// Use our custom method
myArray.customMethod(); // Output: "This is a custom method."
```

In this example, we create a new object called `myArray` using the `Object.create()` method, passing in the `Array.prototype` object as its prototype. This means that `myArray` will inherit all of the properties and methods of `Array.prototype`.

We then add a custom method to `myArray` using dot notation, just like any other object in JavaScript. Finally, we call our custom method on `myArray` and it outputs the expected message.

Overall, prototypal inheritance is a powerful feature in JavaScript that allows us to create new objects that inherit properties and methods from existing objects, making our code more efficient and easier to maintain.

### what is Difference between Inheritance and classes

Inheritance और Classes दोनों JavaScript में Object-Oriented Programming (OOP) के भिन्न पहलुओं हैं।

Classes, जैसा कि नाम से पता चलता है, एक बनावट हैं जो एक नया Object बनाने के लिए उपयोग होती है। क्लास में आमतौर पर constructor फ़ंक्शन, method और properties होते हैं। निम्नलिखित उदाहरण में, हम क्लास बनाते हैं जिसका नाम Car होता है जिसमें मॉडल, रंग और स्पीड के लिए Properties और start, stop और drive के लिए methods होते हैं।

example

```
class Car {
  constructor(model, color, speed) {
    this.model = model;
    this.color = color;
    this.speed = speed;
  }

  start() {
    console.log("Starting the car...");
  }

  stop() {
    console.log("Stopping the car...")
  }

  drive() {
    console.log(`Driving the ${this.color} ${this.model} at ${this.speed} mph`);
  }
}

const myCar = new Car("Tesla", "Red", 100);
myCar.start(); // Starting the car...
myCar.drive(); // Driving the Red Tesla at 100 mph
```

Inheritance में, एक Class को दूसरी Class से inherit किया जाता है और उसकी Properties और methods को उस class के objects में उपलब्ध कराया जाता है। जब हम एक Class को inherit करते हैं, तो नई Class parent Class की सभी Properties और methods को इंहेरिट करती है और उन्हें override भी कर सकती है। निम्नलिखित उदाहरण में, हम Car class को extend करते हुए ElectricCar class बनाते हैं। ElectricCar class में नई Property battery को add किया गया है और drive method को override किया गया है।

example

```
class ElectricCar extends Car {
  constructor(model, color, speed, battery) {
    super(model, color, speed); // Calling parent constructor
    this.battery = battery;
  }

  drive() {
    console.log(`Driving the ${this.color} ${this.model} at ${this.speed} mph using the electric motor`);
  }
}

const myElectricCar = new ElectricCar("Tesla", "Red", 100, "Lithium-ion");
myElectricCar.start(); // Starting the car...
myElectricCar.drive(); // Driving the Red Tesla at 100 mph using the electric motor
```

इस उदाहरण में, ElectricCar ने Car class को inherit किया है और उसकी Properties जैसे model, color और speed को भी inherit कर लिया है जो कि उस Class के Objects में उपलब्ध हैं। इसके अलावा, ElectricCar class में एक नई Property battery को add किया गया है और drive method को override किया ग

### How to use constructor functions ? Explain in detail with example and in Hinglish language.

Constructor functions ka upyog hum new keyword ke saath object banane ke liye karte hai. Ye ek special type ki function hoti hai jo hume class-based programming mei constructor ke taur par use ki jaati hai.

A constructor function ka naam hamesha capital letter se shuru hota hai, jisse wo aasani se distinguish ho sake. Jab hum ise call karte hai to ye ek naya object bana deta hai aur usko return kar deta hai.

example

```javascript
// Constructor function definition
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}

// Creating a new object using the constructor function
var myCar = new Car("Honda", "Civic", 2010);

// Accessing object properties
console.log(myCar.make); // Output: Honda
console.log(myCar.model); // Output: Civic
console.log(myCar.year); // Output: 2010
```

Is example me humne `Car` naam ka ek constructor function define kiya hai. Ismein humne teen parameters `make`, `model`, aur `year` liye hai. Jab hum object create karenge to hum in teeno properties ko set kar payenge.

Phir humne `new` keyword ka use kiya hai jisse ki humne ek naya object `myCar` banaya hai. Is object ke andar `Car` constructor function ke property `make`, `model`, aur `year` ki values store ho gayi hai.

Last mein humne console par `myCar` ke alag alag properties ko access kiya hai.
### this key word and it's uses in many places

I assume you are referring to the keyword "this" in JavaScript.

The keyword "this" is a reference to the current object or context. It can be used in various ways in JavaScript, depending on how it is being called.

For example, if "this" is used inside a function that is called as a method of an object, then "this" refers to the object itself. Let's say we have an object called "person" with a property called "name", and a method called "greet":

```
const person = {
  name: "John",
  greet: function() {
    console.log("Hello, my name is " + this.name);
  }
};

person.greet(); // Output: Hello, my name is John
```

In this example, when we call the "greet" method on the "person" object, "this" refers to the "person" object itself. So when we use "this.name" inside the "greet" method, it prints out the person's name.

Another common use of "this" is in event handlers, where it refers to the element that triggered the event. For example:

```
const button = document.querySelector("button");

button.addEventListener("click", function() {
  console.log("You clicked the " + this.textContent + " button.");
});
```

In this example, when we click the button, the anonymous function that we passed to "addEventListener" is executed, and "this" refers to the button element. So when we use "this.textContent" inside the function, it prints out the text content of the button.

Overall, "this" is a powerful keyword in JavaScript that allows us to reference different contexts and objects dynamically.
### what is OOP

OOP stands for "Object-Oriented Programming." In JavaScript, OOP is a programming paradigm that focuses on creating objects to represent real-world entities and then using those objects to perform actions and interact with other objects.

Let's consider an example of a car. We can create an object called "car" that has properties like "model," "make," "color," and "year," as well as methods like "start," "stop," and "drive." Here's some code to create a car object:

```javascript
class Car {
  constructor(model, make, color, year) {
    this.model = model;
    this.make = make;
    this.color = color;
    this.year = year;
  }

  start() {
    console.log("Starting the car...");
  }

  stop() {
    console.log("Stopping the car...");
  }

  drive() {
    console.log("Driving the car...");
  }
}

const myCar = new Car("Civic", "Honda", "Silver", 2022);
console.log(myCar.model); // Output: Civic
myCar.start(); // Output: Starting the car...
```

In this example, we have created a class called "Car" that has a constructor function to initialize the car object with its properties. We also defined three methods: "start," "stop," and "drive," which can be called on any car object.

We then create a new instance of the Car class called "myCar," passing in the values for its properties. We can access and modify these properties using dot notation (e.g., `myCar.model = "Accord";`). We can also call the methods on "myCar" (e.g., `myCar.start();`).

OOP provides a way to organize code into reusable and modular pieces that can be easier to maintain and understand. By encapsulating data and behavior into objects, we can create more robust and flexible programs.

### what is Constructor functions and new operator

Constructor functions aur new operator JavaScript mein object-oriented programming ke concepts hai. Constructor functions ka use objects ko create karne ke liye kiya jata hai.

Constructor functions khud ek function hote hai jo ek blueprint ki tarah work karte hai. Ye blueprint se based on objects banate hai. Ismein, ham class ki tarah property aur method define kar sakte hai.

New operator ka use constructor function ke object create karne ke liye kiya jata hai. Jab bhi hum new operator ka use karte hai, toh ek empty object create hota hai aur uske baad constructor function call karke, us object mein properties aur methods set kiye jaate hai.

Example ke liye, hum ek Person constructor function bana sakte hai:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
  this.greet = function () {
    console.log(
      "Hello, my name is " + this.name + " and I am " + this.age + " years old."
    );
  };
}
```

Yahan, humne ek Person constructor function banaya hai jismein "name" aur "age" properties hain, aur "greet" method hai jiske zariye hum person ko greet kar sakte hai.

Ab hum new operator ka use karke, is constructor function se objects create kar sakte hai:

```javascript
const person1 = new Person("John", 30);
const person2 = new Person("Jane", 25);

console.log(person1.name); // Output: John
console.log(person2.age); // Output: 25
person1.greet(); // Output: Hello, my name is John and I am 30 years old.
```

Yahan, humne `new Person` ka use karke do objects banaye hai. Ek person1 jiska naam John hai aur age 30 hai, aur dusra person2 jiska naam Jane hai aur age 25 hai. Humne `console.log` aur `person1.greet()` ke zariye inke properties aur methods ko access kiya hai.

Ummid hai yeh samjh mein aaya hoga!

### what is Prototypes

Prototypes in JavaScript refer to the mechanism through which objects inherit properties and methods from other objects.

In simpler terms, when you create an object in JavaScript, it automatically inherits certain properties and methods from another object, known as its prototype. These inherited properties and methods can be accessed and used by the new object.

For example, let's say we want to create a new object called "person". We can do so using the following code:

```javascript
var person = {
  firstName: "John",
  lastName: "Doe",
  age: 30,
  fullName: function () {
    return this.firstName + " " + this.lastName;
  },
};
```

Here, we have created an object with four properties - `firstName`, `lastName`, `age`, and `fullName`. The `fullName` property is a method that returns the full name of the person.

Now, let's create another object called "student" that inherits from the "person" object:

```javascript
var student = Object.create(person);
student.firstName = "Jane";
student.lastName = "Smith";
student.grade = "A";
```

Here, we have used the `Object.create()` method to create a new object called "student" that inherits from the "person" object. We have then added three additional properties to the "student" object - `firstName`, `lastName`, and `grade`.

Since the "student" object inherits from the "person" object, it also has access to the `fullName` method. We can call this method on the "student" object as follows:

```javascript
console.log(student.fullName()); // Output: Jane Smith
```

So, in essence, prototypes in JavaScript allow us to create objects that inherit properties and methods from other objects, making our code more efficient and reusable.

Ab sabko samajh mein aaya hoga ki Prototypes kya hote hai JavaScript mein. Yah ek mechanism hai jiski madad se hum ek naye object ko kisi dusre object se properties aur methods ko inherit karne ki suvidha pradaan karte hain. Iski madad se hum apna code efficient tarike se likh sakte hain aur use dobara upyog me la sakte hain.

### what is Prototypal inheritance and prototype chain

Prototypal Inheritance aur Prototype Chain JavaScript mein kya hai? Isko Example ke saath detail mein explain karein, Hinglish mein.

JavaScript mein Prototypal Inheritance ek bahut hi important concept hai. Har object ke paas apna prototype hota hai, jo use inheriting properties and methods allow karta hai.

Prototype chain yeh determine karta hai ki object kis tarah se inheriting properties and methods leta hai. Jab aap kisi property or method ke liye ek object par access karte hain, JavaScript sabse pehle uss object ke prototype mein search karta hai, aur agar woh usmein nahi milta toh uske prototype ka prototype mein search karta hai. Yeh process prototype chain kehte hai.

For example:

```
// Hum ek constructor function bana rahe hai
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Hum Person ke prototype mein ek method add kar rahe hai
Person.prototype.greet = function() {
  console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
};

// Ek instance create kar rahe hai
const person1 = new Person('John', 30);

// greet method call karte hai
person1.greet(); // Output: Hello, my name is John and I am 30 years old.
```

Is example mein humne ek constructor function `Person` banaya jiske prototype mein humne `greet` method add kiya. Fir humne ek instance `person1` create kiya aur uspe `greet` method call kiya. Jab `greet` method ko call kiya gaya toh JavaScript sabse pehle `person1` object ke prototype mein search kiya, aur wahaan `greet` method mil gaya.

### what is Prototypal inheritance on Built-in objects

Prototypal inheritance in JavaScript means that objects can inherit properties and methods from other objects, known as their "prototype". When a property or method is accessed on an object, JavaScript first looks for it on the object itself, and if it's not found there, it checks the object's prototype, and so on up the prototype chain until the property or method is found or there are no more prototypes to check.

For example, let's say we have an array object in JavaScript. The array object has a prototype, which is another object that contains all of the methods and properties that arrays can use. We can create a new array like this:

```javascript
let myArray = [1, 2, 3];
```

When we try to access a method or property on `myArray`, JavaScript first checks to see if it exists on `myArray` itself. If it doesn't, then it checks the array prototype for the method or property. For example, if we call the `map()` method on `myArray` like this:

```javascript
let newArray = myArray.map(function (num) {
  return num * 2;
});
```

JavaScript will first look for the `map()` method on `myArray`. Since `map()` is not a property of `myArray`, JavaScript will look for it on the array prototype. It will find `map()` there and execute it, which will return a new array with each element multiplied by 2.

Prototypal inheritance ka matlab hai ki objects kay pass kisi aur object se properties aur methods inherit kiye jaa sakte hai, jo uske "prototype" ke naam se jaante hai. Jab koi property ya method access hota hai kisi object per JavaScript mei, sabse pehle wo uss object mei dhundta hai agar wo waha nahi hai to wo uss object ke prototype ko check karta hai, is tarah se prototype chain ke through jate jate check karta hai property ya method ko.

For example: Agar hum JavaScript mei ek array object lete hai, toh uska prototype bhi hota hai jo dusre object mei methods aur properties ko store karta hai. Hum ek naya array aise create kar sakte hai:

```javascript
let myArray = [1, 2, 3];
```

Agar hum `myArray` per koi method ya property access karte hai, toh JavaScript sabse pehle check karta hai ki wo property/method `myArray` mei hai ya nahi, agar nahi hai toh wo array ke prototype mei jaata hai aur waha se search karta hai. Jaise ki agar hum `map()` method use karte hai `myArray` per:

```javascript
let newArray = myArray.map(function (num) {
  return num * 2;
});
```

Toh JavaScript sabse pehle `map()` method ko `myArray` mei dhundega, lekin waha ye method nahi hai, isliye wo array ke prototype mei jayega aur waha se `map()` method ko execute karega. Ye method ek new array return karega jismein har element ko 2 se multiply kiya hua hai.

### what is ES6 classes

ES6 classes are a feature in JavaScript that allow you to create object-oriented programming (OOP) structures in a more familiar way, similar to other programming languages like Java or Python.

In Hinglish language, ES6 classes ko hum JavaScript mein use karke OOP ki tarah programming kar sakte hai jaise Java ya Python mein hota hai.

To explain with an example, let's say you want to create a class for a Car object. In traditional JavaScript, you might use a constructor function and add properties and methods to its prototype:

```
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}

Car.prototype.getDescription = function() {
  return `This is a ${this.year} ${this.make} ${this.model}.`;
}
```

But with ES6 classes, you can define the same class in a more concise way:

```
class Car {
  constructor(make, model, year) {
    this.make = make;
    this.model = model;
    this.year = year;
  }

  getDescription() {
    return `This is a ${this.year} ${this.make} ${this.model}.`;
  }
}
```

The `class` keyword declares a new class called `Car`. The `constructor` method is automatically called when you create a new instance of the class and sets the initial values of the object's properties. The `getDescription` method defines a behavior for the Car object.

You can then create instances of the class just like in traditional JavaScript:

```
const myCar = new Car('Honda', 'Civic', 2022);
console.log(myCar.getDescription()); // "This is a 2022 Honda Civic."
```

Overall, ES6 classes provide a cleaner syntax for creating objects in JavaScript and make it easier to write and read OOP code.

### what is Setters and Getters

Setters aur Getters JavaScript mein properties ko access aur modify karne ke liye use kiye jaate hain. Setters property values ko set karte hain, jabki Getters property values ko retrieve karte hain.

Iska ek example dekhte hain:

```js
class Person {
  constructor(name) {
    this._name = name;
  }

  get name() {
    return this._name;
  }

  set name(value) {
    this._name = value;
  }
}

const person1 = new Person("John");
console.log(person1.name); // Output: John

person1.name = "Jane";
console.log(person1.name); // Output: Jane
```

Yahan `Person` class mein `name` property ko access karne aur modify karne ke liye `get` aur `set` functions ka use kiya gaya hai. `get` function `name` ki current value ko return karta hai, jabki `set` function `name` ki value ko set karta hai.

`person1` object ko create karne ke baad, humne `name` property ko `John` se `Jane` mein update kiya aur phir console par uski value ko print kiya.

Setters aur Getters JavaScript mein properties ko handle karne ke kaam aate hain. Setters property ki value ko set karte hain, jabki Getters property ki value ko retrieve karte hain. Upar diye gaye example mein, `Person` class mein `name` property ke liye `get` aur `set` functions ka use kiya gaya tha. `get` function `name` ki current value ko return karta hai, jabki `set` function `name` ki value ko set karta hai.

### what is Static methods

Static methods in JavaScript are functions that belong to a class rather than an instance of the class. These methods can be called directly on the class itself, without the need to create an instance.

Static methods JavaScript mein wo functions hote hai jo ki ek class ke andar hote hai, lekin class ke ek instance ke andar nahi hote hai. In methods ko class ke object ke bina seedhe class pe call kiya ja sakta hai.

Example:
Let's say we have a class called `Math` with a static method called `square` which calculates the square of a given number:

Humein maan lo ki humare paas ek "Math" class hai jismein "square" naam ka static method hai, jo ki diye gaye number ka square calculate karta hai:

```javascript
class Math {
  static square(num) {
    return num * num;
  }
}

console.log(Math.square(5)); // Output: 25
```

Here, we define a static method `square` inside the `Math` class using the `static` keyword. We can then call this method directly on the `Math` class without creating an instance of it.

Is example mein humne `static` keyword ka upyog karke `square` naam ka static method define kiya hai `Math` class ke andar. Fir humne iss method ko `Math` class ke object ke bina direct call kiya hai.

### how to Object.create

Object.create() JavaScript mein ek method hai jo aapko ek naya object banaane mein madad karta hai, jiske paas ek prototype ke roop mein ek existing object ka reference hota hai. Yeh method aapko inheritance-based programming ki suvidha deta hai.

Iska upyog karne ke liye, aap pehle se hi ek object ko prototype ke roop mein define karte hain aur uske baad Object.create() ko use karke naye object ko us prototype se inherit kar sakte hain.

Syntax:

```
Object.create(prototype_object, optional_properties_object);
```

Yahan `prototype_object` ek object hai jo naye object ka prototype banega. Agar aap chahte hain ki naya object mein kuch aur upalabdh vikalpon ke saath banaya jaaye to aap ise optional_properties_object ke roop mein bhi pass kar sakte hain.

Example:

```
// Ek person object ka prototype tayyar karo
const personPrototype = {
  greeting: function() {
    console.log(`Namaste, mera naam ${this.name} hai.`);
  }
};

// Ek naya person object create karo, jismein name property hai.
const person1 = Object.create(personPrototype, {
  name: { value: 'Rahul' },
});

// Output: Namaste, mera naam Rahul hai.
person1.greeting();
```

Is example mein, humne `personPrototype` object ko prototype ke roop mein tayyar kiya hai. Fir `Object.create()` method ka upyog karke humne `person1` object ko `personPrototype` se inherit karne ke liye banaya hai. Ismein `name` ek optional property hai, jo humne `{ value: 'Rahul' }` ke roop mein define kiya hai.

Jab `person1.greeting()` method call hua, toh `this.name` ka value `"Rahul"` ho gaya aur output `"Namaste, mera naam Rahul hai."` aaya.

### what is difference between Inheritance and classes

Inheritance aur classes dono JavaScript mein programming concepts hain. Inheritance ka matlab hota hai ki ek object dusre object se kuchh properties ya methods inherit karta hai. Jabki Classes bahut saare objects ko define karne ke liye use ki jaati hai.

JavaScript mein inheritance ke liye prototype concept ka use kiya jaata hai. Ek object ka prototype dusre object se inherit kar sakta hai. Prototype chaining ke dwara, ek object ke prototype se uske parent object ka prototype tak pahuncha ja sakta hai.

Classes ke liye ES6 standard ne class keyword introduce kiya hai. Ye class JavaScript mein bhi ek constructor function hi hoti hai. Class ke andar properties aur methods define kiye jaate hain, jo object banane ke liye use kiye jaate hain.

Ab dekhte hain ek example se:

```
//Inheritance Example
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.printDetails = function() {
  console.log(`Name: ${this.name}, Age: ${this.age}`);
};

function Employee(name, age, salary) {
  Person.call(this, name, age);
  this.salary = salary;
}

Employee.prototype = Object.create(Person.prototype);

Employee.prototype.printDetails = function() {
  console.log(`Name: ${this.name}, Age: ${this.age}, Salary: ${this.salary}`);
};

let emp1 = new Employee('John', 30, 50000);
emp1.printDetails(); //Output: Name: John, Age: 30, Salary: 50000

//Classes Example
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  printDetails() {
    console.log(`Name: ${this.name}, Age: ${this.age}`);
  }
}

class Employee extends Person {
  constructor(name, age, salary) {
    super(name, age);
    this.salary = salary;
  }

  printDetails() {
    console.log(`Name: ${this.name}, Age: ${this.age}, Salary: ${this.salary}`);
  }
}

let emp1 = new Employee('John', 30, 50000);
emp1.printDetails(); //Output: Name: John, Age: 30, Salary: 50000
```

Is example mein humne ek Person class banayi hai, jiske properties name aur age hain, aur ek printDetails method hai. Fir humne Employee class banai hai, jo Person class ko extend karti hai. Employee class ke andar bhi properties name aur age hain, saath hi salary property hai. Employee class ka printDetails method override kiya gaya hai, jisme name, age aur salary sabhi details print ho rahi hain.

Dono examples mein output same aa raha hai, lekin Inheritance example mein prototype chaining ki madad se inheritance kiya gaya hai, jabki Classes example mein ES6 standard ke class keyword ka use kiya gaya hai.

### how to Using constructor functions

Constructor functions are used in Javascript to create objects with predefined properties and methods. They are similar to classes in other languages.

constructor functions ko Javascript mein istemaal karne ke liye hum pehle ek function banate hain jismein hamari object ki properties aur methods define hote hain. Ismein hamari function ka naam capital letter se shuru hota hai taaki yeh ek constructor function ki tarah use ho sake.

Let's take an example of creating a person object using a constructor function:

```
function Person(name, age) {
  this.name = name;
  this.age = age;

  this.greet = function() {
    console.log("Hello, my name is " + this.name);
  }
}

var person1 = new Person("John", 25);
var person2 = new Person("Mary", 30);

console.log(person1.name); // Output: John
console.log(person2.age); // Output: 30

person1.greet(); // Output: Hello, my name is John
```

In the above example, we have created a constructor function called `Person` which takes two parameters - name and age. Inside the function, we set the `name` and `age` properties of the object using `this`. We also define a `greet` method which logs a greeting message to the console.

To create a new object using the `Person` constructor function, we use the `new` keyword followed by the name of the function and the arguments for the constructor. In this case, we create two person objects - `person1` and `person2`.

We can access the properties of the object using dot notation (`person1.name`) and call the methods on the object (`person1.greet()`).

Using constructor functions allows us to create multiple instances of an object with the same properties and methods, and also provides a way to encapsulate the logic for creating an object.

### how to Using ES6 classes

ES6 classes are a way to create objects in JavaScript using the class syntax. The class keyword provides a more familiar syntax for defining object-oriented programming (OOP) constructs such as classes and inheritance.

Here's an example of how to use ES6 classes to create a Person class:

```
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  sayHello() {
    console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
  }
}

const person1 = new Person('John', 30);
person1.sayHello(); // Output: "Hello, my name is John and I am 30 years old."
```

In this example, we've defined a `Person` class with a constructor that takes `name` and `age` parameters. We've also added a `sayHello` method that logs a message to the console.

To create a new instance of the `Person` class, we use the `new` keyword and pass in arguments for the `name` and `age` parameters. We then call the `sayHello` method on the new object.

ES6 classes also allow us to extend a class to create a subclass. Here's an example of how to use inheritance to create a `Student` class that extends the `Person` class:

```
class Student extends Person {
  constructor(name, age, grade) {
    super(name, age);
    this.grade = grade;
  }

  sayHello() {
    console.log(`Hello, my name is ${this.name}, I am ${this.age} years old, and I am in grade ${this.grade}.`);
  }
}

const student1 = new Student('Jane', 15, 10);
student1.sayHello(); // Output: "Hello, my name is Jane, I am 15 years old, and I am in grade 10."
```

In this example, we've defined a `Student` class that extends the `Person` class using the `extends` keyword. We've also added a `grade` property to the constructor and overridden the `sayHello` method to include the `grade`.

To call the `sayHello` method on the `Student` object, we create a new instance of the `Student` class and call the `sayHello` method on that object.

Overall, ES6 classes provide a cleaner and more intuitive syntax for creating objects and implementing inheritance in JavaScript.

### how to Using object.create in javascript?

`Object.create` ek JavaScript method hai jo aapko naye objects ko create karne me help karta hai. Yah method parent object ke properties and methods ko inherit karke new object banata hai.

Is method ka syntax yeh hota hai:

```
Object.create(parentObj, propertiesObject)
```

Yaha `parentObj` parameter vo object hai jisse aapki new object inheritance legi. Agar aap null denge to new object khali hoga.

`propertiesObject` parameter optional hai aur isse aap new object me additional properties or methods add kar sakte hai.

Ab example dekhte hai:

```javascript
// Parent object
const vehicle = {
  type: "vehicle",
  displayType: function () {
    console.log(`This is a ${this.type}.`);
  },
};

// Child object
const car = Object.create(vehicle, {
  type: {
    value: "car",
  },
});

car.displayType(); // Output: This is a car.
```

Yahan humne `vehicle` naam ka parent object banaya hai jisme ek `type` property hai aur `displayType` method hai.

Fir humne `Object.create()` method ka use karke `car` naam ka new object banaya hai jo `vehicle` object se inherit karega aur usme `type` property ki value "car" set ki gayi hai.

Finally, humne `displayType()` method call kiya jo `car` object ke type ko print karega.

I hope aapko samajh me aaya hoga ki `Object.create()` method kaise kaam karta hai aur iska use kaise kiya jata hai.

### expalin Encapsulation: Protected Properties and Methods

Encapsulation is a concept in object-oriented programming where the internal data and methods of an object are kept private and only accessible through public interfaces. In JavaScript, we can achieve encapsulation using the access modifiers: public, private, and protected.

Protected properties and methods are only accessible within the object itself and its subclasses. They cannot be accessed outside of the object. We can denote a property or method as protected by adding an underscore prefix to its name.

For example, let's say we have a class called `Person` with a protected property called `_name` and a protected method called `_sayHello()`:

```
class Person {
  constructor(name) {
    this._name = name;
  }

  _sayHello() {
    console.log(`Hello, my name is ${this._name}.`);
  }
}
```

In this example, `_name` and `_sayHello()` are both protected. We can create a subclass of `Person` called `Employee` that can access these protected members:

```
class Employee extends Person {
  constructor(name, title) {
    super(name);
    this._title = title;
  }

  introduce() {
    this._sayHello();
    console.log(`I'm a(n) ${this._title}.`);
  }
}
```

In this example, `Employee` is a subclass of `Person` and can access the protected `_name` property and `_sayHello()` method. The `introduce()` method uses `_sayHello()` to introduce the employee and then displays their job title.

To summarize, encapsulation is the idea of keeping internal data and methods private and only accessible through public interfaces. We can use the protected access modifier in JavaScript to make certain properties and methods only accessible within an object and its subclasses.

### explain Encapsulation: Private Class Fields and Methods

Encapsulation refers to the practice of keeping certain parts of an object or class hidden from the outside world, while exposing only a limited set of methods and properties for interaction.

In JavaScript, this can be achieved through the use of private class fields and methods. Private fields are data members that can only be accessed within the class that defines them, while private methods are functions that can only be called from within the class.

Suppose you have a class called BankAccount that represents a user's bank account. It has properties like the account holder's name, account number, and balance. You don't want anyone to be able to directly modify these properties from outside the class, as it could lead to security issues. Instead, you want to provide a limited set of methods that users can use to interact with the account, such as deposit(), withdraw(), and checkBalance().

To achieve this, you can use private class fields and methods. For example, you can define the balance property as a private field by prefixing it with a # symbol:

```
class BankAccount {
  #balance = 0;

  deposit(amount) {
    this.#balance += amount;
  }

  withdraw(amount) {
    if (amount <= this.#balance) {
      this.#balance -= amount;
    } else {
      console.log("Insufficient funds!");
    }
  }

  checkBalance() {
    console.log(`Current balance: ${this.#balance}`);
  }
}
```

In this example, the #balance field is only accessible within the BankAccount class. Users can interact with the account by calling the public methods deposit(), withdraw(), and checkBalance(), but they cannot directly access or modify the balance field.

Using encapsulation in this way helps to keep your code organized and secure. It allows you to control how users interact with your objects and prevents them from accidentally or intentionally modifying data they shouldn't have access to.

### what is Chaining methods

Chaining methods in JavaScript is a technique that allows you to call multiple methods on the same object in a single line of code. When chaining methods, each method returns the object itself, allowing you to call another method on it. This can help make your code more concise and readable.

For example, let's say we have an array of numbers and we want to filter out all the even numbers, then square each remaining number, and finally get their sum. We can achieve this using chaining methods as follows:

```
const numbers = [1, 2, 3, 4, 5];

const result = numbers
  .filter(num => num % 2 !== 0) // filter out even numbers
  .map(num => num ** 2) // square each remaining number
  .reduce((total, num) => total + num, 0); // get their sum

console.log(result); // Output: 35
```

In this example, we first call the `filter()` method on the `numbers` array to filter out all the even numbers, which returns a new array containing only the odd numbers. Then, we call the `map()` method on this filtered array to square each remaining number, which returns another new array with the squared numbers. Finally, we call the `reduce()` method on this mapped array to get their sum, which is stored in the `result` variable.
### what is Constructor function

Constructor function JavaScript mein ek special type ka function hai jo object create karne ke liye use kiya jaata hai. Isko hum class jaise consider karte hai, kyunki isse bhi hum multiple objects create kar sakte hai.

Ek Constructor function ko define karne ke liye hum function keyword ke saath ek naam specify karte hai, aur usmein properties or methods define karte hai. Saath hi, jab hum constructor function ko call karte hai toh ye ek new object create karta hai.

Example ke taur par, agar hum ek Car object create karna chahte hai, toh hum aisa kar sakte hai:

```javascript
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}

const myCar = new Car("Toyota", "Corolla", 2020);
console.log(myCar.make); // Output: Toyota
```

Is example mein, humne `Car` constructor function ko define kiya hai jismein `make`, `model`, aur `year` properties hain. Fir humne `new` keyword ka use karke ek naya Car object create kiya hai, jiska make `'Toyota'`, model `'Corolla'`, aur year `2020` hai.

hum keh sakte hai ki Constructor function ek template hai jisko hum use karke multiple objects create kar sakte hai. Ye ek blueprint ki tarah hota hai jismein hum properties and methods define karte hai jo har object ke liye same hote hai.

### what is new keyword

`new` एक JavaScript की keyword है जो object के instance को create करने के लिए use किया जाता है। जब हम `new` keyword का use करते हैं तो एक नया object create होता है जो class या constructor function से बना होता है।

इसके लिए, हमें एक constructor function बनानी होती है जो नया object create करती है। उसके बाद, हम `new` keyword का use करते हुए उस constructor function को call करते हैं। इस प्रकार, नया object create होता है और उसे variable में assign किया जाता है।

example

```javascript
// Constructor function
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Creating object using new keyword
const person1 = new Person("John", 25);
console.log(person1); // Output: {name: "John", age: 25}
```

जैसा कि ऊपर दिखाया गया है, हमने `Person` constructor function create किया जो `name` और `age` property के साथ एक object create करता है। फिर हम `new` keyword का use करते हुए `Person` constructor function को call करते हैं और नया object `person1` create करते हैं।
### How to use Object.create

Object.create() ek JavaScript function hai jo ek naya object create karne me help karta hai. Yeh function do parameters leta hai: prototype aur propertiesObject.

Prototype parameter ke through aap specify kar sakte hai ki aapka naya object kis prototype se inherit karega. Prototype ek existing object ho sakta hai jiska aap clone banana chahte hai.

PropertiesObject parameter optional hai aur ismein aap apne naye object ke property aur unki values set kar sakte hai.

example

```
// Create a person object as prototype
const person = {
  greeting: function() {
    console.log(`Hello, my name is ${this.name}`);
  }
};

// Create a new object using person as prototype
const john = Object.create(person);

// Set properties of john object
john.name = 'John';
john.age = 30;

// Call the method of john object
john.greeting(); // Output: Hello, my name is John
```

Is example mein humne ek `person` object create kiya jiska `greeting` method hai. Fir humne `Object.create()` function ka use karke ek naya object `john` create kiya jiske prototype ke roop mein `person` object set kiya gaya hai. Ab humne `john` object ke properties set kiye jaise ki `name` aur `age`, fir `greeting()` method ko call kiya jisne apna output `"Hello, my name is John"` diya.
### What is Chaining methods and how to do it for custom functions

Chaining methods is a technique in JavaScript that allows you to call multiple functions on the same object in a single line of code. This can make your code more concise and easier to read.

To use chaining methods with custom functions in JavaScript, you need to ensure that each function returns the object it was called on (usually using the `return this;` statement at the end of the function). This allows you to chain additional functions onto the end of the initial function call.

Let's take an example of a custom function that manipulates an array of numbers:

```javascript
function NumberArray(numbers) {
  this.numbers = numbers;

  this.add = function (num) {
    this.numbers.push(num);
    return this;
  };

  this.subtract = function (num) {
    for (let i = 0; i < this.numbers.length; i++) {
      this.numbers[i] -= num;
    }
    return this;
  };

  this.multiply = function (num) {
    for (let i = 0; i < this.numbers.length; i++) {
      this.numbers[i] *= num;
    }
    return this;
  };

  this.divide = function (num) {
    for (let i = 0; i < this.numbers.length; i++) {
      this.numbers[i] /= num;
    }
    return this;
  };
}
```

Here, we have created a custom `NumberArray` object that contains an array of numbers and four functions: `add`, `subtract`, `multiply`, and `divide`. Each function modifies the array of numbers and returns the object itself (`this`) so that you can chain additional function calls onto it.

Now, we can create a new `NumberArray` object and chain together some function calls like this:

```javascript
const myNumbers = new NumberArray([1, 2, 3]);

myNumbers.add(4).subtract(1).multiply(2).divide(3);

console.log(myNumbers.numbers); // Output: [2, 4, 6]
```

In this code, we create a new `NumberArray` object with the numbers `[1, 2, 3]`. Then, we chain together four function calls to add `4`, subtract `1`, multiply by `2`, and divide by `3`. Finally, we log the resulting array of numbers (`[2, 4, 6]`) to the console.

So, chaining methods in JavaScript allows you to call multiple functions on the same object in a single line of code, which can make your code more concise and easier to read.
### what is Primitive vs Object

JavaScript में, Primitive डेटा टाइप्स उन जानकारियों को दर्शाते हैं जो सबसे आसानी से होल्ड होती हैं और वे Immutable होते हैं ( अर्थात परिवर्तन योग्य नहीं होते हैं।) जबकि Objects डेटा टाइप्स उन जानकारियों को दर्शाते हैं जो अधिक जटिल होती हैं और mutable होती हैं ( अर्थात परिवर्तन योग्य होती हैं।)

Primitive डेटा टाइप्स में 5 विभिन्न टाइप्स होते हैं: Strings, Numbers, Booleans, null और undefined.

example

```
let name = "John"; //String
let age = 30; //Number
let isStudent = true; //Boolean
let job = null; //null
let pet; //undefined
```

Objects डेटा टाइप्स अनेक key-value pairs को सामने रखते हैं, जो की properties कहलाते हैं। Objects बनाने के लिए, { } विशेषकों में कुछ values दर्ज करने से एक नया object बनता है।

example

```
let person = {
  name: "John",
  age: 30,
  isStudent: true
};
```

इसमें, "person" एक Object है जिसके अंदर "name", "age", और "isStudent" properties हैं।आप इस प्रकार भी एक नया property add कर सकते हैं:

```
person.job = "developer";
```

इससे, "person" object के अंदर एक नया property ("job") add हो गया है।

### what is Understanding of how primitive and non-primitives are stored in memory

Primitive data types in JavaScript are stored directly in memory, whereas non-primitive data types are stored by reference.

Primitive data types include strings, numbers, booleans, null, and undefined. When a primitive value is assigned to a variable, the actual value is stored in memory at that variable's location. For example:

```
let name = "John";
let age = 25;
let isMarried = true;
```

In this code snippet, the variables `name`, `age`, and `isMarried` are all primitive data types. The string "John" is stored at the memory location for the variable `name`, the number 25 is stored at the memory location for the variable `age`, and the boolean value `true` is stored at the memory location for the variable `isMarried`.

Non-primitive data types include objects, arrays, and functions. When a non-primitive value is assigned to a variable, only the reference to the memory location where the value is stored is stored in that variable. For example:

```
let person = { name: "John", age: 25 };
let numbers = [1, 2, 3, 4];
```

In this code snippet, the variable `person` is an object and the variable `numbers` is an array, both of which are non-primitive data types. When these values are assigned to their respective variables, only a reference to the memory location where the values are stored is stored in those variables.

To illustrate this concept, let's say we create another variable `anotherPerson` and assign it the value of `person`:

```
let anotherPerson = person;
```

Now, if we change the `name` property of `anotherPerson`, it will also change the `name` property of `person`. This is because both variables hold a reference to the same memory location where the object `{ name: "John", age: 25 }` is stored, so any changes made to one variable will be reflected in the other variable as well:

```
anotherPerson.name = "Jane";
console.log(person.name); // Output: Jane
```

In summary, primitive data types in JavaScript are stored directly in memory, while non-primitive data types are stored by reference to their memory location. This means that when non-primitive values are assigned to variables, only a reference to the memory location where the value is stored is stored in that variable, not the value itself.

### How to Copy object? Shallow copy and deep copy

Object copy refers to creating a new object with the same values as an existing object. In JavaScript, there are two types of copying methods: Shallow Copy and Deep Copy.

Shallow Copy:
A Shallow copy only creates a new object but does not duplicate the nested objects. Instead, it creates a reference to the nested objects in the original object. Therefore, any changes made to the nested objects will be reflected in both the original and copied objects. We use the Object.assign() method to create a shallow copy.

Let's take an example to understand this better:

```
// Original object
const originalObj = {
  name: "John",
  age: 30,
  address: {
    city: "New York",
    state: "NY"
  }
};

// Shallow copy of original object
const copiedObj = Object.assign({}, originalObj);

// Modifying the nested object in the copied object
copiedObj.address.city = "Los Angeles";

console.log(copiedObj);
// Output: {name: "John", age: 30, address: {city: "Los Angeles", state: "NY"}}

console.log(originalObj);
// Output: {name: "John", age: 30, address: {city: "Los Angeles", state: "NY"}}
```

As you can see, even though we modified the nested object in the copied object, the changes also got reflected in the original object.

Deep Copy:
A Deep copy creates a completely independent clone of the original object, including all the nested objects. Therefore, any changes made to the nested objects in the copied object will not affect the original object. We can use the JSON.parse() and JSON.stringify() methods to create a deep copy.

Let's take an example to understand this better:

```
// Original object
const originalObj = {
  name: "John",
  age: 30,
  address: {
    city: "New York",
    state: "NY"
  }
};

// Deep copy of original object
const copiedObj = JSON.parse(JSON.stringify(originalObj));

// Modifying the nested object in the copied object
copiedObj.address.city = "Los Angeles";

console.log(copiedObj);
// Output: {name: "John", age: 30, address: {city: "Los Angeles", state: "NY"}}

console.log(originalObj);
// Output: {name: "John", age: 30, address: {city: "New York", state: "NY"}}
```

As you can see, even though we modified the nested object in the copied object, the changes did not get reflected in the original object.
### How the web works in javascript

JavaScript is a programming language that can be used to create interactive web pages. To understand how JavaScript works on the web, it's important to first understand how the web itself works.

Web pages are created using a combination of HTML, CSS, and JavaScript. HTML provides the structure of the page, CSS is used to style the page, and JavaScript adds interactivity and functionality to the page.

When you visit a website in your web browser, the browser sends a request to the server where the website is hosted. The server then sends back the files needed to display the website in your browser, including the HTML, CSS, and JavaScript files.

Once these files are downloaded by the browser, the HTML file is parsed and a Document Object Model (DOM) is created. The DOM is a tree-like structure that represents the elements on the web page. JavaScript can then be used to manipulate the DOM, adding or removing elements, changing styles, or responding to user interactions.

For example, let's say you have a button on your web page with an id of "myButton". You could use JavaScript to add a click event listener to the button, so that when someone clicks it, a message appears on the screen:

```javascript
const myButton = document.getElementById("myButton");

myButton.addEventListener("click", function () {
  alert("Hello, world!");
});
```

In this example, we're using the `getElementById` method to get a reference to the button element on the page. We then use the `addEventListener` method to add a click event listener to the button. When the button is clicked, the anonymous function passed as the second argument to `addEventListener` is executed, which displays an alert message.

JavaScript can also be used to make requests to the server without reloading the entire page. This is called AJAX (Asynchronous JavaScript and XML). For example, you could use JavaScript to send a request to a server to get data and then update the page without refreshing it:

```javascript
fetch("/api/data")
  .then((response) => response.json())
  .then((data) => {
    // Do something with the data, like update the DOM
  })
  .catch((error) => {
    console.error(error);
  });
```

In this example, we're using the `fetch` method to make a request to a server endpoint at `/api/data`. The `then` method is used to handle the response from the server. We convert the response to JSON format using the `json` method, and then use the data to update the DOM or do some other operation. If an error occurs, the `catch` method is used to handle it.

Overall, JavaScript is a powerful language for adding interactivity and functionality to web pages. By manipulating the DOM, making AJAX requests, and handling events, you can create dynamic and engaging web experiences for your users.

### what is Server in javascript and how to works

JavaScript में सर्वर एक कंप्यूटर होता है जो अन्य कंप्यूटर को डेटा और संसाधनों के लिए सेवा प्रदान करता है। सर्वर जीवन में बहुत महत्वपूर्ण होता है, जिसमें उपयोगकर्ता अन्य संसाधनों जैसे कि फ़ाइल, डेटाबेस और वेब पृष्ठों आदि तक पहुंच प्राप्त कर सकते हैं।

एक साधारण उदाहरण समझने के लिए, आप एक वेबसाइट खोलते वक्त सर्वर से संपर्क करते हो। जब आप वेबसाइट पते को अपने ब्राउज़र में भरते हो, तो आपका ब्राउज़र उस URL को सर्वर के पते तक भेजता है।

सर्वर, फिर उस URL के आधार पर डेटा और संसाधनों को ढूंढता है और अपने उपयोगकर्ताओं के लिए उन्हें भेजता है। उदाहरण के लिए, आप सर्वर से एक वेब पृष्ठ की जानकारी (HTML, CSS, फ़ोटो, वीडियो आदि) मांग सकते हैं।

इसके अलावा, सर्वर डेटाबेस से भी जुड़ा होता है जो उपयोगकर्ताओं के लिए डेटा को संग्रहित करता है। उदाहरण के लिए, एक ई-कॉमर्स वेबसाइट आपके खाते और खरीदों को एक डेटाबेस में संग्रहित करता है।

### what is Client in javascript and how to works

Client in JavaScript refers to the part of a web application that runs on the user's browser. When a user requests a webpage from the server, the server sends back HTML, CSS, and JavaScript files to the client's browser. The client then renders the webpage using these files.

JavaScript runs on the client-side, which means it is executed on the user's computer rather than on the server. This allows for dynamic and interactive features on a webpage, such as form validation, animations, and responsive design.

Let me explain this in Hinglish:

Client ka matlab hota hai wo hissa jise hum user ke browser mein use karte hain. Jab kabhi koi user server se webpage request karta hai toh server usko HTML, CSS aur JavaScript files bhejta hai. Fir client un files ko use karke webpage ko render karta hai.

JavaScript client-side pe chalta hai, matlab ye user ke computer pe execute hota hai aur server pe nahi. Isse webpage pe dynamic aur interactive features add kar sakte hai jaise form validation, animations aur responsive design.

For example, let's say you are visiting a website that has a form where you need to enter your name and email address. When you submit the form, JavaScript can validate whether you have entered a valid email address or not. It can also display an error message if any required fields are left blank.

Another example is when you visit a website that has a menu bar with dropdown options. JavaScript can be used to make the menu responsive, meaning it will adjust based on the size of the user's screen. Additionally, JavaScript can create animations when the user hovers over the menu options, making the website more engaging and interactive.

### what is Request in javascript and how to works

Request in JavaScript refers to the process of sending a network request to a server to retrieve or manipulate data. It can be used to fetch data from APIs, submit form data, or perform other types of HTTP requests.

For example, suppose you want to fetch data from an API using JavaScript. You can do so by creating a new instance of the XMLHttpRequest object, which allows you to send HTTP requests and receive responses.

Here's an example code snippet that demonstrates how to fetch data from an API using JavaScript:

```
var request = new XMLHttpRequest();
request.open('GET', 'https://api.example.com/data');
request.onload = function() {
  if (request.status === 200) {
    // Do something with the retrieved data
    console.log(request.response);
  } else {
    // Handle errors
    console.log('Error retrieving data');
  }
};
request.send();
```

In this example, we create a new XMLHttpRequest object and specify the URL of the API we want to fetch data from. We then set up an event listener for the `onload` event, which is triggered when the response is received. If the response status is 200 (OK), we log the response to the console. Otherwise, we log an error message.

Overall, the `XMLHttpRequest` object allows us to send requests to a server and handle the responses in our JavaScript code.

### what is Response in javascript and how to works?

Response ka matlab hai "javasript ke dwara prapt uttar", jo hum apne JavaScript code ko chalate samay aata hai. Jab hum kisi URL ki request bhejte hain, to server uske pehle uski authenticity aur security ko verify karke usi URL par corresponding data ka response bhejta hai. Is response mei hume us webpage ke HTML, CSS, aur JavaScript code ke sath-sath anya details jaise images ya database entries bhi mil sakte hain.

Jab tak hum JavaScript ke ajax API ka use nahi karte hain, tab tak hume browser ke dvara automatically ek page refresh hona padega. Lekin jab hum response ka use karte hain, tab hum server se data asynchrnously (bina page refresh ke) receive kar sakte hain aur use apne webpage par display kar sakte hain.

Example ke tor par, consider karein ki humare paas ek search box hai aur hum user ke dwara input kiye gaye keywords ke hisab se related results dikhana chahte hain. Jab user search button par click karte hain, tab hum JavaScript ka use karke unke dwara diye gaye keywords ko server ke paas bhej sakte hain aur server uska response ek JSON object ke roop mei bhej sakta hai. Us JSON object ko hum phir apne webpage par parse karke dikhane ke liye use kar sakte hain.
### what is Prototypes

Prototypes in JavaScript refer to an object that serves as a blueprint for other objects. Every object in JavaScript has a prototype, which provides it with default properties and methods.

For example, let's say we have an object called "Person" with two properties - name and age. We can create another object called "john" and set its prototype to be the "Person" object. This means that the "john" object will inherit the properties and methods of the "Person" object.

Here's an example code snippet:

```
// Creating the Person object
var Person = {
  name: "",
  age: 0,
  greet: function() {
    console.log("Hello, my name is " + this.name);
  }
};

// Creating the john object
var john = Object.create(Person);

// Setting the name and age properties of the john object
john.name = "John";
john.age = 30;

// Calling the greet method on the john object
john.greet(); // Output: "Hello, my name is John"
```

In the above example, we first create the "Person" object with two properties (name and age) and a method called "greet". Then, we create a new object called "john" using the "Object.create()" method and set its prototype to be the "Person" object.

Next, we set the "name" and "age" properties of the "john" object. Finally, we call the "greet" method on the "john" object, which outputs "Hello, my name is John".

So, in summary, prototypes in JavaScript allow us to create objects that inherit properties and methods from other objects. This makes it easy to create reusable code and avoid repetition.
### what is ES6 classes

ES6 classes in JavaScript are a new syntax for creating reusable objects with properties and methods. Think of classes as blueprints or templates for creating multiple instances of similar objects.

Let's take an example of a class called `Car`:

```javascript
class Car {
  constructor(model, year, color) {
    this.model = model;
    this.year = year;
    this.color = color;
  }

  startEngine() {
    console.log(`Starting engine of ${this.color} ${this.model}...`);
  }
}
```

In the above code, we have defined a class called `Car` which has three properties: `model`, `year` and `color`. The `constructor` method is used to initialize these properties when a new instance of the class is created.

We have also defined a method called `startEngine` which logs a message to the console when called. This method can be called on any instance of the `Car` class.

To create a new instance of the `Car` class, we can use the following code:

```javascript
let myCar = new Car("Toyota", 2022, "red");
```

This creates a new instance of the `Car` class with the properties `model` set to `'Toyota'`, `year` set to `2022`, and `color` set to `'red'`.

We can now call the `startEngine` method on `myCar` like this:

```javascript
myCar.startEngine();
// Output: Starting engine of red Toyota...
```

So, in summary, ES6 classes provide a simpler and more concise way to define and create objects with predefined properties and methods.

### what is Setters and Getters

Setters and Getters in JavaScript are functions that allow us to control the access and modification of object properties. In simpler terms, they enable us to get and set the values of object properties using functions.

For example, suppose we have an object called `person` with properties `name` and `age`. We can define setters and getters for these properties as follows:

```javascript
const person = {
  _name: "",
  _age: 0,

  set name(name) {
    // Setter for name property
    this._name = name;
  },

  set age(age) {
    // Setter for age property
    if (age > 0 && age < 120) {
      this._age = age;
    } else {
      console.log("Invalid age");
    }
  },

  get name() {
    // Getter for name property
    return this._name;
  },

  get age() {
    // Getter for age property
    return this._age;
  },
};
```

Here, we have defined setters and getters for the `name` and `age` properties using `set` and `get` keywords respectively. The `_name` and `_age` variables with an underscore prefix are used to store the actual values of these properties.

Now, we can set and get the values of the `name` and `age` properties using these setters and getters as follows:

```javascript
person.name = "John"; // Using setter for name property
person.age = 30; // Using setter for age property

console.log(person.name); // Using getter for name property
console.log(person.age); // Using getter for age property
```

In Hinglish, we can say ki Setters aur Getters JavaScript mein functions hai jo humein object ke properties ko access aur modify karne ki permission dete hai. Ye humein functions use karke object ke properties ki values ko get aur set karne ki suvidha pradaan karte hai.

### what is Static methods

Static methods in JavaScript are functions that belong to the class itself rather than to any specific instance of that class. These methods can be accessed directly on the class without creating an object of the class.

Static methods are declared using the keyword `static` before the function name. Here's an example:

```javascript
class MyClass {
  static myStaticMethod() {
    console.log("This is a static method.");
  }
}

MyClass.myStaticMethod(); // Output: This is a static method.
```

In this example, `myStaticMethod()` is a static method of the `MyClass` class. It can be called directly on the class without creating an instance of `MyClass`.

Now let me explain in Hinglish:

Static method ka matlab hota hai ki ye woh method hota hai jo sirf class se related hota hai aur kisi bhi particular instance se nahi. Ismein hum ek class ke andar ek function likhte hain jisko `static` keyword ke sath define kiya jata hai. Is tarah ke methods ko direct class ke upar call kiya jaa sakta hai bina kisi object ke banaye.

Upar diye gaye example mein `MyClass` class ka ek static method hai jiska naam `myStaticMethod()` hai. Hum ise `MyClass.myStaticMethod()` syntax se direct call kar sakte hain bina kisi `MyClass` ke object ke banaye.

### How to use ES6 classes

ES6 classes in JavaScript are a way to create objects using a class-based syntax. Here's how you can use them, explained in Hinglish with an example:

Sabse pehle, hum ek class banayenge "Person" naam se. Is class mein hum log "name" aur "age" properties rakhenge.

```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}
```

Yahan `constructor` ek special method hai, jo class ke objects ko initialize karta hai. Hum yahaan `name` aur `age` arguments le rahe hain, aur fir `this` keyword se unhein instance variables mein store kar rahe hain.

Ab hum log is class se ek object banaenge, jiska naam "john" hoga, aur age 25 hogi.

```javascript
const john = new Person("John", 25);
```

Yahan `new` keyword se hum log ek naya instance (ya object) banarahe hain, jiske liye hum log `Person` class ka use kar rahe hain. Hum arguments mein "John" aur 25 pass kar rahe hain, jisse `john` object ke `name` aur `age` properties set ho jaayenge.

Ab hum log `console.log()` se `john` object ke properties dekh sakte hain:

```javascript
console.log(john.name); // Output: "John"
console.log(john.age); // Output: 25
```
### what is Handling Rejected Promises

"Rejected Promises" refers to the situation where a Promise in JavaScript fails to fulfill its intended task, such as due to an error or exception. Handling Rejected Promises involves defining what should happen when a Promise is rejected, so that the program can gracefully handle errors and prevent potential crashes.

To handle a Rejected Promise, we attach a ".catch()" method to the Promise object. This method takes a function as its argument, which will be called if the Promise is rejected. Within this function, we can define how to handle the error, such as logging it to the console, displaying an error message to the user, or attempting to recover from the error.

Here's an example of handling a Rejected Promise:

```
fetch('https://example.com/data')
  .then(response => response.json())
  .then(data => {
     // process the data
  })
  .catch(error => {
     console.error('Failed to retrieve data:', error);
     // handle the error
  });
```

In this example, we are using the "fetch()" function to retrieve data from a web API. If the retrieval fails for any reason (e.g., due to network connectivity issues), the Promise will be rejected and the code within the ".catch()" method will be executed. This code logs an error message to the console and provides a fallback option for handling the error.

Handling Rejected Promises is important for writing robust and reliable JavaScript code, as it helps prevent unexpected behavior and improves the overall user experience.
JavaScript me classical inheritance ni hota hai jisme parent ek class hoti hai. Iske bjay JavaScript prototypal inheritance use krti hai.

### Prototypal Inheritance:

Prototypal inheritance me object ka parent prototype hota hai. Javascript object ki ek hidden property prototype hoti hai. Yeh prototype property ya to null hoti hai ya fir kisi dusre object ko refer krti hai.
Ek object ki sirf ek hi prototype property ho skti hai

Why do we use prototypal inheritance and what are the benefits of using it? : Prototypal inheritance me object ka parent prototype object hota hai. Is prototype object me common properties and functions add kr skte hain. Jinhe ki sare objects use kr skte hain.

- Prototypal inheritance 3 ways se kr skte hain:

  1. Constructor function
  2. ES6 classes
  3. Object.create

### Constructor function:

Constructor function ek normal function ki trah hi hota hai lekin is function me kuch chize extra hoti hain.

Is function ko call krte time new keyword ka use krte hain. new keyword lgane se ek new object create ho jata hai. Aur is object me properties ki value assign krne ke lie constructor function me this keyword ka use hota
hai.

- for example:

```
const Person = function (name, age, address) {
  this.name = name;
  this.age = age;
  this.address = address;
};

const sajid = new Person("Sajid", 31, "Jhotwara, Jaipur");
```

ek constructor function se hm kitne b objects create kr skte hain. Ek new object bnane ke lie firse new keyword ka use krna pdega. for example:

```
 const afzal = new Person("Afzal", 28, "Sikar");
```

Jab b hm constructor function se object bnate hain to prototype chain automatically bn jati hain. Agar hume ise verify krna hai to console me object ko print karvane ke bad expand krke dekh skte hain.

object (individual properties and functions)
prototype (common properties and functions)
prototype (JavaScript predefined properties and functions)

### What is Prototype chain?:

Created object ka parent ek Prototype object hota hai. Vah is prototype object ka parent b ek Prototype object hota hai. Jb b hm koi method call krte hain ya property use krte hain to vah property/function ko prototype object me search kia jata hai. Agar vah function/property prototype object me ni milti hai to error throw hoti hai.

### How to add common properties and functions in a prototype:

Iske 2 ways hai. Ek to hm direct constructor function ke prototype me add kr skte hain and dusra tarika ye hai ki object ki **proto** property use kr skte hain

\_proto\_\_ property outdated ho chuki hai islie hume ise use ni krna chahiye. Iski jgah hm Object.getPrototypeOf/Object.setPrototypeOf use kr skte hain.

```
 Person.prototype.pincode = 302012; //first tarika
   sajid.__proto__.pincode = 302012; //Dusra tarika
```

Isi trah se hm kisi b prototype me ek function b add kr skte hain.

- for example:

```
 Person.prototype.getAddress = function () {
       return this.address;
   };
   const sajid = new Person("Sajid", 31, "Jhotwara, Jaipur");
   console.log(sajid.getAddress());
```

### ES6 classes:

ES6 classes constructor function ko different tarike se likhne ka way provide krata hai. But ES6 classes internally (behind the scene) costructor function hi use krta hain. Ye modern tarika hai hai constructor function ko class ki form me likhne ka

- for example:

```
class Person {
  constructor(name, age, address) {
    this.name = name;
    this.age = age;
    this.address = address;
  }
}

const sajid = new Person("Sajid", 31, "Jhotwara, Jaipur");
console.log(sajid);
```

Yadi hume kisi class ke prototype me koi function/property add krna hai to constructor se bahar add kr skte hain. Vah automatically prototype me add ho jayega.

- For example:

```
 class Person {
      constructor(name, age, address) {
       this.name = name;
         this.age = age;
          this.address = address;
      }
      getAddress() {
          return this.address; //Will be part of prototype object
      }
  }

```

### Object.create:

Object create function new object create krne ke kaam aata hai. create function ko hm ek object pass kr skte hain aur vah object create ho jayega aur uski prototype chain b automatically bn jayegi.

Yadi hm object ni bnana chahte hai aur proerties bad me set krna chahte hai to create function ko ek empty object pass krna pdega.

- For example:

```
const Person = Object.create(); //Error
 console.log(Person);

```

- Another example:

```
const Person = Object.create({});
  Person.name = "Sajid";
   Person.age = 31;
    Person.address = "Jhotwara, Jaipur";
  console.log(Person); //Person object me prototype chain automatically create ho jayegi.

```
### what is Building a Simple Promise

Promises in JavaScript are used to handle asynchronous operations like fetching data from a database or making an API call. A Promise represents the eventual completion (or failure) of an asynchronous operation and allows you to handle that result when it becomes available.

To build a simple Promise in JavaScript, you can use the Promise constructor function which takes a callback function with two arguments: resolve and reject. The resolve function is called when the Promise is fulfilled with a successful result, while the reject function is called when there's an error.

Here's an example of building a simple Promise which returns a message after a delay of 2 seconds:

```javascript
const myPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("Hello World!");
  }, 2000);
});

myPromise
  .then((result) => {
    console.log(result); // prints 'Hello World!' after 2 seconds
  })
  .catch((error) => {
    console.error(error);
  });
```

In this example, we create a new Promise using the Promise constructor and pass in a callback function which uses the setTimeout function to delay the execution of the resolve function by 2 seconds. When the timeout is complete, the resolve function is called with the message 'Hello World!'.

We then chain the `.then()` method to the Promise object which will execute its callback function when the Promise is fulfilled successfully. The `console.log` statement inside the callback function prints the result of the Promise, which is the message 'Hello World!'.

If there was an error during the execution of the Promise, the `.catch()` method would be executed, which logs the error to the console with `console.error`.
### What is Ajax

Ajax in javascript hai ek technique jiske dwara hum webpage ko dynamically update kar sakte hain bina page ko refresh kiye. Iska full form hai "Asynchronous JavaScript and XML".

Jab hum koi webpage load karte hain, toh server se data retrieve karne ke liye ek naya request bhejna padta hai aur page ko refresh karna padta hai. Lekin Ajax ka upyog karke, hum ek web page par hi data receive kar sakte hain aur use display kar sakte hain.

Ek example lete hain: Suppose ki hum ek blog post padh rahe hain aur comment section open hai. Jab hum comment section ko refresh karte hain, tab humein naye comments dikhai dete hain. Lekin agar hum Ajax ka upyog karein, toh jab bhi koi naya comment aaye ga, tab wo automatically comment section mein add ho jaayega bina page refresh kiye.

Iske liye, hum JavaScript ka istemal karenge jo server ke saath asynchronous request bhejega, jismein data exchange ke liye JSON (JavaScript Object Notation) ka use kiya jaata hai. JSON ek lightweight data interchange format hai jo easy to read and write hota hai.

Upar di gayi example mein, jab koi naya comment aata hai, toh JavaScript us data ko retrieve karta hai aur use DOM (Document Object Model) ke through comment section mein add karta hai. Is tarah se, web page ko refresh kiye bina new data display kiya ja sakta hai.
### what is Error Handling with Try catch

Error handling with try-catch in JavaScript is a way to gracefully handle errors that may occur while running our code. The basic idea is to try something and if it fails, catch the error and handle it appropriately.

Here's an example of how to use try-catch in JavaScript:

```javascript
try {
  // code that may throw an error
  let result = someFunction();
} catch (error) {
  // handle the error
  console.log("An error occurred: " + error.message);
}
```

In this example, we're trying to call a function called `someFunction()`. If this function throws an error, the catch block will be executed and the error message will be logged to the console. Note that the error object passed into the catch block contains information about the error, such as the error message.

Now, let me explain this in Hinglish:

Error handling ka matlab hota hai ki hum apne code ko aise likhe jisme agar koi error aa bhi jaye toh usse handle kar sakein aur code kaam karna jari rahe. Try-catch ka use karke hum apne code mei errors ko gracefully handle kar sakte hain.

Aap yeh code dekhiye:

```javascript
try {
  // Code jisse Error aa sakta hai
  let result = someFunction();
} catch (error) {
  // Error ko handle karein
  console.log("Kuch galat ho gaya: " + error.message);
}
```

Iss example mei hum ek function `someFunction()` ko call kar rahe hain. Agar yeh function koi error throw karta hai toh catch block execute hoga aur error message console mei print hoga. Yaad rakhiye ki catch block mei pass kiya gaya error object error ke baare mei information deta hai, jaise error message.
### What is Promise

Promise ek JavaScript object hota hai jiska use asynchronous code ke liye kiya jaata hai. Asynchronous code ka matlab hota hai ki jab hum kisi task ko execute kar rahe hote hai aur uska result time lagakar aata hai tab tak hum dusre tasks ko perform kar sakte hai.

Promise ek tarah se guarantee deta hai ki kisi task ka result future me available ho jayega. Jab hum koi task Promise object me wrap karte hai, to wo task ek new thread me execute hota hai aur promise hume ek reference deta hai jisse hum task ke result ko future me access kar sakte hai.

Example:

Ek common example hai fetch() function jo network request ko execute karta hai. Ye function data ko retrieve karne ke liye server se communication karta hai. Iska syntax niche diya gaya hai:

```
fetch(url)
  .then(response => {
    // handle the response
  })
  .catch(error => {
    // handle the error
  });
```

Is example me, `fetch()` ek Promise object return karta hai. Hum `then()` method me ek callback function pass karte hai jo response ko handle karti hai. Agar fetch() me koi error hota hai to `catch()` method error ko handle karta hai.

Upar diye gaye example se hum ye samajh sakte hai ki Promise ek asynchronous operation ko represent karta hai jo future me resolve ya reject ho sakta hai. Hum `then()` aur `catch()` methods se resolve aur reject cases ko handle kar sakte hai.
### What is Fetch

Fetch ek JavaScript API hai jo humein server se data fetch karne ki suvidha deta hai. Iska upyog hum client-side web applications mein karte hai jahan par humein server se data retrieve karne ki zarurat hoti hai without reloading the entire page.

Fetch method ek HTTP request bhejta hai aur uska response promise ke roop mein wapas milta hai. Iske liye hum `fetch()` function ka upyog karte hai, jismein hum URL ka naam aur request method (GET, POST, PUT, DELETE etc.) specify karte hain.

Example:

```
fetch('https://api.example.com/data')
  .then(response => {
    if (!response.ok) {
      throw new Error('HTTP error ' + response.status);
    }
    return response.json();
  })
  .then(data => {
    console.log(data);
  })
  .catch(error => {
    console.error(error);
  });
```

Yahan humne `fetch()` function ka upyog kiya hai ek URL ('https://api.example.com/data') ke sath GET request bhejne ke liye. Phir humne Promise chain ka upyog kiya hai jisse ki hum response ko handle kar sakein. Agar response OK nahi hai toh humne ek error throw kiya hai. Agar response sahi hai toh hum JSON parse kiya hai aur console mein data print kiya hai.
### what ia Promise Combinators: race, allSettled and any

Promise Combinators are higher-order functions in JavaScript that allow you to combine multiple Promises and handle their results in a concise way. These functions include `Promise.race()`, `Promise.allSettled()`, and `Promise.any()`. Let's look at each of these in more detail:

1. `Promise.race()` - Yeh function multiple promises ko combine karta hai aur sabse pehle resolve ya reject hone wali promise ka result return karta hai.

Example: Imagine you have two Promises, one that resolves after 2 seconds and another that resolves after 5 seconds. If you want to get the result of whichever Promise resolves first, you can use `Promise.race()` like this:

```
const promise1 = new Promise((resolve) => {
  setTimeout(() => {
    resolve('Result of Promise 1');
  }, 2000);
});

const promise2 = new Promise((resolve) => {
  setTimeout(() => {
    resolve('Result of Promise 2');
  }, 5000);
});

Promise.race([promise1, promise2])
  .then((result) => {
    console.log(result); // Output: "Result of Promise 1"
  });
```

2. `Promise.allSettled()` - Yeh function ek array mein diye gaye promises ko combine karta hai aur jab sabhi promises settle ho jaate hain (yani resolve ya reject ho jaate hain), to ek array of objects return karta hai jo har promise ke liye uske status, value/ reason properties mein details deta hai.

Example: Let's say you have three Promises, but you don't care about which ones resolve or reject, you just want to know the status of all of them. You can use `Promise.allSettled()` like this:

```
const promise1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('Result of Promise 1');
  }, 2000);
});

const promise2 = new Promise((resolve, reject) => {
  setTimeout(() => {
    reject('Error: Promise 2 rejected');
  }, 5000);
});

const promise3 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('Result of Promise 3');
  }, 3000);
});

Promise.allSettled([promise1, promise2, promise3])
  .then((results) => {
    console.log(results);
    /* Output: [
      { status: 'fulfilled', value: 'Result of Promise 1' },
      { status: 'rejected', reason: 'Error: Promise 2 rejected' },
      { status: 'fulfilled', value: 'Result of Promise 3' }
    ] */
  });
```

3. `Promise.any()` - Yeh function ek array mein diye gaye promises ko combine karta hai aur sabse pehle resolve hone wali promise ka result return karta hai. Agar saare promises reject ho jayein to, ek AggregateError throw karta hai.

Example: Imagine you have three Promises, but you only care about the result of the first one that resolves. You can use `Promise.any()` like this:

```
const promise1 = new Promise((resolve) => {
  setTimeout(() => {
    resolve('Result of Promise 1');
  }, 2000);
});

const promise2 = new Promise((resolve, reject) => {
  setTimeout(() => {
    reject('Error: Promise 2 rejected');
  }, 5000);
});

const promise3 = new Promise((resolve) => {
  setTimeout(() => {
    resolve('Result of Promise 3');
  }, 3000);
});

Promise.any([promise1, promise2, promise3])
  .then((result) => {
    console.log(result); // Output: "Result of Promise 1"
  })
  .catch((error) => {
    console.log(error); // This block will not execute in this example
  });
```
### what is Consuming Promises

Consuming Promises in JavaScript refers to the process of handling the resolved or rejected values returned by a Promise object. When a Promise is created, it can either resolve successfully with a value or fail with an error. To consume these values, we use the then() and catch() methods.

The .then() method takes two optional callback functions as arguments - one for handling the resolved value and another for handling errors. For example:

```
fetch('https://jsonplaceholder.typicode.com/todos/1')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error))
```

In this example, we use the fetch API to make a request to a JSON placeholder API endpoint. The first .then() method converts the response into a JSON object. The second .then() method logs the data to the console. If there is an error, the .catch() method logs the error to the console.

If we want to handle both success and failure cases in a single callback function, we can use the .finally() method, which is called regardless of whether the promise was resolved or rejected. For example:

```
fetch('https://jsonplaceholder.typicode.com/todos/1')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error))
  .finally(() => console.log('Request completed'))
```

In this example, the .finally() method logs a message indicating that the request has completed, regardless of whether it succeeded or failed.

To summarize, consuming promises in JavaScript involves using the then(), catch(), and finally() methods to handle the resolved or rejected values returned by a Promise object.
### what is Chaining Promises

Chaining Promises in JavaScript refers to a technique that allows multiple asynchronous operations to execute sequentially, where the output of one operation becomes the input of the next operation.

For example, suppose you want to fetch data from an API, process it, and then display it on the webpage. In this case, you can use Promises to chain these operations together. Here's an example:

```
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => processData(data))
  .then(result => displayData(result))
  .catch(error => console.error(error));
```

In the above code, `fetch` is used to make an HTTP request to the API and return a Promise that resolves with the response. The first `then` method is used to extract the JSON data from the response. The second `then` method calls the `processData` function with the extracted data, which returns a new Promise that resolves with the processed data. Finally, the third `then` method calls the `displayData` function with the processed data to display it on the webpage. If any error occurs during any of these steps, the `catch` method will handle it.

In Hinglish, chaining Promises in JavaScript ka matlab hai ki ek Technique jismein ek se zyada async operations ko sequence mein execute kiya ja sakta hai, jahan ek operation ka output agle operation ka input banta hai.

Jaise ki agar aapko API se data fetch karna hai, usse process karna hai aur phir web page pe display karna hai. Iss case mein, aap Promises ka use kar sakte hai aur inse operations ko chain kar sakte hai. Neeche diya gaya code dekhiye:

```
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => processData(data))
  .then(result => displayData(result))
  .catch(error => console.error(error));
```

Upar diye gaye code mein, `fetch` ka use HTTP request banane ke liye kiya gaya hai aur ek Promise ko return kar dia jata hai jo response ke saath resolve hota hai. Pehla `then` method response se JSON data extract karne ke liye use kiya jata hai. Dusra `then` method `processData` function ko extracted data ke saath call karta hai jo ek naya Promise ko resolve karta hai processed data ke saath. Antim `then` method `displayData` function ko process kiya hua data ke saath call karta hai taki usse web page pe display kiya ja sake. Agar koi error in steps mein kahin bhi aati hai to `catch` method ise handle karega.
### what is Expalin Encapsulation: Protected Properties and Methods

Encapsulation is a fundamental concept of object-oriented programming that enables you to group related data and functions together into a single unit called an object, and hide the internal details of how the object works from other parts of the program.

In JavaScript, we can achieve encapsulation using classes and objects. We can define properties and methods as public or private based on their visibility. Public properties and methods are accessible from outside the class, whereas private properties and methods are only accessible within the class.

Protected properties and methods are a type of visibility in between public and private. They are accessible within the class and any subclasses derived from it, but not from outside the class hierarchy.

Here's an example to illustrate this concept:

```
class Person {
  constructor(name, age) {
    this.name = name; // Public property
    this._age = age; // Protected property
  }

  greet() {
    console.log(`Hello, my name is ${this.name}.`); // Public method
  }

  _getAge() { // Protected method
    return this._age;
  }
}

class Employee extends Person {
  constructor(name, age, salary) {
    super(name, age);
    this.salary = salary; // Public property
  }

  getSalary() {
    console.log(`${this.name} earns ${this.salary}.`);
  }

  getAge() {
    console.log(`${this.name} is ${this._getAge()} years old.`); // Accessing protected method from subclass
  }
}

let john = new Employee("John", 30, 50000);
john.greet(); // Outputs: Hello, my name is John.
john.getSalary(); // Outputs: John earns 50000.
john.getAge(); // Outputs: John is 30 years old.
console.log(john._age); // Undefined (protected property)
console.log(john._getAge()); // TypeError (protected method)
```

In this example, we have a `Person` class that has a public property `name`, a protected property `_age`, and a public method `greet()`. The `_getAge()` method is a protected method.

We also have an `Employee` subclass that extends the `Person` class and adds a public property `salary` and a public method `getSalary()`. In its `getAge()` method, it accesses the protected `_getAge()` method from the parent class to print the age of the employee.

From outside the class hierarchy, we cannot access the protected property `_age` or the protected method `_getAge()`.

So, the concept of protected properties and methods helps in achieving encapsulation by restricting access to certain properties and methods to within the class hierarchy.

### what is Explain Encapsulation: Private Class Fields and Methods

Encapsulation is a concept in object-oriented programming where we bundle data and methods that operate on that data into a single unit, known as a class. Private class fields and methods are a way to encapsulate data and methods within a class in JavaScript such that they are inaccessible from outside the class.

Let's take an example to understand this concept better. Suppose we want to create a class for a bank account that stores the account holder's name, balance, and allows them to withdraw money from their account. We can use private class fields and methods to ensure that the account holder's balance cannot be accessed or modified from outside the class, while still allowing them to withdraw money.

Here's how we can implement this in JavaScript:

```javascript
class BankAccount {
  #balance = 0; // Private class field

  #updateBalance(amount) {
    // Private class method
    this.#balance -= amount;
  }

  constructor(name) {
    this.name = name;
  }

  withdraw(amount) {
    if (amount > this.#balance) {
      console.log("Insufficient balance!");
      return;
    }

    this.#updateBalance(amount);
    console.log(
      `Withdrawn ${amount} from ${this.name}'s account. Remaining balance: ${
        this.#balance
      }`
    );
  }
}

const johnsAccount = new BankAccount("John");
johnsAccount.withdraw(100); // Output: Insufficient balance!
johnsAccount.#balance = 500; // Error: Cannot access private field
johnsAccount.#updateBalance(100); // Error: Cannot access private method
```

In this example, we've used the '#' symbol before the 'balance' and 'updateBalance' identifiers to make them private class fields and methods respectively. This means that they can only be accessed from within the 'BankAccount' class, and not from outside.

We then defined a constructor method that takes the account holder's name as a parameter and initializes the balance to 0. We also defined a 'withdraw' method that allows the account holder to withdraw money from their account, but only if they have sufficient balance.

Finally, we created an instance of the 'BankAccount' class for John and tried to access his balance and updateBalance method from outside the class. However, since they are private, we got errors indicating that we cannot access them.

In summary, encapsulation using private class fields and methods is a powerful feature in JavaScript that allows us to protect our data and methods from outside interference, ensuring that our code is more robust and secure.
### Asynchronous

Asynchronous JavaScript refers to the ability of JavaScript to execute non-blocking code, allowing other code to run in the meantime. This is achieved through the use of callbacks, promises, and async/await functions, which allow developers to write code that can be executed in a non-sequential order. Asynchronous JavaScript is important for building responsive and efficient web applications, as it allows for tasks to be performed without delaying the execution of other code.

### Ajax

Ajax (Asynchronous JavaScript and XML) ek programming technique hai jismein JavaScript ka use hota hai web pages ko dynamic banane ke liye. Ismein, web page pe data ko load karne ke liye ek HTTP request bheja jaata hai server se, aur server JSON, XML, ya HTML format mein response deti hai. Ye response phir client-side (web browser) mein use kiya jaata hai usse webpage ko update karne ke liye.

Ek example ke through samjhate hain:

Maan lo hume ek webpage banana hai jismein ek button ho. Jab user uss button ko click kare toh hamare webpage pe ek image show hone lage. Ab iske liye humare paas 2 options hai:

1. Page ko refresh kare: Jab user button pe click karega toh hamari website refresh hogi aur image dikhayi degi. Lekin yeh ek slow process hai aur user ko wait karna padega.

2. Ajax ka use kare: Jab user button pe click karega, toh hum ajax ka use karke server se image fetch kar lete hai aur usse webpage pe show kar dete hai. Yeh process behad fast hota hai kyunki page reload nahi hota. Isse user ko bhi wait nahi karna padta.

Iska syntax yeh hota hai:

```javascript
var xhttp = new XMLHttpRequest();
xhttp.onreadystatechange = function () {
  if (this.readyState == 4 && this.status == 200) {
    // Action after successful response
  }
};
xhttp.open("GET", "url_of_server_api", true);
xhttp.send();
```

Yahan `url_of_server_api` server-side code ka URL hota hai jismein api end-point diya hota hai. Is API endpoint se data fetch karne ke liye `GET` method ka use kiya jata hai.

Ummid hai aap samajh gaye honge!

### API

API stands for "Application Programming Interface," which is essentially a set of rules and protocols that allow software programs to communicate with each other. In the context of JavaScript, an API can refer to a variety of things, including browser APIs (which allow JavaScript to interact with web page elements), third-party APIs (which allow developers to access data or functionality provided by external services), and server-side APIs (which allow client-side JavaScript to communicate with backend servers).

Let me give you an example to understand it better. Suppose you want to display the weather on your website. You could write code to scrape weather data from various websites, but that would be time-consuming and unreliable. Alternatively, you could use a weather API, which provides a standardized way to access weather data from a reliable source.

Here's a simple example of how you might use a weather API in JavaScript:

```javascript
fetch(
  "https://api.openweathermap.org/data/2.5/weather?q=London&appid=<your-api-key>"
)
  .then((response) => response.json())
  .then((data) => {
    const temperature = data.main.temp - 273.15;
    const description = data.weather[0].description;
    console.log(
      `The temperature in London is ${temperature}°C and the weather is ${description}.`
    );
  })
  .catch((error) => {
    console.error("Error fetching weather data:", error);
  });
```

In this code, we're using the `fetch` function (which is part of the browser's built-in `window` object) to make a request to the OpenWeatherMap API, passing in our API key and the city we want to get weather data for (`London`). The API will respond with a JSON object containing weather data for that location, which we can parse and use to display information to the user.

I hope this helps you understand what an API is in JavaScript!

### XMLHttpRequest

XMLHttpRequest ek JavaScript object hai jo web pages ko dynamic banane ke liye istemal hota hai. Iska istemal server ki taraf se data lene aur bhejne ke liye kiya jata hai, bina page ko refresh kiye.

Ismein JavaScript code se kuch data ko server se mangwa kar use web page mein dikhaya ja sakta hai. Iske liye humein XMLHttpRequest ka object create karna hota hai aur uske baad request ko send kar dena hota hai. Jab server se request complete ho jaati hai to hum uska response receive kar sakte hain aur use web page mein show karva sakte hain.

Example:

```
// XMLHttpRequest object create karein
var xmlhttp = new XMLHttpRequest();

// Request URL set karein
xmlhttp.open("GET", "https://api.example.com/data", true);

// Response aane par function ko call karein
xmlhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    document.getElementById("data").innerHTML = this.responseText;
  }
};

// Request ko server tak send karein
xmlhttp.send();
```

Iss example mein humne XMLHttpRequest ka object create kiya aur server se data mangne ke liye request bheji. Agar response successful aayega to `onreadystatechange` function call hoga jismein humne response data ko `data` id wale HTML element mein show kiya hai.

### How the web works

Web JavaScript mein kaise kaam karta hai? Example ke saath detail mein samjhao.

Web ko Javascript se chalane ke liye, humein client-side programming ki zaroorat hoti hai. Client-side programming ka matlab hai ki humare code ko user ke browser mein execute kiya jaata hai aur uske dwara hi website ki functionality provide ki jaati hai.

Jab user browser par kisi website ka URL enter karta hai toh browser server se request bhejta hai aur server response mein HTML, CSS aur Javascript files bhejta hai. Yeh sabhi files browser ke taraf se download ho jaate hai aur phir HTML file ke andar CSS aur Javascript files ko link kiya jaata hai.

Javascript ka use karke hum apne HTML page ko interactive bana sakte hain. Jaise ki hum apne webpage par buttons, forms, animations, navigation menus add kar sakte hain. Javascript mein DOM (Document Object Model) ka use hota hai. Isse hum apne webpage ke elements ko manipulate kar sakte hain aur unke saath interact kar sakte hain.

Example ke liye, agar humein ek button par click karne par background color change karna hai, toh hum Javascript ka use kar sakte hain. Iske liye hum HTML file mein button tag create karenge aur usmein onclick event add karenge. Jab user button par click karega toh onclick event trigger hoga aur Javascript code run hoga. Javascript code mein hum DOM ka use karke background color ko change karenge.

HTML:

```
<button onclick="changeColor()">Click me</button>
```

Javascript:

```
function changeColor() {
  document.body.style.backgroundColor = "blue";
}
```

Iss example mein, jab user button par click karega toh changeColor function call hoga. Iss function mein hum DOM ka use karke page ke background color ko blue kar rahe hain.

Aise hi Javascript ka use karke hum apne webpage ko aur bhi interactive bana sakte hain.

### Server

Server ek computer program hai jo internet par chalta hai aur client ko data provide karta hai. JavaScript mein bhi server-side programming kiya ja sakta hai. Server-side programming ke liye Node.js ka use kiya jata hai.

Node.js ek open-source, cross-platform, server-side JavaScript runtime environment hai. Iska use JavaScript code ko server-side execute karne ke liye kiya ja sakta hai. Node.js mein server banane ke liye `http` module ka use kiya jata hai.

Neeche diye gaye example mein, hum ek simple Node.js server banayenge jo `Hello World` message ko dikhata hai:

```javascript
const http = require("http");

const server = http.createServer((req, res) => {
  res.writeHead(200, { "Content-Type": "text/plain" });
  res.end("Hello World\n");
});

server.listen(3000, () => {
  console.log("Server listening on port 3000");
});
```

Is example mein, `http` module ko `require` karke server variable mein store kiya gaya hai. Fir, `createServer()` function se ek naya server create kiya gaya hai. Ye function ek callback function accept karta hai jiske parameters `request` object (client request) aur `response` object (server response) hote hain. Callback function mein `writeHead()` function se HTTP header set kiya gaya hai aur `end()` function se response body (yahaan `Hello World`) ko send kiya gaya hai.

Finally, `listen()` function se server ko specified port number (yahaan 3000) par start kiya gaya hai. Jab ye chalne lagta hai to command prompt mein "Server listening on port 3000" message show hota hai.

Is tarah se, JavaScript mein server-side programming ka use karke hum web applications ko bana sakte hain.

### Client

Client in JavaScript refers to the part of a web application that runs in a user's web browser. It can be thought of as the user-facing side of the application, responsible for displaying content and handling user interactions.

For example, let's say you visit a website like Facebook. When you open the website in your browser, the client-side code written in JavaScript is executed on your computer, rendering the webpage and allowing you to interact with it.

In Hinglish language:
Javascript me Client ka matlab hota hai wo hissa jiska istemal user apne web browser me karta hai. Ye uss web application ka wo hissa hai jo user ko dikhta hai aur jisme wo interact karta hai. Jaise ki agar hum Facebook jaisi website kholein to jab hum usse apne browser me kholte hain, to Client-side me likha JavaScript code humare computer par chalta hai jo webpage ko render karta hai aur hum usme interact kar sakte hain.

### Request ?

Request JavaScript mein ek tarika hai jiske dwara hum server se data ya resources ko retrieve kar sakte hai. Iske liye hum XMLHttpRequest (XHR) object ka upyog karte hai.

Jab hum kisi webpage par jaate hai, toh hum essentially ek request bhejte hai server ko us webpage ke saath related resources haasil karne ke liye, jaise ki images, CSS files, aur scripts. Jab server request ko poore tarike se process kar leta hai, toh woh response send karta hai client tak. Request object XHR object ke madhyam se banaya jata hai aur iska upyog hum asynchronous HTTP (AJAX) requests ke liye karte hai.

Ek example ke tor par, aap kisi API se data retrieve karna chahte hai, jaise ki OpenWeatherMap API jo current weather data provide karta hai. Aap ek GET request bhejte hai server ko, jismein endpoint URL aur API key hote hai. Server aapki request ko process karta hai aur JSON format mein weather data return karta hai.

Neeche diye gaye code snippet mein ek example diya gaya hai jismein XHR object ka upyog kiya ja raha hai ek GET request bhejne ke liye OpenWeatherMap API ko:

```
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.openweathermap.org/data/2.5/weather?q=London&appid=yourAPIkey', true);
xhr.onload = function() {
  if (this.status === 200) {
    console.log(JSON.parse(this.response));
  }
};
xhr.send();
```

Is code mein, `new XMLHttpRequest()` se ek naya XHR object banaya gaya hai. `xhr.open()` mein, humne GET request ke liye endpoint URL aur API key provide kiya hai, aur `xhr.onload()` mein humne response ko handle kiya hai - yahaan par, hum log console mein return kiya hai JSON response. Finally, `xhr.send()` se request send kiya gaya hai server tak.

### Response ?

Response ek JavaScript object hota hai jo HTTP requests ke response ko represent karta hai. Ye object server se received data, headers aur status codes ko store karta hai.

Jab hum JavaScript se kisi HTTP request ko bhejte hai, server uss request ka response bhejta hai. Iss response mei bohot saare information hote hai jaise ki response ka status code (200, 404 etc.), content type (text, JSON, HTML), cookies, headers (cache-control, content-length etc.) aur actual data.

Iss response ko handle karne ke liye hum Response object ka use karte hai. Iss object mei hum response ka data access kar sakte hai aur uska use apni application mei kar sakte hai.

Example ke taur par, agar hum ek GET request bhej rahe hai to hum "fetch" API ka use kar sakte hai. Iske baad hum response ko handle karne ke liye "then()" method ka use kar sakte hai.

Jaise ki:

```javascript
fetch("https://example.com/data")
  .then((response) => {
    console.log(response.status);
    console.log(response.headers.get("content-type"));
    return response.json();
  })
  .then((data) => console.log(data))
  .catch((error) => console.error(error));
```

Iss example mei, hum server se data fetch karte hai. Phir hum response ke status code aur headers ko console mei print karte hai. Uske baad hum response ka JSON data access karke console mei print karte hai.

Iss tarah se hum Response object ka use karke server se received data ko access aur manipulate kar sakte hai aur iss data ko apni application mei use kar sakte hai.

### Callback ?

Callback JavaScript mein ek function hai jo dusre function mein pass kiya jaata hai. Jab woh function complete ho jaata hai, toh callback function execute hota hai. Ye ek common programming concept hai jo JavaScript mein bahut use hota hai.

For example, suppose aap ek image download karna chahte hain aur jab wo download ho jaye toh uske baad kuch aur kaam karna chahte hain. Toh aap ek function bana sakte hain jismein image download karne ka code hai aur ek callback function pass kar sakte hain. Jab image download ho jaaye, toh callback function execute hoga aur aap apna agla kaam kar sakte hain.

Ek or example dekhte hian:

```
function getDataFromServer(url, callback) {
  // server se data fetch karne ka code
  // ...
  // jab data aa jaye toh callback function ko call karein
  callback(data);
}

// function call with callback function
getDataFromServer('https://example.com/data', function(data){
    console.log(data); // fetched data
    // do something with fetched data
});
```

Ismein `getDataFromServer()` function mein humne `callback` parameter pass kiya hai. Jab server se data fetch ho jata hai, toh `callback()` function ko call ho jata hai aur uss function mein hum fetched data ko use kar sakte hain.

Aap is concept ko apne project mein bhi use kar sakte hain. Isse aap apne code ko modular and reusable bana sakte hain.

### Promise and Fetch API ?

Promise aur Fetch API dono JavaScript ke important concepts hain jo web development mein kaafi use kiye jaate hain.

Promise ek aisa object hota hai jo async operations ko handle karne ke liye use kiya jaata hai. Jab hum kisi async operation jaise ki network request ya file reading ko perform karte hain, to uska result humein future mein milta hai. Promise humein ek reference deta hai future result ke liye, jisse hum uske liye wait kar sakte hain aur jab result available ho jaaye, hum usko handle kar sakte hain.

Example:

```
const myPromise = new Promise((resolve, reject) => {
  // async operation (e.g., network request)
  const result = performAsyncOperation();

  if (result) {
    resolve(result); // promise resolved with result
  } else {
    reject('Error occurred'); // promise rejected with error
  }
});

myPromise
  .then((result) => console.log(result))
  .catch((error) => console.error(error));
```

Yahan humne `new Promise()` ka use kiya hai ek async operation ko perform karne ke liye. Agar async operation successful raha, to hum `resolve()` method se promise ko resolve karte hain aur agar koi error aata hai to `reject()` method se promise ko reject karte hain. Phir humne `.then()` method ka use kiya hai resolve value ko handle karne ke liye aur `.catch()` method ka use kiya hai error ko handle karne ke liye.

Fetch API ek Web API hai jo client-side se server-side data retrieve karne ke liye use kiya jaata hai. Ye XMLHttpRequest (XHR) ke alternative ke roop mein introduce kiya gaya hai. Fetch API promises based hai, jisse aap async operations ko easily handle kar sakte hain.

Example:

```
fetch('https://api.example.com/data')
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error(error));
```

Yahan humne `fetch()` method ka use kiya hai server-side se data retrieve karne ke liye. Fir humne `.then()` method ka use kiya hai response ko parse karne ke liye aur `.catch()` method ka use kiya hai error ko handle karne ke liye.

### Consuming Promises ?

Promises in JavaScript are a way to handle asynchronous operations, such as fetching data from an API or reading from a file. When you create a Promise, it can be in one of three states: pending, fulfilled, or rejected.

Consuming Promises refers to the process of handling the result of a Promise after it has been fulfilled or rejected. This involves using the `.then()` method to handle successful cases and the `.catch()` method to handle errors.

For example, let's say we want to fetch data from an API using the `fetch()` function which returns a Promise. We can consume the Promise like this:

```javascript
fetch("https://jsonplaceholder.typicode.com/todos/1")
  .then((response) => response.json()) // Handle successful case
  .then((data) => console.log(data)) // Handle successful case
  .catch((error) => console.error(error)); // Handle error case
```

In this example, we first call the `fetch()` function with the URL of the API endpoint. This returns a Promise that resolves to a Response object. We then use the `.json()` method on the Response object to extract the JSON data from the response, which also returns a Promise. We chain another `.then()` method to handle the successful case and log the data to the console. Finally, we add a `.catch()` method to handle any errors that may occur during the process.

In Hinglish language, Consuming Promises ka matlab hai ki jab ham async operations ko handle karte hai jaise ki APIs se data fetch karna ya files se read karna, to hamein Promise ke result ko handle karna hota hai. Isme `.then()` method ko use karke hum successful cases ko handle karte hai aur `.catch()` method ko use karke errors ko handle karte hai. Ye process Promise ko consume karna kehlata hai.

### Chaining Promises ?

Chaining Promises in JavaScript is a technique where you can connect multiple Promise objects together to execute one after the other in a sequence.

Consider an example where you want to fetch some data from a server using an API call. The API call returns a Promise object that resolves with the response data. Now, after receiving the data, you want to perform some operation on it, say filter or map, which also returns a Promise object. Finally, you want to display the processed data on the UI.

Here's how you can chain these promises together:

```
fetch('https://example.com/data')
  .then(response => response.json())
  .then(data => data.filter(item => item.price > 10))
  .then(filteredData => {
    // Display the filtered data on the UI
  })
  .catch(error => {
    // Handle any errors
  });
```

In the above code, the `fetch()` method returns a Promise object that resolves with the response data. We then use the `.then()` method to parse the JSON data returned by the response.

We then chain another `.then()` method to filter the data based on our condition. The result of this operation is then passed to the next `.then()` method, which displays the processed data on the UI.

If any error occurs during the execution of the promises, the `.catch()` method is used to handle the error.

Hope this helps!

### Handling Rejected Promises ?

Rejected Promises in JavaScript are a way for asynchronous code to report errors or failures. When a Promise is rejected, it means that an error has occurred and the result of the operation is not available.

Handling Rejected Promises involves catching the error or failure and taking appropriate action. This can be done using the `catch` method on the Promise object or by passing a second argument to the `then` method.

Here's an example:

```
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    reject(new Error('Something went wrong!'))
  }, 1000)
})

promise.catch(error => {
  console.error(error.message)
})
```

In this example, we create a Promise that will be rejected after a delay of one second using the `reject` function. We then use the `catch` method to handle the rejection by logging the error message to the console.

Another way to handle rejected Promises is by chaining a `then` method with a second argument which is a function that handles the error.

```
promise.then(null, error => {
  console.error(error.message)
})
```

This achieves the same result as the previous example.

Handling Rejected Promises means dealing with cases when things go wrong while executing asynchronous operations in JavaScript. We can catch these errors using the `catch` method on the Promise object or by passing a second argument to the `then` method. It's important to handle these errors properly so that we can take appropriate action and prevent our code from crashing.

### explain Asynchronous Behind the Scene: The Event Loop in javascript ?

JavaScript is a popular programming language that is used in web development. It is a single-threaded language, which means it can only execute one task at a time. However, JavaScript has a feature called the "event loop" that allows it to handle asynchronous code.

Asynchronous code is code that does not run synchronously or in a predictable order. For example, when making an HTTP request to a server, the response may take some time to arrive. In the meantime, the JavaScript code should continue to run without waiting for the response. The event loop helps to handle this type of asynchronous code.

The event loop is a mechanism that allows JavaScript to handle asynchronous tasks by continuously checking if there are any pending tasks in the event queue. If there are any tasks, it will pick them up and execute them one by one. Once a task is completed, it moves on to the next task in the queue.

Here's an example: Suppose you have a JavaScript function that makes an HTTP request:

```
function makeRequest() {
  fetch('https://example.com/data')
    .then(response => response.json())
    .then(data => console.log(data))
}
```

When this function is called, it makes an HTTP request to `https://example.com/data` and retrieves some data. However, since this is an asynchronous operation, the JavaScript code will continue to run while waiting for the response.

The event loop comes into play here. While waiting for the response, the JavaScript engine can perform other tasks instead of blocking the thread. Once the response arrives, the event loop will pick it up from the event queue and execute the code inside the `then` block, logging the returned data to the console.

JavaScript ek single-threaded programming language hai jo ki sirf ek kaam ko ek saath karta hai. Lekin JavaScript mein "event loop" naam ka ek feature hai jo asynchronous code ko handle karne mein madad karta hai.

Asynchronous code wo hota hai jo syncronously nahi chalta ya phir ek predictable order mein nahi chalta. Jaise ki HTTP request bhejne par server se uska response aane mein time lag sakta hai. Is beech mein, JavaScript code ko response ka wait karne ke bina execute karna chahiye. Event loop asynchronous code ko handle karne mein madad karta hai.

Event loop ek mechanism hai jo JavaScript ko continuously check karta hai ki koi pending tasks event queue mein hai ya nahi. Agar koi task hai to wah use pick up karta hai aur ek-ek karke execute karta hai. Task complete hone ke baad, wah next task mein move karta hai.

Ek example ke roop mein dekha jaye: Maan lijiye ki aapke paas ek JavaScript function hai jo HTTP request bhejta hai:

```
function makeRequest() {
  fetch('https://example.com/data')
    .then(response => response.json())
    .then(data => console.log(data))
}
```

Is function ko call karne par, yah `https://example.com/data` par HTTP request bhejta hai aur kuch data retrieve karta hai. Lekin, kyunki ye asynchronous operation hai, JavaScript code response ka wait karte hue bhi run karna shuru karta hai.

Yahaan event loop kaam mein aata hai. Response ka wait karte hue, JavaScript engine thread ko block nahi hone deta aur instead mein dusre tasks perform kar sakta hai. Jab response aata hai, event loop wah event queue se ise pick up karta hai aur `then` block ke andar return hua data ko console pe log karta hai.

### Building a Simple Promise in javascript ?

Promise ka use JavaScript mein asynchronous code ko handle karne ke liye kiya jata hai. Jab hum kisi task ko async tarike se execute karte hain, to uski output aane mein der lagti hai aur tab tak humare code ke execution process par wait karna padta hai.

Promise ka use karke hum async task ka output ek promise object mein store kar sakte hain, jiske baad hum usko resolve ya reject kar sakte hain. Promise mein do states hote hain - resolved aur rejected.

Ek simple example ke through Promise ko samjhate hain:

```
// Ek function banayein jo 2 numbers ka sum return kare
function addNumbers(num1, num2) {
  // Promise object create karein
  const promise = new Promise((resolve, reject) => {
    // Sum calculate karenge
    const sum = num1 + num2;

    // Agar sum 50 se bada hai to resolve karein
    if (sum > 50) {
      resolve(sum);
    } else {
      // Agar sum 50 se chota hai to reject karein
      reject("Sum is less than 50");
    }
  });

  // Promise object return karein
  return promise;
}

// Function call karein aur sum print karein
addNumbers(30, 25)
  .then((result) => console.log(result)) // Output: 55
  .catch((error) => console.log(error));

addNumbers(10, 20)
  .then((result) => console.log(result)) // Output: Error message "Sum is less than 50"
  .catch((error) => console.log(error));
```

Is example mein humne `addNumbers()` naam ka ek function banaya hai, jismein humne do numbers liye aur unka sum calculate kiya. Agar sum 50 se bada hai to usko resolve kiya, warna reject kiya.

`Promise` object ke through humne function ka output ko handle kiya hai. `addNumbers()` function mein promise object create kiya gaya hai, jismein humne resolve ya reject function ko call kiya. Promise object return karne ke baad humne use `.then()` aur `.catch()` methods se access kiya hai.

`.then()` method ka use humne tab kiya hai jab promise object resolved ho gaya tha. Is case mein, humne `console.log(result)` kiya, jiske output mein sum print hua.

Isi tarah, `.catch()` method ka use humne tab kiya hai jab promise object rejected ho gaya tha. Is case mein, humne `console.log(error)` kiya, jiske output mein error message print hua.

Yeh ek basic example tha. Promise ko aur bhi depth mein jaane ke liye aur examples ke saath practice karna chahiye.

### Consuming Promise with Async/Await in javascript ?

Async/Await is a feature in JavaScript that allows developers to write asynchronous code in a synchronous fashion. It makes use of the Promise object to handle the asynchronous operations.

Let's first understand what a Promise is. In simple terms, a Promise is an object representing the eventual completion or failure of an asynchronous operation and its resulting value.

Now, suppose you have a function that returns a Promise object. To consume this promise using Async/Await, first, you need to mark your current function as async using the `async` keyword. Then, within this function, you can use the `await` keyword before calling the function that returns the Promise object. This will pause the execution of the function until the Promise is resolved or rejected. Once resolved, you can get the result of the Promise using the `.then()` method. If the Promise is rejected, you can catch the error using the `.catch()` method.

Here's an example:

```javascript
// Function that returns a Promise object
function getData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Data received"); // Resolves after 2 seconds
    }, 2000);
  });
}

// Consume Promise using Async/Await
async function processData() {
  try {
    const result = await getData();
    console.log(result); // Logs 'Data received' after 2 seconds
  } catch (error) {
    console.error(error);
  }
}

processData(); // Calls processData function
```

In this example, the `getData()` function returns a Promise object that resolves after 2 seconds with the string `'Data received'`. The `processData()` function is marked as async and uses the `await` keyword to pause the execution until the Promise returned by `getData()` is resolved. Once resolved, the result is logged to the console. If an error occurs, it is caught using the `catch()` method.

I hope this explanation helps you understand how to consume Promise with Async/Await in JavaScript. If you have any further queries, feel free to ask!

### Error Handling with Try catch in javascript ?

Try-Catch statement is used in JavaScript to handle runtime errors that may occur during the execution of a code block. The basic idea is to try and execute a block of code, if it throws an error, catch that error and handle it gracefully without stopping the execution of the entire program.

Here's an example of how to use Try-Catch statement in JavaScript:

```javascript
try {
  // Block of code that may throw an error
  let num = "hello";
  console.log(num + 5);
} catch (error) {
  // Handle the error
  console.log("An error occurred: " + error.message);
}
```

In this example, the `try` block attempts to concatenate a string with a number. Since `num` is not a valid number, this operation will throw a TypeError. However, instead of crashing the program, the error is caught by the `catch` block and handled gracefully. The error message is printed to the console, indicating that an error occurred.

The Hinglish equivalent of this code would look something like this:

```javascript
koshishKaro {
  // Kode ka ek block, jo ki kisi galati ko utpann kar sakta hai
  let num = "hello";
  console.log(num + 5);
} pakdoPakadao(error) {
  // Galati ko sambhalo
  console.log("Ek galati aayi hai: " + error.message);
}
```

code, `koshishKaro` corresponds to the `try` keyword, while `pakdoPakadao` corresponds to `catch`. The rest of the code is similar to the original JavaScript example. Keep in mind that this is just for illustrative purposes and using proper English keywords is generally recommended for better code readability and maintainability.

### Returning values from Async functions in javascript ?

Async functions in JavaScript are special functions that allow you to write asynchronous code using the `async` and `await` keywords. These functions always return a promise, which can be resolved with the value returned by the function.

For example, let's say we have an async function called `getAlbums()` that fetches a list of albums from an API:

```javascript
async function getAlbums() {
  const response = await fetch("https://example.com/api/albums");
  const data = await response.json();
  return data;
}
```

In this function, we use the `await` keyword to wait for the response from the API before parsing its JSON data. Finally, we return the parsed data from the function.

To use this function and get the data it returns, we can call it and use the `then()` method to handle the promise:

```javascript
getAlbums().then((data) => {
  console.log(data);
});
```

In Hinglish language:

Async functions JavaScript mein kuchh aise functions hain jo `async` aur `await` shabdon ka upayog karke aysnchronous code likhne ki suvidha dete hain. Ye functions hamesha ek promise ko vapas karte hain, jise function se vapas kiya gaya value resolve kar sakta hai.

Jaise ki, maan lo hamare paas ek async function hai jiska naam hai `getAlbums()` jo ek API se albums ki ek list laata hai:

```javascript
async function getAlbums() {
  const response = await fetch("https://example.com/api/albums");
  const data = await response.json();
  return data;
}
```

Is function mein hum `await` keyword ka upayog karke API se response ka intezaar karte hain, uske baad iske JSON data ko parse karte hain aur ant mein function se parse kiya gaya data vapas karte hain.

Is function ka upayog karne ke liye aur isse vapas kiya gaya data prapt karne ke liye, hum ise call kar sakte hain aur `then()` method ka upayog karke promise handle kar sakte hain:

```javascript
getAlbums().then((data) => {
  console.log(data);
});
```

### Running promises in Parallel in javascript ?

JavaScript promises are used to handle asynchronous operations in a more readable and maintainable way. Running promises in parallel means executing multiple promises simultaneously, without waiting for one promise to resolve before starting the next one.

Let's consider an example where we need to fetch data from three different APIs and then process the results:

```
const fetchAPI1 = () => {
  return fetch('https://api.example.com/data1')
    .then(response => response.json())
}

const fetchAPI2 = () => {
  return fetch('https://api.example.com/data2')
    .then(response => response.json())
}

const fetchAPI3 = () => {
  return fetch('https://api.example.com/data3')
    .then(response => response.json())
}

Promise.all([fetchAPI1(), fetchAPI2(), fetchAPI3()])
  .then(([data1, data2, data3]) => {
    // Process results
  })
  .catch(error => {
    // Handle errors
  })
```

In this example, we define three separate functions to fetch data from different APIs using the `fetch` function, which returns a Promise that resolves with the JSON response. We then use `Promise.all()` to execute all three promises in parallel and wait for all of them to resolve. The `Promise.all()` method takes an array of promises and returns a new Promise that resolves with an array of results when all the promises have resolved.

Once all promises are resolved, we can access the results in the `.then()` callback. The results will be passed as an array in the order that the promises were passed to `Promise.all()`.

To summarize, running promises in parallel allows us to perform multiple asynchronous tasks at the same time, which can significantly improve performance in applications that rely heavily on network requests or other long-running operations.

### Promise Combinators: race, allSettled and any in javascript ?

Promise Combinators in JavaScript are helper functions that allow developers to work with promises more efficiently. Three commonly used Promise Combinators are - `Promise.race`, `Promise.allSettled`, and `Promise.any`.

1. `Promise.race`: It accepts an array of Promises, and it returns a new Promise that resolves or rejects as soon as one of the promises in the array resolves or rejects.

Example: Suppose you want to get data from two APIs, and you only need the data from the API that responds first. You can use `Promise.race` to achieve this:

```javascript
const promise1 = fetch("https://api.example.com/data1");
const promise2 = fetch("https://api.example.com/data2");

Promise.race([promise1, promise2])
  .then((result) => {
    console.log(result);
  })
  .catch((error) => {
    console.error(error);
  });
```

In this example, we have two fetch requests that return Promises. We pass both of these promises to `Promise.race`. The `then` method is called when one of the promises is resolved. If either of the promises is rejected, the `catch` method will be called.

2. `Promise.allSettled`: It accepts an array of Promises, and it returns a new Promise that resolves after all the Promises in the array have settled (either fulfilled or rejected). The resolution value is an array of objects that describe the outcome of each Promise.

Example: Suppose you want to make multiple API requests, and you want to know the status of each request after it has completed. You can use `Promise.allSettled` to achieve this:

```javascript
const promise1 = fetch("https://api.example.com/data1");
const promise2 = fetch("https://api.example.com/data2");
const promise3 = fetch("https://api.example.com/data3");

Promise.allSettled([promise1, promise2, promise3])
  .then((results) => {
    results.forEach((result) => {
      console.log(result.status, result.value);
    });
  })
  .catch((error) => {
    console.error(error);
  });
```

In this example, we have three fetch requests that return Promises. We pass all these promises to `Promise.allSettled`. The `then` method is called after all the Promises have settled. It loops through the array of objects and logs the status and value of each Promise.

3. `Promise.any`: It accepts an array of Promises, and it returns a new Promise that resolves as soon as one of the Promises in the array fulfills. If all the promises are rejected, then it rejects with an AggregateError containing an array of rejection reasons.

Example: Suppose you want to make multiple API requests, and you only need the data from the first successful request. You can use `Promise.any` to achieve this:

```javascript
const promise1 = fetch("https://api.example.com/data1");
const promise2 = fetch("https://api.example.com/data2");

Promise.any([promise1, promise2])
  .then((result) => {
    console.log(result);
  })
  .catch((error) => {
    console.error(error);
  });
```

In this example, we have two fetch requests that return Promises. We pass both of these promises to `Promise.any`. The `then` method is called when one of the promises is fulfilled. If all the promises are rejected, the `catch` method will be called with an AggregateError containing an array of rejection reasons.

To summarize, Promise Combinators (`Promise.race`, `Promise.allSettled`, and `Promise.any`) provide useful abstractions for working with Promises in JavaScript. They allow developers to write cleaner and more concise code while also improving the overall reliability of their applications.
### what is Consuming Promise with Async/Await

JavaScript mein Promise ek aisa feature hai jo asynchronous code ko manage karne ke liye istemal kiya jata hai. Async/Await keywords bhi ismein shamil hote hain, jo humein ek easier way provide karte hain promises ko consume karne ke liye.

Async/Await ka use Promises ko consume karne ke liye hota hai. Asynchronous code ke liye Promises kaafi useful hote hain, aur ismein Async/Await ka use humein code ko cleaner aur readable banane mein help karta hai.

Let's take an example:

```
function getUserDetails(userId) {
  return new Promise((resolve, reject) => {
    // simulate API call
    setTimeout(() => {
      const users = [
        { id: 1, name: 'John Doe', age: 25 },
        { id: 2, name: 'Jane Smith', age: 30 },
        { id: 3, name: 'Bob Johnson', age: 40 }
      ];
      const user = users.find(user => user.id === userId);
      if (user) {
        resolve(user);
      } else {
        reject('User not found');
      }
    }, 2000);
  });
}

async function printUserDetails(userId) {
  try {
    const userDetails = await getUserDetails(userId);
    console.log(`Name: ${userDetails.name}, Age: ${userDetails.age}`);
  } catch (error) {
    console.error(error);
  }
}

printUserDetails(2); // Output: Name: Jane Smith, Age: 30
```

Is example mein `getUserDetails` ek promise return karta hai, jo simulate kiya gaya hai ki ye ek API call hai. `printUserDetails` function mein hum async keyword ka use karte hain, aur getUserDetails function ko await ke saath call karte hain.

Jab hum getUserDetails function ko await ke saath call karte hain, to ye promise resolve karne tak wait karta hai. Jab promise resolve ho jaata hai, to userDetails variable mein uska data store hota hai. Iske baad hum console mein user details print karte hain.

Agar promise reject hua to catch block mein error message print hota hai.
### What is an API

Ek API (Application Programming Interface) JavaScript mein ek tarika hai jisse hum apne code ko dusre software ya websites se connect kar sakte hain. API ke dwara, hum kisi bhi remote server ki information ko access kar sakte hain aur usme input/output ka use karke data ko manipulate bhi kar sakte hain.

Ek example ke tor par, agar hum kisi weather website se real-time weather data fetch karna chahte hain to hum unke API ka use kar sakte hain. Aise me, hum ek HTTP request bhejte hain jo server tak pahuchta hai aur jisme JSON format mein weather data hota hai. Fir hum is data ko parse karke apne code mein use kar sakte hain.

JavaScript me, hum fetch() function ka use kar API se data fetch kar sakte hain. Jaise ki niche diya gaya hai:

```
fetch('https://api.weather.com/data/weather?location=NewYork&apikey=12345')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error))
```

Is code snippet mein hum 'https://api.weather.com' se weather data fetch kar rahe hain. Hum 'fetch()' function mein URL aur API key ka use kar rahe hain. Fir hum promise-based approach ka use karke response ko JSON format me parse kar rahe hain (`.json()`), aur fir console mein print kar rahe hain (`console.log(data)`). Agar koi error aata hai to hum `.catch()` block mein error handle karte hain.
### What is Polyfilling

Polyfilling in JavaScript is a technique used to add support for new features or functionality to older browsers that do not natively support them. Let me explain it in Hinglish:

Suppose aapne ek new bike li hai, aur usme kuch advanced features hai jaise ki digital speedometer, automatic headlight, etc. Lekin aapki friend ki bike mein ye sabhi features nahi hai, woh purani bike hai. Aise mein agar aap apni friend ko bataana chahte hai ki ye saare features aapki bike mein hai, toh aap unke bike mein ye sabhi features add kar sakte hai. Ye hi hota hai polyfilling.

Ab isko JavaScript mein translate karte hai. Suppose aapne ek new version of JavaScript use kiya hai aur isme kuch new functions aur methods aaye hai, lekin purane browsers mein ye functions aur methods support nahi karte. Toh aap polyfilling technique ka use karke un purane browsers ko upgrade kar sakte hai.

For example, let's say you want to use the `Array.prototype.includes()` method, which was introduced in ECMAScript 2016. However, this method is not supported by some older browsers like Internet Explorer. To make sure it works on these older browsers, you can use a polyfill like this:

```
if (!Array.prototype.includes) {
  Array.prototype.includes = function(searchElement /*, fromIndex*/) {
    'use strict';
    var O = Object(this);
    var len = parseInt(O.length) || 0;
    if (len === 0) {
      return false;
    }
    var n = parseInt(arguments[1]) || 0;
    var k;
    if (n >= 0) {
      k = n;
    } else {
      k = len + n;
      if (k < 0) {k = 0;}
    }
    while (k < len) {
      var currentElement = O[k];
      if (searchElement === currentElement ||
         (searchElement !== searchElement && currentElement !== currentElement)) {
        return true;
      }
      k++;
    }
    return false;
  };
}
```

This polyfill checks whether the `Array.prototype.includes()` method is already defined. If not, it defines the method using a custom implementation that provides similar functionality. Now you can use this method in your code without worrying about browser compatibility issues.
### what is Running promises in Parallel

JavaScript promises allow for asynchronous operations to be run without blocking the main thread. Running promises in parallel means running multiple promises simultaneously, without waiting for one to finish before starting the next one.

For example, let's say we have three functions that return promises: `fetchUserData()`, `fetchPostData()`, and `fetchCommentData()`. We want to fetch all three sets of data at the same time, instead of waiting for one to finish before starting the next.

To do this, we can use the `Promise.all()` method, which takes an array of promises as an argument and returns a single promise that resolves when all the promises in the array have resolved. Here's how it works:

```js
const userDataPromise = fetchUserData();
const postDataPromise = fetchPostData();
const commentDataPromise = fetchCommentData();

Promise.all([userDataPromise, postDataPromise, commentDataPromise])
  .then(([userData, postData, commentData]) => {
    // Do something with the fetched data
  })
  .catch((error) => {
    // Handle any errors that occurred during fetching
  });
```

In this example, we create three promises for fetching user data, post data, and comment data. Then we pass these promises as an array to `Promise.all()`. When all three promises have resolved, the `.then()` callback function is called with an array of the resolved data from each promise.

Note that if any of the promises passed to `Promise.all()` are rejected (i.e., their `.catch()` method is called), then the entire `Promise.all()` call will be rejected and skip straight to the `.catch()` function.

"parallel mein promises chalana" to mean "running promises in parallel". We can also say "ek saath kai promises ko chalana" to mean "running multiple promises simultaneously".
### what is Exporting and importing in ES6 Modules

ES6 modules are a way to organize and share code in JavaScript. Exporting and importing are the two main features of ES6 modules that allow you to share code between different files.

Exporting is the process of making variables, functions or objects available to other modules. To export a variable, function or object from a module, you can use the "export" keyword followed by the name of the variable, function or object.

For example, let's say we have a module named "utils.js" which contains a function named "addNumbers". We can export this function using the following syntax:

```js
// utils.js

export function addNumbers(a, b) {
  return a + b;
}
```

Now, we can import this function in another module using the "import" keyword.

Importing is the process of loading variables, functions or objects from another module into your own module. To import a variable, function or object from a module, you can use the "import" keyword followed by the name of the variable, function or object.

For example, let's say we have another module named "main.js" which wants to use the "addNumbers" function from the "utils.js" module. We can import this function using the following syntax:

```js
// main.js

import { addNumbers } from "./utils.js";

console.log(addNumbers(2, 3)); // Output: 5
```

In the above example, we're importing the "addNumbers" function from the "utils.js" module using curly braces {}. We also provide the path to the module we want to import from using the "./" notation.

Overall, exporting and importing in ES6 modules makes it easier to organize and share code across different files in your application.
### what is Top-Level await (ES2022)

Top-level await is a new feature that was introduced in ECMAScript 2022 (ES2022) which allows you to use the `await` keyword at the top level of your code, outside of an `async` function. This means that you can now use asynchronous code in the global scope without having to wrap it inside an IIFE or other workarounds.

For example, suppose you have an API call that you want to make at the start of your script:

```javascript
const response = await fetch("https://api.example.com/data");
const data = await response.json();
console.log(data);
```

Before top-level await, this code would have resulted in a syntax error because you cannot use the `await` keyword outside of an `async` function. To work around this, you would have had to wrap this code inside an IIFE or a function:

```javascript
(async function () {
  const response = await fetch("https://api.example.com/data");
  const data = await response.json();
  console.log(data);
})();
```

With top-level await, you can simply use `await` at the top level:

```javascript
const response = await fetch("https://api.example.com/data");
const data = await response.json();
console.log(data);
```

Note that for top-level await to work, you need to be using a module script (`<script type="module">`) or have enabled the `"module"` option in your `package.json` file. This is because top-level await is only allowed in modules, not in traditional scripts.
### what is Module Pattern

Module Pattern ek design pattern hai jise Javascript mein use kiya jaata hai. Is pattern mein, hum apne code ko module ke roop mein organise karte hain, taaki hamara code reusable ho aur code ki complexity kam ho.

Is pattern mein, hum apna code ek function ke andar likhte hain aur us function ka return value, hum module ke roop mein use karte hain. Isse, hum dusre files mein bhi apne code ko import kar sakte hain aur usko reuse kar sakte hain.

Ek example ke dwara samjhte hain:

// Module definition
var MyModule = (function() {
// Private variable
var myPrivateVar = "Hello World";

// Private function
function myPrivateFunc() {
console.log(myPrivateVar);
}

// Public API
return {
publicVar: "I am a public variable",
publicFunc: function() {
console.log("I am a public function");
},
invokePrivateFunc: function() {
myPrivateFunc();
}
};
})();

// Usage
console.log(MyModule.publicVar); // Output: "I am a public variable"
MyModule.publicFunc(); // Output: "I am a public function"
MyModule.invokePrivateFunc(); // Output: "Hello World"

Is example mein, hum ek self-invoking function ka use kiya hai jise hum MyModule variable mein store karte hain. Is function mein, hum private aur public variables aur functions define karte hain.

Private variable aur function directly access nahi kiye jaa sakte hai lekin public variable aur function ko access kiya jaa sakta hai.

yeh samjhaya ja sakta hai ki module pattern mein hum apna code function ke andar likhte hain aur us function ka return value, hum module ke roop mein use karte hain. Isse hamara code reusable aur organised hota hai.
### what is Bundling With Parcel and NPM Scripts

Bundling is the process of combining multiple files into a single file for optimized performance. In JavaScript, we often use bundling tools like Parcel and NPM Scripts to bundle our code.

Parcel is a zero configuration bundler that automatically handles many tasks such as bundling, minification, and optimization without any additional setup required. You can install Parcel using NPM by running the following command in your terminal:

```
npm install -g parcel-bundler
```

Once you have installed Parcel, you can create a new project directory and create an index.html file and an index.js file inside it. Your file structure should look like this:

```
project/
├── index.html
└── index.js
```

Inside your index.js file, you can write some basic JavaScript code:

```javascript
const greet = (name) => {
  console.log(`Hello ${name}!`);
};

greet("World");
```

To bundle this code using Parcel, you simply need to run the following command in your terminal:

```
parcel build index.js
```

This will create a new file called `dist/main.js` which contains your bundled code.

NPM Scripts is another popular tool used for bundling in JavaScript. With NPM Scripts, you can define custom scripts in your package.json file that can be used to run various tasks, including bundling. Here's an example of how you can use NPM Scripts to bundle your code:

First, you need to install some dependencies:

```
npm install --save-dev webpack webpack-cli babel-loader @babel/core @babel/preset-env
```

Next, you can add the following script to your package.json file:

```json
{
  "scripts": {
    "build": "webpack --mode production ./src/index.js --output ./dist/bundle.js"
  }
}
```

This script tells webpack to bundle your code in production mode and output the result to a file called `bundle.js` inside a directory called `dist`.

To run this script, you can simply execute the following command in your terminal:

```
npm run build
```

This will bundle your code using webpack and output the result to the specified location.

In Hinglish, bundling ek process hai jisme kai files ko combine kiya jata hai ek optimized performance ke liye. JavaScript mein, ham bundling tools jaise ki Parcel aur NPM Scripts ka use kar sakte hai apne code ko bundle karne ke liye. Parcel ek zero configuration bundler hai jo bundling, minification, optimization jaise tasks ko automatically handle karta hai bina kisi additional setup ke. Aap Parcel ko NPM se install kar sakte hai niche diye gaye command ka use karke:

```
npm install -g parcel-bundler
```

Parcel ko install karne ke baad, aap ek new project directory create kar sakte hai aur usmein ek index.html file aur ek index.js file create kar sakte hai. Aapka file structure isi tarah ka dikhega:

```
project/
├── index.html
└── index.js
```

Aapke index.js file mein, aap basic JavaScript code likh sakte hai:

```javascript
const greet = (name) => {
  console.log(`Hello ${name}!`);
};

greet("World");
```

Apne code ko Parcel ke jariye bundle karne ke liye, aapko terminal mein niche diye gaye command ko execute karna hoga:

```
parcel build index.js
```

Yeh aapka code bundle karke `dist/main.js` namak ek naya file create karega jismein aapka bundled code hoga.

NPM Scripts ek aur popular tool hai jo JavaScript mein bundling ke liye use kiya jata hai. NPM Scripts ke jariye, aap apne package.json file mein custom scripts define kar sakte hai jo ki bundling jaisi various tasks ko run karne ke liye use kiye ja sakte hai. Yahaan ek example diya gaya hai jisme aap NPM Scripts ka use karke apna code bundle kar sakte hai:

Sabse pehle, aapko kuch dependencies install karne hoge:

```
npm install --save-dev webpack webpack-cli babel-loader @babel/core @babel/preset-env
```

Next, aap apne package.json file mein niche diye gaye script ko add kar sakte hai:

```json
{
  "scripts": {
    "build": "webpack --mode production ./src/index.js --output ./dist/bundle.js"
  }
}
```

Is script mein, webpack ko bataya jata hai ki code ko production mode mein bundle karna hai aur result ko `dist` naamak directory mein `bundle.js`
### What is Babel

Babel ek JavaScript compiler hai jo aapki code ko modern JavaScript version se purane versions mein compile kar deta hai, taaki aapka code purane browsers aur environments mein bhi sahi tarike se chale.

Suppose aapko apna JavaScript code kisi naye feature jaise ki "template literals" ka istemaal karke likhna hai:

```javascript
const name = "Alice";
console.log(`Hello ${name}!`);
```

Parantu ye code purane browsers mein kaam nahi karega kyunki vo template literals feature support nahi karte hain. Iss scenario mein, Babel aapki code ko ECMAScript 5 (ES5) version mein compile kar dega, jo purane browsers ki standard version hai aur support karta hai:

```javascript
var name = "Alice";
console.log("Hello " + name + "!");
```

Babel ka upyog karne ke liye, sabse pehle aapko usse install karna hoga. Aap ye command use karke Babel ko apne project mein add kar sakte hain:

```
npm install --save-dev @babel/core @babel/cli @babel/preset-env
```

Phir aap apni code ko compile karne ke liye ye command use kar sakte hain:

```
npx babel script.js --out-file compiled.js
```

Iss example mein `script.js` aapka original JavaScript code file hai aur `compiled.js` aapka compiled code file hai.

Babel ke bahut sare plugins aur presets available hote hain jo aapki code ko specific requirements ke according customize kar sakte hain. For example, agar aap React.js ka upyog kar rahe hain to aap `@babel/preset-react` preset ka upyog kar sakte hain jo React.js ke specific requirements ko compile karta hai.
### what is Transpiling

Transpiling in JavaScript means converting code written in one version of the language (ES6 or higher) to an earlier version that can be executed by all browsers. This is done using a tool called a transpiler or compiler.

Transpiling is important because not all browsers support the latest version of JavaScript. By transpiling, developers can write modern code without worrying about browser compatibility issues.

For example, consider the arrow function syntax introduced in ES6:

```
const add = (a, b) => a + b;
```

This syntax is not supported in some older browsers like Internet Explorer. To make this code compatible with those browsers, we can use a transpiler like Babel to convert it to the equivalent ES5 code:

```
var add = function(a, b) {
  return a + b;
};
```

Here's an example in Hinglish:

Transpiling Javascript ka matlab hota hai ki ham modern javascript code ko older versions mein convert karte hain jo ki sabhi browsers ke dwara execute kiya ja sakta hai. Iske liye hum ek tool ka istemal karte hain jise transpiler ya compiler kaha jata hai.

Transpiling ka use isliye important hai kyunki sabhi browsers latest version of Javascript ko support nahi karte hain. Transpiling se developers modern code likh sakte hain bina browser compatibility issues ke dar ke.

Udharan ke taur par, ES6 mein introduce hue arrow function syntax ko dekhein:

```
const add = (a, b) => a + b;
```

Ye syntax kuch older browsers jaise Internet Explorer mein support nahi karta hai. Is code ko un browsers ke liye compatible banane ke liye, hum Babel jaise transpiler ka upyog kar sakte hain jo is code ko equivalent ES5 code mein convert kar dega:

```
var add = function(a, b) {
  return a + b;
};
```
### what is Returning values from Async functions

Async functions in JavaScript are special functions that allow asynchronous programming, which means the code within these functions can execute independently of the main program flow. One important feature of async functions is their ability to return values.

When an async function returns a value, it does so by wrapping the value in a Promise object. This Promise is returned immediately when the function is called, but its final value may not be available until some time later when the async operation completes.

Here's an example of how to define and call an async function that returns a value:

```
async function fetchData() {
  const response = await fetch('https://example.com/data.json');
  const data = await response.json();
  return data;
}

fetchData()
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

In this example, the `fetchData` function uses the `await` keyword to wait for the result of a network request before returning the value of `data`. When you call `fetchData`, it returns a Promise object that will eventually resolve to the actual value of `data`.

To get the final value of `data`, you can use the `then` method on the returned Promise, passing in a callback function that will be executed with the resolved value. You can also handle any errors that occur during the execution of the function by using the `catch` method.

Overall, async functions provide a powerful way to write asynchronous code in a more synchronous style, while still allowing you to work with Promises and handle errors effectively.
### what is Modules

Modules in JavaScript are a way to organize code into reusable, independent components. Each module can have its own state, functions, and variables that are not accessible from other modules unless explicitly exported.

For example, let's say you have two files: "math.js" and "main.js". In "math.js", you define some mathematical functions like add() and multiply(), and then export them using the keyword "export":

```
// math.js

function add(a, b) {
  return a + b;
}

function multiply(a, b) {
  return a * b;
}

export { add, multiply };
```

In "main.js", you can import these functions using the keyword "import":

```
// main.js

import { add, multiply } from './math.js';

console.log(add(2, 3)); // Output: 5
console.log(multiply(2, 3)); // Output: 6
```
### Hoisting

hoisting ka matlab hai ki, kisi bhi variable or function declaration ko uske scope ke top par move kar diya jata hai, jabki unhe originally code mein declare kiya gaya ho. Jaise ki agar humne ek variable ko declare kiya hai aur usse pehle hi use karne ki koshish kari hai, toohamare code mein error aa sakta hai. Lekin hoisting ke dwara, variable ki declaration yaad rakhi jaati hai aur execution time par, undefined value assign ki jaati hai. Yehi process function declarations ke liye bhi apply hota hai.

For example, let's say you have the following code:

```
console.log(x);
var x = 10;
```

Normally, this code would result in an error because `x` is undefined at the time it is being logged. However, due to hoisting, the variable declaration `var x` is moved to the top of its scope (in this case, the global scope), resulting in the following code:

```
var x;
console.log(x);
x = 10;
```

So when the code is actually executed, `x` has a value of `undefined`, which is what gets logged to the console.

Similarly, hoisting also applies to function declarations. For example:

```
foo();

function foo() {
  console.log("Hello world!");
}
```

In this case, the function declaration for `foo()` is moved to the top of its scope, resulting in the following code:

```
function foo() {
  console.log("Hello world!");
}

foo();
```
