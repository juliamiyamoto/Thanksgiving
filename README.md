# Friendsgiving sign-up

Guests claim a dish, everyone sees who's bringing what, and nobody can claim a dish twice.
The host's dishes (turkey, ham, stuffing, gravy, cranberry sauce) are set at the top of the script in `index.html`.

Sign-ups are saved in Firebase (free). One-time setup, about 10 minutes:

## 1. Create a Firebase project
1. Go to https://console.firebase.google.com and sign in with a Google account.
2. **Add project** → name it (e.g. `friendsgiving`) → you can turn Google Analytics off → **Create project**.

## 2. Add a web app and copy its settings
1. On the project home page, click the **</>** (Web) icon.
2. Give it a nickname, leave "Firebase Hosting" unchecked, click **Register app**.
3. Firebase shows a `firebaseConfig = { ... }` block. Copy the values into the
   `firebaseConfig` block at the top of the `<script type="module">` in `index.html`,
   replacing every `PASTE...` value.

## 3. Turn on anonymous sign-in
Guests don't make accounts. Each browser gets a silent anonymous ID so people can remove only their own dish.
1. Left menu: **Build → Authentication → Get started**.
2. **Sign-in method** tab → **Anonymous** → enable → **Save**.
3. Still in Authentication: **Settings → Authorized domains → Add domain** → add
   `YOUR-GITHUB-USERNAME.github.io`.

## 4. Create the database and paste the rules
1. Left menu: **Build → Firestore Database → Create database**.
2. Pick a location near you (e.g. `nam5 (United States)`), start in **production mode**.
3. Open the **Rules** tab, replace everything with the contents of `firestore.rules`, click **Publish**.

## 5. Put it on GitHub Pages
1. Create a new public repo (e.g. `friendsgiving`) and upload `index.html`, `flyer.jpg` (and this README).
2. Repo **Settings → Pages** → Source: **Deploy from a branch** → Branch: `main`, folder `/ (root)` → **Save**.
3. After a minute the site is live at `https://YOUR-GITHUB-USERNAME.github.io/friendsgiving/`.

## Managing the list
- To remove or fix anyone's dish: Firebase console → **Firestore Database → Data → dishes** → delete the document.
- To change what the host is making: edit `HOST_DISHES` at the top of the script in `index.html`.

The Firebase `apiKey` in `index.html` is meant to be public; the rules in `firestore.rules` are what protect the list.
