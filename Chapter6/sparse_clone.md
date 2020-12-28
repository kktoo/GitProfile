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
