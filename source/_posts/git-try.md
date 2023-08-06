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



#### 节点回退

- 先通过git log查看所有节点，然后通过上下键找到想要换的节点
- 通过git switch commitid(输入前几位即可)，但需要在后面加 - -detach
- 注意：这样操作会出现“分离头指针”的问题

<img src="../AppData/Roaming/Typora/typora-user-images/image-20230806111150677.png" alt="分离头指针" style="zoom:60%;" />

- HEAD指针指到哪里就显示哪里的代码，按理说HEAD应该指到某个分支上，如图所示就是节点回退产生分离头指针的问题，这种状态下也能修改代码，但这种修改不会出现在任何分支上（所以没什么意义）
- 要想解决，可以选择在C2上先创建一个新分支，然后在这个分支上进行操作



#### Tag

- 为了便于快速找到之前某个稳定版本的节点，可以给某个节点打上一个标签

```bash
git tag v1.0(名字可以自己随便设) #这表示给当前节点打上v1.0标签
git tag v1.2 <commitid> #这表示给某个节点打上标签
git switch <tagname> #加了标签后就可以这样切换了
git push origin v1.0 #将这个标签推送到远程仓库
git push origin --tags #将所有标签推送到远程仓库
git tag -d <tagname> #删除标签
git push --delete <tagname> #删除远程仓库标签
```



- 命令行输入code .回车可以快速打开vscode
