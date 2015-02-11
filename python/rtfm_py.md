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