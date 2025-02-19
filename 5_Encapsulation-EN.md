## Encapsulation: Data packaging in the network

**Encapsulation** is the process by which each layer of the network model adds its own **header** (and sometimes a **trailer**) to its data structure. This process ensures that the data is routed correctly and efficiently through the network.

**Why is encapsulation important?

- Each layer focuses only on its specific task.
- This ensures that data is transported error-free from the sender to the receiver.

---

A **header** and **trailer** are like tags or labels that are “stuck” to data to ensure that it can travel safely and correctly through the network.

Imagine you are sending a package:

- **Header**: This is like the address label on the front of the package. It contains important information such as the sender's address, the destination address and the type of contents so that the package does not get lost en route. Contains all the necessary shipping information to ensure the data takes the right route.

- **Trailer**: This is like the sealing or inspection stamp at the end of the parcel. It ensures that the parcel has not been damaged en route and that no data is missing. It is used to check for errors and ensures data integrity. Without these “tags”, the data could be lost or reach the recipient incorrectly.

### Encapsulation steps:

1. **Application data (application layer)**:

   - You enter data, e.g. a search query in a web browser or writing an email.
   - The application layer (e.g. via **HTTP** or **SMTP**) prepares the data for transmission and sends it to the transport layer.

**Example**:
You enter “youtube” in the search bar and press Enter. The search query is packaged by the browser as a data packet via the HTTP protocol.

2 **Transport protocol (transport layer)**:

   - The transport layer (e.g. **TCP** or **UDP**) adds a **header** that contains information about the connection:
     - Sender and destination port numbers
     - Sequence numbers for data order
     - Error control information
   - A **TCP segment** (or **UDP datagram**) is created and forwarded to the network layer.

**Example**:
When you download a file, **TCP** splits the data into small **packets** and makes sure they all arrive correctly. Each **packet** contains a **sequence number**.

3. **Network packet (network layer)**:

   - The network layer adds an **IP header** to the **TCP segment** or **UDP datagram**, which contains important delivery information:
     - **Sender IP address** (e.g. your IP)
     - Destination IP address** (e.g. the IP of the server)
     - Lifetime of the packet** (TTL - Time to Live)
   - The result is an **IP packet** that is forwarded to the data link layer.

**Example**:
Imagine sending a letter and specifying the recipient's address (destination IP) and your own address (sender IP) so that the letter can be sent back if necessary.

4 **Data frame (Data Link Layer)**:
   - The data link layer adds a **header** and a **trailer** to the IP packet to form a **frame**.
     - The header contains the **MAC addresses** of the sender and the destination (local device identifiers).
     - The trailer contains checksums for error detection.

**Example**:
The letter is packed in an envelope with a sender and recipient label and a stamp. It is now ready to be taken to the post office.

Here is a visualization of the encapsulation process:

![Encapsulation Process](../images/9.svg)

1. application data →
1st TCP/UDP segment →
1st IP packet →
1st data frame →
1. physical transmission via cable or radio

---

### Decapsulation: The reverse direction

The reverse process is carried out on the receiver device: **decapsulation**. Each layer removes its respective **header** and passes the **usage data** to the layer above until the original data (e.g. your **search request**) is passed to the **application layer**.

1. the physical layer receives the signal and passes it on to the data link layer.
1. the data link layer removes the **frame header** and **trailer** and passes the **IP packet** to the network layer.
1. the network layer removes the **IP header** and passes the **TCP segment** to the transport layer.
1. the transport layer removes the **TCP header** and passes the **data** to the application layer.

---

## The Life of a Packet

Let's look at an example to better understand the life cycle of a packet:

Example: You search for a video on the website Youtube

1st **Enter the search query**:

   - You type “YouTube Rick-Astley” in the search bar of your browser and press enter.

2. **HTTP request (application layer)**:

   - The web browser uses the **HTTP protocol** to wrap the search request and send it to the **transport layer**....

3. **TCP connection**:

   - The **TCP layer** establishes a connection to the Youtube server (via the three-way handshake). The data is then transferred to the **network layer** as **TCP segments**.

4. **IP addressing (network layer)**:

   - The **network layer** adds **sender** and **destination** IP addresses to ensure that the **packet** is delivered correctly over the Internet.

5. frame creation (security layer)**:

   - The **secure layer** wraps the **packet** into an **Ethernet frame** and sends it over the **local network** (e.g. **WLAN router**).

6. **Router processing:**:

   - The router removes the link layer header and the trailer.
   - It checks the **IP destination address** and forwards the packet to the next router.
   - This process is repeated until the packet reaches the router for the destination server.

7 **Decapsulation at destination**:
   - The Google server performs **decapsulation** until the original **HTTP request** reaches the **application layer** and the search request is processed.

---

### TL;DR

**Encapsulation:** Each layer adds its own header to transport data securely and correctly through the network.

**Decapsulation:** At the destination device, the headers are removed again to extract the original data.

**The life of a packet (Packet Life):** Data flows through different layers, is forwarded over the network and reassembled at the destination device.