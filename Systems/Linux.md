Lessons:
	HTB - Linux Fundamentals

Linux philosophy - simplicity, modularity, and openness. Creating programs that complete one task well, that can be combined to solve complex problems. 

#### Tips 
/etc/passwd can be useful directory to look at for penetration testers as it contains passwords for the user
/etc/shadow - stores the hashes but has stricter security settings 

Commands can be used without being directly accessed like echo ~ (which will show the home directory) or ls ~ to see the files or directories in the home directory. 



# OverTheWire: Bandits 

# Commands:

apropos - helps finds commands related to keywords. 

id -un : prints only the username 

cd . . ( the double dots means - the directory above) || cd ~ -> go to home directory || cd -   Goes to previous directory || cd -> another way to home directory 
cd /home -> considered an absolute path because it starts from the root directory 

pwd -> working directory path || -L logical path || -P physical path

echo "Hello, Linux" > file2.txt -> || The > redirects the output of echo to file2.txt || Also creates the file if it does not exist || >> can be used to add a line to the end of a file || -e allows for the interpretation of backslashes used to create new lines \n 

ls -l testdir -> generates a total count of files or directories within the selected directory || -R can be used to see subdirectories when listing || -d shows the permission on directories  || -t -> the most recently modified first || \*/ shows the contents of the next subdirectory || --color=never -> no color 

cp -> copy || cp file1.txt file1_copy.txt -> creates a copy of file1 || cp file2.txt /testdir -> creates a copy of file2 and sends it to the /testdir directory || cp  -r testdir testdir_copy -> creates a copy of the file, the -r ensures everything within the directory is copied 

touch - creates files
```
touch note_{1..5}.txt - creates five notes starting at 1 through 5 
```
mv -> changes names || mv file1.txt  newname.txt ||  mv newname.txt testdir/ -> moves the file to the selected directory || mv also works on directories just like files || mv testdir/newname.txt ./original_file1.txt -> moves the file out of testdir and changes its name. 

rm -> remove a single file || rm file1.txt || rm -i file1.txt -> gives a warning prompt before deleting || rmdir new_testdir -> only removes empty directories, add -r to remove directories with files | -f can be used to force a delete | -rf can be used to force delete directories or files |

cat -> read out the contents of a file || -n numbers the lines of the output 

head -> read out the beginning of a file, normally 10 lines || -n1 tells only to show the first line || -c1 only prints the first byte of the file  
tail -> reads out the end of a file - has the same commands as head and works as its opposite

diff - command to compare two files and see the difference between the them || can be used to also look at directories -> -r allows for recursively compare subdirectories as well, the output shows that is in one directory but not in the other 

mkdir - makes directories ||
-p allows you to make parent and subdirectories in the same command || mkdir -p new-dir/subdir 
-m 777 allows you to set the permissions of the directory when it is being made 
-v -> verbose, prints messages about the directories being made 

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

passwd - sets a user password || -l to lock a password || -u to unlock a password || an exclamation mark in the user profile means the account is locked 
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

userdel - to delete a user || -r removes the user's home directory and mail spool

uname - prints system information || -a prints all information 

uptime - Tells how long the system has been running 

top - display linux processes 

grep - find information || -i to make something not case sensitive | -E to look for multiple names
```
grep -iE 'fail|error'
```

date - tells the date on the local machine || cal - for calendar 

expr - allows for basic arithmetic math || expr 5 + 3 

figlet - commands turn into ASCII Text 

clear - clears the terminal screen

type - tells you the type of command it is
```
type cd -> cd is a shell builtin
```
- built in commands 
- external commands ls 
groupadd - creates new groups || may need the sudo command to work 

##### Wildcards 
Asterix \* is used to match any character  
```
ls \* .txt -> shows all files ending in .txt
```

? - matches any single character 
\[abc] - matches any one character listed in the brackets

Here Document 
```
cat >> EOF < multiline.txt -> this creates a here document allowing the user to write multiple lines, ending once the delimiter (in this case EOF) is written by its self 
```

