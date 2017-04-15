# Sync across machines

Something like "git sync" would be nice, no commits, no mess for your collaborators or in your Git history, just my current work, safe on the server, to be synced elsewhere without formally committing anything so that commits can be real improvements that require a commit message. 

Git sync would be the equivalent of hitting ctrl-S working on a doc in a Dropbox folder. You hit ctrl-S, boom it's safe on the server. 

I'd setup git sync to sync regularly and allow you to go back in time, or if you want, completely back to the last formal commit.

## Possible solutions

One way is to commit to a private, expendable branch. 

* Git made branching cheap and easy by design - you can go crazy on your private 'backup' branches without having to add detailed commit messages. 

* When you are happy, you can rebase or squash merge into the 'real' branch with proper commit messages and delete the backup branch. This will not create a mess for collaborators or your Git history (after you've deleted the ephemeral branches). 

* You could create an alias for 'git sync' that does the above in the background, if you find the individual steps too tedious to manually type in.

One way is to call your branches wip-* to indicate that it is "work in progress" and you'll be using it haphazardly.

* Don't bother doing "clean" commits while working.

* Commit stuff whenever you feel like it or when you might want to backtrack an experimental change.

* Use a commit message "wip". 

* Push to branch whenever you want a "backup", e.g. when moving to a different machine. 

* When done, clean up the history, push to a different "real" branch for review. Delete wip-* branch.

Unless people have actively checked out your branch locally they shouldn't have any "mess" on their end. 

  * They'll have a remote branch listed by "git branch -r".

  * All of those branches can be cleaned up periodically with a "git prune ..."

