# Commands

Basic terms and commands used in git.

## Basic Terms

**Directory:** A different word for a folder.  
**Terminal or Command Line:** The interface used for Text Commands.  
**CLI:** Command Line Interface.  
**`cd`:** CLI command to Change Directory.  
**Code Editor:** Application for writing code.  
**Repository:** Project, or the folder/place where your project is kept.  
**GitHub:** A website to host your repositories online.  

## Basic Commands

> [!NOTE]
> Git commands are in lowercase.

**`clone`:** Bring a repository that is hosted somewhere like Github into a folder on your local machine.  
**`add`:** Track your files and changes in Git.  
**`commit`:** Save your files in Git.  
**`push`:** Upload Git commits to a remote repo, like Github.  
**`pull`:** Download changes from remote repo to your local machine, the opposite of push.  

## Using Commands

When you want to commit files always run `git status` first.
This will give you the status of the working tree.
Including what files are new, what files have been modified, and more.

If there are untracked changes you will want to run `git add <file_name>` if there are multiple files that you want to include you can run `git add .` instead. 
*Essentially the . is a wildcard for all.*

When all changes show up under tracked when `git status` is run they are ready to be committed.
We will run `git commit -m "message"` the message will be the title of the message in Github.
This only saves the code locally, to make it live we will use `git push`.

**`git push origin master`:**   
*origin* stands for the location of our git repository.  
*master* is the branch we want to push to.
