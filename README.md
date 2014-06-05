#Useful Git Commands

##About it
> I have recently started using git professionally and on a daily basis and I really don't look back! This is a lits of useful Git commands and descritptions I have put together which helps me quickly find stuff I need.

## Table of contents

* [Install git](#install-git)
* [Setting up git](#setting-up-git)
* [Applying colour to git ](#applying-colour-to-git)
* [Initializing a repository in an existing directory](#initializing-a-repository-in-an-existing-directory)
* [Checking the status of your files](#checking-the-status-of-your-files)
* [Staging files](#staging-files)
* [Committing files](#committing-files)
* [Branching and merging](#branching-and-merging)
* [Resetting HEAD](#resetting-head)
* [Useful tricks](#useful-commands)
* [Contributing](#contributing)

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
#### Checking the status of your files

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

#### Staging files

After initializing a git repository in the chosen directory, all files will now be tracked. Any changes made to any file will be shown after a $ git status as changes not staged for commit.

To stage changes for commit you need to add the file(s) - or in other words, stage file(s).

```sh
# Adding a file
$ git add filename

# Adding all file
$ git add -A

# Adding a all files changes in a directory
$ git add .
```

#### Committing files

After adding/staging a file, the next step is to commit staged file(s)

```sh
# Commit staged file(s)
$ git commit -m 'commit message'

# Amending a commit
$ git commit --amend 'new commit message' or no message to maintain previous message
```

#### Branching and merging

Creating a local branch

```sh
$ git checkout -b branchname
```

Pushing local branch to remote

```sh
$ git push -u origin branchname
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

##### Merging branch to trunk/master

```sh
# First checkout trunk/master
$ git checkout trunk/master

# Now merge branch to trunk/master
$ git merge branchname

# To cancel a merge
$ git merge --abort
```


##### Resetting HEAD

```sh
# Upstream master
$ git reset HEAD origin/master -- filename

# The version from the most recent commit
$ git reset HEAD -- filename

# The version before the most recent commit
$ git reset HEAD^ -- filename

# Move head to specific commit
$ git reset --hard sha

# Reset the staging area and the working directory to match the most recent commit. In addition to unstaging changes, the --hard flag tells Git to overwrite all changes in the working directory, too.
$ git reset --hard
```

##### Useful commands 

```sh
# Number os commits by author
$ git shortlog -s --author 'Author Name'

# List of commits by author
$ git log --author 'Author Name'

# List of commit comments by author
$ git shortlog -n --author 'Author Name'
#This also shows the total number of commits by the author

# Number of commits by contributors
$ git shortlog -s -n
```


### Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request - cheers!





