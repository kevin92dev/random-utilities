# random-utilities

## Show the branch on your Git folders

Add this snippet to ~/.bashrc

```
get_dir() {
    printf "%s" $(pwd | sed "s:$HOME:~:")
}

get_sha() {
    git rev-parse --short HEAD 2>/dev/null
}

GIT_PS1_SHOWDIRTYSTATE=1
GIT_PS1_SHOWSTASHSTATE=1
GIT_PS1_SHOWUNTRACKEDFILES=1
# Explicitly unset color (default anyhow). Use 1 to set it.
GIT_PS1_SHOWCOLORHINTS=
GIT_PS1_DESCRIBE_STYLE="branch"
GIT_PS1_SHOWUPSTREAM="auto git"

TIME_COLOR="\[\e[38;5;239m\]"
USER_COLOR="\[\e[38;5;156m\]"
ATSIGN_COLOR="\[\e[38;5;239m\]"
HOST_COLOR="\[\e[38;5;154m\]"
COLON_COLOR="\[\e[38;5;239m\]"
BRACKET_COLOR="\[\e[38;5;239m\]"
BRANCH_COLOR="\[\e[38;5;214m\]"
SHA_COLOR="\[\e[38;5;228m\]"
DIR_COLOR="\[\e[38;5;079m\]"
SIGN_COLOR="\[\e[38;5;161m\]"
RESET_COLOR="\[\e[0m\]"

export PS1="\[\e[31m\]\t\[\e[m\] \[\e[34m\]\`\`\[\e[m\] \[\e[32m\]\u\[\e[m\]\[\e[33m\]@\[\e[m\]\[\e[35m\]\h\[\e[m\]\[\e[36m\]:\[\e[m\]\[\e[31m\]\w\[\e[m\]\[\e[32m\]\\$\[\e[m\] "
export PROMPT_COMMAND='__git_ps1 "$TIME_COLOR[\D{%H:%M:%S}] $USER_COLOR\u$ATSIGN_COLOR@$HOST_COLOR\h$COLON_COLOR:" "$DIR_COLOR\w$SIGN_COLOR\\\$$RESET_COLOR " "$BRACKET_COLOR[$BRANCH_COLOR%s $SHA_COLOR$(get_sha)$BRACKET_COLOR] "'
```
