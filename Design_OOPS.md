## **Object-Oriented Programming (OOPs) Kya Hai?**

OOP ek programming style hai jo "objects" par based hai. Ismein hum real-world cheezon (jaise car, person, bank account) ko code mein objects ke roop mein represent karte hain. Har object ke paas apna data (properties/attributes) aur behavior (methods/functions) hota hai.

**Analogy**: Ek car ke baare mein sochiye.

  * **Data/Properties**: Uska color, model, speed, fuel level.
  * **Behavior/Methods**: `start()`, `stop()`, `accelerate()`, `brake()`.

OOP in cheezon ko code mein manage karna aasan banata hai. Iske chaar main pillars (stambh) hain.

-----

## **1. Classes and Objects (Class aur Object)**

Yeh OOPs ke sabse basic building blocks hain.

### **Class**

Ek **class** object ke liye ek **blueprint** ya template hota hai. Yeh batata hai ki us type ke object mein kya-kya properties (variables) aur behaviors (methods) honge. Yeh memory mein jagah nahi leta.

**Analogy**: Ghar ka naksha (blueprint). Naksha sirf design batata hai, woh khud ek ghar nahi hai.

### **Object**

Ek **object** class ka ek **instance** hota hai. Yeh ek real entity hai jiske paas state (data) aur behavior (methods) hote hain. Jab aap ek object banate hain, tab memory allocate hoti hai.

**Analogy**: Blueprint (class) ko dekh kar banaya gaya asli ghar (object). Aap ek hi naksh-e se kai ghar bana sakte hain.

### **Java Code Example**

```java
// Yeh ek class hai - ek blueprint
class Dog {
    // Properties (Data)
    String breed;
    int age;
    String color;

    // Behavior (Method)
    void bark() {
        System.out.println("Woof Woof!");
    }

    void sleep() {
        System.out.println("Dog is sleeping...");
    }
}

public class Main {
    public static void main(String[] args) {
        // 'myDog' naam ka ek Dog object banaya gaya
        Dog myDog = new Dog(); // Class ka instance (Object)

        // Object ki properties set ki
        myDog.breed = "German Shepherd";
        myDog.age = 5;
        myDog.color = "Black";

        // Object ke methods ko call kiya
        System.out.println("My dog's age is: " + myDog.age);
        myDog.bark(); // Output: Woof Woof!
    }
}
```

-----

## **2. Constructors (Nirmaata)**

Constructor ek special method hai jo object banate samay automatically call hota hai. Iska kaam object ki initial values (state) set karna hota hai.

  * Constructor ka naam hamesha class ke naam jaisa hota hai.
  * Iska koi return type nahi hota, `void` bhi nahi.

### **Constructor Overloading**

Ek hi class mein ek se zyada constructor ho sakte hain, bas unke parameters alag-alag hone chahiye. Ise **Constructor Overloading** kehte hain.

### **Java Code Example**

```java
class Person {
    String name;
    int age;

    // 1. No-argument constructor
    Person() {
        this.name = "Unknown";
        this.age = 0;
        System.out.println("Ek Person object bina naam aur age ke banaya gaya.");
    }

    // 2. Parameterized constructor (Overloading)
    Person(String name, int age) {
        this.name = name;
        this.age = age;
        System.out.println("Ek Person object naam aur age ke saath banaya gaya.");
    }

    void introduce() {
        System.out.println("Hello, my name is " + this.name + " and I am " + this.age + " years old.");
    }
}

public class Main {
    public static void main(String[] args) {
        // Pehla constructor call hoga
        Person person1 = new Person();
        person1.introduce(); // Output: Hello, my name is Unknown...

        System.out.println("---");

        // Doosra constructor call hoga
        Person person2 = new Person("Anjali", 25);
        person2.introduce(); // Output: Hello, my name is Anjali...
    }
}
```

**Note**: Java mein C++ ki tarah destructors nahi hote. Java mein **Garbage Collector** hota hai jo un-used objects ko memory se automatically hata deta hai.

-----

## **3. Encapsulation (Data Bandhan)**

Encapsulation ka matlab hai data (variables) aur us data par kaam karne wale methods ko ek saath ek single unit (class) mein baandh dena. Ismein data ko `private` banakar hide kiya jaata hai aur use sirf `public` methods (getters and setters) ke zariye hi access karne ki anumati di jaati hai.

**Kyun Zaroori Hai?**: Isse data par control rehta hai aur bahar ka koi bhi code use direct change nahi kar sakta. Ise **Data Hiding** bhi kehte hain.

**Analogy**: Ek medical capsule. Dawa (data) capsule ke andar safe rehti hai (`private`). Aapko use khane ke liye poora capsule (public methods) istemal karna padta hai. Aap direct dawa ko nahi chhedte.

### **Java Code Example**

```java
class BankAccount {
    // Data ko private rakha gaya hai
    private double balance;

    // Public method to deposit money
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposit successful. New balance: " + balance);
        } else {
            System.out.println("Invalid amount.");
        }
    }

    // Public method to get balance (Getter)
    public double getBalance() {
        return balance;
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount myAccount = new BankAccount();
        // myAccount.balance = -1000; // Error! Kyunki balance private hai. Direct access nahi kar sakte.

        myAccount.deposit(5000); // Sahi tarika
        System.out.println("Current Balance: " + myAccount.getBalance());
    }
}
```

-----

## **4. Abstraction (Vivaran Chhipana)**

Abstraction ka matlab hai zaroori cheezein dikhana aur unki implementation details (woh kaam kaise kar rahi hain) ko chhipana. Yeh complexity ko kam karta hai.

**Kyun Zaroori Hai?**: User ko sirf yeh jaanna hota hai ki *kya karna hai*, yeh nahi ki *kaise karna hai*.

**Analogy**: TV ka remote. Aap volume badhane ke liye `Volume+` button dabate hain. Aapko ye jaanne ki zaroorat nahi ki button dabane se andar kaunsa circuit kaam karta hai. Aapko sirf functionality se matlab hai.

Java mein abstraction **Abstract Classes** aur **Interfaces** ke through achieve kiya jaata hai.

### **Java Code Example (Using Abstract Class)**

```java
// Abstract class - iska object nahi ban sakta
abstract class Shape {
    // Abstract method - iski body nahi hoti
    abstract void draw();

    // Concrete method - iski body hoti hai
    void description() {
        System.out.println("This is a shape.");
    }
}

class Circle extends Shape {
    // Abstract method ko implement karna zaroori hai
    void draw() {
        System.out.println("Drawing a circle.");
    }
}

public class Main {
    public static void main(String[] args) {
        // Shape s = new Shape(); // Error! Abstract class ka object nahi ban sakta.
        Shape myCircle = new Circle(); // Sahi hai
        myCircle.draw();
        myCircle.description();
    }
}
```

-----

## **5. Inheritance (Viraasat)**

Inheritance ek mechanism hai jismein ek class (jise **child** ya **subclass** kehte hain) doosri class (jise **parent** ya **superclass** kehte hain) ki properties aur methods ko prapt (acquire) karti hai.

**Kyun Zaroori Hai?**: Isse **code reusability** badhti hai. Aapko baar-baar same code likhne ki zaroorat nahi padti. Yeh "IS-A" relationship batata hai (e.g., "A Car IS-A Vehicle").

**Analogy**: Parents aur bachhe. Bachhon ko apne parents se kuch gun (properties jaise eye color) viraasat mein milte hain. Iske alawa, unke apne kuch unique gun bhi hote hain.

### **Java Code Example**

```java
// Parent / Superclass
class Vehicle {
    String brand = "Ford";
    void honk() {
        System.out.println("Tuut, tuut!");
    }
}

// Child / Subclass
// 'Car' Vehicle ki saari properties aur methods inherit karegi
class Car extends Vehicle {
    String modelName = "Mustang";
}

public class Main {
    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.honk(); // Parent class ka method use kiya
        System.out.println(myCar.brand + " " + myCar.modelName);
    }
}
```

-----

## **6. Polymorphism (Bahuroopata)**

Polymorphism ka matlab hai "ek naam, anek roop". Yeh ek task ko alag-alag तरीkon se karne ki ability hai.

Java mein polymorphism do tarah se achieve hota hai:

### **1. Method Overloading (Compile-time Polymorphism)**

Ek hi class mein same naam ke multiple methods, lekin unke **parameters** (number of arguments ya type of arguments) alag-alag hote hain. Compiler decide karta hai ki kaunsa method call hoga.

### **2. Method Overriding (Run-time Polymorphism)**

Jab ek subclass (child class) apne superclass (parent class) ke method ko apni khud ki implementation deti hai. Dono methods ka naam aur parameters same hote hain. Kaunsa method call hoga, yeh run-time par (object ke type ke आधार par) decide hota hai.

**Analogy**: Ek insaan (object). Woh alag-alag jagah alag-alag behave karta hai. Office mein woh ek 'Employee' hai, ghar par 'Parent' hai, aur doston ke saath 'Friend' hai. Vyakti ek hi hai, lekin uske roop (behavior) alag-alag hain.

### **Java Code Example (Method Overriding)**

```java
class Animal {
    void makeSound() {
        System.out.println("Animal makes a sound");
    }
}

class Pig extends Animal {
    // Parent ke method ko override kiya
    @Override
    void makeSound() {
        System.out.println("The pig says: wee wee");
    }
}

class Cat extends Animal {
    // Parent ke method ko override kiya
    @Override
    void makeSound() {
        System.out.println("The cat says: meow meow");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal myAnimal = new Animal();
        Animal myPig = new Pig(); // Animal reference, lekin object Pig ka hai
        Animal myCat = new Cat(); // Animal reference, lekin object Cat ka hai

        myAnimal.makeSound(); // Animal wala method
        myPig.makeSound();    // Pig wala method (overridden)
        myCat.makeSound();    // Cat wala method (overridden)
    }
}
```

-----

## **Access Modifiers**

Yeh keywords hain jo class, variable, method, ya constructor ki accessibility (pahunch) ko control karte hain.

1.  **`public`**: Kahin se bhi access kiya ja sakta hai (dusre package se bhi). Sabse kam restrictive.
2.  **`protected`**: Same package mein aur dusre package ki subclasses mein access kiya ja sakta hai.
3.  **`default` (koi keyword nahi)**: Agar aap kuch nahi likhte, toh woh `default` hota hai. Sirf same package ke andar access ho sakta hai.
4.  **`private`**: Sirf usi class ke andar access ho sakta hai jismein use declare kiya gaya hai. Sabse zyada restrictive.

---



### **Encapsulation 💊**

**Encapsulation** ka matlab hai data (variables) aur us data par kaam karne wale methods ko ek saath ek single unit (class) mein baandh dena. Iska sabse bada fayda hai **data hiding**: aap variables ko **`private`** bana dete hain taaki unhe class ke bahar se direct access na kiya ja sake. Phir aap **`public`** methods (getters and setters) banate hain jinke zariye us data ko safely access ya modify kiya jaata hai.

Yeh aapke data ko galat changes se bachata hai aur aapko variable ki value change karne se pehle validation logic add karne ki power deta hai.

**Analogy**: Ek medical capsule ki tarah sochiye. Dawa (`private` data) capsule ke andar safe rehti hai. Aap direct dawa ko nahi chhedte, balki poore capsule (`public` methods) ko istemal karte hain.

-----

#### **Java Example: `BankAccount` Class**

Yahan, `balance` ko `private` rakha gaya hai. Aap uski value direct set nahi kar sakte. Aapko `deposit` aur `withdraw` jaise methods ka istemal karna hoga, jinmein zaroori logic likha hua hai.

```java
public class BankAccount {
    // 1. Data ko 'private' banakar hide kiya gaya hai.
    private double balance;

    // Constructor to set an initial balance
    public BankAccount(double initialBalance) {
        if (initialBalance >= 0) {
            this.balance = initialBalance;
        } else {
            this.balance = 0;
        }
    }

    // 2. Public 'getter' method: balance ko safe tarike se read karne ke liye.
    public double getBalance() {
        return this.balance;
    }

    // 3. Public 'setter' jaisa method: validation ke saath paise deposit karne ke liye.
    public void deposit(double amount) {
        if (amount > 0) {
            this.balance += amount;
            System.out.println("Deposit successful. New balance: $" + this.balance);
        } else {
            System.out.println("Invalid amount. Deposit must be positive.");
        }
    }

    // 4. Dusra public method: validation ke saath paise nikalne ke liye.
    public void withdraw(double amount) {
        if (amount > 0 && amount <= this.balance) {
            this.balance -= amount;
            System.out.println("Withdrawal successful. New balance: $" + this.balance);
        } else {
            System.out.println("Withdrawal failed. Insufficient funds or invalid amount.");
        }
    }
}

// Ise istemal kaise karein
class Main {
    public static void main(String[] args) {
        BankAccount myAccount = new BankAccount(5000.0);

        // myAccount.balance = -1000; // COMPILE ERROR! private variable ko direct access nahi kar sakte.

        // Public methods ka istemal hi sahi tarika hai
        System.out.println("Initial Balance: $" + myAccount.getBalance());

        myAccount.deposit(2000.0);
        myAccount.withdraw(8000.0); // Yeh fail ho jayega
        myAccount.withdraw(1500.0);

        System.out.println("Final Balance: $" + myAccount.getBalance());
    }
}
```

-----

### **Inheritance 👪**

**Inheritance** ek process hai jismein ek nayi class (jise **subclass** ya **child class** kehte hain) ek purani class (jise **superclass** ya **parent class** kehte hain) ke gunon (properties) aur kaam (methods) ko viraasat mein leti hai. Isse **code reusability** badhti hai aur "IS-A" relationship banta hai (jaise, "A Car IS-A Vehicle").

  * **`extends`**: Yeh keyword child class ko parent class se jodne ke liye istemal hota hai.
  * **Method Overriding**: Jab child class apne parent class ke kisi method ko apni khud ki specific implementation deti hai. `@Override` annotation likhna ek acchi practice hai, yeh compiler ko batata hai ki aap method override kar rahe hain.
  * **`super`**: Yeh keyword parent class ko refer karne ke liye hota hai. Aap isse parent class ke constructor (`super()`) ya methods (`super.methodName()`) ko call kar sakte hain.

**Analogy**: Bachhon ko apne parents se kuch aadat (properties) viraasat mein milti hain. Lekin woh un aadaton ko apne tareeke se badal bhi sakte hain (method overriding) aur unke paas apni khud ki alag aadat bhi hoti hain.

-----

#### **Java Example: `Vehicle`, `Car`, aur `Bike` Classes**

Yahan, `Car` aur `Bike` dono `Vehicle` se inherit kar rahe hain. Unhein `brand` aur `stop()` method viraasat mein milte hain. Lekin, dono `start()` method ko apne-apne tareeke se implement karte hain.

```java
// Superclass ya Parent Class
class Vehicle {
    String brand;

    public Vehicle(String brand) {
        this.brand = brand;
        System.out.println("Vehicle ka constructor call hua.");
    }

    public void start() {
        System.out.println("Vehicle ka engine start ho raha hai...");
    }

    public void stop() {
        System.out.println("Vehicle ka engine stop ho raha hai.");
    }
}

// Subclass ya Child Class
class Car extends Vehicle {

    public Car(String brand) {
        // 1. 'super()' se parent class ka constructor call karna.
        // Yeh constructor ki pehli line honi chahiye.
        super(brand);
        System.out.println("Car ka constructor call hua.");
    }

    // 2. Method Overriding: start() method ko Car ke liye redefine kiya gaya.
    @Override
    public void start() {
        System.out.println(this.brand + " car chabi se start ho rahi hai.");
    }
}

// Ek aur Subclass
class Bike extends Vehicle {

    public Bike(String brand) {
        super(brand);
        System.out.println("Bike ka constructor call hua.");
    }

    @Override
    public void start() {
        // 3. 'super' keyword se parent ka method call karna.
        super.start(); // Yeh "Vehicle ka engine start ho raha hai..." print karega.
        System.out.println(this.brand + " bike kick se start ho rahi hai.");
    }
}

// Ise test kaise karein
class TestDrive {
    public static void main(String[] args) {
        Car myCar = new Car("Maruti");
        myCar.start(); // Car ka apna overridden start() method call hoga.
        myCar.stop();  // Vehicle ka inherited stop() method call hoga.

        System.out.println("---");

        Bike myBike = new Bike("Honda");
        myBike.start(); // Bike ka apna overridden start() method call hoga.
        myBike.stop();
    }
}
```

----


## **Polymorphism (Bahuroopata) 🎭**

**Polymorphism** ka matlab hai "ek naam, anek roop." Programming mein, yeh ek object ya method ki alag-alag tarike se behave karne ki ability hai. Iska sabse powerful use hota hai **Run-time Polymorphism**, jo method overriding se achieve hota hai. Ismein, aap ek parent class ke reference variable mein child class ka object rakh sakte hain, aur jab aap us reference se koi method call karte hain, to Java run-time par decide karta hai ki child class wala method call karna hai.

**Analogy**: Ek TV ka remote sochiye. Remote mein `Power` button ek hi hai. Jab aap use TV ke liye use karte hain, to TV on/off hota hai. Jab aap usi tarah ke remote ko AC ke liye use karte hain, to AC on/off hota hai. Button ek hi hai (`method`), lekin uska kaam device (`object`) ke hisaab se alag-alag hai.

Polymorphism ko interfaces aur abstract classes ke zariye istemal karna sabse common tareeka hai.

-----

### **Java Example: `Shape` Interface**

Yahan, `Circle` aur `Rectangle` dono alag-alag classes hain, lekin kyunki woh `Shape` interface ko implement karti hain, hum unke objects ko `Shape` ke reference mein store kar sakte hain. Isse humara code bahut flexible ho jaata hai.

```java
// 1. Ek interface ek contract ki tarah hai.
// Yeh batata hai ki ek Shape ko kya-kya karna aana chahiye.
interface Shape {
    void draw(); // Method jiska koi body nahi hai
    double getArea();
}

// 2. Circle class is contract ko poora karti hai.
class Circle implements Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public void draw() {
        System.out.println("Ek circle banaya ja raha hai.");
    }

    @Override
    public double getArea() {
        // Area of circle: π * r^2
        return Math.PI * radius * radius;
    }
}

// 3. Rectangle class bhi is contract ko poora karti hai.
class Rectangle implements Shape {
    private double width;
    private double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public void draw() {
        System.out.println("Ek rectangle banaya ja raha hai.");
    }

    @Override
    public double getArea() {
        return width * height;
    }
}

// Polymorphism ka pradarshan
class DrawingApp {
    public static void main(String[] args) {
        // Yahan polymorphism ho raha hai. Reference 'Shape' type ka hai,
        // lekin object Circle aur Rectangle type ke hain.
        Shape myShape1 = new Circle(5.0);
        Shape myShape2 = new Rectangle(4.0, 6.0);

        // Ek hi tarah se dono alag-alag objects ko treat kar pa rahe hain.
        myShape1.draw(); // Run-time par Circle ka draw() call hoga.
        System.out.println("Area: " + myShape1.getArea());

        System.out.println("---");

        myShape2.draw(); // Run-time par Rectangle ka draw() call hoga.
        System.out.println("Area: " + myShape2.getArea());
    }
}
```

-----

## **Abstraction (Vivaran Chhipana)  abstra**

**Abstraction** ka matlab hai zaroori cheezein dikhana aur unki implementation details (woh kaam kaise kar rahi hain) ko chhipana. Yeh complexity ko kam karta hai aur humein "kya karna hai" par focus karne deta hai, na ki "kaise karna hai" par.

**Analogy**: Jab aap car chalate hain, to aap steering wheel, accelerator, aur brakes ka istemal karte hain. Yeh car ka **interface** hai. Aapko yeh janne ki zaroorat nahi ki engine ke andar kya ho raha hai ya brakes kaise kaam karte hain. Woh sab **implementation details** hain jo aapse chhipayi gayi hain.

Java mein abstraction do tareekon se achieve hota hai:

1.  **Abstract Classes**: Aisi class jiska object nahi banaya ja sakta. Yeh ek blueprint ki tarah hoti hai jise doosri classes `extend` karti hain. Ismein `abstract` methods (bina body ke) aur normal methods (body ke saath) dono ho sakte hain.
2.  **Interfaces**: Yeh 100% abstract blueprint ya contract hota hai. Koi bhi class jo ise `implements` karti hai, use iske saare methods ko define karna padta hai.

-----

### **Java Example: `Animal` Abstract Class**

Ek "Animal" apne aap mein kuch nahi hota; uske types hote hain jaise `Dog`, `Cat`, etc. Isliye hum `Animal` ko ek abstract class banate hain. Hum kehte hain ki har animal ek `sound()` nikalta hai, lekin har animal ka sound alag hota hai. Isliye `makeSound()` ko `abstract` bana dete hain taaki har child class use apne tareeke se define kare.

```java
// 1. Abstract class ka object nahi ban sakta.
abstract class Animal {
    // 2. Abstract method - iski body nahi hoti. Child class ko ise define karna zaroori hai.
    public abstract void makeSound();

    // Abstract class mein normal method bhi ho sakta hai.
    public void sleep() {
        System.out.println("Yeh janwar so raha hai... Zzz");
    }
}

// 3. Dog class Animal ko extend kar rahi hai.
class Dog extends Animal {
    // Isko makeSound() method ko define karna hi padega.
    @Override
    public void makeSound() {
        System.out.println("Kutta bhaukta hai: Woof Woof!");
    }
}

// 4. Cat class bhi Animal ko extend kar rahi hai.
class Cat extends Animal {
    // Isko bhi makeSound() method ko define karna hi padega.
    @Override
    public void makeSound() {
        System.out.println("Billi bolti hai: Meow!");
    }
}

class PetShop {
    public static void main(String[] args) {
        // Animal myAnimal = new Animal(); // ERROR! Abstract class ka object nahi ban sakta.

        Dog myDog = new Dog();
        myDog.makeSound(); // Dog ka apna defined method call hoga.
        myDog.sleep();     // Animal class se viraasat mein mila method call hoga.

        System.out.println("---");

        Cat myCat = new Cat();
        myCat.makeSound(); // Cat ka apna defined method call hoga.
        myCat.sleep();
    }
}
```


---


## **Exception Handling 🚨**

**Exception** ek aisi unwanted event hai jo program ke normal execution ko rok deti hai. Jaise zero se divide karna ya aisi file ko padhna jo exist hi nahi karti. **Exception Handling** ek mechanism hai jisse hum in runtime errors ko gracefully handle karte hain, taaki humara program crash na ho.

Isko hum `try-catch-finally` block se karte hain.

  * **`try`**: Is block mein hum woh code rakhte hain jismein exception aane ka chance hota hai.
  * **`catch`**: Agar `try` block mein koi exception aati hai, to `catch` block usko pakad leta hai aur usko handle karne ke liye code chalata hai.
  * **`finally`**: Yeh block hamesha chalta hai, chahe exception aaye ya na aaye. Ismein hum zaroori cleanup code likhte hain, jaise file ya database connection ko band karna.

**Analogy**: Aap ek chef hain jo ek dish banane ki koshish (`try`) kar rahe hain. Agar koi ingredient (`Exception`) khatam ho jaye, to aap ek backup plan (`catch`) use karte hain. Chahe kuch bhi ho, aap aakhir mein kitchen hamesha saaf (`finally`) karte hain.

-----

### **Custom Exceptions**

Kabhi-kabhi Java ki built-in exceptions humari zaroorat ke liye kaafi nahi hoti. Aise mein hum apni khud ki **custom exception** class bana sakte hain `Exception` class ko extend karke. Isse humara code zyada saaf aur padhne mein aasan ho jaata hai.

### **Java Example: `BankAccount` with Custom Exception**

Hum apne `BankAccount` ko behtar banate hain. Agar koi balance se zyada paise nikalne ki koshish kare, to hum ek `InsufficientFundsException` throw karenge.

```java
// 1. Apni custom exception class banayein.
class InsufficientFundsException extends Exception {
    public InsufficientFundsException(String message) {
        super(message); // Message ko parent class (Exception) ko pass karein.
    }
}

// 2. BankAccount class ko update karein.
class BankAccount {
    private double balance;

    public BankAccount(double initialBalance) {
        this.balance = initialBalance;
    }

    public double getBalance() {
        return this.balance;
    }

    // Yeh method ab exception 'throw' kar sakta hai.
    public void withdraw(double amount) throws InsufficientFundsException {
        if (amount > this.balance) {
            // Agar paise kam hain, to exception banakar 'throw' karein.
            throw new InsufficientFundsException("Paise nikalne mein asamarth. Aapke account mein sirf $" + this.balance + " hain.");
        }
        this.balance -= amount;
        System.out.println("Safaltapoorvak nikale gaye: $" + amount);
    }
}

// 3. Exception ko try-catch block se handle karein.
class BankTransaction {
    public static void main(String[] args) {
        BankAccount account = new BankAccount(500.0);

        try {
            System.out.println("Koshish: $200 nikalne ki...");
            account.withdraw(200.0); // Yeh safal hoga.

            System.out.println("Koshish: $400 nikalne ki...");
            account.withdraw(400.0); // Yahan exception aayegi.

            System.out.println("Yeh line kabhi print nahi hogi.");

        } catch (InsufficientFundsException e) {
            // Exception aane par catch block chalega.
            System.out.println("Error: " + e.getMessage());
        } finally {
            // Finally block hamesha chalega.
            System.out.println("\nTransaction samapt hui.");
            System.out.println("Aapka antim balance hai: $" + account.getBalance());
        }
    }
}
```

