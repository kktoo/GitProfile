# 常用操作

## 分支

### 查看分支

查看本地分支
git branch

查看所有分支（包括远程分支）
git branch -a

查看本地分支及链接的远程分支
git branch -vv

### 创建分支

创建本地分支，名字叫xxx
git checkout -b xxx

创建本地分支，名字叫xxx，并和远程分支develop_xxx链接
git checkout -b xxx origin/develop_xxx

把本地分支abc推送到远程，在远程名称叫develop_abc
git push origin abc:develop_abc

创建远程分支feature_abc
git checkout -b abc
git push origin abc:feature_abc

### 删除分支

删除本地分支xxx
git branch -d xxx

删除远程分支develop_xxx
git push origin -d develop_xxx

注：--delete等价于-d

推送一个空分支到远程分支，也可以起到删除远程分支的作用，注意冒号和origin之间是2个空格
git push origin  :develop_xxx

### 修改本地分支名称
git branch -m old_branch new_branch

### 修改远程分支名称
修改本地分支名
git branch -m old_branch new_branch
删除远程分支
git push origin :old_branch
将本地分支推送到远程创建新的远程分支
git push origin local_branch:new_branch

### 合并分支
git merge xxx

合并某个提交
git cherry-pick 0128660c08e325d410cb845616af355c0c19c6fe

### 切换分支

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

### 清除本地的已被远端删除的分支

使用git branch查看本地分支
使用git branch -r查看远程分支
使用git branch -a查看本地分支和远程分支

有时候发现，远程已经删除的分支，在使用git branch -a查看时，依然存在，git fetch也不会刷新，这时使用精简指令可以解决：
git remote prune origin
即可刷新

---

## 更新
git rebase
git svn使用git svn rebase

---

## 打tag



----

Command line instructions

Git global setup
git config --global user.name " wangwenxu"
git config --global user.email "wengwx@dingtalk.com"

Create a new repository
git clone git@192.168.8.62:wangwenxu/book.git
cd book
touch README.md
git add README.md
git commit -m "add README"
git push -u origin master

Existing folder
cd existing_folder
git init
git remote add origin git@192.168.8.62:wangwenxu/book.git
git add .
git commit -m "Initial commit"
git push -u origin master

Existing Git repository
cd existing_repo
git remote rename origin old-origin
git remote add origin git@192.168.8.62:wangwenxu/book.git
git push -u origin --all
git push -u origin --tags

---

查看某次提交的编辑文件列表

git diff --name-only 3317b1702fb795d6200238338e00c09a6c176a6c 65ca2ea6d7fbf4878892ee7da3d0361992f7b33c

git diff --name-only HEAD HEAD~