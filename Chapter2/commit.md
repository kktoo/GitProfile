# 第5章：commit

## 提交

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