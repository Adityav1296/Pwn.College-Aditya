# Practicing Piping

## Redirecting Errors
Just like standard output, you can also redirect the error channel of commands. Here, we'll learn about File Descriptor numbers. A File Descriptor (FD) is a number that describes a communication channel in Linux.  
When you redirect process communication, you do it by FD number, though some FD numbers are implicit. For example, a > without a number implies 1>, which redirects FD 1 (Standard Output). Thus, the following two commands are equivalent:

```bash
hacker@dojo:~$ echo hi > asdf
hacker@dojo:~$ echo hi 1> asdf
```

Redirecting errors is pretty easy from this point. If you have a command that might produce data via standard error (such as /challenge/run), you can do:

```bash
hacker@dojo:~$ /challenge/run 2> errors.log
```

Furthermore, you can redirect multiple file descriptors at the same time! For example:

```bash
hacker@dojo:~$ some_command > output.log 2> errors.log
```

### Objective 
In this challenge, you will need to redirect the output of /challenge/run, like before, to myflag, and the "errors" (in our case, the instructions) to instructions.

### Solve
**Flag:** `pwn.college{wli1RBlChfOD1bW-HfT9VUIl4jE.ddjN1QDLygjN0czW}`

- In this challenge, following the given instructions, I direct the output of the `/challenge/run` command to myflag using '>' character while I redirect the error of this command to instructions file using '2>' character where '2' denotes that an error message is being redirected.

```bash
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat instructions
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will check that error output is redirected to a specific file path : instructions
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!

[TEST] You should have redirected my stderr to instructions. Checking...

[PASS] The file at the other end of my stderr looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-errors:~$ ls
Desktop  flag  home-backup.tar.gz  instructions  myflag  the-flag
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{wli1RBlChfOD1bW-HfT9VUIl4jE.ddjN1QDLygjN0czW}
```

### New Learnings
1. File descripters are the numbers used to describe the type of the file whether it is an input, output or an error message. The three common ones are :
   1. FD 0 : input
   2. FD 1 : output
   3. FD 2 : error
2. When we use the '>' character, it actually expands to '1>' meaning that the output is being redirected.
3. Similarly, using '2>' when redirecting means the error message is being redirected.