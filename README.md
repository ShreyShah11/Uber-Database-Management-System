# Uber-Database-Management-System
## 🧩 Entity-Relationship (ER) Model

The system is designed around core entities and their relationships, covering ride requests, payments, drivers, discounts, and user interactions. The ER diagram follows standard notation and ensures 3NF-compliant mapping to relational schema.

### 📌 Core Entities

- **USER**: Represents registered riders with basic details (User_ID, Name, Phone, Email).
- **DRIVER**: Contains info about drivers (Driver_ID, Name, Email, Phone, License, Vehicle Assigned).
- **VEHICLES**: Maintains vehicle data like Vehicle_ID, Type, Model, linked to drivers.
- **RIDE**: Central entity capturing ride data including pickup/dropoff, status, fare, and time.
- **PAYMENT**: Tracks transaction details for rides with mode, amount, and associated promo codes.
- **DISCOUNTS**: Promo codes with offer amount, expiry, and other conditions.
- **RATINGS**: Feedback data on rides submitted by users.
- **CANCELLATION**: Captures penalties and timestamps for cancelled rides.

### 🔗 Relationships Overview

- `User - Requests -> Ride` (1:N): A user can request multiple rides.
- `Driver - Accepts -> Ride` (1:N): Each ride is accepted by one driver.
- `User - Pays -> Payment` (1:N): Each user can pay for many rides.
- `Discount - Applied -> Payment` (1:N): Multiple payments can use the same promo code.
- `Ride - Has -> Rating` (1:1): A ride has one associated rating by the user.
- `Driver - Owns -> Vehicle` (1:N): A driver can own multiple vehicles.
- `Ride - Cancels -> Cancellation` (1:1 optional): Some rides are cancelled and incur penalties.

---

## 🔄 Mapping to Relational Schema

Every entity and relationship has been carefully normalized and translated into relational tables with appropriate:
- Primary & foreign keys
- Constraints (NOT NULL, UNIQUE)
- Referential integrity
- Many-to-many relationships resolved via bridge tables where required

---

## 🛠 ER Design Tools Used

- **Draw.io** / Lucidchart for visual modeling  
- Design decisions based on real-world ride-sharing use cases

## 🛠 Implementation in MySQL

The ER model was translated into a fully functional **MySQL database system**, including:

### 🧾 Schema Implementation
- Created all entities as **relational tables** using `CREATE TABLE` statements.
- Applied **primary and foreign key constraints** to ensure referential integrity.
- Used appropriate **data types** (e.g., `VARCHAR`, `DATE`, `DECIMAL`, `ENUM`) for real-world modeling.
- Added **CHECK constraints**, `NOT NULL`, and `AUTO_INCREMENT` where needed.

### 🗃 Sample Tables Created
- `Users(User_ID, Name, Email, Phone)`
- `Drivers(Driver_ID, Name, Email, Phone, Vehicle_ID)`
- `Vehicles(Vehicle_ID, Type, Model, Driver_ID)`
- `Rides(Ride_ID, User_ID, Driver_ID, Pickup, Dropoff, Fare, Status, Start_Time, End_Time)`
- `Payments(Payment_ID, Ride_ID, Promo_ID, Final_Amount, Pay_Mode, Status)`
- `Ratings(Rating_ID, Ride_ID, User_ID, Driver_ID, Rating, Feedback)`
- `Discounts(Promo_ID, Code, Offer_Amount, Expiry_Date)`
- `Cancellations(Ride_ID, Cancel_Time, Penalty)`

> All schema definitions are available in `schema.sql`.

---

### 🔍 SQL Query Highlights
- **SELECT queries** for trip history, user analytics, driver ratings
- **JOINs** for multi-table queries involving rides, payments, ratings
- **GROUP BY** and **aggregation** for revenue and performance reports
- **Subqueries** to find top drivers, most active users, etc.
- **UPDATE** and **DELETE** operations for ride status changes and cancellations

---

### 🧪 Data Population & Testing
- Populated with **realistic test data** for 50+ users, drivers, and 100+ rides
- Validated:
  - Ride booking with driver availability
  - Discount code application
  - Payment workflow
  - Cancellation penalties
  - Feedback submission
