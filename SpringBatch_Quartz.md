# Spring batch quartz integration [https://www.jackrutorial.com/2018/03/quartz-scheduler-annotation-with-spring-batch-in-spring-boot-tutorial.html]

1. Add maven dependencies

```
<dependency>
 <groupId>org.quartz-scheduler</groupId>
 <artifactId>quartz</artifactId>
 <version>2.2.3</version>
</dependency>

<dependency>
 <groupId>org.springframework</groupId>
 <artifactId>spring-context-support</artifactId>
 <version>4.3.0.RELEASE</version>
</dependency>
```

2. Configure Spring batch quartz

2.1 Create job launcher extends QuartzJobBean
    
    - jobName
    - JobLauncher
    - jobLocator
    
    overide executeInternal
    
  2.2 Configure QuartzConfig
    - declare jobRegistryBeanPostProcess
        - Set jobregistry
    - JobDetailFactoryBean
        Add job , joblauncher and joblocator into jobdetailfactorybean
        
  2.3 cronTriggerFactoryBean
  
  2.4 scheduleFactoryBean
    
  
