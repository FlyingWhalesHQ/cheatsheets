---
layout: default
title: Git
parent: Misc
---

{% include toc.md %}

## Config

```sh
# set user name and email that will be associated with version history
git config --global user.name "John Doe"
git config --global user.email "johndoe@example.com"

# set automatic command line coloring for Git for easy reviewing
git config --global color.ui auto

# config alias & common alias config
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.unstage 'reset HEAD --' # unstage a file
git config --global alias.last 'log -1 HEAD' # show last commit
```

See more at https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration

## Create

```sh
# create a new local repository
git init

# clone an existing repository
git clone <url>
```

## Branches & Tags

```sh
# list all branches, a * will appear next to the currently active branch
git branch
# list all branches with keyword
git branch | grep <keyword>

# create a new branch
git branch <branch>
# create a new branch and check it out into your working directory
git checkout -b <branch>

# create a new tracking branch based on a remote branch
git checkout --track <remote>/<branch>
# or
git branch --track <branch> <remote>/<branch>

# change current branch name
git branch -m <newname>

# delete the specified branch
git branch -d <branch>

# switch to another branch and check it out into your working directory
git checkout <branch>
# switch to previous active branch
git checkout -

# merge the specified branch’s history into the current one
git merge <branch>

# mark the current commit with a tag
git tag <tag>
```

Branch names should follow a convention. Read more at:

- [https://stackoverflow.com/questions/273695/what-are-some-examples-of-commonly-used-practices-for-naming-git-branches](https://stackoverflow.com/questions/273695/what-are-some-examples-of-commonly-used-practices-for-naming-git-branches)
- [A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/)

## Stage & Commit

File status lifecycle:

![File status lifecycle](https://git-scm.com/book/en/v2/images/lifecycle.png)

### stage

```sh
# show the status of the working directory and staging area
git status

# add the specified file to the staging area
git add <file>

# add all files to the staging area
git add .

# add all files to the staging area and remove all deleted files
git add -A

# unstage the specified file
git reset <file>

# unstage all files
git reset

# undo changes of the specified file (not staged)
git checkout <file>

# undo changes of all files (not staged)
git checkout .
```

### diff

`git diff` show differences between the working directory, the staging area, and the
most recent commit:

```sh
# show differences between the working directory and the most recent commit
git diff

# show differences between the staging area and the most recent commit
git diff --staged # or
git diff --cached

# show differences between the working directory and staging area versus the
# most recent commit
git diff HEAD

# show differences between the specified commit and the most recent commit
git diff <commit>

# show diff with stats
git diff --stat

# only display the names of changed files
git diff --name-only
```

`git diff` visualized:

![git diff visualized](https://i.stack.imgur.com/tVHYO.png)

### commit

```sh
# commit all staged changes
git commit -m "commit message"

# commit all staged changes and add all untracked files
git commit -am "commit message"

# commit all staged changes and amend the previous commit
git commit --am
```

## Merge & Rebase

### merge

```sh
# merge the specified branch’s history into the current one
git merge <branch>

# merge the specified branch’s history into the current one, but always
# generate a merge commit (even if it was a fast-forward merge)
git merge --no-ff <branch>
```

### rebase

`git rebase` is a powerful tool that can be used to rewrite the history of a
branch.

```sh
# rebase the current branch onto <base>
git rebase <base>

# rebase the current branch onto <base> and use <branch> as the new base
git rebase --onto <base> <branch>

# rebase all commits of the current branch onto <base>
git rebase --root <base>

# abort a rebase
git rebase --abort

# continue a rebase after resolving conflicts
git rebase --continue
```

### cherry-pick

`git cherry-pick` is used to apply the changes introduced by some existing
commits to the current branch.

```sh
# apply the change introduced by the commit <commit> to the current branch
git cherry-pick <commit>
```

### revert

`git revert` is used to apply a new commit that undoes the changes from a
previous commit.

```sh
# create a new commit that undoes all of the changes made in <commit>
git revert <commit>
```

### reset

`git reset` is used to reset the state of the current branch to a specific
commit.

```sh
# reset the staging area to match the most recent commit, but leave the working
# directory unchanged
git reset

# undo changes of the specified file and remove it from the staging area
git reset HEAD <file>

# undo changes of all files and remove them from the staging area
git reset HEAD

# reset the staging area and the working directory to match the most recent commit
# USE THIS CAREFULLY
git reset --hard

# reset the staging area to match the specified commit, but leave the working
# directory unchanged
git reset <commit>

# reset the staging area and the working directory to match the specified commit
# USE THIS CAREFULLY
git reset --hard <commit>
```

## Update & Publish

Manage the information about remote repositories.

```sh
# list all currently configured remotes
git remote -v

# add a new remote repository
git remote add <name> <url>

# show information about the specified remote repository
git remote show <name>

# remove the specified remote repository
git remote rm <name>

# rename the specified remote repository
git remote rename <old> <new>
```

Pull & push changes from & to remote repositories.

```sh
# fetch the latest history from the remote
git fetch <remote>

# fetch a specific branch from the remote
git fetch <remote> <branch>

# fetch the latest history from the remote and merge it into the current branch
git pull

# fetch the latest history from the remote and rebase your changes on top of it
git pull --rebase

# push the specified branch to the remote, along with necessary commits and
# objects
git push <remote> <branch>

# use HEAD to refer to the current branch
git push <remote> HEAD

# force push the specified branch to the remote, along with necessary commits
# and objects
git push <remote> <branch> -f

# push all branches to the remote, along with necessary commits and objects
git push --all <remote>

# publish your tags
git push --tags <remote>

# delete a remote branch
git push <remote> -d <branch>
```

## Stash

`stash` is a stack of changesets that you can reapply at any time even on a
different branch. It’s a great way to quickly store your changes temporarily.

```sh
# save your local modifications to a new stash
git stash

# list all stashes
git stash list

# apply the specified stash and remove it from the stash list
git stash pop <stash>

# apply the latest stash and remove it from the stash list
git stash pop

# apply the specified stash and keep it in the stash list
git stash apply <stash>

# apply the latest stash and keep it in the stash list
git stash apply

# remove the specified stash from the stash list
git stash drop <stash>

# remove all stashes
git stash clear
```

## History / Log

```sh
# show the commit history for the currently active branch
git log

# show the commit history for the specified branch
git log <branch>

# show each commit in one line and limit to 10 commits
git log --oneline -n 10
# this will also work
git log --oneline -10

# show the commit history in a nice graph
git log --graph

# show the commit history in a nice graph with all branches
git log --graph --oneline --decorate --all

# show the commit history for the specified file
git log -p <file>

# who change what and when in the specified file
git blame <file>

# show log in a pretty format
git log --pretty=format:"%h - %an, %ar : %s"

# shortlog format
git shortlog
```

See more at [https://git-scm.com/docs/pretty-formats](https://git-scm.com/docs/pretty-formats)

## gitignore

A `.gitignore` file specifies intentionally untracked files/directories
that Git should ignore.

See more at [https://git-scm.com/docs/gitignore](https://git-scm.com/docs/gitignore) and [A collection of
`.gitignore` file templates](https://github.com/github/gitignore)

## More links

- [Pro Git book](https://git-scm.com/book/en/v2)
- Hosted Git services
  - [GitHub](https://github.com/)
  - [GitLab](https://gitlab.com/)
  - [Bitbucket](https://bitbucket.org/)
- Self-hosted Git services
  - [Gitea](https://gitea.io/en-us/)
  - [Gogs](https://gogs.io/)
  - [GitLab](https://about.gitlab.com/install/)