Find - used to locate files 
```
find . -name "/*.txt" -> show all the files ending in txt in current directory 
```

source -> used to update the shell without having to reset it. 
##### Environment Variables 
creating variables  || A shell variable, which can only be accessed in the terminal 
```
my_var=var value || my_var="Hello World" -> there must be no spaces 
```
view variable value || the $ tells the shell to substitute the value of the variable 
```
echo $my_var 
```
env -> shows current environment variables 
export -> creates a environmental variable 
```
export MY_ENV_VAR="This is an environment variable"
```


![](../assets/Pasted%20image%2020260712160732.png)

Adding a directory to the PATH variable 
```
export PATH="$PATH:$HOME/my_scripts
: -> used to seperate directories 

```
This allows the script to be run in any directory || you have to remember to change the file permission to have executable rights 

To make a variable permanent you have to add it to the startup file, which depends on the shell being used || if zsh -> .zshrc || if bash -> .bashrc

$HOME -> pints to the home directory of the current user 

$USER -> Contains the username of the current user 

$SHELL -> Specifies the user's default shell

$PWD -> contains the path to current directory 

$TERM -> specifies the type of terminal to emulate when running the shell

unset -> used to remove variables || -v to ensure you are not deleting something important || this does not remove it from the .zshrc file, so the variable will return on the next shell
```
unset MY_ENV_VAR
```

##### Package and Compressions 
tar - commonly used to create compressed archive files on disk || using the .gz extension 
```
tar -cfz archive.tar.gz file1 fil2 
```
-c : creates a new archive || -z : compresses the archive using gzip || -f : specify the filename of the archive 
```
tar -cvf test_archive.tar test_dir
-v -> verbose, prints outs the name of the files its adding to the archive 
```

```
tar -tvf test_archive.tar 
-t contents of archive 
-v verbose 
-f from the file 
```

```
tar -xvf test_archive.tar -C extracted_tar
-x extract files 
-C change to the selected directory before extracting files 
```

gzip to compress tar files. 

```
tar -xzvf test_combined.tar.gz -C extracted || extracts compressed files 
```

zip -> more compatible with windows machines 
```
zip -r test_archive.zip test_dir 
-r -> recursive 

unzip -d unzipped_files test_archive.zip 
-d -> points to the directory, which unzip will create 
```

##### File Systems and Disk Management 
df (disk free) command for checking disk space usage on Linux machines 
```
df -h 
-h makes it more readable
```
du -> (disk usage) shows which directories and files are taking up the most space 
```
du -h ~
-s -> can be added to see a summary report 
```
```
du -h --max-depth=1 ~ 
gives a summary of only the immediate subdirectories 

du -h ~ | sort -rh | head -n 10 
This command gives a list of the top 10 file sizes within the selected directory 
```

dd - used to create virtual disk 
```
dd if=/dev/zero of=virtual.img bs=1M count=256

dd -> utility for copying and converting files 

if=/dev/zero -> "input files is /dev/zero" || A special file that provides endless zeros 

of=virtual.img -> output file is virtual.img

bs=1M -> set the block size to 1 megabyte 
cout - 256 -> copy 256 blocks resulting in a 256MB file


```
formatting 
```
sudo mkfs.ext4 virtual.img

this creates a file system within our folder following the .ext4 format 
```
Create mounting directory
```
sudo mkdir /mnt/virtualdisk
```
Mounting virtual disk
```
sudo mount -o loop virtual.img /mnt/virtualdisk

-o loop -> treat our files as if it were a real disk device 

```
Check work 
```
mount | grep virtualdisk
```
dismount 
```
sudo umount /mnt/virtualdisk
```

fdisk - for viewing partition information || also creating, deleting and modifying partitions 
```
sudo fdisk -l
```

##### Sequence Control and Pipeline:

&& - means and, this tells Linux to run the next command if the first one was successful 
```
date && ls ~
```
Two lines || -> is the logical OR operator, it tells Linux to run the next command if the first command fails 

