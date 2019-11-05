# 第4章：add

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