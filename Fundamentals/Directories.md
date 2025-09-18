
# Linux Directory Structure

The Linux directory structure follows the Filesystem Hierarchy Standard (FHS), providing a consistent and organized layout across different Linux distributions. Understanding this structure is essential for system administrators as it enables:

- **Efficient navigation** - Quickly locate files and directories
- **System maintenance** - Know where to find configuration files, logs, and binaries
- **Troubleshooting** - Understand where different components store their data
- **Security management** - Apply appropriate permissions and access controls
- **Application deployment** - Install software in the correct locations

The hierarchical structure starts from the root directory (/) and branches into specialized directories, each serving specific purposes in the Linux ecosystem.

## Table of Contents
- [Linux Directory Structure](#linux-directory-structure)
  - [Table of Contents](#table-of-contents)
  - [Overview](#overview)
  - [Comprehensive Directory Listing](#comprehensive-directory-listing)
  - [Application Directory Structures](#application-directory-structures)
  - [Commands](#commands)
    - [Find Command](#find-command)
      - [Patterns](#patterns)
      - [Examples](#examples)
    - [Locate Command](#locate-command)
      - [Examples](#examples-1)
    - [Creating and Removing Directories](#creating-and-removing-directories)

## Overview
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

## Comprehensive Directory Listing
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

## Application Directory Structures

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

## Commands

### Find Command

Recursively finds files in path that match the expression. If no arguments are supplied, it finds all files in the current directory.

#### Patterns
- **-name** - Find files and directories that match pattern
- **-iname** - Like -name, but ignores case
- **-ls** - Performs an *ls* on each of the found items
- **-mtime {days}** - Finds files that are days old
- **-size {num}** - Finds file that are size num
- **-newer {file}** - Finds files that are newer than file
- **-exec {command}** - Run command against all the files that are found

#### Examples

Find 
```bash
find /usr/bin/ -name zic
```

Find case insensitive
```bash
find /usr/bin/ -iname ZIC
```

Find any files that ends in ***c***
```bash
find /usr/bin/ -name "*v"
```

Find files more than 10 days old and less than 90 days old
```bash
find /usr/bin -mtime +10 -mtime -90
```

Find files that begins with ***s*** and using long list format
```bash
find /usr/bin -name "s*" -ls
```

Find files that are greater than 1MB
```bash
find . -size +1M
```

Find all the directories from ***x*** that is newer than ***y***
```bash
find /x -type d -newer /x/y 
```

Find everything in the current directory and execute a command
```bash
find . -exec file {} \;
```

### Locate Command

The locate command is similar to find command

- List files that match pattern
- **Faster** than the ***find*** command
- Queries an index. If it happens that you create a new file, chances is that it may not be in index.
- Results are not in real time
- May not be enabled on all systems or may need manual installation

#### Examples

Find files and directories that have ***uptime*** on their name
```bash
locate uptime
```

Find files and directories that have partial ***upti*** on their name
```bash
locate upti
```

### Creating and Removing Directories
- **mkdir* [-p] dir** - Create a directory
- **rmdir* [-p] dir** - Remove a directory
- **rm -rf dir** - Recursively removes directory