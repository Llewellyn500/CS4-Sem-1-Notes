---
course: CSM 483 - Operating Systems
date: 2025-02-10
tags:
  - lecture
  - CSM483
---
## Detailed Notes

#### First come, first served (FCFS) Scheduling

| Process | Bus time |
| ------- | -------- |
| $P_1$   | 24       |
| $P_2$   | 3        |
| $P_3$   | 3        |

waiting time -> $P_1 = 0$, $P_2 = 24$, $P_3 = 27$
Average waiting time -> $(0+24+27)/3 = 17$ 

#### shortest-job first (SJF) scheduling

- It's optimal -> it gives minimum wait time for a given process
- It takes the process with the lowest bus time first before thinking of the rest.

#### Shortest remaining time first scheduling

- primitive version of SJF
- uses SJF whenever a new process joins the ready queue. 

| Process | Arrival time | Burst time |
| ------- | ------------ | ---------- |
| $P_1$   | 0            | 8          |
| $P_2$   | 1            | 4          |
| $P_3$   | 2            | 9          |
| $P_4$   | 3            | 5          |

Average waiting time = $[(10-1)+(1-1)+(17-2)+(5-3)]/4 = 26/4 = 6.5$

until a process entered the queue you can't know the burst time. 

#### Round Robin (RR)

- each process gets a small unit of CPU time (**time quantum** q), usually 10 - 100 milliseconds. After this time has elapsed, the process is preempted and added to the end if the ready queue. 
- No process waits more than (n-1)q time units
- Note that q mist be large with respect to context switch, otherwise overhead is too high.
- performance 
	- q large -> SJF
	- q small -> RR

#### Priority Scheduling 


## Questions
- 

## Summary
- 

## Homework Assignments
-