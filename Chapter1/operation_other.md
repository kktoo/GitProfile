# 第8章：其他

## git pull -r丢失代码后，如何找回？
git pull --rebase后代码丢失，如何找回？
有时候进行git pull -r操作后，会发现之前本地commit的代码都没有了，用git log查看也找不到之前的commit记录，这时候肯定吓了个半死吧(*^▽^*)，不要怕，git不会这么弱鸡的，只要提交过，肯定是可以找回来的：
1. 使用git reflog查看操作日志
2. 找到git pull -r之前的commitid，比如是bed6d6916
3. 根据当前情况决定是否创建新的分支操作或者直接在当前分支操作
4. 使用git reset --hard bed6d6916
这样就找回之前的代码啦\(^o^)/~

## 查看帮助信息
人脑记忆力是有限的，git命令很多，加上参数就更多了，难免有记不清的时候，这时候可以用-h参数查看对应命令的帮助信息。
比如查看git clean命令的帮助信息：
```shell
git clean -h
```
得到帮助信息如下：
```shell
usage: git clean [-d] [-f] [-i] [-n] [-q] [-e <pattern>] [-x | -X] [--] <paths>...

    -q, --quiet           do not print names of files removed
    -n, --dry-run         dry run
    -f, --force           force
    -i, --interactive     interactive cleaning
    -d                    remove whole directories
    -e, --exclude <pattern>
                          add <pattern> to ignore rules
    -x                    remove ignored files, too
    -X                    remove only ignored files
```
