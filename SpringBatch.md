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

  
 - Execute the flow by using next or start to end methods.


## Plural sight:

###### Basic Spring Batch concepts

Jobs ==> Step ==> 


### Spring batch tutorials [https://www.tutorialspoint.com/spring_batch/spring_batch_architecture.htm]

Components of spring batch:

1. Job - It runs from start to finish without interruption
  Job further devided into steps
  
  
##### Create configuration file

1. Add @configuration annotation to the file
2. @EnableBatchProcessing
3. @Autowired on JobBuilderFactory and StepBuilderFactory, this will be referenced in Bean methods


Flow:(Create a simple job) 

1. Create a step 

```
@Bean
	public Step step1() {
		return stepBuilderFactory.get("step1").tasklet(new Tasklet() {
			
			@Override
			public RepeatStatus execute(StepContribution contribution, ChunkContext chunkContext) throws Exception {
				System.out.println("Step 1");
				return RepeatStatus.FINISHED;
			}
		}).build();
	}
```

2. Execute the step using job

```
@Bean
	public Job helloWorldJob() {
		return jobBuildFactory.get("helloWorldJob").start(step1()).build();
  }
```

Job
Step
  Tasklet
  Chunk - Item based
  
  
Spring batch stores in the job repository information into either map/memory based/JDBC based repository


Job ==> Job Instance(Many) ==> Job Execution(Many)

Spring Batch data model

![image](https://user-images.githubusercontent.com/5713791/120812132-b4519880-c51a-11eb-96e0-f730834d91ab.png)


##### JOb ==> JOb Execution ==> Step execution


BATCH_JOB_INSTANCE --> BATCH_JOB_EXECUTION(PARAMS, CONTEXT) --> BATCH_STEP_EXECUTION(CONTEXT)


###### Step transition


```
@Bean
public Job transitionJobSimpleNext(){
  return jobBuilderRepository.get("job_name")
    .start(step1())
    .next(step2())
    .build();
}
```

###### Spring batch transition

```
@Bean
public Job transitionJobSimpleJobNext(){
  return jobBuilderFactory.get("transitionJobNext")
    .start(step1())
    .on("COMPLETED").to(step2())
    .from(step2()).on("COMPLETED").to(step3())
    .from(step3()).end() --> indicate the last step(programatically set the complete status)
    .build();
}
```

After completion of any step we can set the status to FAIL. It means, not going to continue the next step

```
.start(step1()).on("FAIL")
.from(step1()).to(step2())

In this scenarion step2() never going to call
```

stopAndRestart

```
.start(step1()).stopAndRestart(step2()) ==> complete step1 and wait for human intervention to start step2

```

###### Spring batch flows

- Flows is the collection of steps, this can reusable
- Flow can made up of other flows or steps


##### Spring batch splits


##### Spring batch decision


##### Spring batch nested jobs


##### Spring Batch listeners

1. JobExecutionListener (Before and After job execution)
2. StepExecutionListener (Before and After Step execution)
3. ChunkListener (Before and After chunk execution)
4. IteamReadListener
5. ItemProcessListener
6. ItemWriteListener


##### Job Parameters







