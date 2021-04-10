# Ant - Another Neat tool

Source: https://www.tutorialspoint.com/ant/ant_environment.htm


- Why we need build tool?
  - Compiling the code
  - Packagin the binaries
  - Deploying the binaries to the test server
  - Testing the changes
  - Copy the code from one location to another

Build tool can automate the and simplify the above tasks.

- Features of Apache Ant

    - Ant scripts are written using plain XML.
    - Ant is good at automating complicated repetitive tasks

## Installing Apache Ant

- download the Apache Ant from https://ant.apache.org/bindownload.cgi
- Extract the files and add the entry to Environmental variable
  - ANT_HOME - [c:\apache-ant-1.10.9-bin]
  - Path = %ANT_HOME%   
- Verify the installation
 
 ```
 ant -verion
 
 Apache Ant(TM) version 1.10.9 compiled on September 27 2020
 ```
 
 ### Ant = Build Files
 
 - Typically Ant's build file called build.xml and saved in the base dir, it can be any name and stored in any dir
 
 ```
 <?xml version="1.0"?>
   <project name="Hello World Project" default="info">
   <target name="info">
      <echo>Hello World - Welcome to Apache Ant!</echo>
   </target>
</project>

Note: There shouldn't be a blonk line or whitespaces before the xml declaration. 
 ```
 
 - project element has 3 elements
    - name(Optional)
    - default(Optional)
    - basedir(Optional)

- target element has following attributes

1. name - Name of the target(Optional)
2. depedns - Comma seperated list of all targets that this target depends on(Optional)
3. description  - Short description of the target(Optional)
4. if - allows the execution of a target based on the trueness of the condition
5. unless - Adds the target to the dependency list of the specified extension point. 
       Ext point is similar to target but it does not have any task(Optional)
     
#### Run the ant script
  - Open the command prompt
  - go to the path where build.xml resides
  - type ant and hit enter
  
  
## Ant - Property task

- user can define the propety value by declaring the property element

```
<?xml version="1.0"?>
	<project name="Hello World Project" default="info">
		<property name="name" value="Madhav" />
  </project>
```
- Reuse the property name and also use predefined ant property such as 
  - ant.version - Ant current verion
  - ant.file - Full location of the build file
  - basedir - basedir of the build
  - ant.java.version - version of the JDK that ant use
  - ant.project.name - Name of the project
  - ant.project.default-target default target of the currnet project
  - ant-project-invoked-targets - Comma seperated list of the target that were invoked in the current project
  - ant.core.lib - Full location of the Ant jar file
  - ant.home - Ant dir of the Ant installation
  - ant.library.dir - Home dir for Ant lib files, typically ANT_HOME/lib

```
<?xml version="1.0"?>
<project name="Hello World Project" default="info">

   <property name="sitename" value="www.tutorialspoint.com"/>
   <target name="info">
      <echo>Apache Ant version is ${ant.version} - You are at ${sitename} </echo>
   </target>
</project>
```

- Setting a property directly in the build file is fine for small project
- For larger project, use external property file

Benefits of Storing the properties in a seperate file
  - Allows you to reuse the same build file with different property settings for different execution environment. build properties file can be maintained seperately for DEV, TEST, PROD env
  - Properties file is named build.properties and it is placed along-side the build.xml file.
  - Create different properties file such as
      -   build.properties.dev and build.properties.test.


```
build.xml

<?xml version="1.0"?>
	<project name="Hello World Project" default="info">
		<property name="name" value="Madhav" />
		<property file="build.properties"/>
		<target name="info">
			<echo>Hello ${name} - Welcome to Apache Ant! version - ${ant.version}</echo>
			<echo>Site name - ${sitename}</echo>
		</target>
	</project>
  
 build.properties
 
#Site name
sitename= 'https://borntolearn.com'
```

#### Ant - Data types

1. File set - data tyle represents a collection of files. it is used as a filter to include or exclude files that match a particular pattern.

```
<fileset dir="${src}" casesensitive="yes">
   <include name="**/*.java"/>
   <exclude name="**/*Stub*"/>
</fileset>
```
2. Pattern set - pattern that allows to filter files or folders easily based on certain patterns. The patternes can be created using the following meta characters.
  - ? Matches one char only
  - - Mathces zero or many chars
  -  ** - Matches zero or many directories recursively

```
<patternset id="java.files.without.stubs">
   <include name="src/**/*.java"/>
   <exclude name="src/**/*Stub*"/>
</patternset>

The patternset can then be reused with a fileset as follows −

<fileset dir="${src}" casesensitive="yes">
   <patternset refid="java.files.without.stubs"/>
</fileset>

```


3. File list - filelist data type is similar to the file set except the following differences


```
<filelist id="config.files" dir="${webapp.src.folder}">
   <file name="applicationConfig.xml"/>
   <file name="faces-config.xml"/>
   <file name="web.xml"/>
   <file name="portlet.xml"/>
</filelist>
```

4. Filter Set - data type along with the copy task, you can replace certain text in all the files that matches the pattern with a replacement value.

```
<copy todir="${output.dir}">
   <fileset dir="${releasenotes.dir}" includes="**/*.txt"/>
   <filterset>
      <filter token="VERSION" value="${current.version}"/>
   </filterset>
</copy>
```

5. Path - The path data type is commonly used to represent a class-path

```
<path id="build.classpath.jar">
   <pathelement path="${env.J2EE_HOME}/${j2ee.jar}"/>
   <fileset dir="lib">
      <include name="**/*.jar"/>
   </fileset>
</path>
```

6. Ant - Building projects

```
<?xml version="1.0"?>
<project name="fax" basedir="." default="build">

----Property file start ------------
   <property name="src.dir" value="src"/> -->  src dir
   <property name="web.dir" value="war"/> --> war dir
   <property name="build.dir" value="${web.dir}/WEB-INF/classes"/> --> classes dir
   <property name="name" value="fax"/> --> name = fax
---------------Property file end -------------   

-------Read all jar files from web-inf/lib
   <path id="master-classpath">
      <fileset dir="${web.dir}/WEB-INF/lib">
         <include name="*.jar"/>
      </fileset>
      <pathelement path="${build.dir}"/>
   </path>

-----Steps----------
1. Create build directory, if it does not exist
2. Execute the javac command(specifying jdk1.5 as our target compilation)
3. Supply source folder and the classpath to the javac task
----------------------
   <target name="build" description="Compile source tree java files">
      <mkdir dir="${build.dir}"/>
      <javac destdir="${build.dir}" source="1.5" target="1.5">
         <src path="${src.dir}"/>
         <classpath refid="master-classpath"/>
      </javac>
   </target>
   
   <target name="clean" description="Clean output directories">
      <delete>
         <fileset dir="${build.dir}">
            <include name="**/*.class"/>
         </fileset>
      </delete>
   </target>
</project>
```
