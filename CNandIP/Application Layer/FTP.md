# FTP

# Client-Server Model

- Standard model for developing network applications
- Notion of client and server
    - A server is a process that is offering some service
    - A client is a process that is requesting the service
    - Server or client may be running on different machines
    - Server waits for requests from client(s).

![Untitled](FTP%2023697f215c23486483e11fffcda7c9d4/Untitled.png)

- Typical Scenario:
    - The server process starts on some computer system
        - Initializes itself, then goes to sleep waiting for a client request.
    - A client process starts, either on the same system or on some other system
        - Sends a request to the server
    - When the server process has finished providing its service to the client, the server goes back to sleep, waiting for the next client request to arrive.
- The process repeats
- Roles of the client and the server processes are asymmetric
- Two types of server:
    - ***************************************************Iterative servers***************************************************
    - ******************************************************Concurrent servers******************************************************

## Iterative servers

- Used when the server process knows in advance how long it takes to handle each request and it handles each request itself.
    - Single copy of server runs at all times
    - A client may have to wait if the server is busy.

## Concurrent servers

- Used when the amount of work required to handle a request is unknown; the server starts another process to handle each request
    - A copy of the server caters to a client’s request in a dedicated fashion.
    - As many copies of server as there are client requests

# Using TCP or UDP

- Before start of communication, a connection has to be established between the two hosts
- Five components in a connection
    - Protocol used
    - Source IP address
    - Source port number
    - Destination IP address
    - Destination port number

# Develop a Network Application

- The best way is to use some standard and well-accepted protocol
    - At the data link layer level, use ****************Ethernet****************
    - At the network layer level, use ****IP****.
    - At the transport layer level, use ********TCP.********
    - At the application layer level, use a standard API like the **************************************************Berkeley Socket Interface**************************************************.

# What is a Socket?

- The *******socket*******  is the method for achieving inter-process communication (IPC).
- It is used to allow one process to speak to another (on same or different machine).
    - *******Analogy*******: Like the telephone is used to allow one person to speak to another.

## Basic Idea of Sockets

- When two processes located on two machines communicate, we defines association and socket
    - ***********Association***********: basically a 5-tuple
        - Protocol
        - Local IP address
        - Local port number
        - Remote IP address
        - Remote port number
    - ********Socket:******** also called half-association (a 3-tuple)
        - Protocol, local IP address, local port number
        - Protocol, remote IP address, remote port number

---

# File Transfer Protocol (FTP)

- Facilitates transfer of files over network
- Server/Client model
- FTP often works with
    - TCP
    - Telnet protocol
- Defined as ************RFC959************

## Overview

- FTP uses TCP as a transport protocol to provide reliable end-to-end connections and implements two types of connection in managing data transfers
- The FTP client initiated the first connection, referred to as the control connection, to well-known port 21 (the client’s port is typically ephemeral). It is on this port that an FTP server listens for and accepts new connections
- The control connection is used for all the control commands client user uses to log on to the server, manipulates files, and terminate a session. This is also the connection across which the FTP server will send messages to the client in response to these control commands.
- The second connection used by FTP is referred to as the data connection.
- Typically, the data connection is established on server port 20. However, depending on how the data connection is established, both the client and server might use ephemeral ports
- FTP transfers the data over data connection. FTP only opens a data connection when a client issues a command requiring a data transfer, such as a request to retrieve a file, or to view a list of the files available. It is possible for an entire FTP session to open and close without a data connection ever having been opened.
- The data connection is unidirectional. FTP can transfer data only from the client to the server, or from the sever to the client, but not both.
- The data connection can be initiated from either the client or the server. Data connections initiated by the server are active, while those initiated by the clients are passive.

## Basic Working

- FTP has to be on both server and client computers to work
- Connection
    - Control connection (port 21)
        - Used to send and receive FTP commands
    - Data connection (port 20)
        - Used to upload and download files
- Processes
    - Data Transfer Process (DTP)
        - Establishing the connection and managing the data channel
    - Protocol Interpreter (PI)
        - Interprets the protocol
        - let DTP be controlled using commands received over the control channel
- Transferring mode between server and client
    - Active mode
        - Control connection port: Client: Large port (N>1023); Server: 21
        - Data connection port: Client: N+1; Server: 20
    - Passive mode
        - Control connection port: Client: Large port (N>1023); Server: 21
        - Data connection port: Client: N+1; Server: Large port (P >1023)
- File Transferring mode
    - ASCII mode
        - .txt, .html, .aspm .vbs, .js
    - Binary
        - .doc, .pdf, .mp3 / .mp4
- The client FTP application is built with a protocol interpreter (PI), a data transfer process (DTP), and a user interface
- The server FTP application typically only consists of a PI and DTP

![Untitled](FTP%2023697f215c23486483e11fffcda7c9d4/Untitled%201.png)

- FTP client’s user interface communicates with the protocol interpreter (PI), which manages the control connection
- PI translates any application-specific commands to the RFC architected FTP commands, and then communicates these control commands to the FTP server
- The FTP server’s PI receives these commands, and then initiates the appropriate processes to service the client’s requests. If the requests require the transfer of data, data management is performed by the DTPs on both the client and server applications.
- After the completion of the data transfer, the data communication is closed, and control is returned to the PIs of the client and server applications.
- Only one data transfer can occur for each data connection. If multiple data transfers are required for a single FTP session, one distinct control connection will be opened for each transfer

### FTP Operation — User’s perspective

When using FTP, the user performs some or all of the following operations: 

- Connect to a remote host
- Navigate and manipulate the directory structure
- List files available for transfer
- Define the transfer mode, transfer type, and data structure.
- Transfer data to or from the remote host
- Disconnect from the remote host

## A Typical FTP scenario

![Untitled](FTP%2023697f215c23486483e11fffcda7c9d4/Untitled%202.png)

# Trivial File Transfer Protocol (TFTP)

- TFTP file transfer is a disk-to-disk data transfer, and is an simple protocol used to transfer files. The simplicity of the architecture is deliberate in order to facilitate ease of implementation
- This simplistic approach has many benefits over traditional FTP, including:
    - Use by diskless devices to download firmware at boot time
    - Use by any automated process for which the assignment of a user ID or password is not feasible
    - Small application size, allowing it to be implemented inexpensively and in environments where resources are constricted.
- TFTP is implemented on top of the User Datagram Protocol
- The TFTP client initially send read/write request through well-known port 69. The server and the client then determine the port that they will use for the rest of the connection
- TFTP lacks most of the features of FTP, and instead is limited to only reading a file from a server or writing a file to a server.
- TFTP has no provisions for use authentication; in that respect, it is an insecure protocol

## FTP — Access Commands

![Untitled](FTP%2023697f215c23486483e11fffcda7c9d4/Untitled%203.png)

## FTP — File Management Commands

![Untitled](FTP%2023697f215c23486483e11fffcda7c9d4/Untitled%204.png)

## FTP — Data Formatting Command

![Untitled](FTP%2023697f215c23486483e11fffcda7c9d4/Untitled%205.png)

## FTP — File Transfer Commands

![Untitled](FTP%2023697f215c23486483e11fffcda7c9d4/Untitled%206.png)