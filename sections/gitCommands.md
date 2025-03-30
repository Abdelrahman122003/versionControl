# Version Control

## Git Commands

- Edit the Git Configuration File

  ```sh
  git config --global --edit
  ```

- `git init`

  Initialize a new Git repository in the current directory

- To remove the version history

  ```sh
  rm -rf .git
  ```

  The command rm -rf .git is a Unix/Linux command used to remove a Git repository directory. Here’s what it does:

  - `rm`: The command used to remove files or directories.
  - `-r`: Stands for "recursive," allowing the command to delete directories and their contents recursively.
  - `-f`: Stands for "force," ignoring nonexistent files and suppressing confirmation prompts.
  - `.git`: The directory that stores the Git repository metadata and history.

- `git clone` **repository-url**

  Clone a remote repository into the current directory

- `git status`

  Check the status of the repository (e.g., modified files, untracked files)

- `git add` Command

  - git add **file-or-directory**: Adds a specific file or directory to the staging area, preparing it for the next commit.

  - git add `.` : Adds all changes (modified, deleted, new files) in the current directory and its subdirectories to the staging area.

- `git reset` .

  Use git reset when you want to unstage changes without discarding them, allowing you to adjust or re-stage different files before committing.

- `git reset --soft HEAD~1`

  If you want to undo a commit but keep the changes in your working directory.

- `git checkout` Command

  - git checkout -- **file-name**:

    Discards changes in the specified file and restores it to its last committed

  - git checkout **branch-name**:

    Switches the working directory to the specified branch.

  - git checkout **commit-hash**:

    Switches the working directory to the state of the specified commit.

  - git checkout -b **new-branch**:

    Creates a new branch and switches to it immediately.

- `git commit -m` "Your commit message here"

  Commit the staged changes with a descriptive message

- `git log`

  Show a list of all the commits in the current branch

- `git push origin` **branch-name**

  Push changes from the local repository to the remote repository

- `git pull origin` **branch-name**

  Pull the latest changes from the remote repository to the local repository

- `git branch` **new-branch-name**

  Create a new branch

- `git merge` **branch-name**

  Merge a specified branch into the current branch

- `git diff` **commit-id-or-branch** **commit-id-or-branch**

  View a summary of the changes between two commits or branches

- `git branch -d` **branch-name**

  Delete a branch locally

- `git reset` --hard HEAD

  Reset the staging area and working directory to the state of the last commit

- `git stash`

  Stash changes in the working directory temporarily

- `git stash` apply

  Apply stashed changes back to the working directory

- `git push origin` --delete **branch-name**

  Delete a remote branch

- `git remote add origin` **new-repository-url**

  Add a new remote repository or change the URL of an existing one

## Aliases

- **Add or Update an Alias**
  ```sh
  git config --global alias.<alias-name> '<command>'
  ```
- **List All Aliases**

  Display all the aliases you have set.

  ```sh
  git config --get-regexp alias
  ```

- **Remove an Alias**

  Remove a specific alias.

  ```sh
  git config --global --unset alias.<alias-name>
  ```

- **Add an Alias for a Complex Command**

  Create an alias for a more complex command.

  ```sh
  git config --global alias.st 'status -s'
  ```

## Rename Branch

1. **Switch to the Branch You Want to Rename**:

   ```bash
   git checkout old-branch-name
   ```

2. **Rename the Branch**:

   ```bash
   # (-m or --move)
   git branch -m new-branch-name
   ```

3. **Push the Renamed Branch to Remote** (if the branch exists on the remote):

   ```bash
   # -u => The -u flag in Git is short for --set-upstream. It is used when pushing a branch to a remote repository to set the upstream (tracking) reference
   git push origin -u new-branch-name
   ```

4. **Delete the Old Branch from Remote** (if the branch exists on the remote):
   ```bash
   git push origin --delete old-branch-name
   ```

## **Step-by-Step Explanation of Interactive Rebase to Remove a File from a Commit**

- **1️⃣ `Start an Interactive Rebase`**  
  **Command:**

  ```sh
  git rebase -i <commit>~
  ```

  **What it does:**

  - Starts an **interactive rebase** from the commit **before** the one you want to modify.
  - The `~` ensures Git includes that commit for editing.
  - To find the commit ID, use:
    ```sh
    git log --oneline
    ```
    Example log:
    ```
    a1b2c3d Fixing UI bug
    e4f5g6h Added new feature
    i7j8k9l Initial commit
    ```
    If you want to modify `e4f5g6h`, run:
    ```sh
    git rebase -i e4f5g6h~
    ```

- **2️⃣ `Edit the Commit`**

  **What happens next:**

  - Git opens an editor (like Vim or VS Code) listing commits:
    ```
    pick e4f5g6h Added new feature
    pick a1b2c3d Fixing UI bug
    ```
  - **Change** `pick` to `edit` on the target commit:
    ```
    edit e4f5g6h Added new feature
    pick a1b2c3d Fixing UI bug
    ```
  - **Save and exit** (In Vim: press `Esc`, type `:wq`, and press `Enter`).

- **3️⃣ `Remove the Unwanted File`**

  **Command:**

  ```sh
  git rm <unwanted-file>
  ```

  **What it does:**

  - **Deletes the file** from the commit without affecting other files.
  - Example: If you accidentally committed `secrets.txt`, remove it:
    ```sh
    git rm secrets.txt
    ```

- **4️⃣ `Amend the Commit`**

  **Command:**

  ```sh
  git commit --amend
  ```

  **What it does:**

  - Opens the commit message editor so you can **re-save the commit** without the removed file.
  - You **don’t need to change the message**—just save and exit.
  - The commit is now **modified** with the file removed.

- **5️⃣ `Continue the Rebase`**

  **Command:**

  ```sh
  git rebase --continue
  ```

  **What it does:**

  - Tells Git to continue applying the rest of the commits **on top of the modified one**.
  - If there are conflicts, Git will ask you to resolve them before proceeding.
