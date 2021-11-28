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

I have always been interested in writing systems and their digital representation, and thus the themes of this
week were particularly interesting to me. They were also particularly useful to me as an aspiring linguist and
language technologist. I knew the fundamentals of regular expressions from before, but I appreciated the
opportunity to repeat them, as well as learning how to use them through `grep` and `egrep` in a command-line
environment. I also appreciated learning about handling CSV and TSV files through the command line.

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

`cat text.utf8.txt` returns the text content of the text file, and the `|` pipes the output to the following
command, i.e. to the translation command `tr -s "[:space:][:punct:]" "\n"`, in which `"[:space:][:punct:]"`
indicates what we want to replace, i.e. the so-called Posix classes of all whitespace and punctuation characters,
and `"\n"` indicates what we want to translate these characters into, i.e. into newlines. The option `-s` squeezes
repeats, i.e. drops repeated replacements, so that we always get just one newline, not multiple newlines. Finally,
the output of the translation command is redirected into the file `text.utf8.tok.txt`.

## Week 4: Advanced Corpus Processing

This week we learnt about more advanced tools for text processing in Unixlike environments. First, we learnt about
the tool `sed`, or _stream editor_, a powerful command-line tool for quickly editing text files without opening
them in an editor. It can be used for finding strings, replacing strings, insertion, deletion, and other similar
tasks. It is commonly used with regular expressions, and thus we also repeated and learnt more about regular
expressions.

Finally, we also learnt more about combining simple commands into more complex pipelines in Unixlike environments.
In particular, we learnt how to create more advanced pipelines for processing text. Using pipelines, we don't
generate many unnecessary intermediate files.

Among the commands we learnt this week were:

**Command**  | **Usage**
:---         | :---
`sed`        | _stream editor_
`sed -n`     | `sed` without default printing
`sed -E`     | `sed` with extended regular expressions
`sed '//d'`  | `sed` delete
`sed '//p'`  | `sed` print
`sed 's//'`  | `sed` substitution
`sed 's//g'` | `sed` global substitution

The command `sed -n '/pattern/p'` would duplicate the function of `grep`, using the regular-expression pattern
`pattern`.

### Example

For example, if we had the text file `text.txt` (with LF line endings)which we wanted to transform into
one-sentence-per-line format, we could, in Bash, use the following command pipeline:

```bash
~$ cat text.txt | sed 's/^$/#/' | tr '\n' ' ' | sed -E 's/(.?!) ([[:upper:]])/\1# \2/g' | tr '#' '\n' | sed 's/^ *//' | sed 's/ *$//' | grep -v "^$" > text.sent.txt
```

`cat text.utf8.txt` returns the text content of the text file, and the `|` pipes the output to the following
command. The _stream-editor_ command `sed 's/^$/#/'` replaces empty lines (matched by the regular expression
`^$`) with a placeholder character `#`. The following command `tr '\n' ' '` replaces newlines with a space.
The following command `sed -E 's/(.?!) ([[:upper:]])/\1# \2/g'` uses extended regular expressions to find final
punctuation, followed by a space, followed by an uppercase character, and uses capture groups to insert a
placeholder `#` at the apparent end of the sentence. The following command `tr '#' '\n'` replaces the
placeholders `#` with newlines. The following command `sed 's/^ *//'` removes whitespace at the beginning of
a line and the following command `sed 's/ *$//'` at the end of a line. The final command `grep -v "^$"`
inversely finds empty lines, and thus returns all non-empty lines, while the final `> text.sent.txt` redirects
the output to the file `text.sent.txt`.

## Week 5: Scripting and Configuration Files

This week we learnt about Bash scripting as well as about Bash environment variables and configuration files.
Scripting can be described as storing a command pipeline, possibly complex and branching, as a programme, a file
which can be executed.

Specifically, we learnt the fundamentals of writing Bash scripts, about command-line variables and how to use
them in scripts, about conditional execution with `if`, and about command substitution. Furthermore, we learnt
about environment variables in Bash and how to alter the behaviour of the system by changing such variables.
Finally, we learnt how to use Bash configuration files such as `.bashrc` or `.bash_profile` to effectively make
changes to the environment permanent, by setting environment variables at login. This can, for example, be used
to set a helpful custom prompt, or to set useful custom shortcut commands.

Among the shell commands, statements, and variables we learnt this week were:

