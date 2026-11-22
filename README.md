# Pocketboard setup (no Android Studio needed)

1. console.firebase.google.com > Add project > Build > Firestore Database > Create (production mode).
2. Project settings > Your apps > Web (</>) > copy the config into `index.html` (firebaseConfig).
3. Firestore > Rules, paste, then Publish:

   rules_version = '2';
   service cloud.firestore {
     match /databases/{db}/documents {
       match /rooms/{room}/items/{item} {
         allow read, write: if true;
       }
     }
   }
   (Anyone who knows a room code can read it. Keep codes long and never store secrets.)

4. Host the folder: `npm i -g firebase-tools && firebase login && firebase init hosting && firebase deploy`
   (public dir = this folder, single-page app = No). You get https://YOUR_PROJECT.web.app

5. Phone: open the URL in Chrome. An Install banner appears in the app; tapping it adds Pocketboard to the app drawer with its icon (iPhone: Share > Add to Home Screen).
   On Android, "Pocketboard" then appears in the system Share sheet.
6. Use the same room code on every device (tap Room).
