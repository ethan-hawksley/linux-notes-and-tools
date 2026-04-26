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

### 06/04/2026
grep -F "password" file.txt
Searches for the string password in file.txt. Returns all lines which contain the pattern.

grep is supposed to be used for text files, not binary files.

### 08/04/2026
tr stands for translate.
Performs replacements on a per-character level.

echo 'bash' | tr 'a-z' 'A-Z'
Outputs BASH, as it converts all lowercase to uppercase.
echo 'bash' | tr 'bh' 't'
Outputs tast
echo 'abcdefghijklmnopqrstuvwxyz' | tr 'a-z' '0-9'
Outputs 01234567899999999999999999
echo 'this is a sentence' | tr -d ' '
Outputs thisisasentence

rev stands for reverse.
Reverses the provided text.
echo 'bash' | rev
Outputs hsab.

echo 'aoeu' | cut -b 1-2
Outputs ao, it outputs bytes 1 and 2
echo 'aoeu' | cut -c 2-
Outputs oeu, but it outputs all characters after the second, inclusive. It uses the locale to distinguish character boundaries.

uptime
 20:30:11 up  3:02,  2 users,  load average: 0.11, 0.03, 0.01
uptime | cut -d ' ' -f 2
20:30:11
The uptime command outputs with a leading space. To access the time, you must use spaces as a delimiter, and check the second field.

### 10/04/2026

echo 'hello world' | sed 's/wor/bui/'
Outputs hello build. sed is useful for substitution, amongst other things.
echo 'what and why' | sed 's/wh/th/g'
Outputs that and thy. By default, sed only replaces once per line. Use the g flag to replace multiple times.

### 12/04/2026

cat access.log | cut -d ' ' -f 7 | grep -F '.zip' | sort -u | wc -l
Outputs the number of unique zip files accessed from a web server.

cut -d ' ' -f 7 access.log | grep -F '.zip' | sort -u | wc -l
Also outputs the number of zip files. cut can read files directly, it doesn't need to pipe through cat.

echo "$SHELL"
echo "${SHELL}"
Both output the environment variable containing the path to the shell.
Favour ${VARIABLE} syntax as it is more explicit.
It allows for variables such as "${SHELL}aoeu".

$HOME stores path to user's home directory.
$PWD stores current working directory.
$OLDPWD stores previous working directory.
$USER stores the username.

export GREETING1=hi
export GREETING2=hello everybody
export GREETING3='hello everybody'
echo $GREETING1 , $GREETING2 , $GREETING3
Outputs hi , hello , hello everybody
Environment variables must be quoted if they are more than one word.

unset GREETING1
Deletes the corresponding environment variable.

PATH stores all the directories to be searched for executables.
Delimited by colons.
Searched sequentially until a matching command is found.

Different directories have historic significance.
/bin and /usr/bin store standard binaries.
/sbin and /usr/sbin store binaries that typically require root.
On modern systems, /bin and /sbin are often symlinks.

/usr/local/bin and /usr/local/sbin are binaries specific for this host.

To append directories to the path, use:
PATH="${PATH}:/path/to/directory"

which cat
Outputs /usr/bin/cat, which is the file location of the binary.

Shebangs at the top of a file tell the shell how to run it.
#!/bin/bash
#!/bin/sh
#!/usr/bin/env python3
The shell will run the file in the corresponding program.
/usr/bin/env python3 makes the shell lookup where python3 is actually located, and use that path, instead of hardcoding one.

import os
print(os.environ)
This prints out all the environment variables. They are accessible to all called programs.

API_KEY='1234' python program.py
Environment variables can be passed specifically to programs one-off, and not preserved.

ch -s '/bin/bash'
This changes the default shell for the system to bash.

Interactive Login Shell
These are raw tty's. You can access them by using Ctrl + Alt + F3-6.
Return to the main desktop with Ctrl + Alt + F2
These run /etc/profile and the first of the following:
	~/.bash_profile
	~/.bash_login
	~/.profile

Interactive Non-Login Shell
These are terminals you access through a terminal emulator, e.g. Konsole.
These run ~/.bashrc

Non-Interactive Login Shell
These are shells when you run a set of instructions, but for example the computer is over SSH, so you need to login before those instructions run automatically.
echo 'test' | ssh server
Runs the file indicated by BASH_ENV, if it exists.

Non-Interactive Non-Login Shell
These are shells spawned by running shell scripts.
Runs the file indicated by BASH_ENV, if it exists.

