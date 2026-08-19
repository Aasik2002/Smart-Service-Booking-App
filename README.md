# 🛠️ Smart Location-Based Service Booking Platform

A full-stack mobile application that acts as an "Uber for local services." This platform connects customers with nearby professionals (plumbers, electricians, carpenters, etc.) in real-time using GPS coordinates and spatial database querying.

Built by the **NexDigital** Team.

## ✨ Key Features
* **Real-Time Geospatial Search:** Finds providers within a specific radius using PostGIS `ST_DWithin`.
* **Live GPS Tracking:** Integrates Google Maps API to pinpoint customer and provider locations.
* **Secure Authentication:** JWT-based stateless authentication with BCrypt password hashing.
* **Instant Notifications:** Firebase Cloud Messaging (FCM) for real-time booking alerts.
* **End-to-End Booking Flow:** Complete lifecycle from pending request to job completion and reviews.

## 💻 Tech Stack
**Frontend (Mobile):**
* Kotlin
* Jetpack Compose (Modern UI)
* Retrofit & OkHttp (Network/API Calls)
* Google Maps SDK for Android

**Backend (Server):**
* Java 17+
* Spring Boot 3.x (Spring Web, Spring Security, Spring Data JPA)
* PostgreSQL
* PostGIS Extension (For spatial data & geography coordinates)
* Firebase Admin SDK (For push notifications)

## 👥 Team Structure (Vertical Slicing)
This project is built using a vertical full-stack ownership model:
1. **Dev 1 (Identity & Auth):** Users table, Spring Security, JWT, Login/Signup Mobile UI.
2. **Dev 2 (Geospatial Core):** Providers table, PostGIS queries, Google Maps integration, Location tracking.
3. **Dev 3 (Booking System):** Bookings table, Booking APIs, Customer Dashboard UI, Date/Time pickers.
4. **Dev 4 (Provider Engine):** Accept/Reject APIs, Provider Dashboard UI, Firebase Push Notifications.
5. **Dev 5 / Tech Lead (Reviews & DevOps):** Reviews table, Rating calculations, UI integration, Code Review & PR Merging.

## 🌿 Git Workflow & Branching Strategy
We follow a strict Git workflow to prevent merge conflicts.
* `main` - Stable, production-ready code ONLY.
* `develop` - Active integration branch. All completed features are merged here.
* `feature/<feature-name>` - Dedicated branches for individual tasks (e.g., `feature/login-api`).

**Daily Routine:**
1. `git checkout develop`
2. `git pull origin develop`
3. `git checkout -b feature/your-task`
4. Code, commit, and push.
5. **Open a Pull Request (PR)** to merge into `develop`. (Requires Tech Lead approval).

## 🚀 Setup Instructions

### 1. Prerequisites
* Android Studio (Latest Version)
* IntelliJ IDEA or Eclipse
* PostgreSQL installed locally with the **PostGIS** extension enabled.
* Git

### 2. Backend Setup (Spring Boot)
1. Open the `backend-server` folder in IntelliJ.
2. Create a local PostgreSQL database named `service_booking_db`.
3. Enable PostGIS on your database by running: `CREATE EXTENSION postgis;`
4. Navigate to `src/main/resources/application.properties.example`, rename it to `application.properties`, and add your local database credentials:
   ```properties
   spring.datasource.url=jdbc:postgresql://localhost:5432/service_booking_db
   spring.datasource.username=YOUR_DB_USERNAME
   spring.datasource.password=YOUR_DB_PASSWORD
