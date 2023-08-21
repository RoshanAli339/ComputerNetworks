# SMTP and SNMP

# Simple Mail Transfer Protocol (SMTP)

- Protocol originate in 1982 (RFC821, Jon Postel)
- Standard Message Format (RFC882, 2822, D. Crocker)
- Goal: To transfer mail reliably and efficiently

![Untitled](SMTP%20and%20SNMP/Untitled.png)

- SMTP clients and servers have two main components
    - User Agents — Prepares the messages, encloses it in an envelope (Thunderbird, Eudora)
    - Mail Transfer Agent — Transfers the mail across the internet (Sendmail, Exim)
    - Analogous to the postal system in many ways

![Untitled](SMTP%20and%20SNMP/Untitled%201.png)

- SMTP also allows the use of Relays allowing other MTAs to relay the mail
- Mail Gateways are used to relay mail prepared by a protocol other than SMTP and convert it to SMTP

![Untitled](SMTP%20and%20SNMP/Untitled%202.png)

## SMTP keywords

**************Keyword**************

HELO

MAIL FROM:

RCPT TO:

DATA

QUIT

RSET

VRFY

NOOP

TURN

EXPN

HELP

******************Arguments******************

Sender’s Host Domain Name

Email Address of sender

Email of Intended Recipient

Body of the message

Name to be verified

Mailing list to expand

Command Name

## Status Codes

- The server responds with a 3 digit code that may be followed by text info
    - 2## — Success
    - 3## — Command can be accepted with more information
    - 4## — Command was rejected, but error condition is temporary
    - 5## — Command rejected, bad user

## Connection Establishment

![Untitled](SMTP%20and%20SNMP/Untitled%203.png)

## Message Progress

![Untitled](SMTP%20and%20SNMP/Untitled%204.png)

## Connection Termination

![Untitled](SMTP%20and%20SNMP/Untitled%205.png)

## Problem with generic SMTP

It cannot handle with all kinds of data

# Solution: SMTP Extensions

- MIME — Multipurpose Internet Mail Extensions
    - Transforms non-ASCII data to NVT (Network Virtual Terminal) ASCII data
        - Text
        - Application
        - Image
        - Audio
        - Video

![Untitled](SMTP%20and%20SNMP/Untitled%206.png)

## MIME Headers

Located between the Email Header and Body

- MIME-Version: 1.1
- Content-Type: type/subtype
- Content-Transfer-Encoding: encoding type
- Content-Id: message id
- Content-Description: textual explanation of non-textual contents
- Content-Type – Type of data used in the Body
– Text: plain, unformatted text; HTML
– Multipart: Body contains different data types
– Message: Body contains a whole, part, or pointer to a message
– Image: Message contains a static image (JPEG, GIF)
– Video: Message contains an animated image (MPEG)
– Audio: Message contains a basic sound sample (8kHz)
– Application: Message is of data type not previously defined
- Content-Transfer-Encoding – How to encode the message
– 7 bit – no encoding needed
– 8 bit – Non-ASCII, short lines
– Binary – Non-ASCII, unlimited length lines
– Base64 – 6 bit blocks encoded into 8-bit ASCII
– Quoted-printable – send non-ASCII characters as 3 ASCII characters, =##, ## is the hex representation of the byte

## MTAs and Mail Access Protocols

- The MTA delivers email to the user’s mailbox
- Can be complex with numerous delivery methods, routers, and ACLs
- Exim, Postfix, Sendmail
- The Mail Access Protocols are used by the users to retrieve the email from the mailbox
    - POP3
    - IMAP4

## POP vs IMAP

![Untitled](SMTP%20and%20SNMP/Untitled%207.png)

## Post Office Protocol v3

- Simple
- Allows the user to obtain a list of their emails
- Users can retrieve their emails
- Users can either delete or keep the email on their system
- Minimizes server resources

## Internet Mail Access Protocol (IMAP) v4

- Has more features than POP3
- User can check the email header from downloading
- Emails can be accessed from any location
- Can search the email for a specific string of characters before downloading
- User can download parts of an email
- User can create, delete, or rename mailboxes on a server

---

# Simple Network Management Protocol (SNMP)

## Network Management

