# 遵循PEP8风格指南
_&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;《Python Enhancement proposal #8》   （8号Python增强提案）_

|             TYPES               |                           VALUE                          |
|:-------------------------------:|:--------------------------------------------------------:|
|             PEP:                |                            8                             |
|             Title:              |                Style Guide for Python Code               |
|             Author:             |           Guido van Rossum (guido at python.org)         | 
|             Author:             |           Barry Warsaw (barry at python.org）            |
|             Author:             |           Nick Coghlan (ncoghlan at gmail.com)           |
|             Stats:              |                         Active                           |
|             Type:               |                         Process                          |
|             Greated:            |                       05-Jul-2001                        |
|           Post-History:         |                 05-Jul-2001, 01-Aug-2013                 |

----



- &emsp;它是针对Python代码格式编订的风格指南

- &emsp;尽管可以在保证语法正确的前提下随意编写代码，但是采用一致风格书写的代码更加易懂、易读

- &emsp;采用和其他程序员相同的风格来写代码，也更利于项目多人协作

- &emsp;即使代码只会由你自己读写，但是遵循这套风格也依然可以令后续的修改改变的容易一些

---


  **指南链接<https://www.python.org/dev/peps/pep-0008>**

**几条绝对应该遵守的规则：**
-

- **空白**

     使用space来表示缩进，而不要用tab

     和语法相关的每一层缩进都有4个空格来表示

     每行的字符数不应超过79

     对于占据多行的长表达式来说。除了首行之外的其余各行都应该在通常的缩进级别之上再加上4个空格

     文件中的函数与类之前应该用一个空行隔开

     在使用下标来获取列表元素、调用函数或是给关键字参数赋值的时候，不要在两旁添加空格

     为变量赋值的时候，赋值符号的左侧和右侧应该各写上一个空格，而且只写一个就好
--------------------
- **命名**

     函数、变量及属性应该用小写字母来拼写，各单词之间下划线相连
    
     受保护的实例属性，应该以单个下划线开头，eg : _first_name

     私有实例属性，应该以两个下划线开头, eg : __last_name

     类与异常，应该以每个单词首字母均大写的形式来拼写
    
     模块级别的常量，应该全部采用大写字母来拼写，各单词之间以下划线相连 

     类中的实例方法，应该把首个参数命名为self，以表示该对象自身

     类方法的首个参数，应该命名为cls,以表示该类自身
  
-------------

   _**“每件事都应该有直白的做法，而且最好只有一种”   ----《The Zen of Python》**_
     
--------
- **表达式和语句**
    
     采用内联形式的否定词，而不要把否定词放在整个表达式的前面，eg : 应该采用 if a is not b  
而不是if not a is b
    
     不要通过检测长度的方法 （if len(somelist) == 0)  来判断somelist是否为[]或''等空值，而是
采用 if not  somelist这种写法来判断，它会假定：空值将会自动评估为Faulse
    
     检测somelist是否为[1]或'hi'等非空值时，也应如此，if somelist 语句默认会把非空的值判断为True

     不要编写单行的if语句、for循环、while循环及except符合语句，而是把这些语句分成多行来书写

     import语句应该总是放在头文件开头

     引入模块的时候，总是应该使用绝对名称，而不应该根据当前模块的路径来使用相对名称

     如果一定要以相对名称来编写import语句，采用明确写法：from.import foo
    
     文件中的那些import语句应该按顺序划分成三个部分，分别表示标准模块、第三方模块以及自用模块。在每       一部分中，各import语句应该按照字母的顺序来排列








