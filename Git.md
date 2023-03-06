### 基础操作

- 初始化一个Git仓库：git init	
- 添加文件到暂存区：git add <file>  
- 确认修改，提交至仓库：git commit -m <message> 

### 自定命令

- 查看提交历史，颜色分类：git lg
- 开启代理：git spx
- 关闭代理：git uspx

### 远程仓库

- 关联远程与本地仓：git remote add <remote> git@github.com:<username/reponame.git>
- 推送本地库到远程：git push  [-u] <remote> <branch>
  - -u参数用于初次推送时关联本地库和远程库。
- 查看远程库信息：git remote -v
- 删除远程库信息：git remote rm <remote>
- 拉取远程库到本地库：git pull
- 建立远程分支和本地分支的关联：git branch --set-upstream-to <branch> <remote>/<branch>
- 本地创建对应远程分支的分支：git checkout -b <branch> <remote>/<branch>

### 分支管理

- 查看分支：git branch

- 创建分支：git branch <branch>

- 重命名分支：git branch -m <branch> <newBranch>

- 切换分支：git switch <branch>

- 创建+切换分支：git switch -c <branch>

- 合并到当前分支：git merge <branch>git 

- 删除分支：git branch -d <branch>

- 强制删除分支(分支未合并时)：git branch -D <branch>

  

- 暂存工作现场：git stash

- 回到工作现场并删除暂存：git stash pop

- 返回工作现场：git stash apply

- 删除已返回的工作现场的暂存：git stash drop

- 查看已暂存的工作现场：git stash list

- "复制"提交合并：git cherry-pick <commit>

### 标签管理

- 在当前分支最新提交上打标签：git tag <tag>
- 在当前分支的过去提交上打标签：git tag [-a] <tag> <commit> [-m "document"]
  - -a参数用来指定标签名
  - -m参数用来设定说明文字
- 查看标签：git tag
- 查看标签信息：git show <tag>
- 删除标签：git tag -d <tag>
- 推送标签到远程库：git push <remote> <tag>
- 推送全部标签到远程库：git push <remote> --tags
- 删除已推送的标签：
  1. 本地删除标签
  2. git push <remote> :refs/tags/<tag>



Write by lWaterLite.