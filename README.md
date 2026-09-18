# NITS Telugu Network

### Distributed Event Management System for Telugu Students at NIT Silchar

**NITS Telugu Network** is a full-stack community platform built for the Telugu student community at **National Institute of Technology, Silchar (NIT Silchar)**.

The platform provides a centralized system for managing community events, registrations, movie ticket bookings, payment verification, notifications, and administrative operations.

🌐 **Live Website:** https://nitstelugu.in

---

## ✨ Features

### 👤 User Management

* User authentication and access control
* Student registration and profile details
* Mobile-friendly interface
* Community-focused event portal

### 🎉 Event Management

* Online event registration
* Event contribution/registration portals
* Registration tracking
* Automated booking ID generation
* Event-wise participant management

### 🎬 Movie Ticket Booking

* Telugu movie show booking system
* Student details collection
* Payment proof submission
* UTR / transaction ID submission
* Automated booking ID generation
* Booking status tracking
* Duplicate submission detection

### 💳 Payment Verification

* Payment screenshot upload
* OCR-based UTR detection using **Tesseract OCR**
* Payment verification workflow
* Admin approval/rejection system
* Cloud-based storage of payment proof screenshots using **Cloudinary**

### 🖼️ Cloud Image Storage

* Payment screenshots are uploaded to **Cloudinary**
* Cloud URLs are stored and associated with booking records
* Admin dashboard allows authorized administrators to view submitted payment proofs
* Eliminates the need to store large image files directly in the database

### 🔔 Notifications & Automation

* Telegram Bot notifications for new registrations/bookings
* Automated administrative alerts
* Google Sheets synchronization
* Backend automation workflows

### 🛠️ Admin Dashboard

* View submitted registrations
* Filter registrations by year and branch
* Review payment information
* View payment proof screenshots
* Approve or reject payments
* Track booking IDs and transaction details
* Registration and payment analytics
* Real-time data updates
* Export and synchronization workflows

---

## 🏗️ System Architecture

```text
                         ┌─────────────────────┐
                         │       Users         │
                         │  Students / Admins   │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │   NITS Telugu Web   │
                         │   HTML/CSS/JS UI    │
                         └──────────┬──────────┘
                                    │
                   ┌────────────────┼────────────────┐
                   │                │                │
                   ▼                ▼                ▼
            ┌─────────────┐  ┌─────────────┐  ┌─────────────┐
            │  Firebase   │  │ Cloudinary  │  │ Google      │
            │  Firestore  │  │   Storage   │  │   Sheets    │
            └──────┬──────┘  └─────────────┘  └─────────────┘
                   │
                   ▼
            ┌─────────────┐
            │   Admin     │
            │  Dashboard  │
            └──────┬──────┘
                   │
          ┌────────┴────────┐
          ▼                 ▼
   ┌─────────────┐   ┌─────────────┐
   │ Tesseract   │   │ Telegram    │
   │    OCR      │   │     Bot     │
   └─────────────┘   └─────────────┘
```

---

## 🔄 Movie Booking Workflow

```text
Student
   │
   ▼
Enter Details
   │
   ▼
Select Movie / Show
   │
   ▼
Make Payment
   │
   ▼
Upload Payment Screenshot
   │
   ▼
Cloudinary Image Upload
   │
   ▼
OCR / UTR Detection
   │
   ▼
Firestore Booking Record
   │
   ├──────────────► Google Sheets
   │
   └──────────────► Telegram Notification
                         │
                         ▼
                   Admin Dashboard
                         │
                  ┌──────┴──────┐
                  ▼             ▼
                Approve       Reject
                  │
                  ▼
             Booking Status
```

---

## 🧩 Core Modules

| Module               | Description                                     |
| -------------------- | ----------------------------------------------- |
| Authentication       | User authentication and access management       |
| Event Management     | Event registration and contribution workflows   |
| Movie Booking        | Movie show registration and ticket booking      |
| Payment Verification | UTR and payment proof verification              |
| OCR                  | Automatic extraction of transaction information |
| Cloud Storage        | Payment proof image storage using Cloudinary    |
| Admin Dashboard      | Registration and payment management             |
| Notifications        | Telegram Bot-based administrative alerts        |
| Data Sync            | Google Sheets integration                       |
| Database             | Firebase Firestore                              |

