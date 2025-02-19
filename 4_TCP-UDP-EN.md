## UDP and TCP: The transport protocols of the Internet

The **IP protocol** enables us to reach a target device in the network via an **IP address**. However, an IP address alone is not enough to ensure that two applications on different devices can communicate with each other in a meaningful way. For this we need **transport protocols**, namely **UDP** and **TCP**

---

### UDP (User Datagram Protocol) - Simple, fast data transfer

The **UDP protocol** is a **connectionless** protocol and works on the **transport layer (layer 4)** of the OSI model

#### Key features of UDP:

- **Connectionless**: UDP sends data without prior connection between sender and receiver
- **No guarantee of delivery:**: There are no mechanisms to check whether the data has actually arrived or been received correctly
- **Minimal overhead**: UDP is simple, lightweight and fast as it performs minimal checks

#### Port numbers in UDP:

- UDP uses **port numbers** to identify applications that are sending or receiving data
- A port is a 16-bit number and has a value range from **1 to 65535** (port 0 is reserved)

#### Real example:

Think of UDP like sending a **postcard**. You write a message on it and send it - quickly, without confirming that it actually arrives. If the card gets lost, you won't know about it

#### Why UDP is still useful:

UDP is especially useful when speed is more important than accuracy. E.G:

- **Video streaming**: If a few data packets are lost, the video is not noticeably disrupted

- VoIP (Internet telephony)**: Small losses in the audio stream do not normally disrupt the call

---

### TCP (Transmission Control Protocol) - Reliable data transmission

The **TCP protocol** is a **connection-oriented** protocol and also works on the transport layer (layer 4) of the OSI model. In contrast to UDP, TCP ensures that data arrives reliably, completely and in the correct order

#### Key features of TCP:

- **Connection-oriented**: Before data is sent, a connection must be established between the sender and receiver
- Reliable delivery**: TCP uses mechanisms such as sequence numbers and acknowledgments (ACKs) to ensure that all data is transmitted correctly
- Error control**: If a data packet is lost, TCP requests a retransmission

#### How TCP ensures reliability:

1. **Sequence numbers**: Each data packet is assigned a sequence number to ensure that it is assembled in the correct order
2. **Acknowledgements (ACKs)**: The recipient confirms receipt of each packet with a so-called ACK message. If the confirmation is missing, the packet is sent again

#### The three-way handshake

Before TCP transmits data, it establishes a connection with the receiver. The so-called **three-way handshake** is used for this purpose:

1. **SYN (synchronization) packet**: The client (e.g. your computer) sends a SYN packet to the server, specifying an initial sequence number
2. **SYN-ACK (synchronization and confirmation) packet**: The server receives the SYN packet and responds with a SYN-ACK packet. The server specifies its own sequence number and confirms the sequence number of the client
3. **ACK (acknowledgement) packet**: The client confirms receipt of the SYN-ACK packet with an ACK packet. The connection is now established and data transmission can begin

![Three-Way Handshake](../images/8.svg)

#### Port numbers in TCP:

- As with UDP, TCP also uses **port numbers** to identify the applications that communicate with each other. The port numbers also range from **1 to 65535**

#### Real example:

Think of TCP like sending a registered letter with return receipt. You send the letter and receive a confirmation as soon as the recipient has received the letter. If the letter does not arrive, it will be redelivered

**Why TCP is useful**:
TCP is ideal for situations where data integrity is critical:

- **Website requests (HTTP/HTTPS)**: Ensuring that all data is received correctly

- File transfers (FTP)**: Prevent parts of the file from being missing or corrupted

- E-mails (SMTP)**: Guarantee that the entire message is delivered

---

### UDP vs. TCP

| Feature | UDP | TCP |
| ------------------- | -------------------------- | ---------------------------------------------------------- |
| **Type** | Connection-free | Connection-oriented |
| **Reliability** | No guarantee | Reliable through uses acknowledgments |
| **Data loss** | Possible | Automatic error correction |
| **Speed** | Fast, low overhead | Slower due to control mechanisms |
| **Use cases** | Video streaming, VoIP, DNS | Websites (HTTP), file transfers (FTP), emails (SMTP) |

#### Summary of use cases:

- UDP:

  - Used when speed is more important than reliability, e.g:
    - DNS requests (fast name resolution)
    - Video streaming (small losses do not interfere)
    - VoIP telephony (minimal delay is crucial)

- TCP:
  - Used when reliability and data integrity are critical, e.g.:
    - Web page requests (HTTP/HTTPS)
    - E-mail communication (SMTP)
    - File transfers (FTP)

---

### TL;DR:

**UDP:** Fast but unreliable - like sending a postcard with no guarantee that it will arrive

**TCP:** Reliable but slower - like sending a registered letter with acknowledgement of receipt