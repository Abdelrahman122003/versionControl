# Professional Git Workflow

A professional Git workflow helps teams collaborate efficiently and maintain a clean codebase. Here’s a simple way to work with Git, along with an example.

## Steps for a Professional Git Workflow

1.  **Initialize Your Repository:**

    ```s
    git init my-project
    cd my-project
    ```

2.  **Create Main Branches:**

    ```s
    git checkout -b main   # Create and switch to main branch
    git checkout -b develop # Create and switch to develop branch

    ```

3.  **Create a New Branch:** When starting a new feature, create a feature branch off the develop branch:

    ```s
    git checkout develop
    git checkout -b feature/my-new-feature

    ```

4.  **Work on Your Feature:** Make changes to your code, then stage and commit them:

    ```s
       # Edit files...
    git add .
    git commit -m "Add my new feature"
    ```

5.  **Merge Feature Branch into Develop**Once the feature is complete, merge it back into the develop branch:

    ```s
    git checkout develop
    git merge feature/my-new-feature
    ```

6.  **Delete the Feature Branch**: After merging, you can delete the feature branch:

    ```s
    git branch -d feature/my-new-feature
    ```

7.  **Prepare for Release**: When you’re ready to release, create a release branch from develop:

    ```s
    git checkout -b release/v1.0.0
    ```

8.  **Final Adjustments**: Make any final changes or bug fixes in the release branch, then commit them:

    ```s
    # Edit files...
    git add .
    git commit -m "Finalize release v1.0.0"

    ```

9.  **Merge Release into Main**: Merge the release branch into the main branch and tag it:

    ```s
    git checkout main
    git merge release/v1.0.0
    git tag -a v1.0.0 -m "Release version 1.0.0"
    ```

10. **Merge Back into Develop:** It’s important to keep develop up to date, so merge the main changes back into develop:

    ```s
    git checkout develop
    git merge main

    ```

11. **Delete the Release Branch**: After the release, you can delete the release branch:

    ```s
    git branch -d release/v1.0.0

    ```

12. **Hotfix Branches**: If a critical bug is found in production, create a hotfix branch from main:

    ```s
    git checkout main
    git checkout -b hotfix/fix-bug
    ```

    After fixing the bug, merge it back into both main and develop:

    ```s
    git add .
    git commit -m "Fix critical bug"
    git checkout main
    git merge hotfix/fix-bug
    git checkout develop
    git merge hotfix/fix-bug
    git branch -d hotfix/fix-bug

    ```

## Summary of the Workflow

- Feature branches allow developers to work on new features without affecting the main codebase.
- Release branches help in preparing and stabilizing new releases.
- Hotfix branches provide a quick way to address production issues.
