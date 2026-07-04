Lessons:
	HTB - Linux Fundamentals

Linux philosophy - simplicity, modularity, and openness. Creating programs that complete one task well, that can be combined to solve complex problems. 

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
<username>@<hostname><current working directory>$ <- the dollar sign represents a user >

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


Commands

ls - list the files and directories within the current folder 

man ls - (man) displays the manual pages for commands and provides detailed information about their usage 

ls --help  or -h  // to get additional information, -h for a short version, --help for a complete breakdown 

apropos <keyword> searching for the description within a manual page 

Useful resource - https://explainshell.com/


