# What's new in Java 9
##Some of important java 9 features are:
1. Java 9 REPL (JShell)
2. Factory Methods for Immutable List, Set, Map and Map.Entry
3. Private methods in Interfaces
4. Java 9 Module System
5. Process API Improvements
6. Try With Resources Improvement
7. CompletableFuture API Improvements
8. Reactive Streams
9. Diamond Operator for Anonymous Inner Class
10. Optional Class Improvements
11. Stream API Improvements
12. Enhanced @Deprecated annotation
13. HTTP 2 Client
14. Мulti-Resolution Image API
15. Miscellaneous Java 9 Features

All feature detail list, see openJDK(<http://openjdk.java.net/projects/jdk9/>)

##Java 9 REPL(JShell)
Oracle Corp has introduced a new tool called “jshell”. 
It stands for Java Shell and also known as REPL (Read Evaluate Print Loop). 
It is used to execute and test any Java Constructs like class, interface, enum, object, statements etc. very easily.

```Java
G:\>jshell
|  Welcome to JShell -- Version 9-ea
|  For an introduction type: /help intro


jshell> int a = 10
a ==> 10

jshell> System.out.println("a value = " + a )
a value = 10
```

##Factory Methods for Immutable List, Set, Map and Map.Entry
Oracle Corp has introduced some convenient factory methods to create Immutable List, Set, Map and Map.Entry objects. 
These utility methods are used to create empty or non-empty Collection objects. <br><br>
In Java SE 8 and earlier versions, We can use Collections class utility methods like unmodifiableXXX to create Immutable Collection objects. 
For instance, if we want to create an Immutable List, then we can use Collections.unmodifiableList method. <br><br>
However these Collections.unmodifiableXXX methods are very tedious and verbose approach. 
To overcome those shortcomings, Oracle corp has added couple of utility methods to List, Set and Map interfaces.<br><br>
List and Set interfaces have “of()” methods to create an empty or no-empty Immutable List or Set objects as shown below:
```Java
List immutableList = List.of();  //Empty List Example
List immutableList = List.of("one","two","three"); //Non-empty List Example
```
Map has two set of methods: of() methods and ofEntries() methods to create an Immutable Map object and an Immutable Map.Entry object respectively.
```Java
jshell> Map emptyImmutableMap = Map.of()
emptyImmutableMap ==> {}
...
jshell> Map nonemptyImmutableMap = Map.of(1, "one", 2, "two", 3, "three")
nonemptyImmutableMap ==> {2=two, 3=three, 1=one}
```

##Private methods in Interfaces
In Java 8, we can provide method implementation in Interfaces using Default and Static methods. However we cannot create private methods in Interfaces.<br><br>
To avoid redundant code and more re-usability, Oracle Corp is going to introduce private methods in Java SE 9 Interfaces. 
From Java SE 9 on-wards, we can write private and private static methods too in an interface using ‘private’ keyword.<br><br>
These private methods are like other class private methods only, there is no difference between them.
```java
public interface Card{

  private Long createCardID(){
    // Method implementation goes here.
  }

  private static void displayCardDetails(){
    // Method implementation goes here.
  }

}
```

##Java 9 Module System
One of the big changes or java 9 feature is the Module System. Oracle Corp is going to introduce the following features as part of **Jigsaw Projec**

+ Modular JDK
+ Modular Java Source Code
+ Modular Run-time Images
+ Encapsulate Java Internal APIs
+ Java Platform Module System

Before Java SE 9 versions, we are using Monolithic Jars to develop Java-Based applications. 
This architecture has lot of limitations and drawbacks. To avoid all these shortcomings, Java SE 9 is coming with Module System.<br><br>
JDK 9 is coming with 92 modules (can be more as releasing going on). We can use JDK Modules and also we can create our own modules as shown below:
```java
module com.foo.bar { }
```

More detail will be posted later...

##Process API Improvements
Java SE 9 is coming with some improvements in Process API. They have added couple new classes and methods to ease the controlling and managing of OS processes.<br><br>
Two new interfcase in Process API:
+ java.lang.ProcessHandle
+ java.lang.ProcessHandle.Info

```java
ProcessHandle currentProcess = ProcessHandle.current();
System.out.println("Current Process Id: = " + currentProcess.getPid());
```

##Try With Resources Improvement
We know, Java SE 7 has introduced a new exception handling construct: Try-With-Resources to manage resources automatically. 
The main goal of this new statement is “Automatic Better Resource Management”<br><br>
Java SE 9 is going to provide some improvements to this statement to avoid some more verbosity and improve some Readability.

#####Java SE 7 Example
```java
void testARM_Before_Java9() throws IOException{
 BufferedReader reader1 = new BufferedReader(new FileReader("journaldev.txt"));
 try (BufferedReader reader2 = reader1) {
   System.out.println(reader2.readLine());
 }
}
```
#####Java SE 9 Example
```java
void testARM_Java9() throws IOException{
 BufferedReader reader1 = new BufferedReader(new FileReader("journaldev.txt"));
 try (reader1) {
   System.out.println(reader1.readLine());
 }
```

##CompletableFuture API Improvements
In Java SE 9, Oracle Corp is going to improve CompletableFuture API to solve some problems raised in Java SE 8. 
They are going add to support some delays and timeouts, some utility methods and better sub-classing.
```java
Executor exe = CompletableFuture.delayedExecutor(50L, TimeUnit.SECONDS);
```
Here delayedExecutor() is static utility method used to return a new Executor that submits a task to the default executor after the given delay.

##Reactive Streams
Now-a-days, Reactive Programming has become very popular in developing applications to get some beautiful benefits. 
Scala, Play, Akka etc. Frameworks has already integrated Reactive Streams and getting many benefits. 
Oracle Corps is also introducing new Reactive Streams API in Java SE 9.<br><br>
Java SE 9 Reactive Streams API is a Publish/Subscribe Framework to implement Asynchronous, Scalable and Parallel applications very easily using Java language.<br><br>
Java SE 9 has introduced the following API to develop Reactive Streams in Java-based applications.
+ java.util.concurrent.Flow
+ java.util.concurrent.Flow.Publisher
+ java.util.concurrent.Flow.Subscriber
+ java.util.concurrent.Flow.Processor

##Diamond Operator for Anonymous Inner Class
We know, Java SE 7 has introduced one new feature: Diamond Operator to avoid redundant code and verbosity, to improve readability. 
However in Java SE 8, Oracle Corp (Java Library Developer) has found that some limitation in the use of Diamond operator with Anonymous Inner Class. 
They have fixed that issues and going to release as part of Java 9.
```java
public List getEmployee(String empid){
     // Code to get Employee details from Data Store
     return new List(emp){ };
  }
```
Here we are using just “List” without specifying the type parameter. <br><br>
Detail will be posted later...


#####Reference:
OpenJDK<http://openjdk.java.net/projects/jdk9/> <br>
Journalde<https://www.journaldev.com/13121/java-9-features-with-examples#java-9-core>