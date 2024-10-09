# .dotfiles

stored in a `bare` git repository (
[link](https://www.atlassian.com/git/tutorials/dotfiles)
)

**NB:** You will be used to typing `git` all the time but the below alias sets `config` to now replace `git` when interacting with this `bare` repo (you'll only do this in your root directory).

```
# Use default usr.bin.git initial before homebrew
alias config='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'
# Afterwards start using homebrew git
alias config='/opt/homebrew/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'
echo ".dotfiles" >> .gitignore
git clone --bare https://github.com/SaranyaSel/.dotfiles.git $HOME/.dotfiles
config checkout

# probably want to
config config --local status.showUntrackedFiles no
```

if there are errors due to existing files

```
mkdir -p .config-backup && \
  config checkout 2>&1 | egrep "\s+\." | awk {'print $1'} | \
  xargs -I{} mv {} .config-backup/{}
```
