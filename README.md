# bash-utils

## TL;DR
```bash
git clone https://github.com/quiram/bash-utils.git
cd bash-utils
./make-available
```
Enjoy bash-utils :)

## Details
Check also the ongoing port to zsh: [zsh-utils](https://github.com/quiram/zsh-utils).

Useful bits of Bash code, separated by categories. Each folder will have a number of scripts, each of them with comments
at the beginning explaining objective and usage. For a longer explanation check the following presentation:

[![Power up your development experience with Bash scripts](http://img.youtube.com/vi/engxUm-Cji4/0.jpg)](https://youtu.be/engxUm-Cji4 "Power up your development experience with Bash scripts")

Many of the commands support defaults in the form of environment variables, check them out!

The best way to make use of this repository is to place wherever you want to keep it and then run `make-available`. You
will need to reload your bash defaults (typically `source $HOME/.bashrc` or `source $HOME/.bash_profile`, depending on
your system) for changes to be effective in other open shell sessions.
