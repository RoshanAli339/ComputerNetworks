# Connection 1

# Connection Establishment

![Untitled](Connection%201/Untitled.png)

- Consider a scenario when the network can lose, delay, corrupt and duplicate packets (the underline network layers uses unreliable data delivery)
- Consider retransmission for ensuring reliability — every packet uses different paths to reach the destination
- Packets may be delayed and got struck in the network congestion, after the timeout, the sender assumes that the packets have been dropped, and retransmits the packets
- It may happen that the server has crashed and reinitiated the connection. So distinguishing between these two is essential

![Untitled](Connection%201/Untitled%201.png)

****************How will the server differentiate whether CONNECTION REQ -1 is a new connection request or a duplicate of the CONNECTION REQ-2?****************

- **********Protocol correctness verses Protocol performance — an eternal debate in computer networks…**
- Delayed duplicates create a huge confusion in the packet switching network. A major challenge in packet switching network is to develop ******************correct****************** or **********************at least acceptable********************** protocols for handling delayed duplicates

## Connection Establishment — Handling Delayed Duplicates

### Solution 1: Use Throwaway Transport Address (Port Numbers)

- Do not use a port number if it has been used once already — Delayed duplicate packets will never find their way to a transport process
- Is this solution feasible?

### Solution 2: Give each connection a unique identifier chosen by the initiating party and put in each segment

Can you see the problem in this approach?

### Solution 3: Devise a mechanism to kill off aged packets that are still hobbling about (restrict the packet lifetime)

- Makes it possible to design a feasible solution

## Handling Delayed Duplicates

Three ways to restrict packet life

- **************************************************Restricted Network Design************************************************** — Prevents packets from looping (bound the maximum delay including congestion)
- ******************************************************************************Putting a hop count in each packet —** initialize to a maximum value and decrement each time the packet traverses a single hop (most feasible implementation)
- **********************************Timestamping each packet —** define the lifetime of a packet in the network, need time synchronization across each other

### Design Challenge:

We need to guarantee not only that a packet is dead, but also that all acknowledgements to it are also dead

- Let us define a maximum packet lifetime T — If we wait a time T secs after a packet has been sent, we can be sure that all traces of it (packet and its acknowledgement) are now gone
- Rather than a physical clock (clock synchronization in the Internet is difficult to achieve), let us use a virtual clock —  ****************************************************sequence number generated based on the clock ticks****************************************************
- Label segments with sequence numbers that will not be reused within T secs
- The period T and the rate of packets per second determine the size of the sequence number — at most one packet with a given sequence number may be outstanding at any given time.

## Sequence Number Adjustment

- Two important requirements (Tomilson 1975, Selecting Sequence Numbers)
    - ********R1.******** Sequence numbers must be chosen such that a particular sequence number never refers to more than one byte (for byte sequence numbers) at any one time
        - ********************************************************************************How to choose the initial sequence number********************************************************************************
    - ********R2.******** The valid range of sequence numbers must be positively synchronized between the sender and the receiver, whenever a connection is used.
        - **********The three way handshaking followed by the flow control mechanism — once connection is established, only send the data with expected sequence numbers**********

## Initial Sequence Number during Connection Establishment

![Untitled](Connection%201/Untitled%202.png)

A delayed duplicate packet for connection 1 can create a confusion for connection 2

## What we Ideally want? Either

![Untitled](Connection%201/Untitled%203.png)

## Or

![Untitled](Connection%201/Untitled%204.png)