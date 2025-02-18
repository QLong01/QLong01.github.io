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
``` shell
clear #清空当前终端界面
history #查看历史命令

man # 查看命令的使用方法
```

### **与进程相关**
```shell
ps #查看当前所有进程
kill #向进程发送某些信号，比如终止信号等
```

## **其他shell操作**
### **which where**
``` shell
which #查看shell如何解析输入
where #查看shell解析输入的所有情况，第一条为which的结果
```

### **输入输出流重定向**
``` shell
touch my.txt
echo "hello world" > my.txt #原文件为空，相当于直接追加
echo "123" > my.txt #将原有内容覆盖
echo "456" >> my.txt #将输出追加到文件

mkdir ha/haha 2> /dev/null #忽略错误
mkdir ha/haha 2>> error.log #追加错误到日志文件中
```

* 重定向符号
    * `>`: 输出到给定路径处的文件，并覆盖原有内容
    * `>!`: 强制覆盖 
    * `>>`: 不覆盖，进行追加
    * `<`: 接收输入，并给到指定路径上的程序
    * 注: 对于输出到`/dev/null`的情况，通常用来存储不需要输出的信息

* 输入和输出主要有三种:
    1. 标准输入: 用`0`表示，即`stdin`，使用方式为`<` 
    1. 标准输出: 用`1`表示，即`stdout`，使用方式为`1>` 
    1. 错误输出: 用`2`表示，即`stderr`，使用方式为`2>` 

### **管道**
`|` 上一个命令的输出作为下一个命令的输入，应用例子如下:
```shell
# 想查找之前创建了哪些文件，使用history一条条查看
history
# 直接使用grep搜素命令，更快捷
history | grep "mkdir"
```

### **grep**
通常搭配正则表达式进行使用
``` shell
# 在错误日志里查找数字0-9
grep "[0-9]" error.log
```

### **Ctrl+C**
结束当前正在执行的程序；命令输到一半也用它来重吸输

### **Ctrl+D**
退出一个shell(终端)



