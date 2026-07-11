Lessons:
	HTB - Linux Fundamentals

Linux philosophy - simplicity, modularity, and openness. Creating programs that complete one task well, that can be combined to solve complex problems. 

#### Tips 
/etc/passwd can be useful directory to look at for penetration testers as it contains passwords for the user
/etc/shadow - stores the hashes but has stricter security settings 

Commands can be used without being directly accessed like echo ~ (which will show the home directory) or ls ~ to see the files or directories in the home directory. 



# OverTheWire: Bandits 

# Commands:
id -un : prints only the username 
cd . . ( the double dots means - the directory above)
cd /home -> considered an absolute path because it starts from the root directory 
echo "Hello, Linux" > file2.txt -> || The > redirects the output of echo to file2.txt || Also creates the file if it does not exist || >> can be used to add a line to the end of a file

ls -l testdir -> generates a total count of files or directories within the selected directory || -R can be used to see subdirectories when listing || -d shows the permission on directories 

cp -> copy || cp file1.txt file1_copy.txt -> creates a copy of file1 || cp file2.txt /testdir -> creates a copy of file2 and sends it to the /testdir directory || cp  -r testdir testdir_copy -> creates a copy of the file, the -r ensures everything within the directory is copied 

mv -> changes names || mv file1.txt  newname.txt ||  mv newname.txt testdir/ -> moves the file to the selected directory || mv also works on directories just like files || mv testdir/newname.txt ./original_file1.txt -> moves the file out of testdir and changes its name. 

rm -> remove a single file || rm file1.txt || rm -i file1.txt -> gives a warning prompt before deleting || rmdir new_testdir -> only removes empty directories, add -r to remove directories with files | -f can be used to force a delete | -rf can be used to force delete directories or files |

cat -> read out the contents of a file || -n numbers the lines of the output 

head -> read out the beginning of a file, normally 10 lines || -n1 tells only to show the first line || -c1 only prints the first byte of the file  
tail -> reads out the end of a file - has the same commands as head and works as its opposite

diff - command to compare two files and see the difference between the them || can be used to also look at directories -> -r allows for recursively compare subdirectories as well, the output shows that is in one directory but not in the other 

mkdir - makes directories || -p allows you to make parent and subdirectories in the same command || mkdir -p new-dir/subdir


Chown - used to modify both user and group permissions on a file. || -R to operate recursively changing all the permissions of files within directories and subdirectories 
```
-rw-rw-r-- 1 labex labex 0 Jul 29 15:11 example.txt
```

The first tack - means is a normal file, d would be for directory 
Each grouping of three after the fist dash represents different peoples permissions: The first is user, then group, and last others 

If there is a dash then that actions is denied, the order goes read (r), write (w) and execute (x)

Each action is given a numeric value:
- 4 for reading || this allows you to see the contents of a directory 
- 2 for writing || Create new files within a directory 
- 1 Execute  || access files within the directory 
- o No permission 

When using Symbolic notation for Permissions:
- u - user(owner)
- g - group
- o -other
- a - all 
- + symbol adds 
- - minus removes 
```
chmod u+x example.sh
```
The first labex represents the user, the second represents the group. Next is the file size represented here as a zero. 
```
sudo chown root:root example.txt 
```

sudo - represents root privileges
root:root represents the new user and group 

Chmod changes the permissions on a file. || Also works on directories, effecting peoples ability to see the contents of a directory, add files to the directory, and access files within the directory 
```
sudo chmod 700 example.txt
```
The first number is user, then group, than other, the number represents the action numbers added up

useradd - adds user to the system || -m creates a home directory 
```
sudo useradd joker
```
/etc/passwd is the phone book for user information, with information separated by colons : 
```
joker:x:5001:5001::/home/joker:/bin/sh
```
username - joker
password - x (stored securely elsewhere )
user ID - 5001
Group ID - 5001 
Home Directory - /home/joker 
Default shell - /bin/sh 

passwd - sets a user password 
```
sudo passwd joker 
```
This password is stored in /etc/shadow 

usermod - modifies user information || -d specifics a new home directory 
```
sudo usermod -d /home/wayne joker 
```
```
sudo grep -w 'joker' /etc/passwd
This code verifies the changes we made to the user 
- w : used to match the whole word 
```

change the default shell to bash (more advanced shell)
```
sudo usermod -s /bin/bash joker 
```

