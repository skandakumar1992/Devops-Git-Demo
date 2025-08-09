# TASKS — DevOps Git Project (step-by-step)

## Objective
Manage a DevOps project using Git best practices (branches, PRs, README, .gitignore, tags).

## Steps performed
1. Create GitHub repository `devops-git-best-practices`.
2. Initialize local Git repository on `main`:
   - `git init -b main`
   - add `README.md`, `.gitignore`
   - `git commit -m "chore: initial commit"`
3. Add remote and push:
   - `git remote add origin <REMOTE_URL>`
   - `git push -u origin main`
4. Create `dev` branch:
   - `git checkout -b dev`
   - `git push -u origin dev`
5. Create a feature branch from `dev`:
   - `git checkout -b feature/<name>`
   - make changes, `git add`, `git commit -m "feat(...): <desc>"`
   - `git push -u origin feature/<name>`
6. Open PR (feature → dev), review, merge (Squash and merge recommended).
7. Delete the feature branch after merging.
8. When ready, open PR (dev → main), review, merge, then tag release:
   - `git tag -a v0.1.0 -m "Release v0.1.0"`
   - `git push origin v0.1.0`
9. Protect `main` branch via GitHub settings.

## Conventions
- Branch names: `feature/<short>`, `bugfix/<id>`, `hotfix/<desc>`.
- Commit messages follow Conventional Commits: `type(scope?): subject`.
- Pull requests must include description and checklist.

## Helpful commands
- `git status` — see changes
- `git add <file>` — stage
- `git commit -m "msg"` — commit
- `git push` — push
- `git pull` — pull updates
- `git checkout -b <branch>` — create branch
- `git merge <branch>` — merge
- `git tag -a vX.Y.Z -m "message"` — annotate tag
- `git push origin <tag>` — push tag

