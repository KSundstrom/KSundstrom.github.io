---
layout: default
---

# Command-Line Tools for Linguists

The course KIK-LG221 _Command-Line Tools for Linguists_ is a regular intermediate-level undergraduate course
at Uni Helsinki comprising 5 credits. Students are recommended to have previously taken the introductory
course on language technology.

The course focusses on basic usage of Unix-like command-line tools, basic regular expressions, handling text
files and different character encodings with the command line, handling text corpora using command-line tools,
running and installing applications from the command line, writing basic scripts, working with remote servers,
and using version-control tools.

## Week 1: Introduction to Command-Line Environments

This week we had a live lecture on how computers work, and learnt about Linux and Unix, about setting up a
command-line environment, some basic Bash commands, how to quit applications, about command-line text editors,
and about file formats and sizes.

I use Windows on my laptop, so in order to get a Unixlike command line up and running, I chose to install
Windows Subsystem for Linux, and to try a few different distros for it, among these Debian, Ubuntu, Kali Linux,
openSUSE, and Alpine. In the end, I settled for Debian, and have used it as my primary command-line environment
ever since. During the course, I upgraded from Windows 10 to Windows 11, and from WSL1 to WSL2. I also learnt how
to upgrade my Debian distro, and am now running Debian 12 Bookworm.

Here is Debian’s well-known swirl logo:

