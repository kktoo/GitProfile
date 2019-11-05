# 第三篇 妥协方案：使用git svn

如果远程仓库是svn，由于某些原因，不能切换为git，可以采用git svn的方案。
本地用git，来管理远程的svn仓库。

**git svn从svn克隆**
git svn clone <svn仓库路径> [本地文件夹名] [其他参数] 相当于git clone
git svn clone file:///d/Projects/svn_repo proj1_git -s --prefix=svn/

**push到远程**
类似git push
git svn使用git svn dcommit

**更新**
类似git rebase
git svn使用git svn rebase

**更新所有分支**
类似git fetch --all
git svn使用git svn fetch --all