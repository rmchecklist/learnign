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
<project default="sample_test_1"> --> Parent tag, it has mandatory attribute default which will be target name
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