change group 
```
sudo usermod -aG sudo joker 
- aG : append to Group || adds user to group without removing them from others 
- sudo is the group name is this example 
```

-su allows you to change users: || type exit to return to default user 
```
su - username || su - joker 
```


## Principles 

Everything is a file - All system hardware, processes, and network connections are represented as files, meaning they can be manipulated using the same basic tools 

Small, single purpose programs - simple programs combined together to solve problems 

No captive user interface - most of the work must be done in the terminal, allowing for greater control 

Configuration data stored in a text file - all data stored in files 



## Components 

![](../assets/Pasted%20image%2020260704091239.png)


## Linux Architecture 

![](../assets/Pasted%20image%2020260704091413.png)

## File System Hierarchy 

![](../assets/Pasted%20image%2020260704091508.png)

|**Path**|**Description**|
|---|---|
|`/`|The top-level directory is the root filesystem and contains all of the files required to boot the operating system before other filesystems are mounted, as well as the files required to boot the other filesystems. After boot, all of the other filesystems are mounted at standard mount points as subdirectories of the root.|
|`/bin`|Contains essential command binaries.|
|`/boot`|Consists of the static bootloader, kernel executable, and files required to boot the Linux OS.|
|`/dev`|Contains device files to facilitate access to every hardware device attached to the system.|
|`/etc`|Local system configuration files. Configuration files for installed applications may be saved here as well.|
|`/home`|Each user on the system has a subdirectory here for storage.|
|`/lib`|Shared library files that are required for system boot.|
|`/media`|External removable media devices such as USB drives are mounted here.|
|`/mnt`|Temporary mount point for regular filesystems.|
|`/opt`|Optional files such as third-party tools can be saved here.|
|`/root`|The home directory for the root user.|
|`/sbin`|This directory contains executables used for system administration (binary system files).|
|`/tmp`|The operating system and many programs use this directory to store temporary files. This directory is generally cleared upon system boot and may be deleted at other times without any warning.|
|`/usr`|Contains executables, libraries, man files, etc.|
|`/var`|This directory contains variable data files such as log files, email in-boxes, web application related files, cron files, and more.|
## Prompt 

Format breakdown:
username @ hostname - current working directory>$ <- the dollar sign represents a user >\

home directory represented by <~> tilde and is the default folder when logging on
[~] 

if we switch over to the root user the dollar sign $ turns to a Hash # 

The prompt can be customized in the configuration file<  .bashrc >
	Special characters 
	\d - Date (Mon Feb 6 )
	\D{%Y-%m-%d} - date (YYYY-MM-DD)
	\H - Full hostname
	\j - Number of jobs managed by the shell 
	\n - newline 
	\r - Carriage return 
	\s - Name of the shell 
	\t - Current time 24-hour (HH:MM:SS)
	\T - Current time 12-hour (HH:MM:SS)
	\@ -  Current time 
	\u - Current username
	\w -  Full path of the current working directory 

Useful links:
	Bash-prompt-generator
	Powerline github


# Commands

ls - list the files and directories within the current folder 

man ls - (man) displays the manual pages for commands and provides detailed information about their usage 

ls --help  or -h  // to get additional information, -h for a short version, --help for a complete breakdown 

apropos - keyword  searching for the description within a manual page 

Useful resource - https://explainshell.com/

## System Information 

|**Command**|**Description**|
|---|---|
|`whoami`|Displays current username.|
|`id`|Returns users identity|
|`hostname`|Sets or prints the name of current host system.|
|`uname`|Prints basic information about the operating system name and system hardware.|
|`pwd`|Returns working directory name.|
|`ifconfig`|The ifconfig utility is used to assign or to view an address to a network interface and/or configure network interface parameters.|
|`ip`|Ip is a utility to show or manipulate routing, network devices, interfaces and tunnels.|
|`netstat`|Shows network status.|
|`ss`|Another utility to investigate sockets.|
|`ps`|Shows process status.|
|`who`|Displays who is logged in.|
|`env`|Prints environment or sets and executes command.|
|`lsblk`|Lists block devices.|
|`lsusb`|Lists USB devices|
|`lsof`|Lists opened files.|
|`lspci`|Lists PCI devices
### SSH Logging 

ssh htb-students@[IP Address]

### CheatSheet 