-----

## **Java Collections Framework 📚**

**Java Collections Framework** classes aur interfaces ka ek set hai jo objects ke group ko store aur manage karne ke liye taiyaar (ready-made) data structures provide karta hai.

Iske teen mukhya hisse hain:

1.  **`List`**: Ek **ordered** collection jismein **duplicate** elements ho sakte hain. Elements ko unke index se access kiya jaata hai.
      * **`ArrayList`**: Index se element get karne ke liye tez hai.
      * **`LinkedList`**: Beech mein se elements add ya remove karne ke liye tez hai.
2.  **`Set`**: Ek **unordered** collection jismein **duplicate** elements **nahi** ho sakte.
3.  **`Map`**: **Key-Value pairs** ka collection. Har key unique honi chahiye. Ek phone book ki tarah, jahan naam (key) ek number (value) se juda hota hai.

-----

### **Java Example: `Library` with a Collection of `Book` Objects**

Hum ek `Library` class banayenge jo `Book` objects ko store karne ke liye `ArrayList` ka istemal karegi.

```java
import java.util.ArrayList;
import java.util.List;

// Ek simple Book class.
class Book {
    String title;
    String author;

    public Book(String title, String author) {
        this.title = title;
        this.author = author;
    }

    @Override
    public String toString() {
        return "Kitaab: '" + title + "' by " + author;
    }
}

// Library class jo books ko manage karti hai.
class Library {
    private List<Book> books;

    public Library() {
        this.books = new ArrayList<>(); // Hum ArrayList ka istemal kar rahe hain.
    }

    public void addBook(Book book) {
        this.books.add(book);
    }
    
    public List<Book> getBooks() {
        return this.books;
    }

    public void displayBooks() {
        System.out.println("--- Library ki Kitaabein ---");
        // Enhanced for-loop se collection ko traverse karna.
        for (Book book : this.books) {
            System.out.println(book);
        }
        System.out.println("--------------------------");
    }
}
```

-----

## **Java Streams API 🌊**

**Java Streams API** (Java 8 mein introduce hua) collections of data ko process karne ka ek naya aur powerful tareeka hai. Yeh functional programming style ka istemal karta hai. Ismein aap yeh batate hain ki aapko **"kya karna hai"**, na ki **"kaise karna hai"**.

**Analogy**: Ek factory ki assembly line ki tarah sochiye. Raw material (`data source`) ek taraf se aata hai. Phir woh alag-alag machines (`intermediate operations` jaise `filter`, `map`) se guzarta hai, aur aakhir mein final product (`terminal operation`) bankar nikalta hai.

Iske kuch zaroori methods hain:

  * **`filter(condition)`**: Sirf un elements ko chunta hai jo di gayi condition ko poora karte hain.
  * **`map(function)`**: Har element ko ek naye form mein badal deta hai.
  * **`forEach(action)`**: Har element par koi action perform karta hai.
  * **`collect()`**: Stream ke results ko ek List, Set, ya Map mein ikattha karta hai.

-----

### **Java Example: `Library` with Streams**

Hum upar wali `Library` class ka istemal karke uski books ko Streams se process karenge.

```java
import java.util.stream.Collectors;
import java.util.List;

class LibraryApp {
    public static void main(String[] args) {
        Library myLibrary = new Library();
        myLibrary.addBook(new Book("The Alchemist", "Paulo Coelho"));
        myLibrary.addBook(new Book("Atomic Habits", "James Clear"));
        myLibrary.addBook(new Book("The Psychology of Money", "Morgan Housel"));
        myLibrary.addBook(new Book("Deep Work", "Cal Newport"));

        // Use Case 1: Sirf un kitabon ke title print karein jinke naam 'The' se shuru hote hain.

        System.out.println("\n--- Sirf Titles (Stream se) ---");
        
        myLibrary.getBooks() // 1. Collection prapt karein
                 .stream()   // 2. Stream shuru karein
                 .filter(book -> book.title.startsWith("The")) // 3. Filter: 'The' se shuru hone wali kitabein
                 .map(book -> book.title) // 4. Map: Har Book object ko uske title (String) mein badlein
                 .forEach(title -> System.out.println(title)); // 5. ForEach: Har title ko print karein
    }
}
```
---
Yeh woh C++ features hain jo ya to Java mein hain hi nahi, ya unka kaam karne ka tareeka Java se bilkul alag hai.

-----

### **1. Memory Management (Memory ka Prabandhan)**

Yeh Java aur C++ ka sabse bada antar hai.

  * **C++ mein**: Aapko memory manually manage karni padti hai. Jab aap `new` keyword se memory allocate karte hain, to aapki zimmedari hai ki kaam khatam hone par use `delete` keyword se free karein. Agar aap bhool gaye, to **memory leak** ho jaata hai. Classes mein **Destructor (`~ClassName()`)** is cleanup ke liye istemal hote hain.
  * **Java mein**: Memory management automatic hai. **Garbage Collector** (GC) naam ka ek process background mein chalta rehta hai aur un objects ko memory se हटा deta hai jinka ab koi istemal nahi ho raha. Aapko `delete` jaisa kuch karne ki zaroorat nahi.

**Analogy**: C++ mein memory manage karna ek kothi kiraye par lene jaisa hai. Aapko kiraya dena (`new`) aur chhodte waqt makaan maalik ko batana (`delete`) dono aapki zimmedari hai. Java ek hotel jaisa hai, aap bas check-out karte hain, aur room ki safai (`memory cleanup`) housekeeping (`Garbage Collector`) khud kar leti hai.

#### **C++ Code Example**

```cpp
#include <iostream>

class Box {
public:
    Box() {
        std::cout << "Box ban gaya! (Memory allocated)" << std::endl;
    }
    ~Box() {
        std::cout << "Box nasht ho gaya! (Memory freed)" << std::endl;
    }
};

int main() {
    // Pointer banakar 'new' se memory allocate ki
    Box* myBox = new Box();

    // Jab kaam khatam ho jaye, memory ko 'delete' karna zaroori hai
    delete myBox; // Agar yeh line nahi likhi to memory leak ho jayegi

    return 0;
}
```

-----

### **2. Operator Overloading**

  * **C++ mein**: Aap `+`, `-`, `*`, `==`, `<<` jaise operators ko apne banaye hue objects (classes) ke liye naya matlab de sakte hain. For example, aap `+` operator ko sikha sakte hain ki do `ComplexNumber` objects ko kaise joda jaaye.
  * **Java mein**: Java language ko saral rakhne ke liye operator overloading support nahi karta (sirf String concatenation ke liye `+` internally overloaded hai, lekin aap apne liye nahi kar sakte).

**Analogy**: C++ mein aap ek purane auzaar (`+` operator) ko naye kaam (`ComplexNumber` add karna) ke liye istemal karna sikha sakte hain. Java mein, har auzaar ka kaam fix hai, aap use naye kaam ke liye nahi badal sakte.

#### **C++ Code Example**

```cpp
#include <iostream>

class Complex {
private:
    float real, imag;
public:
    Complex(float r = 0, float i = 0) : real(r), imag(i) {}

    // '+' operator ko overload kar rahe hain
    Complex operator+(const Complex& obj) {
        Complex temp;
        temp.real = this->real + obj.real;
        temp.imag = this->imag + obj.imag;
        return temp;
    }

    void print() {
        std::cout << real << " + " << imag << "i" << std::endl;
    }
};

int main() {
    Complex c1(3, 2);
    Complex c2(1, 7);
    
    // Yahan overloaded '+' operator call ho raha hai
    Complex c3 = c1 + c2;
    
    c3.print(); // Output: 4 + 9i
    return 0;
}
```

-----

### **3. Multiple Inheritance**

  * **C++ mein**: Ek class ek se zyada parent classes se inherit kar sakti hai. Jaise ek `Bat` class `Mammal` aur `FlyingCreature` dono se inherit kar sakti hai. Isse "Diamond Problem" jaisi complexity aa sakti hai, jise C++ virtual inheritance se solve karta hai.
  * **Java mein**: Java mein ek class sirf ek hi class ko `extends` kar sakti hai. Isse language saral rehti hai. Multiple inheritance jaisa kaam karne ke liye Java mein `interfaces` ka istemal hota hai, jahan ek class kai interfaces ko `implements` kar sakti hai.

**Analogy**: C++ mein ek bachhe ke do biological parents (`class Father`, `class Mother`) ho sakte hain, aur woh dono se gun le sakta hai. Java mein, ek bachhe ka ek hi biological parent (`extends class`) ho sakta hai, lekin woh kai alag-alag guruon (`implements interface`) se alag-alag vidya seekh sakta hai.

#### **C++ Code Example**

```cpp
#include <iostream>

class Father {
public:
    void gardening() {
        std::cout << "I love gardening." << std::endl;
    }
};

class Mother {
public:
    void cooking() {
        std::cout << "I love cooking." << std::endl;
    }
};

// Child class ne Father aur Mother dono se inherit kiya
class Child : public Father, public Mother {
};

int main() {
    Child ch;
    ch.gardening(); // Father se mila
    ch.cooking();   // Mother se mila
    return 0;
}
```

-----

### **4. Virtual Functions**

  * **C++ mein**: Run-time polymorphism achieve karne ke liye C++ `virtual` keyword ka istemal karta hai. Jab aap base class ke pointer se derived class ke object ko point karte hain, to `virtual` function yeh sunishchit karta hai ki derived class ka hi version call ho. Jin functions ko `  = 0; ` laga kar declare karte hain, woh **pure virtual functions** kehlate hain aur woh class ko **abstract** bana dete hain.
  * **Java mein**: Java mein saare non-static methods by default `virtual` hi hote hain. Aapko alag se koi keyword lagane ki zaroorat nahi. Abstract methods ke liye Java `abstract` keyword ka istemal karta hai.

#### **C++ Code Example**

```cpp
#include <iostream>

class Base {
public:
    // virtual keyword batata hai ki ise override kiya ja sakta hai
    virtual void show() {
        std::cout << "Base class show" << std::endl;
    }
};

class Derived : public Base {
public:
    // Base class ke virtual function ko override karna
    void show() override {
        std::cout << "Derived class show" << std::endl;
    }
};

int main() {
    Base* ptr = new Derived();
    ptr->show(); // Output: Derived class show (virtual ki wajah se)
    delete ptr;
    return 0;
}
```

-----

### **5. Templates (Generic Programming)**

  * **C++ mein**: **Templates** se aap generic functions ya classes bana sakte hain jo kisi bhi data type ke saath kaam kar sakti hain (jaise `int`, `float`, `string`, ya aapke apne objects). Yeh compile-time par hota hai.
  * **Java mein**: Java mein iske jaisa kaam **Generics** (`<T>`) se hota hai. Lekin Java ke Generics type erasure ka istemal karte hain aur woh C++ templates jitne flexible ya powerful nahi hote (jaise, aap primitive types jaise `int` use nahi kar sakte, `Integer` use karna padta hai).

**Analogy**: C++ ka Template ek adjustable saancha (mould) jaisa hai. Aap use `int`, `string`, ya kisi bhi type ke liye set kar sakte hain, aur compiler us type ke liye ek special version bana dega. Java ke Generics ek "one-size-fits-all" dibbe jaise hain jiske bahar likha hota hai ki ismein sirf ek hi type ka saaman aayega, lekin andar sabhi saaman ko `Object` ki tarah treat kiya jaata hai.

#### **C++ Code Example**

```cpp
#include <iostream>

// Ek generic function template
template <typename T>
T add(T a, T b) {
    return a + b;
}

int main() {
    // Integer ke liye istemal
    std::cout << "Sum of 5 and 10 is: " << add(5, 10) << std::endl;

    // Double ke liye istemal
    std::cout << "Sum of 3.5 and 7.2 is: " << add(3.5, 7.2) << std::endl;

    return 0;
}
```

----

### **6. Pointer Arithmetic**

  * **C++ mein**: C++ aapko **pointers** ka poora control deta hai. Pointer ek variable hota hai jo doosre variable ka memory address store karta hai. Aap in pointers par ganit (arithmetic) jaise `ptr++` (agle memory location par jao) ya `ptr - 5` (5 memory location peeche jao) kar sakte hain. Yeh arrays ke saath kaam karne mein bahut powerful hai, lekin khatarnaak bhi, kyunki galat istemal se program crash ho sakta hai.
  * **Java mein**: Suraksha (safety) ke liye, Java pointers ka direct access nahi deta. Java mein **references** hote hain, jo internally memory address hi rakhte hain, lekin aap unpar C++ jaisi arithmetic nahi kar sakte. Yeh Java ko memory-related bugs se bachata hai.

**Analogy**: C++ ka pointer ek ghar ke poore address (`Plot No. 420, Sector 10`) jaisa hai. Aapko address pata hai to aap uske bagal wale ghar (`Plot No. 421`) ka address khud nikal sakte hain. Java ka reference ek contact list mein save naam (`Anjali`) jaisa hai. Aap Anjali ko call kar sakte hain, lekin aapko uska address nahi pata, aur na hi aap uske naam se uske padosi ka naam nikal sakte hain.

#### **C++ Code Example**

```cpp
#include <iostream>

int main() {
    int arr[] = {10, 20, 30, 40, 50};
    
    // Pointer 'ptr' array ke pehle element ko point kar raha hai
    int* ptr = arr;

    std::cout << "Array ke elements pointer se:" << std::endl;
    for (int i = 0; i < 5; ++i) {
        // *ptr se value print karo
        std::cout << *ptr << " ";
        // ptr++ se pointer ko agle integer location par le jao
        ptr++; 
    }
    std::cout << std::endl;

    return 0;
}
```

-----

### **7. RAII (Resource Acquisition Is Initialization)**

Yeh C++ ka ek bahut hi important design pattern hai.

  * **C++ mein**: RAII ka matlab hai ki aap resource (jaise file, network connection, memory) ko object ke banne (construction) ke waqt haasil (acquire) karte hain, aur jab object nasht (destroy) hota hai to uske **destructor** mein resource ko automatically release kar dete hain. Isse yeh pakka ho jaata hai ki resource kabhi leak nahi hoga, chahe koi exception hi kyun na aa jaye.
  * **Java mein**: Kyunki Java mein destructors nahi hote, isliye woh RAII pattern ka istemal nahi kar sakta. Iske badle, Java mein `try-with-resources` statement ka istemal hota hai un resources ke liye jo `AutoCloseable` interface ko implement karte hain.

**Analogy**: C++ ka RAII ek automated system jaisa hai. Jab aap ek object banate hain (kamre mein enter karte hain), to light (`resource`) apne aap on ho jaati hai. Jab object destroy hota hai (aap kamre se bahar jaate hain), to light apne aap band ho jaati hai. Java ka `try-with-resources` ek special room jaisa hai jahan aapko pehle batana padta hai ki aap light istemal kar rahe hain, aur us room (`try` block) se nikalte hi light band ho jaayegi.

#### **C++ Code Example**

```cpp
#include <iostream>
#include <fstream>

class FileManager {
private:
    std::ofstream file;
public:
    // Constructor mein file acquire (open) ho rahi hai
    FileManager(const char* filename) {
        file.open(filename);
        if (file.is_open()) {
            std::cout << "File khul gayi." << std::endl;
        }
    }
    // Destructor mein file automatically release (close) ho jayegi
    ~FileManager() {
        if (file.is_open()) {
            file.close();
            std::cout << "File band ho gayi." << std::endl;
        }
    }
};

void manageFile() {
    // Jaise hi 'fm' object banega, constructor file khol dega
    FileManager fm("test.txt"); 
    // Jaise hi yeh function khatam hoga, 'fm' destroy hoga
    // aur destructor automatically file band kar dega.
}

int main() {
    manageFile();
    return 0;
}
```

-----

### **8. C++ `friend` Keyword**

  * **C++ mein**: `friend` keyword encapsulation ko todne ka ek tareeka hai. Agar ek class kisi doosre function ya class ko apna `friend` banati hai, to woh friend function/class us class ke `private` aur `protected` members ko direct access kar sakta hai.
  * **Java mein**: Java mein `friend` jaisa koi concept nahi hai. Access sirf `public`, `protected`, `default`, aur `private` modifiers se hi control hota hai.

**Analogy**: Ek class ke `private` members ek personal diary ki tarah hain. Normally koi use nahi padh sakta. Kisi function ko `friend` banana matlab apne best friend ko us diary ki chabi de dena. Woh aapke parivar (`class`) ka hissa nahi hai, lekin aap uspar vishwas karte hain. Java is tarah diary ki chabiyan baantne mein vishwas nahi rakhta.

#### **C++ Code Example**

```cpp
#include <iostream>

class MyClass {
private:
    int secret = 42;
public:
    // Is function ko friend declare kiya gaya
    friend void showSecret(const MyClass& obj);
};

// Yeh ek normal function hai, class ka member nahi
void showSecret(const MyClass& obj) {
    // Lekin 'friend' hone ki wajah se yeh private member access kar sakta hai
    std::cout << "The secret value is: " << obj.secret << std::endl;
}

int main() {
    MyClass obj;
    showSecret(obj); // Friend function ko call kiya
    return 0;
}
```

-----

### **9. Static Methods & Variables**

  * **C++ aur Java mein**: Dono mein concept lagbhag same hai. **Static** members class se jude hote hain, na ki uske individual objects se. Ek static variable ki sirf ek copy banti hai jo saare objects share karte hain. Static methods ko bina object banaye, seedhe class ke naam se call kiya ja sakta hai.
  * **Antar**: Inheritance ke mamle mein kuch chote-mote antar hain (jaise Java mein static methods override nahi hote, hide hote hain), lekin basic behavior dono mein ek jaisa hai.

**Analogy**: Ek static variable ek cricket team (`class`) ke scoreboard jaisa hai. Woh poori team ka hota hai, na ki kisi ek player (`object`) ka. Koi bhi player score update kar sakta hai, aur sabhi players ko wahi score dikhega.

#### **C++ Code Example**

```cpp
#include <iostream>

class Player {
public:
    static int playerCount; // Static variable declare kiya
    
    Player() {
        playerCount++; // Jab bhi object banega, count badhega
    }
};

int Player::playerCount = 0; // Static variable ko initialize karna zaroori hai

int main() {
    std::cout << "Initial players: " << Player::playerCount << std::endl;
    Player p1;
    Player p2;
    std::cout << "Players after creation: " << Player::playerCount << std::endl;
    return 0;
}
```

-----

### **10. Destructors**

  * **C++ mein**: **Destructor** (`~ClassName()`) ek special function hai jo tab call hota hai jab object ki lifetime khatam hoti hai (jaise woh scope se bahar chala jaye ya use `delete` kiya jaye). Iska mukhya kaam object dwara li gayi resources (jaise memory, files) ko release karna hota hai.
  * **Java mein**: Java mein **destructors nahi hote**. Garbage Collector memory saaf karta hai, lekin doosre resources ki safai ke liye `finally` block ya `try-with-resources` ka istemal kiya jaata hai. Java mein `finalize()` method hota tha, lekin woh deprecated hai aur use istemal nahi karna chahiye.

#### **C++ Code Example**

```cpp
#include <iostream>

class MyResource {
private:
    int* data;
public:
    MyResource() {
        data = new int[100]; // Constructor mein memory allocate ki
        std::cout << "Resource acquired." << std::endl;
    }

    ~MyResource() {
        delete[] data; // Destructor mein memory free ki
        std::cout << "Resource released." << std::endl;
    }
};

int main() {
    {
        MyResource res; // Object bana
    } // Yahan scope khatam hua, 'res' ka destructor automatically call ho jayega
    
    return 0;
}
```

----
hum Java mein core OOP concepts ko implement karte hain Hinglish mein, jaisa aapne kaha. Har example mein concept ko code aur uski explanation ke saath samjhaya gaya hai.

-----

### **1. `BankAccount` Class (Encapsulation ka Example)**

**Concept**: Encapsulation ka matlab hai data (variables) aur uss data par kaam karne wale methods ko ek saath ek unit (class) mein baandh dena. Hum data ko `private` banakar hide karte hain aur use access karne ke liye `public` methods (getters/setters) banate hain. Isse data safe rehta hai aur uspar control bana rehta hai.

**Analogy**: Ek medical capsule ki tarah. Dawa (`private` data) capsule ke andar safe rehti hai, aur aap use sirf public tareeke se (poora capsule kha kar) hi le sakte hain.

#### **Java Code**

```java
// BankAccount.java

public class BankAccount {
    // 1. Encapsulation: balance ko private rakha gaya hai taaki koi ise direct access na kar sake.
    private double balance;
    private String accountHolderName;

    // Constructor: Jab object banega tab initial values set karne ke liye.
    public BankAccount(String accountHolderName, double initialBalance) {
        this.accountHolderName = accountHolderName;
        // Balance negative na ho, isliye check laga rahe hain.
        if (initialBalance > 0) {
            this.balance = initialBalance;
        } else {
            this.balance = 0;
        }
    }

    // 2. Public method: Paise deposit karne ke liye.
    // Yahan hum validation kar sakte hain.
    public void deposit(double amount) {
        if (amount > 0) {
            this.balance = this.balance + amount;
            System.out.println("Rs. " + amount + " safaltapoorvak deposit hue. Naya balance: " + this.balance);
        } else {
            System.out.println("Anya maan. Deposit amount positive hona chahiye.");
        }
    }

    // 3. Public method: Paise nikalne ke liye.
    // Yahan bhi validation hai.
    public void withdraw(double amount) {
        if (amount > 0 && amount <= this.balance) {
            this.balance = this.balance - amount;
            System.out.println("Rs. " + amount + " safaltapoorvak nikale gaye. Bacha hua balance: " + this.balance);
        } else {
            System.out.println("Transaction fail hui. Ya to amount galat hai ya balance kaafi nahi hai.");
        }
    }

    // 4. Getter method: Private balance ko read karne ka safe tareeka.
    public double getBalance() {
        return this.balance;
    }

    public String getAccountHolderName() {
        return this.accountHolderName;
    }
}

// Main.java (Ise run karne ke liye)
class Main {
    public static void main(String[] args) {
        BankAccount myAccount = new BankAccount("Anjali Sharma", 5000.0);
        
        // myAccount.balance = -1000; // ERROR! Aisa nahi kar sakte kyunki balance private hai.

        System.out.println(myAccount.getAccountHolderName() + " ka initial balance: " + myAccount.getBalance());

        myAccount.deposit(2000.0);
        myAccount.withdraw(1500.0);
        myAccount.withdraw(6000.0); // Yeh fail ho jayega
        
        System.out.println(myAccount.getAccountHolderName() + " ka final balance: " + myAccount.getBalance());
    }
}
```

#### **Code ki Explanation**

  * Humne `balance` ko `private` banakar **Data Hiding** achieve ki hai. Iska matlab hai ki koi bhi class ke bahar se `myAccount.balance = ...` likhkar balance ko galat value (jaise negative) nahi de sakta.
  * Paise daalne (`deposit`) ya nikalne (`withdraw`) ke liye `public` methods hain. In methods ke andar humne logic likha hai jo check karta hai ki amount sahi hai ya nahi. Yahi **Encapsulation** ka fayda hai.

-----

### **2. `Employee` Class (Inheritance aur Polymorphism ka Example)**

**Concept**: **Inheritance** se hum ek parent class ki properties child class mein laate hain (code reusability). **Polymorphism** ka matlab hai "ek naam, anek roop". Yahan, alag-alag type ke employee hain (`Manager`, `Developer`), lekin sabhi ki salary calculate ho sakti hai, bas sabka tareeka alag hai. Hum ek hi method `calculateMonthlySalary()` ko alag-alag classes mein override karke yeh achieve karte hain.

#### **Java Code**

```java
// Employee.java (Parent Class)
class Employee {
    String name;
    double baseSalary;

    public Employee(String name, double baseSalary) {
        this.name = name;
        this.baseSalary = baseSalary;
    }

    // Yeh ek general method hai. Child classes ise override karengi.
    public double calculateMonthlySalary() {
        return baseSalary;
    }

    public String getName() {
        return name;
    }
}

// Manager.java (Child Class)
class Manager extends Employee {
    private double bonus;

    public Manager(String name, double baseSalary, double bonus) {
        // 'super' keyword se parent class ka constructor call kiya.
        super(name, baseSalary);
        this.bonus = bonus;
    }

    // 1. Polymorphism: Method Overriding. Manager ki salary alag tareeke se calculate hogi.
    @Override
    public double calculateMonthlySalary() {
        // Parent ka method call karke base salary li aur usmein bonus joda.
        return super.calculateMonthlySalary() + bonus;
    }
}

// Developer.java (Ek aur Child Class)
class Developer extends Employee {
    private int overtimeHours;
    private double hourlyRate;

    public Developer(String name, double baseSalary, int overtimeHours, double hourlyRate) {
        super(name, baseSalary);
        this.overtimeHours = overtimeHours;
        this.hourlyRate = hourlyRate;
    }

    // 2. Polymorphism: Method Overriding. Developer ki salary alag tareeke se calculate hogi.
    @Override
    public double calculateMonthlySalary() {
        return super.calculateMonthlySalary() + (overtimeHours * hourlyRate);
    }
}

// Company.java (Ise run karne ke liye)
class Company {
    public static void main(String[] args) {
        // 3. Polymorphism in action: Humne Employee type ke array mein Manager aur Developer dono ke objects rakhe hain.
        Employee[] employees = new Employee[2];
        employees[0] = new Manager("Rohan Singh", 80000, 15000);
        employees[1] = new Developer("Priya Verma", 60000, 20, 500);

        for (Employee emp : employees) {
            // Yahan Java run-time par decide karega ki kaunsa calculateMonthlySalary() call karna hai.
            // Manager ke liye Manager wala, aur Developer ke liye Developer wala.
            System.out.println("Employee: " + emp.getName() + ", Salary: Rs. " + emp.calculateMonthlySalary());
        }
    }
}
```

