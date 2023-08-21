# HTTP, HTML, TELNET

# Hyper Text Transfer Protocol (HTTP)

- HTTP is the protocol that supports communication between web browsers and web servers
- A “********************Web Server********************” is a HTTP server
- A “**********************Web browser**********************” is a HTTP client
- Most clients/servers run version 1.1, but 1.0 is also in use.
    - RFC 1945 (HTTP 1.0)
    - RFC 2616 (HTTP 1.1)
- HTTP version 1.1 specified a persistent connection by default

## Overview

- “HTTP is an application-level protocol with the lightness and speed necessary for distributed, hypermedia information systems.
- Transport Independence
    - HTTP protocol generally takes place over a TCP connection
    - However, the protocol itself is not dependent on a specific transport layer

## Request - Response

- HTTP has a simple structure
    - client sends a request
    - server returns a reply
- HTTP can support multiple request-reply exchanges over a single TCP connection
- The well known TCP port for HTTP servers is port 80.
    - Other ports also can be used

# Architecture

WWW is a distributed client/server service, in which a HTTP client (browser) can access a service from a HTTP server

- Client (browser)
- Server
- Uniform Resource Locator
- Cookies

## Operation

![Untitled](HTTP,%20HTML,%20TELNET/Untitled.png)

## HTTP client (browser)

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%201.png)

## URL

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%202.png)

## Web Documents

Web documents can be grouped into three broad categories:

- Static
- Dynamic
- Active

## Static Document

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%203.png)

## Dynamic document using CGI (Common Gateway Interface)

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%204.png)

## Dynamic document using Server-site script

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%205.png)

## Active document using Java Applet

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%206.png)

## Active document using Client-Site script

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%207.png)

## HTTP Transaction

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%208.png)

## HTTP: Request and Response messages

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%209.png)

## HTTP Request and Status lines

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%2010.png)

## HTTP Methods

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%2011.png)

## HTTP status codes

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%2012.png)

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%2013.png)

## HTTP Header

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%2014.png)

## Request Headers

### Header

Cache-Control

Connection

Date

MIME-version

Upgrade

Accept

Accept-charset

Accept-encoding

Accept-language

Authorization

From

Host

If-modified-since

If-match

If-not-match

If-range

If-unmodified-since

Referrer

User-agent

Accept-range

Age

Public

Retry-after

Server

### Description

Specifies information about caching

Shows whether the connection should be closed or not

Shows the current data

Shows the MIME version used

Specified the preferred communication protocol

Shows the medium format the client can accept

Shows the character set the client can handle

Shows the encoding scheme the client can handle

Shows the language the client can accept

Shows what permissions the client has

Shows the e-mail address of the user

Shows the host and port number of the server

Sends the document if newer than specified date

Sends the document only if it matches given tag

Sends the document only if it does not match given tag

Sends only the portion of the document that is missing

Sends the document if not changed since specified data

Specifies the URL of the linked document

Identified the client program

Shows if the server accepts the range requested by client

Shows the age of the document

Shows the supported list of methods

Specified the date after which the server is available

Shows the server name and version number

## Entity headers

### Header

Allow

Content-encoding

Content-language

Content-length

Content-range

Content-type

Etag

Expires

Last-modified

Location

### Description

Lists valid methods that can be used with a URL

Specifies the encoding scheme

Specified the scheme

Shows the length of the document

Specified the range of the document

Specifies the medium type

Gives an entity tag

Gives the date and time when contents may change

Gives the date and time of the last change

Specifies the location of the created or moved document

## Example 1

This example retrieves a document. We use the GET method to retrieve an image with the path */usr/bin/image1*. The request line shows the method (GET), the URL, and the HTTP version (1.1). The header has two lines that show that the client can accept images in the GIF or JPEG format. The request does not have a body. The response message contains the status line and four lines of header. The header lines define the date, server, MIME version, and length of the document. The body of the document follows the header.

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%2015.png)

## Example 2

In this example, the client wants to send data to the server. Use the POST method. The request line shows the method (POST), URL, and HTTP version (1.1).  are four lines of headers. The request body contains the input information. The response message contains the status line and four lines of headers. The created document, which is a CGI document, is included as the body

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%2016.png)

