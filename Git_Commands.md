## Set the global details
```
git config --global user.name "Nawal Sah"
git config --global user.email "nawal@example.com"
```
Use ``` --global ``` To set the configuration for all projects. If ``` git config ``` is used without ``` --global ``` and run inside a project directory, the settings are set for the specific project.

## Make git ignore file modes
``` 
cd project/
git config core.filemode false
```
This option is useful if the file permissions are not important to us, for example when we are on Windows.

## See your settings
```
git config --list
```

## Initialize a git repository for existing code
```
cd existing-project/
git init
```

## Clone a remote repository
```
git clone <repository_url>
```
Example ``` git clone https://github.com/nssaga/docs.git ```


This creates a new directory with the name of the repository.

## Clone a remote repository in the current directory
```
git clone https://github.com/nssaga/docs.git .
```
``` . ``` at last represent the current directory.


## Clone a remote repository from specific branch
```
git clone <repository_url> --branch <branch_name>
```

Example ``` git clone https://github.com/nssaga/docs.git --branch feature/change ```
## Sample gitignore file
https://github.com/nssaga/docs/blob/master/Eclipse%20Java%20gitignore


## Help for a specific git command
``` git help <command_name> ```
Example ``` git help clone ```

## Update and merge your current branch with a remote
```
cd repository/
git pull origin master
```

Where origin is the remote repository, and master the remote branch. If you don't want to merge your changes, use ``` git fetch ```

## View remote urls
```
git remote -v
```

## Change origin url
``` git remote set-url origin http//github.com/repo.git ```

## Add remote
``` git remote add remote-name https://github.com/user/repo.git ```

## See non-staged (non-added) changes to existing files
``` git diff ```

**Note that this does not track new files.**

## See staged, non-commited changes
``` git diff --cached ```

## Print out differences between your working directory and the index.
``` git diff (no parameters) ```

## Print out differences between your working directory and the HEAD.
``` git diff HEAD ``` 

## Show only names of changed files.
``` git diff --name-only ``` 

## Show only names and status of changed files.
``` git diff --name-status ``` 

## Word by word diff instead of line by line.
``` git diff --color-words ``` 

## See differences between local changes and master
``` git diff origin/master ```

Note that origin/master is one local branch, a shorthand for refs/remotes/origin/master, which is the full name of the remote-tracking branch.

## See differences between two commits
``` git diff <COMMIT1_ID> <COMMIT2_ID> ```

## See the files changed between two commits
```
git diff --name-only <COMMIT1_ID> <COMMIT2_ID>
```

## See the files changed in a specific commit
``` git diff-tree --no-commit-id --name-only -r <COMMIT_ID> ```

or

``` git show --pretty="format:" --name-only <COMMIT_ID> ```

Source: http://stackoverflow.com/a/424142/1391963

## See diff before push
```
git diff --cached origin/master
```

## See details (log message, text diff) of a commit
``` git show <COMMIT_ID> ```

## Check the status of the working tree (current branch, changed files...)
``` git status ```

## Make some changes, commit them
```
git add changed_file.txt
git add folder-with-changed-files/
git commit -m "Commiting changes"
```

## Rename/move and remove files
``` 
git rm removeme.txt tmp/crap.txt
git mv file_oldname.txt file_newname.txt
git commit -m "deleting 2 files, renaming 1"
```

## Change message of last commit

```
git commit --amend -m "New commit message"
```

## Push local commits to remote branch
```
git push origin master
```

## See recent commit history
``` git log ```

## See commit history for the last two commits
``` git log -2 ```

## See commit history for the last two commits, with diff
``` git log -p -2 ```

## See commit history printed in single lines
``` git log --pretty=oneline ```

## Revert one commit, push it
```
git revert <commit_id>
git push origin master
```

## Revert to the moment before one commit
### reset the index to the desired tree
``` git reset <commit_id> ```

### move the branch pointer back to the previous HEAD
``` 
git reset --soft HEAD@{1}

git commit -m "Revert to commit id"
```

### Update working copy to reflect the new commit
git reset --hard

Source: http://stackoverflow.com/q/1895059/1391963

## Undo last commit, preserving local changes
```
git reset --soft HEAD~1
```

## Undo last commit, without preserving local changes
```
git reset --hard HEAD~1
```

