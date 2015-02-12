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

### Computing

	A = [1 2; 3 4; 5 6]
	B = [2 4; 5 6]
	A * B % 矩阵相乘
	A .* 2 % 相当于每个元素乘以2
	a = [1;2;15;0.5]	
	floor(a) %舍去小数
	ceil(a) %进一位
	A = magic(3)
	max(A, [], 1) %获取每一列最大的
	max(A, [], 2) %获取每一行最大的
	max(max(A)) %获取矩阵最大数
	max(A[:])	%先把矩阵转换成vector 获取矩阵最大数

### Plotting

	t = [0:0.01:0.98];
	y1 = sin(2*pi*4*t);
	y2 = cos(2*pi*4*t);
	plot(t,y1);	 	% plot the sin function
	hold on;		% don't replace with new function
	plot(t,y2,'r');	% plot the cos function with red color
	xlabel('time')
	ylabel('value')
	legend('sin', 'cos') %注释函数线
	title('my plot')
	print -dpng 'myPlot.png' % save as file
	close
	figure(1); plot(t, y1);
	figure(2); plot(t, y2); % plot two figure
	subplot(1, 2, 1);
	plot(t, y1);
	subplot(1, 2, 2);
	plot(t, y2);		% plot two functions in one figure
	clf;
	A = magic(5);
	imagesc(A), colorbar, colormap gray;

### Control statement

	if / for / while
	if x == 1,
		disp(1);
	end;
	
	for i = 0:0.01:0.98,
		disp(i);
	end;
	
	i = 1;
	while i <= 5,
		disp(i);
	end;

	addpath('path'); % add the path to use in different directory