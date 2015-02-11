### Install

`curl -LsSf http://github.com/mxcl/homebrew/tarball/master | sudo tar xvz -C/usr/local --strip 1`

### Use brew
	// install 
	sudo brew install wget
	// uninstall
	sudo brew uninstall wget
	// search
	sudo brew search /regex/

### jenv

	jenv是OSX管理java版本的一个工具

	通过brew安装:brew install https://raw.github.com/gcuisinier/jenv/homebrew/jenv.rb
	使用jenv local [version]调整java的版本
	通过jenv gloabl [version]设置默认值