### GIT 常用命令

##### 提交命令

* git add -A // 暂存缓存区
* git commit -m '提交说明'
* git reset --soft HEAD^ 撤回刚commit的内容
* git push origin master // 从暂存区提交到远程 master主分支 换成分支提到当前分支（或把本地分支push到远程）
* git pull origin master // 拉去 换成分支拉去分支

##### 本地仓库和远程仓库建立连接
* 本地有现成的项目，需要关联远程仓库或者提交到github
* git init 
* git add -A
* git commit -m '提交说明'
* git remote add origin [url] // 仓库地址
* git push -u origin master // 正常提交不用带 -u
* git pull --rebase origin master 如果远程有readme.md 本地没有执行
* git pull origin master --allow-unrelated-histories 同上

##### 操作远程仓库

* git clone https://github.com/zhanghuawei/tool.git // 克隆仓库
* git clone -b [分支名称] https://github.com/zhanghuawei/tool.git // 拉去远程分支，master分支可以直接切换
* git remote -v  // 查看远程仓库
* git remote add [name] [url] // 添加远程仓库
* git remote rm [name] // 删除远程仓库
* git remote set-url --push[name][newUrl] // 修改远程仓库
* git pull [remoteName] [localBranchName] // 取远程仓库
* git push [remoteName] [localBranchName] // 推送远程仓库

#### 操作分支

* git branch // 查看本地分支
* git branch -r // 查看远程分支
* git branch -a // 查看远程和本地所有分支
* git branch [name] // 创建分支
* git checkout [name] // 切换分支
* git checkout -b [name] // 创建分子并切换到当前分支
* git checkout -b [name] origin/[name] // 拉去远程分支到本地分支
* git branch -d [name] // 删除分支 -d 删除已经参与了合并的分支，未合并无法删除 -D 强制删除 
* git merge [name] // 与当前分支合并
* git merge origin/dev 合并其他分支或者他人创建的分支

#### 关联分支

* git fetch // 更新远程代码到本地仓库
* git branch --set-upstream [name] origin/[name] // 分支追踪远程分支（）
* git branch --set-upstream-to=origin/<remote_branch> <your_branch> // 分支追踪远程分支
* git branch -u origin/[name] // 设置当前分支跟踪远程分支origin/serverfix
* git branch -vv // 查看本地分支和远程分支的跟踪关系
* git push origin [name] // 本地分支推到远程
* git push origin [name]:master // 本地分支推送到master分支和创建远程分支
* git push origin [name]:[name] // 提交本地test分支作为远程的test分支
* git push origin test:test  // 提交本地test分支作为远程的test分支
* git push origin :test // 删除远程分支 本地会存储

#### 版本操作

* git tag // 查看版本
* git tag [name] // 创建版本
* git tag -d [name] // 删除版本
* git tag -r // 查看远程版本
* git push origin [name] // 创建远程版本
* git push origin :refs/tags/[name] // 删除远程版本

#### .gitignore 文件忽略 每个元素占一行
#### 恢复操作
* git log // 查看历史版本
  -- 如果commit的内容过多的话，我们可以进行过滤查找：
    - git log --pretty=oneline 调出所有commit记录
    - git log -g --author="用户名"   // 根据用户名过滤，模糊匹配
    - git log -g --grep "xx"  // 根据commit时候的提交信息查找，模糊匹配
* git reflog 调出所有在HEAD上的记录 
* git fsck --full找出没有被指向的记录.找出相应SHA值.
* git reset --hard commit_id 回到这个版本
#### OTHER

* git init // 初始化仓库
* git status // 查看变化

* git diff // 查看工作区和暂存区中的文件区别
* git diff --cached 比较的是暂存区和版本库的差别
* git diff HEAD 可以查看工作区和版本库的差别
* git push origin master --force 本地代码覆盖远程 慎用 




* mkdir [name] // 创建一个文件夹
* touch [name] // 创建一文件
* pwd // 查看位置
* ls [name] // 仓库下的文件
* ls -a // 显示隐藏文件
* cd // 打开文件夹


## 常见问题处理

* 此项错误是由于本地仓库和远程有不同的开始点，也就是两个仓库没有共同的 commit 出现的无法提交。这里我们需要用到 
--allow-unrelated-histories。也就是我们的 pull 命令改为下面这样的：git pull origin master --allow-unrelated-histories
* 如果设置了默认分支，可以这样写 git pull --allow-unrelated-histories
