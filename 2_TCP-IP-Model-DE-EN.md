## TCP/IP model: The real network model

Now that we have covered the conceptual **ISO OSI model**, let's take a look at the practical and actually implemented **TCP/IP model**. **TCP/IP** stands for **Transmission Control Protocol/Internet Protocol** and was developed by the **US Department of Defense** (**DoD**) in the 1970s.

### Why was the TCP/IP model developed?

The DoD developed this model to keep networks functioning even if parts of the network fail - for example, in the event of a military attack. This **resilience** is achieved through intelligent **routing protocols** that adapt to changes in the network structure.

### Overview of the TCP/IP model:

In contrast to the **ISO OSI model**, which consists of **seven layers**, the **TCP/IP model** has **four layers**:

1. **Application Layer**: Corresponds to a combination of the application, presentation and session layers (layers 5, 6 and 7) of the OSI model.
2. transport layer **: Corresponds to layer 4 of the OSI model. It ensures end-to-end communication.
3rd **Internet Layer**: Corresponds to the network layer (layer 3) of the OSI model. It is responsible for routing and IP addresses.
4. network access layer or link layer **: Combines the physical and link layers (layers 1 and 2) of the OSI model.

### Modern view: Five layers

In more modern networking textbooks, such as Computer Networking: A Top-Down Approach, the TCP/IP model is divided into five layers:

- **Application Layer
- Transport Layer
- **Network Layer
- Link Layer
- **Physical layer **

The difference is that the physical layer (e.g. cables, antennas) is considered an independent layer here, whereas the classic TCP/IP model integrates it into the link layer.

### Mapping of the TCP/IP model to the ISO OSI model

| Layer number | ISO OSI model | TCP/IP model (RFC 1122) | Protocols |
| ------------- | ----------------------- | ----------------------------- | ----------------------------------------------- |
| 7 | Application layer | Application layer | HTTP, HTTPS, FTP, POP3, SMTP, IMAP, Telnet, SSH |
| 6 | Presentation layer | | (integrated into the application layer) |
| 5 | Session layer | | (integrated into the application layer) |
| 4 | Transport layer | Transport layer | TCP, UDP |
| 3 | Network layer | Internet layer | IP, ICMP, IPSec |
| 2 | Data link layer | Link layer | Ethernet (802.3), WiFi (802.11) |
| 1 | Physical layer | (part of the link layer) | Cable, radio, optical transmission |

The TCP/IP model combines several layers of the OSI model in order to simplify it for practical use. This means that there is less separation between presentation, session and application.

### Real example: How the TCP/IP model works

1. **Application layer:**
   You open your web browser and enter “tryhackme.com”. The browser uses the HTTP protocol to connect to the server.

1st **Transport layer:**
   The TCP protocol divides the data into segments, numbers them and determines how errors are recognized and corrected.

1st **Internet layer:**
   The IP protocol adds sender and destination addresses to ensure that the data packets are routed correctly.

1st **Connection layer:**
   The data packets are converted into frames that are sent via the local network (e.g. Ethernet or WiFi).

1st **Physical layer:**
   The frames are converted into electrical signals, optical signals or radio signals and forwarded to the router or the next device.

### Why the TCP/IP model is useful:

- It is actually used in practice and forms the basis of today's Internet.
- It is more robust and flexible than the ISO OSI model and adapts dynamically to network changes.

### Summary

**TL;DR:**

- The TCP/IP model is a simpler, more practical version of the OSI model with four layers (application, transport, Internet, connection) and was developed to ensure network resilience.

- It consists of four main layers: Application, Transport, Internet and Connection.