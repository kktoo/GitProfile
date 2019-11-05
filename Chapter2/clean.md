# 第9章：clean

## 清除

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