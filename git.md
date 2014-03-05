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

* Squash merge topic branches when merging them into master.
* If a squash merge has multiple stories in it that cannot be split out into
  separate commits, include a list of each story addressed in the commit
  message.
* Commit messages should explain 'why' more than they explain 'what'
* Mark commits that so not have an associated story or defect with some kind of
  marker that identifes what the commit is for:
  * OPPREF: Opportunisitc refactoring
* Add link to story or defect at the end of the commit message

## External References

[1] http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html

