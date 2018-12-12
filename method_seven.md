# 用列表推导来取代map和filter

---
- Python提供了一种精炼的写法，可以根据一份列表来制作另一份。这种表达式称为_list comprehension_(列表推导)。

>

    #例如用列表中每个元素的平方构建另一份列表。 
    a = [1,2,3,4,5,6,7,8,9,10]
    squares = [x ** 2 for x in a]
    print(squares)
    
    >>>
    [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

- 除非是调用只有一个参数的函数，否则，对于简单的情况来说，列表推导要比内置的map函数更清晰。如果使用map函数，那就要创建lambda函数，以便计算新列表中各个元素的值，这会使代码看起来有些乱。
>

    squares = list(map(lambda x:x ** 2,a))
    print(squares)

    >>>
    [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

---
- 列表推导则不像map那么复杂，他可以直接过滤原列表中的元素，使得生成的新列表不会包含对应的计算结果。例如在计算平放值时，我们只想计算那些可以为2 所整除的数。如果采用列表推导来做，那么只需在循环后面添加条件表达式即可：
>

    squares = [x ** 2 for x in a if x % 2 ==0]
    print(squares)

    >>>
    [4, 16, 36, 64, 100]

- 把内置的filter函数和map函数结合起来，也能达到同样的效果，但是代码会写的非常难懂。
>

    a = [1,2,3,4,5,6,7,8,9,10]
    alt = list(map(lambda x:x ** 2,filter(lambda x: x % 2 == 0,a)))
    print(alt)

    >>>
    [4, 16, 36, 64, 100]

---

- 字典(dict)和集合(set)也有和列表类似的推导机制。编写算法时可以通过这些推导机制来创建衍生的数据结构。
>

    chile_ranks = {'ghost':'A','habanero':'B','cayenne':'C'}
    rank_dict = {rank: name for name,rank in chile_ranks.items()}
    chile_len_set = {len(name) for name in rank_dict.values()}
    print(rank_dict)
    print(chile_len_set)

    >>>
    {'A': 'ghost', 'B': 'habanero', 'C': 'cayenne'}
    {8, 5, 7}