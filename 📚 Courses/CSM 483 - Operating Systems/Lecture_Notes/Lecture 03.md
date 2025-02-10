---
course: CSM 483 - Operating Systems
date: 2025-01-27
tags:
  - lecture
  - CSM483
---
## Detailed Notes
### Processes 
![[📚 Courses/CSM 483 - Operating Systems/Lecture_Notes/Lecture 02#Process Management|Lecture 02]]

Multi parts of a process
- text section -> program code
- program counter
- stack -> contain temporary data
- data section -> containing global variables
- heap

- Program becomes an executable file when it's loaded into the memory 
#### Process state
 - New -> created process
 - Running -> executing instructions 
 - Waiting -> waiting for event to occur 
 - Ready -> waiting to be assigned to a processor 
 - Terminated -> finished execution 

A process in the new state has to be admitted into the ready state 1st. 
A scheduler dispatches the process from the ready state to running state. An interrupt sends it back.
#### Process Control Block (PCB)
- Process state
- process counter -> location of instructions to execute next.
- cpu registers
- cpu scheduling information 
- memory management information
- accounting information
- I/O status information
#### Threads
- Process has a single thread of execution.
~~INPUT GPT RESPONSE~~ 
#### Process Scheduler 
- selects among available processes for next execution on CPU core
- 2 types
	Ready queue
	Wait queue

There's an algorithm that looks at the age of the program so as the age goes up it will give it priority. (Uses the clock) - **aging** 

#### Operations on processes
##### Process creation
- parent process create children processes which in turn create other processes forming a tree of processes.
- Process identifier (pid) -> identifies and manages processes.
	Resource sharing options
	- parent & children share all resources
	- children share subset of parents resources 
	- parent and children share no resources
Execution options
- parent and children execute concurrently 
- parents waits until children terminate.
#### Process Termination 
- process finiah executing then asks the OS to delete it using the exit() system call.
	- return status data from child (via **wait()**)
- parent terminates child using the abort() system call.
- zombie -> if no parent waiting (did not invoke wait())
- orphan -> if parent Terminated without invoking wait()

#### Android process importance hierarchy **(most to least)**
- Foreground process
- visible process
- service process
- background process
- empty process

## Questions
- when does the switch happen?
	- between the save state and the reload state 