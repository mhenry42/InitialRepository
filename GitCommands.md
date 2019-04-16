# Git Commands

## Getting Started
First, setup your username and e-mail address which will accompany your commits to your remote repository:

```
	git config --global user.name "YOUR_USERNAME"
	
	git config --global user.email "your_email_address@example.com"
```

You can then confirm that your username and e-mail address set correctly by running the following:

```
	git config --global --list
```

Navigate to the folder where the files you want to track are located.

If this is the first time this folder has been setup for tracking, run the command:

```
	git init
```

This will create a hidden folder called /.git/ which will contain the necessary components to keep track of changes to the files/folders in your project.

## Setting Up Remote Repository
If you want to copy a remote repository to your local, use the git clone command.  This will create a copy on your local and create a /.git/ folder to keep track of the changes made

```
    git clone https://github.com/mhenry42/MyRepository.git
```

Navigate to the root local folder (where the /.git/ folder is located) and then run the following to setup the remote repository:

```
    git remote add origin https://github.com/mhenry42/MyRepository.git
```

If the remote repository already exists under that name, you can run the following to see the details:

```
    git remote -v
```

To remove a remote repository from your local settings, run the following (in this example, the remote is named origin):

```
    git remote rm origin
```

## Adding, Committing, and Pushing Files
Running the following will show you files that are tracked/untracked:

```
    git status
```

To add files that are marked as untracked files, you can run the following command:

```
    git add <file>
```

If changes were made to multiple files and folders, you can run the following to add all to be tracked

```
    git add .
```

To commit the file to the remote repository, run the following:

```
    git commit -m "Adding <file> for first time"
```

To push the committed files to the remote repository, run the following (you will be prompted to input your github username and password):

```
    git push -u origin master
```

If any changes are made to the file on your local machine, you need to add the files to the staging area, commit those changes, and push to the remote repository:

```
    git add README.md

    git commit -m "Made <list of changes> to <file>"

    git push -u origin master
```

## Viewing changes made

To see the changes made to the local file versus the remote file, run the following:

```
    git fetch origin master

    git diff FETCH_HEAD -- <file>
```

To view the commits that have been made, run the following:

```
    git log
```

## Rolling back changes

Using the Commit ID in the log, you can roll back a specific file from a specific Commit ID using (be sure to commit after roll back to finalize):

```
    git checkout COMMIT_ID FILE_NAME
```

If you want to undo all changes since the last commit, run the following:

```
    git reset --hard
```

## Pull current version from remote repository

To pull down the latest version of the remote repository to your local computer and have your local computer update to match the remote repository

```
    git pull origin master
```

If you have made changes to your local and changes have also been made to the remote repository, you may receive message:

"error: Your local changes to the following files would be overwritten by merge: Another file ________ Please, commit your changes or stash them before you can merge. Aborting"

If that occurs, you need to complete the following to save your changes locally and merge the remote and local together in the local copy.

```
    git add .
    git commit -m "notes about changes made to local copy"
```

You then need to push your local changes to the remote repository.

```
    git push -u origin master
```