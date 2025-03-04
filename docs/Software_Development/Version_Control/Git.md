# Git Cheat Sheet

## Basic Setup
- **Configure Git (Set Username & Email)**
  ```bash
  git config --global user.name "Your Name"
  git config --global user.email "your.email@example.com"
  ```
- **Check Configuration**
  ```bash
  git config --list
  ```

## Creating and Cloning Repositories
- **Initialize a new repository**
  ```bash
  git init
  ```
- **Clone an existing repository**
  ```bash
  git clone <repository-url>
  ```

## Working with Files
- **Check the status of your working directory**
  ```bash
  git status
  ```
- **Track a new file**
  ```bash
  git add <file>
  ```
- **Track all files**
  ```bash
  git add .
  ```
- **Commit changes with a message**
  ```bash
  git commit -m "Your commit message"
  ```
- **Commit changes with all modified files**
  ```bash
  git commit -a -m "Your commit message"
  ```

## Branching and Merging
- **Create a new branch**
  ```bash
  git branch <branch-name>
  ```
- **List all branches**
  ```bash
  git branch
  ```
- **Switch to another branch**
  ```bash
  git checkout <branch-name>
  ```
- **Create and switch to a new branch**
  ```bash
  git checkout -b <branch-name>
  ```
- **Merge a branch into the current branch**
  ```bash
  git merge <branch-name>
  ```
- **Delete a branch**
  ```bash
  git branch -d <branch-name>
  ```

## Remote Repositories
- **Add a remote repository**
  ```bash
  git remote add origin <repository-url>
  ```
- **View remote repositories**
  ```bash
  git remote -v
  ```
- **Fetch latest changes from remote**
  ```bash
  git fetch
  ```
- **Pull latest changes and merge**
  ```bash
  git pull origin <branch-name>
  ```
- **Push changes to remote**
  ```bash
  git push origin <branch-name>
  ```

## Undoing Changes
- **Undo changes in working directory**
  ```bash
  git checkout -- <file>
  ```
- **Reset staged changes**
  ```bash
  git reset HEAD <file>
  ```
- **Revert a commit**
  ```bash
  git revert <commit-hash>
  ```
- **Hard reset to a previous commit**
  ```bash
  git reset --hard <commit-hash>
  ```

## Stashing Changes
- **Stash current changes**
  ```bash
  git stash
  ```
- **List stashes**
  ```bash
  git stash list
  ```
- **Apply latest stash**
  ```bash
  git stash apply
  ```
- **Apply and remove latest stash**
  ```bash
  git stash pop
  ```

## Git Logs and History
- **View commit history**
  ```bash
  git log
  ```
- **Compact commit history (one-liner)**
  ```bash
  git log --oneline --graph --decorate
  ```
- **Show changes in a commit**
  ```bash
  git show <commit-hash>
  ```

## Tagging
- **Create a tag**
  ```bash
  git tag <tag-name>
  ```
- **Push tag to remote**
  ```bash
  git push origin <tag-name>
  ```
- **List all tags**
  ```bash
  git tag
  ```
- **Delete a tag locally**
  ```bash
  git tag -d <tag-name>
  ```
- **Delete a tag from remote**
  ```bash
  git push --delete origin <tag-name>
  ```

## Advanced Commands
- **Rebase a branch**
  ```bash
  git rebase <branch-name>
  ```
- **Squash commits**
  ```bash
  git rebase -i HEAD~<number-of-commits>
  ```
- **Cherry-pick a commit**
  ```bash
  git cherry-pick <commit-hash>
  ```

## Aliases for Efficiency
- **Create a shortcut for a long command**
  ```bash
  git config --global alias.co checkout
  ```
- **List configured aliases**
  ```bash
  git config --get-regexp alias
  
