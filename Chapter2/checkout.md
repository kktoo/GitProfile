# 第7章：checkout

## 检出

**放弃本地某个文件的修改**
git checkout 文件名

**切换分支**
例如有分支develop和hotfix，当前在develop分支上，要切换到hotfix分支上，
git checkout hotfix

**新建分支并切换到此分支**
git checkout -b newBrach2

**用暂存区内容覆盖工作区内容**

常用于想放弃某个文件修改内容的时候，
git checkout readme.md

建议用下面的格式，文件名称前面有两个短杠，并且中间有空格和文件名称分隔。此种方式，可以防止有分支名和文件名相同的时候，git优先当分支处理的问题。
git checkout -- readme.md

还原多个文件，用空格分隔
git checkout readme.md changelog.md

还原所有文件
git checkout .

还原指定目录
git checkout subdir/*

**用指定某个commit提交的内容来覆盖工作区内容**

用提交记录的sha-1值来标识
git checkout dfdfc5c -- readme.md

也可以这样写
git checkout HEAD^^ -- readme.md

也可以用其他分支的指定提交内容来覆盖当前工作区内容
git checkout develop -- readme.md