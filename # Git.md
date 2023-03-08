# Git指令
```git

git init  --使用当前目录作为git仓库
git init path --使用path作为git仓库

git add fileName/path  --把fileName/path加入到暂存区

git commit -m --把暂存区内容添加到仓库
git commit fileName1 fileName2 -m --把暂存区的fileName1和fileName2加到仓库中
git commit -a -- -a 参数设置修改文件后不需要执行 git add 命令，直接来提交

git status  --查看仓库当前状态，显示有变更的内容

git diff  --比较文件的不同，即暂存区和工作区的差异

git reset --回退版本

git rm fileName --将fileName从文件区和暂存区删除
git rm --cached fileName  --将fileName从暂存区删除，但是保留在文件区

git log - 查看历史提交记录。

git mv fileName newFileName 
git mv -f fileName newFileName  --新文件名已经存在，但还是要重命名它

```