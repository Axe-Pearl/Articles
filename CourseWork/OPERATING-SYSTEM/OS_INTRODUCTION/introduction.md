# **OPERATING SYSTEMS:**
### Introduction to software and Operating System:
+ Operating system is the system software, which acts as an interface between the user and the system.
+ **Software** is a computer program that contains a set of instructions that are used to execute specific tasks.
+ Software is of two types:- 
  + **Application Software:**
Application software is software that is designed to perform a specific task.

    **Examples:** VLC Media Player, Microsoft Word, Calculator, etc.
  + **System Software:** System software provides a platform for application software to perform its tasks (i.e System software is used to run the application software).

    **Examples:** Operating system, Device Drivers, linker, loader, etc.

  ![Software interaction image](https://octodex.github.com/images/01.png)
  
+ PC users can't use system peripherals, memory, and CPU directly to perform their computation tasks. Hence **Operating System** is used for effective usage of CPU, main memory, and other system peripherals to perform their tasks.

___

### Basic Functionalities of Operating System:
  1. **Resource Manager/Resource allocator:**   
      + The operating system allocates the resources/devices (system peripherals), main memory, and CPU for the application software (user) to perform their respective tasks.

         **Example:** If we want to play an audio file, the operating system assigns speakers to play the respective audio file for us.

      + Operating system also manages the issues related to resource allocation.

         **Example:** If two or more processes want to access the same resource at the same time, then OS will decide which process will access the respective resource first. Such tasks are taken care by OS.

  2. **Processor Management:**
     + The CPU is the brain of the computer, i.e it is responsible for all the tasks performed by the system.
     + OS will determine to which process/task the CPU will be assigned and for how long (done using process scheduling).

  3. **Memory Management:**
     + In order to run any application software, it must be loaded into the main memory.

       ![program being loaded into main memory](https://octodex.github.com/images/02.png)
     + Size of the main memory is limited.
     + OS determines which process (program) should be in the main memory and its time duration in the main memory (i.e for how long the program will be in the main memory). And also how much memory will be allocated for the process in the main memory.

  4. **Input-Output Device Management:**
     + One process can 1 input-output device at a time
     + If 2 or more processes needs to access a particular input/output device at the same time, the OS will allocate and manage that input/output deviceamong those processes.
     + **Operating System** is responsible for allocating and managing input-output devices among the processes.

  5. **Storage Management:**
     + **Operating System** will determine that how the data will be stored in secondary memory (i.e the hard disk). and also how the data will be accessed/retrieved from the secondary memory to main memory with the help of file system.

  6. **Security and Protection:**
      + **Operating System** takes the responsibility that no unauthorized users can access the system.

___

### Goals of Operating System:

#### **The two main goals of operating system are:**
   1. To provide convience to the user, i.e making the system user friendly. (End user/Customer goal)
   2. To provide efficient computation, i.e making computation process more efficient. (Developer/System goal)
___

### Types of Operating Systems:
The main types of Operating systems are:-
   1. **Batch OS**
   2. **Multiprocessing OS**
   3. **Time Shared OS/Multi-tasking OS**
   4. **Multiprocessor OS**
   5. **Distributed OS/Network OS**
   6. **Real Time OS**


1. **Batch OS:**
     + Batch OS is the oldest types of operating system, where the tasks/processes are assinged in the form of punching cards. These tasks/processes in Batch OS are referred as jobs.
     + Batch is a collection of jobs.
     + Here the user provides tasks/processes (jobs) in the form of punch cards.
     + These punch cards consists of input data + program + control instructions (in the form which can be understood by the computer)
     + After inserting the all required information in the punch card(s) (jobs), all the job details will be provided to the computer operator. We have a computer operator which is an interface between the user and the computer, it takes input (jobs) in the form of punch cards.
     + The computer operator will group all these jobs into batches. Jobs that are similar are grouped together into batches.
     + After grouping jobs into batches, the batches are arranged in a queue where they will be executed one at a time.
     + Computer will execute one batch at a time. After executing a batch it gives the user the corresponding output for each job. After that, it executes the remaining batches.
       **Example:** 
       ![batch OS example](https://octodex.github.com/images/03.png)

       + In the above image we have B1,B2,B3,B4,B5 and B6 jobs. B1,B2 and B6 are similar whereas B3,B4 and B5 are similar.
       + The computer operator has batched B1,B2 and B6 jobs in batch 1 and B3, B4 and B5 jobs in batch 2.
       + These batches are arranged in the queue. So batch 1 (which is first in the queue) gets executed first. After executing batch 1, the computer gives the output for respective jobs in batch 1, and then it executes batch 2.

    **Major Drawbacks in Batch OS:**
      1. There is no proper interaction between the user and the system (Error messages and other notifications will not be properly notified)
      2. Consider the above example. Assuming that the CPU is executing batch-1. All the jobs in batch 1 have a process that involves the usage of an input/output device. During the input/output device operations, the CPU remains idle (i.e it won't be executing batch-2 jobs unless it completely executes batch-1). Hence there is no efficient use of CPU/processor.

2. **Multiprogrammed OS:**
    + In multiprogrammed OS, we can place multiple tasks(programs) in the main memory and we can execute all the programs simultaneously.
    + Unlike in Batch OS, CPU utilization in Multiprogramming OS is done effectively, i.e CPU will not remain idle, it keeps on executing the tasks simultaneously.
      **Example:**
       ![Multiprogrammed OS example](https://octodex.github.com/images/04.png)

       + In the above example, we have 3 tasks T1,T2 and T3 lined up which are to be executed.
       + the CPU will execute the process T1 first, when T1 needs some input-output operation, the OS assigns T1 to the input/output devices. During the input-output operations of T1, the CPU happens to be idle, so it starts executing T2. (the same thing is done in case of T2 and T3).

3. **Time Shared OS/Multi-Tasking OS:**
    + Multi-Tasking OS is an extension of Multiprogrammed OS, where the main memory consists of 1 or more programs (which are to be executed) and each program is executed simultaneously.
    + in Multi-Tasking OS, the CPU will allocate equal time to all the programs/tasks present in the main memory.
      **Example:**
       ![Time-Shared OS example](https://octodex.github.com/images/05.png)

       + In the above diagram, we have 3 tasks B1,B2 and B3 which are to be executed.
       + Task B1 takes 4ms to complete, whereas tasks B2 and B3 take 8ms and 6ms respectively.
       + The given processor in this time-sharing OS allocates 2ms for each process/task.
       + So, in the first iteration, the processor will spend 2ms on each task (leaving the rest of the unfinished process in each task for the next iteration. 6ms have been spent till the end of the first iteration). Same as in the second iteration. By the end of 2nd iteration task B1 will be completed as it takes 4ms to be completed (2ms in the first iteration and 2ms in the second iteration). By the end of the third iteration, task B3 will be finished as it takes 6ms to complete (2ms in the first iteration, 2ms in the second iteration and 2ms in the third iteration)
       + After the completion of the third iteration by the processor, we only have task B2, so the processor will spend complete time finishing task B2.
       + So by 18ms all our tasks will be completed (6ms in the first iteration, 6ms in the second iteration, 4ms in the third iteration and the rest of the time taken to complete B2)

4. **Multiprocessor OS:**
    + In all the above OS, we have only 1 processor involved to complete all the assigned tasks. In this OS we have multiple processors connected to the system to perform tasks.
    + All the processors are equally involved to complete the tasks.
      **Example:**
       ![multiprocessor OS example](https://octodex.github.com/images/06.png)
        
        + In the above image, we have P1, P2 and P3 processors involved to complete tasks.
        + P1 executes the tasks t1,t2 and t3. Whereas P2 executes t4,t5 and t6, and P3 executes t7,t8 and t9.
        + All the 9 tasks/programs/processes are executed together.
      
      **Advantages of Multiprocessor OS:**
       + **Increased throughput:** output will be received in relatively less time.
       + **More reliable:** in case a processor fails/crashes, the remaining processors will do the work of crashed processor.

5. **Network OS/Distributed OS:**

    + In Distributed OS, the task and the information related to the task is distributed among all the systems present in a network.
      **Example:** 
       ![Distributed OS example](https://octodex.github.com/images/07.png)

       + In the above image, we have 10 systems (C1, C2, C3,... ,C10) working on a same project(task).
       + The project information is distributed among 10 systems.
       + If any of the systems makes progress in completing the task/project, the progress is shared with rest of the systems.
       + There will be no problem if any of the system in the network fails/crashes as the remaining systems will have the copies of its tasks and progress.

6. **Real time OS:**
    + Real time OS is used when we have to implement real time applications.
    + **Examples:** Scientific observations such as astronomical observations, medical observations, motion tracking of an object, etc.
    + There are two types of Real time OS:
       1. **Hard Real time OS:**
          + In Hard Real time OS, the application should be executed in stipulated amount of time, else the process or the system will fail.
            **Example:**  Flying areoplane. The pilot will fly the areoplane based on the response received from the sensors.

       2. **Soft Real time OS:**
          + In Soft Real time OS, there will not be any problem if we won't get the desired output in stipulated time.
            **Example:**  Weather forecasting.      











 

  


 









