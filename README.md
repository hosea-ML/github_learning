# Git & GitHub Learning Journey

A practical, step-by-step repository documenting my journey of learning **Git and GitHub from the fundamentals to real-world development workflows**.

This repository is not just a collection of Git commands. It is a practical learning environment where I experiment with repositories, commits, branches, remote repositories, Pull Requests, merges, merge conflicts, and other essential Git concepts.

The goal is that another beginner can clone this repository, read this README, and understand not only **what commands to use**, but also **why and when to use them**.

---

## Table of Contents

- [1. What is Git?](#1-what-is-git)
- [2. What is GitHub?](#2-what-is-github)
- [3. Git vs GitHub](#3-git-vs-github)
- [4. Repository](#4-repository)
- [5. Local vs Remote Repository](#5-local-vs-remote-repository)
- [6. Basic Git Workflow](#6-basic-git-workflow)
- [7. Creating a Git Repository](#7-creating-a-git-repository)
- [8. Git Status](#8-git-status)
- [9. Git Add and the Staging Area](#9-git-add-and-the-staging-area)
- [10. Git Diff](#10-git-diff)
- [11. Git Commit](#11-git-commit)
- [12. Git Push](#12-git-push)
- [13. Git Pull](#13-git-pull)
- [14. Git Fetch](#14-git-fetch)
- [15. Branches](#15-branches)
- [16. Feature Branch Workflow](#16-feature-branch-workflow)
- [17. Local and Remote Branches](#17-local-and-remote-branches)
- [18. Pull Requests](#18-pull-requests)
- [19. Merging](#19-merging)
- [20. Merge Conflicts](#20-merge-conflicts)
- [21. Resolving Merge Conflicts](#21-resolving-merge-conflicts)
- [22. Git History](#22-git-history)
- [23. Git Show](#23-git-show)
- [24. Undoing Changes](#24-undoing-changes)
- [25. Important Git Concepts](#25-important-git-concepts)
- [26. Commands Cheat Sheet](#26-commands-cheat-sheet)
- [27. Practical Workflow](#27-practical-workflow)
- [28. Lessons Learned](#28-lessons-learned)
- [29. Next Topics](#29-next-topics)

---

# 1. What is Git?

**Git is a distributed version control system.**

It allows developers to track changes made to files over time.

Instead of having:

```text
project-final
project-final-2
project-final-new
project-final-new-real
project-final-new-real-v2

Git allows us to maintain a structured history of changes.
For example:
Initial commit
      ↓
Add login system
      ↓
Fix login bug
      ↓
Add authentication
      ↓
Improve error handling

Each saved version is represented by a commit.
Git also allows developers to:
- work on different features independently
- return to previous versions
- compare changes
- collaborate with other developers
- merge different lines of development
- recover from mistakes

# 2. What is GitHub?
GitHub is a platform for hosting Git repositories online.
Git operates primarily on my computer.
GitHub provides a remote location where Git repositories can be stored and shared.
For example:
My Computer
     │
     │ Git
     ▼
Local Repository
     │
     │ git push
     ▼
GitHub
     │
     ▼
Remote Repository

Git and GitHub are therefore related, but they are not the same thing.
3. Git vs GitHub
Git	GitHub
Version control system	Hosting and collaboration platform
Runs locally	Runs online
Tracks file history	Hosts Git repositories
Creates commits	Stores remote commits
Creates branches	Provides remote branches
Can work without internet	Requires internet for remote collaboration
Command-line tool	Web-based platform + Git integration


A simple way to remember:
Git manages the history. GitHub hosts and helps collaborate on that history.

4. Repository
A repository, often called a repo, is a project managed by Git.
A repository contains:
- project files
- Git history
- commits
- branches
- configuration information
When I created this learning project, I initialized Git with:
git init

This created the hidden .git directory.
The .git directory contains the information Git needs to manage the repository.
5. Local vs Remote Repository
There are two important copies of a Git project:
Local repository
The repository on my computer.
C:\Users\Hosea\hosea-ML_github\github_learning

Remote repository
The repository hosted on GitHub.
The remote is named:
origin

The relationship is:
LOCAL REPOSITORY
       │
       │ git push
       ▼
GITHUB REMOTE
       │
       │ git pull
       ▼
LOCAL REPOSITORY

6. Basic Git Workflow
The fundamental Git workflow is:
Edit
  ↓
git status
  ↓
git add
  ↓
git diff --staged
  ↓
git commit
  ↓
git push

For remote changes:
GitHub
  ↓
git fetch / git pull
  ↓
Local repository

7. Creating a Git Repository
To turn a normal project folder into a Git repository:
git init

Example:
mkdir github_learning
cd github_learning
git init

Git responds with a message indicating that an empty Git repository has been initialized.
After this, Git begins tracking the project.
8. Git Status
One of the most important commands is:
git status

It tells me the current state of my repository.
It can tell me:
- which branch I am on
- whether files have changed
- which files are staged
- which files are not staged
- whether my branch is ahead of or behind GitHub
- whether a merge is in progress
- whether my working tree is clean
Example:
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

A useful way to think about git status:
Git status is my Git dashboard.

9. Git Add and the Staging Area
When I modify a file, the change initially exists in the working directory.
Example:
git add app.py

moves the change into the staging area.
The Git workflow is therefore:
Working Directory
       │
       │ git add
       ▼
Staging Area
       │
       │ git commit
       ▼
Git Repository

The staging area is useful because I can decide exactly which changes should be included in the next commit.
For example:
git add app.py

stages only app.py.
I can also stage everything:
git add .

10. Git Diff
git diff shows changes that have not been staged.
git diff

Conceptually:
Working Directory
       ↓
git diff
       ↓
Unstaged changes

To see changes that have already been staged:
git diff --staged

Therefore:
git diff
    ↓
Changes NOT staged

git diff --staged
    ↓
Changes already staged

11. Git Commit
A commit saves a version of the project in the local Git repository.
Example:
git commit -m "Add user age information"

A commit contains information such as:
- commit message
- author
- timestamp
- snapshot of relevant changes
- unique commit hash
Example:
c5005db Add user age information

The commit hash uniquely identifies that commit.
Important:
A commit is local until it is pushed to a remote repository.

12. Git Push
git push sends local commits to a remote repository.
Example:
git push

For a new branch:
git push -u origin feature/user-info

The structure is:
git push <remote> <branch>

For example:
git push origin feature/user-info
          │        │
          │        └── branch
          └────────── remote

The -u option establishes upstream tracking.
After that, future pushes can usually be done with:
git push

13. Git Pull
git pull gets changes from the remote repository and integrates them into the current local branch.
Example:
git switch main
git pull

A common situation is:
GitHub main
     │
     │ new changes
     ▼
Local main
     │
     │ git pull
     ▼
Updated local main

After a Pull Request is merged on GitHub, I normally update my local main with:
git switch main
git pull

14. Git Fetch
git fetch checks for new information from the remote repository without immediately integrating it into my current branch.
Example:
git fetch origin

It updates Git's knowledge of the remote repository.
A simple distinction:
git fetch
    ↓
"Tell me what changed on GitHub."

git pull
    ↓
"Get the changes and update my current branch."

15. Branches
A branch is an independent line of development.
Instead of making changes directly on main, I can create a feature branch:
git switch -c feature/user-info

This creates and switches to the new branch.
Example:
main
 │
 └── feature/user-info

The feature branch can now develop independently.
16. Feature Branch Workflow
A typical development workflow is:
main
 │
 │
 ├──── feature/my-feature
 │             │
 │             ├── change
 │             ├── commit
 │             └── commit
 │
 │             git push
 │                  │
 │                  ▼
 │               GitHub
 │                  │
 │             Pull Request
 │                  │
 │                Review
 │                  │
 │                Merge
 │                  ▼
 └──────────────── main

Typical commands:
git switch main
git pull
git switch -c feature/my-feature

# Make changes

git add .
git commit -m "Add my feature"
git push -u origin feature/my-feature

Then create a Pull Request on GitHub.
17. Local and Remote Branches
A branch can exist locally and remotely.
For example:
Local:
feature/user-info

Remote:
origin/feature/user-info

origin is the name of the GitHub remote.
To see local branches:
git branch

To see remote branches:
git branch -r

To see both:
git branch -a

18. Pull Requests
A Pull Request (PR) is a request to merge changes from one branch into another.
For example:
feature/user-info
        │
        │ Pull Request
        ▼
       main

A Pull Request allows developers to:
- review code
- discuss changes
- identify problems
- run automated checks
- approve changes
- request modifications
- merge the feature
A Pull Request is therefore more than simply "uploading code."
It is a code review and collaboration workflow.
19. Merging
Merging combines changes from one branch into another.
Example:
git switch main
git merge feature/user-info

If Git can combine the changes automatically, the merge succeeds.
GitHub can also perform the merge through a Pull Request.
20. Merge Conflicts
A merge conflict occurs when Git cannot automatically determine how two sets of changes should be combined.
A common example:
main
 │
 ├── feature/conflict-a
 │       │
 │       └── changes line X
 │
 └── feature/conflict-b
         │
         └── changes line X differently

If both branches modify the same part of the same file differently, Git may report:
CONFLICT (content): Merge conflict in app.py

This does not mean the repository is broken.
It means:
Git needs a human to decide what the final code should be.

21. Resolving Merge Conflicts
When a conflict occurs, Git places conflict markers in the file.
Example:
<<<<<<< HEAD
Version from current branch
=======
Version from branch being merged
>>>>>>> feature/conflict-b

The sections mean:
<<<<<<< HEAD
Current branch version

=======

Incoming branch version

>>>>>>> feature/conflict-b

I manually decide what the final code should be.
After fixing the file:
git add app.py

Then:
git commit -m "Resolve merge conflict"

The general conflict-resolution workflow is:
git merge
    ↓
CONFLICT
    ↓
Open conflicting file
    ↓
Decide final code
    ↓
Remove conflict markers
    ↓
git add
    ↓
git commit

22. Git History
Git keeps a history of commits.
A simple history:
git log

A compact version:
git log --oneline

A visual version:
git log --oneline --decorate --graph --all

The graph is particularly useful for understanding branches and merges.
Example:
*   Merge commit
|\
| * Feature commit
* | Main commit
|/
* Previous commit

23. Git Show
git show allows me to inspect a particular commit.
For example:
git show HEAD

HEAD means:
The commit I am currently on.

To see a summary:
git show --stat HEAD

Useful distinction:
git log
    ↓
"What commits exist?"

git show
    ↓
"What did this commit change?"

24. Undoing Changes
Git has several ways to undo things.
They should not be confused.
git restore
Used mainly to discard uncommitted changes.
git restore app.py

This restores the file to its last committed state.
git restore --staged
Used to remove a file from the staging area without deleting its modifications.
git restore --staged app.py

Conceptually:
Staging Area
     │
     │ git restore --staged
     ▼
Working Directory

git reset
Moves the current branch/HEAD to another commit.
Example:
git reset --hard HEAD~1

reset --hard can discard work, so it should be used carefully.
git revert
Creates a new commit that reverses the effect of an earlier commit.
Example:
git revert <commit-hash>

This is generally safer for commits that have already been shared with others.
Conceptually:
A → B → C → D
          ↑
      bad commit

git revert C

A → B → C → D
              ↓
           undo C

The original history remains.

25. Important Git Concepts
HEAD
HEAD represents where I am currently positioned in Git's history.
For example:
HEAD -> main

means I am currently on main.
origin
origin is the conventional name assigned to the remote GitHub repository.
For example:
origin/main

means the remote-tracking reference for GitHub's main branch.
Working Directory
The actual files I am currently editing.
app.py
README.md

Staging Area
The changes selected for the next commit.
git add

moves changes into the staging area.
Local Repository
The Git history stored on my computer.
commits
branches
history

Remote Repository
The repository hosted on GitHub.

26. Commands Cheat Sheet
Repository
git init
git clone <url>

Status and information
git status
git log
git log --oneline
git log --oneline --decorate --graph --all
git branch
git branch -a

Changes
git diff
git diff --staged

Staging
git add <file>
git add .
git restore --staged <file>

Commits
git commit -m "Message"
git commit --amend -m "New message"
git show <commit>
git show --stat <commit>

Remote
git remote -v
git remote add origin <url>
git fetch origin
git pull
git push

Branches
git branch
git switch main
git switch -c feature/name
git branch -d feature/name

Merging
git merge <branch>

Conflict resolution
git status
# manually fix conflicts
git add <file>
git commit

Undo
git restore <file>
git restore --staged <file>
git reset
git revert <commit>

27. Practical Workflow
For normal feature development:
# Start from an updated main
git switch main
git pull

# Create feature branch
git switch -c feature/my-feature

# Make changes

# Check changes
git status
git diff

# Stage
git add .

# Review staged changes
git diff --staged

# Commit
git commit -m "Add my feature"

# Upload branch to GitHub
git push -u origin feature/my-feature

Then:
GitHub
   ↓
Pull Request
   ↓
Code Review
   ↓
Approval
   ↓
Merge

After the Pull Request is merged:
git switch main
git pull

Now the local main contains the merged changes.

28. Lessons Learned
Through this practical project, I have learned that Git is not simply about memorizing commands.

The most important concepts I have learned are:
## 1. Commit and push are different
git commit
    ↓
Save changes locally

git push
    ↓
Send commits to GitHub

A commit does not automatically appear on GitHub.

## 2. Branches provide isolated development
I can create a feature branch without disturbing main.
main
 │
 └── feature/my-feature

## 3. Pull Requests are collaboration tools
A Pull Request allows code to be reviewed before it becomes part of main.

## 4. git pull and git fetch are different
git fetch
    ↓
Update knowledge of remote changes

git pull
    ↓
Fetch + integrate changes

## 5. Merge conflicts are normal
A conflict does not mean Git failed.
It means:
Git needs the developer to decide which code should remain.

## 6. The staging area matters
Git provides an intermediate step between editing and committing:
Working Directory
       ↓
   git add
       ↓
Staging Area
       ↓
  git commit
       ↓
Git Repository

This allows precise control over what goes into a commit.

29. Next Topics
The next topics I plan to explore include:
- [ ] .gitignore
- [ ] Git tags
- [ ] GitHub Issues
- [ ] GitHub Discussions
- [ ] Releases
- [ ] GitHub Actions
- [ ] Forks
- [ ] Working with upstream repositories
- [ ] Rebasing
- [ ] Interactive rebase
- [ ] Cherry-pick
- [ ] Stashing
- [ ] Remote tracking
- [ ] SSH authentication
- [ ] GitHub project collaboration
- [ ] Conventional commit messages
- [ ] Professional Git workflows
- [ ] Git workflows for data science and machine learning projects

## My Learning Philosophy
I am learning Git and GitHub through practical experimentation rather than memorizing commands.
Every concept in this repository is practiced through an actual Git workflow.
The goal is to understand:
What is Git doing? Why is it doing it? What problem does the command solve? And what happens to my project after I run it?

## Author
Adebayo Oluwabusola
Marine Geoscientist | Data Science & Machine Learning | Geospatial & Coastal Intelligence
GitHub: @hosea-ML

## Repository Purpose
This repository is a continuously evolving learning project.
As I learn new Git and GitHub concepts, I will update this README and add practical examples demonstrating them.
Learning by doing. One commit at a time. 🚀