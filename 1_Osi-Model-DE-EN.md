# Basics of the OSI model

The OSI model was developed by the ISO (International Organization for Standardization) and helps network administrators and developers to understand how data flows are structured and how errors in networks can be localized. Each layer has its specific role in data transmission.

## What is the OSI model?

The OSI (Open Systems Interconnection) model was developed by the ISO (International Organization for Standardization) and describes how communication between devices in a computer network works. It consists of **7 layers**, with each layer taking on a specific role in the communication process:

1. **Physical layer**
2. **Security layer**
3. **Network layer**
4. **Transport layer**
5 **Session layer**
6. **Presentation layer**
7. **Application layer**

### Key points:

- Layer 1 is the **Physical Layer**, and Layer 7 is the **Application Layer**.
- Use mnemonics like “All stupid students only drink still peppermint water.”
  This makes it easier to remember the order of the layers - from the application layer (7) to the physical layer (1).
- The numbers of the layers are crucial for understanding terms such as “layer 3 switch” or “layer 7 firewall”.

![OSI model layers](../images/1.svg)

---

## TL;DR

The OSI model has 7 layers that describe how devices communicate on a network; learning these layers will help you understand networking concepts.

## Layer 1: Physical layer

The physical layer, also known as layer 1, deals with the physical connection between devices. This includes the medium, e.g. a cable, and the definition of the binary digits 0 and 1. Data transmission can take place via electrical, optical or wireless signals.

Depending on the medium, the devices use data cables or antennas.

### Task:

- Conversion of bits (0 and 1) into physical signals

- Definition of physical properties such as cables, connectors and frequencies

- Mechanisms for signal transmission and amplification

Examples of bit transmission layer media:

- **Ethernet cable**
- Optical fiber cables**
- WiFi radio bands**: 2.4 GHz, 5 GHz and 6 GHz
- Wireless technologies** WiFi, Bluetooth
- **Hardware repeaters**, hubs, network adapters

![Physical Layer Media](../images/2.svg)

## TL;DR

The physical layer is about the hardware (cables, signals, antennas) that connects devices and transmits raw data in the form of 0s and 1s.

## Layer 2: Data link layer

The physical layer defines a medium for transmitting our signal. The data link layer, i.e. layer 2, represents the protocol that enables data transmission between nodes in the same network segment; in simple terms, it describes an agreement between systems in the same network segment on how to communicate.

### What is a network segment?

A network segment is a group of networked devices that share a common medium or channel for transmitting information. For example, a company office with ten computers connected to a network switch is a network segment.

### task:

- Create and transmit data frames

- Error detection and correction on layer 2

- Use of MAC addresses for device identification

### Examples for layer 2:

- **Ethernet (802.3)** for wired networks
- WiFi (802.11)** for wireless networks
- MAC address (Media Access Control)** Hardware address for identifying a device in the local network