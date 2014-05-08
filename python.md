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
