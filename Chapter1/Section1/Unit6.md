# 第6节：切换分支

切换本地分支
git checkout v1.2.0

切换分支
git checkout -b origin/xxxx

远端到本地分支
git checkout -b xxx origin/xxxx

更新所有分支，命令可以简写为：
git fetch
git fetch --all
git svn使用git svn fetch --all
注：--all等价于-a