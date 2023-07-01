# Linux

## Linux Introduction

there are literally hundreds of Linux distributions

the three main (most used) families and their most used distributions are..

**Red Hat** Family Systems (including **CentOS** and **Fedora**)
**SUSE** Family Systems (including **openSUSE**)
**Debian** Family Systems (including **Ubuntu** and **Linux** **Mint**)

note: Red Hat, SUSE, and Debian are all, themselves, distributions (maybe called 'pure' distributions)

Kernel version 5.8 is used in Ubuntu 20.04 LTS

in a narrow sense **Linux** refers only to the operating system **kernel**: the basic program that underlies everything else

when people use the loosely defined term **Linux System** they really should be saying **Linux-based System**

files are stored in a hierarchical filesystem with the top node of the system being the **root** or simply "/"

<u>Terms:</u>
**kernal**: glue between hardware and applications
**distribution**: a collection of softwares making up a Linux-based OS
**boot loader**: program that boots the OS (ex: GRUB and ISOLINUX)
**service**: program that runs as a background process (ex: httpd, nfsd, ntpd, ftpd, etc)
**filesystem**: method for organizing files (ex: ext3, ext4, FAT, XFS, NTFS, and Btrfs)
**X Window System**: provides the standard protocol for building out the GUI
**desktop environment**: the GUI (ex: GNOME and KDE)
**command line**: interface for typing commands
**shell**: command line interpreter that bridges the command line and the OS (ex: bash, tcsh, and zsh)

Linux borrows heavily from the **UNIX** operating system, Linus was well-versed in UNIX at the time he built LINUX.



## File Manipulation

Some basic command line utilities that are used constantly are..

**cat**: used to type out a file (or combine files).
**head**: used to show the first few lines of a file.
**tail**: used to show the last few lines of a file.
**man**: used to view documentation.

the pipe symbol `|` is used to have one program use the output of another program as input

for example you can 'pipe' an output into `grep` which will filter for `keyword`

ex: `ls | grep myfile`
or
`find | grep myfile`

Most input lines entered at the shell prompt have three basic elements:

Command
Options
Arguments

The command is the name of the program you are executing. It may be followed by one or more options (or switches) that modify what the command may do. Options usually start with one or two dashes, for example, -p or --print, in order to differentiate them from arguments, which represent what the command operates on.

a user configured with **sudo** capabilities provides the user with administrative (admin) privileges when required

**sudo** allows users to run programs using the security privileges of another user, generally root (superuser)

shutdown command: `sudo shutdown -h` or `sudo shutdown -P` (they do the same thing) or depending on your user priveleges, you may not need sudo.. use `shutdown now`

to locate a program's executable on the system, use the command `which`
for example `which typora` returns..
`/usr/bin/typora`

if `which` does not find the program, `whereis` can be used next to search through a broader range of system directories
for example `whereis typora` returns..
`typora: /usr/bin/typora /usr/share/typora`

`echo $HOME` will return the path to your home directory

`pwd` displays present working directory

`cd /home` change directory to /home.. cd = change directory aka open folder

`cd` change to your home directory

`cd ..` change to parent directory

`cd -` change to previous directory
`popd` does the same thing

`pushd /home` will change directory to /home AND show the directory we came from (and keep a record of your pushd/popd travels)

`dirs` lists the history of directories you recently visited using popd/pushd

`ls` list contents of pwd

`ls -a` list contents of pwd, including hidden files (all)

`ls -l` list contents of pwd, just with more info

`ls -lR` list contents of pwd, with more info, and shows contents of folders too

note `~` is shorthand for your home directory aka `/home/parker` = `~`

**Absolute Pathname**: always starts with `/` and writes out the whole path for ex `/home/parker/Dropbox/Apps`

**Relative Pathname**: starts from the pwd and so do not start with `/` and instead starts with..

`.` = present directory
`..` = parent directory
`~` = home directory

`tree` displays a tree view of the filesystem

`tree -d` displays a tree view of the filesystem (and suppresses file names)

`ln` creates a hard link between two files aka *shortcut* but DON'T do this bc it's screwy

`ln -s` creates a soft link, aka symbolic link, aka symlink which is a *shortcut* and is the **preferred** method for creating shortcut folders
can even be used to point to a path that doesn't currently exist, like to an unplugged usb
ex: `ln -s file1 file2` creates a shortcut (folder) called file2 which links to file1

<u>Manipulating Files</u>:

`cat filename` returns the contents of a file - used for viewing files that are not very long bc it does not provide any scroll-back

`tac filename` returns the contents of a file but starting with the last line - opposite of cat

