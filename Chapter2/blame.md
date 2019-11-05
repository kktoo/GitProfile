# 第8章：blame

追责，查看文件的每行内容，是由哪个用户的哪次提交修改的

例如：
git blame readme.md

指定文件的指定行范围
git blame -L 3,5 readme.md