**Command** | **Usage**
:---        | :---
`chmod u+x` | Grants the owner of a file execution rights
`printenv`  | Returns all or part of the environment variables
`echo`      | Returns a line of text
`export`    | Exports a variable to the environment
`source`    | Reads and executes commands from the specified file
`alias`     | Creates an alias, i.e. a shortcut command
`if`        | Begins a conditional statement
`$?`        | Variable containing the exit status of the last task
`$#`        | Variable containing the number of arguments given

### Example

For example, if we wanted to write a simple Bash script for creating a word-frequency list based on a given text
file, outputting the list to another file, we could write the following script:

```bash
#!/bin/bash

if [ $# -ne 2 ]
then
	echo "ERROR: Two command line arguments required."
	echo "$0 input_text_file output_freq_file"
	exit 1
fi

cat $1 |
dos2unix |
tr -s "[:space:]" "\n" |
tr -d "[:punct:]" |
sort |
uniq -c |
sort -nr > $2
```

The very first line is a so-called shebang or hashbang, identifying what kind of script the script is. The
subsequent `if` block tests that the user has given exactly two arguments (an input file and an output file), and
aborts if the user has not. The final block is a pipeline taking the contents of file that was the first argument,
converting the line endings to LF, replacing all whitespace with newlines, deleting all punctuation, sorting the
list, counting repeated occurences, sorting the lines (now with number of occurences prepended) in reverse
numerical order, and outputting to the file that was the second argument.

## Week 6: Installing and Running Programs

This week we learnt about becoming the superuser or root user, about installing and managing software, about
Python packages and virtual environments, and about Makefiles.

We learnt it is not recommended to be logged in as the superuser more than absolutely necessary, which is why it
is wise to use `sudo` for running commands requiring superuser privileges.

Furthermore, we learnt that software generally has complicated dependencies, which is why software tends to be
managed with dedicated package managers, such as APT, which can be called with `apt` or `apt-get`. We also learnt
some fundamentals about the programming language Python, and learnt how to use Python’s package manager Pip to
manage Python packages, specifically. In connection with this, we also learnt about so-called virtual Python
environment, in which package dependencies are handled separately from the rest of the system. I have since tried
actively using both `venv` and `pipenv` virtual environments in other projects, generally preferring `venv`.

Finally, we learnt about Makefiles, a useful tool for building various projects in a command-line environment,
through automation of pipelines. The command used to build according to the Makefile is `make`.

Among the commands we learnt this week were:

**Command**   | **Usage**
:---          | :---
`sudo`        | Executes a command as the superuser (or another user)
`su`          | Runs an interactive shell as root (when no user specified)
`passwd`      | Changes user password
`apt-get`     | Calls the APT package manager
`locate`      | List files in databases matching a pattern
`python`      | Calls the Python interpreter
`pip`         | Calls Python’s package manager Pip
`pip install` | Has Pip install a Python package

### Example

This is an example of a Makefile which could be used in a project, where we wanted to run the shell scripts
`freqlist.sh` and `sent_per_line.sh` (located in the directory `bin`) on a possibly large number of text files
(located in the directory `data`; in this example there are only the two files `foo.txt` and `bar.txt`),
outputting to similarly named files in the directory `results`:

```makefile
# Makefile

TEXTS = foo bar
RESULTDIR = results
DATADIR = data
BINDIR = bin

FREQLISTS = $(TEXTS:%=$(RESULTDIR)/%.freq.txt)
SENTEDTEXTS = $(TEXTS:%=$(RESULTDIR)/%.sent.txt)

.PHONY: all clean

all: $(FREQLISTS) $(SENTEDTEXTS)

$(RESULTDIR)/%.freq.txt: $(DATADIR)/%.txt
	$(BINDIR)/freqlist.sh $< $@

$(RESULTDIR)/%.sent.txt: $(DATADIR)/%.txt
	$(BINDIR)/sent_per_line.sh $< $@

clean:
	@echo "Cleaning up..."
	rm -f $(RESULTDIR)/*
```

To explain some part in detail, the `clean` block is a rule `make` rule for cleaning up what has been built, by
(forcibly) removing all files in the `results` directory. It first echoes, i.e. prints, the string ‘Cleaning
up...’ and then calls the ordinary Bash command `rm`. The `clean` rule can be called from the command line with
`make clean`.

## Week 7: Version Control

Lorem ipsum

Among the shell commands we learnt this week were:

**Command** | **Usage**
:---        | :---
``          | 

### Example

```bash
~$ 
```

## Final Assignment: Building Webpages using GitHub Pages

Jekyll and GitHub Pages

Among the shell commands we learnt this week were:

**Command** | **Usage**
:---        | :---
``          | 

### Example

```bash
~$ 
```