`head` used to print the first 10 lines of a file (or use `head -15` to display the first fifteen, or any n)

`tail` used to print the last 10 lines of a file (or use `tail -15` to display the last fifteen, or any n)

`touch filename` creates a txt file called 'filename' in the current directory - unless a file already exists there by that name, in which case `touch` will simply update the file's timestamp to match the current time
`touch -t 12251600 filename` will set the file's timestamp to 4pm December 25th

`mkdir name` make directory - makes a directory named 'name' (in the current directory)

`mkdir /home/parker/name` \- makes a directory named 'name' (in the 'parker' folder)

`rmdir name` removes directory - deletes the folder 'name' but 'name' must be empty

`rm -rf name` removes directory recursively and forcefully - deletes the folder 'name' and all of its contents

`mv name name2` changes the name of name to name2 (if name2 already exists, it will be overwritten) works for files and folders

`mv name /home` moves the file 'name' to the folder '/home'

`cp name /home/newname` copies the file 'name' to the folder '/home' and names it 'newname'

`rm filename` will remove the file filename

`rm -f filename` will remove the file filename forcefully - does not prompt before deleting

`rm -i filename` will remove the file filename interactively - prompts before deleting

<u>File Input and Output</u>

a command typed into the command line or grabbed from a file is called a **stdin** (standard input)

the output of that command is called a **stdout** (standard output) unless it is an error message..

an output that is an error message is called a **stderr** (standard error)

normally **stdin** comes from your keyboard, **stdout** and **stderr** display in the command window

but we can change the source of **stdin** and the destinations of **stdout** and **stderr**

note these 'file descriptors' are labeled by number as **stdin = 0** and **stdout = 1** and **stderr = 2**

so if we want a program (command) called **do_something** to get its input from file 'input-file' we run the command

`do_something < input-file`

if we want **do_something** to print its output to file 'output-file' we run the command

`do_something > output-file` (output-file will be overwritten)

or

`do_something >> output-file` (output-file will be appended to)

if we want **do_something** to print its error messages to file 'error-file' we run the command

`do_something 2> error-file`

if we want the output *and* error messages to go to the same file we run the command

`do_something >& file`

Now..

we can also 'pipe' the output of one program (command) into another as input.. you do this with the pipe `|` symbol

`command1 | command2 | command3`

this is called a pipeline



## File Manipulation 2

`ls > foo.txt` will write the output from `ls` to `foo.txt` (and overwrite foo.txt if it exists)

`ls >> foo.txt` will write the output from `ls` to `foo.txt` (and append foo.txt if it exists)

use `unzip foo.zip` to unzip/extract a zip file to the current directory

use `unzip foo.zip -d /path/to/directory` to unzip/extract a zip file to `directory` which will be created if it does not exist

Wildcards: note that `*` represents **zero or more** characters, while `?` represents exactly one character

use wildcards to run commands on multiple files at once - for ex `wc *.txt`

`wc foo.txt` will display the number of

lines words characters

20 156 1158

in foo.txt

options: `-l` (lines) `-w` (words) `-m` (characters)

`sort foo.txt` will display the (sorted) contents of foo.txt (alphanumerically)

`sort -n foo.txt` will display the (sorted) contents of foo.txt (numerically)

note: option `-r` will reverse the sort order

note: sort does not manipulate the actual file

the `cut` command will display specified column(s) from a file(s) - the command expects the columns to be seperated by a delimiter (like , . - etc) and assumes a TAB as the default delimiter

else use option `-d ,` or `-d .` or `-d etc` to specify the delimiter

and option `-f n` as in `-f 2` to specify the column(s)

for example, for a text file with..

date,deer,5
date,rabbit,22
date,raccoon,7

`cut -d , -f 2 text.txt` would give..

deer
rabbit
raccoon

example: `wc -l *.txt | sort -n | head -n 1`

will display the number of lines in all .txt files in pwd

and sort those results numerically

and then display the first (1) line of those results (display the file with the fewest number of lines)



## Less

`less filename` used to view larger files because it is a paging program that provides scroll-back capabilities and lets you search and navigate within the file.

