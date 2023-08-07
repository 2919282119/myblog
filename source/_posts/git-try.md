---
title: git应用
tags: ["music","sport","movies"]
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
git push -u(表示推送之后直接关联) origin xxx(:yyy)
#这句表示将本地的xxx分支推送给远程的xxx分支,如果加:yyy，表示将本地的xxx分支推送给远程的yyy分支
#(branchname一般是master,表示将本地的master推送给远程的master,关联之后就直接git push即可)
git fetch #从远程仓库拉取最新代码,要手动合并 git merge origin/master
git pull #从远程仓库拉取最新代码，并自动合并
```

- 注意：如果本地库的版本低于远程库，直接提交是提交不上去的
- 要想成功提交，要先git fetch从远程仓库拉取代码，但不会自动合并，要手动进行合并
- 比如：将本地的master分支和origin/master进行合并，在master分支下：git merge origin/master,然后解决冲突即可



#### 节点回退

- 先通过git log查看所有节点，然后通过上下键找到想要换的节点
- 通过git switch commitid(输入前几位即可)，但需要在后面加 - -detach
- 注意：这样操作会出现“分离头指针”的问题

<!-- <img src="git-try/头指针分离.png" alt="分离头指针"/> -->

- HEAD指针指到哪里就显示哪里的代码，按理说HEAD应该指到某个分支上，如图所示就是节点回退产生分离头指针的问题，这种状态下也能修改代码，但这种修改不会出现在任何分支上（所以没什么意义）
- 要想解决，可以选择在C2上先创建一个新分支，然后在这个分支上进行操作git switch -c xxx



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

  

#### bug解决方案

当我把本地的代码改完之后（在test分支），如果我想直接把远程的master分支变成这个，两种办法:

1. 先把test分支和master分支进行merge（准确来说是把master分支和test进行merge，因为合并之后是前面的），merge之后再git pull从远程仓库拉取代码，然后修改矛盾代码之后再次commit，然后再push
2. 切到xxx分支（或标签），删除本地和远程的master分支，然后新建本地master分支，将xxx分支merge到master分支，然后再推到远程仓库(==这种一般是对于不需要保留master的==)



- 据说vscode是会先拉取后提交的

<!-- <img src="https://postimg.cc/LY5665Rf" alt="远程仓库较新" style="zoom:90%;" /> -->

有时报这种错就是因为远程库的代码要比本地库的要新，这种情况要先git pull的(==先拉再推==)





#### 子模块问题

- hexo安装新的主题（如butterfly）使用以下命令：

```bash
git clone -b master https://github.com/2919282119/hexo-theme-butterfly.git themes/butterfly #这个命令表示将该主题安装在themes/butterfly目录下
```

- 这里是将别人的仓库先fork到自己的Github仓库，所以上面是用的自己仓库的链接，如果不fork而是直接用别人的仓库，子模块会没有修改权限
- 然后将_config.yml中的theme改为butterfly(和目录名字一样)
- 然后回到项目根目录添加子模块，使用以下命令：

```bash
git submodule add xxx(上面的仓库链接)
git commit -m "添加了子模块"
git push
```

- #这样就会在根目录下生成一个.gitmodules文件，内容如下：

```bash
[submodule "sub/b-project"]
	path = sub/b-project
	url = https://github.com/2919282119/hexo-theme-butterfly.git
```

- 想要更新子模块的内容，修改完之后，在子模块（如butterfly）路径下执行以下命令:

```bash
git add *
git commit -m "提交子模块修改"
git push
```

- 然后在主模块提交子模块更新

```bash
git add *
git commit -m "提交子模块更新"
git push #这样子模块就更新完毕了
```
