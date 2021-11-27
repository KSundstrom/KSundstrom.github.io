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

## Week 2: Navigating a UNIX System

This week we watched an interview with Tatu Ylönen, the creator of `ssh` and PhD candidate at Uni Helsinki, and
learnt more about Unixlike systems. In particular, we learnt how to copy, move and remove directories, about
the standard system directories in a Unixlike system, about permissions and privacy in Unixlike systems, and how
to archive, extract, compress, and decompress files and directories using `tar` and `gzip`.

Furthermore, we learnt about processes and the management of processes, and how to control processes from the
command line.

Finally, we learnt how to work with remote servers using `ssh` and and the related `scp`, working
with the CSC server Puhti.

Among the basic shell commands we learnt this first week were:

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

For example, if we, in Bash as the user ‘user’, would want to log onto the remote server Puhti
using SSH, we would give the command:

```bash
~$ ssh user@puhti.csc.fi
```

Understanding and using SSH and SCP was something I had wanted to learn for a long time, so I very
much appreciated in particular these aspects of this week. I have since learnt a bit more and I am
now comfortable using RSA, ECDSA, and Ed25519 keys and SSH config and authorization files for
logging onto and working with a variety of different remote servers in a variety of different ways.

## Week 3: Basic Corpus Processing

Lorem ipsum

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