## Undo last commit, preserving local changes in index
```
git reset --mixed HEAD~1
Or git reset HEAD~1
```

### See also http://stackoverflow.com/q/927358/1391963

## Undo non-pushed commits
``` git reset origin/master ```

## Reset to remote state
``` 
git fetch origin
git reset --hard origin/master
```

## See local branches
`` git branch ```

## See all branches
``` git branch -a ```

## Make some changes, create a patch
``` git diff > patch-issue-1.patch ```

## Add a file and create a patch
``` 
git add newfile
git diff --staged > patch-issue-2.patch
```

## Add a file, make some changes, and create a patch

```
git add newfile
git diff HEAD > patch-issue-2.patch
```

## Make a patch for a commit
``` git format-patch COMMIT_ID ```

## Make patches for the last two commits
``` git format-patch HEAD~2 ```

## Make patches for all non-pushed commits
``` git format-patch origin/master ```

## Create patches that contain binary content
``` git format-patch --binary --full-index origin/master ```

## Apply a patch
``` git apply -v patch-name.patch ```

## Apply a patch created using format-patch
``` git am patch1.patch ```

## Break up multiple changes into separate commits (or commit only part of a changed file)
``` git add --patch file.txt
(press 'y' for the chunks to add)
git commit -m 'first part of the file'
```

(repeat if desired)

Sources: https://stackoverflow.com/q/4948494/1391963, https://stackoverflow.com/q/1085162/1391963

## Create a tag
``` git tag 7.x-1.3 ```

## Push a tag
``` git push origin 7.x-1.3 ```

## Create a branch
```
git checkout master
git branch new-branch-name
```

###### Here ``` master ``` is the starting point for the new branch. Note that with these 2 commands we don't move to the new branch, as we are still in master and we would need to run ``` git checkout new-branch-name ```. The same can be achieved using one single command: ``` git checkout -b new-branch-name ```


## Create a branch from a previous commit
```
git branch branchname sha1-of-commit
```

or using a symbolic reference (e.g. last commit):

```
git branch branchname HEAD~1
```

## You can also use
```
git checkout -b branchname sha1-of-commit
```

Source: http://stackoverflow.com/a/2816728/1391963

## Checkout a branch
```
git checkout new-branch-name
```

## See commit history for just the current branch
```
git cherry -v master
```

### (master is the branch you want to compare)

## Merge branch commits
```
git checkout master
git merge branch-name
```

### Here we are merging all commits of branch-name to master.

## Merge a branch without committing
```
git merge branch-name --no-commit --no-ff
```

## See differences between the current state and a branch
```
git diff branch-name
```

## See differences in a file, between the current state and a branch
```
git diff branch-name path/to/file
```

## Delete a branch
```
git branch -d new-branch-name
```

## Push the new branch
```
git push origin new-branch-name
```

## Get all branches
```
git fetch origin
```

## Get the git root directory
```
git rev-parse --show-toplevel
```

### Source: http://stackoverflow.com/q/957928/1391963

## Remove from repository all locally deleted files
```
git rm $(git ls-files --deleted)
```

### Source: http://stackoverflow.com/a/5147119/1391963

## Delete all untracked files
``` git clean -f ```

### Including directories:

``` git clean -f -d ```

### Preventing sudden cardiac arrest:

``` git clean -n -f -d ```
### Source: http://stackoverflow.com/q/61212/1391963

## Delete all files from a git repository that have already been deleted from disk:
```
git ls-files --deleted -z | xargs -0 git rm
````

###### Source (and alternatives): https://stackoverflow.com/a/5147119/1391963

Show total file size difference between two commits
Short answer: Git does not do that.
Long answer: See http://stackoverflow.com/a/10847242/1391963

## Reload locally deleted file from remote:
```
git checkout HEAD <path>
```

eg: ``` git checkout HEAD . ```
###### . represent current directory

## Unstage (undo add) files:
```
git reset HEAD file.txt
```

## See previous git commands executed
```
history | grep git
or

grep '^git'  /root/.bash_history
```

## See recently used branches (i.e. branches ordered by most recent commit)
```
git for-each-ref --sort=-committerdate refs/heads/ | head
```

## Switch to another branch
```
git checkout -b <new branch name>
```

Source: http://stackoverflow.com/q/5188320/1391963

