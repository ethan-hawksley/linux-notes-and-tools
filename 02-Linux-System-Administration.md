Sections 13-24

### 25/06/2026
Files store plenty of metadata.
Size, Permissions, Ownership, Timestamps (creation, access, modification).

A file has a pointer to an inode entry, which then points to where the data is physically stored.

Types of files:
Ordinary files (-)
Directories (d)
Symbolic links (l)
Character devices (c)
Block devices (b)
Named pipes (p)
Sockets (s)

ls -l
-rw-r--r--.  1 user user   510 Mar 28 17:16 .bashrc
drwx------. 15 user user  4096 Apr 25 19:42 .cache
The first character shows the type.
.bashrc has -, so it is a file.
.cache has d, so it is a directory.

Symlinks act as shortcuts, they point to other files.
Point to a specific path.
Works with files and directories.
ln -s target link
Creates a symbolic link to the target path.
If the file at the target path is replaced with a different one, the link is intact.

### 28/04/2026
Hard links are where multiple files point to the same inode.
Only after all files pointing to the inode are deleted, the data is deleted.
All files are technically hard links.
Hard links must all be on the same file system, as they point to the same inode.
Not all file systems support hard links. ext4 and btrfs do, but fat32 doesn't.

ext4 can run into an inode limit before filling the storage space itself.
btrfs allocates inodes dynamically and has no such limit.

Devices in linux are represented as files, or more accurately as streams of bytes.
Drivers in the kernel are responsible for representing devices in easy to interact ways.
Devices can be physical or virtual. For example, /dev/urandom is virtual.

Character devices (c):
Unbuffered access to the hardware. Accessed on a character by character level (byte by byte). Supports arbitrary reading.
Block devices (b):
Buffered access to the hardware. Data is delivered in blocks consisting of multiple bytes.
Pseudo devices:
Devices that aren't real. Can be either character or block devices, it depends.

### 04/05/2026
/dev/null
Reading it return EOF.
EOF is not a character, it is a signal from the kernel.
Writing to it discards input. 

/dev/random
Reading returns random data.
Requires environmental noise to produce the random data.
However, on recent kernels, it has been unified with /dev/urandom, and doesn't block anymore when there is low entropy, meaning it is practically limitless.

/dev/urandom
Also returns random data, but is more loose with entropy requirements.
This difference no longer matters, as it has been united with /dev/random

/dev/stdin, /dev/stdout, /dev/stderr
Correspond to the currently used terminal, reading or writing to them correspond to the basic terminal streams.
cp access.log /dev/stdout
Outputs the contents of the log to the terminal.

/proc files allow access to lots of information about the system.

cat /proc/cpuinfo
Outputs information about the current CPU(s).

cat /proc/meminfo
Outputs information about the memory.

cat /proc/version
Outputs information about the kernel, os, and compiler.

cat /proc/uptime
Outputs duration the system has been up, and duration it has been idle.

cat /proc/loadavg
Outputs load averages for system load over 1, 5, and 15 minutes.

### 07/05/2026
Filesystem Hierarchy Standard (FHS)
Dictates the structure of directories on the system.

/ (Root directory)

/bin
Contains all essential binaries, for day to day and if recovery was needed, etc.
Being migrated to /usr/bin, usually a symlink to /usr/bin.

/boot
Contains all files required for the bootloader.
Containing initramfs, kernels, grub2, efi, etc.

/dev
Contains device files, such as /dev/null, /dev/stdout, /dev/tty, etc.

/etc
Contains systemwide configuration, typically text files.

/home
Contains personal directories for each user.
Not typically featured if it is userless, e.g. a server with only a root account.

/lib, /lib32, /lib64
Contains libraries for binaries in other directories like /bin and /sbin.
/lib32 and /lib64 are explicitly 32bit and 64bit respectively.
These are being merged with /usr/lib, /usr/lib32, /usr/lib64 and are currently symlinks.

/media
Contains mount points to external media, e.g. USB drives or SD cards.

/mnt
Contains mount points for file systems that typically stay connected, like remote servers.

/opt
Contains optional software that's installed. Most software is installed in other places, but sometimes they do install to /opt.

/proc
Contains a virtual file system provided by procfs.
Provides information about processes and the kernel.

/root
Contains personal files for the root user.

/run
Contains runtime data that will not be preserved between boots.
df -h shows all the mounted filesystems. 
It shows that /run is a tmpfs, so data is lost on shutdown.

/sbin
Contains essential system binaries, typically used by the root user.
Being merged to /usr/sbin

/srv
Contains files being served by services.
Not frequently used, often /var is used instead.

/sys
Contains information about device drivers and kernel features.

/tmp
Contains temporary files.
Typically deleted on reboot.

/usr
Contains shareable, read-only data.
On a multi-user machine, many users can access this freely.
Contains binaries, documentation, source code, etc.
However, /usr/local is for files that should not be shared between computers.

/var
Contains variable data, for logs, databases, websites, email, etc.

There are many different types of linux user.

Root user has highest priviliges and id 0, there is only one root user.
Regular users have limited privileges but can be temporarily granted higher privileges through sudo.
Service users only do one specific task, like a web server or a database. They have limited privileges for security.

All users are placed in a primary group, and can be assigned an unlimited amount of additional groups.

/etc/passwd
Contains the info about accounts.
Username, user id, group id, user description, home directory, default shell.
Readable by all users.

/etc/shadow
Contains sensitive info about accounts.
Username, password hash, date of last password change, min and max password age, password warning period, inactivity period, and expiration date.
Requires root to read.

/etc/group
Contains info about which users are members of which groups.
Readable by all users.

useradd \[options] username
-m Make home directory at /home/username
-d Make home directory at custom path
-s Specify default shell
-g Specify primary group of the account
-G Specify list of secondary groups of the account

passwd \[options] username
-S Display password status
-d Delete password
-n Set minimum password age
-x Set maximum password age
-l Lock account
-u Unlock account

### 08/05/2026
usermod \[options] username
-c Change comment
-s Change login shell
-d Change home directory
-m Moves current home directory to new directory, requires -d
-l Change username
-g Change primary group
-G Change secondary groups
-aG Append list of groups to the user's secondary groups

chsh -s path/to/shell
Changes the current user's login shell.
The shell must be listed in /etc/shells

