---
date: 2025-02-23
course: CSM 483 - Operating Systems
tags:
  - personal
  - study
  - CSM483
---

## **Overview**

#### **Basic Concepts (CPU–I/O Burst Cycle)**

![[Pasted image 20250223141504.png]]

- **CPU and I/O Bursts**: A process alternates between CPU bursts (doing computations) and I/O bursts (waiting for I/O).
- **Goal**: Maximize CPU utilization by overlapping CPU bursts of one process with I/O bursts of another.

#### **Histogram of CPU-Burst Times**

![[Pasted image 20250223141528.png]]

- **Typical Distribution**: Many short CPU bursts and only a few long ones.
- **Implication**: Scheduling algorithms often cater to the large number of short bursts for efficiency and responsiveness.

#### **CPU Scheduler**

- **Role**: Chooses which process in the ready queue should execute next.
- **Scheduling Decisions** occur when a process:
    1. Switches from running to waiting (e.g., I/O request).
    2. Switches from running to ready (e.g., time slice expires).
    3. Switches from waiting to ready (I/O completes).
    4. Terminates.
- **No Choice vs. Choice**:
    - In situations (1) and (4), there’s no scheduling choice—another process **must** run.
    - In (2) and (3), the scheduler **chooses** which ready process runs next.

#### **Preemptive and Nonpreemptive Scheduling**

- **Nonpreemptive**: Once a process is given the CPU, it keeps it until it either terminates or switches to waiting.
- **Preemptive**: The OS can forcibly take the CPU away (e.g., after a time slice or higher-priority process arrival).
- **Modern OSes**: Typically use preemptive scheduling for better responsiveness.

#### **Preemptive Scheduling and Race Conditions**

- **Risk**: When processes share data, a preempted process may leave shared data in an inconsistent state. Another process could read/update that data incorrectly.
- **Solution**: Proper synchronization (e.g., locks, semaphores) to prevent data corruption.

#### **Dispatcher**

![[Pasted image 20250223142322.png]]

- **Definition**: The dispatcher hands over control of the CPU to the process selected by the scheduler.
- **Tasks**:
    1. Perform context switch (save state of old process, load state of new).
    2. Switch to user mode.
    3. Jump to the correct location in the user program.
- **Dispatch Latency**: The time it takes to stop one process and start another.

#### **Scheduling Criteria**

1. **CPU Utilization**: Keep the CPU as busy as possible.
2. **Throughput**: Number of processes completed per time unit.
3. **Turnaround Time**: Total time from process submission to completion.
4. **Waiting Time**: Time a process spends in the ready queue.
5. **Response Time**: Time from request submission until the first response is produced.

#### **Scheduling Algorithm Optimization Criteria**

- **Max CPU Utilization**: Keep the CPU as busy as possible.
- **Max Throughput**: Complete the highest number of processes per time unit.
- **Min Turnaround Time**: Reduce the total time from process submission to completion.
- **Min Waiting Time**: Decrease the time a process spends in the ready queue.
- **Min Response Time**: Shorten the delay from when a request is made until the first response is produced.

#### **First-Come, First-Served (FCFS) Scheduling**

**Basic Idea**
- Processes are scheduled in the order they arrive (the “first in, first out” principle).

**Convoy Effect**: Short processes get stuck waiting behind a very long CPU-bound process, increasing average waiting time.

![[Pasted image 20250223160708.png]]

#### **Shortest-Job-First (SJF) Scheduling**

**Concept**
- Schedule the process with the shortest next CPU burst time first.
- **Optimal** in terms of minimizing the average waiting time for a given set of processes.

**Variants**
- **Preemptive**: Shortest-Remaining-Time-First (SRTF) — if a new process arrives with a shorter burst, it preempts the current process.
- **Challenge**: Estimating the length of the next CPU burst (could ask the user, or guess based on past behavior).

![[Pasted image 20250223161151.png]]

**Waiting Times**:
- $P_4 = 0$ (starts immediately),
- $P_1 = 3$,
- $P_3 = 9$,
- $P_2 = 16$.

