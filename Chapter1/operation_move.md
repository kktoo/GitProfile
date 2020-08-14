# 第7章：仓库操作

## 7.1 快速初始化仓库

### 使用命令行创建仓库

如果您还没有任何代码， 可以通过命令行工具创建一个全新的 Git 仓库并初始化到本项目仓库中。

```shell
git clone https://xxx01.git
cd xxx01
echo "# 演示" >> README.md
git add README.md
git commit -m "首次创建"
git push -u origin master
```

### 使用命令行推送已存在的仓库

如果您已有一个 Git 仓库， 可以通过命令行工具将其直接推送到本仓库中。

```shell
git remote add origin https://xxx.git
git push -u origin master
```

## 7.2 迁移git仓库带commit记录

迁移git仓库，不仅将所有代码迁移到新的仓库，而且保留所有的commit记录。
举例：
1. 在当前目录下创建一个名称为xxx 的文件夹
```shell
mkdir xxx && cd xxx
```
2. 从旧仓库地址克隆一份裸版本库
```shell
git clone --bare 旧的仓库地址
```
这个操作会在xxx目录下产生一个和文件夹名称相同的 xxx.git 的文件夹。
这个操作，就是克隆git每一次的提交信息，但是并不克隆代码等文件，这样可以快速完成必要的克隆操作。
3. 推送裸版本库到新的仓库地址
```shell
cd xxx.git
git push --mirror 新的仓库地址
```
这个操作完成以后，浏览远程仓库地址，可以发现所有的代码文件以及commit历史记录，所有的分支，全部迁移到了新的仓库地址上。

至此大功告成！