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
- **Asynchronous**: Simple, good for sporadic data; each packet framed with start/stop bits; potentially more overhead.
- **Synchronous**: Continuous, higher throughput, but needs clock synchronization; data is read exactly on clock pulses.
- **Synchronization** is critical: if timing is off, data integrity is lost.

- **General Concept of Serialized Data**
    - Data bits are sent one after another (serially), but **not always at a uniform rate**.
    - In practice, data often travels in bursts, separated by pauses.
    
- **Importance of Timing/Synchronization**
    - The receiver must know **when a packet starts** and **how to space out each bit**.
    - If the receiver and transmitter are not synchronized, **errors** (corrupted or lost data) will occur.
    
- **Asynchronous Transmission**
    - Data is sent in **short bursts** or packets, often with **variable-length gaps** in between.
    - Each burst contains its own **timing or framing information** (e.g., start and stop bits) so the receiver can resynchronize for every packet.
    - Less complex hardware but **higher overhead** due to start/stop bits on every packet.\
    
- **Synchronous Transmission**
    - Uses **separate channels** for data and for timing (clock pulses).
    - The transmitter sends a **continuous clock signal**; upon each clock pulse, the receiver **latches** (reads) the data bit.
    - Because both data and timing come from the transmitter, **synchronization is guaranteed**—no extra start/stop bits are needed.
    - More efficient (less overhead) but **requires more complex hardware** and a dedicated timing channel.

#### **Manchester Coding**

- A form of **biphase** or self-timed encoding used in digital communications.
    - Ensures **clock recovery** by embedding timing information directly in the signal transitions.
    
- **Self-Timed Methods**
    - **Non-Return-to-Zero (NRZ)** and **Manchester Coding** both transform a data stream into a specific electrical waveform that can be reliably decoded.
    - Because timing is embedded, a separate timing channel is unnecessary.
    
- **Asynchronous Systems**
    - Do **not** use a dedicated clock signal; instead, the transmitter and receiver agree on a **baud rate** beforehand.
    - The receiver’s local oscillator is calibrated to match the transmitter’s rate “within a fraction of a percent.”
    - Data is often sent in **packets** of 10 or 11 bits (e.g., 1 start bit, 8 data bits, optional parity bit, and 1 stop bit).
    
- **Idle State**
    - When no data is being transmitted, the line typically remains at a **logic ‘1’** voltage level.
    
- **Why It Matters**
    - Manchester coding (and similar schemes) make it easier to keep transmitter and receiver in sync without a separate clock line.
    - Asynchronous protocols rely on accurate oscillators and framing bits to stay synchronized.

#### **Data Packet**

![[Pasted image 20250227204105.png]]

1. **Start Bit**
    - A logic ‘0’ at the beginning signals the receiver that a new packet is starting.
    - This triggers the receiver’s internal timer to generate the necessary clock pulses.
    
2. **Data Bits**
    - Typically **8 bits** of actual message data follow the start bit.
    - Transmitted at the agreed-upon baud rate (e.g., 110, 300, 9600 baud, etc.).
    
3. **Optional Parity Bit**
    - Can be added after the data bits for **error detection** (odd, even, or none).
    
4. **Stop Bit(s)**
    - Usually one (sometimes two) stop bits at a **logic ‘1’** level to mark the end of the packet.
    
5. **Synchronization & Packet Length**
    - Each packet is short (often 10 or 11 bits total) to **minimize timing drift** between transmitter and receiver.
    - Every new start bit **re-synchronizes** the receiver’s internal clock, so **pauses** between packets can be any length.
    
6. **EIA232 Standard vs. Protocol**
    - **EIA232** (often called RS‑232) defines **electrical, timing, and mechanical** details of a serial interface.
    - It does **not** define the exact asynchronous framing (start, stop, parity bits); that is a **separate protocol** layer.

#### **Parity and Checksums**

![[Pasted image 20250227205409.png]]

- **Purpose of Parity Bits**
    - A **parity bit** is appended to a binary data transmission to detect potential errors that occur during data transfer.
    - By counting the number of 1s in the transmitted data plus the parity bit, the receiver can quickly check if a single‑bit error has occurred.
    
