# Version Control
VC is a system that records version of a file or a set of files so that you can recall specific versions later.

Git is a **DVCS** - Distributed Version Control System

# GIT 
Git has 3 main states that files can reside in: commited, staged, modified.

**Committed** - the files is safely stored in the local database
**Staged** - you have marked a modified files in its current version to go into your next snapshot
**Modified** - you have changed the file but have not commited it to be store in the local database

# First time GIT setup

**git config** - gets and sets user configuration variables that control all aspects of how GIT looks and operates

**git config --global user.name "eduard"**
**git config --global user.email "email@email"** 

This will set the config variables global and will be remembered throughout your projects.
To override write the same command without the --global
e.g: **git config user.name "Eduard name"**

**git config --global core.editor code** - changes the default editor (when git asks you to type a command) to vs code ("code")
**git config --list** - reveals all the configuration rules

To reaveal a particular git configuration type:
**git config user.name**(user.name stands for the name of the configuration)

# Getting Help
**git help verb** 
e.g: git help config

# Git Basics

**git init** - initializes a git repository, however it does not track your files yet.

## Cloning a repository
*git clone <repository-name>* - clones a repository

## Checking the status of a file
*git status*

## Add a file to the staging area
**git add <file-name>** 

!Note - **git add** is a multipurpose command, it is more like add this content to the next commit

## See the status
*git status*

## See the short status
*git status -s* - shows the short status with abreviation in front of every file
List of abbreviations:
**??** - files untracked
**A** - new files added to the staging area
**M** - file is modified but not yet staged

## To inform GIT that it should ignore some files create an .gitignore file
In gitignore you can use the special characters:
1. "#" and blank lines are ignored 
2. Standard glob patterns work
3. you can end patterns with a / to specify a directory
4. You can negate a pattern by starting with !

https://github.com/github/gitignore

## Glob patterns
1. * - matches 0 or more characters
2. [abc] - matches any character inside the brackets (a, b or c in this case)
3. ? - matches a single character
4. [0-9] - matches any character between the characters inside the brackets (0 to 9 in this case)
5. ** - you can use this to match nested directories

# To see what you changed instead of git status do
git diff - compares what is in the working directory against what is in the staging area
git diff --staged - compares what you have in your staging area and goes into the commit

# Commit
If you would like to change the default editor when you type a commit message type:
**git config --global core.editor "<editor-name> -w"** - the "-w" tells git to wait until you typed a message.
**git commit -a -m "name of the message"** - the "-a" flag stages your files and commits in one go

# Removing files
**git rm <filename>**
*add "-f" option* - to force the removal

git rm log/\*.log - can remove patterns of files. Note the "\" in front of the special character.

# Moving files

**git mv file_from file_to**

# Viewing the commit history

**git log** - shows a logging history
git log --pretty=oneline
git log --pretty=short
git log --pretty=full
git log --pretty=fuller

The most interesting is the 
**git log --pretty=format:"%h - %an, %ar : %s"**

Useful options
1. %H Commit hash
2. %h Abbreviated commit hash
3. %T Tree hash
4. %t Abbreviated tree hash
5. %P Parent hash
6. %p Abbreviated parent hash
7. %an Author name
8. %ae Author e-mail
9. %ad Author date (format respects the –date= option
10. %ar Author date, relative
11. %cn Committer name
12. %ce Committer e-mail
13. %cd Committer date
14. %cr Committer date, relative
15. %s Subject


Another useful option is **--graph** which adds a nice ASCII graph to the commit log.
e.g: **git log --pretty=oneline --graph** 

# Common Options to git log

1. -p  - Show the patch introduced with each commit.
2. --stat - Show statistics for files modified in each commit.
3. --shortstat - Display only the changed/insertions/deletions line from the --stat command.
4. --name-only - Show the list of files modified after the commit information.
5. --name-status - Show the list of files affected with added/modified/deleted information as well.
6. --abbrev-commit - Show only the first few characters of the SHA-1 checksum instead of all 40.
7. --relative-date -  Display the date in a relative format (for example, “2 weeks ago”) instead of using the full date
format.
8. --graph - Display an ASCII graph of the branch and merge history beside the log output.
9. --pretty -  Show commits in an alternate format. Options include oneline, short, full, fuller, and format
(where you specify your own format).




# Limiting Log Output
**git log -n** - shows the n number of commits
e.g: git log -2 - last two commits
**git log --since=2.weeks**

Options to limit the output log

1. -(n) Show only the last n commits
2. --since, --after Limit the commits to those made after the specified date
3. --until, --before Limit the commits to those made before the specified date
4. --author Only show commits in which the author entry matches the specified string
5. --committer Only show commits in which the committer entry matches the specified string
6. --grep Only show commits with a commit message containing the string
7. -S
You can specifiy multiple limiting criterias:
e.g: **git log --author="Eduard" --grep="asd" --match-all**
!Note - in order to filter logs based on both author and grep (commit msg) you need to pass **--match-all** option


# Undoing things
**git commit --amend**


# Unmodifying a modified file
**git checkout -- <file-name>**
eg. git checkout -- Readme
!Note - this is a dangerous method, it basically overwrites your file



# Working with remotes
git remote 
git remote -v - shows the url

## Adding remote repositories
git remote add [shortname] [url]
e.g: git remote add ab https://github.com/asdasd
Now you can reference the repository after the shortname.
e.g: git fetch ab

!Note - **git fetch** only pulls data to your local repository and you have to merge it manually
**git pull** - does the merge for you


# Pushing to Your Remotes
**git push [remote-name] [branch-name]**

To see more info about a remote
git remote show origin

# Removing and renaminig remotes
**git remote rename [old-name] [new-name]**
TO remove a remote
**git remote rm [name]**


# Git Aliases
**git config --global alias.co checkout**
**git config --global alias.br branch**
**git config --global alias.last 'log -1 HEAD'**



# Branches

## To create a bracn
**git branch [name]**
**git log --decorate** - shows the branches and the HEAD
**git checkout [branch-name]** - changes the branch


To see the branches in a full way
**git log --oneline --decorate --all --graph**

**git checkout -b iss53** - creates and switches to the new branch
**git merge [branch-name]** - merges the branch
**git branch -d [branch-name]** - delets the named branch


Display all branches:
**git branch**
 To delete a branch
 **git branch -d [branch-name]**
 To force deletion use **-D** flag