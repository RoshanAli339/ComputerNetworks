# Switched Network

# Switched Network

- Communication between distant stations/ end-devices is typically done over a network of switching nodes.
- Switching nodes do not concern with content of data. The purpose is to provide a switching facility that will communicate/transmit the data from source to destination via intermediate node(s).
- A collection of nodes and connections forms a communication network
- In a switched communications network, data entering the network from a source station are routed to the destination by being switched from node to node.

# Typical Switching Network

![Untitled](Switched%20Network/Untitled.png)

# Switching Technologies

Switching nodes may connect to other nodes, or to some stations.

Network is usually partially connected — however, some redundant connections are desirable for reliability

**********************************************************************Two different switching techniques:**********************************************************************

1. **Circuit Switching**
2. **Packet Switching** 

# Circuit Switching

Dedicated communication path between two stations

There are three phases

- Establishment of connection
- Transferring of data
- Termination of connection

Must have switching capacity and channel capacity to establish connection

Must have intelligence to work out routing

# Packet Switching

A station breaks long message into packets

Packets are sent out to the network sequentially, one at a time

The stream of packets are routed through the network and are delivered to the intended destination.

Two approaches

- ********************************Datagram approach** (each packet follows different paths)
- **************************Virtual approach** (a virtual path is created and all the packets move through it)

# Circuit Switching Approaches

- **Space-Division Switch**
- **Time-Division Switch**
- **TDM Bus**
- **Combinations**

![Untitled](Switched%20Network/Untitled%201.png)

### Space Division Switch

![Untitled](Switched%20Network/Untitled%202.png)

### Multi-stage Space Division Switch

![Untitled](Switched%20Network/Untitled%203.png)

### Time Division Multiplexing

![Untitled](Switched%20Network/Untitled%204.png)

Extensively used in telephone connectivity

### Time Slot Interchange

![Untitled](Switched%20Network/Untitled%205.png)

## Circuit Switching - Properties/Issues

- Once connected, transfer is transparent
- Developed for voice traffic (phone)
- Inefficient
    - Channel capacity dedicated for duration of connection
    - If no data, capacity wasted
- Set up (connected) takes time
- Data rate is fixed — both ends must operate at the same rate

# Packet Switching — Basics

- Data transmitted in small packets
    - Typically 1000 octets (8 bit byte)
    - Longer messages split into series of packets
    - Each packet contains a portion of user data plus some control info
- Control info
    - Routing (addressing) information
- Packets received, stored briefly (buffered) and passed on to the next node
    - Store and forward mechanism

## Packet Switched Network

![Untitled](Switched%20Network/Untitled%206.png)

## Packet Switching — Advantages

1. Line efficiency
    1. Single node to node link can be shared by many packets over time
    2. Packets queued and transmitted as fast as possible
2. Data rate conversion
    1. Each station connects to the local node at its own speed
    2. Nodes buffer data if required to equalize rates
3. Packets are accepted even when network is busy
    1. Delivery may slow down
4. Priorities can be used

## Packet Switching — Datagram

- Each packet treated independently
- Packets can take any practical route
- Packets may arrive out of order
- Packets may get lost or delayed
- Up to receiver to re-order packets and recover from missing packets

![Packet Switching — Datagram approach](Switched%20Network/Untitled%207.png)

Packet Switching — Datagram approach

## Packet Switching - Virtual Circuit

- Preplanned route established before any packets sent
- Call request and call accept packets stablish connection (handshake)
- Each packet contains a virtual circuit identifier instead of destination address
- No routing decisions required for each request
- Clear request to drop circuit
- Not a dedicated path

![Packet Switching — Virtual Circuit Approach](Switched%20Network/Untitled%208.png)

Packet Switching — Virtual Circuit Approach

## VC Switching Table

![Untitled](Switched%20Network/Untitled%209.png)

## Virtual Circuit — Source to Destination

![Untitled](Switched%20Network/Untitled%2010.png)

# Packet Switching — Virtual Circuits vs Datagram

- Virtual Circuits
    - Network can provide sequencing and error control
    - Packets are forwarded more quickly
        - No routing decisions to make
    - Less reliable
        - Loss of node loses all circuits through the node
- Datagram
    - No call setup phase
        - Better if few packets
    - More flexible
        - Routing can be used to avoid congested parts of the network

# Circuit vs. Packet Switching

### Circuit Switched

Bandwidth guaranteed

Circuit capacity not reduced by other network traffic

Circuit costs independent of amount of data transmitted, resulting in wasted bandwidth

Suitable for voice communication 

### Packet Switched

Bandwidth dynamically allocated on as-needed basis

May have concurrent transmissions over physical channel

May have delays and congestion.

More cost-effective, offer better performance

Suitable for data communication