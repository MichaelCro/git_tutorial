# Git tutorial

## 简介
- 学习git过程中的一些记录

## 目录
- 创建版本库
- 版本回退
- 撤销修改与删除文件操作
- 远程仓库
- 创建与合并分支
- bug分支
- 多人协作
- git常用命令汇总

## 创建版本库
创建目录，将在当前目录变成git可以管理的仓库；
```bash
git init
```
在当前目录下创建readme.md文件，将该文件添加至暂存区当中；
```bash
git add readme.txt
```
将文件提交到仓库；
```bash
git commit -m "备注信息。。。"
# -m 添加备注信息
```

git diff: 查看当前目录内容与仓库中内容的区别；<br>
git status: 查看当前目录状态；<br>



## 版本回退
首先查看版本记录信息；
```bash
git log
```
进而执行版本回退命令；
```bash
git reset --hard 
```

git log: 查看详细版本记录<br>
git log --pretty=oneline: 查看简易版本记录<br>


## 工作区/暂存区/版本库区别
工作区：电脑上看到的目录；<br>
暂存区：git add 是将工作的改变的内容提交到暂存区；<br>
版本库：git commit 是将暂存区的内容体检到版本库中；<br>



## 撤销修改与删除文件操作
### 撤销修改
```bash
git checkout -- readme.txt
```

### 删除文件
删除某个文件之后，执行，
```bash
git commit -m "备注信息。。。"
```

如果想恢复删除的文件（该文件没有被执行commit），执行，
```bash
git checkout -- file1.txt
```


## 远程仓库
### 本地创建git仓库，并同步到github官网上
- 第一步：创建SSH Key。<br>
在用户主目录下，看看有没有.ssh目录，如果有，
再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，
如果有的话，直接跳过此如下命令，如果没有的话，打开命令行，输入如下命令：
```bash
ssh-keygen -t rsa -C "your_email@example.com"
```
id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。

- 第二步：登录github,打开” settings”中的SSH Keys页面，然后点击“Add SSH Key”，填上任意title，在Key文本框里黏贴id_rsa.pub文件的内容。<br>
- 第三步：登录github上，然后在右上角找到“create a new repo”创建一个新的仓库。<br>
- 第四步：把本地仓库的内容推送到GitHub仓库。<br>
```bash
git remote add origin https://github.com/xxx/xxx.git
git push origin main
```
### github官网创建，并同步到本地
- 第一步：首先，登录github，创建一个新的仓库。
- 第二步：使用 git clone 到本地库；



## 创建与合并分支
创建分支dev，并切换到该分支
```bash
git branch dev
git checkout dev
```
在dev进行修改操作提交之后，切换到main，进而将main分支与dev进行合并
```bash
git checkout main
git merge dev
```
git branch: 查看所有分支信息。<br>
git branch -d dev: 删除dev分支。<br>


## bug分支
描述：当前正基于dev分支，进行bug1的修改，可进行到一半时，有一个优先级更高的bug2，现在需要优先完成bug2，bug1只能先搁置。
此时可以用到 git stash 将当前的工作现场“隐藏起来”，等以后恢复现场后继续工作。
```bash
git stash
git checkout main
git branch dev2 # 对应bug2
git checkout dev2
```
待dev2完成开发后，切换至main分支，并进行合并，
```bash
git checkout main
git merge dev2
```
进而回到dev分支继续开发，
```bash
git checkout dev
git stash list # 查看所有stash版本
git stash apply stash@{x}
```


## 多人协作
设定现在远程只有master主分支，a员工本地有master主分支以及dev分支，b同事需要和a同事同时进行开发，
那么a需要先将dev分支上传到远程仓库，b再进行拉取，流程如下，
```bash
git push origin dev # a同事将dev分支上传至远程
git clone https://github.com/xxx/xxx.git # b同事先拉取主分支main
git checkout –b dev origin/dev # b同事继续同步dev分支
```
git checkout –b dev: 基于当前分支创建dev分支副本；<br>
git checkout –b dev origin/dev: 本地创建dev分支，该分支为远程dev分支的副本；<br>

同事b在dev开发完成之后，需要提交到远程dev分支，可同事a在b提交之前已经完成过一次提交，那么同事b需要先git pull远程仓库，进而继续git push；
```bash
git pull # 有可能会需要解决冲突
git push origin dev
```
因此：多人协作工作模式一般是这样的：
- 首先，可以试图用git push origin branch-name推送自己的修改.
- 如果推送失败，则因为远程分支比你的本地更新早，需要先用git pull试图合并。
- 如果合并有冲突，则需要解决冲突，并在本地提交。再用git push origin branch-name推送。



## 常见命令汇总
- git branch: 查看本地分支有哪些
- git branch -a: 查看远程分支有哪些
- git branch demo: 建立demo分支。（demo分支与当前分支保持一致）

- git checkout demo: 切换至demo分支。

- git push origin --delete dev: 删除远程dev分支

- git checkout -b demo: 创建demo分支，并切换至demo分支