in less..
use `h` or `--help` to display help (summary of commands)
use `-J` to toggle the status column
use `-N` to toggle line numbers
use `-S` to toggle line wrapping (line portions longer than the screen are not shown)
use `-W` to highlight the first 'new' line of text after a forward movement
use `/pattern` to search forward in the file - the search starts at the first line displayed
use `/!pattern` to search for lines which do NOT contain pattern
use `-I` to cause searches to ignore lower/uppercase
use `n` to move to the next instance
use `shift n` to move to the previous instance 
use `g` to go to line 1 (top) of the file
use `Ng` to go to line N
use `G` to go to the end of the file
use `?pattern` to search backward in the file - the search starts at the last line displayed
use `&pattern` to display only lines which contain pattern
use `&!pattern` to display only lines which do NOT contain pattern
press `d` to scroll down a half page
press `u` to scroll up a half page
press `f` to scroll forward a full page
press `b` to scroll back a full page
press `q` to quit
press `F` to continually update the view for a file whose tail is being written to (to monitor the tail of a file which is growing while it is being viewed) This is similar to the "tail -f" command.
press `ESC F` which is like F, but as soon as a line is found which contains the last search pattern, the terminal bell is rung and forward scrolling stops.
press `ESC u` to turn off/on on highlighting of pattern or use `-G`

OR just use `gedit` honeslty



## SEARCHING for Files/Folders

`locate` command is a comprehensive search of all files/folders on your system that match a specified character string or filepath.
Note it will display all file paths containing that character string. Note `locate` utilizes a database created by the program `updatedb` which updates automatically once a day - so newly created files/folders won't always be found by `locate` therefore you can run the command `sudo updatedb` at any time to update the database before using the `locate` command

to search for a file path containing two separate words.. use `grep`

`locate newfolder | grep Desktop` will display all file paths that include both 'newfolder' and 'Desktop'

`?` represents any 1 character

`*` represents any 0+ characters

* * *

`find` command lists all files/paths in the pwd

`find | grep keyword` is a good way to search the pwd for something YES THIS

`find /home/parker/Desktop` lists all files/paths in the Desktop folder

ex `find . -name "searchterm"` note the . is the directory and you can use 'wildcards' like * and ? in the searchterm

the `-name` argument instructs to 'only list files with a certain pattern in their name' (always surround searchterm with **)

the `-i -name` arguments instructs just like `-name` but is not case sensative (always surround searchterm with **)

the `-type` argurment restricts the search to files of a certain type `d` = directory / `l` = symbolic link / `f` = regular file

`find -type f` lists files in the pwd

`find /usr -type f` lists files in the /usr directory

`find /usr -type f -name "*file3"` lists files in /usr that end in 'file3'

and we can execute commands on the entire results of a `find` for example..

`find /home -name "my*" -exec mv {} /usr ';'` finds the files in `/home` that start with `my` and moves them to `/usr` (note the `';'` is needed)

* * *

`find /home -ctime 3` will find files whose inode metadata (file ownership, permissions, etc) last changed 3 days ago (note this is usually the files creation date)

`find /home -atime 3` will find files that were last **accesses** 3 days ago

`find /home -mtime 3` will find files that were last **modified** 3 days ago

can also specify `+3` = greater than 3 days ago

`-3` = less than 3 days ago

`-cmin n` or `-amin n` or `-mmin n` would be for minutes

* * *

`find /home -size 1G` will find files whose size is 1 gigabyte. note: `c` = bytes or `k` = kilobytes or `M` = megabytes or `G` = gigabytes

`find /home -size +1G` greater than 1 gigabyte

`find /home -size -1G` less than 1 gigabyte

`find /home -size +1G -exec rm {} ';'` finds the files in `/home` that are greater than 1 gigabyte and removes them



## Software Installation intro

