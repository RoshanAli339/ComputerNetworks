# Network Protocol Stack

# Network Protocol Stack

- Application layer → where the end user operated using an application software
- Transport layer → where the signals sent from a the application are brought down to send to the other layers
- Network layer → where the different network devices manage the traffic between the internal networks
- Data link layer → where the data is transferred between machines
- Physical Layer → where the data is converted from analog to digital signals

# Protocols at Different layers

- Application → HTTP, FTP, SMTP [DNS]
- Transport → TCP, UDP, RTP [DNS] [SNMP]
- Network → IPv4, IPv6, MPLS  [SNMP] [ARP, DHCP]
- Data link → Ethernet, Wi-Fi, Bluetooth, UMTS, LTE
- Physical

# OSI Network Model

- Application
- Presentation
- Session
- Transport
- Network
- Data link
- Physical

# TCP/IP - Packet Encapsulation

![Untitled](Network%20Protocol%20Stack/Untitled.png)

## NIC Specifics

- NIC (Network Interface Card)s provide hosts with access to media by using a MAC address
- MAC stands for Media Access Control
- NICs operate at layer 2 → Data link.

## Repeaters

Repeaters are devices used to increase the range or length of data cable between two computers to connect and communicate with each other

## Hubs

A *multi-port repeater* also called a Hub is used to extend range and connect multiple computers to communicate with each other.

***Problems with cascading multiple hubs for larger number of computer systems***

- Hubs share bandwidth between all attached devices, reducing the bandwidth each device receives
- They are layer 1 devices and cannot filter traffic.
- Most LANs use a “broadcast topology”, so every device sees every packet sent down the media.

## Bridges

Bridges also known as ************smarter hubs************ are a better solution to the problems faced with Hubs.

They filter network traffic based on MAC addresses.

## Switches

A Switch (also known as multi-port bridge) can effectively replace multiple bridges in a network.

Another benefit of a switch is that each LAN segment gets dedicated bandwidth. So the computer systems are not effected.

They are layer 2 devices.

## Routers

Routers filter traffic based on IP addresses. The IP address tells the router which LAN segment the ping belongs to. They are network layer devices.

# Few points to note….

- Routers, by default, break up broadcast domain
- ************************************************Broadcast domain**************** —** set of all devices on a network segment that hear all the broadcasts sent on that segment
- Breaking-up of network broadcast is important —  because when a host or server sends a network broadcast, each device on the network “************must”************ read and process that broadcast.
- When a router’s interface receives this broadcast — it discards the broadcast without forwarding it on to other network
- Router also breaks up “************************************************collision domain************************************************” as well.
- Switches aren’t used to create internetworks, they’re employed to add functionality to an internetwork LAN
- Switches only “switches” frames from one port to other within a “switched network”
- Switches break-up *********************collision domains*********************
- ********************************Collision domain******************************** — used to describe a network scenario in which one particular device sends a packet on a network segment, forcing other devices on the same segment to pay attention to it. At the same time, a different device tries to transmit, leading to collision, then both the devices must re-transmit — a situation found in a Hub
- Each and every port on a switch represent its own collision domain