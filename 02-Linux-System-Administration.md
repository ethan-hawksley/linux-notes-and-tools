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
