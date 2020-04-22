# Git and Github guide
In this brief guide we are going to learn the basics of different functions Git and GitHub has to offer, including:
1. Getting Started with Git
2. Repository creation
3. Staging
4. Commiting
5. Checkout, Revert and Reset
6. Branches
7. GitHub
  1. Creating a repository in GitHub
  2. Making changes in GitHub
  3. Team work

## Getting Started with Git
After getting [Git](https://git-scm.com/downloads) installed, we are going to set up the default user
name and email.

In order to set up username and email, type these commands in the console:

Username
```
  git config --global user.name sampleusername
```
Email
```
  git config --global user.email sampleuseremail@gmail.com
```
If you want to visualize the global user name and email, type these commands:

Username
```
  git config user.name
```
Email
```
  git config user.email
```

### Previous definitions
Before starting to create a repository and type commands, some concepts are
necessary to understand the dynamics Git and Github offer:
1. Repository : A repository is a container for a project which is going to
   be tracked with Git. An user can have as many repositories as he/she wants
   on the computer.
2. Commit : A commit is the statement of a change done in a repository,
   whenever the user does a commit, it saves these changes, these are saved
   in order to return into them at any moment.
3. Branch : Every project has at least one branch, which is the master branch,
   branches are the workflow of a process in a project, for example, adding a
   new feature can be done in a branch, then when it comes the moment to add
   that feature into the project, it is merged into the master branch, hence,
   the master branch defines the project's main thread.

## Repository creation
Before creating a repository, we need to have at least one folder and file,
to make this task, type these commands:

Folder
```
  mkdir folderName
```
File
```
  touch fileName.extension
```
In addition, having a text editor which recognizes Git is useful,
[Atom](https://atom.io) is a good example of it.

Now, we have a project (it can be a new project) and want to create a
Git repository with it. It is necessary that the following command
is executed in the core folder, where all the project's folders are located:
```
  git init
```
Once the line is executed, the file .Git in our text editor will appear, we
will be able to execute Git commands on the folder.

## Staging
The project is made, we have made a change or executed the previous command
on an existing project, since the master branch is the default branch,
every change actually is going to be located in this branch, once a file
is changed, we can verify which files have been changed with the
following command:
```
  git status
```
It will show us the files that have been changed, these files are only
**modified**, now we are going to add these changes, this process is also called **staging**, to stage a change, type this command:
```
  git add fileChanged.extension
```
If you want to stage all the files at once, type this:
```
  git add -A
  git add .
```
Both of them work. If you type 'git status', you can see that the changes have been staged, they are highlited in green,

Now, if we want to delete a file from our *staging area*, we can type this command:
```
  git rm --cached fileStaged.extension
```
Also, there is a command to remove all the files from the *staging area*:
```
  git reset HEAD --
```  

## Commiting
The files located in our *staging area* are ready to be commited, the
most frequent commit is represented with this command:
```
  git commit -m"a well made message describing the change made"
```  
Remember, every change made can be commited, it is a good practice to be as specific as possible in the commit message.

### The log
All commits we make can be seen with the log command:
```
  git log
```  
This gives us all the information for every commit (ID, Author, branch, date and commit description) made on the repository. For a shorter version of the log, we can type this command:
```
  git log --oneline
```
This will show us a short version of the commit ID, the branch and the
commit description.

## Checkout, Revert and Reset
There are three ways to go back in the project, it could be only see the
previous version, reverting a commit or reseting a commit, these ways are:
* Checkout commit
* Revert commit
* Reset commit

### Checkout commit
This way allows us to see the project when a specific commit was done, it
is only for spectations so it is important to not modify the code when a
checkout is being executed, to checkout a commit, type this command:
```
  git checkout commitID
```
in this 'commitID' we can type either the complete ID, or the reduced ID shown when you type  'git log --oneline', it is easier to type or copy the
reduced ID. You can do this action in the next ways.

At the moment you execute the line within the commit ID, Git will change
the project to the moment when that commit was done, if you are using
Atom, it may not change instantly if the editor is opened, for that case
we can close and open the folder **in the editor**, we don't need to close
the editor and open it once again. If a file is opened before the checkout,
select the file in the editor again to see the file at the moment when the
commit was done, if it does not work, close and open the file **in the editor**.

### Revert commit
This way allows us to revert a change the commit made, however, the
changes made after and before that commit will still remain in the project,
also the reverted commit remains in the commit history, so we could go back to them if we regret to revert that change.
```
  git revert commitID
```
A long text will appear, saying which changes it will do in our project,
to continue, **press Ctrl+x and save the file**. Then, we will see that this
command reverts the changes from the selected commit.

### Reset commit
This way allows us to go back in the project from a specific commit, however,
the changes made after that selected commit will not be able, so **be careful** when using this command.

There are **two ways** to reset a commit

#### The safe way
The safe way is by typing this command:
```
  git reset commitID
```
The changes made after the commit are going to exist, but are not going to
be staged changes, in order to stage and save these changes you will have to add them and commit them, in few words, the commits going after are going to be reduced in one, of course you can change the code as you wish, not necessarily all the changes have to remain in that single commit.

#### The dangerous way
This way will delete all the changes made after the selected commit:
```
  git reset commitID --hard
```
Those deleted changes are not going to be anymore in the project

## Branches
Branches are one of the core features Git has to offer, in few words, it is an environment in which we can modify our project without affecting the project itself, then, when we want to add to the project those modifications we can **merge** it with a commit, ending the life of that branch and updating the master branch, which, as mentioned, is where the project's main thread is located. This Git's feature also enhances the team work experience, since each team's partner can work on different branches at the same time.

### Creating a branch
Creating a branch is quite simple, don't forget that you have to be in the branch where you want to create a new branch, for example, if we are in the master branch, we will create a new branch based on the master branch, by typing this command we will create a new branch:
```
  git branch branchName
```

To enter into this branch, type this command:
```
  git checkout branchName
```
To visualize all the branches, type this command:
```
  git branch
```
If that command doesn't work, add an ' -a' after the branch word.
Also, there is a way we can create a branch and enter into it with one single command:
```
  git branch -b branchName
```

### Merging a branch
After we have created a branch and modified it, we will merge this branch
to the "origin" branch (it is not necessary that all the branches have
to be created on the master branch), in order to do this, go to the "origin" branch first and type this command:
```
  git merge branchName
```
#### Conflicts
In some cases, **more than one branch could work in the same feature
in a project**, it doesn't matter which branch made the commit, what it does matter is that these branches don't know what has the other branches changed in that feature they are working on, so it comes the case when that situation **generates a conflict**, all the branches in this situation made the commit, Git doesn't recognize which branch bellongs to the actual project, when this happens Git notificates that there is conflict at the moment the user wants to merge one of those branches.

When that situation happens, Git firsts allows to merge one of the branches, then, when a second branch wants to be merged, Git notifies the conflict and modifies the project, showing the changes made in the first and second branch, specifiying which branch made what, in order to solve that, we must **modify the project until we know how to integrate all the conflicted changes**. Then, if we have a third branch which also modifies that specific feature, Git once again notifies and modifies the project with the integrated changes made previously and the changes the third branch made, so we must modify the project again and so on with a possible fourth, fifth, ... branch.

Remember, if a conflict exists it probably means there is more than one person working on the project, to **integrate** the conflicted branches it is highly recommendable to communicate with the involved people, in order to consider which branches' content should stay and which should leave.   
### Deleting a branch
After the branch is merged, the typical situation is to delete that branch, to do this, type this command:
```
  git branch -d branchName
```
If the branch is not merged, it will request you to type this command,
since the branch is not merged Git is considering you forgot to merge
it and if that is the case, all the changes made on that branch will not be
available anymore:
```
  git branch -D branchName
```
# GitHub
We know the basics about Git, now, [GitHub](https://github.com) will be the useful environment in which our repositories will be connected in the internet, of course there are other environments that can help us with these tasks, but in this case we are going to focus in GitHub.

Having repositories online is an important upgrade for team working, as every partner has the opportunity to see these repositories and can easily access them by **cloning** a repository and having a copy of the project's repository in their own computers.

A partner of our project wants to add a feature or do a certain change, when that change is done, he/she can **push** up that changes into the online repository, also **merge** to the repository's master branch. Now the other partners can have access to the new changes by **pulling** down the project with that change.

In order to access to GitHub, we must register an account into GitHub.

## Creating a repository in GitHub
There are two forms to create a remote repository in GitHub, the first way is having the local project created and uploading it, and the other is creating it before the existence of a project.

A Github repository has the following characteristics:
1. Name.
2. Public or Private. Public means everyone can see it, private means only the creator or a specific group of users can see it.
3. Readme. It is a document which has general information about the project, it is a good practice to actually have that information in README.
4. gitignore. Defines the type of the project taking into account which environments are we using, for example a framework.
5. License.

### Existing Project
First of all, create a repository in GitHub, there is a green button which says "New", click it and fill the spaces setting the characteristics of the repository.

When the repository is created, you can see a link in the first part of the page, copy that link, other to do it is clicking the button "clone or download", it shows that link we need to copy.

Now, in the console where the project has all the folders, type this command:
```
  git push https://github.com/UserName/RepositoryName.git master
```
We can push other branches but for this case, is the master branch.
It pushes all the project into the Repository, including branches and
commits with all the details (changes, commit messages, branch).

#### Making a change in GitHub
Now that we have a repository in GitHub we can make a change in the repository online, to make a new change we know how is the workflow, first, we make the change, second, add it, and third, commit it, now we push the master branch, taking into account we made the change in the master branch:
```
  git push https://github.com/UserName/RepositoryName.git master
```
This same command can update our project, however, there is an easier way to this in order to save time everytime we update our project, we can add an alias to our repository by typing this code, this alias is going to be 'origin', since it is the default alias of a repository:
```
  git remote add origin https://github.com/UserName/RepositoryName.git
```
Now with this command we can do the same push made previously but with less characters.
```
  git push origin master
```
We can see the changes in the online repository.

**If GitHub constantly request for user name and password, type this command** :
```
  git config --global credential.helper store
```
And then, type this command, it will request user and password once again:
```
  git pull
```

### New project
In this case we follow the first step done in the previous situation, create a repository in GitHub, now with the repository created, we will clone the repository in our computer wit this command, note that the repository will be cloned in the folder we deploy our command line:
```
  git clone https://github.com/UserName/RepositoryName.git
```
And now we got the folder that Git created for the repository, which can be treated as the project's folder.
#### Making a change in GitHub
To make a change we once again know how is the process, change, add and commit, now, we don't have to create an alias for the repository, it is donde automatically, to see that, type this command:
```
  git remote -v
```
Now we push the master branch, taking into account we made the change in the master branch:
```
  git push origin master
```
We can see the changes in the online repository.

## Team work
A simple way to work in team is having one common repository in GitHub, so everyone can have a central core of information.

At the moment we want to work in our group project, we should know if our local project is up to date with the online repository, in order to do this, we type this command :
```
  git pull origin master
```
### Changing the project
To do a certain change, as we have seen, we should create a branch in order to avoid mixing our work with the group main project (the master branch), after we create the branch and make the changes **in the created branch**, we can push our branch in the GitHub repository with this command:
```
  git push origin branchName
```
Now that the branch is pushed, we can see it in the repository, GitHub will recommend us to do a pull request, which means, a request to merge the changes in the master branch. If we click on the "Compare and pull request button" it will shows us a detailed comparison of the changes, comparing the master branch with the branch we have made, we can add a description to describe deeply what we have done and finally click on "Merge pull request", in this process it also notifies if conflicts exists, if not, it will send a message to the work team and finally decide to merge that branch into the master branch, now we can delete that branch.


This is the end of the introductory guide, you can find the original information source of this guide in order to practice and see the process in an actual computer, follow this link to see it : [Git & GitHub Tutorial for Beginners](https://www.youtube.com/playlist?list=PL4cUxeGkcC9goXbgTDQ0n_4TBzOO0ocPR) by The Net Ninja. It also cover the Forking and Contributing, which is basically collaborating with open source repositories made by other users in GitHub.
