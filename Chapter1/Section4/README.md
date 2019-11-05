# 第4章：准备工作目录

## Git global setup
git config --global user.name " wangwenxu"
git config --global user.email "wengwx@dingtalk.com"

## Create a new repository
git clone git@192.168.8.62:wangwenxu/book.git
cd book
touch README.md
git add README.md
git commit -m "add README"
git push -u origin master

## Existing folder
cd existing_folder
git init
git remote add origin git@192.168.8.62:wangwenxu/book.git
git add .
git commit -m "Initial commit"
git push -u origin master

## Existing Git repository
cd existing_repo
git remote rename origin old-origin
git remote add origin git@192.168.8.62:wangwenxu/book.git
git push -u origin --all
git push -u origin --tags