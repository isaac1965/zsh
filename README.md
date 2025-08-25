![Captura desde 2023-09-23 12-27-18](https://github.com/isaac1965/zsh/assets/44930181/80c54517-cd6a-4f5f-9a18-49f35e9dc124)

# * Step one install `zsh`:
```sh
sudo apt install zsh
```

### Con oh-my-zsh
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
### Con zsh zsh-vi-mode | paru -S zsh-vi-mode
```sh
function zvm_config() {
   ZVM_LINE_INIT_MODE=$ZVM_MODE_INSERT
   ZVM_VI_INSERT_ESCAPE_BINDKEY=jj
 }
function zvm_after_init() { echo -ne "\033]12;#a1f601\x7" }

function zvm_after_select_vi_mode() {
  if [[ $ZVM_MODE == $ZVM_MODE_NORMAL ]]; then
    echo -ne "\033]12;#00ffff\x7" # cyan en normal
  else
    echo -ne "\033]12;#a1f601\x7" # verde en insert
  fi
}

```
### Pokemon-icat config
```sh
if [[ "$TERM" == "xterm-kitty" ]]; then
    # Ejecutar pokemon-icat en Kitty
    pokemon-icat --quiet 
elif [[ "$TERM" == "alacritty" ]]; then
    # Ejecutar colorscript en Alacritty
    "$HOME/.local/bin/colorscript" -r
else
    # echo "Terminal no soportado: $TERM"
fi
```
### Install "fd" paru -S fd fastest & efficient that "find"
```sh
 alias f='fd ~/ --type f | fzf --bind "enter:become(nvim {}),ctrl-e:become(vim {})"'
```
### PROMPT
```sh
PS1='%B%F{blue}%f%b  $(dir_icon)  %B%F{red}%~%f%b${vcs_info_msg_0_} %(?.%B%F{green}.%F{red})%f%b '
```
