# **Linux系统命令行操作学习**

> Writed on 250212

> Author: Jack_hui

## **编写命令行程序**

### **切换终端工作路径**
```shell
# 显示当前终端工作路径
pwd
# 进入上一级文件夹
cd ..
# 在当前文件夹下创建CODE文件夹
mkdir CODE
# 切换
cd CODE
```

### **使用命令行程序的文本编辑器vim将代码写入文件SayHello.cpp**
按i进入编辑模式，可直接复制。然后按`exc`退出编辑模式，再按`:`输入编辑器的选项，并使用`wq`保存推出。
```shell
# 进入vim编辑器
vim SayHello.cpp
```
编译成可执行文件，可使用g++编译器
```shell
# -o后面跟输出的程序名
g++ SayHello.cpp -o "SayHello"
```
这里生成的程序必须使用相对路径或者绝对路径进行调用，因为没有添加到环境变量中。

## **常用的shell命令**
### **与工作路径相关**
```shell
pwd #显示当前工作路径
cd #切换当前路径
cd.. #返回上级路径
cd - #切换到上个路径

ls #显示当前路径下的所有文件
ls -a #包含隐藏文件
ls -l #查看指定文件详细信息
ls- al #包含隐藏文件且查看详细信息
```
### **与文件操作相关**
``` shell
rm # 直接删除指定文件
rm -d testDirectory #删除空文件夹
rm -rf testDirectory #强制删除文件夹

mv #移动文件 原地移动相当于重命名
cp #复制文件

find #查找文件
# 查找当前目录下所有的c++文件，并将这些文件复制到cpp-files里面，\为命令结束符
find . -name "*.cpp" -exec cp {} cpp-files \ #
```

### **与纯文本相关**
``` shell
# 相当于新建了一个文件
vim new.txt
# 新建文本文件
touch new.txt
#查看文件内容
cat <file> 
# 查看前10行
head <file>
```

### **与命令相关**
```
clear #清空当前终端界面
```