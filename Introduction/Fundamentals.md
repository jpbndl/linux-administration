# Linux Administration

## What is Linux?
Linux is an operating system and the core of a Linux distribution.

## What is a Linux distribution?
A distribution (distro) is the flavor or toppings on top of **Linux**. Think of Linux as ice cream, and a distro as the flavor, toppings, or how it is served.

Distribution provides different extras, such as:
- Graphical user interface (GUI)
- Software installation and mangement applications
- Security software

## Linux Directory Structure
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

## Shell
Default interface to Linux. Can be access via terminal or CLI.

### Command Line Interface vs GUI
- CLI is more powerful than interface - For instance, renaming 100 files in a GUI will require you to click and rename each file, on the other hand you can just run a command to update all files.
- CLI is always available
- Server distributions do not include GUIs
- Connect over Network
- Desktop distribution have GUIs and CLIs

### Prompt
For normal user: 
[jp@linuxsvr ~]$

For root user: 
[jp@linuxsvr:~]#

*~* represents a **home** directory

- *~jp~* = /home/jp
- *~root* = /root
- *~ftp* = /var/ftp

### Root (Superuser)
- Administrator account
- Normal accounts can only do a subset of the things root can do
- Root access is typically restricted to system administrators
- Root access may be required to install, start or stop an application
- Day to day activities will be performed using a normal account

## Basic Linux Commands
- **pwd** - Display the presnet working directory. Current directory that you are in
- **cd** - Changes the current directory to dir. *cd {dir}*
- **ls** - Lists directory contents
  - **ls -l** - List directory contents using *a*
- **cat** - Display the contents of files, combine multiple files, or create new ones
- **clear** - Clears the screen
- **man** - Displays the online manual for command
  - **space** - Display the next page
  - **q** - Command to quit

> ⚠️ **Note**  
> Linux commands, directories and file are **case-sensitive**.

## Learn How To Fish 
Getting Help at the Command Line

### Display Documentation
-  **man ls** - Navigating man pages
   -  **g** - Move to the top of the page
   -  **space** - Next page
   -  **G** - Move to the bottom of the page
   -  **-k {search}** - Search for the command. For instance *man -k calendar*
   -  **q** - Quit
   
### Environment Variables
- Storage location that has a name and value
- Typically uppercase
- Access the contents by executing:
  - echo $VAR_NAME

### Path
- An environment variable 
- Controls the command search path
- Contains a list of directories
- **which** - To know the location or the full path to the command that you're executing

### Get Help
- Add *-help* to a command to get help, Try *-h* if --help does not work

## Working with Directories
- Containers for other files and directories
- Provide a tree like structure
- Can be access by name or shortcut

### Directory Shortcuts
- **.** - Current directory
- **..** - Parent directory
- **cd** - Change to previous directory
- **/** - Directory separator

### Executing Commands
Execute command in $PATH, in full path or outside the $PATH

- echo $PATH
- cat mydata.txt -
- /bin/cat mydata.txt

### Creating and Removing Directories
- **mkdir* [-p] dir** - Create a directory
- **rmdir* [-p] dir** - Remove a directory
- **rm -rf dir** - Recursively removes directory

### ls Command
- **ls -l** - List all files in long format
- Hidden files begin with a period. Sometimes called "dot files". Hidden files are not displayed by default
  - **-a** - Command is used to show hidden files. Example, *ls -la*
- **ls -F** - Used to reveal file types
  - / - Directory
  - @ - Link
  - * - Executable
- **ls -t** - List files by time
- **ls -r** - Reverse order
- **ls -latr** - Long listing including all files reverse sorted by time
- **ls -R** - List files recursively. Tree commands works similarly with the -R command.
  - **tree -d**
  - **tree -C**
- **ls -d** - List directory name, not contents
- **ls --color** - Colorize the output
- **""** - Use quotes to handle file name with space. For example, ls -l "my file.txt"

### Symbolic Links
- A link points to the actual file or directory
- Use the link as if it were the file
- A link can be used to create a shortcut.
  - Use for long file or directory names
  - Use to indicate the current version of software

## Permissions
- **r** - Read allows file\directory to be read
- **w** - Write allows file\directory to be read
- **x** - Execute allows execution of a file and access to contents and metadata in directories.

### Permission Categories
- **u** - User
- **g** - Group
- **o** - Other
- **a** - All

### Groups
- Every user is in at least one group
- Users can belong to many groups
- Groups are used to organize users
- The *groups* or *id -Gn* command displays a user's groups

### How to read Permissions

-rw-r--r--

- **-rw** - The first segment is for Users
- **r--** - The second segment is for Groups
- **r--** - The third segment is for Other
 
> ⚠️ **Note**  
> Permissions must be in order.

### Changing Permissions
Permissions are also known as modes.
- **chmod** - Change mode command
  - chmod {permission_category}{add_subtract_or_set_permission}{permissions}
  - chmod u+x mycommand.sh - Set execute permission to user
  - chmod u+x,g-r mycommand.sh - Set execute permission to user and remove read permission to groups
  - chmod a=r mycommand.sh - Set read permissions to all

### Numeric Based Permission
- **Value for off** - r=0 w=0 x=0
- **Binary value for on** - r=1 w=1 x=1
- **Base 10 value for on** - r=4 w=2 x=1

| Octal | Binary | String | Description          |
| ----- | ------ | ------ | -------------------- |
| 7     | 111    | rwx    | Read, write, execute |
| 6     | 110    | rw-    | Read, write          |
| 5     | 101    | r-x    | Read, execute        |
| 4     | 100    | r--    | Read only            |
| 3     | 011    | -wx    | Write, execute       |
| 2     | 010    | -w-    | Write only           |
| 1     | 001    | --x    | Execute only         |
| 0     | 000    | ---    | No permissions       |

> ⚠️ **Note**  
> Permissions must be in order.

### Commonly Used Permissions
- **-rwx------** - 700
- **-rwxr-xr-x** - 755
- **-rw-rw-r--** - 664
- **-rw-rw----** - 660
- **-rw-r--r--** - 644

### Working with Groups

Permission on a directory can affect the files in the directory. 

- **chgrp** - Command to change group
  - chngrp it mytext.text

