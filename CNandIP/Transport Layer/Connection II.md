# Connection II

# Connection Establishment

## Handling Delayed Duplicates

- Receiver receives two segments having the same sequence number within a duration T
    - One packet must be the duplicate
    - The receiver discards the duplicate packets

![Untitled](Connection%20II%2055308767a7a34790892b3e6295000cf4/Untitled.png)

- ********************************Adjust the initial sequence numbers properly -******************************** A host does not restart with a sequence number in the forbidden region,, based on the sequence number it used before crash and the time duration T

****************************************Two possible source of problems****************************************

1. A host sends too much data too fast on a newly opened connection
2. The data rate is too slow that the sequence number for a previous connection enter the forbidden region for the next connection

![Untitled](Connection%20II%2055308767a7a34790892b3e6295000cf4/Untitled%201.png)

## Adjust the sending rate based on sequence numbers

The maximum data rate on any connection is one segment per clock tick

- Clock ticks (inter-packet transmission duration) is adjusted based on the sequence acknowledged — ******************************************************************************************************************************************************************ensure that no two packets are there in the network with the same sequence number******************************************************************************************************************************************************************
- We call this mechanism as ****************self-clocking (used in TCP)****************
- Ensures that the sequence numbers do not wrap around too quickly (RFC 1323)
- **We do not remember sequence number at the receiver:** Use a ****************************************three way handshake**************************************** to ensure that the connection request is not a repetition of an old connection request
    - The individual peers validate their own sequence number by looking at the acknowledgement (ACK)
    - ******Positive synchronization among the sender and the receiver******

# Three Way Handshake

- By looking at the ACK, host 1 ensures that sequence number x does not belong to the forbidden region of any previously established connection
- By looking at the ACK in DATA, Host 2 ensures the sequence number y does not belong to the forbidden region of any previously established connection

![Untitled](Connection%20II%2055308767a7a34790892b3e6295000cf4/Untitled%202.png)

## CONNECTION REQUEST is a Delayed Duplicate

![Untitled](Connection%20II%2055308767a7a34790892b3e6295000cf4/Untitled%203.png)

## CONNECTION REQUEST and ACK both are Delayed Duplicates

![Untitled](Connection%20II%2055308767a7a34790892b3e6295000cf4/Untitled%204.png)

## Connection Release — Asymmetric Release

- When one party hangs up, the connection is broken
- This may result in data loss

![Untitled](Connection%20II%2055308767a7a34790892b3e6295000cf4/Untitled%205.png)

## Connection Release — Symmetric Release

- Treats the connection as two separate unidirectional connections and requires each one to be released separately
- Does the job when each process has a fixed amount of data to send and clearly knows when it has sent it,
- What can be a protocol for this?
    - **************************************Host 1: “I am done”**************************************
    - ************************Host 2: “I am done too”************************
- Does this protocol work good always?

# The Two Army Problem

![Untitled](Connection%20II%2055308767a7a34790892b3e6295000cf4/Untitled%206.png)

## Connection Release

![Untitled](Connection%20II%2055308767a7a34790892b3e6295000cf4/Untitled%207.png)

## Connection Release — Final ACK Lost

![Untitled](Connection%20II%2055308767a7a34790892b3e6295000cf4/Untitled%208.png)

## Connection Release — Response Lost

![Untitled](Connection%20II%2055308767a7a34790892b3e6295000cf4/Untitled%209.png)

## Connection Release — Response Lost and Subsequent DRs Lost

![Untitled](Connection%20II%2055308767a7a34790892b3e6295000cf4/Untitled%2010.png)