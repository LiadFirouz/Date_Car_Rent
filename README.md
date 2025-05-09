# Date_Car_Rent
# 📅 Date, 🚗 Car & 📝 Rent Java Classes

This repository contains three fully-implemented Java classes as part of an OOP (Object-Oriented Programming) exercise. The focus is on encapsulation, data validation, method design, object copying, and inter-class behavior.

---

## 📁 Classes Overview

### 1. `Date.java`

Represents a calendar date with validation (including leap years). Provides functionality for comparing dates, checking legality, and computing differences in days.

<details>
<summary>Click to expand Date features</summary>

#### 🔐 Fields:
- `int _day` – Day (1–31)
- `int _month` – Month (1–12)
- `int _year` – Four-digit year

#### 🔨 Constructors:
- `Date(int day, int month, int year)` – If invalid, defaults to 01/01/2000
- `Date(Date other)` – Copy constructor

#### 📥 Methods:
- `getDay()`, `getMonth()`, `getYear()`
- `setDay()`, `setMonth()`, `setYear()` – Ignore invalid changes
- `boolean equals(Date other)`
- `boolean before(Date other)`
- `boolean after(Date other)` *(uses only `before()`)*
- `int difference(Date other)`
- `String toString()` – Format: `dd/mm/yyyy`
- `Date tomorrow()` – Returns new object for the next day

</details>

---

### 2. `Car.java`

Represents a car with rating, brand, and transmission type. Includes validation and comparison logic.

<details>
<summary>Click to expand Car features</summary>

#### 🔐 Fields:
- `int _id` – 7-digit license number, or `9999999` if invalid
- `char _type` – Rating (`A`, `B`, `C`, `D`), default: `A`
- `String _brand`
- `boolean _isManual` – Transmission type

#### 🔨 Constructors:
- `Car(int id, char type, String brand, boolean isManual)`
- `Car(Car other)`

#### 📥 Methods:
- `getId()`, `getType()`, `getBrand()`, `isManual()`
- `setId()`, `setType()`, `setBrand()`, `setIsManual()` – With validation
- `String toString()` – Format: `id:1234567 type:A brand:Mazda gear:manual`
- `boolean equals(Car other)` – Compares by type, brand, and gear
- `boolean better(Car other)` – Based on rating & gear
- `boolean worse(Car other)` – Must use `better()`

</details>

---

### 3. `Rent.java`

Represents a car rental record for a customer, with validation and logic for pricing, upgrades, overlaps, and more.

<details>
<summary>Click to expand Rent features</summary>

#### 🔐 Fields:
- `String _name` – Customer name
- `Car _car` – Rented car
- `Date _pickDate` – Start date
- `Date _returnDate` – Return date (must be at least 1 day later)

#### 🔨 Constructors:
- `Rent(String name, Car car, Date pick, Date ret)`  
  Ensures valid dates; adjusts `returnDate` if needed.
- `Rent(Rent other)` – Copy constructor

#### 📥 Methods:
- Getters & Setters for all fields (with defensive copying)
- `boolean equals(Rent other)` – Compares name, car, and both dates
- `int howManyDays()` – Total number of rental days
- `int getPrice()` – 
  - A: 100₪/day  
  - B: 150₪/day  
  - C: 180₪/day  
  - D: 240₪/day  
  - 10% discount per full week (7 days)
- `int upgrade(Car newCar)` – Replaces car if it's better and returns extra cost
- `Rent overlap(Rent other)` – Returns merged Rent object if periods overlap for same car & customer, otherwise `null`
- `String toString()` – Format:  
  `Name:Rama From:30/10/2022 To:12/11/2022 Type:B Days:13 Price:1845`

</details>

---

## 💻 Compilation & Execution

To compile:
```bash
javac Date.java
javac Car.java
javac Rent.java
