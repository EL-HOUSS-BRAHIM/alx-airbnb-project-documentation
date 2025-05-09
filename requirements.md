# 📌 Backend Requirement Specifications – Airbnb Clone

This document outlines the **technical** and **functional** requirements for key backend features in the Airbnb Clone project. These specifications cover API endpoints, input/output contracts, validation logic, and performance expectations.

---

## 🔐 1. User Authentication

### 🔧 Functional Requirements
- Users must be able to register as a guest or host.
- Users must be able to log in and receive a JWT token.
- Users should be able to update their profiles securely.

### 📡 API Endpoints

| Method | Endpoint        | Description                | Auth Required |
|--------|------------------|----------------------------|----------------|
| POST   | /api/auth/register | Register a new user        | No             |
| POST   | /api/auth/login    | Authenticate user          | No             |
| PUT    | /api/users/:id     | Update user profile        | Yes            |

### 🧾 Input/Output Specification

#### Registration Payload
```json
{
  "first_name": "John",
  "last_name": "Doe",
  "email": "john@example.com",
  "password": "Secure123!",
  "role": "host"
}
````

#### Response (Success)

```json
{
  "message": "User registered successfully",
  "token": "<JWT>"
}
```

### ✅ Validation Rules

* Email must be unique and valid.
* Password must be at least 8 characters with letters and numbers.
* Role must be one of: guest, host.

---

## 🏡 2. Property Management

### 🔧 Functional Requirements

* Hosts can create, update, and delete listings.
* Listings should include details such as title, description, price, amenities, and availability.

### 📡 API Endpoints

| Method | Endpoint             | Description           | Auth Required |
| ------ | -------------------- | --------------------- | ------------- |
| POST   | /api/properties      | Add a new property    | Yes (Host)    |
| PUT    | /api/properties/\:id | Edit property details | Yes (Host)    |
| DELETE | /api/properties/\:id | Delete a property     | Yes (Host)    |
| GET    | /api/properties      | View all listings     | No            |

### 🧾 Input/Output Specification

#### Create Property Payload

```json
{
  "name": "Luxury Loft",
  "description": "Spacious downtown loft",
  "location": "New York, NY",
  "pricepernight": 150.00,
  "amenities": ["wifi", "kitchen", "air conditioning"]
}
```

#### Response (Success)

```json
{
  "message": "Property listed successfully",
  "property_id": "uuid"
}
```

### ✅ Validation Rules

* Name, description, location, and price are required.
* Price must be a positive number.
* Only authenticated hosts can create listings.

---

## 📅 3. Booking System

### 🔧 Functional Requirements

* Guests can book properties for a date range.
* Prevent overlapping bookings.
* Allow users to cancel bookings.

### 📡 API Endpoints

| Method | Endpoint           | Description         | Auth Required |
| ------ | ------------------ | ------------------- | ------------- |
| POST   | /api/bookings      | Create new booking  | Yes (Guest)   |
| DELETE | /api/bookings/\:id | Cancel a booking    | Yes           |
| GET    | /api/bookings/user | Get user’s bookings | Yes           |

### 🧾 Input/Output Specification

#### Create Booking Payload

```json
{
  "property_id": "uuid",
  "start_date": "2025-05-10",
  "end_date": "2025-05-15"
}
```

#### Response (Success)

```json
{
  "message": "Booking confirmed",
  "booking_id": "uuid",
  "total_price": 750.00
}
```

### ✅ Validation Rules

* Start date must be before end date.
* Prevent double bookings using a date conflict check.
* Only guests can book properties.

---

## 🚀 Performance & Security Criteria

* All endpoints should respond in <500ms for 95% of requests.
* Passwords must be hashed using bcrypt or Argon2.
* API should throttle excessive requests to prevent abuse.
* JWT tokens must be used for authentication with expiration.

---

## 📌 Notes

* All timestamps should be in UTC and follow ISO 8601.
* The system must support multi-currency transactions in the future.

