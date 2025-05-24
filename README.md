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
  git commit
  ```
  OR
  ```bash
  git log --oneline
  ```
    - Git works on the idea of atomic commits which means **ONE COMMIT FOR ONE FEATURE/COMPONENT/FIX/BUG**
    - **ONE BUG: ONE COMMIT**



**Git configuration**

- Setting up username and email
  ```bash
  git config --global user.name "Your Name"
  git config --global user.email "Your Email"
  ```

- Setting up the text editor - in this case VS Code
  ```bash
  git config --global core.editor "code --wait"
  ```

**.gitignore file** 
<br>
A very special file read by git itself. You need to manually create it. There are a lot of information for instance API keys, passwords etc which are sensitive and need to store it separately. This is the folder where you can store this without git tracking any of these info.

```bash
touch .gitignore
```
<br>
Verify the existence of the `.gitignore` file using `ls -la` command.
<br>
Whatever files/folders aren't supposed to be tracked by git, just write it down in the `.gitignore` file, simply write it down and then check the `git status` to confirm if they have been removed. `.gitignore` would be tracked by git itself.




### Notes
- Develop a habit of using `git status` as the first thing. It tells you if git has been initialized in the folder or not yet.
- `git status` also tells which files have been staged or not yet, tracked or not tracked yet, modified or not modified yet.
- Always check the working directory where you want git to be initialized with `pwd` command.
- `git add` tells git to start tracking the particular file and also shifts the file to the staging area
- `git commit` always needs a message that's why it works with `-m`.
