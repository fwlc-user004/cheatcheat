
![The San Juan Mountains are beautiful!](images/git.webp "San Juan Mountains")     

# Git Cheat Sheet 
                             
## **Git Configuration**
 
### Set User Details
```bash
git config --global user.name <name>
git config --global user.email <email>
```
Define the author name and email to be used for all commits by the current user.
 
### Create Git Aliases
```bash
git config --global alias.<alias-name> <git-command>
```
Create shortcuts for Git commands (e.g., `alias.glog "log --graph --oneline"`).
 
### Set Default Editor
```bash
git config --system core.editor <editor>
```
Set the default editor for all users on the machine (e.g., `vi`).
 
### Edit Global Config
```bash
git config --global --edit
```
Open the global configuration file for manual editing.
 
---
 
## **Git Basics**
 
### Initialize a Repository
```bash
git init <directory>
```
Create an empty Git repository in the specified directory. Run without arguments to initialize the current directory.
 
### Clone a Repository
```bash
git clone <repo>
```
Clone a repository located at `<repo>` onto your local machine.
 
---
 
## **Staging and Committing Changes**
 
### Stage Changes
```bash
git add <file>
git add <directory>
```
Stage specific files or all changes within a directory.
 
### Commit Changes
```bash
git commit -m "<message>"
```
Commit the staged snapshot with the specified message.
 
### Amend Last Commit
```bash
git commit --amend
```
Replace the last commit with the staged changes and last commit combined.
 
---
 
## **Inspecting History**
 
### View Commit History
```bash
git log
```
Display the commit history using the default format.
 
### Simplify Output
```bash
git log --oneline
```
Condense each commit to a single line.
 
### Graphical Log
```bash
git log --graph --decorate
```
Draw a text-based graph of commits.
 
### Filter Log by Author
```bash
git log --author="<pattern>"
```
Search for commits by a specific author.
 
### Search Commit Messages
```bash
git log --grep="<pattern>"
```
Find commits with messages matching a specific pattern.
 
---
 
## **Undoing Changes**
 
### Unstage a File
```bash
git reset <file>
```
Remove a file from the staging area without overwriting changes.
 
### Discard Changes in Working Directory
```bash
git checkout -- <file>
```
Discard all changes in the specified file (irreversible).
 
### Reset to Previous Commit
```bash
git reset --hard <commit>
```
Reset the working directory and staging area to the specified commit.
 
---
 
## **Branching and Merging**
 
### Create a Branch
```bash
git branch <branch>
```
Create a new branch.
 
### Switch Branches
```bash
git checkout <branch>
git switch <branch>
```
Switch to an existing branch.
 
### Merge Branches
```bash
git merge <branch>
```
Merge the specified branch into the current branch.
 
### Rebase Branch
```bash
git rebase <base>
```
Rebase the current branch onto `<base>`.
 
---
 
## **Remote Repositories**
 
### Add a Remote
```bash
git remote add <name> <url>
```
Create a new connection to a remote repository.
 
### Fetch Changes
```bash
git fetch <remote>
```
Fetch changes from a remote repository.
 
### Pull Updates
```bash
git pull <remote>
```
Fetch and merge changes from the specified remote repository.
 
### Push Changes
```bash
git push <remote> <branch>
```
Push commits to the specified branch in the remote repository.
 
---
 
## **Tagging**
 
### Create a Tag
```bash
git tag <tag>
```
Create a lightweight tag.
 
### Annotated Tag
```bash
git tag -a <tag> -m "<message>"
```
Create an annotated tag with a message.
 
### Push Tags
```bash
git push <remote> --tags
```
Push tags to the remote repository.
 
---
 
## **Rewriting History**
 
### Interactive Rebase
```bash
git rebase -i <base>
```
Interactively rebase the current branch onto `<base>`.
 
### Amend a Commit
```bash
git commit --amend
```
Modify the most recent commit.
 
---
 
## **Stashing**
 
### Save Work in Progress
```bash
git stash
```
Save changes for later use.
 
### Apply Stashed Changes
```bash
git stash apply
```
Apply changes without removing them from the stash.
 
### Drop a Stash
```bash
git stash drop
```
Remove a specific stash entry.
 
---
 
## **Additional Tips**
 
- **Use Aliases:** Create shortcuts for frequently used commands.
- **Pull Before Push:** Always pull changes from the remote branch before pushing to avoid conflicts.
- **Clean Up:** Use `git clean` to remove untracked files from your working directory.
 
For more information, visit [Atlassian Git Tutorials](http://atlassian.com/git).
