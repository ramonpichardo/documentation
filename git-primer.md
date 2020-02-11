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

### Create a local working directory on your development computer
E.g., `mkdir /home/username/working/`  

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

### Teamwork

* `remote` - a shared Git repository that allows multiple collaborators to work on the same Git project from different locations.  
* `git clone <remote_location> <clone_name>`  
```
Notes on git clone:
- Creates a replica of a repo on your computer.  
- Remote location can be a web address or a file path.  
- Clone_Name is the name you give to the directory in which Git will clone the repo.  
```
* `git remote -v` - List the remotes of a Git project. Git automatically names the remote "origin" because it refers to the remote repo of origin. However, it is possible to safely change its name.  
* `git fetch` - See of changes have been made to the remote and bring the changes down to your local copy. First '`cd`' to cloned directory. Then run `git fetch`.  
* `git merge origin/master` - After new commits are fetched to your local copy those commits are on the origin/master branch. We will need to use git merge to integrate origin/master into the local master branch.  
* `git push origin <branch_name>` - Push a local branch to the origin remote.  

### Typical Collaborative Workflow

1. Fetch and merge changes from the remote.  
2. Create a branch to work on a new project feature.  
3. Develop the feature on your branch and commit your work.  
4. Fetch and merge from the remote again (in case new commits were made while you were working).  
5. Push your branch up to the remote for review.  
