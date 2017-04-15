# Git: sign commits vs. merge fast forward

If the workflow rule is that merge commits to master are not permitted (ie. all commits must be rebased onto master first), then one person cannot rebase someone else's signed commits without losing those signatures. 

Theoretically one could devise a tool which allows each contributor to re-sign (in the correct order), but I'm not aware that any such thing exists, and it'd probably be too impractical anyway.

In a shared repository, we prefer creating "useless" merge commits to changing other peoples signatures.
