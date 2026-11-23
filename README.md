# Splitfare

Split trip costs with friends. Start a trip, share its six-character code (or invite link), and everyone logs what they paid. Splitfare keeps running balances and shows the fewest payments needed to settle up.

It's a single static page (`index.html`), so it runs on GitHub Pages or any web host. Trips are stored in a free Firebase Firestore database, and everyone sees changes live.

## Features

- Create a trip with a name, currency and the people going. You get a code like `K7MQ2P`.
- Join with the code, or open an invite link (`…/#trip-K7MQ2P`).
- Add expenses split equally, by exact amounts, or by shares (for example, a couple counts as 2).
- Balances per person, plus a settle-up plan with the fewest payments.
- Record payments with "Mark paid", and copy a summary for your group chat.
- "I'm ___" picker that shows what you owe or are owed.
- Light and dark themes. Works on phones.

## Setup (about 10 minutes, free)

### 1. Create the database

1. Go to <https://console.firebase.google.com> and click **Create a project** (Google Analytics is optional; you can turn it off).
2. In the left menu, open **Build → Firestore Database → Create database**. Pick a region near you and start in **production mode**.
3. Open the **Rules** tab, replace everything with the contents of [`firestore.rules`](firestore.rules), and click **Publish**.
4. Open **Project settings** (gear icon) → **Your apps** → the **Web** (`</>`) button. Register an app (no hosting needed) and copy the `firebaseConfig` object.
5. Paste it into [`firebase-config.js`](firebase-config.js):

   ```js
   window.SPLITFARE_FIREBASE = {
     apiKey: "AIza...",
     authDomain: "your-project.firebaseapp.com",
     projectId: "your-project",
     appId: "1:1234567890:web:abc123"
   };
   ```

   Committing these values is fine. They identify your project but don't grant access; `firestore.rules` controls that.

### 2. Publish with GitHub Pages

1. Commit and push `firebase-config.js`.
2. On GitHub, open the repo → **Settings → Pages**. Under **Build and deployment**, choose **Deploy from a branch**, branch `main`, folder `/ (root)`, and save.
3. After a minute the site is live at `https://<your-username>.github.io/Splitfare/`. Share that link, or a trip's invite link, with friends.

### Device-only mode

If `firebase-config.js` is left as `null`, Splitfare still works but saves trips only in the current browser. A banner at the top shows when this is the case.

## Run locally

Open `index.html` in a browser, or serve the folder:

```
python -m http.server 8000
```

Then visit <http://localhost:8000>.

## Privacy and limits

- Anyone with a trip's code can view and edit that trip. There are no accounts or passwords, so share codes only with your group.
- Trips can't be listed or browsed. Someone needs the code to find one.
- Firebase's free Spark plan allows 50,000 reads and 20,000 writes per day, which is plenty for group trips.
