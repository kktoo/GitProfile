# 第1章：分支

### 第1节：查看分支

查看本地分支
```
git branch
```
查看远程分支
```
git branch -r
```

查看所有分支（包括本地分支和远程分支）
```
git branch -a
```

查看本地分支及链接的远程分支
```
git branch -vv
```

### 第2节：创建分支

**创建本地分支**
*例如：创建一个本地分支，名为xxx*

```
git checkout -b xxx
```

**创建本地分支，联接远程分支**
*例如：本地分支名为xxx，并和远程分支develop_xxx链接*
```
git checkout -b xxx origin/develop_xxx
```

**把本地分支推送到远程**
*例如：本地分支名为abc，远程分支名为develop_abc*
```
git push origin abc:develop_abc
```

**创建远程分支**
*例如：本地分支名为abc，远程分支名为feature_abc*
先创建本地分支，再推送到远程
```
git checkout -b abc
git push origin abc:feature_abc
```

**从当前分支的某一个commit创建新分支：**
git checkout commitId -b 本地新branchName
*例如从sha值为d3ac8cc2的commit id开始，创建新分支fitABC，并推送到远程，同时建立本地分支和远程分支的关联：*

```shell
git checkout d3ac8cc2 -b fitABC
git push --set-upstream origin fitABC
```

### 第3节：删除分支

删除本地分支xxx
```
git branch -d xxx
```

删除远程分支develop_xxx
```
git push origin -d develop_xxx
```

注：--delete等价于-d

推送一个空分支到远程分支，也可以起到删除远程分支的作用，注意冒号和origin之间是2个空格
```
git push origin  :develop_xxx
```

### 第4节：修改分支名称

**修改本地分支名称**
```
git branch -m old_branch new_branch
```
**修改远程分支名称**

步骤：

   1. 修改本地分支名
   1. 删除远程分支
   1. 将本地分支推送到远程创建新的远程分支
```
git branch -m old_branch new_branch
git push origin :old_branch
git push origin local_branch:new_branch
```

### 第5节：切换分支

切换本地分支
```
git checkout v1.2.0
```
切换分支
```
git checkout -b origin/xxxx
```
远端到本地分支
```
git checkout -b xxx origin/xxxx
```

### 第6节：更新所有分支
命令可以简写为：
```
git fetch
```
也可以
```
git fetch --all
```

### 第7节：合并分支

**简单合并分支**

*例如：合并feature分支到develop分支*
1. 确认当前处于develop分支，如果不是，切换到develop分支
1. 合并feature分支到develop分支
```
git checkout develop
git merge master
```

**合并开发分支到发布分支**

*例如：合并develop分支到master分支*

1. 到项目根目录切换到 develop 分支，拉取最新代码
1. 到项目根目录切换到 master 分支，拉取最新代码
1. 合并develop代码到master 分支
1. 使用 git push origin master 上传同步代码
```
git checkout develop
git pull -r
git checkout master
git pull -r
git merge --no-ff develop
git push origin master
```

**合并某个分支某个commit 到当前分支**
假设分支A和分支B, 我们想把A上的某个commit 点合并到B分支上。
步骤：
1. 先拿到commit id
2. 切换当前分支为分支B
3. 使用cherry-pick命令来完成单点合并。
```
git cherry-pick 0128660c08e325d410cb845616af355c0c19c6fe
```

### 第8节：精简分支

精简指令用于在本地记录的远端分支中，清除已被远端删除的分支

有时候发现，远程已经删除的分支，在使用git branch -a查看时，依然存在，git fetch也不会刷新，这时使用精简指令可以即可刷新：
```
git remote prune origin
```