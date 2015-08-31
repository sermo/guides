# Git Style Guide

## Rules

* Use the standard commit message format that is popular in the community[1]
  * The first line contains a summary of the commit, and is limited to 50
    characters.
  * The second line is an empty line.
  * The remaining lines contain details about the commit, and are limited to 72
    characters.
* In the first line of the commit, include the identity of the story or defect
  being addresses. For example:
  * US1234: Allow users to log into the site
* When including bulleted lists in a commit message, denote each item with an
  asterisk. Do not include an empty newline between bullet points.

## Guides

* Rebase feature branches against master frequently.  This will help you stay
  up to date with the most recent code in master, and will make your merges
  cleaner.
* Rebase against master before merging feature branches back into master.
* Squash merge topic branches when merging them into master.
* If a squash merge has multiple stories in it that cannot be split out into
  separate commits, include a list of each story addressed in the commit
  message.
* Commit messages should explain 'why' more than they explain 'what'
* Mark commits that so not have an associated story or defect with some kind of
  marker that identifes what the commit is for:
  * OPPREF: Opportunisitc refactoring
* Add link to story or defect at the end of the commit message

### Merging

In a perfect world the history in a git repository would be perfectly linear,
with each commit encapsulating a complete unit of functionality attached to
a story or bug.  Of course, during development you don't do all of your work
in one single commit on master - that's why it's important to use feature
branches, rebase frequently, and to use squash merges.  For example, consider
the following scenario, where a new feature is being completed on the branch
named *feature*:

```
A             (master)
 \
  \
   B--C--D--E (feature)
```

It's time to merge back into master, so the first step is to checkout the
master branch on your machine and bring it back up to date:

```
|feature ✓|$ git checkout master
|master ✓|$ git pull

A--F--G--H--I (master)
 \
  \
   B--C--D--E (feature)
```

Git has pulled in commits F-I.  Now you need to update your feature branch
to replay it on top of master.  Checkout the feature branch and rebase it:

```
|master ✓|$ git checkout feature
|feature ✓|$ git rebase master

A--F--G--H--I                 (master)
             \
              \
               B'--C'--D'--E' (feature)
```

Note that the commits B, C, D, and E have been replace by B', C', D', E'.  The
content of these commits is the same as they previously were, but the SHAs of
each commit has changed because the entire git history has changed.

With the feature branch up to date, it's time to merge it back into master.
Checkout the master branch, and issue a squash merge.  This will take all of
your feature branch commits and compress them down into a single commit.

```
|feature ✓|$ git checkout master
|master ✓|$ git merge --squash feature

A--F--G--H--I-----------------J (master)
             \               /
              \             /
               B'--C'--D'--E'   (feature)
```

By default a squash merge will complete the merge, but it will not do the
commit.  You will need to issue a `git commit`, and update the commit message.
Git will include all of the intermediate commit messages that you have made
for your feature branch, but you should cut this down to a single message
using the standard commit message format (50-character first line, blank
line, then more descriptive paragraphs limited to 72-character lines).

Now commit J contains all of the functionality of the feature branch.
Rebasing branches and squash merges help keep the master history clean.

Note that when you rebase your branch, you are effectively creating replacing
your commits and re-creating a new history for your branch.  For this reason,
be careful when rebasing a branch that is being worked on by multiple
developers and be sure to coordinate your work accordingly.

## External References

[1] http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html

