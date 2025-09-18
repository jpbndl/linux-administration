# Permissions

File and directory permissions are the cornerstone of Linux security, controlling who can access, modify, or execute files and directories. Understanding permissions is critical for system administrators to:

- **Secure systems** - Prevent unauthorized access to sensitive files
- **Control access** - Grant appropriate permissions to users and groups
- **Troubleshoot issues** - Resolve permission-related problems
- **Maintain compliance** - Meet security and regulatory requirements
- **Protect data integrity** - Prevent accidental modification or deletion

Linux uses a robust permission system based on users, groups, and three types of access: read, write, and execute. This system applies to both files and directories with different meanings for each.

## Table of Contents
- [Permissions](#permissions-1)
- [Permission Categories](#permission-categories)
- [Groups](#groups)
- [How to read Permissions](#how-to-read-permissions)
- [Changing Permissions](#changing-permissions)
- [Numeric Based Permission](#numeric-based-permission)
- [Commonly Used Permissions](#commonly-used-permissions)
- [Working with Groups](#working-with-groups)
- [Directory Permissions](#directory-permissions)
- [File Creation Mask](#file-creation-mask)
  - [The umask Command](#the-umask-command)
  - [Common unmask modes](#common-unmask-modes)
  - [Special Modes](#special-modes)

## Permissions
- **r** - Read allows file\directory to be read
- **w** - Write allows file\directory to be read
- **x** - Execute allows execution of a file and access to contents and metadata in directories.

## Permission Categories
- **u** - User
- **g** - Group
- **o** - Other
- **a** - All

## Groups
- Every user is in at least one group
- Users can belong to many groups
- Groups are used to organize users
- The *groups* or *id -Gn* command displays a user's groups

## How to read Permissions

-rw-r--r--

- **-rw** - The first segment is for Users
- **r--** - The second segment is for Groups
- **r--** - The third segment is for Other
 
> ⚠️ **Note**  
> Permissions must be in order.

## Changing Permissions
Permissions are also known as modes.
- **chmod** - Change mode command
  - chmod {permission_category}{add_subtract_or_set_permission}{permissions}
  - chmod u+x mycommand.sh - Set execute permission to user
  - chmod u+x,g-r mycommand.sh - Set execute permission to user and remove read permission to groups
  - chmod a=r mycommand.sh - Set read permissions to all

## Numeric Based Permission
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

## Commonly Used Permissions
- **-rwx------** - 700
- **-rwxr-xr-x** - 755
- **-rw-rw-r--** - 664
- **-rw-rw----** - 660
- **-rw-r--r--** - 644

## Working with Groups

- New files belong to your primary group
- **chgrp** - Command to change group
  - chngrp itgroup mytext.text
  - Verify the group by running *ls -l*

## Directory Permissions
- Permission on a directory can affect the files in the directory
- If the file permissions look correct, start checking directory permissions
- Work your way up to the root

## File Creation Mask
- File creation mask determines default permissions
- If no mask were used permissions would be:
  - **777** for directories
  - **666** for file

### The umask Command
Unlike chmod, umask turns off or takes away permission

```bash
umask [-S] [mode]
```
- Sets the file creation mask to mode, if given
- Use -S to for symbolic notation
- umask is ideal for working with members of your group since the permissions allow members of the group to manipulate those files and directories that you create

Example:

If default permission for directory is ***777*** and umask ***002*** is applied, the result will be ***775***

### Common unmask modes
- 022
- 002
- 077
- 007

### Special Modes
- umask 0022 is the same as umask 022
- chmod 0644 is the same as chmod 644
- The special modes are:
  - setuid
  - setgid
  - sticky