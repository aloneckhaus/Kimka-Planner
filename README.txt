
Weekly Planner – Alon & Kim (PWA + Realtime Sync)

1) Edit Firebase config:
   - Open config.js and fill in your Firebase Web App keys (apiKey, authDomain, projectId, appId).
   - Optional: change HOUSEHOLD_ID (both of you should use the same value).

2) Enable Firebase services (free tier is enough):
   - Firestore: start in production mode.
   - Authentication: enable Anonymous sign-in.

3) Deploy (pick one):
   - Netlify: drag the folder; set Deploy settings → Publish directory = the folder root.
   - Vercel: import the folder as a static project.
   - GitHub Pages: push & enable Pages; use the root as the site.
   - Or just open index.html locally (sync requires https in browsers for service worker; Firebase still works).

4) Install as an app (PWA):
   - Open the deployed URL on desktop or mobile.
   - “Install app” / “Add to Home Screen”.
   - Works offline; syncs automatically when back online.

5) Share:
   - Send the link to Kim.
   - Make sure both of you use the same HOUSEHOLD_ID (in the blue banner or in config.js).
   - All changes sync in real time.

Security tip (optional Firestore rules snippet):
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /plans/{household} {
      allow read, write: if true; // dev/demo
      // For private access, use auth.uid checks or a shared secret doc.
    }
  }
}
