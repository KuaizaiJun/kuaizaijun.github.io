##日记

#2021 01 19

昨天，今天两天配置了本地Git环境以及远程仓库Github

并且学会了Git的基本操作

配置完后测试不通过

>git报错

```bash
git@github.com: Permission denied (publickey).
```

解决办法：

>先清除所有的key-pair，在本地仓库目录中操作

```bash
ssh-add -D
rm -r ~/.ssh
```

>然后重新生成ssh密钥对(在上一个目录！！),一路回车

```bash
ssh-keygen -t rsa -C "kuaizaijun@qq.com"
```

接下来在上一个目录找到隐藏文件夹.ssh里面的公钥文件id_rsa.pub复制内容

然后在github设置里添加公钥

>最后在终端进行测试(通过)

```bash
kzj@linux:~/Github$ ssh -T git@github.com
Warning: Permanently added the RSA host key for IP address '13.229.188.59' to the list of known hosts.
Hi KuaizaiJun! Youve successfully authenticated, but GitHub does not provide shell access.
```

配置完成后马上Git了大佬学长们的Github仓库。

发现他们真的太厉害了，目标清晰，路径明确又落力执行。

再看看自己，不知道自己两个月能做些什么，希望自己往后的目标一定要清晰起来，制定明确的路径，一定要每天都执行。至少心中明确要完成什么。

接下来是一些常用命令

>命令git clone克隆一个本地库

```bash
kzj@linux:~/Github$ git clone git@github.com:TangMisaka23001/TangMisaka23001.github.io.git
正克隆到 'TangMisaka23001.github.io'...
remote: Enumerating objects: 573, done.
remote: Counting objects: 100% (573/573), done.
remote: Compressing objects: 100% (154/154), done.
remote: Total 2704 (delta 234), reused 548 (delta 211), pack-reused 2131
接收对象中: 100% (2704/2704), 4.84 MiB | 2.22 MiB/s, 完成.
处理 delta 中: 100% (1171/1171), 完成.
```

>初始化，初通过git init命令把这个目录变成Git可以管理的仓库

```bash
kzj@linux:~/Github$ git init 
已初始化空的 Git 仓库于 /home/kzj/Github/.git/
```

>用命令git add告诉Git，把文件添加到仓库(暂存区)

```bash
kzj@linux:~/Github$ git add kuaizaijun.github.io/
```

>用命令git commit告诉Git，把文件提交到仓库(master分支)

```bash
kzj@linux:~/Github$ git commit -m "add study"
[master（根提交） 076ddb6] add study
 8 files changed, 99 insertions(+)
 create mode 100644 kuaizaijun.github.io/README.md
 create mode 100644 kuaizaijun.github.io/img/trail.jpg
 create mode 100644 kuaizaijun.github.io/index.html
 create mode 100644 kuaizaijun.github.io/list/book/book.html
 create mode 100644 kuaizaijun.github.io/list/movie/movie.html
 create mode 100644 kuaizaijun.github.io/list/music/music.html
 create mode 100644 kuaizaijun.github.io/list/software/software.html
 create mode 100644 kuaizaijun.github.io/list/system/system.html
 ```

> git status命令可以让我们时刻掌握仓库当前的状态

```bash
zj@linux:~/Github$ git status 
位于分支 master
尚未暂存以备提交的变更：
  （使用 "git add <文件>..." 更新要提交的内容）
  （使用 "git checkout -- <文件>..." 丢弃工作区的改动）

        修改：     kuaizaijun.github.io/README.md

未跟踪的文件:
  （使用 "git add <文件>..." 以包含要提交的内容）

        Notes/
        TangMisaka23001.github.io/
        learnc/
        lsuplusclub/
        zhuzhenyuan.github.io/

修改尚未加入提交（使用 "git add" 和/或 "git commit -a"）
```

>查看修改的具体内容

```bash
kzj@linux:~/Github$ git diff
diff --git a/kuaizaijun.github.io/README.md b/kuaizaijun.github.io/README.md
index a8cb4eb..a6bdb0e 100644
--- a/kuaizaijun.github.io/README.md
+++ b/kuaizaijun.github.io/README.md
@@ -72,10 +72,44 @@ kzj@linux:~/Github$ git init
 >用命令git add告诉Git，把文件添加到仓库(暂存区)
 
 ```bash
