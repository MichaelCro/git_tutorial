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

git log: 查看详细版本记录
git log --pretty=oneline: 查看简易版本记录


## 工作区/暂存区/版本库区别
工作区：电脑上看到的目录；<br>
暂存区：git add 是将工作的改变的内容提交到暂存区；<br>
版本库：git commit 是将暂存区的内容体检到版本库中；<br>



## 撤销修改与删除文件操作
### 撤销修改
```bash
git checkout -- readme.txt
```





```bash
pip3 install "fschat[model_worker,webui]"
```




## 准备工作
- 安装和配置Git
- 创建一个GitHub账户（如果需要）

## 基本概念
- 什么是Git？
- 什么是版本控制？
- 什么是仓库（Repository）？
- 什么是提交（Commit）？

## Git的基本命令
- 初始化一个仓库
- 添加文件到仓库
- 提交更改
- 查看提交历史
- 撤销更改
- 分支和合并基础
- 解决冲突

## 远程仓库管理
- 连接远程仓库
- 克隆远程仓库
- 推送本地更改
- 拉取远程更改
- 解决远程冲突

## 高级主题
- Git分支策略
- 子模块（Submodules）的使用
- Git Hook
- 重写提交历史
- 使用Git GUI工具

## 协作与开源
- 协作工作流程
- GitHub的使用
- 贡献到开源项目

## 最佳实践
- 代码审查
- 使用Issue跟踪问题
- 编写有意义的提交消息

## 常见问题解答
- 解决常见的Git问题和错误
- 有关Git的其他资源

## 结语
- 总结教程的关键点
- 鼓励读者进一步深入学习Git

## 参考资料
- 推荐阅读的书籍、文章和其他学习资源