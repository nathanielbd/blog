---
title: git familiar with git
---

## About

Git is a distributed version control system. Think of it as a program that organizes your files as you change them instead of calling them ``resume_final_for_real_this_time.pdf``` all the time. Notably, it has functionality to easily undo and redo changes, collaborate with others, and even host your code on [https://github.com](https://github.com).

## Setup

* Install git
  * Linux: [https://git-scm.com/download/linux](https://git-scm.com/download/linux)
  * Windows: [https://git-scm.com/download/win](https://git-scm.com/download/win)
  * Mac: [https://git-scm.com/download/mac](https://git-scm.com/download/mac)

* Create a GitHub account: [https://github.com/join](https://github.com/join)

## Terminology

Git organizes your file versions in a tree-like fashion in a repository or repo. Each line of history is called a ``branch``. The canonical branch for deployment is called ``master``. You can change branches if you plan to change make a significant change or are collaborating with someone else. You can tell git to keep track of certain files and ignore others. When you want to add a checkpoint to your file version history, you will ``commit`` them along with a descriptive message. Once you have finished, you can then merge your branch with ``master``.

## Basics

You should be familiar with the terminal or command line as git uses a command line interface.

* ``git init`` initializes the current directory as a git repository.
* ``git clone [url]`` retrieve and copy a repo from the url. The url should look like ``https://github.com/<user>/<repo>.git``
* ``git add [file]`` adds the file in its current state. This must be done before committing.
* ``git commit -m "[mesg]"`` adds a snapshot of the repo to your branch history
* ``git branch`` lists your branches
* ``git branch [name]`` creates a new branch
* ``git checkout [branch]`` switches branches
* ``git merge [branch]`` merges the specified branch into the current branch's history
* ``git remote add [alias] [url]`` remote refers to a non-local repo (like one hosted on GitHub). This command will add a GitHub repo at the specified url under an alias.
* ``git push [alis] [branch]`` transmits local branch history to the remote

See [this cheat sheet](https://education.github.com/git-cheat-sheet-education.pdf) for common git commands. If you forget anything, git is self-documenting. You can always run ``git --help``!

## Example

I want to create an app with my friend. I navigate the GitHub website and create an empty repo. Now it's hosted at https://github.com/nathanielbd/app.git.

I hop into my terminal and create some boilerplate code in a directory. While in the directory, I type ``git init`` on the terminal. I run ``git add .`` to stage all the files in my current directory for commiting. Typing ``git commit -m "first commit"`` adds the first snapshot to my repo's history. Running ``git remote add origin https://github.com/nathanielbd/app.git`` adds the remote host. I can then use the command ``git push -u origin master`` to send the changes in my terminal to GitHub (``-u`` in this case means upstream, which is needed as I created the remote before the local repo). 

If I were to instead help my friend on an app they've already created and hosted on GitHub, I'd only need to run ``git clon https://github.com/nathanielbd/app.git``. That would create a folder called 'app' that will have all of my friend's code ready to go.