-kzj@linux:~/Github$ cd kuaizaijun.github.io/
-kzj@linux:~/Github/kuaizaijun.github.io$ git add README.md 
+kzj@linux:~/Github$ git add kuaizaijun.github.io/
:q
```

>在git版本控制系统中，查看历史记录

```bash
kzj@linux:~/Github$ git log
commit 77750b51ea57814c1fd3e8dc8033025b99241b69 (HEAD -> master)
Author: kuaizaijun <kuaizaijun@qq.com>
Date:   Tue Jan 19 20:06:15 2021 +0800

    add git diff status

commit 076ddb64056ccaad87a02b16e5a25ce066276eea
Author: kuaizaijun <kuaizaijun@qq.com>
Date:   Tue Jan 19 19:59:25 2021 +0800

    add study
```

>创建文件和删除文件


```bash
kzj@linux:~/Github$ touch kuaizaijun.github.io/test.md
kzj@linux:~/Github$ git add kuaizaijun.github.io/test.md 
kzj@linux:~/Github$ git commit -m "touch test.md"
[master 1a61b7a] touch test.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 kuaizaijun.github.io/test.md
kzj@linux:~/Github$ rm kuaizaijun.github.io/test.md 
kzj@linux:~/Github$ git status 
位于分支 master
尚未暂存以备提交的变更：
  （使用 "git add/rm <文件>..." 更新要提交的内容）
  （使用 "git checkout -- <文件>..." 丢弃工作区的改动）

        修改：     kuaizaijun.github.io/README.md
        删除：     kuaizaijun.github.io/test.md

未跟踪的文件:
  （使用 "git add <文件>..." 以包含要提交的内容）

        Notes/
        TangMisaka23001.github.io/
        learnc/
        lsuplusclub/
        zhuzhenyuan.github.io/

修改尚未加入提交（使用 "git add" 和/或 "git commit -a"）
kzj@linux:~/Github$ git rm kuaizaijun.github.io/test.md
rm 'kuaizaijun.github.io/test.md'
kzj@linux:~/Github$ git commit -m "remove test.md"
[master 36d20c3] remove test.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 kuaizaijun.github.io/test.md
 ```

>把本地库关联到远程库

```bash
git remote add origin git@github.com:KuaizaiJun/learnc.git
```

>下一步，把本地库推送到远程库上

```bash
kzj@linux:~/Github/kuaizaijun.github.io$ git push -u origin master 
枚举对象: 7, 完成.
对象计数中: 100% (7/7), 完成.
使用 8 个线程进行压缩
压缩对象中: 100% (6/6), 完成.
写入对象中: 100% (6/6), 2.79 KiB | 2.79 MiB/s, 完成.
总共 6 （差异 1），复用 0 （差异 0）
remote: Resolving deltas: 100% (1/1), done.
To github.com:KuaizaiJun/kuaizaijun.github.io.git
   4caa384..6900ef3  master -> master
```

提送成功后github页面就和本地目录一模一样了

>从远程库克隆到本地库

```bash
kzj@linux:~/Github$ git clone git@github.com:KuaizaiJun/kuaizaijun.github.io.git
正克隆到 'kuaizaijun.github.io'...
remote: Enumerating objects: 88, done.
remote: Total 88 (delta 0), reused 0 (delta 0), pack-reused 88
接收对象中: 100% (88/88), 3.67 MiB | 2.09 MiB/s, 完成.
处理 delta 中: 100% (20/20), 完成.
```

>创建分支，日后再学

```bash
https://www.liaoxuefeng.com/wiki/896043488029600/900003767775424

Git鼓励大量使用分支：

查看分支：git branch

创建分支：git branch <name>

切换分支：git checkout <name>或者git switch <name>

创建+切换分支：git checkout -b <name>或者git switch -c <name>

合并某分支到当前分支：git merge <name>

删除分支：git branch -d <name>
```

一定要保存本地文件再添加到暂存区