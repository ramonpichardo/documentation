# Git Primer

### Basic Git Workflow

| Working Directory      | -->       | Index              | -->          | Repository          |
|:----------------------:|:---------:|:------------------:|:------------:|:-------------------:|
| Make changes to files: | `git add` | Bring changes into | `git commit` | Save changes to the |
| + additions            |           | the staging area   |              | repo as a "commit"  | 
| - deletions            |           |                    |              |                     |
| modifications          |           |                    |              |                     |

* `git init` - The word *init* means initialize. The command sets up all the Git tools to track changes to the project. Run this command inside the folder for this project.  
* `git status` - Check the status of the changes.  
* `git add <filename>` - Add a file by its filename to the staging area.  
* `git diff <filename>` - Check the difference between files in the working directory and staging area.  
* `git log` - View commits stored chronologically. The most recent commit is shown first.  
* `git commit -m "message"` - Permanently store changes from the staging area inside the repository.  
```
Standard conventions for commit messages:  
- Must be in quotation marks  
- Written in the present tense  
- Be brief (i.e., 50 characters or less)  
```

### Backtracking

* `git show HEAD` - In many cases, the most recently made commit is the `HEAD` commit. `HEAD` must be typed in uppercase. Type this command to see the `HEAD` commit. Take note of the 40-character alphanumeric SHA; or at least the first seven characters of that string.  
* `git checkout HEAD <filename>` - Restore the file in your working directory to the last commit made.  
* `git reset HEAD <filename>` - Unstage a file from the staging area. Useful for unwanted adds to the staging before a commit.  
* `git reset <SHA>` - Rewind your project to a previous commit. For the SHA, use the first seven characters of the alphanumeric string.  
```
Notes:  
- Run "git log" to view the Git commit log.  
- The commits that came after the one you reset to are gone.  
- The HEAD commit is reassigned to the reset-to commit. I.e., the HEAD designation is reassigned to a previously made commit of your choice.  
```

### Branching

* `git branch` - Check what branch you are currently on. The line with an asterisk shows you which branch you are on. List all of a Git project's branches.  
* `git branch <new_branch>` - Creates a new branch. Note: Branch names cannot contain spaces. Dashes and underscores in a branch name are valid characters to use.  
* `git checkout <branch_name>` - Switch to a branch named branch_name.  
* `git merge <branch_name>` - Include all changes made on another branch that is not "master". First, switch from the other branch to "master" branch. Then merge changes on another branch by invoking this command with the branch_name being the other branch's name that is not "master".  
* `git branch -d <branch_name>` - Delete a branch named branch_name. This is usually done after a merge.  
