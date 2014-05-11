### 数据类型

python的dict类型写起来有点太啰唆了。
可以如下定义，使得使用变得方便一点：
```python
class edict(dict):
	def __getattribute__(self, x):
		return self[x]
```
访问起来就方便一点了：
```python
a = edict{'name' = 'xx', 'age' = 26'}
print a.name
```


### 面向对象

我不懂面向对象。但是有些人说面向对象很好；有些人说面向对象让事情变得不必要的复杂 -- 不管是褒是贬，反正是有很多人在讨论这个东西。   
所以，我打算搞懂他们究竟在说些什么。

对象有方法、字段。
python中，对象的操作有两种：

* 创建对象
* 访问对象的字段/方法

字段是在对 对象的域当赋值时创建。
方法，其实是类方法。

```python
class A:
	n = 10	# 0
	def __init__(self, id):
		self.id = id
		A.n = A.n + 1
	def show(self):
		print self.id
	def count(self):
		print A.n

a = A('a')
a.count()	# => 11
b = A('b')	# => 12
```

注意，**在类定义中，访问字段以及方法的时候，必须要使用`obj.field`, `obj.method`的形式去访问**
