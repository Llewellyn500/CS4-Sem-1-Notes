---
date: 2025-02-10
course: CSM 483 - Operating Systems
tags:
  - personal
  - study
  - CSM483
---
## **Overview**

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

#### **Multiprogramming (Batch System)**

- Multiprogramming organizes jobs (code and data) so CPU always has one to execute
- One job selected and run via **Job Scheduling**

#### **Multitasking (Timesharing)**

- extension of Batch systems
- The CPU switches jobs so frequently that users can interact with each job while it is running, creating interactive computing
- Response time -> less than 1 second
- Each user has at least one program executing in memory - **process**
- If several jobs ready to run at the same time - **CPU scheduling**
- If processes don’t fit in memory, **swapping** moves them in and out to run
- **Virtual memory** allows execution of processes not completely in memory

#### **Memory layout for multiprogram system**

![[Pasted image 20250223104849.png]]


#### **Dual-mode operation**

- **Purpose of Dual-Mode Operation**
    - Allows the operating system (OS) to protect itself and other system components from potentially harmful or unauthorized user processes.
    - Enforces two distinct execution contexts: **user mode** and **kernel mode**.
    
- **Mode Bit (Hardware Support)**
    - A hardware-provided **mode bit** distinguishes whether the system is running **user code** or **kernel code**.
    - When running **user code**, the mode bit is set to “user.”
    - When running **kernel code**, the mode bit is set to “kernel.”
    
- **Ensuring Proper Mode Transitions**
    - The OS prevents user processes from directly setting the mode bit to “kernel.”
    - **System calls** automatically switch the mode from user to kernel.
    - When the system call completes (returns), the mode bit is reset to user mode.
    
- **Privileged Instructions**
    - Certain instructions are marked as **privileged** and can only be executed in kernel mode.
    - This restriction helps maintain security and system integrity, ensuring that only trusted OS code can perform critical operations.

![[Pasted image 20250223105539.png]]

#### **Timer**

- **Purpose**: Prevents infinite loops or processes hogging resources.
- **Operation**:
    - A timer is set to interrupt the computer after a specified time interval.
    - A counter decrements (driven by the physical clock).
    - When the counter reaches zero, an interrupt is generated.
    
- **OS Control**:
    - The operating system sets the counter (a **privileged instruction**).
    - The timer interrupt ensures the OS can regain control or terminate programs exceeding their allotted time.

#### **Process Management**

- **Process**: A program in execution (active entity), as opposed to a passive program file (passive entity).
- **Resources**: Requires CPU, memory, I/O devices, and initialization data to run.
- **Termination**: When a process finishes, the OS reclaims its resources.
- **Program Counter**:
    - Single-threaded processes have one program counter (one thread of execution).
    - Multi-threaded processes can have multiple program counters (multiple threads) sharing resources.
- **Concurrency**: Many processes can run concurrently on one or more CPUs (multiplexing CPU resources among them).

#### **Process Management Activities**

**OS Responsibilities**:

1. **Creating and deleting** both user and system processes.
2. **Suspending and resuming** processes.
3. Providing **mechanisms for process synchronization** (ensuring correct sequencing and data sharing).
4. Providing **mechanisms for process communication** (e.g., inter-process communication).
5. Providing **mechanisms for deadlock handling** (detecting and recovering or preventing deadlocks).

#### **Memory Management**

- **Key Requirement**: All (or part) of the program instructions and data must be in memory to execute.
- **Goals**:
    - Optimize CPU utilization and provide good user response times.
    - Decide which processes (or parts thereof) stay in memory and which move out (swapping, paging, etc.).
- **OS Activities**:
    1. **Tracking** which parts of memory are currently in use and by whom.
    2. **Deciding** which processes (or data) to move in/out of memory.
    3. **Allocating and deallocating** memory space as needed.

####  **File-System Management**

- **Logical View**: The OS abstracts physical storage (e.g., disks, tape drives) into a **logical storage unit** called a file.
- **Varying Media**: Different devices vary by speed, capacity, data-transfer rate, and access methods (sequential vs. random).
- **Directories**: Files are organized into directories for better management.
- **Access Control**: Determines who can access what files or directories.
- **OS Activities**:
    1. **Creating and deleting** files and directories.
    2. Providing **primitives to manipulate** files and directories.
    3. **Mapping files** onto secondary storage.
    4. **Backing up files** to stable (non-volatile) storage.

#### **Mass-Storage Management**

