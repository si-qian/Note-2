# Git 备忘

## 配置Git

- git config --global user.name "s_qian"	配置用户名
- git config --global user.email "s_qian@icloud.com"	配置用户邮箱
- git config --list	检查配置

## 获取帮助

- git <verb> --help	查看帮助

## 仓库操作


- git init	初始化仓库
- git add *.c	暂存
- git commit -m "messages"	提交
- git restore *.c	撤销工作区的修改
- git restore --staged *.c 从暂存区撤销修改
- git reset --hard HEAD~2 （回退到上上版本）版本回退	
- git reset --hard commit_id （回到该版本号）版本重回
- git log	查看提交历史
- git reflog	查看命令历史
- git status	检查文件状态
- git diff	查看文件更新
- git rm *.c	删除文件
- git tag -a v1.4 -m "my version 1.4" <commit-id>	针对某次提交创建标签
- git show	查看标签与提交信息

## 标签

- git tag	列出标签
- git push <remote-name> v1.5	推送标签（git push命令默认不会传送标签）
- git tag -d <tag-name>	删除标签
- git push <remote-name> :ref/tag/v1.4	更新远程库的标签（本地删除标签，不会自动删除远程库的标签）

## 远程操作

- git clone https://github.com/si-qian/TechNotes.git	克隆仓库
- git remote -v	查看远程仓库
- git remote show <remote-name>	查看某远程库的信息
- git remote add <shortname> <url>	添加远程仓库，并起名
- git remote nename <remote-name> <new-name>	重命名远程库
- git remote rm <remote-name>	删除远程库
- git fetch <remote-name>	只是拉取远程库的工作，并没有自动合并
- git pull <remote-name>	拉取关联分支的工作，并自动合并
- git push <remote-name> <branch-name>	将当前分支的工作推送到远程