Linux File System Hierarchy: [Link](https://courses.edx.org/assets/courseware/v1/66def40e2774fd96011565107706da2d/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/dirtree.jpg) 

software installation files are referred to as 'packages'

some packages depend on other packages to work (both must be installed to work)

for Ubuntu, **dpkg** is the underlying package manager - it can install, remove, and build packages. But unlike higher-level package management systems, it does not automatically download and install packages and satisfy their dependencies.

for Ubuntu, **apt** (Advanced Packaging Tool) is the higher-level package manager. (ex: apt and apt-get)

on top of that, Ubuntu also creates its own user-interface for package management: Ubuntu Software Center

Synaptic Package Manager is a more old-school manager



## Package Management

the **Package Management System** is how the core parts of Ubuntu Linux and add-on software are installed

each package contains the files needed to make one software component work *and* cooperate with the other components in the system

packages can depend on each other

Ubuntu uses a **Debian**-based low-level package manager, as opposed to a **RPM**-based one, note the two are not compatible

`dpkg` program/command is the **low-level** package manager which takes care of the actual install

`apt` program/command is the **high-level** package manager which finds and downloads packages and figures out dependencies

we usually don't mess with `dpkg` because `apt` will usually command `dpkg` automatically

NOTE: because `apt` is in charge of finding and installing each dependency required to run a certain software/package - this means installing a single package could result in dozens or even hundreds of dependent packages being installed

`apt` = advanced packaging tool = the back-end for Ubuntu Software Center

`apt` = a command/program for finding and downloading packages from your linked repositories, then coordinating their install and satisfying dependencies

`apt-get` = a command that functions similar to apt - but apt is meant to be used interactively (you type it in) while apt-get is the preferred command to be used in a script - the syntax of apt and apt-get is identical for basic commands

* * *

APT INSTALL

not-yet-installed packages are stored in repositories which are distribution and version specific servers maintained by Ubuntu or other software distributors - my Ubuntu system already knows the paths to servers which contain many of the packages relevant to my Ubuntu system - these package files usually have the .deb extension

these repositories are defined in the `/etc/apt/sources.list` file and in the `/etc/apt/sources.list.d` directory

to edit the repositories: https://ubuntu.com/server/docs/package-management

`apt help` for more info

`sudo apt update` will update my *local* copies of these repositories

`apt search packagename` will search my local repositories for the package 'packagename'

if it is there, then you can use..

`sudo apt install packagename` to install it - and apt is smart enough to find and install needed dependencies - it will also remove packages that need to be removed in order for the new package to work

now, `which packagename` will show you the installed location



`wget` = a command/program for downloading files from the web with HTTP, HTTPS, or FTP protocol

`wget [options] [url]` when used without any option will download the resource specified (in the url) to the current directory (usually a .deb file)
then use `sudo apt install xxx.deb` to install it - you can `rm` the the .deb file after installation if desired

* * *

APT REMOVE

USE THIS `sudo apt remove packagename` will uninstall packagename - but keep its configuration files and dependency packages

THEN THIS `sudo apt purge packagename` will uninstall packagename and its configuration files - can be used on already uninstalled packages

`sudo apt autoremove packagename` will uninstall packagename and its dependency packages (if not used by other packages)

AND THIS `sudo apt autoremove` will uninstall all unused dependency packages from the system

*nothing here will delete config files in the /home directory (can be deleted manually if desired)

* * *

APT UPDATE

to upgrade (update) all apt-installed software (like update all on iPhone)..

`sudo apt update` again to update your local package repositories

`sudo apt upgrade` will upgrade any upgradable packages - note this does not upgrade (update) any packages that require something to be removed or if updating will require additional packages to be installed

`sudo apt dist-upgrade` will take care of those packages that require removal and/or additional packages to be installed - note this could also apply kernal or other major updates - and if it does you should probably reboot your computer afterwards

`sudo apt autoremove` will uninstall all unused dependency packages from the system

* * *

SNAP INSTALL/REMOVE

if the desired package is not in your local **APT** repositories it may be a snap package (or it may be a .deb but just not included in the default APT repositories) - also there may be both snap and .deb packages available for a program

snapcraft is a package management system by Canonical - snap packages differ from .deb packages in that they are packaged as archives - and the archive must be unpacked each time you run/execute the application - so the software runs in a sandbox, without ever editing your system files - it is not technically ever 'installed' on your system - also this means all dependencies are included in the snap package so there is no need to worry about dependencies

just like apt, snap can pull from repositories stored locally on your system, that are updated from external repositories

snaps are updated automatically - so no need to worry about manually updating

`snap help` for more info

`snap search packagename`

`sudo snap install packagename`

`sudo snap remove packagename`

you can also remove the folder `/home/parker/snap/packagename` if desired

*note since apt/deb packages are installed on your system - they will likely boot faster than snap apps

* * *

DPKG INSTALL

if the desired package is not available in your local apt or snap respositories..

find the .deb from the web - download it - run it through the GUI or you could..

`sudo apt install ./packagename.deb`

or in some rare cases you might use..

`sudo dpkg -i ./packagename.deb`

and then to resolve any dependency issues..

`sudo apt install -f` which will fix all broken dependencies on your system

* * *

RECOMMENDED to use apt over dpkg if possible

OTHER COMMANDS

`apt install packagename` fetch new version and update package and related dependencies

`dpkg -i ./packagename.deb` update package (if you have downloaded a new .deb file)

`dpkg --search filename` asks what package is 'filename' a part of



## UPDATE every month or so

to upgrade (update) all apt-installed software (like update all on iPhone)..

`sudo apt update` to update your local package repositories

`sudo apt upgrade` will upgrade any upgradable packages - note this does not upgrade any packages that require something to be removed or if upgrading will require additional packages to be installed

`sudo apt dist-upgrade` will take care of those packages that require removal and/or additional packages to be installed - note this could also apply kernal or other major updates - and if it does you should probably reboot your computer afterwards

`sudo apt install packagename` to upgrade those that were missed (if not running `dist-upgrade`)

`sudo apt autoremove` to remove any no-longer-needed dependency packages

<u>snap update:</u>

snap packages update automatically

<u>dpkg update:</u>

to update packages/software you downloaded manually from the web as .deb files, you would need to go and find the updated .deb file, download, and install it with..

`sudo apt install ./packagename.deb`

or in some rare cases you might use..

`sudo dpkg -i ./packagename.deb`

and then to resolve any dependency issues..

`sudo apt install -f` which will fix all broken dependencies on your system



## Documentation and Help

if you want help on, say, command **grep**
`whatis grep`
`grep --help`
`man grep`

----

**command help**

`help` or `--help` = provides a short description for most commands

ex `command --help`

ex `touch --help`

simply typing `help` will show the syntax of many commonly used commands

---

**man pages**

`man topic` will display the relevent page for 'topic' in the section | ex: (8) is section 8 | of the manual pages (there are 9 sections)

note that topic may appear in other sections of the manual, so use..

`whatis topic` will display which pages are called 'topic' = same as command `man -f topic`

`apropos topic` will display which pages involve topic = same as `man -k topic`

`man 7 topic` will display the man page for topic in section 7

navigate with `↑` and `↓` to move line-by-line, or try `b` and `f` to move full page. 

To search use `/` and move between hits using `n` (for moving forward) and `shift+n` (for moving backward)

---

**GNU info**

the GNU Info System is the GNU project's standard documentation - which is prefferred by some as an alternative to man because it supports linked subsections

it can be accessed through the command line, the GUI, or online

`info` displays an index of available topics

`info topic` displays information on 'topic'

the topic which you view in an info page is called a **node** which are essentially sections and subsections

to move between nodes..

n = go to next subsection

p = go to previous subsection

u = go up one level

t = go to the first subsection of this level

d = go to the main directory node

H = help and how to navigate 'info'

---

**other docs**

Ubuntu desktop guide (blue icon in the dock)

Package documentation - under the usr/share/doc directory - grouped in directories named after each package (with the version number)

Online reasorces - 



## Processes

a **process** is the execution of one or more related tasks (threads) on your system - it is not the same as a **program** or **command** as a single command may start several processes simultaneously

processes use system resources such as memory (RAM), CPU cycles, and peripheral devices such as network cards, hard drives, printers, and displays

the OS (especially the kernel) is responsible for allocating resources to each process and ensuring optimal system utilization

* * *

<u>Process Types:</u>

Interactive Process - needs to be started by a user (through CL or GUI) ex: bash and firefox

Batch Process - automatic processes which are scheduled from but then disconnected from the terminal ex: updatedb
these tasks are queued and work on a FIFO basis

Daemons - are server processes that run continuously - many are launched during system startup and ex: httpd and sshd
then wait for a user or system request indicating that their service is needed

Threads - are lightweight processes - tasks which run under the umbrella of a main process ex: firefox

Kernel Threads - are kernal tasks that users neither start nor terminate and have little control over ex: kthreadd

* * *

<u>Process IDs:</u>

at any given time there are multiple processes being executed

the OS keeps track of them by assigning each a unique **process ID** or **PID** number

new PIDs are assigned in ascending order as processes are born (starting with PID 1 as the `init` or initialization process at startup)

<u>PID types:</u>

PID - Process ID - a unique process ID number

PPID - Parent Process ID - is the process ID of the (parent) process that started this process - if the parent dies, then PPID defaults to 2

TID - Thread ID - is the ID number of the thread - this is the same as the PID for single-thread processes (note for a multi-threaded process, each thread will have the same PID but different TIDs)

* * *

<u>View and Kill a Process:</u>

to view processes from a GUI, run..

`gnome-system-monitor`

to view from the command line, run..

`ps` or `ps lf`

if a job is going to take a long time (like installing a large program) you can choose to run the job in the background

this way you will free the shell for other tasks - the background job will just be executed at lower priority, but it will finish eventually

to do this, attach a & to the end of the command, for ex..

`sudo updatedb &`

run `jobs -l` utility to display all jobs running in the background

you can use **CTRL-Z** to **suspend** a foreground job

you can use **CTRL-C** to **terminate** a foreground job

to terminate a process (like END TASK) use.. note you can only kill your own processes (unless you are root)

`kill -SIGKILL <pid>` or

`kill -9 <pid>`



## More Notes

