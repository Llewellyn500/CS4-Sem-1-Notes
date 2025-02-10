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

#### What Operating Systems Do

- Its a **resource allocator** and **control program** making efficient use of HW(Hardware) and managing execution of user programs.
- An OS is **Interrupt Driven**
- **Kernel** -> The program running at all times on the computer
- **System Program** -> Ships with the OS, but not part of the kernel
- **Application Program** -> all programs not associated with the OS
- **Middleware** -> A set of software frameworks that provide additional services to application developers such as databases, multimedia, graphics.

#### Overview of Computer System Structure

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

#### Interrupt Timeline

![[Pasted image 20250210161319.png]]

##### Interrupt-drive I/O Cycle

![[Pasted image 20250210161407.png]]

- Two methods for handling I/O
	- After I/O starts, control returns to user program only upon I/O completion
	- After I/O starts, control returns to user program without waiting for I/O completion

## **References**

![[ch1.pptx]]
