# 第3章：打tag

列出已有的tag
git tag

新建tag
使用git tag命令跟上tag名字，直接创建一个tag。
git tag v1.0

新建tag，带备注信息
加上-a参数来创建一个带备注的tag，备注信息由-m指定。如果你未传入-m则创建过程系统会自动为你打开编辑器让你填写备注信息。
git tag -a tagName -m "my tag"

将tag同步到远程服务器
同提交代码后，使用git push来推送到远程服务器一样，tag也需要进行推送才能到远端服务器。
使用git push origin [tagName]推送单个分支。
git push origin v1.0

推送本地所有tag
git push origin --tags。


切换到某个tag
git checkout v0.9

本地删除tag
git tag -d v0.1.2 

远端删除tag
git push origin :refs/tags/<tagName>
git push origin :refs/tags/v0.1.2