---
title: 'Git: Installation'
date: '2025-12-24'
---

## Download and Install

- Download from here: https://git-scm.com/downloads.
- Suggestions on different installation options: https://gist.github.com/bhagatabhijeet/e08bec472c1a7ee9fb5414b3192b0d3b.

## Set up Git with `git config`

- Open Git Bash.
- Setting up some basic information following instructions here: https://pslmodels.github.io/Git-Tutorial/content/using/git_config.html.

```git
git config --list --show-origin
git config --global user.name "my_name"
git config --global user.email my_email@gmail.com
```

## Create a GitHub Account and Connect Git and GitHub

-  Make sure that the name of the account is meaningful.
- There are many ways to connect Git with GitHub. See the general overview here: https://docs.github.com/en/get-started/git-basics/set-up-git. 
-  In what follows, I will connect to GitHub over SSH. 
  - Check if there is an existing SSH key in the laptop. 
    - The reference for this step is here: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys. 
    - In the Git Bash command line terminal, type the following command: `ls -al ~/.ssh`. 
    - If the result is "No such file or directory", then move to the next step.
    - If there is, then skip step 2, and directly to step 3 (i.e., using the existing SSH key). Or you can delete the folder containing the SSH key.
  - Generate a SSH key.
    - The reference for this step is here: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent.
    - Type the following command in Git Bash: `ssh-keygen -t ed25519 -C "my_email@gmail.com"`.
    - Press `Enter` so that the default location is used to store the SSH key.
    - Enter my own password twice to finally secure the SSH key you generated.
  - Add the SSH key to your local machine.
    - Make sure ssh-agent is running. 
    - Open the Windows bash as administrator. And then type the "Run as administrator" commands.
    - Type the "Add to path" command in Git Bash: Notice that the specific location where the key is stored should be replaced with yours.
  - Add the SSH key to your GitHub account.
    - The reference for this step is here: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account.
    - This step is very simple. You just open the `id_ed25519.pub` file and copy it into your GitHub setting. The link above is very clear.


```bash {name="Run as administrator"}
Get-Service -Name ssh-agent | Set-Service -StartupType Manual
Start-Service ssh-agent
```
```bash {name="Add to path"}
ssh-add my_path_to_ssh/.ssh/id_ed25519 
```