# Movie Ticket Booking System 🎬

A **menu-driven Movie Ticket Booking System** developed in **C++** for a single cinema. This project applies **Object-Oriented Programming, UML-based system design, modular programming, and SOLID principles** to model a practical movie booking workflow.

## 🎬 Project Overview

The system allows a customer to:

* View movies currently playing
* View available shows
* Display the seat layout
* Select one or more seats
* Check seat availability
* Calculate ticket price based on seat type
* Pay using UPI, Card, or Cash
* Confirm a booking after successful payment
* Print the booking ticket
* Cancel an existing booking
* Release seats after cancellation

The project was developed as part of the **System Design (TCS-504)** coursework.

## 🏗️ System Architecture

The system is divided into multiple classes, with each class having a specific responsibility.

### Core Classes

| Class      | Responsibility                                                    |
| ---------- | ----------------------------------------------------------------- |
| `Movie`    | Stores movie title, language, and duration                        |
| `Seat`     | Represents a physical seat and its type                           |
| `Screen`   | Manages seats belonging to a screen                               |
| `Cinema`   | Manages screens in the cinema                                     |
| `Show`     | Represents a movie screening on a particular screen and time      |
| `ShowSeat` | Maintains the availability status of a seat for a particular show |
| `Customer` | Stores customer information                                       |
| `Booking`  | Maintains booking details and selected seats                      |

### Service & Supporting Classes

| Class             | Responsibility                                   |
| ----------------- | ------------------------------------------------ |
| `Payment`         | Abstract payment interface                       |
| `UpiPayment`      | Handles UPI payment                              |
| `CardPayment`     | Handles card payment                             |
| `CashPayment`     | Handles cash payment                             |
| `PriceCalculator` | Calculates the total booking amount              |
| `TicketPrinter`   | Prints ticket details                            |
| `BookingService`  | Coordinates the booking and cancellation process |

## 💺 Seat Pricing

| Seat Type | Price |
| --------- | ----: |
| Silver    |  ₹150 |
| Gold      |  ₹250 |
| Platinum  |  ₹400 |

## 💳 Payment Methods

The system supports:

* **UPI**
* **Card**
* **Cash**

The payment system uses an abstract `Payment` interface with separate implementations for each payment method.

## 🧩 OOP Concepts Demonstrated

* **Encapsulation** through private data members and public methods
* **Abstraction** through the `Payment` interface
* **Inheritance** through `UpiPayment`, `CardPayment`, and `CashPayment`
* **Runtime Polymorphism** through the `Payment` hierarchy
* **Compile-Time Polymorphism** through overloaded methods/constructors
* **Static Members** for generating unique booking IDs
* **`this` Keyword** for referring to the current object
* **Composition** between Cinema–Screen, Screen–Seat, and Show–ShowSeat
* **Aggregation** between Show–Movie
* **Association** between collaborating classes

## 📐 UML Design

The project includes:

### Class Diagram

The UML class diagram represents:

* Class attributes and methods
* Relationships between classes
* Multiplicities
* Composition and aggregation
* Payment inheritance hierarchy

### Sequence Diagram

The sequence diagram represents the **book a ticket and make payment** workflow, starting from seat selection and availability checking through price calculation, payment, booking confirmation, and ticket printing.

## 🔄 Booking Workflow

```text
Customer
   ↓
Select Movie / Show
   ↓
Display Seat Layout
   ↓
Select Seat(s)
   ↓
Check Availability
   ↓
Calculate Price
   ↓
Select Payment Method
   ↓
Process Payment
   ↓
Payment Successful?
   ├── No → Booking Not Confirmed
   │        Seats Released
   │
   └── Yes
        ↓
   Confirm Booking
        ↓
   Generate Booking ID
        ↓
   Print Ticket
```

## 🛡️ Edge Case Handling

The system handles:

* Attempting to book an already-booked seat
* Failed payment
* Cancelling a booking
* Invalid seat numbers
* Invalid menu choices

A failed payment does not confirm the booking, while cancellation makes the previously booked seats available again.

## 🧱 SOLID Principles

### Single Responsibility Principle (SRP)

Each class has a focused responsibility. For example, `PriceCalculator` handles pricing while `TicketPrinter` handles ticket printing.

### Open/Closed Principle (OCP)

The payment hierarchy allows new payment implementations to be added without changing the existing payment classes.

### Liskov Substitution Principle (LSP)

`UpiPayment`, `CardPayment`, and `CashPayment` can be used through the common `Payment` interface.

### Interface Segregation Principle (ISP)

The payment abstraction contains only the operation required for payment.

### Dependency Inversion Principle (DIP)

The booking process works with the `Payment` abstraction instead of depending directly on a specific payment implementation.

## 📁 Project Structure

```text
Movie_Ticket_Booking_System/
│
├── 01_Movie.cpp
├── 02_Seat.cpp
├── 03_Screen.cpp
├── 04_Cinema.cpp
├── 05_ShowSeat.cpp
├── 06_Show.cpp
├── 07_Customer.cpp
├── 08_Booking.cpp
├── 09_Payment.cpp
├── 10_PaymentTypes.cpp
├── 11_PriceCalculator.cpp
├── 12_TicketPrinter.cpp
├── 13_BookingService.cpp
└── main.cpp
```

The project follows a **one-class-per-file** structure without traditional header files.

## ▶️ How to Run

Compile the project using:

```bash
g++ main.cpp -o MovieTicketBooking
```

Run the program on Windows:

```bash
MovieTicketBooking.exe
```

Or on Linux/macOS:

```bash
./MovieTicketBooking
```

## 🖥️ Main Menu

```text
====================================
     MOVIE TICKET BOOKING SYSTEM
====================================
1. List Movies
2. List Shows
3. Display Seat Layout
4. Book Ticket
5. Cancel Booking
6. Print Ticket
7. Exit
```

## 🚀 Future Enhancements

Possible future improvements include:

* Database integration
* Multiple cinemas and locations
* Online payment gateway integration
* User authentication
* Graphical seat selection
* Booking history
* Email/SMS ticket confirmation
* Additional payment methods such as Net Banking

## 👨‍💻 Author

**Manthan**

B.Tech CSE | Semester 5

**Course:** System Design
**Subject Code:** TCS-504
