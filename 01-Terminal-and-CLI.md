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
The command only sees ls a.jpg, b.jpg. Not the folder itself.

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

$ echo \*
-rf, documents, important.txt, secrets.txt
$ rm \*
$ ls
-rf

Bash expands the file names before the program sees them, so it can treat some file names as parameters. This is very dangerous.
It can be avoided through either
rm -- \*
rm ./*
The first forces the command to view all subsequent text as arguments, not parameters.
The second prefixes all of the glob results with ./, ensuring they are processed as a path


