---
date: 2025-02-10
course: CSM 483 - Operating Systems
tags:
  - personal
  - study
  - CSM483
---
## **Overview**

-

## **Key Concepts**

- **Operating System** is a program that acts as an intermediary between a user of a computer and the computer hardware.
- Computer system components:
	- **Hardware** -> Provides basic computing resources
	- **Operating System** -> Controls and coordinates the use of hardware among various applications and users
	- **Application programs** -> define the ways in which the system resources are used to solve the computing problems of the users
	- **Users** -> People, machines, other computers
	![[Pasted image 20250210155821.png]]

#### **What Operating Systems Do**

- Its a **resource allocator** and **control program** making efficient use of HW(Hardware) and managing execution of user programs.
- An OS is **Interrupt Driven**
- **Kernel** -> The program running at all times on the computer
- **System Program** -> Ships with the OS, but not part of the kernel
- **Application Program** -> all programs not associated with the OS
- **Middleware** -> A set of software frameworks that provide additional services to application developers such as databases, multimedia, graphics.

#### **Overview of Computer System Structure**

- One or more CPUs, device controllers connect through common bus providing access to shared memory.
 ![[Pasted image 20250210160904.png]]
- I/O devices and the CPU can execute concurrently
- Each device controller is in charge of a particular device type
- Each device controller has a local buffer
- Each device controller type has an operating system device driver to manage it
- CPU moves data from/to main memory to/from local buffers
- I/O is from the device to local buffer of controller
- Device controller informs CPU that it has finished its operation by causing an interrupt

Interrupts transfers control to the interrupt service routine generally, through the interrupt vector, which contains the addresses of all the service routines

A trap or exception is a software-generated interrupt caused either by an error or a user request

#### **Interrupt Timeline**

![[Pasted image 20250210161319.png]]

This diagram represents the **interrupt timeline**, showing how the CPU and I/O devices interact during interrupt handling.

##### **Simplified Explanation:**

1. **I/O Request**:
    
    - The CPU (running a user program) sends a request to an I/O device to perform a task (e.g., read/write data).
2. **I/O Device Transfers Data**:
    
    - The I/O device begins its task (e.g., transferring data) while the CPU continues processing other tasks or programs. The device operates independently during this time.
3. **Interrupt Signal**:
    
    - Once the I/O device finishes its task, it sends an **interrupt signal** to the CPU to inform it that the transfer is complete.
4. **Interrupt Handling**:
    
    - The CPU pauses its current task and executes the **Interrupt Service Routine (ISR)** to process the I/O completion.
    - After handling the interrupt, the CPU resumes the user program.

##### **Key Points:**

- The **gray areas** show when the CPU is busy with I/O interrupt processing.
- The **green line** shows the state of the I/O device, alternating between idle and transferring.
- Multiple I/O requests and interrupts can occur, with the CPU handling them one at a time.

This timeline illustrates the efficient use of resources: while the I/O device works, the CPU continues executing other tasks, maximizing performance.

##### **Interrupt-drive I/O Cycle**

![[Pasted image 20250210161407.png]]

- Two methods for handling I/O
	- After I/O starts, control returns to user program only upon I/O completion
	- After I/O starts, control returns to user program without waiting for I/O completion
	
 **Synchronous I/O** (Waits for completion):
- CPU idles or waits for the I/O to finish:
    - **Wait instruction**: CPU remains idle until the next interrupt.
    - **Wait loop**: CPU keeps checking for I/O completion (contends for memory access).
- Only one I/O request is processed at a time (no simultaneous I/O).
**Asynchronous I/O** (Does not wait for completion):
- **System call**: Program requests the OS to handle I/O and notify upon completion.
- **Device-status table**:
    - Tracks all I/O devices (type, address, and state).
    - OS uses it to check device status and update when an interrupt occurs.

#### **Storage Structure**

- **Main Memory (RAM) ->** Storage media that the CPU accesses directly
	- Volatile
	- Typically Random-access memory in the form of Dynamic Random-access Memory (DRAM)
- **Secondary Storage ->** Large nonvolatile storage capacity
- **Hard Disk Drives (HDD) ->** Made of rigid metal or glass platters coated with magnetic recording material.
	- **Logical Structure**:
	    - Disk surface is divided into **tracks**.
	    - Tracks are further subdivided into **sectors**.
	- **Disk Controller**: Manages the logical interaction between the disk and the computer.
