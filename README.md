#Useful Git Commands

##About it
I have recently started using git professionally and on a daily basis and I really don't look back! This is a lits of useful Git commands and descritptions I have put together which helps me quickly find stuff I need.

## Table of contents

* [Install git](#install-git)
* [Setting up git](#setting-up-git)
* [Applying colour to git ](#applying-colour-to-git)
* [Initializing a repository in an existing directory](#initializing-a-repository-in-an-existing-directory)
* [Checking the status of your files](#checking-the-status-of-your-files)

#### Git 

Git is a distributed version control system, very easy to learn and supper fast!

#### Install Git 

There are a few different ways to install git (from source or for Lynux) but the pupose of this page is to focus on git commands, so I am going to assume you are installing git on a Mac.

To view other ways of installing it visit the [Git official site](http://git-scm.com/book/en/Getting-Started-Installing-Git)

Click [here](http://git-scm.com/download/mac) to download and install Git

#### Setting up git

```sh
$ git config --global user.name "User Name"
```
```sh
$ git config --global user.email "email"
```

#### Applying colour to git 

```sh
$ git config --global color.ui true
```

#### Initializing a repository in an existing directory

If you’re starting to track an existing project in Git, you need to go to the project’s directory and type:

```sh
$ git init
```
This creates a new subdirectory named .git that contains all of your necessary repository files — a Git repository skeleton. At this point, nothing in your project is tracked yet. 

To start version-controlling existing files you should start by tracking those files and do an innitial commit. To accomplish that you should start with a few  `$ git add` that specifies the files you want to track followed by a commit.

```sh
$ git add *.c
$ git add README
$ git commit -m 'Initial project version'
```
#### Checking the Status of Your Files

The main tool you use to determine which files are in which state is the `$ git status` command. If you run this command directly after a clone, you should see something like this:

```sh
$ git status
# On branch master
nothing to commit (working directory clean)
```

If you add a new file to your project, if the file didn\'\t exist before and you run a `$ git status` you should see your untracked file like this:

```sh
$ vim README
$ git status
# On branch master
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#   README
nothing added to commit but untracked files present (use "git add" to track)
```

#### Branching and merging

Creating a local branch

```sh
$ git checkout -b branchname
```

Deleting a local branch

```sh
$ git branch -D branchname
```

Viewing all branches, including local and remote branches

```sh
$ git branch -a
```

Viewing local branches

```sh
$ git branch
```

Viewing remote branches

```sh
$ git branch -r
```

##### Fetching and checking out remote branches

```sh
$ git fetch origin
```

This will fetch all of the remote branches for you. With the remote branches in hand, you now need to check out the branch you are interested in, giving you a local working copy:

```sh
$ git checkout -b test origin/test
```
Deleting a remote branch

```sh
$ git branch -rd origin/branchname

$ git push origin --delete branchname  or  $ git push origin:branchname
```







