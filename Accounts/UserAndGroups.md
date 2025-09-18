# User And Groups Management

## Table of Contents
- [User And Groups Management](#user-and-groups-management)
  - [Table of Contents](#table-of-contents)
  - [User Managements](#user-managements)
    - [Accounts](#accounts)
    - [Username](#username)
    - [Passwords](#passwords)
    - [UIDs](#uids)
    - [GID](#gid)
    - [Comment Fields](#comment-fields)
    - [Home Directory](#home-directory)
    - [Shell](#shell)
    - [Commands](#commands)
      - [useradd](#useradd)
      - [passwd](#passwd)
      - [System or Application Accounts](#system-or-application-accounts)
    - [userdel](#userdel)
    - [usermod](#usermod)
  - [Group Management](#group-management)
    - [Commands](#commands-1)
      - [groups](#groups)
      - [groupadd](#groupadd)
      - [groupdel](#groupdel)
      - [groupmod](#groupmod)
  - [Example](#example)

## User Managements
Linux is muli-user operating system. All accounts can be used at the same time

### Accounts
Accounts includes:
- Userame or login ID
- UID (user ID). This is a unique number
- Default group
- Comments
- Shell
- Home directory location

All of this information is stored in ***/etc/passwd***
```
username:password:UID:GID:comments:home_dir:shell

ec2-user:x:1000:1000:EC2 Default User:/home/ec2-user:/bin/bash
```

### Username
- Less that 8 characters in length by convention
- Case sensitive
- In all lowercase by convention
- Numbers are allowed in usernames
- Do not use special characters

### Passwords
- Encrypted password used to be stored in /etc/passwd
- /etc/passwd is readable by everyone
- Now, encrypted passwords are stored in /etc/shadow
- /etc/shadow is only readable by root
- Prevents users trying to crack passwords

The format of each line in ***/etc/shadow*** is:
```
username:enc_password:last_change:min:max:warn:inactive:expire:reserved
```
- **username**: The user's login name.
- **enc_password**: The encrypted password (or special values like `*` or `!`).
- **last_change**: Days since Jan 1, 1970 that password was last changed.
- **min**: Minimum number of days between password changes.
- **max**: Maximum number of days the password is valid.
- **warn**: Number of days before password expires to warn the user.
- **inactive**: Number of days after password expires until account is disabled.
- **expire**: Days since Jan 1, 1970 when the account will be disabled.
- **reserved**: Reserved field for future use.

**Example:**
```
ec2-user:$6$abc123...:19123:0:99999:7:::
```

### UIDs
- The root account is always UID 0
- UIDs are unique numbers
- System accounts have UIDs < 1000
  - Configured in /etc/login.defs

### GID
- The GID listed in the /etc/passwd is the default group for an account
- New files belong to a user's default group
- Users can switch groups by using the **newgrp** command

### Comment Fields
- Typically contains the user's full name
- In the case of a system or application account, it often contains what the account is used for
- May contain additional information like a phone number
- Also called the GECOS field

### Home Directory
- User login lands on /home directory or "/" if /home directory does not exists

### Shell
- The shell will be executed when a user logs in
- A list of available shells are in /etc/shells
- The shell doesn't have to be a shell
- To prevent interactive use of an account, use /usr/sbin/nologin or /bin/false as the shell
- Shells can be command line applications

### Commands
#### useradd
Create an account using useradd command
```
$ useradd[options]username
```
Options:
- **-c**                - Comments for the account
- **-m**                - Create the home directory
  - When using -m the home directory for the account is created
  - The contents of */etc/skel* are copied into the home directory
  - /etc/skel typically contains shell configuration files. (.profile, .bashrc. etc)
- **-s /shell/path**    - The path to user's shell
- **-g GROUP**          - Specify the default group
- **-G GROUP1,GROUP2**  - Additional groups
- **-d**                - Specify the home directory
- **-r**                - Create a system account
- **-u**                - Specify UID

Example:
```bash
$ useradd -c "New developer" -m -s /bin/bash jp
```

#### passwd
Create a password
```bash
$ useradd -c "New developer" -m -s /bin/bash jp
$ passwd jp
```

#### System or Application Accounts
Not all accounts pertain to a person, some account may be used to run system or applications

Create an account for a system
```bash
$ useradd -c "Apache Web Server" -d /opt/apache -r -s /usr/sbin/nologin apache
```

### userdel
Used to delete an account

Delete user jp and remove the home directory
```bash
$ userdel -r jp
```

### usermod
To update or modify an existing account

```bash
$ usermod[options]username
```
Options:
- **-c**                - Comment account
- **-g GROUP**          - Specify the default group
- **-G GROUP1,GROUP2**  - Additional groups
- **-s /shell/path**    - Path to the user's shell

## Group Management
Group details are stored in the /etc/group. For the root account the defaut group id (GID) is 0
Format of the group file:
```
group_name:password:GID:account1,accountN
```

### Commands
#### groups
To display the groups the user belongs to
```bash
$ groups [username]
```

Display the groups of jp
```bash
$ groups root
```

#### groupadd
Used to create a group
```bash
$ groupadd [options]group_name
```
Add web group
```bash
$ groupadd web
```

Verify the webgroup
```bash
$ tail -1 /etc/group
```

#### groupdel
To delete a group
```bash
$ groupdel group_name
```

Delete web group
```bash
$ groupde web
```

#### groupmod
To change the properties of the group
```bash
$ groupmod [options] group_name
```
Options:
- **-g GID**    - Change the group ID to GID
- **-n GROUP**  - Rename the group to GROUP

## Example

Create a group of tech lead and developers

```bash
$ groupadd tech_lead
$ groupadd developers

$ useradd -c "Lead developer" -g tech_lead -G developers -m -s /bin/bash jp
$ passwd jp
$ useradd -c "Frontend developer" -g developers -m -s /bin/bash jaine
$ passwd jaine

$ groups developers

$ tail -3 /etc/group
```