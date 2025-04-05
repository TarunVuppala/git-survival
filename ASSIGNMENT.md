# Git Survival

This repository documents my journey through a series of Git challenges designed to simulate real-world disasters. Below is a summary of each assignment (1 through 10), including the commands I ran and the final deliverables (commit logs, remote info) from my Git history.

---

## Assignment 1: "I Forgot to Track This" Crisis

**Task:**  
Initialize a Git repository for an existing project.

**Solution:**  
1. Created the project folder and added a `README.md` with "I’m already screwed."  
2. Ran:
   ```bash
   git init
   git add README.md
   git commit -m "Initial commit, losers"
   ```

**Deliverable (Commit Log Snippet):**
```
9b0fd0f (HEAD -> master) Initial commit, losers
```

---

## Assignment 2: "Boss Wants It Split Up" Drama

**Task:**  
Commit file updates separately.

**Solution:**  
1. Updated `README.md` to say "I’m still screwed."  
2. Created `todo.txt` with "Fix everything."  
3. Committed each change separately:
   ```bash
   git add README.md
   git commit -m "Update readme, ugh"

   git add todo.txt
   git commit -m "Add todo, whatever"
   ```

**Deliverables (Commit Log Snippets):**
```
af8df0c (HEAD -> master) Add todo, whatever
d15364b Update readme, ugh
```

---

## Assignment 3: "Switch Branches, Oh Crap" Panic

**Task:**  
Manage uncommitted changes when switching branches.

**Solution:**  
1. Made an uncommitted change in `todo.txt`.  
2. Created (or switched to) the `feature` branch:
   ```bash
   git checkout -b feature
   ```
3. Stashed the change, switched (or stayed) on `feature`, then reapplied and committed:
   ```bash
   git stash
   git stash pop
   git add todo.txt
   git commit -m "Saved my bacon"
   ```

**Deliverable (Commit Log Snippet):**
```
a366e21 (HEAD -> feature) Saved my bacon
```

---

## Assignment 4: "Client Wants It Online" Rush

**Task:**  
Publish the local repo to GitHub.

**Solution:**  
1. Created a GitHub repository named `git-survival`.  
2. Linked the local repo to GitHub and pushed:
   ```bash
   git remote add origin https://github.com/TarunVuppala/git-survival
   git push -u origin master
   ```

**Deliverable (GitHub URL):**
```
https://github.com/TarunVuppala/git-survival
```

---

## Assignment 5: "Feature Creep" Branch Fiasco

**Task:**  
Work on a new feature in a separate branch and merge it into `master`.

**Solution:**  
1. Created a `feature` branch, added `coolstuff.txt` with "This better work," and committed:
   ```bash
   git checkout -b feature
   echo "This better work" > coolstuff.txt
   git add coolstuff.txt
   git commit -m "Add coolstuff feature"
   ```
2. Merged the feature branch into `master` and pushed:
   ```bash
   git checkout master
   git merge feature
   git push
   ```

**Deliverable (Commit Log Snippet):**
```
88ec285 (HEAD -> master, origin/master, feature) Add coolstuff feature
```

---

## Assignment 6: "Steal Their Code" Fork Debacle

**Task:**  
Fork an external repository, track upstream changes, and merge updates.

**Solution:**  
1. Forked `octocat/Spoon-Knife`, cloned it, and added the upstream remote:
   ```bash
   git clone https://github.com/TarunVuppala/Spoon-Knife.git
   cd Spoon-Knife
   git remote add upstream https://github.com/octocat/Spoon-Knife.git
   ```
2. Fetched and merged updates from upstream:
   ```bash
   git fetch upstream
   git merge upstream/master
   ```

**Deliverable (Remote Info):**
```
D:\code\Spoon-Knife> git remote -v
origin  git@github.com:TarunVuppala/Spoon-Knife.git (fetch)
origin  git@github.com:TarunVuppala/Spoon-Knife.git (push)
upstream        https://github.com/octocat/Spoon-Knife.git (fetch)
upstream        https://github.com/octocat/Spoon-Knife.git (push)
```

---

## Assignment 8: "Reviewer Hates Your History" Rewrite

**Task:**  
Clean up a messy commit history using interactive rebase.

**Solution:**  
1. On the `bugfix` branch, after adding extra commits, used interactive rebase to squash them into one.  
2. Force-pushed the updated history.

**Deliverable (Commit Log Snippet):**
```
55540ce (HEAD -> master, origin/master) Oops
```

---

## Assignment 9: "Merge Conflict Hell" Showdown

**Task:**  
Resolve a merge conflict caused by divergent changes in the same file.

**Solution:**  
1. On `master`, updated `README.md` to "I’m the best" and committed.  
2. On `feature`, changed `README.md` to "No, I’m the best" and committed.  
3. Merged `feature` into `master`, resolved the conflict by editing `README.md` to "We’re both the best, ugh," then committed:
   ```bash
   git checkout master
   git merge feature
   # Resolve conflict in README.md
   git add README.md
   git commit -m "Merge conflict resolved: Were both the best, ugh"
   ```

**Deliverables (Commit Log Snippets):**
```
85bf9a1 (HEAD -> master, origin/master) Merge conflict resolved: Were both the best, ugh
a7109f8 (feature) Feature: No, Im the best
493a343 master: Im the best
```

---

## Assignment 10: "I Screwed Up, Now What?" Recovery

**Task:**  
Rebase the experiment branch, then reset it to the first commit.

**Solution:**  
1. Created an `experiment` branch off `master`:
   ```bash
   git checkout master
   git checkout -b experiment
   ```
2. Made three commits to `todo.txt`:
   ```bash
   echo "Try this" >> todo.txt
   git add todo.txt
   git commit -m "Try this"

   echo "Nope" >> todo.txt
   git add todo.txt
   git commit -m "Nope"

   echo "Maybe" >> todo.txt
   git add todo.txt
   git commit -m "Maybe"
   ```
3. Rebased onto `master` and then reset to the first commit:
   ```bash
   git rebase master 64e3063
   git reset --hard 
   git push -f origin experiment
   ```

**Deliverables (Commit Log Snippets):**
```
ec03901 (HEAD -> experiment) Maybe
2dda7d6 Nope
64e3063 Try this
```