- **Types of Parity**
    - **Even Parity:** The parity bit is set to 0 or 1 so that the total number of 1s (data + parity) is an even number.
    - **Odd Parity:** Ensures the total number of 1s (data + parity) is odd.
    - **Space Parity (Always 0):** The parity bit is always 0 (used sometimes as a filler bit).
    - **Mark Parity (Always 1):** The parity bit is always 1 (also used as a filler bit).
    
- **Examples**
    - If the data bits `1010101` have four 1s (which is even), then:
        - **Odd Parity** → parity bit is `1` (making five 1s total).
        - **Even Parity** → parity bit is `0` (keeping four 1s total).
    - The letter **A** (`1000001` in binary) has two 1s (which is even), so:
        - Under **even parity**, the parity bit would be `0`.
        - Under **odd parity**, the parity bit would be `1`.
        
- **Reliability of Parity**
    - Parity can detect **any single‑bit error** (it flips parity from even to odd or vice versa).
    - **Multiple‑bit errors** might not be caught if they preserve the total number of 1s. For example, if two bits are flipped, the parity may remain unchanged.
    - Therefore, parity is a **useful first line of defense** but **not 100% foolproof**.

- **Checksums**
    - A **checksum** is another error‑detection method where a numerical sum of the data (and sometimes headers) is appended.
    - More robust than parity, but also not guaranteed to detect every error; its effectiveness depends on the size of the checksum and the nature of the data.
    
- **Practical Considerations**
    - **Small Packets**: Parity is most reliable when packet sizes are small, reducing the chance of multiple‑bit errors.
    - If an error is detected, **retransmission** is often requested. In some systems, additional error‑correcting codes can fix certain errors automatically.

- **Purpose:** A single parity bit is added to each data packet to detect single-bit errors.
    - **Even Parity:** The total count of ‘1’ bits (data + parity) is kept even.
    - **Odd Parity:** The total count of ‘1’ bits (data + parity) is kept odd.
    - **Detection Limit:**
        - Single-bit flips (errors) will change parity from even to odd or vice versa, thus being caught.
        - Multiple-bit errors that preserve the total number of ‘1’s can go undetected.
    
- **Error Handling**
    - If a parity check fails, the receiver can request retransmission (e.g., in a protocol with Automatic Repeat reQuest—ARQ).
    - In some systems, more complex error-correcting codes can correct one- or two-bit errors automatically.
    
- **Checksums**
    - **How It Works:** Each packet’s data bytes are added together arithmetically; the resulting sum (or an inverted form) is appended to the packet.
    - **Verification:** The receiver re-sums the data plus checksum. If the result is zero (or some agreed-upon constant), it is assumed no errors occurred.
    - **Advantages & Limitations:**
        - Detects a broader range of errors than simple parity.
        - Still not foolproof; certain error patterns can produce the same checksum.

- **Checksum Computation**

![[Pasted image 20250227205446.png]]

- **How It Works:**
        1. All bytes in the data block are added arithmetically (mod 256 or mod some agreed base).
        2. The resulting sum (or an inverted form) is appended as the checksum.
        3. The receiver recomputes the sum of the data plus the checksum; if the final result is zero (or another predetermined constant), no error is assumed.
    
    - **Advantages:**
        - Detects a broader range of errors than simple parity.
        - Easy to compute in software or hardware.
        
    - **Limitations:**
        - Not 100% foolproof—certain patterns of errors can produce the same checksum.
        
- **Error Correction**
    - **Error-Correcting Codes (ECC):**
        - Additional redundancy bits are added to detect and **correct** certain errors (e.g., one- or two-bit errors).
        - Useful in situations where retransmission is impractical or costly (e.g., satellite links).
        
    - **Tradeoff:**
        - More redundancy means less channel efficiency and a drop in overall throughput.
        - Implement only when the error probability is high or retransmission is not possible.
    
#### **Data Compression**

