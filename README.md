# General Git tips and tricks

General tips and tricks for git users

## Installing Git and other tools

TODO

## Git env setup

```bash
git config --global user.name "FIRST_NAME LAST_NAME"
git config --global user.email "MY_NAME@example.com"
```

## Git shortcuts

```bash
# Enables 'git s' as a shortcut to 'git status'
git config --global alias.s status

# Enables 'git l' as a shortcut to 'git log --oneline'
git config --global alias.l 'log --oneline'
```

## Some commands

```bash
git push -u origin master
# Links the origin target to the local master branch

git switch -c BRANCH
# Same as:
#   git checkout -b BRANCH

git branch -r
# Lists local branches and their respective upstream (remote repo)

git reflog
# TODO add comments on reflog
```

## Conventions

### Commit message verb tense preference:

TODO: https://stackoverflow.com/a/3580764/1239006

### Gitflow

TODO
