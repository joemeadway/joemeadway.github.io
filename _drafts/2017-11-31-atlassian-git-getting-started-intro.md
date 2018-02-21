---
layout: post
title:  "Atlassian Git Tutorial: Getting Started - Setting up a Repository"
date:   2017-11-31 15:25:00 +0800
categories: git atlassian
---


A git repository: virtual storiage of a project, allowing access to different versions as needed

`git init`

- creates a repository
- can be run in an empty foler, or in an existing project folder
- creates a `master` branch

`git clone`

- copy an existing repository from one location (usually remote) to another (usually local)
- pass the url of the repository being cloned: `git@<hostname>:<username>/<reponame>`
- latest version of files and folders are copied into a new folder named after the repository

Saving Changes
---

`git add`
- add file(s) to staging
- tells git that these need to be tracked
- pass filename, filder, or `--all` flag

`git commit`

- stored the staged changes in the repository
- pass flag `-m 'commit message'` 

Repo-to-Repo Collaboration
---

Git has a concept of a working copy that is different to most other cersion control systems. Traditionally, have had a central repository, and local working copies were checked out, edited, and then checked back into this central repository.

All git repositories however are full repositories in their own right, no matter where they are. Git depends on the interaction between all the clones of a reposiory. Instead of changes all being checked in to one central repo, they are pushed to all copies of the repo. 

Setting up with `git clone` automatically sets up the remote repository. Can skip this with the `--bare` option.

Configuration
---

`git config`

Once remote is set up, it will need to be added to the local repository as a remote.

`git remote add <remote name> <remote-url>`

and can then push to that remote

`git push -u <remote name> <local branch name>`

`git config` allows setting of values such as username, or email - can set globally, or for individual repositories:

Local: `<repo>/.git/config`
Global: `./.gitconfig`
System: `$(prefix)/etc/gitconfig`

On Windows, the global configs will most likely be under `c:\Users\LoginName`.

```
git config --global user.email <email address>
git config --global user.name <username>
```

Can also use config to create alias commands, to, for example, create shortcuts:

`git cinfig --global alias.ci commit`

- this creates `ci` as an alias for `commit` 


*Write up of notes from [Atlassian Git Tutorial](https://www.atlassian.com/git/tutorials/setting-up-a-repository). While I've been using git for a while, seemed a decent chance to formalise some of what I've been doing, and fill in gaps.*