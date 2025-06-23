## Question  
What is the difference between `git fetch` and `git pull`, and when would you use each?

### 📝 Short Explanation  
This question checks if you understand how Git handles remote updates. Many developers use `git pull` out of habit but don’t realize that it’s a combination of two actions — which `git fetch` separates for more control.

## ✅ Answer  
- `git fetch` retrieves the latest changes like commits, updated branches, tags from the remote repository and update them on to the .git into your local machine like **without merging** them into your current branch and if you find no changes required and all good then you can do git merge or git rebase and updated the changes to your local repo of machine.
- `git pull` does the same as `fetch` but **also automatically merges** the changes into your current branch.
- It does entire same thing in one command.
- Git pull can be considered as git pull + git merge

### 📘 Detailed Explanation  
When you run `git fetch`, you’re asking Git to contact the remote (like GitHub) and download any changes (new commits, branches, tags) — **but not apply them** to your working directory.

```bash
git fetch origin
```

This is useful when:
- You want to see what others have pushed
- You're preparing for a manual merge or rebase
- You want to avoid surprise changes to your working branch

With `git pull`, you're doing this **plus** merging the changes into your current branch in one step:

```bash
git pull origin main
```

That’s shorthand for:
```bash
git fetch origin
git merge origin/main
```

While `git pull` is faster, it can cause **unintended merges** if you’re not ready. That’s why many teams prefer doing `fetch` first, reviewing the changes, and then merging or rebasing manually.

> Summary:  
> Use `git fetch` when you want control.  
> Use `git pull` when you’re ready to sync changes directly.

---
