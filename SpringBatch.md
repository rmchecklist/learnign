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
  
  
  
