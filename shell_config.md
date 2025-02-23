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

## Zoxide

A great package to navigate through your directory. 
It remembers which directories you use most frequently, so you can "jump" to them in just a few keystrokes.
zoxide works on all major shells.

[zoxide](https://github.com/ajeetdsouza/zoxide)

### installation

It will put the zoxide command in the .zshrc and .bashrc and replace the cd command with zoxide.

```bash
brew install zoxide
brew install fzf
echo 'eval "$(zoxide init --cmd cd bash)"' >> ~/.bashrc && source ~/.bashrc
echo 'eval "$(zoxide init --cmd cd zsh)"' >> ~/.zshrc && source ~/.zshrc
```

### Usage

- The search is case insensitive.
- You can switch between the directories with only the first few characters.
- 
Some useful commands:
```bash
zoxide query -l -s # list all the directories you have visited with the weight associated with each directory
cd -  # switch to previous directory
```

## Fzf
