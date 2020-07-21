# Git

参考：[廖雪峰的Git教程](https://www.liaoxuefeng.com/wiki/896043488029600 "https://www.liaoxuefeng.com/wiki/896043488029600")

## Git 常用命令

1. `git config --global user.name "name"` #配置git使用用户
2. `git config --global user.email "mail"` #配置git使用邮箱
3. `git config --global color.ui true` #配置颜色
4. `git config --list` #查看当前配置
5. `git init` #初始为git工作目录
6. `git status` #查看git状态
7. `git reflog` #查看未来历史更新点
8. `git reset --hard 4bf5b29` #找到历史还原点的SHA-1值，就可以还原(值不写全,系统会自动匹配)
9. `git checkout -- file` #恢复暂存区至上一版本
10. `git add [file1] [file2] ...` #添加指定文件至暂存区
11. `git add [dir]` #添加指定目录至暂存区,包括子目录(递归添加)
12. `git add .` #添加当前目录所有文件至暂存区
13. `git rm [file1] [file2] ...` #删除工作区文件,并将这次删除放入暂存区
14. `git rm –cached [file]` #停止追踪指定文件，但该文件会保留在工作区
15. `git mv [file-old] [file-new]` #重命名文件,修改后放入暂存区
16. `git commit -m <message>` #把文件提交到仓库，`-m`后面输入的是本次提交的说明

## 基本步骤

1. 新建空文件
2. 初始化和配置：
    - `git init`：注意：在当前仓库下进行Git的初始化
    - `git config --global user.name "name"` #配置git使用用户
    - `git config --global user.email "mail"` #配置git使用邮箱

3. 添加和更改：
    - 暂存：`git add [file1] [file2] ...` #添加指定文件至暂存区
    - 提交：`git commit -m <message>`

4. Push / Pull：
    - Push：推送，将本地的一个分支Branch，推送到远程仓库的一个关联分支
    - Pull：拉取，Push的反向操作

5. Merge：
    - 合并：将子分支的更改，在比对之后，合并到master

## 版本控制

## 分支管理

## 远程仓库
