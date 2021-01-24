# SEA SEI 125 Install Fest

This install fest is adapted from the gitbook notes that can be found [here](https://gawdiseattle.gitbook.io/wdi/00-config-deployment/installfest)

## UNIT 1 Installs:

We will be installing and conifguring the following tools to set up your development and classroom enviroments:

* Slack Desktop - workspace messaging app
* Homebrew - A commandline package/installation manager 
* Iterm2 - a hot-rodded terminal app for running commandline shells
* zshell - a Unix login shell
* oh-my-zsh - a framework for managing zshell's configuration 
* git - everyone's favorite content management system
* vscode - a lgihtweight and flexible code editor designed for web development (and more)

### Slack

We will be using slack to communicate throughout the course. You should've received an invite to our channels via e-mail. You can login via the web browser, but downloading / installing the app is highly recommended.

[Download Slack](https://slack.com/downloads)

### Homebrew

Homebrew is a package manager that we will use to install various command line tools in our class.

Open up your terminal app and paste the following command into it to install homebrew:

```text
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
If you need to, you can visit the [homebrew website](https://brew.sh/) for more details.

You may be prompted to installed XCode command line tools. When prompted, click and install through that, and you're homebrew installation will continue.

After the installation process, run the command `brew doctor`. If any warnings or errors are displayed, we will need to resolve them before proceeding with the rest of the install fest.

### Xcode

We do not use Xcode in class but some other applications that we do use require some Xcode libraries. Normally, all you need is the Xcode CLI which should have already been installed when you installed Homebrew. If it didn't get installed, you can use this command:

```text
xcode-select --install
```

If you need to, you can install Xcode through the App Store. [Link here](https://itunes.apple.com/us/app/xcode/id497799835?mt=12)

### iTerm2

Although not strictly required, iTerm2 is a tricked out version of the Terminal app that is the default command line interface for Mac. It will help with the visuals of the command line navigation, especially with ohmyZSH.

Install iTerm2 by copying the following homebrew command into your terminal:

```text
brew install --cask iterm2
```

When it has completed, you will be able to find iTerm2 in your applications folder.

If you need to, you can also [Download iTerm2 here](https://www.iterm2.com/) manually. Check out the features tab for all of the cool tricks iTerm2 does.

While using iTerm2 in the beginning it may ask your password or for permissions in the mac OS. Click 'yes' all the prompts.

### zsh

A shell is a text interface into our computer, and we will be using a lot to run commands.

Zshell is the defualt mac shell these days, but if you don't have it (or aren't sure) you can install it with the command:

```text
brew install zsh
```

Don't worry, if homebrew noticed you already have it installed running this command won't cause any problems.

If it prompts you to change your default shell to zsh, select yes! When it asks you for your password, enter your computer user password \(it wont show up, but iTerm is keeping track of your keystrokes\).

### oh-my-zsh

Oh my ZSH?!!! We will be tricking out commandline even further with [Oh-My-Zsh](https://github.com/robbyrussell/oh-my-zsh). iTerm2 and zsh give you all the functionality your heart can desire, but oh-my-zsh is the real life of the party. It is used to easily configure the look and feel of your commandline.

Copy and past the following command into your terminal to install oh-my-zsh:

```text
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Restart your terminal, and you should see a brand new and colorful command prompt.

### GIT

Before we do this process, please make sure you have signed up for an account on [Github](http://www.github.com). We will be installing a version of GIT from home brew and also configuring it in a moment.

To install GIT

```text
brew install git
```

after git is installed run the following command to check your git version:

```text
git --version
```

If it is anything less than 2.30.0, run the following command to get the latest version:

```text
brew upgrade git
```

*NOTE if you are on Linux and not using homebrew, you can use the following commands to get the most recent version of GIT from PPA*

```text
sudo add-apt-repository ppa:git-core/ppa
sudo apt update; sudo apt install git
```

### Install VS Code

Currently the most popular editor according to developer polls. This is Microsoft's free version of Visual Studio.

Run the following command to install vscode with homebrew:

```text
brew install --cask visual-studio-code
```

vscode will appear in your applications folder when the installation is completed 

You can also download and install VS Code from [here](https://code.visualstudio.com/download)

## UNIT 1 Configs:

### vs code:

**Adding the code Command to your Termianl**

First lets configure vscode. For ease of use, let's make it so we can automatically open up any file or project in VS Code, from our command line. The following instructions are taken from [these docs](https://code.visualstudio.com/docs/setup/mac). If you're on a windows or linux, see the left-side menu to switch to the instructions for your machine.

To be able to open VS Code from any directory, open the Command Palette (Shift+⌘+P) and type 'shell command' to find the Shell Command: Install 'code' command in PATH command (it will be the first one that comes up).

Alternatively, you can achieve this functionality by adding VS Code to your path inside your ~/.zshrc file (zshell config file):

*NOTE: you don't need to do both*

Open your zshell config file with the following command:
```text
open ~/.zshrc
```
add this to the file path and save:

```bash
export PATH=$PATH:"/Applications/Visual Studio Code.app/Contents/Resources/app/bin"
```

Restart the terminal for the new $PATH value to take effect. You'll be able to type `code .` in any folder to start editing files in that folder. You can also open specific files with `code [filenname]`

**Installing the Open In Browser Extension**

Now open up your extensions by clicking on the blocks icon found on the upper left-hand side of vscode and search for 'open in browser'. Once you have found it, click install. This extension will make it very easy to open basic html pages in your browser as you work on them. 

The extensions icon looks like this:

![open in browser](img/vscode-extensions.png)

[more info about the open in browser extension](https://marketplace.visualstudio.com/items?itemName=techer.open-in-browser)

### zshell

**Adding a Useful Color Theme with oh-my-zsh**

Now we will make our termianl extra lit using oh-my-zsh. Use the command `code ~/.zshrc` to open your zsh config file in vscode. It lives in your root folder `~/` and is hidden, hence the `.` before the file name. 

Add the following line in the theme section (near the top) to set the oh-my-zsh theme to a handy one called 'af-magic'. af-magic will convientently display your git information and working directory in your shell which is very helpful. It also display virtualenv information which will be helpful when we get into python in unit 4.

```bash
ZSH_THEME="af-magic"
```

You can of course experiment with different themes or even make your own! there are instructions in the .zshrc file to have a different theme shown in your console everytime your start it up to explore the different flavors. 

**Setting the Shell Editor To Vscode**

Next, add the follow lines towards the bottom to set your default shell editor to vscode. The current default editor is [vim](https://www.vim.org/) which is, well, not ideal to begin with. You can remove this later if you want to get into vim editing.

```bash
# default editor
export EDITOR="code -w"
```

Save your .zshrc file and restart the terminal to enjoy!

## Configuring Git

**Configuring GIT Locally**

Make sure you have a [github](www.github.com) account and get ready with your user name and account email.

Using your github username and email, run these commands one by one replacing "YOUR-USERNAME" and "YOUR-EMAIL-ADDRESS" with your personal credentials.

```text
git config --global init.defaultBranch main
git config --global user.name "YOUR-USERNAME"
git config --global user.email "YOUR-EMAIL-ADDRESS"
git config --global push.default simple
git config --global credential.helper cache
```

**Setting up SSH Key**

In this next part we will generate a SSH key on our local machine, and then link it to our github account. This is to prevent github from demanding login credentials everytime you want to push to github from your local machine.

There are a few steps to the process, and we are going to follow github's guide found here:

[Github Generating SSH Keys](https://help.github.com/articles/generating-ssh-keys/)

