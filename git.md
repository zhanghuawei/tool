### GIT 常用命令
##### 提交命令
* git add -A // 暂存缓存区
* git commit -m '提交说明'
* git push origin master // 从暂存区提交到远程 master主分支 换成分支提到当前分支
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
* git push origin [name]:mater // 本地分支推送到master分支
* * * git push origin test:master // 提交本地test分支作为远程的master分支，远程的github就会自动创建一个test分支
* * * git push origin test:test  // 提交本地test分支作为远程的test分支

*


 

删除分支：$ git branch -d [name] ---- -d选项只能删除已经参与了合并的分支，对于未有合并的分支是无法删除的。如果想强制删除一个分支，可以使用-D选项
合并分支：$ git merge [name] ----将名称为[name]的分支与当前分支合并
创建远程分支(本地分支push到远程)：$ git push origin [name]
删除远程分支：$ git push origin :heads/[name]
我从master分支创建了一个issue5560分支，做了一些修改后，使用git push origin master提交，但是显示的结果却是'Everything up-to-date'，发生问题的原因是git push origin master 在没有track远程分支的本地分支中默认提交的master分支，因为master分支默认指向了origin master 分支，这里要使用git push origin issue5560：master 就可以把issue5560推送到远程的master分支了。

如果想把本地的某个分支test提交到远程仓库，并作为远程仓库的master分支，或者作为另外一个名叫test的分支，那么可以这么做。

$ git push origin test:master         // 提交本地test分支作为远程的master分支 //好像只写这一句，远程的github就会自动创建一个test分支
$ git push origin test:test              // 提交本地test分支作为远程的test分支

如果想删除远程的分支呢？类似于上面，如果:左边的分支为空，那么将删除:右边的远程的分支。

$ git push origin :test              // 刚提交到远程的test将被删除，但是本地还会保存的，不用担心
3.版本(tag)操作相关命令
查看版本：$ git tag
创建版本：$ git tag [name]
删除版本：$ git tag -d [name]
查看远程版本：$ git tag -r
创建远程版本(本地版本push到远程)：$ git push origin [name]
删除远程版本：$ git push origin :refs/tags/[name]
 
4.子模块(submodule)相关操作命令
添加子模块：$ git submodule add [url] [path]
如：$ git submodule add git://github.com/soberh/ui-libs.git src/main/webapp/ui-libs
初始化子模块：$ git submodule init ----只在首次检出仓库时运行一次就行
更新子模块：$ git submodule update ----每次更新或切换分支后都需要运行一下
删除子模块：（分4步走哦）
1)$ git rm --cached [path]
2) 编辑“.gitmodules”文件，将子模块的相关配置节点删除掉
3) 编辑“.git/config”文件，将子模块的相关配置节点删除掉
4) 手动删除子模块残留的目录
 
5.忽略一些文件、文件夹不提交
在仓库根目录下创建名称为“.gitignore”的文件，写入不需要的文件夹名或文件，每个元素占一行即可，如
target
bin
*.db
 
2. git pull：相当于是从远程获取最新版本并merge到本地
git pull origin master


## 常见问题处理
1.此项错误是由于本地仓库和远程有不同的开始点，也就是两个仓库没有共同的 commit 出现的无法提交。这里我们需要用到 
--allow-unrelated-histories。也就是我们的 pull 命令改为下面这样的：
git pull origin master --allow-unrelated-histories1
如果设置了默认分支，可以这样写
git pull --allow-unrelated-histories
