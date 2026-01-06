---
title: 'Git: Useful commands'
date: '2025-12-23'
---

## New project

Suppose I want to start a new project, with a new local folder, and a new GitHub repository.
- Create a new repository in GitHub. 
  - I will call it test-git. 
  - Make it public and add nothing to it, so it is empty.
- Change the working directory to a local folder that I wish to put the local project, e.g., `C:\test_git`.
- Create a markdown file called `README.md` and add some description.
- Open a new terminal (Git Bash or VSCode terminal), and type in the following commands as GitHub suggests.
- Check if the `README.md` file has been uploaded to your GitHub repository.

```powershell
git init
git add README.md
git commit -m "Add the README.md file"
git branch -M main
git remote add origin git@github.com:your_github_account/test-git.git
git remote -v
git push -u origin main
```

## Record changes and upload them to GitHub repository

```powershell
git status
git add test.do
git commit -m "Add the test.do file"
git push origin main
```

Sometimes, you may wish to push changes using another GitHub account. It is possible to achieve this by setting up username and email locally.

```powershell
git config user.name econnotes
git config user.email econ.learning.resources@gmail.com
```

## Pull changes from an online GitHub repository

```powershell
git remote add upstream https://github.com/your_github_account/another
git fetch upstream
git merge upstream/main

git fetch origin
git fetch origin/main

git commit
git push origin 
```

## Make changes in a new branch

```powershell
git branch testing1
git checkout testing1

git checkout -b testing2

git checkout main 
git merge testing2
git branch -d testing2
```

## Go back to a previous version and make changes

- Using the VSCode extension `Git Graph` to manually compare two versions of commits, or past versions with current version is often enough for my needs.