|   |   |
|---|---|
|`man <tool>`|Opens man pages for the specified tool.|
|`<tool> -h`|Prints the help page of the tool.|
|`apropos <keyword>`|Searches through man pages' descriptions for instances of a given keyword.|
|`cat`|Concatenate and print files.|
|`whoami`|Displays current username.|
|`id`|Returns users identity.|
|`hostname`|Sets or prints the name of the current host system.|
|`uname`|Prints operating system name.|
|`pwd`|Returns working directory name.|
|`ifconfig`|The `ifconfig` utility is used to assign or view an address to a network interface and/or configure network interface parameters.|
|`ip`|Ip is a utility to show or manipulate routing, network devices, interfaces, and tunnels.|
|`netstat`|Shows network status.|
|`ss`|Another utility to investigate sockets.|
|`ps`|Shows process status.|
|`who`|Displays who is logged in.|
|`env`|Prints environment or sets and executes a command.|
|`lsblk`|Lists block devices.|
|`lsusb`|Lists USB devices.|
|`lsof`|Lists opened files.|
|`lspci`|Lists PCI devices.|
|`sudo`|Execute command as a different user.|
|`su`|The `su` utility requests appropriate user credentials via PAM and switches to that user ID (the default user is the superuser). A shell is then executed.|
|`useradd`|Creates a new user or update default new user information.|
|`userdel`|Deletes a user account and related files.|
|`usermod`|Modifies a user account.|
|`addgroup`|Adds a group to the system.|
|`delgroup`|Removes a group from the system.|
|`passwd`|Changes user password.|
|`dpkg`|Install, remove and configure Debian-based packages.|
|`apt`|High-level package management command-line utility.|
|`aptitude`|Alternative to `apt`.|
|`snap`|Install, remove and configure snap packages.|
|`gem`|Standard package manager for Ruby.|
|`pip`|Standard package manager for Python.|
|`git`|Revision control system command-line utility.|
|`systemctl`|Command-line based service and systemd control manager.|
|`ps`|Prints a snapshot of the current processes.|
|`journalctl`|Query the systemd journal.|
|`kill`|Sends a signal to a process.|
|`bg`|Puts a process into background.|
|`jobs`|Lists all processes that are running in the background.|
|`fg`|Puts a process into the foreground.|
|`curl`|Command-line utility to transfer data from or to a server.|
|`wget`|An alternative to `curl` that downloads files from FTP or HTTP(s) server.|
|`python3 -m http.server`|Starts a Python3 web server on TCP port 8000.|
|`ls`|Lists directory contents.|
|`cd`|Changes the directory.|
|`clear`|Clears the terminal.|
|`touch`|Creates an empty file.|
|`mkdir`|Creates a directory.|
|`tree`|Lists the contents of a directory recursively.|
|`mv`|Move or rename files or directories.|
|`cp`|Copy files or directories.|
|`nano`|Terminal based text editor.|
|`which`|Returns the path to a file or link.|
|`find`|Searches for files in a directory hierarchy.|
|`updatedb`|Updates the locale database for existing contents on the system.|
|`locate`|Uses the locale database to find contents on the system.|
|`more`|Pager that is used to read STDOUT or files.|
|`less`|An alternative to `more` with more features.|
|`head`|Prints the first ten lines of STDOUT or a file.|
|`tail`|Prints the last ten lines of STDOUT or a file.|
|`sort`|Sorts the contents of STDOUT or a file.|
|`grep`|Searches for specific results that contain given patterns.|
|`cut`|Removes sections from each line of files.|
|`tr`|Replaces certain characters.|
|`column`|Command-line based utility that formats its input into multiple columns.|
|`awk`|Pattern scanning and processing language.|
|`sed`|A stream editor for filtering and transforming text.|
|`wc`|Prints newline, word, and byte counts for a given input.|
|`chmod`|Changes permission of a file or directory.|
|`chown`|Changes the owner and group of a file or directory.|
## Navigation:

pwd - tell you what directory you are currently in 

ls - list all the contents within a directory or files. 
	-l : for more information on those directories and files - the breakdown of the additional information is show in the table 
	-la - list all ( shows hidden files )
	ls -l /directory name/ Example ls -l /var/ to see what files are within this directory 

