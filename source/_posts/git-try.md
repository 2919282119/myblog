---
title: git应用
---

+ 查看文件状态

```
git status
```



- 文件状态

  >1. 未跟踪
  >2. 已跟踪
  >3. 暂存
  >4. 未修改
  >5. 已修改



- 未跟踪 到 暂存

```
git add <filename>
git add * 将所有已修改(未跟踪的文件暂存)
```

- 暂存 到 未修改

```
git commit -m "xxxx" 将暂存的文件存储到仓库
git commit -a -m "xxx" 提交所有已修改的文件(未跟踪的不会)
```

- 未修改 到 修改

  >修改代码后变未修改



#### 常用的git命令

```bash
git restore <filename> #重置文件
git restore * #重置所有文件
git rm <filename> #删除文件(提交后才可以删除)
git restore --staged <file name> #取消暂存文件
git log #显示过去的操作(节点信息)
git branch #显示现在的分支
git switch xxx #切换到xxx分支(如果没有xxx可以先创建)
git branch -d xxx #删除xxx分支
git branch -c xxx #创建xxx分支
git switch -c xxx #创建并切换到xxx分支(这个方便，更常用)
git merge <branchname> #合并分支
```

Head表示当前的

#### 远程库

```bash
git remote #列出当前关联的远程库
git remote add 库名(一般叫origin) url(xxx.git) #关联远程库
git remote remove origin #取消关联远程库
git push -u(表示推送之后直接关联) origin <branchname>
#(branchname一般是master,表示将本地的master推送给远程的master,关联之后就直接git push即可)
git fetch #从远程仓库拉取最新代码
git pull #从远程仓库拉取最新代码，并自动合并
```

- 注意：如果本地库的版本低于远程库，直接提交是提交不上去的
- 要想成功提交，要先git fetch从远程仓库拉取代码，但不会自动合并，要手动进行合并
- 比如：将本地的master分支和origin/master进行合并，在master分支下：git merge origin/master,然后解决冲突即可