#### **Code ki Explanation**

  * `Manager` aur `Developer` dono `Employee` ko `extends` kar rahe hain, isliye unhein `name` aur `baseSalary` viraasat (`Inheritance`) mein mil gaye.
  * Dono child classes ne `calculateMonthlySalary()` method ko `@Override` karke apni-apni logic likhi hai.
  * `Company` class ke `main` method mein, humne `Employee` ke array mein `Manager` aur `Developer` dono ko store kiya. Jab hum loop mein `emp.calculateMonthlySalary()` call karte hain, to Java dekhta hai ki `emp` اصل mein `Manager` hai ya `Developer`, aur usi ke hisaab se sahi method call karta hai. Yahi **Run-time Polymorphism** hai.

-----

### **3. `Shape` Drawing System (Abstraction ka Example)**

**Concept**: **Abstraction** ka matlab hai zaroori cheezein dikhana aur unki implementation details ko chhipana. Hum ek `abstract class` banate hain jiska object nahi ban sakta. Yeh ek adhura blueprint hota hai. Hum usmein `abstract methods` (bina body ke) define karte hain, jinko uski child classes ko zaroor implement karna padta hai.

**Analogy**: Ek "Vehicle" ek abstract concept hai. Aap "Vehicle" nahi chala sakte, aap ek specific vehicle jaise "Car" ya "Bike" chalaate hain. Hum `Vehicle` class ko `abstract` bana sakte hain aur usmein `start()` naam ka ek `abstract` method daal sakte hain, kyunki har vehicle start hota hai, lekin sabka tareeka alag hai.

#### **Java Code**

```java
// Shape.java (Abstract Class)
abstract class Shape {
    String color;

    public Shape(String color) {
        this.color = color;
    }

    // 1. Abstract method: Iski koi body nahi hai.
    // Har child class ko ise zaroor define karna hoga.
    public abstract void draw();

    // Abstract class mein normal (concrete) method bhi ho sakta hai.
    public String getColor() {
        return color;
    }
}

// Circle.java (Concrete Child Class)
class Circle extends Shape {
    double radius;

    public Circle(String color, double radius) {
        super(color);
        this.radius = radius;
    }

    // 2. Abstract method ko implement karna zaroori hai.
    @Override
    public void draw() {
        System.out.println(super.getColor() + " rang ka ek circle banaya ja raha hai jiska radius " + radius + " hai.");
    }
}

// Rectangle.java (Ek aur Concrete Child Class)
class Rectangle extends Shape {
    double length;
    double width;

    public Rectangle(String color, double length, double width) {
        super(color);
        this.length = length;
        this.width = width;
    }

    // 3. Yahan bhi abstract method ko implement kiya gaya.
    @Override
    public void draw() {
        System.out.println(super.getColor() + " rang ka ek rectangle banaya ja raha hai (Length: " + length + ", Width: " + width + ").");
    }
}

// DrawingBoard.java (Ise run karne ke liye)
class DrawingBoard {
    public static void main(String[] args) {
        // Shape myShape = new Shape("Blue"); // ERROR! Abstract class ka object nahi bana sakte.

        Shape circle = new Circle("Laal", 10.5);
        Shape rectangle = new Rectangle("Neela", 20, 10);

        circle.draw();      // Circle ka draw() method call hoga.
        rectangle.draw();   // Rectangle ka draw() method call hoga.
    }
}
```

#### **Code ki Explanation**

  * `Shape` ek `abstract class` hai. Iska matlab hai ki hum iska object nahi bana sakte. Yeh sirf ek template hai.
  * `draw()` ek `abstract method` hai. Isse humne yeh rule bana diya ki jo bhi class `Shape` ko extend karegi, use `draw()` method banana hi padega.
  * `Circle` aur `Rectangle` concrete classes hain jinhone `Shape` ke `draw()` method ko implement kiya hai. Isse **Abstraction** achieve hoti hai - humein pata hai ki har shape `draw()` ho sakti hai, lekin kaise hogi, yeh us shape ki class batayegi.
----



### **Q: What is Object-Oriented Programming (OOP) and why is it popular?**
**A:** **Object-Oriented Programming (OOP)** ek programming style hai jo "objects" ke concept par aadharit hai. Ismein hum real-duniya ki cheezon (jaise car, insaan, ya bank account) ko code mein objects ke roop mein represent karte hain. Har object ke paas apna data (properties) aur behavior (methods) hota hai.

Yeh **isliye popular hai** kyunki:
1.  **Real-World Connection**: Yeh asal duniya ki problems ko code mein model karna aasan bana deta hai.
2.  **Code Reusability**: Inheritance jaise features se hum ek baar likhe gaye code ko baar-baar istemal kar sakte hain.
3.  **Manageability**: Bade aur complex software ko chote-chote objects mein todkar manage karna aasan ho jaata hai.
4.  **Security**: Encapsulation se data ko hide karke use safe rakha jaata hai.

---

### **Q: What are the advantages and disadvantages of OOP?**
**A:**
#### **Advantages (Fayde)** 👍
* **Code Reusability (Code ka dobara istemal)**: Inheritance ki wajah se code ko dobara likhne ki zaroorat kam padti hai.
* **Modularity (Hisson mein vibhajit)**: Har object ek alag unit hota hai, isliye code saaf-suthra aur organized rehta hai.
* **Easy Maintenance**: Code organized hone ki wajah se use aage aakar badalna ya theek karna aasan hota hai.
* **Security (Suraksha)**: Data hiding se program ka data anchahe badlav se surakshit rehta hai.
* **Flexibility (Lacheelapan)**: Polymorphism ki wajah se code bahut flexible ho jaata hai.

#### **Disadvantages (Nuksan)** 👎
* **Bade Programs**: OOPs ke program procedural programs se aakaar mein bade ho sakte hain.
* **Thoda Dheema**: Kuch mamlon mein, OOPs programs thode dheeme chal sakte hain dynamic binding jaise features ki wajah se.
* **Adhik Planning**: Ise istemal karne ke liye shuruaat mein zyada planning aur design ki zaroorat padti hai.
* **Chote Projects ke liye Overkill**: Bahut hi simple aur chote projects ke liye yeh zaroorat se zyada complex ho sakta hai.

---

### **Q: What are the main features (or principles) of OOP?**
**A:** OOPs ke chaar mukhya stambh (pillars) ya features hain:
1.  **Encapsulation**: Data aur methods ko ek saath ek class mein baandh dena.
2.  **Abstraction**: Zaroori cheezein dikhana aur unki complexity (implementation details) ko chhipana.
3.  **Inheritance**: Ek class (child) ka doosri class (parent) se gunon (properties) ko viraasat mein lena.
4.  **Polymorphism**: Ek cheez ke anek roop, jaise ek method ka alag-alag classes mein alag-alag kaam karna.

---

### **Q: What is the difference between Object-Oriented Programming and Structured Programming?**
**A:**

| Feature                 | Structured Programming (Jaise C)                                             | Object-Oriented Programming (Jaise Java)                                              |
| :---------------------- | :--------------------------------------------------------------------------- | :------------------------------------------------------------------------------------ |
| **Approach**            | **Top-Down Approach**. Program ko chote-chote functions mein toda jaata hai. | **Bottom-Up Approach**. Chote-chote objects ko jodkar poora program banaya jaata hai. |
| **Focus**               | Functions aur logic par zyada focus hota hai.                                | Data aur objects par zyada focus hota hai.                                            |
| **Data Security**       | Data aam taur par `global` hota hai, isliye kam secure hota hai.             | Data `private` banakar hide kiya ja sakta hai, isliye zyada secure hota hai.          |
| **Reusability**         | Code ko dobara istemal karna mushkil hota hai.                               | Inheritance ki wajah se code ko dobara istemal karna aasan hai.                       |
| **Real-World Modeling** | Asal duniya ki problems ko model karna mushkil hai.                          | Asal duniya ki problems ko objects ke roop mein model karna aasan hai.                |

---

### **Q: What is the difference between a Class and an Object?**
**A:**
* **Class**: Ek **class** ek **blueprint** ya template hota hai. Yeh batata hai ki ek particular type ke object mein kya-kya properties (variables) aur behaviors (methods) honge. Yeh memory mein jagah nahi leta.
    * **Analogy**: Ghar ka naksha (blueprint).

* **Object**: Ek **object** uss class ka ek **instance** yaani asli roop hota hai. Jab aap class se object banate hain, tab woh memory mein jagah leta hai aur uski apni values hoti hain.
    * **Analogy**: Naksh-e ko dekhkar banaya gaya asli ghar. Aap ek hi naksh-e se kai ghar (objects) bana sakte hain.

---

### **Q: What are some commonly used OOP languages?**
**A:** Kuch mashhoor OOP languages yeh hain:
* Java
* C++
* Python
* C# (C-sharp)
* Ruby
* PHP
* Swift

---



## **1. Encapsulation (डेटा छिपाना)** 💊

### **Q: What is Encapsulation and why is it important?**
**A:** **Encapsulation** ka matlab hai data (variables) aur uss data par kaam karne wale methods (functions) ko ek saath ek single unit, yaani **class**, mein baandh dena.

Yeh **isliye important hai** kyunki yeh **data hiding** achieve karta hai. Hum class ke data ko `private` bana dete hain taaki koi use bahar se direct badal na sake. Uss data ko access ya modify karne ke liye `public` methods banaye jaate hain. Isse data par control rehta hai aur woh anchahe badlav se surakshit rehta hai.

**Analogy**: Ek medical capsule. Dawa (`private` data) capsule ke andar safe rehti hai. Aap use sirf capsule ke zariye (`public` methods) hi le sakte hain.

***

### **Q: What are access modifiers and what is their role?**
**A:** **Access Modifiers** (ya access specifiers) keywords hote hain jo yeh tay karte hain ki ek class, variable, ya method ko code mein kahan-kahan se access kiya ja sakta hai. Inka mukhya kaam encapsulation aur security laagu karna hai.

Java mein yeh chaar tarah ke hote hain:

1.  **`private` (सबसे ज़्यादा सख़्त)**
    * **Kaun access kar sakta hai?** Sirf usi class ke andar, jismein use banaya gaya hai.
    * **Kab istemal karein?** Jab aap data ko poori tarah se hide karna chahte hain, jaise ek bank account ka `balance`. Bahar ki duniya use sirf methods ke zariye hi chhu sakti hai.

2.  **`default` (कोई कीवर्ड नहीं)**
    * **Kaun access kar sakta hai?** Usi class mein aur usi **package** ke andar ki doosri classes.
    * **Kab istemal karein?** Jab aap chahte hain ki kuch cheezein sirf ek hi package ke andar aapas mein share hon, lekin package ke bahar se unhe koi access na kar paaye. Agar aap koi modifier nahi likhte, to woh `default` hota hai.

3.  **`protected`**
    * **Kaun access kar sakta hai?** Usi package ki saari classes aur doosre package ki sirf **subclasses** (child classes).
    * **Kab istemal karein?** Jab aap chahte hain ki koi feature uske child classes mein inherit to ho, lekin aam public ke liye available na ho. Yeh inheritance ke liye bahut upyogi hai.

4.  **`public` (सबसे कम सख़्त)**
    * **Kaun access kar sakta hai?** Kahin se bhi. Poore program mein koi bhi class ise access kar sakti hai.
    * **Kab istemal karein?** Jab aap ek aisi functionality banana chahte hain jo har koi istemal kar sake, jaise `deposit()` ya `withdraw()` methods.

**Analogy**: Ek ghar sochiye.
* `public` -> Ghar ka Drawing Room. Koi bhi mehmaan aa sakta hai.
* `protected` -> Family Room. Sirf parivar ke log (`same package`) aur kuch khaas rishtedaar (`subclasses`) aa sakte hain.
* `default` -> Ghar ke andar ke kamre. Sirf parivar ke log (`same package`) hi jaa sakte hain.
* `private` -> Aapki personal tijori (safe). Sirf aap (`same class`) hi use khol sakte hain.

***

### **Q: What is the difference between a public and a private constructor?**
**A:**
* **Public Constructor**: Ek `public` constructor ko koi bhi class, kahin se bhi call kar sakti hai. Iska matlab hai ki koi bhi uss class ka object (`new ClassName()`) bana sakta hai. Yeh sabse aam tarika hai.

* **Private Constructor**: Ek `private` constructor ko sirf usi class ke andar se call kiya ja sakta hai. Iska matlab hai ki class ke bahar se koi bhi uss class ka object nahi bana sakta. Iska sabse bada istemal **Singleton Design Pattern** banane mein hota hai, jahan aap yeh sunishchit karna chahte hain ki ek class ka poore program mein sirf ek hi object bane.

***

## **2. Abstraction (ज़रूरी चीज़ें दिखाना)** 🎭

### **Q: What is Abstraction?**
**A:** **Abstraction** ka matlab hai user ko sirf zaroori jaankari dikhana aur parde ke peeche ki complex details ko chhipana. Yeh "kya karna hai" par focus karta hai, na ki "kaise karna hai" par.

**Analogy**: Jab aap car chalate hain, to aap steering wheel, accelerator aur brakes ka istemal karte hain. Aapko yeh janne ki zaroorat nahi ki engine ke andar kya ho raha hai. Yahan, steering wheel aur pedals ek abstraction hain.

***

### **Q: What is the difference between encapsulation and data abstraction?**
**A:** Yeh ek aam confusion hai.
* **Abstraction** ek **design principle** hai. Iska focus बाहरी look and feel par hota hai, yaani complexity ko chhipana.
* **Encapsulation** ek **implementation mechanism** hai. Iska focus data ko methods ke saath baandhne aur data ko hide karne par hota hai.

Aasan shabdon mein, **Encapsulation data ko chhipata hai, jabki Abstraction kaam karne ki complexity ko chhipata hai.** Encapsulation, abstraction ko haasil karne ka ek tareeka ho sakta hai.

***

### **Q: How can you achieve data abstraction?**
**A:** Java mein abstraction do mukhya tareekon se haasil kiya jaata hai:
1.  **Abstract Classes**: Aisi classes banakar jinka object nahi banaya ja sakta aur jinmein `abstract` methods hote hain (bina body ke).
2.  **Interfaces**: Ek 100% abstract blueprint banakar, jise classes implement karti hain.

***

## **3. Inheritance (विरासत)** 👨‍👩‍👧‍👦

### **Q: What is Inheritance and what is its purpose?**
**A:** **Inheritance** ek process hai jismein ek nayi class (jise **child** ya **subclass** kehte hain) ek purani class (jise **parent** ya **superclass** kehte hain) ke gunon (properties) aur kaam (methods) ko viraasat mein leti hai.

Iska mukhya **purpose** hai **code reusability (code ka dobara istemal)**. Isse aapko baar-baar same code likhne ki zaroorat nahi padti aur classes ke beech ek **"IS-A" relationship** (jaise, "A Car IS-A Vehicle") banta hai.

***

### **Q: What are the different types of inheritance?**
**A:** Inheritance ke mukhya prakar hain:
1.  **Single Inheritance**: Ek child class sirf ek parent class se inherit karti hai. (A -> B)
2.  **Multilevel Inheritance**: Ek class doosri class se inherit karti hai, aur woh class teesri class se inherit karti hai. (A -> B -> C)
3.  **Hierarchical Inheritance**: Ek parent class se kai child classes inherit karti hain. (A -> B, A -> C)
4.  **Multiple Inheritance**: Ek child class ek se zyada parent classes se inherit karti hai. (Java mein yeh classes ke saath possible nahi hai, sirf interfaces ke saath hai).
5.  **Hybrid Inheritance**: Upar diye gaye do ya do se zyada inheritance types ka combination.



***

### **Q: What are the limitations of inheritance?**
**A:**
* **Tightly Coupled**: Parent aur child classes aapas mein mazbooti se jud jaati hain. Parent class mein kiya gaya koi bhi badlav child class ko prabhavit kar sakta hai.
* **Slow Performance**: Inheritance mein ek method call ko resolve karne ke liye poori hierarchy mein travel karna pad sakta hai, jisse performance thodi kam ho sakti hai.
* **Complexity**: Agar inheritance ka design theek se na kiya jaye, to code bahut complex aur samajhne mein mushkil ho sakta hai.

***

### **Q: What is a subclass and a superclass?**
**A:**
* **Superclass (Parent Class)**: Woh class jiski properties aur methods ko doosri class inherit karti hai. Ise **base class** bhi kehte hain.
* **Subclass (Child Class)**: Woh class jo doosri class se properties aur methods inherit karti hai. Ise **derived class** bhi kehte hain.

***

### **Q: What is the Diamond Problem in the context of multiple inheritance?**
**A:** **Diamond Problem** ek aisi samasya hai jo multiple inheritance waali languages (jaise C++) mein aati hai.

Yeh tab hoti hai jab ek class `D` do classes `B` aur `C` se inherit karti hai, aur `B` aur `C` dono ek hi superclass `A` se inherit karti hain. Ab agar `A` mein koi method hai jise `B` aur `C` ne override kiya hai, aur `D` uss method ko call karta hai, to compiler confuse ho jaata hai ki woh `B` ke zariye wala method call kare ya `C` ke zariye wala. Isi confusion ko Diamond Problem kehte hain.

Java is samasya se bachne ke liye classes ke saath multiple inheritance support nahi karta.

***

## **4. Polymorphism (बहुरूपता)** 🎭

### **Q: What is Polymorphism?**
**A:** **Polymorphism** do shabdon se bana hai: "Poly" (matlab anek) aur "Morph" (matlab roop). Iska matlab hai **"ek naam, anek roop"**. OOPs mein, yeh ek object, variable, ya method ki alag-alag tarike se behave karne ki ability hai.

**Analogy**: Ek insaan. Woh office mein ek 'Employee' hai, ghar par ek 'Parent' hai, aur doston ke saath ek 'Friend' hai. Vyakti ek hi hai, lekin uske roop (behavior) alag-alag hain.

***

### **Q: What is the difference between static and dynamic polymorphism?**
**A:**
* **Static Polymorphism (Compile-time)**: Ismein, compiler ko program run hone se **pehle** hi pata hota hai ki kaunsa method call karna hai. Yeh **Method Overloading** ke zariye achieve kiya jaata hai. Isko **early binding** bhi kehte hain.

* **Dynamic Polymorphism (Run-time)**: Ismein, kaunsa method call hoga, yeh program ke **run hone ke waqt** decide hota hai, object ke actual type ke aadhar par. Yeh **Method Overriding** ke zariye achieve kiya jaata hai. Isko **late binding** bhi kehte hain.

***

### **Q: What is the difference between method overloading and method overriding?**
**A:**

| Feature                | Method Overloading                                          | Method Overriding                                         |
| :--------------------- | :---------------------------------------------------------- | :-------------------------------------------------------- |
| **Kahan hota hai?**    | Ek hi class ke andar.                                       | Parent aur Child classes ke beech.                        |
| **Kya same hota hai?** | Sirf method ka **naam**.                                    | Method ka **naam, parameters, aur return type** (mostly). |
| **Kya alag hota hai?** | Method ke **parameters** (ya to unki sankhya ya unka type). | Method ki **implementation** (body).                      |
| **Polymorphism Type**  | Compile-time (Static) Polymorphism.                         | Run-time (Dynamic) Polymorphism.                          |
| **Relationship**       | Koi relationship zaroori nahi.                              | **Inheritance (IS-A)** relationship zaroori hai.          |

---


## **Class & Object In-Depth** 🔬

### **Q: What is the difference between a static and a non-static method?**
**A:**
* **Non-static Method (Instance Method)**: Yeh method class ke **object (instance)** se juda hota hai. Ise call karne ke liye aapko pehle uss class ka object banana padta hai. Yeh class ke static aur non-static, dono tarah ke members ko access kar sakta hai.
    * **Example**: `myCar.getSpeed()` - Yahan `getSpeed()` ek particular car object ki speed batayega.

* **Static Method (Class Method)**: Yeh method poori **class** se juda hota hai, kisi ek object se nahi. Ise bina object banaye, seedhe class ke naam se call kiya ja sakta hai. Yeh sirf class ke **static members** ko hi access kar sakta hai.
    * **Example**: `Math.sqrt(25)` - Yahan `sqrt()` ko call karne ke liye `Math` class ka object banane ki zaroorat nahi hai.

**Analogy**: Ek `Car` class sochiye.
* `getColor()` ek **non-static** method hoga, kyunki har car (object) ka rang alag ho sakta hai.
* `getNumberOfWheels()` ek **static** method ho sakta hai, kyunki sabhi caron ke liye yeh value (4) same hai aur class ka ek universal feature hai.

***

### **Q: What is a static member (variable or method) in a class?**
**A:** Ek **static member** (chahe woh variable ho ya method) woh member hota hai jo class se belong karta hai, na ki uske individual objects se.

Iska matlab hai ki uski sirf **ek hi copy** banti hai jo uss class ke **sabhi objects aapas mein share karte hain**. Agar ek object static variable ki value badalta hai, to woh badlav baaki sabhi objects ke liye bhi dikhega.

**Analogy**: Ek college (`class`) mein, har student (`object`) ka apna Roll Number (`non-static variable`) hota hai. Lekin, college ka naam (`static variable`) sabhi students ke liye ek hi hota hai aur sabke ID card par wahi print hota hai.

***

### **Q: What is the role of the "this" keyword?**
**A:** `this` ek reference variable hai jo hamesha **current object** ko refer karta hai (yaani, woh object jiske andar se `this` ko call kiya gaya hai).

Iske mukhya role hain:
1.  **Instance variables aur parameters mein antar karna**: Jab constructor ya method ke parameter ka naam instance variable jaisa hi ho, to `this` ka istemal karke compiler ko bataya jaata hai ki hum instance variable ki baat kar rahe hain.
    * `this.name = name;`
2.  **Constructor chaining**: Ek constructor se usi class ka doosra constructor call karne ke liye (`this(...)`).
3.  **Current object ko pass karna**: Kisi method mein current object ko as an argument bhejne ke liye.

***

### **Q: What is the difference between a shallow copy and a deep copy?**
**A:** Jab hum ek object ki copy banate hain, to do tarah ki copy ho sakti hai:

* **Shallow Copy**: Ismein, sirf object ke top-level fields copy hote hain. Agar object ke andar koi doosra object (referenced object) hai, to uss object ki copy nahi banti, sirf uska **reference (memory address)** copy hota hai. Iska natija yeh hota hai ki original aur copied object, dono andar ke same object ko point karte hain. Agar aap ek mein badlav karenge, to woh doosre mein bhi dikhega.

* **Deep Copy**: Ismein, object ke top-level fields ke saath-saath uske andar ke **sabhi referenced objects bhi recursively copy hote hain**. Har referenced object ki ek nayi copy banti hai. Iska natija yeh hota hai ki original aur copied object ek doosre se poori tarah se azaad (independent) hote hain.

**Analogy**: Aapke paas ek file folder hai.
* **Shallow Copy**: Aapne folder ki ek copy banayi, lekin andar jo documents hain, unki copy banane ke bajaye unke shortcuts bana diye jo original documents ko hi point kar rahe hain.
* **Deep Copy**: Aapne folder ki copy banayi aur uske andar ke har document ki bhi alag-alag copy banakar naye folder mein rakhi.

***

### **Q: How much memory does a class occupy?**
**A:** Yeh ek trick question hai. Ek **class** memory occupy **nahi karti**. Class sirf ek blueprint ya template hai.

Memory uss class ka **object (instance)** occupy karta hai. Ek object kitni memory lega, yeh uske **non-static instance variables** par depend karta hai. `Static` variables ki memory alag se, class level par, sirf ek baar allocate hoti hai, na ki har object ke liye. Methods (code) bhi class ke saath store hote hain, har object ke saath alag se nahi.

***

### **Q: Is it always necessary to create objects from a class?**
**A:** Nahi, hamesha zaroori nahi hai.

Agar ek class mein sirf `static` methods aur `static` variables hain, to aap uski functionality ko bina object banaye, seedhe class ke naam se istemal kar sakte hain.

**Best Example**: Java ki `Math` class. Hum hamesha `Math.sqrt()` ya `Math.PI` likhte hain, kabhi bhi `Math m = new Math();` karke object nahi banate, kyunki uske saare members static hain.

***

## **Abstract Classes & Interfaces** ✍️

### **Q: What is an Abstract Class?**
**A:** Ek **Abstract Class** ek aisi class hai jiska aap **object nahi bana sakte** (`new` karke instantiate nahi kar sakte). Yeh ek adhoora blueprint hota hai jo doosri classes ke liye ek common template ka kaam karta hai.

Iske andar **abstract methods** (jinki body nahi hoti) aur **non-abstract (concrete) methods** (jinki body hoti hai) dono ho sakte hain. Jo bhi class is abstract class ko `extend` karegi, uski zimmedari hai ki woh saare abstract methods ko implement kare.

***

