## Question  
Explain three challenges you faced while using Git in your work experience.

I faced git branching strategy issue.
When I was in the company and switched to the project. 
There was no branching startegy followed. People were creating random branches in their own way.
So I intorduced trunk based branches accor to organization startegy.
It was near suitable for us.
So as per trunk based branched
1st I created main branch where all developers created and updated code.
Features:- Some developers works on features branch.
Realease branch:- Since we had 2 month ready cycle for feature branch so we created release branch
and at last hotflix for any issue occur in production.

### 📝 Short Explanation  
This question is aimed at evaluating real-world Git usage and how well you’ve handled common pain points like collaboration, history management, and contribution workflows. It gives the interviewer insight into how deeply you've worked with Git in a team setting.

## ✅ Answer  
1. **Merge Conflicts During Pulls**  
   I used to rely heavily on `git pull` without checking what changes others had pushed. This led to merge conflicts, especially in fast-moving branches. Eventually, I switched to using `git fetch` followed by a manual `merge` or `rebase`, which gave me more control over how I integrated changes.

2. **Messy Commit History with Frequent Merges**  
   Early in my career, I used `git merge` frequently while working on long-lived feature branches. It cluttered the history with multiple merge commits, making it difficult to follow the actual changes. I learned to use `git rebase` (before pushing) to create a clean, linear history — especially before opening pull requests.

3. **Confusion Between Fork and Clone in Open-Source Work**  
   When I first started contributing to open-source, I cloned repositories directly and couldn’t push my changes. I realized I should’ve used `git fork` to create my own copy of the repo on GitHub. After forking, I was able to push changes to my own version and submit pull requests to the original repository.

### 📘 Detailed Explanation  
These challenges reflect how Git is powerful but not always beginner-friendly:
- **Merge conflicts** are a common problem in collaborative teams. Using `git fetch` and reviewing changes before merging helped me avoid surprise conflicts.
- **Messy commit history** can make debugging or code reviews painful. Switching to `rebase` in local branches before pushing made the history easier for teammates to follow.
- **Forking confusion** taught me about GitHub’s collaboration model. Understanding when to fork vs when to clone was key to contributing effectively to open-source.

---
