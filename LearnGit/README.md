实验楼Git与GitHub入门实践教程
=========================

# Git入门与简介
## 目录
`````
Git 仓库的三大区域：工作区+暂存区+版本区
修改工作区
将工作区的修改添加到暂存区
从暂存区撤销修改到工作区
查看提交历史
配置个人信息
完成一次提交
版本回退
处理提交时间线分叉问题
使用 git reflog 命令查看本地仓库版本变化

`````
## 指令说明

`````
git clone ~~  #仓库网址

cd shiyanlou #打开本地仓库

git status  #查看本地仓库状态

echo 'hello world' > one.txt #在仓库内新建文件 放在工作区

git add one.txt #把工作区的文件放到暂存区

git add .  #把工作区的所有文件放到暂存区

echo 'Change the README.md' > README.md  #修改本地仓库已有文件，末尾添加文字

git config --global user.email "you@example.com" #配置GitHub邮箱
git config --global user.name "Your Name" #配置云端GitHub用户名
git config -l  # 显示本地仓库在云端仓库的配置信息
cat -n ~/.gitconfig #查看配置后的邮箱和用户名

git commit -m 'commit one.txt, shiyanlou.txt, README.txt and README.md changed' #暂存区提交到版本区，一个必须的选项 -m 用来提供该提交的备注,后面为注释内容，依然只是操作的本地仓库
git log #查看版本区的提交历史记录,紫色框中的十六进制序列号就是提交版本号，每个提交都有自己单独的版本号
git branch -avv #查看云端与本地的版本差异
git push #将版本区推送到云端同步 或者push -f 提交修改的版本
git reset --soft HEAD^ #退回到之前的一个版本，HEAD^^表示之前两个版本,撤销 n 次可以简写为 HEAD~n
git reset one.txt #撤回修改的版本

git diff (git diff --cached) #查看工作区被跟踪的文件的修改详情,cached查看暂存区的全部修改
git diff HEAD -- readme.txt  #查看该文件在工作区和版本库里面最新版本的区别
# 此时会跳到新的页面，即工作区修改详情页，按 Q 退出此页面。

`````

Git分支操作
===========

# 章节目录
``````
添加 SSH 关联授权
为 Git 命令设置别名
git fetch 刷新本地分支信息
创建新的本地分支
将新分支中的提交推送至远程仓库
本地分支跟踪远程分支
删除远程分支
本地分支的更名与删除
``````````

# 获取SSH永久授权

好处：

1)不用每次push都要密码和用户名

2）提高传输速率

## 指令说明
``````
ssh-keygen #在git本地库目录下运行，生成配对的公私钥
tree ~/.ssh #查看生成的公私钥文件名
cat ~/.ssh/id_rsa.pub #复制pub文件具体公钥内容

终端执行 ssh-keygen 命令按几次回车生成公私钥，公私钥存放在家目录下的隐藏目录 .ssh 中的两个文件中。
**图片中的路径，一路默认回车即可。**
在GitHub上的Settings里点击SSH配置，Add New SSH key, Title随便写，把内容全部复制进去即可。
回到仓库主目录，点击所示的绿色按钮Clone and download，点击紫色框中的 “Use SSH”，然后复制这个链接。

rm -rf shiyanlou #删除本地的仓库
git clone git@github.com:ioMayday/shiyanlou.git #重新克隆下载SSH配对的云端仓库
**重要的一点：只有使用这种 git 开头的地址克隆仓库，SSH 关联才会起作用。**

 git branch dev #创建新的名为dev的分支，内容均复制master的

```````

# 分支管理
 
`````

【推送本地分支到远程分支】
git push [主机名] [本地分支名]:[远程分支名] 
git push origin  dev:dev #例子

【本地分支跟踪远程分支及撤销】
git branch -u [主机名/远程分支名] [本地分支名]  #如果是设置当前所在分支跟踪远程分支，最后一个参数本地分支名可以省略不写
git branch -u origin/dev dev1 #将远程的dev分支跟踪到本地的dev1，保持两者同步
git branch --unset-upstream [分支名] #可撤销该分支对远程分支的跟踪，同样地，如果撤销当前所在的分支的跟踪，分支名可以省略不写


【删除远程分支】
git push [主机名] :[远程分支名]  #如果一次性删除多个，可以这样：git push [主机名] :[远程分支名] :[远程分支名] :[远程分支名] 。
【命令原理：将空分支推送到远程分支，结果自然就是远程分支被删除】

git push [主机名] --delete [远程分支名]

【删除本地分支】
git branch -D [分支名] 

【更名本地分支】
git branch -m [原分支名] [新分支名] ，若修改当前所在分支的名字，原分支名可以省略不写

【切换本地分支】
git checkout -b master  #切换当前分支到master分支
现在要一次性删除本地分支 ved 和 dev1。需要注意的一点：当前所在的分支不能被删除。切换到 master 分支，然后执行 git branch -D ved dev1 命令

`````


# Git tag and GitHub releases

## 目录

`````
Git 标签的作用
创建标签
查看标签
推送本地标签至远程仓库
删除标签
签出标签对应的提交版本
Git tag and GitHub releases 简介
`````

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
