# 第4章：准备工作目录


#### Git global setup
```
git config --global user.name "xiaobaitu"
git config --global user.email "xiaobaitu@kktoo.com"
```

准备我们的工作目录，有以下几种常见的情况

#### 新建仓库Create a new repository
```
git clone git@192.168.8.8:xiaobaitu/book.git
cd book
touch README.md
git add README.md
git commit -m "add README"
git push -u origin master
```

#### 已存在的文件夹Existing folder
```
cd existing_folder
git init
git remote add origin git@192.168.8.8:xiaobaitu/book.git
git add .
git commit -m "Initial commit"
git push -u origin master
```

#### 已存在的仓库Existing Git repository
```
cd existing_repo
git remote rename origin old-origin
git remote add origin git@192.168.8.8:xiaobaitu/book.git
git push -u origin --all
git push -u origin --tags
```