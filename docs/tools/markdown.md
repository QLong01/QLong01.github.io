# **Markdown学习笔记**

> Writed on 250202

> Author: Jack_hui

> 依照<https://thu-ios.github.io/tutorials/lecture/git.html>上的讲义，跟着打一遍很快能上手
## **具体语法**
### **标题**
`1`~`6`个`#`加一个空格再加上标题的名称

```
# 一级标题
## 二级标题
......
###### 六级标题 
```

### **加粗和斜体**
```
*This text will be italic* _This will also be italic_

**This text will be bold** __This will also be bold__

_You **can** combine them_
```

*This text will be italic* _This will also be italic_

**This text will be bold** __This will also be bold__

_You **can** combine them_

对于`_`和`*`，斜体用一对即可表示，而粗体需要用两对表示。

### **列表**
#### **Unordered无序列表**
```
* Item 1
* Item 2
    * Item 2a
    * Item 2b
```

* Item 1
* Item 2
    * Item 2a
    * Item 2b

#### **有序列表**
```
1. Item 1
1. Item 2
1. Item 3
   1. Item 3a
   1. Item 3b
```

1. Item 1
1. Item 2
1. Item 3
    1. Item 3a
    1. Item 3b

#### **任务列表**
```
- [x] this is a complete item
- [ ] this is an incomplete item
```

- [x] this is a complete item

- [ ] this is an incomplete item

这里注意:如果在`mkdocs`里对`md`文件添加任务列表，需要在`mkdocs.yml`添加如下依赖

``` yml
markdown_extensions:
  - def_list
  - pymdownx.tasklist:
      custom_checkbox: true
```

### **链接**
`[Text](url)`：中括号，后面小括号。小括号里面放链接，中括号里面必须放说明；不需要说明可直接写链接

```
[GitHub Official Site](https://github.com)

https://github.com
<https://github.com>
```
[GitHub Official Site](https://github.com)

https://github.com

<https://github.com>

注意，只写链接不加`<>`无法点击

### **图片**
`![Text](url)`:感叹号，中括号，小括号。小括号里面放图片链接，中括号里面放图片说明（不必须；写了的话会在图片下方或某处显示说明，当因为某种原因图片无法加载的时候，显示时也会用说明替代图片）

```
![GitHub Logo](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png)
```

![GitHub Logo](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png)

### **行内代码**
```
`行内代码`是行内代码
```

`行内代码`是行内代码

### **代码块**
用一对三个反撇```包裹，在最开始三个反撇后可以加代码的语言名称或简写以在渲染时获得高亮支持。

\```c++

int main(){
    
return 0;
    
}

\```


```c++
int main(){
    return 0;
}
```

注意：在mkdocs中还需要添加如下依赖
```yml
markdown_extensions:
  - pymdownx.highlight:
      anchor_linenums: true
  - pymdownx.inlinehilite
  - pymdownx.snippets
  - pymdownx.superfences
```

一般支持的代码高亮会有很多，比如：`shell`、`bash`、`c`、`cpp`、`java`、`objectivec`、`python`、`swift`、`yaml`、`html`、`xml`等

### **引用**
```
> 作者：...
> 日期：...
```

> 作者：...

> 日期：...

一般用来在开头注明时间作者等信息

### **表格**

```
First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column
```

| First Header | Second Header |
| ------------ | ------------- |
| Content from cell 1 | Content from cell 2 |
| Content in the first column | Content in the second column |

markdown不太注重排版，调格式需要自己写html相关静态页面代码
