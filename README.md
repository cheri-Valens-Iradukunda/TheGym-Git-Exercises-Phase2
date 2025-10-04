
## 1. Create new repository
    * I have created a repository
    * I have cloned it to have it locally
### Commands
```bash
    git clone https://github.com/cheri-Valens-Iradukunda/TheGym-Git-Exercises-Phase2.git
```

## 2. Initialization of my environment
* I have created 4 files, stage them and commit them
### Commands
```bash
touch test{1..4}.md
git add test1.md && git commit -m "chore: Create initial file"
git add test2.md && git commit -m "chore: Create another file"
git add test3.md && git commit -m "chore: Create third and fourth files"
```
# Exercises:
## Part 1 Refining git history
### 1. Missing file fix
* I have assessed the current status of my repository
* After finding that test4.md is not staged, I staged it and commit it using amend
    * Git status: for checking the staged and unstaged files
    * Git log for checking the commit history
    #### commands
    ```bash
    git status
    git log
    git add test4.md
    git commit --ammend --no-edit
    ```
### 2. Editing commit history
* Task is to modify a commit message from "create another file" to "create second file"
#### commands
```bash
git rebase -i HEAD~2
```
* in the .git/COMMIT-EDITMSG change the pick to reword in the commit
```bash
reword chore: Create another file
```
* in the next .git/COMMIT-EDIMSG change the message you want
```bash
chore: Create second file
```
### 2. Keeping History Tidy - Squashing Commits
* Merging "Create second file" into "Create initial file" for a cleaner history using squahs

```bash
git rebase -i HEAD~2
pick chore: Create third and fourth files
squash chore: Create second file
```
* in the next .git/COMMIT-EDITMSG change the message you want
```bash
chore: Create second file
```
### 4. Splitting a Commit:
* separating multiple commits  for tracking two different commits messages using git reset
* checking the  history and then reset to the last commit
```bash
git log --oneline
git reset HEAD~1
git add third.txt && git commit -m "Create third file"
git add forth.txt && git commit -m "Create fourth file"
```
### 5. Advanced Squashing
* combining last two commits ("Create third file" and "Create fourth file") into a single commit named "Create third and fourth files" using rebase
```bash
git rebase -i HEAD~2
pick chrore create forth file
squash chrore create third file
```
* in the next .git/COMMIT-EDITMSG change the message you want
```bash
chore: Create third and fourth files
git rebase --continue
```
### 6. Dropping a Commit
* Create a new file named unwanted.txt
```bash
touch unwanted.txt
git add unwanted.txt
git commit -m"chrore: unwanted file
git rebase -i HEAD~4
drop chrore:unwanted file
git rebase --continue
```
### 7. Reordering Commits
* Rearrange commits within your history
```bash
git rebase -i HEAD~4
```
* Rearrange the commits as you want
```bash
pick chrore:create inital file
pick create third and forth file
pick chrore: create second file
```
```bash
git rebase --continue
```
### Cherry-Picking Commits
* Creating a branch called ft/branch
```bash
git checkout -b ft/branch
touch test5.md
git add test5.md && git commit -m "chrore: Implemented test5"
```
* using git cherry-pick to selectively bring ft/branch commit into main.

```bash
git checkout main
git cherry-pick ft/branch
```
### 9. Visualizing Commit History (Bonus)
* visualize commit history in a tree-like structure.
```bash
git log --graph
```
### 10. Understanding Reflogs (Bonus)
* track all movements of HEAD
```bash
git reflog
```
## Part 2: Branching Basics
### Feature Branch Creation
* Creating a new branch named ft/new-feature and switch to that branch
```bash
git checkout -b ft/new-feature
```
### Working on the Feature Branch
* Create a new file named feature.txt and Commit these changes
```bash
touch feature.txt
git add feature.txt && git commit -m "Implemented core functionality for new feature"
```
### 3. Switching Back and Making More Changes
* Switching from dev and make changes to readme.txt
```bash
git checkout dev
git add readme.txt && git commit -m"chrore: Updated project readme"
```
### 4. Local vs. Remote Branches:
* pushing local changes to the remote repository
```bash
git push origin dev
```

### 5. Branch Deletion
* deleting the ft/new-feature branch
```bash
git merge ft/new-feature
git commit -m"Chrore: merges from ft/new-feature"
git branch -d ft/new-feature
```
### 6. Creating a Branch from a Commit:
* creating branch that have content as the commit changes specified
```bash
git log --oneline
git branch -b ft/new-branch-from-commit <commit-hash>
```
### 7. Branch Merging:
* merging changes from ft/new-branch-from-commit into dev and resolve conflicts if exist
```bash
git checkout dev
git merge ft/new-branch-from-commit
```
### 8. Branch Rebasing
* git rebase moves your branch's commmits on top of anothre brnach
* unlike as a merge this can not create a commit
```bash
git checkout ft/new-branch-from-commit
git rebase dev
```
### 9. Renaming Branches
*  Let's rename ft/new-branch-from-commit to ft/improved-branch-name
```bash
git branch -m ft/new-branch-from-commit ft/improved-branch-name
```
### 10. Checking Out Detached HEAD
* Let use checkout from a specific commit
```bash
git log --oneline
git checkout <commit-hash>
```
## Part 3:Advanced Workflows
### 1. Stashing Changes
* stashing my current changes of dev
```bash
git stash
```
### 2. Retrieving Stashed Changes
* Retrieving the most recent stash into dev
```bash
git stash pop
```
### 3. Branch Merging Conflicts (Continued)
* merging changes from ft/new-branch-from-commit to dev and resolve conflicts in text editor
```bash
git merge origin ft/new-branch-from-commit
```
* Resolve conflicts that arises
### 4. Resolving Merge Conflicts with a Merge Tool
### 5. Understanding Detached HEAD State
### 6. Ignoring Files/Directories
* I created .gitignore file and the path /tmp and then add tmp in .gitignore

### 7. Working with Tags
* I use git tag v1.0 to create a tag named v1.0 on the current commit in your dev branch
```bash
git tag v1.0
```
### 8. Listing and Deleting Tags
* Listing all tags
```bash
git tag
```
* delete a tag
```bash
git tag -d v1.0
```
### 9. Pushing Local Work to Remote Repositories
```bash
git push
```



