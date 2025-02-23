Questions: ![[Operating system pasco.docx]]

# Question 2
## Given Process Information

|Process|Arrival Time|Burst Time|Priority|
|:-:|:-:|:-:|:-:|
|**P1**|0 ms|8 ms|3|
|**P2**|1 ms|4 ms|1|
|**P3**|2 ms|9 ms|4|
|**P4**|3 ms|5 ms|2|
|**P5**|4 ms|2 ms|5|

> **Important Conventions**
> - Lower priority number ⇒ **Higher** priority.
> - All times are in milliseconds (ms).
> - Turnaround Time (TAT) = Completion Time − Arrival Time
> - Waiting Time (WT) = TAT − Burst Time
> - Response Time (RT) = Time from arrival until the first time the process gets the CPU (not explicitly asked for each algorithm but useful for comparisons).

---

# Part (a): Detailed Scheduling for Each Algorithm

---

## 1. First-Come, First-Served (FCFS)

1. **Order of Arrival**: P1 (t=0), then P2 (t=1), P3 (t=2), P4 (t=3), P5 (t=4).
2. **Non-Preemptive**: Once a process starts, it runs to completion before the next arrives in queue order.

**Gantt Chart**

```
 Time: 0        8       12        21      26      28
       |---P1---|---P2---|---P3---|---P4---|--P5--|
          8 ms     4 ms      9 ms     5 ms   2 ms
```

**Completion Times**

- P1 finishes at 8
- P2 finishes at 12
- P3 finishes at 21
- P4 finishes at 26
- P5 finishes at 28

**Turnaround & Waiting Times**

|Process|Arrival|Burst|Completion|TAT = Completion - Arrival|WT = TAT - Burst|
|:-:|:-:|:-:|:-:|:-:|:-:|
|P1|0|8|8|8 − 0 = 8|8 − 8 = 0|
|P2|1|4|12|12 − 1 = 11|11 − 4 = 7|
|P3|2|9|21|21 − 2 = 19|19 − 9 = 10|
|P4|3|5|26|26 − 3 = 23|23 − 5 = 18|
|P5|4|2|28|28 − 4 = 24|24 − 2 = 22|

- **Average Waiting Time (AWT)** = (0 + 7 + 10 + 18 + 22) / 5 = 57 / 5 = **11.4**
- **Average Turnaround Time (ATAT)** = (8 + 11 + 19 + 23 + 24) / 5 = 85 / 5 = **17.0**

---

## 2. Round Robin (RR) with Time Quantum = 3 ms

### Key Steps

- **Time Quantum (q)** = 3 ms.
- As soon as a process uses 3 ms (or finishes earlier), it goes to the back of the ready queue if it still needs more CPU.

**Timeline Analysis**

1. **t = 0 to 3**:
    
    - Only P1 is in the system. Runs for 3 ms (remaining burst = 8 − 3 = 5).
    - At t=1, P2 arrives; t=2, P3 arrives; t=3, P4 arrives (exactly at time 3).
2. **Ready Queue at t=3**:
    
    - P1(remaining 5), P2(4), P3(9), P4(5).
    - Next to run: P2.
3. **t = 3 to 6**:
    
    - P2 runs for 3 ms (remaining = 4 − 3 = 1).
    - At t=4, P5 arrives.
4. **Ready Queue at t=6**:
    
    - P3(9), P4(5), P1(5), P5(2), P2(1).
    - Next: P3.
5. **t = 6 to 9**:
    
    - P3 runs 3 ms (remaining = 9 − 3 = 6).
6. **t = 9 to 12**:
    
    - P4 runs 3 ms (remaining = 5 − 3 = 2).
7. **t = 12 to 15**:
    
    - P1 runs 3 ms (remaining = 5 − 3 = 2).
8. **t = 15 to 17**:
    
    - P5 needs only 2 ms total, so it finishes at t=17.
    - 1 ms of the 3-ms quantum remains (t=17 to t=18).
9. **t = 17 to 18** (still within the same 15–18 slice):
    
    - P2 (remaining = 1) finishes at t=18.
10. **t = 18 to 21**:
    
    - P3 runs next 3 ms (remaining = 6 − 3 = 3).
11. **t = 21 to 24**:
    
    - P4 runs 2 ms to finish at t=23 (remaining 0).
    - 1 ms leftover in this quantum → next is P1 (2 ms left).
    - P1 runs from t=23 to t=24 (remaining = 1).
12. **t = 24 to 25**:
    
    - P1 uses 1 ms and finishes at t=25. 2 ms remain in that quantum (24–27).
    - Next is P3 (3 ms left), so it runs from t=25 to t=27 (remaining = 1).
13. **t = 27 to 28**:
    
    - P3 finishes its last 1 ms at t=28.

**Completion Times**

- P5 = 17
- P2 = 18
- P4 = 23
- P1 = 25
- P3 = 28

**Turnaround & Waiting Times**

