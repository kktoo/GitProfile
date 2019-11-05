# 第3节：删除分支

删除本地分支xxx
git branch -d xxx

删除远程分支develop_xxx
git push origin -d develop_xxx

注：--delete等价于-d

推送一个空分支到远程分支，也可以起到删除远程分支的作用，注意冒号和origin之间是2个空格
git push origin  :develop_xxx