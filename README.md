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

## Android extras (after `npx cap add android`)
1. `android/app/src/main/AndroidManifest.xml`: add `<uses-permission android:name="android.permission.USE_BIOMETRIC" />` and set `android:allowBackup="false"` on the `<application>` tag.
2. Hide Sika from screenshots and the recent-apps preview: in `MainActivity.java`, inside `onCreate`, add `getWindow().setFlags(android.view.WindowManager.LayoutParams.FLAG_SECURE, android.view.WindowManager.LayoutParams.FLAG_SECURE);`
3. App icon: replace the launcher icons in `android/app/src/main/res/mipmap-*` (Android Studio: right-click `res` > New > Image Asset).
4. Release build: Build > Generate Signed Bundle (AAB). Keep the signing key safe, since losing it means you cannot update the app.
