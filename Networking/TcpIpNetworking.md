# TCP/IP Networking

TCP/IP (Transmission Control Protocol/Internet Protocol) is the fundamental communication protocol suite that powers the internet and most modern networks. For Linux administrators, understanding TCP/IP networking is essential for:

- **Network configuration** - Set up and manage network interfaces and routing
- **Troubleshooting connectivity** - Diagnose and resolve network issues
- **Security implementation** - Configure firewalls and network access controls
- **Service deployment** - Deploy and manage network services and applications
- **Performance optimization** - Monitor and tune network performance
- **System integration** - Connect Linux systems in complex network environments

TCP/IP operates through a layered model, with each layer handling specific aspects of network communication. Linux provides powerful tools and utilities for managing TCP/IP networking, from basic configuration to advanced monitoring and troubleshooting.

## Table of Contents
- [Introduction](#introduction)
- [IP Networking](#ip-networking)
  - [IP Address Breakdown](#ip-address-breakdown)

## Introduction
- TCP/IP
  - Used for network communications
  - TCP = Transmission Control Protocol
  - IP = Internel Protocol
- TCP - Controls data exchange
- IP - Sends data from one device to another
- Hosts
  - Devices on a network that have an IP address

## IP Networking
IP networking need the following:
- IP address
- Subnet mask
- Broadcast address
- octet.octet.octet.octet - values from 0 to 255

### IP Address Breakdown

An IP address consists of four octets (8-bit numbers) separated by dots, forming a 32-bit address:

**Format:** `192.168.1.100`

#### Parts of an IP Address:
- **First Octet (192)** - Network portion (most significant bits)
- **Second Octet (168)** - Network portion (continued)
- **Third Octet (1)** - Network/Host boundary (depends on subnet mask)
- **Fourth Octet (100)** - Host portion (least significant bits)

#### Binary Representation:
```
192.168.1.100 in binary:
11000000.10101000.00000001.01100100
```

#### Address Components:
- **Network Address** - Identifies the network segment
- **Host Address** - Identifies the specific device on the network
- **Subnet Mask** - Determines which bits are network vs host
  - Example: `255.255.255.0` or `/24`
  - Binary: `11111111.11111111.11111111.00000000`

#### Address Classes (Traditional):
- **Class A** - 1.0.0.0 to 126.255.255.255 (8-bit network, 24-bit host)
  - Total addresses: 2^24 = 16,777,216
  - Usable hosts: 16,777,214 (minus network and broadcast)
- **Class B** - 128.0.0.0 to 191.255.255.255 (16-bit network, 16-bit host)
  - Total addresses: 2^16 = 65,536
  - Usable hosts: 65,534 (minus network and broadcast)
- **Class C** - 192.0.0.0 to 223.255.255.255 (24-bit network, 8-bit host)
  - Total addresses: 2^8 = 256
  - Usable hosts: 254 (minus network and broadcast)

#### Special Addresses:
- **Network Address** - All host bits are 0 (192.168.1.0)
- **Broadcast Address** - All host bits are 1 (192.168.1.255)
- **Loopback** - 127.0.0.1 (localhost)
- **Private Ranges**:
  - 10.0.0.0/8 (10.0.0.0 - 10.255.255.255)
  - 172.16.0.0/12 (172.16.0.0 - 172.31.255.255)
  - 192.168.0.0/16 (192.168.0.0 - 192.168.255.255)

#### Classless Inter-Domain Routing (CIDR)
CIDR is a more flexible way to specify IP address ranges than traditional classes
It uses a suffix number (like /24) to indicate how many bits are used for the network portion
For example:
- 192.168.1.0/24 means first 24 bits are network, last 8 bits are for hosts
- /16 means first 16 bits are network, last 16 bits are for hosts
- The smaller the suffix number, the larger the network (more host addresses available)
Common CIDR blocks:
/8  = 16,777,214 hosts (like Class A)
/16 = 65,534 hosts (like Class B)
/24 = 254 hosts (like Class C)

#### How /8 Becomes 16,777,214 Hosts:

**Step 1: Understanding /8**
- `/8` means the first 8 bits are for network
- Remaining 24 bits are for hosts (32 total - 8 network = 24 host bits)

**Step 2: Calculate Total Addresses**
- 24 host bits = 2^24 = 16,777,216 total addresses

**Step 3: Subtract Reserved Addresses**
- Network address (all host bits = 0): 1 address
- Broadcast address (all host bits = 1): 1 address
- Usable host addresses: 16,777,216 - 2 = 16,777,214

**Example with 10.0.0.0/8:**
```
Network:    10.0.0.0      (reserved)
First host: 10.0.0.1      (usable)
Last host:  10.255.255.254 (usable)
Broadcast:  10.255.255.255 (reserved)
```

**Binary Breakdown:**
```
Network bits:  10.xxxxxxxx.xxxxxxxx.xxxxxxxx
               ^^^^^^^^^^^ (8 bits fixed)
                          ^^^^^^^^^^^^^^^^^ (24 bits variable)
```

This is why `/8` provides the same number of hosts as traditional Class A networks. 
