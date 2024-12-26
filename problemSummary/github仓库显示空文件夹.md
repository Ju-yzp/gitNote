# 情景
1. 我们上传项目以后，发现远程仓库内有的文件夹为空，但是我们的工作区同一个文件夹内是有文件的
- 远程仓库如下：
[空项目](../image/emptyProject.png)
## 原因
1. 克隆其他人仓库时，文件夹中带有.git文件夹导致，所以克隆他人仓库后，检查项目文件夹下是否含有.git文件夹
## 措施

```
#ubuntu下
#终端输入：
ls -a
#如果出现.git,则输入以下命令:
rm -rf .git
```

```
#ubuntu下
#终端输入
git rm --cached <目标文件夹>
#重新上传
git add <目标文件夹>
git commit -m <msg>
git push
```