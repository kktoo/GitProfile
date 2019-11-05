# 第2章：clone

**clone远程**
git clone https://gitee.com/oschina/android-app.git
git clone https://gitee.com/oschina/android-app.git e:/wkrm_git/

**clone远程分支**
git clone -b v4.1.7 https://gitee.com/oschina/android-app.git

**git svn从svn克隆**
git svn clone <svn仓库路径> [本地文件夹名] [其他参数] 相当于git clone
git svn clone file:///d/Projects/svn_repo proj1_git -s --prefix=svn/