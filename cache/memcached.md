### 安装

	在Linux使用包管理器安装`sudo apt-get install memcached`, 装完后memcached跑在localhost
	的11211端口，如果要在其他机子上访问memcached，使用`service memcached stop`后，
	`memcached -d -m 1024 -p 11211 -l 192.168.0.110`， l后的不能写成localhost/127.0.0.1
	/0.0.0.0，否则会导致远端连接不上

### 连接

	使用`telnet host port`连接进去之后就可以使用memcached了。

### 命令

	set key flags exptime bytes [noreply] 
	
	例子:
	set hello 0 900 5
	world
	hello是存储的key，900是存储900s，5是对应的value的长度，也就是world的长度
	再次对该key进行set的话会使原来的数据被覆盖掉，如果想要不被覆盖的话，使用add命令
	用法与set语法类似。


	get key

	get hello就可以获得之前存储的world

	
	incr key increment_value
	该命令可以增加key的值
	例子：
	set i 0 900 2
	10
	incr i 5
	get i 这时候的i是15 (10 + 5)
	decr i 10
	get i 这时候的i是5 (15 - 10)
