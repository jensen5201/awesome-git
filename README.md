# Awesome git

## 配置git账号

- git config  <--local / --global> alias.xx xx / user.name xx
- git config <--local / --global> --list
- git config --global --bool pull.rebase true

## 常用操作

- git clone [-o / origin] [-b master] git@xxxxx
- git init
- git status
- git checkout [-b] master
- git add .
- git commit . -m ‘xxxxx'
- git push
- git pull [--rebase] 如果有多人在同一个分支上操作，推荐加--rebase，可以优化gitlog记录线方便查看
- git checkout . 撤销修改【慎用】
- git checkout head filename 用head版本的对应文件替换暂存区和工作区的文件
- git reset .  回退git add
- git clean [-f / -d] 删除文件/文件夹（-n 可以预览将要删除的文件）

## 仓库操作

- git remote add origin git@xxxxxxxxxx   添加远端仓库
- git remote rename <oldName> <newName>  修改仓库名
- git remote  查看远端仓库
- 同步仓库分支状态
  - git remote update origin --prune
  - git fetch --all

## 关联本地分支到远端分支

- git push -u origin master
- git branch --set-upstream-to=origin/master master

## 创建本地分支并推送到远端【重要】

- git checkout -b develop   +   git push --set-upstream origin develop
  - git branch develop
  - git checkout develop
  - git push origin develop
  - git branch --set-upstream-to=origin/develop

## 拉取远端分支到本地【重要】

- git checkout -b develop origin/develop   +   git push
  - git branch develop
  - git checkout develop
  - git push -u origin develop

## 分支操作

- git branch [-l / -r / -a] 查看分支
- git branch -vv 查看当前分支的基
- git branch master [origin/master] 创建分支 [基于远端分支]
- git checkout master 切换分支
- git branch -d master 删除分支
- git push origin -d master 删除远程分支

## 合并操作

- git merge b a 合并b到a中
- git merge origin b a 合并远端b到a中
- git merge --abort  合并发生冲突时放弃合并

## 暂存操作

- git stash [save ‘xxxxxx’] 暂存当前修改
- git stash pop [stash_id] 恢复进度
- git stash drop [stash_id] 删除进度
- git stash clear 清空进度
- git stash list 查看暂存

## 回退版本

- 方式一 reset
  - git fetch --all  同步所有分支的状态
  - git reset [--hard]  <origin/master / commit_id / head>   回滚到指定提交
  - git push -f

- 方式二 revert 【推荐】可以保留回退之前版本，方便查看记录
  - git revert -n <commit_id>
  - git add + git commit
  - git push


## 标签操作

- git tag 查看所有tag
- git tag -a tagname -m “注释”   本地添加tag
- git push [origin] --tags 推送tag到远程
- git tag -d tagname 删除本地tag
- git push origin -d tagname 删除远程tag

## 子模块操作

- git submodule init
- git submodule update

## 删除远端文件

- git rm -r --cached a/2.txt

## 查看git操作记录

- git reflog
- git log --oneline
- 获取commit_id
  - git rev-parse  [—short] HEAD 获取最近的一次commit_id
- 复制某分支的部分提交到另一个分支
  - git cherry-pick commit_id 单个复制
  - git cherry-pick (commit_startId..commit_endId] 多个复制，不包括startId
