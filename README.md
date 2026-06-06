# DataLake 3.0 Mobile Application
<p align="left">
  <a href="https://drive.google.com/file/d/1aYJAAE1fx-hoFzDOY3aqnBmSN3KOCayo/view?usp=sharing">
    <img src="https://img.shields.io/badge/Watch-Demo%20Video-blue?style=for-the-badge" alt="Demo Video"/>
  </a>
  <a href="./docs/DataLake%203.0%20Guide.pdf">
    <img src="https://img.shields.io/badge/Docs-Integration%20Guide-green?style=for-the-badge" alt="Integration Guide"/>
  </a>
</p>
<p align="left">
  <img src="docs/demo.gif" width="800"/>
</p>

## Overview

DataLake 3.0 is an Offline-First AI-powered attendance management application built using React Native and Expo.

Unlike traditional attendance systems that depend on continuous internet connectivity, DataLake 3.0 allows users to securely mark attendance even in offline environments. Attendance data is stored locally using SQLite and automatically synchronized with AWS cloud infrastructure once connectivity becomes available.

The application integrates multiple AI verification stages including head movement verification, blink detection, and face recognition to ensure secure attendance marking and prevent spoofing attempts.

---

## Key Features

### Offline-First Attendance

* Attendance works without internet
* Local SQLite storage
* Sync queue management
* Automatic cloud synchronization

### AI-Based Verification

* Head Movement Verification
* Blink Detection
* Face Recognition
* Multi-step Liveness Validation

### Smart Synchronization

* Network Awareness
* Retry Mechanism
* Background Sync Queue
* Conflict Prevention

### User Features

* Attendance History
* Weekly Summary
* Project Tracking
* Profile Management
* Location Capture

---

## Technology Stack

| Layer                   | Technology         |
| ----------------------- | ------------------ |
| Mobile Framework        | React Native       |
| Runtime                 | Expo SDK 54        |
| Language                | TypeScript         |
| Routing                 | Expo Router        |
| State Management        | Zustand            |
| Local Database          | Expo SQLite        |
| Local Storage           | AsyncStorage       |
| Networking              | Axios              |
| Connectivity Monitoring | NetInfo            |
| Camera                  | Expo Camera        |
| Face Detection          | Expo Face Detector |
| Cloud Integration       | AWS API Gateway    |
| Cloud Backend           | AWS Lambda         |
| Cloud Database          | DynamoDB           |

---

## System Workflow

```text
User Opens App
        │
        ▼
Attendance Screen
        │
        ▼
Camera Verification
        │
        ▼
Head Movement Verification
        │
        ▼
Blink Detection
        │
        ▼
Face Recognition
        │
        ▼
Attendance Marked
        │
        ▼
Store in SQLite
        │
        ▼
Network Available?
    ┌───┴───┐
    ▼       ▼
  Yes       No
    │        │
    ▼        ▼
AWS Sync  Keep Local
```

---

## Project Structure

```text
app/
├── (auth)
├── (tabs)
├── attendance.tsx
├── attendance-camera.tsx
└── profile.tsx

components/
├── blinkEyes.tsx
├── headMovement.tsx
├── faceRecognition.tsx
├── syncStatus.tsx
└── attendanceCard.tsx

services/
├── mlApi.ts
├── awsSync.ts
└── config.ts

store/
├── attendanceStore.ts
└── projectStore.ts
```

---

## Installation

### Prerequisites

* Node.js 20.x
* npm 10.x
* Expo CLI

### Install

```bash
npm install
```

### Start

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

## Cloud Synchronization

Attendance records are stored locally first.

When connectivity becomes available:

1. Pending records are fetched from SQLite
2. Records are sent to AWS API Gateway
3. Lambda validates requests
4. Data is stored in DynamoDB
5. Local records are marked as synced

---

## Why Offline-First?

Field employees often work in low-connectivity areas.

DataLake 3.0 guarantees:

* No attendance loss
* Reliable data collection
* Automatic synchronization
* Improved user experience
* Reduced dependency on internet connectivity