The development of SNMP was to be kept simple, facilitating rapid deployment of the protocol throughout the Internet community. After the immediate management needs were met, albeit temporarily, by SNMP, thorough research and development could be performed on CMIS/CMIP. Ultimately, this protocol would then be deployed as a permanent solution, replacing SNMP.

Fundamental objective of Simple Network Management Protocol (SNMP) is to manage all aspects of a network, as well as applications related to the network

- ****************Monitor:**************** SNMP implementations allow network administrations to monitor their networks in order to (among other things) ensure the health of the network, forecast usage and capacity, and in problem determination
- **************Manage:************** SNMP provides the capability for network administrations to affect aspects with the network. Values which regulate network operation can be altered, allowing administrations to quickly respond to network problems, dynamically implement new network changes, and to perform real-time testing on how changes may affect their network
- SNMP implements a manager/agent/subagent model, which conforms very closely to the client/server model
- RFC 1157 defines the components and interactions involved in an SNMP community, which include:
    - A Management Information Base
    - An SNMP agent
    - A manager
    - SNMP subagents

![Untitled](SMTP%20and%20SNMP/Untitled%208.png)

- ********SNMP agent******** is the software that runs on a piece of network equipment (host, router, printer, or others) and that maintains information about its configurations and current state in a database.
- Information in the database is described by **********************************************************************************Management Information Bases (IMBs)**********************************************************************************
- An ************************SNMP manager************************ is an application program that contacts an SNMP agent to query or modify the database at the agent
- **************************SNMP protocol************************** is the application layer protocol used by SNMP agents and managers to send and receive data

## SNMP interactions

![Untitled](SMTP%20and%20SNMP/Untitled%209.png)

## Management Information Bases (IMBs)

- A **MIB** specifies the managed objects
- ******MIB****** is a text file that describes managed objects using the syntax of ASN.1 (Abstract Syntax Notation 1)
- ASN.1 is a formal language for describing data and its properties
- In Linux, MIB files are int he directory *****/usr/share/snmp/mibs*****
    - **************Multiple MIB files**************
    - ****MIB-II (defined in RFC 1213) defines the managed objects of TCP/IP networks****

## Managed Objects

- Each managed object is assigned an **********************object identifier(OID)**********************
- OID is specified in a MIB file
- An OID can be represented as a sequence of integers separated by decimal points or by a text string
- When an SNMP manager requests an object, it sends the OID to the SNMP agent

## SNMP Protocol

- SNMP manager and an SNMP agent communicate using the SNMP protocol
    - Generally: Manager sends queries and agent responds
    - Exception: Traps are initiated by agent

![Untitled](SMTP%20and%20SNMP/Untitled%2010.png)

- ************Get-request:************ Requests the values of one or more objects
- ******Get-next-request:****** Requests the value of the next object, according to a lexicographical ordering of OIDs.
- ************************Set-request:************************ A request to modify the value of one or more objects
- ********Get-response:******** Sent by SNMP agent in response to a ***********get-response***********, ********get-next-response, or set-request******** message
- ********Trap********: An SNMP trap is a notification sent by an SNMP agent to an SNMP manager, which is triggered by certain events at the agent

## SNMP versions

- Three versions are in use today:
    - SNMPv1 (1990)
    - SNMPv2c (1996)
        - *******************Adds “GetBulk” function and some new types*******************
        - *****************Adds RMON (remote  monitoring) capability*****************
    - SNMPv3 (2002)
        - *****SNMPv3 started from SNMPv1 (and not SNMPv2c)*****
        - ******************Addresses security******************
- All versions are active
- Many SNMP agents and managers support all three versions of the protocol

## Format of SNMP packets

SNMPv1 Get/Set messages:

![Untitled](SMTP%20and%20SNMP/Untitled%2011.png)

## SNMP Security

- SNMPv1 uses plain text community strings for authentications as plain text without encryption
- SNMPv2 was supposed to fix security problems, but effort de-railed (The “c” in SNMPv2c stands for “community"
- SNMPv3 has numerous security features
    - Ensure that a packet has not been tampered with (********************integrity)********************
    - Ensures that a message is from a valid source (********************authentication)********************
    - Ensures that a message cannot be read by unauthorized (********************privacy)********************