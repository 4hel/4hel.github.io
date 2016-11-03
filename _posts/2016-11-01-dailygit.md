---
layout: post
title:  "Daily Git"
date:   2016-11-01 17:50:00
categories: book
---

From Martin Dilger

The author tells that Git is probably the most important innovation in software development in the last 10 years.

## Basics

When looking at the files in the .git directory there is a config file:

```bash
$ cat config | grep url
# url = https://user@github.com/user/repo.git
```

The `git log` command shows the commit messages for one or all files. The parameter `--oneline` leaves out author and email:

```bash
$ git log --oneline _posts/irre.md
# 7ce9393 fix spelling
# d88cf88 irre
```

The `git status` command shows untracked or modified files.

\"everything\" is stored in the **.git/objects/** database. An object is represented as a binary file named as the hash value of the original content and compressed with zlib. This SHA-1 hash can be created with `git hash-object _posts/irre.md`. There are four types ob objects: **Commit**, **Tree**, **Blob** and **Tag**. The objects can be retrieved via the hash value and pretty printed with `git cat-file -p bf59ee...`. Every commit references its parent commit or 0 in case of the initial commit or multiple parents in case of a merge commit.


## Branch

Branching is the feature that makes git so popular and powerful.

The most upper commit of every branch is called the **head**. It's hash value can be found in **.git/refs/heads/** in files named like the branch. The currently checked out branch can be found in **.git/HEAD**.

Creating a branch:

```bash
$ git branch feature-4711
$ git branch 
#   feature-4711
# * master
$ git checkout feature-4711
```

Resetting the current branch to the status of before the last two commits:

```bash
$ git reset --hard HEAD~2
```

For merging a merge tool is needed:

```bash
$ sudo aptitude install meld
$ git config --global merge.tool meld
$ git merge feature-4711
$ git status
$ git diff
$ git mergetool
$ git status # forgot commit?
$ git log --graph
```

When there is no conflict a fast forward merge is done, just referencing the latest commit from the feature branch.

## Rebase

Lorem Ipsum