**Key Point**:
- SJF can significantly reduce average waiting time compared to FCFS, but requires an accurate prediction or estimate of CPU burst lengths.

#### **Determining Length of Next CPU Burst**

- **Estimation**
    - We can’t know the next CPU burst length exactly; instead, we **predict** it based on previous bursts.
    - **Exponential Averaging**:  $\tau_{n+1} = \alpha \cdot t_n + (1 - \alpha) \cdot \tau_n$​
        - $\tau_{n+1}$​: Predicted burst for the (n+1)-th CPU burst.
        - $t_n$​: Actual length of the n-th CPU burst.
        - $\tau_n$​: Previously predicted burst length.
        - $\alpha$: Weight (often set to 0.5).
- **Key Point**: This formula helps the scheduler guess the next CPU burst time and prioritize processes accordingly (especially in SJF or SRTF).

![[Pasted image 20250223162556.png]]


#### **Shortest Remaining Time First (SRTF) Scheduling**

- **Preemptive Version of SJF**
    - Whenever a new process arrives, the scheduler compares its burst time to the remaining time of the currently running process.
    - If the new process has a shorter burst, it preempts the current one.
    
- **Optimality**
    - In terms of **minimizing average waiting time**, SRTF can be even better than non-preemptive SJF, because it adapts to new arrivals.
    
    ![[Pasted image 20250223162748.png]]

#### **Round Robin (RR)**

- **Time Quantum (q)**
    - Each process gets a small, fixed slice of CPU time (e.g., 10–100 ms).
    - After q elapses, the process is preempted and placed at the back of the ready queue.

- **Performance**
    - If **q is large**, RR behaves like FCFS (long time slice).
    - If **q is too small**, context-switch overhead becomes significant.

- **Key Point**: RR improves **response time** for all processes (no one is starved for CPU), but might increase overhead if the time quantum is too short.

![[Pasted image 20250223163248.png]]

Quantum = 4

**Trade-off**
- **Better Response** than SJF, because every process gets CPU time fairly quickly.
- Potentially **higher Turnaround** than SJF, especially if a process has a large burst and gets sliced repeatedly.

##### Calculating the Average waiting time

![[Pasted image 20250223172514.png]]

#### **Time Quantum and Context Switch Time**

![[Pasted image 20250223163936.png]]

- If $q = 12$ for a process needing 10 units of CPU time, there are **0** context switches (the process runs uninterrupted).
	- If $q = 6$, the process will be preempted once, leading to **1** context switch.
	- If $q = 1$, there will be many context switches (9 in this example), significantly increasing overhead.

- **Key Point**:
    - **Larger Quantum** → Fewer context switches but potentially poorer response time for other processes.
    - **Smaller Quantum** → Better responsiveness but increased context-switch overhead.

#### **Turnaround Time Varies with the Time Quantum**

![[Pasted image 20250223164304.png]]

- **80% Rule**: A common heuristic is to choose $q$ so that **80% of CPU bursts** are shorter than $q$. This helps most bursts finish in one time slice, minimizing context switches.

- **Key Point**:
    - There is a **sweet spot** where $q$ is large enough to avoid excessive context switching, yet small enough to provide good responsiveness.

#### **Priority Scheduling**

- **Definition**: Each process has a priority number (often an integer). The CPU is allocated to the process with the **highest priority**.

- **Preemptive vs. Nonpreemptive**:
    - **Preemptive**: A new, higher-priority process can interrupt a running lower-priority process.
    - **Nonpreemptive**: Once a process starts, it continues until it completes or yields the CPU.

- **SJF Connection**: Shortest Job First (SJF) is effectively **priority scheduling** where the “priority” is the **predicted CPU burst time** (shorter burst = higher priority).

- **Starvation Problem**: Low-priority processes may never run if higher-priority processes keep arriving.

- **Solution (Aging)**: Increase a process’s priority the longer it waits, preventing indefinite starvation.

![[Pasted image 20250223165056.png]]

