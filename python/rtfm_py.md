### global variable

	想要使用全局变量，先要在前面使用global关键词
	
	i = 0
	def set_i_to_one():
		global i
		i = 1
	def print_i():
		print i

	set_i_to_one()
	print_i()		# 1

### function object

	>>> def f():
	pass

	>>> print f() # null return function return None
	None
	>>> def f():
	return 'hhh'

	>>> print f()
	hhh
	
	# init only once.
	def f(a, L=[]):
		L.append(a)
		return L
	print f(1)		# [1]
	print f(2)		# [1, 2]
	print f(3)		# [1, 2, 3]

	# initialize L as empty list each time.
	def f(a, L=None):
		if L is None:
			L = []
		L.append(a)
		return L
	print f(1)		# [1]
	print f(2)		# [2]	
	print f(3)		# [3]
	
### list
	
	# list as stack
	stack = []
	stack.append(1)
	stack.append(2)	# push element to stack
	stack.pop()
	stack.pop()		# pop element

	# list as queue
	from collections import deque
	queue = deque([1, 2, 3])
	queue.append(5)
	queue.append(6)		# append to the last
	queue.popleft()		
	queue.popleft()		# pop the most left element

### Functional Programming Tools

	filter
	def f(x): return x % 3 == 0 or x % 5 == 0
	filter(f, range(2, 25)) # return all number which mod 3/5 is 0

	def f(x): return x ** 3
	map(f, range(10)) # return all element's cube
	
	map can pass more than one parameter

	reduce
	def add(x, y): return x + y
	reduce(add, range(1, 10)), pass the first two element to function, and continue until return one result
	
### Input and Output	

	# 打开一个文件
	f = open('file.txt', 'r')
	# 按行读取
	f.readline() #再次执行读取下一行
	f.read()	 #一次性读完所有内容
	
	# 获取一个文件并且有写入权限
	f = open('file.txt', 'w') # 若使用a权限则是加在原文后面
	f.write('0123456')
	
### Error and Exception

	基本上和java的类似，语法结构如下：
	try:
		xxx
	except XXXError:
		xxx
		
	当要抛出一个Error或者Exception的时候，使用raise
	
	raise ZerorDivisionError
	
### Class(Object Oriented)
	
	定义一个类使用class关键字，结构如下
	
	class ClassName:
		<statements>
		
	class MyClass:
		i = 1
		def f(self):
			print "hello"
			
	这里的i是公有变量,可以MyClass.i或者x = MyClass() x.i获取
	在调用方法时，一定要有一个对象，如x.f()，其等同于MyClass.f(x)
	
	
	
	如果要把变量变为对象私有，把属性放入__init__方法中，例子如下
	
	class MyClass:
		def __init__(self, i):
			self.i  = i
			
	如此利用init方法构造两个对象
	x = MyClass(1)
	y = MyClass(2)
	x和y的i属性是不同的
	
	
	继承
	class MyClass(FartherClass):
		pass
		
	把父类放入括号中即可，也支持多继承，找属性或者方法时，是从左到右找的
	
	