add this to the bashrc file :


```
alias ll="ls -l"

bind '"\e[A": history-search-backward'
bind '"\e[B": history-search-forward'

git_branch() {
  git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}

PS1='\[\033[0;32m\]\[\033[0m\033[0;32m\]\u\[\033[0;36m\] @ \[\033[0;36m\]\h \w\[\033[0;32m\]$(git_branch)\n\[\033[0;32m\] ^t^t ^t^`\[\033[0m\033[0;32m\] \$\[\033[0m\033[0;32m\]  ^v \[\033[0m\] '


```