#### **Priority Scheduling with Round-Robin**

![[Pasted image 20250223165738.png]]

**Tie-Breaking**: If multiple processes share the **same priority**, they can be scheduled **round-robin** among themselves.

#### **Multilevel Queue**

- **Multiple Queues**: The ready queue is split into several separate queues.
- **Parameters**:
    1. **Number of queues**
    2. **Scheduling algorithm** for each queue (e.g., FCFS, Round Robin, Priority Scheduling)
    3. **Queue assignment policy** (how a process is placed into a specific queue)
    4. **Scheduling among queues** (e.g., strict priority between queues or time-slice across queues)
- **Separate Queues per Priority**: Processes with higher priority go into higher-priority queues and are scheduled first.
- **Example**:
    - **Priority = 0**: Highest-priority queue
    - **Priority = n**: Lowest-priority queue
- **Scheduling**: Always pick from the highest-priority (non-empty) queue.

![[Pasted image 20250223173005.png]]

![[Pasted image 20250223173046.png]]

**Queue Assignment** can be based on **process type**:
- **Real-time processes** (highest priority)
- **System processes**
- **Interactive processes**
- **Batch processes** (lowest priority)

#### **Multilevel Feedback Queue**

- **Key Difference**: A process **can move** between queues.
- **Parameters**:
    1. **Number of queues**
    2. **Scheduling algorithm** for each queue
    3. **Method** to upgrade a process to a higher-priority queue
    4. **Method** to demote a process to a lower-priority queue
    5. **Aging**: Prevents starvation by gradually increasing a waiting process’s priority
- **Purpose**: Adapt to a process’s behavior over time. CPU-bound processes eventually get demoted; short or interactive tasks remain in higher-priority queues.

![[Pasted image 20250223173244.png]]

- **Three Queues**:
    1. **Q₀**: Round Robin with 8 ms time quantum
    2. **Q₁**: Round Robin with 16 ms time quantum
    3. **Q₂**: FCFS (no time quantum)
- **Scheduling Flow**:
    - New processes start in **Q₀** with the smallest quantum (8 ms).
    - If a process **uses** its entire 8 ms slice without finishing, it moves down to **Q₁** (time quantum 16 ms).
    - If it still doesn’t finish, it is moved to **Q₂** (FCFS).

- **Multilevel Queue** scheduling is a static partition of processes into different queues (no movement between queues).
- **Multilevel Feedback Queue** scheduling is dynamic, allowing processes to change queues based on their execution characteristics, thus balancing responsiveness and throughput while avoiding starvation.

#### **Thread Scheduling**

- **User-Level vs. Kernel-Level Threads**:
    - **User-Level Threads** are managed by a thread library within a single process; scheduling is invisible to the OS.
    - **Kernel-Level Threads** are managed directly by the operating system.

- **Scheduling Focus**: Modern systems typically schedule **threads**, not processes.
- **Process-Contention Scope (PCS)**: Thread scheduling occurs **within** the process (e.g., user-level library scheduling).
- **System-Contention Scope (SCS)**: The kernel schedules threads across the entire system, competing for CPU time.

#### **Difference Between a Thread and a Process**

| **Feature**       | **Process**                                                                 | **Thread**                                                                                    |
| ----------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| **Definition**    | An independent program in execution, with its own memory space & resources. | A lightweight unit within a process, sharing code, data, and resources of the parent process. |
| **Memory**        | Has a private address space (code, data, stack).                            | Shares memory (code, data, heap) but has its own stack.                                       |
| **Communication** | Requires Inter-Process Communication (pipes, sockets, shared memory).       | Directly communicates via shared memory within the same process.                              |
| **Overhead**      | Higher overhead (context switching between processes is more expensive).    | Lower overhead (switching between threads is typically faster).                               |
| **Creation Time** | Slower (new address space needed).                                          | Faster (shares the parent’s address space).                                                   |
| **Crash Impact**  | If one process crashes, it typically does not affect others.                | A thread crash can potentially bring down the entire process.                                 |
| **Examples**      | Opening a new browser or running a new database server.                     | Multiple tabs in the same browser, parallel tasks in one application.                         |

