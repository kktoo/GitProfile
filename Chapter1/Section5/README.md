# 第5章：其他

**查看某次提交的编辑文件列表**

git diff --name-only 3317b1702fb795d6200238338e00c09a6c176a6c 65ca2ea6d7fbf4878892ee7da3d0361992f7b33c

git diff --name-only HEAD HEAD~

---

**.gitignore规则不生效的解决办法**
把某些目录或文件加入忽略规则，按照上述方法定义后发现并未生效，原因是.gitignore只能忽略那些原来没有被追踪的文件，如果某些文件已经被纳入了版本管理中，则修改.gitignore是无效的。那么解决方法就是先把本地缓存删除（改变成未被追踪状态），然后再提交：
```
git rm -r --cached .
git add .
git commit -m 'update .gitignore'
```
---

**相对引用**
如果想看 HEAD 指向，可以通过 cat .git/HEAD 查看

通过哈希值指定提交记录很不方便，所以 Git 引入了相对引用。这个就很厉害了!

使用相对引用的话，你就可以从一个易于记忆的地方（比如 bugFix 分支或 HEAD）开始计算。

相对引用非常给力，这里我介绍两个简单的用法：

使用 ^ 向上移动 1 个提交记录
使用 ~<num> 向上移动多个提交记录，如 ~3
git checkout HEAD^

---

