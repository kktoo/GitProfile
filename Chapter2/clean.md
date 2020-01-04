# 第9章：clean

**删除工作区中未跟踪的文件**

### 常用参数：
-n	列出将要删除的目标列表
-f	 force强制删除
-d	删除整个目录包括子目录
-x	删除目标包括gitignore指定的忽略文件
-X	删除目标只包括gitignore指定的忽略文件

### 常用方法：
**仅列出将要删除的文件，并不会真正删除**
git clean -n

**删除未跟踪的文件，但不会删除gitignore文件指定的文件（包括跟踪和未跟踪的文件）**
当前目录下
git clean -f
指定目录下
git clean -f <path>

**删除当前目录及其子目录下未跟踪的文件**
git clean -df

删除当前目录下的所有未跟踪文件，无论是否被gitignore文件指定
git clean -xf

### 题外话：
git clean经常和git reset --hard搭档使用. reset只影响被track过的文件，clean来删除没有track过的文件，结合使用这两个命令能让工作目录丢弃所有的改变，完全回到一个指定<commit>的状态
常常这样使用：
```
git reset --hard
git clean -df
```
运行后,，工作目录和缓存区将回到一个干干净净的状态， 可以迎接一个新的开始了！

>需要注意的是：如果在工作目录还有需要保留的文件，那么不适合使用这个指令，如果一定要执行，请提前备份