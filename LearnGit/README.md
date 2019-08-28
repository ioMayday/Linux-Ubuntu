实验楼Git与GitHub入门实践教程
=========================



# Git tag and GitHub releases

## 目录
Git 标签的作用
创建标签
查看标签
推送本地标签至远程仓库
删除标签
签出标签对应的提交版本
Git tag and GitHub releases 简介

## 指令说明

`````
git tag v1.0 -m 'version 1.0' #创建本地标签

git tag  # 显示本地仓库中的全部标签列表

git show v1.0  #查看标签详情

tree .git/refs/tags #查看当前标签文件

git push origin v1.0 #向远程库发布标签，origin为主机名

git push origin :refs/tags/v1.0  #删除远程仓库的标签，命令中的标签名其实也就是文件名

git tag -d v1.0  #删除本地标签，标签文件也会被删除

``````
