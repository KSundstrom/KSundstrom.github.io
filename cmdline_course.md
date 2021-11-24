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
`pwd`       | Prints the currect working directory
`whoami`    | Prints the current user
`mv`        | Moves (or renames) a file
`cat`       | Concatenates files
`less`      | Displays file contents
`cp`        | Copies a file
`rm`        | Removes a file
`mkdir`     | Creates a new directory
`cd`        | Changes the current directory

For example, if we, in Bash, would want to create a new directory named ‘foo’, move into it, confirm where we are
in the directory tree (i.e. print our current working directory), then move back up in the directory tree, and
finally confirm who we are (i.e. print the current user), our terminal would look like this:

```bash
~$ mkdir foo
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
the standard system directories in a Unixlike system, and about permissions and privacy in Unixlike systems.
Furthermore, we learnt about processes and the management of processes, and how to control processes from the
command line. Finally, we learnt how to work with remote servers using `ssh` and and the related `scp`, working
with the CSC server Puhti.

cp -R
rm -R
rmdir
which
ls

This is going to be some repetition from last week and some new contents on how to copy, move and delete files
and directories. This tutorial uses the option "-F" for the ls command. It makes ls indicate whether the items
are regular files or directories by appending a slash at end of he directory name. You can try it out if you like.

Users, groups and file permissions

There can be several users on a single UNIX computer. File permissions are a system for controlling which
files users can access and also controlling the way that they can access the files. Each file has an owner
and the owner can decide what kind of access she grants to other users.

Reducing the size of a file/directory by compressing it

Read about compressing and decompressing files and directories using the command gzip and tar.

Each time we run a command on the command line, or execute a program, a new process is started in our
operating system. The following video talks about the basics of processes, and process management in the
command line.

top, &, fg, CTRL+Z, ps, kill

It is becoming more and more common to work on remote servers which provide us much better computational
resources (ie. GPUs) and memory space than our personal computers can hope to match. In this video, we will
see the basics of how we can connect and work on such a remote server, as well as how we can transfer files
to and from such a server.

ssh, scp

We use the ssh command for connecting to remote servers, and scp for copying files to/from servers.

If you have questions about how to set up the .ssh/config file, you can find more information here

Some useful scp tips: (eg. How to send/receive multiple files at once, How to send/receive all files of a
certain type, etc)

* You are able to copy, move and delete a directory.
* You have visited the root directory of your system. 
* You know how to compress a file and a directory using gzip and tar.
* You know how to find out and change the read and write permissions for a file.
* You can find the PID of a process and kill it.
* You're able to run commands in the background.
* You know how to form a remote connection to a server.
* You can to copy files to and from a server using scp.

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
