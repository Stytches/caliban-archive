# Quartz Setup Guide for Caliban's Archive

This guide will help you turn your current folder of Vampire: The Masquerade notes into a beautiful, public website using **Quartz**.

## Prerequisites

Since you are on Linux, you will need the following installed in your terminal:

1. **Git** (for version control)
2. **Node.js** (version 18 or higher) and **npm** (to build the site)

You can check if you have them by running:

```bash
git --version
node --version
npm --version
```

---

## Step 1: Clone the Quartz Repository

You need to download the Quartz "engine" to a new folder. It's best to keep this separate from your current notes folder initially, then move your notes into it.

1. Open your terminal.
2. Navigate to where you want the website project to live (e.g., your `Gaming` folder).
3. Run the following command to clone the starter code:

```bash
git clone https://github.com/jackyzha0/quartz.git caliban-archive
cd caliban-archive
```

4. Install the necessary dependencies:

```bash
npm install
```

5. Initialize a new setup:

```bash
npx quartz create
```

*(Select "Empty Quartz" or "Default" when prompted. "Default" is good to see how it works, but you'll delete the example files later.)*

---

## Step 2: Import Your Content

Quartz looks for markdown files in a specific folder called `content`.

1. **Clear the example content:**
    Delete everything inside the `caliban-archive/content` folder (except `.gitkeep` if it exists).

2. **Copy your files:**
    Copy all your `.md` files (`Caliban_Character_Sheet.md`, `Caliban_Backstory.md`, etc.) into the `caliban-archive/content` folder.

    *Tip: If you want to keep your current folder as the "source of truth," you can create a symbolic link instead of copying, but copying is safer for beginners to avoid messing up your original files.*

3. **Set the Index:**
    Quartz needs a "Home" page. Rename `Caliban_Character_Sheet.md` (or whichever file you want as the front page) to `index.md`.

---

## Step 3: Preview the Site Locally

Before publishing, see how it looks on your computer.

1. In the `caliban-archive` terminal, run:

```bash
npx quartz build --serve
```

2. Open your browser and go to `http://localhost:8080`.
3. You should see your character sheet rendered as a website!
4. Press `Ctrl+C` in the terminal to stop the server.

---

## Step 4: Configuration (Optional)

You can customize the site name and settings in the `quartz.config.ts` file.

1. Open `quartz.config.ts` in VS Code.
2. Look for `pageTitle`. Change it from "Quartz" to something like **"The Scholar of Dust"**.
3. Look for `theme`. You can change the colors here to match a "Vampire" aesthetic (e.g., dark grays and deep reds).

---

## Step 5: Publish to GitHub Pages (Free)

This is the easiest way to get it online.

1. **Create a new Repository on GitHub:**
    * Go to GitHub.com and create a new repo named `caliban-archive` (or whatever you like).
    * Do **not** initialize it with a README or .gitignore.

2. **Link your local folder to GitHub:**
    Inside your `caliban-archive` terminal folder:

```bash
git remote set-url origin https://github.com/YOUR_USERNAME/caliban-archive.git
git branch -M v4
git push -u origin v4
```

3. **Enable Automatic Deployment:**
    Quartz has a built-in command to sync to GitHub Pages.

```bash
npx quartz sync
```

This command will:

* Build your site.
* Commit the changes.
* Push them to your GitHub repository.

4. **Activate GitHub Pages:**
    * Go to your repository settings on GitHub.
    * Go to **Pages** (on the left sidebar).
    * Under "Build and deployment", select **GitHub Actions** as the source.

In a few minutes, your site will be live at `https://YOUR_USERNAME.github.io/caliban-archive/`.

---

## Updating Your Site

Whenever you edit your character sheet or add new lore:

1. Edit the files in the `content` folder.
2. Run:

    ```bash
    npx quartz sync
    ```

3. The website updates automatically.
