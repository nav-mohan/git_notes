## Notes for GIT 
These are some collection of notes that I find myself referencing often.  

1. [Rebasing a topic branch onto another topic branch](https://github.com/nav-mohan/git_notes/blob/main/Rebasing-topic-branch-onto-another-topic-branch/README.MD)
    * Suppose you have a branch `topic-1` forked from `master`, and another branch `topic-2` forked from `topic-1`. Subsequently you push new commits into `master` that you wish you had incorporated before forking off `topic-1` and `topic-2`. How do you ___rebase___ `topic-1` and `topic-2` onto `master` without ___merging___ `master` into `topic-1` and `topic-2`?

2. [Pull-Request between two diverging forks](https://github.com/nav-mohan/git_notes/blob/main/Pull-Request-between-diverging-forks/README.MD)
* Suppose two users fork a topic branch - `github.com/user1/topic` and `github.com/user2/topic`. Now, `user2` performs some rebasing operation (such as reordering or squashing of commits) on their fork thus causing a divergence between `user1` and `user2`. How does `user1` sync their fork with `user2` without having to ___manually repeat the same rebase operation___ but rather through a ___pull-request___ from `user2` to `user1`? 