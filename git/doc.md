# gitctl

## 安装

```bash
sudo apt install git-all
```

## 初始化配置
配置用户信息
```bash
 git config --global user.name "fursion"
 git config --global user.email fursion@fursion.cn
```
## 初始化向项目
### 本地项目
```bash
cd projectpath #进入项目根目录
git init #git 初始化
git add <file> 添加需要跟踪的文件
git commit ##初始化提交
```
## 远程仓库

### 查看远程仓库

```bash
git remote -v 
###以下为实机输出  origin ——这是 Git 给你克隆的仓库服务器的默认名字
fursion@fursionStudio:~/Linuxlearning$ git remote -v
origin  https://github.com/fursion/Linuxlearning.git (fetch)
origin  https://github.com/fursion/Linuxlearning.git (push)

```

### 添加远程仓库

```bash
#命令格式: git remote add <shortname> <url>
git remote add pb https://github.com/paulboone/ticgit
```
### 从远程仓库抓取和拉取
```bash
#git fetch <remote> 这个命令会访问远程仓库，从中拉取所有你还没有的数据。 执行完成后，你将会拥有那个远程仓库中所有分支的引用，可以随时合并或查看(需要手动合并)

```

### 推送到远程仓库

```bash 
# git push <remote> <branch>
git push origin master
```