# Files and Editors

## Table of Contents
- [Files](#files)
  - [Delete Files](#delete-files)
  - [Copy Files](#copy-files)
  - [Move and Rename Files](#move-and-rename-files)
  - [Sort Data](#sort-data)
  - [Creating a Collection of Files](#creating-a-collection-of-files)
  - [Compressing Files To Save Space](#compressing-files-to-save-space)
  - [Disk Usage](#disk-usage)
- [Nano Editor](#nano-editor)
  - [Displaying the Contents of Files](#displaying-the-contents-of-files)
  - [Head and Tail](#head-and-tail)
  - [Viewing Files in Real Time](#viewing-files-in-real-time)
  - [Edit files using Nano](#edit-files-using-nano)
- [Vi Editor](#vi-editor)
  - [Vi Command Mode and Navigation](#vi-command-mode-and-navigation)
  - [Vi Insert Mode](#vi-insert-mode)
  - [Vi Line Mode](#vi-line-mode)
  - [Vi Repeating Commands](#vi-repeating-commands)
  - [Vi Deleting Text](#vi-deleting-text)
  - [Vi Changing Text](#vi-changing-text)
  - [Vi Copying and Pasting](#vi-copying-and-pasting)
  - [Vi Undo / Redo](#vi-undo--redo)
  - [Vi Searching](#vi-searching)
  - [Vi Tutor](#vi-tutor)
- [Emacs](#emacs)
  - [Emacs Edit File](#emacs-edit-file)
  - [Emacs Commands](#emacs-commands)
  - [Emacs Navigation](#emacs-navigation)

# Files

### Delete Files
- **rm file** - Remove file
- **rm -r dir** - Remove the directory and its contents recursively
- **rm -f file** - Force removal and never prompt for confirmation

### Copy Files
- **cp source_file destination_file** - Copy source_file to destination_file
- **cp src_file1 [src_fileN ...] dest_dit** - Copy source_files to destination_directory
- **cp -r** - Copy directories only works with -r

Run in interactive mode
```bash
cp -i
```

Copy files to directory
```bash
cp file1 file2 my-directory
```

Copy recursively to destination. If the destination does not exits, it will create the directory.
```bash
cp -r
```

### Move and Rename Files
- **mv** - Move or rename files and directories
- **mv source destination** - Move file from source to destination
- **mv -i source destination** - Move file from source to destination interactively

Rename file1 to file2
```bash
mv file1 file2
```

### Sort Data
- **sort file** - Sort text in file
    - **-k F** - Sort by key. F is the field number
    - **-r** - Sort in reverse order
    - **u** - Sort unique

Reverse sort
```bash
sort -r test.txt
```

Sort second column
```bash
sort -u -k2 test.text
```

### Creating a Collection of Files
Create, extract or list contents of a tar archive using pattern, if supplied

- **tar [-] c|x|t f tarfile [patter]**

**tar Options**
- **c** - Create a tar archive
- **x** - Extract files from the archive
- **t** - Display the table of contents (list)
- **v** - Be verbose
- **z** - Use compression
- **f file** - Use this file
 
Create a tar archive that is compressed
```bash
tar zcf tps.tgz data-dir
```

To work on a compressed file
```bash
tar ztvf tps.tgz
```

### Compressing Files To Save Space
- **gzip** - Compress files
- **gunzip** - Uncompress files
- **gzcat** - Concatenates compressed files
- **zcat** - Concatenates compressed files

```bash
gzip data
```

```bash
gunzip data.gz
```

### Disk Usage
- **du** - Estimates file usage
- **du -k** - Display sizes in Kilobytes
- **du -h** - Display sizes in human readable format

---

# Nano Editor
- Nano is a simple editor
- Easy to learn
- Not as advanced as vi or emacs
- If nano isn't available, look for pico

### Displaying the Contents of Files
- **cat file** - Displays the contents of file
- **more file** -  Browse through a text file
  - **space** - to go to the next page
  - **enter** - go down just one line
  - **q** - to quit
- **less file** - More features than more
  - **space** - to go to the next page
  - **enter** - go down just one line
  - **q** - to quit
  - **/** - search within the file
- **head file** - Output the beggining (or top) portion of file
- **tail file** - Output the endind (or bottom) portion of file
  - **ctrl + c** - to exit

### Head and Tail
- Display only 10 lines by default
- Change this behavior with -n
  - n = number of lines
  - tail -15 file.txt

### Viewing Files in Real Time
Displays data as it is being written to the file
```bash
tail -f file 
```

#### Examples
Find and display the top 10 lines of a file
```bash
head file.txt
```

Find and display the top 2 lines of a file
```bash
head -2 file.txt
```

Find and display the last 10 lines of a file
```bash
tail file.txt
```

Find and display the last line of a file
```bash
tail -1 file.txt
```

### Edit files using Nano
```bash
nano file.txt
```
---

# Vi Editor
- **vi file** - Edit file
  - Always available in linux systems
- **vim file** - Same as vi, but more features
  - vim stands for vi improved
  - Compatible with all the commands found in vi
  - Additional features like syntax highlighting
  - Edit files over the network
- **view file** - Starts vim in read-only mode

### Vi Command Mode and Navigation
- **k** - Up one line
- **j** - Down one line
- **h** - Left one character
- **l** - Right one character
- **w** - Right one word
- **b** - Left one word
- **^** - Go to the begging of the line
- **$** - Go to the end of the line

### Vi Insert Mode
- **i** - Insert at the cursor position
- **I** - Insert at the beggining of the line
- **a** - Append after the cursor position
- **A** - Append at the end of the line

### Vi Line Mode
Begins with ***:***

- **:w** - Writes (saves) the file
- **:w!** - Forces the file to be saved
- **:q** - Quit
- **:q!** - Quit without saving changes
- **:wq!** - Write and quit
- **:x** - Same as :wq
- **:n** - Positions the cursor at line n
- **:$** - Positions the cursor on the last line
- **:set nu** - Turn on line numbering
- **:set nonu** - Turn off line numbering
- **:help** - **This is a subcommand** to get help

### Vi Repeating Commands
- Repeat a command by preceeding it with a number
    - **5k** - Move up a line 5 times
    - **80i<Text><Esc>** - Insert text 80 times
    - **80i_<Esc>** - Insert 80 "_" characters

### Vi Deleting Text
- **x** - Delete a character
- **dw** - Delete a word
- **dd** - Delete a line
- **D** - Delete from current position

### Vi Changing Text
- **r** - Replace the current character
- **cw** - Change the current word
- **cc** - Change the current line
- **c$** - Change the text from the current position
- **C** - Same as c$
- **~** - Reverses the case of a character

### Vi Copying and Pasting
- **yy** - Yank (copy) the current line
- **y<position>** - Yank the <position>
- **p** - Paste the most recent deleted or yanked text

### Vi Undo / Redo
- **u** - Undo
- **Ctrl-R** - Redo

### Vi Searching
- **/<pattern>** - Start a forward search
  - **n** - move to next item
  - **N** - move to the previous item
- **?<pattern>** - Start a reverse search

**~** represents a line beyond the file

### Vi Tutor
```bash
vimtutor
```

---

# Emacs
- Powerful editor
- Some people prefer vi, other emacs.
- Either are great editors
- Use what feels comfortable to you

### Emacs Edit File
- **emacs file** - Edit file
- **C-<char>** - Ctrl while pressing <char>
- **M-<char>** - "Meta" key (alt key) while pressing <char>
- **M-<char>** - Esc, then type <char>

### Emacs Commands
- **C-h** - Help
- **C-x C-c** - Exit
- **C-x C-s** - Save the file
- **C-h t** - Built-in tutorial
- **C-h k <key>** - Describe key

### Emacs Navigation
- **C-p** - Previous line
- **C-n** - Next line
- **C-b** - Backward on character
- **C-f** - Forward one character
- **M-f** - Forward on word
- **M-b** - Backward one word
- **C-a** - Go to the beggining of the line
- **C-e** - Go to the end of the line
- **M-<** - Go to the beggining of the file
- **M->** - Go to the end of the file