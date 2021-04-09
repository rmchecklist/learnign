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
     
Run the ant script
