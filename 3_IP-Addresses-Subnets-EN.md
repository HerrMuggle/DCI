## IP addresses and subnets

When you hear the term **IP address**, you may think of something like “192.168.0.1” or “172.16.159.243”. Both are valid IP addresses and belong to the **IPv4** version (IP version 4).

### Why do we need IP addresses?

Every device (host) in a network needs a **unique identifier** to be able to communicate with other devices. Without a unique identifier, messages on the network cannot be delivered correctly. In the **TCP/IP protocol**, this identifier is assigned by **IP address**.

#### Analogy:

An IP address works like your **house address:**

- It makes it possible to receive or send letters or parcels (network data).
- Without an address, the letter carrier (the network) would not be able to find your house (the host).

### IPv4 and IPv6: Two versions of IP addresses

- IPv4**: The most commonly used version today. When someone talks about “IP addresses”, they usually mean IPv4.
- IPv6**: A new standard created to overcome the limitation of **IPv4 addresses**. (**IPv4** only has about **4 billion** possible addresses, which is not enough for today's number of devices).

---

### How is an IPv4 address structured?

An IPv4 address consists of **four octets** (4 blocks of 8 bits each, 32 bits in total). Each octet can represent a number between **0 and 255**. For example:

- `192.168.0.1`

Each octet is separated by dots and can be configured differently to identify different networks and devices.

Here is an example of a visualization:

![IPv4 address octet](../images/6.png)

#### Special cases:

- 0: Used for the **network address** to identify an entire network (e.g. `192.168.1.0`).
- 255: Is used for the **broadcast address** to send data to all devices in the network (e.g. `192.168.1.255`).

The broadcast address is used to address **all hosts in the network**.

---

### How many IPv4 addresses are there?

With 32 bits, the total number of possible IPv4 addresses is approximately **2³² (~4 billion)**. However, due to reserved network and broadcast addresses, not all of them can be used.

---

### How to look up your IP address:

You can find out your IP address with these commands:

#### Under Windows:

```bash
ipconfig

# linux
ifconfig

# alt linux
ip address show
# or abbreviated as
ip a s
```

```bash

user@TryHackMe$ ifconfig
[...]
wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST> mtu 1500
        inet 192.168.66.89 netmask 255.255.255.0 broadcast 192.168.66.255
        inet6 fe80::73e1:ca5e:3f93:b1b3 prefixlen 64 scopeid 0x20<link>
        ether cc:5e:f8:02:21:a7 txqueuelen 1000 (Ethernet)
        RX packets 19684680 Bytes 18865072842 (17.5 GiB)
        RX errors 0 discarded 364 overflows 0 frame 0
        TX packets 14439678 bytes 8773200951 (8.1 GiB)
        TX errors 0 discarded 0 overflows 0 carriers 0 collisions 0


```

#### Output 1:

The terminal output shows the following:

- The **IP address** of the host (laptop) is “192.168.66.89”.
- The **subnet mask** is `255.255.255.0`
- The **broadcast address** is `192.168.66.255`.

---

#### Output 2:

Using the command “ip a s”:

- The **IP address** of the host is “192.168.66.89/24”.
- The **broadcast address** is `192.168.66.255`.

---

```bash

user@TryHackMe$ ip a s
[...]
4: wlo1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether cc:5e:f8:02:21:a7 brd ff:ff:ff:ff:ff:ff:ff:ff:ff
    altname wlp3s0
    inet 192.168.66.89/24 brd 192.168.66.255 scope global dynamic noprefixroute wlo1
       valid_lft 36795sec preferred_lft 36795sec
    inet6 fe80::73e1:ca5e:3f93:b1b3/64 scope link noprefixroute
       valid_lft forever preferred_lft forever


```

### Subnet mask Simplified:

A **subnet mask** determines how many devices can be on a particular network. It separates the part of the IP address that identifies the network from the part that identifies the specific device (the host).

- The `/24` means that the **last 24 bits** of the IP address remain constant throughout the subnet.
- For example:
  - IP range in the subnet: `192.168.66.1` to `192.168.66.254`
  - Reserved addresses:
    - `192.168.66.0`: Network address
    - 192.168.66.255': Broadcast address

---

### Private and public IP addresses:

There are two types of **IP addresses**:

1. **Public IP addresses**: Reachable from anywhere in the world.
2. **Private IP addresses**: Only accessible within a local network.

#### Private IP ranges according to RFC 1918:

- **10.0.0.0 - 10.255.255.255** (`10/8`)
- **172.16.0.0 - 172.31.255.255** (`172.16/12`)
- **192.168.0.0 - 192.168.255.255** (`192.168/16`)

#### Analogy:

- A **public IP address** is like your home address - which can be found by anyone in the world.
- A **private IP address** is like an internal address in a company building that is only accessible to employees. To communicate with the outside world, a gateway or router is required.

Routers with NAT (Network Address Translation) translate private IP addresses into a public IP address so that devices in the local network can communicate with the Internet.

---

### What does a router do?

A **router** is like your local post office:

- It receives data packets from your device and forwards them to the correct address.
- When you send a packet to the Internet, the router checks the destination IP address and decides where to forward it.
- On its way to its destination, the packet often passes through several routers, similar to how a letter is transported via several post offices.

**Important:** Routers work on the network layer (layer 3) and use IP addresses to determine the best route to the destination.

![Routing example](../images/7.svg)

### Visualization:

Imagine you are sending a letter:

1. you write the recipient address (IP address) and your sender address (source IP) on the envelope (header).
1. the packet is processed by the router and forwarded to other routers until it reaches the recipient.
1. the packet is opened there (decapsulation) and the recipient reads the data.

---

### TL;DR

1. IP addresses: Uniquely identify devices in a network.
1. subnet masks: Determine the range of IP addresses in a network.
1. private IP addresses: Can only be used within a local network.
1. routers: Forward data between networks using IP addresses, similar to how post offices forward letters.