- **Goal:** Reduce the size of the transmitted data without losing the original information.
    - **Method:**
        1. Statistically analyze data.
        2. Assign short binary codes to frequently used characters/values and longer codes to rare ones.
        3. Transmit compressed data; the receiver decompresses it back to the original form.
        
    - **Benefits:**
        - Often achieves **50% or greater** data reduction overall.
        - Image data (e.g., fax transmission) may compress by **80%** or more.
        - Text or program data may see **15–20%** compression.
        
    - **Huffman Coding:**
        - Commonly used in fax and data communications.
        - Particularly effective if large portions of the data are repetitive (e.g., long runs of white pixels in a fax).
        - Yields significant savings in transmission time and bandwidth.
        
- **Practical Considerations**
    - **Compression Overhead:**
        - Some processing time is needed for compression and decompression, but overall time saved (due to reduced transmission) usually outweighs that cost.
    - **When Compression Helps Most:**
        - Highly repetitive data (like large white areas in fax images).
        - Not as beneficial when data is already random or compressed.

#### **Data Encryption**

- **Purpose:** Protect privacy by scrambling data so it appears indecipherable to unauthorized interceptors.
    - **Use Cases:** Faxed business letters, digitized phone calls, or any sensitive data communication over potentially insecure channels (phone lines, microwave transmissions, etc.).
    - **How It Works:**
        1. **Encryption (Scrambling):** Binary codes are rearranged or substituted based on an algorithm.
        2. **Decryption (Descrambling):** Authorized receivers use a matching key or decoder to restore the original message.
    - **Implementation:**
        - Often done by custom integrated circuits, which can be built into devices or used externally.
        - Can be transparent to users (automatic within the device’s circuitry) or managed via standalone hardware.

#### **Data Storage Technology**

- **Parallel to Data Communications:** Many error-correcting techniques used in data transmission (e.g., ECC) are also applied to data storage.
    - **Examples:**
        - **Compact Discs (CDs) / CD-ROMs**
        - **Tape Backup Systems**
    - **Goal:** Ensure accurate retrieval of stored data, just as with transmitted data, by detecting and correcting errors that may arise over time or during the read process.

#### **Data Transfer in Digital Circuits**

![[Pasted image 20250227205655.png]]

- **Data Grouping and Registers**
    
    - Digital data is usually grouped into packets of **8, 16, or 32 bits**.
    - These bits are stored temporarily in **registers**, which hold data in parallel (each bit on a separate conductor).
- **Buses for Data Transfer**
    
    - **Bus:** A set of parallel conductors used to transfer data from one register to another.
    - The output lines of a source register are connected to the bus, and the destination register’s input lines also connect to that same bus.
- **Transfer Mechanics**
    
    - When the bus is enabled for a source register, its data is placed onto the bus.
    - The destination register, also enabled by control signals, captures that data.
    - **Key Point:** After a transfer, the source register still retains its data—nothing is erased.
- **Bus Contention**
    
    - **Only one source** may drive the bus at any time.
    - If multiple sources attempt to transmit simultaneously, **electrical conflict** occurs (opposing bit values driving the same line).
    - This “bus contention” can cause data loss and damage circuitry.
- **Control Logic**
    
    - A central control unit coordinates which register can place data on the bus at a given moment.
    - Ensures no two sources drive the bus at once.
- **Half-Duplex Nature**
    
    - Buses in typical microprocessors are often **half-duplex**: they can carry data in two directions, but not simultaneously on the same lines.


#### **Transmission over Short Distances**

![[Pasted image 20250227205824.png]]

- **On-Chip vs. Off-Chip Transfers**
    - **On-Chip:**
        - Source and destination registers can be extremely close (thousandths of an inch apart).
        - Signals travel at very low power and are minimally affected by external noise or distortion—an ideal environment for digital communications.

    - **Off-Chip:**
        - Data must leave the integrated circuit (IC) through external pins, requiring amplifiers or buffer circuits to drive the signals over longer distances (e.g., a few inches on a printed circuit board).

