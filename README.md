# PulseFit — Fitness Tracker App

A responsive fitness tracker web app built with HTML, CSS, and JavaScript. This repository contains the Firebase-enabled version.

## Features
- Email/password sign-up and login using Firebase Authentication
- Daily dashboard for steps, calories, workout minutes, and activity count
- Manual workout/activity logging and history
- Daily goals stored in Cloud Firestore
- User-specific cloud records protected by Firestore Security Rules
- Responsive interface for mobile and desktop

## Setup
1. Read [README_SETUP.md](README_SETUP.md) and create a Firebase project.
2. Enable Email/Password under Firebase Authentication.
3. Create a Cloud Firestore database.
4. Replace the `PASTE_..._HERE` placeholders in `index.html` with your Firebase web app configuration.
5. Publish the rules in `firestore.rules` from Firebase Console → Firestore Database → Rules.
6. Serve `index.html` using HTTPS or a local web server; ES modules may not work when opened directly as a `file://` file.

## Important
- This repository is not ready for live use until Firebase configuration and security rules are set up and tested.
- Never commit Firebase service-account private keys, passwords, or other secrets.
- Firebase web app configuration is intended for client-side use; security must be enforced with Authentication and Firestore Security Rules.
- Phone OTP authentication is not configured; this version uses email/password.

## Files
- `index.html` — app interface and JavaScript
- `firestore.rules` — per-user database access rules
- `README_SETUP.md` — Android-friendly Firebase setup and test checklist
