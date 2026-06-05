# DataLake 3.0

## Overview

DataLake 3.0 is an Offline-First AI-powered attendance management application built using React Native and Expo. The application enables employees or field workers to mark attendance through a multi-stage AI verification process consisting of face recognition, blink detection, and head movement verification.

The system is designed to function even in low-connectivity environments by storing attendance records locally using SQLite and synchronizing them automatically when internet connectivity becomes available.

---

## Features

### AI-Based Attendance Verification

* Face Recognition
* Blink Detection (Liveness Check)
* Head Movement Verification
* Multi-Step Authentication Flow

### Offline-First Architecture

* Local SQLite Database
* Offline Attendance Recording
* Automatic Sync Queue
* Network Aware Synchronization

### Attendance Management

* Check-In / Check-Out
* Weekly Attendance Summary
* Attendance History
* Project-Based Attendance Tracking

### User Features

* OTP Authentication
* Profile Management
* Location Capture
* Sync Status Monitoring

---

## Tech Stack

| Layer                   | Technology         |
| ----------------------- | ------------------ |
| Mobile Framework        | React Native       |
| Framework Runtime       | Expo SDK 54        |
| Language                | TypeScript         |
| Routing                 | Expo Router        |
| State Management        | Zustand            |
| Database                | Expo SQLite        |
| Storage                 | AsyncStorage       |
| Networking              | Axios              |
| Connectivity Monitoring | NetInfo            |
| Camera                  | Expo Camera        |
| Face Detection          | Expo Face Detector |

---

## Project Structure

```text
app/
├── (auth)
│   ├── index.tsx
│   └── verify-otp.tsx
│
├── attendance.tsx
├── attendance-camera.tsx
├── profile.tsx
│
├── (tabs)
│   ├── index.tsx
│   ├── projects.tsx
│   └── sync.tsx
│
components/
├── blinkEyes.tsx
├── headMovement.tsx
├── faceRecognition.tsx
├── attendanceCard.tsx
├── syncStatus.tsx
└── weeklySummary.tsx
│
services/
├── mlApi.ts
├── awsSync.ts
└── config.ts
│
store/
├── attendanceStore.ts
└── projectStore.ts
│
lib/
└── db.ts
```

---

## Local Database Schema

The application uses SQLite for offline storage.

### attendance_records

Stores daily attendance data.

### projects

Stores assigned project information.

### sync_queue

Tracks pending synchronization requests.

### user_session

Stores local user session data.

---

## Attendance Flow

```text
User Opens App
        ↓
Attendance Screen
        ↓
Camera Opens
        ↓
Blink Verification
        ↓
Head Movement Verification
        ↓
Face Recognition
        ↓
Attendance Marked
        ↓
Stored in SQLite
        ↓
Network Available?
      /      \
    Yes       No
     ↓         ↓
 Sync AWS   Store Offline
```

---

## Installation

### Prerequisites

* Node.js 20+
* npm 10+
* Expo CLI

### Install Dependencies

```bash
npm install
```

### Start Development Server

```bash
npx expo start
```

### Android

```bash
npm run android
```

### iOS

```bash
npm run ios
```

---

## Environment Configuration

Create a `.env` file:

```env
BASE_URL=http://YOUR_FASTAPI_SERVER:8000
```

---

## Sync Mechanism

Attendance records are stored locally first.

When connectivity becomes available:

1. Pending records are fetched from SQLite
2. Records are sent to AWS backend
3. Records are marked as synced
4. Sync status is updated locally

---

## Future Improvements

* Background Sync Service
* Push Notifications
* AWS Cognito Authentication
* Real-Time Dashboard
* Admin Panel

---

## License

MIT License

