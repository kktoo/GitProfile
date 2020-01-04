# 第5章：撤销操作

撤销操作常见于以下几种情况：
1. 本地文件有修改，还没有add到缓存区
1. 本地已经add，还没有commit
1. 本地已经commit，还没有push
1. 已经push到远程服务器

撤销操作主要是使用下列命令：
- [checkout命令](http://kktoo.com/wiki/gitprofile/Chapter2/checkout.html)
- [reset命令](http://kktoo.com/wiki/gitprofile/Chapter2/reset.html)
- [clean命令](http://kktoo.com/wiki/gitprofile/Chapter2/clean.html)

### 撤销文件修改

<u>*本地文件有修改，还没有add到缓存区*</u>

用checkout命令，使用暂存区的替换掉工作区的文件

撤销指定文件的修改
```
git checkout <file>
```
“.” 代表撤销所有 
```
git checkout .
```

### 撤销add操作

<u>*本地已经add，还没有commit*</u>

撤销刚才的add操作
```
git reset HEAD   <file>
```
如果不指定文件名，则撤销add的所有文件
```
git reset HEAD
```
如果是对目录执行了add操作以后，此时需要撤销 add操作，则执行：
git rm -r dir_name --cached
其中的dir_name可以是.也可以是之前add过的某个目录
比如之前操作了
```
git add src/
```
如下操作便可撤销
```
git rm -r src/ –cached 
```
由于目录已经添加到git 暂存（stage）中了，所以需要加--cached参数
如果有增加文件，并且还没有被tracked，可以使用clean命令清理
```
git clean -df
```
### 撤销commit操作

<u>*本地已经commit，还没有push*</u>

主要是使用reset命令：
git reset --soft|--mixed|--hard <commit_id>
这里的<commit_id>是每次commit的SHA-1，可以在log里查看

**注意三种参数的区别**（主要是分别对代码内容，working tree和index和HEAD的影响不同）：
--mixed   保留代码的修改内容，将commit和index撤销到指定版本；
--soft   保留代码的修改内容，将commit信息撤销到指定版本，index没有修改，如果需要继续提交，直接commit即可；
--hard    代码和commit和index 都会回撤销到指定版本（<u>注意备份，否则会丢失代码的修改内容</u>）；

默认值为--mixed方式，即不带任何参数的git reset等价于git reset --mixed

**常见操作示例：**

刚刚commit，想撤销本次误提交，又想保证代码的修改内容还在，则撤销上一次提交，这也是使用最频繁的情况：
```
git reset HEAD~
```

回退一个版本,且会将暂存区的内容和本地已提交的内容全部恢复到未暂存的状态,不影响原来本地文件(未提交的也 
不受影响) 

```
git reset (–mixed) HEAD~1 
```
回退一个版本,不清空暂存区,将已提交的内容恢复到暂存区,不影响原来本地的文件(未提交的也不受影响) 
```
git reset –soft HEAD~1 
```
回退一个版本,清空暂存区,将已提交的内容的版本恢复到本地,本地的文件也将被恢复的版本替换
```
git reset –hard HEAD~1
```

### 撤销push操作
<u>*已经push到远程服务器*</u>

对于已经把代码push到线上仓库的情况，想将本地代码和线上代码同时回退到某个指定的版本，线上线下代码保持一致。
使用revert命令将本地代码会回退到指定的历史版本，再push到线上把线上的代码更新。

```
git revert <commit_id>
git push
```
这里的<commit_id>是每次commit的SHA-1，可以在log里查看

注意：git revert是用一次新的commit来回滚之前的commit，git reset是直接删除指定的commit，看似效果相同，其实不然，至少有以下差异：
1. 如果已经push到线上代码库, reset方法删除指定commit以后，后面再git push可能导致一大堆冲突，但是revert方法并不会。
2. 以后现有分支和历史分支需要合并的时候，reset方法恢复部分的代码依然会出现在历史分支里，但是revert方法提交的commit 并不会出现在历史分支里。
3. reset方法是在正常的commit历史中，删除了指定的commit，这时 HEAD 是向后移动了，而 revert方法是在正常的commit历史中再commit一次，内容变了，但 HEAD 是一直向前的，符合我们一直向前的工作流。
