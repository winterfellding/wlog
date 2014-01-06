2014/01/06
==============================

###异步单线程

通过回调函数来实现在数据库，文件io等一些时间操作较长的操作的时候，直接执行后面的程序，而不会阻塞。

###包引入

通过require关键字引入包，然后调用其方法。

node的一些命令，

node -v version
	 -e eval
	 -i interpreter

###Http hello world
	
	var http = require('http');
	http.createServer(function(req, res) {
		res.writeHead(200, {'Content-Type': 'text/html'});
		res.write('<p>Hello, World</p>')
		res.end('<p>Node</p>');
	}).listen(3000);

######supervisor
通过npm可以装supervisor以达到修改代码无需重启服务器刷新即可得到新代码的结果。

###异步和同步
	// read file async
	var fs = require('fs');
	fs.readFile('file.txt', 'utf-8', function(err, data) {
		if (err) {
			console.log(err);
		} else {
			console.log(data);
		}
	});
	console.log('end.');
执行后会显示end在文件内容之前，因为是异步，在读取文件内容没完成之前，直接执行了后面的语句。

	// read file sync
	var fs = require('fs');
	var data = fs.readFileSync('file.txt', 'utf-8');
	console.log(data);
	console.log('end.');
执行完就是end在文件内容之后，调用的同步读取文件api。