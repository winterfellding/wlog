###### add directory into PATH

	export PATH=dir:$PATH

##### shutdown computer on xxx time

	sudo shutdown -h yyMMddhhmm
	
##### envirment variables

	winterfalldeMacBook-Pro:~ winterfall$ echo $HOME
	/Users/winterfall
	winterfalldeMacBook-Pro:~ winterfall$ echo $LANG
	zh_CN.UTF-8
	winterfalldeMacBook-Pro:~ winterfall$ echo $PATH
	/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin
	
##### ls pwd

	# list file
	winterfalldeMacBook-Pro:~ winterfall$ ls -l  
	total 0
	drwx------   3 winterfall  staff   102  2 14 00:16 Applications
	drwx------+ 15 winterfall  staff   510  2 14 00:02 Desktop
	drwx------+ 14 winterfall  staff   476  2 14 00:06 Documents
	drwx------+ 29 winterfall  staff   986  2 14 00:30 Downloads
	drwx------@ 49 winterfall  staff  1666  2 11 22:18 Library
	drwx------+  3 winterfall  staff   102  2  8 11:19 Movies
	drwx------+  6 winterfall  staff   204  2  9 00:55 Music
	drwx------+  7 winterfall  staff   238  2 10 23:02 Pictures
	drwxr-xr-x+  5 winterfall  staff   170  2  8 11:19 Public
	winterfalldeMacBook-Pro:~ winterfall$ ls -a
	.			.emacs.d		Downloads
	..			.gitconfig		Library
	.CFUserTextEncoding	.m2			Movies
	.DS_Store		.ssh			Music
	.Trash			.viminfo		Pictures
	.appcfg_cookies		Applications		Public
	.bash_history		Desktop
	.distlib		Documents
	
	# show current directory
	winterfalldeMacBook-Pro:~ winterfall$ pwd
	/Users/winterfall