- **Practical Distance Limits**
    - Signals can typically travel about **one foot** on a printed circuit board at standard logic levels.
    - For greater distances or multiple connections (e.g., memory chips), **special buffer or driver circuits** are used to maintain signal integrity.

- **Implications for System Design**
    - It’s not yet feasible to integrate all computer components (CPU, memory, I/O, etc.) on a single chip; hence off-chip data paths are necessary.
    - As soon as data leaves the chip, more robust driving circuitry and noise mitigation become crucial.


#### **Noise and Electrical Distortion**

![[Pasted image 20250227210617.png]]

![[Pasted image 20250227210626.png]]

![[Pasted image 20250227210645.png]]

![[Pasted image 20250227210653.png]]

- **Why Noise is a Concern**
    - Modern computers use very **high switching rates** and **low-voltage signals** on data, address, and control buses.
    - Extending these signals beyond the main circuit board can expose them to external electromagnetic interference (EMI) from motors, switches, and other electronics.

- **Effects of Noise**
    - Longer cable runs or more connections increase the chance of picking up interference.
    - Even a **single bit error** in a critical instruction can cause a system crash or other major malfunction.

- **Signal Distortion**
    - Metallic conductors (like copper wires) introduce **capacitance and inductance**, causing pulses to become rounded or show ringing at their edges.
    - The problem worsens as **conductor length** increases.
    - To compensate, either **increase signal power** or **reduce the data rate**.

- **Amplifiers and Buffers**
    - Special **line drivers** or **amplifier circuits** (often simple IC chips) boost signal levels for transmission over longer distances.
    - These amplifiers typically operate from standard power supplies (e.g., +5 V) and ensure the signal remains within acceptable voltage thresholds despite noise and attenuation.

- **Noise Margin**
    - **Definition:** The difference between an amplifier’s output voltage (for a logic ‘1’ or logic ‘0’) and the minimum or maximum threshold voltage recognized as a valid logic level.
    - **Importance:** This margin represents how much noise can be added to the signal before an error occurs.
    - **Example:**
        - For a logic ‘1,’ the amplifier might output slightly above the minimum needed (e.g., 3 V if 2.5 V is the threshold).
        - The gap between this output (3 V) and the threshold (2.5 V) is the noise margin.

- **Transmission Over Medium Distances**    
    - **Challenge:** Simply extending a computer’s internal buses with a long cable to reach a peripheral (like a printer) would expose all bus traffic to noise and interference.
    - **Solution:**
        - Use a **bus interface circuit** that includes:
            1. A **holding register** for peripheral data.
            2. **Timing/formatting circuitry** to package data with error-detecting codes.
            3. **Signal amplifiers** to boost the data for reliable cable transmission.
        - This way, only the data destined for the peripheral is sent through the cable at a relatively slow rate with higher signal power.
    - **Benefits:**
        - Prevents corruption of the computer’s main bus signals.
        - Minimizes noise and distortion on the extended cable.
        - Ensures efficient, reliable communication over distances up to about 20 feet.

- **Peripheral-Only Data Transmission**
    - Only the data **intended for the peripheral** travels through the external cable; all other internal bus signals remain on the computer’s main board and are not exposed to external noise.
    - Transmission can be:
        - **Byte-Serial** (parallel) if multiple conductors are available (e.g., 8 lines + control signals).
        - **Bit-Serial** if only a single channel is available.

- **Importance of Matching Transmission Medium**
    - **Medium Options:** Metallic conductors (copper), optical fiber, or free‑space (wireless).
    - **Key Consideration:** Each medium has unique characteristics (bandwidth, noise susceptibility, distance limits) that must align with the system’s data rate and reliability needs.

- **Amplifiers and Repeaters**
    - **Analog Amplifiers:** Provide a continuous linear gain for analog signals.
    - **Digital Repeaters:** Used typically every 2–3 km to regenerate (amplify and reshape) digital pulses.
        - They “clean up” the signal to a fixed logic level, removing accumulated noise or distortion.

#### **Cabling**





















## **Key Concepts**

-

## **References**
![[Datacom00020101.pptx]]
