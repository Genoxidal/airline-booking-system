# Technical Specifications Document

## Project Name: Airline Booking System  
**Version:** 1.0.0  
**Date:** July 30, 2025  
**Author(s):** Christian Nievera and Ryan Oxales  

---

## Table of Contents

1. [Introduction](#introduction)  
2. [Overall Description](#overall-description)  
3. [Visual Mockup Reference](#visual-mockup-reference)  
4. [Features](#features)  
5. [Functional Requirements](#functional-requirements)  
6. [Non-Functional Requirements](#non-functional-requirements)  
7. [Data Requirements](#data-requirements)  
8. [External Interface Requirements](#external-interface-requirements)  
9. [Glossary](#glossary)  
10. [Appendices](#appendices)  

---

## Introduction

This document outlines the technical specifications for the "Airline Booking System" project. It provides a comprehensive overview of the system's design, functionality, and requirements to guide development and ensure alignment among stakeholders.

---

## Overall Description

The Airline Booking System is a full-stack web application designed to streamline flight reservations for airline customers.  
Its purpose is to allow users to search for flights, make bookings, manage passenger information, and process payments.  

**Target Users:**  
- Passengers  
- Admin Staff  
- Airline Management  

**Problems Solved:**  
- Manual flight reservations  
- Delayed updates to availability  
- Fragmented data across multiple platforms  

---

## Visual Mockup Reference

### Entity Relationship Diagram (ERD)

![ERD](https://drive.google.com/uc?export=view&id=1V5g0pUB92cq_z69OPMH1VSaNmNy0bjEu)

*Figure 1: ERD showing core relationships in the Airline Booking System.*

---

## Features

- User registration and login  
- Flight search and filtering  
- Booking and payment processing  
- Passenger management (add/edit/delete)  
- Admin dashboard for managing flights, routes, and aircrafts  
- Email confirmation for successful bookings  
- Seat selection interface  

---

## Functional Requirements

**FR-001:** The system shall allow users to register and authenticate securely.  
**FR-002:** The system shall allow users to search flights by date, origin, and destination.  
**FR-003:** The system shall display available seats and pricing for selected flights.  
**FR-004:** The system shall allow users to book flights with passenger details.  
**FR-005:** The system shall process payments through a secure payment gateway.  
**FR-006:** The system shall store and retrieve booking history for users.  
**FR-007:** The system shall allow admins to add/edit/delete flights, aircrafts, and routes.  
**FR-008:** The system shall send a confirmation email after successful booking.  

---

## Non-Functional Requirements

- **Performance:** Page loads should complete within 2 seconds under normal load.  
- **Usability:** Intuitive interface with minimal steps to complete a booking.  
- **Security:** JWT authentication, bcrypt password hashing, and HTTPS required.  
- **Scalability:** Support up to 10,000 users with load balancing in production.  
- **Availability:** 99.9% uptime with cloud-based hosting.  
- **Maintainability:** Modular code structure following MVC pattern.  

---

## Data Requirements

### Users
- `id`: UUID  
- `name`: String  
- `email`: String (unique)  
- `password`: Hashed string  
- `role`: Enum ("admin", "user")  

### Flights
- `id`: UUID  
- `flight_number`: String  
- `origin`: String  
- `destination`: String  
- `departure_time`: DateTime  
- `arrival_time`: DateTime  
- `aircraft_id`: UUID  

### Aircraft
- `id`: UUID  
- `model`: String  
- `capacity`: Integer  

### Bookings
- `id`: UUID  
- `user_id`: UUID (FK)  
- `flight_id`: UUID (FK)  
- `booking_date`: DateTime  
- `status`: Enum ("confirmed", "cancelled")  
- `total_amount`: Decimal  

### Passengers
- `id`: UUID  
- `booking_id`: UUID (FK)  
- `full_name`: String  
- `age`: Integer  
- `seat_number`: String  

---

## External Interface Requirements

- **Payment Gateway:** Integration with Stripe or PayPal API  
- **Email Service:** Nodemailer for sending booking confirmations  
- **Authentication:** JWT-based session management  

---

## Glossary

- **JWT:** JSON Web Token, used for secure user authentication  
- **UUID:** Universally Unique Identifier  
- **REST API:** A web API following RESTful principles  
- **CRUD:** Create, Read, Update, Delete operations  
- **ORM:** Object-Relational Mapping (e.g., Mongoose)  
- **ERD:** Entity Relationship Diagram  

---

## Appendices

- [Source Code Repository](https://github.com/Genoxidal/airline-booking-system)  
- [Deployment Instructions](to be added)  
- [Live Demo](to be added)

---

