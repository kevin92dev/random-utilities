# random-utilities

## Show the branch on your Git folders

Add this snippet to ~/.zsh_profile (only works on Mac OS X Catalina and newer)

```
function get_git_branch() {
    git branch 2> /dev/null | sed -n -e 's/^\* \(.*\)/[\1]/p'
}

get_sha() {
    git rev-parse --short HEAD 2>/dev/null
}

COLOR_DEF=$'\e[0m'
COLOR_USR=$'\e[38;5;243m'
COLOR_DIR=$'\e[38;5;197m'
COLOR_GIT=$'\e[38;5;39m'
setopt PROMPT_SUBST
export PROMPT='${COLOR_USR}%n ${COLOR_DIR}%~ ${COLOR_GIT}$(get_git_branch)${COLOR_DEF} ${COLOR_GIT}($(get_sha))${COLOR_DEF} $ '
```
