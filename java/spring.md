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

###### Bean's scope

	bean entry has a property 'scope', the default value is singletone, when use this
	it'll always get the same instance of the bean, it has more values to use
	
	prototype		allow the bean to be initialize anytime
	request			define to HTTP request
	session			define to HTTP session
	global-session 	define to global session

##### Use the Spring auto wire

	Threse're 4 ways for spring autowire for the bean construction.

	1. byName when a bean has a property name, and you define the property class with an id which the id is
	   same as the name of the bean, you can use autowire="byName" to autowire the property, if multiple beans
	   use the autowire byName, they'll use the same property with bean that has an id named the same name of the
	   bean property.

	
	2.byType almost like byName, the difference is this autowire use the class type,
	  if the xml file has multiple bean has the type, Spring has two options to deal with this,
	  to identify a primary candidate, or elimate beans from autowiring candidacy. 

	  To identify a primary bean, we can config it with the primary attribute for the bean, the default value is true, 
	  so when we don't want this bean to be primary, we can just set the primary attribute to false.
	  To eliminate a bean from autowiring, we can set the autowire-candidate attribute to false.

	3.constructor if the bean is configured using constructor injection, we can put away the constructor-arg, we 
	  can let the spring autowire to construct it. The limit is the same as byType, this need to config which bean
      is the constructor-arg, furthermore, if one bean has multiple constructors, Spring can not guess which one to
      use.

	4.autodetect this will first use constructor, then use the byType.
	
    If you wan every bean use one type, you can define the default-autowire attribute on the beans element, the default value is none, at the same time, you can still define your own bean's autowire to overwirte the 
	default-autowire.


##### Annotation config

	1. define the config in the xml, use <context:annotation-config/> in the beans entry.
	@Autowired
	@Qualifier(preferred way)
	@Value(string expression) the string expression can also be el expression


