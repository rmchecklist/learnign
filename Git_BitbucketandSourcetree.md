# What is Git?
  - Distributed controlled system
# Git glossary

- Git
      - Open source version control system, it takes screenshot when you save the file
- Branch
      - Mirror of current repository, Main branch is better known as Master
- Clone
      - Copying a repository and make a local copy for your own modifications, 
        you can commit the files locally that won't affect remote repository, 
        we need to use push command to move the changs to remote repo
-  Push
     - Push local files into remote repository 
- Pull
    - Pull(Fetch and merge) changes from remote repository[updated] 
- Merge
    - Combines changes into one   
- Fetch
    - Pull the code to compare the changes 
- checkout
    - Navigate the branch 


# Install Git

- download the file from [https://git-scm.com/download] 

# Commands
 - **pwd** -> Print working directory

 - Set user name gloablly -> **git config --global user.name 'rengith manickam'**
 - Find the user name -> **git config user.name**
 - Set email id -> **git config --global user.email 'mrengith@gmail.com'**
 - Find the email id -? **git global user.email**

# Command line

1. pwd - print working directory
2. mkdir - create directory
3. cd - change directory
4. touch file_name - create new file
5. ls - list the files and folder
6. vim file_name - open the file using vi improve editor
    i - insert new word
    :w - write the file(use ESC before hitting w)
    :q - quit
7. rm file_name - remove file name
8. cd .. - go to previous directory
9. rmdir dir_name - remove directory

# Creating a Git repository

- mkdir MyGitRepo
- git init -> initialize the git repo
- view all files under repo
-  ls -a -> view all hidden files

# Adding files
- touch indedx.html style.css -> creating new files

# Git status

- git status -> track all files under working directory

# Tracking files
 - branch -> independent source of code 
 - track/staging file
      git add file_name
      
  - untrack/unstage a file
      git rm --cached file_name
  - Commit all files
     git add .
# Committing files

- git commit -m 'add skeleton files for webpage' -> -m refers adding message

# Viewing history
- git log

# Introduction to branch
- git branch
- creating a new branch
    git branch user-authentication
- Switch/Checkout branch
    git checkout user-authentication
    
# Staging and Tracking
untracked file - Files are in local not added to repo
unstaged - files are committed, and modified and untracked
