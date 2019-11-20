# 第三篇 使用git svn过渡

一些历史比较久远的老项目，远程仓库是svn，由于种种原因（比如配套工具链更新成本过大，比如领导不接受新理念等等），不能切换为git，可以采用git svn过渡。
即本地用git来管理远程的svn仓库。

**克隆仓库**
git svn clone <svn仓库路径> [本地文件夹名] [其他参数] 相当于git clone，例如：
```
git svn clone file:///d/Projects/svn_repo proj1_git -s --prefix=svn/
```
**push到远程**
类似git push

```
git svn dcommit
```
**更新**
类似git rebase

```
git svn rebase
```
**更新所有分支**
类似git fetch --all

```
git svn fetch --all
```