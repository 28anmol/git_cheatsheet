# Git and Github Cheatsheet

## Documentation which runs through important git commands and their explanation! Learning git the conventional way - through command line interface!
#### What is Git? - Git is a version control software which helps keep a track of changes or modifications in computer file(s)!
#### What is Github? - It's a service, which hosts/saves your git repository and git workflow on an online cloud environment

<br>
<br>

**Tutorial: Learn Git - Full Course For Beginners from FreeCodeCamp:** [Link Tutorial](https://www.youtube.com/watch?v=zTjRZNkhiEU&t=12s)<br>
**Github docs link:** [Github docs](https://docs.github.com/en/get-started)<br>
**Generating ssh key:** [SSH Key Generate](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)<br>
**Adding ssh key:** [Add SSH Key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)<br>

### Follow the steps to have git up and running on a folder existing locally on your machine

- Download current version Git(2.49.0): [Git Software Download](www.git-scm.com)
- Verify version
    ```bash
    git --version
    ```

    Output in terminal:
    ```bash
    > git --version
    git version 2.49.0
    ```


### Setup git on a folder

- create a folder in your working directory
  ```bash
  mkdir learngit
  ```
- create 3 subfolders
  ```bash
  mkdir gitone gittwo gitthree
  ```
- Check git software status in first folder 
  ```bash
  git status
  ```

  Output on terminal without initializing git
  ```bash
  > git status
  fatal: not a git repository (or any of the parent directories): .git
  ```

- Initialize git inside first folder
  ```bash
  git init
  ```

  Output of git status will be:
  ```bash
  > git status
  On branch master
  
  No commits yet
  
  nothing to commit (create/copy files and use "git add" to track)
  ```

- Check hidden folders:
  ```bash
  ls -la
  ```

  Output:
  ```bash
  > ls -la
  total 0
  drwxr-xr-x  3 anmolsingh  staff   96 May 24 12:03 .
  drwxr-xr-x@ 5 anmolsingh  staff  160 May 24 12:02 ..
  drwxr-xr-x  9 anmolsingh  staff  288 May 24 12:50 .git
  ```

- Check contents of .git folder  (**Warning: Do not make any changes in this folder, else the consequenses are on you!**
  ```bash
  cd .git
  ls
  ```

  Output:
  ```bash
  > ls
  HEAD		config		description	hooks		info		objects		refs
  ```


### Basics of Git and it's working

```bash
Working Directory -----> git add -----> Staging Area -----> git commit -----> Repo -----> git push -----> Github
```

```bash
Write code -----> add to trackimng zone of git -----> commit
```

- Tracking a file by git or adding the file to git's trackable zone or staging a file for next commit:
  ```bash
  git add <filename>
  ```

  OR

  ```bash
  git add .
  ```
  This would add all modified files to staging area.

  ```bash
  git add -p <filename>
  ```
  This above command, instead of staging the whole file would break down changes into chunks (called hunks) and then you can manually select which part of the file to be staged.

- Unstaging a file from the stage:
  ```bash
  git reset <filename>
  ```
  OR

  ```bash
  git reset
  ```
  This unstages all files from the staging area but saves your modified files

- Committing to a file with a message (-m):
  ```bash
  git commit -m "add file one"
  ```

- Adding and commiting at the same time
  ```bash
  git commit -am "Your commit message"
  ```

- log command (it's a log of commits with details)
  ```bash
  git log
  ```
  OR
  ```bash
  git log --oneline
  ```
    - Git works on the idea of atomic commits which means **ONE COMMIT FOR ONE FEATURE/COMPONENT/FIX/BUG**
    - **ONE BUG: ONE COMMIT**
  
  OR
  
  ```bash
  git log -p
  ```
  This shows every commit + actual changes made.

  OR

   ```bash
  git log --oneline --graph
  ```
  This shows the graph of the git workflow tree on the command line interface

  OR

  ```bash
  git log --oneline --graph --all
  ```
  This shows the git tree


### Git configuration

- Setting up username and email (global scope)
  ```bash
  git config --global user.name "Your Name"
  git config --global user.email "Your Email"
  ```

- Setting up the text editor - in this case VS Code (global scope). First add `code` in shell path. Cmd+Shift+P in vscode and run Install code in PATH. Then run this config command
  ```bash
  git config --global core.editor "code --wait"
  ```

- Setting up username and email (local scope, confined to that repository itself)
  ```bash
  git config --local user.name "Your Name"
  git config --local user.email "Your Email"
  ```

- Setting up username and email (system wide - for all users on that system)
  ```bash
  git config --system user.name "Your Name"
  git config --system user.email "Your Email"
  ```

- configuration list
  ```bash
  git config --list
  ```

- Verify git configuration
  ```bash
  git config --list --show-origin
  git config --local --list
  git config --global --list
  git config --system --list
  git config core.editor
  git config --global core.editor

  # Check config of local repo
  .git/config

  # Check global config folder
  ~/.gitconfig
  ```

### .gitignore file

A very special file read by git itself. You need to manually create it. There are a lot of information for instance API keys, passwords etc which are sensitive and need to store it separately. This is the folder where you can store this without git tracking any of these info.

```bash
touch .gitignore
```

Verify the existence of the `.gitignore` file using `ls -la` command. <br>

Whatever files/folders aren't supposed to be tracked by git, just write it down in the `.gitignore` file, simply write it down and then check the `git status` to confirm if they have been removed. `.gitignore` would be tracked by git itself. <br>


### Git Branches

- To know which branch are you working on, use the following command:
  ```bash
  git branch
  ```

- Creating a git branch
  ```bash
  git branch <name of new branch>
  ```

- Switching to a different branch
  ```bash
  git checkout <name of new branch>
  ```

  OR

  ```bash
  git switch <name of new branch>
  ```

- Create branch and move to the new branch
  ```bash
  git switch -c <name of new branch>
  ```

  OR

  ```bash
  git checkout -b <name of new branch>
  ```

### Git branch merging

In order to merge, you need to first switch to the branch wehere you want codebase to be merged to. Then run the following command which merges the branch to the intended branch where you are currently sitting on.

```bash
git merge <name of the branch>
```

You can now check the git graph and also check the logs of the master branch.

To delete a branch, write the following command:

```bash
git branch -d <name of branch>
```

### Git diff

Git diff tells the difference between same files (file A and file A). The only difference is that it shows you the version of the file in X time and Y time.
- example 1: difference between files when staged and not staged
- example 2: difference between file 2 commits before vs current file version
- example 3: how does the same file look in this branch vs other branch

How to read file difference:
- a: represents file 1
- b: represents file 1 but in a different timeline (the same file undergoes changes over time)
- --- : file 1
- +++ : file 2 (the same file over time) - they don't mean removing or adding code.

The command below shows the changes in your working directory which hasn't been staged yet. BAsically you have modified some files but you haven't added them on the staging area yet. This command shows exact line by line changes. You'll see the diffs for all modified but unstaged files. 
```bash
git diff
```

The command below shows the changes in that specific file but haven't been staged. So it shows the difference between the working directory and the staging area for that particular `<filename>`.
```bash
git diff <filename>
```

The command below shows the difference between same files in staging area vs last commit), staged changes for all files vs last commit
```bash
git diff --staged
```

This commsnd shows the staged changes for that particular file vs last commit.
```bash
git diff --staged <filename>
```

If you want to know which files are staged(without showing the cide diffs)
```bash
git diff --staged --name-only
```

This is when you punch in different commit ids from the timeline to see the differences in code 
```bash
git diff <commit-hash-id> <commit-hash-id>
```

Tells difference between two different branches
```bash
git diff <branch-name-one> <branch-name-two>
```

### Git Stashing
- Create a repo, work on it and commit it on the main
- switch on another branch and work on it
- conflicting changes do not allow to switch branch, without commits

Basically you are for instance working on your branch, fixing a bug and havent staged it yet (still in middle of fixing the bug) and you switch to another branch because your colleague needs your help - then git won't allow you to switch branches before you commit or stash those changes. The output would looks as follows:

```bash
> git switch footer
error: Your local changes to the following files would be overwritten by checkout:
	footer.html
Please commit your changes or stash them before you switch branches.
Aborting
```

In this situation you can stash your changes with the following command
```bash
git stash
```
Now you can switch to another branch with `git switch <branch-name>` command

When you come back to your branch - you still don't see you changes because you stashed them. Stashing is basically a temporary shelf where you can keep your code, go back move around but you need to bring the changes back to your code. The following command brings back the work in progress changes to your code

```bash
git stash pop
```

Popping stashes to other branches by first changing the branch and then using the following command. This shows that stashing/popping is not just limited to one branch but can be moved to other branches as well.
```bash
git stash pop
```

More commands
```bash
git stash list
git stash apply stash@{0}
```

Stash pop brings back those changes<br>
Stash apply: applies changes and keeps them in stash


### More commands in Git

This goes back in timeline/git tree to show the version of your code at that particular commit
```bash
git checkout <hash-commit-id>
```

```bash
git checkout HEAD
```

To come back to present time in git timeline
```bash
git checkout master
```

This command also moves you to where you were in present timeline(it just moves your HEAD back to current time or to the latest commit)
```bash
git reflog
```

To move HEAD 2 commits back
```bash
git checkout HEAD~2
```

This command reattaches HEAD
```bash
git switch main
```

To get back to last commit version
```bash
git restore <filename>
```

### Git Rebase

This command kinda rewrites the history, so be extremely cautious while working with `git rebase`.
- It can be used as an alternative to merging(since it literally performs the merging BUT in merging it keeps your branches separately whereas in rebase it just merges everything into a single timeline)
- It can also be used as a clean up tool(clean up commits since it re writes the history)
- Note: if you are on the main branch or master branch, this command `git rebase` is never supposed to run from that branch. This command is meant to run always from the side branch where we are working like bugfix or new feature branch or whatsoever.
- Never rebase the commits you have already shared.
- Pushed to github??? - **NEVER Rebase**

This command always runs on a side branch and it means: I am rebasing my branch with the master. Do not ever run rebase command on master branch else the whole mess is on you!!
```bash
git rebase master
```

```bash
git rebase --abort
```

```bash
git rebase --continue
```

```bash
git rebase --skip
```

In case of conflicts during rebase, you need to resolve the manually and then run `git add <filename>` to stage it and then `git rebase --continue` to continue with halted rebase process.<br>
There is no concept of automatic conflict resolver.

### Github, Working with Github Using Command Line Interface
- The most important thing is that github shoud be able to work with your terminal.
- Github doesn't work with your terminal with simply email and password. It works using **SSH** keys.
- These SSH keys need to be generated and this key needs to be saved in the github settings page so that github knows that you are the same guy who is communicating
- The communication with github through terminal happens on the basis of SSH and not on the basis of email and password
- The email and passwoe=rd work well with the web, not on the command line
- You can also install `gh utility` also known as *github utility*
- We need to have ssh key on our system as well as on github to verify that communication is authentic and communication can take place through terminal(local machine)
- We have two authentication methods: SSH key and PATs (Personal access token) to work with github through command line interface.
- Generate and add ssh key to start communicating with github through command line interface using Github Docs (links attached above)

To verify is ssh is successful, paste the following command on your terminal:
```bash
ssh -T git@github.com
```

**Creating an empty repository on github, Connecting github repo to local folder on computer to that github repository through command line**
- Please have your ssh key generated and added to your computer and github account. Follow the links attached at the top for more info!
- Create an empty repository (don't add readme, make it public/private, don't add license yet, add a short description, dont add .gitignore yet)
- Once repo created you will see a set of commands shown up on github (Quick setup)
- Following is the complete detialed workflow of connecting your local git repository to github cloud environment:

  ```bash
  # Create a folder
  mkdir gitthree

  # Check directory for confirmation
  pwd
  
  # Check git status
  git status

  # If git isn't initialized, initialize git
  git init

  # Check git status again
  git status

  # Create a README.md file
  echo "# learn-git" >> README.md

  # Add readme to staging area
  git add README.md

  # Do the first commit - readme commit
  git commit -m "Made the README file for this repository"

  # Create your index.html file
  touch index.html

  # Add code to it
  # Config your user name, email etc for that repository

  # Then add it to staging area
  git add index.html

  # Commit your file
  git commit -m "Add index.html file to master branch"

  # Create the gitignore file
  touch .gitignore

  # Add and commit gitignore file
  git commit -am "add gitignore file to repository"

  # Rename your master branch to main
  git branch -M main

  # Check git branch
  git branch

  # Optionally you can also check the exisitence of hidden files and folders like .git & .gitignore using this command
  ls -la

  # Other optional commands for directories
  cd, ls, mkdir, touch, echo "Hello", cat <filename>, echo "Hello" >> <filename>

  # Command tells you if you have any remote repository being setup
  git remote -v

  # To connect a remote repository, have a connection with them, So origin is the name of the remote repository - we just named it origin(can also call it branch) for our convenience - see the command below
  git remote add <name> <url>

  # Link your local folder to cloud repository - you are free to use HTTPS url or SSH url
  git remote add origin https://github.com/28anmol/learn-git.git

  # Confirm the remote po configuration
  git remote -v

  # Optionally use other commands:
  git remote rename <oldname> <newname>
  git remote remove <name>

  # Start pushing stuff to your cloud repository, push into this origin repo from my main branch(master branch on local system), -u is setup as upstream which allows you to run future command
  git push <remote> <branch>
  git push <remote> # local branch : remote branch
  git push
  
  git push -u origin main
  # OR
  git push origin main

  ```

- Important note: Once u have multiple files committed prehand, you cannot select which files to push, github basically pushes all commits to the cloud environment.
- If you want to control push - control it from the `git add` stage, commit only those you want to push and then finally push the files you want.
- If your repo is setup remotely to a repo, you can undo it as well or change it to another repo as well.

**Case Scenario: when you have a repo on the cloud already and you would like to work on it on your local system**
- Copy the HTTPS or SSH clone url from github
- Go to your terminal and follow these steps
  
```bash
# URL can be SSH URL or HTTPS URL
git clone <URL>

# Use the SSH or HTTPS url
git clone git@github.com:username/website.git

# navigate to your repo
cd website

# make edits

git status

#add to staging area
git add index.html

# commit
git commit -m "Update homepage"

# push
git push origin main
```

### Git Clone, Pull, Fetch, Push

When you clone a repo, you just get the main branch connected, rest of the branches aren't configured.

```bash
git clone <URL>
```
This brings the code from the repository on to your system so that you can go through it and understand it better or maybe even work on it.

Workflow now:
```bash
|               |		|		|		|
| Working Area  | Staging Area	| Local Repo 	| Remote Repo	|
|		|		|		|		|
| 		|		|		|		|
|		|		|		|		|
|		|		|		|		|
|		|		|		|<--git fetch-- |
|		|		|		|		|

< ---------------------	git pull --------------------------------					

```

- Working Directory: This is the directory where actual work is happening
- Staging Area: This is the staging area where you decide which codebase is gonna be the next for commit (you prepare a picture for a snapshot, but haven't done it yet)
- Local Repository: Once staging ia done, you commit it(take a snapshot) and goes down in the git history. But this happens still on local repository on your system (Github not introduced yet)
- Remote Repository: This is the remote repo on github where you oiush your changes to the cloud environment
- `git fetch` and `git pull` both bring the code from the connected remote repository to your codebase
- `git clone` brings code to you local system only once or one at a time. Basically it downloads the entire repository/project including it's branches, commits and history but then it puts you on only one branch which is the master or main brnach. In order to work on other branches, you need to manually navigate there through command line.
- `git fetch` gets infor from the remote repository but doesn't place it in the working repository. It gets info to the locsl repository but doesn't make any changes to your working directory
- `git pull` gets all the info from the remote repository and places it in your working directory.
- `git pull = git fetch + git merge`

```bash
git pull origin main	# changes will be merged to main
```
The pull command updates only the branch you are currently on but doesn't update other branches. In order to update other branches you manually need to checkout to the other branch and run the same command again


```bash
git fetch
```
The above command makes sense to run per se and not merge to see what changed in the code base since the fetch command only downloads latest commits, branches, tags from the remote repository but doesn't merge them, doesn't update your working directory, instead just updates your remote tracking info (origin/<branch>)<br>

This is helpful in situations to see what changed on remote before messing with your code. Sometimes you don’t want to merge right away — maybe:
- You’ve made local changes that aren’t committed yet.
- You want to see what others pushed.
- You want to compare or review first.

Example:
```bash
git fetch
git diff main origin/main   # See what's different
```

`git fetch` is also limited to the branch you are working on.

Other Github features:
- Active collaborations
- Readme file
- Markdown format
- Dev container
- Adding Codespaces
- Adding Gists (code snippets)

### Making pull requests and contributing to open source projects

```bash
Find an open source project(how? - On github mostly through github advanced search) ---> Talk to maintainers(slack,twitter,discord whatever) ---> Open an issue ---> Get the issue assigned (to save others time for other productive stuff) --->
Work & Add value to the project ---> make a PR and iterate over it ---> Have Patience ---> Then later it would be merged if it works out. (Making a PR is not a job guarentee)


Fixing readme or improving documentation/ isn't generally considered a meaningful contribution to open source projects or worth raising a PR. Documentation is ofcourse important but being a programmer it is expected from you to contribute first to the codebase and then the documentation.

Also contribute good code/meaningful code as a contribution not throw random code which might break or anything!

ADD VALUE THAT'S IT!
```

Steps to create a pull request
```bash
# Fork the project to your repo

# Clone it to you local system and in order to work with your command line

# Good idea to make a new branch first to add your contributions

# Add and commit code

# Push the code (so updates local repo and remote forked repo on github). Push my new branch to origin (main) of the remote repo
git push -u origin <newly created branch>

# Compare and pull request
# I have forked repo, created a neew branch where i fixed the bug , now compare and pull request.
# Whole idea is: i have made these changes and i want to send the changes to the main owner of the repository.
In this case the repo is ours since it is forked

# Add title and description very thoughtfully

# Create pull request

# Manually inspection of code happens before merging to main

# Accept the request (merge pull request) to main

#Contributed to open source developers community
```

### Personal research, more advanced commands:

This includes for instance: to undo changes, go back in time, view and explore history, fix mistakes, use commit hashes effectively, recovery, undo commits, restoring, how to make a repo in terminal and initialize readme, public/private repo, description, gitignore, license and much more...

*WIP.................*

```bash
# Undoing Changes and Going Back In Git

git status				# Check current status of working directory & staging area

git log					# Full log
git log --oneline			# Short Summary
git log --graph --oneline --all		# Visual Graph

git diff				# Unstaged changes
git diff --staged			# Staged Changes
git diff HEAD				# Changes from last commit

git checkout <commit-hash>		# To go back and explore state of past commit (detached HEAD)
git checkout main			# To come back to present
git checkout -- <file>			# Discard changes in a file in the working directory (revert to last commit).
git checkout -- filename.txt

git restore				# Modern alternative to checkout for restoring files.
git restore <file>			# Discard local changes (like checkout --)
git restore --staged <file>		# Unstage a file from index but keep the changes

git reset				# Undo changes in your staging area or even move HEAD and rewrite history (cautiously).
git reset --soft HEAD~1        		# Undo last commit, keep staged changes
git reset --mixed HEAD~1       		# Undo last commit, keep files but unstaged
git reset --hard HEAD~1        		# Undo last commit and delete all changes
git reset <commit-hash>        		# Rewind to that commit

					# --soft — Move HEAD to a previous commit, keep changes staged.
					# --mixed (default) — Move HEAD, keep changes in working directory.
					# --hard — Dangerous: resets everything (HEAD, staging area, working directory).

git revert <commit-hash>		# Safely create a new commit that undoes the changes made by a specific commit.

git reflog				# Show a log of where your HEAD and branches have been. Recover lost commits even after a reset or rebase.
git checkout <commit-hash>  		# From the reflog to recover



# Committing And Amending Mistakes

git commit --amend			# Modify the last commit (message or staged content). Don’t use this if the commit is already pushed.
git add <fixed-file>
git commit --amend
git commit --amend -m "New commit message"
git rebase -i HEAD~3			# If you want to change an older commit yet not pushed, you can use interactive rebase
git reset --soft HEAD~1			# Undo a commit , change a commit message or add more changes but keep changes staged
git reset --mixed HEAD~1		# Undo commit and unstage the changes (keep changes in working directory)
git reset --hard HEAD~1			# Undo commit and discard everything (dangerous)
git revert <commit-hash>		#  Revert a commit (safe way, creates a new commit that undoes it)

git clean				# Remove untracked files from the working directory.
git clean -n 				# — Preview
git clean -f 				# — Delete
git clean -fd 				# — Delete untracked files and directories

git cherry-pick <commit-hash>		# Apply a commit from anywhere in history onto your current branch.



# Time Travel And Navigating History

git show <commit-hash>			# See changes, author, and commit message of a commit.
git bisect				# Debug tool to find which commit introduced a bug.
git bisect start
git bisect bad       			# Current commit is broken
git bisect good <commit>  		# Older good commit
git bisect reset     			# Stop the bisection

git tag					# Mark specific points in history (e.g., version 1.0).
git tag v1.0 <commit-hash>
git checkout v1.0



# Recovery And Safety

git stash				# Temporarily save your changes without committing.
git stash              			# Save changes
git stash pop          			# Re-apply stashed changes
git stash list         			# View stash history
git stash show -p      			# Show stash content

git merge --abort			# Abort a merge or rebase that’s going wrong.
git rebase --abort

# How to go back in time or restore deleted code in git

git log					# See the Commit History (Timeline)
git log --oneline --graph		# Shows all commits with their hash IDs, authors, dates, and messages.
git checkout <commit-hash>		# Check Out a Previous Commit (Read-only exploration).This puts you in a detached HEAD state — safe to explore, but you can’t commit here (unless you branch from it)
git checkout abc1234

git restore --source=<commit-hash> <file-path>		# Restore a File from an Older Commit (to Working Directory)
git restore --source=abc1234 src/utils.py		# If you deleted or changed something and want just a specific file back from an old commit

# Recover a Deleted Function or File from Past Version
git log <file-path>  			# See history of this file
git show <commit-hash>:<file-path>	# This prints the file as it was in that commit. You can then copy-paste your deleted function from here.
git diff HEAD~1  			# See what changed in the last commit
git diff <old-commit> <new-commit> <file>	# Or to see what was removed from a file, you’ll see deleted lines prefixed with -
git revert <commit-hash>		# To go back safely

git checkout -b old-version abc1234	# Creating a branch from an older commit. This creates a new branch starting at that commit.



# View the Timeline / Commit History

git log					# Full log
git log --oneline			# Compact view
git log --oneline --graph --all		# Visual tree
git show <commit-hash>			# Show changes in a commit
git log <file>				# File-specific history
git blame <file>			# Who changed which line (blame)



# Undoing Changes in Working Directory & Staging

git restore --staged <file>		# Unstage files (keep changes)
git restore <file>			# Discard local changes (careful!)
git restore .				# Discard all local changes
git checkout -- <file>			# Revert to last committed version (Older Git)
git clean -f				# Remove all untracked files
git clean -fd				# Remove untracked dirs too



# Undoing Commits

git commit --amend -m "New message"	# Change last commit message
git reset --soft HEAD~1			# Undo last commit, keep changes staged
git reset --mixed HEAD~1		# Undo last commit, keep changes unstaged
git reset --hard HEAD~1			# Undo last commit, discard everything
git revert <commit-hash>		# Revert a specific commit (safe, keeps history)



# Going Back to Older Versions

git checkout <commit-hash>		# Explore old commit (readonly)
git checkout -b <branch> <commit-hash>	# Create a branch from old commit
git restore --source=<commit-hash> <file>	# Restore a file from older commit
git show <commit-hash>:<file>		# View content of file from past



# Editing Old Commits

git rebase -i HEAD~n 			# Change message of older commit → change pick to reword
git rebase -i 				# Edit content of older commit → edit
git rebase --abort			# Abort a rebase in progress
git rebase --continue			# Continue rebase after fix



# Diff & Recovery Tools

git diff				# Show changes not staged
git diff --cached			# Show staged changes
git diff <commit1> <commit2>		# Compare two commits
git diff <file>				# See what changed in a file
git diff <commit> -- <file>		# Compare working dir vs commit



# Cleaning Up Mistakes

git clean -f				# Remove untracked files
git clean -fd				# Remove untracked dirs too
git checkout -				# Revert to previous branch
git merge --abort			# Abort current merge
git cherry-pick --abort			# Abort current cherry-pick
git rebase --abort			# Abort current rebase
git reset --hard origin/<branch>	# Reset to remote state



# Deleting files through github

git rm myfile.txt			# This removes the file and stages the deletion for commit.

rm myfile.txt           		# or delete from File Explorer
git status              		# shows it as deleted
git add myfile.txt      		# yes! this stages the *deletion*
git commit -m "Deleted myfile.txt"	# Commit the deletion of file
git restore myfile.txt			# If you deleted but haven't committed yet, this brings the file back from the last committed state
git log -- myfile.txt			# Restore a file from an earlier commit (after deletion is committed), If you committed the deletion but want to bring back an old version.
git checkout <commit-hash> -- myfile.txt	# Find the commit hash where the file existed. Then restore it like this
git log --diff-filter=D --summary	# how deleted files in history
git reset HEAD~1         		# go back 1 commit, f you want to undo the deletion commit
git reset --soft HEAD~1			# soft undo (keep changes)
git revert <commit-hash>		# revert the commit


# Branch Recovery / Safe Actions

git reflog				# Recover lost commit (if lost after reset)
git checkout <reflog-hash>		# Checkout commit from reflog
git checkout -b recovered <reflog-hash> # Create branch from reflog commit
git checkout -b <branch> <hash>		# Recover deleted branch	git reflog → find tip →



# Reflog: Time Machine for Git

git reflog
					# Tracks every movement of HEAD — commits, checkouts, rebases, resets, etc. Useful when:
					# 	- You did a reset --hard and want to undo it.
					# 	- You deleted a branch and want to recover it.
					# 	- You want to restore something from an accidentally lost commit.


# Safety Tips

					# Use --soft, --mixed, --hard resets carefully.
					# Always commit or stash before rebasing, merging, or resetting.
					# NEVER force-push (git push --force) to shared branches without understanding the consequences.



# Track which files have been committed/pushed

git ls-tree -r HEAD --name-only		# See files committed in current branch
git log --name-only --pretty=format:	# Show history of committed files
git status				# modified/untracked files and also uncommitted files
git log -- <filename>			# Using it to track a specific file
git diff --name-only origin/main..HEAD	# To check difference with remote branch
git ls-tree -r origin/main --name-only	# Shows all files pushed to remote
git ls-tree -r HEAD --name-only		# Show all committed files in local branch
git show --name-only <commit-hash>	# Shows files added to specific commit only
git log origin/main..HEAD --oneline	# List unpushed commits
git show				# quit command with :q


# Git HEAD : It is a very powerful tool in git and is a pointer to your current position in the git repository usually pointing to the latest commit in your currently checked out branch.
# You can movr your HEAD to any commit(detached HEAD) which helps in inspection, navigation and inspection of git commit history

git log					# shpws the position of HEAD
git checkout <branch>			# Moves HEAD to that tip of the branch
git reset --hard HEAD~1			# Moves head position one commit back and resets your files accordingly
cat .git/HEAD				# Shows where your HEAD points to
git checkout <commit-hash-id>		# Detached HEAD state
HEAD~n					# takes it n commits back
git show HEAD				# shows latest version of your project
git show HEAD~1
git show HEAD~2
git checkout HEAD~1 -- filename.txt	# Restore older version temporarily
git reset --soft HEAD~1			# undo latest commit but keeps your changes
git reset --hard HEAD~1			#undo last commit completely, deletes your changes
git checkout HEAD~2			# Browse past version of your codebase
git checkout <commit-hash>
git diff HEAD
git diff HEAD -- file.txt
git checkout <commit-hash>
code.
git checkout <commit-hash> -- path/to/file.txt		# viewing a single file only in the past
code path/to/file.txt
git checkout main  			# or whatever your branch is, coming back to present




# Bonus: GUI Tools to Visualize Git History
# Tool						Description
# gitk						Classic Git GUI history viewer
# tig						Terminal Git history viewer
# VS Code Source Control			Integrated timeline and file history
# GitLens (VS Code extension)			Super powerful Git history, blame, and commit tools
```

### Helpful Notes & Tips
- Git is a version control system which tracks every change in your code over time. It allows you to undo changes at any point in history, tracks who changed what and why, experiment safely without breaking the fear of breaking the code, wok with others without overwriting each others changes.
- Git prevents you from making backup of working code(project_final_reallyfinal_reallythisone.zip) before you try a major change where you fear breaking up the whole code because git helps you undo things, go back in time and retrieve previous versions. It's more like a personal time machine.
- Git tracks files in 3 layers
      - Working directory
      - Staging Area
      - Git repository
- Git commit is a 2 stage process
      - From working directory to staging area(index area)
      - From staging area to git repository
- Develop a habit of using `git status` as the first thing. It tells you if git has been initialized in the folder or not yet.
- `git status` also tells which files have been staged or not yet, tracked or not tracked yet, modified or not modified yet.
- Always check the working directory where you want git to be initialized with `pwd` command.
- `git add` tells git to start tracking the particular file and also shifts the file to the staging area
- `git commit` always needs a message that's why it works with `-m`.
- `HEAD` points to where the branch is currently at. OFc, you can change the location pointer of `HEAD` explicitly in the codebase at your will and to your choice. Ultimately, the are just checkpoints like in a video game.
- There are multiple commits in a branch and `HEAD` points to the latest commit in that branch. But you can change to which commit the `HEAD` points to in that particular branch.
- Always commit before switching to another branch
- Go to `.git` folder and checkout the `HEAD` file to see where does the `HEAD` point in that current active branch
- A general rule of writing commits: present tense + imperative. Example: add file to codebase, add 4 lines in python file, merge header with footer. It'a like a command you give in present tense: "Hey codebase, do this, do that, add this code, add that code".
- Basically when you merge two branches with conflict, you resolve it manually, then you need to `git add` the file and perform `git commit` afterwards. `git merge` is also basically merging+commiting with a message essentially. If there are no conflicts, you can merge with editor open, you type in the merge message, save and close and you see that the file has been merged with a commit successfully in the terminal.
- If you want to move your `HEAD` to a previous commit, or you want to go back in time or you want to branch from past, you have to use `<commit-hash>` or the commit id you see on `git log` to do all that stuff. It helps you time travel in git branches to mend your faults or to experiment on a version from the past without affecting the main branch.
- Stashing is meant for temporary purpose only. It should be used very carefully and one shouldn't be heavily dependent on it.
- Use Git Graph, source control extensions in vs code to view your files simultaneously being updated through the command line interface.
- Default text editor such as vim, gdit, nano and sublime can also be used to edit the code, upto you. In this case, VS code is the prime text editor in use.
- Many a times, it happens that merging of main/master branch happens on a side branch where you are working on some experiment to check/merge the latest updates so not a surprise
- Once a side/regular branch is merged on main/master branch, you can still work on side branch and merge it again with new features or bug fixes etc.
- As soon as you initialize git in a folder it turns into a repository or commonly known as git repository.
- On github master branch is called `main` while git software still calls it `master`
- Git is a software and github is a service to host your git and codebase online
- Github: Collaboration + Backup + open Source
- Other online services are: GitLab OR BitBucket
- Github uses PAT or SSH to work with Command line Interface on your local machine. user-id, email or password based code push is not allowed on github
- Check instructions for your OS on github website, along with updated resources
- Local Repository: On your system, Remote Repository: On the github cloud environment
- A million dollar question is: **When do you commit? :** The answer is, you commit only when you make a meaningful change in your codebase such as: fixing a bug, addng a new functionality, improving the documentation, refactoring the code(cleaning or reorganizing the code structure without changing it's functionality), updating configuration or dependencies.
- **Why committing these points? :** Each commit represents a logical or self contained change, it helps to track what changed when and why, makes it easier to review history debug or make changes later
- Another million dollar question is: **Why does git have a staging(index) area and not commit directly from the owrking directory? :** The git staging or indexing area acts a buffer and gives fine grained control over commits. The staging area lets you commit only specific changes and not everything from working directory. For example: if you modified 5 files in working dorectory but only 2 of them are ready for commit, you can stage only 2 and commit only 2 of them out of 5. It also helps in atomic and cleaner commits which means it encourages logical, focused commits. You can group related changes together, even from different files.
- If you want to contribute to open source projects on github - **PLEASE ADD VALUE TO IT! DON'T SPAM! SPAMMING A REPO AND CONSIDERING IT AS A CONTRIBUTION IS UNACCEPTABLE**
- **What is Open Source?** : It is not just about making your codebase available on github, bitbucket or it's not about anybody walking in to contribute in that code but there is much more to it. Open source is a full fledged philosophy that software can be or should be distributed for free so that other programmers can save some time and it's a contribution to the society/community of programmers. That is the whole sense of open source. And no open source project irrespective of size should be taken for granted. Everyone should try to contribute to the ecosystem of developers through open source projects. Contributions are wildly appreciated throughtout the community of developers. But again, it should add a value and shouldn't be misused/abused or be used for personal gains by mindlessly contributing to open source project and their maintainers without adding any value
- Learn more on git rebasing, git branching, git merging, pull requests, raising issues, manual inspection of pull requests, checking code and merging pull requests.
- Practice git in daily life!
