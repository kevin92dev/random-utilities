# random-utilities

## Show the branch on your Git folders (Mac OS)

### Requirements
Source code pro + Font awesome font: https://github.com/Falkor/dotfiles/blob/master/fonts/SourceCodePro%2BPowerline%2BAwesome%2BRegular.ttf

### Steps:
1. Install font
2. Add this snippet to ~/.zsh_profile (only works on Mac OS X Catalina and newer)

```
function get_git_branch() {
    git branch 2> /dev/null | sed -n -e 's/^\* \(.*\)/[\1]/p'
}

get_sha() {
    git rev-parse --short HEAD 2>/dev/null
}

GIT_ICON=$'\UE822'
TRIANGLE=$'\UE0B0'

setopt PROMPT_SUBST
export PROMPT='%K{#18C7FF}%F{black}%~%f %K{#17DC38}%F{black} ${GIT_ICON}$(get_git_branch)%f%F{black}($(get_sha))%f %k%F{#17DC38}${TRIANGLE}%f '
```
