# Ant(Another Neat Tool)


##### Setting up the environment

 - Automate the below action
    - Copy all the files except java files to "build/classes"
    - Compile .java files in "src" directory and copy .class files in "build/classes"
    - packeage all the content in "build/classes" and "webcontent" as a war file
    - deploy the war file into "webapps" directory of tomcat
    - cleanup "build/classes"  

1. Install Ant
    - download the file and extract to local path
    -  Set environmental variable - ANT_HOME and path
    -  It needs an java setup, make sure java environment variables are set correctly
        - JAVA_HOME, JDK_HOME, JRE_HOME 
2. Check the ant version by typing ant -version

```
Apache Ant(TM) version 1.10.9 compiled on September 27 2020
```

##### Hello world with ANT

- Write a message and create a directory

```
<?xml version="1.0" encoding="UTF-8" ?>  --> XML declaration
<project default="sample_test_1"> --> Root tag, it has mandatory attribute default which will be target name, we should mention atleast one target
	<target name="sample_test_1"> --> target where all task should be placed
		<echo message="Test message" /> --> Task#1 Print message on the console
		<mkdir dir="new_dir" /> --> Task#2 create new directory
	</target>
</project>
```
- Run the ant file 
  - go to dir where we create a xml file
  - run the ant script by ant -buildfile ant_script.xml 
  - ant expect build.xml if our file name is build.xml then we can skip the "-buildfile file_name", simply ant will execute the build.xml file


##### Project tasks and tags

- project	

```
<project default="" basedir="." name="">

default - name of the target 
name - this is the project name can be used for creating war or other file
basedir - this is current dir, it can be any dir
```

Execute the task in order

```
<?xml version="1.0" encoding="UTF-8" ?>
<project default="task#2">
	<target name="task#1">
		<echo message="Hello" />
	</target>
	
	<target name="task#2" depends="task#1">
		<echo message="World!" />
	</target>
</project>
```
1. Ant script look for project default target name, here task#2, it executes task#2
2. Task#2 depends on task#1, so it executes task#1 and then task#2

```
task#1:
     [echo] Hello

task#2:
     [echo] World!
```

##### Dealing with properties

```
<?xml version="1.0" encoding="UTF-8" ?>
<project default="test"> --> default target name
	<property file="build.properties" /> --> Read property from external file
	<property name="name" value="Madhav" /> --> User defind property
	<target name="test"> --> target
		<echo message="User defined properties: ${name}" /> --> it look for the name from property tag	
		<echo message="Read from external property file: ${sitename}" /> --> Read property from external property file
		<echo message="System properties: ${java.vm.vendor}" /> --> System properties 	
		<echo message="Buildin properties: ${ant.home}" />  --> Buildin properties	
		
		<fileset id="xmlfiles" dir="." includes="*.xml" /> --> Fileset tag it reads all xml files from current directory
		<echo message="toString of fileset: ${toString:xmlfiles}" /> --> Print the xml files using toString:	
	</target>
</project>
```

###### Path like structures

- call property file from external file

