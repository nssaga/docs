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


