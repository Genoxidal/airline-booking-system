# Technical Specifications Document: Airline Booking System API

## Project Overview
- **Project Name:** Airline Booking System API  
- **Date:** July 17, 2025  
- **Version:** 1.0  
- **Authors:** Ryan Oxales, Christian Nievera  

---

## Table of Contents
1. [Introduction](#1-introduction)  
2. [Functional Requirements](#2-functional-requirements)  
3. [Non-Functional Requirements](#3-non-functional-requirements)  
4. [Visual Mockup (Figma)](#4-visual-mockup-figma)  
5. [Data Requirements](#5-data-requirements)  
6. [Technology Stack](#6-technology-stack)  
7. [Development Team](#7-development-team)  
8. [API Endpoints](#8-api-endpoints)  
9. [Authentication and Authorization](#9-authentication-and-authorization)  
10. [Error Handling](#10-error-handling)  
11. [External Interface Requirements](#11-external-interface-requirements)  
12. [Deployment](#12-deployment-to-be-detailed)  
13. [Future Enhancements](#13-future-enhancements-to-be-detailed)  
14. [Glossary](#14-glossary)  
15. [Appendices](#15-appendices)  

---

## 1. Introduction
This document defines the technical specifications for the Airline Booking System, covering both frontend and backend components. It details the system’s architecture, features, and development strategy to ensure a robust and scalable booking platform.

---

## 2. Functional Requirements

### ✈️ Flight Search
- Frontend UI for inputting origin, destination, dates, and number of passengers.
- Display results with airline, flight number, departure/arrival times, duration, price, and seats.
- Filters and sorting on search results.
- API to query flights and return structured flight data.

### 📘 Booking Management
- User form for entering passenger info.
- Seat selection (interactive seat map if available).
- Booking summary page before confirmation.
- Confirmation page with booking ID and itinerary.
- Users can view, update, or cancel bookings.

### 👤 User Management
- Registration/login interfaces.
- Profile management (view/update).
- Password recovery.
- Secure backend endpoints for user operations.

### 💳 Payment Integration *(Placeholder)*
- Secure form for payment input.
- Payment status UI.
- API integration with Stripe/PayPal.

### 🛠️ Admin Functionalities *(Placeholder)*
- Admin dashboard for managing flights, routes, aircraft, and users.
- Admin CRUD operations via protected endpoints.

---

## 3. Non-Functional Requirements

### 🚀 Performance
- API response time: [X] ms for search, [Y] sec for booking.
- Handle [N] concurrent users, [M] TPS.

### 🔐 Security
- JWT authentication + role-based access control.
- SSL/TLS encryption, hashed passwords.
- Protection against SQLi, XSS, CSRF.

### ✅ Usability
- Intuitive, accessible (WCAG 2.1 AA), responsive frontend.

### 🧱 Reliability
- Uptime target: 99.9%  
- Error handling with user/developer-friendly messages.

### 🧩 Maintainability & Portability
- Modular code, testable components.
- Portable deployment on cloud or on-prem.

### 🌐 Compatibility
- Frontend supports latest Chrome, Firefox, Edge, Safari.

---

## 4. Visual Mockup (Figma)
- **Figma Design Link:** [Insert Figma link here]

---

## 5. Data Requirements

### ✍️ Data Models
- **User, Airport, Flight, Booking, Passenger, Payment, Ticket**

Refer to [Detailed Schema](#detailed-database-schema) below.

---

### 💽 Detailed Database Schema (MySQL/PostgreSQL)
**users**  
- `user_id`, `first_name`, `last_name`, `email`, `password`, `mobile_number`, `role`, `created_on`, `updated_on`

**airport_info**  
- `airport_id`, `name`, `logo`, `email`, `mobile_number`, `address`

**flights**  
- `flight_id`, `from_location`, `to_location`, `departure_date`, `arrival_date`, `seats_available`, `price`

**booking_details**  
- `booking_id`, `user_id`, `flight_id`, `passengers`, `seat_number`, `total_amount`

**passenger_details**  
- `passenger_id`, `booking_id`, `first_name`, `last_name`, `email`, `baggage_details`

**payment_details**  
- `payment_id`, `booking_id`, `amount`, `payment_method`, `status`

**ticket_info**  
- `ticket_id`, `user_id`, `passenger_id`, `class`, `fare`

---

### 🧠 Storage & Security Strategy
- Encrypted sensitive data (SSL, at rest)
- Read replicas, connection pooling
- Regular backups, archiving
- GDPR/CCPA-compliant handling of user data

---

## 6. Technology Stack

| Layer        | Technology                |
|--------------|---------------------------|
| Frontend     | HTML, CSS, JavaScript, Vue.js |
| Backend      | Node.js + Express *(tentative)* |
| Database     | PostgreSQL or MySQL       |
| Authentication | JWT                      |
| Payment      | Stripe or PayPal *(planned)* |

---

## 7. Development Team

- Ryan Oxales  
- Christian Nievera  

---

## 8. API Endpoints (Overview)

```http
GET    /api/flights                  # Retrieve available flights  
POST   /api/bookings                 # Create a new booking  
GET    /api/bookings/:id             # View booking details  
POST   /api/users/register           # User registration  
POST   /api/users/login              # User login  
