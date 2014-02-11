##### install 

	download the dmg pack file, install with the permission to install software not from app store.

##### run mysql server

	/usr/local/mysql/bin  sudo mysqld_safe to run server

##### connect to mysql server
	Make sure the mysqld is opened in ActivityViewer, use Sequel Pro to open the connect with socket and then connect, the standard way is also ok, the host is 127.0.0.1(don't use localhost).
	


##### something about shell
	
	e.g. I want to write an short cut for run goagent after intall and config it and I put it in /Applications/goagent,
	I can write these code in a file with .sh ending,
	
	cd /Applications/goagent/local
	python proxy.py
	
	After these code saved into the shell file, two steps
	1. in the terminal use chmod +x file.sh
	2. right click the file use open with -> Others Choose Terminal as the open application
	After that, we can just double click to open the goagent
	
	We can also write shell file to run mysql server. 
	