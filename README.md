📌 Field Attendance Tracker

A lightweight web app for check-in/check-out with real-time location logging.

🚀 Overview

The Field Attendance Tracker is a simple, fast, and mobile-friendly web application designed to record employee or field-worker attendance using:

Real-time geolocation

Cloud Firestore database

Anonymous Firebase Authentication

Modern Tailwind-based UI

Fully responsive design

Hosted for free on Netlify

Users can check in and check out, with each event storing the timestamp, latitude, longitude, and position accuracy directly in the cloud.

This project demonstrates full-stack skills using a serverless architecture — perfect for lightweight, real-world attendance tracking systems.

✨ Features
✔ Check-In / Check-Out System

Records timestamped attendance events with one click.

✔ Real-time Geolocation

Automatically captures:

Latitude

Longitude

Accuracy

using the browser’s Geolocation API.

✔ Firebase Authentication

Uses anonymous sign-in so each device/user gets a unique, secure user ID.

✔ Cloud Firestore Storage

Attendance is saved under:

artifacts/{appId}/users/{userId}/attendance/{doc}


with automatic real-time listeners.

✔ Fully Responsive UI

Built with TailwindCSS and optimized for mobile usage.

✔ Real-time History View

Attendance updates instantly as entries are added.

✔ Hosted on Netlify

Completely free hosting with HTTPS.

🛠️ Tech Stack
Layer	Tech
Frontend	HTML, CSS, TailwindCSS, Vanilla JavaScript
Authentication	Firebase Auth (Anonymous Sign-In)
Database	Firebase Cloud Firestore
Hosting	Netlify
Geolocation	Browser Geolocation API
📂 Project Structure
index.html        → Main UI + Firebase logic
assets/           → (Optional assets, icons, etc.)
README.md         → Project documentation


All logic is handled inside index.html using ES module imports.

🔧 Setup & Installation

If you want to run or modify this project locally:

1. Clone the repository
git clone https://github.com/<your-user>/<your-repo>.git
cd <your-repo>

2. Configure Firebase

Create a new Firebase project and copy your config:

const firebaseConfig = {
  apiKey: "...",
  authDomain: "...",
  projectId: "...",
  storageBucket: "...",
  messagingSenderId: "...",
  appId: "...",
};


Make sure to enable:

Anonymous Authentication

Firestore Database

3. Set Firestore Rules
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {

    match /artifacts/{appId}/users/{userId}/attendance/{docId} {
      allow read, write: if request.auth != null
                         && request.auth.uid == userId;
    }

  }
}

4. Open the file locally

Just open:

index.html

in any modern browser.

🌐 Deployment

The site is deployed using Netlify:

Create a new site → Deploy manually

Drag-and-drop the folder containing index.html

Netlify assigns an HTTPS domain instantly

Alternatively, you can use Firebase Hosting:

firebase init hosting
firebase deploy

📄 License

This project is open for educational and personal use.
You may modify or reuse it with credit.