![Debian’s Open Use Logo](https://www.debian.org/logos/openlogo-nd-100.png "Debian’s Open Use Logo")

Among the basic shell commands we learnt this first week were:

**Command** | **Usage**
:---        | :---
`ls`        | Lists the contents of the currect directory
`pwd`       | Returns the currect working directory
`whoami`    | Returns the current user
`mv`        | Moves (or renames) a file
`cat`       | Concatenates files
`less`      | Displays file contents with scrolling ability
`cp`        | Copies a file
`rm`        | Removes a file
`mkdir`     | Creates a new directory
`cd`        | Changes the current directory

We also learnt how to fetch contents from the internet using `wget`, and how to open and edit text files with the
text editor `emacs`.

We also learnt various keys and key combinations for quitting applications, for example:

* Single keys:
  * q
  * Esc
* Key combinations:
  * Ctrl-c
  * Ctrl-d
* Multiple key combinations:
  * Ctrl-x Ctrl-c

### Example

For example, if we, in Bash as the user ‘user’, would want to create a new directory named ‘foo’, move into it,
confirm where we are in the directory tree (i.e. print our current working directory), then move back up in the
directory tree, and finally confirm who we are (i.e. print the current user), our terminal would look like this:

```bash
~$ mkdir foo
~$ cd foo
~/foo$ pwd
/home/user/foo
~/foo$ cd ..
~$ whoami
user
```

## Week 2: Navigating a UNIX System

This week we watched an interview with Tatu Ylönen, the creator of `ssh` and PhD candidate at Uni Helsinki, and
learnt more about Unixlike systems. In particular, we learnt how to copy, move and remove directories, about
the standard system directories in a Unixlike system, about permissions and privacy in Unixlike systems, and how
to archive, extract, compress, and decompress files and directories using `tar` and `gzip`.

Furthermore, we learnt about processes and the management of processes, and how to control processes from the
command line.

Finally, we learnt how to work with remote servers using `ssh` and and the related `scp`, working
with the CSC server Puhti.

Among the shell commands we learnt this week were:

**Command** | **Usage**
:---        | :---
`cp -R`     | Copies recursively
`rm -R`     | Removes recursively
`rmdir`     | Removes an empty directory
`which`     | Returns the pathname of the file a command would execute
`ls -F`     | `ls` with indication of item type
`top`       | Provides a real-time view of the system and its processes
`&`         | Starts a process in the background
`fg`        | Brings a process to the foreground
`ps`        | Lists the current processes
`kill`      | Sends a signal to a process, typically to end it
`ssh`       | Connects securely to a remote server via SSH
`scp`       | Copies securely to a remote server via SSH

We also learnt the key combination Ctrl-z to stop the currently running process.

Understanding and using SSH and SCP was something I had wanted to learn for a long time, so I very
much appreciated in particular these aspects of this week. I have since learnt a bit more and I am
now comfortable using RSA, ECDSA, and Ed25519 keys and SSH config and authorization files for
logging onto and working with a variety of different remote servers in a variety of different ways.

### Example

For example, if we, in Bash, would want to log onto the remote server Puhti as the user ‘user’ using
SSH, we would give the command:

```bash
~$ ssh user@puhti.csc.fi
```

## Week 3: Basic Corpus Processing

This week we learnt about various fundamental tools for text processing in Unixlike environments. First, we
learnt about different character encodings, in particular about ASCII, Latin-1, and UTF-8, and how to convert
between these. We also learnt about the different line endings in Windows and UNIX text files, and how to
convert between these.

Furthermore, we learnt various useful commands for processing and searching text, about standard streams and
their redirection, and the basics of regular expressions. Finally, we also learnt about structured text, such
as tables in the form of CSV or TSV, and commands for processing such structured text.

Among the shell commands we learnt this week were:

**Command**   | **Usage**
:---          | :---
`file`        | Returns information about a file, e.g. encoding and line endings
`dos2unix`    | Converts CRLF line endings to LF line endings
`unix2dos`    | Converts LF line endings to CRLF line endings
`iconv`       | Converts text from one character encoding to another
`tr`          | Translates, squeezes, or deletes characters
`sort`        | Sorts lines in alphabetical or numerical order
`uniq`        | Reports or omits repeated lines
`head`        | Returns the beginning of a file
`tail`        | Returns the end of a file
`wc`          | Returns the number of lines, words, or bytes in file
`cut`         | Remove sections from each line
`grep`        | Returns lines matching the given regular expression pattern
`egrep`       | `grep` with extended regular expressions

I have always been interested in writing systems and their digital representation, and thus the themes of this week
were particularly interesting to me. They were also particularly useful to me as an aspiring linguist and language
technologist. I knew the fundamentals of regular expressions from before, but I appreciated the opportunity to
repeat them, as well as learning how to use them through `grep` and `egrep` in a command-line environment. I also
appreciated learning about handling CSV and TSV files through the command line.

### Example

For example, if we had the text file `text.txt` with CRLF line endings and Latin-1 encoding, and, in Bash,
would want to convert the line endings to LF, convert the encoding to UTF-8, and then tokenize the text, our
terminal would look like this:

```bash
~$ dos2unix text.txt
dos2unix: converting file text.txt to Unix format...
~$ iconv -f latin1 -t utf-8 text.txt > text.utf8.txt
~$ cat text.utf8.txt | tr -s "[:space:][:punct:]" "\n" > text.utf8.tok.txt
```

The option `-f latin1` in `iconv -f latin1 -t utf-8 text.txt > text.utf8.txt` indicates the encoding _from_ which
we want to convert, i.e. Latin-1, and `-t utf-8` the encoding _to_ which we want to convert, i.e. UTF-8. The `>`
redirects the output, and thus `> text.utf8.txt` redirects the result of the conversion into the file
`text.utf8.txt`.

`cat text.utf8.txt` returns the text content of the text file, and the `|` ‘pipes’ the output to the following
command, i.e. to the translation command `tr -s "[:space:][:punct:]" "\n"`, in which `"[:space:][:punct:]"`
indicates what we want to replace, i.e. the so-called Posix classes of all whitespace and punctuation characters,
and `"\n"` indicates what we want to translate these characters into, i.e. into newlines. The option `-s` squeezes
repeats, i.e. drops repeated replacements, so that we always get just one newline, not multiple newlines. Finally,
the output of the translation command is redirected into the file `text.utf8.tok.txt`.

## Week 4: Advanced Corpus Processing

Lorem ipsum

## Week 5: Scripting and Configuration Files

Lorem ipsum

## Week 6: Installing and Running Programs

Lorem ipsum

## Week 7: Version Control

Lorem ipsum

## Final Assignment: Building Webpages using GitHub Pages

Jekyll and GitHub Pages