### **Q: What is an Interface and what is its purpose?**
**A:** Ek **Interface** ek 100% abstract blueprint hota hai. Yeh ek **contract** ki tarah kaam karta hai. Iske andar sirf methods ke signature hote hain (body nahi hoti, Java 8 se pehle).

**Purpose**:
1.  **100% Abstraction achieve karna**: Yeh batata hai ki ek object ko "kya karna chahiye", lekin yeh nahi batata "kaise karna chahiye".
2.  **Multiple Inheritance support karna**: Java mein ek class ek se zyada class ko `extend` nahi kar sakti, lekin woh ek se zyada interfaces ko `implement` kar sakti hai. Isse multiple inheritance jaisi functionality milti hai.

***

### **Q: What are the key differences between an abstract class and an interface?**
**A:**

| Feature                 | Abstract Class                                                                                                 | Interface                                                                                                                   |
| :---------------------- | :------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------- |
| **Methods**             | Ismein `abstract` (bina body ke) aur `non-abstract` (body ke saath) dono tarah ke methods ho sakte hain.       | Ismein by default saare methods `public abstract` hote hain. (Java 8+ se `default` aur `static` methods bhi ho sakte hain). |
| **Variables**           | Ismein `final`, `non-final`, `static`, `non-static` har tarah ke variables ho sakte hain.                      | Ismein variables by default `public static final` hote hain (yaani, constants).                                             |
| **Constructor**         | Iska apna constructor hota hai (jo child class se `super()` ke zariye call hota hai).                          | Iska koi constructor nahi hota.                                                                                             |
| **Inheritance**         | Ek class sirf **ek** hi abstract class ko `extend` kar sakti hai.                                              | Ek class **kai** interfaces ko `implement` kar sakti hai.                                                                   |
| **Keyword**             | `extends` keyword ka istemal hota hai.                                                                         | `implements` keyword ka istemal hota hai.                                                                                   |
| **Kab Istemal Karein?** | Jab aap kuch common code share karna chahte hain jo related classes istemal kar sakein. ("IS-A" relationship). | Jab aap ek contract define karna chahte hain jo unrelated classes bhi follow kar sakein. ("CAN-DO" relationship).           |
---


## **Object Lifecycle (ऑब्जेक्ट का जीवन चक्र)** 🔄

### **Q: What is a constructor?**
**A:** Ek **constructor** ek special method hota hai jo tab call hota hai jab kisi class ka object banaya jaata hai (`new` keyword se). Iska naam class ke naam jaisa hi hota hai aur iska koi return type nahi hota.

Iska mukhya kaam object ke **instance variables** ko shuruaati (initial) value dena hai.

**Analogy**: Jab aap ek naya ghar (`object`) khareedte hain, to constructor uss Mistri (`mechanic`) ki tarah hai jo ghar mein initial setup karta hai—jaise paani ka connection, bijli meter lagana, etc.

***

### **Q: What is a copy constructor? (Primarily C++)**
**A:** Ek **copy constructor** ek khaas tarah ka constructor hota hai jo ek naye object ko, pehle se maujood object ki a-to-z copy ke roop mein banata hai. Yeh apne argument mein usi class ke doosre object ka reference leta hai.

**Analogy**: Yeh objects ke liye ek high-quality photocopier machine ki tarah hai. Aap ek original document (`object`) daalte hain, aur machine ek bilkul nayi, hubahu copy (`new object`) bana deti hai.

***

### **Q: What is a destructor? (Primarily C++)**
**A:** Ek **destructor** ek special method hai jo tab automatically call hota hai jab ek object nasht (destroy) hota hai (yaani, jab uska scope khatam ho jaata hai ya use `delete` kiya jaata hai). Iska naam class ke naam ke aage ek tilde (`~`) lagakar banta hai (jaise `~ClassName()`).

Iska mukhya kaam object dwara istemal kiye gaye resources (jaise memory, files, ya network connections) ko azaad (release) karna hota hai, taaki resource leak na ho.

**Analogy**: Jab aap hotel ke kamre (`object`) se check-out karte hain, to destructor uss housekeeping staff ki tarah hai jo kamre ko saaf karta hai aur use agle guest ke liye taiyaar karta hai.

***

### **Q: What is Garbage Collection?**
**A:** **Garbage Collection** ek automatic memory management process hai, jo khaas kar Java aur C# jaisi languages mein hota hai.

**Garbage Collector (GC)** naam ka ek program background mein chalta rehta hai aur aise objects ko dhoondhta hai jinka ab code mein koi istemal nahi ho raha (yaani, unhe koi refer nahi kar raha). Phir, GC un "laawaris" objects dwara gheri hui memory ko apne aap saaf kar deta hai. Isse programmer ko memory manually manage karne ki chinta nahi rehti.

**Analogy**: Yeh ek sheher mein kaam karne wali automatic safai team ki tarah hai, jo sadak par khadi laawaris gaadiyon (`unreferenced objects`) ko dhoondhkar kabaadkhane (`memory cleanup`) bhej deti hai, taaki nayi gaadiyon ke liye jagah ban sake.

***

## **Advanced Concepts & Design Principles** 🧠

### **Q: What is the difference between early (static) and late (dynamic) binding?**
**A:** **Binding** ka matlab hai ek method call ko uske actual code se jodna. Yeh do tarah ka hota hai:

* **Early Binding (Static Binding)**: Yeh **compile-time** par hota hai. Yahan, compiler ko program run hone se pehle hi theek-theek pata hota hai ki kaunsa method call karna hai. Yeh **Method Overloading** mein istemal hota hai. Yeh tez (fast) hota hai.

* **Late Binding (Dynamic Binding)**: Yeh **run-time** par hota hai. Yahan, kaunsa method call hoga, iska faisla program ke chalne ke dauraan, object ke actual type ke aadhar par kiya jaata hai. Yeh **Method Overriding** mein istemal hota hai. Yeh flexible hota hai lekin thoda dheema ho sakta hai.

***

### **Q: What is Coupling and Cohesion in OOP?**
**A:** Yeh do principles hain jo software design ki quality ko naapte hain. Ek achhe software design mein **Low Coupling** aur **High Cohesion** hona chahiye.

* **Coupling (जुड़ाव)**: Yeh batata hai ki do classes ek doosre par kitna nirbhar (dependent) hain.
    * **Low Coupling (अच्छा)**: Classes azaad hain. Ek class mein badlav karne se doosri class par koi asar nahi padta.
    * **High Coupling (बुरा)**: Classes ek doosre se bahut zyada judi hui hain. Ek mein badlav karne se doosri bhi toot sakti hai.

* **Cohesion (एकजुटता)**: Yeh batata hai ki ek class ke andar ke members (methods aur variables) aapas mein kitne aache se jude hue hain aur ek hi kaam kar rahe hain.
    * **High Cohesion (अच्छा)**: Ek class sirf ek hi kaam karti hai aur use aache se karti hai.
    * **Low Cohesion (बुरा)**: Ek class biryani bhi bana rahi hai aur car bhi chala rahi hai (yaani, bahut saare alag-alag kaam kar rahi hai).

**Analogy**:
* **Coupling**: Low coupling ek USB port jaisa hai (koi bhi device lagao). High coupling ek ajeeb sa charger hai jo sirf ek hi phone model mein lagta hai.
* **Cohesion**: High cohesion ek aache se organize kiya gaya toolbox hai (saare screwdrivers ek jagah). Low cohesion ek "junk drawer" jaisa hai jismein sab kuch mix pada hai.

***

### **Q: What is the difference between Aggregation and Composition?**
**A:** Dono hi **"HAS-A" relationship** (ek object ke paas doosra object hona) ko darshate hain, lekin inki mazbooti mein fark hai.

* **Aggregation (कमज़ोर रिश्ता)**: Ismein, child object parent object ke bina bhi azaad roop se exist kar sakta hai. Agar parent object ko delete kar diya jaye, to child object delete nahi hota.
    * **Analogy**: Ek `Department` ke paas kai `Teachers` hote hain. Agar department band ho jaaye, to bhi teachers exist karte hain aur doosre department mein jaa sakte hain.

* **Composition (मजबूत रिश्ता)**: Ismein, child object parent object ka ek hissa (`part-of`) hota hai aur uske bina exist nahi kar sakta. Agar parent object ko delete kar diya jaye, to child object bhi apne aap delete ho jaata hai.
    * **Analogy**: Ek `Ghar` ke paas kai `Kamre` hote hain. Agar aap ghar ko tod denge, to kamre bhi apne aap nasht ho jaayenge.

***

### **Q: What is the principle of "Composition over Inheritance"?**
**A:** Yeh ek design salah hai jo kehti hai: **"Jab bhi possible ho, Inheritance (IS-A) ke bajaye Composition (HAS-A) ka istemal karein."**

**Aisa kyun?** Kyunki Inheritance, classes ke beech ek bahut hi **tight coupling** bana deta hai. Composition zyada **flexible** hota hai. Composition se aap run-time par bhi kisi object ka behavior badal sakte hain, jabki Inheritance compile-time par fix ho jaata hai.

***

### **Q: What are the SOLID principles of design?**
**A:** **SOLID** paanch design principles ka ek acronym hai jo Object-Oriented code ko behtar, flexible aur maintainable banane mein madad karte hain.

* **S - Single Responsibility Principle**: Ek class ke paas badalne ka sirf **ek hi kaaran** hona chahiye (yaani, ek class ko sirf ek hi kaam karna chahiye).
* **O - Open/Closed Principle**: Software ko **extension ke liye open** hona chahiye, lekin **modification ke liye closed** hona chahiye (yaani, naya feature jodne ke liye purana code na badalna pade).
* **L - Liskov Substitution Principle**: Child class ke objects parent class ke objects ki jagah bina kisi problem ke istemal kiye jaa sakne chahiye.
* **I - Interface Segregation Principle**: Clients ko aise interfaces par depend hone ke liye majboor nahi karna chahiye jinka woh istemal nahi karte (bade-bade interfaces ke bajaye chote aur specific interfaces banayein).
* **D - Dependency Inversion Principle**: High-level modules ko low-level modules par depend nahi karna chahiye. Dono ko abstractions (interfaces) par depend karna chahiye.

---
## **Language-Specific Concepts (भाषा-विशेष अवधारणाएं)** C++/Java

### **Q: What is the difference between a Class and a Struct? (Primarily C++)**
**A:** C++ mein `class` aur `struct` lagbhag ek jaise hi hain, lekin unmein ek mukhya antar hai: **default access**.

* **`struct`**: Iske members by default **public** hote hain. Yani, agar aap `public` ya `private` nahi likhte, to sab kuch public maana jayega.
* **`class`**: Iske members by default **private** hote hain.

**Istemal ka Antar**: Rivaaj (convention) ke anusaar, `struct` ka istemal simple data containers ke liye kiya jaata hai jismein sirf data hota hai (Plain Old Data). Jabki, `class` ka istemal bade objects ke liye kiya jaata hai jinke paas data (variables) aur behavior (methods) dono hote hain, aur jahan encapsulation aur inheritance jaise features zaroori hote hain. Java mein `struct` nahi hota.

***

### **Q: What is operator overloading? (Primarily C++)**
**A:** **Operator Overloading** C++ ka ek feature hai jo programmer ko maujooda operators (jaise `+`, `-`, `==`, `<<`) ko apne banaye hue custom data types (classes) ke liye ek naya matlab dene ki anumati deta hai.

**Analogy**: Aap `+` operator ko sikha sakte hain ki do `ComplexNumber` objects ko kaise joda jaaye, ya `==` operator ko sikha sakte hain ki do `Employee` objects ko kab barabar maana jaaye. Isse code padhne mein aasan aur swabhavik (intuitive) lagta hai. Java yeh feature support nahi karta.

***

### **Q: What is a virtual function and a pure virtual function? (Primarily C++)**
**A:** Dono hi C++ mein run-time polymorphism haasil karne ke liye istemal hote hain.

* **Virtual Function**: Yeh base class ka ek member function hota hai jiske aage `virtual` keyword lagaya jaata hai. Yeh compiler ko batata hai ki is function ko child class mein **override** kiya ja sakta hai. Ek `virtual` function ki base class mein apni default implementation ho sakti hai.

* **Pure Virtual Function**: Yeh ek aisa virtual function hai jiski base class mein koi implementation nahi hoti. Ise ` = 0;` laga kar declare kiya jaata hai (jaise, `virtual void draw() = 0;`). Jis class mein ek bhi pure virtual function hota hai, woh apne aap ek **abstract class** ban jaati hai, aur uske child classes ko us pure virtual function ko zaroor implement karna padta hai.

**Aasan shabdon mein**: Ek `virtual function` kehta hai, "Yeh mera default kaam hai, lekin agar tum chaho to ise behtar tareeke se kar sakte ho." Ek `pure virtual function` kehta hai, "Yeh kaam karna hai, lekin kaise karna hai, yeh tumhe (child class ko) hi batana hoga."

***

### **Q: What is the purpose of the `final` keyword in Java?**
**A:** Java mein `final` keyword kisi bhi cheez ko **aparivartansheel (unchangeable)** banane ke liye istemal hota hai. Iske teen istemal hain:

1.  **`final` variable**: Iski value ek baar assign hone ke baad dobara badli nahi ja sakti. Yeh ek **constant** ban jaata hai. (Jaise `final double PI = 3.14;`).
2.  **`final` method**: Is method ko child class mein **override nahi kiya ja sakta**.
3.  **`final` class**: Is class ko **inherit nahi kiya ja sakta** (yaani, iski koi child class nahi banayi ja sakti). Java mein `String` class iska ek achha udaharan hai.

***

### **Q: What is the purpose of the `super` keyword in Java?**
**A:** `super` keyword ek reference variable hai jo hamesha **immediate parent class** ke object ko refer karta hai.

Iske do mukhya kaam hain:
1.  **Parent class ke constructor ko call karna**: Child class ke constructor se parent class ke constructor ko call karne ke liye (`super(arguments)`). Yeh hamesha constructor ki pehli line honi chahiye.
2.  **Parent class ke members ko access karna**: Jab child class mein parent class ke jaisa hi koi method ya variable ho, to `super` ka istemal karke parent version ko access kiya ja sakta hai (jaise, `super.methodName()`).

***

## **Exception Handling (अपवाद प्रबंधन)** ⚙️

### **Q: What is the difference between an exception and an error?**
**A:** Java mein, `Exception` aur `Error` dono `Throwable` class ke child hain, lekin unmein ek bada fark hai.

* **Exception**: Yeh aisi samasyaayein hain jinhein ek program ke andar **handle kiya ja sakta hai** (`try-catch` se). Yeh aam taur par program ki galti ya unexpected situation se aati hain jinse recover kiya ja sakta hai.
    * **Example**: `FileNotFoundException`, `NullPointerException`.

* **Error**: Yeh aisi gambhir samasyaayein hain jinhein ek program ko handle **nahi karna chahiye**. Yeh aam taur par JVM (Java Virtual Machine) ke level par hoti hain aur inhein recover karna lagbhag namumkin hota hai. Program aam taur par crash ho jaata hai.
    * **Example**: `OutOfMemoryError` (memory khatam ho jana), `StackOverflowError`.

**Aasan shabdon mein**: `Exception` ek flat tyre jaisa hai jise aap theek kar sakte hain. `Error` ek engine failure jaisa hai, jiske baad gaadi aage nahi badh sakti.

***

### **Q: What is the purpose of the `finally` block?**
**A:** `finally` block `try-catch` statement ka ek hissa hai. Iska mukhya uddeshya "cleanup code" ko execute karna hai.

`finally` block mein likha gaya code **hamesha execute hota hi hai**, chahe `try` block mein exception aaye ya na aaye, aur agar aaye to woh `catch` block mein pakda jaaye ya na pakda jaaye.

**Sabse Zaroori Istemal**: Aise resources ko band karna jo program ke baad khule na reh jaayein, jaise files (`file.close()`), database connections, ya network sockets. Isse resource leak hone se bachta hai.

----
# **Questions To look Forward**

* Make **class hierarchy**
* Show **Encapsulation, Inheritance, Polymorphism, Abstraction**
* Define only **class names, fields, and method signatures** (no full implementation needed).

## 🔹 Beginner Level (Focus on 4 OOP pillars)

1. **Design a Library Management System**

   * Books, Members, Borrowing/Returning, Fines.
2. **Design an Online Shopping Cart System**

   * Products, Cart, Discounts, Payment.
3. **Design a Hospital Management System**

   * Patients, Doctors, Appointments, Billing.
4. **Design an ATM Machine System**

   * Accounts, Withdrawals, Deposits, Balance Inquiry.
5. **Design a Food Delivery System**

   * Restaurants, Menu, Orders, Delivery Agents.

---

## 🔹 Intermediate Level (Inheritance + Polymorphism focus)

6. **Design a Zoo Management System**

   * Different Animals, Food, Habitats.
7. **Design an Online Movie Ticket Booking System**

   * Theaters, Seats, Shows, Payment.
8. **Design a Hotel Booking System**

   * Rooms (Single/Double/Suite), Reservation, Payment.
9. **Design an Employee Payroll System**

   * Different Employees (Full-time, Part-time, Contractor), Salary Calculation.
10. **Design a School Management System**

    * Students, Teachers, Subjects, Exams, Results.

---

## 🔹 Advanced Level (Scalability + Real-life OOD patterns)

11. **Design a Ride Sharing System (like Uber/Ola)**

    * Drivers, Riders, Rides, Payments.
12. **Design an Airline Reservation System**

    * Flights, Seats, Passengers, Bookings.
13. **Design an Online Auction System (like eBay)**

    * Items, Bids, Users, Payment.
14. **Design a File Storage System (like Google Drive)**

    * Files, Folders, Permissions, Sharing.
15. **Design a Chess Game**

    * Pieces, Board, Moves, Game Rules.

---

## 🔹 Bonus (Very High-level / Fun practice)

16. **Design a Vending Machine**

    * Products, Coins, Transactions, Inventory.
17. **Design a Music Streaming System (like Spotify)**

    * Songs, Playlists, Users, Subscriptions.
18. **Design a Social Media System (like Twitter)**

    * Users, Posts, Followers, Notifications.
19. **Design a Learning Management System (like Coursera)**

    * Courses, Students, Instructors, Assignments.
20. **Design a Parking Ticket Violation System**

    * Cars, Violations, Fines, Officers.

---
## Library Management System ka C++ Code

Yahan C++ code hai jo ek Library Management System ke liye class hierarchy define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ko dikhaya gaya hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward declaration taaki Member class Book ko use kar sake
class Book;

// ===================================
// == ABSTRACTION & BASE CLASS ==
// ===================================
// Yeh ek abstract base class hai. Iska object nahi ban sakta.
// Yeh ek common interface (template) provide karti hai Member jaise derived classes ke liye.
class Person {
protected:
    // Protected members derived class access kar sakti hai
    string name;
    int id;

public:
    // Pure virtual function, isko derived class mein define karna zaroori hai (Abstraction)
    virtual void displayDetails() = 0;
};

// ===================================
// == ENCAPSULATION ==
// ===================================
// Book class data (title, author) aur uss data par kaam karne wale functions ko ek saath rakhti hai.
class Book {
private:
    // Private members ko class ke bahar se directly access nahi kiya ja sakta (Encapsulation)
    string title;
    string author;
    string isbn;
    bool isAvailable;

public:
    // Constructor book object ko initialize karne ke liye
    Book(string title, string author, string isbn);

    // Public methods data ko access aur modify karne ke liye
    string getTitle();
    string getISBN();
    bool checkAvailability();
    void updateStatus(bool status);
    void displayBookDetails();
};

// ===================================
// == INHERITANCE & POLYMORPHISM ==
// ===================================
// Member class, Person class ki saari properties aur methods inherit karti hai.
class Member : public Person {
private:
    // Member ke specific details
    vector<Book*> borrowedBooks; // Member ne kaunsi books li hain
    double finesDue;

public:
    // Constructor Member object ko initialize karne ke liye
    Member(string name, int id);

    // Member ke specific functions
    void borrowBook(Book* book);
    void returnBook(Book* book);
    void calculateFine();

    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    void displayDetails() override;
};

// ===================================
// == MAIN CONTROLLER CLASS ==
// ===================================
// Library class poore system ko manage karti hai.
// Yeh books aur members ko ek jagah encapsulate karti hai.
class Library {
private:
    vector<Book> bookCollection;
    vector<Member> members;

public:
    // Library mein nayi book add karne ke liye
    void addBook(const Book& newBook);

    // Naya member register karne ke liye
    void registerMember(const Member& newMember);

    // Kisi member ko book issue karne ka process
    void issueBook(int memberId, string isbn);

    // Member se book wapas lene ka process
    void receiveBook(int memberId, string isbn);

    // Book ko uske title se search karna
    void findBookByTitle(string title);

    // Member ko uski ID se search karna
    void findMemberById(int memberId);
};

// main function jahan se program shuru hoga
int main() {
    // Yahan par Library class ka object banakar saare operations perform kiye ja sakte hain.
    // Abhi ke liye yeh khaali hai kyunki sirf design dikhana tha.
    cout << "Library Management System Design Ready!" << endl;
    return 0;
}
```

-----

### OOP Concepts Kaise Use Huye Hain? 🤔

1.  **Encapsulation (Data Hiding)**

      * Har class (jaise `Book`, `Member`) apne data members (`title`, `name`, etc.) ko `private` rakhti hai.
      * Iss data ko access ya modify karne ke liye `public` methods (jaise `getTitle()`, `borrowBook()`) diye gaye hain. Isse data safe rehta hai.

2.  **Inheritance (Virasat)**

      * `Member` class `Person` class se inherit karti hai.
      * Iska matlab hai ki `Member` ke paas `Person` ke saare `protected` members (`name`, `id`) aur methods aa jaate hain. Yeh code reusability ko badhata hai.

3.  **Polymorphism (Anek Roop)**

      * `Person` class mein `displayDetails()` function ko `virtual` banaya gaya hai.
      * `Member` class isko `override` karke apni specific details display karti hai.
      * Agar hum `Person* ptr = new Member();` banate hain, toh `ptr->displayDetails();` call karne par `Member` ka version run hoga. Ise **Runtime Polymorphism** kehte hain.

4.  **Abstraction (Zaroori Cheezein Dikhana)**

      * `Person` ek **abstract class** hai kyunki usmein ek pure virtual function (`virtual void displayDetails() = 0;`) hai.
      * Hum `Person` class ka object nahi bana sakte. Yeh sirf ek blueprint (khaka) hai jo batata hai ki har "Person" type ke object mein `displayDetails()` function hona hi chahiye, lekin kaise hoga, yeh derived class (`Member`) decide karegi.
---



## Online Shopping Cart System ka C++ Code

Yeh C++ code ek Online Shopping System ke liye class hierarchy define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ko dikhaya gaya hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// ===================================
// == ENCAPSULATION ==
// ===================================
// Product class, data (name, price) aur functions ko ek saath rakhti hai.
class Product {
private:
    // Private members ko class ke bahar se directly access nahi kiya ja sakta (Encapsulation)
    int productId;
    string name;
    double price;

public:
    // Constructor naye product ko banane ke liye
    Product(int id, string name, double price);

    // Public methods, private data ko access karne ke liye
    int getId();
    double getPrice();
    void displayProductDetails();
};


// ===================================
// == ABSTRACTION & POLYMORPHISM (For Discounts) ==
// ===================================
// Yeh ek abstract class hai jo ek discount ka basic template batati hai.
// Iska object nahi ban sakta, yeh sirf inheritance ke liye hai.
class Discount {
public:
    // Pure virtual function. Har type ke discount ko isse implement karna hi hoga (Abstraction).
    // Isse hum alag-alag discount types ko ek hi tarike se apply kar payenge (Polymorphism).
    virtual double applyDiscount(double totalAmount) = 0;
};

// PercentageDiscount class, Discount class se inherit ho rahi hai
class PercentageDiscount : public Discount {
private:
    double percentage;

public:
    PercentageDiscount(double percent);
    // Base class ke virtual function ko override kiya gaya hai
    double applyDiscount(double totalAmount) override;
};

// FixedAmountDiscount class, Discount class se inherit ho rahi hai
class FixedAmountDiscount : public Discount {
private:
    double flatAmount;

public:
    FixedAmountDiscount(double amount);
    // Base class ke virtual function ko override kiya gaya hai
    double applyDiscount(double totalAmount) override;
};


// ===================================
// == ABSTRACTION & POLYMORPHISM (For Payment) ==
// ===================================
// Payment ke liye ek abstract base class.
class PaymentStrategy {
public:
    // Har payment method ko 'pay' function define karna hoga.
    virtual void pay(double amount) = 0;
};

// CreditCardPayment class, PaymentStrategy se inherit ho rahi hai
class CreditCardPayment : public PaymentStrategy {
private:
    string cardNumber;
    string nameOnCard;

public:
    CreditCardPayment(string num, string name);
    void pay(double amount) override;
};

// UpiPayment class, PaymentStrategy se inherit ho rahi hai
class UpiPayment : public PaymentStrategy {
private:
    string upiId;

public:
    UpiPayment(string id);
    void pay(double amount) override;
};


// ===================================
// == MAIN CONTROLLER CLASS ==
// ===================================
// ShoppingCart class poore cart ke logic ko manage karti hai.
class ShoppingCart {
private:
    vector<Product> items;
    double totalAmount;

public:
    // Cart mein naya product add karne ke liye
    void addProduct(const Product& product);

    // Cart se product hatane ke liye
    void removeProduct(int productId);

    // Cart ka current total calculate karne ke liye
    double calculateTotal();

    // Cart ke saare items dikhane ke liye
    void viewCart();
    
    // Final bill pay karne ke liye. Yahan polymorphism ka use hoga.
    // Hum koi bhi discount ya payment method pass kar sakte hain.
    void checkout(Discount* discount, PaymentStrategy* paymentMethod);
};


// main function jahan se program shuru hoga
int main() {
    // Yahan par ShoppingCart ka object banakar saare operations perform kiye ja sakte hain.
    cout << "Online Shopping Cart System Design Ready!" << endl;
    return 0;
}
```

