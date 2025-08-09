# DevOps Git Demo
configure Git with your name/email once:

git config --global user.name "Skanda Kumar"
git config --global user.email "skandakumar192@gmail.com"


Local repo initialized with main branch.

dev branch and one or more feature/* branches.
Proper commits and push to GitHub.
Pull Requests (feature → dev, dev → main).
README.md, .gitignore, tags (v0.1.0), and a TASKS.md documenting everything in Markdown.
Basic PR template for consistent PRs.

Step-by-step (do these in order)

1) Create the repository on GitHub

Using GitHub web:

Log into github.com.
Click New (or + ► New repository).
Repository name: https://github.com/skandakumar1992/Devops-Git-Demo.git.
Set Visibility: Public or Private.
Do not initialize with README (we’ll initialize locally). Click Create repository.
You’ll see the remote URL (HTTPS or SSH). Copy it — you’ll need it later.


2) Initialize local repo and make the initial commit

Open terminal, pick a directory where you want the project, then:

mkdir devops-git-Demo
cd devops-git-Demo

# initialize git with main branch
git init -b main

# create files: README, .gitignore, TASKS.md 
echo "# DevOps Git Best Practices" > README.md
# create a basic .gitignore 
echo "node_modules/" > .gitignore

# stage and commit
git add .
git commit -m "chore: initial commit — add README and .gitignore"
Now connect to the remote you created on GitHub. Replace <REMOTE_URL> with the HTTPS or SSH URL from GitHub:

git remote add origin <https://github.com/skandakumar1992/Devops-Git-Demo.git>
git branch -M main
git push -u origin main

3) Create dev branch (integration) and push

git checkout -b dev        
git push -u origin dev     

4) Create a feature branch, work, commit, push
Naming convention: feature/<short-description> or feat/<short>. Example feature:

git checkout dev                    
git pull origin dev                 
git checkout -b feature/add-readme-section

# edit README.md (add a short section). Then:
git add README.md
git commit -m "feat(readme): add usage section"
git push -u origin feature/add-readme-section

5) Open a Pull Request (PR) — feature → dev

On GitHub web

Go to the repo > “Compare & pull request” (you’ll often see a banner) or go to Pull requests → New pull request.
Base branch: dev | Compare : feature/add-readme-section.
Title: feat(readme): add usage section
In PR description use a checklist (example template included below).
Click Create pull request.

6) Review, request changes, and merge the PR

Reviewer(s) add comments or request changes on GitHub.
When ready, merge options: Squash and merge (recommended for tidy history), Rebase and merge, or Create a merge commit.
After merging, delete the remote feature branch via the GitHub UI (button) or:

git push origin --delete feature/add-readme-section
git checkout dev
git pull origin dev
git branch -d feature/add-readme-section

7) Promote dev → main via PR (release)

When dev is stable:
Open PR: base = main, compare = dev.
Use a meaningful title: chore(release): merge dev into main for v0.1.0.
Merge once checks pass and at least one review approves.
Optionally create a tag for the release (next step).

8) Tagging releases (Semantic versioning)

Create an annotated tag and push it:
git checkout main
git pull origin main
git tag -a v0.1.0 -m "Release v0.1.0 — baseline"
git push origin v0.1.0
git tag -l

You can create GitHub Releases from the tag on the website (Release -> Draft a new release).

9) Protect the main branch (recommended on GitHub)

On GitHub: Settings → Branches → Add branch protection rule for main. Recommended settings:
Require pull requests before merging.
Require at least one approving review.
Require status checks to pass (if you add CI later).
Do not allow force pushes.
