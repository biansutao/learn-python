# Python 处理Json数据

#需要导入json模块

import json


## 1. 将python对象转换为字符串

json.dumps ：将 Python 对象编码成 JSON 字符串

json.dump

## 2.将Json字符串转化为Python对象

json.loads： 将已编码的 JSON 字符串解码为 Python 对象

json.load

 ```
实例
以下实例将数组编码为 JSON 格式数据：
#!/usr/bin/python
import json

data = [ { 'a' : 1, 'b' : 2, 'c' : 3, 'd' : 4, 'e' : 5 } ]

json = json.dumps(data)
print json
以上代码执行结果为：
[{"a": 1, "c": 3, "b": 2, "e": 5, "d": 4}]
使用参数让 JSON 数据格式化输出：
>>> import json
>>> print json.dumps({'a': 'Runoob', 'b': 7}, sort_keys=True, indent=4, separators=(',', ': '))
{
    "a": "Runoob",
    "b": 7
}
python 原始类型向 json 类型的转化对照表：
Python	JSON
dict	object
list, tuple	array
str, unicode	string
int, long, float	number
True	true
False	false
None	null
 ```
