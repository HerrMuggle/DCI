# Bytes and bits

A byte is a small unit of data consisting of 8 bits
A bit can only have two values: 0 or 1 (like a light switch: on or off)

## Why are bytes important?

Everything in computers and networks is stored and transmitted using bytes:

- Texts (one letter = 1 byte in ASCII)
- Images (e.g. one pixel color = 3 bytes for RGB)
- Files (the file size is specified in bytes)
- Networks & IP addresses (data is sent in packets of bytes)

## Bytes in IP addresses

An IPv4 address consists of 4 bytes

Example: The IP address `192.168.1.1`

- Each number (192, 168, 1, 1) is one byte

- In binary (0 and 1) it looks like this:

```mathematica
192 = 11000000
168 = 10101000
1 = 00000001
1 = 00000001

0 = 00000000
```

### Why is this important?

- Each byte can only have values from 0 to 255 (because 8 bits result in a maximum of 256 values: 2^8 = 256)
- This is why there is no IP address like 300.168.1.1 (300 is too big for a byte)
- Networks use bytes to define subnets (e.g. 255.255.255.0 for network boundaries)

## Bytes in the system and network admin

### 1. file sizes & memory

- If you manage RAM or hard disks, you will see sizes such as KB, MB, GB, TB
- These units are based on bytes:
  - 1 KB (kilobyte) = 1,024 bytes
  - 1 MB (megabyte) = 1,024 KB (= 1,048,576 bytes)
  - 1 GB (gigabyte) = 1,024 MB (= 1,073,741,824 bytes)
  
#### Why is this important?

- If a server only has 1 GB of RAM and a program needs 2 GB, there are problems
- Backup memory, logs, databases → Everything is based on byte sizes

---

### 2. bandwidth & network speed

- Internet speed is often given in megabits per second (Mbps), but file sizes are in megabytes (MB)

- 1 byte = 8 bits, so:

  - 100 Mbps = 12.5 MB/s (because 100 / 8 = 12.5)

    - If you download a 1 GB file, it takes:

      - 1 GB = 1,024 MB

      - 1,024 MB / 12.5 MB/s = 81.92 seconds → So you always have to convert bits to bytes when planning bandwidth

### 3. network protocols & data packets

- Data on the internet is sent in packets
- Each packet has a header size (in bytes), e.g:

  - IPv4 header: 20 bytes
  - TCP header: 20 bytes
  - UDP header: 8 bytes

#### Why is this important?

- A ping command (ping google.com) sends e.g. 32 bytes of data
- If you configure a firewall, you can set rules based on the packet size (bytes)
- For large amounts of data (e.g. streaming, VoIP), MTU (Maximum Transmission Unit) and Jumbo Frames are important because they determine the number of bytes per packet

## What are hexadecimal numbers (hex)?

Hexadecimal (hex for short) is a number system with a base of 16
This means it has 16 digits and letters:

```mathematica
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

- A stands for 10, B for 11, C for 12 ... up to F for 15

- After F it continues with 10 (which is 16 in the decimal system)  

### Why is hex important?

- Computers work with binary (0 and 1), but binary numbers are long and difficult to read
- Hex is a shorter way of writing binary
- 1 hex character = 4 bits, so:

  - FF (Hex) = 1111 1111 (Binary) = 255 (Decimal)

### Hex in IP and Sysadmin

#### 1. Hex in IP addresses - IPv6

IPv4 uses decimal numbers (e.g. `192.168.1.1`)

But IPv6 uses hex!

Example IPv6 address:

```mathematica
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

- Each group (e.g. 2001) is a 16-bit value in hex
- IPv6 was introduced because IPv4 only has 4.3 billion addresses
- IPv6 has many more addresses due to the larger format

##### Why hex?

- Shorter and more readable than long binary numbers
- Easy to convert to binary for networks & routers

#### 2. Hex in MAC addresses

Every network card (LAN, WLAN) has a MAC address

```mathematica
00:1A:2B:3C:4D:5E
```

- Each group of numbers is one byte (8 bits) in hex
- MAC addresses are used for local networks & device identification
- Hex is used because it is shorter than binary and can be easily converted to bytes

#### 3. Hex in file systems & memory management

- Hex is important everywhere in the system admin area:
  - RAM addresses (e.g. memory addresses in debugging tools)
  - Error codes (0x404 for “Not found”, 0x500 for server errors)
  - File systems (NTFS, FAT32, ext4 store data in hex blocks)

Example for hex in memory addresses:

```nginx
Segmentation fault at 0x7ffde3451a30
```

An error log shows:

- `0x` means hex number
- Hex is used because memory addresses are large, but with hex shorter than binary

#### 4. Hex in encryption & hashes

- Passwords are often stored as hashes in hex (e.g. SHA-256, MD5)
- Example MD5 hash for `password123`:

```
482c811da5d5b4bc6d497ffa98491e38
```

→ Hex representation of a long binary number

##### Why hex?

- More readable than binary, but still secure
- Compact & efficient for storage & transmission

## TL;DR

- Hexadecimal (Hex) is a number system with base 16 (0-9, A-F)
- IPv6 uses hex because it is more readable than binary
- MAC addresses are written in hex (e.g. 00:1A:2B:3C:4D:5E)
- File systems & storage addresses use hex for efficiency
- Hashes & encryption are often stored as hex
- Hex is a compact, more human-friendly representation of binary

