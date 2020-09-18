# GIT - Main Command Line ## SUMARY
## SUMARY
### PART 1: Reminder
### PART 2: Main command line
### PART 3: Cancel a commit
### PART 5: Edit GIT History 
### PART 6: GIT Log 
### PART 4: GIT Diff
### PART 7: GIT Release 
### PART 8: GIT Tags
### PART 9: Project Initialisation
### BONUS PART :

# PART 1: Reminder
Don’t forget: the command line help.
* $ git help config
* $ git help push
* $ git help pull
* $ git help branch

## Configuration
Identity Name
* $ git config --global user.name « axel.chenu

Identity Email
* $ git config --global user.email « mail@mail.com »

Editor Tool
* $ git config --global core.editor subl

Diff Tool
* $ git config --global merge.tool filemerge

## Globals lists
* $ git config --list

# PART 2: Main command line
Files status
* $ git status

## Branchs lists
* $ git branch -a

## Branch creation
Two lines: create and switch to the new branch
* $ git branch name_of_the_new_branch
* $ git checkout name_of_the_new_branch
OR
* $ git checkout -b name_of_the_new_branch

## Delete a branch
* $ git branch -d nom_de_ma_branch_local
OR
* $ git push origin --delete name_branch

## Change a branch
* $ git checkout name_branch
GIT --version 2.23
* $ git switch name_branch

## First commit
* $ git add .
* $ git commit -m "initial commit"

## Following commit
* $ git add 
* $ git commit -m «commit message »

## Undo last commit  ## Undo last changes
* $ git reset --hard message_commit
* $ git push --force

##Backdated a commit
* $ git add .
* $ git commit -m "Commit bac »kdated

## Update the local repository 
* $ git pull

## Update the local repository of a specific branch
* $ git pull - u origin My_Branch

## Send your commits to the remote repository
* $ git push

## Send your commits to the remote repository on a specific branch
* $ git push origin My_Branch

## Delete a file from the working directory and index
* $ git rm nom_du_fichier

## Delete a file from the index
* $ git rmg --cached name_files

# PART 3: Cancel a commit

## Cancel commit: the soft version 
Only the commit is removed from Git; your files are still modified.  You can then change your files again if necessary and commit again.

## Cancel the last commit: the soft version 
* $ git reset HEAD^

To indicate which commit you want to return to, there are several notations:
    * HEAD : last commit ;
    * HEAD^ : last last commit ;
    * HEAD^^ : last last last commit ;
    * HEAD~2 : last last last commit ;

## Cancel commit: the hard version 
If you want to undo your last commit and the changes made in the files, you have to do a hard reset. This will cancel all your work without confirmation!

## Undo commits and lose all changes 
* $ git reset --hard HEAD^

## Undo changes to a file before a commit
If you have changed several files but have not yet sent the commit and want to restore a file as it was at the last commit:
* $ git checkout name_branch

* $ git restore name_branch

## Undo/Delete a file before a commit
* $ git reset HEAD -- name_file

# PART 4: Edit GIT History 

## Edit the last commit message
* $ git commit --amend

## The above command loads the last message in the editor,
    * Modify message;
    * Save and exit the editor to take changes into account.

## Add files to the last commit 
* $ git add mon_fichier
* $ git commit --amend

## Edit history with rebase
History of the last three commits 
* $ git rebase -i HEAD~3

### Commands:
    * -p, pick = use commit
    * -r, reword = use commit, but edit the commit message
    * -e, edit = use commit, but stop for amending
    * -s, squash = use commit, but meld into previous commit
    * f, fixup = like "squash", but discard this commit's log message
    * x, exec = run command (the rest of the line) using shell
    * d, drop = remove commit

Note that empty commits are commented out

# PART 5: GIT Log 

## Classic git log
* $ git log

## Displays  X  last commits
* $ git log -n X

## Displays commits for a folder
* $ git log --oneline -- path/to/my_folder

## Displays a set of commits per date
* $ git log --since= DD/MM/YYY --until= DD/MM/YYY

## Representation of the history from HEAD: commit / branch
* $ git log --oneline --graph --decorate

## Representation of the history from a file: commit / branch
* $ git log --oneline --graph --decorate name_file

# PART 6: GIT Diff
Displays the difference between the content of the last commit and the 
working directory. This is what would be committed by git commit -a.
* $ git diff HEAD

Displays the difference between the content pointed to by A and the content pointed to by B.
* $ git diff A B

Diff between a folder present on two branches
* $ git diff master..MA_BRANCH chemin/vers/mon_dossier

# PART 7: GIT Release 

## Create a new release/qwerty_azerty
* $ git checkout -b release/qwerty/azerty

## Change the version number in the root file READ.md.
* $ git commit -a -m « Commit message »

## Move to the dev branch 
* $ git merge release/file_number

### To finalise the release, merge any corrections on the master and dev
* $ git checkout master 
* $ git merge --no-ff release/20212223_01 
* $ git push origin master
OR
* $ git checkout master && git merge --no-ff release/20212223_01 && git push origin master

### Marking the version on the branch master
* $ git tag -a 20212223_01 -m "New realisation 20212223_01" master
* $ git push origin master --tags
OR
* $ git tag -a 20140707_01 -m "New prod 20140707_01" master && git push origin master --tags

#PART 8: GIT Tags

## Returns the list of available tags
* $ git tag
OR
* $ git tag -l
* $ git tag --list

## Create a tag
« -m » create a tags with a message 
* $ git tag -a v1.0 -m « My message for the version 1.0 »

Add a tag from a previous commit
* $ git tag -a v1.0 -m « My message for the version 1.0 » md5_commit

## Check a tag by displaying the information
* $ git tag -v tag_name

## Push a tags on the remote branch 
* $ git push origin tag_name

##Push several tags on the remote branch 
* $ git push origin --tags

# PART 9: Project Initialisation

## Project initialisation
* $ cd path/to/my_filer
* $ touch README.md
* $ echo « My Project » >> README.md
* $ git init
* $ git add README.md
* $ git commit -m "Initial commit"
* $ git remote add origin ....git
* $ git push -u origin master

## Recuperate the repo on GitHub or GitLab
* $ git clone ....git chemin/vers/mon_dossier

Minimum of 2 branches on my repo:
- « develop »: dedicated to development and resolution. 
- « master »: production code. No one should work directly on this branch.

To retrieve your branch develop:
* $ git branch -a
* $ git checkout origin/develop
* $ git checkout -b develop origin/develop
* $ git branch

## Developement : Branch develop
###Prod : Branch Master
Lets go on the master branch 
* git checkout master

Merge the develop branch 
* git merge develop

Push the change
* git push origin master

Go back to the develop branch 
* git checkout develop

# BONUS PART : How to move to GitLb to GitHub on the same project 

Identify on which project we are working 
* $ git remote -v
origin  git@gitlab.com:ACHENU26/javascript-exercices.git (fetch)
origin  git@gitlab.com:ACHENU26/javascript-exercices.git (push)

Delete the branch master from git 
* $ git remote rm origin

Identify on which project we are working 
* $ git remote -v

remote add origin
* $ git remote add origin https://….//

Identify on which project we are working 
* git remote -v  