- **Typical Use**: Disks store data not fitting in main memory or data needing long-term storage.
- **Central Importance**: Proper disk management affects overall system performance.
- **OS Responsibilities**:
    1. **Mounting and unmounting** storage devices.
    2. **Free-space management** (tracking available disk blocks).
    3. **Storage allocation** (deciding where files go on disk).
    4. **Disk scheduling** (managing read/write requests for efficiency).
    5. **Partitioning** (dividing physical disks into logical sections).
    6. **Protection** (ensuring secure access to disk data).

#### **Caching**

- **Concept**: Storing data from slower storage (e.g., disk) into faster storage (cache) to speed up access.
- **Process**:
    - Check if data is in the cache. If yes, use it (faster).
    - If not, bring it from the slower storage into the cache.
- **Challenges**:
    - Cache is smaller than the data being cached.
    - **Cache management** involves decisions on cache size and **replacement policy** (which data to keep or evict).

#### **Characteristics of Various Types of Storage**

![[Pasted image 20250223111021.png]]


#### **Migration of Data "A" from Disk to Register**

![[Pasted image 20250223111259.png]]

- **Storage Hierarchy Awareness*
    - In multitasking environments, data (e.g., variable “A”) may reside at different levels: **disk**, **main memory**, **cache**, or **hardware register**.
    - The system must ensure the **most recent** copy of the data is always used, regardless of its location.
    
- **Cache Coherency in Multiprocessors**
    - In a **multiprocessor environment**, each CPU might have its own cache.
    - **Cache coherency** hardware/logic is necessary to guarantee that all CPUs see the **most up-to-date** value of shared data.
    
- **Distributed Environments**
    - Complexity increases when data is replicated across **multiple machines** in a network.
    - Multiple copies of the same data may exist, requiring synchronization to ensure consistency.

#### **I/O Subsystem**

- **Abstraction Purpose**
    - One of the OS’s roles is to **hide the complexities** of hardware devices from users and application programs.
    
- **Responsibilities**
    - **Memory management for I/O**:
        - **Buffering**: Temporarily storing data while transferring between devices.
        - **Caching**: Keeping data in a faster storage area for quick access.
        - **Spooling**: Overlapping the output of one job with the input of another to optimize resource usage.
    - **Device-Driver Interface**:
        - A general interface that allows the OS to communicate with a wide range of hardware devices.
    - **Device Drivers**:
        - Specific drivers handle the details for particular hardware.

#### **Protection and Security**

- **Protection**
    - Mechanisms for **controlling access** of processes or users to resources (e.g., files, memory, CPU).
    
- **Security**
    - Broader defense against external/internal threats such as **viruses, worms, denial-of-service attacks**, etc.
    - Involves ensuring **integrity, confidentiality, and availability** of system resources.
    
- **User and Group Identification**
    - **User IDs (UIDs)**: Unique identifiers (name and numeric ID) assigned to each user.
    - **Group IDs (GIDs)**: Collections of users, each user can belong to multiple groups.
    - **Privilege Escalation**: A mechanism allowing a user to change to an ID with **more privileges** temporarily (e.g., `sudo` in Unix).

#### **Virtualization**

- **Definition**
    - Technology enabling one operating system (or multiple OSes) to **run on top of another** or on the same hardware **simultaneously**.
    
- **Emulation**
    - Used when the CPU type is **different** from the target platform (e.g., running a PowerPC program on an Intel CPU).
    - **Slower** because every instruction must be translated.
    
- **Virtualization**
    - Typically used when the **host** and **guest** systems share the same CPU architecture.
    - The OS can run natively compiled code with minimal overhead.
    - **Examples**: VMware, VirtualBox, Hyper-V, etc.
    
- **Virtual Machine Manager (VMM)**
    - Also known as a **hypervisor**.
    - Provides virtualization services, managing guest OSes on top of the host hardware.
    
- **Use Cases**
    1. **Running multiple OSes** (e.g., macOS and Windows) on the same machine.
    2. **Quality assurance testing** without requiring multiple physical systems.
    3. **Server consolidation**: Multiple server OSes on one physical server.
    4. **Development and isolation**: Test different environments safely.
    
- **Types of VMM**
    - **Native / Bare-metal**: The hypervisor runs directly on hardware and also acts as the host (e.g., VMware ESXi, Citrix XenServer).
    - **Hosted**: The hypervisor runs as an application on a conventional host OS (e.g., VMware Workstation, VirtualBox).

![[Pasted image 20250223112123.png]]

- **Diagram (a)**: Traditional system with a single **kernel** directly on **hardware**, and processes on top of the kernel.
- **Diagram (b)**: Virtualized environment where a **virtual machine manager (VMM)** runs on hardware, hosting multiple **VMs** (each with its own **kernel** and **processes**).
- **Key Point**: Virtualization provides isolation between VMs while sharing the same physical hardware.

