# Shell Config

## Instal zsh
Zsh or z shell is an alternative to bash shell. Parameter expansion in Zsh is more powerful than in Bash  has plenty of plugins, themes and frameworks avilable. 
It helps you get a fancy looking terminal with useful features.

## Oh my zsh
[ohmyzsh](https://github.com/ohmyzsh/ohmyzsh) is an open source framework to manage your zsh config.

## File
```json
export ZSH="$HOME/.oh-my-zsh"
ZSH_THEME="alanpeabody"
zstyle ':omz:update' mode reminder
HIST_STAMPS="yyyy-mm-dd"
plugins=(git zsh-autosuggestions zsh-syntax-highlighting zsh-autocomplete fast-syntax-highlighting)
source $ZSH/oh-my-zsh.sh
```
