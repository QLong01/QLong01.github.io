# **Git版本管理工具学习**

> Writed on 250213

> Author: Jack_hui

## **Git架构概述**
执行下段代码，会在当前文件夹下生成一个.git/文件夹，并进行版本初始化，便于后续进行版本管理
``` shell
git init
```

工作区(Working Directory):在本地环境下通过相关集成开发工具(`ide`)自己修改的代码等相关文件

暂存区(Stage):通过`git add`将修改过的文件添加到暂存区，该区域由Git进行管理

本地仓库(Repository):通过`git commit`根据暂存区中的文件对本地仓库进行修改以及更新，后续可利用`git log`快速查看这些commits或进行版本回退

## **基本操作**
``` shell
#查看git版本
git --version
#查看用户名和邮箱
git config user.name
git config user.email
#修改用户名和邮箱
git config --global user.name <...>
git config --global user.email <...>
```

### **git add**
``` shell
#可以添加文件，也可添加文件夹，也可按照通配符来添加
git add <file>
```

### **git commit**
``` shell
# 生成一次提交记录，后面附带修改信息
git commit -m "<message>"
# 覆盖上一次的提交
git commit -m "<message>" --amend
```

### **git status**
查看每个区的状态，比如当前在哪个分支，修改提交到哪一步等

### **git log**
查看提交日志

### **gitignore**
在`git add`过程中忽略掉不想上传的文件，比如第三方库，图片等

### **版本回退**
``` shell
# 用本地仓库中的指定文件覆盖当前工作区
git restore --source HEAD <file>
# 用暂存区中的指定文件覆盖当前工作区
git restore <file>
# 用本地仓库中的指定文件覆盖当前的暂存区
git restore --staged <file>

# 直接回退到指定的commit版本，输入提交id，不用输全
git reset --hard <commit>
# 撤销某一个commit带来的修改，生成新commit！！！
git revert <commit> #git直接提交
git revert -n <commit> #自己提交
```

### **分支**
``` shell
git branch --create(-c) <branch> #创建分支
git branch # 查看本地分支
git switch <branch> #切换分支

#版本更新步骤
# 切换到主分支
git switch main
# 将原来开发新功能的分支合并过来
git merge <branch>
# 合并后再删掉原来的分支
git branch --delete(-d) <branch> 
```

### **合作开发**
``` shell
# 先拉取，再合并
git fetch <repo-nickname>
git merge
```