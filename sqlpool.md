数据库连接池

1. 安装DBUtils插件
pip install DBUtils 
2.使用连接池的方法

import MySQLdb
from DBUtils.PooledDB import PooledDB
pool = PooledDB(MySQLdb,5,host='localhost',user='root',passwd='pwd',db='myDB',port=3306) #5为连接池里的最少连接数

 
conn = pool.connection()  #以后每次需要数据库连接就是用connection（）函数获取连接就好了
cur=conn.cursor()
SQL="select * from table1"
r=cur.execute(SQL)
r=cur.fetchall()
cur.close()
conn.close()

3.PooledDB的参数
1. mincached，最少的空闲连接数，如果空闲连接数小于这个数，pool会创建一个新的连接
2. maxcached，最大的空闲连接数，如果空闲连接数大于这个数，pool会关闭空闲连接
3. maxconnections，最大的连接数，
4. blocking，当连接数达到最大的连接数时，在请求连接的时候，如果这个值是True，请求连接的程序会一直等待，直到当前连接数小于最大连接数，如果这个值是False，会报错，
5. maxshared 当连接数达到这个数，新请求的连接会分享已经分配出去的连接

在uwsgi中，每个http请求都会分发给一个进程，连接池中配置的连接数都是一个进程为单位的（即上面的最大连接数，都是在一个进程中的连接数），而如果业务中，一个http请求中需要的sql连接数不是很多的话（其实大多数都只需要创建一个连接），配置的连接数配置都不需要太大。
连接池对性能的提升表现在：
1.在程序创建连接的时候，可以从一个空闲的连接中获取，不需要重新初始化连接，提升获取连接的速度
2.关闭连接的时候，把连接放回连接池，而不是真正的关闭，所以可以减少频繁地打开和关闭连接