### 16/04/2026
Changes to .bashrc don't take effect immediately, need sourcing.
. .bashrc or source .bashrc work identically.

alias gohome='cd ~'
Sets gohome as an alias for cd ~
Single quotes used so bash doesn't expand command.

### 19/04/2026
Use set to change the features of bash.

set -FEATURE
Enables a sh feature.
set +FEATURE
Disables a sh feature.

set -x
Prints every command the shell executes.

shopt -s FEATURE
Enables a bash feature.
shopt -u FEATURE
Disables a bash feature.

PS1 is a special bash variable that controls the appearance of the prompt.
PS1='prompt$ '
Makes all prompts start with the string prompt$

PS1 supports many placeholders.
\u for username.
\h for hostname.
\H for full hostname.
\w for working directory path.
\W for the name of the working directory.
\t for 24h time.
\\@ for 12h time.
\\$ for a $ for normal users, # for root users.

Terminals interpret escape sequences as instructions to change rendering.
echo -e '\e\[30;40m'
This changes the colour of the foreground to black, and the background to black.

### 22/04/2026
The infocmp command outputs a list of supported escape codes.

echo "The files in this directory are: $(ls)"
$(ls) is command substitution to run one command within another.

tput clear
Clears your screen by outputting the relevant escape codes to stdout.
tput cup 5 20
Moves cursor to row 5 column 20.
echo -n "$(tput cup 5 20)"
Also moves cursor to row 5 column 20.

echo "\$(tput bold)this is bold$(tput sgr0) and this isn't."
Outputs **this is bold** and this isn't.
sgr0 represents the reset.

In scripts, tput should be executed once and stored in a bash variable.
bold=$(tput bold)
reset=$(tput sgr0)
echo "\${bold}this is bold${reset} and this isn't."

tput smul
Start underline
tpum rmul
Stop underline

tput setaf COLOUR
Set foreground colour. COLOUR is one of the terminal numbers.
tput setab COLOUR
Set background colour. COLOUR is one of the terminal numbers.

for i in {0..255}; do echo "$(tput setab ${i}) colour: ${i}$(tput sgr0)"; done
Prints all available colours in the terminal colour palette.
However, most modern terminals support true colour, so they don't need to use this palette.

In PS1, bash needs to know how long it is to print correctly. To do this, wrap all non-printing escape sequences with \\\[ \\].

### 23/04/2026
Shell expansions are done by the shell before execution.

echo \*Public
Outputs Public.
\* expands to every file and directory in the directory, and matches 0 or more characters.
\* cannot match hidden files.
? expands to all files and directory, but only matches a single character.
echo \*e\*
Outputs all files and directories containing e.

~ is expanded by bash to the value of the $HOME environment variable.

### 24/04/2026
~+ expands to $PWD value.
$PWD is preferred in practice as it is more readable.

Bash does word splitting based on spaces.
By using double quotes "" or single quotes '', the splitting is prevented.

### 25/04/2026
echo $HOME
echo ${HOME}
echo "$HOME"
echo "${HOME}"
All of the above function, but "${HOME}" is the clearest and prevents word splitting.

echo ${#PATH}
Outputs length of variable in bytes, unicode characters count as multiple.

${VARIABLE:start:length}
echo ${PATH:0:4}
Outputs /hom, extracting the substring.

${VARIABLE/pattern/replacement}
${VARIABLE//pattern/replacement}
Performs find and replace. / does it once, // does it multiple times.

echo 'hello'"world"
Outputs helloworld, it is entirely valid. Quotes are stripped and the whole thing is outputted.

test=cat
$test --help
Outputs the help text for cat.

mkdir test && cd $_
touch echo
*
Outputs a newline, as the echo program was run.

echo data.{txt,csv}
Outputs data.txt data.csv
Brace expansion automatically generates words for each combination.
echo {a..z}
Outputs the alphabet.
echo {18..26}
Outputs all numbers between 18 and 26 inclusive.
echo {26..18}
Outputs all numbers between 18 and 26 inclusive in reverse.

echo "The directory is $(pwd)"
Executes the command inside $().
Should be in double quotes to avoid word splitting.

diff <(ls directory1) <(ls directory2)
Outputs the diff of the two directories
<(command) creates a temporary pipe that can be used as a file.

wc -l < <(ls)
This works too, the files can be redirected to stdin, though in most cases using | is clearer.

echo test > >(cat)
Outputs test. echo outputs test, which is redirected to the temporary file, and cat reads the data as stdin.