2014/01/12
===========================================

###1.有意义的命名(或者说带有目的性的命名)
	public List<int[]> getThem() {
		List<int[]> list1 = new ArrayList<int[]>();
		for (int[] x : theList)
			if (x[0] == 4)
				list1.add(x);
		return list1;
	}

例如此段，getThem them是什么东西，要指出来， list1是什么东西要指出来，x具体是什么东西， theList是什么东西，为什么要去取theList中每个元素的第一个元素，4又是代表的什么，所以可以修改成如下代码:

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