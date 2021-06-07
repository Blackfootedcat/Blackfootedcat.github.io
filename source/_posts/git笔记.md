---
title: git笔记
date: 2021-02-28 12:02:28
tags: Git
categories: Git
description:
top_img: 
comments:
cover:
---

## 本地库初始化
```
git init
```
## 设置签名

	用户名 ： tom
	Email地址： 12@1.com
	作用：区分不同开发人员

项目级别：

```
 git config user.name tom
 git config user.email tom@gmail.com
```

系统用户级别：


```
git config --global  user.name tom
git config --global  user.email tom@gmail.com
```

项目级配置文件存放在 .git / config
系统级配置文件在 用户家目录下 .gitconfig
## 添加提交和查看状态
添加到暂存区

```
git add <files>
```
从暂存区中删除

```
git rm --cached <files>
```
提交到本地库

```
git commit -a       //提交暂存区所有
gti commit -m “提交信息” <files>
```
从暂存区删除

```
git reset HEAD <files>
```

 设置提交信息编辑器
```
 git config -–global core.editor vim
```
## 版本穿梭
查看详细历史记录

```
git log
git log --pretty=oneline   //一行显示
git log --oneline     //一行简略显示
git reflog          //显示步数
```
基于索引值前进后退

```
git reset --hard  [索引值]
```
基于~  ^

```
git reset --hard HEAD^    //一个^回退一步
git reset --hard HEAD~3    //会退三步
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021012813571297.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzNzU5Njk0,size_16,color_FFFFFF,t_70)

删除文件找回
	
	回退版本
比较文件差异

```
git diff <file>
git diff HEAD[索引] <file>
```
## 分支
主干 master
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210128140518922.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzNzU5Njk0,size_16,color_FFFFFF,t_70)

查看所有分支

```
git branch -v
```
创建分支

```
git brach [分支名]
```
切换分支
```
git checkout [分支名]
```
合并分支

1. 切换到被修改的分支上（a合并到b，切换到b）
2. 执行merge命令

```
git merge [分支名]
```

冲突解决
1. 提交遇到冲突
2. 编辑文件，解决冲突
3. 添加到暂存区  git add
4. 提交  git commit [-m]  （不带文件名）

## github
查看远程库别名

```
git remote -v
```

远程库地址别名
```
git remote add [别名] [https://地址]
```
推送到远程库
```
git push [远程库别名] [分支]
```
```
git clone 地址
```
>git fetch是将远程主机的最新内容拉到本地，用户在检查了以后决定是否合并到工作本机分支中。

>git pull 则是将远程主机的最新内容拉下来后直接合并，即：git pull = git fetch + git merge，这样可能会产生冲突，需要手动解决。

推送冲突
1. pull
2. 解决冲突，编辑文档
3. 添加暂存区 `git add [文件]` 
4. 提交到本地库 `git commit -m "----"` 
5. 推送到远程库 `git push [远程仓库别名] [分支]`

SSH免密登录
生成密钥

```
ssh-keygen -t rsa -C github邮箱号
```
cd  .ssh
id_rsa.pub  文件内容 密钥