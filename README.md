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

- Download current version Git(2.49.0) [Git](www.git-scm.com)
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

- Setting up the text editor - in this case VS Code (global scope)
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
- Pleasw have your ssh key generated and added to your computer and github account. Follow the links attached at the top for more info!
- Create an empty repository (don't add readme, make it public/private, don't add license yet, add a short description, dont add .gitignore yet)
- Once repo created you will see a set of commands shown up on github (Quick setup)
- Follow these steps

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

  # Then add it to staging area
  git add index.html

  # Commit your file
  git commit -m "Add index.html file to master branch"

  # Create the gitignore file
  touch .gitignore

  # Rename your master branch to main
  git branch -M main

  # Check git branch
  git branch

  #
  
  ```

### Personal research, more advanced commands:
- To undo changes
- Go back in time
- View and explore history
- Fix mistakes
- Use commit hashes effectively
- Recovery
- undo commits
- Restoring
- (readme, public/private repo,description, gitignore, license) how to do in terminal

*WIP.................*

```bash
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
- there are multiple commits in a branch and `HEAD` points to the latest commit in that branch. But you can change to which commit the `HEAD` points to in that particular branch.
- Always commit before switching to another branch
- Go to `.git` folder and checkout the `HEAD` file to see where does the `HEAD` point in that current active branch
- A general rule of writing commits: present tense + imperative. Example: add file to codebase, add 4 lines in python file, merge header with footer. It'a like a command you give in present tense: "Hey codebase, do this, do that".
- Basically when you merge two branches with conflict, you resolve it manually, then you need to `git add` the file and perform `git commit` afterwards. `git merge` is also basically merging+commiting with a message essentially. If there are no conflicts, you can merge with editor open, you type in the merge message, save and close and you see that the file has been merged with a commit successfully in the terminal.
- If you want to move your `HEAD` to a previous commit, or you want to go back in time or you want to branch from past, you have to use `<commit-hash>` or the commit id you see on `git log` to do all that stuff. It helps you time travel in git branches to mend your faults or to experiment on a version from the past without affecting the main branch.
- Stashing is meant for temporary purpose only. It should be used very carefully and one shouldn't be heavily dependent on it.
- Use Git Graph, source control extensions in vs code to view your files simultaneously being updated through the command line interface.
- Default text editor such as vim, gdit, nano and sublime can also be used to edit the code, upto you. In this case, VS code is the prime text editor in use.
- Many a times, it happens that merging of main/master branch happens on a side branch where you are working on some experiment to check/merge the latest updates so not a surprise
- Once a side/regular branch is merged on main/master branch, you can still work on side branch and merge it again with new features or bug fixes etc.
- As soon as you initialize git in a folder it turns into a repository or commonly known as git repository.
- On github master branch is called `main` while git software still calls it `master`
