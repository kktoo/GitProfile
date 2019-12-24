 # 第六篇 一些技巧

### git区分文件夹大小写

相信很多人遇到这种情况：
修改了一个文件名的大小写，然后通过git commit提交或者git status查看，却发现git认为没有变化。

这个是因为git考虑到兼容，默认不区分文件及文件夹的名称大小写。这个默认配置是分系统的：
windows	不区分
macOS	不区分
Linux	**区分**

有些网上的建议是通过修改config配置来区分大小写
查看默认配置
```
git config --get core.ignorecase 
```
设置为区分大小写
```
git config core.ignorecase false
```

这个方法当然也有效，git status识别到了变化，可以git commit，但这个方法有一些后患。
比如已存在的resource目录，我们将其修改为Resource目录后，提交推送到远程仓库。
这时浏览远程仓库，发现远程仓库里竟然resource目录和Resource目录同时存在，惊不惊喜？
如果其他人拉取远程仓库到本地，会发现只有一个resource目录，没有Resource目录，意不意外？
上面的例子是以目录为例的，如果是文件，也是一样的现象。

上述的弊端，我们需要通过先删除旧文件夹，再增加新文件夹来解决。
有**一个更好的办法：使用git mv命令来进行重命名操作**
git不显式跟踪文件的移动操作，git是通过推断来进行的，这样不能体现出重命名操作，所以有了git mv命令。
```bash
git mv resource Resource
git add .
git commit -m "update:文件夹重命名"
git push origin
```
git mv这一条命令相当于执行了三条命令：复制resource为tmp，删除resource，重命名tmp为Resource，并且在commit记录中有显式的重命名记录。

