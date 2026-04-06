Sections 1-12

### 19/03/2026
CentOS Stream & Ubuntu are two major distributions.
CentOS Stream supports SELinux properly unlike Ubuntu, and it is downstream from RHEL.

Using Oracle Virtualbox for virtualisation of the operating system.
For following the course, using Rocky Linux 9 instead of CentOS. It is very similar but more stable and well supported by the Virtualbox custom drivers due to an older kernel version.

### 24/03/2026
epel-release is an additional repository that enables access to more packages on Rocky Linux.

sudo dnf install epel-release
sudo dnf install gcc kernel-devel kernel-headers make bzip2 perl

Installs plenty of packages necessary for compiling and installing the VirtualBox drivers.

### 28/03/2026
Bash expands globs before the command even gets to see what's passed to it
ls \*.jpg
The command only sees ls a.jpg, b.jpg. Not the directory itself.

If there are no matches to the glob, it is passed as a literal string.
In zsh, it errors instead of passing a literal string.

In bash, ? is expanded as any single character.
[0-9] is expanded as any number.
[a-z] is expanded as any lowercase letter.

\*\* is expanded as any number of characters, including the /
To find files, you need \*\*/\*.txt
\*\* requires enabling with shopt -s globstar
If used like \*\*.txt, it falls back to acting like a single asterisk.
It only functions when alone as \*\* or as \*\*/pattern

Globbing can be dangerous.
$ echo \*
-rf, documents, important.txt, secrets.txt
$ rm \*
$ ls
-rf
Bash expands the file names before the program sees them, so it can treat some file names as parameters.

It can be avoided through either:
rm -- \*
rm ./*
The first forces the command to view all subsequent text as arguments, not parameters.
The second prefixes all of the glob results with ./, ensuring they are processed as a path.


Find creates a list of files.
find .
Lists all of the files and directories recursively from current working directory.
find . -type f
Lists only files.
find . -type d
Lists only directories.
find . -type f -mtime -7
Lists only files modified less than 7 days ago.
find . -type f -mtime 7
Lists only files modified exactly 7 days ago.
find . -type f -mtime +7
Lists only files modified greater than 7 days ago.
find . -type f -size +10M
Lists only files greater than 10MB.
find . -type f -size +10M -delete
Delete all files greater than 10MB.

### 29/03/2026
Catting binary data can be a real threat.
Special characters in the sequence can hide others, making malicious scripts seem benign.
It is also a common cause of CVE's in terminal emulators.

Can use head and tail to read parts of files.
head -n 5 romeo.txt
Outputs the first 5 lines of romeo.txt
tail -n 15 romeo.txt
Outputs the last 15 lines of romeo.txt

Less acts like a read-only vi.
j & k for up and down.
g and G for start and end.
= for information about current position.
-N for line numbers.
/ and ? to search forwards and backwards.

wc -lwc romeo.txt
Outputs number of lines, words, and characters (bytes) in file.
aoeue

### 31/03/2026
du romeo.txt
Outputs size of file on disk, in terms of disk blocks. Each block is 1024 bytes. On a mac, a block is 512 bytes.
du --apparent-size romeo.txt
Outputs size of the file itself, in terms of disk blocks.
du -h romeo.txt
Outputs size of the file in a human readable way. Includes units.

### 01/04/2026
2 main cli editors for text files are nano and vi/vim
Nano is more straightforward, but vim is quicker and I've already learned it so I'll be using that.
In benchmarking vim-minimal, vim, and neovim, they were approximately performant in that order.

### 02/04/2026
Use > to write to file.
Use >> to append to file.

The 3 main streams are stdin, stdout, and stderr.

\> is shorthand for 1> and redirects stdout.
2> redirects stderr.

du file.txt > stdout.txt 2> stderr.txt
This redirects the two types of output to two different files.

This works with >>, so 2>> can be used to append the stderr.

du file.txt > stdout.txt 2> /dev/null
Discards the stdout.

### 03/04/2026
du file.txt > output.txt 2>&1
Writes stdout to output.txt, and sends stderr to where stdout is currently going.
du file.txt 2>&1 > output.txt
Writes stdout to output.txt, and sends stderr to where stdout usually goes, e.g. the terminal.
The order matters where 2>&1 is placed.

Many commands accept stdin when not given a filename.

wc -l < document.txt
This feeds the contents of a file as stdin, instead of as an argument.

### 04/04/2026
ls | cat
When ls is being used in a pipe, it outputs the list of files on newlines.

echo 'Hello World' | tee output.txt
This outputs Hello World, and stores it to a file. tee does both.

ls | tee debug.txt | wc -l
tee can be inserted in the middle of a pipe chain without breaking logic.

sort students.txt
Outputs all of the students, in alphabetical order.

sort students.txt | uniq
Outputs sorted students without duplicates. uniq requires sorted data, as it only compares each line to the previous.

sort -u students.txt
This outputs sorted students without duplicates too. It does it in one command and is more idiomatic.

sort students.txt | uniq -d
Outputs a sorted list of only the duplicates. Each duplicate appears once.