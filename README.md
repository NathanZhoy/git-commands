# git-commands

# git常用命令
```shell
git init #初始化git仓库
git status #查看当前状态（是否有修改）
git add -A #天添加全部修改的文件
git commit -m "<msg>" #提交 msg=描述本次提交的信息
git push #推送修改到远程
git push origin branch-name:remote-name #将本地分支branch-name提交到远程别名为origin的remote-name

git stash save "msg" #暂时保存当前修改并回到修改前 msg=描述暂存的信息
git stash list #查看暂存列表本次
git stash apply stash@{1} #恢复第<stash@{1}>个暂存数据， stash@{1} 不写则默认上一次save的数据

git log #查看操作记录
git branch #查看本地全部分支
git branch <name> #新建分支
git checkout <name> #切换分支
git checkout -b <name> #创建分支并且切换到该分支
git pull <remote-alias> <branch-name>#拉取远程<remote-alias>的<branch-name>分支

## 推送命令
git push --set-upstream origin master #（没有追踪的情况下{连接模式#6实现追踪}）推送并且追踪远程分支master

git push origin HEAD:main #当本地分支与追踪的远程分支名字不相同时，推送到远程main分支，推送到远程main分支

git push origin HEAD:main #当本地分支与追踪的远程分支名字不相同时，推送远程相同分支，不存在则建立远程分支，推送到远程main分支

git push #当本地分支与追踪的远程分支名字相同时，推送到远程对应分支

##修改近期提交过的commit方法
git rebase -i HEAD~n #n代表要修改的最近提交次数

##然后在打开的文件内，把要修改的次数由pack给为edit
##然后保存，然后进行修改，使用git commit --amend保存
##修改满意之后，使用git rebase --continue恢复

```

# git通用步骤

## 获取一个仓库（克隆模式）

1、在本地新建一个文件夹

```shell
mkdir gitWorkplace #创建文件夹
cd gitWorkplace/ #进入文件夹
```

2、在GitHub上面创建一个仓库（Repository），拿到对应仓库的地址，然后使用git clone <地址>命令。创建仓库默认的分支为origin/main

```shell
git clone <url>
```

3、这个时候本地仓库就和远程仓库一模一样，并且分支也是对应的

## 获取一个仓库（链接模式）

1、在本地新建一个文件夹

```shell
mkdir gitWorkplace
cd gitWorkplace/
```
2、在GitHub上面创建一个仓库（Repository），拿到对应仓库的地址。创建仓库默认的分支为origin/main

3、初始化本地仓库，使用git init命令

```shell
git init
```

4、将本地仓库与远程仓库进行链接，通过远程仓库的地址

```shell
git remote add origin <url>
```

5、然后把远程仓库的分支拉取到本地，本地默认分支为master

```shell
git pull origin main #拉取远程main分支
```

6、将本地master分支追踪到远程main分支，git branch --set-upstream-to=origin/<remote-branch-name> <local-branch-name>

```shell
git branch --set-upstream-to=origin/main master #把本地master分支追踪到远程main分支
```


7、推送当前本地分支修改到远程分支，git push origin HEAD:<remote-branch-name>

```shell
#当本地分支与追踪的远程分支名字不相同时，推送到远程main分支
git push origin HEAD:main #推送到远程main分支

#当本地分支与追踪的远程分支名字不相同时，推送远程相同分支，不存在则建立远程分支
git push origin HEAD:main #推送到远程main分支

#当本地分支与追踪的远程分支名字相同时
git push #推送到远程对应分支
```








