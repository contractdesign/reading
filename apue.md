Notes on "Advanced Programming in the UNIX Environment 3rd Edition" (APUE)

# Introduction

## Section 1.2

**operating system** definition:

-   (strict) software that controls the hardware resources of a computer
    and provides an environment under which programs can run
-   (broad) all software that makes a computer useful, including system
    utilities, applications, shells, libraries

**kernel**: small core of the environment

**system calls**: programmatic interface to the kernel.  Applications
access system calls via either the shell or library routines.

Comment: `man` pages are organized into 8 sections, corresponding to the
type of the command or term.  Examples of sections include (1) executable
programs, (2) system calls provided by the kernel, (6), games.

## Section 1.5

**File descriptor**: small non-negative integer that the kernel uses to
identify files accessed by a process.

Shells open three file descriptors whenever a new program is run:
standard input (0), output (1), and error (2) ([wikipedia](https://en.wikipedia.org/wiki/File_descriptor%5Dwikipedia)).  Constants
for these file descriptors are defined in <unistd.h>.

### Unbuffered I/O (<unistd.h>)

Unbuffered I/O is provided by functions `open`, `read`, `write`,
`lseek`, `close`.  These functions require a file descriptor as an
argument.

### Standard I/O (stdio.h)

Buffered I/O is provided stdio.h

## Section 1.6 Programs and Processes

**program**

-   an executable file residing on disk in a directory
-   read into memory and executed as a results of one of 7 `exec` functions

**process**

-   an executing instance of a program (aka task)
-   identified by a non-negative integer called the **process ID**

### Process Control

Functions for process control:

1.  `fork`
2.  `exec` (7 variants)
3.  `waitpid`

Comment: to find the location of a header file, use `find` in
/usr/include and /usr/lib (see [stackoverflow](http://stackoverflow.com/questions/13079650/how-can-i-find-the-header-files-of-the-c-programming-language-in-linux)).

## TODO how is /usr organized?

## TODO continue notes after figure 1.7
