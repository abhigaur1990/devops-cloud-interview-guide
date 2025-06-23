## Question  
How do you combine multiple commits into a single commit in Git?

### 📝 Short Explanation  
This question is meant to evaluate your understanding of Git history manipulation — especially around commit hygiene, squashing, and preparing a clean pull request.

## ✅ Answer  
I use **interactive rebase** to squash multiple commits into a single, meaningful commit before pushing my changes. This helps in keeping the Git history clean and easy to read.

### 📘 Detailed Explanation  
Let’s say I made 4 commits while working on a single feature:

```bash
git log --oneline
abc123 Fix typo  
def456 Add input validation  
ghi789 Update error message  
jkl012 Initial work on login form  
```

Before pushing or raising a PR, I might want to **combine them into a single commit** that says something like:  
`Add login form with validation and error handling`

#### ✅ Here’s how I do it:

```bash
We use this command
git rebase -i HEAD~4(4 means number of commits you want put in single commit) like head~3 means top 3 commit.
```so once you press enter

This opens an editor with the last 4 commits:

pick jkl012 Initial work on login form
pick ghi789 Update error message
pick def456 Add input validation
pick abc123 Fix typo
```
The only thing we do is
change pick` to `squash` or `s`:
like as follow
pick jkl012 Initial work on login form
squash ghi789 Update error message
squash def456 Add input validation
squash abc123 Fix typo
```once you save it . Instantly it will ask you for the commit message

Then I write a new commit message when prompted, save, and exit.

Finally:
now chekc by git log and you will see those 4 commits change to one commit.
and then push it to git hub repo by
git push origin branch-name --force
```

> Note: You only force-push if the commits were already pushed to remote. Otherwise, a normal push is fine.

---

### 🧠 Why This Is Useful  
- Keeps Git history clean and easier to understand
- Combines all related changes into one atomic commit
- Helpful for reviewers and future debugging
- Commonly used before merging a feature branch into `main`

> This is often referred to as **squashing commits**, and it's a best practice when preparing PRs or fixing review feedback across multiple small commits.

---