#### **Distributed Systems**
- **Definition**
    - A **collection of separate systems**, often heterogeneous, **networked** together to appear to users as a **single coherent system**.
    
- **Networks**
    - Communication path is typically **TCP/IP** based.
    - Examples of networks:
        - **LAN** (Local Area Network)
        - **WAN** (Wide Area Network)
        - **MAN** (Metropolitan Area Network)
        - **PAN** (Personal Area Network)
        
- **Network Operating System**
    - Provides **features across the network** such as shared file systems, remote process execution, etc.
    - **Communication scheme** that allows processes on different machines to exchange messages.
    - Strives for an **illusion of a single system** to end users, even though multiple machines are involved.

#### **Computer-System Architecture**

- **Single vs. Multiprocessor Systems**
    - Most computers have a single general-purpose CPU, but special-purpose processors also exist.
    - **Multiprocessors** (parallel or tightly-coupled systems) are increasingly common, offering:
        1. **Increased throughput**: More tasks completed in parallel.
        2. **Economy of scale**: Shared resources reduce overall cost per CPU.
        3. **Increased reliability**: If one processor fails, others can continue (fault tolerance).

- **Asymmetric vs. Symmetric Multiprocessing**
    - **Asymmetric**: Each processor is assigned a specific task (master-slave relationship).
    - **Symmetric (SMP)**: Each processor runs all tasks and shares the same memory, OS, and I/O.

#### **Symmetric Multiprocessing Architecture**

![[Pasted image 20250223113303.png]]

- **Shared Memory**
    - All processors (CPU₀, CPU₁, …) share the same main memory.
- **Local Caches**
    - Each processor has its own **registers** and **cache** to speed up access to frequently used data.
- **Key Benefit**: Any CPU can run any process or thread, which improves load balancing and system performance.

#### **Dual-Core Design**

![[Pasted image 20250223113456.png]]

- **Multi-Chip vs. Multicore**
    - **Multicore** means having multiple CPU cores on a single chip (e.g., dual-core, quad-core).
    - Each core has its own **registers** and **L1 cache**, but typically shares an **L2 cache** (or higher-level caches) and main memory with the other core(s).
    
- **Systems with Multiple Chips**
    - A single computer chassis can contain multiple **separate processors**, each of which might be multicore.
    - This allows for even greater parallelism and performance.

#### **Non-Uniform Memory Access (NUMA) System**

![[Pasted image 20250223113551.png]]

- **Distributed Memory**
    - Each CPU has local memory, forming “nodes.”
- **Interconnect**
    - A high-speed connection links these nodes together.
- **Non-Uniform Latency**
    - Access to local memory is faster than access to remote memory (memory connected to a different CPU).
- **Goal**
    - Improve scalability by reducing memory bottlenecks when multiple processors need simultaneous memory access.

#### **Clustered Systems**

![[Pasted image 20250223113739.png]]

- **Definition**
    - Multiple **independent systems** working together, often sharing storage via a **Storage-Area Network (SAN)**.
- **High-Availability**
    - If one system fails, others can pick up the workload.
    - **Asymmetric Clustering**: One node is in “hot standby” mode, ready to take over if the active node fails.
    - **Symmetric Clustering**: Multiple nodes run applications concurrently, monitoring each other.
- **High-Performance Computing (HPC)**
    - Some clusters are designed to run parallelized applications that split tasks across multiple nodes.
    - A **Distributed Lock Manager (DLM)** may be used to synchronize access to shared data.

#### **PC Motherboard**

![[Pasted image 20250223113754.png]]

- **Key Components**
    - **CPU socket**: Where the processor(s) plug in.
    - **DRAM slots**: For system memory modules.
    - **PCI bus slots**: Expansion slots for add-on cards (e.g., graphics, networking).
    - **Various I/O and power connectors**: Interfaces for peripherals, power supply, etc.
- **Functionality**
    - A motherboard is a complete platform once populated with CPU(s), memory, and other components.
    - Modern motherboards can support **multiple CPU sockets** (for multiprocessor setups) and potentially **NUMA** configurations.
    - Even lower-cost boards often support multicore CPUs, enabling basic parallel processing.


#### **Computer System Environment**

These represent different ways computers and devices interact with each other and the broader network:
- Traditional
- Mobile
- Client Server
- Peer-to-Peer
- Cloud Computing
- Real-time Embedded

#### 1.Traditional

