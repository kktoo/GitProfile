# 常用命令

## init

**初始化**for match debug 
git init

在指定子目录初始化
git init subDir

例：
git init client
git init ./

**初始化裸仓库**
git init --bare

---

## clone

**clone远程**
git clone https://gitee.com/oschina/android-app.git
git clone https://gitee.com/oschina/android-app.git e:/wkrm_git/

**clone远程分支**
git clone -b v4.1.7 https://gitee.com/oschina/android-app.git

**git svn从svn克隆**
git svn clone <svn仓库路径> [本地文件夹名] [其他参数] 相当于git clone
git svn clone file:///d/Projects/svn_repo proj1_git -s --prefix=svn/

---

## status

**查看当前工作区和暂存区的文件状态**
git status

**文件状态：**
未跟踪状态 Untracked
位于暂存区待提交状态 Staged
被编辑状态 Modified

---

## add

将文件放入暂存区

放入单个文件
git add readme.md

放入多个文件，文件名用空格分隔
git add readme.md changelog.md

放入所有未跟踪或者已修改的文件（当前目录及其子目录的）
git add .

放入所有未跟踪或者已修改的文件（和当前在哪个目录无关）
git add --all

放入指定目录下的所有文件
git add dir

还可以使用通配符
git add dir/*

git stage是git add 的新词，推荐使用stage
git stage

---

## commit提交

提交
git commit

提交带备注信息
git commit -m "update:修改了显示样式"

放入所有文件到暂存区，同时提交
git commit -a -m "update:修改为翻页排版"
git commit -am "update:修改为翻页排版"

修改最近一次提交的备注信息
git commit --amend -m "update:修改了显示条件"

修改最近一次提交的文件列表，例如追加note.txt文件，--no-edit表示不修改最近一次提交的备注信息
git add note.txt
git commit --amend --no-edit

既追加文件，也同时修改备注信息
git commit --amend -m "update：修改了显示条件，增加了备注文本文件"

---

## push推送

推送到远程
git push

git svn使用git svn dcommit

---

## checkout 检出

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

---

## blame

追责，查看文件的每行内容，是由哪个用户的哪次提交修改的

例如：
git blame readme.md

指定文件的指定行范围
git blame -L 3,5 readme.md

------

## clean清除

删除工作区未跟踪的文件

仅列出将要删除的文件，并不会真正删除
git clean -n

删除当前目录下未跟踪的文件，但不会删除gitignore文件指定的文件（包括跟踪和未跟踪的文件）
git clean -f

删除指定目录下未跟踪的文件，但不会删除gitignore文件指定的文件（包括跟踪和未跟踪的文件）
git clean -f <path>

删除当前目录及其子目录下未跟踪的文件
git clean -df

删除当前目录下的所有未跟踪文件，无论是否被gitignore文件指定
git clean -xf

---

## config配置

**配置文件级别：**

- local 当前项目级别

- global 当前系统用户级别

- system 系统级别

**配置文件优先级：**

配置文件的配置项可以重复，优先级关系从大到小：
当前项目级别 > 当前系统用户级别 > 系统级别

**查看配置**
l是list的缩写
git config --local -l

如果写全称list，注意是两个短杠
git config --local --list

查看当前项目配置
git config --local -l

查看当前系统用户级别的配置
git config --global -l

查看系统级别的配置
git config --system -l

**设置配置**

git config --global user.name " kktoo"
git config --global user.email "kktoo99@qq.com"

---

## diff

对比文件差异

git diff <filepath>
git diff --stat <filepath>
git diff --numstat <filepath>
git diff HEAD

----

## stash

git stash

git stash list

git stash save -a "xxxx"

git stash pop

git stash pop  --index stash@{0}

git stash apply --index stash@{0}

git stash drop

git stash drop  --index stash@{0}

git stash clear

---

## branch

git branch 

git branch -r

git branch -a

git branch -vv

git branch -d 

git branch -D

git branch -m  oldname newname

git push origin --delete v3.0.4

---

## log

git log 查看提交记录
git log --oneline 以精简模式显示

git log --graph 图标形式显示

---

## pull

git pull

git pull --rebase

git pull -r

如果有冲突

git add

git rebase --continue

git rebase --abort

查看冲突的文件

git ls-files -s

查看对应文件的对应版本的内容

git show :1:filename

---

## push

删除远程分支

git push origin :feature/cashmall_3.0.2

---

## remote

路径修改之后如何做：

git remote -v

git remote remove origin

git remote add origin git@192.168.8.62:Y9-MLCP/client/mlcp_client.git

git pull remote develop

查看remote地址，远程分支，和本地分支的对应关系

git remote show origin

---

## reset

放弃本地修改 (注意是两个短杠)： 
git reset –hard HEAD

放弃最近一次提交
git reset HEAD~

---

## reflog

显示操作历史
git reflog