## Connecting HTTP server using TELNET

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%2017.png)

## HTTP Proxy Server

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%2018.png)

---

# HTML

- Stands for Hyper Text Markup Language
- Computer language used to create web pages
- HTML file = text file containing markup tags such as `<p>`
- Tags tell web browser how to display a page
- Can have either *.html or *.html file extension

## HTML elements

- Tags are the elements that create the components of a page
- Tags surrounded by angel brackets < >
- Usually come in pairs
    - Example: Start tag `<p>` and end tag `</p>`
- Stuff between is called “element content”
- Tags are not case sensitive
    - New standard is to use lower case

## Your created HTML document

```html
<html>
	<head>
		<title>Document title</title>
	</head>
	<body>
		your page content
	</body>
</html>
```

## Page components

`<!DOCTYPE html>`

- First line of code
- Declaration of version of html

`<html> … </html>`

- Container for the document

`<head>`

`<title> Title of the page</title>`

`</head>`

- Contains the meta data and title of the page

`<body> … </body>`

- Contains the content of the page

## Basic Tags

- Headings
    - `<h1> .. </h1>` to  `<h6> … </h6>`
    - Like in word
- Paragraph
    - `<p> … </p>`
    - Inserts a line space before and after a paragraph
- Link tag
    - Anchor tag `<a> … </a>`
    - 3 kinds
        - Link to page in same folder
        - Link to page in different folder
        - Link to outside webpage on the internet
- Image source tag
    - Empty tag — no closing tag
    - Components of img tag
        - `<img> src=”url” alt=”description of image” />`
        - ******url****** = points to location of the image file
        - ******alt****** = describes image for screen readers
- Division tag
    - `<div> … </div>`
    - Division or section of document
    - Use to group elements to apply formatting or style

---

# TELNET

- **TELNET** is a *protocol* that provides “a general, bi-directionals eight-bit byte oriented communications facility”
- ************telnet************ is a *program* that supports TELNET protocol over TCP.
- Many application protocols are built upon the TELNET protocol

## The TELNET protocol

Reference: **************RFC 854**************

- TCP connection (popular port: 23)
- Data and control over the same connection
- Network Virtual Terminal
    - intermediate representation of a generic terminal
    - provides a standard language for communication of terminal control functions

## Network Virtual Terminal (NVT)

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%2019.png)

## TELNET

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%2020.png)

## Negotiated Options

- ALL NVTs support a minimal set of capabilities
    - Some terminals have more capabilities than the minimal set
- The set of options is not part of the TELNET protocol,
    - so that new terminal features can be incorporated without changing the TELNET protocol
- Two endpoints negotiate a set of mutually acceptable options
    - Line mode vs. character mode
    - echo modes
    - character set (EBCDIC vs. ASCII)

## Control Functions

- TELNET includes support for a series of control functions commonly supported by servers.
- This provides a uniform mechanism for communication of (the supported) control functions.
- Interrupt Process (IP)
    - suspend/abort process
- Abort Output (AO)
    - send no more output to user’s terminal
- Are You There (AYT)
    - check to see if system is still running
- Erase Character (EC)
    - delete last character sent
- Erase Line (EL)
    - delete all input in current line

## Command Structure

- All TELNET commands data flow through the same TCP connection
- Commands start with a special character called the Interpret as Command ****escape**** character
    - The IAC code is 255.
    - If a 255 is sent as data - it must be followed by another 255
- If IAC is found and the next byte is IAC
    - a single bye is represented to application/terminal
- If IAC is followed by any other code
    - the TELNET layer interprets this as a command

## Telnet operations

- You can use the ************telnet************ program to play with the **************TELNET************** protocol
- ************telnet************ is a *******generic******* TCP client
    - Sends whatever you type to the TCP socket
    - Prints whatever comes back through the TCP socket
    - Useful for testing TCP servers (ASCII based protocols)
- Many UNIX systems have these servers running (by default):
    - **********echo**********               port 7 **************discard**************     port 9
    - **************daytime**************          port 13 ******chargen****** port 19

## telnet hostname port

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%2021.png)

## TELNET

![Untitled](HTTP,%20HTML,%20TELNET/Untitled%2022.png)