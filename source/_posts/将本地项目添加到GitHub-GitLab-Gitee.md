---
title: 将本地项目添加到GitHub/GitLab/Gitee
date: 2018-05-19 14:14:29
tags: git
categories: Git
---

##### 将本地项目添加到GitHub/GitLab/Gitee
1.  在GitHub/GitLab/Gitee新建项目。
2.  进入本地项目文件夹下
```
1. git init
2. git add .
3. git commit -m "xxxx"
4. git remote add origin git@gitee.com:xxx/xxx.git(GitHub/GitLab/Gitee项目地址)
5. git pull origin master
   (拉取远程项目master分支，如果报：refusing to merge unrelated histories
      使用: git pull origin master --allow-unrelated-histories)
6. git push -u origin master
```
<!--more-->

##### 附:GitHub的说明
```
create a new repository on the command line：
1. git init
2. git add .
3. git commit -m "xxxx"
4. git remote add origin git@github.com:xxxxx/xxx.git
5. git push -u origin master

push an existing repository from the command line
1. git remote add origin git@github.com:xxxxx/xxx.git
2. git push -u origin master
```

参考资料
[git无法pull仓库refusing to merge unrelated histories](https://blog.csdn.net/lindexi_gd/article/details/52554159)
[git实战篇--将本地项目提交到github/gitlab中](https://favoorr.github.io/2015/01/09/use-gitlab-or-github/)
