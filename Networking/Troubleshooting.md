# Network Troubleshooting

## Table of Contents
- [Network Troubleshooting](#network-troubleshooting)
  - [Table of Contents](#table-of-contents)
  - [Testting Connectivity with Ping](#testting-connectivity-with-ping)
  - [Examine the route](#examine-the-route)
  - [netstat](#netstat)
  - [tcpdump](#tcpdump)

## Testting Connectivity with Ping
If you are having trouble connecting to a host over a network, the first thing you can do is ping the host.
```bash
ping HOST
```

Send 3 packets to google.com
```bash
ping -c 3 google.com
```

## Examine the route
To examine the route, use **traceroute** command
```bash
traceroute -n google.com
```

By default traceroute will try to translate IP addressess to DNS. To omit and speed this up, use **-n**

## netstat 
Can be used to collect a wide variety of network information

- **-n** - Display numerical address and ports
- **-i** - Displays a list of networks interfaces
- **-r** - Displays the route table (netstat -rn)
- **-p** - Display the PID and program used
- **-l** - Display listening sockets (netstat -nlp)
- **-t** - Limit the output to TCP (netstat -ntlp)
- **-u** - Limit the output to UDP (netstat -nulp)

## tcpdump
Examine contents of network traffic to ensure payload are actually being delivered or reaching its destination

```bash
$ sudo tcpdump
```
Options:
- **-n**    - Display numerical addresses and ports
- **-A**    - Display ASCII (text) output
- **-v**    - Verbose mode. Produce more output

```bash
$ sudo tcpdump -Anvvv
```
