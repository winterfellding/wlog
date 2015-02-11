#### Basics

	在octave命令行中也可以使用*nix工具,例如ls pwd等	
	A = ones(10, 10) % 生成10*10矩阵，元素都为1
	A = zeros(10, 10) % 生成10*10矩阵，元素都为0
	A = rand(10, 1) % 生成10维vector，元素都为0～1之间的随机数
	A = randn(10, 1) % 生成10维vector, 元素都为高斯分布随机数
	A = eye(10) %生成10阶单位矩阵
	disp(A) %显示A
	a = pi
	disp(sprintf('2 decimals: %0.2f', a)) %类似于c的占位符打印
	format short/long %小数长度
	A = [1 2; 3 4; 5 6] % 3*2矩阵
	hist(A) %生成图像	
	whos % 查看当前的所有数据
	clear % 清空数据
	load xx.dat %载入数据
	save xx.dat matrix %保存数据
	size(A, 1) % 矩阵的行, 2的话是列
	length(A) % 矩阵行或者列中大的那个

