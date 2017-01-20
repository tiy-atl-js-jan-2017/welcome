_Note: All of this is based on the latest version of OSX. 10.11 at the time of this writing._

# Computer Setup

Hey y'all. I want to be sure everyone is ready to roll on Monday, so here's are a few things I'd like
for you to go ahead and install.
Please ask if you have any trouble, or just are curious about why something works the way it does.

After each step, I'll leave a note saying how to check that it was installed properly.
*Please be sure to run these checks!*

The most common sorts of errors are commands not finishing due to a permissions problem.
If that happens, feel free to flag me down and we'll get it fixed up quick!
I'll assume things went smoothly unless I hear otherwise.
So open a terminal (by going to Applications -> Utilities in Finder) and let's get started.

*Convention Note:* Text surrounded by `a grey box` indicates commands to be run in the terminal.

## Xcode Tools

To install the Xcode command line tools, run

`xcode-select --install`

If running the above command returns an error that the tools are installed already, you're in good shape.

## Homebrew

Homebrew is a package manager - that is, a program that helps us manage what other programs are installed.
Think of it like a more hackerly version of the app store. :)

They've got installation notes on [their website](http://brew.sh/) but the tl;dr is
you should just be able to run the following command and input your password if prompted:

`ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

It is possible you'll encounter some permissions issues here as the recent version of OS X (El Capitan) added something called SIP that affects the user's ability to modify system files. The gory details are [here](https://github.com/Homebrew/homebrew/blob/master/share/doc/homebrew/El_Capitan_and_Homebrew.md) but if you run into this feel free to grab me.

### Homebrew Check

Everything was installed correctly as long as

`brew --version`

returns something >= 0.9.

## Git

We'll be using Git as our version control/source management tool throughout this class (and almost certainly for the first decade of your professional career).

You probably have an existing version on your machine, but

`brew install git`

to grab a more recent one.

In addition, you'll want to configure Git to make sure it can accurately track the code you write and
won't prompt you endlessly for your username and password when pushing code up to the net.

1. `git config --global user.name "YOUR NAME"`
2. `git config --global user.email "YOUR EMAIL"`
3. `git config --global credential.helper osxkeychain`
4. `git config --global push.default simple`

### Git Check

You're all set if

`git --version`

returns something >= 2.4 and

`git config --global user.name`
`git config --global user.email`

shows your name and email.

## Prezto

To make the terminal a more pleasant place to work, we'll switch to zsh for our shell and use a basic
configuration from prezto to give us better tab completion, a more useful prompt, and other niceties.

Install [prezto](https://github.com/sorin-ionescu/prezto#installation) as follows:

1. Start zsh with `zsh`
2. Download prezto with `git clone --recursive https://github.com/sorin-ionescu/prezto.git "${ZDOTDIR:-$HOME}/.zprezto"`
3. Setup the necessary config files with:

```
setopt EXTENDED_GLOB
for rcfile in "${ZDOTDIR:-$HOME}"/.zprezto/runcoms/^README.md(.N); do
  ln -s "$rcfile" "${ZDOTDIR:-$HOME}/.${rcfile:t}"
done
```

4. Make zsh your default shell with `chsh -s /bin/zsh`
5. Finally, use your text editor to open the file `~/.zpreztorc` and change the module loading section on line 25 to look like this:

```
# Set the Prezto modules to load (browse modules).
# The order matters.
zstyle ':prezto:load' pmodule \
  'environment' \
  'terminal' \
  'editor' \
  'history' \
  'directory' \
  'spectrum' \
  'utility' \
  'completion' \
  'prompt' \
  'git'
```

Note that you will need to quit and restart the *terminal* after this for the install to take effect.

### Prezto Check

Running `echo $SHELL` should return "/bin/zsh". Also your prompt should look cool and hackerly now.

## Text Editors Etc

If you haven't installed a text editor yet, do the following:

  * Install Atom
    - Get it here: https://atom.io/
  * Setup shell commands
    - Open Atom
    - Click `Atom` in the upper left of your screen and choose `Install Shell Commands` 

If you're running Sublime Text, Vim, Emacs, Light Table, or something else, just let me know.

### Git Setup

Run the appropriate command for your editor.

For Atom:

`git config --global core.editor "atom --wait"`

For Sublime Text:

`git config --global core.editor "subl -n -w"`

## Finished!

Congrats, we'll be hacking real soon now! :)

![woooo](http://stream1.gifsoup.com/view3/2169429/nets-fan-o.gif)
