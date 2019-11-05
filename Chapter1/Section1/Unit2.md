# 第2节：创建分支

创建本地分支
例如：本地分支名为xxx
git checkout -b xxx

创建本地分支
例如：本地分支名为xxx，并和远程分支develop_xxx链接
git checkout -b xxx origin/develop_xxx

把本地分支推送到远程
例如：本地分支名为abc，远程分支名为develop_abc
git push origin abc:develop_abc

创建远程分支
例如：本地分支名为abc，远程分支名为feature_abc
git checkout -b abc
git push origin abc:feature_abc