# Guide: How to Move a Local Project to a New GitHub Repository

This document provides a step-by-step guide on how to take an existing local project that is tracked by Git and push it to a new, empty repository on GitHub without affecting the original repository.

### **Core Concept**

Your local Git project has a configuration file that stores the URL of the remote repository it's connected to (usually named `origin`). The process involves simply changing this URL to point to a new repository. This way, all push and pull operations will be directed to the new location, leaving the original repository untouched.

---

### **Step-by-Step Instructions**

#### **Step 1: Create a New, Empty Repository on GitHub**

First, you need a new, empty home for your project on GitHub.

1.  Navigate to [github.com/new](https://github.com/new).
2.  Choose a **Repository name** for your new project.
3.  **Important**: Leave the repository empty. **Do NOT** check the boxes to initialize it with a `README`, `.gitignore`, or `license` file. This is crucial to prevent errors when you push your existing project.
4.  Click the **Create repository** button.
5.  After the repository is created, copy the HTTPS URL provided. It will look like this: `https://github.com/YourUsername/New-Repository-Name.git`.

#### **Step 2: Open Your Local Project in the Terminal**

Using your command line or terminal, navigate into the root directory of the local project you want to move.

#### **Step 3: Verify Your Current Remote Connection (Optional)**

To see which remote repository your project is currently connected to, run the following command:

```bash
git remote -v
```

This will display the URLs for the `origin` remote, which should be pointing to your *old* GitHub repository.

#### **Step 4: Update the Remote URL to Point to Your New Repository**

This is the key step where you disconnect from the old repository and connect to the new one. Run the `git remote set-url` command, pasting the URL you copied in Step 1.

```bash
# Replace the URL with your new repository's URL
git remote set-url origin https://github.com/YourUsername/New-Repository-Name.git
```

To confirm the change was successful, you can run `git remote -v` again. You should now see the URL of your new repository.

#### **Step 5: Ensure Your Branch is Named `main`**

It is a modern convention for the default branch to be named `main`. To rename your current branch to `main`, run this command:

```bash
git branch -M main
```
This command forces the rename, which is safe and effective.

#### **Step 6: Push Your Code to the New Repository**

Now it's time to upload your project's files and history to their new home. Run the following command:

```bash
git push -u origin main
```

*   `git push`: The command to upload your code.
*   `-u origin main`: This sets the upstream branch. It creates a link between your local `main` branch and the `main` branch on the `origin` remote. This is a one-time setup that allows you to use simpler commands like `git push` and `git pull` in the future.

Your project is now successfully hosted on the new GitHub repository. The original repository has not been changed or affected in any way. 