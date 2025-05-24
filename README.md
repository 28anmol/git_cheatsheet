# Git and Github Cheatsheet

## Documentation which runs through important git commands and their explanation! Learning git the conventional way - through command line interface!


#### What is Git? - Git is a version control software which helps you to keep a track of changes or modifications in a computer file!
#### What is Github? - It's a service!

<br>
<br>

**Follow the steps to have git up and running on a folder existing locally on your machine**

- Download Git from www.git-scm.com (Current version - 2.49.0)
- Verify version
    ```bash
    git --version
    ```

    Output in terminal:
    ```bash
    > git --version
    git version 2.49.0
    ```


**Setup and configure git on a folder:**

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


**Basics of Git and it's working**

```bash
Working Directory -----> git add -----> Staging Area -----> git commit -----> Repo -----> git push -----> Github
```

```bash
Write code -----> add to trackimng zone of git -----> commit
```

- Tracking a file by git or adding the file to git's trackable zone:
  ```bash
  git add <filename>
  ```

  OR

  ```bash
  git add .
  ```

- Committing to a file with a message (-m):
  ```bash
  git commit -m "add file one"
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
  git log --oneline --graph --all
  ```
  This shows the git tree


**Git configuration**

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
  

**.gitignore file**

A very special file read by git itself. You need to manually create it. There are a lot of information for instance API keys, passwords etc which are sensitive and need to store it separately. This is the folder where you can store this without git tracking any of these info.

```bash
touch .gitignore
```

Verify the existence of the `.gitignore` file using `ls -la` command. <br>

Whatever files/folders aren't supposed to be tracked by git, just write it down in the `.gitignore` file, simply write it down and then check the `git status` to confirm if they have been removed. `.gitignore` would be tracked by git itself. <br>


**Git Branches**

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

**Git branch merging**

In order to merge, you need to first switch to the branch wehere you want codebase to be merged to. Then run the following command which merges the branch to the intended branch where you are currently sitting on.

```bash
git merge <name of the branch>
```

You can now check the git graph and also check the logs of the master branch.

To delete a branch, write the following command:

```bash
git branch -d <name of branch>
```







### Notes
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