|Process|Arrival|Burst|Completion|TAT = C - A|WT = TAT - Burst|
|:-:|:-:|:-:|:-:|:-:|:-:|
|P1|0|8|25|25 − 0 = 25|25 − 8 = 17|
|P2|1|4|18|18 − 1 = 17|17 − 4 = 13|
|P3|2|9|28|28 − 2 = 26|26 − 9 = 17|
|P4|3|5|23|23 − 3 = 20|20 − 5 = 15|
|P5|4|2|17|17 − 4 = 13|13 − 2 = 11|

- **AWT** = (17 + 13 + 17 + 15 + 11) / 5 = 73 / 5 = **14.6**
- **ATAT** = (25 + 17 + 26 + 20 + 13) / 5 = 101 / 5 = **20.2**

---

## 3. Shortest Job First (SJF) – Non-Preemptive

### Key Steps

- At each scheduling decision, choose the **arrived process** with the smallest **burst**.
- Once a process starts, it runs to completion (no preemption).

**Timeline Analysis**

- **t = 0**: Only P1 (8 ms) is available, so P1 starts first.
- **P1** runs from 0..8. Meanwhile, P2 arrives at t=1, P3 at t=2, P4 at t=3, P5 at t=4 (all must wait).
- **t = 8**: The CPU is free. Among P2(4), P3(9), P4(5), P5(2), the shortest is **P5** (2 ms).
    - Run P5 from 8..10.
- **t = 10**: Next shortest is **P2** (4 ms) among P2, P3, P4.
    - Run P2 from 10..14.
- **t = 14**: Among P3(9) and P4(5), choose **P4**.
    - Run P4 from 14..19.
- **t = 19**: Finally, run **P3** (9 ms) from 19..28.

**Gantt Chart**

```
0---8   8--10   10--14   14--19   19------28
| P1 | | P5 | |  P2  | |  P4  | |    P3    |
```

**Completion Times**

- P1 = 8
- P5 = 10
- P2 = 14
- P4 = 19
- P3 = 28

**Turnaround & Waiting Times**

|Process|Arrival|Burst|Completion|TAT = C - A|WT = TAT - Burst|
|:-:|:-:|:-:|:-:|:-:|:-:|
|P1|0|8|8|8 − 0 = 8|8 − 8 = 0|
|P5|4|2|10|10 − 4 = 6|6 − 2 = 4|
|P2|1|4|14|14 − 1 = 13|13 − 4 = 9|
|P4|3|5|19|19 − 3 = 16|16 − 5 = 11|
|P3|2|9|28|28 − 2 = 26|26 − 9 = 17|

- **AWT** = (0 + 4 + 9 + 11 + 17) / 5 = 41 / 5 = **8.2**
- **ATAT** = (8 + 6 + 13 + 16 + 26) / 5 = 69 / 5 = **13.8**

---

## 4. Shortest Remaining Job First (SRJF) – Preemptive SJF

### Key Steps

- Always pick the process with the **shortest remaining** burst among those that have arrived.
- If a new process arrives with a shorter burst than the current, preempt.

**Timeline Analysis**

1. **t=0**: Only P1(8) is available → start P1.
2. **t=1**: P2 arrives(4). Compare P1’s remaining(7) vs. P2(4) → P2 is shorter, so preempt P1 and run P2.
3. **t=2**: P3 arrives(9). P2 has 3 left, which is still shorter than P1(7) or P3(9). Continue P2.
4. **t=3**: P4 arrives(5). P2 has 2 left, still shorter. Continue P2.
5. **t=4**: P5 arrives(2). P2 has 1 left, which is still shorter than P5(2). Continue P2.
6. **t=5**: P2 finishes. Next shortest among P1(7), P3(9), P4(5), P5(2) is **P5**(2). Run P5 from 5..7 → P5 finishes at 7.
7. **t=7**: Among P1(7), P3(9), P4(5), shortest is **P4**(5). Run P4 from 7..12 → finishes at 12.
8. **t=12**: Among P1(7), P3(9), shortest is **P1**(7). Run P1 from 12..19 → finishes at 19.
9. **t=19**: Only P3(9) remains. Run from 19..28 → finishes at 28.

**Gantt Chart (Simplified View)**

```
 0-1   1-----5   5-7   7----12   12----19   19------28
 P1   [P2 runs]  P5   P4 runs   P1 runs    P3 runs
 (8)   until 5   (2)    (5)       (7)         (9)
```

_(Exact second-by-second details show each preemption point.)_

**Completion Times**

- P2 = 5
- P5 = 7
- P4 = 12
- P1 = 19
- P3 = 28

**Turnaround & Waiting Times**

|Process|Arrival|Burst|Completion|TAT = C - A|WT = TAT - Burst|
|:-:|:-:|:-:|:-:|:-:|:-:|
|P1|0|8|19|19 − 0 = 19|19 − 8 = 11|
|P2|1|4|5|5 − 1 = 4|4 − 4 = 0|
|P3|2|9|28|28 − 2 = 26|26 − 9 = 17|
|P4|3|5|12|12 − 3 = 9|9 − 5 = 4|
|P5|4|2|7|7 − 4 = 3|3 − 2 = 1|

