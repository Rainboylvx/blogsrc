---
title:git学习笔记

tags:
    - git
    - 学习笔记
---


## git资源

 - [廖雪峰git教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/)
 - [Git分支管理策略](http://www.ruanyifeng.com/blog/2012/07/git.html)
 - [在线git学习-推荐](http://pcottle.github.io/learnGitBranching/)


## 我的git 理解

Git的作者就是Linux开源OS的作者:**Linus Benedict Torvalds)**,大神就是牛!!!

Git一种版本管理软件,Git管理的是每一次的提交(相当于操作的多出的binary),可以把Git的管理想像成维护一个树结构,每一个结点是就是一个commit,有一个buffer区来存下add操作.

我们的操作就是在和个结点和结点指针之间移动,commit 增加一个结点并移动相对应的指针,branch 分出一个分支或移动分支指针,checkout 切换分支或移动HEAD指针
merge 合并两个branch(当然是从分支指针开始merge),


## git命令学习


| git commit                      | 提交增量,产生一个新的结点 [1]                           |
| git branch                      | 创建或切换到已有分支                                    |
| git merge                       | 合并,会把两不同的结点 并为一个孩子,也就是包含所有修改   |
| git rebase <dst>                | 取一系列commit点,copy,在别的dst放下,能到列线性的history |
| git rebase <src> <dst>          |                                                         |
| HAED                            | 指向当前commit点的指针,最近一次提交记录                 |
| git checkout <dst>              | 移动HEAD 到dst,HEAD^^,HEAD~1                            |
| git branch -f <branch> <dst>    | 强行移到分支到某个点                                    |
| HEAD^,HEAD~1,branch^,branch~1   | 祖先结点                                                |
| git reset HEAD^                 | 把当前分支记录退回到某个点                              |
| git revert HEAD                 | 回退,眀会重新生成一个commit                             |
| git cherry-pick <c1> <c2 <c3>   | 复制commit到当前HEAD下面                                |
| git rebase -i HEAD~4 --abvoeAll | 会有一个UI来手动选择                                    |
| git commit --amend              | 可以使用 git commit --amend 修改上一次的提交信息。      |
| git tags  <tag> <commit>        | 见下面                                                  |
| git describe                    | 显示离HEAD最近的tag                                     |
| git checkout HEAD^2             | 多个父亲时,选第二个父亲                                 |
| git fetch                       | 下载远程分支                                            |
| git pull                        | 下载并merge                                             |
| git pull -rebase                | 将远端的新提交fetch来,本地rebase到o/master上            |
|git b


git cherry-pick origin/master
git rebase origin/master
git merge origin/master


remotes track
1. 远端分支分出一个branch
git checkout -b totallyNotMaster origin/master
2.
git checkout -u origin/master totallyNotMaster


Git 手动建立tracking 

git branch --set-upstream <local> origin/<remote>

git push 参数
git push <remote> <place>
git push origin <src>:<dst>
如果<dst>不存在,那就会在远程程创建一个new branch,如果<src>为空 会删除远程的分支

git fetch


git tag  : 永远指向某个特定的commit,有新的commit里,
git checkout <tagname> 到tagname的点
http://blog.csdn.net/wangjia55/article/details/8793577

git describe <ref>  ref 是一个位置commit

git revert :回退某次提交,并重新提交,相当于代码恢复修改前,也就说revert也是一个commit,只是比较特殊,会修改某些操作
git reset :回退到某次提交,同时回退修改log,但是修改内容回退到本地local buffer,由用户确定是不是checkout丢弃


gitk
git log 
    --pretty=oneline


### git 处理冲突

### git 使用原则

 - 多多commit
 - 不要commit half work
 - 主分支 master 只进行 push 和 fetch ,pull 操作,本地有一个dev分支
 - git 分支管理策略 http://www.ruanyifeng.com/blog/2012/07/git.html

[1] : 如果我们
```
git commit -m "3"
git checkout HEAD^
git commit -m "4"
git branch -f master HEAD

上面的操作很有意思
我们强制的HEAD指向上一个结点,然后创建一个新的结点,移动master

没有分支名,也没有HEAD指针的分支,会被删除(也许仅仅是看不到)
因为分支名也是指针,没有指针指向的分支会不见!?
上面说的可能不太对?因使用gitk 和 git log 都看不到,但是使用Git gui 可以看到前三条命令的history!! 难受
```