- **Stand-Alone General-Purpose Machines**: Historically, computers were often single systems running locally installed software.
- **Internet Connectivity**: Nowadays, even “stand-alone” machines typically connect to the internet, blurring the distinction.
- **Portals**: Provide web-based access to internal systems (e.g., corporate intranets).
- **Network Computers (Thin Clients)**: Minimal hardware/software devices that rely on networked servers for most processing.
- **Mobile Computing via Wireless**: Laptops and other portable devices increasingly connect over Wi-Fi or cellular networks.
- **Security Measures**: Firewalls are common to protect home and enterprise networks from external attacks.

**Explanation**:  
The “traditional” environment covers desktop PCs and servers that may have started as isolated systems but now almost always connect to larger networks or the internet. The focus is on local processing power and storage, with additional networked capabilities for communication and data exchange.

#### 2. Mobile

- **Devices**: Smartphones, tablets, and other handheld devices.
- **Key Differences from Laptops**: Mobile devices typically have additional sensors (GPS, accelerometer, gyroscope) and specialized operating systems.
- **New Application Types**: Apps leveraging location data, augmented reality, and other sensor-driven features.
- **Connectivity**: Use Wi-Fi (IEEE 802.11) or cellular networks (3G/4G/5G) for internet access.
- **Market Leaders**: Apple iOS and Google Android.

**Explanation**:  
Mobile computing emphasizes portability, battery life, and connectivity. The added sensors enable unique features (like GPS-based apps), and the operating systems are designed for touch-based interfaces and app ecosystems. Security and power management are also critical considerations in mobile environments.

#### 3. Client-Server

![[Pasted image 20250223115136.png]]

- **Evolution**: Early “dumb terminals” replaced by smart PCs, but the fundamental concept of a **server** responding to **client** requests remains.
- **Types of Servers**:
    1. **Compute-Server System**: Offers services like database access or computation.
    2. **File-Server System**: Manages file storage and retrieval for networked clients.
- **Interaction**: Clients (desktop, laptop, smartphone) send requests to servers over a network.

**Explanation**:  
In a client-server model, specialized servers provide resources or services (e.g., data storage, database queries), and clients request those services. This structure centralizes certain functions, improving manageability and resource sharing. Most web and corporate applications still rely on some variation of the client-server model.

#### 4. Peer-to-Peer (P2P)

![[Pasted image 20250223115353.png]]

- **Decentralized Architecture**: Unlike client-server, P2P treats all nodes (peers) as equals.
- **Roles**: Each node can act as both a client (requesting services) and a server (providing services).
- **Joining the Network**: A peer may register with a central lookup service or broadcast requests for resources using a discovery protocol.
- **Examples**: Napster, Gnutella, Skype (Voice over IP).

**Explanation**:  
Peer-to-Peer networks distribute workload among many nodes, removing the single point of failure typical of client-server models. While this can improve scalability and resilience, it also introduces challenges in coordination, security, and resource discovery.

#### 5. Cloud Computing

![[Pasted image 20250223115557.png]]

- **Definition & Purpose**
    - Delivers computing resources—such as servers, storage, and even applications—as a service over the internet.
    - A logical extension of virtualization, leveraging virtual machines (VMs) to host services at scale.
    
- **Examples**
    - **Amazon EC2**: Offers thousands of servers, millions of virtual machines, and petabytes of storage to users who pay based on usage.

- **Cloud Deployment Models**
    1. **Public Cloud**: Services available over the internet to anyone willing to pay.
    2. **Private Cloud**: Operated by a single organization for internal use.
    3. **Hybrid Cloud**: A combination of both public and private cloud components.
    
- **Cloud Service Models**
    1. **Software as a Service (SaaS)**: Complete software applications delivered via the internet (e.g., word processors, email).
    2. **Platform as a Service (PaaS)**: A full software development platform online (e.g., database servers, development frameworks).
    3. **Infrastructure as a Service (IaaS)**: Virtual servers and storage made available over the internet (e.g., backup solutions)
    
**Components & Tools**
- Consists of virtual machines, operating systems, plus specialized **cloud management** tools for provisioning and monitoring.
- **Security** is crucial due to internet connectivity; firewalls, encryption, and other measures protect data and services.
- **Load Balancers** help distribute traffic across multiple servers to handle high demand efficiently.

#### 6. Real-Time Embedded Systems

- **Definition & Prevalence**
    - Special-purpose computers with strict timing constraints (e.g., automotive systems, medical devices).
    - They are the **most common form of computers** worldwide (in devices like microwaves, sensors, industrial machines).
    
