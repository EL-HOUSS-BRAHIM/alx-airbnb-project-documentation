# 🔄 Data Flow Diagram – Airbnb Clone Backend

This document explains the **Data Flow Diagram (DFD)** for the Airbnb Clone backend, illustrating how data flows between users, system processes, and the database.

---

## 🎯 Objective

To visualize the movement of data across the system’s core components and understand how backend processes interact with users and data storage systems.

---

## 🧱 Components in the DFD

### 🧑‍💼 External Entities:
- **Guest**
- **Host**
- **Admin**
- **Payment Gateway**

### ⚙️ Key Processes:
- User Registration & Login
- Property Listing Management
- Property Search & Filter
- Booking Creation & Cancellation
- Review Submission
- Payment Processing
- Admin Management

### 🗄️ Data Stores:
- User Database
- Property Listings
- Booking Records
- Reviews
- Payment History

---

## 🔁 Data Flows Overview

- Guests/Hosts submit data through forms (registration, property listings, bookings, etc.).
- Backend processes validate and route this data to appropriate databases.
- Booking and payment systems interact with each other for availability and transaction management.
- Admins access data to monitor and manage the platform.

---

## 📁 Files Included

- `data-flow.png`: The exported DFD created using [Draw.io](https://draw.io), representing system-wide data movement.

---