## Binary tutorial

Each **0 or 1** is called a **bit**.  
Several bits together form **bytes, memory addresses, data and instructions**.

### Why does a computer only use 0 and 1?

Computers are built from **electrical circuits** that only have two states:

- **0** = No current (OFF)
- **1** = Current is flowing (ON)

Each piece of information in the computer is represented by a **set of bits**

---

## Binary & Hardware: How does it work?

### Transistors - The smallest building blocks

- A **transistor** is a tiny switch that turns **electric current** on or off.
- Millions (or billions) of transistors make up a **processor** or **memory chip**.
- Each **bit** is represented by a transistor:
  - Current flowing (1)
  - No current (0)

**Example:**  
A modern **processor (CPU)** has over **30 billion** transistors!

---

### Memory (RAM, SSD, HDD) & Binary

- RAM (working memory)** stores data as electrical charges (1 or 0).
- **SSD (Solid State Drive)** uses flash memory with **electron traps** that store charge (1) or no charge (0).
- HDD (hard disks)** store bits as **magnetic fields**:

  - North pole on top = **1**
  - South pole on top = **0**

  **Everything you store is binary data.  
  Whether an image, a text or a video - everything is stored in **0 and 1**.

---

### Processors & binary instructions (machine code)

A **processor (CPU)** only understands **binary instructions**.  
These instructions are called **machine code** and consist only of **0 and 1**.

**Example of a CPU instruction (machine language)**:

```mathematica
10110000 01100001
```

This binary code means for the CPU:  
“Load the value **'a'** into the register”.

**Everything a computer does (e.g. execute a program) is based on binary code**

---
## Binary & networks: How is data transmitted?

All data on the Internet (websites, videos, messages) is sent as **binary packets**
Each file is broken down into small **data packets (bytes)**.

**Example of a data packet:**

```mathematica
01001101 01100001 01101001 01101100
```

This means in ASCII:  
`Mail` (an e-mail is transmitted)

---

### Binary & IP addresses

Each IP address is stored and transmitted **binary**

Example of an **IPv4 address:**

`192.168.1.1`

In binary:

```mathematica
11000000.10101000.00000001.00000001
```

**Why?**

- Routers and network cards can process binary much faster than text

---

## How are numbers stored in binary?

### Decimal → Binary

Any **decimal number** can be converted to binary.

**Example for the number 13 in binary:**

```
13 (decimal) = 1101 (binary)
```

Why?

```mathematica
13 = 1×2³ + 1×2² + 0×2¹ + 1×2⁰ = 8 + 4 + 0 + 1 = 13
```

---

### Binary → Text (ASCII)

Computers store letters as **numbers in binary**
This is called **ASCII (American Standard Code for Information Interchange)**.

**Example for the word “Hi” in binary:**

```mathematica
H = 72 → 01001000 i = 105 → 01101001
```

**The computer stores “Hi” as**:  
`01001000 01101001`

---

## TL;DR

- **Hardware**: Each transistor works with 0 & 1
- **Memory**: Hard disks, SSDs, RAM only store binary
- **Networks**: Data is transmitted as 0 & 1
- Programming**: Every programming language is translated into machine code (0 & 1)
- IP addresses & protocols**: Routers only understand binary data

**Without binary there would be no computers, no smartphones and no internet**.

## Hex tutorial

### What is hex?

The **hexadecimal system** (short: **hex**) is a number system with **base 16**:

```mathematica
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

- **A = 10, B = 11, C = 12, D = 13, E = 14, F = 15**
- After `F` it continues with `10` (16 in decimal)

**Why hex?**

- **More compact than binary (1 hex character = 4 bits)**
- **Easy to convert to binary & decimal**
- **Used in hardware, memory, networks & programming**

---

## Hex & Hardware: Why is it used?

### Memory & Addresses

- Computers store data in **binary**, but **hex is more readable**
- Memory addresses (RAM, SSD, CPU registers) use hex**

**Example memory address:**

```nginx
0x7FFDE3451A30
```

- `0x` indicates that this is a **hex number**
- CPUs use these addresses for fast access to memory

---

### Colors & Hex

Colors are often written as **hex codes**

**Example (red in hex & binary):**

```nginx
#FF0000 → 11111111 00000000 00000000
```

- `FF` (255) = Maximum red
- `00` (0) = No green, no blue

**Use hex color codes in CSS & graphic design for precise colors**

---

## Hex & networks

### MAC addresses

Each network card has a **MAC address**, written in hex

**Example MAC address:**

```nginx
00:1A:2B:3C:4D:5E
```

- Each number is **one byte in hex** (8 bits)
- Hex is used because **binary would be too long**

---

- IPv6 uses hex
- IPv6 addresses consist of **hex numbers**

**Example IPv6 address:**

```mathematica
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

- Shorter than a long binary number
- Routers & systems work faster with hex

---

## TL;DR

- Shorter & more readable than binary** (1 hex character = 4 bits)
- **Memory addresses, colors, IPs & networks use hex**
- **CPU instructions & encryption based on hex representation**
- **Hex facilitates debugging, reverse engineering & system analysis**

**Without hex, computer usage & network management would be much more complicated**
