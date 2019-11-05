# 第17章：config

**配置文件级别：**

- local 当前项目级别
- global 当前系统用户级别
- system 系统级别

**配置文件优先级：**

配置文件的配置项可以重复，优先级关系从大到小：
当前项目级别 > 当前系统用户级别 > 系统级别

**查看配置**
l是list的缩写
git config --local -l

如果写全称list，注意是两个短杠
git config --local --list

查看当前项目配置
git config --local -l

查看当前系统用户级别的配置
git config --global -l

查看系统级别的配置
git config --system -l

**设置配置**

git config --global user.name " kktoo"
git config --global user.email "kktoo99@qq.com"