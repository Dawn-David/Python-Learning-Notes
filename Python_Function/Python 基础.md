# list列表和tuple元组
## list
Python内置的一种数据类型是列表：list。list是一种有序的集合，可以随时添加和删除其中的元素。
比如，列出班里所有同学的名字，就可以用一个list表示：
>>> classmates = ['Michael', 'Bob', 'Tracy']
>>> classmates
['Michael', 'Bob', 'Tracy']

## tuple
另一种有序列表叫元组：tuple。tuple和list非常类似，但是tuple一旦初始化就不能修改，比如同样是列出同学的名字：
>>> classmates = ('Michael', 'Bob', 'Tracy')

只有1个元素的tuple定义时必须加一个逗号,，来消除歧义：
>>> t = (1,)
>>> t
(1,)
Python在显示只有1个元素的tuple时，也会加一个逗号,，以免你误解成数学计算意义上的括号。

最后来看一个“可变的”tuple：
>>> t = ('a', 'b', ['A', 'B'])
>>> t[2][0] = 'X'
>>> t[2][1] = 'Y'
>>> t
('a', 'b', ['X', 'Y'])
这个tuple定义的时候有3个元素，分别是'a'，'b'和一个list。

