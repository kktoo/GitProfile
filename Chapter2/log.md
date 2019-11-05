# 第13章：log

git log 查看提交记录
git log --oneline 以精简模式显示

git log --graph 图标形式显示

查看指定数量的log记录：
git log -n5

可以看到fileName相关的commit记录
git log filename

显示每次提交的diff
git log -p filenam

只看某次提交中的某个文件变化，可以直接加上fileName
git show c5e69804bbd9725b5dece57f8cbece4a96b9f80b filename