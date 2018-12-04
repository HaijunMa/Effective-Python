# 了解 bytes、str与unicode的区别
---

- **Python3有两种表示字符序列的类型：bytes 和 str**
 
        bytes的实例包含原始的8位值，str的实例包含Unicode字符

- **python2有两种表示字符序列的类型：str 和 unicode**

        str的实例包含原始的8位值, unicode的实例包含Unicode字符

**编写Python程序的时候，一定要把编码（encode）和解码（decode）操作放在界面最外围来做**

----

- **在Python3中**

a.编写接受str或bytes，并总是返回str的方法：

      def to_str(bytes_or_str):
          if isinstance(bytes_or_str,bytes):
              value = bytes_or_str.decode("utf-8")
          else :
              value = bytes_or_str
          return value

b.编写接受str或bytes，并总是返回bytes的方法:

     def to_str(bytes_or_str):
         if isinstance(bytes_or_str,str):
            value = bytes_or_str.encode("utf-8")
         else :
            value = bytes_or_str
         return value

---
- **在Python2中**

a.编写接受str或unicode，并总是返回unicode的方法：

      def to_str(unicode_or_str):
         if isinstance(unicode_or_str,str):
            value = unicode_or_str.decode("utf-8")
         else :
            value = unicode_or_str
         return value

b.编写接受str或unicode，并总是返回str的方法：

      def to_str(unicode_or_str):
         if isinstance(unicode_or_str,unicode):
            value = unicode_or_str.encode("utf-8")
         else :
            value = unicode_or_str
         return value

---

### The first question

        在Python2里面，如果str只包含7位ASCII字符，那么unicode和str实例似乎
    就成了同一种类型。在Python3中，bytes和str实例绝不会等价，即使空字符也不行。

### The second question

        在Python3里面，通过内置的open函数获取了file handle，该file handle默认会
    采用UTF-8编码格式操作文件。而在Python2中，文件操作的默认编码格式则是二进制形式。


_从文件中读取二进制数据，或向其中写入二进制数据时，总应该以"rb"或"wb"等二进制模式开启文件_
