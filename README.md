# Sika setup

## 1. Firebase (10 minutes, free plan is enough)
1. console.firebase.google.com > Add project.
2. Build > Authentication > Get started > turn on **Email/Password**.
3. Build > Firestore Database > Create (production mode), then open Rules and paste `firestore.rules`.
4. Project settings > Your apps > Web (</>) > copy the config into `public/firebase-config.js`.

## 2. Vercel
Push this folder to GitHub, import it in Vercel, deploy. No settings needed (`vercel.json` handles it).
Open the link on your phone and choose "Add to Home screen" to install it.

## 3. Android app (optional, same code)
```
npm install
npx cap add android
npx cap sync
npx cap open android
```
In Android Studio: Build > Build APK.

## Moving your test data
Old preview: Settings > Create backup. New app: log in, set a PIN, Settings > Restore, unlock with the same PIN.

## Good to know
- Cloud holds only locked text. Your PIN never leaves the phone, so a forgotten PIN cannot be recovered by anyone.
- Changing the PIN on one device means the others need the new PIN after their next sync.
