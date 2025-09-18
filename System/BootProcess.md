# Boot Process

The Linux boot process is a complex sequence of events that transforms your computer from a powered-off state into a fully functional operating system. Understanding this process is essential for system administrators as it helps with:

- **Troubleshooting boot failures** - Identify where the boot process fails
- **System optimization** - Improve boot times and performance
- **Security hardening** - Secure the boot chain against attacks
- **Recovery operations** - Fix broken systems and recover data
- **Custom configurations** - Modify boot parameters and runlevels

The boot process involves several key stages: firmware initialization (BIOS/UEFI), boot loader execution (GRUB), kernel loading, and system initialization (init/systemd). Each stage has specific responsibilities and potential failure points.

## Table of Contents
- [BIOS](#bios)
- [Boot Loaders](#boot-loaders)
  - [Initial RAM Disk](#initial-ram-disk)
- [Linux Kernel](#linux-kernel)
  - [The /boot Directory](#the-boot-directory)
  - [King Ring Buffer](#king-ring-buffer)
- [Runlevels](#runlevels)
  - [Init](#init)
  - [Systemd](#systemd)
  - [Changing runlevels or targets](#changing-runlevels-or-targets)
  - [Rebooting](#rebooting)
  - [Poweroff](#poweroff)

## BIOS

The first piece of software that runs when the computer is turned on. 

- Stands for Basic Input Output System
- Special firmware
- It's operating system independent
  - This is not unique to the linux OS
- Primary purpose is to find and execute the boot loader
- Performs the POST
  - Power-On Self Test
- Knows about bootable devices
  - Hard drives
  - USB drives
  - DVD drives
  - etc
- The boot device search order can be changed

## Boot Loaders
Primary purpose of Boot Loaders is to start the operating system

- LILO
  - Linux Loader
- GRUB
  - Grand Unified Bootloader
  - Replaced LILO
- Boot loaders can start the operating system with different options

### Initial RAM Disk
- initrd
  - initial RAM disk
- Temporary filesystem that is loaded from disk and stored in memory
- Contains helpers and modules required to load the permanent OS file system

## Linux Kernel

### The /boot Directory
- **/boot**
  - Contains the files require to boot Linux 
  - initrd
  - kernel
  - boot loader configuration

### King Ring Buffer
Contains message from the Linux kernel
- dmesg
- /var/log/dmesg

## Runlevels
- **0** - Shuts down the system
- **1,S,s** - Single user mode. Used for maintenance
- **2** - Multi-user mode with graphical interface
- **3** - Multi-user text mode (RedHat/CentOs)
- **4** - Undefined
- **5** - Multi-user mode with graphica interface
- **6** - Reboot

### Init
Runlevels were controlled by init program but **being phased out by systemd**
- Traditional System V init system
- Uses /etc/inittab configuration file
- Sequential startup process
- Slower boot times compared to systemd
- Still found on older systems
  
### Systemd
Uses targets instead of runlevels. Most widely adopted.
- Modern init system and service manager
- Parallel service startup for faster boot times
- Uses unit files instead of shell scripts
- Backward compatible with System V init scripts
- Default on most modern Linux distributions

Systemd targets equivalent to runlevels:
- **poweroff.target** - runlevel 0
- **rescue.target** - runlevel 1
- **multi-user.target** - runlevel 3
- **graphical.target** - runlevel 5
- **reboot.target** - runlevel 6

To see the list of available targets
```bash
cd /lib/systemd/system
ls -l runlevel5.target
```

To change the default run level or target
```bash
systemctl set-default graphical.target
```

### Changing runlevels or targets
- telinit RUNLEVEL
  - telinit 5
- systemctl isolate graphical.target

### Rebooting
- telinit 6
- systemctl isolate reboot.target
- reboot
- shutdown [otpions] time [message]

Reboot using shutdown
```bash
shutdown -r 15:30 "rebooting!"
shutdown -r +5 "rebooting soon!"
shutdown -r now
```

### Poweroff
- telinit 0
- systemctl isolate poweroff.target
- poweroff
- shutdown -h now

Poweroff using shutdown
```bash
shutdown -h 15:30 "shutting down!"
shutdown -h +10 "system going down in 10 minutes"
shutdown -h now
```