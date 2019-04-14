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