- **Real-Time OS Requirements**
    - Must perform tasks within a guaranteed time frame; failure to meet deadlines can cause system errors or unsafe conditions.
    - Some embedded systems run with no full OS at all, just minimal software to manage specific tasks.

#### 7. Free and Open-Source Operating Systems

- **Open Source vs. Proprietary**
    - Open-source OSes are distributed with source code, enabling modification and redistribution by users (e.g., Linux, BSD variants).
    - Contrasts with closed-source, proprietary systems that do not allow code inspection or modification.

- **Licensing & Examples**
    - Governed by licenses like the **GNU Public License (GPL)**.
    - Examples: **Linux**, **BSD UNIX** (including Darwin, which underlies macOS).
    - Virtual machine platforms (VMware Player, VirtualBox) enable users to experiment with multiple open-source OSes easily.
    
#### **The Study of Operating Systems**

- **Current Landscape**
    - There has never been a more interesting time to study operating systems due to the variety of commercial and open-source options.
    - Virtualization allows multiple OSes to run on a single physical machine, broadening the scope for experimentation and research.
    
- **Open-Source Ecosystem**
    - Wide availability of open-source OSes (Linux, BSD variants) encourages learning, customization, and innovation.
    - Tools like VirtualBox and VMware facilitate testing new OS features or running older ones, all on standard hardware.
    
- **Impact on Learning & Research**
    - Students and developers can experiment without needing specialized hardware.
    - The abundance of free resources and large communities fosters collaboration and rapid development of new OS features.

#### **Kernel Data Structure**

##### 1. **Linked Lists**

- **Singly Linked List**
    ![[Pasted image 20250223120417.png]]
    - Each node contains data and a pointer to the next node.
    - Traversal is one-directional.
    - Operations such as insertion and deletion can be efficient if the pointer to the correct node is already known, but searching can take $O(n)$ time in the worst case.
    
- **Doubly Linked List**
    ![[Pasted image 20250223120434.png]]
    - Each node has pointers to both the next and the previous node.
    - Allows bidirectional traversal and can simplify deletion operations (no need to find the previous node first).
    - Requires additional memory for the extra pointer.
    
- **Circular Linked List**
    ![[Pasted image 20250223120445.png]]
    - The last node links back to the first node, forming a circle.
    - Useful for applications that repeatedly cycle through elements (e.g., round-robin scheduling).
    - Care is needed to detect the “end” of the list or to avoid infinite loops.

**Explanation:**  
Linked lists are fundamental data structures used by the kernel for tasks like maintaining lists of processes, open files, or buffers. The choice of singly, doubly, or circular lists depends on the access patterns and update operations required.

##### 2. **Binary Search Trees (BST)**

![[Pasted image 20250223120518.png]]

- **Basic BST**
    - Nodes arranged so that all keys in the left subtree are $\le$ the node’s key, and keys in the right subtree are $\ge$ the node’s key.
    - **Search Complexity**: $O(n)$ in the worst case if the tree is unbalanced (e.g., a degenerate “linked list” shape).
    
- **Balanced BST**
    - Techniques like AVL or Red-Black trees keep the tree’s height relatively small.
    - **Search Complexity**: $O(\log n)$ for insertion, deletion, and lookup in typical balanced trees.

**Explanation:**  
BSTs allow fast lookups, insertions, and deletions when balanced. In kernel contexts, balanced tree structures (like Red-Black trees) are often used for efficient indexing of data (e.g., for scheduling or memory management structures).

##### 3. **Hashing, Bitmaps, and Kernel Headers**

![[Pasted image 20250223120547.png]]
- **Hash Function & Hash Map**
    - A hash function converts a key into an index in a hash table.
    - **Lookup/Insert** can be near $O(1)$ on average, assuming a good hash function and low collision rate.
    - Collisions (when two keys map to the same index) require resolution strategies (e.g., chaining or open addressing).
    
- **Bitmap**
    - A string of bits representing the status (e.g., free/allocated) of $n$ items.
    - Useful for tracking resources (e.g., pages in memory, disk blocks).
    
- **Linux Kernel Data Structures**
    - The Linux kernel provides common data structure implementations in headers like:
        - `<linux/list.h>` (linked lists)
        - `<linux/kfifo.h>` (FIFO buffers)
        - `<linux/rbtree.h>` (Red-Black trees)

**Explanation:**  
Hash maps and bitmaps are common in OS kernels for managing resources quickly and compactly. Linux’s kernel headers offer pre-written, highly optimized data structures for developers to use, ensuring consistent performance and maintainability across different kernel components.



























## **References**

![[ch1.pptx]]
