### GIT 常用命令

##### 提交命令

* git add -A // 暂存缓存区
* git commit -m '提交说明'
* git push origin master // 从暂存区提交到远程 master主分支 换成分支提到当前分支（或把本地分支push到远程）
* git pull origin master // 拉去 换成分支拉去分支

##### 操作远程仓库

* git clone https://github.com/zhanghuawei/tool.git // 克隆仓库
* git remote -v  // 查看远程仓库
* git remote add [name] [url] // 添加远程仓库
* git remote rm [name] // 删除远程仓库
* git remote set-url --push[name][newUrl] // 修改远程仓库
* git pull [remoteName] [localBranchName] // 取远程仓库
* git push [remoteName] [localBranchName] // 推送远程仓库

#### 操作分支

* git branch // 查看本地分支
* git branch -r // 查看远程分支
* git branch [name] // 创建分支
* git checkout [name] // 切换分支
* git checkout -b [name] // 创建分子并切换到当前分支
* // 创建分支，切换到当前分支和关联远程分支
* git branch -d [name] // 删除分支 -d 删除已经参与了合并的分支，未合并无法删除 -D 强制删除 
* git merge [name] // 与当前分支合并
* git push origin [name] // 本地分支推到远程
* git push origin [name]:master // 本地分支推送到master分支和创建远程分支
** git push origin [name]:[name] // 提交本地test分支作为远程的test分支
** git push origin test:test  // 提交本地test分支作为远程的test分支
** git push origin :test // 删除远程分支 本地会存储
#### 版本操作
* git tag // 查看版本
* git tag [name] // 创建版本
* git tag -d [name] // 删除版本
* git tag -r // 查看远程版本
* git push origin [name] // 创建远程版本
* git push origin :refs/tags/[name] // 删除远程版本

#### .gitignore 文件忽略 每个元素占一行

## 常见问题处理
* 此项错误是由于本地仓库和远程有不同的开始点，也就是两个仓库没有共同的 commit 出现的无法提交。这里我们需要用到 
--allow-unrelated-histories。也就是我们的 pull 命令改为下面这样的：git pull origin master --allow-unrelated-histories1
* 如果设置了默认分支，可以这样写 git pull --allow-unrelated-histories
