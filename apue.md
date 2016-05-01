# Notes on *Advanced Programming in the UNIX Environment*

## Introduction (1)

### UNIX Architecture (1.2)

**operating system**

-   (strict) software that controls the hardware resources of a computer
    and provides an environment under which programs can run
-   (broad) all software that makes a computer useful, including system
    utilities, applications, shells, libraries

**kernel**: small core of the environment

**system calls**: programmatic interface to the kernel.  Applications
access system calls via either the shell or through library routines.
The system calls are listed in the man pages:

    $ man syscalls

The standard C library is described in `man libc`.  glibc is the most
commonly used standard C library in Linux.

Note: `man` pages are organized into 8 sections, corresponding to the
type of the command or term.  Examples of sections include (1) executable
programs, (2) system calls provided by the kernel, (6) games.

### Input and Output (1.5)

**File descriptor**: small non-negative integer that the kernel uses to
identify files accessed by a process.

Shells open three file descriptors whenever a new program is run:
standard input (0), output (1), and error (2) ([wikipedia](https://en.wikipedia.org/wiki/File_descriptor%5Dwikipedia)).  Constants
for these file descriptors are defined in `unistd.h`.

Note: To list metadata about a file use the command `stat`.

1.  Unbuffered I/O

    Unbuffered I/O is defined in `unistd.h` which provides the functions
    `open`, `read`, `write`, `lseek`, `close`.  These functions require a
    file descriptor as an argument.

2.  Standard I/O

    Buffered I/O is provided by `stdio.h`, including functions such as
    `fopen`, `fseek`, `fclose` These functions generally require a file
    pointer (`FILE *`) as an argument.  For a full list of functions, do
    
        $ man stdio

### Programs and Processes (1.6)

**program**

-   an executable file residing on disk in a directory
-   read into memory and executed as a results of one of 7 `exec` functions

**process**

-   an executing instance of a program (aka task)
-   identified by a non-negative integer called the **process ID**

1.  Process Control

    Functions for process control:
    
    1.  `fork`
    2.  `exec` (7 variants)
    3.  `waitpid`
    
    Note: to find the location of a header file, use `find` in
    /usr/include and /usr/lib (see [stackoverflow](http://stackoverflow.com/questions/13079650/how-can-i-find-the-header-files-of-the-c-programming-language-in-linux)).
    
    :dirstructure:
    Note: the Unix file system directory structure is defined in
    [Filesystem Hierarchy Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) as maintained by the Linux Foundation.

### Error Handling (1.7)

-   convention: a negative value is returned in the event of an error,
    while a non-negative value is returned for normal operation
-   the last error value stored in a global value called `errno` which
    is defined in `errno.h`
-   the function `perror` will print a string corresponding to the error

There are two categories of errors:

1.  fatal: has no recovery action.  print message and exit.
2.  non-fatal: could be due to a temporary condition, such as a
    resource crunch.  the action is to delay and retry again

### User Identification (1.8)

`getuid` and `getgit` return the user and group IDs, respectively.

Login name is in `/etc/passwd`

Users may belong to supplementary groups which are listed in
`/etc/group`.

### Signals (1.9)

**signal**: notifies a process that some condition has occurred

Use the `signal` to specify a function to handle the signal (signal handler)

    signal( SIGINT, sig_int)  // sig_int is the handler

A list of the signals can be found from `man -s 7 signal`.
