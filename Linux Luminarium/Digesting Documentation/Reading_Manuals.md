# Digesting Documentation 

## Reading Manuals
This level introduces the man command. man is short for manual, and will display (if available) the manual of the command you pass as an argument. For example, let's say we wanted to learn about the yes command:

```bash
hacker@dojo:~$ man yes
YES(1)                           User Commands                          YES(1)

NAME
       yes - output a string repeatedly until killed

SYNOPSIS
       yes [STRING]...
       yes OPTION

DESCRIPTION
       Repeatedly output a line with all specified STRING(s), or 'y'.

       --help display this help and exit

       --version
              output version information and exit

AUTHOR
       Written by David MacKenzie.

REPORTING BUGS
       GNU coreutils online help: <https://www.gnu.org/software/coreutils/>
       Report any translation bugs to <https://translationproject.org/team/>

COPYRIGHT
       Copyright  ©  2020  Free Software Foundation, Inc.  License GPLv3+: GNU
       GPL version 3 or later <https://gnu.org/licenses/gpl.html>.
       This is free software: you are free  to  change  and  redistribute  it.
       There is NO WARRANTY, to the extent permitted by law.

SEE ALSO
       Full documentation <https://www.gnu.org/software/coreutils/yes>
       or available locally via: info '(coreutils) yes invocation'

GNU coreutils 8.32               February 2022                          YES(1)
```

The important sections are:

```
NAME(1)                           CATEGORY                          NAME(1)

NAME
	This gives the name (and short description) of the command or
	concept discussed by the page.

SYNOPSIS
	This gives a short usage synopsis. These synopses have a standard
	format. Typically, each line is a different valid invocation of the
	command, and the lines can be read as:

	COMMAND [OPTIONAL_ARGUMENT] SINGLE_MANDATORY_ARGUMENT
	COMMAND [OPTIONAL_ARGUMENT] MULTIPLE_ARGUMENTS...

DESCRIPTION
	Details of the command or concept, with detailed descriptions
	of the various options.

SEE ALSO
	Other man pages or online resources that might be useful.

COLLECTION                        DATE                          NAME(1)
```

You can scroll around the manpage with your arrow keys and PgUp/PgDn. When you're done reading the manpage, you can hit q to quit.

Manpages are stored in a centralized database. If you're curious, this database lives in the /usr/share/man directory, but you never need to interact with it directly: you just query it using the man command. The arguments to the man command aren't file paths, but just the names of the entries themselves

### Objective
The challenge in this level has a secret option that, when you use it, will cause the challenge to print the flag. You must learn this option through the man page for challenge!

### Solve
**Flag:** `pwn.college{obVbBPa6hQyssBv2m8yvHR2BLBZ.dRTM4QDLygjN0czW}`

-> In this challenge, the first thing I did was to use *man* command with *challenge* as the argument to understand how the *challenge* command works.  
-> Then I changed my directory to */challenge* and ran the different versions of the *challenge* program. They were:
  1. /challenge/challenge --version
  2. /challenge/challenge --fortune
  3./challenge/challenge --obbahy NUM ->to get the flag if the NUM is 628.

```bash
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ cd /challenge
hacker@man~reading-manuals:/challenge$ ls
DESCRIPTION.md  bin  challenge
hacker@man~reading-manuals:/challenge$ ./challenge --version
I"'"m exactly the version I need to be!
hacker@man~reading-manuals:/challenge$ ./challenge --fortune
* wichert_ imagines master without a MTA
<james> wichert: ehm?  that might hinder peformance of the BTS :p
hacker@man~reading-manuals:/challenge$ ./challenge --obbahy 628
Correct usage! Your flag: pwn.college{obVbBPa6hQyssBv2m8yvHR2BLBZ.dRTM4QDLygjN0czW}
```

### New Learning
1. Commands in Linux can be used in various different ways according to the situation. To understand and make use of the different options provided by the command, we use the *man command* command which displays the manual for that particular program.  
2. From the manual we can see how different options work with that command and their correct syntax under the DESCRIPTION section. These options can then be used to perform specific tasks through that command.