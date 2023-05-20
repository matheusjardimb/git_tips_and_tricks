# General Git tips and tricks

Opinionated list of tips and tricks for using git. This page is **UNDER DEVELOPMENT**, feel free to
contribute via PR's.

- [Setting up the environment](#setting-up-your-environment)
- [Popular conventions](#popular-conventions)
- [Useful Resources](#useful-resources)

## Setting up your environment

### Installing Git and other tools

Run the following command for installing [git](https://git-scm.com/) and [gitk](https://git-scm.com/docs/gitk):

```bash 
sudo apt-get install git gitk
```

### Setting user information

General information which needs to be set to identify commits' authors:

```bash
git config --global user.name "FIRST_NAME LAST_NAME"
git config --global user.email "MY_NAME@example.com"
 
# Switch 'nano' with your preferred editor
git config --global core.editor "nano"
```

Run these commands inside a repo with `--local` (instead of `--global`) to override such values at project level.

Check the stored settings with:

```bash
# Change the param name to check a specific value
git config user.name

# Or list all settings with
git config -l
```

### Adding Git shortcuts

Add the following lines at `~/.gitconfig` to create aliases globally:

```gitconfig
[alias]
    # Short-formatted version of 'git log'
    l = log --pretty=format:"%C(yellow)%h\\ %ad%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --date=short

    a = add
    aa = add -A
    ap = add -p

    c = commit --verbose
    ca = commit -a --verbose
    cm = commit -m
    cam = commit -a -m
    m = commit --amend --verbose

    d = diff
    ds = diff --stat
    dc = diff --cached

    s = status -s
    st = status

    co = checkout
    cob = checkout -b

    # List branches sorted by last modified
    b = "!git for-each-ref --sort='-authordate' --format='%(authordate)%09%(objectname:short)%09%(refname)' refs/heads | sed -e 's-refs/heads/--'"

    # List aliases
    la = "!git config -l | grep alias | cut -c 7-"
```

### Displaying current branch on console

Add the following snippet at the end of `~./bashrc` to display the current branch on the console (took
from [askubuntu](https://askubuntu.com/a/946716)):

```bash
### Shows git branch name
force_color_prompt=yes
color_prompt=yes
parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[01;31m\]$(parse_git_branch)\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w$(parse_git_branch)\$ '
fi
unset color_prompt force_color_prompt
```

## Popular conventions

### Squash commits while merging code

> TODO: fill this section

### Commit message verb tense preference:

> TODO: fill this section

- https://stackoverflow.com/a/3580764/1239006
- https://stackoverflow.com/questions/3580013/should-i-use-past-or-present-tense-in-git-commit-messages

### Gitflow

> TODO: fill this section

## Useful Resources

### Useful commands to keep in mind

> TODO: fill this section

```bash
# Links the origin target to the local master branch
git push -u origin master

# Newer version of: git checkout -b BRANCH
git switch -c BRANCH

# Lists local branches and their respective upstream (remote repo)
git branch -r

# TODO add comments on reflog
git reflog
```

### Useful links

- https://udemy.com/course/git-and-github-bootcamp
- https://gist.github.com/mwhite/6887990
- https://durdn.com/blog/2012/11/22/must-have-git-aliases-advanced-examples
- https://github.com/GitAlias/gitalias