Pipelines -> allow you to connect the output of one command into the input of another and is done with the | single line 
```
ls -l /etc | grep '^d' | wc -l 

ls -l /etc -> list the contents of /etc
grep '^d' -> filters for lines starting with d (directories)
wc -l -> counts those lines 
```

cut - used to extract specific parts of each line of a file
```
cut -d: -f1,6 /ect/passwd | head -n 5

-d: -> is the delimiter set to seperate charactes after each : 
-f1,6 -> extract the 1st and 6th field ( corresponding to the username and home diectory)
```
wc (word count) useful for counting lines, words and characters in text
```
wc -l /etc/passwd -> output is a number 
-l -> count lines 

head -n 1- /etc/passwd | wc -w 
-w -> count words 
```

Sort - used to sort lines of text 
```
sort -t: -k3 -n /etc/passwd | head -n 5 

-t: -> use : as a field seperator 
-k3 -> sort based on the third field
-n -> sort numerically 
```
uniq - used to remove or identify duplicate lines in sorted text
```
cut -d: -f7 /etc/passwd | sort | uniq 

-c -> option shows the number of occurrences 
```

##### Simple Text Processing 
tr (translate) tool used to translate or delete characters in a text stream
```
echo 'hello labex' | tr -d 'olh' -> outcome e abex
-d -> delete specified characters 
-s -> removes duplicate characters 

echo 'hello labex' | tr '[:lower:]' '[:upper:]' -> changes lowercase to upper case 

```
col - used to filer reverse line feeds from input 
```
cat /etc/protocols | col -x | cat -A | head -n10

-x -> convert tabs to spaces 

outcome is to change the ^I character within the protocol output to spaces 
```
Join - used to join lines of two files on a common field 
```
Join fruits.txt colors.txt
```
paste -> used to merge lines of files 
```
paste fruits.txt colors.txt taste.txt
-d ':' can be used to set a new deliminator 
-s -> serializes the paste 
```

##### Data Stream Redirection 

![](../assets/Pasted%20image%2020260713134530.png)

```
cat documents/test.c nonexistent.c > output.log 2 > error.log

combined_output.log 2>&1cat 

short hand 
&> another_combined_output.log
```

/dev/null (bit bucket or black hole) -> is a special file that discards all data written to it
```
ls -l > /dev/null

clear contexts of a file 

cat /dev/null > combined_output.log
```

##### Text Processing and Regular Expressions 

^ -> symbol matches the start of a line, so the code below matches lines that begin with - lab
```
grep "^lab" practice.txt

-i -> can be used to make the search case-insensitive
-n -> will show the line number of matches 

grep -C 1 "exlab" practice.txt

-C 1 -> shows one line before and after the context 
-v -> inverts the matches, showing lines that don't contain the pattern

grep "lab[ex]\*" practice.txt
[ex]\* -> is a regex that matches zero or more occurances of either e or x 
```

sed (stream editor) - used to parse and transform text 
![](../assets/Pasted%20image%2020260713143316.png)

Important to understand that forward slashes (/) are used as separators between command parts, while bask slashes (\) are used for escape characters or command terminators 

```
sed 's/Hello/Hi/' sed_test.txt -> outcome, hello is replaced with Hi in the file, one the first occurance of the word on each line 
-g -> makes it global replaceing all the Hellos within the file with Hi

Normally this would only modify the output, not the file itself. To keep the changes add 
-i 

sed '2d' sed_test.txt -> outcome deletes the 2nd line 
d - stand for delete

sed '1i\First line' sed_test.txt -> inserts First line before the first line of the file || notice the backslash used here as a command deliminator
i - stand for insert 

sed '$a\Last line' sed_test.txt
$ - represents the last line
a = append command 

-e can be used for mulitple substitutions in the same command 
sed -e 's/Hi/Hello/g' -e 's/labex/LabEx/g' sed_test.txt
```

awk - treats each line of input as a record and each word on that line as a field
```
awk '{print $1}' awk_test.txt -> outcome prints the first field 
$0 -> refers to the entire line
$1 -> first field 
$2 -> second field || and so on
awk '{print $1, $2}' awk_test.txt -> multiple fields
```

