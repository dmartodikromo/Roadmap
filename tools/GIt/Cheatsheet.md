this is a cheatsheet of git commands that you will encounter most frequently.

# intro

git is a version control system(VCS) for tracking changes in computer files.

1. distributes version control

2. coordinates work between multiple developers

3. track who made changes and when

4. revert back changes

5. designed for remote and local repositories

# concepts of git

1. keeps track of code history

2. takes snapshots of your files

3. decide when to take a snapshot by making a commit

4. visit any snapshot anytime

5. you can stage files before commiting

# basic commands

```bash
git init
```

> initialize local git repository.

$ git add <file>

//add files to index

$ git add * .filetype

//add all files with specified filetype

$ git add .

//add all files

$ git status

//check status of working tree. you can view staged files, unstaged files, modified files.

$ git commit

//commit changes in index. terminal will open. 'i' for inserting text.

'esc' to go into the editor. 'wq' to commit the file.

$ git commit -m 'type message here'

//commit changes to master and add a commit message

$ git push

//push to remote repository

$ git remote add origin <url>

//add a link to a remote repository

$ git push -u origin master

//push the code to the remote repository specified location

$ git pull

//pull latest version of files from a remote repository

$ git clone

//clone repository into a new directory. copy a remote repo.

$ git --version

//check the current version of your git

$ touch <file>

//create a file

$ git config --global user.name 'name'

//add your name to git

$ git config --global user.email '@email.com'

//add your email to git

$ git rm --cached <file>

//remove file to unstage

$ git branch <name>

//create a branch to work in instead of the main branch

$ git checkout <name>

//switch to another branch to work in. if you switch to the master

the changes will not be visible.

$ git merge

//merges the branch to master. a terminal will appear like the

commit one.

$ git-credential-store - Helper

//stores your credentials on your device