- **AWT** = (11 + 0 + 17 + 4 + 1) / 5 = 33 / 5 = **6.6**
- **ATAT** = (19 + 4 + 26 + 9 + 3) / 5 = 61 / 5 = **12.2**

---

## 5. Priority Scheduling (Non-Preemptive)

### Key Steps

- Lower priority number = higher priority.
- We must also respect arrival times.
- Once a process starts, it runs to completion (non-preemptive), even if a higher-priority process arrives later.

**Priorities**:

- **P2** (priority=1) is highest
- **P4** (priority=2)
- **P1** (priority=3)
- **P3** (priority=4)
- **P5** (priority=5) is lowest

**Timeline Analysis**

1. **t=0**: Only P1( priority=3 ) has arrived, so start P1 at t=0.
2. **t=1,2,3,4**: P2, P3, P4, P5 arrive, but we do **not** preempt P1 (non-preemptive). P1 runs until t=8.
3. **t=8**: CPU is free. Among the arrived (P2, P3, P4, P5), pick the **highest priority** (lowest number) = P2(1). Run P2 from 8..12.
4. **t=12**: Next highest priority is P4(2). Run from 12..17 (burst=5).
5. **t=17**: Next is P1(3) – but it’s already finished, so skip. Actually we consider the remaining: P3(4), P5(5). So P3(4) is higher than P5(5). Run P3 from 17..26 (burst=9).
6. **t=26**: Finally, P5(5) from 26..28 (burst=2).

**Gantt Chart**

```
0------8   8----12   12---17   17--------26   26--28
    P1      P2       P4         P3           P5
```

**Completion Times**

- P1 = 8
- P2 = 12
- P4 = 17
- P3 = 26
- P5 = 28

**Turnaround & Waiting Times**

|Process|Arrival|Burst|Priority|Completion|TAT = C - A|WT = TAT - Burst|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|P1|0|8|3|8|8 − 0 = 8|8 − 8 = 0|
|P2|1|4|1|12|12 − 1 = 11|11 − 4 = 7|
|P4|3|5|2|17|17 − 3 = 14|14 − 5 = 9|
|P3|2|9|4|26|26 − 2 = 24|24 − 9 = 15|
|P5|4|2|5|28|28 − 4 = 24|24 − 2 = 22|

- **AWT** = (0 + 7 + 9 + 15 + 22) / 5 = 53 / 5 = **10.6**
- **ATAT** = (8 + 11 + 14 + 24 + 24) / 5 = 81 / 5 = **16.2**

---

# Part (b): Performance Comparison

Below is a **summary table** of the average waiting time (AWT) and average turnaround time (ATAT) for each algorithm:

|**Algorithm**|**AWT**|**ATAT**|
|:--|:-:|:-:|
|**FCFS**|11.4|17.0|
|**Round Robin (q=3)**|14.6|20.2|
|**SJF (Non-Preempt)**|8.2|13.8|
|**SRJF (Preemptive)**|6.6|12.2|
|**Priority (Non-Preempt)**|10.6|16.2|

### Observations

1. **Waiting Time & Turnaround Time**
    - **SRJF (Shortest Remaining Job First)** yields the lowest average waiting and turnaround times overall, because it dynamically gives preference to the shortest remaining burst.
    - **SJF** (non-preemptive) is the second best in terms of these metrics, but it can’t preempt if a new, shorter process arrives mid-execution.
    - **FCFS** and **Priority** are somewhere in the middle, with **Round Robin** showing a higher waiting time in this particular example (due to the overhead of frequent context switches and time-slicing).
    
2. **Response Time**
    - **Round Robin** typically offers better **response time** for each process (it quickly gives each process some CPU time), but at the cost of more context switches, which can inflate waiting/turnaround times.
    - **SRJF** also can yield good response times for short jobs, since they often preempt longer jobs.

3. **Starvation**
    - **Priority Scheduling** (non-preemptive) can cause starvation for lower-priority processes if higher-priority processes keep arriving.
    - **FCFS** avoids starvation but can penalize short jobs arriving behind very long ones.

---

# Question 5:

**What is a long-term scheduler?**
	  The long-term scheduler (also known as the admission scheduler) decides which processes from the job pool are admitted into the system (i.e., loaded into main memory) for execution.

# Question 6:

**What is a short-term scheduler?**
	The short-term scheduler (or CPU scheduler) selects from the processes that are ready to execute, deciding which one should be given the CPU next.

# Question 8:

**What is the difference between blocking and non-blocking communication?**
- **Blocking Communication**:
    - In blocking communication, a process that issues a send or receive operation waits (blocks) until the operation completes.
    - The process remains idle until the data is transmitted or received.
- **Non-Blocking Communication**:
    - In non-blocking communication, a process initiates the send or receive operation and continues executing without waiting for the operation to finish.
    - The process can later check (or be notified) whether the communication has completed, allowing for better overlap of computation and communication.