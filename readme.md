# Intro to Git
> Quick Links:
> - [Link to Basic Git Command Cheatsheet](./cheatsheet.md)
> - [Screencast: The Homework Submission Process](https://vimeo.com/167925651)

## Overview

In this lesson, we will learn the basics of using Git and see how Git is used with Github, a website for hosting and sharing code.

- Git is a wonderful tool that allows developers to collaborate
- Git has features that give us a safety net for experimenting and writing code, without breaking already working code

---

## Lesson Objectives

- Define **version control** and identify what problems it solves for developers
- Define a **repository** (aka *repo*) is, and identify what the parts of a **repo** are
- Differentiate between a **local repository** and a **remote repository** and their workflows
- Synchronize a **local repository** with a **remote repository** using **git** with **Github**

---

## Version Control (10:00 - 10:20)

Simply put, version control is a way of tracking *changes* made to a file or group of files over time.

It's very likely that each of us has tried to keep track of changes made to a file by creating different versions of that file. However, many conventional ways of doing this can become messy or complicated.

Let's look at some questions that hint at potential complications of having multiple or many versions of a file.

### Think Pair Share
> 5 min exercise, 5 min review

Turn to the person next to you and discuss the questions below. After 5 minutes, we'll go over responses as a class.

- Why might we want to have different versions of a file?
- What strategies have you used to keep track of changes you've made to a document or file before? If you haven't, brainstorm ways you might keep track of different versions of a file/document.
- How well did that strategy work? Was it painful? Can you see any limitations or problems associated with that strategy?
- How might that approach work in a team environment?

Luckily, we have a specialized tool called Git that does a much better job of tracking changes to files.

## Git (10:20 - 10:30)

Git is version control software; We'll be using Git in the command line via the `git` command.

### Common Problems that Git Solves

- I wrote some code to implement a feature, but I broke a bunch of stuff in the process.
**I want to be able to go back in time to a point where my code works!**

- I'm trying to see how my codebase or some files have changed over time.
**I'd like to be able to compare various states of my files.**

- I want to work on someone else's project, but don't want to break their code and ruin everything.
**I want to have my own "area" where I can try out code or build out a feature without adversely affecting another developer's work.**

- I'm working on a project with a team, and **I want to have an easy way to collaborate with my team.**

### How Git Works

- With Git, we can create "save-points" called **commits** that, collectively, track the version of our project at a given point in time.

- A **commit** records a set of related *changes* made to a project. Each **commit** has a **commit message** that describes the changes made to a file or group of files. **Commits** get stored together in a **repository**.

- For every feature you add, even a very small one, you should make a **commit**. If you go an hour without committing, it's usually best to go ahead and commit what you have gotten to work in the last hour.
> **Commit Early, Commit Often!**

- At any given time, we can go back to the version of our project at any given **commit**. This ability gives us a lot of room to experiment. It's *absolutely essential* to have this kind of safety net as a developer!

- When collaborating on a project with other developers, Git gives us tools to create our own "area" for writing code, within that project. This "area" is called a **branch**. A **branch** is a sequence of commits that represents a version of our project. All Git repositories start with at least one branch (`master`).

- Use cases for creating separate **branches** would include implementing a new feature, refactoring (re-writing) working code, or to develop different variations of a project. We'll cover **branching** in-depth with the next lesson on Git.


## The Git Repository (Repo) (10:30 - 11:10)

At its top-most level, Git tracks changes to a project via a **repository**. A **repository** is like a special kind of filing cabinet that stores a bunch of snapshots of a project taken at different points the project's development. It contains all of a project's **branches**, each of which are composed of **commits** representing individual changes to a project over time. As such, a **repository** encompasses all of the different versions of a project and their development histories.

**Repositories** are highly "aware" of changes made within them; they can detect when files have been added or modified.

We're used to thinking about files stored on the computer in terms of files and folders. Our projects, and actually all files on a computer are contained in structures called ***file trees***.

  - What changes are our **repos** tracking?
  - How are these changes recorded?
  - What is a **repo** "made out of"?


### Terminology

* **commit** - a snapshot of changes made to the working tree at a given time (along with a message explaining what changed)
* **the index** - also called the **staging area**; where we add changes we want committed to the git repository
* **HEAD** - the commit that is currently "checked out" in the repo
  * by default, this will be most recent commit on the current branch
* **status** - what files have changed and whether or not these changes are "staged" (have been added to **the index**)
  * try typing `git status` within a directory containing a repository

### Anatomy of a Repo: Commits and Repositories

When we create save-point or a commit, we're saving changes to our project's **file tree** since the last commit. A repo is made up of commits, just as a filing cabinet is made up of files.

![Git Local Diagram](/images/git-local.jpg)

- Repo is made out of commits
- The staging area (also called the index) is where we add files to be committed. This allows us to group together related changes.
  - `git add <filename>`
- After we have added our file(s) to the staging area, we can commit them with `git commit -m "<commit message>"` This is the step that actually creates the save-point or **commit**
-  If we check out a previous commit, we are moving the **HEAD** to that commit. This also happens when we check out a **branch**, which we will cover in a follow-up lesson.

### The Staging Area

You must call `git add` every time you alter a file to send the changes made to that file to the **staging area** (index).

The **staging area** is one of Git's more unique features, and it can take some time to wrap your head around it. It helps to think of the **staging area** as a buffer between the working directory and the project history.

> [Why stage files?](http://gitolite.com/uses-of-index.html)

Instead of automatically committing all of the changes you've made since the last commit, the **staging area** lets you group *related changes* into highly focused snapshots before actually committing to the project history. This means you can make all sorts of edits to unrelated files, then go back and split them up into logical commits by adding related changes to the stage and commit them piece-by-piece. If you change 3 files to implement a certain feature, or fix a certain bug, you'd add those 3 files to the staging area:
 ```
 git add <file1> <file2> <file3>
 ```
 Then a commit with a description of the related changes:
```
git commit -m "fixes bug <where thing does not work>"
```
```
git commit -m "adds <some> feature"
```

### Exercise 1: Create a Repository and Committing Locally - We Do
> 5 min exercise

1. Create a new `sample_portfolio` folder in sandbox directory.
2. Change your working directory to `sample_portfolio`.
  - ```cd sample_portfolio```
3. Initialize a git repository in the `sample_portfolio` folder.
  - ```git init```
4. Create a `index.html` file and write anything in it.
  - save it!
5. Add `index.html` to the staging area and then make a commit.

[What makes a great commit message?](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)

### Exercise 1.5: More Commits / History - You Do
> 5 min exercise

1. Modify `index.html` and create a new `style.css` file and add something to it.
1. Add both files to the staging area and create a create a new commit, with an appropriate message.
1. Repeat previous step (committing) but this time, change two files.
1. View the **commit history** by running `git log` to see the log of commits, and what changed each commit changed.

> TROUBLESHOOTING: If you've initialized the git repository in your sandbox directory instead of the resume folder, try running:
>
> `rm -rf .git`
>
> MAKE SURE YOU DONT FORGET `.git` IF YOU DO THIS


## Break (10 min)

## Local vs. Remote Repositories (11:20 - 12:00)

In the last exercise, we were working locally, on files stored our hard drives. Very often, we are going to want to push the changes we have made to a **remote repository**. For example, when we submit WDI homework or want to share our code with our colleagues. We're going to take an in-depth look at local and remote workflows.

### Git Local Workflow

Working on a project with git revolves around the basic **edit/stage/commit** pattern.

#### Summary

1. Edit your files in the **working directory** and save them in your text editor.
2. Use `git add <file1> <file2>` to add them to the **staging area**.
3. Use `git commit -m "descriptive message"` to make a **commit** of the staged changes and store them in the **repo**.
4. Lather. Rinse. Repeat.


### Remote Repositories and Github

So far we've been doing everything on our own machine, or **locally**. However, we can also host repositories online as well, as **remote repositories**. By using **remote repositories**, we can safely backup our local development and more easily collaborate with other developers.

#### Documentation Dive Exercise
> 10 min exercise / 10 min review

Documentation takes time to be able to read, it's not easy at first to be able to extract what you need to know. Documentation can vary in readability; some documentation will be particularly difficult to read through for beginners. But with this exercise, we'll get some early practice.

##### Instructions:

1.  Pair with a partner and spend 10 minutes to do research on the terms using one or a mix of the methods listed below.
2. Afterwards, we'll spend a few minutes discussing our findings.

**Option 1** - Run `git help` in your terminal to output a glossary.

**Option 2** - Look over this [Github Glossary](https://help.github.com/articles/github-glossary/).

**Option 3** - Google all the terms / find your own documentation.

##### Key Terms to Define
- **remote**
- **Github**
- **clone**  
- **fetch**
- **merge**  
- **pull**   
- **push**   
- **merge conflict**

<details>
  <summary>
  Answer Key
  </summary>
  <ul>
    <li> remote - another (non-local) repository that can be synchronized with your local one
    </li>
    <li> Github - a service that hosts Git remote repositories, and provides a web app to interact / collaborate on them
    </li>
    <li> clone - download an entire remote repository, to be used as a local repository
    </li>
    <li> fetch - downloading the set of changes (commits) from a remote repository
    </li>
    <li> merge - taking two histories (sequences of commits), and combining them together
    </li>
    <li> pull - fetching changes and merging them into the current branch (a combo of `git fetch` and `git merge`)
    </li>
    <li> push - sending changes to a remote repository and merging them into the specified branch
    </li>
    <li> merge conflict - when two commits conflict with one another during a merge (when they both modify the same line of code, typically)
    </li>
  </ul>
</details>

### Creating your own remote repo

In this section, we'll learn to push changes made **locally** to our **remote** repo, hosted on our GitHub account.

![Git Process Diagram](/images/git07.jpg)

### Exercise 2: Publish to a remote repository on Github
> 20 min exercise / 10 min review

The first step is to make sure you have SSH keys set up with GitHub so you don't have to type your password each time you want to push code. Generally speaking, SSH keys allows you to connect to a server without remembering a password.

To check whether you have SSH access set up with GitHub / GHE, run these two commands:
```
ssh -T git@github.com
```
```
ssh -T git@generalassemb.ly
```

If you are already set up, you should see a response like:

```
Hi <username>! You've successfully authenticated, but GitHub does not provide shell access.
```

If you get `Permission Denied`, please reference [this lesson](https://git.generalassemb.ly/ga-wdi-lessons/git-ssh) and take a few minutes to set up SSH access for GitHub.
> NOTE: Once you have finished setting up GitHub, set up you account on `git.generalassemb.ly` (GHE) in the same way

Once you've configured your SSH Keys with both Github and GHE:

1. Make sure you are in the `sample_portfolio` directory and you have no uncommitted changes (`git status`)
2. Ensure you have at least one commit (`git log` to verify)
3. Create a Github repo on GHE
  - To create a repo, click on the '+' at the top right of your Github profile
4. Give the repo a name and description, and ensure it's public
  - Don't worry about the other selections
5. Follow the steps provided to add repo as a remote and push your local commits to the remote repository
  - NOTE: there are 3 options for setting up your repo. take a second to think about which commands you need here
  - Hint: Does the repository on your LOCAL system already exist?
6. Open the repo on GHE, and explore the code there
7. Make a change locally, commit it, and push it
8. Open the repo on Github, and note that the changes have synced

## Forking & Pull Requests (12:00 - 12:30)

### Terms and Concepts (Forking and Pull Requests)

- **fork** - make a copy of a repo on Github under a different account, used for open-source software (OSS) collaboration
  - **This happens only once**
- **cloning** - download a copy of a remote repo locally onto your machine
  - **This too, happens only once**
- **push** - send changes (commits) made on a local repo to its remote counterpart
- **pull request** - a Github feature which allows a user to suggest and discuss changes to a repo based on changes present in their forked version of the project

### Below is a step by step illustration of how the forking and cloning process works.

##### 1. A Remote Repo (Our HW in this case)
![Git Process Diagram](/images/git01.jpg)
##### 2. Forking the Repo to our Github account
![Git Process Diagram](/images/git02.jpg)
##### 3. Cloning to our Local Machine
![Git Process Diagram](/images/git03.jpg)
##### 4. Pushing to a Remote, the Forked Repo on our GH account
![Git Process Diagram](/images/git04.jpg)
##### 5. Creating a Pull Request and Pulling Changes from the original source repo
![Git Process Diagram](/images/git06.jpg)

##### GIF Recap
![Git Process Diagram](/images/git.gif)

## Bonus Material

Anyone missing the git branch `(master)` in their bash prompt?

https://git-scm.com/book/en/v2/Git-in-Other-Environments-Git-in-Bash

Check out the Pro Git book - available for free online! https://git-scm.com/book/en/v2

### Bonus Exercise 3: Reset your work
What if you staged some work and realize you don't want that saved? Or, what if you've gone even further and committed something, but want to revert back to the last commit?

1. make a few changes to your resume.txt file
2. stage those files, but do NOT commit
3. check your ```git status```
4. try reverting that file back to before it was staged, what happens when you run ```git status``` again?
  * ```git reset head```
5. make a new change to your resume.txt file, and this time ```add``` and ```commit``` it
6. can you still revert with the same command?
7. try ```git reset head^```
  * ***note, be VERY careful when reseting! you cannot undo if you go back a commit***
  - this will return the changes you made to be untracked
8. to completely undo the changes, run ```git checkout -- resume.txt``` after ```git reset head^```

### More Practice with Git: Git challenge exercise - Tutorial

1. Navigate to the [Git Challenege](https://try.github.io/levels/1/challenges/1)
2. Complete all exercises.

### Closing

- Why is version control important for developers?
- What problems do we anticipate using git / github?
- Differentiate between git as a tool, and github as a service
- Define and differentiate between forking and cloning

## Quiz Questions

1. What are the main components of a git repository and how do they relate?
2. Describe the steps of the process for contributing to open source software on
   Github (the same as our homework submission process).


## Homework

### 1. Visit the [haiku](https://git.generalassemb.ly/ga-wdi-exercises/haiku) repo and follow the instructions there.

In the comments of the Pull Request description, please include a block like so (numbers out of 5):

```
comfort_level: 4
completeness: 5
```

### 2. Read [Understanding git for real by exploring the .git directory](https://medium.freecodecamp.org/understanding-git-for-real-by-exploring-the-git-directory-1e079c15b807)
Optional but highly recommended!

## Resources
* [Interactive Git Cheetsheet](http://ndpsoftware.com/git-cheatsheet.html)
* [Syncing with Git](https://www.atlassian.com/git/tutorials/syncing/)
* [Github Guides](https://guides.github.com)
* [Github Training](https://training.github.com/kit/)
* [Git Immersion - Interactive Course](http://gitimmersion.com/lab_05.html)
* [Pro Git](http://git-scm.com/book/en/v2) - An in-depth free PDF book for those wanting to understand git deeper
* [GitUp - Interactive Commit Visualizer](http://gitup.co)
* [Practice with Git](https://github.com/grayghostvisuals/practice-git)


## Appendix - Git CLI Commands

### Creating Repositories

* `git init` - run this command in a folder to turn it into a git repository
  * note: don't init a repo inside an existing repo! (also don't init in your home folder)
OR
* `git clone <URL>` - download (clone) a repo from github (or other remote source)

### Linking an existing repo to github

1. Create the repo on github.com (make sure not to check the 'initialize with readme').
2. Follow the instructions on the new repo's webpage to add as a remote:
3. Change directories to the local repo
  * `cd ~/path/to/repo`
4. Add the github remote, and name it 'origin':
  * `git remote add origin <URL>`
5. Push the existing commits up to the remote called 'origin' , and set it to track master branch:
  * `git push -u origin master`

Once linked, you can just run `git push` to push master branch to master branch

### Committing

1. Add the files you want to commit to the index (equivalent to checking which files you want to commit in the Github GUI app)
  * `git add file1 file2 ...`, or `git add .` will add all changes in the current folder
2. Create the commit:
  * `git commit -m "description message for commit"`
  * if you omit the `-m` and message, then git will open an editor for you to write the message in

### Syncing with a remote (push/pull)

1. `git pull [remote] [branch]` - fetch and merge changes (from the origin and branch specified) and merge them into the current branch.
  * If origin and branch aren't specified, git will default to the tracking branch (usually origin and the remote branch with the same name as the current branch).
  * If no origin/branch are specified, and no tracking branch is set up, git may tell you to specify
2. 'git push [remote] [branch]' - push and merge local changes from the current branch to the specified branch on the remote repo and branch specified.
  * Same rules apply as `git pull` above.


### [Screencast: The Homework Submission Process](https://vimeo.com/167925651)


### Optional Bonus assignments:
* Create a blog site using jekyll (hosted using a separate repo at **your_github_username*.github.io/blog, this is called a 'project' rep)
* Register for a custom domain name (usually $6 - $10 a year), and associate it with your github project site

You'll find instructions that will help at the bottom of the [github pages guide](https://pages.github.com).**
