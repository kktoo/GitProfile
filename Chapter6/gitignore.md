## 创建.gitignore文件

应该已经有朋友发现，如果我们在windows文件管理器下鼠标右键，直接创建文件名为.gitignore文件，是会被文件管理器拒绝的。创建gitignore文件的方法如下：
1. 打开git bash或者其他命令行工具
2. 进入目录目录，确保与.git在同一目录下
3. 执行touch指令

```bash
touch .gitignore
```
就会发现成功创建了.gitignore文件

## 自动生成.gitignore文件内容

国外有个网站，专门辅助大家快速生成.gitignore文件内容。

比如需要unity的，需要visual studio的，直接在此网站输入关键词检索，就会依据模板自动生成.gitignore文件内容，再结合自己的需要进行二次加工就可以了。
地址在这里：

http://www.gitignore.io

