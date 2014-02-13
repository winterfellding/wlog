###### Dependency Injection

	Spring use the constructor to inject data into object, and use xml config 
	file to construct java object, we can get these object from ApplicationContext 
	container.

	Dependency Injection can make code loosely coupled, which can make code more 
	reuseable and more easy to do unit test.

###### Bean

	With the example in Spring in Action(3rd version), when the bean.xml construct
	object with no constructor-arg element, the bean get the default value 3, and 
	after adding constructor-arg element into the bean entry, it become the value 
	which the constructor-arg give, in fact, it use the constructor with the int 
	argument instead of the default constructor with no parameters.

	We can comment the default construtor with no parameters, and use the bean
	without the constructor-arg element, it'll throw exception
	Caused by: java.lang.NoSuchMethodException: com.springinaction.springidol.Juggler.<init>(),
	that means the xml is the config file for creating bean through constructor.