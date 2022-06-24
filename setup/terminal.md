# Customizing your Terminal

- [Homebrew](#install-homebrew)
- [iTerm2](#Install-iTerm2)
- [Oh My Zsh](#install-oh-my-zsh)
- [Intro to vim](#Brief-intro-to-vim)
- [Auto-suggestions & Syntax highlighting](#Set-Up-Auto-suggestions-&-Syntax-highlighting)
- [Select Your Theme](#select-your-theme)
- [Starship Theme](#install-starship-theme)
- [Nerd Font](#add-nerdfont)

Life can be easier if you become accustomed to using terminal. 
By pimping your terminal, you boost the appearance and get cool features that make your work more efficient.

> A brief **warning** before we start: The following instructions on how to upgrade your terminal will require the installation of software, that doesn't work well with older verisons of macOS. We recommend to follow the instructions only when you are using macOS Catalina or higher.

## Install [Homebrew](https://brew.sh) 

Homebrew is a free and open-source package management system available for macOS and (now also) Linux. You can install it directly from the terminal.

* Paste the following at the Terminal prompt.

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

* Check out the "next steps" that will be suggested to you in the terminal after installing brew:
If it's suggested to you, please run the following two commands:

```sh
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
```

   and 

```sh
eval "$(/opt/homebrew/bin/brew shellenv)"
```


If you're a Linux user you can also use homebrew. But if you are familiar with using another tool to manage your packages or run into an issue when using homebrew, feel free to use an alternative. Depending on your Linux distribution you can use e.g. `apt-get` instead of `brew`.

You will find a nice blog post describing how to customize your Terminal with Oh my Zsh on Ubuntu (not using brew) [here](https://caffeinedev.medium.com/customize-your-terminal-oh-my-zsh-on-ubuntu-18-04-lts-a9b11b63f2).


## Install [iTerm2](https://www.iterm2.com/)
iTerm2, an alternative to the Terminal on Mac, is equipped with a bunch of nice features that make your life easier. 

* Install iTerm2 by entering the following line at the command prompt in your Terminal: 

```sh
brew install --cask iterm2
```


## Install [Oh My Zsh](https://github.com/robbyrussell/oh-my-zsh)
The newer versions of macOS ship come with zsh pre-installed. You can see if you are using zsh or something else (for example bash) in the header of your terminal window. If you're not using zsh yet, make sure to set it up before you run the next command. The next command will install Oh My Zsh, which allows you to customize the appearance of your terminal in many different ways. 

```sh
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
When you open Oh My Zsh for the first time it will tell you that it detected insecure completion-dependent directories. Don't worry it will also suggest a command to fix this problem. You have to run the command only once to fix this issue. 

```sh
compaudit | xargs chmod g-w, o-w
```

## Brief Intro to vim

Before we will install cool plugins like auto-suggestion or syntax highlighting here is short introduction to Vim. Vim is a text editor you can use from a command-line interface and it is usually set as the default editor in the Terminal. So if you type a command that will in some way open an editor, it will usually open Vim. Since navigating through Vim is not intuitive, it is good to know some basics:

* Moving inside the editor works with the arrow keys. 
* Vim has different modes:
  - To survive at the beginning you should know the **insert mode** and **command mode**. You can switch to the insert mode by pressing `i`. If you are in the insert mode the word **-- INSERT --** will appear in the lower left corner. Like the name already implies you can now insert text into the file. 
  - To change from insert mode to the **command mode** you can press `ESC` and the **-- INSERT --** will disappear. In this mode you can save the file, abort the changes and exit Vim. (Actually you can do a lot more, but let's keep it simple for now.)
  To save and exit Vim write `:wq` (write & quit). It will appear in the lower left corner. Click enter to execute. Only saving your changes works with `:w`. To trash all changes and exit Vim you can use `:q!`.

If you want to learn more about Vim you can use the command `vimtutor` to start a tutorial directly in the command-line interface. 



### Set Up Auto-suggestions & Syntax highlighting

A. Auto-suggestion allows you to save time typing repeated commands, by suggesting strings from your history that you can select by just using the right arrow and tab keys in sequence.  To install it, paste the following line at the terminal prompt:

```sh
brew install zsh-autosuggestions
```
B. Syntax highlighting will display text in different colors and fonts according to the category of terms.  To install syntax hightlighting, paste the following line at the terminal prompt:

```sh
brew install zsh-syntax-highlighting
```

C. In order to activate both auto-suggestion and syntax highlighting you have to modify the .zshrc file. 
You can open the file with the following command:

```sh
vim ~/.zshrc
```
The vim editor will open and you can append the following lines at the end of the file. (Make sure that only the first line will start with an `#`. The other lines have to start directly with `source`.)

```sh
# additional zsh plugins 
source /opt/homebrew/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
source /opt/homebrew/share/zsh-autosuggestions/zsh-autosuggestions.zsh
```

D. For the changes to take effect you have to reload your .zshrc file with the following command or restart your Terminal:

```sh
source ~/.zshrc
```


## Select Your Theme 

Now you are using the (default) Robby Russell theme... but you can try different ones: [ZSH Themes](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes)

To change for example from "robbyrussel" to the "cloud" theme all you have to do is open the .zshrc file (you will find the command above) and change value of the ZSH_Theme attribute as follows:

from

```sh
ZSH_THEME="robbyrussell"
```
to 

```sh
ZSH_THEME="cloud"
```

## Install [Starship Theme](https://starship.rs/)

There is a plethora of different Terminal themes. Depending on the tasks you are doing some themes are better suited than others. For our purpose the starship theme is a good choice. 

You can install the starship theme with the following command: 

```
brew install starship
```

In order to activate it, open the .zshrc file and paste the following line

```
eval "$(starship init zsh)"
```

at the end of the file. To make sure everything works fine scroll to the part were the zsh theme is set and comment out the following line (add a # at the beginning):
```sh
# ZSH_THEME="robbyrussell"
```

Don't forget to run the source command or restart your Terminal and that's it. :) 

## Add [Nerdfont](https://www.nerdfonts.com)

You will probably notice that some of the icons in your Terminal are not displayed correctly. To fix this you need to install a font which supports those icons. Open the website www.nerdfonts.com and download a font you like. Before you can activate it in your Terminal you have to add it to the font collection. Open the font book by e.g. opening the spotlight search (press `command`+`space`) and search for font book. (If your Mac language is set to german it's called "Schriftsammlung".) Click on the little plus on the top of the window and select the downloaded files. To activate the font open the Terminal and go to `Preferences`. When you click on `Profiles` and select `Text` you can set the `Font` at the bottom of the window. 
![terminal](image/terminal.png)
