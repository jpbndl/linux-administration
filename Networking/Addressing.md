# DHCP, Dynamic and Static Addressing

Network addressing is fundamental to how devices communicate on a network. Linux systems can obtain IP addresses through different methods, each with specific use cases and advantages. Understanding these addressing methods is crucial for:

- **Network planning** - Choose the right addressing strategy for your environment
- **System deployment** - Configure servers and workstations appropriately
- **Troubleshooting** - Diagnose network connectivity issues
- **Security management** - Control which devices can access the network
- **Infrastructure scaling** - Manage IP address allocation efficiently

Linux supports both dynamic addressing (where IP addresses are automatically assigned) and static addressing (where IP addresses are manually configured). DHCP (Dynamic Host Configuration Protocol) is the most common method for automatic IP assignment.

## Table of Contents
- [DHCP, Dynamic and Static Addressing](#dhcp-dynamic-and-static-addressing)
  - [Table of Contents](#table-of-contents)
  - [Network Ports](#network-ports)
  - [/etc/services](#etcservices)
  - [DHCP](#dhcp)
  - [Configure a DHCP Client - RHEL](#configure-a-dhcp-client---rhel)
  - [Assigning a Static IP Address - RHEL](#assigning-a-static-ip-address---rhel)
  - [Manually Assigning an IP Address](#manually-assigning-an-ip-address)
  - [ifup/ifdown](#ifupifdown)
  - [GUI / TUI Tools](#gui--tui-tools)

## Network Ports
Ports identified the services on the host

- When a service starts it binds itself to a port
- Ports 1-1,023 are well-known ports
  - 22 - SSH
  - 25 - SMTP
  - 80 - HTTP
  - 143 - IMAP
  - 389 - LDAP
  - 443 - HTTPS
  - 1,024 ports are unreserved and can be used for your own application

## /etc/services
Map port names to port numbers
- **ssh**     - 22/tcp # SSH Remote Login Protocol
- **smtp**    - 25/tcp # SMTP
- **http**    - 80/tcp # http
- **ldap**    - 389/tcp
- **https**   - 443/tcp

## DHCP
Dynamic Host Configuration Protocol assigns IP address to host on a network
- Each IP is "leased" from the pool of IP addresses the DHCP manages
  - The lease expiration time is configurable on the DHCP server. (1hr, 1day, 1week, etc)
  - The client must renew the lease if it wants to keep using the IP address. If no renewal is received, the IP is available to other DHCP clients.

## Configure a DHCP Client - RHEL
```bash
$ ifconfig -a or ip link 
```

## Assigning a Static IP Address - RHEL
```bash
$ vi /etc/sysconfig/network-scripts/ifcfg-eth0
DEVICE=eth0
BOOTPROTO=static
IPADDR=10.109.155.174
NETMASK=255.255.255.0
NETWORK=10.109.155.0
BROADCAST=10.109.155.255
GATEWAY=10.109.155.1
ONBOOT=yes
```

## Manually Assigning an IP Address
```bash
$ ip address add 10.11.12.13 dev eth0
$ ip link set eth0 up
```

## ifup/ifdown
- Can be used instead of ifconfig/ip
```bash
$ ifup eth0
```

## GUI / TUI Tools
- RedHat
  - nmtui
  - system-config-network
- SUSE
  - YaST
- Ubuntu
  - No official tool available