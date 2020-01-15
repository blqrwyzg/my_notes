## git**常用命令**

[官网]: https://git-scm.com/book/zh/v2
[廖雪峰]: https://www.liaoxuefeng.com/wiki/896043488029600
[讲解]: https://juejin.im/post/5dba383cf265da4d144e7cf5



### **--配置用户信息**

```
git config --global user.name + '名字'

git config --global user.email + 邮箱
```



### --查看配置信息 

`git config --list`



### **git项目概念**

--工作区 

--暂存区 or 索引

--版本库



### **命令**

#### 常用命令

--检查文件状态	`git status + -s（可选）`     ?? 未跟踪、A 新添加到暂存区、右m 修改 但未缓存、左m修改，放入缓存

--初始化仓库	`git init` 

--添加到暂存区域or跟踪文件	`git add +文件名` （.）代表全部

--提交到版本库	`git  commit -m '注解‘`

--克隆仓库	 `git clone + 地址+命名（可选）` 	

--查看文件与暂存区区别	`git diff`

--未暂存文件提交版本库 	`git commit -a -m  '注解'`



--移除文件 1、删除文件 2、 `git rm +文件名字` ，下次commit后，文件就不纳入版本控制管理中了。

--吧文件从git仓库删除，但保留文件在工作目录	`git rm --cached+文件名`

​		git rm -f <file> 强制 如果文件在暂存区

--移动文件也就是改名	`git mv 本名 新名` 

--查看历史 

​	--git log

​	--git log -p -2 最近两次提交差异

​	--git log --stat 简略统计信息

​	-等等等

--为上次提交补充

```console
$ git commit -m 'initial commit'
$ git add forgotten_file
$ git commit --amend
```

--撤销修改将文件还原上次提交时的样子 `git checkout --文件`



##### 版本回退：

​	--`git reset --hard HEAD^ （上个版本）`

​	--`git reste --hard <版本号>`

​	--`git reflog` 命令历史



##### 撤销修改：

--撤销文件在工作区的修改	`git checkout -- <文件名>` 	

​		--回到版本库状态  

​		--回到暂存区状态

--撤销暂存区 `git reset HEAD +文件名`



##### 删除文件

​	--在工作区删除文件后

​		--	`git rm <文件>`

​		--	`git commit -m ''`

--删错了恢复到最新版本

​	--用版本库里的版本替换工作区的版本	`git checkout -- <文件>`



### git分支

--切换并创建分支	`git checkout -b <名称>`

--查看分支	`git branch`

--切换分支	`git checkout <分支名>`









### 远程仓库

--添加远程git仓库	 `git remote add 简写+url`

--查看配置的远程服务器 	`git remote`

​		-- 	`git remote -v 	命名与url`

##### 配置github

--将公钥添加到github，如果公钥不在github 则只能获取 不能推送

--在github上建立仓库

--在本地添加远程仓库：	`git remote add <shortname> <url>`		

--推送远程仓库：	`git push -u 命名 分支` （**第一次推送**将本地master 与远程master关联）

​		--	`git push <命名><分支>`（关联后就可以简化命令）

--克隆本地库		`git clone <url>`	

--拉去仓库中内容		`git fetch <名>`

