# Git: vim diff

I'm a long time vim user and I like keyboard shortcuts in vimdiff to jump from diff to diff. 

Also, I really love diffing entire trees in one vim session using the DirDiff plugin (https://github.com/will133/vim-dirdiff).

Here's how I wire it into my .gitconfig, which gets me the alias "git dirdiff":

  ~~~gitconfig
  [difftool "default-difftool"]
    cmd = gvim -f '+next' '+execute \"DirDiff\" argv(0) argv(1)' $LOCAL $REMOTE

  [difftool]
    prompt = false

  [alias]
    dirdiff = difftool --dir-diff
  ~~

I like to use gvim to open new windows separate from my terminal, but if you prefer you can just use plain vim in there as well.

Also, if using vim for viewing diffs, you might want to hack vim's config as well to make it look good. I like to (effectively) disable folding of lines with no diffs so I can still read the whole file- I use the shortcuts ]c (next diff) and [c (previous diff) to jump around diffs. I also like to disable editing in diff mode.

Here's my diff-related .vimrc hackage:

  ~~~vimrc
  if &diff
    set lines=60 columns=184
    set foldminlines=99999
    set nomodifiable
    set nowrite
  endif
  ~~~ 