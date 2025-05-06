# Temple connect: Connecting Devotees and Temples Digitally

![Temple connect Logo](https://example.com/devconnect-logo.png)

## Table of Contents
1. [Introduction](#introduction)
    - [Purpose](#purpose)
    - [Scope](#scope)
    - [Intended Audience](#intended-audience)
    - [Definitions and Acronyms](#definitions-and-acronyms)
2. [Overall Description](#overall-description)
    - [Product Perspective](#product-perspective)
    - [Product Functions](#product-functions)
    - [User Classes and Characteristics](#user-classes-and-characteristics)
    - [Operating Environment](#operating-environment)
3. [Functional Requirements](#functional-requirements)
    - [User Module](#user-module)
    - [Temple Admin Module](#temple-admin-module)
    - [Super Admin Module](#super-admin-module)
    - [Additional Features](#additional-features)
4. [Non-Functional Requirements](#non-functional-requirements)
    - [Performance](#performance)
    - [Security](#security)
    - [Usability](#usability)
    - [Availability](#availability)
    - [Maintainability](#maintainability)
5. [System Architecture](#system-architecture)
    - [Backend](#backend)
    - [Frontend](#frontend)
    - [Integrations](#integrations)
6. [User Interface Mockups](#user-interface-mockups)
7. [Assumptions and Constraints](#assumptions-and-constraints)
8. [Appendices](#appendices)

## 1. Introduction

### 1.1. Purpose
This document defines the requirements for Temple connect, a digital platform designed to connect Hindu temples across India with devotees. The platform will enable devotees to:

- Book archanas, poojas, and nerchas online.
- Receive prasadam and official receipts delivered to their homes.
- Get real-time updates on temple events and festivals.
- Participate in religious services remotely, regardless of their location.

This initiative aims to make spiritual services more accessible, efficient, and transparent through the use of modern technology.

### 1.2. Scope
Temple connect will:

- Allow users to discover and book services at verified Hindu temples across India.
- Offer a web and mobile application for devotees and a dedicated admin panel for temple staff.
- Support prasadam delivery services and the generation of digital receipts.
- Integrate secure payment gateways and order tracking functionalities.
- Be designed to be scalable to accommodate a growing number of temples and users.

### 1.3. Intended Audience
This document is intended for the following stakeholders:

- ORAAK Technologies Development Team
- Project Stakeholders
- Temple Administration Boards
- Quality Assurance and Testing Teams
- Courier and Logistics Integration Teams

### 1.4. Definitions and Acronyms

| Term | Definition |
|------|------------|
| Archana | Devotional offering with the recitation of divine names. |
| Nercha | Special offering made, typically in fulfillment of vows or wishes. |
| Prasadam | Blessed food or item distributed after a pooja or ritual. |
| DRF | Django REST Framework |
| PWA | Progressive Web App |
| SaaS | Software as a Service |
| MVP | Minimum Viable Product |
| SSL | Secure Sockets Layer |
| CSRF | Cross-Site Request Forgery |
| GDPR | General Data Protection Regulation |
| IT Act | Information Technology Act (India) |
| UI | User Interface |
| API | Application Programming Interface |
| AWS | Amazon Web Services |
| GCP | Google Cloud Platform |
| OTP | One-Time Password |

## 2. Overall Description

### 2.1. Product Perspective
Temple connect will be implemented as a standalone Software as a Service (SaaS) application comprising three distinct interfaces:

- **User Interface**: A web application and a mobile application (developed using React and React Native, respectively) for devotees.
- **Temple Admin Panel**: A web portal designed for temple staff to manage their services and bookings.
- **Super Admin Panel**: A web portal for ORAAK Technologies staff to oversee the entire platform ecosystem.

### 2.2. Product Functions
The core functionalities of Temple connect include:

- User registration and profile management.
- Advanced search capabilities for temples and pooja services.
- Comprehensive booking management system with calendar integration.
- Secure online payment integration (e.g., Razorpay/UPI).
- Real-time status tracking for bookings and prasadam delivery.
- Automated generation and delivery of digital receipts (in PDF format and via email).
- Dedicated administrative tools for both temples and super administrators.

### 2.3. User Classes and Characteristics

| User Role | Description |
|-----------|-------------|
| Devotee (User) | Individuals who can browse temples, book services, make payments, and track their orders. |
| Temple Admin | Authorized personnel from temples who can manage their services, view and confirm bookings, and update pooja information. |
| Super Admin (ORAAK) | ORAAK Technologies staff responsible for managing the platform, approving temples, monitoring transactions, and handling system-level configurations. |

### 2.4. Operating Environment
The Temple connect platform will operate within the following environment:

- **Web Application**: Built using React.js for the frontend and a Django backend.
- **Mobile Application**: Developed using React Native for cross-platform compatibility (Android and iOS).
- **Hosting Infrastructure**: To be hosted on cloud platforms such as AWS or GCP for scalability and reliability.
- **Database**: PostgreSQL will be used as the primary database for storing application data.
- **Caching**: Redis will be implemented for efficient data caching to improve performance.
- **Background Tasks**: Celery will manage asynchronous tasks such as sending email notifications and processing order updates.

## 3. Functional Requirements

### 3.1. User Module

| FR | Description |
|----|-------------|
| FR1 | Users must be able to register and log in securely using either their email address or a mobile OTP (One-Time Password). |
| FR2 | Users should be able to search for temples based on various criteria, including location (state, city), deity, and popularity. |
| FR3 | For each temple, users must be able to view a detailed list of available pooja options, including their descriptions, prices, and available timings or dates. |
| FR4 | Users must be able to book their desired poojas or nerchas by selecting available dates and times as presented in a calendar interface. |
| FR5 | Upon successful payment for a booking, users must receive a digital receipt, which should be sent via email and also accessible within their account. |
| FR6 | For bookings that include prasadam delivery, users should be able to track the shipment status of their package. |
| FR7 | Users should be able to access a history of their previous bookings and download the corresponding receipts. |

### 3.2. Temple Admin Module

| FR | Description |
|----|-------------|
| FR8 | Temple administrators must be able to log in to their dedicated panel using secure credentials. |
| FR9 | Temple admins should have the ability to list the various types of poojas offered by their temple, along with their respective pricing and any capacity limitations. |
| FR10 | Temple admins should be able to view a list of all upcoming bookings, along with the devotee's details and the specifics of the service booked, and have the option to confirm these bookings. |
| FR11 | Once a pooja has been performed, temple admins must be able to mark it as completed and initiate the process for prasadam dispatch, if applicable. |
| FR12 | Temple admins should be able to generate and download official receipts for the services rendered. |

### 3.3. Super Admin Module

| FR | Description |
|----|-------------|
| FR13 | ORAAK Technologies staff should be able to review and either approve or reject applications from temples wishing to onboard onto the platform. |
| FR14 | Super admins should have a comprehensive view of all activities occurring on the platform, including user actions and temple operations. |
| FR15 | Super admins should be able to manage commission rates, handle any disputes or issues related to bookings or deliveries, and access platform-wide analytics and revenue reports. |
| FR16 | Super admins should have the capability to broadcast important announcements or updates to all users and/or temples. |

### 3.4. Additional Features

| FR | Description |
|----|-------------|
| FR17 | Users should be able to leave reviews and ratings for temples and services. |
| FR18 | Implement a feature for users to donate to temples. |
| FR19 | Provide a feature for users to request special poojas or services not listed. |
| FR20 | Enable users to set reminders for upcoming poojas or events. |

## 4. Non-Functional Requirements

### 4.1. Performance
The platform must be designed to support at least 10,000 concurrent users during the Minimum Viable Product (MVP) stage without significant performance degradation.

### 4.2. Security
- All communication between the client and server must be secured using SSL encryption.
- The platform must implement secure API authentication mechanisms to protect against unauthorized access.
- CSRF (Cross-Site Request Forgery) protection must be implemented to prevent malicious attacks.
- The platform must comply with relevant data privacy regulations, including GDPR for international users and the Indian IT Act for users within India.

### 4.3. Usability
- The user interface must support multiple languages, including English, Hindi, Tamil, Malayalam, and Telugu.
- The design of both the web and mobile applications should follow a mobile-first approach, ensuring a seamless experience on smaller screens.

### 4.4. Availability
The platform should aim for an availability of 99.5% uptime, with mechanisms in place for automatic restarts and load balancing to ensure continuous operation.

### 4.5. Maintainability
The system architecture should be modular to facilitate easy updates, debugging, and the addition of new features without affecting the stability of the existing system.

## 5. System Architecture

### 5.1. Backend
- **Framework**: Python Django with Django REST Framework (DRF) for building APIs.
- **Database**: PostgreSQL for persistent data storage.
- **Caching & Task Queue**: Redis for caching frequently accessed data and Celery for managing asynchronous background tasks.
- **Real-time Communication**: Django Channels for handling real-time updates, such as pooja status notifications.

### 5.2. Frontend
- **Web Application**: React.js for building a dynamic and responsive user interface.
- **Mobile Application**: React Native for developing cross-platform mobile apps (iOS and Android).
- **Styling**: Tailwind CSS for rapid and consistent styling across the frontend.

### 5.3. Integrations
- **Payment Gateway**: Integration with Razorpay or Paytm for secure online payment processing.
- **Delivery Service**: Integration with Shiprocket API or a similar service like Delhivery for managing prasadam delivery logistics.
- **Email Service**: AWS SES (Simple Email Service) for sending transactional emails, including booking confirmations and receipts.
- **Push Notifications**: Firebase Cloud Messaging (FCM) or AWS Pinpoint for delivering push notifications to users.

## 6. User Interface Mockups
(To be attached separately or built in Figma)

- Homepage with temple search functionality.
- Temple details page showcasing available poojas and services.
- Booking calendar and confirmation page.
- User dashboard displaying booking history and tracking information.
- Temple admin panel with booking management and service listing features.
- Super admin dashboard with key metrics and management tools.

## 7. Assumptions and Constraints
- All temples onboarding the platform must be registered entities with valid identification documents such as GST and PAN.
- The initial phase of prasadam delivery will be limited to locations within India.
- The feasibility of real-time live streaming of poojas will depend on the availability of necessary infrastructure at the respective temples.

## 8. Appendices
- Sample list of major temples to be onboarded initially.
- Example matrix detailing various pooja types and their associated pricing.
- Illustrative workflow of the prasadam delivery process.
- API documentation (to be created using Swagger or Postman).
