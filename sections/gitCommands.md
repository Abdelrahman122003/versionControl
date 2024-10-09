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
