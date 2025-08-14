![Captura desde 2023-09-23 12-27-18](https://github.com/isaac1965/zsh/assets/44930181/80c54517-cd6a-4f5f-9a18-49f35e9dc124)

# * Step one install `zsh`:
```sh
sudo apt install zsh
```

### paru -S zsh-vi-mode
```sh
# ┬  ┬┬   ┌┬┐┌─┐┌┬┐┌─┐  ┌─┐┌─┐┌┐┌┌─┐┬┌─┐
# └┐┌┘│───││││ │ ││├┤   │  │ ││││├┤ ││ ┬
#  └┘ ┴   ┴ ┴└─┘─┴┘└─┘  └─┘└─┘┘└┘└  ┴└─┘

function zle-line-init zle-keymap-select {
  if [ $KEYMAP = vicmd  ]; then
    echo -ne "\033]12;#00ffff\x7\e[2 q"
  else
    # the insert mode for vi
    echo -ne "\033]12;#a1f601\x7\e[6 q"
  fi
  zle reset-prompt
}

zle -N zle-line-init
zle -N zle-keymap-select
bindkey -M viins 'jj' vi-cmd-mode

```
### PROMPT
```sh
PS1='%B%F{blue}%f%b  $(dir_icon)  %B%F{red}%~%f%b${vcs_info_msg_0_} %(?.%B%F{green}.%F{red})%f%b '
```
