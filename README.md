## git

从根本上来讲 Git 是一个内容寻址（content-addressable）文件系统，并在此之上提供了一个版本控制系统的用户界面。 

- 速度
- 简单的设计
- 对非线性开发模式的强力支持（允许成千上万个并行开发的分支）
- 完全分布式
- 有能力高效管理类似 Linux 内核一样的超大规模项目（速度和数据量）


### 常用命令

```
# 生成 key
$ ssh-keygen -t rsa -C "youremail@example.com"

# 本地项目与远程 git 关联
$ git init
$ git remote add origin git@server-name:path/repo-name.git
$ git push -u origin master

# 通用的提交步骤
$ git add .
$ git commit -m 'commit log'
$ git push origin master

$ git diff (--cached)

# 查看日志
$ git log		查看提交历史
$ git reflog	查看命令历史
$ git log -- graph	查看分支合并图

# 分支操作
$ git branch -b feature-branch  新建分支
$ git checkout branch-name      切换分支
$ git branch [-a]   查看分支
$ git branch -d feature-branch      删除本地分支
$ git push origin :feature-branch      将删除推送至远程

# 使用暂存
$ git stash
$ git stash list
$ git stash apply
$ git stash pop
$ git stash apply stash@{0}

# 打标签
$ git tag v1.0		创建标签
$ git tag v0.9 6224937		为指定的 commit 创建标签
$ git tag -a v0.1 -m "version 0.1 released" 3628164	为标签添加日志
$ git tag		查看当前所有标签
$ git tag -d v0.1	删除标签
$ git push origin :reg/tags/v0.1	已推送至远程的标签 -d 删除后需要 push
$ git push origin v0.1	将标签推送至远程
$ git push origin —tags	将所有本地未推送的标签推送至远程
```

> HEAD	当前版本
>
> HEAD^	上一个版本
>
> HEAD^^	上上个版本
> 
> HEAD~10  往上10个版本

### git 内部原理

#### 底层命令和高层命令

- 底层（plumbing）命令

在目录下执行 `git init` 命令之后，会生成一个 `.git` 目录，这个目录包含了几乎所有git 存储和操作的对象。

```
➜  learn-git git:(master) ll .git
total 56
## 指示目前被检出的分支
-rw-r--r--   1 letica  staff    23B  1 12 15:26 HEAD
## 项目特有配置项
-rw-r--r--   1 letica  staff   309B  1 12 14:41 config
## 仅供 gitweb 程序使用
-rw-r--r--   1 letica  staff    73B  1 12 14:40 description
## 包含客户端或服务端的钩子脚本（hook scripts）
drwxr-xr-x  12 letica  staff   384B  1 12 14:40 hooks
## 保存暂存区信息
-rw-r--r--   1 letica  staff   236B  1 12 15:26 index
## 包含一个全局性排除（global exclude）文件，用以放置那些不希望被记录在 .gitignore 文件中的忽略模式（ignored patterns）
drwxr-xr-x   3 letica  staff    96B  1 12 14:40 info
drwxr-xr-x   4 letica  staff   128B  1 12 14:41 logs
## 存储所有数据内容
drwxr-xr-x  66 letica  staff   2.1K  1 12 15:26 objects
## 存储指向数据（分支）的提交对象的指针
drwxr-xr-x   5 letica  staff   160B  1 12 14:41 refs
```

- 高层（porcelain）命令
通常使用的 git 命令都是高层命令。
