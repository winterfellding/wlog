###1.有意义的命名(或者说带有目的性的命名)
	public List<int[]> getThem() {
		List<int[]> list1 = new ArrayList<int[]>();
		for (int[] x : theList)
			if (x[0] == 4)
				list1.add(x);
		return list1;
	}

例如此段，getThem them是什么东西，要指出来， list1是什么东西要指出来，x具体是什么东西，
theList是什么东西，为什么要去取theList中每个元素的第一个元素，4又是代表的什么，所以可以修改成如下代码:

	public List<int[]> getFlaggedCells() {
		List<int[]> flaggedCells = new ArrayList<int[]>();
		for (int[] cell : gameBoard)
			if (cell[STATUS_VALUE] == FLAGGED)
				flaggedCells.add(cell);
		return flaggedCells;
	}

更进一步，cell[STATUS_VALUE] == FLAGGED可以提取为方法，可以修改如下：

	public List<int[]> getFlaggedCells() {
		List<int[]> flaggedCells = new ArrayList<int[]>();
		for (int[] cell : gameBoard)
			if (cell.isFlagged())
				flaggedCells.add(cell);
		return flaggedCells;
	}

##### class names

	class的名字应该是一个名词，并且要尽量避免Manager, Processor, Data, Info这些太大概念的名词

##### method names
	
	方法名应该是一个动词，表明做什么，并且要避免get set is前缀，因为javabean标准。

	当一个类的构造器被重载，使用静态工厂类并利用parameter的名字来命名一个方法名要比直接new好，为了强制使用这个方
	法，应把构造器写成private的。
	Complex fulcrumPoint = Complex.fromRealNumber(23.0);
	就要比
	Complex fulcrumPoint = new Complex(23.0);
	来得好  

##### 不要使用俏皮的名字

	使用俏皮的名字只有你自己活着懂得这种幽默的人能懂，其他人就看不懂了

##### 对于一个概念使用同一名词

	为了防止混淆，对一个概念使用同一名字以免造成混淆，例如: controller 以及manager， provider这些词。

##### 不要使用双关语

	同理，也会造成混淆，例如一个add方法，到底是insert进入一张表，还是append在List后呢，这会造成混淆，直接使用更清
	楚概念，如果是插入数据库，直接使用insertXXX， 如果是添加在List后，就使用appendXXX。

##### 使用专业领域词语

	例如一个类叫做AccountVisitor，很明显这就是一个使用了Visitor模式的类, 而一个JobQueue也很明显是一个队列。

##### 使用针对问题的名字

	当没用专业词语使用时，搞清楚问题到底是干什么的，然后以之进行命名。

##### 加上有意义的名词前缀

	例如看到firstName, lastName, idNo很明显是一个人，但如果只看到firstName的时候，可能会理解成地址名或者其他名字
	，加上有意义的名字前缀，例如personFirstName, personLastName, personIdNo。
	