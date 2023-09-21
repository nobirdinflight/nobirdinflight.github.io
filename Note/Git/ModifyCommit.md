- [修改Commit](#修改commit)
  - [新增修改到上次提交的commit](#新增修改到上次提交的commit)


修改Commit
===

新增修改到上次提交的commit
---

1. 将修改保存到暂存区
2. 执行`git commit --amend --no-edit`
3. 执行`git push -f`同步至远程

该命令等效于
1. `git commit`
2. `git rebase -i HEAD~2`
3. `...squash`