-----

### OOP Concepts Kaise Use Huye Hain? 🤔

1.  **Encapsulation (Data Hiding)**

      * `Product` aur `ShoppingCart` jaisi classes apne data members (`name`, `price`, `items`) ko `private` rakhti hain.
      * Iss data ko access karne ke liye `public` methods (jaise `getPrice()`, `addProduct()`) diye gaye hain. Isse data safe aur organized rehta hai.

2.  **Inheritance (Virasat)**

      * Discount ke liye humne ek base class `Discount` banayi hai. `PercentageDiscount` aur `FixedAmountDiscount` uss se inherit karti hain.
      * Isi tarah, `CreditCardPayment` aur `UpiPayment` classes `PaymentStrategy` base class se inherit karti hain. Yeh code ko reuse karne mein madad karta hai.

3.  **Abstraction (Zaroori Cheezein Dikhana)**

      * `Discount` aur `PaymentStrategy` **abstract classes** hain. Unke andar pure virtual functions (`= 0;` wale) hain.
      * Iska matlab hai ki woh sirf ek contract ya template provide karti hain. Koi bhi class jo unse inherit karegi, usse `applyDiscount()` ya `pay()` function ko define karna hi padega. Hum yeh chinta nahi karte ki discount *kaise* apply hoga, bas yeh pata hai ki *hoga*.

4.  **Polymorphism (Anek Roop)**

      * `ShoppingCart` ke `checkout` method mein hum `Discount*` type ka pointer lete hain. Is pointer mein hum `PercentageDiscount` ya `FixedAmountDiscount` ka object bhej sakte hain. Jab `discount->applyDiscount()` call hoga, toh C++ automatically sahi object ka function call karega.
      * Yahi concept `PaymentStrategy*` ke saath bhi use hota hai. Ise **Runtime Polymorphism** kehte hain aur isse system bahut flexible ho jaata hai.


---



## Hospital Management System ka C++ Code

Yeh C++ code ek Hospital Management System ke liye class hierarchy ko define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ke concepts ko istemal kiya gaya hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward declarations taaki classes ek doosre ko use kar sakein
class Doctor;
class Patient;

// ===================================
// == ABSTRACTION & INHERITANCE (Base Class) ==
// ===================================
// Person ek abstract class hai. Doctor aur Patient dono hi Person hain.
// Isse code dobara likhne ki zaroorat nahi padti (Inheritance).
class Person {
protected:
    // Protected members ko derived classes (Doctor, Patient) access kar sakti hain
    int id;
    string name;
    int age;

public:
    // Pure virtual function. Har derived class ko isse define karna hi hoga (Abstraction).
    virtual void displayDetails() = 0;
};


// ===================================
// == INHERITANCE & POLYMORPHISM ==
// ===================================
// Doctor class, Person class se inherit ho rahi hai.
class Doctor : public Person {
private:
    // Doctor ke specific details
    string specialization;
    vector<string> availableSlots; // Doctor kab available hai

public:
    // Constructor naye doctor ko system mein add karne ke liye
    Doctor(int id, string name, string spec);

    // Doctor ki availability check karne ke liye
    void checkAvailability();

    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    void displayDetails() override;
};


// Patient class, Person class se inherit ho rahi hai.
class Patient : public Person {
private:
    // Patient ke specific details
    string medicalHistory;
    int doctorId; // Patient kis doctor se consult kar raha hai

public:
    // Constructor naye patient ko register karne ke liye
    Patient(int id, string name, string history);

    // Patient ki medical history update karne ke liye
    void updateMedicalHistory(string newDetails);

    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    void displayDetails() override;
};


// ===================================
// == ENCAPSULATION ==
// ===================================
// Appointment class, data aur functions ko ek saath encapsulate karti hai.
class Appointment {
private:
    int appointmentId;
    int doctorId;
    int patientId;
    string appointmentTime;
    string status; // Jaise "Scheduled", "Completed", "Cancelled"

public:
    // Constructor naya appointment book karne ke liye
    Appointment(int id, int docId, int patId, string time);

    // Appointment ka status update karne ke liye
    void updateStatus(string newStatus);

    // Appointment ki details dikhane ke liye
    void displayAppointmentDetails();
};


// Bill class, billing se judi saari jaankari manage karti hai.
class Bill {
private:
    int billId;
    int patientId;
    double amount;
    bool isPaid;

public:
    // Constructor bill generate karne ke liye
    Bill(int id, int pId, double amt);

    // Payment process karne ke liye
    void processPayment(double paidAmount);

    // Bill ki details dikhane ke liye
    void displayBillDetails();
};


// ===================================
// == MAIN CONTROLLER CLASS ==
// ===================================
// Hospital class poore system ke operations ko manage karti hai.
class Hospital {
private:
    vector<Doctor> doctors;
    vector<Patient> patients;
    vector<Appointment> appointments;
    vector<Bill> bills;

public:
    // Naye doctor ko hospital staff mein add karna
    void addDoctor(const Doctor& doc);

    // Naye patient ko hospital mein register karna
    void registerPatient(const Patient& pat);

    // Doctor aur Patient ke liye appointment book karna
    void bookAppointment(int docId, int patId, string time);

    // Patient ke liye bill generate karna
    void generateBillForPatient(int patientId, double amount);
};


// main function jahan se program shuru hoga
int main() {
    // Yahan par Hospital class ka object banakar saare operations manage kiye ja sakte hain.
    cout << "Hospital Management System Design Ready!" << endl;
    return 0;
}

```

-----

### OOP Concepts Kaise Use Huye Hain? 🏥

1.  **Encapsulation (Data Hiding)**

      * Har class jaise `Appointment` aur `Bill` apne data members (`appointmentId`, `amount`, etc.) ko `private` rakhti hai.
      * In private members ko access karne ke liye `public` methods diye gaye hain, jaise `updateStatus()` ya `processPayment()`. Isse data galat istemal se bacha rehta hai.

2.  **Inheritance (Virasat)**

      * `Doctor` aur `Patient` dono classes `Person` class ki properties ko inherit karti hain.
      * Isse `name`, `id`, `age` jaise common attributes ko dobara likhne ki zaroorat nahi padti aur code saaf rehta hai.

3.  **Abstraction (Zaroori Cheezein Dikhana)**

      * `Person` ek **abstract class** hai, jiska `displayDetails()` function pure virtual hai (`= 0;`).
      * Yeh class ek rule banati hai ki har "Person" (chahe woh Doctor ho ya Patient) ke paas apni details display karne ka ek tarika hona chahiye. Implementation ki detail chhupa di jaati hai.

4.  **Polymorphism (Anek Roop)**

      * `displayDetails()` function `Person` class mein `virtual` hai aur `Doctor` aur `Patient` dono classes mein `override` kiya gaya hai.
      * Iska fayda yeh hai ki hum `Person*` pointer se `Doctor` aur `Patient` dono ke objects ko point kar sakte hain, aur jab `ptr->displayDetails()` call karenge, toh C++ apne aap sahi object ka function (Doctor ka ya Patient ka) call karega. Ise **Runtime Polymorphism** kehte hain.

---


## ATM Machine System ka C++ Code

Yeh C++ code ek ATM Machine System ke liye class hierarchy ko define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ke concepts ko istemal kiya gaya hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// ===================================
// == ENCAPSULATION ==
// ===================================
// Account class customer ke bank account ki saari jaankari rakhti hai.
// Data members private hain aur unhe access karne ke liye public methods hain.
class Account {
private:
    string accountNumber;
    string accountHolderName;
    double balance;

public:
    // Constructor naya account banane ke liye
    Account(string accNum, string holderName, double initialBalance);

    // Account se paise nikalne ke liye
    void withdraw(double amount);

    // Account mein paise jama karne ke liye
    void deposit(double amount);

    // Current balance check karne ke liye
    double getBalance();

    // Account number get karne ke liye
    string getAccountNumber();

    // Account ki details display karne ke liye
    void displayAccountDetails();
};

// ===================================
// == ABSTRACTION & INHERITANCE (Base Class) ==
// ===================================
// Yeh ek abstract class hai jo kisi bhi transaction ka blueprint hai.
// Iska object nahi ban sakta, yeh sirf inheritance ke liye hai.
class Transaction {
protected:
    int transactionId;
    
public:
    // Pure virtual function. Har type ke transaction ko isse implement karna hi hoga (Abstraction).
    // Yeh batata hai ki har transaction "execute" hoga, par kaise, woh child class batayegi.
    virtual void executeTransaction(Account* account) = 0;
};

// ===================================
// == INHERITANCE & POLYMORPHISM ==
// ===================================
// WithdrawalTransaction class, Transaction se inherit ho rahi hai.
class WithdrawalTransaction : public Transaction {
private:
    double amount;

public:
    WithdrawalTransaction(int transId, double amt);
    
    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    void executeTransaction(Account* account) override;
};

// DepositTransaction class, Transaction se inherit ho rahi hai.
class DepositTransaction : public Transaction {
private:
    double amount;

public:
    DepositTransaction(int transId, double amt);

    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    void executeTransaction(Account* account) override;
};

// BalanceInquiryTransaction class, Transaction se inherit ho rahi hai.
class BalanceInquiryTransaction : public Transaction {
public:
    BalanceInquiryTransaction(int transId);

    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    void executeTransaction(Account* account) override;
};

// ===================================
// == MAIN CONTROLLER CLASS ==
// ===================================
// ATM class poori machine ke operations ko manage karti hai.
class ATM {
private:
    // Yeh ek dummy database hai, real world mein yeh bank ke server se connect hoga
    map<string, Account> bankDatabase;
    Account* currentAccount;

public:
    // ATM start karne aur accounts load karne ke liye
    ATM();

    // User ko uske card/account number se authenticate karna
    bool authenticateUser(string accountNumber);

    // User se transaction type select karwana (Withdraw, Deposit, etc.)
    void selectTransaction();
    
    // Transaction ko anjaam dena. Yahan polymorphism ka asli istemal hoga.
    void performTransaction(Transaction* transaction);
};


// main function jahan se program shuru hoga
int main() {
    // Yahan par ATM class ka object banakar system ko chalaya ja sakta hai.
    cout << "ATM Machine System Design Ready!" << endl;
    return 0;
}
```

-----

### OOP Concepts Kaise Use Huye Hain? 🏧

1.  **Encapsulation (Data Hiding)**

      * **`Account`** class mein `balance` jaisa zaroori data **`private`** hai. Ise bahar se direct nahi badla ja sakta.
      * Paise nikalne ya jama karne ke liye **`public`** methods jaise **`withdraw()`** aur **`deposit()`** ka istemal karna padta hai, jo internal logic (jaise balance check karna) ko handle karte hain.

2.  **Inheritance (Virasat)**

      * Humne ek common base class **`Transaction`** banayi hai.
      * **`WithdrawalTransaction`**, **`DepositTransaction`**, aur **`BalanceInquiryTransaction`** jaisi specific classes ne uss se inherit kiya hai. Isse har transaction class ko baar-baar `transactionId` jaisi common cheezein define nahi karni padti.

3.  **Abstraction (Zaroori Cheezein Dikhana)**

      * **`Transaction`** ek **abstract class** hai, jismein ek pure virtual function **`executeTransaction() = 0;`** hai.
      * Yeh class ek "contract" banati hai ki har transaction ko execute karna zaroori hai, lekin yeh nahi batati ki *kaise* karna hai. Yeh detail child classes (jaise `WithdrawalTransaction`) par chhod di jaati hai.

4.  **Polymorphism (Anek Roop)**

      * Yeh sabse powerful concept hai yahan. **`ATM`** class mein **`performTransaction(Transaction* transaction)`** method hai.
      * Yeh method `Transaction` type ka pointer leta hai. Hum ismein `WithdrawalTransaction`, `DepositTransaction`, ya `BalanceInquiryTransaction` kisi ka bhi object bhej sakte hain.
      * Jab `transaction->executeTransaction()` call hota hai, toh C++ automatically pata laga leta hai ki pointer ke peeche kaunsa object hai aur usi ka function call karta hai. Isse ATM ka code bahut saaf aur flexible rehta hai.

---

## Food Delivery System ka C++ Code

Yeh C++ code ek Food Delivery System ke liye class hierarchy ko define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ke concepts ko istemal kiya gaya hai.

```cpp
#include <bits/stdc++.hh>
using namespace std;

// Forward declarations
class Order;
class Customer;
class DeliveryAgent;

// ===================================
// == ENCAPSULATION ==
// ===================================
// Ek single food item ko represent karne ke liye.
class MenuItem {
private:
    int itemId;
    string name;
    double price;
    bool isVeg;

public:
    // Constructor naye menu item ko banane ke liye
    MenuItem(int id, string name, double price, bool isVeg);

    // Item ki details get karne ke liye public methods
    string getName();
    double getPrice();
};

// Restaurant ki saari details yahan manage hongi.
class Restaurant {
private:
    int restaurantId;
    string name;
    string cuisine; // Jaise "Italian", "North Indian"
    vector<MenuItem> menu;
    double rating;

public:
    // Constructor naye restaurant ko register karne ke liye
    Restaurant(int id, string name, string cuisine);

    // Menu mein naya item add karne ke liye
    void addToMenu(const MenuItem& item);

    // Restaurant ka poora menu dikhane ke liye
    void displayMenu();

    // Restaurant ki details display karne ke liye
    void displayRestaurantDetails();
};

// ===================================
// == ABSTRACTION & INHERITANCE (Base Class) ==
// ===================================
// User ek abstract class hai. Customer aur DeliveryAgent dono hi User hain.
class User {
protected:
    int userId;
    string name;
    string contactNumber;

public:
    // Pure virtual function. Har derived class ko isse define karna hi hoga (Abstraction).
    virtual void displayProfile() = 0;
};

// Customer class, User class se inherit ho rahi hai.
class Customer : public User {
private:
    string address;
    vector<Order*> orderHistory;

public:
    Customer(int id, string name, string phone, string addr);
    void placeOrder(Order* order);
    void viewOrderHistory();
    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    void displayProfile() override;
};

// DeliveryAgent class, User class se inherit ho rahi hai.
class DeliveryAgent : public User {
private:
    string vehicleNumber;
    bool isAvailable;
    Order* currentDelivery;

public:
    DeliveryAgent(int id, string name, string phone, string vehicle);
    void acceptDelivery(Order* order);
    void updateDeliveryStatus(string status);
    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    void displayProfile() override;
};

// ===================================
// == ABSTRACTION & POLYMORPHISM (For Payment) ==
// ===================================
// Payment ke liye ek abstract base class (Extra Feature).
class PaymentMethod {
public:
    virtual void processPayment(double amount) = 0;
};

class UpiPayment : public PaymentMethod {
private:
    string upiId;
public:
    UpiPayment(string id);
    void processPayment(double amount) override;
};

class CardPayment : public PaymentMethod {
private:
    string cardNumber;
public:
    CardPayment(string num);
    void processPayment(double amount) override;
};

// ===================================
// == MAIN LOGIC CLASS ==
// ===================================
// Order class saari cheezon ko jodti hai - Customer, Restaurant, aur Delivery Agent.
class Order {
private:
    int orderId;
    Customer* customer;
    Restaurant* restaurant;
    vector<MenuItem> orderedItems;
    DeliveryAgent* deliveryAgent;
    double totalBill;
    string orderStatus; // Jaise "Placed", "Preparing", "Out for Delivery", "Delivered"

public:
    // Constructor naya order place karne ke liye
    Order(int id, Customer* cust, Restaurant* rest);

    // Order mein item add karne ke liye
    void addItemToOrder(const MenuItem& item);

    // Order ke liye delivery agent assign karna
    void assignDeliveryAgent(DeliveryAgent* agent);

    // Bill calculate aur generate karna
    void generateBill();
    
    // Order ka final payment karna (Polymorphism ka use)
    void checkout(PaymentMethod* payment);

    // Order ka status track karne ke liye
    void trackOrder();
};

// ===================================
// == MAIN CONTROLLER CLASS ==
// ===================================
// FoodDeliverySystem poore platform ko manage karta hai.
class FoodDeliverySystem {
private:
    vector<Restaurant> restaurants;
    vector<Customer> customers;
    vector<DeliveryAgent> deliveryAgents;
    vector<Order> activeOrders;

public:
    // Naya restaurant platform par add karna
    void addRestaurant(const Restaurant& rest);

    // Naye customer ko register karna
    void registerCustomer(const Customer& cust);

    // Naye delivery agent ko hire karna
    void onboardDeliveryAgent(const DeliveryAgent& agent);

    // Order place karne ka poora process handle karna
    void createOrder(int customerId, int restaurantId);
};

// main function jahan se program shuru hoga
int main() {
    // Yahan par FoodDeliverySystem ka object banakar saare operations manage kiye ja sakte hain.
    cout << "Food Delivery System Design Ready!" << endl;
    return 0;
}
```

-----

### OOP Concepts Kaise Use Huye Hain? 🍕

1.  **Encapsulation (Data Hiding)**

      * Har class jaise `Restaurant`, `Order`, `MenuItem` apne data (`name`, `price`, `orderStatus`) ko **`private`** rakhti hai.
      * Is data ko modify ya access karne ke liye **`public`** methods (jaise `addToMenu()`, `trackOrder()`) ka use hota hai, jisse system ka data safe rehta hai.

2.  **Inheritance (Virasat)**

      * **`Customer`** aur **`DeliveryAgent`** dono ne **`User`** class se inherit kiya hai.
      * Isse `userId`, `name`, `contactNumber` jaisi common properties ko dobara likhne ki zaroorat nahi padi, jisse code reuse hota hai.

3.  **Abstraction (Zaroori Cheezein Dikhana)**

      * **`User`** aur **`PaymentMethod`** **abstract classes** hain. Inke andar pure virtual functions (`= 0;` wale) hain.
      * Yeh classes ek rule (contract) banati hain. Jaise har `User` ko apna profile display karna hi hoga (`displayProfile()`) aur har `PaymentMethod` se payment process (`processPayment()`) hona hi chahiye. Kaise hoga, yeh detail chhupa di jaati hai.

4.  **Polymorphism (Anek Roop)**

      * **`Order`** class ka `checkout(PaymentMethod* payment)` function iska behtareen example hai. Hum ismein `UpiPayment` ya `CardPayment` kisi ka bhi object bhej sakte hain. Jab `payment->processPayment()` call hoga, C++ apne aap sahi payment method ko run karega.
      * Isi tarah, `User*` pointer `Customer` aur `DeliveryAgent` dono ke `displayProfile()` function ko call kar sakta hai. Isse system bahut flexible aur future-proof banta hai.

----


## Zoo Management System ka C++ Code

Yeh C++ code ek Zoo Management System ke liye class hierarchy ko define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ke concepts ko istemal kiya gaya hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// ===================================
// == ABSTRACTION & INHERITANCE (Base Class) ==
// ===================================
// Yeh ek abstract class hai jo kisi bhi janwar ka basic blueprint hai.
// Iska object nahi ban sakta, yeh sirf inheritance ke liye hai.
class Animal {
protected:
    string name;
    string species;
    int age;

public:
    // Pure virtual functions. Har janwar ki class ko inhe define karna hi hoga (Abstraction).
    virtual void makeSound() = 0; // Har janwar alag aawaz nikalta hai.
    virtual void eat() = 0;       // Har janwar ka khana alag hota hai.

    // Common function jo har janwar ke liye kaam karega.
    void displayInfo() {
        cout << "Name: " << name << ", Species: " << species << ", Age: " << age << endl;
    }
};

// ===================================
// == INHERITANCE & POLYMORPHISM ==
// ===================================
// Mammal class, Animal class se inherit ho rahi hai.
class Mammal : public Animal {
    // Mammals ke specific features yahan aa sakte hain
};

// Bird class, Animal class se inherit ho rahi hai.
class Bird : public Animal {
    // Birds ke specific features yahan aa sakte hain
};

// Lion class, Mammal se inherit kar rahi hai.
class Lion : public Mammal {
public:
    Lion(string n, int a);
    // Base class ke virtual functions ko override kiya gaya hai (Polymorphism)
    void makeSound() override;
    void eat() override;
};

// Eagle class, Bird se inherit kar rahi hai.
class Eagle : public Bird {
public:
    Eagle(string n, int a);
    // Base class ke virtual functions ko override kiya gaya hai (Polymorphism)
    void makeSound() override;
    void eat() override;
};

// ===================================
// == ENCAPSULATION ==
// ===================================
// Food class, khane ke stock aur details ko manage karti hai.
class Food {
private:
    string foodType; // Jaise "Meat", "Fruits", "Vegetables"
    int stockQuantity; // Kitna stock hai (kg mein)

public:
    Food(string type, int quantity);
    void addStock(int quantity);
    void consumeStock(int quantity);
    void displayStock();
};

// Habitat class, janwaron ke rehne ki jagah ko manage karti hai.
class Habitat {
private:
    int habitatId;
    string habitatType; // Jaise "Savannah", "Jungle", "Aviary"
    bool isClean;
    vector<Animal*> residentAnimals; // Is habitat mein rehne wale janwar

public:
    Habitat(int id, string type);
    void addAnimal(Animal* animal);
    void cleanHabitat();
    void displayHabitatDetails();
};

// Zookeeper class, staff ki details manage karti hai (Extra Feature).
class Zookeeper {
private:
    int keeperId;
    string name;
    vector<int> assignedHabitatIds; // Yeh keeper kaunse habitats ke liye responsible hai

public:
    Zookeeper(int id, string name);
    void assignToHabitat(int habitatId);
    // Zookeeper janwaron ko khana khilayega aur habitat saaf karega.
    void feedAnimal(Animal* animal, Food* foodItem);
    void startCleaning(Habitat* habitat);
    void displayKeeperDetails();
};

// ===================================
// == MAIN CONTROLLER CLASS ==
// ===================================
// Zoo class poore system ke operations ko manage karti hai.
class Zoo {
private:
    vector<Animal*> allAnimals;
    vector<Habitat> allHabitats;
    vector<Zookeeper> allZookeepers;
    map<string, Food> foodInventory;

public:
    // Zoo mein naya janwar add karna
    void addAnimal(Animal* animal);
    
    // Naya habitat banana
    void addHabitat(const Habitat& habitat);

    // Naye zookeeper ko hire karna
    void hireZookeeper(const Zookeeper& keeper);
    
    // Khane ka stock add karna
    void addFoodToInventory(const Food& food);

    // Din ke saare tasks schedule karna, jaise feeding time
    void scheduleDailyTasks();
};

