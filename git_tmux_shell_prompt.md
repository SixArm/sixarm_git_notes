# Git: tmux shell prompt

I have a dedicated Git tmux tab for every repo I'm working on, in that tab I use a git shell. Initiated by this bash function:

  ~~~shell
  # A nice shell prompt for inside git repostories
  # Shows a short status of the repository in the prompt
  # Adds an alias `g=git` and makes autocomplete work
  gitprompt() {

      __color_bold_blue='\[$(tput bold)\]\[$(tput setaf 4)\]'
      __color_white='\[$(tput sgr0)\]'

      export GIT_PS1_SHOWDIRTYSTATE=true;
      export GIT_PS1_SHOWSTASHSTATE=true;
      export GIT_PS1_SHOWUNTRACKEDFILES=true;
      export GIT_PS1_SHOWUPSTREAM="auto";
      export GIT_PS1_SHOWCOLORHINTS=true;
      . /usr/lib/git-core/git-sh-prompt;

      local ps1_start="$__color_bold_blue\w"
      local ps1_end="$__color_bold_blue \\$ $__color_white"
      local git_string=" (%s$__color_bold_blue)"

      export PROMPT_COMMAND="__git_ps1 \"$ps1_start\" \"$ps1_end\" \"$git_string\""

      # Short alias for git stuff
      alias g=git

      # Make autocomplete also work fo the `g` alias
      eval $(complete -p git | sed 's/git$/g/g')

  }
  ~~~

So I have this in my `.bashrc` and when I want my bash to get a handy Git prompt I type `gitprompt`.

You do need the file `git-sh-prompt` which should come with git, for me it's located in `/usr/lib/git-core/git-sh-prompt`. 

It's also available here:

* https://github.com/git/git/blob/master/contrib/completion/git-prompt.sh
