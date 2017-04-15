# Merge or rebase

In my opinion when using rebase you don't lose history or make it inaccurate. A bug would still be introduced by the commit that made it, so tracking down bugs with bisect or other tools works the same. The main advantage is that your history is much cleaner.

If you are rebasing (or otherwise changing history), merge commits can come back to bite you. You've got to make sure that you are dealing with the correct side of the branch. One side will have the history you need, while the other side may not. This can lead to serious weirdness like git reverting changes without telling you.

If you are not changing history, then merge commit cause no harm at all. You've got to be a bit careful about reverts and again choosing the correct side of the history, though.

IMHO, the rebasing style is great when you are working with a group that understands how git is working under the hood. As long as they don't do anything to break stuff, then it's very nice. If you are working with a team which a bit more laissez fair, then merge commits are generally safer -- just make sure to tell then never to change history (rebase, force push, etc).

If you mix the two, you will be spending the odd afternoon piecing your git repository's history together by hand. It is seriously not fun.
