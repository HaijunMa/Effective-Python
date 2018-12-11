# 在单次切片操作内，不要同时指定start、end和stride
---

- 除了基本的切片操作，Python还提供了somelist[start\:end\:stride]形式的写法，以实现步进式切割，也就是从每n个元素里取出一个。
>

    #指定步进值(stride),把列表的奇偶数分开
    a = [1,2,3,4,5,6,7,8,9,10]
    odds = a[::2]
    evens = a[1::2]
    print(odds)
    print(evens)

    >>>
    [1, 3, 5, 7, 9]
    [2, 4, 6, 8, 10]

---
 - 采用stride方式进行切片时，经常会出现不符合预期的结果
 
   >>例如Python中有一种常见的技巧，能够把字节形式存储的字符串反转过来，这个技巧就是采用-1做步进值

    a = b'I love Python!'
    b = a[::-1]
    print(b)

    >>>
    b'!nohtyP evol I'

>>这种技巧字节串和ASCII字符有用，但是对已经编码成UTF-8的字节串的Unicode字符来说，则无法奏效。

    m = "军军"
    x = m.encode('utf-8')
    y = m[::-1]
    z = n.decode('utf-8')
    
    >>>
     AttributeError: 'str' object has no attribute 'decode'

---

- 我们不应该把stride与start和end写在一起，如果非要用stride，就尽量采用正值，同时省略start和end索引。
如果一定要配合start和end索引使用stride，那么就考虑先进行步进式切片，把切割的结果赋值给某个变量，然后在那个变量上进行第二次切割。
>

    b = a[::2]
    c = b[1:-1]

- 上面这种先做步进式切割，再做范围切割的办法，会产生一份原数据的浅拷贝。执行第一次切割操作时，应该尽量缩减切割后的列表尺寸。如果你所开发的程序对执行时间或内存用量要求非常严格，以致不能采用两阶段切割法，那就请考虑Python内置的itertools模块。该模块中有个islice方法，这个方法不允许为start、end和stride指定负值。

