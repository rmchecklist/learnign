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
 - untracked file - Files are in local not added to repo
 - unstaged - files are committed, and modified and untracked

# Viewing file difference

 - Find the specific file difference -> git diff file_name
 - Find all file differnece -> git diff

 - clear the console -> clear

# Ignoring files
- create .gitignore file and add the files to ignore(you can use *.log, this will ignore all log files)

# Committing our work
 - git commit -m 'add .gitignore'

# Merge

1. Checkout the master branch -> git checkout master
2. merge the file from user-authentication to master -> git merge user-authentication
3. Hisotry of the commit -> git log

# Adding a Tag
annotate the tag and adding a message
- git tag -a v1.0.0 -m 'Version 1.0.0 release'
- Find all tag -> git tag

# Git commands

[https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html]

# Bitbucket

- Remote repository
  It's a central repository and globally available to access, you can push and pull the data.
- Pull
  Pull data from remote repo
- Push 
  Push the local changes to remote repo
  
  # Creating Remote repository
  
  1. Login to [https://bitbucket.org/]
  2. Create a account as per the instructions
  3. Create a repository
  
  # Bitbucket interface
  
  pull request => Request a change before integrating a official project
  pipeline
  Boards
  
  # Cloning: HTTPS vs SSH
  
  - HTTPS -> always going to verify using cert auth, when you push the changes system prompt you to enter credentials
  - SSH => use public key authentication, public key for bitbucket, private key will locally, more secure
  
  # Clone HelloBitbucket
  
  - copy the url from bitbucket account(clone repo "git clone https://rengithmanickam@bitbucket.org/rengithmanickam/rengithrepo.git")
  - Open git command line and paste under you target dir

# Creating and committing files

- Create a file under bitbucket cloned dir 
    Step1:
        create file -> touch helloworld.txt
        create and open the file at one shot -> vim helloworld.txt(create new when you save or else won't be created)
        Add text and save them by ESC wq command
    
    Step2:
        check status of untracked files by git status
    
    Step3: 
      Add all files by git add .
      Check the status by git status , Files are staged and ready to committed
      
    Step4: 
      Commit the files by git commit -m 'commit message'
      Check the status, You will be receive the mesage 'Your branch is based on 'orgin/master' but the upstream is gone' because we cloned empty repo
      
 # Pushing changes
     - git push origin master -> we are pushing local changes to repo master branch repo, after this command all changes will be available in the remote repo/orgin
     
 # Pulling changes
 
 - git pull -> fetch all changes from remote repo and merge the changes. it's a combination of 2 commands
    - git fetch and git merge
  
# Setting up and SSH key

- ssh-keygen --> generate ssh key
      Simply enter when prompt to enter the file and password
      key will be generated under ~/.ssh(~ -> home dir)
      view the key ==> ls ~/.ssh

Add public key to bitbucket
  Click on the avator(bottom left), settings ==> Security==> SSH-keys ==> Add key
  
  copy the key using following commands
  MAC OS ==> pbcopy < ~/.ssh/id_rsa.pub
  Linux ==> cat < ~/.ssh/id_rsa.pub
  Windows ==> clip < ~/.ssh/id_rsa.pub
  
  
  Paste key, Set label name as Default key or something else and Click on Add key
  
  Add key to local through command line
  
    ssh -T git@bitbucket.org
    
    
 # Sourcetree
 
 # What is sourcetree?
  - GUI for git
  - DVCS(Distributed version control system) friendly
  
# Install source tree
  
  - download the installation file from [https://sourcetreeapp.com/]
# The sourcetree interface
 - Local/Remote tab to select the repo
 - On remote, hit the refresh the button to pull the information from remote
 - There are other button, clone, Add and Create

# The sourcetree interface: Toolbar, sidebar, and more

  - Sidebar
      Branches
      History -> view hitory of the file, code differences
  - Searching for commits
      Search by commit message to identify the files or you can find by date search
      
 # Get branching model
 
 ![image](https://user-images.githubusercontent.com/5713791/131427287-0e9ef76c-9b68-4228-b919-5e9c8542608e.png)
 
 # Getting started with MyGitRepo
 
