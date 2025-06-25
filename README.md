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

