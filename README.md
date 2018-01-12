## git
(trying to rebase)
分布式版本控制系统(Distributed Version Control System)。

- 速度
- 简单的设计
- 对非线性开发模式的强力支持（允许成千上万个并行开发的分支）
- 完全分布式
- 有能力高效管理类似 Linux 内核一样的超大规模项目（速度和数据量）


```
$ ssh-keygen -t rsa -C "youremail@example.com"

$ git remote add origin git@server-name:path/repo-name.git
$ git push -u origin master

$ git log		查看提交历史
$ git reflog	查看命令历史
$ git log -- graph	查看分支合并图

$ git stash
$ git stash list
$ git stash apply
$ git stash pop
$ git stash apply stash@{0}

```