// main function jahan se program shuru hoga
int main() {
    // Yahan par Zoo class ka object banakar saare operations manage kiye ja sakte hain.
    cout << "Zoo Management System Design Ready!" << endl;
    return 0;
}
```

-----

### OOP Concepts Kaise Use Huye Hain? 🦁

1.  **Encapsulation (Data Hiding)**

      * **`Habitat`**, **`Food`**, aur **`Zookeeper`** jaisi classes apne data (`isClean`, `stockQuantity`, `name`) ko **`private`** rakhti hain.
      * Is data ko access ya modify karne ke liye **`public`** methods (jaise `cleanHabitat()`, `addStock()`) diye gaye hain. Isse system ka data organized aur safe rehta hai.

2.  **Inheritance (Virasat)**

      * Humne ek general base class **`Animal`** banayi hai.
      * Phir **`Mammal`** aur **`Bird`** jaisi classes ne `Animal` se inherit kiya.
      * Uske baad **`Lion`** ne `Mammal` se aur **`Eagle`** ne `Bird` se inherit kiya. Yeh ek multi-level hierarchy hai jo real-world relationships ko dikhati hai aur code reuse karti hai.

3.  **Abstraction (Zaroori Cheezein Dikhana)**

      * **`Animal`** ek **abstract class** hai, jismein pure virtual functions **`makeSound() = 0;`** aur **`eat() = 0;`** hain.
      * Yeh class ek rule banati hai ki har "Animal" (chahe woh `Lion` ho ya `Eagle`) ko aawaz nikalni aur khana khana aana chahiye. Lekin *kaise*, yeh detail us janwar ki specific class batayegi.

4.  **Polymorphism (Anek Roop)**

      * Yeh sabse interesting part hai. `makeSound()` function ko har specific animal class (`Lion`, `Eagle`) ne **`override`** kiya hai.
      * Agar hum `Zoo` class mein sabhi janwaron ko `vector<Animal*>` mein rakhte hain, toh hum ek loop chala kar `animal->makeSound()` call kar sakte hain. C++ apne aap pata laga lega ki pointer ke peeche `Lion` hai ya `Eagle` aur usi ki aawaz (roar ya screech) produce karega. Ise **Runtime Polymorphism** kehte hain.
---


## Online Movie Ticket Booking System ka C++ Code

Yeh C++ code ek Online Movie Ticket Booking System ke liye class hierarchy ko define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ke concepts ko istemal kiya gaya hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class Show;
class User;

// ===================================
// == ENCAPSULATION (Core Components) ==
// ===================================
// Movie class, film ki details rakhti hai.
class Movie {
private:
    int movieId;
    string title;
    int durationInMinutes;

public:
    Movie(int id, string title, int duration);
    void displayMovieDetails();
};

// Seat class, theater ki ek single seat ko represent karti hai.
class Seat {
private:
    int seatId;
    string seatNumber; // Jaise "A1", "C5"
    bool isBooked;

public:
    Seat(int id, string number);
    void bookSeat();
    void cancelBooking();
    bool checkAvailability();
};

// Screen class, theater ke ek auditorium ko represent karti hai.
class Screen {
private:
    int screenId;
    vector<vector<Seat>> seatLayout; // 2D vector for seat arrangement

public:
    Screen(int id, int rows, int cols);
    void displaySeatLayout();
};

// Theater class, poore cinema hall ko represent karti hai.
class Theater {
private:
    int theaterId;
    string name;
    string location;
    vector<Screen> screens;

public:
    Theater(int id, string name, string loc);
    void addScreen(const Screen& screen);
    // Yahan aur bhi methods ho sakte hain jaise getShows() etc.
};

// Show class, ek particular movie, time aur screen ko jodti hai.
class Show {
private:
    int showId;
    Movie* movie; // Pointer to a Movie object
    Screen* screen; // Pointer to a Screen object
    string startTime;

public:
    Show(int id, Movie* mov, Screen* scr, string time);
    void displayShowDetails();
};


// ===================================
// == ABSTRACTION & POLYMORPHISM (For Payment) ==
// ===================================
// Payment ke liye ek abstract base class.
class PaymentProcessor {
public:
    // Pure virtual function (Abstraction)
    virtual bool makePayment(double amount) = 0;
};

// CreditCardProcessor, PaymentProcessor se inherit ho raha hai (Inheritance)
class CreditCardProcessor : public PaymentProcessor {
private:
    string cardNumber;
public:
    CreditCardProcessor(string cardNum);
    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    bool makePayment(double amount) override;
};

// UpiProcessor, PaymentProcessor se inherit ho raha hai (Inheritance)
class UpiProcessor : public PaymentProcessor {
private:
    string upiId;
public:
    UpiProcessor(string id);
    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    bool makePayment(double amount) override;
};


// ===================================
// == MAIN LOGIC CLASS ==
// ===================================
// Booking class, ek transaction ki saari details rakhti hai.
class Booking {
private:
    int bookingId;
    User* user;
    Show* show;
    vector<Seat*> bookedSeats;
    double totalAmount;
    bool isConfirmed;

public:
    Booking(int id, User* usr, Show* shw);
    void selectSeats(vector<Seat*> seats);
    void calculateTotalAmount();
    // Payment ke liye Polymorphism ka use
    void confirmBooking(PaymentProcessor* processor);
    void cancelBooking();
};

// User class, customer ki details rakhti hai.
class User {
private:
    int userId;
    string name;
    string email;

public:
    User(int id, string name, string email);
    void displayUserDetails();
};

// ===================================
// == MAIN CONTROLLER CLASS ==
// ===================================
// TicketBookingSystem poore platform ko manage karta hai.
class TicketBookingSystem {
private:
    vector<Theater> theaters;
    vector<Movie> movies;
    vector<Show> shows;
    vector<Booking> bookings;

public:
    // User ko movies search karne mein help karna
    void searchMovie(string movieName);

    // Ek particular movie ke shows dekhna
    void viewShows(int movieId, string date);

    // Nayi booking ka process start karna
    void createBooking(int userId, int showId);
};


// main function jahan se program shuru hoga
int main() {
    // Yahan par TicketBookingSystem ka object banakar saare operations manage kiye ja sakte hain.
    cout << "Online Movie Ticket Booking System Design Ready!" << endl;
    return 0;
}
```

-----

### OOP Concepts Kaise Use Huye Hain? 🍿

1.  **Encapsulation (Data Hiding)**

      * Har class jaise **`Movie`**, **`Seat`**, aur **`Theater`** apne data members (`title`, `isBooked`, `name`) ko **`private`** rakhti hai.
      * Is data ko access karne ke liye **`public`** methods (jaise `displayMovieDetails()`, `checkAvailability()`) provide kiye gaye hain. Isse system ka data organized aur safe rehta hai.

2.  **Inheritance (Virasat)**

      * Humne ek general base class **`PaymentProcessor`** banayi hai.
      * Phir **`CreditCardProcessor`** aur **`UpiProcessor`** jaisi specific classes ne uss se inherit kiya hai. Isse code reuse hota hai aur payment system ko extend karna aasan ho jaata hai.

3.  **Abstraction (Zaroori Cheezein Dikhana)**

      * **`PaymentProcessor`** ek **abstract class** hai, jismein ek pure virtual function **`makePayment(double amount) = 0;`** hai.
      * Yeh class ek "contract" banati hai ki har payment method ko payment process karna aana chahiye, lekin yeh nahi batati ki *kaise* karna hai (card se ya UPI se). Yeh detail child classes par chhod di jaati hai.

4.  **Polymorphism (Anek Roop)**

      * **`Booking`** class ka **`confirmBooking(PaymentProcessor* processor)`** method iska sabse accha example hai.
      * Yeh method `PaymentProcessor` type ka pointer leta hai. Hum ismein `CreditCardProcessor` ya `UpiProcessor` kisi ka bhi object bhej sakte hain.
      * Jab `processor->makePayment()` call hota hai, toh C++ automatically pata laga leta hai ki pointer ke peeche kaunsa object hai aur usi ka payment method call karta hai. Isse hum future mein naye payment options (jaise NetBanking) aasani se add kar sakte hain.


----

## Hotel Booking System ka C++ Code

Yeh C++ code ek Hotel Booking System ke liye class hierarchy ko define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ke concepts ko istemal kiya gaya hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class Reservation;
class Guest;
class Amenity;

// ===================================
// == ABSTRACTION & INHERITANCE (Base Class for Rooms) ==
// ===================================
// Room ek abstract class hai. Yeh har tarah ke room ka ek basic blueprint hai.
class Room {
protected:
    int roomNumber;
    bool isBooked;
    double pricePerNight;

public:
    // Pure virtual functions (Abstraction).
    // Har specific room type (Single, Double, Suite) ko inhe define karna hi hoga.
    virtual void displayRoomDetails() = 0;
    virtual double calculatePrice(int nights) = 0;

    // Common methods jo sabhi rooms ke liye hain
    void bookRoom() { isBooked = true; }
    void freeRoom() { isBooked = false; }
    bool checkAvailability() { return !isBooked; }
    int getRoomNumber() { return roomNumber; }
};

// ===================================
// == INHERITANCE & POLYMORPHISM ==
// ===================================
// SingleRoom class, Room class se inherit ho rahi hai.
class SingleRoom : public Room {
public:
    SingleRoom(int number);
    // Base class ke virtual functions ko override kiya gaya hai (Polymorphism)
    void displayRoomDetails() override;
    double calculatePrice(int nights) override;
};

// DoubleRoom class, Room class se inherit ho rahi hai.
class DoubleRoom : public Room {
public:
    DoubleRoom(int number);
    void displayRoomDetails() override;
    double calculatePrice(int nights) override;
};

// Suite class, Room class se inherit ho rahi hai.
class Suite : public Room {
private:
    vector<Amenity*> complimentaryAmenities; // Suites mein extra suvidhayein
public:
    Suite(int number);
    void displayRoomDetails() override;
    double calculatePrice(int nights) override;
};


// ===================================
// == ENCAPSULATION & EXTRA FEATURES ==
// ===================================
// Guest class, mehmaan ki details rakhti hai.
class Guest {
private:
    int guestId;
    string name;
    string contactInfo;

public:
    Guest(int id, string name, string contact);
    void displayGuestDetails();
};

// Amenity class, extra suvidhaon ke liye.
class Amenity {
private:
    string serviceName; // Jaise "Spa", "Pool Access", "Breakfast"
    double price;
public:
    Amenity(string name, double cost);
    string getName();
    double getPrice();
};


// ===================================
// == ABSTRACTION & POLYMORPHISM (For Payment) ==
// ===================================
// Payment ke liye ek abstract base class.
class PaymentStrategy {
public:
    virtual bool processPayment(double amount) = 0;
};

class CreditCardPayment : public PaymentStrategy {
private:
    string cardNumber;
public:
    CreditCardPayment(string num);
    bool processPayment(double amount) override;
};


// ===================================
// == MAIN LOGIC & CONTROLLER CLASSES ==
// ===================================
// Reservation class, ek booking ki poori jaankari rakhti hai.
class Reservation {
private:
    int reservationId;
    Guest* guest;
    Room* room;
    string checkInDate;
    string checkOutDate;
    double totalBill;

public:
    Reservation(int id, Guest* g, Room* r, string checkIn, string checkOut);
    void calculateTotalBill();
    void confirmBooking(PaymentStrategy* paymentMethod); // Polymorphism ka use
    void displayReservationDetails();
};

// Hotel class, poore hotel ke operations ko manage karti hai.
class Hotel {
private:
    string hotelName;
    vector<Room*> rooms; // Base class ka pointer, taaki har type ka room store ho sake
    vector<Guest> guests;
    vector<Reservation> reservations;

public:
    Hotel(string name);
    // Destructor to free memory for rooms
    ~Hotel();

    void addRoom(Room* room);
    void registerGuest(const Guest& guest);
    void searchAvailableRooms(string date);
    void createReservation(int guestId, int roomNumber, string checkIn, string checkOut);
};


// main function jahan se program shuru hoga
int main() {
    // Yahan par Hotel class ka object banakar saare operations manage kiye ja sakte hain.
    cout << "Hotel Booking System Design Ready!" << endl;
    return 0;
}
```

-----

### OOP Concepts Kaise Use Huye Hain? 🏨

1.  **Encapsulation (Data Hiding)**

      * **`Guest`**, **`Reservation`**, aur **`Amenity`** jaisi classes apne data members (`name`, `totalBill`, `price`) ko **`private`** rakhti hain.
      * Is data ko access ya modify karne ke liye **`public`** methods (jaise `displayGuestDetails()`, `calculateTotalBill()`) provide kiye gaye hain, jisse data safe aur organized rehta hai.

2.  **Inheritance (Virasat)**

      * Humne ek general base class **`Room`** banayi hai.
      * Phir **`SingleRoom`**, **`DoubleRoom`**, aur **`Suite`** jaisi specific room classes ne uss se inherit kiya hai. Isse har room class ko `roomNumber` aur `isBooked` jaisi common cheezein dobara define nahi karni padti.

3.  **Abstraction (Zaroori Cheezein Dikhana)**

      * **`Room`** aur **`PaymentStrategy`** **abstract classes** hain. Inke andar pure virtual functions (`= 0;` wale) hain.
      * Yeh classes ek "contract" banati hain. Jaise har `Room` ko apni details display karni hi hongi (`displayRoomDetails()`) aur har `PaymentStrategy` se payment process (`processPayment()`) hona hi chahiye. *Kaise* hoga, yeh detail chhupa di jaati hai.

4.  **Polymorphism (Anek Roop)**

      * **`Hotel`** class mein humne `vector<Room*>` ka istemal kiya hai. Yeh iska sabse powerful example hai. Hum is vector mein `SingleRoom`, `DoubleRoom`, aur `Suite` - teeno ke objects ko store kar sakte hain.
      * Jab hum is vector par loop karke `room->displayRoomDetails()` call karte hain, toh C++ automatically pata laga leta hai ki pointer ke peeche kaunsa room hai aur usi ka specific details wala function call karta hai. Ise **Runtime Polymorphism** kehte hain aur isse system bahut flexible ban jaata hai.


---
## Employee Payroll System ka C++ Code

Yeh C++ code ek Employee Payroll System ke liye class hierarchy ko define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ke concepts ko istemal kiya gaya hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// ===================================
// == ABSTRACTION & INHERITANCE (Base Class) ==
// ===================================
// Employee ek abstract class hai. Yeh har tarah ke employee ka ek basic template hai.
class Employee {
protected:
    int employeeId;
    string name;

public:
    // Constructor
    Employee(int id, string name);

    // Pure virtual function (Abstraction).
    // Har specific employee type (Full-time, Part-time) ko isse define karna hi hoga.
    virtual double calculateSalary() = 0;
    
    // Virtual destructor for proper memory cleanup in case of polymorphism
    virtual ~Employee() {}

    // Common function jo sabhi employees ke liye kaam karega.
    void displayEmployeeInfo();
};


// ===================================
// == INHERITANCE & POLYMORPHISM ==
// ===================================
// FullTimeEmployee class, Employee class se inherit ho rahi hai.
class FullTimeEmployee : public Employee {
private:
    double monthlySalary;

public:
    FullTimeEmployee(int id, string name, double salary);
    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    double calculateSalary() override;
};

// PartTimeEmployee class, Employee class se inherit ho rahi hai.
class PartTimeEmployee : public Employee {
private:
    double hourlyRate;
    int hoursWorked;

public:
    PartTimeEmployee(int id, string name, double rate, int hours);
    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    double calculateSalary() override;
};

// Contractor class, Employee class se inherit ho rahi hai.
class Contractor : public Employee {
private:
    double contractFee;

public:
    Contractor(int id, string name, double fee);
    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    double calculateSalary() override;
};


// ===================================
// == ENCAPSULATION & EXTRA FEATURES ==
// ===================================
// PaySlip class, ek employee ki salary slip ki details rakhti hai.
class PaySlip {
private:
    int employeeId;
    string employeeName;
    string payPeriod;
    double grossSalary;
    double deductions;
    double netSalary;

public:
    PaySlip(int id, string name, string period, double gross, double deduct);
    void displayPaySlip();
};


// ===================================
// == MAIN CONTROLLER CLASS ==
// ===================================
// PayrollSystem poore payroll process ko manage karta hai.
class PayrollSystem {
private:
    vector<Employee*> employees; // Base class ka pointer, taaki har type ka employee store ho sake

public:
    // Destructor to free memory for employees
    ~PayrollSystem();

    void addEmployee(Employee* employee);

    // Sabhi employees ki salary calculate karke payslips generate karna
    void runPayroll();
};


// main function jahan se program shuru hoga
int main() {
    // Yahan par PayrollSystem class ka object banakar saare operations manage kiye ja sakte hain.
    cout << "Employee Payroll System Design Ready!" << endl;
    return 0;
}
```

-----

### OOP Concepts Kaise Use Huye Hain? 💼

1.  **Encapsulation (Data Hiding)**

      * **`PayrollSystem`** class `employees` ke vector ko **`private`** rakhti hai. Bahar se koi is list ko directly access nahi kar sakta. Employees ko add karne ya payroll run karne ke liye `addEmployee()` aur `runPayroll()` jaise **`public`** methods ka istemal karna padta hai.

2.  **Inheritance (Virasat)**

      * Humne ek common base class **`Employee`** banayi hai.
      * Phir **`FullTimeEmployee`**, **`PartTimeEmployee`**, aur **`Contractor`** jaisi specific classes ne uss se `employeeId` aur `name` jaisi common properties ko inherit kiya hai. Isse code reuse hota hai.

3.  **Abstraction (Zaroori Cheezein Dikhana)**

      * **`Employee`** ek **abstract class** hai, kyunki iske andar ek pure virtual function **`calculateSalary() = 0;`** hai.
      * Yeh class ek "contract" banati hai ki har `Employee` ki salary calculate honi chahiye, lekin yeh nahi batati ki *kaise* honi chahiye. Yeh detail child classes (jaise `PartTimeEmployee` ke liye ghante ke hisab se) par chhod di jaati hai.

4.  **Polymorphism (Anek Roop)**

      * Yeh is system ka sabse powerful feature hai. **`PayrollSystem`** class mein humne `vector<Employee*>` ka istemal kiya hai. Hum is vector mein `FullTimeEmployee`, `PartTimeEmployee`, aur `Contractor` - sabhi ke objects ko store kar sakte hain.
      * Jab `runPayroll()` method mein hum loop chala kar `employee->calculateSalary()` call karte hain, toh C++ **Runtime** mein pata laga leta hai ki pointer ke peeche kaunse type ka employee hai aur usi ka specific `calculateSalary()` function call karta hai. Isse hamara system naye type ke employees (jaise Interns) ke liye bhi aasani se extend ho sakta hai.


---


## School Management System ka C++ Code

Yeh C++ code ek School Management System ke liye class hierarchy ko define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ke concepts ko istemal kiya gaya hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class Subject;
class Student;
class Teacher;

// ===================================
// == ABSTRACTION & INHERITANCE (Base Class) ==
// ===================================
// Person ek abstract class hai. Student aur Teacher dono hi Person hain.
class Person {
protected:
    int personId;
    string name;
    int age;

public:
    Person(int id, string name, int age);
    // Pure virtual function (Abstraction).
    // Har derived class (Student, Teacher) ko isse define karna hi hoga.
    virtual void displayDetails() = 0;
    virtual ~Person() {} // Virtual destructor for base class
};

// ===================================
// == INHERITANCE & POLYMORPHISM ==
// ===================================
// Student class, Person class se inherit ho rahi hai.
class Student : public Person {
private:
    int grade; // Kis class mein hai
    int rollNumber;

public:
    Student(int id, string name, int age, int grade, int rollNum);
    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    void displayDetails() override;
};

// Teacher class, Person class se inherit ho rahi hai.
class Teacher : public Person {
private:
    string specialization; // Teacher kaunsa subject padhata hai

public:
    Teacher(int id, string name, int age, string spec);
    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    void displayDetails() override;
};

// ===================================
// == ENCAPSULATION (Core Components) ==
// ===================================
// Subject class, ek vishay (subject) ki details rakhti hai.
class Subject {
private:
    int subjectId;
    string subjectName;
    Teacher* assignedTeacher;

public:
    Subject(int id, string name);
    void assignTeacher(Teacher* teacher);
    void displaySubjectInfo();
};

// Exam class, ek pariksha (exam) ki details rakhti hai.
class Exam {
private:
    int examId;
    Subject* subject;
    double maxMarks;
    string examDate;

public:
    Exam(int id, Subject* sub, double marks, string date);
    void displayExamSchedule();
};

// Result class, student ke marks aur grade ko store karti hai.
class Result {
private:
    int resultId;
    Student* student;
    Exam* exam;
    double marksObtained;

public:
    Result(int id, Student* std, Exam* ex, double marks);
    char calculateGrade(); // Marks ke hisab se A, B, C grade calculate karna
    void displayResultCard();
};

// ===================================
// == MAIN CONTROLLER CLASS ==
// ===================================
// School class poore school ke operations ko manage karti hai.
class School {
private:
    string schoolName;
    vector<Person*> people; // Student aur Teacher dono ko store karega (Polymorphism)
    vector<Subject> subjects;
    vector<Exam> exams;
    vector<Result> results;

public:
    School(string name);
    ~School(); // Destructor to free memory for people

    void admitStudent(Student* student);
    void hireTeacher(Teacher* teacher);
    void createSubject(const Subject& subject);
    void scheduleExam(const Exam& exam);
    void publishResult(const Result& result);

    // School ke sabhi logon (students aur teachers) ki list dikhana
    void displayAllPeople();
};

// main function jahan se program shuru hoga
int main() {
    // Yahan par School class ka object banakar saare operations manage kiye ja sakte hain.
    cout << "School Management System Design Ready!" << endl;
    return 0;
}
```

-----

### OOP Concepts Kaise Use Huye Hain? 🏫

1.  **Encapsulation (Data Hiding)**

      * **`Subject`**, **`Exam`**, aur **`Result`** jaisi classes apne data members (`subjectName`, `maxMarks`, `marksObtained`) ko **`private`** rakhti hain.
      * Is data ko access ya modify karne ke liye **`public`** methods (jaise `assignTeacher()`, `calculateGrade()`) provide kiye gaye hain. Isse system ka data organized aur galti se change hone se bacha rehta hai.

2.  **Inheritance (Virasat)**

      * Humne ek common base class **`Person`** banayi hai.
      * **`Student`** aur **`Teacher`** classes ne uss se `personId`, `name`, aur `age` jaisi common properties ko inherit kiya hai. Isse code ko dobara likhne ki zaroorat nahi padti.

3.  **Abstraction (Zaroori Cheezein Dikhana)**

      * **`Person`** ek **abstract class** hai, kyunki iske andar ek pure virtual function **`displayDetails() = 0;`** hai.
      * Yeh class ek "rule" banati hai ki har `Person` (chahe woh `Student` ho ya `Teacher`) ko apni details display karni aani chahiye. Lekin *kaise*, yeh detail child classes par chhod di jaati hai.

4.  **Polymorphism (Anek Roop)**

      * **`School`** class mein `vector<Person*>` iska sabse accha example hai. Hum is vector mein `Student` aur `Teacher` - dono ke objects ko store kar sakte hain.
      * Jab `displayAllPeople()` method mein hum loop chala kar `person->displayDetails()` call karte hain, toh C++ **Runtime** mein khud hi pata laga leta hai ki pointer ke peeche `Student` hai ya `Teacher` aur usi ka specific `displayDetails()` function call karta hai. Isse code bahut saaf aur flexible ho jaata hai.

---



## Ride-Sharing System ka C++ Code

Yeh C++ code ek Ride-Sharing System ke liye class hierarchy ko define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ke concepts ko istemal kiya gaya hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class Ride;
class Driver;
class Rider;
class Vehicle;

// =aps================================
// == ABSTRACTION & INHERITANCE (Base Class) ==
// ===================================
// User ek abstract class hai. Rider aur Driver dono hi User hain.
class User {
protected:
    int userId;
    string name;
    double rating;

public:
    User(int id, string name);
    // Pure virtual function (Abstraction).
    // Har derived class (Rider, Driver) ko isse define karna hi hoga.
    virtual void displayProfile() = 0;
    virtual ~User() {} // Virtual destructor for base class
};

// ===================================
// == INHERITANCE & POLYMORPHISM ==
// ===================================
// Rider class, User class se inherit ho rahi hai.
class Rider : public User {
private:
    string homeAddress;
public:
    Rider(int id, string name);
    void requestRide(string pickup, string destination);
    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    void displayProfile() override;
};

// Driver class, User class se inherit ho rahi hai.
class Driver : public User {
private:
    Vehicle* vehicle;
    string licenseNumber;
    bool isAvailable;

public:
    Driver(int id, string name, string license, Vehicle* v);
    void acceptRide(Ride* ride);
    void endRide(Ride* ride);
    void updateAvailability(bool status);
    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    void displayProfile() override;
};

// ===================================
// == ENCAPSULATION & EXTRA FEATURES ==
// ===================================
// Vehicle class, gaadi ki details rakhti hai.
class Vehicle {
private:
    string licensePlate;
    string model;
    string type; // Jaise "Sedan", "SUV", "Auto"

public:
    Vehicle(string plate, string model, string type);
    void displayVehicleDetails();
};

// Location class, location ko manage karne ke liye.
class Location {
private:
    double latitude;
    double longitude;
public:
    Location(double lat, double lon);
    double calculateDistance(const Location& other);
};

// ===================================
// == ABSTRACTION & POLYMORPHISM (For Payment) ==
// ===================================
// Payment ke liye ek abstract base class.
class PaymentGateway {
public:
    virtual bool processPayment(double amount) = 0;
};

class UpiPayment : public PaymentGateway {
private:
    string upiId;
public:
    UpiPayment(string id);
    bool processPayment(double amount) override;
};

class CashPayment : public PaymentGateway {
public:
    bool processPayment(double amount) override;
};


// ===================================
// == MAIN LOGIC & CONTROLLER CLASSES ==
// ===================================
// Ride class, ek trip ki poori jaankari rakhti hai.
class Ride {
private:
    int rideId;
    Rider* rider;
    Driver* driver;
    Location startLocation;
    Location endLocation;
    double fare;
    string status; // "Requested", "Ongoing", "Completed"

public:
    Ride(int id, Rider* r, const Location& start, const Location& end);
    void assignDriver(Driver* d);
    void calculateFare();
    void completeRide();
    void displayRideDetails();
};

// RideSharingApp class, poore platform ko manage karti hai.
class RideSharingApp {
private:
    vector<User*> users; // Rider aur Driver dono ko store karega (Polymorphism)
    vector<Ride> activeRides;

public:
    ~RideSharingApp(); // Destructor to free memory for users
    void registerUser(User* user);
    void requestRide(int riderId, const Location& start, const Location& end);
    Driver* findNearbyDriver(const Location& pickupLocation);
    void processPaymentForRide(int rideId, PaymentGateway* paymentMethod);
};

// main function jahan se program shuru hoga
int main() {
    // Yahan par RideSharingApp ka object banakar saare operations manage kiye ja sakte hain.
    cout << "Ride-Sharing System Design Ready!" << endl;
    return 0;
}
```

-----

### OOP Concepts Kaise Use Huye Hain? 🚕

1.  **Encapsulation (Data Hiding)**

      * **`Vehicle`** aur **`Ride`** jaisi classes apne data members (`licensePlate`, `fare`, `status`) ko **`private`** rakhti hain.
      * Is data ko access ya modify karne ke liye **`public`** methods (jaise `displayVehicleDetails()`, `calculateFare()`) provide kiye gaye hain. Isse system ka data organized aur safe rehta hai.

2.  **Inheritance (Virasat)**

      * Humne ek common base class **`User`** banayi hai.
      * **`Rider`** aur **`Driver`** classes ne uss se `userId`, `name`, aur `rating` jaisi common properties ko inherit kiya hai. Isse code ko dobara likhne ki zaroorat nahi padti.

