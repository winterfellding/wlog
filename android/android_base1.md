2014/01/12
====================

###Hello World

创建一个andorid project，直接运行即可, activity_main.xml中已经画好了布局，调用了strings.xml中的HelloWorld string，显示出了一个hello world字符串的app

###本地化

在res/values文件夹下添加andorid xml file, 找到resources, 起名strings.xml next后选择Language, 在选择语言缩写，生成xml后把相应的entry改成翻译后的结果即可，测试的时候可以修改模拟器或者手机的语言设置，即可得到相应的文字。

###Export

在Manifest或者File->Export下找到export android application, 然后生成相应的keystore, 之后就可以导出apk包， 在安装的时候要在设置中把未知来源勾上，就可以安装不是Google market来源的apk包了。