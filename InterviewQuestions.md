# Java Interview Questions

1. Reason for using Java?
    - Builtin support for multi-theading, socket communication and memory management
    - Object oriented
    - Portability
    - Supports Web application, entriprise application
    
2. What is the difference between the java platform and other software platform?
    - Java is a software only platform which can run on any hardware(windows, unix, linux)
    - Java code --> Byte code --> JVM

3. Difference between Java and C++
    - Java does not support pointers
    - Java does not support mutiple inheritance, instead it supports multiple interface inheritance
    - Java does not support destructors rather add finalize() method. Finalize methods are in invoked by the garbage collector prior to reclaiming the memory occupied by the object.
    - All the code in java program is encapsulated within classes therefore java does not have global variables or functions.

4. Java class loaders
    1. Bootstrap - Loads JDK internal classes, java.* packages
    2. Extensions - Loads jar files from JDK extension directory(java.ext.*)
    3. System - Loads classes from system classpath

5. Static vs dynamic class loading?
    Static class loading: 
        1. classes are statically loaded by new operator
        2. NoClassDefFoundException
    Dynamic loading: 
        1. loaded programatically invoking the functions at runtime(Class.forName())
        2. NoClassFoundException

6. What are static initializers or static blocks with no function names?
      static variables and blocks are executed even before constructors are executed.
      They typically initialize the static fields
      
7. What are the advantages of OOPL(Object oriented programming language)?
     1. Polyporphism - Same method name with difference functionality
     2. Inheritance - extends the class functionality
     3. Encapusulation - using private access modifier to protect the variable methods.

8. How does Objecet orient approach improve the software development?
    1. Re-use - Inheritance
    2. Real mapping to the problem domain  - Encapsulation
    3. Modular architechture
    4. Increased quality and reduced development time

9. How do you express 'Is a ' and 'has a' or explain inheritance and composition
    'Is a'
        Inheritence [House is a building] House extends Buildign
        Unidirectional and uses extends keyword
    Has a - House has a Batchroom , 
      Class House{
        Bathroom br = new Bathroom()
      }
    
      Composition simply means using instance variable that refer to other objects
      
      
  10. When to use inheritance/composition?
      - Don't use inheritance to resue the code if there is not 'Is a' relationship, use composition to reuse the code
      - Overuse of implementation inheritance(use extends keyword) can break all the subclasses, if superclass is modified
      
      
  11. Aggregation vs composition
      
      Aggregation: It is an association in which one class belongs to collection. Weaker relationship, 
      e.g. Part can exist with out the product
      
      Composition: Its is an association in which one class belogs to collection. Stronger relationship
      e.g. Item cannot exist if order is deleted.
      
      
 12. What you mean by Polymorphism, inheritance, encapsulation, dynamic binding?
      Polymorphism: It is bottom up method call. Benefits of polymorphism is that it is very easy to new classes of derived object without breaking the calling code.
      
      Inheritance: 
          1. Implementation inheritance(class inheritance)
          2. Interface inheritance(type inheritance)

      Encapsulation: 
      
  13. What is the difference between an abstract class and an interface?
        - Abstract class: 
            - You want the base class to present only an interface for its derived classes.
            - You don't want anyone to actually instatiate an object of the base class.
          
         - Interface: 
            - Preventing any method implementation.


    14. Why there are some interfaces with no defined methods? or Marker interface?
            The interfaces with no defined methods act like markers. They just tell the complier that the object of the classes implementing the interfaces with no defined methods need to be treated differently.
            
            e.g. Serializable, Clonable
            
            
    15. Overloading vs Overriding
    
            Overloading: deals with mutiple methods with same name but different signatures
            
            Overriding: deals with two methods, one in the parent class and the other one in the child class and has the same name and signatures.
          
    16. equals() and hashcode() 
        - If a class overrides equals(), it must override hascode()
        - If 2 objects equal, then theri hasCOde values must be equal as well 
        - If a field is not used in equals(), then it must not be used in hashCode().
        - if it is accessed often, hashCode() is a  candidate for caching to enhance performance.
          
   17. Enum constants 
            Which provides readability and maintainability of your code.
    
  18. Main difference between a String and StringBuffer class?
        - String is immutable - Can't modify a string object but can replace it by creating a new instance and it is expensive.
        - StringBuffer - It is mutable and not synchronized
        - StingBuilder - mutable and sychronized
        - toString(), concat(), trim(), subString() and replace() creates new string instances

  19. What is the difference between pass by value and pass by reference?
        - Java always get a copy of that data which is exactly how pass by value works

  20. What is serialization?
        - Searialization is process of reading and writing an object.
        - Transient variable cannot be serialized

  21. Deep and shallow copy?
  22. Static and instance variable?
        - Class variables are called static. There is only one occurance of the class variable per JVM per class loader.
        - Instance variables are non-static and there ios one occirnce of tan instance variable in each class instance.
  23. What are acces modifiers?
        public , protected, private , no modifer
        
 24. What are the java modifiers?
        - static
        - abstract - cannot be instantiated, must be a superclass
        - synchronized 
        - trainient - Fields should not be serialized
        - final - class can't inherited, method can't be overriden, mark variable constant
  25. How does java allocate stack and heap memory?
        - Primitive variable - stack
        - local method varibles in the heap
        
26. What is the difference between process and threads? 
        - Process - It is an execution of a program
        - Thread - It is a single execution sequence witin the process.           

27. What are the Thread states?
        - Runnable
        - Running - yield
        - Sleep - Runnable
        - wait --> notify & notifyAll
        - yield --Runnable