---

## 🛠️ Technologies & Tools

### Frontend

* HTML5
* CSS3
* JavaScript
* Responsive Web Design

### Backend & Database

* Firebase
* Firebase Firestore
* Cloudinary
* Google Sheets API

### Automation & APIs

* Telegram Bot API
* Google Apps Script
* REST APIs

### OCR

* Tesseract.js

### Deployment

* GitHub
* Web Hosting / Custom Domain

---

## ☁️ Cloudinary Integration

Payment proof screenshots are stored using **Cloudinary** rather than storing image files directly inside Firestore.

### Upload Flow

```text
User Upload
     │
     ▼
Frontend
     │
     ▼
Cloudinary
     │
     ▼
Secure Image URL
     │
     ▼
Firestore Booking Record
     │
     ▼
Admin Dashboard
```

This architecture keeps the database lightweight while allowing administrators to access payment proof images when reviewing bookings.

---

## 🔥 Firebase Integration

Firebase Firestore is used as the primary database for managing:

* Student information
* Event registrations
* Movie bookings
* Booking IDs
* UTR / transaction details
* Payment status
* Cloudinary image URLs
* Administrative records

Real-time database capabilities allow the admin dashboard to reflect booking updates without requiring manual page refreshes.

---

## 🤖 Telegram Bot Automation

The Telegram Bot integration is used to send administrative notifications when important events occur, such as:

* New registration
* New movie booking
* Payment submission
* Booking status updates

This helps administrators monitor activity without continuously checking the dashboard.

---

## 📊 Google Sheets Integration

Google Sheets is integrated for data synchronization and administrative record management.

Typical booking information includes:

```text
Timestamp
Name
Mobile
Year
Branch
UTR
Booking ID
Payment Status
```

This provides an additional accessible record for event organizers.

---

## 🔍 OCR-Based Payment Verification

**Tesseract.js** is used to process uploaded payment screenshots and identify transaction-related information.

The OCR workflow:

```text
Payment Screenshot
       │
       ▼
    Tesseract OCR
       │
       ▼
Extract Text
       │
       ▼
Identify UTR / Transaction ID
       │
       ▼
Compare / Verify
       │
       ▼
Admin Review
```

OCR assists administrators by reducing the amount of manual data entry required during payment verification.

---

## 🔐 Security Considerations

The platform follows several practices to reduce exposure of sensitive information:

* Firebase security rules for database access
* Restricted administrative operations
* No sensitive API credentials committed to the public repository
* Cloud-based image storage
* Validation of submitted booking information
* Duplicate booking / UTR detection

> **Important:** Never commit Firebase private credentials, Cloudinary API secrets, Telegram Bot tokens, or other sensitive configuration values to GitHub.

---

## 📱 Responsive Design

The platform is designed to work across:

* 📱 Mobile devices
* 💻 Laptops
* 🖥️ Desktop screens
* 📟 Tablets

The interface focuses on simple navigation and easy access to event and booking functionality.

---

## 📈 Future Improvements

Potential improvements include:

* Online ticket QR generation
* Automated payment reconciliation
* Advanced booking analytics
* Role-based admin permissions
* Automated email notifications
* Event-specific dashboards
* Digital ticket generation
* Improved fraud/duplicate detection
* Progressive Web App (PWA) support

---

## 👨‍💻 Developer

**Bukke Naveen Kumar Naik**

Computer Science & Engineering
National Institute of Technology, Silchar

* GitHub: `NaveenKumar8824`
* LinkedIn: `bukkenaveenkumarnaik`

---

## 📄 Project Information

**Project:** NITS Telugu Network
**Type:** Community & Event Management Platform
**Domain:** `nitstelugu.in`
**Primary Users:** Telugu Student Community at NIT Silchar
**Status:** Deployed & Actively Developed

---

## ⭐ Support

If you find this project interesting, consider giving the repository a ⭐ on GitHub.

**Built with ❤️ for the Telugu student community at NIT Silchar.**
