# Linux Administration

### What is Linux?

Linux is an operating system and the core of a Linux distribution.

### What is a Linux distribution?

A distribution (distro) is the flavor or toppings on top of **Linux**. Think of Linux as ice cream, and a distro as the flavor, toppings, or how it is served.

Distribution provides different extras, such as:
- Graphical user interface (GUI)
- Software installation and mangement applications
- Security software

### Linux Directory Structure
- **/** - "Root", the top of the file system hierarchy
- **/bin** - Binaries and other executable programs
- **/etc** - System configuration files
- **/home** - Home directories. 
- **/opt** - Optional or third party software
- **/tmp** - Temporary space, typically cleared on reboot
- **/usr** - User related programs. Can also have a sub directory like "/bin"
- **/var** - Variable data, most notably log files from the operating system or applications
  
```
/
├── bin
├── etc
├── home
├── opt
├── tmp
├── usr
│   └── bin
└── var
```

### Comprehensive Directory Listing
- **/lib** - System libraries
- **/lib64** - System libraries, 64 bit
- **/sys** - Used to display and sometimes configure the devices known to the Linux kernel
- **/boot** - Files needed to boot the operating system
- **/media** - Used to mount removable media (USBs, CD-ROMs)
- **/mnt** - Used to mount external file systems
- **/root** - The home directory for the root account
- **/mnt** - Used to mount external file systems
- **/proc** - Provides info about running processes
- **/sbin** - System administration binaries
- **/selinux** - Used to display information about SELinux
- **/srv** - Contains data which is served by the system
- **/srv/www** - Web server files
- **/srv/ftp** - FTP files
- **/usr/bin** - Binaries and other executable programs
- **/usr/lib** - Libraries
- **/usr/local** - Locally installed software that is not part of the base operating system
- **/usr/sbin** - System administration binaries
- **/varlog** - Log files

### Application Directory Structures

User application sample

- **/usr/local/jpbndl/bin** - Binaries for *jpbndl* application
- **/usr/local/jpbndl/etc** - Config files for *jpbndl* application
- **/usr/local/jpbndl/lib** - Libraries for *jpbndl* application
- **/usr/local/jpbndl/log** - Log files for *jpbndl* application

Third party application sample

- **/opt/avg/bin** - Binaries for *avg* application
- **/opt/avg/etc** - Config files for *avg* application
- **/opt/avgl/lib** - Libraries for *avg* application
- **/opt/avg/log** /- Log files for *avg* application

Mixed directories sample

- **/etc/opt/myapp** 
- **/opt/myapp/etc**
- **/opt/myapp/lib**
- **/var/opt/myapp**

Shared directory sample

- **/usr/local/bin/myapp**
- **/usr/local/etc/myapp.conf**
- **/usr/local/lib/libmyspp.so**

Company focused sample

- **/opt/google** 
- **/opt/google/chrome**
- **/opt/google/earth**
