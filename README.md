# MD Mamun Uddin — Teaching Portfolio

Personal portfolio and admin dashboard for a secondary **Mathematics & Computing Technology (IPT)** teacher.
The whole site is one file: `index.html`.

**Live site (after step 1):** https://mamunbracu.github.io/portfolio-Teaching/

---

## What's inside

**Public website**
- Separate pages: Home, About, Education, Experience, Skills, Gallery, Documents, CV and Contact
- On a computer the menu is a sidebar; on a phone it opens from the ☰ button
- The top bar has the latest updates, a theme picker, light/dark mode and **Login**
- The CV can be viewed online or downloaded as **PDF** or **Word**
- The photo gallery can be filtered by category; documents can be viewed and downloaded

**Admin dashboard** (log in at `…/#/login`)
- **Website content:** homepage text and pictures, profile, education, experience, skills, contact, CV, gallery and documents
- **Teaching library:** private Year 7–12 classes, books and previous classes (notes, PDFs, slides, worksheets…)
- **Settings:** change password, website title, maintenance mode, themes, classes, backup, Firebase connection
- Every save shows a pop-up message, and changes appear live without reloading

---

## Step 1 — Turn on GitHub Pages (2 minutes)

1. In this repository, open **Settings → Pages**.
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Set **Branch: `main`** and folder **`/ (root)`**, then click **Save**.
4. Wait 1–2 minutes and open **https://mamunbracu.github.io/portfolio-Teaching/**

> Until Firebase is connected the site runs in **demo mode**: login password `admin123`, and changes are saved only in your own browser.

---

## Step 2 — Connect the Firebase database (about 15 minutes)

### 2.1 Create the project
1. Go to **https://console.firebase.google.com** and sign in with your Google account.
2. Click **Create a project** → name it e.g. `mamun-portfolio` → Continue (Google Analytics is optional) → **Create project**.

### 2.2 Turn on login (Authentication)
1. Left menu: **Build → Authentication → Get started**.
2. **Sign-in method** tab → **Email/Password** → switch **Enable** on → **Save**.
3. **Users** tab → **Add user**
   - Email: `md.mamun.uddin.fv@gmail.com` (it must be exactly this email; only it can open the dashboard)
   - Password: choose a strong password. This is your admin password.

### 2.3 Create the database (Firestore)
1. Left menu: **Build → Firestore Database → Create database**.
2. Location: **australia-southeast1 (Sydney)** → Next.
3. Choose **Start in production mode** → **Create**.
4. Open the **Rules** tab, delete everything, paste the contents of [`firestore.rules`](firestore.rules) from this repo, then click **Publish**.

### 2.4 Get your web app keys
1. Click the ⚙️ gear next to **Project Overview** → **Project settings**.
2. Scroll to **Your apps** → click the **Web** icon `</>`.
3. App nickname: `portfolio` → **Register app** (you don't need Firebase Hosting).
4. You will see a block like this. Keep this page open:
   ```js
   const firebaseConfig = {
     apiKey: "AIza…",
     authDomain: "mamun-portfolio.firebaseapp.com",
     projectId: "mamun-portfolio",
     storageBucket: "mamun-portfolio.appspot.com",
     messagingSenderId: "1234567890",
     appId: "1:1234567890:web:abc123"
   };
   ```

### 2.5 Paste the keys into the website
1. On GitHub, open **`index.html`** in this repository → click the ✏️ **pencil (Edit)** icon.
2. Near the top (around line 1050) find:
   ```js
   const FIREBASE_CONFIG = {
     apiKey: "",
     authDomain: "",
     ...
   ```
   Tip: press **Ctrl+F** (or ⌘F) and search for `FIREBASE_CONFIG`.
3. Copy each value from Firebase into the matching empty `""`.
4. Click **Commit changes…** → **Commit changes**. GitHub Pages updates in about a minute.

### 2.6 Allow your website address to log in
1. Firebase → **Authentication → Settings → Authorized domains → Add domain**
2. Add: `mamunbracu.github.io` → **Add**.

### 2.7 Log in and add your content
1. Open your site → **Login** → use your Firebase email and password.
2. In Settings the status changes from **Demo mode** to **● Live**.
3. Fill in Profile, Education (add your Bangladesh bachelor degree), Experience, CV, Gallery and Documents.

> **Moving demo content:** anything you added in demo mode lives only in that browser. Before connecting, open
> **Settings → Backup & data → Export backup**; after connecting, **Import backup**. (Uploaded files aren't included in the backup, so upload them again.)

---

## Free plan limits

- Files are stored inside Firestore on the free **Spark** plan, up to **15 MB per file** (1 GB total storage).
- For bigger files, upgrade to **Blaze**, enable **Cloud Storage**, and set `USE_FIREBASE_STORAGE = true` in `index.html`.

## Change your password later
Admin → **Settings → Account & password**, or use **Forgot password?** on the login page.
