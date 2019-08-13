# Git and The Terminal

Before we dive into building cool things, we have a bit of work to do with learning the tools of the trade. 

## This lesson is meant to teach the students:
* Navigation using the terminal
* Installing and managing packages
* Using git for version control

### Using the terminal
This is a tool that many are resistant to at first but come to love it over time. It's just a very different way to navigate and interact with your computer. Below is a cheatsheet for the basic commands you'll need. You can do things such as create, rename, delete and copy files and much more.
``` bash
# Lists the contents of the directory you're in
$ ls

# Lists the contents in list form with additional information
$ ls -l

# Lists all of the content (including hiden files)
$ ls -a

# Combines the two commands above into a single command
$ ls -la

# Stands for 'print working directory', and will print the directory you're currently in
$ pwd

# 'change directory' moves you between directories
$ cd [location]

# Takes you to the parent directory of the one you're currently in
$ cd ..

# Used for copying a file or directory
$ cp filename newfilename

# Changes your location to your home directory 
$ cd ~

# Changes your location to your root location (the top parent)
$ cd /

# Recurively copies the directory and its contents to the specified destination
$ cp -r source_dirname destination_dirname

# Deletes a file
$ rm [filename]

# Deletes a directory or file and doesn't prompt you with warnings
$ rm -rf [filename/directory]

# Is a dangerous command that will irreversably delete anything. It can literally wipe your computer - so watch out.
$ sudo rm -rf

# Moves the target to the destination, or renames a file if there is no directory by that name 
$ mv target /destination

# Creates a file
$ touch [filename]

# Creates a directory
$ mkdir [dirname]
```

### Opening your favorite text editor from the terminal
You will often be in the terminal, so it's nice to have the ability to open files and directories quickly from the terminal.
* Launch the command palette in Visual Code Studio
* F1 or shift+cmd+P for Mac
* search 'shell command'
* click: 'Shell Command: install 'code' command in path
* Restart your terminal
* Now you can navigate to the directory you want to open in Visual Studio Code and open it by typing `code .` (the period refers to the current location)

### Editing files using VIM (basics)
Sometimes it's convenient to update files from the terminal as well, so let's learn the basics of doing this as well!
* Open a file by typing `vim [filename]`
* To edit a file press `i`, this will enter "insert mode"
* To exit "insert mode" press esc
* Once you are done and want to save and exit, make sure to escape insert mode, press ":", type "x" and press Enter (this will save and quit, alternatively use "q!" to quit without saving, or "w" to save and stay in the file)
* You may encounter the editor "nano" as well - in case you do, there will be commands listed at the bottom, unlike VIM


### Using the basic commands of git: git add, git status, git commit, git clone, git stash, git pop
Git is a clumsy tool at first, and not exactly intuitive, but it will grow on you over time. It's very useful for collaborative work and keeping track of changes in your code.
``` bash
# Initializes an empty repository
$ git init

# Creates a file where you can list files and directories which should be ignored by git
touch .gitignore

# Connects your initalized repo with github
$ git remote add origin [repo]

# Tells you the current status of your git repository
$ git remote add origin [repo]

# Lists the commits for the branch you're currently on
$ git log

# Adds the file/directory to your "stage"
git add [filename/directory]

# Adds all unstaged things to the stage
git add all

# Takes everything from the stage, and creates a commit with the message specified
$ git commit -m "<message>"

# Pushes your commits to the branch 
$ git push origin [branch_name]

# Pulls the latest changes from a branch
$ git pull origin [branch_name]

# Clones a github repository (always use SSH rather than HTTPS)
$ git clone [repository url.git]

# Copies the current branch you're on and creates a new one
$ git checkout -b [new_branch_name]

# Lists all the branches for your repository
$ git branch -a

# Takes you to the specified branch
$ git checkout [branch_name]

# merges the branch you named, into the one you're currently on
$ git merge [branch_name]
```