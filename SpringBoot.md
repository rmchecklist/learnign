Creating a dependency using BeanFactory

```
BeanFactory factory = new XmlBeanFactory(new FileSystemResource("spring.xml"));

Alien obj = factory.getBean("alien")
```
New class bean information should be declated in spring.xml file

```
<bean name="alien" class"Alien"></bean>
```

Alternatively we can use ApplicationContext

```
ApplicationContext factory = new ClassPathXmlApplicationContext("spring.xml")
Alien obj = fatory.getBean("alien")
```
Since we are using ClassPathXmlApplicationContext read the xml file, we should place the file under class path

Defaultly spring container objects are declared as singleton, even if you create mutiple object, all objects are refered to single object.

# Singleton
```
ApplicationContext factory = new ClassPathXmlApplicationContext("spring.xml")
Alien obj = fatory.getBean("alien")
Alien obj1 = fatory.getBean("alien")

```

obj1 and obj2 are refered to same object instance.

# Prototype 
When you need different object then needs to udpate the bean xml file scope to prototype.

- Singleton object will be created automatically
- Prototype, created on request

Assigning a value though sping xml

```
<bean id="alien" class="Alien">
  <property name="age" value="20"></property>
</bean>
```

```
<bean name="alien" class"Alien" type="prototype"></bean>
```

