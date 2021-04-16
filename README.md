# Notes to self:

- [New machine setup](#a)
- [TODO](#d)
  [comment]: <> (- [Backups]&#40;#b&#41;)
  [comment]: <> (- [Snippets for VS Code]&#40;#c&#41;)
<!-- REFERENCE #A -->

<a name="a"></a>

---

## New Mac Setup

### Git related actions

- Key agent does not load automatically?
  - Add`eval "$(ssh-agent -s)"` in the `.zshrc` config

Configure the **shared profiles** in `~/.ssh/config`
```
# Personal account
Host personal
HostName github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_ed25519

Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa

# Company account
#Host company
#HostName github.com
#PreferredAuthentications publickey
#IdentityFile ~/.ssh/id_rsa_company
```

Some tricks to configure GIT
https://stackoverflow.com/questions/2389361/undo-a-git-merge-that-hasnt-been-pushed-yet?rq=1

- `git config --global help.autocorrect 1`
- `git config --global rebase.autoStash true`
- `git checkout -` to switch between branches quickly
- `git revert HEAD` **double check this one**
- `git branch -m old new` renaming branches
- `git commit --amend -m ”YOUR-NEW-COMMIT-MESSAGE”` amend
- `git reset` unstage all
- `git reset --soft HEAD~1` undo most recent commit

### Terminal

- `zsh` comes by default nowadays (Catalina I would say)
- get [homebrew](https://brew.sh/)
    - `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
- [ohmyzsh](https://ohmyz.sh/)
  - `sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`
- iterm2
  - `brew install --cask iterm2`
- powerlevel10k
  - `brew install romkatv/powerlevel10k/powerlevel10k`
  - `p10k configure` to get fonts [powerlevel10k](https://github.com/romkatv/powerlevel10k#meslo-nerd-font-patched-for-powerlevel10k)
  - ~~ZSH_THEME="powerlevel10k/powerlevel10k"~~

#### Custom entries in `.zshrc`
```
plugins=( git zsh-syntax-highlighting zsh-autosuggestions)
eval "$(ssh-agent -s)"
ZSH_THEME="powerlevel10k/powerlevel10k"
```

  Project specific
  - source ~/code/astra-ui/app/bashrc

#### *Don't forget NVM* `brew install nvm`
```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"
```

##### Generic aliases
```
alias latest="gf && gl"
alias master="gcm && glo"
alias ngrok="~/Downloads/ngrok http 3000"
```

#### Custom, project-specific aliases
**TODO: improve this!**
```    
alias ui="gcm && latest && rmall && npmall && sourceastraui && runbe; runfe"
alias runfe="cd /Users/.../app/ && pwd"
alias runbe="cd /Users/.../graphql/ && back-end; graphql-remote"
alias sourceastraui="source /Users/.../app/bashrc; source /Users/.../graphql/bashrc"
alias npmall="cd /Users/.../app/ && npm i; cd /Users/.../graphql/ && npm i"
alias rmall="rm -rf /Users/.../app/node_modules; rm -rf /Users/.../graphql/node_modules"
``` 

--------
## New Windows Setup

### Inside the Windows Host

- Getting Windows updated to latest
- Upgrade Windows version to Professional
- Enable WSL 2, and set it as default
- Install Debian distro (convert to WSL 2 if needed)
- Install Windows Terminal from the store
- Install Docker
- Install VS Code
- Configure terminal to be zsh
- Sync VS Code extensions

### Inside the VM

- Update distro `sudo apt get update`
- Install Git `sudo apt install git`
- Restore all .ssh entries from backup and fix folder permissions
- Install curl `sudo apt install curl`
- Install NVM https://github.com/nvm-sh/nvm
- Install latest Node `nvm install 14`
- Install yarn without node https://classic.yarnpkg.com/en/docs/install/#debian-stable
- Install ZSH https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH
- Install Oh My Zsh https://github.com/ohmyzsh/ohmyzsh
- Sync VS Code extensions (from host to gues:::debian)
  - restore Quokka license
  - create a .eslintrc on ~/
  - create a .prettierrc on ~/

<!-- REFERENCE #B -->

<a name="b"></a>

---

[comment]: <> (# Backups:)

[comment]: <> (- SSH keys)

[comment]: <> (- GPG &#40;_how to backup this one?_&#41;)

[comment]: <> (- 2-step codes for some services)

[comment]: <> (  - GitHub)

[comment]: <> (  - Lastpass)

[comment]: <> (  - Microsoft)

[comment]: <> (  - Google)

# TODO

- Create script to automate environment generation (linux only)
- Move all snippets to a separate folder/wiki
