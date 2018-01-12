## git

分布式版本控制系统(Distributed Version Control System)。

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
