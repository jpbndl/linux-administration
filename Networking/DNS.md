# DNS And Hostnames

## Table of Contents
- [DNS And Hostnames](#dns-and-hostnames)
  - [Table of Contents](#table-of-contents)
  - [IP Address](#ip-address)
    - [Determining Your IP Address](#determining-your-ip-address)
  - [Hostname](#hostname)
  - [DNS hostnames](#dns-hostnames)
    - [Command](#command)
      - [Displaying the hostname](#displaying-the-hostname)
      - [Setting the hostname](#setting-the-hostname)
      - [Resolving DNS Names](#resolving-dns-names)
  - [Hosts file](#hosts-file)
    - [NSS](#nss)

## IP Address

### Determining Your IP Address
```bash
$ ip address
$ ip addr
$ ip a
$ ip address show
$ ip a s
$ ifconfig (deprecated)
```

## Hostname
A host is a device connected to a network. It is a human-readable name for an IP address
Example:
```
fms = 10.102.155.189
```

## DNS hostnames
Translate and IP address into a hostname

- FQDN = fully qualified domain name
  - fms.jpbndl.com
- TLD
  - .com,.net,.jp
- Domains
  - sub-domain.domain.tld
- sub-domain
  - sub-domain.domain.tld

### Command
#### Displaying the hostname
```bash
$ hostname (current hostname)
$ uname -n 
$ hostname -f (display FQDN)
```

#### Setting the hostname
```bash
$ hostname webapp
$ vi /etc/sysconfig/network 
    HOSTNAME=webapp
```

#### Resolving DNS Names
```bash
$ host www.company.com
```

## Hosts file
Contains the list of IP addresses and hostnames located at **/etc/hosts**.

Example 
127.0.0.1 localhost

### NSS
Name Service Switch (NSS) controls the search order for resolutions

