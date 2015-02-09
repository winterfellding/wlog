
#### Hello Gradle

	先准备好项目的层次
	gradle/
	└── src
    └── main
        └── hello
            └── HelloGradle.java
            
    HelloGradle.java中可以写一个main方法用来运行
    
    在gradle目录下建一个文件叫build.gradle
    
    apply plugin: "java"

	sourceSets {
		main.java.srcDir "src/main" // main source directory
		test.java.srcDir "src/test" // test source directory
	}

	jar {
		manifest.attributes "Main-Class": "hello.HelloGradle" // set main class for jar step
	}
	
	运行gradle tasks可以看到当前可以运行的一些任务，运行gradle build就可以build了
	
	build完后就可以使用java -jar build/libs/gradle.jar来运行build完的project了
	
