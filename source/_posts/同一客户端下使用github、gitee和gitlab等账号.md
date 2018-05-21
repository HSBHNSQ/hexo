---
title: 同一客户端下使用github、gitee和gitlab等账号
date: 2018-05-19 14:20:22
tags: git
categories: Git
---

** Git 客户端与服务器端的通信支持多种协议，其中SSH是最常用的。SSH的公钥登录流程：用户将自己的公钥存储在远程主机，登录时，远程主机会向用户发送一条消息，用户用自己的私钥加密后，再发给服务器。远程主机用事先存储的公钥进行解密，如果成功，就证明用户可信。**

<!--more-->

#### 生成SSH
ssh生成命令
```
ssh-keygen -t rsa -C "注册 gitlab 账户的邮箱"
```
使用命令分别生成不同的ssh文件（文件名要有区别）
完成后会在 ~/.ssh/目录下生成以下文件:
> github_id_rsa
> github_id_rsa.pub
> gitee_id_rsa
> gitee_id_rsa.pub
> gitlab_id_rsa
> gitlab_id_rsa.pub

** 然后将.pub文件分别配置到GitHub,Gitee,GitLab的ssh keys中 **
#### 编写config文件
```
touch ~/.ssh/config
```
编辑文件内容
```
Host github.com
   HostName github.com
   User xxxx
   IdentityFile ~/.ssh/github_id_rsa

Host gitee.com
   HostName gitee.com
   User xxxx
   IdentityFile ~/.ssh/gitee_id_rsa

Host 公司GitLab的域名
   HostName 公司GitLab的域名
   User xxxx
   IdentityFile ~/.ssh/gitlab_id_rsa
```

#### 创建本地仓库

在任意位置创建一个文件夹作为本地仓库，然后在该文件夹下进入git命令行界面,GitHub,Gitee和GitLab各创建一个仓库。
例如
> github工作仓库:~/workspace/GitHub
  gitee工作仓库:~/workspace/Gitee
  gitlab工作仓库:~/workspace/GitLab


本地配置
```
# GitHub
cd ~/workspace/GitHub
git init
git config --global user.name "注册GitHub的用户名"
git config --global user.email "注册GitHub的邮箱"

# Gitee
cd ~/workspace/Gitee
git init
git config --global user.name "注册Gitee的用户名"
git config --global user.email "注册Gitee的邮箱"

# GitLab
cd ~/workspace/GitLab
git init
git config --global user.name "注册GitLab的用户名"
git config --global user.email "注册GitLab的邮箱"

```

#### 验证是否配置成功

GitHub
```
ssh -T git@github.com
```
Gitee
```
ssh -T git@gitee.com
```
GitLab
```
ssh -T git@公司GitLab的域名
```

#### 资料

[在一台电脑上同时关联GitLab和GitHub](https://blog.csdn.net/litianxiang_kaola/article/details/79485680)
[同一客户端下使用多个git账号](https://www.jianshu.com/p/89cb26e5c3e8)
