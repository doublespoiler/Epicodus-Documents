Git commands cheatsheet

config --global user.name/user.email "name"/email

init                       - Initialize new Git repository
status                     - Gets status
add FILENAME               - Adds file for Git to track
clone URL                  - Clone repository at URL
commit -m "comment"        - Commits, with comment
log                        - Shows log of commits
remote add NICK URL        - Stores information about remote repository NICKNAME at URL
remote -v                  - shows all the remotes stored in Git for this project
push NICK main             - Pushes code to the remote nicknamed NICK from the main branch
branch BRANCHNAME          - Check branches, OR create new branch with BRANCHNAME
checkout BRANCHNAME        - Switch to branch BRANCHNAMEs
merge BRANCHNAME           - Merge branch BRANCHNAME onto the branch you are currently on



Arguments
-m - message
-v 
-M - This branch
--oneline - shows git log in condensed format

Creating a new Project
1. Create the repository on GitHub
2. Create project folder on your computer
3. INITialize Git inside the project folder (git init)
4. ADD files/folders for git to track (git add FILENAME)
5. COMMIT your changes (git commit -m "MESSAGE")
6. Add REMOTE (git remote add NICK URL)
7. PUSH your code! (git push NICK main)

You must choose which files to commit with (git add) 
