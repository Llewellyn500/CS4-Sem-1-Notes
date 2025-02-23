---
date: 2025-02-23
course: CSM 483 - Operating Systems
tags:
  - personal
  - study
  - CSM483
---

## **Overview**

#### **Process Concept**

- **Definition**: A process is a program in execution, meaning the program code is actively running on the CPU.
- **Components of a Process**:
    - **Text Section**: The program code (instructions).
    - **Program Counter**: Indicates the next instruction to execute.
    - **Stack**: Holds temporary data (function parameters, return addresses, local variables).
    - **Data Section**: Contains global variables.
    - **Heap**: Dynamically allocated memory at runtime.
    - **Program vs. Process**:
	    - **Program** is a passive entity (executable file on disk).
	    - **Process** is the active entity in memory.
- **Execution Start**: A program becomes a process when it is loaded into memory for execution (e.g., via GUI click, command-line command).
- **Multiple Instances**: The same program can be run multiple times, creating separate processes.

#### **Process In Memory**

![[Pasted image 20250223121850.png]]

- **Memory Layout** (typical structure for a process):
    - **Text** (lowest addresses)
    - **Data** (global variables)
    - **Heap** (grows upward for dynamic allocation)
    - **Stack** (grows downward for function calls, local variables)
- **Address Range**: The process stack starts near the top of the process’s allocated memory, and the text section sits at the bottom.

#### **Memory Layout of a C Program**

![[Pasted image 20250223122044.png]]

- **Sections**:
    - **Text**: Compiled program instructions.
    - **Initialized Data**: Global/static variables with initial values.
    - **Uninitialized Data (BSS)**: Global/static variables without initial values.
    - **Heap**: Dynamically allocated data (e.g., `malloc` in C).
    - **Stack**: Local variables, function parameters, return addresses.
- **High vs. Low Memory**: Typically, the stack is near the top of the process’s address space, while text is at the lower addresses.

#### **Process State**

- **New**: The process is being created.
- **Running**: The process’s instructions are being executed on the CPU.
- **Waiting**: The process is waiting for some event (e.g., I/O completion).
- **Ready**: The process is ready to be assigned to a CPU.
- **Terminated**: The process has finished execution.

![[Pasted image 20250223122140.png]]

**State Transitions**:
    - **new → ready** (admission)
    - **ready → running** (scheduler dispatch)
    - **running → waiting** (I/O or event wait)
    - **running → ready** (interrupt or time slice)
    - **waiting → ready** (I/O completes)
    - **running → terminated** (exit)

#### **Process Control Block (PCB)**

![[Pasted image 20250223122235.png]]

- **Purpose**: Data structure that holds all the information needed to manage a process. Also known as a **task control block**.
- **Contents**:
    1. **Process State** (new, ready, running, waiting, terminated).
    2. **Process Number** (ID).
    3. **Program Counter** (next instruction address).
    4. **CPU Registers** (contents saved/restored during context switches).
    5. **CPU Scheduling Information** (priority, scheduling queue pointers).
    6. **Memory-Management Information** (page tables, segment tables).
    7. **Accounting Information** (CPU time used, process creation time).
    8. **I/O Status** (list of open files, I/O devices in use).

#### **Threads**

**Definition**:  
A thread is a lightweight process that shares the same memory space and resources (like open files) with other threads within the same process.

- **Multiple Threads of Execution**
    - Traditionally, each process has a single thread (one program counter).
    - Modern systems allow **multiple threads** within the same process, each with its own program counter.
    
- **Storage of Thread Details**
    - The OS must store thread-specific data (e.g., registers, stack) and manage multiple program counters within a single process.

**Key Point**: Threads enable concurrency within a process, allowing multiple parts of the same program to run in parallel.

**Benefits**:

- **Concurrency**: Threads allow a program to perform multiple tasks at once, such as handling user input, performing background computations, or managing I/O operations concurrently.
- **Responsiveness**: In user interfaces, for example, one thread can handle the UI while another performs time-consuming operations, keeping the application responsive.
- **Efficient Resource Use**: Since threads share the same memory space, creating a new thread is generally less resource-intensive than creating a new process.

#### **Process Scheduling**

- **Purpose of the Scheduler**
    - Selects among available processes (or threads) for next CPU execution.
    - **Goal**: Maximize CPU utilization and quickly switch processes on the CPU core.
    
- **Scheduling Queues*
![[Pasted image 20250223124340.png]]

- **Ready Queue**
	- Processes that are in memory, ready, and waiting for CPU time.
    - Organized typically as a linked list of PCBs, with head and tail pointers for efficient enqueue/dequeue.
- **Wait Queue**
	- Processes waiting for an event (e.g., I/O completion).
    - Processes that are blocked or waiting on an event are linked in a similar queue structure.

##### Representation of Process Scheduling

![[Pasted image 20250223124605.png]]

- **State Transitions**
    - Processes move from **ready** to **running** when scheduled, from **running** to **waiting** if they request I/O, and back to **ready** when I/O completes.
    - A time slice expiration can also move a running process back to ready.
- **Other Events**
    - **Child termination** can place the parent process in a wait queue (if it’s waiting for the child to finish).
    - **Interrupts** can preempt the running process.

**Key Point**: The OS manages complex transitions between states, ensuring processes receive CPU time and handle I/O or other events correctly.

#### **CPU Switch From Process to Process**

![[Pasted image 20250223124717.png]]

- **Context Switch**
    - Occurs whenever the CPU switches from one process (P₀) to another (P₁).
    - Involves saving the current process state into its PCB and loading the next process’s state from its PCB.

**Key Point**: Context switches are overhead; no useful work is done during the switch itself, but they are essential for multitasking and process isolation.

