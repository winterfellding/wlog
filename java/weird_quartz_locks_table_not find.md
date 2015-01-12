### The weird table 'quartz_lock' not find

	I wrote a module using spring and quartz to do a repeatable schedule job today, the bean
	config file is like down below.

	<bean id="sampleJob" class="quartz.SampleJob"></bean>
    
    <bean id="sampleJobBean" 
        class="org.springframework.scheduling.quartz.MethodInvokingJobDetailFactoryBean">
        <property name="targetObject" ref="sampleJob"></property>        
        <property name="targetMethod" value="sampleJobMethod"></property>
    </bean>
    
    <bean id="sampleJobTrigger" class="org.springframework.scheduling.quartz.SimpleTriggerBean">
        <property name="jobDetail" ref="sampleJobBean"></property>
        <property name="repeatInterval" value="10000"></property>
        <property name="startDelay" value="3000"></property>
    </bean>
    
    <bean class="org.springframework.scheduling.quartz.SchedulerFactoryBean">
        <property name="jobDetails">
            <list>
                <ref bean="sampleJobBean"/>
            </list>
        </property>
        <property name="triggers">
            <list>
                <ref bean="sampleJobTrigger"/>
            </list>
        </property>
    </bean>

	And when I start server, an exception that MYSQL Syntax error occurs, it named table
	'dbname.quartz_locks' not found.

	Finally, I got the answer with google, it's because the SchedulerFactoryBean has a method
	named setDataSource, the data source autodetected by spring, so the server tried to find
	the datasource, it will get the error.

	Solution:
	add the autowired="no" to the ScheduleFactoryBean entry

	<bean class="org.springframework.scheduling.quartz.SchedulerFactoryBean" autowired="no">
	    <property name="jobDetails">
	        <list>
	            <ref bean="sampleJobBean"/>
	        </list>
	    </property>
	    <property name="triggers">
	        <list>
	            <ref bean="sampleJobTrigger"/>
	        </list>
	    </property>
	</bean>