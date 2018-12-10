# 用辅助函数来取代复杂的表达式


- **Python的语法非常精简，可以用一行表达式来实现许多逻辑**

   _eg:从URL中解码查询字符串_

      #每个参数都可以表示一个整数值
      from urllib.parse import parse_qs
      my_values = parse_qs('red=5&blue=0&green=',keep_blank_values=True)
      print(repr(my_values))

      >>>
      {'red':['5'],'blue':['0'],'green':['']

 ---  
- **用get方法在my_values字典中查询不同的参数时就有可能获得不同的返回值**  
>

    print('Red:',my_values.get('red'))
    print('Blue:',my_values.get('blue'))
    print('Opactiy:',my_values.get('opactiy'))

    >>>
     Red: ['5']
     Blue: ['0']
     Opactiy: None

---
- **如果待查询的参数没有出现在字符串中，或是当该参数的值为空白时能够返回默认值0，那就更好了。  
   这个逻辑看上去似乎并不值得用完整的if语句或辅助函数来实现，于是你就可能考虑用Boolean表达式**  
>

    # For query string 'red=5&blue=0&green='
    red = my_values.get('red',[''])[0] or 0
    blue = my_values.get('blue',[''])[0] or 0
    opaccity = my_values.get('opacityt',[''])[0] or 0

    print('Red: %r'  % red)
    print('Blue: %r' % blue)
    print('Opacity: %r' % opaccity)

    >>>
    Red: '5'
    Blue: 0
    Opacity: 0

---
- **上面的长表达式虽然语法正确，阅读起来却很困难，有时也未必完全符合要求。这样的代码不容易理解，  
 初次拿到这种代码的人，可能先要下些功夫把表达式拆开，然后才能看明白它的作用。Python2.5 添加了  
if/else条件表达式（三元操作符），可以把上述逻辑写的更清楚一点，还能保持代码整洁。**

>

    red = my_values.get('red',['']) 
    if red[0]:
        red = int(red[0])
    else :
        red =0

- **现在需要把它总结成辅助函数了，如果是频繁操作那就更需要了**
>

    def get_first_int(values,key,default=0):
    found = values.get(key,[''])
    if found[0]:
        found = int(found[0])
    else:
        found =0
    return found

- **调用辅助函数所使用的的代码，比使用or操作符长表达式版本和用if/else表达式两行版本更加清晰整洁**
>

    red = get_first_int(my_values,'red')

---

# **Note:**
### _表达式如果变的比较复杂，那就应该考虑将其拆解成小块，并把这些逻辑移入辅助函数中。_  
### _这会让代码更加易读、整洁 。编写Python程序时，不要一味追求过于紧凑的写法，那样会_
### _写出非常辅助的表达式。_


---

# Blessing:

### _I believe that you will stick to it. Come on!_ 