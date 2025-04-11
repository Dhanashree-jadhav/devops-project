# Interview Questions and Answers on Git

These are key Git-related questions I prepared for interviews, along with answers based on my experience with the `devops-project` repository on GitHub (`github.com/Dhanashree-jadhav/devops-project`).

## Questions and Answers

1. **What is Git?**  
   Git is a distributed version control system (VCS) that allows multiple developers to track and manage changes to code in a project. It enables collaborative development by maintaining a full history of changes, supporting branching for parallel work, and allowing offline operations. In my `devops-project`, I used Git to create branches like `dev` and `feature/add-logging`, commit changes (e.g., `deploy.sh`, `logging.sh`), and push them to GitHub, ensuring version control throughout the development process.

2. **What is the difference between merge and rebase?**  
   - **Merge**: Combines changes from one branch into another, creating a new "merge commit" that preserves the history of both branches. It’s non-destructive and shows the full lineage. In my project, I merged `feature/add-logging` into `dev` and `dev` into `main` via pull requests, keeping a clear history of integrations.  
   - **Rebase**: Moves or reapplies commits from one branch onto another, rewriting history to make it appear as if the changes were made on the target branch. It creates a linear history but can be disruptive if shared. I didn’t use rebase in my project to avoid altering the public history on GitHub.  
   - **Key Difference**: Merge preserves branch history; rebase rewrites it. Merge is safer for collaborative workflows, while rebase is better for cleaning up local commits before sharing.

3. **What is a pull request?**  
   A pull request (PR) is a GitHub feature that proposes changes from one branch to another, typically for review and integration. It allows team members to discuss, review, and approve code before merging. In my `devops-project`, I created PRs like “Add logging script to dev” (from `feature/add-logging` to `dev`) and “Merge dev to main” (from `dev` to `main`), enabling a structured workflow to ensure quality before integrating changes into `main`.

4. **How do you resolve merge conflicts?**  
   Merge conflicts occur when Git can’t automatically combine changes from different branches (e.g., overlapping edits). To resolve them:  
   1. Start the merge (e.g., `git merge dev` on `main`).  
   2. If conflicts arise, Git pauses and marks conflicted files (e.g., with `<<<<<<<`, `=======`, `>>>>>>>` markers).  
   3. Open the file in VS Code, manually edit to resolve conflicts (e.g., choose one version or combine changes).  
   4. Mark the resolution by staging the file: `git add <file>`.  
   5. Complete the merge: `git commit`.  
   In my project, I avoided conflicts by working on separate files (`deploy.sh` vs. `logging.sh`), but if they occurred, I’d follow this process to ensure a clean merge.

5. **What are Git tags?**  
   Git tags are markers used to label specific commits, typically for releases. They are immutable and can be annotated with messages. In my `devops-project`, I created an annotated tag `v1.0.0` with `git tag -a v1.0.0 -m "Initial release with scripts"` and pushed it with `git push origin v1.0.0` to mark the stable version of `main` with `deploy.sh` and `logging.sh`, making it easy to reference that release point.

6. **What is Git workflow?**  
   A Git workflow is a structured process for managing code changes using branches, commits, and merges. A common workflow (used in my project) is the **Gitflow-like approach**:  
   - **Main**: Stable production code.  
   - **Dev**: Integration branch for features.  
   - **Feature Branches**: Isolate new work (e.g., `feature/add-logging` for `logging.sh`).  
   - **Process**: Develop on a feature branch, create a pull request to `dev`, merge after review, then merge `dev` to `main`, and tag releases (e.g., `v1.0.0`). This ensured organized collaboration and versioning in my project.

7. **Explain git stash.**  
   `git stash` temporarily saves uncommitted changes (both staged and unstaged) in your working directory, allowing you to switch branches or pull updates without committing. For example, if I edited `deploy.sh` but needed to switch to `main` to pull changes, I’d run:  
   - `git stash` to save the changes.  
   - `git checkout main` and perform the task.  
   - `git stash pop` to reapply and continue work.  
   In my project, I didn’t need it due to planned commits, but it’s useful for managing interruptions.

8. **What is the use of .gitignore?**  
   The `.gitignore` file specifies which files or directories Git should ignore when tracking changes, preventing clutter like build artifacts or sensitive data from being committed. In my `devops-project`, I added a `.gitignore` to exclude unnecessary files (e.g., `.vscode/` or `node_modules/` if applicable), ensuring only relevant files like `deploy.sh` and `logging.sh` were tracked, keeping the repository clean and focused.