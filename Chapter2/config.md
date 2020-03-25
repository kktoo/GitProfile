# 第17章：config

## 配置文件级别：
- local 当前项目级别
- global 当前系统用户级别
- system 系统级别

## 配置文件优先级：
配置文件的配置项可以重复，优先级关系从大到小：
当前项目级别 > 当前系统用户级别 > 系统级别

## 配置文件的路径：
**windows系统**
- 全局配置文件通常在C:\User\Administrator\.gitconfig文件中，具体路径，大家根据自己的系统盘符和用户名略作调整。
- 局部配置文件在隐藏目录.git下的config文件

**mac系统**
- 全局配置文件在登录用户的根目录下，是隐藏文件
- 局部配置文件在隐藏目录.git下的config文件

## 查看配置
```
git config --list
```
如果写全称list，注意是两个短杠
l是list的缩写，如果用缩写，注意是一个短杠

```
git config -l
```
查看当前项目配置
(在当前项目下面查看的配置是全局配置+当前项目的配置)
```
git config --local -l
```

查看当前系统用户级别的配置
```
git config --global -l
```

查看系统级别的配置
```
git config --system -l
```

#### 查看配置中指定变量的值
查看用户名
```
git config user.name
```
查看邮件地址
```
git config user.email
```
使用get也是可以的
```
git config --get user.name
```

## 设置用户名和邮箱

**Git全局配置和单个仓库的用户名邮箱配置**
```
git config --global user.name "kktoo"
git config --global user.email "kktoo99@qq.com"
```

**为项目单独配置用户名、邮箱**
```
git config user.name "gitlab’s Name"
git config user.email "gitlab@xx.com"
```

## 常用配置项

除了用户名和邮箱外，还以有以下常用配置项

**换行符设置：autocrlf**

crlf是windows下的换行符，而lf是unix下的换行符。
当多人多平台合作时，会出现换行符混合的风险，此配置就是针对这种情况应运而生的。其配置如下：

- autocrlf为true 在提交时将crlf转换为lf，在检出时将crlf转换为lf。  
- autocrlf为false 提交和检出代码时均不进行转换  
- autocrlf为input 在提交时将crlf转换为lf，而检出时不转换 

可以用查看配置命令查看其值
```
git config core.autocrlf
```

有一个实用的小技巧，比如服务器程序员在windows下做linux开发，会设置全局autocrlf为false，但是某些项目需要autocrlf为true，则可以利用local和global的优先级进行单独定义，给指定项目单独设置local的autocrlf配置项。

与此配合的还有一个配置项safecrlf，详见下文。

**处理混合换行符的策略：safecrlf**

safecrlf默认值是false，其配置如下：

- safecrlf为true 拒绝提交包含混合换行符的文件
- safecrlf为false 允许…
- safecrlf为warn 警告

在windows下有时候会设置为true，表示拒绝提交混合换行符的代码。错误提交时会有提示。



