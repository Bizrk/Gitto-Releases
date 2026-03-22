# Gitto 🚀

<div align="center">
  <img src="./logo.svg" alt="Gitto Logo" width="300" />
</div>

Welcome to **Gitto** — a lightweight, lightning-fast native desktop Git client built with Tauri, Rust, and React! 

Gitto is designed to get out of your way and act as a transparent GUI over your existing Git setup. Instead of reinventing the wheel with a heavy standalone Git library, Gitto interacts directly with your machine's native `git` CLI.

<div align="center">
  <img src="./Main%20UI.png" alt="Gitto Main Interface" width="800" />
</div>

---

## 📥 Installation & Updating

1. **Downlod Latest Release**: Visit the [Releases page](https://github.com/Bizrk/Gitto-Releases/releases) directly on this repository to download the newest `.exe` or `.msi` native installer.
2. **Auto-Updater**: Gitto includes a built-in seamless automatic updater! Whenever a new update drops here on GitHub, Gitto will automatically download it in the background and pop up an `Update Ready (Restart)` pill inside the app. One click, and you're up to date!

---

## 🔐 Credentials & Authentication (How it Works)

Many Git clients force you to log into their app, handle OAuth, generate custom tokens, or store passwords internally. **Gitto doesn't do any of that.** 

Because Gitto relies completely on your machine's native `git` executable, it offloads 100% of credential management to your operating system and your local Git Credential Manager (GCM). 

* **GitHub, GitLab, & Bitbucket**: Whether your repo is public or private, Gitto executes a standard pull/push action. If you aren't authenticated, your OS's Credential Manager will intercept the request and show you a native platform login popup in your browser.
* **Self-Hosted / Private Servers**: For internal servers, GCM will usually pop up a standard username/password/PAT box. 
* **Zero Storage**: Gitto never stores, sees, or even touches your passwords. Your keys remain completely locked in the Windows Credential Manager or macOS Keychain. Secure by design!

---

## 📂 Setting up Repositories

Gitto handles repository onboarding smoothly through two flows. If you open Gitto in a non-tracked, empty folder, you get two choices:

### 1. Clone a Remote Repository (Recommended)
By selecting **Clone Remote Repository**, Gitto will ask for your repository URL (e.g., `https://github.com/user/repo.git`). It will automatically run a native `git clone` into the folder. 
* *Note: If authentication is required, your Credential Manager will pop up securely to log you in.* It will download the entire repository, check out the default branch, and you'll be ready to go immediately!

### 2. Init & Add Remote Origin
If you select **Initialize Local Repository**, Gitto runs `git init` locally. You can begin tracking files right away. 
* **To add a remote server later**: Click the **+ ADD REMOTE ORIGIN** button on the bottom of the left sidebar.
* **What happens?**: Gitto maps the origin URL and immediately runs a `git fetch` in the background (prompting for credentials if needed). All remote branches will instantly populate your sidebar, ready for Worktree or local checkouts.

---

## 🌲 Core Philosophy & Features

Gitto is built around treating native Git features like first-class citizens:

- **Worktrees over Branch-Switching**: Instead of constantly stashing your work and forcing your editor to reload all its files just to look at a bug on another branch, Gitto uses **Git Worktrees**. Selecting "Create Worktree" from a branch will attach it to an isolated folder sitting physically next to your primary repository. Work in parallel completely cleanly! 
  * Note: To prevent confusion, newly created Worktree folders are intentionally "locked" to the branch they were created for. You will use your primary core repo folder if you just want to swap branches traditionally.
  <br/><br/><img src="./New%20Worktree%20Branch.png" alt="Creating a New Worktree" width="600" /><br/>
- **Local Setup & Config Files**: Easily configure `.env` syncing to automatically bring essential local files to new worktrees so your local development flow is never broken by missing secrets.
  <br/><br/><img src="./Local%20Setup%20Files.png" alt="Configuring Local Setup Files" width="600" /><br/>
- **Diff Viewing**: Inline viewing of code changes and staging statuses straight from the active branch in an aggressively optimized panel.

---

### Need Help or Found a Bug?
Feel free to open an Issue here in this `Gitto-Releases` repository if you encounter any problems, find a bug, or want to request new functionality!