people over 28 
```
awk '$2 > 28 {print $1 " is over 28"}' awk_test.txt
```

calculates and prints the average age, skipping the header row
```
awk 'NR > 1 {sum += $2} END {print "Average age:", sum/(NR-1)}' awk_test.txt
```

##### Software Installation on Linux 
best practice, before installing you update the system
```
sudo apt update
apt - package management command 

sudo apt install w3m -y 
w3m - name of package
-y -> flag automatically answer yes if prompted

apt-cache search "text editor" -> to search for a package you many need without knowing the name 

sudo apt remove w3m -y -> removes the package selected, but leaves the configuration files 

sudo apt purge w3m -y -> removes the package and configuration files 

sudo apt autoremove - y -> removes leftover dependencies from deleted packages 
```

.deb file installs 
need to use wget to get from the internet 

check package 
```
dpkg -I tree_2.0.2-1_amd64.deb

sudo dpkg -i tree_2.0.2-1_amd64.deb -> install the package

sudo apt -f install -> this will install any missing dependencies tr
```

##### File Content Operations 
```
cat -E filename -> puts a dollarsign $ when a line has ended 
```

more -> help navigate large files 
	space -> to move to the next page 
	Enter -> move down one line 
	b -> go back one page 
	q -> to quit and return to the prompt 

```
more +100 -> start on line 100 

more -10 -> display only 10 lines at a time 

more +/"2023-07-15" -> will go to the first instance of this pattern
```

less -> allows you to scroll within a terminal when looking at large files 
	Space -> move forward a page 
	b -> move back a page 
	up/down arrow -> move up or down a line 
	G -> end of file
	g -> beginning of file
	q-> quit
	/search -> searches for specified information 
	n -> next occurrence of searched information 
	N -> previous occurrence 
	
```
less filename
-N -> display line numbers 

less +/ERROR:.Database server_log.txt
+/ERROR: -> jumps to the first occurance when opening file 
.Database -> fist occurance of ERROR: followed by any character than Database
```

Head command allows you to view multiple files at the same time 
	-c Displays the first few bytes of a file instead of lines 
	-q suppress headers when examining multiple files 
	-v Always displays headers when examining multiple files 

tail -> often used to view the end of a file
```
tail -n +50 filename -> starts at the 50th line and display till end of the file
```
live monitoring of a file 
```
tail -f filename
-f (follow)
```


nl -> used for line numbering 
```
nl filename
-b a -> numbers empty lines || -b controls the line numbering for the body of the file || -a stands for all

-n rz -> outcome 00001 for the first line and so on
-n -> specify the numbering format 
r -> right aligned 
z -> means adding leading zeroes 

```
pattern numbering 
```
nl -b p'^[^#]' filename

-b p -> only number lines that match the pattern 

'^[^#]' -> regular expression pattern ^ means start of line || [^#] mean any character that is not # 
```

##### File Searching 

which -> used to locate the executable files associated with a given command by searching through the directories listed in PATH environment variable 
```
which command -> which gcc 
-a -> discover all installations of a command 
```
The order of paths matter within the PATH variable || 
```
export PATH="$PATH:$HOME" -> adds the $home directory to the end of path for this termial session
```

whereis -> tool used to locate binary, source, and manual page files for various commands in the Linux system
```
whereis ls 
-b -> binary search || Binary fiels are the executable programs that run when you type a command 
-m -> manual pages search 
-s -> search for sources files || source files can be useful for understanding how a program works or for compiling custom versions
```

find -> used for locating files and directories based on various criteria 
```
find . -name "clue.txt"
. -> current directory 

find . -name "*.txt" -o -name "*.log"
-o -> means or 

-type f -> regular files 

-size +1M -> larger than 1 megabyte 

-mtime -1 -> files modified less than 1 day ago 
```
combined commands
```
find . -name "*.txt" -exec cat {} \; 

-exec cat {} \; -> execute the cat command, {} is a place holder for files found by find, and the \; ends the execute command. 
This prints the files to terminal that are found within this pattern 
```

##### Text Processing 


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

