# SETUP

## INSTALLATION

To download git for all platforms go to [git-scm.com](https://git-scm.com)

To download via CLI on Void Linux run:
```
sudo xbps-install -S
sudo xbps-install git
```

To verify installation run `git --version`

## INITIAL USER SETUP

Configuring user information used across all local repositories.

`git config --global user.email "email@ddress"`  
*Set an email address that will be associated with each history maker*

`git config --global user.name "firstname lastname"`  
*Set a name that is identifiable for credit when reviewing version history*

`git config --global color.ui auto`  
*Set automatic command line coloring for git for easy reviewing.

## SETUP & INIT

Configuring user information, initializing, and cloning repositories.

`git init`  
*Initialize an existing directory as a git repository*

`git clone <URL>`  
*Retrieve an entire repository from a hosted location via URL.*
