 # 第六篇 一些技巧

## git区分文件夹大小写

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

## 只拉取Git仓库的部分目录内容

在某些场合下，我们的Git仓库会很大。相信我，这个世界这么大，总会有些人喜欢把所有部门的文件都放在一个仓库里。美术的地图，3d模型，客户端的代码，服务器的工程，等等等等。动辄以G计算的硬盘空间，既耗时也耗硬盘。
所以我们可以只克隆和拉取我们关心的部分目录年内容，避免拉取其他目录。
Git官方对这种行为的名称叫做：稀疏检出（sparse checkout）。

稀疏检出的行为主要依赖两个：
- core.sparsecheckout属性要配置为true
- 通过.git/info/sparse-checkout文件来配置针对什么样的目录

下面我们举个栗子：
比如我们想在一个新目录下克隆仓库，快速开展实际工作
### 步骤1:初始化空白仓库
```shell
mkdir client_code
cd client_code/
git init
```
### 步骤2 :  拉取remote的all objects信息（替换成自己的库地址）
```shell
git remote add -f origin http://kktoo@192.168.1.1:90/fc.git 
```
### 步骤3：开启sparse clone属性
```shell
git config core.sparsecheckout true 
```
### 步骤4：配置指定目录
这部分工作主要是针对配置文件，文件路径为.git/info/sparse-checkout
可以用任意一种文本编辑方式进行编辑。
详细的配置规则可以查看官方文档或相关资料，这里列出几种常用写法：

**一级目录**
A．如果目录名称前带斜杠，如/docs/，将只匹配项目根目录下的docs目录
B．如果目录名称前不带斜杠，如docs/，其他目录下如果有同名目录，也会包括进来

**多级目录**
如docs/chapter1/，则不管前面是否带有斜杠，都只匹配项目根目录下的目录，如client/docs/chapter1/是不能被匹配的

**通配符**
比如docs/index.*
比如*.png

**排除模式**
比如不拉取docs目录
```
!/docs/
```
### 步骤5：拉取指定目录下的文件
```shell
git pull origin master
```
其他切换分支等等操作没有区别
