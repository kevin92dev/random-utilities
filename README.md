# random-utilities

## Show the branch on your Git folders (Mac OS)

![Prompt](example.png?raw=true "Resulting prompt")

### Requirements
Source code pro + Font awesome font: https://github.com/Falkor/dotfiles/blob/master/fonts/SourceCodePro%2BPowerline%2BAwesome%2BRegular.ttf

### Steps:
1. Install Source code pro font
2. Add this snippet to ~/.zsh_profile or ~/.zshrc (it only works on Mac OS X Catalina and newer)

```
function get_git_branch() {
    git branch 2> /dev/null | sed -n -e 's/^\* \(.*\)/[\1]/p'
}

get_sha() {
    git rev-parse --short HEAD 2>/dev/null
}

GIT_ICON=$'\UE822'
RIGHT_TRIANGLE=$'\UE0B0'
LEFT_TRIANGLE=$'\UE0B2'

setopt PROMPT_SUBST
export PROMPT='%K{#429bf5}%F{black}~%1d%F %K{#3bc46d}%F{#429bf5}${RIGHT_TRIANGLE}%f%F{black} ${GIT_ICON}$(get_git_branch)%f%F{black}($(get_sha))%f%k%F{#3bc46d}${RIGHT_TRIANGLE}%f '
export RPROMPT="%F{#fcba03}${LEFT_TRIANGLE}%f%K{#fcba03} %F{black}[%D{%f/%m/%y} %D{%H:%M:%S}]%f %k"
```
