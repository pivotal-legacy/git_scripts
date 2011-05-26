# Git Scripts

These scripts are helpers for managing developer workflow when using git repos hosted on GitHub.  Install as a rubygem and they can be run as standard git commands like `git about`.

## Gem Installation

    $ gem install pivotal_git_scripts
    
## System Wide Installation

    $ cd /usr/local/bin && curl -L http://github.com/pivotal/git_scripts/tarball/master | gunzip | tar xvf - --strip=2

## git-about

`git about` shows settings set by `git pair` and `git project`

## git-pair

    $ git pair js sp
    user.name=Josh Susser & Sam Pierson
    user.email=pair+jsusser+sam@pivotallabs.com


Use `git pair` to set the git config user info that sets the commit user metadata.  You'll need to create a `.pairs` config file to map initials to names and email ids.  The example file:

    # .pairs - configuration for 'git pair'
    # place in project or home directory
    pairs:
      eh: Edward Hieatt
      js: Josh Susser; jsusser
      sf: Serguei Filimonov; serguei
    email:
      prefix: pair
      domain: pivotallabs.com
    #global: true

You can put the .pairs file in your project repo root directory and check it into git, or you can put it in your ~ directory so it's available to all projects on the workstation.

By default this command affects the configuration in the current project (.git/config). Use the `--global` option or add 'global: true' to your pairs file to set the global git configuration for all projects (~/.gitconfig).

## git-project

    $ git project pivots

This script sets the user account you will use to access repos hosted on github.com.  It creates a symlink from `id_github_current` to `id_github_pivotal<project>`, which switches the SSH key you are currently using to access GitHub repos.  Make sure you have the following lines in your .ssh/config file:

    Host github.com
      User git
      IdentityFile /Users/pivotal/.ssh/id_github_current

Copyright (c) 2010 Pivotal Labs. This software is licensed under the MIT License.
