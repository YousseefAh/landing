# Complete Guide: How to Migrate a Project to a New Repository & Back

This document provides a detailed, beginner-friendly guide explaining the entire process of temporarily pointing a local project to a new GitHub repository, pushing your code there, and then restoring the local project's connection to its original repository.

**The core principle is simple: your local project folder has a "mailing address" (a URL) that tells it where to send code on GitHub. All we are doing is changing that address. The original repository on GitHub is never directly touched and remains safe.**

---

### **Part 1: Pushing Your Local Project to a NEW GitHub Repository**

**Goal:** To upload a complete copy of your local project to a new, empty repository on GitHub.

#### **Step 1: Create a New, Empty Repository on GitHub**
First, you need a new, empty home for your project on GitHub.

1.  Go to [github.com/new](https://github.com/new).
2.  Enter a **Repository name** (in our case, we used `Hero`).
3.  **This is the most important step:** Leave the repository completely empty. **Do NOT** check the boxes to add a `README`, `.gitignore`, or `license`. This prevents conflicts later.
4.  Click **Create repository**.
5.  On the next page, copy the repository's HTTPS URL. It will look like this: `https://github.com/YourUsername/Hero.git`.

#### **Step 2: Go to Your Project Folder in the Terminal**
Open your terminal and navigate to the directory of the project you want to move.
```bash
# Example for your project
cd D:/Code/landing
```

#### **Step 3: Change Your Local Project's "Mailing Address"**
Now, you'll tell your local project to point to the new repository. This is the key step. It **only changes a setting on your computer**.

```bash
# This command sets the URL for the remote named "origin"
# Replace the URL with the one you copied in Step 1
git remote set-url origin https://github.com/YourUsername/Hero.git
```
To confirm it worked, you can run `git remote -v`. You should see the new `Hero` repository URL.

#### **Step 4: Prepare and Push All Your Code**
Now you'll send your project's files to the new `Hero` repository.

1.  **Rename your main branch (Best Practice):** It's a modern standard to name the primary branch `main`.
    ```bash
    git branch -M main
    ```

2.  **Push your code:** This command sends your `main` branch to the new `origin` (which is now your `Hero` repo).
    ```bash
    git push -u origin main
    ```

**Result of Part 1:** Your `Hero` repository on GitHub is now a complete copy of your project. Your original `landing` repository on GitHub is completely unchanged.

---

### **Part 2: Restoring Your Local Project to its ORIGINAL Repository**

**Goal:** To reconnect your `D:/Code/landing` folder back to the original `landing` repository on GitHub.

#### **Step 1: Change the "Mailing Address" Back**
Just like in Part 1, you use the `set-url` command, but this time with the URL of your **original** repository.

```bash
# Make sure you are still in the D:/Code/landing directory
git remote set-url origin https://github.com/YourUsername/landing.git
```
You can run `git remote -v` again to confirm it's pointing back to the `landing` repo.

**Result of Part 2:** Your `D:/Code/landing` project is now back to normal, fully connected to its original `landing` repository on GitHub.

---

### **Part 3: Creating a Separate Local Copy of the New Repo**

**Goal:** To have both projects on your computer in separate folders, so you can work on them independently.

#### **Step 1: Navigate to a General Code Folder**
In your terminal, move up from your specific project folder to a general-purpose directory.
```bash
# This command moves you up one level
cd ..
# You should now be in D:/Code
```

#### **Step 2: Clone the New Repository**
The `git clone` command downloads a fresh copy of a repository from GitHub into a new folder.

```bash
# This will download the "Hero" repo into a new folder named "hero-landing"
git clone https://github.com/YousseefAh/Hero.git hero-landing
```

### **Final Summary**

You now have a perfect setup:
*   The folder `D:/Code/landing` is your original project, connected to the `landing` GitHub repo.
*   The folder `D:/Code/hero-landing` is your new project, connected to the `Hero` GitHub repo.

Both projects are independent and can be worked on without affecting each other. 