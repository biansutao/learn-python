1. ## Python namedtuple 


namedtuple 能够用来创建类似于元祖的数据类型，除了能够用索引来访问数据，能够迭代，更能够方便的通过属性名来访问数据：

from collections import namedtuple

Animal = namedtuple('Animal', 'name age type')

big_yellow = Animal(name="big_yellow", age=3, type="dog")

big_yellow

Animal(name='big_yellow', age=3, type='dog')

big_yellow.name

'big_yellow'


2. ## deque

使用list存储数据时，按索引访问元素很快，但是插入和删除元素就很慢了，因为list是线性存储，数据量大的时候，插入和删除效率很低。

deque是为了高效实现插入和删除操作的双向列表，适合用于队列和栈：

from collections import deque

q = deque(['a', 'b', 'c'])

q.append('x')

q.appendleft('y')

q

deque(['y', 'a', 'b', 'c', 'x'])

deque除了实现list的append()和pop()外，还支持appendleft()和popleft()，这样就可以非常高效地往头部添加或删除元素。

