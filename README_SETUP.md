# PulseFit — Firebase backend setup

This version keeps the existing PulseFit design and connects sign-up/login, activity records, and daily goals to Firebase Authentication + Cloud Firestore.

## Important
- This web version signs in with **email + password**. Firebase phone sign-in needs a separate phone/SMS OTP setup, so the original “email or phone” field is now email-only.
- Do not publish your Firebase service-account key in browser code. This project only uses the Firebase web app config, which is designed to be included in client apps.
- Use HTTPS or a local web server to test. ES module imports may not work if you open the HTML as a `file://` page.

## Setup (Android-friendly)
1. Open https://console.firebase.google.com/ and create a Firebase project.
2. In the project, open **Build → Authentication → Get started → Sign-in method** and enable **Email/Password**.
3. Open **Project settings → General → Your apps**. Add a **Web app** (`</>` icon) if you have not already.
4. Copy the web app config values into the `firebaseConfig` object near the top of `index.html`. Replace every `PASTE_..._HERE` value. Do not change the quote marks or commas.
5. Open **Build → Firestore Database → Create database**. Create the database.
6. Open Firestore **Rules**, replace the rules with the contents of `firestore.rules`, and publish them.
7. Upload `index.html` to a static hosting service that serves HTTPS (for example Firebase Hosting or another static host). Do not just open it as a local file. You can also test it using a local development server.
8. Open the hosted page, create an account using an email address and password of at least 6 characters, then log in.

## Database structure
- `users/{Firebase UID}/records/{record ID}` — each activity's type, name, date, duration, calories, steps, notes, and creation time.
- `users/{Firebase UID}/settings/goals` — the user's daily step and workout-minute goals.

The security rules restrict each signed-in user to their own `users/{UID}/...` data. Never use public “allow read, write: if true” rules for a real app.

## Test checklist
- Create account and log in.
- Add an activity; refresh the page; check that the record remains.
- Change daily goals; refresh; check that goals remain.
- Delete an activity and confirm it disappears after refresh.
- Log out, then log in again.

## Troubleshooting
- `auth/operation-not-allowed`: enable Email/Password in Authentication.
- “Could not load your cloud data”: confirm Firestore is created, rules are published, and the config's project ID is correct.
- Firebase errors in browser: check the config values and that the page is served over HTTPS.
