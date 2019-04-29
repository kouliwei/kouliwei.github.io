---
title: github 常见命令
date: 2019-01-29 12:12:57
categories: 
- 程序猿
tags:
- github
---



# github 常见命令汇总



## 仓库初始化+密钥生成

// configurate ssh

git init

git config --global user.name  myname

git config --global user.email  "myemail"

ssh-keygen -t rsa -C "myemail"







## 远程仓库拉取

git pull = git fetch + git merge

git pull <远程仓库名>   <远程分支名>：<本地分支名>

git pull origin master:master





git 远程仓库命令笔记

git remote  :显示远程仓库信息

git remote -v :显示远程仓库详细信息





git remote add <name> <url> : 添加远程仓库关联

eg: git remote add origin [git@github.com:kouliwei/STM32F4.git](mailto:git@github.com:kouliwei/paperofkou.git)

git remote rm <name>:删除远程仓库关联



## 仓库版本回退

git log 						查询提交历史

git reset  --hard HEAD^		回退到上一版本

git reset  --hard HEAD_100		回退到前100版本

git reset --hard commit _id		回退到指定版本

如果用户先指到了以前的版本，又突然关机找不到最新的commit_id 无法回退到最新的版本该怎么办，github可以通过 **git reflog** 来查询回退到各个版本





# 忽略文件.gitignore

仓库的某些文件（配置文件，密码文件等）无需提交到远程仓库中。可以使用 .gitignore 来决定哪些文件不要提交到远程仓库中。语法规则如下：(#代表注释)

*.pptx        # 不再track 以pptx 结尾的文件

test.txt   #  不再track test.txt 文件

!test.pptx  # test.pptx 不适用此规则，应该被track

Obj/	# 文件夹Obj整个包括的文件都不会被track

/Obj/*.md    # Obj目录下的所有以md结尾的文件不被tra, 其他的文件将被track.



需要注意的是：.gitignore 只能忽略那些尚未被track 的文件，如果某些文件已被提交到了reposity. 则修改  .gitignore 是无效的。解决办法是清除需要忽略的文件本地缓存，然后重新提交。 例如 test.txt原来已被track。 现在想要忽略它。分为以下几步：

（1）git rm -r --cached test.txt   //使得test.txt 不被track

（2）重新提交  git add/git commit /git push ....