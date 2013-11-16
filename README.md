#Useful Git Commands

##About it
I have recently started using git professionally and on a daily basis and I really don't look back! This is a lits of useful Git commands and descritptions I have put together which helps me quickly find stuff I need.

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

#### Innitializing a repository in an existing directory

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










