# File Globbing

## Matching with *
The first glob we'll learn is *. When it encounters a * character in any argument, the shell will treat it as a "wildcard" and try to replace that argument with any files that match the pattern.

```bash
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_*
Look: file_a file_b file_c
```

Of course, though in this case, the glob resulted in multiple arguments, it can just as simply match only one.  
When zero files are matched, by default, the shell leaves the glob unchanged:

```bash
hacker@dojo:~$ touch file_a
hacker@dojo:~$ ls
file_a
hacker@dojo:~$ echo Look: nope_*
Look: nope_*
```

The * matches any part of the filename except for / or a leading . character. For example:

```bash
hacker@dojo:~$ echo ONE: /ho*/*ck*
ONE: /home/hacker
hacker@dojo:~$ echo TWO: /*/hacker
TWO: /home/hacker
hacker@dojo:~$ echo THREE: ../*
THREE: ../hacker
```

### Objective 
Starting from your home directory, change your directory to /challenge, but use globbing to keep the argument you pass to cd to at most four characters! Once you're there, run /challenge/run for the flag!

### Solve
**Flag:** `pwn.college{AqvkLx552oBZvGpjO8W6IrA_f0C.dFjM4QDLygjN0czW}`

-> This was a direct challenge where I just had to use '*' and keep the number of argument characters to cd command limited to 4.  
-> So since the first character will be '/' and one of the characters has to be *, therefore I just chose any 2 random characters from the word challenge and put them in the argument to solve the challenge and obtain the flag.

```bash
This challenge resets your working directory to /home/hacker unless you change
directory properly...
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /c*e
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{AqvkLx552oBZvGpjO8W6IrA_f0C.dFjM4QDLygjN0czW}
```

### New Learnings
1. The * symbol can replace any of the characters in the file name. As a result, the shell tries to replace the * symbol with any files that match the pattern given before or after it.  
2. Using this, we can search up multiple files having the same pattern by a single command rather than searching them one by one.  
3. We can also use * symbol to perform its function with the directories as well, just like how we did in this challenge.