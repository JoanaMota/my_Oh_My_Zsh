# my_Oh_My_Zsh
My Terminal Setup with Zsh + Oh-My-Zsh + PowerLevel9k + WSL(if needed)

1. Install zsh + oh-my-zsh + PowerLevel9k
3. Configure zsh/oh-my-zsh 
5. Configure Powerlevel9k
5. Installing Powerline Fonts

## Install zsh + oh-my-zsh + PowerLevel9k

#### zsh
```
sudo apt-get install zsh
```
#### oh-my-zsh
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
This will:

    - Write on $HOME/.zshrc
    - Set zsh as default Shell (if typed `y` when asked, if not check the zsh configuration)
    - Create $HOME/.oh-my-zsh directory that contains Oh-My-Zsh scripts and plugins!


#### PowerLevel9k

To install PowerLevel9k just run:
(Make sure you have git installed)
```
git clone https://github.com/bhilburn/powerlevel9k.git ~/.oh-my-zsh/custom/themes/powerlevel9k
```

## Configure zsh/oh-my-zsh

If zsh was not set has default in the installation part you need to edit the ~/.bashrc file, otherwise you will need to type zsh every time to open it.
For that, just edit the ~/.bashrc file with `nano ~/.bashrc` (or with your favorite editor) and paste the following lines right after the first comments:
```
if test -t 1; then
exec zsh
fi
```
To configure zsh just open the ~/.zshrc file with `nano ~/.zshrc`.

Now is the time to change the theme of oh-my-zsh, which has several cool themes. I am using Powerlevel9k (has you already suspected). So just change the theme in:
```
ZSH_THEME="powerlevel9k/powerlevel9k"
```
More zsh configurations in:
https://github.com/robbyrussell/oh-my-zsh

## Configure Powerlevel9k

For colors add:
```
export TERM="xterm-256color"
```

My Powerlevel9k configuration:
```
# FONT
POWERLEVEL9K_MODE='nerdfont-complete'

# PROMPT
POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(context dir dir_writable vcs)
POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(status)  

# CONTEX
POWERLEVEL9K_CONTEXT_DEFAULT_BACKGROUND="dark"
POWERLEVEL9K_CONTEXT_DEFAULT_FOREGROUND="green"
POWERLEVEL9K_CONTEXT_TEMPLATE="%n"

# VCS -> GIT
POWERLEVEL9K_VCS_GIT_HOOKS=(vcs-detect-changes git-untracked git-aheadbehind git-stash git-remotebranch git-tagname)
POWERLEVEL9K_VCS_CLEAN_FOREGROUND='black'
POWERLEVEL9K_VCS_CLEAN_BACKGROUND='green'
POWERLEVEL9K_VCS_UNTRACKED_FOREGROUND='white'
POWERLEVEL9K_VCS_UNTRACKED_BACKGROUND='orange'
POWERLEVEL9K_VCS_MODIFIED_FOREGROUND='white'
POWERLEVEL9K_VCS_MODIFIED_BACKGROUND='red'

POWERLEVEL9K_VCS_GIT_GITHUB_ICON=$'\uf408'

# COLORS DIR
POWERLEVEL9K_DIR_DEFAULT_BACKGROUND='024'
POWERLEVEL9K_DIR_DEFAULT_FOREGROUND='grey82'
POWERLEVEL9K_DIR_HOME_BACKGROUND='green'
POWERLEVEL9K_DIR_HOME_FOREGROUND='grey82'
POWERLEVEL9K_DIR_HOME_SUBFOLDER_BACKGROUND='blue'
POWERLEVEL9K_DIR_HOME_SUBFOLDER_FOREGROUND='grey82'

# COLORS ROOT
POWERLEVEL9K_CONTEXT_ROOT_FOREGROUND='white'
POWERLEVEL9K_CONTEXT_ROOT_BACKGROUND='red'

# Truncate DIR
POWERLEVEL9K_SHORTEN_DIR_LENGTH=3
POWERLEVEL9K_SHORTEN_DELIMITER=".."
POWERLEVEL9K_SHORTEN_STRATEGY="truncate_from_right"
```

Afterwards it should look somethin like this:

Git repository in Clean mode
![Git repository in Clean mode](images/git1_Clean.png)

Git repository with untracked files
![Git repository with untracked files](images/git2_Untracked.png)

Git repository with modified files
![Git repository with modified files](images/git3_Modified.png)

Git repository after commit
![Git repository after commit](images/git4_Back_to_Clean.png)

Git repository after push
![Git repository after push](images/git5_AfterPush.png)

For more configurations visit:
    - https://github.com/Powerlevel9k/powerlevel9k


## Installing Powerline Fonts
It can happen that when you open the shell you have something like this:

![Broken Theme](images/brokenTheme.png)

To fix that you need to install some missing Powerline Fonts. I follow the intructions from here to patch my fonts. 

Windows

``` bash
wget https://github.com/powerline/powerline/raw/develop/font/PowerlineSymbols.otf
wget https://github.com/powerline/powerline/raw/develop/font/10-powerline-symbols.conf
mkdir -p  ~/.local/share/fonts/
mkdir -p ~/.config/fontconfig/conf.d/
mv PowerlineSymbols.otf ~/.local/share/fonts/
fc-cache -vf ~/.local/share/fonts/
mv 10-powerline-symbols.conf ~/.config/fontconfig/conf.d/
```
Linux

``` bash
wget https://github.com/powerline/powerline/raw/develop/font/PowerlineSymbols.otf
wget https://github.com/powerline/powerline/raw/develop/font/10-powerline-symbols.conf
mkdir ~/.fonts/
mkdir -p .config/fontconfig/conf.d #if directory doesn't exists
mv PowerlineSymbols.otf ~/.fonts/
fc-cache -vf ~/.fonts/
mv 10-powerline-symbols.conf ~/.config/fontconfig/conf.d/

```

Another easy way to install is just double click on the font (the `.ttf` or `.otf` file) and click install.

The font that I used in Linux was [DejaVu Sans Mono](https://github.com/powerline/fonts/tree/master/DejaVuSansMono).
If you have some problem with the icons try the [Droid Sans Mono](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/DroidSansMono).


If you are using Windows with WSL, fixing this broken theme issue can be a bit pain in the ass. You have to find a Font that works for you and that is recognized in the Settings of the terminal. The `Ubuntu Mono Nerd Font Complete Mono Windows Compatible.ttf` worked for me. (this font is in the repository)

If you are using Bash on Ubuntu on Windows just change the font in the Properties as shown bellow:

Open Properties

![Open Properties](images/changeFont1.png)

Change Font

![Change Font](images/changeFont2.png)

