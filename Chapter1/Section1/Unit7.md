# 第7节：其他

### 清除本地的已被远端删除的分支

使用git branch查看本地分支
使用git branch -r查看远程分支
使用git branch -a查看本地分支和远程分支

有时候发现，远程已经删除的分支，在使用git branch -a查看时，依然存在，git fetch也不会刷新，这时使用精简指令可以解决：
git remote prune origin
即可刷新