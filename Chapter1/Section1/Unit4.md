# 第4节：修改分支名称

### 修改本地分支名称

git branch -m old_branch new_branch

### 修改远程分支名称

修改本地分支名
git branch -m old_branch new_branch
删除远程分支
git push origin :old_branch
将本地分支推送到远程创建新的远程分支
git push origin local_branch:new_branch