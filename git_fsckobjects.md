# Git: fsckobjects

The fsckObjects settings are entirely separate from the SHA. They are about syntactic and semantic rules in the objects themselves (e.g., well-formatted committer name/dates, tree filenames that don't contain "/", etc).

Git doesn't check validity of commit hashes by default.
 
We prefer to set fsckobjects=true because we want to verify all trees.

## Counter-opinion

Don't set fsckobjects=true. There are normal repositories that have broken trees which will not download if you have it set. Yes it is irritating and I would rather turn it on, but I had to turn it off after several repos failed for me.

