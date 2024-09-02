# GIT GUIDE

### Setup git

1. Check if there is .git folder by `ls -a`
2. If there is already a .git in the directory, delete it by `rm -rf .git`
3. Configuring .gitignore file: (if you don't see one, you can create it)
   - Add files you don't want to upload to git repository. If there is forward slash in front of it, just remove it.
     For example: `/filename` this is a comment in .gitignore file which means it WILL upload that file

---

### Initialize git

- Initialize git repository with `git init`

---

### Add - Add changes in current directory to staging area

- `git add .` (add all)

---

### Commit - Capture a snapshot of staged files

- `git commit -m 'commit message'`

---

### Create remote git repo - If you haven't created your remote git repo, follow these steps

1. Go to GitHub website
2. New repository
3. Repository name
4. Set Public/Private
5. Click on Create repository button

---

### Push - Upload changes from local git repo to remote git repo

1. `git remote add origin https://github.com/your-github-name/remote-repo.git` (replace your-github-name and remote-repo accordingly)
2. `git branch -M main`
3. `git push -u origin main`

---

### Git Authentication - You need your GitHub email and a Personal Token to authenticate

1. Go to GitHub and click on your profile picture > Settings > Developer settings (at the bottom) > Personal access tokens > Tokens (classic)
2. Click Generate new token > Generate new token (classic)
3. Confirm your github access (by using authenticator app or your GitHub password)
4. Write a name for this personal token in Note. For example "For Selenium"
5. Choose an Expiration (this personal token will expire on this expiration date)
6. Select/Check "repo" from scope list. No need to choose others for this purpose
7. Copy and paste this to somewhere safe. IMPORTANT! Make sure you copied it before you close the browser or you won't see it again and you will need to create new token

---

### Clone - Get clone of remote repo (when you are collaborating with others)

1. Go to GitHub and click on the repo
2. Click on Code with a green button
3. Copy the link which ends with .git
4. Open terminal and go to the directory where you want to save the clone
5. use `git clone remote-repo-url.git`

---

### Fetch

1. `git fetch` to download new update from online git repo to the local git repo (NOT to the working tree/directory)
2. `git merge` to merge new update with the working tree

---

### Pull

- `git pull` runs both above commands (git fetch, git merge)
  <br><br>![this is alt text: an image of git fetch, merge, pull](git-fetch-pull.gif)

---

### Stash - Stash any changes that haven't been committed

Stash changes

1. Make some changes
2. `git add .` (add changes to stage)
3. `git stash` or `git stash push` to stash changes that haven't been committed

Pop - Bring back old changes from stash

- `git stash pop` or `git stash apply` (similar to pop, but pop will remove the item from stash)

List - Check all items in the stash

- `git stash list` (on Mac, to quit current window, press "Q")

Clear - Clear items in the stash

- `git stash clear`

In case you want to stash un-tracked changes, you need to use -u (un-tracked)

- `git stash -u`

---

### Git Branch

View branch

- `git branch` (shows only local branch)
- `git branch -a` (shows all local and remote branches)

Create a branch

- `git branch branch-name` (creates a new branch)
- `git checkout -b branch-name` (creates a new branch and switches to it automatically)

Switch branch

- `git checkout branch-name` (switches to a branch manually)

Delete a branch

- `git branch -D branch-name` (removes a branch. Make sure you are on another branch)

---

### Handling Merge Conflict with Stash

In a scenario where you made some changes and at the same time another collaborator made also changes in the same file as well

1. `git add .` (first add your changes in staging area)
2. `git stash -m "my changes"` (stash your changes)
3. `git pull` (get changes of other collaborators)
4. `git stash pop` (bring back your changes from stash. This will merge two files and will show both changes in same file)
5. now you can open that file and make your decision. For example which changes you want to keep or remove and save the file
6. `git add .` (add merged file to the staging area)
7. `git commit -m "commit message"`
8. `git push`

---

### Handling Merge Conflict with Branch (Pull Request)

1. `git branch new-branch` (creates a new branch)
2. Make your changes and then `git add .` and `git commit -m "made some changes"` (notice that when you are in the new branch and use git add . and git commit, it ONLY affects to the current branch you are in)
3. `git push origin new-branch` (pushes your changes to the new branch. If some reason, you get `! [rejected]` message, you can simply use `git push -f origin new-branch` (-f for force push))
4. On the GitHub, if you see `Compare & pull request` on main branch, click on it. If you don’t see, then go to the new-branch and click `Contribute` and click `Open pull request`
5. If there is no conflict then simply click `Create pull request` > `Merge pull request` > `Confirm merge` (you can delete the branch or simply leave it there)
6. In case if there is a merge conflict, you will see `Can’t automatically merge`
7. Click on `Create pull request`, Add a title and description and then click `Create pull request`
8. Now you will see the `Resolve conflict` button and click on it
9. Here you can make changes to the files and decide which line of code you want to keep or delete and click `Mark as resolved`
10. Click `Commit merge` (if you see pop up, click on `I understand, continue updating main`)
11. Now you can click `Merge pull request` > `Confirm merge`
12. Finally pull merged main with `git pull origin main` to update current branch (new-branch). And then switch to main branch and `git pull` to update main branch as well

---

### Steps to push updated files

1. `git pull` (when you collaborate with others, always first pull updated files)
2. Make some changes
3. `git add .` (add changes to stage)
4. `git commit -m 'Your message'`
5. `git push`

by khen
