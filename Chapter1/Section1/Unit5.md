# 第5节：合并分支

git merge xxx

合并develop分支到master分支
* 到项目根目录切换到 develop 分支，执行 git pull --rebase
* 合并代码到master 分支,使用命令git merge --no-ff develop
* 使用 git push origin master 上传同步代码

合并某个提交
git cherry-pick 0128660c08e325d410cb845616af355c0c19c6fe