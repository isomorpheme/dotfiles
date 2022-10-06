# **To be continued at [isomorpheme/nixfiles](https://github.com/isomorpheme/nixfiles)**

----

Hi there. This is my dotfiles repo. Feel free to nose around and copy stuff, or if you know an awesome plugin or configuration trick, send me a PR.

# What's a "dotfile"?
On Linux and other Unix-like operating systems, most programs store user-specific configuration in a file or directory with a name prefixed by a dot (e.g. `.zshrc` or `.bashrc`) inside the user's home directory. Hence the name dotfiles. Dotfiles make reusing settings across systems quite easy, because they go in the same directory on many different systems. Because of this portability of dotfiles, most power users keep them easily acessible in a special Git repository, like this one. :)

# How to use
When cloning this repo, be sure to add the --recursive flag, like so:

```ShellSession
$ git clone --recursive https://github.com/ijks/dotfiles
```

This is necessary because my zsh config lives in a separate repo and is used here as a submodule. By passing --recursive, the submodule will get cloned as well.

For most files and folders, all you have to do is copy them to your home folder. Personally, I use a program called stow to keep all my files in a git repo without having to version control my whole home directory. To install a certain configuration, go to the top folder in this repo, and run `stow $config_dir`, e.g. to install the vim configuration: `stow vim`. The files within the vim directory will then be symlinked to your home directory, assuming you placed this repo there.

## Exceptions
Some configurations don't live in the home directory and are installed relative to the filesystem root instead. To install them properly, you have to use the `-t` flag, like so: `stow -t / pacman`.

The current directories which need to be installed from the file root are:
  * pacman
  * figlet

For zsh, one extra step is needed:

```ShellSession
$ cd ~/.zprezto
$ ./install.sh
```

All this does is link the appropriate files into your home directory.

# Thanks to
  * @xero for explaining how to use stow for dotfile management. Check out [his dotfile repo](https://github.com/xero/dotfiles).
  * @sorin-ionescu for developing [Prezto](https://github.com/sorin-ionescu/prezto), which is awesome.

# See also
  * https://dotfiles.github.io
  * https://github.com/ijks/prezto
