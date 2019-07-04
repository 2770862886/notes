% Git techs

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

# git stage #

![stage](images/git_stage.jpg)

# git elements #

## git rebase -i ##

``` shell
git rebase -i HEAD^^
```

## git alias ##

``` shell
git config --global alias.l "log --color --graph --decorate --pretty=oneline --abbrev-commit"
git config --global alias.l0 "log --color --graph --decorate --pretty=oneline --abbrev-commit -U0"
git config --global alias.la "log --color --graph --decorate --pretty=oneline --abbrev-commit --all"
git config --global alias.lb "log --color --graph --decorate --pretty=oneline --abbrev-commit --all --simplify-by-decoration"
git config --global alias.lg "log --color --graph --decorate"
git config --global alias.dl "log --date-order --color --graph --decorate --pretty=oneline --abbrev-commit"
git config --global alias.dla "log --date-order --color --graph --decorate --pretty=oneline --abbrev-commit --all"
git config --global alias.dlb "log --date-order --color --graph --decorate --pretty=oneline --abbrev-commit --all --simplify-by-decoration"
git config --global alias.dlg "log --date-order --color --graph --decorate"
git config --global alias.d "diff --color"
git config --global alias.dc "diff --color --cached"
git config --global alias.d0 "diff --color --unified=0"
git config --global alias.ci "commit --verbose"
git config --global alias.ct commit
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.df diff
git config --global alias.br branch
```

## repo commands ##

``` shell
repo forall -c "git reset --hard && git clean -xfd"
```

## Fix simple ssh does not support port ##

``` shell
git config --global ssh.variant ssh
```
