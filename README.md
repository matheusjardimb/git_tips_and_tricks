# General Git tips and tricks

Opinionated list of tips and tricks for setting up a git env.

This page is **UNDER DEVELOPMENT**, feel free to enrich it and solve TODO's via PR's.

## Installing Git and other tools

Run the following command for installing git and gitk:

```bash
sudo apt-get install git gitk
```

## Git env setup

```bash
git config --global user.name "FIRST_NAME LAST_NAME"
git config --global user.email "MY_NAME@example.com"
git config --global core.editor "nano"
```

## Git shortcuts

Add the following lines to `~/.gitconfig` to add aliases globally:

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

## Useful commands to keep in mind

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

## Conventions

### Commit message verb tense preference:

- https://stackoverflow.com/a/3580764/1239006
- https://stackoverflow.com/questions/3580013/should-i-use-past-or-present-tense-in-git-commit-messages

### Gitflow

TODO: add brief description.

References:

- https://nvie.com/posts/a-successful-git-branching-model/
- https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow
- https://leanpub.com/git-flow/read

![Gitflow](images/git-flow-nvie.png "Author: Vincent Driessen - Original blog post: http://nvie.com/posts/a-succesful-git-branching-model")

### Edit .bashrc

Edit `~./bashrc` file and add the following at the end:

https://askubuntu.com/a/946716

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

### Sources

- https://www.udemy.com/course/git-and-github-bootcamp/
- https://gist.github.com/mwhite/6887990
- https://www.durdn.com/blog/2012/11/22/must-have-git-aliases-advanced-examples/
- https://github.com/GitAlias/gitalias