3.  **Abstraction (Zaroori Cheezein Dikhana)**

      * **`User`** aur **`PaymentGateway`** **abstract classes** hain, kyunki inke andar pure virtual functions (`= 0;` wale) hain.
      * Yeh classes ek "contract" banati hain. Jaise har `User` ko apna profile display karna aana chahiye (`displayProfile()`) aur har `PaymentGateway` se payment process (`processPayment()`) hona hi chahiye. *Kaise* hoga, yeh detail child classes par chhod di jaati hai.

4.  **Polymorphism (Anek Roop)**

      * **`RideSharingApp`** class mein `vector<User*>` iska sabse accha example hai. Hum is vector mein `Rider` aur `Driver` - dono ke objects ko store kar sakte hain. Jab hum is vector par loop karke `user->displayProfile()` call karte hain, toh C++ **Runtime** mein khud hi pata laga leta hai ki pointer ke peeche `Rider` hai ya `Driver` aur usi ka specific `displayProfile()` function call karta hai.
      * Isi tarah `processPaymentForRide()` method mein hum alag-alag `PaymentGateway` (UPI, Cash) use kar sakte hain, jisse system bahut flexible ho jaata hai.

---

## Airline Reservation System ka C++ Code

Yeh C++ code ek Airline Reservation System ke liye class hierarchy ko define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ke concepts ko istemal kiya gaya hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class Flight;
class Passenger;
class Booking;

// ===================================
// == ENCAPSULATION (Core Components) ==
// ===================================
// Seat class, flight ki ek single seat ko represent karti hai.
class Seat {
private:
    string seatNumber; // Jaise "14A", "2B"
    string seatClass;  // "Economy", "Business", "First Class"
    bool isBooked;

public:
    Seat(string number, string sClass);
    void book();
    void unbook();
    bool isAvailable();
    string getSeatDetails();
};

// Flight class, ek particular flight ki saari details rakhti hai.
class Flight {
private:
    string flightNumber;
    string origin;
    string destination;
    string departureTime;
    vector<vector<Seat>> seatMap;

public:
    Flight(string fNum, string orig, string dest, string depTime, int rows, int cols);
    void displayFlightDetails();
    bool checkSeatAvailability(string seatNumber);
};

// ===================================
// == ABSTRACTION & INHERITANCE (Base Class) ==
// ===================================
// Person ek abstract class hai. Passenger aur FlightCrew dono hi Person hain.
class Person {
protected:
    int personId;
    string name;
public:
    Person(int id, string name);
    // Pure virtual function (Abstraction)
    virtual void displayInfo() = 0;
    virtual ~Person() {} // Virtual destructor
};

// ===================================
// == INHERITANCE & POLYMORPHISM ==
// ===================================
// Passenger class, Person se inherit ho rahi hai.
class Passenger : public Person {
private:
    string passportNumber;
    vector<Booking*> bookingHistory;

public:
    Passenger(int id, string name, string passport);
    void addBookingToHistory(Booking* booking);
    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    void displayInfo() override;
};

// FlightCrew class (Extra Feature), Person se inherit ho rahi hai.
class FlightCrew : public Person {
private:
    string role; // Jaise "Pilot", "Cabin Crew"
    string employeeId;
public:
    FlightCrew(int id, string name, string role, string empId);
    void displayInfo() override;
};

// ===================================
// == ABSTRACTION & POLYMORPHISM (For Payment) ==
// ===================================
// Payment ke liye ek abstract base class.
class PaymentService {
public:
    virtual bool executePayment(double amount) = 0;
};

class CreditCardService : public PaymentService {
private:
    string cardNumber;
public:
    CreditCardService(string cardNum);
    bool executePayment(double amount) override;
};

// ===================================
// == MAIN LOGIC & CONTROLLER CLASSES ==
// ===================================
// Booking class, ek reservation ki poori jaankari rakhti hai.
class Booking {
private:
    int bookingId;
    Passenger* passenger;
    Flight* flight;
    Seat* seat;
    string bookingStatus; // "Confirmed", "Cancelled"
    double totalFare;

public:
    Booking(int id, Passenger* p, Flight* f, Seat* s);
    void calculateFare();
    void confirmBooking(PaymentService* paymentMethod); // Polymorphism ka use
    void cancelBooking();
    void displayBookingDetails();
};

// AirlineReservationSystem class, poore airline ke operations ko manage karti hai.
class AirlineReservationSystem {
private:
    string airlineName;
    vector<Flight> flights;
    vector<Person*> people; // Passenger aur FlightCrew dono ko store karega
    vector<Booking> bookings;

public:
    AirlineReservationSystem(string name);
    ~AirlineReservationSystem(); // Destructor to free memory for people

    void addFlight(const Flight& flight);
    void registerPerson(Person* person);
    void searchFlights(string origin, string destination, string date);
    void createBooking(int passengerId, string flightNumber, string seatNumber);
};

// main function jahan se program shuru hoga
int main() {
    // Yahan par AirlineReservationSystem ka object banakar saare operations manage kiye ja sakte hain.
    cout << "Airline Reservation System Design Ready!" << endl;
    return 0;
}
```

-----

### OOP Concepts Kaise Use Huye Hain? ✈️

1.  **Encapsulation (Data Hiding)**

      * **`Flight`**, **`Seat`**, aur **`Booking`** jaisi classes apne data members (`flightNumber`, `isBooked`, `bookingStatus`) ko **`private`** rakhti hain.
      * Is data ko access ya modify karne ke liye **`public`** methods (jaise `displayFlightDetails()`, `isAvailable()`) provide kiye gaye hain. Isse system ka data organized aur safe rehta hai.

2.  **Inheritance (Virasat)**

      * Humne ek common base class **`Person`** banayi hai.
      * **`Passenger`** aur **`FlightCrew`** classes ne uss se `personId` aur `name` jaisi common properties ko inherit kiya hai. Isse code reuse hota hai.

3.  **Abstraction (Zaroori Cheezein Dikhana)**

      * **`Person`** aur **`PaymentService`** **abstract classes** hain, kyunki inke andar pure virtual functions (`= 0;` wale) hain.
      * Yeh classes ek "contract" banati hain. Jaise har `Person` ko apni info display karni aani chahiye (`displayInfo()`) aur har `PaymentService` se payment (`executePayment()`) hona hi chahiye. *Kaise* hoga, yeh detail child classes par chhod di jaati hai.

4.  **Polymorphism (Anek Roop)**

      * **`AirlineReservationSystem`** class mein `vector<Person*>` iska behtareen example hai. Hum is vector mein `Passenger` aur `FlightCrew` - dono ke objects ko store kar sakte hain. Jab hum is vector par loop karke `person->displayInfo()` call karte hain, toh C++ **Runtime** mein khud hi pata laga leta hai ki pointer ke peeche `Passenger` hai ya `FlightCrew` aur usi ka specific `displayInfo()` function call karta hai.
      * Isi tarah `confirmBooking()` method mein hum alag-alag `PaymentService` use kar sakte hain, jisse system bahut flexible ho jaata hai.
---



## Online Auction System ka C++ Code

Yeh C++ code ek Online Auction System ke liye class hierarchy ko define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ke concepts ko istemal kiya gaya hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class User;
class Item;
class Bid;
class Auction;

// ===================================
// == ENCAPSULATION (Core Components) ==
// ===================================
// User class, platform ke user (seller/bidder) ko represent karti hai.
class User {
private:
    int userId;
    string username;
    double rating;

public:
    User(int id, string name);
    void placeBid(Auction* auction, double amount);
    void listItemForAuction(string itemName, string desc, double startPrice);
    void displayUserInfo();
};

// Item class, auction mein rakhe gaye product ki details rakhti hai.
class Item {
private:
    int itemId;
    string name;
    string description;
    User* seller;

public:
    Item(int id, string name, string desc, User* seller);
    void displayItemDetails();
};

// Bid class, ek user dwara lagayi gayi boli ko represent karti hai.
class Bid {
private:
    User* bidder;
    double amount;
    time_t timestamp;

public:
    Bid(User* b, double amt);
    void displayBidInfo();
};

// Notification class (Extra Feature), users ko updates bhejti hai.
class NotificationService {
public:
    void sendBidConfirmation(User* user);
    void sendOutbidAlert(User* user);
    void sendAuctionEndNotification(User* winner, User* seller, Item* item);
};


// ===================================
// == ABSTRACTION & INHERITANCE (For Auction Types) ==
// ===================================
// Auction ek abstract class hai. Yeh alag-alag type ke auctions ka blueprint hai.
class Auction {
protected:
    int auctionId;
    Item* item;
    vector<Bid> bids;
    time_t startTime;
    time_t endTime;

public:
    Auction(int id, Item* item, time_t start, time_t end);
    // Pure virtual function (Abstraction).
    // Har auction type ko winner decide karne ka apna tarika batana hoga.
    virtual User* determineWinner() = 0;
    virtual ~Auction() {} // Virtual destructor
    
    void addBid(const Bid& bid);
};

// StandardAuction, Auction class se inherit ho raha hai. Ismein sabse unchi boli wala jeet'ta hai.
class StandardAuction : public Auction {
public:
    StandardAuction(int id, Item* item, time_t start, time_t end);
    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    User* determineWinner() override;
};


// ===================================
// == ABSTRACTION & POLYMORPHISM (For Payment) ==
// ===================================
// Payment ke liye ek abstract base class.
class PaymentHandler {
public:
    virtual bool processPayment(User* buyer, User* seller, double amount) = 0;
};

class PayPalHandler : public PaymentHandler {
public:
    bool processPayment(User* buyer, User* seller, double amount) override;
};


// ===================================
// == MAIN CONTROLLER CLASS ==
// ===================================
// AuctionSystem poore platform ko manage karta hai.
class AuctionSystem {
private:
    vector<User> users;
    vector<Auction*> activeAuctions;
    NotificationService* notifier;

public:
    AuctionSystem();
    ~AuctionSystem(); // Destructor to free memory for auctions

    void registerUser(const User& user);
    void createAuction(Auction* auction);
    void placeBidOnAuction(int userId, int auctionId, double amount);
    void endAuction(int auctionId, PaymentHandler* paymentHandler);
};


// main function jahan se program shuru hoga
int main() {
    // Yahan par AuctionSystem ka object banakar saare operations manage kiye ja sakte hain.
    cout << "Online Auction System Design Ready!" << endl;
    return 0;
}
```

-----

### OOP Concepts Kaise Use Huye Hain? 🔨

1.  **Encapsulation (Data Hiding)**

      * **`Item`**, **`Bid`**, aur **`User`** jaisi classes apne data members (`name`, `amount`, `username`) ko **`private`** rakhti hain.
      * Is data ko access ya modify karne ke liye **`public`** methods (jaise `displayItemDetails()`, `placeBid()`) provide kiye gaye hain, jisse system ka data organized aur safe rehta hai.

2.  **Inheritance (Virasat)**

      * Humne ek general base class **`Auction`** banayi hai.
      * Phir **`StandardAuction`** jaisi specific auction type ne uss se `item`, `bids` jaisi common properties ko inherit kiya hai. Isse hum future mein naye auction types (jaise Dutch Auction) aasani se add kar sakte hain.

3.  **Abstraction (Zaroori Cheezein Dikhana)**

      * **`Auction`** aur **`PaymentHandler`** **abstract classes** hain, kyunki inke andar pure virtual functions (`= 0;` wale) hain.
      * Yeh classes ek "contract" banati hain. Jaise har `Auction` ko apna winner chunna hi hoga (`determineWinner()`) aur har `PaymentHandler` se payment (`processPayment()`) hona hi chahiye. *Kaise* hoga, yeh detail child classes par chhod di jaati hai.

4.  **Polymorphism (Anek Roop)**

      * **`AuctionSystem`** class mein `vector<Auction*>` iska behtareen example hai. Hum is vector mein alag-alag type ke auctions (jaise `StandardAuction`) ko store kar sakte hain.
      * Jab `endAuction()` method mein hum `auction->determineWinner()` call karte hain, toh C++ **Runtime** mein khud hi pata laga leta hai ki pointer ke peeche kaunsa auction type hai aur usi ka winner-deciding logic call karta hai. Isse system bahut flexible aur scalable ban jaata hai.
---



## File Storage System ka C++ Code

Yeh C++ code ek File Storage System ke liye class hierarchy ko define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ke concepts ko istemal kiya gaya hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class File;
class Folder;
class User;

// ===================================
// == ABSTRACTION & INHERITANCE (Base Class) ==
// == COMPOSITE PATTERN ka base ==
// ===================================
// FileSystemEntity ek abstract class hai. File aur Folder dono hi iske types hain.
class FileSystemEntity {
protected:
    string name;
    time_t creationDate;
    User* owner;

public:
    FileSystemEntity(string name, User* owner);
    // Pure virtual functions (Abstraction).
    // Har entity (File/Folder) ko apna size batana hoga aur display karna hoga.
    virtual double getSize() = 0;
    virtual void display(string indent = "") = 0;
    virtual ~FileSystemEntity() {} // Virtual destructor
};

// ===================================
// == INHERITANCE & POLYMORPHISM ==
// == COMPOSITE PATTERN ka Leaf ==
// ===================================
// File class, FileSystemEntity se inherit ho rahi hai. Yeh ek "leaf" node hai.
class File : public FileSystemEntity {
private:
    double sizeInMB;
    string content; // Dummy content

public:
    File(string name, User* owner, double size);
    // Base class ke virtual functions ko override kiya gaya hai (Polymorphism)
    double getSize() override;
    void display(string indent = "") override;
};

// ===================================
// == COMPOSITE PATTERN ka Composite ==
// ===================================
// Folder class, FileSystemEntity se inherit ho rahi hai. Yeh "composite" node hai.
// Iske andar doosre FileSystemEntity (Files/Folders) ho sakte hain.
class Folder : public FileSystemEntity {
private:
    vector<FileSystemEntity*> children;

public:
    Folder(string name, User* owner);
    ~Folder(); // Destructor to free memory for children
    void add(FileSystemEntity* entity);
    // Base class ke virtual functions ko override kiya gaya hai (Polymorphism)
    double getSize() override; // Folder ka size uske andar ki sabhi cheezon ka total hoga
    void display(string indent = "") override;
};

// ===================================
// == ENCAPSULATION & EXTRA FEATURES ==
// ===================================
// User class, platform ke user ko represent karti hai.
class User {
private:
    int userId;
    string username;
    Folder* rootFolder; // Har user ka apna ek root folder hoga

public:
    User(int id, string name);
    ~User();
    string getUsername();
    Folder* getRoot();
};

// Permission class, sharing logic ko manage karti hai.
class Permission {
private:
    User* sharedWithUser;
    FileSystemEntity* entity;
    string accessLevel; // "VIEW_ONLY", "EDIT"

public:
    Permission(User* user, FileSystemEntity* entity, string level);
    void displayPermissionDetails();
};

// ===================================
// == MAIN CONTROLLER CLASS ==
// ===================================
// FileStorageSystem poore platform ko manage karta hai.
class FileStorageSystem {
private:
    map<int, User*> users;
    map<FileSystemEntity*, vector<Permission>> sharingMap;

public:
    ~FileStorageSystem();
    void registerUser(int id, string name);
    void uploadFile(int userId, string folderPath, string fileName, double size);
    void createFolder(int userId, string parentPath, string folderName);
    void shareEntity(int ownerId, int sharedWithId, string entityPath, string accessLevel);
    void viewDirectory(int userId, string path);
};


// main function jahan se program shuru hoga
int main() {
    // Yahan par FileStorageSystem ka object banakar saare operations manage kiye ja sakte hain.
    cout << "File Storage System Design Ready!" << endl;
    return 0;
}
```

-----

### OOP Concepts Kaise Use Huye Hain? 📁

1.  **Encapsulation (Data Hiding)**

      * **`User`** aur **`Permission`** jaisi classes apne data members (`username`, `accessLevel`) ko **`private`** rakhti hain.
      * Is data ko access ya modify karne ke liye **`public`** methods (jaise `getUsername()`, `displayPermissionDetails()`) provide kiye gaye hain, jisse system ka data organized rehta hai.

2.  **Inheritance (Virasat)**

      * Humne ek common base class **`FileSystemEntity`** banayi hai.
      * **`File`** aur **`Folder`** classes ne uss se `name`, `owner`, `creationDate` jaisi common properties ko inherit kiya hai. Isse code reuse hota hai aur ek tree-like structure banana possible hota hai.

3.  **Abstraction (Zaroori Cheezein Dikhana)**

      * **`FileSystemEntity`** ek **abstract class** hai, kyunki iske andar pure virtual functions **`getSize() = 0;`** aur **`display() = 0;`** hain.
      * Yeh class ek "contract" banati hai ki har entity (chahe woh `File` ho ya `Folder`) ko apna size batana aur display hona aana chahiye. Lekin *kaise*, yeh detail child classes par chhod di jaati hai.

4.  **Polymorphism (Anek Roop)**

      * Yeh is system ka sabse powerful feature hai, jo **Composite Design Pattern** ke through achieve hota hai.
      * **`Folder`** class mein `vector<FileSystemEntity*>` hai. Is vector mein hum `File` aur `Folder` - dono ke objects ko store kar sakte hain.
      * Jab hum `Folder` ka `getSize()` ya `display()` function call karte hain, toh woh apne sabhi children par loop karke unka `getSize()` ya `display()` function call karta hai. C++ **Runtime** mein khud hi pata laga leta hai ki pointer ke peeche `File` hai ya `Folder` aur usi ka specific function call karta hai. Isse nested folder structure ko handle karna bahut aasan ho jaata hai.

---


## Chess Game ka C++ Code

Yeh C++ code ek Chess Game ke liye class hierarchy ko define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ke concepts ko istemal kiya gaya hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class Board;
class Piece;
class Spot;
class Player;

// Enums for clarity
enum class Color { WHITE, BLACK };

// ===================================
// == ABSTRACTION & INHERITANCE (Base Class) ==
// ===================================
// Piece ek abstract class hai. Yeh har mohre (piece) ka ek basic blueprint hai.
class Piece {
protected:
    Color color;
    bool isAlive;

public:
    Piece(Color c);
    // Pure virtual functions (Abstraction).
    // Har piece ko batana hoga ki woh kaise move kar sakta hai aur uska symbol kya hai.
    virtual bool canMove(Board* board, Spot* start, Spot* end) = 0;
    virtual char getSymbol() = 0;
    virtual ~Piece() {} // Virtual destructor
    
    Color getColor();
};

// ===================================
// == INHERITANCE & POLYMORPHISM (Specific Pieces) ==
// ===================================
// Har specific piece (King, Queen, etc.) Piece class se inherit ho raha hai.
// Aur sabhi apne canMove() method ko override kar rahe hain.
class King : public Piece {
public:
    King(Color c);
    bool canMove(Board* board, Spot* start, Spot* end) override;
    char getSymbol() override;
};

class Queen : public Piece {
public:
    Queen(Color c);
    bool canMove(Board* board, Spot* start, Spot* end) override;
    char getSymbol() override;
};

class Rook : public Piece {
public:
    Rook(Color c);
    bool canMove(Board* board, Spot* start, Spot* end) override;
    char getSymbol() override;
};
// ... Isi tarah Bishop, Knight, aur Pawn ke liye bhi classes banengi.

// ===================================
// == ENCAPSULATION (Core Components) ==
// ===================================
// Spot class, board ke ek single square ko represent karti hai.
class Spot {
private:
    int x, y;
    Piece* piece; // Spot par kaunsa piece hai

public:
    Spot(int x, int y, Piece* p);
    void setPiece(Piece* p);
    Piece* getPiece();
};

// Board class, poore 8x8 chessboard ko manage karti hai.
class Board {
private:
    vector<vector<Spot>> board;

public:
    Board();
    void initializeBoard(); // Board par pieces set karna
    void drawBoard();
    Spot* getSpot(int x, int y);
};

// Player class, khiladi ki details rakhti hai.
class Player {
private:
    string name;
    Color color;
public:
    Player(string name, Color c);
    string getName();
    Color getColor();
};

// Move class, ek chaal (move) ki details rakhti hai.
class Move {
private:
    Player* player;
    Spot* start;
    Spot* end;
    Piece* pieceMoved;
    Piece* pieceKilled;
public:
    Move(Player* p, Spot* s, Spot* e);
};

// ===================================
// == MAIN CONTROLLER CLASS (Game Rules) ==
// ===================================
// Game class poore game ke flow aur rules ko manage karti hai.
class Game {
private:
    Board* board;
    Player players[2];
    Player* currentPlayer;
    vector<Move> moveHistory;
    string status; // "ACTIVE", "CHECKMATE", "STALEMATE"

public:
    Game(string player1Name, string player2Name);
    void startGame();
    bool makeMove(int startX, int startY, int endX, int endY);
    void changeTurn();
    bool isCheck(Color playerColor);
    bool isCheckmate(Color playerColor);
};

// main function jahan se program shuru hoga
int main() {
    // Yahan par Game class ka object banakar game shuru kiya ja sakta hai.
    cout << "Chess Game Design Ready!" << endl;
    return 0;
}
```

-----

### OOP Concepts Kaise Use Huye Hain? ♟️

1.  **Encapsulation (Data Hiding)**

      * **`Board`** class 64 `Spot` objects ke state ko **`private`** rakhti hai. Board ko access karne ke liye `getSpot()` jaise **`public`** methods ka istemal hota hai.
      * **`Game`** class `currentPlayer`, `status` jaise game ke critical data ko encapsulate karti hai aur `makeMove()` jaise controlled functions ke through game aage badhta hai.

2.  **Inheritance (Virasat)**

      * Humne ek common base class **`Piece`** banayi hai.
      * Phir **`King`**, **`Queen`**, **`Rook`**, **`Knight`**, **`Bishop`**, aur **`Pawn`** jaisi sabhi specific pieces ne uss se `color` jaisi common properties ko inherit kiya hai. Isse code reuse hota hai.

3.  **Abstraction (Zaroori Cheezein Dikhana)**

      * **`Piece`** ek **abstract class** hai, kyunki iske andar pure virtual function **`canMove() = 0;`** hai.
      * Yeh class ek "contract" banati hai ki har `Piece` ko move karna aana chahiye, lekin yeh nahi batati ki *kaise*. Yeh detail har piece ki child class (jaise `Rook` ke liye seedha, `Bishop` ke liye diagonal) par chhod di jaati hai.

4.  **Polymorphism (Anek Roop)**

      * Yeh is system ki jaan hai. **`Spot`** class ke andar `Piece*` pointer hai. Is pointer mein `King`, `Queen`, ya `Pawn` kisi ka bhi object ho sakta hai.
      * Jab **`Game`** class ka `makeMove()` function kisi piece ki validity check karta hai, toh woh `piece->canMove()` call karta hai. C++ **Runtime** mein khud hi pata laga leta hai ki pointer ke peeche `Rook` hai, `Knight` hai, ya `Pawn` aur usi ka specific `canMove()` function call karta hai. Isse `Game` class ko har piece ke rule alag se janne ki zaroorat nahi padti.

---



## Vending Machine ka C++ Code

Yeh C++ code ek Vending Machine ke liye class hierarchy ko define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ko State Design Pattern ke through dikhaya gaya hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class VendingMachine;
class VendingMachineState;
class Item;

// ===================================
// == ENCAPSULATION (Core Components) ==
// ===================================
// Item class, machine ke andar rakhe product ko represent karti hai.
class Item {
private:
    int itemId;
    string name;
    double price;

public:
    Item(int id, string name, double price);
    int getId();
    string getName();
    double getPrice();
};

// Inventory class, saare items ke stock ko manage karti hai.
class Inventory {
private:
    map<Item*, int> itemStock; // Kaunsa item kitna hai

public:
    void addItem(Item* item, int quantity);
    void deductItem(Item* item);
    int getStockCount(Item* item);
};


// ===================================
// == ABSTRACTION & INHERITANCE (State Pattern Base) ==
// ===================================
// VendingMachineState ek abstract class hai. Yeh machine ki alag-alag states ka blueprint hai.
class VendingMachineState {
public:
    // Pure virtual functions (Abstraction).
    // Har state ko in actions ka jawab dena hoga.
    virtual void insertCoin(VendingMachine* machine, double amount) = 0;
    virtual void selectProduct(VendingMachine* machine, Item* item) = 0;
    virtual void dispenseProduct(VendingMachine* machine) = 0;
    virtual ~VendingMachineState() {} // Virtual destructor
};

// ===================================
// == INHERITANCE & POLYMORPHISM (Concrete States) ==
// ===================================
// Har specific state (NoCoin, HasCoin, etc.) VendingMachineState se inherit ho rahi hai.
// Aur sabhi apne methods ko override kar rahe hain.

// Jab machine mein paise nahi hain.
class NoCoinState : public VendingMachineState {
public:
    void insertCoin(VendingMachine* machine, double amount) override;
    void selectProduct(VendingMachine* machine, Item* item) override;
    void dispenseProduct(VendingMachine* machine) override;
};

// Jab machine mein paise daal diye gaye hain.
class HasCoinState : public VendingMachineState {
public:
    void insertCoin(VendingMachine* machine, double amount) override;
    void selectProduct(VendingMachine* machine, Item* item) override;
    void dispenseProduct(VendingMachine* machine) override;
};

