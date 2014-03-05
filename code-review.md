# Code Review

## As a code author

* Only post code that is in a state ready to be reviewed.
* Each indivudual review should be a single shippable unit.
* Each diff posted in a review roundshould be based off of the same parent commit.
* As the author, you make the call on when your code ships.
  *  No specific number of ShipIts are needed in order to ship -- use your
     best judgment that the number of eyes on the change are proportional to
     the change's size and complexity.
* Though not strictly required, you should post a code review for virtually
  all the code you write. No change is too small to be reviewed, but make sure
  you have good reasoning for directly merging without posting a review.
* You don't need to post reviews for changes that only impact code/file
  formatting (such as reformatting code before working on it).
* It's up to you to decide if an issue opened by a reviewer should be dropped
  or addressed in a follow-on commit. Consider each suggestion seriously, but
  at the end of the day it is up to the code author.

## As a reviewer

* Try and keep the review cycle short. If you find that a review is going many
  rounds, meet with the author in a room and walk through it all in person.
* Don't open issues for nitpicks. It's OK to point out tiny details and
  esoteric formatting stuff, but don't let that get in the way of a developer
  shipping their work.
* Avoid opening issues on "bystander code" -- this is code that existed
  independently of the code that was changed for the review. Often, it shows up
  in the diff simply because it exists a few lines above or below a change.