- **Non-volatile memory (NVM) ->** NVM devices are faster than hard disks and retain data without power.
	- **Technologies**: Includes various advanced technologies.
	- **Trends**:
	    - Increasing capacity and performance.
	    - Decreasing prices, making NVM more popular.
#### **Storage Notations and Definitions**

1. **Basic Unit**:
    - **Bit**: The smallest unit of storage, representing either **0** or **1**.
    - Collections of bits can represent numbers, letters, images, videos, sounds, and programs.
2. **Bytes and Words**:
    - **Byte**: Consists of **8 bits** and is the smallest practical storage unit in most computers.
    - **Word**: The native unit of data for a computer, typically made up of multiple bytes. For example:
        - A 64-bit computer has words of **8 bytes (64 bits)**.
3. **Storage Measurement**:
    - Data storage and throughput are measured in **bytes** and their multiples:
        - **Kilobyte (KB)**: 1,024 bytes.
        - **Megabyte (MB)**: 1,024² bytes.
        - **Gigabyte (GB)**: 1,024³ bytes.
        - **Terabyte (TB)**: 1,024⁴ bytes.
        - **Petabyte (PB)**: 1,024⁵ bytes.
    - Manufacturers often approximate:
        - 1 MB ≈ 1 million bytes.
        - 1 GB ≈ 1 billion bytes.
4. **Networking Exception**:
    - Networking speeds are measured in **bits**, as networks transmit data one bit at a time.

This structure ensures clarity in how data is represented, stored, and transmitted across computing and networking systems.

#### **Storage Hierarchy**

- **Caching ->** Copying information into faster storage systems.
- **Device Driver ->** Provides uniform interface between controller and kernel

![[Pasted image 20250210235628.png]]

#### **How a Modern Computer Works**

![[Pasted image 20250210235703.png]]

This diagram illustrates the interactions between the **CPU**, **memory**, and **I/O devices** during data processing and communication.

##### **Key Components and Their Roles:**

1. **CPU**:
    
    - Contains threads of execution responsible for processing instructions.
    - Includes a **cache** for temporary storage of frequently accessed data.
2. **Memory:**
    
    - Stores **instructions and data** used by the CPU for processing.
    - Facilitates **data movement** between memory and the CPU during the **instruction execution cycle**.
3. **I/O Devices:**
    
    - Represent external devices (e.g., disks, keyboards, printers).
    - Communicate with the CPU through:
        - **I/O Requests**: Sent by the CPU to initiate an I/O operation.
        - **Data Transfer**: Data flows between the device and the CPU or memory.
        - **Interrupts**: Signals from the device to notify the CPU of completion or errors.
4. **DMA (Direct Memory Access):**
    
    - Allows I/O devices to transfer data directly to/from memory without CPU intervention.
    - Frees the CPU to focus on other tasks while data is moved independently.

##### **Key Processes:**

5. The **CPU** executes the **instruction execution cycle** by fetching and processing data from memory.
6. I/O devices communicate with the CPU for data transfer or when attention is needed (via interrupts).
7. **DMA** handles large data transfers efficiently by bypassing the CPU, improving overall performance.

##### **Summary:**

This system demonstrates how the CPU, memory, and I/O devices work together, with the use of interrupts and DMA to manage resources efficiently while maximizing processing speed.

#### **Direct Memory Access (DMA)**

DMA is an efficient method for transferring data from high-speed I/O devices, as it reduces CPU involvement and the number of interrupts, making data transfers faster and less resource-intensive.

#### **Operating-System Operations**

- **Bootstrap program ->** A small simple code that initialize the system and load the OS kernel into memory.
- **Kernel ->** The core of the OS that manages system resources and processes. It starts **system daemons** which are background services providing functionality outside the kernel.
	- The kernel handles interrupts to respond to events efficiently.
	
In summary, the operating system starts with a **bootstrap program** that loads the **kernel**. The kernel initializes background services (daemons) and operates using **interrupts** to handle hardware signals and software requests efficiently. It addresses errors, system calls, and process issues through interrupts.

**Software Interrupts (Exceptions or Traps):**
- Caused by:
    - **Errors**: Such as division by zero.
    - **System Calls**: Requests from user programs for operating system services.
    - **Process Issues**: Problems like infinite loops or processes interfering with others or the OS.
~~Reached Slide 30~~

## **References**

![[ch1.pptx]]
