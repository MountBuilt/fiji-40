# Fiji Fabulous 40 Planner

Live collaborative trip planner for June 21–27 at Shangri-La Yanuca Island.

---

## Step 1 — Set Firebase Database Rules

The default Firebase rules block all reads/writes. You need to open them up for your app to work.

1. Go to the [Firebase Console](https://console.firebase.google.com)
2. Select your **fiji-40** project
3. In the left sidebar: **Build → Realtime Database**
4. Click the **Rules** tab
5. Replace the rules with this:

```json
{
  "rules": {
    "fijiPlanner": {
      ".read": true,
      ".write": true
    }
  }
}
```

6. Click **Publish**

> This allows anyone who knows your Firebase database URL to read and write.
> Since you're only sharing the GitHub Pages link with friends, this is fine
> for a short trip. The database URL is not easily guessable.

---

## Step 2 — Add your GitHub Pages domain to Firebase

This restricts your API key so it only works from your deployed site (and localhost for testing).

1. In the Firebase Console, click the **gear icon → Project Settings**
2. Scroll down to **Authorised domains**
3. Click **Add domain**
4. Add: `mountbuilt.github.io`

---

## Step 3 — Deploy to GitHub Pages

### Option A: GitHub web interface (easiest)

1. Go to [https://github.com/MountBuilt/fiji-40](https://github.com/MountBuilt/fiji-40)
2. Delete the existing `index.html` (click the file → pencil icon → three dots → Delete)
3. Click **Add file → Upload files**
4. Upload the `index.html` file from this folder
5. Commit directly to `main`

### Option B: Git command line

```bash
git clone https://github.com/MountBuilt/fiji-40.git
cd fiji-40
# Copy the index.html from this folder into the repo
git add index.html
git commit -m "Add Fiji Fabulous 40 Planner"
git push origin main
```

### Enable GitHub Pages

1. Go to your repo on GitHub
2. **Settings → Pages**
3. Under **Source**, select **Deploy from a branch**
4. Branch: `main`, folder: `/ (root)`
5. Click **Save**

Your site will be live at:
**https://mountbuilt.github.io/fiji-40/**

(Takes 1–2 minutes after first deploy.)

---

## Sharing with families

Just send them the link: **https://mountbuilt.github.io/fiji-40/**

Each person selects their family from the dropdown. Their selection is remembered in their browser. Any changes they make (checking attendance, editing activities, adding cards) sync live to everyone else.

---

## First load behaviour

On the very first visit after deploy, the app will seed the database with the pre-populated activities. This happens automatically — you'll see the planner fill in within a second or two.

---

## Making changes to activities

All activities are editable directly in the planner — click any name or notes field to edit, then click away to save. Changes sync instantly to all users.