#### **Multiple-Processor Scheduling**

- **Complexity**: Scheduling becomes more complicated when multiple CPUs or cores are available.
- **Possible Architectures**:
    - **Multicore CPUs** (multiple cores on a single chip)
    - **Multithreaded Cores** (each core can handle multiple hardware threads)
    - **NUMA Systems** (Non-Uniform Memory Access)
    - **Heterogeneous Multiprocessing** (different types of cores in the same system)

- **Symmetric Multiprocessing (SMP)**:
    - Each processor is self-scheduling, either from a **common ready queue** or with **per-core queues**.
    - All threads may be placed in the same pool, or each core has its own queue.
![[Pasted image 20250223174256.png]]

#### **Multicore Processors**

- **Multiple Cores on One Chip**: Modern processors combine multiple cores on a single physical chip for higher performance and lower power consumption.
- **Growing Thread Support**: Each core can run multiple threads, allowing one thread to continue work while another is stalled on a memory access.

![[Pasted image 20250223174709.png]]

#### **Multithreaded Multicore System**

- **Hardware Threads per Core**: Each core can support more than one hardware thread.
- **Switch on Stall**: If one hardware thread encounters a memory stall, the core can switch to another thread that’s ready to run. This improves overall CPU utilization.

![[Pasted image 20250223174739.png]]

#### **Chip-Multithreading (CMT) / Hyper-Threading**

- **CMT**: Assigns multiple hardware threads to each core.
- **Example**: On a quad-core CPU with 2 hardware threads per core, the operating system sees 8 “logical processors.”
- **OS View**: The OS schedules software threads onto these logical processors.

![[Pasted image 20250223174900.png]]

#### **Two Levels of Scheduling**

1. **Level 1 (OS Level)**: The operating system decides which software thread to assign to each logical CPU.
2. **Level 2 (Core Level)**: The hardware (each core) decides which hardware thread to run at any given moment, often switching on memory stalls or other events.

![[Pasted image 20250223174933.png]]

#### **Multiple-Processor Scheduling – Load Balancing**

- **Goal**: Keep all CPUs or cores as busy as possible in a Symmetric Multiprocessing (SMP) system.
- **Push Migration**: A load balancer periodically checks for imbalances and **pushes** tasks from an overloaded CPU to a less busy one.
- **Pull Migration**: An **idle** CPU looks for tasks on a busy CPU and **pulls** them over.

#### **Multiple-Processor Scheduling – Processor Affinity**

- **Processor Affinity**: A thread that has been running on a particular processor benefits from that processor’s cache contents (hot cache).
- **Soft Affinity**: The OS tries to keep a thread on the same processor, but it’s not guaranteed.
- **Hard Affinity**: A process can explicitly specify the set of processors on which it can run, restricting migration.

#### **NUMA and CPU Scheduling**

- **Non-Uniform Memory Access (NUMA)**: Each CPU (or group of CPUs) has its own local memory, which it can access faster than memory connected to other CPUs.
- **NUMA-Aware OS**:
    - Tries to schedule threads on the CPU whose local memory holds the data.
    - Improves performance by reducing access times (avoiding “remote” memory access).
- **Key Benefit**: Better cache locality and lower memory latency for processes that stay near their allocated memory.

#### **Real-Time CPU Scheduling**

- **Soft Real-Time Systems**:
    - Critical real-time tasks have higher priority.
    - There is no strict guarantee they will always meet deadlines, but the system attempts to prioritize them.
- **Hard Real-Time Systems**:
    - Tasks must be serviced within their deadlines.
    - The OS must guarantee that critical tasks always receive enough CPU time to complete on schedule.












## **Key Concepts**

- **Context switch overhead** refers to the extra time and resources required by the operating system to switch the CPU from executing one process (or thread) to another.
- **Overhead** refers to the extra time, memory, or other resources that are consumed by a process, function, or system in addition to the primary work being performed.

## **References**

-
