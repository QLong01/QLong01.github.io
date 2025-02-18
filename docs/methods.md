# **个人网站搭建**

> Writted on 250203

> Author: Jack_hui

> 个人感觉利用第三方建站碰到的坑不能说多，但也不少，在此记录一下

## **准备**
采用的是`github pages`+`mkdocs`，并利用`material for mkdocs`进行美化

### **安装mkdocs**
安装之前需要`python`相关依赖，配置好环境后执行：
``` shell
pip install mkdocs
# 新建mkdocs项目
mkdocs new blogger
# 进入创建项目
cd blogger/
# vscode打开
code.
```

### **安装Material for MkDocs**
``` shell
pip install mkdocs-material
```
安装好后，打开mkdocs.yml文件，增加如下：
```yml hl_lines="2 3 4"
site_name: My site
site_url: https://mydomain.org/mysite(改成自己的发布网址)
theme:
  name: material
```
然后试运行，执行：
```shell
mkdocs serve
```

## **远程连接**
这里利用`vscode`连接`Github`，需要先配置好`git`，然后右键之前创建的文件夹，选择`git bash here`，在命令行输入命令，按下三次回车生成一个**.ssh文件夹**，一般在用户的`user`根目录下，文件夹中包括名为`id_rsa`的私钥文件和一个名为`id_rsa.pub`的公钥文件
``` bash
 ssh-keygen -t rsa -C "注册邮箱地址"//按下三次回车，生成公钥和私钥两个文件
```

### **设置config文件**
找到`.ssh`文件夹后，在里面新建(修改)一个名为`config`的文件，不需要后缀名，然后在里面写入（不要忘记保存）：
```
Host github.com
HostName ssh.github.com  
User git
Port 443
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa
```

### **配置ssh免密登录**
将`id_rsa.pub`的公钥文件的所有内容复制，进入`github`右上角个人设置里找到配置`ssh`的选项，点击新建，将复制的公钥内容粘贴到`key`中，`title`里可以随意取个名字，点击`add ssh key`就配置成功了

### **新建远程仓库**
``` bash
git init//仓库初始化
git add README.md//添加readme.md文件
git commit -m "init"//提交
git branch -M main//构建分支
git remote add origin git@github.com:用户名/项目名.git//连接到远程仓库
git push -u origin main//推送
```

## **利用Github Pages发布网页**
### **配置workflows文件**
在项目的`.github`(没有则新建)文件夹中新建`workflows`文件夹。然后新建一个`PublishMySite.yml`文件，复制如下代码进去：
``` yml
name: publish site
# 触发条件
on:
  push:
    branches:
      - main
# workflow 的具体内容
jobs:
  deploy:
    # 创建一个 Ubuntu 容器
    runs-on: ubuntu-latest
    steps:
      # 先打开 main 分支
      - uses: actions/checkout@v2
      # 再安装 Python 和相关环境
      - uses: actions/setup-python@v2
        with:
          python-version: 3.x
      # 使用包管理工具 pip 安装 mkdocs-material
      - run: pip install mkdocs-material
      # 使用 mkdocs-material 构建网站并部署到 gh-pages 分支
      - run: mkdocs gh-deploy --force
```
该文件主要作用是在提交给`Github`修改过的代码文件后，让`Github-pages`同步更新个人网站并进行发布
### **更改仓库设置**
首先进入`GitHub`> `Repository` > `Settings` > `Actions` > `General` >

* Actions permissions: Allow all actions and reusable workflows
* Workflow permissions: Read and write permissions
* Click Save

然后进入`GitHub` > `Repository` > `Settings` > `Pages` > `Branch` > `gh-pages`(只修改第一项，后面可不改) > `Click Save`
### **修改提交**
以上设置好后，即可利用终端进行提交
``` bash
git add .   
git commit -m "Your commit message"(可随便命名，主要用于版本控制区分)
git push
```
更新完后访问网址链接即可
<!-- ## 例子
!!! example

    === "Unordered List"

        _Example_:

        ``` markdown
        * Sed sagittis eleifend rutrum
        * Donec vitae suscipit est
        * Nulla tempor lobortis orci
        ```

        _Result_:

        * Sed sagittis eleifend rutrum
        * Donec vitae suscipit est
        * Nulla tempor lobortis orci

    === "Ordered List"

        _Example_:

        ``` markdown
        1. Sed sagittis eleifend rutrum
        2. Donec vitae suscipit est
        3. Nulla tempor lobortis orci
        ```

        _Result_:

        1. Sed sagittis eleifend rutrum
        2. Donec vitae suscipit est
        3. Nulla tempor lobortis orci -->