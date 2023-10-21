# Version Control

* Revision history provides history of all changes
* Identity: Who is responsible for a change

## Centralized Version Control System (CVCS)

Consist of Server and Client. The Server contains the Code with the full history of the code base. The Client needs to pull/clone (copy) the code to itself. Each client has a copy of the latest code. When a change is made it has to be pushed to the repository server. 

* Easier to learn
* More access control to users
* Slower

## Distributed Version Control System (DVCS)

Each client is also a server. Each client has the entire history.

* No connection to server needed
* Only need to connect to push or pull changes
* Speed is better than with CVCS

## Continuous Integration (CI)

Automate integration of code from multiple developers into single main stream. A workflow where many small changes are merged frequently reduce the number of conflicts. 

CI is often used to to automatically compile the code and run tests to make sure that the software stays stable. (github actions)

## Continuous Delivery (CD)

Extension of CI to automatically package application and prepares it for deployment. Avoids human error when packaging. Instead of running everything manually each time a new version has to be shipped this is done automatically. Just has to be defined once.

## Contiunous Deployment

An extension of continuous delivery. Usually the packaged application is usually deployed to a test/staging environment first to validate that it works. Once it has been validated it can automatically be pushed to production. 

### Staging

### Production

It is never a good idea to migrate databases in a production environment. If it does break the database there is no easy way to undo that.

## MORE
* [Getting started with Version Control](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)
* [What is Cloning](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository)


# Command Line

``` bash
cd /path/to/dir
touch file.txt
```

## Pipes

Pipes allow you to redirect output from one command to the input of another command

## Redirection

Each program has an input and an output. The stdin (standard input) is usually the keyboard and the stdout (standard output) is usually the screen. 

Redirection makes it possible to change stdin, stdout and stderr.

``` bash
# Redirect stdin from cat to input.txt
cat < input.txt

# Redirect stdout from ls to output.txt
ls -l > output.txt
```

The commands above **do not** work with the **|** symbol, because *input.txt* and *output.txt* are not commands. The Pipe command is used to connect stdout from one command to stdin from another one. 

To redirect *stderr* simply add a 2 to the redirection symbol.

``` bash
ls -l 2> error.txt
```

To redirect both **stderr** and **stdout** add an &1.

``` bash
ls -l > err_stdout.txt 2>&1
```

## GREP (Global Regular Expression Print)

``` bash
# Case insensitive
grep -i Abc file.txt

# Match exactly
grep -w Abc file.txt

# Find programs containing zip (mac)
ls /usr/bin | grep zip
```

## MORE

* [Agile Methodologies](https://www.planview.com/resources/guide/agile-methodologies-a-beginners-guide/)
* [Bash reference manual](https://www.gnu.org/software/bash/manual/html_node/index.html#SEC_Contents)
* [Bash scripting cheat sheet](https://devhints.io/bash)
* [Vim cheatsheet](https://vim.rtorr.com/)


# GIT

Version control system developed by Linus Torvalds. 

**Github** is a cloud based servive that hosts git repositories and extends them by offering more features on top (automation, access control, ...)

Github is a **remote** repository while the one on my machine is called **local**

## Cloning a Repository

To clone with SSH a ssh key needs to be added to the github account
To clone with HTTPS a token has to be generated

## Git Workflow

The git workflow consists of 3 Stages

1. Modified - Adding, removing or updating any file is a modification. Git does not track this but knows that there have been changes made. 
2. Staged - In order for git to track a file it has to be **added** to the staging area. 
3. Committed - Like a save point. Git takes a snapshot of the current changes. 


``` bash
# Add a file to the staging area
git add <file>


# To remove a file from the staging area
git restore --staged <file>

# Show repository status
git status

# Create a branch and switch to it
git checkout -B 'feature/lesson'

# List, create or delete branches
git branch --help
```

## Git Branches

Git branches exist in isolation and have to be merged back into the main branch so that the changes will be 'recognized'.

### Pull request

Obtain a peer review of changes made to a branch i.e. to validate that the changes are correct. 


## Resolving conflicts

Conflicts typically occur when trying to merge a branch with competing changes. These competing changes need to be resolved by the end user. This is called **merging** or **rebasing**.

A merge conflict example is when two developers work on their dependent branches. Both developers are working on the same file called Feature.js. Each of their tasks is to add a new feature to an existing method. Developer 1 has a branch called feature1, and developer 2 has a branch called feature2. 


### HEAD

Head is a file in the *.git* folder. It refers to the current commit I am viewing. 

### Blame

`git blame -L start,end <file>`




