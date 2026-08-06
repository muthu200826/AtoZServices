# Paramesh Bridal Studio — Website

A complete, mobile-responsive bridal studio website: public site, customer
dashboard, and admin panel, built with plain HTML/CSS/JS and Firebase.

## What's inside

```
index.html          Home (hero, about, services)
contact.html         Contact page + map
enquiry.html          Enquiry form → opens WhatsApp with a pre-filled message
book.html             Booking form → saves to Firestore/Firebase
dashboard.html        Customer dashboard: search services, view reviews, track booking status
admin-login.html       Admin sign-in
admin.html             Admin panel: services / reviews / orders management + stats
css/styles.css         Design system (colors, type, components)
js/firebase-config.js  ⭐ Put your Firebase project keys here
js/data.js              Data layer (Firestore in production, demo data if unconfigured)
js/nav.js                Shared header/footer/dark mode/floating buttons
js/main.js, enquiry.js, book.js, dashboard.js, admin.js, admin-auth.js
```

## Try it instantly (no setup)

Open `index.html` in a browser (or serve the folder with any static
server). Because `js/firebase-config.js` still has placeholder keys, the
site runs in **demo mode** automatically — a small in-memory dataset powers
services, reviews and bookings so you can click through the entire site,
including the admin panel.

Demo admin login: `admin@parameshbridalstudio.com` / `admin123`

Demo mode data resets on page refresh — connect Firebase (below) to persist
real bookings, services and reviews.

## Connect Firebase (for the real site)

1. Create a project at https://console.firebase.google.com
2. **Build → Firestore Database** → Create database (start in production mode).
3. **Build → Authentication** → Sign-in method → enable **Email/Password**,
   then add yourself as a user under the **Users** tab — this becomes your
   admin login.
4. **Build → Storage** → Get started (only needed if you extend the admin
   panel to upload real service photos instead of emoji icons).
5. **Project settings → General → Your apps** → add a Web app → copy the
   `firebaseConfig` object into `js/firebase-config.js`, replacing every
   `"REPLACE_ME"`.
6. Reload the site — the demo banner disappears and every page now reads
   and writes real Firestore data.

### Firestore security rules (starting point)

Paste into **Firestore → Rules**, then adjust as needed:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {

    match /services/{id} {
      allow read: if true;
      allow write: if request.auth != null;
    }

    match /reviews/{id} {
      allow read: if true;
      allow write: if request.auth != null;
    }

    match /orders/{id} {
      allow read: if request.auth != null;
      allow create: if true;          // customers can submit bookings
      allow update, delete: if request.auth != null;  // admin only
    }
  }
}
```

This lets any visitor read services/reviews and create a booking, but only
a signed-in admin (your Firebase Auth user) can add/edit/delete services,
reviews, or manage orders.

## Customize

- **Branding**: studio name, phone, WhatsApp number, email, address and map
  link all live in the `window.STUDIO` object at the bottom of
  `js/firebase-config.js`.
- **Colors/fonts**: CSS variables at the top of `css/styles.css`
  (`--maroon-800`, `--gold-500`, etc).
- **Seed services**: edit the `demo.services` array in `js/data.js` — once
  Firebase is connected, use the Admin Panel's "Add Service" instead.

## Deploy

Any static host works (Firebase Hosting, Netlify, Vercel, GitHub Pages).
For Firebase Hosting:

```
npm install -g firebase-tools
firebase login
firebase init hosting     # choose this folder as the public directory
firebase deploy
```