|**Column Content**|**Description**|
|---|---|
|`drwxr-xr-x`|Type and permissions|
|`2`|Number of hard links to the file/directory|
|`cry0l1t3`|Owner of the file/directory|
|`htbacademy`|Group owner of the file/directory|
|`4096`|Size of the file or the number of blocks used to store the directory information|
|`Nov 13 17:37`|Date and time|
|`Desktop`|Directory name|

Some files may be hidden, which is represented by a dot . in front of the file .bashrc for example. These files can be seen using the ls -la (list all) files or directories 

to look at the connects of a directory we do not have to go to it. We can use the ls -l /directory name/

Cd - can be used to move between directories // Example cd /dev/shm
	cd -  // to jump back to the last directory used 
	We can double tap shift to have the terminal auto complete our request. 
	cd . . // the first dot is the current directory, the second dot is the parent directory - another way of jumping back to the parent directory 


Clear - can be used to clear the command used 

Ctrl+L = allows you to move up and down through passed commands 

Ctrl + R = another way to look through command history 

## Files and Directories 

touch /filename/  || Example touch info.txt 

mkdir /name/ || mkdir Storage 
	 -p allows you to make parent directories automatically || Example mkdir -p Storage/local/user/documents

tree - can be used to look at the structure of your directories || Example: tree . 


We can also create files and list the directories we want to store the file in. The dot is used to start in the current directory 
touch ./Storage/local/user/userinfo.txt

mv file/directory renamed file/directory || the mv command allows us to move and rename files or directories 

Rename File:
	mv info.txt information.txt 

Move files 
	mv information.txt Storage/

Copy Files 
	cp Storage/readme.txt Storage/local/ 

### Editing Files 

Nano Editing
	nano notes.txt 

File Viewing:
	cat filename || cat notes.txt 

VIM: 
	vim 
	 : to enter command mode 
	 :q to quit 
	 :tutor - to enter the vimtutor mode to learn the software 
	

|**Mode**|**Description**|
|---|---|
|`Normal`|In normal mode, all inputs are considered as editor commands. So there is no insertion of the entered characters into the editor buffer, as is the case with most other editors. After starting the editor, we are usually in the normal mode.|
|`Insert`|With a few exceptions, all entered characters are inserted into the buffer.|
|`Visual`|The visual mode is used to mark a contiguous part of the text, which will be visually highlighted. By positioning the cursor, we change the selected area. The highlighted area can then be edited in various ways, such as deleting, copying, or replacing it.|
|`Command`|It allows us to enter single-line commands at the bottom of the editor. This can be used for sorting, replacing text sections, or deleting them, for example.|
|`Replace`|In replace mode, the newly entered text will overwrite existing text characters unless there are no more old characters at the current cursor position. Then the newly entered text will be added.|
|`Ex`|Emulates the behavior of the text editor [Ex](https://man7.org/linux/man-pages/man1/ex.1p.html), one of the predecessors of `Vim`. Provides a mode where we can execute multiple commands sequentially without returning to Normal mode after each command.|
### Finding Files and Directories 

Which - returns the path to a tool - allowing us to see what type of program may be on the system || example - which python

Find - used to find files and folder, but can also act as a filter || find location option 
	Example: find / =type f -name * .config -user root -size +20K -newermt 2020-03-03 -exec ls -al {} \; 2> /dev/null 


|**Option**|**Description**|
|---|---|
|`-type f`|Hereby, we define the type of the searched object. In this case, '`f`' stands for '`file`'.|
|`-name *.conf`|With '`-name`', we indicate the name of the file we are looking for. The asterisk (`*`) stands for 'all' files with the '`.conf`' extension.|
|`-user root`|This option filters all files whose owner is the root user.|
|`-size +20k`|We can then filter all the located files and specify that we only want to see the files that are larger than 20 KiB.|
|`-newermt 2020-03-03`|With this option, we set the date. Only files newer than the specified date will be presented.|
|`-exec ls -al {} \;`|This option executes the specified command, using the curly brackets as placeholders for each result. The backslash escapes the next character from being interpreted by the shell because otherwise, the semicolon would terminate the command and not reach the redirection.|
|`2>/dev/null`|This is a `STDERR` redirection to the '`null device`', which we will come back to in the next section. This redirection ensures that no errors are displayed in the terminal. This redirection must `not` be an option of the 'find' command.|

locate - looks through a database of all files and folder that exist.
	We can update the database with: sudo updatedb
	Search: locate * .config 
	locate may be faster than find, but does not have the same filter capabilities 

### File Description and Redirections:

