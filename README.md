# Splitfare

Split trip costs with friends. Start a trip, share its six-character code (or invite link), and everyone logs what they paid. Splitfare keeps running balances and shows the fewest payments needed to settle up.

It's a single static page (`index.html`), so it runs on GitHub Pages or any web host. Trips are stored in a free Firebase Firestore database, and everyone sees changes live.

Go to app at : https://harsha-gouda.github.io/Splitfare/

## Features

- Create a trip with a name, currency and the people going. You get a code like `K7MQ2P`.
- Join with the code, or open an invite link (`…/#trip-K7MQ2P`).
- Add expenses split equally, by exact amounts, or by shares (for example, a couple counts as 2).
- Balances per person, plus a settle-up plan with the fewest payments.
- Record payments with "Mark paid", and copy a summary for your group chat.
- "I'm ___" picker that shows what you owe or are owed.
- Light and dark themes. Works on phones.

## Privacy and limits

- Anyone with a trip's code can view and edit that trip. There are no accounts or passwords, so share codes only with your group.
- Trips can't be listed or browsed. Someone needs the code to find one.
- Firebase's free Spark plan allows 50,000 reads and 20,000 writes per day, which is plenty for group trips.
