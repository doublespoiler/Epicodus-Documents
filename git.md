# **Git  cheatsheet**

- [[#git commands|git commands]]
- [[#Creating a new Project|Creating a new Project]]
- [[#Merge checklist|Merge checklist]]
- [[#Push Checklist|Push Checklist]]
- [[#Clone Checklist|Clone Checklist]]
- [[#Default .gitignore_global|Default .gitignore_global]]

## git commands

| command               | description                                     | example             | notes                    |
| --------------------- | ----------------------------------------------- | ------------------- | ------------------------ |
| init                  | initialize new git repo                         | git init            |                          |
| status                | gets tracking status                            | git status          |                          |
| clone                 | clone repository from URL                       | clone URL           |                          |
| commit                | commit changes in tracked (added) files         | commit -m "NOTE"    |                          |
| log                   | prints commit log                               |                     | PRESS Q TO QUIT IF STUCK |
| remote                | for dealing with remotes                        | remote add NICK URL |                          |
| remote -v             | prints all remotes                              |                     |                          |
| remote remove NICK    | removes remote                                  |                     |                          |
| branch                | displays all branches                           |                     |                          |
| branch BRANCHNAME     | creates new branch from current with BRANCHNAME |                     |                          |
| branch -m master main | changes master branch to main instead           |                     |                          |
| checkout              | checkout branches to mess with                  |                     |                          |
| merge                 | merge current branch with defined branch        | merge BRANCHNAME    |                          |
|                       |                                                 |                     |                          |

## Creating a new Project
1. Create the repository on GitHub
2. Create project folder on your computer
3. *INIT*ialize Git inside the project folder (git init)
4. *ADD* files/folders for git to track (git add FILENAME)
5. *COMMIT* your changes (git commit -m "MESSAGE")
6. Add *REMOTE* (git remote add NICK URL)
7. *PUSH* your code! (git push NICK main)
**You must choose which files to commit with (git add)** 

## Merge checklist
* If we have conflicts, we can't merge!
* TBD

## Push Checklist
* TBD

## Clone Checklist
* tbd

## Default .gitignore_global
cd ~ <br>
touch .gitignore_global <br>
code .gitignore_global <br>
git config --global core.excludesfile ~/.gitignore_global <br>

    # OS generated files # 
    ###################### 
    .DS_Store 
    .DS_Store? 
    ._* 
    .Spotlight-V100 
    .Trashes 
    ehthumbs.db 
    Thumbs.db