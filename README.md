# temp
temp
================
Spring Cloud
http://dustin.schultz.io/ps-scf
Netflix OSS(Netflix Open Source Software Center) + Spring + Spring Boot  = Spring Cloud Netflix (AWS Service registry for resilient mid-tier load balancing and failover.)Distributed configuration using Spring configurationClient side load balancing using spring cloud and netflix ribbon (Ribbon is a Inter Process Communication (remote procedure calls) library with built in software load balancers. The primary usage model involves REST calls with various serialization scheme support.)intelligent routing via a gate service using spring cloud and netflix zuul (Zuul is a gateway service that provides dynamic routing, monitoring, resiliency, security, and more.)fault tolerance using spring cloud and netflix hystrix (Hystrix is a latency and fault tolerance library designed to isolate points of access to remote systems, services and 3rd party libraries, stop cascading failure and enable resilience in complex distributed systems where failure is inevitable.)
Spring discovery provides1. A way for service to register itself2. A way for a service to deregister itself3. A way for client to find other services4. A way to check the health of a service and remove unhealthy instances
Cloud native application are built specifically for cloud computing.
Service discovery components1. Discovery server2. Application server3. Application Client

===============
Gradle
Groovy DSL: Gradle is built using Java but the build language is Groovy DSL which is JVM based.Gradle supports Ivy and Maven dependenciesTo Install gradle http://gradle.org OR http://gvmtool.net which is Groovy Enviroment manager(Do not use GVM on windows)the build file in gradle is build.gradlegradle build file has tasks which contains plugins, dependencies etc.
gradle tasks cmd gives out the tasks available in that root project
To Build java Code for e.g.
gradle build cmd is exected
Tasks have life cycle1. Initialization2. configuration3. Execution
Tasks has properties and can define its own properties and being configured during configuration phase
Tasks and actions
Tasks has dependencies
For e.g.
project.task("Task1") and then "gradle tasks" cmd against the gradle file. It prints the Task1 on the screen.//Different types of task definitions as follows
task("Task2")task "Task3"task Task4
Here project is a top level object and everything that gradle file belongs to project definedAssigning the properties like below
Task4.Description="Task 4 Description"
After execution of this task, the output printed is Task4 - Task 4 Description
Assigning a task for action as follows:Task4.doLast {"This is Task4 action"}
Another way to do same thingTask4 << {"This is Task4 action"}ORTask4 << {println "This is Task4 action"}
run with "gradle Task4" cmd
Common model of gradle task definition and execution as follows
task Task5 { description "Some Description for task5" doLast {  println "Task5 Executed" }}
Build PhasesInitialization Phase: Used to configuret the multi project buildsConfiguration Phase: executes the task but not the actionExecution Phase: Execute action
doFirst{"Task6 - First action"} is just like doLast except executed first
task Task6 { description "Some Description for task5" doFirst {  println "Task5 Executed" }}VS Task6.doFirst { println "Another first"}In above case as a comparison, the explicit definition task6.doFirst{} is excuted first vs definingteh task task6 ** Imp. to remember
Task dependenciesTask6.dependsOn task5: In this case task5 methods are executed first and then task6 methods (doFirst and doLast sequence remains same.)
adding properties to gradleFor e.g.def projectVersion = "2.0" //local property
then can be used like below
task Task6 { description "Some Description for task5" doFirst {  println "Task5 Executed - version $projectVersion" }}
Task Dependencies
** We can use -q flag to quite down the gradle's own output ***
mustRunAfter - if two tasks execute one must run after the othershouldRunAfter - if two tasks execute one should run after the otherfinzalizedBy - sort of inverted dependency Typed TasksFor e.g. copy task(built in with gradle)
To run the gradle faster we can use gradle --daemon XX(build/clean/compile) cmd.Another way to do is to create the properties file and put entry like beloworg.gradle.daemon=true
gradle test -test *testClassName should run mentioned single testgradle test OR gradle clean test should run all the tests
For integration testing, we have to import gradle-testsets-plugin
The Gradle Wrapper is the preferred way of starting a Gradle build. The wrapper is a batch script on Windows, and a shell script for other operating systems. 
When we start a Gradle build via the wrapper, Gradle will be automatically downloaded and used to run the build.
The cmd to gradle wrapper os gradlew 
Gradle wrapper (wrapper) allows us to use very specific version of gradle for us. If teh specific version of gradle is not installed on the machine where this script is running then gradle wrapper will down and install that automatically for us.
for e.g.task wrapper(type:Wrapper) { gradleVersion = '2.6'}

======================
Header is a usually a first element in h5(HTML5)hgroup groups together the H1-H(n) headers, aka Fat headers, if they are in parent child relationship
headers and footers are closely related and footer has ancestoral relationship with Section which means we can have more than one footer
article - theya re self containing documents.
Sections have 2 implementations1. They can be in subject areas2. They can be part of articlesImp: Sections do not stand on their own where as articles do.
aside is essentially related to docment but are not part of sections or articles. For.e.g. side bars, nav sections etc.
nav section are for navigations and should be used primarily for major links only.should not be used for everylink or for things liek search results etc.
mark is used to highlight the part of the document/element.
Time is used to display the time and date information in universal format( y, m, day, T(optional), 24ht clock, timezone ),
<dl><dt><dd> should be used to describe publication<em> should be used to subtly change the meaning of the statement<i> should be used to italicized<ol> has 2 new attributes start and reverse<s> should be used to designate something that is not true/relevent <small> should be used to make teh text small
Canvas in HTML5 is designed fror 4th quadrant Stroke is borderfill is the solidclear is the remove the section of the solidcolor has to be added to canvas before stroke is called
Gradients are of linear and radial gradient types
A path is a pattern for pen to follow
Circles can be drawn with arc method

==============================================
S.O.L.I.D. Principles
SOLID principles should be visible at the highest level,MVC grameworks should not be visible at the highest level, They should hide the details in the architecture designframeworks are teh abstractions of architecure design and their details should be hidden,Application layers should be boundary separated from external details such as frameworks, database systems and should be treated as plugins,
High level principles should be dependent on details and details should be dependent on high level principles aka Dependency inversion principle
Good architecture practises to defer the decisions as long as possible.
Rigidity means a system hard to change
Fragility: One change in one module makes other related modules to misbehave.
The dependencies should be managed independently and isolate them.
If the components in a system are not eaily reusable for oither modules purpose then the system is immobile OR rigid.
Viscosity: if the system is taking long time to test then teh system is considered as viscous.
Complexity: This happend mainly because of ancipatory elements. This can be avoided by maintaining the comprehensive suits of tests which also leads to simple design, maintainable code, 
Dependency Inversion prevents the design from dependent on details.
the Single Responsibility principlethe Open closed principlethe Liskov substition principlethe Interface segregationthe Dependency Inversion principle
The principles of CohesionThe release-reuse Equivalency PrincipleThe Common Closure PrincipleThe Common Reuse Principle
Component Coupling PrinciplesThe Acyclic Dependencies principleThe Stable Dependencies principleThe Stable Abstractions principle
====================
