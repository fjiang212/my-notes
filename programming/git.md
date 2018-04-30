# Git commands
* Delete merged local branch
```
git branch --merged | egrep -v "(^\*|master|development)" | xargs git branch -d
```
* Cleanup the origin remote branches
```
git remote prune origin
```
