% FreeRTOS

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

[Getting Started with Amazon FreeRTOS](https://docs.aws.amazon.com/freertos/latest/userguide/freertos-getting-started.html)  

[Amazon FreeRTOS API Reference](https://docs.aws.amazon.com/freertos/latest/lib-ref/index.html)  

[MQTT](https://www.runoob.com/w3cnote/mqtt-intro.html)  



RTOS Fundamentals
=================

### Multitasking Basics ###

The use of **multitasking** operating system can simplify the design of what would otherwise be a complex  
software application:  
1. The multitasking and inter-task communications features of the operating system allow the complex application  
   to be partitioned into a set of smaller and more manageable tasks.  
2. The partitioning can result in easier software testing, work breakdown within teams, and code reuse.  
3. Complex timing and sequencing details can be removed from the application code and become the  
   responsibility of the operating system.  

### Scheduling Basics ###

The **scheduler** is the part of the kernel responsible for deciding which task should be executing at any  
particular time. The kernel can suspend and later resume a task many times during the task lifetime.  

The **scheduling policy** is the algorithm used by the scheduler to decide which task to execute at any  
point in time. The policy of a (non real time) multi user system will most likely allow each task a "fair"  
proportion of processor time. 


### Context Switching ###

### Real Time Applications ###

Real time operating systems (RTOSes) achieve multitasking using these same principals but their objectives are  
very different to those of non real time systems. The different objective is reflected in the scheduling policy.  
Real time / embedded systems are designed to provide timely response to real world events. Events occurring in  
the real world can have deadlines before which the real time / embedded system must respond and the RTOS  
scheduling policy must ensure these dealines are met.  

To achieve this objective the software engineer must first assign a priority to each task. The scheduling policy  
of the RTOS is then to simply ensure that the highest priority task that is able to execute is the task given  
processing time. This may require sharing processing time "fairly" between tasks of equal priority if they are  
ready to run simultaneously.  

### Real Time Scheduling ###
