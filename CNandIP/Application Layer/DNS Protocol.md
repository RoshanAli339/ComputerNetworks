# DNS Protocol

# DNS

- The global database system for Internet addressing, mail and other information
    - Much easier to use and memorize
- Concept of domains and sub-domains
    - Domain management is distributed
    - DNS servers translate domain names to IP addresses

## Top Level Domains

• com	– Commercial	
• org	– Non-profit	
• net	– Network service provider
• gov	– US	govt.
• mil	– military	
• edu	– Education	
• au	– Australian	
• at	– Austrian	
• ca	– Canadian	
• dk	– Dutch	
• fr	– French		
• de	– German
• in	– Indian	
• it	– Italian	
• jp	– Japanese	
• kr	– Korean	
• nz	– New	Zealand				
• es	– Spanish	
• tw	– Taiwanese	
• uk	– British	or	Irish
• us	– U.S.

## Domain Name Space

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled.png)

## Domain Names and Labels

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%201.png)

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%202.png)

## Domain Name Structure

Domain Names are arranged in a hierarchical tree-like structure

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%203.png)

## Fully Qualified domain names (FQDNs)

- If a domain name ends in a dot it is assumed to be complete. This is called a *fully qualified domain name* (FQDN) or an absolute domain name.
- If a domain name does not end in a dot, it is incomplete and the DNS resolver may complete this by appending a suffix to the domain name. The rules for doing this are implementation-dependent and locally configurable

## Generic TLDs

- The top-level names are called the generic top-level domains (gTLDs), and can be three characters or more in length
- These names are registered with and maintained  by the **Internet Corporation for Assigned Names and Numbers (ICANN).**
- Examples
    
    ![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%204.png)
    

## Country Domains

- Top-level domains named for the each of the ISO 3166 international 2-character country codes (from *ae* for the United Arab Emirates to *zw* for Zimbabwe). These are called the country domains or the geographical domains
- Many countries have their own second-level domains underneath which parallel the generic top-level domains.

# Distribution of Name Space

## Hierarchy of Name Servers

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%205.png)

## Zones and Domains

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%206.png)

## What is a Zone?

- Domains are broken into zones for which individual DNS servers are responsible.
    - A domain represents the entire set of names/machines that are contained under and organizational domain name
    - A zone is a domain minus any sub-domains delegated to other DNS servers.

## The Concept

- Each domain name is typically served by 2 or more DNS servers for redundancy.
    - Referred to as primary and secondary.
- Only one DNS server should be configured as primary for a zone.
    - Several secondary DNS servers possible.
    - The primary server contains master copy of the data for a zone
    - Secondary servers get copies of this data through zone transfers.

## Zone Transfer

- A primary server loads all information from the disk file
- The secondary server loads all information from the primary server
- When the primary downloads information from the secondary, it is called Zone Transfer

# DNS in the Internet

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%207.png)

## Generic Domains

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%208.png)

## Country Domains

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%209.png)

## Inverse Domain

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%2010.png)

# Name Resolution

## Name Resolution Process

- The commonly used server is BIND (Berkeley Internal Name Domain).
    - Runs under UNIX as a process called ************named.**
- When an application needs some information from the server, it invokes the DNS name resolver
    - DNS translates a fully qualified domain name into corresponding IP addresses
    - Using the command ****************nslookup****************
    - If the name server does not have the information locally, it asks its primary server, and so on.
    - For redundancy, each host may also have one or more secondary name servers which may be queried when the primary fails.

## Hierarchy of Name Servers

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%2011.png)

## Recursive Resolution

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%2012.png)

## Iterative Name Resolution

- Client sequentially sends queries to DNS servers and recieves response.
    - If response if negative, the DNS server to query next is also returned.
    - Unlike recursive name resolution, where only one response is finally returned back to the client.

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%2013.png)

## DNS Full Resolver

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%2014.png)

## Domain Name stub resolver

- *********Stub resolver*********, a routine linked with the user program, that forwards the queries to a name server for processing.
- On most platforms, the stub resolver is implemented by two library routines (or by some variation of these routines): **************************gethostbyname()************************** and ********************************gethostbyaddr()********************************.

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%2015.png)

# DNS Messages

## DNS Resource Records (RR)

- Domain Name System’s distributed database is composed of *********************resource records (RRs)*********************, which are divided into classes for different kinds of networks.
- Resource Records provide a mapping between domain names and ****************network objects.****************
- The most common network objects are the addresses of **************Internet hosts**************, but the Domain name System is designed to accomodate a wide range of different objects.
- A zone consits of a group of resource records, beginening with a ********************************Start of Authority (SOA)******************************** record.
- The SOA record identifies the domain name of the zone
- There will be a name server (NS) record for the primary name server for this zone. There might also be NS records for the secondary name servers.
- The NS records are used to identify which of the anme servers are authoritative.

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%2016.png)

## DNS RR Message Format

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%2017.png)

## DNS Messages

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%2018.png)

## Query and Response Messages

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%2019.png)

## Header Format

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%2020.png)

## Flag Fields

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%2021.png)

QR: Query/ Response

OpCode: 0 standard, 1 inverse, 2 server status

AA: Authoritative

TC: Truncated

RD: Recursion Desired

RA: Recursion Available

rCode: Status of the error

# Types of Records

## Question Record Format

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%2022.png)

## Query Name Format

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%2023.png)

**admin.atc.fhda.edu**

## Resource Record Format

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%2024.png)

## Example 1

A resolver sends a query message to a local server to find the IP address for the host “chal.fhda.edu”.We discuss the query and response messages seperately

### The Query Message

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%2025.png)

### The Response Message

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%2026.png)

## Example 2

A FTP server has recieved a packet from an FTP client with IP address 153.2.7.9. The FTP server wants to verify that the FTP client is an authorized client

### Inverse Query Message

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%2027.png)

### Inverse Response Message

![Untitled](DNS%20Protocol%208f71aacee59044fe95e1dd10adec9240/Untitled%2028.png)