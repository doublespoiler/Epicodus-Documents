# Git  cheatsheet


## git commands
<table>
  <tr>
    <td>Command</td>
    <td>Description</td>
    <td>Notes/example</td>
  </tr>
  <tr>
    <td>config --global</td>
    <td>In case your global config gets messed up</td>
    <td>config --global user.name "name" <br> config --global user.email "email" <br> config --global core.editor "code --wait" <br> config --global init.defaultBranch main <br> config --global color.ui true</td>
  </tr>
  <tr>
    <td>init</td>
    <td>Initialize new git repository</td>
    <td></td>
  </tr>
  <tr>
    <td>status</td>
    <td>Gets tracking status</td>
    <td></td>
  </tr>
  <tr>
    <td>add</td>
    <td>adds files for git to track</td>
    <td>add FILENAME <br> add FOLDERNAME <br> add .</td>
  </tr>
  <tr>
    <td>clone</td>
    <td>clone repository from URL</td>
    <td>clone URL</td>
  </tr>
  <tr>
    <td>commit</td>
    <td>commit change in tracked (added) files</td>
    <td>commit -m "NOTE"</td>
  </tr>
  <tr>
    <td>log</td>
    <td>prints commit log</td>
    <td>PRESS Q TO QUIT IF STUCK IN LOG <br> -n | -NUM | --max-count=NUM limits the number of commits printed <br> --skip=NUM skips NUM commits before printing <br> --after=DATE shows commits more recent than date <br> --before=DATE shows commits before date </td>
  </tr>
  <tr>
    <td>remote</td>
    <td>For dealing with remotes</td>
    <td>remote add NICK URL - to add a remote <br> remote -v - prints all remotes <br> remote remove NICK - remove a remote</td>
  </tr>
  <tr>
    <td>branch</td>
    <td>Displays all branches</td>
    <td>branch BRANCHNAME - creates new branch from current with BRANCHNAME <br> branch -m master main - Changes a master branch to be main intead</td>
  </tr>
  <tr>
    <td>checkout</td>
    <td>"Checkout" and switch to branch</td>
    <td>checkout BRANCHNAME <br> -q quiet</td>
  </tr>
  <tr>
    <td>merge</td>
    <td>Merge defined branch to curren branch</td>
    <td>--commit -m "MESSAGE"- perform merge and commit, and add message <br> -q quiet <br> -v verbose </td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>




## Options
<table>
  <tr>
    <td>Option</td>
    <td>Description</td>
    <td>Notes</td>
  </tr>
    <td>-r</td>
    <td>Recursive (includes self)</td>
    <td>rm -r</td>
  </tr>
  <tr>
    <td>-a <br> --all</td>
    <td>all</td>
    <td>git add -a <br/>git add --all</td>
  </tr>
  <tr>
    <td>-f <br> --force</td>
    <td>force</td>
    <td>Override up to date check</td>
  </tr>
  <tr>
    <td>-q <br> --quiet</td>
    <td>quiet</td>
    <td>Suppresses output</td>
  </tr>
  <tr>
    <td>-v</td>
    <td>Verbose</td>
    <td></td>
  </tr>
  <tr>
    <td>-u <br> --update</td>
    <td>update</td>
    <td>For use with git add <br> Only updates files, doesn't add new ones</td>
  </tr>
  <tr>
    <td>-u <br> --set-upstream</td>
    <td>set upstream</td>
    <td>For use with git push <br> Adds upstream tracking reference for git-pulls</td>
  </tr>
  <tr>
    <td>--oneline</td>
    <td>Prints condensed log</td>
    <td>git log --oneline</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>

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