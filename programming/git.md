# Git commands
* Git configs
```
git config --global user.name "Feng Jiang"
git config --global user.email "jiangfeng212@gmail.com"
```
* Changing a remote's URL

https://help.github.com/articles/changing-a-remote-s-url/

* Git log 
```
git log --pretty=oneline --decorate=short --graph HEAD..sandbox
git log --pretty="format:%h (%cn) %s" --graph HEAD..origin/sandbox
```
* Delete merged local branch
```
git branch --merged | egrep -v "(^\*|master|development)" | xargs git branch -d
```
* Cleanup the origin remote branches
```
git remote prune origin
```
