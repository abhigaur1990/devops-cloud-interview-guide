## Question  
Explain a recent challenge you faced with Git and how you addressed it.
The challenges I faced was
 Access control:-

 When I joined the project there was access control issue which was not well defined.
 ex:-every developr was able to create on git hub repo .
 So because they were able to create branches. Number of CI/CD pipelines were running.
 It was costing the organization. And aprt from.
 Maintaining the branches was out of control.
 So when I joined the project there was almost more than 100 branchex created on git rep.
 Apart from this. There was many branches that were not in use.
 SO as per the process I started defining Role based access control.
 Like I defined read control access, write role like who can create branches, who can view code etc.
 I also created maintain acess who can maintain repo.
 So this process removed all mess up issue.
And I got appreciation on this.
### 📝 Short Explanation  
This question is intended to assess your experience with Git at scale — especially around collaborative processes and governance. It’s an opportunity to demonstrate how you bring structure to complex codebases across teams.

## ✅ Answer  
A recent challenge I faced was implementing a consistent Git branching strategy across 100+ repositories used by multiple teams in my organization. Each team followed their own style — some had `main/dev`, others used `master/feature`, and a few used no long-lived branches at all. This inconsistency made CI/CD pipelines error-prone, releases chaotic, and collaboration difficult.

To solve this, we standardized on a lightweight **trunk-based branching strategy** with well-defined rules around `main`, `release/*`, and `feature/*` branches — and rolled it out in phases across teams.

### 📘 Detailed Explanation  
At a company-wide level, multiple teams were independently managing Git repos, and the lack of a unified branching approach caused several issues:
- CI pipelines were failing due to missing expected branches like `main` or `release`.
- Some teams rebased public branches, which broke collaborators' work.
- Merge conflicts were common in integration environments.
- Releases were often delayed due to confusion about which branch was production-ready.

Here’s how I addressed it:

#### ✅ Step 1: Analyze the current state
- Audited all repositories using automation (GitHub/GitLab APIs).
- Documented the branching models and naming conventions each team used.

#### ✅ Step 2: Design a unified strategy
- Proposed a **trunk-based development** model:
  - `main` → always production-ready
  - `release/x.y` → for stabilization and hotfixes
  - `feature/*` → short-lived, rebased before merge
- Outlined rules for using `merge`, `rebase`, and protection policies.

#### ✅ Step 3: Rollout with tooling & education
- Created templates (starter repos) with the correct branch structure.
- Set up default branch protections and PR requirements using GitHub Actions and branch policies.
- Ran onboarding sessions and created a lightweight Git handbook tailored to our strategy.

#### ✅ Step 4: Iterate with feedback
- Incorporated feedback from platform, dev, and QA teams.
- Adjusted the policy to allow for temporary exceptions during migration.

---

The result was:
- 95%+ repos aligned within 2 months.
- CI/CD pipeline reliability improved significantly.
- Teams were clearer on how and when to branch or merge.
- It became easier to onboard new developers and automate release workflows.

---
