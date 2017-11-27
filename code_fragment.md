Python namedtuple 


namedtuple 能够用来创建类似于元祖的数据类型，除了能够用索引来访问数据，能够迭代，更能够方便的通过属性名来访问数据：

>>> from collections import namedtuple

>>> Animal = namedtuple('Animal', 'name age type')

>>> big_yellow = Animal(name="big_yellow", age=3, type="dog")

>>> big_yellow

Animal(name='big_yellow', age=3, type='dog')

>>> big_yellow.name

'big_yellow'
