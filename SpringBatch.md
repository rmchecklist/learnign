1. Create a template using https://start.spring.io/

Job - job defines the list of states and transition from one state to other
Step - Independent piece of processing, that make the job, Job can have many steps
Tasklet - will execute within the transaction
Chunk - item based processing, three main component 
  reader
  processor
  writer


Job repository:
  Map based(In memory, not a production based)
  JDBC based 
  
Job ==> Job instance ==> Job Execution
  
  
###### Data Model

![image](https://user-images.githubusercontent.com/5713791/120704954-38594100-c485-11eb-88f5-c9efa8bdf5c9.png)

  