// Jab product bik chuka hai aur dispense hone wala hai.
class SoldState : public VendingMachineState {
public:
    void insertCoin(VendingMachine* machine, double amount) override;
    void selectProduct(VendingMachine* machine, Item* item) override;
    void dispenseProduct(VendingMachine* machine) override;
};


// ===================================
// == MAIN CONTROLLER CLASS (Context for State Pattern) ==
// ===================================
// VendingMachine class poori machine ko manage karti hai.
// Yeh apni current state ke hisab se kaam karti hai.
class VendingMachine {
private:
    VendingMachineState* currentState;
    Inventory* inventory;
    double currentBalance;
    // Machine apni sabhi possible states ko hold karegi
    VendingMachineState* noCoinState;
    VendingMachineState* hasCoinState;
    VendingMachineState* soldState;

public:
    VendingMachine();
    ~VendingMachine();
    
    // User actions jo state par delegate honge
    void insertCoin(double amount);
    void selectProduct(Item* item);
    
    // Internal helper methods
    void setState(VendingMachineState* state);
    void addToBalance(double amount);
    double getBalance();
    
    // State classes ko access dene ke liye getters
    VendingMachineState* getNoCoinState();
    VendingMachineState* getHasCoinState();
    VendingMachineState* getSoldState();
};


// main function jahan se program shuru hoga
int main() {
    // Yahan par VendingMachine ka object banakar system ko chalaya ja sakta hai.
    cout << "Vending Machine System Design Ready!" << endl;
    return 0;
}
```

-----

### OOP Concepts Kaise Use Huye Hain? 🥤

Is design mein OOP concepts **State Design Pattern** ke through bahut khoobsurti se dikhaye gaye hain.

1.  **Encapsulation (Data Hiding)**

      * **`VendingMachine`** class apne `currentState`, `inventory`, aur `currentBalance` ko **`private`** rakhti hai.
      * Machine ko operate karne ke liye user sirf `insertCoin()` aur `selectProduct()` jaise **`public`** methods ka istemal karta hai. Andar ka saara complex logic (state change karna, balance update karna) user se chhupa rehta hai.

2.  **Inheritance (Virasat)**

      * Humne ek common base class **`VendingMachineState`** banayi hai.
      * Phir **`NoCoinState`**, **`HasCoinState`**, aur **`SoldState`** jaisi specific states ne uss se inherit kiya hai. Isse sabhi states mein ek consistent interface rehta hai.

3.  **Abstraction (Zaroori Cheezein Dikhana)**

      * **`VendingMachineState`** ek **abstract class** hai, kyunki iske andar pure virtual functions (`= 0;` wale) hain.
      * Yeh class ek "contract" banati hai ki har "State" ko `insertCoin`, `selectProduct`, aur `dispenseProduct` actions par react karna aana chahiye. Lekin *kaise* react karna hai, yeh har state ki apni logic par depend karta hai.

4.  **Polymorphism (Anek Roop)**

      * Yeh is pattern ki jaan hai. **`VendingMachine`** class ke paas ek pointer hai, `VendingMachineState* currentState`.
      * Jab user `vendingMachine->insertCoin()` call karta hai, toh machine yeh call apne `currentState->insertCoin()` par forward kar deti hai.
      * Agar `currentState` `NoCoinState` ko point kar raha hai, toh alag behavior hoga (balance add hoga aur state `HasCoinState` mein badal jayegi). Agar `currentState` `SoldState` ko point kar raha hai, toh alag behavior hoga (user ko error message milega). C++ **Runtime** mein pata laga leta hai ki `currentState` ke peeche kaunsa object hai aur usi ka function call karta hai.

---

## Music Streaming System ka C++ Code

Yeh C++ code ek Music Streaming System ke liye class hierarchy ko define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ko Strategy Design Pattern ke through dikhaya gaya hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class User;
class Song;
class Album;
class Artist;
class Subscription;

// ===================================
// == ENCAPSULATION (Core Components) ==
// ===================================
// Artist class, kalakaar ki details rakhti hai.
class Artist {
private:
    int artistId;
    string name;
public:
    Artist(int id, string name);
    void displayArtistProfile();
};

// Album class, ek album ke songs aur details rakhti hai.
class Album {
private:
    int albumId;
    string title;
    Artist* artist;
    vector<Song*> tracks;
public:
    Album(int id, string title, Artist* artist);
    void addTrack(Song* song);
    void displayAlbum();
};

// Song class, ek gaane ki details rakhti hai.
class Song {
private:
    int songId;
    string title;
    Artist* artist;
    Album* album;
    int durationInSeconds;
public:
    Song(int id, string title, Artist* artist, Album* album, int duration);
    void playSong();
    void displaySongDetails();
};


// ===================================
// == ABSTRACTION & INHERITANCE (Strategy Pattern Base) ==
// ===================================
// Subscription ek abstract class hai. Yeh alag-alag subscription plans ka blueprint hai.
class Subscription {
public:
    // Pure virtual functions (Abstraction).
    // Har plan ko batana hoga ki usmein ads aayenge ya nahi aur download limit kya hai.
    virtual bool canPlayAdFree() = 0;
    virtual int getDownloadLimit() = 0;
    virtual string getPlanName() = 0;
    virtual ~Subscription() {} // Virtual destructor
};

// ===================================
// == INHERITANCE & POLYMORPHISM (Concrete Strategies) ==
// ===================================
// FreeSubscription, Subscription se inherit ho raha hai.
class FreeSubscription : public Subscription {
public:
    bool canPlayAdFree() override;
    int getDownloadLimit() override;
    string getPlanName() override;
};

// PremiumSubscription, Subscription se inherit ho raha hai.
class PremiumSubscription : public Subscription {
public:
    bool canPlayAdFree() override;
    int getDownloadLimit() override;
    string getPlanName() override;
};


// ===================================
// == MAIN LOGIC & CONTROLLER CLASSES ==
// ===================================
// Playlist class, songs ka collection hai.
class Playlist {
private:
    int playlistId;
    string name;
    User* owner;
    vector<Song*> songs;
public:
    Playlist(int id, string name, User* owner);
    void addSong(Song* song);
    void removeSong(Song* song);
    void play();
};

// User class, jo Strategy (Subscription) ko use karti hai.
class User {
private:
    int userId;
    string username;
    Subscription* currentSubscription; // Strategy Pattern ka core
    vector<Playlist> playlists;
public:
    User(int id, string name);
    ~User();
    void createPlaylist(string name);
    void playSong(Song* song);
    void upgradeSubscription(Subscription* newPlan);
    void displayProfile();
};

// MusicStreamingService poore platform ko manage karta hai.
class MusicStreamingService {
private:
    map<int, Song*> songCatalog;
    map<int, User*> users;
    map<int, Artist*> artists;

public:
    ~MusicStreamingService();
    void registerUser(int id, string name);
    void addSongToCatalog(Song* song);
    User* getUser(int userId);
    Song* searchSong(string title);
};

// main function jahan se program shuru hoga
int main() {
    // Yahan par MusicStreamingService ka object banakar saare operations manage kiye ja sakte hain.
    cout << "Music Streaming System Design Ready!" << endl;
    return 0;
}
```

-----

### OOP Concepts Kaise Use Huye Hain? 🎵

Is design mein OOP concepts **Strategy Design Pattern** ke through bahut acchi tarah se dikhaye gaye hain.

1.  **Encapsulation (Data Hiding)**

      * **`User`**, **`Playlist`**, aur **`Song`** jaisi classes apne data members (`username`, `songs`, `title`) ko **`private`** rakhti hain.
      * Is data ko access ya modify karne ke liye **`public`** methods (jaise `displayProfile()`, `addSong()`) provide kiye gaye hain.

2.  **Inheritance (Virasat)**

      * Humne ek common base class **`Subscription`** banayi hai.
      * Phir **`FreeSubscription`** aur **`PremiumSubscription`** jaisi specific plans ne uss se inherit kiya hai. Isse sabhi plans mein ek consistent interface rehta hai.

3.  **Abstraction (Zaroori Cheezein Dikhana)**

      * **`Subscription`** ek **abstract class** hai, kyunki iske andar pure virtual functions (`= 0;` wale) hain.
      * Yeh class ek "contract" banati hai ki har "Subscription Plan" ko `canPlayAdFree()` aur `getDownloadLimit()` jaisi details batani hi hongi. Lekin unki values kya hongi, yeh har plan ki apni child class batayegi.

4.  **Polymorphism (Anek Roop)**

      * Yeh is pattern ki jaan hai. **`User`** class ke paas ek pointer hai, `Subscription* currentSubscription`.
      * Jab user `playSong()` call karta hai, toh method `currentSubscription->canPlayAdFree()` ko check kar sakti hai.
      * Agar `currentSubscription` `FreeSubscription` ko point kar raha hai, toh `canPlayAdFree()` `false` return karega aur system ad chala sakta hai. Agar woh `PremiumSubscription` ko point kar raha hai, toh `true` return hoga aur gaana bina ad ke chalega. C++ **Runtime** mein pata laga leta hai ki pointer ke peeche kaunsa object hai aur usi ka function call karta hai. Isse user ka plan upgrade ya downgrade karna bahut aasan ho jaata hai, bina User class ko change kiye.

----


## Social Media System ka C++ Code

Yeh C++ code ek Social Media System ke liye class hierarchy ko define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ke concepts ko istemal kiya gaya hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class User;
class Post;
class Notification;

// ===================================
// == ABSTRACTION & INHERITANCE (Base Class for Posts) ==
// ===================================
// Post ek abstract class hai. Yeh har tarah ki post (Tweet, Reply, etc.) ka blueprint hai.
class Post {
protected:
    int postId;
    User* author;
    time_t timestamp;

public:
    Post(int id, User* author);
    // Pure virtual function (Abstraction).
    // Har type ki post ko display hone ka apna tarika batana hoga.
    virtual void display() = 0;
    virtual ~Post() {} // Virtual destructor
};

// ===================================
// == INHERITANCE & POLYMORPHISM (Concrete Post Types) ==
// ===================================
// TextPost, Post class se inherit ho raha hai.
class TextPost : public Post {
private:
    string content;
public:
    TextPost(int id, User* author, string content);
    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    void display() override;
};

// Reply, TextPost se inherit ho raha hai (kyunki reply mein bhi text hota hai).
class Reply : public TextPost {
private:
    Post* parentPost; // Kis post ka reply hai
public:
    Reply(int id, User* author, string content, Post* parent);
    void display() override;
};

// Retweet, Post se inherit ho raha hai.
class Retweet : public Post {
private:
    Post* originalPost; // Asli post jise retweet kiya gaya
public:
    Retweet(int id, User* author, Post* original);
    void display() override;
};


// ===================================
// == ABSTRACTION & POLYMORPHISM (For Notifications) ==
// ===================================
// Notification ke liye ek abstract base class.
class Notification {
public:
    virtual string getMessage() = 0;
};

class FollowerNotification : public Notification {
private:
    User* follower;
public:
    FollowerNotification(User* follower);
    string getMessage() override;
};

// ===================================
// == MAIN LOGIC & CONTROLLER CLASSES ==
// ===================================
// User class, platform ke user ko represent karti hai.
class User {
private:
    int userId;
    string username;
    string displayName;
    vector<User*> followers;
    vector<User*> following;
    vector<Notification*> notifications;

public:
    User(int id, string uname, string dname);
    void follow(User* userToFollow);
    void unfollow(User* userToUnfollow);
    void post(Post* newPost);
    void viewFeed(const vector<Post*>& feed);
    void receiveNotification(Notification* notification);
};

// SocialMediaPlatform poore platform ko manage karta hai.
class SocialMediaPlatform {
private:
    map<int, User*> users;
    map<int, Post*> posts;

public:
    ~SocialMediaPlatform();
    void registerUser(int id, string uname, string dname);
    void createPost(int userId, string content);
    void createReply(int userId, int parentPostId, string content);
    void createRetweet(int userId, int originalPostId);
    void handleFollow(int followerId, int followingId);
    
    // User ke "following" list ke hisab se feed generate karna
    vector<Post*> generateFeedForUser(int userId);
};

// main function jahan se program shuru hoga
int main() {
    // Yahan par SocialMediaPlatform ka object banakar saare operations manage kiye ja sakte hain.
    cout << "Social Media System Design Ready!" << endl;
    return 0;
}
```

-----

### OOP Concepts Kaise Use Huye Hain? 🌐

1.  **Encapsulation (Data Hiding)**

      * **`User`** class apne `followers` aur `following` lists ko **`private`** rakhti hai. Kisi user ko follow ya unfollow karne ke liye `follow()` aur `unfollow()` jaise **`public`** methods ka istemal karna padta hai, jo internal lists ko safely update karte hain.

2.  **Inheritance (Virasat)**

      * Humne ek common base class **`Post`** banayi hai.
      * Phir **`TextPost`**, **`Reply`**, aur **`Retweet`** jaisi specific post types ne uss se inherit kiya hai. `Reply` ne `TextPost` se inherit kiya hai, jo multi-level inheritance ka example hai. Isse code reuse hota hai.

3.  **Abstraction (Zaroori Cheezein Dikhana)**

      * **`Post`** aur **`Notification`** **abstract classes** hain, kyunki inke andar pure virtual functions (`= 0;` wale) hain.
      * Yeh classes ek "contract" banati hain. Jaise har `Post` ko display hona aana chahiye (`display()`) aur har `Notification` ko ek message (`getMessage()`) dena aana chahiye. *Kaise* hoga, yeh detail child classes par chhod di jaati hai.

4.  **Polymorphism (Anek Roop)**

      * Is system mein polymorphism ka use feed generation mein hota hai. User ki feed ek `vector<Post*>` hoti hai. Is vector mein `TextPost`, `Reply`, aur `Retweet` - teeno ke objects ho sakte hain.
      * Jab `viewFeed()` method mein hum loop chala kar `post->display()` call karte hain, toh C++ **Runtime** mein khud hi pata laga leta hai ki pointer ke peeche kaunse type ki post hai aur usi ka specific `display()` function call karta hai. Isse feed mein har tarah ki post ko sahi tarike se dikhana aasan ho jaata hai.


----


## Learning Management System ka C++ Code

Yeh C++ code ek Learning Management System ke liye class hierarchy ko define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ke concepts ko istemal kiya gaya hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class User;
class Student;
class Instructor;
class Course;
class Content;

// ===================================
// == ABSTRACTION & INHERITANCE (Base Class for Users) ==
// ===================================
// User ek abstract class hai. Student aur Instructor dono hi User hain.
class User {
protected:
    int userId;
    string name;
    string email;
public:
    User(int id, string name, string email);
    // Pure virtual function (Abstraction).
    // Student aur Instructor ka dashboard alag dikhega.
    virtual void displayDashboard() = 0;
    virtual ~User() {} // Virtual destructor
};

// ===================================
// == INHERITANCE & POLYMORPHISM (Concrete User Types) ==
// ===================================
// Student class, User se inherit ho rahi hai.
class Student : public User {
private:
    vector<Course*> enrolledCourses;
public:
    Student(int id, string name, string email);
    void enrollInCourse(Course* course);
    // Base class ke virtual function ko override kiya gaya hai (Polymorphism)
    void displayDashboard() override;
};

// Instructor class, User se inherit ho rahi hai.
class Instructor : public User {
private:
    vector<Course*> createdCourses;
public:
    Instructor(int id, string name, string email);
    void createCourse(string title);
    void displayDashboard() override;
};

// ===================================
// == ABSTRACTION & POLYMORPHISM (For Course Content) ==
// ===================================
// Content ek abstract class hai. Yeh Course ke andar ke material (Video, Assignment) ka blueprint hai.
class Content {
protected:
    string title;
public:
    Content(string title);
    virtual void display() = 0;
    virtual ~Content() {}
};

class VideoLecture : public Content {
private:
    string videoUrl;
    int durationMinutes;
public:
    VideoLecture(string title, string url, int duration);
    void display() override;
};

class Assignment : public Content {
private:
    string dueDate;
    double maxMarks;
public:
    Assignment(string title, string date, double marks);
    void display() override;
};

// ===================================
// == ENCAPSULATION & MAIN LOGIC ==
// ===================================
// CourseModule ek course ke chapter ko represent karta hai.
class CourseModule {
private:
    string title;
    vector<Content*> contents; // Ek module mein videos aur assignments ho sakte hain (Polymorphism)
public:
    CourseModule(string title);
    ~CourseModule();
    void addContent(Content* content);
    void displayModuleContents();
};

// Course class, poore course ko manage karti hai.
class Course {
private:
    int courseId;
    string title;
    Instructor* instructor;
    vector<Student*> enrolledStudents;
    vector<CourseModule*> modules;
public:
    Course(int id, string title, Instructor* instructor);
    ~Course();
    void enrollStudent(Student* student);
    void addModule(CourseModule* module);
    void displayCoursePage();
};

// Submission class, ek student ke assignment submission ko track karti hai.
class Submission {
private:
    Assignment* assignment;
    Student* student;
    string submissionText;
    double marksObtained;
public:
    Submission(Assignment* a, Student* s, string text);
    void gradeSubmission(double marks);
};


// ===================================
// == MAIN CONTROLLER CLASS ==
// ===================================
// LmsPlatform poore system ko manage karta hai.
class LmsPlatform {
private:
    map<int, User*> users;
    map<int, Course*> courses;
public:
    ~LmsPlatform();
    void registerUser(User* user);
    void createCourse(int instructorId, string title);
    void enrollStudentInCourse(int studentId, int courseId);
    void submitAssignment(int studentId, int courseId, int moduleId, string submissionText);
};

// main function jahan se program shuru hoga
int main() {
    // Yahan par LmsPlatform ka object banakar saare operations manage kiye ja sakte hain.
    cout << "Learning Management System Design Ready!" << endl;
    return 0;
}
```

-----

### OOP Concepts Kaise Use Huye Hain? 🎓

1.  **Encapsulation (Data Hiding)**

      * **`Course`** class apne `enrolledStudents` aur `modules` ki lists ko **`private`** rakhti hai. Kisi student ko enroll karne ke liye `enrollStudent()` jaise **`public`** methods ka istemal karna padta hai, jo internal lists ko safely update karte hain.

2.  **Inheritance (Virasat)**

      * Humne ek common base class **`User`** banayi hai, jisse **`Student`** aur **`Instructor`** inherit karte hain.
      * Isi tarah, `Content` base class se **`VideoLecture`** aur **`Assignment`** inherit karte hain, jisse code reuse hota hai.

3.  **Abstraction (Zaroori Cheezein Dikhana)**

      * **`User`** aur **`Content`** **abstract classes** hain, kyunki inke andar pure virtual functions (`= 0;` wale) hain.
      * Yeh classes ek "contract" banati hain. Jaise har `User` ka ek dashboard (`displayDashboard()`) hona chahiye aur har `Content` ko display (`display()`) hona aana chahiye. *Kaise* hoga, yeh detail child classes par chhod di jaati hai.

4.  **Polymorphism (Anek Roop)**

      * Is system mein polymorphism do jagah bahut acche se dikhta hai:
          * **User Management**: `LmsPlatform` `map<int, User*>` mein `Student` aur `Instructor` dono ko store karta hai. Jab `user->displayDashboard()` call hota hai, toh C++ **Runtime** mein pata laga leta hai ki user student hai ya instructor aur usi ka specific dashboard display karta hai.
          * **Course Content**: `CourseModule` ke `vector<Content*>` mein `VideoLecture` aur `Assignment` dono objects store ho sakte hain. Jab module ke contents display kiye jaate hain, toh har content ka apna `display()` method call hota hai.

---


## Parking Ticket Violation System ka C++ Code

Yeh C++ code ek Parking Ticket Violation System ke liye class hierarchy ko define karta hai. Ismein **Encapsulation, Inheritance, Polymorphism, aur Abstraction** ke concepts ko istemal kiya gaya hai.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Forward Declarations
class Vehicle;
class ParkingOfficer;
class Violation;
class ParkingTicket;

// ===================================
// == ENCAPSULATION (Core Components) ==
// ===================================
// Vehicle class, gaadi ki details rakhti hai.
class Vehicle {
private:
    string licensePlate;
    string make;
    string color;
    string ownerName;

public:
    Vehicle(string plate, string make, string color, string owner);
    string getLicensePlate();
    void displayVehicleDetails();
};

// ParkingOfficer class, ticket kaatne wale officer ki details rakhti hai.
class ParkingOfficer {
private:
    int officerId;
    string name;
    string badgeNumber;

public:
    ParkingOfficer(int id, string name, string badge);
    void displayOfficerDetails();
    // Officer ek ticket issue karta hai
    ParkingTicket* issueTicket(Vehicle* vehicle, Violation* violation, string location);
};

// ===================================
// == ABSTRACTION & INHERITANCE (Base Class for Violations) ==
// ===================================
// Violation ek abstract class hai. Yeh alag-alag type ke violations ka blueprint hai.
class Violation {
protected:
    string violationCode;
    string description;
public:
    Violation(string code, string desc);
    // Pure virtual function (Abstraction).
    // Har violation ka fine alag ho sakta hai.
    virtual double calculateFine() = 0;
    virtual void displayViolationInfo() = 0;
    virtual ~Violation() {} // Virtual destructor
};

// ===================================
// == INHERITANCE & POLYMORPHISM (Concrete Violation Types) ==
// ===================================
// ExpiredMeterViolation, Violation class se inherit ho raha hai.
class ExpiredMeterViolation : public Violation {
public:
    ExpiredMeterViolation();
    double calculateFine() override;
    void displayViolationInfo() override;
};

// NoParkingZoneViolation, Violation class se inherit ho raha hai.
class NoParkingZoneViolation : public Violation {
public:
    NoParkingZoneViolation();
    double calculateFine() override;
    void displayViolationInfo() override;
};

// ===================================
// == ABSTRACTION & POLYMORPHISM (For Payment) ==
// ===================================
// Payment ke liye ek abstract base class.
class PaymentGateway {
public:
    virtual bool processPayment(double amount, string ticketId) = 0;
};

class OnlinePaymentGateway : public PaymentGateway {
public:
    bool processPayment(double amount, string ticketId) override;
};


// ===================================
// == MAIN LOGIC & CONTROLLER CLASSES ==
// ===================================
// ParkingTicket class, ek ticket ki poori jaankari rakhti hai.
class ParkingTicket {
private:
    string ticketId;
    Vehicle* vehicle;
    ParkingOfficer* officer;
    Violation* violation; // Polymorphism ka istemal
    string location;
    time_t issueTime;
    double fineAmount;
    bool isPaid;

public:
    ParkingTicket(string id, Vehicle* v, ParkingOfficer* o, Violation* viol, string loc);
    void calculateAndSetFine();
    void markAsPaid();
    void displayTicket();
};

// ViolationSystem poore system ko manage karta hai.
class ViolationSystem {
private:
    map<string, ParkingTicket*> tickets; // Ticket ID se ticket search karna
    vector<ParkingOfficer*> officers;

public:
    ~ViolationSystem();
    void addOfficer(ParkingOfficer* officer);
    void recordViolation(ParkingTicket* ticket);
    ParkingTicket* lookupTicket(string ticketId);
    void processPayment(string ticketId, PaymentGateway* paymentMethod);
};

// main function jahan se program shuru hoga
int main() {
    // Yahan par ViolationSystem ka object banakar saare operations manage kiye ja sakte hain.
    cout << "Parking Ticket Violation System Design Ready!" << endl;
    return 0;
}
```

-----

### OOP Concepts Kaise Use Huye Hain? 🚓

1.  **Encapsulation (Data Hiding)**

      * **`Vehicle`**, **`ParkingOfficer`**, aur **`ParkingTicket`** jaisi classes apne data members (`licensePlate`, `badgeNumber`, `fineAmount`) ko **`private`** rakhti hain.
      * Is data ko access ya modify karne ke liye **`public`** methods (jaise `getLicensePlate()`, `markAsPaid()`) provide kiye gaye hain, jisse system ka data organized aur safe rehta hai.

2.  **Inheritance (Virasat)**

      * Humne ek common base class **`Violation`** banayi hai.
      * Phir **`ExpiredMeterViolation`** aur **`NoParkingZoneViolation`** jaisi specific violations ne uss se `violationCode` jaisi common properties ko inherit kiya hai. Isse naye type ke violations (jaise 'Handicap Parking') add karna aasan ho jaata hai.

3.  **Abstraction (Zaroori Cheezein Dikhana)**

      * **`Violation`** aur **`PaymentGateway`** **abstract classes** hain, kyunki inke andar pure virtual functions (`= 0;` wale) hain.
      * Yeh classes ek "contract" banati hain. Jaise har `Violation` ka fine calculate (`calculateFine()`) hona hi chahiye aur har `PaymentGateway` se payment (`processPayment()`) hona hi chahiye. *Kaise* hoga, yeh detail child classes par chhod di jaati hai.

4.  **Polymorphism (Anek Roop)**

      * **`ParkingTicket`** class mein `Violation* violation` pointer iska sabse accha example hai. Is pointer mein `ExpiredMeterViolation` ya `NoParkingZoneViolation` kisi ka bhi object ho sakta hai.
      * Jab `calculateAndSetFine()` method mein `violation->calculateFine()` call hota hai, toh C++ **Runtime** mein khud hi pata laga leta hai ki pointer ke peeche kaunsa violation hai aur usi ke hisab se fine calculate karta hai. Isse `ParkingTicket` class ko har violation ke fine amount ke baare mein alag se janne ki zaroorat nahi padti.


----