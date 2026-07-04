Lessons:
	HTB - Linux Fundamentals

Linux philosophy - simplicity, modularity, and openness. Creating programs that complete one task well, that can be combined to solve complex problems. 

# OverTheWire: Bandits 


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
