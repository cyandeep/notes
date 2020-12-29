### 1.版本回退

- git reset --hard <版本号>
- git restore --staged <filename>  #恢复索引
- git restore <filename> #恢复工作区

### 2.分支管理

- git checkout -b <分支名>
- git branch
- git checkout <分支名>
- git merge <分支名> #将指定分支合并到当前分支
- git branch -d <分支名>

### 3.远程仓库

- git remote add origin <连接>
- git clone <连接>
- git push -u origin <分支名>
- git pull -u origin <分支名>