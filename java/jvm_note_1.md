### build openjdk
从[openjdk](http://download.java.net/openjdk/jdk7/)下载好源代码包后，安装好依赖的jdk，ant等依赖项，找到`$(openjdk_home)/hotspot/make/linux/Makefile`中的所有test_gamma行删掉，找到`$(openjdk_home)/jdk/src/share/classes/java/util/CurrencyData.properties
`中的超过10年的数据改成10年内，搜一下20就都出来了。
接着export LANG=c; export ALT_BOOTDIR=依赖jdk地址; unset JAVA_HOME; unset CLASSPATH;
然后在$(openjdk_home)下执行make就开始build了。