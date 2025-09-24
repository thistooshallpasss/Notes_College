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