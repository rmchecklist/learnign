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


###### Spring Batch input and output data




# Spring Batch Tutorial[ https://www.toptal.com/spring/spring-batch-tutorial ]


Spring batfh data model

![image](https://user-images.githubusercontent.com/5713791/121596864-04929400-ca0e-11eb-822d-a248c8865396.png)


 - Jobs ==> mutiple steps ==> each step has (ItemReader, ItemProcessor, ItemWriter
 - Jobs executed by a JobLauncher
 - Metadata about configured and executed jobs is stored in a JobRepository.


## Job
- Job associated with multiple jobinstance, each of which is defined uniquely by its particular JobParameters that are used to start a batch job.
	- Each run of a JobInstance is referred to as a JobExecution.
	- JobExecution typically tracks what happened during a run, such as current and exit statuses, start and end time etc.

## Step

- Step is an independent specific phase of a batch job, such that every job is composed of one or more step
- Step has an indiviudal StepExecution that represents a single attempt to execute a step. 
- Step Execution stores the inforamation about current and exit statuses, start and end time so on.

## ExecutionContext

- Set of key -value pairs containing information that is scoped that is scoped to either StepExecution or JobExecution.


## Spring batch startup application

```
@EnableBatchProcessing
@SpringBootApplication
public class BatchApplication {
    public static void main(String[] args) {
        prepareTestData(1000);
        SpringApplication.run(BatchApplication.class, args);
    }
}
```
- @EnableBatchProcessing - Annotation enables spring batch features and provides a base configuration for setting up the batch jobs

- @SpringBootApplication - Annotation comes from the spring boot project that provides standalone production ready spring-based applications. It specifies a configuation class that declares one or more spring beans and also triggers auto-configuration and spring component scanning.

## Sample Spring job config

```
@Configuration
public class CustomerReportJobConfig {
    @Autowired
    private JobBuilderFactory jobBuilders;

    @Autowired
    private StepBuilderFactory stepBuilders;

    @Bean
    public Job customerReportJob() {
        return jobBuilders.get("customerReportJob")
            .start(taskletStep())
            .next(chunkStep())
            .build();
    }

    @Bean
    public Step taskletStep() {
        return stepBuilders.get("taskletStep")
            .tasklet(tasklet())
            .build();
    }

    @Bean
    public Tasklet tasklet() {
        return (contribution, chunkContext) -> {
            return RepeatStatus.FINISHED;
        };
    }
}
```

#### There are 2 main approaches to building a step

1. Tasklet-based 
	- It supports a simple interface that has only one method execute(), which is called repeatedly until it either returns RepeatStatus.Finished or throws an exception to singnal a failure. 
	- Each call to the Tasklet is wrapped in a transaction
2. Chunk oriented processing 	
	- It refers to reading the data sequentially and creating chunks that will be written out within a transaction boundary
	- Each individual item is read in from an ItemReader, handded to an ItemProcessor and aggregated.
	- Once the number of item read equal the commit interval, the entire chunk is written out via the Itemwriter, and then transaction is committed.

Example of chunk oriented processing

```
@Bean
public Job customerReportJob() {
    return jobBuilders.get("customerReportJob")
        .start(taskletStep())
        .next(chunkStep())
        .build();
}


@Bean
public Step chunkStep() {
    return stepBuilders.get("chunkStep")
        .<Customer, Customer>chunk(20)
        .reader(reader())
        .processor(processor())
        .writer(writer())
        .build();
}

```

- chunk() method builds a step that processes item in chinks with the size provided, with each chunk then being passed to the specified reader, processor and writer.



### Custom reader

- In order to read a list to information, we need to provide an implementation of the interface org.springframework.batch.item.ItemReader

```
public interface ItemReader<T> {
    T read() throws Exception, UnexpectedInputException, ParseException, NonTransientResourceException;
}
```
- An ItemReader provides the data and is expected to be stateful. It is typically called multiple time for each batch. with each call to read() returning the next value and finally returning null when all input data has been exhausted.

- Spring batch provides some out-of-the-box implementations of ItemReader, which can be used for a variety of purposes such as collections, files, integrating JMS and JDBC as well as multiple resources and so on.

## reader() on spring config

```
@StepScope
@Bean
public ItemReader<Customer> reader() {
    return new CustomerItemReader(XML_FILE);
}
```

- @StepScope, letting spring know that this calss is a step scoped spring compinent and will be craeted once per step execution as follows.


### Custom processors

- Itemprocessor transform items and introduce business login in an item-oriented processing scenario. They must proivde an impelmentation of the interface org.springframework.batch.item.ItemProcessor

```
public interface ItemProcessor<I, O> {
    O process(I item) throws Exception;
}

```

- The method process() accepts one instance of the I class and may or may not return an instance of the same type. Returning null indicates that the item should not continue to be processed.
- Spring provides few standard processors, such as CompositeItemProcessor that passes the item through a sequence of injected OtemProcessors and a ValidatingItemProcessor that validates input.
- 
