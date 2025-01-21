---
course: CSM 477 - Data Communication
date: 2025-01-20
tags:
  - lecture
  - CSM477
---

# Lecture: 01

## Audio Recording

![[Recording 20250120150243.m4a]]

## Key Points
- data communication is the transfer of digital messages to external source.
- channel noise is any other message on the channel other than what's being transferred 

## Detailed Notes
- it's the aim of any communication system to provide the highest possible transmission rate at the lowest possible power and with the least possible noise
#### communication channel
It's a pathway over which information can be conveyed. 
Information is represented by individual data bits which may be encapsulated into multi bit message unit. 
#### channel types
- simplex channel: has a transmitter sending message to the receiver only
- half-duplex channel: has a transmitter transferring message to the receiver and vice versa but one at a time.
- full duplex: both sides has the transmitter and the receiver and can transmit and receive at the same time.
#### serial communication 
- bit serial transmits data in bits one at a time.
- byte serial transition, transmit messages one byte at a time through parallel channels
- although the raw transfer rate is eight times faster than in bit serial transmission, eight channels are needed and the cost may be as much as 8 times higher to transmit the message.
- bit serial is the chosen choice of transmission in many current computers 

Crosstalk - when the signals from 2 different channels seep into each other because the cables are close together.

#### Baud Rate
Refers to the signalling rate at which data is sent through a channel and is measured in electrical transitions per second.
- Baud rate is similar to transmission rate but not the same

**Channel efficiency** is the number of useful bits passed through a channel per second

#### Data rate
- Its often specified by its bit rate.
- The maximum data rate a channel can support is directly proportional to the channels bandwidth and inversely proportional to the channels noise level.
- Bandwidth is the available maximum space given to a device to transmit data.

## Summary
- 