#### **Context Switch**

- **Saving & Restoring State**
    - The old process’s register set and program counter are saved.
    - The new process’s register set and program counter are loaded.
- **Performance Impact**
    - The complexity of the OS and the PCB size can affect how long a context switch takes.
    - Some hardware provides support (e.g., multiple register sets) to speed up switching.

**Key Point**: The OS aims to minimize context switch overhead while still ensuring fair and responsive scheduling.

#### **Multitasking in Mobile Systems**

- **Constraints**
    - Early mobile OSes (like older iOS) often limited true multitasking to a single foreground process, with background processes severely restricted.
    
- **Foreground vs. Background**
    - **Foreground** process has direct user interaction (UI).
    - **Background** processes may handle tasks like music playback, notifications, etc.
    - Android allows more flexible multitasking than older iOS but still enforces limits to conserve battery and manage resources.

**Key Point**: Mobile OSes often impose stricter rules on background processes to optimize battery life and user experience given limited screen size and power constraints.

#### **Operations on Processes**

- **Process Creation**
    - The OS provides mechanisms (e.g., `fork()` in Unix, `CreateProcess()` in Windows) to create new processes.
    - **Parent-Child Relationship**
	    - A **parent** process creates one or more **child** processes, forming a **process tree**.
    - Processes are uniquely identified by a **process identifier (PID)**.
	- **Resource Sharing Options**
	    1. **Share All**: Parent and child share all resources.
	    2. **Share Some**: Child shares a subset of the parent’s resources.
	    3. **Share None**: Parent and child share no resources.
	- **Execution Options**
	    1. **Concurrent**: Parent and child execute simultaneously.
	    2. **Parent Waits**: Parent waits until the child terminates before resuming.

- **Process Termination**
    - Processes can terminate normally (exit) or be terminated by the OS or another process (kill).
    - **Exit System Call**
	    - When a process finishes execution, it calls `exit()`, returning a status to the parent.
    - The OS then deallocates the process’s resources.
	- **Parent Terminating a Child**
	    - A parent may terminate a child (using `abort()`) if:
	        - The child has exceeded allocated resources.
	        - The child’s task is no longer required.
	        - The parent itself is exiting and does not allow the child to continue.
	- **Cascading Termination**
	    - Some OSes automatically terminate children (and further descendants) if the parent terminates.
	- **States After Termination**
	    - **Zombie**: A child has terminated, but the parent has not yet called `wait()`.
	    - **Orphan**: A child continues running even though the parent has terminated (without calling `wait()`).

#### **Android Process Importance Hierarchy**

- **Process Priorities**
    - Android may terminate processes to free memory, prioritizing from **most** to **least** important:
        1. **Foreground Process**
        2. **Visible Process**
        3. **Service Process**
        4. **Background Process**
        5. **Empty Process**
    
- **Termination Strategy**
    - Android starts killing processes that are the least important when resources become constrained.

#### **Multiprocessor Architecture - Chrome Browser**

- **Older Browsers**
    - Typically ran as a **single process**, meaning a single crash could bring down the entire browser.
    
- **Chrome’s Multiprocessor Model**
    1. **Browser Process**: Manages UI, disk access, and network I/O.
    2. **Renderer Process**: Handles rendering of web pages (HTML, JavaScript). Runs in a **sandbox** for security.
    3. **Plug-in Process**: Each plug-in runs in its own process to isolate failures or security issues.
    
- **Benefits**
    - **Stability**: A crash in one renderer or plug-in does not crash the whole browser.
    - **Security**: Sandboxing reduces the impact of malicious or buggy code.
![[Pasted image 20250223130651.png]]









## **Key Concepts**

- **Process vs. Program**
    - **Program**: A static executable file on disk.
    - **Process**: A program in execution with its own memory, CPU state, and resources.
    
- **Process Components**
    - **Text Section**: The code/instructions.
    - **Data Section**: Global variables (initialized/uninitialized).
    - **Heap**: Dynamically allocated memory.
    - **Stack**: Local variables, function calls, and return addresses.
    - **Program Counter**: Tracks the next instruction.
    
- **Memory Layout**
    - Memory is divided into sections: text (low), data, heap (grows upward), and stack (grows downward).
    
- **Process States**
    - **New**: Being created.
    - **Ready**: Waiting for CPU.
    - **Running**: Actively executing.
    - **Waiting**: Paused, awaiting an event/I-O.
    - **Terminated**: Finished execution.

- **Process Control Block (PCB)**
    - A data structure storing all process info (state, PID, registers, memory management, I/O status).
    
- **Threads**
    - Lightweight processes within a process; share memory/resources but have their own stack and program counter.
    - Enable concurrent execution (improves responsiveness and efficiency).
    
- **Process Scheduling**
    - The scheduler manages **ready** and **waiting** queues.
    - It decides which process runs next (using methods like round-robin or priority scheduling).
    
- **Context Switching**
    - The process of saving one process’s state and loading another’s.
    - Involves overhead, so minimizing switches is key.
    
- **Mobile Systems & Multitasking**
    - Mobile OSes often limit background tasks to save power, giving higher priority to foreground apps.
    
- **Process Operations**
    - **Creation**: Using system calls (e.g., fork, Create Process).
    - **Termination**: Exiting normally or being killed; can lead to zombie or orphan processes.
    
- **Special Cases**
    - **Android Process Hierarchy**: Prioritizes processes (foreground > visible > service > background > empty).
    - **Multiprocess Architecture (Chrome Browser)**: Separates browser, renderer, and plug-in processes for better stability and security.

## **References**

![[ch3 updated.pptx]]