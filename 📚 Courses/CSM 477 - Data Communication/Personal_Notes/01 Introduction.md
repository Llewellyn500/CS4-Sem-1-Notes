---
date: 2025-01-27
course: CSM 477 - Data Communication
tags:
  - personal
  - study
  - CSM477
---

## **Overview**

- **Aim** -> Provide the highest possible transmission rate at the lowest possible power and least possible noise.
- **Communication Channel** -> A pathway over which information can be conveyed.
- A collection of bytes may itself be grouped into a frame or other higher-level message unit
- **Transmitter** -> Message source
- **Receiver** -> Message destination.
- A channels whose direction of transmission is unchanging is referred to as a simplex channel
![[📚 Courses/CSM 477 - Data Communication/Lecture_Notes/Lecture 01#channel types|Lecture 01]]

**Data Encapsulation:**  
Digital information is broken into bits, bytes, frames, etc.

#### **Serial Communications**

- Bit-serial transmission conveys a message one bit at a time through a channel
- Byte-serial transmission conveys eight bits at a time through eight parallel channels. (eg. used in Centronics Printer)

- With a time sharing system over a modem, only a single channel is available and bit serial transmission is required

![[Pasted image 20250221223103.png]]

- Bit-serial transmission is normally just called serial transmission and is the chosen communications method in many computer peripherals
- **Tradeoffs:**  
	- Parallel transmission is faster but more expensive and complex, especially over long distances.

#### **Transmission Media**

- Noise immunity is obtained by the use of pairs of wires which are twisted together.
- When carrying an analogue signal, it is necessary to insert an amplifiers to boost signal every 5 or 6 km.

##### **Baud Rate**

- It's the signaling rate at which data is sent through a channel and is measured in electrical transitions per second.
- a rate of 9600 baud corresponds to a transfer of 9,600 data bits per second with a bit period of 104 microseconds (1/9600 sec.)

##### **Channel Efficiency**

- Its the number of bits of useful information passed through the channel per second.
- It does not include framing, formatting, and error detecting bits.
- It is determined by the protocol design rather than by digital hardware considerations.
- There is a tradeoff between channel efficiency and reliability - protocols that provide greater immunity to noise by adding error-detecting and -correcting codes must necessarily become less efficient

![[Pasted image 20250221224323.png]]

##### **Data Rate**

- The data rate of a channel is often specified by its bit rate
- The max data rate a channel can support is directly proportional to the channel's bandwidth and inversely proportional to the channels noise level.

##### **Asynchronous vs. Synchronous Transmission**

- Serialized data is not generally sent at a uniform rate through a channel
- 








































## **Key Concepts**

-

## **References**
![[Datacom00020101.pptx]]
