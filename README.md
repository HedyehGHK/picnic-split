# 🧺 Picnic Split

A lightweight, real-time bill-splitting web app built for three friends — no accounts, no app install, just open the link and start adding items.

![Picnic Split preview](https://picnic-split.vercel.app)

## ✨ Features

- **Real-time sync** — all three friends see changes instantly via Firebase Firestore
- **Auto-save** — data saves automatically as you type
- **Smart settlement** — calculates the minimum number of transfers needed to settle up
- **No login required** — just share the link
- **Mobile friendly** — works on any device

## 🛠 Tech Stack

- Plain HTML, CSS, JavaScript (no framework)
- [Firebase Firestore](https://firebase.google.com/docs/firestore) for real-time data sync
- Deployed on [Vercel](https://vercel.com)

## 🚀 Deploy Your Own

### 1. Clone the repo

```bash
git clone https://github.com/YOUR_USERNAME/picnic-split.git
cd picnic-split
```

### 2. Create a Firebase project

1. Go to [console.firebase.google.com](https://console.firebase.google.com)
2. Create a new project
3. Go to **Firestore Database** → **Create database** → Start in **test mode**
4. Go to **Project Settings** → **Your apps** → click `</>` → register a web app
5. Copy your `firebaseConfig` object

### 3. Add your Firebase config

In `index.html`, find this section and replace with your own config:

```js
const firebaseConfig = {
  apiKey: "...",
  authDomain: "...",
  projectId: "...",
  storageBucket: "...",
  messagingSenderId: "...",
  appId: "..."
};
```

### 4. Set Firestore Rules

In Firebase Console → **Firestore Database** → **Rules**, paste:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if true;
    }
  }
}
```

Click **Publish**.

### 5. Deploy to Vercel

Connect your GitHub repo to [Vercel](https://vercel.com) and deploy with one click. No build step needed.

## 💡 How It Works

Each person opens the same URL, enters their purchases, and the app:

1. Saves everything to a shared Firestore document in real time
2. Calculates each person's fair share (total ÷ 3)
3. Shows the minimum payments needed to settle up

## 📁 Project Structure

```
picnic-split/
├── index.html      # entire app (HTML + CSS + JS)
├── vercel.json     # Vercel routing config
└── README.md
```
