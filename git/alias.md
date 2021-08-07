## 配置git alias（别名）提升开发效率

使用git 的alias(别名)配置可以简化一些git命令操作，对于需要在日常工作中需要频繁使用的命令，通过别名配置可以提高不少效率。
设置别名的语法如下：

```shell
git config --global alias.co checkout
```

也可以参考链接 [https://git-scm.com/book/en/v2/Git-Basics-Git-Aliases](https://git-scm.com/book/en/v2/Git-Basics-Git-Aliases)

以下是我个人的常用配置：

```shell
git config --global alias.st status
git config --global alias.b branch
git config --global alias.co checkout
git config --global alias.cm "commit -m"
git config --global alias.cma "commit --amend"
git config --global alias.pr "pull --rebase"
git config --global alias.pf "push --force-with-lease"
```


#### branch
```shell
# 配置：
git config --global alias.b branch

git b 
# 等价于
git branch

git b -d myBranch    # 删除分支myBranch
git b -m newName     # 分支改名为newName
```

#### checkout
```shell
# 配置：
git config --global alias.co checkout

git co master
# 等价于
git chekcout master

git co -b newBranch   # 创建并切换到newBranch分支
```

#### status
```shell
# 配置：
git config --global alias.st

git st
# 等价于
git status
```

#### commit -m
```shell
# 提交并输入commit message

# 配置：
git config --global alias.cm "commit -m"

git cm 'my commit message'
# 等价于
git commit -m 'my commit message'
```

#### commit --amend
```shell
# 修改上次提交。 提交粗心，漏了东西或有小错误，用这个命令很方便。

# 配置：
git config --global alias.cma "commit --amend"

git cma
# 等价于
git commit --amend  # 如果设置了vs code为git的编辑器，输入这条命令后，就会在VS code中弹出一个修改上次提交的界面
```

#### pull --rebase
```shell
# 我喜欢用pull --rebase， 这能让提交记录更简洁。

# 配置：
git config --global alias.pr "pull --rebase"

git pr origin master
# 等价于
git pull --rebase origin master # 每次推送前我都习惯先pull --rebase, 让当前分支的提交集中在一起且在提交记录的最后。
```

#### push --force-with-lease
```shell
# 搭配pull --rebase使用。 rebase过的分支不能直接push修改远端分支。而--force-with-lease是 force push的安全做法。

# 配置：
git config --global alias.pf "push --force-with-lease"

git pf origin myBranch
# 等价于
git push --force-with-lease origin myBranch
```


我们可以根据日常工作需要自行定制所需的别名，可以让较长的命令精简成少数几个字符，减少要输入的字符数也就减少了输错的概率。
可以提高效率并提高工作体验。

 
好，就到这了。


-------

谢谢观看
